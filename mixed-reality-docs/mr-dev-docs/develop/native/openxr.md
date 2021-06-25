---
title: OpenXR
description: Crie um mecanismo usando o padrão de API do OpenXR portátil e implante-o em headsets Windows Mixed Reality HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, roteiro, extensões, Chronos, BasicXRApp, DirectX, aplicativo nativo, nativo, mecanismo personalizado, middleware
ms.openlocfilehash: 8374cda738cc5b257338728f7d777f546768e71b
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906832"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

O OpenXR é um padrão de API livre de royalties da <a href="https://www.khronos.org/" target="_blank">Kronos,</a>fornecendo aos mecanismos acesso nativo a uma variedade de dispositivos no espectro [de realidade misturada.](../../discover/mixed-reality.md)

Faça o desenvolvimento com o OpenXR em um headset imersivo do HoloLens 2 ou do Windows Mixed Reality na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o Emulador do HoloLens 2 ou o simulador Windows Mixed Reality em vez disso.

## <a name="why-openxr"></a>Por que OpenXR?

Com o OpenXR, você pode criar mecanismos destinados a dispositivos holográficos, como o HoloLens 2, e dispositivos imersivos, como headsets Windows Mixed Reality para computadores desktop. O OpenXR permite escrever código depois que ele é portátil em uma ampla variedade de plataformas de hardware.

A API do OpenXR usa um carregador para conectar seu aplicativo diretamente ao suporte da plataforma nativa do headset. Os usuários finais têm desempenho máximo e latência mínima, independentemente de usarem um Windows Mixed Reality ou qualquer outro headset.

## <a name="what-is-openxr"></a>O que é o OpenXR?

A API do OpenXR fornece a previsão de pose principal, o tempo de quadro e a funcionalidade de entrada espacial que você precisará para criar um mecanismo que possa ser destinado a dispositivos holográficos e imersivos.

Para saber mais sobre a API do OpenXR, confira <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank"></a>a especificação do OpenXR 1.0, a referência de <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API</a>e o <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">guia de referência rápida.</a>  Para obter mais informações, consulte a <a href="https://www.khronos.org/openxr/" target="_blank">página OpenXR do Kronos</a>.

