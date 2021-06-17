---
title: Captura de realidade misturada para desenvolvedores
description: Saiba mais sobre as práticas recomendadas para habilenciar, usar e renderizar a captura de realidade misturada para desenvolvedores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, photo, video, capture, camera
ms.openlocfilehash: ec1a53d2f623a8047c2ee1973d8d6f20458ade88
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110248"
---
# <a name="mixed-reality-capture-for-developers"></a>Captura de realidade misturada para desenvolvedores

> [!NOTE]
> Consulte [Renderizar da câmera PV abaixo](#render-from-the-pv-camera-opt-in) para obter diretrizes sobre uma nova funcionalidade do MRC para HoloLens 2.

Você pode tirar uma foto ou vídeo do MRC (Mixed [Reality Capture)](/hololens/holographic-photos-and-videos) a qualquer momento, mas há algumas coisas a ter em mente ao desenvolver seu aplicativo. Isso inclui as práticas recomendadas para a qualidade visual do MRC e a capacidade de responder às alterações do sistema enquanto os MRCs estão sendo capturados.

Os desenvolvedores também podem integrar perfeitamente a captura e a inserção de realidade misturada em seus aplicativos.

O MRC no HoloLens (primeira geração) dá suporte a vídeos e fotos de até 720p, enquanto o MRC no HoloLens 2 dá suporte a vídeos de até 1080p e fotos de até 4K de resolução.

## <a name="the-importance-of-quality-mrc"></a>A importância do MRC de qualidade

Seja capturas de tela de realidade misturada em sua página Microsoft Store ou outros usuários que compartilham conteúdo de captura em redes sociais, Captura de Realidade Misturada mídia geralmente é uma primeira exposição dos usuários ao seu aplicativo. Você pode usar o MRC para demonstração de seu aplicativo, instruir os usuários, incentivar os usuários a compartilhar suas interações de mundo misto e para pesquisa de usuários e solução de problemas.

## <a name="how-mrc-impacts-your-app"></a>Como o MRC afeta seu aplicativo

### <a name="enabling-mrc-in-your-app"></a>Habilitando o MRC em seu aplicativo

Por padrão, um aplicativo não precisa fazer nada para permitir que os usuários capturem realidade misturada.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Habilitando o alinhamento aprimorado para MRC em seu aplicativo

Por padrão, a captura de realidade misturada combina a saída holográfica do olho direito com a câmera de foto/vídeo (PV). Essas duas fontes são combinadas usando o ponto de foco definido pelo aplicativo imersivo em execução no momento.

Isso significa que os hologramas fora do plano de foco não serão alinhados devido à distância física entre a câmera PV e a exibição à direita.

#### <a name="set-the-focus-point"></a>Definir o ponto de foco

Aplicativos imersivos (no HoloLens) [](../unity/focus-point-in-unity.md) devem definir o ponto de foco de onde eles querem que seu plano de estabilização seja. Isso garante o melhor alinhamento no headset e na captura de realidade misturada.

Se um ponto de foco não estiver definido, o plano de estabilização será padrão para 2 metros.

#### <a name="render-from-the-pv-camera-opt-in"></a>Renderizar da câmera PV (aceitação)

O HoloLens 2 adiciona a capacidade de um aplicativo imersivo renderizar da câmera **PV** enquanto a captura de realidade misturada está em execução. Para garantir que o aplicativo dá suporte à renderização adicional corretamente, o aplicativo precisa optar por essa funcionalidade.

A renderização da câmera PV oferece as seguintes melhorias em relação à experiência de MRC padrão:
* O alinhamento do holograma para seu ambiente físico e mãos para interações próximas deve ser preciso em todas as distâncias. Evite ter um deslocamento em distâncias que não seja o ponto de foco, como você pode ver no MRC padrão.
* O olho direito no headset não será comprometido, pois ele não será usado para renderizar os hologramas para a saída do MRC.

Há três etapas para habilitar a renderização da câmera PV:
1. Habilitar o PhotoVideoCamera HolographicViewConfiguration
2. Manipular a renderização holographicCamera adicional
3. Verifique se os sombreadores e o código renderizaram corretamente deste HolographicCamera adicional

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>Habilitar o PhotoVideoCamera HolographicViewConfiguration no DirectX

Para optar pela renderização da Câmera PV, um aplicativo simplesmente habilita o [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)do PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Manipular a renderização holographicCamera adicional no DirectX

Quando o aplicativo tiver aceitação para renderizar da câmera PV e a captura de realidade misturada for iniciada:
1. O evento CameraAdded do HolographicSpace será ativos. Esse evento poderá ser adiado se o aplicativo não puder lidar com a câmera no momento.
2. Depois que o evento tiver sido concluído sem adiamentos pendentes, o HolographicCamera aparecerá na próxima lista AddedCameras do HolographicFrame.

Quando a captura de realidade misturada for interrompida (ou se o aplicativo desabilitar a configuração de exibição enquanto a captura de realidade misturada estiver em execução): o HolographicCamera aparecerá na próxima lista RemoveCameras do HolographicFrame e o evento CameraRemoved do HolographicSpace será açado.

Uma [propriedade ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) foi adicionada ao HolographicCamera para ajudar a identificar a configuração à qual uma câmera pertence.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Habilitar o PhotoVideoCamera HolographicViewConfiguration no Unity

> [!NOTE]
> Se você estiver usando o Unity 2018, isso exigirá **o Unity 2018.4.13f1** ou mais novo. Se você estiver usando o Unity 2019, isso exigirá **o Unity 2019.4** ou mais novo.

Para optar pela renderização da Câmera PV ao usar [](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) o Kit de Ferramentas de Realidade Misturada, [](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)habilita o provedor de Configurações da Câmera Windows Mixed Reality e marque Renderizar da Câmera **PV.**

Se você não estiver usando o Kit de Ferramentas de Realidade Misturada, poderá usar um componente para optar [manualmente,](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) conforme descrito acima para o DirectX.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Manipular a renderização holographicCamera adicional no Unity

Isso é feito automaticamente pelo Unity.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Habilitar o PhotoVideoCamera HolographicViewConfiguration no Unreal

> [!NOTE]
> Isso requer o **Unreal Engine 4.25** ou posterior.

Para aceitar a renderização por meio da Câmera de PV:

1. Chamar **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**
    * Use os valores de **Tamanho X** e **Tamanho Y** para definir as dimensões do vídeo.

![Terceira câmera](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Manipular a renderização holographicCamera adicional no Unreal

Isso é feito automaticamente pelo Unreal.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Verificar sombreadores e código com suporte a câmeras adicionais

Execute uma captura de realidade misturada e verifique se há alinhamento incomum, conteúdo ausente ou problemas de desempenho. Atualize sombreadores e código conforme apropriado.

Se houver determinadas cenas que não podem dar suporte à renderização para uma câmera adicional, você poderá desabilitar o HolographicViewConfiguration do PhotoVideoCamera.

### <a name="disabling-mrc-in-your-app"></a>Desabilitando o MRC em seu aplicativo

#### <a name="2d-app"></a>Aplicativo 2D

Os aplicativos 2D podem optar por ter seu conteúdo visual obscurecido quando a captura de realidade misturada estiver em execução:
* Presente com o [sinalizador DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) de dados
* Criar a cadeia de permuta do aplicativo com o [sinalizador DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) aplicativo
* Com o Atualização de maio de 2019 para o Windows 10, definindo [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) do ApplicationView

#### <a name="immersive-app"></a>Aplicativo imersivo

Os aplicativos imersivos podem optar por ter seu conteúdo visual excluído da captura de realidade misturada:
* Definindo [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) de HolographicCameraRenderingParameter para desabilitar a captura de realidade misturada para seu quadro associado
* Definindo [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) da HolographicCamera para desabilitar a captura de realidade misturada para sua câmera holográfica associada

#### <a name="password-keyboard"></a>Teclado de senha

Com o Atualização de maio de 2019 para o Windows 10, o conteúdo visual é excluído automaticamente da captura de realidade misturada quando uma senha ou teclado de pino está visível.

### <a name="knowing-when-mrc-is-active"></a>Saber quando o MRC está ativo

A [classe AppCapture](/uwp/api/Windows.Media.Capture.AppCapture) pode ser usada por um aplicativo para saber quando a captura de realidade misturada do sistema está em execução (para áudio ou vídeo).

>[!NOTE]
>A API [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) do AppCapture poderá retornar nulo se a captura de realidade misturada não estiver disponível no dispositivo. Também é importante des registrar o evento CapturingChanged quando seu aplicativo é suspenso, caso contrário, o MRC pode entrar em um estado bloqueado.

### <a name="best-practices-hololens-specific"></a>Práticas recomendadas (específicas do HoloLens)

Espera-se que o MRC funcione sem esforço de desenvolvimento adicional, mas há algumas coisas a serem cientes ao fornecer a melhor experiência de captura de realidade misturada.

**O MRC usa o canal alfa do holograma para combinar com a [imagem da](locatable-camera.md) câmera**

A etapa mais importante é certificar-se de que seu aplicativo está limpando para preto transparente em vez de limpar para preto opaco. No Unity, isso é feito por padrão com o MixedRealityToolkit. Se você estiver desenvolvendo no não Unity, talvez seja necessário fazer uma alteração de linha.

Aqui estão alguns dos artefatos que você poderá ver no MRC se seu aplicativo não estiver desobstruindo para preto transparente:

**Falhas de exemplo:** bordas pretas ao redor do conteúdo (falha ao limpar para preto transparente)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**Exemplo de falhas:** toda a cena em segundo plano do holograma aparece preta. Definir um valor alfa em segundo plano de um resulta em um plano de fundo preto

![Definir um valor alfa em segundo plano de 1 resulta em um plano de fundo preto](images/clearopaqueblack-300px.png)

**Resultado esperado:** os hologramas aparecem corretamente mesclados com o mundo real (resultado esperado se estiver limpando para preto transparente)

![Resultado esperado se estiver limpando para preto transparente](images/cleartransparentblack-300px.png)

**Solução**:
* Altere qualquer conteúdo que aparece como preto opaco para ter um valor alfa de 0.
* Verifique se o aplicativo está limpando para preto transparente.
* O Unity assume como padrão limpar automaticamente com o MixedRealityToolkit, mas se for um aplicativo não Unity, você deverá modificar a cor usada com ID3D11DeiceContext::ClearRenderTargetView(). Você deseja garantir que você limpe para preto transparente (0,0,0,0) em vez de preto opaco (0,0,0,1).

Agora você pode ajustar os valores alfa de seus ativos se quiser, mas normalmente não é necessário. Na maioria das vezes, os MRCs terão uma boa aparência. O MRC assume alfa pré-multiplicado. Os valores alfa afetarão apenas a captura do MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>O que esperar quando o MRC estiver habilitado no HoloLens

O seguinte se aplica ao HoloLens (primeira geração) e ao HoloLens 2, a menos que seja notado de outra forma:

* O sistema irá acelerar o aplicativo para renderização de 30 Hz. Isso cria algum espaço de trabalho para que o MRC seja executado para que o aplicativo não precise manter uma reserva de orçamento constante e também corresponde à taxa de quadros de registro de vídeo mrc de 30 fps
* O conteúdo do holograma no olho direito do dispositivo pode parecer "inativo" ao gravar/transmitir MRC: o texto pode se tornar mais difícil de ler e as bordas do holograma podem parecer mais desajustadas (optar pela terceira renderização de câmera no **HoloLens 2** evita esse comprometimento)
* Fotos e vídeos do MRC [](../unity/focus-point-in-unity.md) respeitarão o ponto de foco do aplicativo se o aplicativo o habilitar, o que ajudará a garantir que os hologramas sejam posicionados com precisão. Para vídeos, o Ponto de Foco é suavizado para que os hologramas possam parecer se desafocar lentamente se a profundidade do Ponto de Foco mudar significativamente. Hologramas que estão em profundidades diferentes do ponto de foco podem parecer deslocamentos do mundo real (veja o exemplo abaixo em que o Ponto de Foco está definido em 2 metros, mas o holograma está posicionado a 1 medidor).

![Hologramas a 2 metros aparecerão perfeitamente registrados para o mundo. Os hologramas a distâncias próximas ou distantes podem ser ligeiramente deslocadas.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrando a funcionalidade do MRC de dentro do seu aplicativo

Seu aplicativo de realidade misturada pode iniciar a captura de fotos ou vídeos do MRC de dentro do aplicativo e o conteúdo capturado é disponibilizado para seu aplicativo sem ser armazenado no "Rolo de câmera" do dispositivo. Você pode criar um gravador personalizado do MRC ou aproveitar a interface do usuário de captura de câmera. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC com interface do usuário da câmera

Os desenvolvedores podem usar a API de *[interface](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* do usuário de Captura de Câmera para obter uma foto ou vídeo de realidade misturada capturada pelo usuário com apenas algumas linhas de código.

Essa API inicia a interface do usuário interna da câmera mrc em que os usuários podem tirar uma foto ou um vídeo e retorna a captura resultante para seu aplicativo. Você pode criar um gravador Captura de Realidade Misturada personalizado se precisar adicionar sua própria interface do usuário da câmera ou acesso de nível inferior para capturar fluxos.

### <a name="creating-a-custom-mrc-recorder"></a>Criando um gravador personalizado do MRC

Embora o usuário sempre possa disparar uma foto ou vídeo usando o serviço de captura mrc do sistema, um aplicativo pode querer criar um aplicativo de câmera personalizado que inclua hologramas no fluxo de câmera, assim como o MRC. Isso permite que o aplicativo inicialize capturas da entrada do usuário, crie uma interface do usuário de gravação personalizada ou personalize as configurações do MRC para nomear alguns exemplos.

**O HoloStudio adiciona uma câmera MRC personalizada usando efeitos de MRC**

![O HoloStudio adiciona uma câmera MRC personalizada usando efeitos de MRC](images/cameraiconholostudio-300px.jpg)

Os aplicativos unity [devem Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) para a propriedade para habilitar hologramas.

Outros aplicativos podem fazer isso usando as [APIs](/uwp/api/Windows.Media.Capture.MediaCapture) do Windows Media Capture para controlar a Câmera e adicionar um efeito mrc video and Audio para incluir hologramas virtuais e áudio do aplicativo em imagens e vídeos.

Os aplicativos têm duas opções para adicionar o efeito:
* A API mais antiga: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* A nova API recomendada da Microsoft (retorna um objeto , possibilitando manipular propriedades dinâmicas): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) que exigem que o aplicativo crie sua própria implementação de [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) [e IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition). Consulte o [aplicativo de exemplo mrc](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) para ver exemplos.

>[!NOTE]
> O namespace Windows.Media.MixedRealityCapture não será reconhecido pelo Visual Studio, mas as cadeias de caracteres ainda são válidas.

Efeito de vídeo mrc (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Nome da propriedade  |  Type  |  Valor padrão  |  Descrição |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Descrever para qual fluxo de captura esse efeito é usado. O áudio não está disponível. |
|  HologramCompositionEnabled  |  booleano  |  TRUE  |  Sinalizador para habilitar ou desabilitar hologramas na captura de vídeo. |
|  RecordingIndicatorEnabled  |  booleano  |  TRUE  |  Sinalizador para habilitar ou desabilitar o indicador de gravação na tela durante a captura do holograma. |
|  VideoStabilizationEnabled  |  booleano  |  FALSE  |  Sinalizador para habilitar ou desabilitar a estabilização de vídeo ativada pelo rastreador do HoloLens. |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Definir quantos quadros históricos são usados para estabilização de vídeo. 0 é de 0 latência e quase "livre" de uma perspectiva de energia e desempenho. 15 é recomendado para a mais alta qualidade (ao custo de 15 quadros de latência e memória). |
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 (headset imersivo)  |  Definir coeficiente de opacidade global do holograma no intervalo de 0,0 (totalmente transparente) para 1,0 (totalmente opaco). |
|  BlankOnProtectedContent  |  booleano  |  FALSE  |  Sinalizador para habilitar ou desabilitar o retorno de um quadro vazio se houver um aplicativo UWP 2d mostrando conteúdo protegido. Se esse sinalizador for false e um aplicativo UWP 2d estiver mostrando conteúdo protegido, o aplicativo UWP 2d será substituído por uma textura de conteúdo protegido no headset e na captura de realidade misturada. |
|  ShowHiddenMesh  |  booleano  |  FALSE  |  Sinalizador para habilitar ou desabilitar mostrando a malha de área oculta da câmera holográfica e o conteúdo vizinho. |
| OutputSize | Tamanho | 0, 0 | Definir o tamanho de saída desejado após o corte para estabilização de vídeo. Um tamanho de corte padrão será escolhido se 0 ou um tamanho de saída inválido for especificado. |
| PreferredHologramPerspective | UINT32 | **Renderizar da configuração** câmera no Portal de Dispositivos do Windows | Enum usado para indicar qual configuração de exibição de câmera holográfica deve ser capturada: 0 (Exibição) significa que o aplicativo não será solicitado a renderizar da câmera de foto/vídeo; 1 (PhotoVideoCamera) solicitará que o aplicativo renderizar da câmera de foto/vídeo (se o aplicativo dá suporte a ele). Somente com suporte no HoloLens 2 |

>[!NOTE]
> Você pode alterar o valor padrão **de PreferredHologramPerspective** no Portal de Dispositivos do Windows indo para a página [Captura de Realidade Misturada e](using-the-windows-device-portal.md#mixed-reality-capture) desmarcando **Renderizar da Câmera.** A configuração assume como **padrão 1 (PhotoVideoCamera),** mas pode ser desmarcada para defini-la **como 0 (Exibição)**.
>
> O valor padrão **de PreferredHologramPerspective** era **0 (Exibição)** antes da atualização de junho de 2020 (Windows Holographic, versão 2004 build 19041.1106 e Windows Holographic, versão 1903 build 18362.1064).

Efeito de áudio MRC (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

| Nome da propriedade | Type | Valor padrão | Descrição |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (microfone e áudio do sistema) | Enum usado para indicar quais fontes de áudio devem ser usadas: 0 (somente áudio de microfone), 1 (somente áudio do sistema), 2 (microfone e áudio do sistema) |
| LoopbackGain | FLOAT | **Configuração ganho de** áudio do aplicativo no Portal de Dispositivos do Windows | Obtenha a aplicação ao volume de áudio do sistema. Varia de 0,0 a 5,0. Somente com suporte no HoloLens 2 |
| MicrophoneGain | FLOAT | Configuração de **lucro de áudio do MIC** no portal do dispositivo Windows | Obter para aplicar ao volume do MIC. Varia de 0,0 a 5,0. Somente com suporte no HoloLens 2 |

>[!NOTE]
> Você pode alterar o valor padrão de **LoopbackGain** ou **MicrophoneGain** no portal do dispositivo Windows acessando a [página de captura da realidade misturada](using-the-windows-device-portal.md#mixed-reality-capture) e ajustando o controle deslizante ao lado de suas respectivas configurações. Ambas as configurações assumem como padrão **1,0**, mas podem ser definidas como qualquer valor entre **0,0** e **5,0**.
>
> O uso do portal de dispositivos do Windows para configurar os valores de obter padrão foi adicionado com a atualização de junho de 2020 (Windows Holographic, versão 2004 Build 19041,1106 e Windows Holographic, versão 1903 Build 18362,1064).

### <a name="simultaneous-mrc-limitations"></a>Limitações de MRC simultâneas

Você precisa estar ciente de determinadas limitações quando vários aplicativos estão acessando a MRC ao mesmo tempo.

#### <a name="photovideo-camera-access"></a>Acesso à câmera de foto/vídeo

No HoloLens 1, a MRC falhará em capturar um vídeo de foto ou captura enquanto um processo estiver gravando vídeo ou tirando uma foto. O inverso também é verdadeiro: se a MRC estiver em execução, o aplicativo não conseguirá obter acesso à câmera. 

Com o HoloLens 2, é possível compartilhar o acesso à câmera. Se você não precisar de controle direto da resolução ou da taxa de quadros, poderá inicializar MediaCapture usando a [Propriedade sharedmode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) com SharedReadOnly.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>Acesso interno à câmera de fotos/vídeo da MRC

Funcionalidade da MRC incorporada ao Windows 10 (via Cortana, menu Iniciar, atalhos de hardware, Miracast, portal de dispositivos Windows):

* Será executado com ExclusiveControl por padrão

No entanto, o suporte foi adicionado ao subsistema da MRC para operar em um modo compartilhado: 

* Se um aplicativo solicitar acesso ExclusiveControl à câmera de foto/vídeo, a MRC interna interromperá automaticamente o uso da câmera de foto/vídeo para que a solicitação do aplicativo seja realizada com sucesso 
* Se a MRC interna for iniciada enquanto um aplicativo tiver ExclusiveControl, a MRC interna será executada no modo SharedReadOnly 

Essa funcionalidade de modo compartilhado tem determinadas restrições:

* Foto via Cortana, atalhos de hardware ou menu iniciar: requer a atualização do Windows 10 de abril de 2018 (ou posterior)
* Vídeo via Cortana, atalhos de hardware ou menu iniciar: requer a atualização do Windows 10 de abril de 2018 (ou posterior)
* Streaming de MRC sobre Miracast: requer a atualização do Windows 10 de outubro de 2018 (ou posterior)
* Streaming de MRC no portal de dispositivo do Windows ou por meio do aplicativo de complemento do HoloLens: requer o HoloLens 2

>[!NOTE]
> A resolução e a taxa de quadros da interface do usuário da câmera da MRC interna podem ser reduzidas de seus valores normais quando outro aplicativo estiver usando a câmera de foto/vídeo.

#### <a name="mrc-access-for-developers"></a>Acesso da MRC para desenvolvedores

Recomendamos que você sempre solicite controle exclusivo para a câmera ao usar a MRC. Isso garantirá que seu aplicativo tenha controle total das configurações da câmera, contanto que você esteja ciente das limitações listadas acima. 

* Criar um objeto de captura de mídia usando as [configurações de inicialização](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)
* Definir a propriedade [sharingmode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) como **exclusiva**

> [!CAUTION]
> Lembre-se de ler atentamente os [comentários de sharingmode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) antes de continuar.

* Configure sua câmera da maneira desejada
* Inicie o aplicativo, Capture quadros de vídeo com a API inicial e, em seguida, habilite a MRC

> [!CAUTION]
> Se você iniciar a MRC antes de iniciar seu aplicativo, não será possível garantir que o recurso funcionará conforme o esperado.

Você pode encontrar uma amostra completa do processo acima no exemplo de [acompanhamento facial do Holographic](/samples/microsoft/windows-universal-samples/holographicfacetracking).

> [!NOTE]
> Antes da atualização do Windows 10 de abril de 2018, o gravador da MRC personalizada de um aplicativo era mutuamente exclusivo com o sistema da MRC (capturando fotos, capturando vídeos ou transmitindo do portal de dispositivos do Windows).

## <a name="see-also"></a>Confira também

* [Captura de realidade mista](/hololens/holographic-photos-and-videos)
* [Modo de exibição Espectador](spectator-view.md)
* [Visão geral do desenvolvimento do Unity](../unity/unity-development-overview.md)
* [Visão geral do desenvolvimento do Unreal](../unreal/unreal-development-overview.md)
