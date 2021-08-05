---
title: Como obter um HolographicSpace
description: Saiba como usar a API HolographicSpace para a renderização Holographic e a entrada espacial em seus aplicativos de realidade misturada.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, entrada espacial, renderização, cadeia de permuta, quadro holographic, loop de atualização, loop de jogo, quadro de referência, locatability, código de exemplo, passo a passos, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 986ccdc6e81d1ac7c7b401a427da548218a68eb0352a0057bf7d7aba3c1d6d6a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212164"
---
# <a name="getting-a-holographicspace"></a>Como obter um HolographicSpace

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herdadas.  Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)**.

A classe <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> é o seu portal no mundo Holographic. Ele controla a renderização de imersão, fornece dados de câmera e fornece acesso a APIs de raciocínio espacial. Você criará um para o <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> do seu aplicativo UWP ou o HWND do seu aplicativo Win32.

## <a name="set-up-the-holographic-space"></a>Configurar o espaço Holographic

criar o objeto holographic space é a primeira etapa para fazer seu aplicativo Windows Mixed Reality. os aplicativos Windows tradicionais são renderizados para uma cadeia de permuta de Direct3D criada para a janela principal de sua exibição de aplicativo. Essa cadeia de permuta é exibida para um Slate na interface do usuário do amholographic. Para fazer com que seu aplicativo exiba Holographic em vez de um Tablet 2D, crie um espaço Holographic para sua janela principal em vez de uma cadeia de permuta. Apresentar quadros Holographic criados por esse espaço de Holographic coloca seu aplicativo no modo de renderização de tela inteira.

