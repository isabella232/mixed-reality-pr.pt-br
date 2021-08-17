---
title: Escrevendo um player de remoção holográfica personalizado (C++)
description: Crie um aplicativo de Remotação Hologaphic personalizado para exibir o conteúdo renderizado em um computador remoto para seu HoloLens 2.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 7/30/2021
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, NuGet, app manifest, player context, remote app, mixed reality headset, windows mixed reality headset, headset de realidade virtual
ms.openlocfilehash: 37388dc9cbf70cb7fccd742fb45e1e29c0ceb971
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184727"
---
# <a name="writing-a-custom-holographic-remoting-player-app-c"></a>Escrevendo um aplicativo personalizado de player de remoção holográfica (C++)

>[!IMPORTANT]
>Este documento descreve a criação de um aplicativo de player personalizado para HoloLens 2. Players personalizados escritos para HoloLens 2 não são compatíveis com aplicativos remotos escritos para HoloLens 1. Isso implica que ambos os aplicativos devem usar NuGet versão **do pacote 2.x.x**.

Ao criar um aplicativo de player de remota holografia personalizado, você pode criar um aplicativo personalizado capaz de exibir exibições [imersivas](../../design/app-views.md) de em um computador remoto em seu HoloLens 2. Todo o código nesta página e projetos de trabalho podem ser encontrados no repositório [GitHub](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)de exemplos de Remo holográfica .

Um player de remota holográfica permite que [](rendering.md) seu aplicativo ex display conteúdo holográfico renderizado em um computador desktop ou dispositivo UWP como o Xbox One com acesso a mais recursos do sistema. Um aplicativo Holographic Remoting Player transmite dados de entrada para um aplicativo remoto holográfico de remoção e recebe de volta uma exibição imersiva como fluxo de áudio e vídeo. A conexão é feita usando o Wi-Fi padrão. Para criar um aplicativo player, use um NuGet para adicionar a Holographic Remoting ao seu aplicativo UWP. Em seguida, escreva o código para manipular a conexão e exibir uma exibição imersiva. 

## <a name="prerequisites"></a>Pré-requisitos

Um bom ponto de partida é um aplicativo UWP baseado em DirectX que já tem como alvo a API Windows Mixed Reality. Para obter detalhes, consulte [Visão geral do desenvolvimento do DirectX.](../native/directx-development-overview.md) Se você não tiver um aplicativo existente e quiser começar do zero, o modelo de projeto [holográfico do C++](../native/creating-a-holographic-directx-project.md) será um bom ponto de partida.

>[!IMPORTANT]
>Qualquer aplicativo que use a Holographic Remoting deve ser autor para usar um [apartment multi-threaded.](/windows/win32/com/multithreaded-apartments) Há suporte para o uso de um apartment [de thread](/windows/win32/com/single-threaded-apartments) único, mas levará ao desempenho abaixo do ideal e possivelmente à gagueja durante a reprodução. Ao usar C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) um apartment multi-threaded é o padrão.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obter o pacote de NuGet de NuGet Holographic

As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.
1. Abra o projeto no Visual Studio.
2. Clique com o botão direito do mouse no nó do projeto **e selecione Gerenciar NuGet Pacotes...**
3. No painel exibido, selecione **Procurar** e, em seguida, pesquise "Holographic Remoting".
4. Selecione **Microsoft.Holographic.Remoting**, escolha a versão **2.x.x** mais recente e **selecione Instalar**.
5. Se a **caixa de** diálogo Visualização for exibida, selecione **OK.**
6. Selecione **Aceito quando a** caixa de diálogo do contrato de licença for exibida.

