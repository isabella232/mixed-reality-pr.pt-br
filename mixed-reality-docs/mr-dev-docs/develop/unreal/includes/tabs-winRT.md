---
ms.openlocfilehash: be267da576e020e88f08d475395b144d42285383
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609397"
---
# <a name="425"></a>[<span data-ttu-id="2af55-101">4.25</span><span class="sxs-lookup"><span data-stu-id="2af55-101">4.25</span></span>](#tab/425)

<span data-ttu-id="2af55-102">Inreal não compila nativamente o código WinRT na versão 4,25, portanto, é o seu trabalho criar um binário separado que o sistema de compilação não real possa consumir.</span><span class="sxs-lookup"><span data-stu-id="2af55-102">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary that Unreal’s build system can consume.</span></span> 

## <a name="objectives"></a><span data-ttu-id="2af55-103">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2af55-103">Objectives</span></span>

- <span data-ttu-id="2af55-104">Criar uma DLL universal do Windows que abre um FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="2af55-104">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="2af55-105">Vincular essa DLL a um projeto de jogo não real</span><span class="sxs-lookup"><span data-stu-id="2af55-105">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="2af55-106">Salvar um arquivo no HoloLens de um projeto não real usando a nova DLL</span><span class="sxs-lookup"><span data-stu-id="2af55-106">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="2af55-107">Introdução</span><span class="sxs-lookup"><span data-stu-id="2af55-107">Getting started</span></span>

1. <span data-ttu-id="2af55-108">Verifique se você tem todas as [ferramentas necessárias](../tutorials/unreal-uxt-ch1.md) instaladas</span><span class="sxs-lookup"><span data-stu-id="2af55-108">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="2af55-109">[Criar um novo projeto inreal](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) e nomeá-lo **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="2af55-109">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="2af55-110">Habilitar os [plug-ins necessários](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) para o desenvolvimento do HoloLens</span><span class="sxs-lookup"><span data-stu-id="2af55-110">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="2af55-111">[Configuração para implantação](../tutorials/unreal-uxt-ch6.md) em um dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="2af55-111">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="2af55-112">Criando uma DLL do WinRT</span><span class="sxs-lookup"><span data-stu-id="2af55-112">Creating a WinRT DLL</span></span> 

1. <span data-ttu-id="2af55-113">Abra um novo projeto do Visual Studio e crie um projeto **dll (universal do Windows)** no mesmo diretório que o arquivo **uproject** do jogo inreal.</span><span class="sxs-lookup"><span data-stu-id="2af55-113">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory as the Unreal game’s **uproject** file.</span></span> 

