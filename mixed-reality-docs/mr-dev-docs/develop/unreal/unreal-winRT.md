---
title: WinRT no Unreal
description: Visão geral do plug-in de áudio espacial do Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Inreal, não real Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicação remota, realidade mista, desenvolvimento, introdução, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, WinRT, DLL
ms.openlocfilehash: fd50e5ecd3186fc8852936affbfedc3d5fd4de75
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679805"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="949f7-104">WinRT no Unreal</span><span class="sxs-lookup"><span data-stu-id="949f7-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="949f7-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="949f7-105">Overview</span></span>

<span data-ttu-id="949f7-106">Ao longo do desenvolvimento do seu HoloLens, talvez seja necessário escrever um recurso usando o WinRT.</span><span class="sxs-lookup"><span data-stu-id="949f7-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="949f7-107">Por exemplo, abrir uma caixa de diálogo de arquivo em um aplicativo HoloLens precisaria do FileSavePicker no arquivo de cabeçalho winrt/Windows. Storage....</span><span class="sxs-lookup"><span data-stu-id="949f7-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="949f7-108">Como inreal não compila nativamente o código WinRT, é seu trabalho criar um binário separado e que pode ser consumido pelo sistema de compilação não real.</span><span class="sxs-lookup"><span data-stu-id="949f7-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="949f7-109">Este tutorial guiará você pelo cenário desse tipo.</span><span class="sxs-lookup"><span data-stu-id="949f7-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="949f7-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="949f7-110">Objectives</span></span>
- <span data-ttu-id="949f7-111">Criar uma DLL universal do Windows que abre um FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="949f7-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="949f7-112">Vincular essa DLL a um projeto de jogo não real</span><span class="sxs-lookup"><span data-stu-id="949f7-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="949f7-113">Salvar um arquivo no HoloLens de um projeto não real usando a nova DLL</span><span class="sxs-lookup"><span data-stu-id="949f7-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="949f7-114">Introdução</span><span class="sxs-lookup"><span data-stu-id="949f7-114">Getting started</span></span>
1. <span data-ttu-id="949f7-115">Verifique se você tem todas as [ferramentas necessárias](tutorials/unreal-uxt-ch1.md) instaladas</span><span class="sxs-lookup"><span data-stu-id="949f7-115">Check that you have all [required tools](tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="949f7-116">[Criar um novo projeto inreal](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) e nomeá-lo **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="949f7-116">[Create a new Unreal project](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="949f7-117">Habilitar os [plug-ins necessários](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) para o desenvolvimento do HoloLens</span><span class="sxs-lookup"><span data-stu-id="949f7-117">Enable the [required plugins](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="949f7-118">[Configuração para implantação](tutorials/unreal-uxt-ch6.md) em um dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="949f7-118">[Setup for deployment](tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="949f7-119">Criando uma DLL do WinRT</span><span class="sxs-lookup"><span data-stu-id="949f7-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="949f7-120">Abra um novo projeto do Visual Studio e crie um projeto **dll (universal do Windows)** no mesmo diretório para o arquivo **uproject** do jogo inreal.</span><span class="sxs-lookup"><span data-stu-id="949f7-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![Criando uma DLL](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="949f7-122">Nomeie o projeto **HoloLensWinrtDLL** e defina o local como um subdiretório **ThirdParty** para o arquivo uproject do jogo inreal.</span><span class="sxs-lookup"><span data-stu-id="949f7-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="949f7-123">Selecione **posicionar solução e projeto no mesmo diretório** para simplificar a procura de caminhos mais tarde.</span><span class="sxs-lookup"><span data-stu-id="949f7-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configurando a DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="949f7-125">Depois que o novo projeto é compilado, você deseja prestar atenção especial aos arquivos cpp e de cabeçalho em branco, chamados **HoloLensWinrtDLL. cpp** e **HoloLensWinrtDLL. h** , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="949f7-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="949f7-126">O cabeçalho é o arquivo de inclusão que usa a DLL em tempo real, enquanto a cpp mantém o corpo de todas as funções que você exporta e inclui qualquer código do WinRT que não seja possível compilar de outra forma.</span><span class="sxs-lookup"><span data-stu-id="949f7-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="949f7-127">Antes de adicionar qualquer código, você precisa atualizar as propriedades do projeto para garantir que o código do WinRT que você precisa pode compilar:</span><span class="sxs-lookup"><span data-stu-id="949f7-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="949f7-128">Clique com o botão direito do mouse no projeto HoloLensWinrtDLL e selecione **Propriedades**</span><span class="sxs-lookup"><span data-stu-id="949f7-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="949f7-129">Alterar a lista suspensa de **configuração** para **todas as configurações** e a lista suspensa de **plataforma** para **todas as plataformas**</span><span class="sxs-lookup"><span data-stu-id="949f7-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="949f7-130">Em **Propriedades de configuração> C/C++> todas as opções**:</span><span class="sxs-lookup"><span data-stu-id="949f7-130">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="949f7-131">Adicionar **Await** a **Opções adicionais** para garantir que possamos aguardar em tarefas assíncronas</span><span class="sxs-lookup"><span data-stu-id="949f7-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="949f7-132">Alterar o **padrão de linguagem C++** para **ISO C++ 17 Standard (/std: C++ 17)** para incluir qualquer código do WinRT</span><span class="sxs-lookup"><span data-stu-id="949f7-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Atualizando Propriedades do projeto](images/unreal-winrt-img-03.png)

<span data-ttu-id="949f7-134">Seu projeto está pronto para atualizar a origem da DLL com o código do WinRT que abre uma caixa de diálogo de arquivo e salva um arquivo no disco do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="949f7-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="949f7-135">Adicionando o código DLL</span><span class="sxs-lookup"><span data-stu-id="949f7-135">Adding the DLL code</span></span>
1. <span data-ttu-id="949f7-136">Abra **HoloLensWinrtDLL. h** e adicione uma função exportada de dll para consumir inrealmente:</span><span class="sxs-lookup"><span data-stu-id="949f7-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="949f7-137">Abra **HoloLensWinrtDLL. cpp** e adicione todos os cabeçalhos que a classe usará:</span><span class="sxs-lookup"><span data-stu-id="949f7-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="949f7-138">Todo o código do WinRT é armazenado em **HoloLensWinrtDLL. cpp** , de modo que não tente incluir nenhum código do winrt ao referenciar o cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="949f7-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="949f7-139">Ainda em **HoloLensWinrtDLL. cpp**, adicione um corpo de função para OpenFileDialogue () e todo o código com suporte:</span><span class="sxs-lookup"><span data-stu-id="949f7-139">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="949f7-140">Adicione uma classe SaveGameManager a **HoloLensWinrtDLL. cpp** para manipular a caixa de diálogo do arquivo e salvar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="949f7-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="949f7-141">Compile a solução para a **versão > ARM64** para criar a dll para o diretório filho ARM64/Release/HoloLensWinrtDLL da solução de dll.</span><span class="sxs-lookup"><span data-stu-id="949f7-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="949f7-142">Adicionar o binário do WinRT a um não real</span><span class="sxs-lookup"><span data-stu-id="949f7-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="949f7-143">Vincular e usar uma DLL em um Unreal requer um projeto C++.</span><span class="sxs-lookup"><span data-stu-id="949f7-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="949f7-144">Se você estiver usando um projeto Blueprint, ele poderá ser facilmente convertido em um projeto C++ adicionando uma classe C++:</span><span class="sxs-lookup"><span data-stu-id="949f7-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="949f7-145">No editor inreal, abra **arquivo > nova classe C++...**</span><span class="sxs-lookup"><span data-stu-id="949f7-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="949f7-146">e crie um novo **ator** chamado **WinrtActor** para executar o código na DLL:</span><span class="sxs-lookup"><span data-stu-id="949f7-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Criando um novo ator](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="949f7-148">Agora, uma solução foi criada no mesmo diretório que o arquivo uproject, juntamente com um novo script de compilação chamado source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="949f7-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="949f7-149">Abra a solução, procure a pasta **Games/ConsumeWinRT/origem/ConsumeWinRT** e abra **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="949f7-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Abrindo o arquivo ConsumeWinRT.build.cs](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="949f7-151">Vinculando a DLL</span><span class="sxs-lookup"><span data-stu-id="949f7-151">Linking the DLL</span></span>
1. <span data-ttu-id="949f7-152">Em **ConsumeWinRT.Build.cs**, adicione uma propriedade para localizar o caminho de inclusão para a dll (o diretório que contém HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="949f7-152">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="949f7-153">A DLL está em um diretório filho para o caminho de inclusão, portanto, essa propriedade será usada como a dir raiz binária:</span><span class="sxs-lookup"><span data-stu-id="949f7-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="949f7-154">No construtor de classe, adicione o seguinte código para atualizar o caminho de inclusão, vincular a nova lib e atrasar o carregamento e copiar a DLL para o local Appx empacotado:</span><span class="sxs-lookup"><span data-stu-id="949f7-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="949f7-155">Abra **WinrtActor. h** e adicione uma definição de função, que será chamada por um plano gráfico:</span><span class="sxs-lookup"><span data-stu-id="949f7-155">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="949f7-156">Abra **WinrtActor. cpp** e atualize BeginPlay para carregar a dll:</span><span class="sxs-lookup"><span data-stu-id="949f7-156">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="949f7-157">A DLL deve ser carregada antes de chamar qualquer uma de suas funções.</span><span class="sxs-lookup"><span data-stu-id="949f7-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="949f7-158">Criando o jogo</span><span class="sxs-lookup"><span data-stu-id="949f7-158">Building the game</span></span>
1. <span data-ttu-id="949f7-159">Crie a solução de jogos para iniciar o editor inreal aberto no projeto de jogo:</span><span class="sxs-lookup"><span data-stu-id="949f7-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="949f7-160">Na guia **local atores** , pesquise o novo **WinrtActor** e arraste-o para a cena</span><span class="sxs-lookup"><span data-stu-id="949f7-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="949f7-161">Abra o Blueprint de nível para executar a função que tem o plano de execução no **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="949f7-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Colocando o WinrtActor na cena](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="949f7-163">Na estrutura **mundial**, encontre o **WindrtActor** que foi previamente colocado na cena e arraste-o para o plano Blueprint:</span><span class="sxs-lookup"><span data-stu-id="949f7-163">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Arrastando o WinrtActor para o plano gráfico de nível](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="949f7-165">No nível Blueprint, arraste o nó saída de WinrtActor, procure a **caixa de diálogo abrir arquivo** e, em seguida, encaminhe o nó de qualquer entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="949f7-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="949f7-166">Nesse caso, a caixa de diálogo abrir arquivo está sendo chamada de um evento de fala:</span><span class="sxs-lookup"><span data-stu-id="949f7-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configurando nós no nível Blueprint](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="949f7-168">[Empacote este jogo para o HoloLens](tutorials/unreal-uxt-ch6.md), implante-o e execute-o.</span><span class="sxs-lookup"><span data-stu-id="949f7-168">[Package this game for HoloLens](tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="949f7-169">Quando as chamadas inreais OpenFileDialogue, uma caixa de diálogo de arquivo é aberta no HoloLens solicitando um nome de arquivo. txt.</span><span class="sxs-lookup"><span data-stu-id="949f7-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="949f7-170">Depois que o arquivo for salvo, vá para a guia **Explorador de arquivos** no portal do dispositivo para ver o conteúdo "Olá WinRT".</span><span class="sxs-lookup"><span data-stu-id="949f7-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="949f7-171">Resumo</span><span class="sxs-lookup"><span data-stu-id="949f7-171">Summary</span></span> 

<span data-ttu-id="949f7-172">Incentivamos você a usar o código neste tutorial como um ponto de partida para consumir o código do WinRT em um estado inreal.</span><span class="sxs-lookup"><span data-stu-id="949f7-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="949f7-173">Ele permite que os usuários salvem arquivos no disco do HoloLens usando a mesma caixa de diálogo de arquivo que o Windows.</span><span class="sxs-lookup"><span data-stu-id="949f7-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="949f7-174">Siga o mesmo processo para exportar funções adicionais do cabeçalho HoloLensWinrtDLL e usadas em um não real.</span><span class="sxs-lookup"><span data-stu-id="949f7-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="949f7-175">Observe o código de DLL que aguarda em qualquer código assíncrono do WinRT em um thread MTA de segundo plano, que evita o deadlock do thread de jogo inreal.</span><span class="sxs-lookup"><span data-stu-id="949f7-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="next-development-checkpoint"></a><span data-ttu-id="949f7-176">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="949f7-176">Next Development Checkpoint</span></span>

<span data-ttu-id="949f7-177">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="949f7-177">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="949f7-178">A partir daqui, você pode prosseguir para qualquer [tópico](unreal-development-overview.md#3-platform-capabilities-and-apis) ou ir diretamente para a implantação de seu aplicativo em um dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="949f7-178">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="949f7-179">Como fazer a implantação no dispositivo</span><span class="sxs-lookup"><span data-stu-id="949f7-179">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="949f7-180">Veja também</span><span class="sxs-lookup"><span data-stu-id="949f7-180">See also</span></span>
* [<span data-ttu-id="949f7-181">APIs do C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="949f7-181">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="949f7-182">Classe FileSavePicker</span><span class="sxs-lookup"><span data-stu-id="949f7-182">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="949f7-183">Bibliotecas de terceiros inreais</span><span class="sxs-lookup"><span data-stu-id="949f7-183">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
