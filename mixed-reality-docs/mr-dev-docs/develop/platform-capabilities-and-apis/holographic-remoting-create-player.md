---
title: Como criar um player personalizado de comunicação remota holográfica
description: crie um aplicativo de comunicação remota Hologaphic personalizado para exibir o conteúdo renderizado em um computador remoto para seu HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicação remota, comunicação remota de Holographic, NuGet, manifesto de aplicativo, contexto do player, aplicativo remoto, headset de realidade misturada, headset de realidade misturada do windows, headset da realidade virtual
ms.openlocfilehash: b395f94f6c98b20f7c0c188f11a718e6da9394de5df3404e7c703558daf526f2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190159"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Como escrever um aplicativo personalizado do Holographic Remoting Player

>[!IMPORTANT]
>este documento descreve a criação de um aplicativo de player personalizado para o HoloLens 2. os players personalizados escritos para o HoloLens 2 não são compatíveis com os aplicativos remotos gravados para HoloLens 1. isso implica que ambos os aplicativos devem usar NuGet pacote versão **2. x. x**.

ao criar um aplicativo de player remoto do Holographic personalizado, você pode criar um aplicativo personalizado capaz de exibir [exibições de imersão](../../design/app-views.md) em um computador remoto no seu HoloLens 2. Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

um player de comunicação remota Holographic permite que seu aplicativo exiba o conteúdo Holographic [renderizado](rendering.md) em um computador desktop ou em um dispositivo UWP como o Xbox One com acesso a mais recursos do sistema. Um aplicativo de player de comunicação remota Holographic transmite dados de entrada para um aplicativo remoto de comunicação remota Holographic e recebe um modo de exibição de imersão como fluxo de áudio e vídeo. A conexão é feita usando Wi-Fi padrão. para criar um aplicativo de player, use um pacote NuGet para adicionar a comunicação remota do Holographic ao seu aplicativo UWP. Em seguida, escreva o código para manipular a conexão e exibir uma exibição de imersão. 

## <a name="prerequisites"></a>Pré-requisitos

um bom ponto de partida é um aplicativo UWP de trabalho baseado em DirectX que já tem como alvo a API de Windows Mixed Reality. Para obter detalhes, consulte [visão geral do desenvolvimento do DirectX](../native/directx-development-overview.md). Se você não tiver um aplicativo existente e quiser começar do zero, o [modelo de projeto do C++ Holographic](../native/creating-a-holographic-directx-project.md) será um bom ponto de partida.

