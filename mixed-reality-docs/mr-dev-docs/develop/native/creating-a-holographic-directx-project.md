---
title: Como criar um projeto holográfico do DirectX
description: Saiba como criar um novo aplicativo Holographic DirectX com base no modelo de aplicativo do Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, aplicativo Holographic, novo aplicativo, aplicativo UWP, aplicativo de modelo, hologramas, novo projeto, passo a passos, download, código de exemplo, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: ffc0da73cc93214bb5bef9142797557c6142b479
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581056"
---
# <a name="creating-a-holographic-directx-project"></a>Como criar um projeto holográfico do DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herdadas.  Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)**.

Um aplicativo Holographic que você cria para um HoloLens será um <a href="/windows/uwp/get-started/universal-application-platform-guide" target="_blank">aplicativo plataforma universal do Windows (UWP)</a>.  Se estiver direcionando headsets de área de trabalho mista do Windows, você pode criar um aplicativo UWP ou um aplicativo Win32.

O modelo de aplicativo do DirectX 11 Holographic UWP é muito parecido com o modelo de aplicativo UWP DirectX 11. O modelo inclui um loop de programa, uma classe **DeviceResources** para gerenciar o dispositivo e o contexto do Direct3D e uma classe de processador de conteúdo simplificada. Ele também tem um <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, assim como qualquer outro aplicativo UWP.

O aplicativo de realidade misturada, no entanto, tem alguns recursos adicionais que não estão presentes em um aplicativo de UWP do Direct3D típico. O modelo de aplicativo do Windows Mixed Reality pode:
* Manipule recursos do dispositivo Direct3D associados a câmeras holographics.
* Recupere buffers de fundo da câmera do sistema. No caso do Direct3D12, crie recursos de buffer de back Holographic e gerencie tempos de vida de recursos.
* Manipule a entrada do [olhar](../../design/gaze-and-commit.md) e reconheça um [gesto](../../design/gaze-and-commit.md#composite-gestures).
* Vá para o modo de renderização estéreo de tela inteira.

## <a name="how-do-i-get-started"></a>Como começar?

Primeiro, [Instale as ferramentas](../install-the-tools.md), seguindo as instruções sobre como baixar o Visual Studio 2019 e os modelos de aplicativos do Windows Mixed Reality. Os modelos de aplicativo de realidade misturada estão disponíveis no Visual Studio Marketplace como um [download da Web](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)ou instalando-os como uma extensão por meio da interface do usuário do Visual Studio.

Agora você está pronto para criar seu aplicativo de realidade mista do Windows DirectX 11! Observe que, para remover o conteúdo de exemplo, comente a diretiva de pré-processador de **DRAW_SAMPLE_CONTENT** em *PCH. h*.

## <a name="creating-a-uwp-project"></a>Criar um projeto UWP

Após a instalação das ferramentas,] (.. /install-the-tools.md) você pode criar um projeto Holographic DirectX UWP.

