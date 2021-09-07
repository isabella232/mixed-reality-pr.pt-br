---
title: Bloqueios mundiais e âncoras espaciais no Unity
description: Saiba como usar as ferramentas de bloqueio mundial e âncoras espaciais em aplicativos de realidade misturada no Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity, âncoras espaciais, repositório de ancoragem, HoloLens, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, ferramentas de bloqueio mundial, hologramas
ms.openlocfilehash: 1de3571d0ad43308acad459021f2c2e9a1a6e1e7
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244308"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Bloqueios mundiais e âncoras espaciais no Unity

![Imagem do herói das ferramentas de bloqueio mundial](images/wlt-img-01.jpeg)

Fazer com que seus hologramas permaneçam em vigor, mover-se para você ou, em alguns casos, posicioná-los em relação a outros hologramas é uma grande parte da criação de aplicativos de realidade misturada. Este artigo o guiará pela solução recomendada usando as ferramentas de bloqueio mundial, mas também abordaremos a configuração manual das âncoras espaciais em seus projetos do Unity. Antes de passarmos por qualquer código, é importante entender como o Unity lida com o espaço de coordenadas e as âncoras em seu próprio mecanismo.

## <a name="world-scale-coordinate-systems"></a>Sistemas de coordenadas de escala mundial

Hoje em dia, ao escrever jogos, aplicativos de visualização de dados ou aplicativos de realidade virtual, a abordagem típica é estabelecer um **sistema de coordenadas do mundo** absoluto que todas as outras coordenadas possam Mapear de forma confiável de volta para o. Nesse ambiente, você sempre pode encontrar uma transformação estável que define uma relação entre quaisquer dois objetos nesse mundo. Se você não moveu esses objetos, suas transformações relativas sempre permanecerão as mesmas. Esse tipo de sistema de coordenadas global é fácil de ser adequado ao renderizar um mundo puramente virtual em que você conhece toda a geometria com antecedência. Atualmente, os aplicativos VR em escala de sala normalmente estabelecem esse tipo de sistema de coordenadas de escala de sala absoluto com sua origem no chão.

por outro lado, um dispositivo de realidade misturada sem compartilhamento de internet, como o HoloLens, tem uma compreensão dinâmica orientada por sensor do mundo, ajustando continuamente seu conhecimento ao longo do tempo do ambiente do usuário à medida que eles orientam muitos medidores em todo um andar de um edifício. Em uma experiência de escala mundial, se você colocou todos os seus hologramas em um sistema de coordenadas rígidos ingênuas, esses hologramas acabarão se esgotando ao longo do tempo, seja com base no mundo ou em relação uns aos outros.

Por exemplo, o headset pode acreditar, no momento, que dois locais do mundo tenham 4 metros de distância e depois refinam essa compreensão, aprendendo que os locais estão na verdade 3,9 metros de distância. Se esses hologramas tiverem sido inicialmente colocados quatro metros de distância em um único sistema de coordenadas rígidos, um deles sempre pareceria de 0,1 metros do mundo real.

Você pode colocar manualmente **âncoras espaciais** no Unity para manter a posição de um holograma no mundo físico quando o usuário é móvel, mas isso sacrifica a autoconsistência no mundo virtual. Âncoras diferentes estão constantemente mudando em relação umas às outras e também estão passando pelo espaço de coordenadas global. Nesse cenário, tarefas simples, como layout, tornam-se difíceis e problemas de simulação de física.

As **ferramentas de bloqueio mundial** oferecem o melhor dos dois mundos, estabilizando um único sistema de coordenadas rígidos usando um fornecimento interno de âncoras espaciais espalhados por toda a cena virtual à medida que o usuário se movimenta. As ferramentas analisam as coordenadas da câmera e as âncoras espaciais a cada quadro. Em vez de alterar as coordenadas de tudo no mundo para compensar as correções nas coordenadas do cabeçalho do usuário, as ferramentas simplesmente corrigem as coordenadas da cabeça.

## <a name="choosing-your-world-locking-approach"></a>Escolhendo sua abordagem de bloqueio mundial

* Recomendamos que você use **ferramentas de bloqueio mundial** para todas as suas necessidades de posicionamento de holograma.
    * As ferramentas de bloqueio Mundial fornecem um sistema de coordenadas estável que minimiza as inconsistências visíveis entre marcadores virtuais e do mundo real. Em outras palavras, o mundo de ti bloqueia toda a cena com um pool compartilhado de âncoras, em vez de bloquear cada grupo de objetos com a própria âncora individual do grupo.
    * As ferramentas de bloqueio mundial manipulam automaticamente toda a criação e o gerenciamento de âncoras espaciais internamente. Você não precisa interagir com **ARAnchorManager** ou **WorldAnchor** para manter seus hologramas protegidos pelo mundo.
* **para o Unity 2019/2020 usando OpenXR ou o plug-in Windows XR**, você precisa usar **ARAnchorManager**
* **Para versões mais antigas do Unity ou** projetos de WSA, você precisa usar o **WorldAnchor**

## <a name="setting-up-world-locking"></a>Configurando o bloqueio mundial

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>Bloqueio mundial persistente

Âncoras espaciais salvam hologramas em espaço real entre as sessões do aplicativo. depois de salvo no repositório de ancoragem do HoloLens, eles podem ser encontrados e carregados em diferentes sessões e são um fallback ideal quando não há conectividade com a internet.

> [!IMPORTANT]
> Elas são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem. Se você pretende usar os serviços de nuvem do Azure para armazenar suas âncoras, temos um documento que pode orientar você na integração das [Âncoras Espaciais do Azure](../mixed-reality-cloud-services.md#azure-spatial-anchors). Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>Compartilhando espaços de coordenadas

Se você quiser compartilhar um espaço de coordenadas do mundo bloqueado, Confira nossa [documentação abrangente de experiência compartilhada](shared-experiences-in-unity.md).

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos principais blocos de construção da realidade misturada. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Mapeamento espacial](spatial-mapping-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Consulte Também
* [Introdução às ferramentas de bloqueio mundial](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [Guias de início rápido](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [Tutoriais](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [Amostras](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [Persistência de ancoragem espacial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a>
* [Escalas de experiência](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Estágio espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Como controlar a perda no Unity](tracking-loss-in-unity.md)
* [Âncoras espaciais](../../design/spatial-anchors.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)
