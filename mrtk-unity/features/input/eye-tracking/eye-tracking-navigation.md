---
title: Navegação de acompanhamento ocular
description: Como usar o alvo dos olhos para navegação no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: e1ca34054a019e26bebf14282cd351467e5c65e2c2c3fa4f35647dd5aba680ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197096"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Navegação com suporte de olho no MRTK

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Imagine você estiver lendo informações em um slate e quando chegar ao final do texto exibido, o texto rolará automaticamente para revelar mais conteúdo. Ou você pode aplicar um zoom fluente no local em que está olhando. O mapa também ajusta automaticamente o conteúdo para manter as coisas de interesse em seu campo de exibição. Outro aplicativo interessante é a observação sem intervenções de hologramas 3D ao trazer automaticamente as partes do holograma que você está olhando para a frente. Estes são alguns dos exemplos descritos nesta página no contexto de navegação com suporte de olho.

As descrições a seguir pressupõem que você já esteja familiarizado com a maneira de [Configurar o acompanhamento de olho em sua cena do MRTK](eye-tracking-basic-setup.md) e com as noções básicas de como [acessar dados de controle de olho](eye-tracking-target-selection.md) no MRTK Unity.
Os exemplos abordados a seguir fazem parte da `EyeTrackingDemo-03-Navigation` cena (ativos/MRTK/exemplos/demos/EyeTracking/cenas/EyeTrackingDemo-03-navegação).

**Resumo:** Rolagem automática de texto, olhar com suporte para panorâmica e zoom de um mapa virtual, rotação de 3D direcionada para olhar-hands.

## <a name="auto-scroll"></a>Rolagem automática

A rolagem automática permite que o usuário Role pelos textos sem levantar um dedo.
Basta continuar lendo e o texto será automaticamente rolado para cima ou para baixo dependendo de onde o usuário estiver olhando.
Você pode começar com o exemplo fornecido em `EyeTrackingDemo-03-Navigation` (ativos/MRTK/exemplos/demos/EyeTracking/cenas).
Este exemplo usa um componente [textmesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) para permitir o carregamento e a formatação de novo texto de maneira flexível.
Para habilitar a rolagem automática, basta adicionar os dois scripts a seguir ao componente colisor da caixa de texto:

### <a name="scrollrecttransf"></a>ScrollRectTransf

Para percorrer uma [textmesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) ou mais falando em um componente [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) , você pode usar o script [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) .
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
UseSkimProofing | Se habilitada, ela impede movimentos de rolagem repentinas ao olhar rapidamente. No entanto, isso pode fazer com que a rolagem fique menos responsiva. Ele pode ser ajustado com o valor *SkimProofUpdateSpeed* .
SkimProofUpdateSpeed | Quanto menor o valor, mais lenta a rolagem será acelerada após espiada. Valor recomendado: 5.

![Configuração de rolagem com suporte de olho no Unity](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

A anexação do componente _EyeTrackingTarget_ permite a manipulação de eventos relacionados ao olhar de olho de maneira flexível.
O exemplo de rolagem demonstra o texto de rolagem que começa quando o usuário *examina* o painel e para quando o usuário está *olhando para fora* dele.
![Configuração de rolagem com suporte de olho no Unity: EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Olhar-panorâmica e zoom com suporte

Who não usou um mapa virtual antes de pesquisar sua residência ou para explorar os locais totalmente novos? O controle de olho permite que você se aprofunde diretamente nas partes em que está interessado e, uma vez ampliado, você pode acompanhar suavemente o curso de uma rua para explorar sua vizinhança!
Isso não só é útil para explorar mapas geográficos, mas também para fazer o check-out de detalhes em fotografias, visualizações de dados ou até mesmo imagens médicas em fluxo dinâmico. Para usar esse recurso em seu aplicativo é fácil! Para o conteúdo renderizado para uma [textura]( https://docs.unity3d.com/ScriptReference/Texture.html) (por exemplo, uma foto, dados transmitidos), basta adicionar o script [PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) .
Para um [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) , use [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf). Estendendo o recurso de [rolagem automática](#auto-scroll) , essencialmente habilitamos a rolagem vertical e horizontal ao mesmo tempo e aumentamos o conteúdo ao lado do ponto de foco atual do usuário.

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
Pan_Speed_y | Se definido como um valor diferente de zero, a rolagem vertical será habilitada. Valores negativos significam uma alteração na direção da rolagem: até baixo versus baixo para cima.
Pan_MinDistFromCenter | Distância mínima normalizada em x e y do centro da caixa de visita do destino (0, 0) para rolar. Portanto, os valores devem variar entre 0 (sempre rolar) e 0,5 (sem rolagem).
UseSkimProofing | Se habilitada, ela impede movimentos de rolagem repentinas ao olhar rapidamente. No entanto, isso pode fazer com que a rolagem fique menos responsiva. Ele pode ser ajustado com o valor *SkimProofUpdateSpeed* .
SkimProofUpdateSpeed | Quanto menor o valor, mais lenta a rolagem será acelerada após espiada. Valor recomendado: 5.

![Configuração de panorâmica e zoom com suporte de olho no Unity](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Rotação 3D com base na atenção

Imagine examinando um objeto 3d e as partes que você deseja ver de forma mágica mais detalhadamente, como se o sistema pudesse ler sua ideia e saber como transformar o item em sua direção!
Essa é a ideia para rotações 3D com base em atenção que permitem investigar todo o lado de um holograma sem levantar um dedo.
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
MinRotX | Ângulo de rotação horizontal mínimo. Isso é para limitar a rotação em direções diferentes.
MaxRotX | Ângulo de rotação horizontal máximo. Isso é para limitar a rotação em direções diferentes.
MinRotY | Ângulo de rotação vertical mínimo para limitar a rotação em torno do eixo x.
MaxRotY | Ângulo de rotação vertical máximo para limitar a rotação em torno do eixo y.

![Configuração de rotação 3D com suporte de olho no Unity](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

Em resumo, os scripts acima devem permitir que você comece a usar os olhos olhar para várias tarefas de navegação de entrada, como textos de rolagem, zoom e texturas panorâmicas, bem como os hologramas 3D de investigação giratória.

### <a name="see-also"></a>Confira também

- [Configuração básica do MRTK para usar o acompanhamento de olho](eye-tracking-basic-setup.md)
- [Seleção de destino com suporte de olho](eye-tracking-target-selection.md)

---
[Voltar para "acompanhamento de olho no MixedRealityToolkit"](eye-tracking-main.md)