Para criar um novo projeto no Visual Studio 2019:
1. Inicie o **Visual Studio**.
2. Na seção **introdução** à direita, selecione **criar um novo projeto**.
3. Nos menus suspensos na caixa de diálogo **criar um novo projeto** , selecione **C++**, **realidade mista do Windows** e **UWP**.
4. Selecione **aplicativo Holographic DirectX 11 (universal do Windows) (C++/WinRT)**.
   ![Captura de tela do modelo de projeto de aplicativo Holographic DirectX 11 C++/WinRT UWP no Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Modelo de projeto de aplicativo Holographic DirectX 11 C++/WinRT UWP no Visual Studio 2019*
   >[!IMPORTANT]
   >Certifique-se de que o nome do modelo de projeto inclui "(C++/WinRT)".  Caso contrário, você tem uma versão mais antiga dos modelos de projeto do Holographic instalados.  Para obter os modelos de projeto mais recentes, [Instale-os](../install-the-tools.md) como uma extensão para o Visual Studio 2019.
5. Selecione **Avançar**.
5. Preencha as caixas de texto **nome do projeto** e **local** e selecione ou toque em **criar**. O projeto de aplicativo Holographic é criado.
6. Para o desenvolvimento direcionado apenas para o HoloLens 2, verifique se a **versão de destino** e a **versão mínima** estão definidas como **Windows 10, versão 1903**.  Se você também estiver visando headsets de HoloLens (1ª gen) ou área de trabalho mista do Windows do desktop, poderá definir a **versão mínima** para o **Windows 10, versão 1809**. Isso exigirá algumas <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">verificações adaptáveis de versão</a> em seu código ao usar os novos recursos do HoloLens 2.
   ![Captura de tela da configuração do Windows 10, versão 1903 como o destino e as versões mínimas](images/new-uwp-project.png)<br>
   *Configurando o **Windows 10, versão 1903** como o destino e as versões mínimas*
   >[!IMPORTANT]
   >Se você não vir o **Windows 10, versão 1903** como uma opção, você não tem o SDK do Windows 10 mais recente instalado.  Para que essa opção seja exibida, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">Instale a versão 10.0.18362.0 ou posterior do SDK do Windows 10</a>.

Para criar um novo projeto no Visual Studio 2017:
1. Inicie o **Visual Studio**.
2. No menu **arquivo** , aponte para **novo** e selecione **projeto** no menu de contexto. A caixa de diálogo **Novo projeto** é aberta.
3. Expanda **instalado** à esquerda e expanda o nó de idioma **Visual C++** .
4. Navegue até o nó **Windows Universal > Holographic** e selecione **aplicativo Holographic DirectX 11 (universal do Windows) (C++/WinRT)**.
   ![Captura de tela do modelo de projeto de aplicativo Holographic DirectX 11 C++/WinRT UWP no Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *Modelo de projeto de aplicativo Holographic DirectX 11 C++/WinRT UWP no Visual Studio 2017*
   >[!IMPORTANT]
   >Certifique-se de que o nome do modelo de projeto inclui "(C++/WinRT)".  Caso contrário, você tem uma versão mais antiga dos modelos de projeto do Holographic instalados.  Para obter os modelos de projeto mais recentes, [Instale-os](../install-the-tools.md) como uma extensão para o Visual Studio 2017.
5. Preencha as caixas de texto **nome** e **local** e selecione ou toque em **OK**. O projeto de aplicativo Holographic é criado.
6. Para o desenvolvimento direcionado apenas para o HoloLens 2, verifique se a **versão de destino** e a **versão mínima** estão definidas como **Windows 10, versão 1903**.  Se você também estiver visando headsets de HoloLens (1ª gen) ou área de trabalho mista do Windows do desktop, poderá definir a **versão mínima** para o **Windows 10, versão 1809**. Isso exigirá algumas <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">verificações adaptáveis de versão</a> em seu código ao usar os novos recursos do HoloLens 2.
   ![Captura de tela da configuração do Windows 10, versão 1903 como o destino e as versões mínimas](images/new-uwp-project.png)<br>
   *Configurando o **Windows 10, versão 1903** como o destino e as versões mínimas*
   >[!IMPORTANT]
   >Se você não vir o **Windows 10, versão 1903** como uma opção, você não tem o SDK do Windows 10 mais recente instalado.  Para que essa opção seja exibida, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">Instale a versão 10.0.18362.0 ou posterior do SDK do Windows 10</a>.

O modelo gera um projeto usando <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c++/WinRT</a>, uma projeção de linguagem c++ 17 das APIs de Windows Runtime que dá suporte a qualquer compilador c++ 17 compatível com padrões.  O projeto mostra como criar um cubo protegido por mundo que é colocado 2 metros do usuário. O usuário pode [tocar em ar](../../design/gaze-and-commit.md#composite-gestures) ou pressionar um botão no controlador para colocar o cubo em uma posição diferente especificada pelo [olhar](../../design/gaze-and-commit.md)do usuário. Você pode modificar este projeto para criar qualquer aplicativo de realidade misturada.

Você também pode criar um novo projeto usando o modelo de projeto Holographic do **Visual C#** , que se baseia em SharpDX.  Se o seu projeto do Holographic C# não foi iniciado no modelo de aplicativo Holographic do Windows, você precisará copiar o arquivo MS. fxcompile. targets de um projeto de modelo C# do Windows Mixed Reality e importá-lo em seu arquivo. csproj para compilar os arquivos HLSL que você adicionar ao seu projeto. Um modelo do Direct3D 12 também é fornecido na extensão de modelos de aplicativos do Windows Mixed Reality para o Visual Studio.

Examine [usando o Visual Studio para implantar e depurar](../platform-capabilities-and-apis/using-visual-studio.md) para obter informações sobre como criar e implantar o exemplo em seu HOLOLENS, PC com dispositivo de imersão anexado ou um emulador.

O restante das instruções a seguir pressupõe que você esteja usando C++ para compilar seu aplicativo.

### <a name="uwp-app-entry-point"></a>Ponto de entrada de aplicativo UWP

Seu aplicativo Holographic UWP é iniciado na função **wWinMain** em AppView. cpp. A função **wWinMain** cria o <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> do aplicativo e inicia o <a href="/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> com ele.

De **AppView. cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

A partir desse ponto, a classe AppView lida com a interação com eventos de entrada do Windows Basic, eventos e mensagens do CoreWindow e assim por diante. Ele também criará o HolographicSpace usado pelo seu aplicativo.

## <a name="creating-a-win32-project"></a>Criando um projeto Win32

A maneira mais fácil de começar a criar um projeto Holographic do Win32 é adaptar o <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">exemplo do Win32 *BasicHologram*</a>.

Este exemplo de Win32 usa <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c++/WinRT</a>, uma projeção de linguagem c++ 17 das APIs de Windows Runtime que dá suporte a qualquer compilador c++ 17 compatível com padrões.  O projeto mostra como criar um cubo protegido por mundo que é colocado 2 metros do usuário. O usuário pode pressionar um botão no controlador para colocar o cubo em uma posição diferente especificada pelo [olhar](../../design/gaze-and-commit.md)do usuário. Você pode modificar este projeto para criar qualquer aplicativo de realidade misturada.

### <a name="win32-app-entry-point"></a>Ponto de entrada do aplicativo Win32

Seu aplicativo Win32 Holographic é iniciado na função **wWinMain** em AppMain. cpp. A função **wWinMain** cria o HWND do aplicativo e inicia seu loop de mensagem.

De **AppMain. cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

Desse ponto em diante, a classe AppMain lida com a interação com as mensagens básicas de janela e assim por diante. Ele também criará o HolographicSpace usado pelo seu aplicativo.

## <a name="render-holographic-content"></a>Renderizar conteúdo Holographic

A pasta de **conteúdo** do projeto contém classes para renderizar hologramas no [espaço Holographic](getting-a-holographicspace.md). O holograma padrão no modelo é um cubo de rotação que é colocado 2 metros de distância do usuário. O desenho desse cubo é implementado em **SpinningCubeRenderer. cpp**, que tem estes métodos principais:

|  Método  |  Explicação | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carrega sombreadores e cria a malha do cubo. | 
|  `PositionHologram` |  Coloca o holograma no local especificado pelo <a href="/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>fornecido. | 
|  `Update` |  Gira o cubo e define a matriz do modelo. | 
|  `Render` |  Renderiza um quadro usando o vértice e os sombreadores de pixel. | 

A subpasta **shaders** contém quatro implementações de sombreador padrão:

|  Sombreador  |  Explicação | 
|----------|----------|
|  `GeometryShader.hlsl` |  Uma passagem que deixa a geometria não modificada. | 
|  `PixelShader.hlsl` |  Passa pelos dados de cor. Os dados de cor são interpolados e atribuídos a um pixel na etapa de rasterização. | 
|  `VertexShader.hlsl` |  Sombreador simples para fazer processamento de vértice na GPU. | 
|  `VPRTVertexShader.hlsl` |  Sombreador simples para fazer o processamento de vértice na GPU, que é otimizado para a renderização de estéreo de realidade mista do Windows. | 

`VertexShaderShared.hlsl` contém o código comum compartilhado entre `VertexShader.hlsl` e `VPRTVertexShader.hlsl` .

Observação: o modelo de aplicativo do Direct3D 12 também inclui `ViewInstancingVertexShader.hlsl` . Essa variante usa recursos opcionais do D3D12 para renderizar imagens estéreo com mais eficiência.

Os sombreadores são compilados quando o projeto é compilado e carregados no método **SpinningCubeRenderer:: CreateDeviceDependentResources** .

## <a name="interact-with-your-holograms"></a>Interaja com os hologramas

A entrada do usuário é processada na classe **SpatialInputHandler** , que obtém uma instância de <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> e assina o evento <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> . Isso permite detectar o gesto de toque do ar e outros eventos de entrada espaciais.

## <a name="update-holographic-content"></a>Atualizar conteúdo do Holographic

O aplicativo de realidade misturada é atualizado em um loop de jogo, que por padrão é implementado no método **Update** no `AppMain.cpp` . O método **Update** atualiza objetos de cena, como o cubo girando, e retorna um objeto <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> que é usado para obter matrizes de exibição e projeção atualizadas e apresentar a cadeia de troca.

O método **render** em `AppMain.cpp` usa o <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> e renderiza o quadro atual para cada câmera Holographic, de acordo com o aplicativo atual e o estado de posicionamento espacial.

## <a name="notes"></a>Observações

O modelo de aplicativo de realidade mista do Windows agora dá suporte à compilação com o sinalizador de mitigação Spectre habilitado (/Qspectre). Certifique-se de instalar a versão Spectre das bibliotecas de tempo de execução do Microsoft Visual C++ (MSVC) antes de compilar uma configuração com a mitigação Spectre habilitada. Para instalar as bibliotecas de C++ Spectre, inicie o Instalador do Visual Studio e selecione **Modificar**. Navegue até **componentes individuais** e pesquise por "Spectre". Selecione as caixas correspondentes às plataformas de destino e à versão MSVC para a qual você precisa compilar o código Spectre mitigado e clique em **Modificar** para iniciar a instalação.

## <a name="see-also"></a>Confira também
* [Como obter um HolographicSpace](getting-a-holographicspace.md)
* <a href="/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Como renderizar no DirectX](rendering-in-directx.md)
* [Como usar o Visual Studio para implantar e depurar](../platform-capabilities-and-apis/using-visual-studio.md)
* [Usando o emulador do HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Como usar o XAML com aplicativos DirectX holográficos](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)