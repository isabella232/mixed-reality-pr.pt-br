---
title: Foco com a cabeça e confirmação
description: Comece a usar o olhar e confirme o modelo de entrada, incluindo dimensionamento, posicionamento e estabilização de destino.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: realidade misturada, olhar, direcionamento de olhar, interação, design, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, destino, foco, suavização
ms.openlocfilehash: 641e403df23b2559429ca80aa06f384c4845ee347518adca2cfde1b3dbe874dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223646"
---
# <a name="head-gaze-and-commit"></a>Foco com a cabeça e confirmação

_Head-olhar e commit_ é um caso especial do modelo de entrada [olhar e commit](gaze-and-commit.md) que envolve o direcionamento de um objeto com uma direção de cabeçalho de usuários. Você pode agir no destino com uma entrada secundária, como o comando de voz do gesto de toque de mão ou "selecionar". 

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Foco com a cabeça e confirmação</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</td>
        <td>➕ Opção alternativa</td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demonstração dos conceitos de design de rastreamento da cabeça e dos olhos

Se quiser ver os conceitos de design de rastreamento da cabeça e dos olhos em ação, confira abaixo nosso vídeo de demonstração do **Projetando hologramas - Rastreamento da cabeça e rastreamento dos olhos**. Depois de assistir ao vídeo, prossiga para saber mais sobre os tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

## <a name="target-sizing-and-feedback"></a>Dimensionamento e comentários sobre o alvo

O vetor olhar de cabeçalho foi mostrado repetidamente para ser usado para direcionamento fino, mas geralmente funciona melhor para direcionamento bruto, adquirindo destinos maiores. Os tamanhos de destino mínimos de 1 grau a 1,5 graus permitem ações de usuário bem-sucedidas na maioria dos cenários, embora os destinos de 3 graus geralmente permitam maior velocidade. O tamanho que o usuário tem como destino é efetivamente uma área 2D mesmo para elementos 3D – qualquer projeção que esteja voltado para eles deve ser a área de destino. Fornecer uma indicação evidente de que um elemento é "ativo" (que o usuário está direcionando para ele) é útil. Isso pode incluir tratamentos como efeitos "focalizar" visíveis, realces ou cliques de áudio ou alinhamento claro de um cursor com um elemento.

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho de destino ideal em distância de 2 metros*

<br>

![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-940px.jpg)<br>
*Um exemplo de realce de um objeto direcionado por foco*

## <a name="target-placement"></a>Posicionamento do alvo

Geralmente, os usuários não conseguem localizar elementos da interface do usuário localizados muito altos ou baixos em seu campo de exibição. A maioria das suas atenções acaba com as áreas em torno do foco principal, que é aproximadamente no nível dos olhos. O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar. Considerando a tendência para os usuários se concentrarem em uma área Visual relativamente pequena a qualquer momento (o cone de atenção de visão é de aproximadamente 10 graus), agrupar elementos da interface do usuário em conjunto com o grau relacionado conceitualmente pode usar comportamentos de encadeamento de atenção do item para o item, uma vez que um usuário move sua olhar por uma área. Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.

![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*

## <a name="improving-targeting-behaviors&quot;></a>Como melhorar os comportamentos de direcionamento

Se a intenção do usuário de direcionar algo puder ser determinada ou aproximada, pode ser útil aceitar tentativas de interação quase ausentes como se elas estivessem corretas corretamente. Aqui estão alguns métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:

### <a name=&quot;head-gaze-stabilization-gravity-wells&quot;></a>Estabilização do foco com a cabeça (&quot;poços gravitacionais")

Isso deve ser ativado na maior parte das vezes. Essa técnica remove a cabeça natural e as tremulações do pescoço que os usuários podem ter também movimento por causa de comportamentos de aparência e fala.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo mais próximo

Esses algoritmos funcionam melhor em áreas com conteúdo interativo esparso. Se houver uma alta probabilidade de que você possa determinar o que um usuário estava tentando interagir, você pode complementar seus recursos de direcionamento assumindo algum nível de intenção.

### <a name="backdating-and-postdating-actions"></a>Ações de backencontros e de reencontros

Esse mecanismo é útil para tarefas que exigem velocidade. Quando um usuário está passando por uma série de manobras de direcionamento e ativação em velocidade, é útil assumir alguma intenção. Também é útil permitir que etapas perdidas atuem em destinos que o usuário tinha em foco um pouco antes ou ligeiramente após o toque (50 ms antes/depois era efetivo no teste inicial).

### <a name="smoothing"></a>Suavização

Esse mecanismo é útil para a trajetória de movimentos, reduzindo a ligeira tremulação e Wobbles devido a características de movimento de cabeçalho natural. Ao suavizar movimentos de caminho, Smooth pelo tamanho e distância dos movimentos em vez de ao longo do tempo.

### <a name="magnetism"></a>Magnetismo

Esse mecanismo pode ser considerado como uma versão mais comum dos algoritmos de link mais próximos, desenhando um cursor em direção a um destino ou simplesmente aumentando hitboxes, seja visivelmente ou não, à medida que os usuários abordam os alvos prováveis usando algum conhecimento do layout interativo para melhorar melhor a intenção do usuário. Isso pode ser poderoso para destinos pequenos.

### <a name="focus-stickiness"></a>Adesão do foco

Ao determinar quais elementos interativos adjacentes fornecem, concentre-se, a adesão do foco fornece uma tendência para o elemento que está atualmente focado. Isso ajuda a reduzir os comportamentos incorretos de alternância de foco ao flutuar em um ponto médio entre dois elementos com ruído natural.

## <a name="see-also"></a>Confira também

* [Interação ocular](eye-gaze-interaction.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)