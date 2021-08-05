---
title: Tabela periódica dos elementos
description: Saiba como estabelecer uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção object com a Tabela Periódica do aplicativo de exemplo Elements.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, aplicativo de exemplo, controles, MRTK, Toolkit de Realidade Misturada, Unity, aplicativos de exemplo, aplicativos de exemplo, open-source, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: aab6789939823b8c6e200bb5456118002b848e3c2f166abe50d4788ac8e7430d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211864"
---
# <a name="periodic-table-of-the-elements"></a>Tabela periódica dos elementos
![Tabela de período do aplicativo Elements](../images/MRDL_PeriodicTable_HL1.jpg)

>[!NOTE]
>Este artigo aborda um exemplo exploratório que criamos nos [Laboratórios](https://github.com/Microsoft/MRDesignLabs_Unity)de Design de Realidade Misturada, um local em que compartilhamos nossos aprendizados e sugestões para o desenvolvimento de aplicativos de realidade misturada. Nossos artigos e código relacionados ao design evoluirão à medida que fazemos novas descobertas.

>[!NOTE]
>Este aplicativo de exemplo foi projetado para HoloLens 1ª geração. Consulte [Tabela periódica dos Elementos 2.0](periodic-table-of-the-elements-2.md) para HoloLens 2.

[A Tabela Periódica dos Elementos é](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) um aplicativo de exemplo de código aberto dos Laboratórios de Design de Realidade Misturada da Microsoft. Saiba como estabelecer uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma **[Coleção de objetos](../../design/object-collection.md)**. Saiba também como criar objetos interagidos que respondem a entradas padrão de HoloLens. Você pode usar os componentes desse projeto para criar sua própria experiência de aplicativo de realidade misturada.


## <a name="demo-video"></a>Vídeo de demonstração 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Gravado com HoloLens 2 usando Captura de Realidade Misturada

## <a name="about-the-app"></a>Sobre o aplicativo

A Tabela Periódica dos Elementos visualiza os elementos quimicos e cada uma de suas propriedades em um espaço 3D. Ele incorpora as interações básicas de HoloLens como o olhar e o toque de ar. Os usuários podem aprender sobre os elementos com modelos 3D animados. Eles podem entender visualmente o shell de electron de um elemento e seus anões , que é composto de protons e anões.

## <a name="background"></a>Tela de fundo

Depois de experimentar a HoloLens, eu sabia que queria experimentar um aplicativo de tabela periódico na realidade misturada. Como cada elemento tem muitos pontos de dados exibidos com texto, eu acho que seria um ótimo assunto explorar a composição tipográfica em um espaço 3D. Dar aos usuários a oportunidade de visualizar o modelo de electron do elemento era outra parte interessante desse projeto.

## <a name="design"></a>Design

Para a exibição padrão da tabela periódica, eu vi caixas tridimensionais que contêm o modelo de electron de cada elemento. A superfície de cada caixa seria translúcida para que o usuário pudesse ter uma ideia aproximada do volume do elemento. Com o olhar e o toque de ar, o usuário pode abrir uma exibição detalhada de cada elemento. Para tornar a transição entre a exibição de tabela e a exibição de detalhes suave e natural, eu a torna semelhante à interação física de uma caixa abrindo na vida real.

![Esboço de design](images/640px-sketch20170406.jpg)<br>
*Esboçar esboços*

Na exibição detalhada, eu queria visualizar as informações de cada elemento com texto renderizado perfeitamente no espaço 3D. O modelo de electron 3D animado é exibido na área central e pode ser exibido de diferentes ângulos.

![Interação](images/640px-periodictable-interaction.jpg)

![Protótipos](images/640px-periodictable-prototypes.jpg)<br>
*Protótipos de interação*

O usuário pode alterar o tipo de superfície tocando ar nos botões na parte inferior da tabela– ele pode alternar entre plano, cilindro, esfera e dispersão.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Controles e padrões comuns usados neste aplicativo

### <a name="interactable-object-button"></a>Objeto interajante (botão)

[O objeto interajante](../../design/interactable-object.md) é um objeto que pode responder a entradas HoloLens básicas. Ele é fornecido como um pré-bb/script, que você pode aplicar facilmente a qualquer objeto. Por exemplo, você pode tornar uma cafeteira em sua cena interagente e responder a entradas como olhar, toque de ar, navegação e gestos de manipulação. [Saiba mais](../../design/interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Coleção de objetos

[A coleção de](../../design/object-collection.md) objetos é um objeto , que ajuda você a estabelecer vários objetos em várias formas. Ele dá suporte a plano, cilindro, esfera e dispersão. Você pode configurar propriedades adicionais, como radius, número de linhas e espaçamento. [Saiba mais](../../design/object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Detalhes técnicos

Você pode encontrar scripts e pré-fabs para a Tabela Periódica do aplicativo Elements nos Laboratórios de Design de [Realidade Misturada GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>História de portação para HoloLens 2

Leia a história sobre como a Tabela Periódica do aplicativo Elements foi atualizada com HoloLens interações instintivas do HoloLens 2.

[Tabela periódica dos elementos 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>Designer de UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Confira também

* [Hub de Exemplos do MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tabela periódica dos elementos 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)