>[!IMPORTANT]
>Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](/windows/win32/com/multithreaded-apartments)multi-threaded. O uso de um [apartamento de thread único](/windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução. Ao usar C++/WinRT [WinRT:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.

## <a name="get-the-holographic-remoting-nuget-package"></a>obter o pacote de NuGet de comunicação remota do Holographic

as etapas a seguir são necessárias para adicionar o pacote de NuGet a um projeto no Visual Studio.
1. Abra o projeto no Visual Studio.
2. clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes de NuGet...**
3. No painel que aparece, selecione **procurar** e, em seguida, pesquise "comunicação remota do Holographic".
4. Selecione **Microsoft. Holographic. Remoting**, certifique-se de selecionar a versão **2. x. x** mais recente e selecione **instalar**.
5. Se a caixa de diálogo **Visualizar** for exibida, selecione **OK**.
6. Selecione **aceito quando o** diálogo do contrato de licença for exibido.

>[!IMPORTANT]
><a name="idl"></a>o ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote de NuGet contém documentação detalhada para a API exposta pela comunicação remota do Holographic.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modificar o Package. appxmanifest do aplicativo

para tornar o aplicativo ciente do Microsoft.Holographic.AppRemoting.dll adicionado pelo pacote NuGet, as etapas a seguir precisam ser executadas no projeto:

1. No Gerenciador de Soluções clique com o botão direito do mouse no arquivo **Package. appxmanifest** e selecione **abrir com...**
2. Selecione **Editor de XML (texto)** e selecione **OK**
3. Adicione as seguintes linhas ao arquivo e salve
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Criar o contexto do Player

Como primeira etapa, o aplicativo deve criar um contexto de Player.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>a comunicação remota do Holographic funciona substituindo o tempo de execução de Windows Mixed Reality que faz parte do Windows com um tempo de execução específico de comunicação remota. Isso é feito durante a criação do contexto do Player. por esse motivo, qualquer chamada em qualquer API de Windows Mixed Reality antes de criar o contexto do player pode resultar em um comportamento inesperado. A abordagem recomendada é criar o contexto do Player o mais cedo possível antes da interação com qualquer API de realidade misturada. nunca misture objetos criados ou recuperados por meio de qualquer API de Windows Mixed Reality antes da chamada para ```PlayerContext::Create``` com objetos criados ou recuperados posteriormente.

Em seguida, o HolographicSpace pode ser criado chamando [HolographicSpace. CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Conexão ao aplicativo remoto

Depois que o aplicativo de Player estiver pronto para o processamento de conteúdo, pode ser estabelecida uma conexão com o aplicativo remoto.

A conexão pode ser estabelecida de uma das seguintes maneiras:
1) o aplicativo de player em execução no HoloLens 2 se conecta ao aplicativo remoto.
2) o aplicativo remoto se conecta ao aplicativo de player em execução no HoloLens 2.

Para se conectar do aplicativo Player ao aplicativo remoto, chame o ```Connect``` método no contexto do Player especificando o nome do host e a porta. A porta padrão é **8265**.

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Assim como acontece com qualquer API do C++/WinRT, você ```Connect``` pode lançar um WinRT:: hresult_error que precisa ser manipulado.

A escuta de conexões de entrada no aplicativo de player pode ser feita chamando o ```Listen``` método. A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada. A porta de handshake é usada para o handshake inicial. Os dados são enviados pela porta de transporte. Por padrão, o número da porta **8265** e **8266** são usados.

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Manipulando eventos relacionados à conexão

O ```PlayerContext``` expõe três eventos para monitorar o estado da conexão
1) Onconnected: disparado quando uma conexão com o aplicativo remoto foi estabelecida com êxito.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnect: disparado se uma conexão estabelecida for encerrada ou não foi possível estabelecer uma conexão.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>Os ```ConnectionFailureReason``` valores possíveis são documentados no ```Microsoft.Holographic.AppRemoting.idl``` [arquivo](#idl).

3) Desescutando: quando a escuta de conexões de entrada é iniciada.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Além disso, o estado da conexão pode ser consultado usando a ```ConnectionState``` propriedade no contexto do Player.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Exibir o quadro processado remotamente

Para exibir o conteúdo renderizado remotamente, chame ```PlayerContext::BlitRemoteFrame``` ao renderizar um [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe). 

