---
ms.openlocfilehash: cc29a6e9d358ba35d1e1ddd336b9df88ba68739b
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98689704"
---
# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>As APIs do WinRT padrão

A maneira mais comum e fácil de usar o WinRT é chamar métodos de WinSDK. Para fazer isso, abra o arquivo YourModule.Build.cs e adicione as seguintes linhas:

```csharp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

Em seguida, você precisa adicionar os seguintes cabeçalhos do WinRT: 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

O código do WinRT só pode ser compilado nas plataformas Win64 e HoloLens, portanto, a instrução If impede que as bibliotecas do WinRT sejam incluídas em outras plataformas. unknwn. h foi adicionado para ter a interface IUnknown. 


## <a name="winrt-from-a-nuget-package"></a>WinRT de um pacote NuGet

É um pouco mais complicado se você precisar adicionar um pacote NuGet com suporte a WinRT. Nesse caso, o Visual Studio pode executar praticamente todo o trabalho para você, mas o sistema de compilação não real não pode. Felizmente, isso não é muito difícil. Veja abaixo um exemplo de como você faria para baixar o pacote Microsoft. MixedReality. QR. Você pode substituí-lo por outro, apenas certifique-se de que você não perca o arquivo winmd e copie a dll correta. 

SDK do Windows DLLs da seção anterior são manipuladas pelo sistema operacional. As DLLs do NuGet devem ser gerenciadas pelo código em seu módulo. É recomendável adicionar o código para baixá-los, copiar para a pasta de binários e carregar na memória do processo na inicialização do módulo.

Na primeira etapa, você deve adicionar um packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) na pasta raiz do seu módulo. Lá, você deve adicionar todos os pacotes que deseja baixar, incluindo todas as suas dependências. Aqui, adicionei o Microsoft. MixedReality. QR como uma carga primária e dois outros como dependências a ele. O formato desse arquivo é o mesmo que no Visual Studio:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

Agora você pode baixar o NuGet, os pacotes necessários ou consultar a [documentação](/nuget/consume-packages/install-use-packages-nuget-cli)do NuGet.

Abra YourModule.Build.cs e adicione o seguinte código:

```csharp
// WinRT with Nuget support
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string [] { "shlwapi.lib", "runtimeobject.lib" });

    // prepare everything for nuget
    string MyModuleName = GetType().Name;
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    ExternalDependencies.Add("packages.config");

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if (!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
            // we aren't focusing on a specific nuget version, we can use any of them but the latest one is preferable
            myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }

    // get list of the installed packages, that's needed because the code should get particular versions of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] { '\r', '\n' });

    // winmd files of the packages
    List<string> WinMDFiles = new List<string>();

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        string WinMDFile = Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd");
        SafeCopy(WinMDFile, Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())),
            Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        //add winmd file to the list for further processing using cppwinrt.exe
        WinMDFiles.Add(WinMDFile);
    }

    if (Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if (!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach (var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);
    }
    else
    {
        // fall back to default WinSDK headers if no winrt package in our list
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }
}
```

Você precisará definir o método SafeCopy da seguinte maneira:

```csharp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

As DLLs do NuGet precisam ser carregadas manualmente na memória do processo Win32; é recomendável adicionar o carregamento manual ao método de inicialização do seu módulo:

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

Por fim, você pode incluir cabeçalhos do WinRT em seu código, conforme descrito na seção anterior.

# <a name="425"></a>[4.25](#tab/425)

Inreal não compila nativamente o código WinRT na versão 4,25, portanto, é o seu trabalho criar um binário separado que o sistema de compilação não real possa consumir. 

## <a name="objectives"></a>Objetivos

- Criar uma DLL universal do Windows que abre um FileSaveDialogue
- Vincular essa DLL a um projeto de jogo não real
- Salvar um arquivo no HoloLens de um projeto não real usando a nova DLL

## <a name="getting-started"></a>Introdução

1. Verifique se você tem todas as [ferramentas necessárias](../tutorials/unreal-uxt-ch1.md) instaladas
2. [Criar um novo projeto inreal](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) e nomeá-lo **Consumewinrt**
3. Habilitar os [plug-ins necessários](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) para o desenvolvimento do HoloLens
4. [Configuração para implantação](../tutorials/unreal-uxt-ch6.md) em um dispositivo ou emulador

## <a name="creating-a-winrt-dll"></a>Criando uma DLL do WinRT 

1. Abra um novo projeto do Visual Studio e crie um projeto **dll (universal do Windows)** no mesmo diretório que o arquivo **uproject** do jogo inreal. 

![Criando uma DLL](../images/unreal-winrt-img-01.png)

2. Nomeie o projeto **HoloLensWinrtDLL** e defina o local como um subdiretório **ThirdParty** para o arquivo uproject do jogo inreal. 
    * Selecione **posicionar solução e projeto no mesmo diretório** para simplificar a procura de caminhos mais tarde. 