Para direcionar o conjunto de recursos completo do HoloLens 2, você também usará extensões OpenXR específicas de fornecedores e fornecedores que habilitam recursos adicionais além do núcleo do OpenXR 1.0, como acompanhamento de mão articulado, acompanhamento ocular, mapeamento espacial e âncoras espaciais. Para obter mais informações, consulte a [seção Roteiro abaixo](#roadmap) sobre as extensões que virão mais adiante neste ano.

O OpenXR não é um mecanismo de realidade misturada.  Em vez disso, o OpenXR permite que mecanismos como Unity e Unreal escrevam código portátil uma vez que possa acessar os recursos da plataforma nativa do dispositivo holográfico ou imersivo do usuário, seja qual for o fornecedor que criou essa plataforma.

## <a name="roadmap"></a>Roteiro

A especificação OpenXR define um mecanismo de extensão que permite que [](#what-is-openxr) os implementadores de runtime exponham funcionalidades adicionais além dos principais recursos definidos na <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação base do OpenXR 1.0</a>.

Há três tipos de extensões OpenXR:
* **Extensões de fornecedor (por exemplo, `MSFT` ): permite** a inovação por fornecedor em recursos de hardware ou software.  Qualquer fornecedor de runtime pode introduzir e enviar uma extensão de fornecedor a qualquer momento.
  * **Extensões de fornecedor experimental (por exemplo, `MSFT_preview` ): extensões** de fornecedor experimental que estão sendo visualizadas para coletar comentários.  `MSFT_preview` as extensões são apenas para dispositivos de desenvolvedor e serão removidas quando a extensão real for adada.  Para experimentá-las, você pode [habilitar extensões de visualização em seu dispositivo de desenvolvedor.](openxr-getting-started.md#using-preview-extensions)
* **Extensões entre `EXT` fornecedores: extensões** entre fornecedores que várias empresas definem e implementam.  Grupos de empresas interessadas podem introduzir extensões EXT a qualquer momento.
* **Extensões `KHR` oficiais: extensões** Oficiais doKhronos verificados como parte de uma versão de especificação principal.  As extensões de KHR são cobertas pela mesma licença que a especificação principal em si.

O Windows Mixed Reality OpenXR Runtime dá suporte a um conjunto de extensões e que traz o conjunto completo de recursos do `MSFT` `EXT` HoloLens 2 para aplicativos OpenXR:

| Área do recurso | Disponibilidade da extensão |
|--------------|------------------------|
| Sistemas + sessões | **Especificação principal do OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Espaços de referência (exibição, local, estágio)](../../design/coordinate-systems.md) | **Especificação principal do OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Exibir configurações (mono, estéreo) | **Especificação principal do OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Swapchains](../platform-capabilities-and-apis/rendering.md)  +  [tempo do quadro](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **Especificação principal do OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Camadas de composição<br />(projeção, quad) | **Especificação principal do OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Entrada e tics](../../design/interaction-fundamentals.md) | **Especificação principal do OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integração do Direct3D 11 | **Extensão `KHR` oficial lançada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Integração do Direct3D 12 | **Extensão `KHR` oficial lançada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Espaço de referência nãobounded <br /> (experiências de escala mundial)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` extensão liberada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Âncoras espaciais](../../design/spatial-anchors.md) | **`MSFT` extensão liberada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [Interação com a <br /> mão (posição da mão/posição do alvo, toque de ar, compreensão)](../../design/hands-and-tools.md)<p>*Somente HoloLens 2*</p> | **`MSFT` extensão liberada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Articulação da mão + malha de mão](../../design/hands-and-tools.md)<p>*Somente HoloLens 2*</p> | <p>**`EXT` extensão lançada no runtime 102:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` extensão lançada no runtime 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Foco com o olhar](../../design/eye-tracking.md)<p>*Somente HoloLens 2*</p> | **`EXT` extensão liberada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| Interop com outros SDKs do HoloLens<br />(por exemplo, [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*Somente HoloLens 2*</p> | <p>**`MSFT` extensão lançada no runtime 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` extensão no runtime 105:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| [Captura de Realidade Misturada <br /> (terceira renderização da câmera PV)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*Somente HoloLens 2*</p> | **`MSFT` extensões lançadas no runtime 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interop com a API do UWP CoreWindow<br />(por exemplo, para teclado/mouse) | **`MSFT` extensão lançada no runtime 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Perfis de interação do controlador de movimento<br />(SamsungSeyy e HP Reverb G2) | **`MSFT` extensões lançadas no runtime 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Modelos de renderização do controlador de movimento](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` extensão lançada no runtime 104:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Compreensão da cena (planos, malhas)](../../design/scene-understanding.md)<p>*Somente HoloLens 2*</p> | <p>**A partir do runtime 102:**<br />Usar <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> com o [SDK de Compreensão de Cena](../platform-capabilities-and-apis/scene-understanding-sdk.md)</p><p>**`MSFT`extensão no [runtime de visualização 105:](openxr-getting-started.md#using-preview-extensions)**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_preview2">XR_MSFT_scene_understanding_preview2</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_serialization_preview">XR_MSFT_scene_understanding_serialization_preview</a></code></p> |
| [Modos de reprojeção da camada de composição (reprojeção somente de orientação ou <br /> planar automaticamente)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT`extensão no [runtime de visualização 105:](openxr-getting-started.md#using-preview-extensions)**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_composition_layer_reprojection_preview">XR_MSFT_composition_layer_reprojection_preview</a></code> |
| Outras extensões entre fornecedores | <p>**Extensões `KHR` oficiais lançadas:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code><p>**`EXT` extensões lançadas:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

Embora algumas dessas extensões possam começar como extensões específicas do fornecedor, a Microsoft e outros fornecedores de runtime do OpenXR estão trabalhando juntos para criar extensões entre fornecedores para muitas dessas áreas de `MSFT` `EXT` `KHR` recurso. Extensões entre fornecedores tornarão o código que você escreve para esses recursos portátil entre fornecedores de runtime, como com a especificação principal.

## <a name="getting-started-with-openxr"></a>Introdução ao OpenXR

![Captura de tela do Minecraft sendo interpretado por um usuário usando um headset de realidade misturada](images/openxr-minecraft.jpg)

*O novo mecanismo RenderDragon do Minecraft criou seu suporte à VR da área de trabalho usando o OpenXR!*

A Microsoft vem trabalhando com o Unity e a Epic Games para garantir que o futuro da realidade misturada seja aberto, não apenas para o HoloLens 2, mas em toda a amplitude do VR do PC, incluindo o novo [headset Reverb G2](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)da HP.  O OpenXR alimenta o suporte à VR entre fornecedores para o envio de títulos principais hoje, como o Simulador de Voo da Microsoft e o Minecraft!  Para obter mais informações sobre como desenvolver para o HoloLens (1ª geração), consulte as notas [de versão](/hololens/hololens1-release-notes).

Para saber como você pode começar a usar o OpenXR no Unity, no Unreal Engine ou em seu próprio mecanismo, continue lendo!

### <a name="openxr-in-unity"></a>OpenXR no Unity

Atualmente, o caminho de desenvolvimento do Unity com suporte para HoloLens 2, HoloLens (1ª geração) e headsets Windows Mixed Reality é **Unity 2019 LTS** com o back-back da API winRT existente.  Você pode ir para [o OpenXR com o Unity;](../unity/xr-project-setup.md) Se você estiver direcionando para o novo controlador HP Reverb G2 em um aplicativo Unity 2019, consulte nossos documentos de entrada do [HP Reverb G2](../unity/unity-reverb-g2-controllers.md).

A partir **do Unity 2020 LTS,** o Unity envia um [back-back do OpenXR](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) que dá suporte ao HoloLens 2 e Windows Mixed Reality headsets.  Isso inclui suporte para as extensões OpenXR que abrem os recursos completos dos headsets do [HoloLens 2 e Windows Mixed Reality](#roadmap), incluindo acompanhamento de mãos/olhos, âncoras espaciais e controladores HP Reverb G2.  MRTK-Unity dá suporte ao OpenXR a partir do [MRTK 2.7.](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)  Para obter mais informações sobre o status atual do suporte do Unity 2020 LTS para HoloLens 2, consulte [Escolhendo uma versão do Unity.](../unity/choosing-unity-version.md)

A partir **do Unity 2021,** o OpenXR será o único back-end do Unity com suporte para direcionar o HoloLens 2 e Windows Mixed Reality headsets.

### <a name="openxr-in-unreal-engine"></a>OpenXR no Unreal Engine

A partir **do Unreal Engine 4.23,** o suporte completo para headsets holoLens 2 e Windows Mixed Reality está disponível por meio do plug-in Windows Mixed Reality (WinRT).

O Unreal Engine 4.23 também foi a primeira versão principal do mecanismo de jogos a enviar suporte à versão prévia para OpenXR 1.0!  Agora, no **Unreal Engine 4.26,** o suporte para HoloLens 2, Windows Mixed Reality e outros headsets de VR da área de trabalho está disponível por meio do suporte integrado ao OpenXR do Unreal Engine.  O Unreal Engine 4.26 também dá suporte ao plug-in de extensão [OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal)da Microsoft, habilitando a interação manual e o suporte ao controlador HP Reverb G2, ativando o conjunto completo de recursos do [HoloLens 2 e Windows Mixed Reality headsets](#roadmap).  O Unreal Engine 4.26 está disponível hoje no [Epic Games Launcher,](https://www.unrealengine.com/download/creators)com suporte MRTK-Unreal em abril.


### <a name="openxr-for-native-development"></a>OpenXR para desenvolvimento nativo

Faça o desenvolvimento com o OpenXR em um headset imersivo do HoloLens 2 ou do Windows Mixed Reality na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o Emulador do HoloLens 2 ou o simulador Windows Mixed Reality em vez disso.

Para começar a desenvolver aplicativos OpenXR para HoloLens 2 ou headsets Windows Mixed Reality imersivos, confira como começar a desenvolver [o OpenXR.](openxr-getting-started.md)

Para um tour por todos os principais componentes da API do OpenXR, juntamente com exemplos dos aplicativos do mundo real que usam o OpenXR hoje, confira este vídeo passo a passo de 60 minutos:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Confira também

* <a href="https://www.khronos.org/openxr/" target="_blank">Mais informações sobre o OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificação do OpenXR 1.0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referência da API do OpenXR 1.0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guia de referência rápida do OpenXR 1.0</a>