```BlitRemoteFrame``` requer que o buffer de fundo para o HolographicFrame atual seja associado como destino de renderização. O buffer de fundo pode ser recebido do [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) por meio da propriedade [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .

Quando chamado, ```BlitRemoteFrame``` o copia o último quadro recebido do aplicativo remoto para o BackBuffer do HolographicFrame. Além disso, o conjunto de pontos de foco é definido, se o aplicativo remoto tiver especificado um ponto de foco durante a renderização do quadro remoto.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` Substitui potencialmente o ponto de foco do quadro atual. 
>- Para especificar um ponto de foco de fallback, chame [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes de ```PlayerContext::BlitRemoteFrame``` . 
>- Para substituir o ponto de foco remoto, chame [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  após ```PlayerContext::BlitRemoteFrame``` .

Em caso de sucesso, ```BlitRemoteFrame``` retorna ```BlitResult::Success_Color``` . Caso contrário, ele retornará o motivo da falha:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: Falhou porque nenhum quadro remoto está disponível.
- ```BlitResult::Failed_NoCamera```: Falhou porque nenhuma câmera presente.
- ```BlitResult::Failed_RemoteFrameTooOld```: Falhou porque a estrutura remota é muito antiga (consulte a propriedade PlayerContext:: BlitRemoteFrameTimeout).

>[!IMPORTANT]
> A partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0) , é possível que um jogador personalizado use a Reprojeção de profundidade por meio da comunicação remota do Holographic.

```BlitResult``` também pode retornar ```BlitResult::Success_Color_Depth``` sob as seguintes condições:

- O aplicativo remoto confirmou um buffer de profundidade por meio de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).
- O aplicativo de player personalizado um buffer de profundidade válido antes de chamar ```BlitRemoteFrame``` .

Se essas condições forem atendidas ```BlitRemoteFrame``` , blit a profundidade remota no buffer de profundidade local atualmente associado. Em seguida, você pode renderizar conteúdo local adicional, que terá a interseção de profundidade com o conteúdo renderizado remotamente. Além disso, você pode confirmar o buffer de profundidade local por meio de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) em seu player personalizado para ter uma Reprojeção de profundidade para conteúdo renderizado remoto e local. Consulte [Reprojeção de profundidade](hologram-stability.md#reprojection) para obter detalhes.

### <a name="projection-transform-mode"></a>Modo de transformação de projeção

Um problema, que se superfícies ao usar a Reprojeção de profundidade por meio da comunicação remota do Holographic é que o conteúdo remoto pode ser renderizado com uma transformação de projeção diferente do conteúdo local processado diretamente pelo seu aplicativo de player personalizado. Um caso de uso comum é especificar valores diferentes para o plano próximo e longe (via [HolographicCamera:: SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) e [HolographicCamera:: SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) no lado do Player e no lado remoto. Nesse caso, não fica claro se a transformação de projeção no lado do jogador deve refletir as distâncias do plano Near/distante remotas ou os locais.

A partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0) , você pode controlar o modo de transformação projeção via ```PlayerContext::ProjectionTransformConfig``` . Os valores com suporte são:

- ```Local``` - [HolographicCameraPose::P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) retorna uma transformação de projeção, que reflete as distâncias do plano próximo/longe definidas pelo seu aplicativo de player personalizado no HolographicCamera.
- ```Remote``` -A transformação de projeção reflete as distâncias do plano próximo/longe especificadas pelo aplicativo remoto.
- ```Merged``` -As distâncias do plano próximo/longe do seu aplicativo remoto e do seu aplicativo de player personalizado são mescladas. Por padrão, isso é feito por meio do mínimo de distâncias do plano próximo e do máximo de distâncias do plano distante. Caso o lado remoto ou local sejam invertidos, digamos que < perto, as distâncias remotas do plano próximo/longe são invertidas.

## <a name="optional-set-blitremoteframetimeout"></a>Opcional: definir BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` tem suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9). 

A ```PlayerContext::BlitRemoteFrameTimeout``` propriedade especifica a quantidade de tempo que um quadro remoto será reutilizado se nenhum quadro remoto for recebido. 

Um caso de uso comum é habilitar o tempo limite de BlitRemoteFrame para exibir uma tela em branco se nenhum novo quadro for recebido por um determinado período de tempo. Quando habilitado, o tipo de retorno do método também pode ser usado para alternar para ```BlitRemoteFrame``` um conteúdo de fallback renderizado localmente. 

Para habilitar o tempo máximo, de definido o valor da propriedade como uma duração igual ou maior que 100 ms. Para desabilitar o tempoout, de definido a propriedade como duração zero. Se o tempoout estiver habilitado e nenhum quadro remoto for recebido durante a duração definida, BlitRemoteFrame falhará e retornará até que um novo quadro ```Failed_RemoteFrameTooOld``` remoto seja recebido.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Opcional: obter estatísticas sobre o último quadro remoto

Para diagnosticar problemas de desempenho ou rede, as estatísticas sobre o último quadro remoto podem ser recuperadas por meio da ```PlayerContext::LastFrameStatistics``` propriedade . As estatísticas são atualizadas durante a chamada para [HolographicFrame::P resentUsingCurrentPrediction.](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Para obter mais informações, consulte ```PlayerFrameStatistics``` a documentação no ```Microsoft.Holographic.AppRemoting.idl``` [arquivo](#idl).

## <a name="optional-custom-data-channels"></a>Opcional: Canais de dados personalizados

Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão de comunicação de comunicação remo já estabelecida. Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.

## <a name="see-also"></a>Consulte Também
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs Windows Mixed Reality holográficas](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs OpenXR](holographic-remoting-create-remote-openxr.md)
* [Canais de dados personalizados de comunicação remota holográfica](holographic-remoting-custom-data-channels.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solução de problemas e limitações de remoção holográfica](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)