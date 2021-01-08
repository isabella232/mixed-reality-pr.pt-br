---
title: Tabela periódica dos elementos
description: Saiba como dispor uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção de objetos com a tabela periódica do aplicativo de exemplo de elementos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, aplicativo de exemplo, controles, MRTK, kit de ferramentas de realidade misturada, Unity, aplicativos de exemplo, aplicativos de exemplo, software livre, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: fd525b0d41efa15ff55097456fb6b06dd3d60c25
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009356"
---
# <a name="periodic-table-of-the-elements"></a>Tabela periódica dos elementos

>[!NOTE]
>Este artigo discute um exemplo exploratório que criamos nos laboratórios de [design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde compartilhamos nossas aprendeções e sugestões para o desenvolvimento de aplicativos de realidade misturada. Nossos artigos e códigos relacionados ao design irão evoluir à medida que fizermos novas descobertas.

[A tabela periódica dos elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) é um aplicativo de exemplo de código-fonte aberto dos laboratórios de design de realidade misturada da Microsoft. Saiba como dispor uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma **[coleção de objetos](../../design/object-collection.md)**. Saiba também como criar objetos que respondam às entradas padrão do HoloLens. Você pode usar os componentes deste projeto para criar sua própria experiência de aplicativo de realidade misturada.

![Tabela de período do aplicativo de elementos](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>Vídeo de demonstração 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Registrado com o HoloLens 2 usando a captura de realidade misturada

## <a name="about-the-app"></a>Sobre o aplicativo

A tabela periódica dos elementos visualiza os elementos químicos e cada uma de suas propriedades em um espaço 3D. Ele incorpora as interações básicas de HoloLens, como olhar e toque de ar. Os usuários podem aprender sobre os elementos com modelos 3D animados. Eles podem entender visualmente o Shell de um dos elementos do seu núcleo, que é composto de protoneladas e neutrons.

## <a name="background"></a>Tela de fundo

Depois de ter experimentado o HoloLens pela primeira vez, sabia que queria experimentar um aplicativo de tabela periódico em realidade misturada. Como cada elemento tem muitos pontos de dados que são exibidos com texto, pensei que seria um ótimo assunto para explorar a composição tipográfica em um espaço 3D. Dar aos usuários a chance de visualizar o modelo de sem interspersão do elemento era outra parte interessante deste projeto.

## <a name="design"></a>Design

Para a exibição padrão da tabela periódica, Imaginai caixas tridimensionais que conteriam o modelo de todos os elementos. A superfície de cada caixa seria translúcida para que o usuário pudesse obter uma ideia aproximada do volume do elemento. Com o olhar e o toque do Air, o usuário pode abrir uma exibição detalhada de cada elemento. Para fazer com que a transição entre a exibição de tabela e a exibição de detalhes seja suave e natural, eu o fiz de forma semelhante à interação física de uma abertura de caixa na vida real.

![Esboço de design](images/640px-sketch20170406.jpg)<br>
*Esboços de design*

No modo de exibição de detalhes, eu queria visualizar as informações de cada elemento com o texto renderizado linda em espaço 3D. O modelo de rede 3D animada é exibido na área central e pode ser exibido a partir de diferentes ângulos.

![Interação](images/640px-periodictable-interaction.jpg)

![Protótipos](images/640px-periodictable-prototypes.jpg)<br>
*Protótipos de interação*

O usuário pode alterar o tipo de superfície por ar tocando nos botões na parte inferior da tabela-eles podem alternar entre plano, cilindro, esfera e dispersão.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Controles e padrões comuns usados neste aplicativo

### <a name="interactable-object-button"></a>Objeto interagir (botão)

O [objeto de interação](../../design/interactable-object.md) é um objeto, que pode responder às entradas básicas do HoloLens. Ele é fornecido como um pré-fabricado/script, que você pode aplicar facilmente a qualquer objeto. Por exemplo, você pode fazer com que uma xícara de café em sua cena interaja e responda a entradas como olhar, toque de ar, navegação e gestos de manipulação. [Saiba mais](../../design/interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Coleção de objetos

A [coleção de objetos](../../design/object-collection.md) é um objeto, que ajuda você a dispor vários objetos em várias formas. Ele dá suporte a plano, cilindro, esfera e dispersão. Você pode configurar propriedades adicionais, como RADIUS, número de linhas e espaçamento. [Saiba mais](../../design/object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Detalhes técnicos

Você pode encontrar scripts e pré-fabricados para a tabela periódica do aplicativo de elementos no [GitHub de laboratórios de design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>A história do portador para o HoloLens 2

Leia a história sobre como a tabela periódica do aplicativo de elementos foi atualizada com as interações de instinctual do HoloLens 2.

[Tabela periódica dos elementos 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Designer de UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Veja também

* [Hub de Exemplos do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tabela periódica dos elementos 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)