---
title: Configuração da câmera no Unity
description: Saiba como configurar e usar a câmera principal do Unity para o desenvolvimento de realidade mista do Windows para fazer a renderização Holographic.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Holographic Rendering, Holographic, imersão, ponto de foco, buffer de profundidade, somente orientação, posicional, opaco, transparente, clipe, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636238"
---
# <a name="camera-setup-in-unity"></a>Configuração da câmera no Unity

Quando você gasta um headset de realidade misturada, ele se torna o centro do seu Holographic World. O componente da [câmera](https://docs.unity3d.com/Manual/class-Camera.html) do Unity manipulará automaticamente a renderização de estereoscópico e seguirá a rotação e o movimento da cabeça. No entanto, para otimizar totalmente a qualidade visual e a [estabilidade do holograma](../platform-capabilities-and-apis/hologram-stability.md), você deve definir as configurações de câmera descritas abaixo.

## <a name="hololens-vs-vr-immersive-headsets"></a>Fone de ouvido do HoloLens versus VR de imersão

As configurações padrão no componente câmera do Unity são para aplicativos 3D tradicionais, que precisam de um plano de fundo Skybox, pois não têm um mundo real.

* Ao executar em um **[headset de imersão](../../discover/immersive-headset-hardware-details.md)**, você está renderizando tudo o que o usuário vê e, portanto, provavelmente desejará manter o Skybox.
* No entanto, ao executar em um **Headset Holographic** como o [HoloLens](/hololens/hololens2-hardware), o mundo real deve aparecer atrás de tudo que a câmera renderiza. Defina o plano de fundo da câmera como transparente (no HoloLens, o preto é renderizado como transparente) em vez de uma textura Skybox:
    1. Selecione a câmera principal no painel hierarquia
    2. No painel Inspetor, localize o componente câmera e altere a lista suspensa limpar sinalizadores de Skybox para cor sólida
    3. Selecione o seletor de cor do plano de fundo e altere os valores de RGBA para (0, 0, 0, 0)
        1. Se estiver configurando a partir do código, você poderá usar o [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Instalação da câmera

Seja qual for o tipo de experiência que você está desenvolvendo, a câmera principal é sempre o principal componente de renderização estéreo anexado à tela de montagem de cabeçalho do dispositivo. Será mais fácil definir o layout do seu aplicativo se você imaginar a posição inicial do usuário como (X: 0, Y: 0, Z: 0). Como a câmera principal está acompanhando a movimentação do cabeçalho do usuário, a posição inicial do usuário pode ser definida definindo a posição inicial da câmera principal.

A opção central que você precisa fazer é se você está desenvolvendo para headsets de imersão ou VR. Depois de fazer isso, pule para qualquer seção de instalação aplicável.

### <a name="hololens-camera-setup"></a>Instalação da câmera do HoloLens

Para aplicativos do HoloLens, você precisa usar âncoras para todos os objetos que deseja bloquear para o ambiente de cena. É recomendável usar espaço não associado para maximizar a estabilidade e criar âncoras em várias salas.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>Configuração da câmera VR

O Windows Mixed Reality dá suporte a aplicativos em uma ampla variedade de [escalas de experiência](../../design/coordinate-systems.md#mixed-reality-experience-scales), desde aplicativos de dimensionamento e de orientação e escalados até aplicativos em escala de sala. No HoloLens, você pode ir além e criar aplicativos de escala mundial que permitem que os usuários passem além de 5 metros, explorando um andar inteiro de um edifício e além disso.

Sua primeira etapa na criação de uma experiência de realidade mista no Unity é determinar qual [escala de experiência](../../design/coordinate-systems.md) seu aplicativo será direcionada:

* [Orientação ou escala colocada](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [Escala de espaço ou em pé](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [Escala mundial](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Experiência em escala ou em posição de sala

> [!NOTE]
> Se você estiver criando para HL2, é recomendável criar uma experiência de nível de olho ou considerar o uso da [compreensão em cena](../platform-capabilities-and-apis/scene-understanding-sdk.md) em relação ao andar da sua cena.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Experiências enfeitas

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Configurando o plano de fundo da câmera

Se você estiver usando o MRTK, o plano de fundo da câmera será automaticamente configurado e gerenciado. Para projetos do XR SDK ou de WSA herdados, é recomendável definir o plano de fundo da câmera como preto sólido no HoloLens e manter o Skybox para VR.

## <a name="using-multiple-cameras"></a>Usando várias câmeras

Quando há vários componentes de câmera na cena, o Unity sabe qual câmera usar para a renderização estereoscópico com base em qual gameobject tem a marca MainCamera. Em Legacy XR, ele também usa essa marca para o rastreamento de cabeçalho de sincronização. No XR SDK, o acompanhamento de cabeçalho é orientado por um script TrackedPoseDriver anexado à câmera.

## <a name="sharing-depth-buffers"></a>Compartilhamento de buffers de profundidade

Compartilhar o buffer de profundidade do seu aplicativo para o Windows cada quadro dará ao seu aplicativo um dos dois aumentos na estabilidade do holograma, com base no tipo de headset que você está renderizando:

* Os **headsets de imersão de VR** podem cuidar da Reprojeção posicional quando um buffer de profundidade é fornecido, ajustando os hologramas para uma previsão incorreta na posição e na orientação.
* Os **headsets do HoloLens** têm alguns métodos diferentes. O HoloLens 1 selecionará automaticamente um [ponto de foco](focus-point-in-unity.md) quando um buffer de profundidade for fornecido, otimizando a estabilidade do holograma ao longo do plano que intercepta a maior parte do conteúdo. O HoloLens 2 irá estabilizar o conteúdo usando [LSR de profundidade (consulte comentários)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Usando planos de recorte

O processamento de conteúdo muito próximo ao usuário pode ser desconfortável em realidade misturada. Você pode ajustar os [planos de corte próximo e longe](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) no componente da câmera.

1. Selecione a **câmera principal** no painel **hierarquia**
2. No painel **Inspetor** , localize os **planos de recorte** do componente da **câmera** e altere a caixa de texto **próximo** de **0,3** para **0,85**. O conteúdo renderizado ainda mais próximo pode levar ao usuário discomfort e deve ser evitado de acordo com as [diretrizes de distância de renderização](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).

## <a name="recentering-the-camera"></a>Recentralizando a câmera

Se você estiver criando uma [experiência de escala](../../design/coordinate-systems.md)em posição, poderá recentralizar a origem mundial da unidade na posição de cabeçalho atual do usuário chamando o **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** em Legacy XR ou o método **[XRInputSubsystem. TRYRECENTER](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** no XR SDK.

## <a name="teleportation"></a>Portabilidade

Esse recurso é normalmente reservado para experiências de VR:

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Modos de Reprojeção

Os headsets de HoloLens e de imersão reprojetarão cada quadro que seu aplicativo renderiza para se ajustar para qualquer previsão incorreta da posição de cabeçalho real do usuário quando fótons são emitidos.

Por padrão:

* Os **headsets de imersão de VR** se encarregarão da Reprojeção de posição, se o aplicativo fornecer um buffer de profundidade para um determinado quadro. Os headsets de imersão também ajustarão os hologramas para uma previsão incorreta na posição e na orientação. Se um buffer de profundidade não for fornecido, o sistema corrigirá apenas as previsões incorretas na orientação.
* Os **fones de ouvido Holographic** , como o HoloLens 2, cuidam da Reprojeção posicional se o aplicativo fornece seu buffer de profundidade ou não. A Reprojeção posicional é possível sem buffers de profundidade no HoloLens, pois a renderização costuma ser esparsa com um plano de fundo estável fornecido pelo mundo real.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Foco](gaze-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Confira também

* [Estabilidade do holograma](../platform-capabilities-and-apis/hologram-stability.md)
* [Escalas de experiência](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Estágio espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Como controlar a perda no Unity](tracking-loss-in-unity.md)
* [Âncoras espaciais](../../design/spatial-anchors.md)
* [Persistência no Unity](persistence-in-unity.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)
* [Âncoras Espaciais do Azure](/azure/spatial-anchors)
* [SDK de âncoras espaciais do Azure para Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)