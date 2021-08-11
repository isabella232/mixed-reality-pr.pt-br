---
title: Captura de realidade misturada para desenvolvedores
description: Saiba mais sobre as práticas recomendadas para habilenciar, usar e renderizar a captura de realidade misturada para desenvolvedores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, photo, video, capture, camera
ms.openlocfilehash: af585cd212ba8f2ddc3ea812c1fff2a5da8603bff0e77d8fc2ad794486821685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192080"
---
# <a name="mixed-reality-capture-for-developers"></a>Captura de realidade misturada para desenvolvedores

> [!NOTE]
> Consulte [Renderizar da câmera PV abaixo](#render-from-the-pv-camera-opt-in) para obter diretrizes sobre uma nova funcionalidade de MRC para HoloLens 2.

Você pode tirar uma foto ou vídeo do MRC (Mixed [Reality Capture)](/hololens/holographic-photos-and-videos) a qualquer momento, mas há algumas coisas a ter em mente ao desenvolver seu aplicativo. Isso inclui as práticas recomendadas para a qualidade visual do MRC e a capacidade de responder às alterações do sistema enquanto os MRCs estão sendo capturados.

Os desenvolvedores também podem integrar perfeitamente a captura e a inserção de realidade misturada em seus aplicativos.

O MRC no HoloLens (primeira geração) dá suporte a vídeos e fotos de até 720p, enquanto o MRC no HoloLens 2 dá suporte a vídeos de até 1080p e fotos de até 4K de resolução.

## <a name="the-importance-of-quality-mrc"></a>A importância do MRC de qualidade

Seja capturas de tela de realidade misturada em sua página Microsoft Store ou outros usuários que compartilham conteúdo de captura em redes sociais, a mídia Captura de Realidade Misturada geralmente é uma primeira exposição dos usuários ao seu aplicativo. Você pode usar o MRC para demonstração de seu aplicativo, instruir os usuários, incentivar os usuários a compartilhar suas interações de mundo misto e para pesquisa de usuários e solução de problemas.

## <a name="how-mrc-impacts-your-app"></a>Como o MRC afeta seu aplicativo

### <a name="enabling-mrc-in-your-app"></a>Habilitando o MRC em seu aplicativo

Por padrão, um aplicativo não precisa fazer nada para permitir que os usuários capturem realidade misturada.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Habilitando o alinhamento aprimorado para MRC em seu aplicativo

Por padrão, a captura de realidade misturada combina a saída holográfica do olho direito com a câmera de foto/vídeo (PV). Essas duas fontes são combinadas usando o ponto de foco definido pelo aplicativo imersivo em execução no momento.

Isso significa que os hologramas fora do plano de foco não serão alinhados devido à distância física entre a câmera PV e a exibição à direita.

#### <a name="set-the-focus-point"></a>Definir o ponto de foco

Os aplicativos imersivos (HoloLens) devem [](../unity/focus-point-in-unity.md) definir o ponto de foco de onde eles querem que seu plano de estabilização seja. Isso garante o melhor alinhamento no headset e na captura de realidade misturada.

Se um ponto de foco não estiver definido, o plano de estabilização será padrão para 2 metros.

#### <a name="render-from-the-pv-camera-opt-in"></a>Renderizar da câmera PV (aceitação)

HoloLens 2 adiciona a capacidade de um aplicativo imersivo renderizar da câmera **PV** enquanto a captura de realidade misturada está em execução. Para garantir que o aplicativo dá suporte à renderização adicional corretamente, o aplicativo precisa optar por essa funcionalidade.

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

Para optar pela renderização da Câmera PV ao usar o Toolkit de Realidade [Misturada,](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)habilita o provedor Windows Mixed Reality [Camera Configurações](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) e marque Renderizar da **Câmera PV.**

Se você não estiver usando o Toolkit realidade misturada, poderá usar um componente para optar [manualmente,](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) conforme descrito acima para o DirectX.

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

### <a name="best-practices-hololens-specific"></a>Práticas recomendadas (HoloLens específicas)

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

**Resultado esperado:** Hologramas aparecem corretamente mesclados com o mundo real (resultado esperado se estiver limpando para preto transparente)

![Resultado esperado se estiver limpando para preto transparente](images/cleartransparentblack-300px.png)

**Solução**:
* Altere qualquer conteúdo que aparece como preto opaco para ter um valor alfa de 0.
* Verifique se o aplicativo está limpando para preto transparente.
* O Unity assume como padrão limpar automaticamente com o MixedRealityToolkit, mas se for um aplicativo não Unity, você deverá modificar a cor usada com ID3D11DeiceContext::ClearRenderTargetView(). Você deseja garantir que você limpe para preto transparente (0,0,0,0) em vez de preto opaco (0,0,0,1).

Agora você pode ajustar os valores alfa de seus ativos se quiser, mas normalmente não é necessário. Na maioria das vezes, os MRCs terão uma boa aparência. O MRC assume alfa pré-multiplicado. Os valores alfa afetarão apenas a captura do MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>O que esperar quando a MRC está habilitada no HoloLens

o seguinte se aplica a HoloLens (primeira geração) e HoloLens 2, a menos que indicado de outra forma:

* O sistema limitará o processamento do aplicativo a 30 Hz. Isso cria algum espaço para a MRC ser executado para que o aplicativo não precise manter uma reserva de orçamento constante e também corresponda à taxa de quadros de gravação de vídeo da MRC de 30 fps
* o conteúdo de holograma no olho certo do dispositivo pode parecer "sparkle" ao gravar/transmitir a MRC: o texto pode ser mais difícil de ler e as bordas do holograma podem parecer mais jaggy (optar pelo terceiro processamento da câmera na **HoloLens 2** evita esse comprometimento)
* Os vídeos e fotos da MRC respeitarão o [ponto de foco](../unity/focus-point-in-unity.md) do aplicativo se o aplicativo o tiver habilitado, o que ajudará a garantir que os hologramas sejam posicionados com precisão. Para vídeos, o ponto de foco é suavizado, de modo que os hologramas podem parecer descompassos mais lentamente se a profundidade do ponto de foco muda significativamente. Hologramas que estão em diferentes profundidades do ponto de foco podem aparecer de deslocamento do mundo real (veja o exemplo abaixo, em que o ponto de foco está definido em 2 metros, mas o holograma está posicionado em 1 metro).

![Hologramas com 2 medidores aparecerão perfeitamente registrados no mundo. Hologramas em distâncias de fechamento ou distantes podem ser um pouco de deslocamento.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrando a funcionalidade da MRC de dentro de seu aplicativo

Seu aplicativo de realidade misturada pode iniciar a captura de vídeo ou foto da MRC de dentro do aplicativo, e o conteúdo capturado é disponibilizado para seu aplicativo sem ser armazenado no "rolo de câmera" do dispositivo. Você pode criar um gravador da MRC personalizado ou aproveitar a interface do usuário de captura de câmera interna. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC com interface do usuário da câmera interna

Os desenvolvedores podem usar a *[API da interface do usuário de captura de câmera](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* para obter uma foto ou vídeo de realidade misturada do usuário com apenas algumas linhas de código.

Essa API inicia a interface do usuário da câmera da MRC interna, na qual os usuários podem tirar uma foto ou um vídeo e retornar a captura resultante para seu aplicativo. Você pode criar um gravador de captura de realidade mista personalizada se precisar adicionar sua própria interface do usuário da câmera ou acesso de nível inferior para capturar fluxos.

### <a name="creating-a-custom-mrc-recorder"></a>Criando um gravador da MRC personalizado

Embora o usuário sempre possa disparar uma foto ou vídeo usando o serviço de captura de MRC do sistema, um aplicativo pode querer criar um aplicativo de câmera personalizado que inclua hologramas no fluxo da câmera, assim como a MRC. Isso permite que o aplicativo inicie capturas de entrada do usuário, crie uma interface de usuário de gravação personalizada ou personalize as configurações da MRC para citar alguns exemplos.

**HoloStudio adiciona uma câmera da mrc personalizada usando os efeitos da mrc**

![HoloStudio adiciona uma câmera da mrc personalizada usando os efeitos da mrc](images/cameraiconholostudio-300px.jpg)

Os aplicativos do Unity devem ver [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) para a propriedade para habilitar os hologramas.

outros aplicativos podem fazer isso usando as [Windows APIs de captura de mídia](/uwp/api/Windows.Media.Capture.MediaCapture) para controlar a câmera e adicionar um efeito de vídeo e áudio da MRC para incluir hologramas virtuais e áudio do aplicativo nos vídeos e continuas.

Os aplicativos têm duas opções para adicionar o efeito:
* A API mais antiga: [Windows. Media. Capture. MediaCapture. AddEffectAsync ()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* A nova API recomendada pela Microsoft (retorna um objeto, possibilitando a manipulação de propriedades dinâmicas): [Windows. Media. Capture. MediaCapture. AddVideoEffectAsync ()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows. Media. Capture. MediaCapture. AddAudioEffectAsync ()](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) que exige que o aplicativo Crie sua própria implementação de [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) e [IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition). Consulte o [aplicativo de exemplo da MRC](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) para obter exemplos.

>[!NOTE]
> O Windows. o namespace Media. MixedRealityCapture não será reconhecido pelo Visual Studio, mas as cadeias de caracteres ainda são válidas.

Efeito de vídeo da MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureVideoEffect**)

|  Nome da Propriedade  |  Type  |  Valor padrão  |  Descrição |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Descreva para qual fluxo de captura esse efeito é usado. O áudio não está disponível. |
|  HologramCompositionEnabled  |  booleano  |  TRUE  |  Sinalizador para habilitar ou desabilitar hologramas na captura de vídeo. |
|  RecordingIndicatorEnabled  |  booleano  |  TRUE  |  Sinalizador para habilitar ou desabilitar o indicador de gravação na tela durante a captura de holograma. |
|  VideoStabilizationEnabled  |  booleano  |  FALSE  |  sinalizador para habilitar ou desabilitar a estabilização de vídeo da plataforma HoloLens tracker. |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Defina quantos quadros históricos são usados para estabilização de vídeo. 0 é a latência e quase "livre" de uma perspectiva de potência e desempenho. 15 é recomendado para a qualidade mais alta (com o custo de 15 quadros de latência e memória). |
|  GlobalOpacityCoefficient  |  FLOAT  |  0,9 (HoloLens) 1,0 (headset de imersão)  |  Defina o coeficiente de opacidade global de holograma no intervalo de 0,0 (totalmente transparente) para 1,0 (totalmente opaco). |
|  BlankOnProtectedContent  |  booleano  |  FALSE  |  Sinalizador para habilitar ou desabilitar o retorno de um quadro vazio se houver um aplicativo UWP 2D mostrando o conteúdo protegido. Se esse sinalizador for false e um aplicativo UWP 2D estiver mostrando o conteúdo protegido, o aplicativo UWP 2D será substituído por uma textura de conteúdo protegida no headset e na captura da realidade misturada. |
|  ShowHiddenMesh  |  booleano  |  FALSE  |  Sinalizador para habilitar ou desabilitar mostrando a malha da área oculta da câmera Holographic e o conteúdo vizinho. |
| Sobrecolocações | Tamanho | 0, 0 | Defina o tamanho de saída desejado após o corte para estabilização de vídeo. Um tamanho de corte padrão será escolhido se 0 ou um tamanho de saída inválido for especificado. |
| PreferredHologramPerspective | UINT32 | **renderizar da** configuração da câmera no Portal do dispositivo Windows | Enum usado para indicar qual configuração de exibição de câmera Holographic deve ser capturada: 0 (display) significa que o aplicativo não será solicitado a renderizar da câmera de foto/vídeo, 1 (PhotoVideoCamera) solicitará que o aplicativo seja renderizado da câmera de foto/vídeo (se o aplicativo oferecer suporte a ele). somente com suporte no HoloLens 2 |

>[!NOTE]
> você pode alterar o valor padrão de **PreferredHologramPerspective** no Portal do dispositivo Windows acessando a [página de captura da realidade misturada](using-the-windows-device-portal.md#mixed-reality-capture) e desmarcando **renderizar da câmera**. A configuração padrão é **1 (PhotoVideoCamera)**, mas pode ser desmarcada para defini-la como **0 (exibição)**.
>
> o valor padrão de **PreferredHologramPerspective** era **0 (Display)** antes da atualização de junho de 2020 (Windows Holographic, versão 2004 build 19041,1106 e Windows Holographic, versão 1903 build 18362,1064).

Efeito de áudio da MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureAudioEffect**)

| Nome da Propriedade | Type | Valor padrão | Descrição |
|----------|----------|----------|----------|
| Mixermode | UINT32 | 2 (MIC e áudio do sistema) | Enum usado para indicar quais fontes de áudio devem ser usadas: 0 (somente áudio do MIC), 1 (somente áudio do sistema), 2 (áudio do sistema e MIC) |
| LoopbackGain | FLOAT | configuração de **aproveitamento de áudio do aplicativo** no Portal do dispositivo Windows | Obter para aplicar ao volume de áudio do sistema. Varia de 0,0 a 5,0. somente com suporte no HoloLens 2 |
| MicrophoneGain | FLOAT | **Configuração ganho de** áudio de microfone no Windows Portal de Dispositivos | Obtenha a aplicação ao volume de microfone. Varia de 0,0 a 5,0. Com suporte apenas no HoloLens 2 |

>[!NOTE]
> Você pode alterar o valor padrão **de LoopbackGain** ou **MicrophoneGain** no Windows Portal de Dispositivos indo para a página [Captura de Realidade Misturada e](using-the-windows-device-portal.md#mixed-reality-capture) ajustando o controle deslizante ao lado de suas respectivas configurações. Ambas as configurações assumem **como padrão 1.0**, mas podem ser definidas como qualquer valor entre **0,0** e **5.0**.
>
> O Windows Portal de Dispositivos para configurar os valores de ganho padrão foi adicionado com a atualização de junho de 2020 (Windows Holographic, versão 2004 build 19041.1106 e Windows Holographic, versão 1903 build 18362.1064).

### <a name="simultaneous-mrc-limitations"></a>Limitações simultâneas do MRC

Você precisa estar ciente de determinadas limitações quando vários aplicativos estão acessando o MRC ao mesmo tempo.

#### <a name="photovideo-camera-access"></a>Acesso à câmera de foto/vídeo

No HoloLens 1, o MRC não capturará uma foto ou capturará um vídeo enquanto um processo estiver gravando um vídeo ou tirar uma foto. O inverso também é verdadeiro: se o MRC estiver em execução, o aplicativo não obterá acesso à câmera. 

Com HoloLens 2, é possível compartilhar o acesso à câmera. Se você não precisar de controle direto da resolução ou da taxa de quadros, poderá inicializar MediaCapture usando a propriedade [SharedMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) com SharedReadOnly.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>Acesso interno à câmera de foto/vídeo do MRC

Funcionalidade do MRC criada em Windows 10 (por Cortana, Menu Iniciar, atalhos de hardware, Miracast, Windows Portal de Dispositivos):

* Será executado com ExclusiveControl por padrão

No entanto, foi adicionado suporte ao subsistema MRC para operar em um modo compartilhado: 

* Se um aplicativo solicitar acesso ExclusiveControl à câmera de foto/vídeo, o MRC interno interromperá automaticamente o uso da câmera de foto/vídeo para que a solicitação do aplicativo seja bem-sucedida 
* Se o MRC integrado for iniciado enquanto um aplicativo tiver ExclusiveControl, o MRC integrado será executado no modo SharedReadOnly 

Essa funcionalidade de modo compartilhado tem determinadas restrições:

* Foto por Cortana, atalhos de hardware ou Menu Iniciar: requer a atualização Windows 10 de abril de 2018 (ou posterior)
* Vídeo por Cortana, atalhos de hardware ou Menu Iniciar: requer a atualização Windows 10 de abril de 2018 (ou posterior)
* Streaming do MRC Miracast: requer o Atualização de outubro de 2018 para o Windows 10 (ou posterior)
* Streaming do MRC Windows Portal de Dispositivos ou por meio do aplicativo HoloLens: requer HoloLens 2

>[!NOTE]
> A resolução e a taxa de quadros da interface do usuário da câmera MRC integrado podem ser reduzidas de seus valores normais quando outro aplicativo estiver usando a câmera de foto/vídeo.

#### <a name="mrc-access-for-developers"></a>Acesso ao MRC para desenvolvedores

Recomendamos que você sempre solicite controle exclusivo para a câmera ao usar o MRC. Isso garantirá que seu aplicativo tenha controle total das configurações da câmera, desde que você esteja ciente das limitações listadas acima. 

* Criar um objeto de captura de mídia usando as [configurações de inicialização](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)
* Definir a [propriedade SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) como **exclusiva**

> [!CAUTION]
> Leia atentamente os comentários [de SharingMode antes](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) de continuar.

* Configurar sua câmera da maneira que você deseja
* Inicie o aplicativo, capture quadros de vídeo com a API inicial e habilita o MRC

> [!CAUTION]
> Se você iniciar o MRC antes de iniciar seu aplicativo, não podemos garantir que o recurso funcionará conforme o esperado.

Você pode encontrar uma amostra completa do processo acima no [exemplo de acompanhamento facial holográfico](/samples/microsoft/windows-universal-samples/holographicfacetracking).

> [!NOTE]
> Antes da atualização de Windows 10 de abril de 2018, o gravador personalizado do MRC de um aplicativo era mutuamente exclusivo com o MRC do sistema (capturando fotos, capturando vídeos ou transmitindo do Windows Portal de Dispositivos).

## <a name="see-also"></a>Confira também

* [Captura de realidade mista](/hololens/holographic-photos-and-videos)
* [Modo de exibição Espectador](spectator-view.md)
* [Visão geral do desenvolvimento do Unity](../unity/unity-development-overview.md)
* [Visão geral do desenvolvimento do Unreal](../unreal/unreal-development-overview.md)
