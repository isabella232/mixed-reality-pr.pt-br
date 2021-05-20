---
title: Navegação de acompanhamento ocular
description: Como usar o direcionamento ocular para navegação no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: d966bbe1d3a256e55c62532e8101c1f2846e1136
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145277"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Navegação com suporte ocular no MRTK

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Imagine que você está lendo informações sobre um slate e, quando chegar ao final do texto exibido, o texto rolará automaticamente para cima para revelar mais conteúdo. Ou você pode ampliar fluentemente onde está olhando. O mapa também ajusta automaticamente o conteúdo para manter as coisas de interesse dentro do seu campo de exibição. Outro aplicativo interessante é a observação prática de hologramas 3D, levando automaticamente as partes do holograma que você está observando para a frente. Estes são alguns dos exemplos descritos nesta página no contexto de navegação com suporte ocular.

As descrições a seguir pressuem que você já está familiarizado com como configurar [](eye-tracking-target-selection.md) o acompanhamento ocular em sua cena do [MRTK](eye-tracking-basic-setup.md) e com as noções básicas de acesso a dados de acompanhamento ocular no MRTK Unity.
Os exemplos discutidos a seguir fazem parte da cena `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes/EyeTrackingDemo-03-Navigation).

**Resumo:** Rolagem automática de texto, painel com suporte ao foco com o olhar e zoom de um mapa virtual, rotação 3D direcionada ao foco sem mãos.

## <a name="auto-scroll"></a>Rolagem automática

A rolagem automática permite que o usuário role textos sem deslizar um dedo.
Basta continuar lendo e o texto rolará para cima ou para baixo automaticamente, dependendo de onde o usuário está procurando.
Você pode começar com o exemplo fornecido em `EyeTrackingDemo-03-Navigation` (Ativos/MRTK/Exemplos/Demonstrações/EyeTracking/Scenes).
Este exemplo usa um [componente TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) para permitir carregamento flexível e formatação de novo texto.
Para habilitar a rolagem automática, basta adicionar os dois scripts a seguir ao componente colisor da caixa de texto:

### <a name="scrollrecttransf"></a>ScrollRectTransf

Para percorrer um [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) ou, de modo geral, um [componente RectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html) você pode usar o script [ScrollRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)
Se você quiser percorrer uma textura em vez de uma [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html), use [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) em vez de [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf).
A seguir, os parâmetros de [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) que estão disponíveis no editor do Unity são explicados em mais detalhes:

Parâmetros | Descrição
:---- | :----
LimitPanning | Se habilitada, interromperá o conteúdo rolável em seu limite.
RectTransfToNavigate | Referência ao [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) para rolar.
RefToViewport | Referência ao [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) pai do conteúdo rolável para determinar o deslocamento e o limite corretos.
AutoGazeScrollIsActive | Se habilitada, o texto rolará automaticamente se o usuário olhar para uma *região ativa* (por exemplo, a parte superior e inferior do painel de rolagem se a velocidade da rolagem vertical não for zero).
ScrollSpeed_x | Se definido como um valor diferente de zero, a rolagem horizontal será habilitada. Valores negativos significam uma alteração na direção da rolagem: da esquerda para a direita versus da direita para a esquerda.
ScrollSpeed_y | Se definido como um valor diferente de zero, a rolagem vertical será habilitada. Valores negativos significam uma alteração na direção da rolagem: até baixo versus baixo para cima.
MinDistFromCenterForAutoScroll | Distância mínima normalizada em x e y do centro da caixa de visita do destino (0, 0) para rolar. Portanto, os valores devem variar entre 0 (sempre rolar) e 0,5 (sem rolagem).
UseSkimProofing | Se habilitada, ela impede movimentos repentinos de rolagem ao olhar rapidamente ao redor. No entanto, isso pode fazer com que a rolagem se sinta menos responsiva. Ele pode ser ajustado com o *valor SkimProofUpdateSpeed.*
SkimProofUpdateSpeed | Quanto menor o valor, mais lenta será a velocidade da rolagem após o derrapagem. Valor recomendado: 5.

![Configuração de rolagem com suporte ocular no Unity](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

Anexar o _componente EyeTrackingTarget_ permite eventos relacionados ao olhar com alça flexível.
O exemplo de rolagem demonstra o  texto de rolagem que começa quando o usuário analisa o painel e para quando o usuário está *olhando para* fora dele.
![Configuração de rolagem com suporte ocular no Unity: EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Panorrama e zoom com suporte para o olhar

Quem não usou um mapa virtual antes para pesquisar sua casa ou explorar locais totalmente novos? O acompanhamento ocular permite que você se adára diretamente nas partes em que está interessado e, uma vez ampliado, você pode seguir sem problemas o curso de uma rua para explorar seu distrito!
Isso não só é útil para explorar mapas geográficos, mas também para verificar detalhes em fotografias, visualizações de dados ou até mesmo imagens médicas transmitidas ao vivo. É fácil usar essa funcionalidade em seu aplicativo! Para o conteúdo renderizado em [uma Textura]( https://docs.unity3d.com/ScriptReference/Texture.html) (por exemplo, uma foto, dados transmitidos), basta adicionar o script [PanZoomTexture.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture)
Para um [RectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html) use [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf). Estendendo [a](#auto-scroll) funcionalidade de Rolagem Automática, essencialmente habilitamos a rolagem vertical e horizontal ao mesmo tempo e ampliar o conteúdo em torno do ponto de foco atual do usuário.

Parâmetros | Descrição
:---- | :----
LimitPanning | Se habilitada, interromperá o conteúdo rolável em seu limite.
HandZoomEnabledOnStartup | Indica se os gestos de mão são habilitados automaticamente para executar um gesto de zoom. Talvez você queira desabilitá-lo primeiro para evitar o disparo acidental de ações de zoom.
RendererOfTextureToBeNavigated | Renderizador referenciado da textura a ser navegada.
Zoom_Acceleration | Aceleração de zoom definindo a acentuação do mapeamento de função de velocidade logística.
Zoom_SpeedMax | Velocidade máxima de zoom.
Zoom_MinScale | Escala mínima da textura para ampliar-por exemplo, 0,5 f (metade do tamanho original).
Zoom_MaxScale | Escala máxima da textura para reduzir-por exemplo, 1F (o tamanho original) ou 2.0 f (o dobro do tamanho original).
Zoom_TimeInSecToZoom | Zoom cronometrado: uma vez disparado, um zoom/saída será realizado durante o período de tempo determinado em segundos.
Zoom_Gesture | Tipo de gesto de mão a ser usado para ampliar/reduzir.
--- | ---
Pan_AutoScrollIsActive | Se habilitada, o texto rolará automaticamente se o usuário olhar para uma *região ativa* (por exemplo, a parte superior e inferior do painel de rolagem se a velocidade da rolagem vertical não for zero).
Pan_Speed_x | Se definido como um valor diferente de zero, a rolagem horizontal será habilitada. Valores negativos significam uma alteração na direção da rolagem: da esquerda para a direita versus da direita para a esquerda.
Pan_Speed_y | Se definido como um valor diferente de zero, a rolagem vertical será habilitada. Valores negativos significam uma alteração na direção da rolagem: para baixo versus para baixo até cima.
Pan_MinDistFromCenter | Distância mínima normalizada em x e y do centro da caixa de acerto do destino (0, 0) para rolar. Portanto, os valores devem variar entre 0 (sempre rolagem) e 0,5 (sem rolagem).
UseSkimProofing | Se habilitada, ela impede movimentos repentinos de rolagem ao olhar rapidamente ao redor. No entanto, isso pode fazer com que a rolagem se sinta menos responsiva. Ele pode ser ajustado com o *valor SkimProofUpdateSpeed.*
SkimProofUpdateSpeed | Quanto menor o valor, mais lenta será a velocidade da rolagem após o derrapagem. Valor recomendado: 5.

![Configuração de panorrama e zoom com suporte ocular no Unity](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Rotação 3D baseada em atenção

Imagine-se olhando para um objeto 3D e as partes que você deseja ver de maneira mais mágica, voltadas para você, como se o sistema tivesse lido sua mente e saiba como transformar o item em sua direção!
Essa é a ideia para rotações 3D baseadas em atenção que permitem investigar todos os lados de um holograma sem a necessidade de apontar um dedo.
Para habilitar esse comportamento, basta adicionar o script [OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) à parte do gameobject com um componente [colisor](https://docs.unity3d.com/ScriptReference/Collider.html) .
Você pode ajustar vários parâmetros listados abaixo para limitar a velocidade e, em que direções o holograma ativará.

Como você pode imaginar, ter esse comportamento ativo em todos os momentos pode rapidamente se tornar muito confuso em uma cena cheia.
É por isso que você talvez queira iniciar com esse comportamento desabilitado e, em seguida, habilitá-lo rapidamente usando comandos de voz.
Como alternativa, adicionamos um exemplo em `EyeTrackingDemo-03-Navigation` (assets/MRTK/examples/demos/EyeTracking/cenas) para usar o [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) para o qual você pode selecionar um destino focado e ele se levanta na frente de você – simplesmente diga *"Venha para mim"*.

Uma vez no modo Near, o modo de rotação automática é habilitado automaticamente.
Nesse modo, você pode observá-lo de todos os lados simplesmente resumindo-o e examinando-o, percorrendo-o ou atingindo-o para pegar e girá-lo com sua mão. Quando você descartar o destino (Olhe & pinçar ou dizer *"enviar de volta"*), ele retornará ao seu local original e deixará de reagir a você do Afar.

Parâmetros | Descrição
:---- | :----
SpeedX | Velocidade de rotação horizontal.
Rápida | Velocidade de rotação vertical.
InverseX | Para inverter a direção da rotação horizontal.
Inverso | Para inverter a direção da rotação vertical.
RotationThreshInDegrees | Se o ângulo entre ' olhar para destino ' e ' câmera para destino ' for menor que esse valor, não faça nada. Isso é para evitar pequenas rotações de tremulação.
MinRotX | Ângulo mínimo de rotação horizontal. Isso é para limitar a rotação em direções diferentes.
MaxRotX | Ângulo máximo de rotação horizontal. Isso é para limitar a rotação em direções diferentes.
MinRotY | Ângulo de rotação vertical mínimo para limitar a rotação ao redor do eixo x.
MaxRotY | Ângulo máximo de rotação vertical para limitar a rotação ao redor do eixo y.

![Configuração de rotação 3D com suporte ocular no Unity](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

Em resumo, os scripts acima devem permitir que você começar a usar o olhar para várias tarefas de navegação de entrada, como rolagem de textos, texturas de zoom e panorâmico, bem como girar investigando hologramas 3D.

### <a name="see-also"></a>Confira também

- [Configuração básica do MRTK para usar o acompanhamento ocular](eye-tracking-basic-setup.md)
- [Seleção de destino com suporte ocular](eye-tracking-target-selection.md)

---
[De volta ao "Acompanhamento ocular no MixedRealityToolkit"](eye-tracking-main.md)
