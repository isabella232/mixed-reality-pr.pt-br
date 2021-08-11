---
title: Texto no Unity
description: 'Para exibir texto no Unity, há dois tipos de componentes de texto que você pode usar: Texto da interface do usuário e Malha de Texto 3D.'
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, design, Controles, fonte, tipografia, interface do usuário, experiência do usuário, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, MRTK, Toolkit
ms.openlocfilehash: 3e5f296e9526e62bde7d03a0fee7847f4664e4a67187fcda1e66e22aa03053b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207914"
---
# <a name="text-in-unity"></a>Texto no Unity

O texto é um dos componentes mais importantes em aplicativos holográficos. Para exibir texto no Unity, há três tipos de componentes de texto que você pode usar– Texto da Interface do Usuário, Malha de Texto 3D e Malha de Texto Pro. Por padrão, o Texto da Interface do Usuário e a Malha de Texto 3D aparecem desfocados e são muito grandes. A alteração de algumas variáveis resulta em texto mais inteligente e de maior qualidade com um tamanho gerenciável em HoloLens. Você pode obter melhor qualidade de renderização aplicando um fator de dimensionamento para obter dimensões adequadas ao usar os componentes de Texto da Interface do Usuário e Malha de Texto 3D.

![Como obter texto inteligente e belo](images/hug-text-02-640px.png)<br>
*Texto padrão desfocado no Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Trabalhando com texto 3D do Unity (malha de texto) e texto da interface do usuário

O Unity presume que todos os novos elementos adicionados a uma cena são uma Unidade do Unity de tamanho ou escala de transformação de 100%. Uma unidade do Unity é traduzida para cerca de 1 medidor HoloLens. Para fontes, a caixa delimitada para um TextMesh 3D entra por padrão com cerca de 1 medidor de altura.

![Trabalhando com fontes no Unity](images/640px-hug-text-03.png)<br>
*O Texto 3D padrão do Unity (Malha de Texto) ocupa uma Unidade do Unity, que é de 1 medidor*

<br>

A maioria dos designers visuais usa pontos para definir tamanhos de fonte no mundo real. Há cerca de 2835 (2.834,645666399962) pontos em 1 medidor. Com base na conversão do sistema de pontos em 1 medidor e no tamanho padrão da fonte da Malha de Texto do Unity de 13, a matemática simples de 13 dividida por 2835 é igual a 0,0046 (0,0045861111116 para ser exato), que fornece uma boa escala padrão para começar (algumas podem querer arredondá-lo para 0,005). Dimensionar o objeto de texto ou contêiner para esses valores não permitirá apenas a conversão 1:1 de tamanhos de fonte em um programa de design, mas também fornece um padrão para que você possa manter a consistência em toda a sua experiência.

![Dimensionamento de valores para o texto 3D do Unity e o texto da interface do usuário](images/Text_In_Unity_Measurements1.png)<br>
*Dimensionamento de valores para o texto 3D do Unity e o texto da interface do usuário*

<br>

![Malha de Texto 3D do Unity com valores otimizados](images/hug-text-05-1000px.png)<br>
*Malha de Texto 3D do Unity com valores otimizados*

<br>

Ao adicionar uma interface do usuário ou um elemento de texto baseado em tela a uma cena, a disparidade de tamanho ainda é maior. As diferenças nos dois tamanhos são cerca de 1000%, o que levaria o fator de escala para componentes de texto baseados na interface do usuário a 0,00046 (0,0004586111116 para ser exato) ou 0,0005 para o valor arredondado.

![Texto da interface do usuário do Unity com valores otimizados](images/hug-text-04-1000px.png)<br>
*Texto da interface do usuário do Unity com valores otimizados*

<br>

>[!NOTE]
>O valor padrão de qualquer fonte pode ser afetado pelo tamanho da textura dessa fonte ou como a fonte foi importada para o Unity. Esses testes foram executados com base na fonte Arial padrão no Unity, bem como em outra fonte importada.

## <a name="working-with-text-mesh-pro"></a>Trabalhando com a malha de texto Pro