![Configurando a DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Depois que o novo projeto for compilado, preste atenção especial aos arquivos cpp e de cabeçalho em branco, chamados **HoloLensWinrtDLL. cpp** e **HoloLensWinrtDLL. h** , respectivamente. O cabeçalho é o arquivo de inclusão que usa a DLL em tempo real, enquanto a cpp mantém o corpo de todas as funções que você exporta e inclui qualquer código do WinRT que não seja possível compilar de outra forma. 

3. Antes de adicionar qualquer código, você precisa atualizar as propriedades do projeto para garantir que o código do WinRT que você precisa pode compilar: 
    * Clique com o botão direito do mouse no projeto HoloLensWinrtDLL e selecione **Propriedades**  
    * Alterar a lista suspensa de **configuração** para **todas as configurações** e a lista suspensa de **plataforma** para **todas as plataformas**  
    * Em **Propriedades de configuração> C/C++> todas as opções**:
        * Adicionar **Await** a **Opções adicionais** para garantir que possamos aguardar em tarefas assíncronas  
        * Alterar o **padrão de linguagem C++** para **ISO C++ 17 Standard (/std: C++ 17)** para incluir qualquer código do WinRT

![Atualizando Propriedades do projeto](../images/unreal-winrt-img-03.png)

Seu projeto está pronto para atualizar a origem da DLL com o código do WinRT que abre uma caixa de diálogo de arquivo e salva um arquivo no disco do HoloLens.  

## <a name="adding-the-dll-code"></a>Adicionando o código DLL

1. Abra **HoloLensWinrtDLL. h** e adicione uma função exportada de dll para consumir inrealmente: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Abra **HoloLensWinrtDLL. cpp** e adicione todos os cabeçalhos que a classe usará:  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> Todo o código do WinRT é armazenado em **HoloLensWinrtDLL. cpp** , de modo que não tente incluir nenhum código do winrt ao referenciar o cabeçalho. 

3. Ainda em **HoloLensWinrtDLL. cpp**, adicione um corpo de função para OpenFileDialogue () e todo o código com suporte: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Adicione uma classe SaveGameManager a **HoloLensWinrtDLL. cpp** para manipular a caixa de diálogo do arquivo e salvar o arquivo: 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. Compile a solução para a **versão > ARM64** para criar a dll para o diretório filho ARM64/Release/HoloLensWinrtDLL da solução de dll. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Adicionar o binário do WinRT a um não real 
Vincular e usar uma DLL em um Unreal requer um projeto C++. Se você estiver usando um projeto Blueprint, ele poderá ser facilmente convertido em um projeto C++ adicionando uma classe C++:  

1. No editor inreal, abra **arquivo > nova classe C++...** e crie um novo **ator** chamado **WinrtActor** para executar o código na DLL: 

![Criando um novo ator](../images/unreal-winrt-img-04.png)

> [!NOTE]
> Agora, uma solução foi criada no mesmo diretório que o arquivo uproject, juntamente com um novo script de compilação chamado source/ConsumeWinRT/ConsumeWinRT. Build. cs.

2. Abra a solução, procure a pasta **Games/ConsumeWinRT/origem/ConsumeWinRT** e abra **ConsumeWinRT.Build.cs**:

![Abrindo o arquivo ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Vinculando a DLL
1. Em **ConsumeWinRT.Build.cs**, adicione uma propriedade para localizar o caminho de inclusão para a dll (o diretório que contém HoloLensWinrtDLL. h). A DLL está em um diretório filho para o caminho de inclusão, portanto, essa propriedade será usada como a dir raiz binária:

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. No construtor de classe, adicione o seguinte código para atualizar o caminho de inclusão, vincular a nova lib e atrasar o carregamento e copiar a DLL para o local Appx empacotado:

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. Abra **WinrtActor. h** e adicione uma definição de função, que será chamada por um plano gráfico: 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. Abra **WinrtActor. cpp** e atualize BeginPlay para carregar a dll: 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> A DLL deve ser carregada antes de chamar qualquer uma de suas funções.

### <a name="building-the-game"></a>Criando o jogo
1. Crie a solução de jogos para iniciar o editor inreal aberto no projeto de jogo: 
    * Na guia **local atores** , pesquise o novo **WinrtActor** e arraste-o para a cena 
    * Abra o Blueprint de nível para executar a função que tem o plano de execução no **WinrtActor** 

![Colocando o WinrtActor na cena](../images/unreal-winrt-img-06.png)

2. Na estrutura **mundial**, encontre o **WindrtActor** que foi previamente colocado na cena e arraste-o para o plano Blueprint: 

![Arrastando o WinrtActor para o plano gráfico de nível](../images/unreal-winrt-img-07.png)

3. No nível Blueprint, arraste o nó saída de WinrtActor, procure a **caixa de diálogo abrir arquivo** e, em seguida, encaminhe o nó de qualquer entrada do usuário.  Nesse caso, a caixa de diálogo abrir arquivo está sendo chamada de um evento de fala: 

![Configurando nós no nível Blueprint](../images/unreal-winrt-img-08.png)

4. [Empacote este jogo para o HoloLens](../tutorials/unreal-uxt-ch6.md), implante-o e execute-o.  

Quando as chamadas inreais OpenFileDialogue, uma caixa de diálogo de arquivo é aberta no HoloLens solicitando um nome de arquivo. txt.  Depois que o arquivo for salvo, vá para a guia **Explorador de arquivos** no portal do dispositivo para ver o conteúdo "Olá WinRT". 

## <a name="summary"></a>Resumo 

Incentivamos você a usar este tutorial como um ponto de partida para consumir o código do WinRT em um estado inreal quando precisar salvar arquivos no disco do HoloLens usando a mesma caixa de diálogo de arquivo que o Windows.  O mesmo processo se aplica à exportação de funções adicionais do cabeçalho HoloLensWinrtDLL e usado em um não real.  Preste atenção especial ao código de DLL que aguarda no código de WinRT assíncrono em um thread MTA de segundo plano, que evita o deadlock do thread de jogo inreal.