![Criando uma DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="2af55-115">Nomeie o projeto **HoloLensWinrtDLL** e defina o local como um subdiretório **ThirdParty** para o arquivo uproject do jogo inreal.</span><span class="sxs-lookup"><span data-stu-id="2af55-115">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="2af55-116">Selecione **posicionar solução e projeto no mesmo diretório** para simplificar a procura de caminhos mais tarde.</span><span class="sxs-lookup"><span data-stu-id="2af55-116">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configurando a DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="2af55-118">Depois que o novo projeto for compilado, preste atenção especial aos arquivos cpp e de cabeçalho em branco, chamados **HoloLensWinrtDLL. cpp** e **HoloLensWinrtDLL. h** , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2af55-118">After the new project compiles, pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="2af55-119">O cabeçalho é o arquivo de inclusão que usa a DLL em tempo real, enquanto a cpp mantém o corpo de todas as funções que você exporta e inclui qualquer código do WinRT que não seja possível compilar de outra forma.</span><span class="sxs-lookup"><span data-stu-id="2af55-119">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="2af55-120">Antes de adicionar qualquer código, você precisa atualizar as propriedades do projeto para garantir que o código do WinRT que você precisa pode compilar:</span><span class="sxs-lookup"><span data-stu-id="2af55-120">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="2af55-121">Clique com o botão direito do mouse no projeto HoloLensWinrtDLL e selecione **Propriedades**</span><span class="sxs-lookup"><span data-stu-id="2af55-121">Right-click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="2af55-122">Alterar a lista suspensa de **configuração** para **todas as configurações** e a lista suspensa de **plataforma** para **todas as plataformas**</span><span class="sxs-lookup"><span data-stu-id="2af55-122">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="2af55-123">Em **Propriedades de configuração> C/C++> todas as opções**:</span><span class="sxs-lookup"><span data-stu-id="2af55-123">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="2af55-124">Adicionar **Await** a **Opções adicionais** para garantir que possamos aguardar em tarefas assíncronas</span><span class="sxs-lookup"><span data-stu-id="2af55-124">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="2af55-125">Alterar o **padrão de linguagem C++** para **ISO C++ 17 Standard (/std: C++ 17)** para incluir qualquer código do WinRT</span><span class="sxs-lookup"><span data-stu-id="2af55-125">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Atualizando Propriedades do projeto](../images/unreal-winrt-img-03.png)

<span data-ttu-id="2af55-127">Seu projeto está pronto para atualizar a origem da DLL com o código do WinRT que abre uma caixa de diálogo de arquivo e salva um arquivo no disco do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2af55-127">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="2af55-128">Adicionando o código DLL</span><span class="sxs-lookup"><span data-stu-id="2af55-128">Adding the DLL code</span></span>

1. <span data-ttu-id="2af55-129">Abra **HoloLensWinrtDLL. h** e adicione uma função exportada de dll para consumir inrealmente:</span><span class="sxs-lookup"><span data-stu-id="2af55-129">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="2af55-130">Abra **HoloLensWinrtDLL. cpp** e adicione todos os cabeçalhos que a classe usará:</span><span class="sxs-lookup"><span data-stu-id="2af55-130">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="2af55-131">Todo o código do WinRT é armazenado em **HoloLensWinrtDLL. cpp** , de modo que não tente incluir nenhum código do winrt ao referenciar o cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="2af55-131">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="2af55-132">Ainda em **HoloLensWinrtDLL. cpp**, adicione um corpo de função para OpenFileDialogue () e todo o código com suporte:</span><span class="sxs-lookup"><span data-stu-id="2af55-132">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="2af55-133">Adicione uma classe SaveGameManager a **HoloLensWinrtDLL. cpp** para manipular a caixa de diálogo do arquivo e salvar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="2af55-133">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="2af55-134">Compile a solução para a **versão > ARM64** para criar a dll para o diretório filho ARM64/Release/HoloLensWinrtDLL da solução de dll.</span><span class="sxs-lookup"><span data-stu-id="2af55-134">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="2af55-135">Adicionar o binário do WinRT a um não real</span><span class="sxs-lookup"><span data-stu-id="2af55-135">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="2af55-136">Vincular e usar uma DLL em um Unreal requer um projeto C++.</span><span class="sxs-lookup"><span data-stu-id="2af55-136">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="2af55-137">Se você estiver usando um projeto Blueprint, ele poderá ser facilmente convertido em um projeto C++ adicionando uma classe C++:</span><span class="sxs-lookup"><span data-stu-id="2af55-137">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="2af55-138">No editor inreal, abra **arquivo > nova classe C++...**</span><span class="sxs-lookup"><span data-stu-id="2af55-138">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="2af55-139">e crie um novo **ator** chamado **WinrtActor** para executar o código na DLL:</span><span class="sxs-lookup"><span data-stu-id="2af55-139">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Criando um novo ator](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="2af55-141">Agora, uma solução foi criada no mesmo diretório que o arquivo uproject, juntamente com um novo script de compilação chamado source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="2af55-141">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="2af55-142">Abra a solução, procure a pasta **Games/ConsumeWinRT/origem/ConsumeWinRT** e abra **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="2af55-142">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Abrindo o arquivo ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="2af55-144">Vinculando a DLL</span><span class="sxs-lookup"><span data-stu-id="2af55-144">Linking the DLL</span></span>
1. <span data-ttu-id="2af55-145">Em **ConsumeWinRT.Build.cs**, adicione uma propriedade para localizar o caminho de inclusão para a dll (o diretório que contém HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="2af55-145">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="2af55-146">A DLL está em um diretório filho para o caminho de inclusão, portanto, essa propriedade será usada como a dir raiz binária:</span><span class="sxs-lookup"><span data-stu-id="2af55-146">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="2af55-147">No construtor de classe, adicione o seguinte código para atualizar o caminho de inclusão, vincular a nova lib e atrasar o carregamento e copiar a DLL para o local Appx empacotado:</span><span class="sxs-lookup"><span data-stu-id="2af55-147">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="2af55-148">Abra **WinrtActor. h** e adicione uma definição de função, que será chamada por um plano gráfico:</span><span class="sxs-lookup"><span data-stu-id="2af55-148">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="2af55-149">Abra **WinrtActor. cpp** e atualize BeginPlay para carregar a dll:</span><span class="sxs-lookup"><span data-stu-id="2af55-149">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="2af55-150">A DLL deve ser carregada antes de chamar qualquer uma de suas funções.</span><span class="sxs-lookup"><span data-stu-id="2af55-150">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="2af55-151">Criando o jogo</span><span class="sxs-lookup"><span data-stu-id="2af55-151">Building the game</span></span>
1. <span data-ttu-id="2af55-152">Crie a solução de jogos para iniciar o editor inreal aberto no projeto de jogo:</span><span class="sxs-lookup"><span data-stu-id="2af55-152">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="2af55-153">Na guia **local atores** , pesquise o novo **WinrtActor** e arraste-o para a cena</span><span class="sxs-lookup"><span data-stu-id="2af55-153">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="2af55-154">Abra o Blueprint de nível para executar a função que tem o plano de execução no **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="2af55-154">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Colocando o WinrtActor na cena](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="2af55-156">Na estrutura **mundial**, encontre o **WindrtActor** que foi previamente colocado na cena e arraste-o para o plano Blueprint:</span><span class="sxs-lookup"><span data-stu-id="2af55-156">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Arrastando o WinrtActor para o plano gráfico de nível](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="2af55-158">No nível Blueprint, arraste o nó saída de WinrtActor, procure a **caixa de diálogo abrir arquivo** e, em seguida, encaminhe o nó de qualquer entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="2af55-158">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="2af55-159">Nesse caso, a caixa de diálogo abrir arquivo está sendo chamada de um evento de fala:</span><span class="sxs-lookup"><span data-stu-id="2af55-159">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configurando nós no nível Blueprint](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="2af55-161">[Empacote este jogo para o HoloLens](../tutorials/unreal-uxt-ch6.md), implante-o e execute-o.</span><span class="sxs-lookup"><span data-stu-id="2af55-161">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="2af55-162">Quando as chamadas inreais OpenFileDialogue, uma caixa de diálogo de arquivo é aberta no HoloLens solicitando um nome de arquivo. txt.</span><span class="sxs-lookup"><span data-stu-id="2af55-162">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="2af55-163">Depois que o arquivo for salvo, vá para a guia **Explorador de arquivos** no portal do dispositivo para ver o conteúdo "Olá WinRT".</span><span class="sxs-lookup"><span data-stu-id="2af55-163">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="2af55-164">Resumo</span><span class="sxs-lookup"><span data-stu-id="2af55-164">Summary</span></span> 

<span data-ttu-id="2af55-165">Incentivamos você a usar este tutorial como um ponto de partida para consumir o código do WinRT em um estado inreal quando precisar salvar arquivos no disco do HoloLens usando a mesma caixa de diálogo de arquivo que o Windows.</span><span class="sxs-lookup"><span data-stu-id="2af55-165">We encourage you to use this tutorial as a starting point for consuming WinRT code in Unreal when you need to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="2af55-166">O mesmo processo se aplica à exportação de funções adicionais do cabeçalho HoloLensWinrtDLL e usado em um não real.</span><span class="sxs-lookup"><span data-stu-id="2af55-166">The same process applies to exporting additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="2af55-167">Preste atenção especial ao código de DLL que aguarda no código de WinRT assíncrono em um thread MTA de segundo plano, que evita o deadlock do thread de jogo inreal.</span><span class="sxs-lookup"><span data-stu-id="2af55-167">Pay special attention to the DLL code that waits on async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

# <a name="426"></a>[<span data-ttu-id="2af55-168">4.26</span><span class="sxs-lookup"><span data-stu-id="2af55-168">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="2af55-169">As APIs do WinRT padrão</span><span class="sxs-lookup"><span data-stu-id="2af55-169">The standard WinRT APIs</span></span>

<span data-ttu-id="2af55-170">A maneira mais comum e fácil de usar o WinRT é chamar métodos de WinSDK.</span><span class="sxs-lookup"><span data-stu-id="2af55-170">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="2af55-171">Para fazer isso, abra o arquivo YourModule.Build.cs e adicione as seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="2af55-171">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```cpp
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

<span data-ttu-id="2af55-172">Em seguida, você precisa adicionar os seguintes cabeçalhos do WinRT:</span><span class="sxs-lookup"><span data-stu-id="2af55-172">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
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

<span data-ttu-id="2af55-173">O código do WinRT só pode ser compilado nas plataformas Win64 e HoloLens, portanto, a instrução If impede que as bibliotecas do WinRT sejam incluídas em outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="2af55-173">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="2af55-174">unknwn. h foi adicionado para ter a interface IUnknown.</span><span class="sxs-lookup"><span data-stu-id="2af55-174">unknwn.h was added for having the IUnknown interface.</span></span> 

<span data-ttu-id="2af55-175">Antes de escrever qualquer código, você precisa desabilitar avisos comuns em cabeçalhos do WinRT usando:</span><span class="sxs-lookup"><span data-stu-id="2af55-175">Before writing any code, you need to disable common warnings in WinRT headers by using:</span></span>

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="2af55-176">WinRT de um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="2af55-176">WinRT from a NuGet package</span></span>

<span data-ttu-id="2af55-177">É um pouco mais complicado se você precisar adicionar um pacote NuGet com suporte a WinRT.</span><span class="sxs-lookup"><span data-stu-id="2af55-177">It’s a little more complicated if you need to add a NuGet package with WinRT support.</span></span> <span data-ttu-id="2af55-178">Nesse caso, o Visual Studio pode executar praticamente todo o trabalho para você, mas o sistema de compilação não real não pode.</span><span class="sxs-lookup"><span data-stu-id="2af55-178">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="2af55-179">Felizmente, isso não é muito difícil.</span><span class="sxs-lookup"><span data-stu-id="2af55-179">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="2af55-180">Veja abaixo um exemplo de como você faria para baixar o pacote Microsoft. MixedReality. QR.</span><span class="sxs-lookup"><span data-stu-id="2af55-180">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="2af55-181">Você pode substituí-lo por outro, apenas certifique-se de que você não perca o arquivo winmd e copie a dll correta.</span><span class="sxs-lookup"><span data-stu-id="2af55-181">You can replace it with another, just make sure you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="2af55-182">SDK do Windows DLLs da seção anterior são manipuladas pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2af55-182">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="2af55-183">As DLLs do NuGet devem ser gerenciadas pelo código em seu módulo.</span><span class="sxs-lookup"><span data-stu-id="2af55-183">NuGet’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="2af55-184">É recomendável adicionar o código para baixá-los, copiar para a pasta de binários e carregar na memória do processo na inicialização do módulo.</span><span class="sxs-lookup"><span data-stu-id="2af55-184">We recommend adding code to download them, copying into binaries folder, and load into the process memory at the module startup.</span></span>

<span data-ttu-id="2af55-185">Na primeira etapa, você deve adicionar um packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) na pasta raiz do seu módulo.</span><span class="sxs-lookup"><span data-stu-id="2af55-185">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="2af55-186">Lá, você deve adicionar todos os pacotes que deseja baixar, incluindo todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="2af55-186">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="2af55-187">Aqui, adicionei o Microsoft. MixedReality. QR como uma carga primária e dois outros como dependências a ele.</span><span class="sxs-lookup"><span data-stu-id="2af55-187">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="2af55-188">O formato desse arquivo é o mesmo que no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="2af55-188">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="2af55-189">Agora você pode baixar o NuGet, os pacotes necessários ou consultar a [documentação](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)do NuGet.</span><span class="sxs-lookup"><span data-stu-id="2af55-189">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="2af55-190">Abra YourModule.Build.cs e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="2af55-190">Open YourModule.Build.cs and add the following code:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

            PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
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
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
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
        // fall to default WinSDK headers
                        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
            }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
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
```

<span data-ttu-id="2af55-191">Você precisará definir o método SafeCopy da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2af55-191">You'll need to define the SafeCopy method as follows:</span></span>

```cpp
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

<span data-ttu-id="2af55-192">As DLLs do NuGet precisam ser carregadas manualmente na memória do processo Win32; é recomendável adicionar o carregamento manual ao método de inicialização do seu módulo:</span><span class="sxs-lookup"><span data-stu-id="2af55-192">NuGet DLLs needs to load into your Win32 process memory manually; we recommend adding manual loading into the startup method of your module:</span></span>

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

<span data-ttu-id="2af55-193">Por fim, você pode incluir cabeçalhos do WinRT em seu código, conforme descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="2af55-193">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>