Com a malha de texto do Unity Pro, você pode proteger a qualidade da renderização de texto. Ele dá suporte a contornos de texto nítido, independentemente da distância usando a técnica [de SDF (Campo](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) de Distância Assinada). Usando o mesmo método de cálculo que usamos acima para a Malha de Texto 3D e o Texto da Interface do Usuário, podemos encontrar os valores de dimensionamento adequados para usar com pontos tipográficos convencionais. Como a fonte de Pro da Malha de Texto 3D padrão com o tamanho de 36 tem um tamanho delimitar de 2,5 unidades do Unity (2,5 m), podemos usar um valor de dimensionamento de 0,005 para obter o tamanho do ponto. A malha de texto Pro no menu da interface do usuário tem um tamanho delimitativo padrão de 25 unidades do Unity (25 m). Isso nos dá 0,0005 para o valor de dimensionamento.

![Dimensionamento de valores para o texto e a interface do usuário do Unity 3D](images/Text_In_Unity_Measurements2.png)<br>
*Dimensionamento de valores para o texto e a interface do usuário do Unity 3D*

## <a name="recommended-text-size"></a>Tamanho de texto recomendado

Como você pode esperar, os tamanhos de tipo que usamos em um computador ou em um dispositivo de tablet (normalmente entre 12 e 32pt) parecem pequenos a uma distância de 2 metros. Depende das características de cada fonte, mas, em geral, o ângulo de exibição mínimo recomendado e a altura da fonte para legibilidade são cerca de 0,35°-0,4°/12,21-13,97 mm com base em nossos estudos de pesquisa de usuário. É cerca de 35 a 40 pt com o fator de dimensionamento introduzido acima.

Para a interação próxima a 0,45 m (45 cm), o ângulo de exibição mínimo da fonte legível e a altura são 0,4°-0,5° / 3,14-3,9mm. É cerca de 9 a 12 pt com o fator de dimensionamento introduzido acima.

![Intervalo de interação próximo e distante ](images/typography-distance-1000px.jpg)
 *Conteúdo no intervalo de interação próximo e distante*

### <a name="the-minimum-legible-font-size"></a>O tamanho mínimo da fonte legível

| Distância | Ângulo de exibição | Altura do texto | Tamanho da fonte |
|---------|---------|---------|---------|
| 45 cm (distância de manipulação direta) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12.21-13.97mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>O tamanho da fonte legível com legível

| Distância | Ângulo de exibição | Altura do texto | Tamanho da fonte |
|---------|---------|---------|---------|
| 45 cm (distância de manipulação direta) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20.9-26.2 mm | 59.4-74.2 pt |

Segoe UI (a fonte padrão para Windows) funciona bem na maioria dos casos. No entanto, evite usar famílias de fontes claras ou semi-claras em tamanho pequeno, pois traços verticais finos vão vibrar e isso prejudicará a legibilidade. Fontes modernas com espessura de traço suficiente funcionam bem. Por exemplo, Helvetica e Arial parecem desalojadas e são legíveis HoloLens pesos regulares ou negritos.

![Exibindo a ](images/Text_In_Unity_ViewingAngle.jpg)
 *distância de exibição de ângulo, ângulo e altura do texto*

## <a name="text-with-mixed-reality-toolkit-v2"></a>Texto com realidade misturada Toolkit v2

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Qualidade de renderização de texto nítido com dimensão adequada

Com base nesses fatores de dimensionamento, criamos pré-fabs de texto com Texto da Interface do Usuário e Malha [de Texto 3D.](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text) Os desenvolvedores podem usar esses pré-requisitos para obter texto inteligente e tamanho de fonte consistente.

![Qualidade de renderização de texto nítido com dimensão adequada](images/hug-text-06-1000px.png)<br>
*Qualidade de renderização de texto nítido com dimensão adequada*

### <a name="shader-with-occlusion-support"></a>Sombreador com suporte para oclusão

O material de fonte padrão do Unity não dá suporte à oclusão. Por isso, você verá o texto por trás dos objetos por padrão. Incluímos um sombreador simples [que dá suporte à oclusão](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader). A imagem abaixo mostra o texto com o material de fonte padrão (esquerda) e o texto com oclusão apropriada (direita).

![Sombreador com suporte para oclusão](images/hug-text-07-1000px.png)<br>
*Sombreador com suporte para oclusão*

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Entrada de voz](voice-input-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Confira também

* [Pré-fab de texto no MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [Tipografia](../../design/typography.md)