para um **aplicativo UWP** [a partir do *modelo de aplicativo Holographic DirectX 11 (Universal Windows)*](creating-a-holographic-directx-project.md), procure esse código no método **setwindow** em AppView. cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Se você estiver criando um **aplicativo Win32** a [partir do exemplo do Win32 *BasicHologram*](creating-a-holographic-directx-project.md#creating-a-win32-project), examine o **aplicativo:: CreateWindowAndHolographicSpace** para obter um exemplo de HWND. Em seguida, você pode convertê-lo em um HWND de imersão criando um <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>associado:

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

Depois de obter um HolographicSpace para o seu CoreWindow UWP ou o HWND do Win32, o HolographicSpace pode lidar com as câmeras de Holographic, criar sistemas de coordenadas e fazer Holographic renderização. O espaço Holographic atual é usado em vários locais no modelo do DirectX:
* A classe **DeviceResources** precisa obter algumas informações do objeto HolographicSpace para criar o dispositivo Direct3D. Esta é a ID do adaptador DXGI associada à exibição Holographic. A classe <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> usa o dispositivo Direct3D 11 de seu aplicativo para criar e gerenciar recursos baseados em dispositivo, como os buffers de fundo para cada câmera Holographic. Se você estiver interessado em ver o que essa função faz nos bastidores, você a encontrará em DeviceResources. cpp.
* A função **DeviceResources:: InitializeUsingHolographicSpace** demonstra como obter o adaptador pesquisando a LUID – e como escolher um adaptador padrão quando nenhum adaptador preferencial for especificado.
* A classe principal do aplicativo usa o espaço Holographic de **AppView:: SetWindow** ou **App:: CreateWindowAndHolographicSpace** para atualizações e renderização.

>[!NOTE]
>Embora as seções a seguir mencionem nomes de funções do modelo, como **AppView:: SetWindow** , que pressupõem que você começou do modelo de aplicativo Holographic UWP, os trechos de código que você vê serão aplicados igualmente entre os aplicativos UWP e Win32.

Em seguida, vamos nos aprofundar no processo de configuração que **SetHolographicSpace** é responsável pela classe AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Assinar eventos de câmera, criar e remover recursos de câmera

O conteúdo do Holographic do aplicativo reside em seu espaço de Holographic e é exibido por meio de uma ou mais câmeras de Holographic, que representam perspectivas diferentes na cena. Agora que você tem o espaço Holographic, você pode receber dados para câmeras Holographic.

Seu aplicativo precisa responder a eventos do **CameraAdded** criando qualquer recurso que seja específico para essa câmera. Um exemplo desse recurso é a exibição de destino de renderização de buffer de fundo. Você pode ver esse código na função **DeviceResources:: SetHolographicSpace** , chamada por **AppView:: SetWindow** antes que o aplicativo crie qualquer quadro de Holographic:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

Seu aplicativo também precisa responder a eventos do **CameraRemoved** liberando recursos que foram criados para essa câmera.

De **DeviceResources:: SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Os manipuladores de eventos devem concluir algum trabalho para manter a renderização de Holographic fluindo sem problemas, e a renderização do aplicativo. Leia o código e os comentários para obter os detalhes: você pode procurar **OnCameraAdded** e **OnCameraRemoved** em sua classe principal para entender como o mapa de **m_cameraResources** é tratado pelo **DeviceResources**.

No momento, estamos concentrados no AppMain e na configuração que ele faz para permitir que seu aplicativo saiba sobre câmeras Holographic. Com isso em mente, é importante anotar os dois requisitos a seguir:

1. Para o manipulador de eventos **CameraAdded** , o aplicativo pode trabalhar de forma assíncrona para concluir a criação de recursos e o carregamento de ativos para a nova câmera Holographic. Os aplicativos que levam mais de um quadro para concluir esse trabalho devem solicitar um adiamento e concluir o adiamento após o carregamento de forma assíncrona. Uma [tarefa ppl](/cpp/parallel/concrt/parallel-patterns-library-ppl) pode ser usada para fazer trabalhos assíncronos. Seu aplicativo deve garantir que esteja pronto para renderizar para essa câmera imediatamente quando ele sair do manipulador de eventos ou quando concluir o adiamento. A saída do manipulador de eventos ou a conclusão do adiamento diz ao sistema que seu aplicativo agora está pronto para receber quadros Holographic com essa câmera incluída.

2. Quando o aplicativo recebe um evento **CameraRemoved** , ele deve liberar todas as referências para o buffer de fundo e sair da função imediatamente. Isso inclui exibições de destino de renderização e qualquer outro recurso que possa conter uma referência para o [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). O aplicativo também deve garantir que o buffer de fundo não seja anexado como um destino de renderização, conforme mostrado em **CameraResources:: ReleaseResourcesForBackBuffer**. Para ajudar a acelerar as coisas, seu aplicativo pode liberar o buffer de fundo e, em seguida, iniciar uma tarefa para concluir de forma assíncrona qualquer outro trabalho de subdivisão para a câmera. O modelo de aplicativo Holographic inclui uma tarefa PPL que você pode usar para essa finalidade.

>[!NOTE]
>Se você quiser determinar quando uma câmera adicionada ou removida aparece no quadro, use as propriedades **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Criar um quadro de referência para o conteúdo do Holographic

O conteúdo do aplicativo deve ser posicionado em um [sistema de coordenadas espaciais](coordinate-systems-in-directx.md) a ser processado no HolographicSpace. O sistema fornece dois quadros principais de referência, que podem ser usados para estabelecer um sistema de coordenadas para seus hologramas.

há dois tipos de quadros de referência em Windows Holographic: quadros de referência anexados ao dispositivo e quadros de referência que permanecem estacionários à medida que o dispositivo passa pelo ambiente do usuário. O modelo de aplicativo Holographic usa um quadro de referência estacionário por padrão; Essa é uma das maneiras mais simples de renderizar hologramas com bloqueios mundiais.

Quadros de referência estacionários são projetados para estabilizar posições perto do local atual do dispositivo. Isso significa que as coordenadas mais adiante do dispositivo podem descompassor um pouco em relação ao ambiente do usuário, pois o dispositivo aprende mais sobre o espaço em torno dele. Há duas maneiras de criar um quadro estacionário de referência: Adquira o sistema de coordenadas do [estágio espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)ou use o <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>padrão. se você estiver criando um aplicativo Windows Mixed Reality para headsets de imersão, o ponto de partida recomendado é o [estágio espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage). O estágio espacial também fornece informações sobre os recursos do headset de imersão gastados pelo jogador. Aqui, mostramos como usar o <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>padrão.

o localizador espacial representa o dispositivo Windows Mixed Reality e rastreia o movimento do dispositivo e fornece sistemas de coordenadas que podem ser compreendidos em relação à sua localização.

De **AppMain:: OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Crie o quadro de referência estacionário uma vez quando o aplicativo for iniciado. Isso é análogo à definição de um sistema de coordenadas mundiais, com a origem colocada na posição do dispositivo quando o aplicativo é iniciado. Este quadro de referência não se move com o dispositivo.

De **AppMain:: SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Todos os quadros de referência estão alinhados com a gravidade, o que significa que o eixo y aponta "para cima" em relação ao ambiente do usuário. como Windows usa sistemas de coordenadas "de mão direita", a direção do eixo – z coincide com a direção "encaminhar" que o dispositivo está enfrentando quando o quadro de referência é criado.

>[!NOTE]
>Quando seu aplicativo exige o posicionamento preciso de hologramas individuais, use um <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> para ancorar o holograma individual em uma posição no mundo real. Por exemplo, use uma âncora espacial quando o usuário indicar um ponto para ser um interesse especial. As posições de âncora não são descompassos, mas podem ser ajustadas. Por padrão, quando uma âncora é ajustada, ela facilita sua posição nos próximos vários quadros depois que a correção ocorre. Dependendo do seu aplicativo, quando isso ocorrer, talvez você queira lidar com o ajuste de uma maneira diferente (por exemplo, adiando-o até que o holograma esteja fora da exibição). A propriedade <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> e os eventos <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> permitem essas personalizações.

## <a name="respond-to-locatability-changed-events"></a>Responder a eventos alterados do locatability

A renderização de hologramas bloqueados no mundo requer que o dispositivo se localize no mundo inteiro. Isso nem sempre pode ser possível por causa de condições ambientais e, nesse caso, o usuário pode esperar uma indicação visual da interrupção do controle. Essa indicação visual deve ser renderizada usando quadros de referência anexados ao dispositivo, em vez de ser estacionário ao mundo.

Seu aplicativo pode solicitar a notificação se o rastreamento for interrompido por qualquer motivo. Registre-se no evento LocatabilityChanged para detectar quando a capacidade do dispositivo de se localizar no mundo é alterada. De **AppMain:: SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Em seguida, use esse evento para determinar quando os hologramas não podem ser renderizados como estáticos para o mundo.

## <a name="see-also"></a>Confira também
* [Como renderizar no DirectX](rendering-in-directx.md)
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md)