>[!IMPORTANT]
><a name="idl"></a>O dentro do pacote NuGet contém documentação detalhada para a ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` API exposta pela Holographic Remoting.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modificar o Package.appxmanifest do aplicativo

Para tornar o aplicativo ciente do Microsoft.Holographic.AppRemoting.dll adicionado pelo pacote NuGet, as seguintes etapas precisam ser realizadas no projeto:

1. No Gerenciador de Soluções clique com o botão direito do mouse **no arquivo Package.appxmanifest** e selecione **Abrir com...**
2. Selecione **Editor xml (texto) e** selecione **OK**
3. Adicione as linhas a seguir ao arquivo e salve
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
## <a name="create-the-player-context"></a>Criar o contexto do player

Como uma primeira etapa, o aplicativo deve criar um contexto de player.

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
>A remoção holográfica funciona substituindo o runtime Windows Mixed Reality que faz parte do Windows por um runtime específico de remoção. Isso é feito durante a criação do contexto do player. Por esse motivo, qualquer chamada em qualquer API Windows Mixed Reality antes de criar o contexto do player pode resultar em um comportamento inesperado. A abordagem recomendada é criar o contexto do player o mais cedo possível antes da interação com qualquer API de Realidade Misturada. Nunca misture objetos criados ou recuperados por meio de qualquer API Windows Mixed Reality antes da chamada para com objetos criados ```PlayerContext::Create``` ou recuperados posteriormente.

Em seguida, o HolographicSpace pode ser criado chamando [HolographicSpace.CreateForCoreWindow.](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Conexão para o aplicativo remoto

Depois que o aplicativo player estiver pronto para renderizar o conteúdo, uma conexão com o aplicativo remoto poderá ser estabelecida.

A conexão pode ser estabelecida de uma das seguintes maneiras:
1) O aplicativo player em execução HoloLens 2 se conecta ao aplicativo remoto.
2) O aplicativo remoto se conecta ao aplicativo player em execução no HoloLens 2.

Para se conectar do aplicativo player ao aplicativo remoto, chame o método no ```Connect``` contexto do player especificando o nome do host e a porta. A porta padrão é **8265**.

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
>Assim como com qualquer API do C++/WinRT pode lançar um ```Connect``` winrt::hresult_error que precisa ser tratado.

A escuta de conexões de entrada no aplicativo player pode ser feita chamando o ```Listen``` método . A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada. A porta de handshake é usada para o handshake inicial. Em seguida, os dados são enviados pela porta de transporte. Por padrão, os **números de porta 8265** e **8266** são usados.

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
1) OnConnected: disparado quando uma conexão com o aplicativo remoto foi estabelecida com êxito.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: disparado se uma conexão estabelecida for encerrada ou não for possível estabelecer uma conexão.
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

3) OnListening: ao escutar conexões de entrada é iniciado.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Além disso, o estado de conexão pode ser consultado usando ```ConnectionState``` a propriedade no contexto do player.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Exibir o quadro renderizado remotamente

Para exibir o conteúdo renderizado remotamente, chame ```PlayerContext::BlitRemoteFrame``` ao renderizar [um HolographicFrame.](/uwp/api/windows.graphics.holographic.holographicframe) 

```BlitRemoteFrame``` requer que o buffer de fundo para o HolographicFrame atual seja vinculado como destino de renderização. O buffer de fundo pode ser recebido dos [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) por meio da [propriedade Direct3D11BackBuffer.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)

Quando chamado, copia o quadro recebido mais recente do aplicativo ```BlitRemoteFrame``` remoto para o BackBuffer do HolographicFrame. Além disso, o conjunto de pontos de foco será definido, se o aplicativo remoto tiver especificado um ponto de foco durante a renderização do quadro remoto.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` potencialmente substitui o ponto de foco para o quadro atual. 
>- Para especificar um ponto de foco de fallback, chame [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes de ```PlayerContext::BlitRemoteFrame``` . 
>- Para substituir o ponto de foco remoto, chame [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  após ```PlayerContext::BlitRemoteFrame``` .

Em caso de sucesso, ```BlitRemoteFrame``` retorna ```BlitResult::Success_Color``` . Caso contrário, retornará o motivo da falha:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: falha porque nenhum quadro remoto está disponível.
- ```BlitResult::Failed_NoCamera```: falha porque nenhuma câmera está presente.
- ```BlitResult::Failed_RemoteFrameTooOld```: falha porque o quadro remoto é muito antigo (consulte a propriedade PlayerContext::BlitRemoteFrameTimeout).

>[!IMPORTANT]
> A partir da [versão 2.1.0,](holographic-remoting-version-history.md#v2.1.0) é possível com um player personalizado usar a reprojeção de profundidade por meio da Holographic Remoting.

```BlitResult``` também pode retornar ```BlitResult::Success_Color_Depth``` sob as seguintes condições:

- O aplicativo remoto comprometeu um buffer de profundidade [por meio de HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).
- O aplicativo de player personalizado tiver vinculado um buffer de profundidade válido antes de chamar ```BlitRemoteFrame``` .

Se essas condições são atendidas, a profundidade remota será apagada para ```BlitRemoteFrame``` o buffer de profundidade local atualmente vinculado. Em seguida, você pode renderizar conteúdo local adicional, que terá interseção de profundidade com o conteúdo renderizado remoto. Além disso, você pode fazer commit do buffer de profundidade local por meio de [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) em seu player personalizado para ter a reprojeção de profundidade para conteúdo renderizado remoto e local. Consulte [Reprojeto de profundidade para](hologram-stability.md#reprojection) obter detalhes.

### <a name="projection-transform-mode"></a>Modo de transformação de projeção

Um problema, que revela ao usar a reprojeção de profundidade por meio da remota holográfica, é que o conteúdo remoto pode ser renderizado com uma transformação de projeção diferente do conteúdo local renderizado diretamente pelo seu aplicativo de player personalizado. Um caso de uso comum é especificar valores diferentes para o plano próximo e distante (via [HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) e [HolographicCamera::SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) no lado do jogador e no lado remoto. Nesse caso, não fica claro se a transformação de projeção no lado do jogador deve refletir as distâncias remotas do plano próximo/distante ou as locais.

A partir da [versão 2.1.0,](holographic-remoting-version-history.md#v2.1.0) você pode controlar o modo de transformação de projeção por meio de ```PlayerContext::ProjectionTransformConfig``` . Os valores com suporte são:

- ```Local``` - [HolographicCameraPose::P rojectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) retorna uma transformação de projeção, que reflete as distâncias de plano próximas/distantes definidas pelo aplicativo de player personalizado no HolographicCamera.
- ```Remote``` – A transformação projeção reflete as distâncias de plano próximas/distantes especificadas pelo aplicativo remoto.
- ```Merged``` - Distâncias de plano próximas/distantes do aplicativo remoto e do aplicativo de player personalizado são mescladas. Por padrão, isso é feito com o mínimo de distâncias de plano próximo e o máximo das distâncias distantes do plano. Caso o lado remoto ou local seja invertido, digamos que < próximo, as distâncias remotas do plano próximo/distante serão invertidas.

## <a name="optional-set-blitremoteframetimeout"></a>Opcional: Definir BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` tem suporte a partir da [versão 2.0.9](holographic-remoting-version-history.md#v2.0.9). 

A ```PlayerContext::BlitRemoteFrameTimeout``` propriedade especifica a quantidade de tempo que um quadro remoto será reutilizado se nenhum novo quadro remoto for recebido. 

Um caso de uso comum é habilitar o tempo de vida de BlitRemoteFrame para exibir uma tela em branco se nenhum novo quadro for recebido por um determinado período de tempo. Quando habilitado, o tipo de retorno do ```BlitRemoteFrame``` método também pode ser usado para alternar para um conteúdo de fallback processado localmente. 

Para habilitar o tempo limite, defina o valor da propriedade como uma duração igual ou maior que 100 ms. Para desabilitar o tempo limite, defina a propriedade como duração zero. Se o tempo limite for habilitado e nenhum quadro remoto for recebido para a duração definida, o BlitRemoteFrame falhará e retornará ```Failed_RemoteFrameTooOld``` até que um novo quadro remoto seja recebido.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Opcional: obter estatísticas sobre o último quadro remoto

Para diagnosticar problemas de desempenho ou de rede, as estatísticas sobre o último quadro remoto podem ser recuperadas por meio da ```PlayerContext::LastFrameStatistics``` propriedade. As estatísticas são atualizadas durante a chamada para [HolographicFrame::P resentusingcurrentprediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Para obter mais informações, consulte a ```PlayerFrameStatistics``` documentação no ```Microsoft.Holographic.AppRemoting.idl``` [arquivo](#idl).

## <a name="optional-custom-data-channels"></a>Opcional: canais de dados personalizados

Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida. Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.

## <a name="see-also"></a>Consulte Também
* [Visão geral da comunicação remota do Holographic](holographic-remoting-overview.md)
* [escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md)
* [Canais de dados personalizados de comunicação remota holográfica](holographic-remoting-custom-data-channels.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)