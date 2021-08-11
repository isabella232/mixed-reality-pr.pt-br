---
title: Estudo de caso – Usando o plano de estabilização
description: Explore como nossa equipe de desenvolvimento usou o plano de estabilização para reduzir a desigualdade holográfica em um aplicativo de realidade misturada.
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, estabilização, estudo de caso, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 4227be39c18e43ad712a14dd61217994a8fc761f41f9416b95b511be5396712a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202344"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Estudo de caso – Usar o plano de estabilização para reduzir a estabilização holográfica

Trabalhar com hologramas geralmente é complicado. Mover-se em torno de um espaço e olhar hologramas de todos os diferentes ângulos fornece um nível de imersão que não está disponível em uma tela normal do computador. Manter esses hologramas no lugar e parecer realista é um aspecto técnico realizado pelo hardware Microsoft HoloLens e pelo design inteligente de aplicativos holográficos.

## <a name="the-tech"></a>A tecnologia

Para fazer os hologramas parece que estão compartilhando o espaço com você, eles devem renderizar corretamente sem separação de cores. Isso é feito, em parte, pela tecnologia integrado ao hardware HoloLens, que mantém os hologramas ancorados no que chamamos de plano [de estabilização](hologram-stability.md#reprojection).

Um plano é definido por um ponto e um normal. Como sempre queremos que o plano de frente para a câmera, estamos preocupados em definir o ponto do plano. Podemos dizer HoloLens em que ponto concentrar seu processamento para manter tudo ancorado e estável. No entanto, definir esse ponto de foco é específico do aplicativo e pode fazer ou quebrar seu aplicativo dependendo do conteúdo.

Hologramas funcionar melhor quando o plano de estabilização é aplicado corretamente, mas o que isso realmente significa depende do tipo de aplicativo que você está criando. Vamos dar uma olhada em como alguns dos aplicativos disponíveis atualmente para HoloLens resolver esse problema.

## <a name="behind-the-scenes"></a>Nos bastidores

Ao desenvolver os aplicativos a seguir, notamos que, quando não usamos o plano, os objetos seriam movidos quando nossa cabeça fosse movida. Também veríamos a separação de cores com movimentos rápidos de cabeça ou holograma. Acabamos aprendendo por meio de avaliação e erro como usar melhor o plano de estabilização e projetar nossos aplicativos em torno dos problemas que ele não pode corrigir.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: conteúdo estacionário, interatividade 3D

[O Galaxy Explorer](../unity/galaxy-explorer.md) tem dois elementos principais na cena: a exibição principal do conteúdo do grupo e a pequena barra de ferramentas da interface do usuário que segue seu foco. Para a lógica de estabilização, vamos ver com o que o vetor de olhar atual intersecções em cada quadro para determinar se ele atinge algo em uma camada de colisão especificada. Nesse caso, as camadas nas qual estamos interessados são os planetas, portanto, se o seu olhar se enquadrar em um planeta, o plano de estabilização será colocado lá. Se nenhum dos objetos na camada de colisão de destino for atingido, o aplicativo usará uma camada secundária de "plano B". Se nada estiver sendo analisado, o plano de estabilização será mantido na mesma distância que estava ao olhar para o conteúdo. As ferramentas de interface do usuário são deixadas de fora como um destino de plano, pois descobrimos que o salto entre quase e muito reduziu a estabilidade da cena geral.

O design do Galaxy Explorer se presta a manter as coisas estáveis e reduzir o efeito da separação de cores. O usuário é incentivado a dar uma volta e cercar o conteúdo em vez de movê-lo de um lado para outro, e os planetas estão em uma distância lenta o suficiente para que a separação de cores não seja perceptível. Além disso, uma constante de 60 FPS é mantida, o que vai muito longe para impedir que a separação de cores ocorra.

Para conferir isso por conta própria, procure um arquivo chamado LSRPlaneModifier.cs no código [do Galaxy Explorer no GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: conteúdo estacionário com um foco de interface do usuário

No HoloStudio, você passa a maior parte do tempo olhando para o mesmo modelo em que está trabalhando. Seu olhar não move uma quantidade significativa, exceto quando você seleciona uma nova ferramenta ou deseja navegar na interface do usuário, para que possamos manter a lógica de configuração do plano simples. Ao olhar para a interface do usuário, o plano é definido como qualquer elemento de interface do usuário ao qual o olhar se encaixa. Ao olhar para o modelo, o plano é uma distância definida, correspondente à distância padrão entre você e o modelo.

![O plano de estabilização visualizado HoloStudio enquanto o usuário se volta para o botão Página Início](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour e Visualizador 3D: conteúdo estacionário com animação e filmes

No HoloTour e Visualizador 3D, você está vendo um objeto animado ou filme animado com efeitos 3D adicionados sobre ele. A estabilização nesses aplicativos é definida como o que você está exibindo no momento.

O HoloTour também impede que você se desvie muito do seu mundo virtual, fazendo com que ele se mova com você em vez de permanecer em um local fixo. Isso garante que você não vá longe o suficiente de outros hologramas para problemas de estabilidade a fim de entrar.

![Neste exemplo do HoloTour, o plano de estabilização seria definido como este filme do Pantheon de Had holograma.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: conteúdo dinâmico e interações ambientais

Definir o plano de estabilização no RoboRaid é surpreendentemente simples, apesar de ser o aplicativo que requer o movimento mais repentino. O plano é voltado para ficar nas paredes ou nos objetos ao redor e vai flutuar a uma distância fixa na sua frente quando você estiver longe o suficiente.

O RoboRaid foi projetado com o plano de estabilização em mente. O reticle, que mais se move, uma vez que está com a cabeça bloqueada, contorna isso usando apenas vermelho e azul, o que minimiza qualquer coloração. Ele também contém um pouco de profundidade entre as partes, minimizando qualquer ressarquite de cor que ocorreria mascarando-o com um efeito paralax já esperado. Os robô não se movem rapidamente e só percorrem distâncias curtas em intervalos regulares. Eles tendem a permanecer cerca de 2 metros na sua frente, em que a estabilização é definida por padrão.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Fragments e Young Conker: conteúdo dinâmico com interação ambiental

Escrito pelo Asobo Studio em C++, Fragments e Young Conker têm uma abordagem diferente para definir o plano de estabilização. Os pontos de interesse (POI) são definidos no código e ordenados por prioridade. OS POIs são conteúdo no jogo, como o modelo do Conker no Young Conker, menus, o aticle de adução e logotipos. As POIs são intersecções pelo olhar do usuário e o plano é definido como o centro do objeto com a prioridade mais alta. Se nenhuma interseção ocorrer, o plano será definido como a distância padrão.

Fragments e Young Conker também projetam você se desviando muito dos hologramas pausando o aplicativo se você sair do que foi verificado anteriormente como seu espaço de reprodução. Assim, eles mantêm você dentro dos limites encontrados para fornecer a experiência mais estável.

## <a name="do-it-yourself"></a>Faça você mesmo

Se você tiver uma HoloLens e quiser experimentar os conceitos deste artigo, poderá baixar uma cena de teste para experimentar os exercícios a seguir. A cena de teste usa a API de gizmo interna do Unity para ajudá-lo a visualizar onde o plano está sendo definido. O código também foi usado para capturar as capturas de tela neste estudo de caso.
1. Sincronize a versão mais recente [do MixedRealityToolkit-Unity.](https://github.com/Microsoft/MixedRealityToolkit-Unity)
2. Abra a [cena HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity.](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)
3. Crie e configure o projeto gerado.
4. Execute em seu dispositivo.

### <a name="exercise-1"></a>Exercício 1

Você verá vários pontos em branco ao seu redor em orientações diferentes. Na frente de você, você verá três pontos em profundidades diferentes. Toque de ar para alterar para qual ponto o plano está definido. Para este exercício e para os outros dois, mova-se em torno de seu espaço enquanto está olhando para os pontos. Gire a cabeça para a esquerda, para a direita, para cima e para baixo. Mova-se para mais perto e para mais longe dos pontos. Veja como eles reagem quando o plano de estabilização é definido como destinos diferentes.

### <a name="exercise-2"></a>Exercício 2

Agora, gire à direita até ver dois pontos móveis, um em um caminho horizontal e outro em um caminho vertical. Mais uma vez, toque no ar para alterar para qual ponto o plano está definido. Observe como a separação de cores é menor e aparece no ponto que está conectado ao plano. Toque novamente para usar a velocidade do ponto na função de configuração do plano. Esse parâmetro fornece uma dica para HoloLens sobre o movimento pretendido do objeto. É importante saber quando usar isso, como você observará quando a velocidade for usada em um ponto, o outro ponto móvel mostrará maior separação de cores. Tenha isso em mente ao projetar seus aplicativos– ter um fluxo coeso para o movimento de seus objetos pode ajudar a impedir que artefatos apareçam.

### <a name="exercise-3"></a>Exercício 3

Voltar para a direita mais uma vez até ver uma nova configuração de pontos. Nesse caso, há pontos na distância e um ponto que entra e sai na frente deles. Toque de ar para alterar para qual ponto o plano está definido, alternando entre os pontos na parte traseira e o ponto em movimento. Observe como definir a posição do plano e a velocidade para a do ponto de descomando faz com que os artefatos apareçam em todos os lugares.

**Dicas**
* Mantenha a lógica de configuração do plano simples. Como você viu, você não precisa de algoritmos de configuração de plano complexo para criar uma experiência imersiva. O plano de estabilização é apenas uma parte do quebra-cabeça.
* Quando possível, sempre mova o plano entre destinos sem problemas. Alternar destinos distantes instantaneamente pode interromper visualmente a cena.
* Considere ter uma opção na lógica de configuração do plano para bloquear em um destino específico. Dessa forma, você pode ter o plano bloqueado em um objeto, como um logotipo ou tela de título, se necessário.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>Engenheiro de Software @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Confira também
* [Noções básicas do MR 100: introdução ao Unity](../unity/tutorials/holograms-100.md)
* [Ponto de foco no Unity](../unity/focus-point-in-unity.md)
* [Estabilidade do holograma](hologram-stability.md)
