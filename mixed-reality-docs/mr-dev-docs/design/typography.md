---
title: Tipografia
description: Saiba como projetar e implementar texto como um elemento importante para fornecer informações em sua experiência de aplicativo de realidade misturada.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, design, estilo, fonte, tipografia, interface do usuário, experiência do usuário, texto, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens
ms.openlocfilehash: 7df2386f3478c0b0b79d198a3342bc9a9a061f6e5a305baedcd91be9c2f09f04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200264"
---
# <a name="typography"></a>Tipografia

![Exemplo de tipografia em HoloLens](images/typography-cover.png)<br>


O texto é um elemento importante para fornecer informações em sua experiência de aplicativo. Assim como a tipografia em telas 2D, a meta é ser claro e legível. Com o aspecto tridimensional da realidade misturada, há uma oportunidade de afetar o texto e a experiência geral do usuário de uma maneira ainda maior.

Quando falamos sobre o tipo em 3D, tendemos a pensar em texto 3D volumoso e extrudido. Com exceção de alguns designs de tipo de logotipo e alguns outros aplicativos limitados, o texto extrudido tende a degradar a capacidade de leitura do texto. Embora estamos projetando experiências para 3D, usamos 2D para o tipo porque é mais legível e mais fácil de ler.

No HoloLens, o tipo é construído com hologramas usando luz com base no sistema de cores aditivo. Assim como outros hologramas, o tipo pode ser colocado no ambiente real em que ele pode ser bloqueado e observado de qualquer ângulo. O [efeito paralax](https://en.wikipedia.org/wiki/Parallax) entre o tipo e o ambiente também adiciona profundidade à experiência.

## <a name="typography-in-mixed-reality"></a>Tipografia na realidade misturada

As regras tipográficas na realidade misturada não são diferentes de qualquer outro lugar. O texto no mundo físico e no mundo virtual precisa ser legível e legível. O texto pode estar em uma parede ou sobreposto em um objeto físico. Ele pode estar flutuante junto com uma interface do usuário digital. Seja qual for o contexto, aplicamos as mesmas regras tipográficas para leitura e reconhecimento.

### <a name="create-clear-hierarchy"></a>Criar hierarquia clara

Crie contraste e hierarquia usando tamanhos e pesos de tipos diferentes. Definir uma rampa de tipos e segui-la durante toda a experiência do aplicativo fornecerá uma ótima experiência do usuário com hierarquia de informações consistente.

![Exemplos de rampa de tipo](images/typography-ramp-1000px.jpg)<br>
*Defina sua rampa de tipos e siga-a durante toda a experiência do aplicativo*

### <a name="limit-your-fonts"></a>Limitar suas fontes

Evite usar mais de duas famílias de fontes diferentes em um único contexto. Muitas fontes quebrarão a consistência e a consistência de sua experiência e dificultarão o consumo de informações. No HoloLens, como as informações são sobreposição sobre o ambiente físico, o uso de muitos estilos de fonte prejudicará a experiência. Segoe UI é a fonte para todos os designs digitais da Microsoft. Ele é usado consistentemente no shell Windows Mixed Reality dados. Você pode baixar o arquivo Segoe UI fonte da página Windows kit de [ferramentas de design do](/windows/uwp/design-downloads/).

[Mais informações sobre a Segoe UI tipo](/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evitar pesos finos de fonte

Evite usar pesos de fonte claro ou semáforo para tamanhos de tipo abaixo de 42 pt porque traços verticais finos vão vibrar e degradar a legibilidade. Fontes modernas com espessura de traço suficiente funcionam bem. Por exemplo, Helvetica e Arial são legíveis HoloLens pesos regulares ou em negrito.

### <a name="color"></a>Color

No HoloLens, como os hologramas são construídos com um sistema de luz aditivo, o texto em branco é altamente legível. Você pode encontrar exemplos de texto em branco na menu Iniciar e na barra aplicativo. Embora o texto em branco funcione bem sem uma placa HoloLens, um plano de fundo físico complexo pode dificultar a leitura do tipo. É recomendável usar texto em branco em uma placa traseira escura ou colorida para melhorar o foco do usuário e minimizar a distração de um plano de fundo físico.

<br>


![É recomendável usar texto em branco em uma placa traseira escura ou colorida. ](images/typography-whiteonblack2-1000px.jpg)
 *Exemplos de texto em branco em uma placa traseira escura ou colorida.*
<br>

Para usar texto escuro, você deve usar uma placa de fundo brilhante para torná-lo acessível. Em sistemas de cores aditiva, preto é exibido como transparente. Isso significa que você não verá o texto preto sem uma placa de fundo colorida.

:::row:::
    :::column:::
        ![Exemplos de branco em preto e preto em texto em branco](images/typography-whiteonblack.png)<br>
        *Exemplos de branco em preto e preto em texto em branco*<br>
    :::column-end:::
    :::column:::
        ![Exemplos de texto preto nos aplicativos do sistema – Store e Configurações](images/640px-typography-blackonwhite.jpg)<br>
        *Exemplos de texto preto nos aplicativos do sistema – Store e Configurações*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>Tamanho recomendado da fonte

Como você pode esperar, os tamanhos de tipo que usamos em um computador ou em um dispositivo de tablet (normalmente entre 12 e 32pt) parecem pequenos a uma distância de 2 metros. Depende das características de cada fonte, mas, em geral, o ângulo de exibição mínimo recomendado e a altura da fonte para legibilidade são cerca de 0,35°-0,4°/12,21-13,97 mm com base em nossos estudos de pesquisa de usuário. É cerca de 35 a 40 pt com o fator de dimensionamento introduzido na [página Texto no Unity.](../develop/unity/text-in-unity.md) 

Para a interação próxima a 0,45 m(45 cm), o ângulo de exibição mínimo da fonte legível e a altura são 0,4°-0,5° / 3,14 a 3,9mm. É cerca de 9 a 12 pt com o fator de dimensionamento introduzido em [Texto no Unity.](../develop/unity/text-in-unity.md)

![Intervalo de interação próximo e distante ](images/typography-distance-1000px.jpg)
 *Conteúdo no intervalo de interação próximo e distante*

### <a name="the-minimum-legible-font-size"></a>O tamanho mínimo da fonte legível

| Distância | Ângulo de exibição | Altura do texto | Tamanho da fonte** |
|---------|---------|---------|---------|
| 45 cm (distância de manipulação direta) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12.21-13.97mm | 34.63-39.58 pt |

### <a name="the-comfortably-legible-font-size"></a>O tamanho da fonte legível com legível

| Distância | Ângulo de exibição | Altura do texto | Tamanho da fonte** |
|---------|---------|---------|---------|
| 45 cm (distância de manipulação direta) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20.9-26.2 mm | 59.4-74.2 pt |


Segoe UI (a fonte padrão para Windows) funciona bem na maioria dos casos. Evite usar famílias de fontes claras ou semi-claras em tamanho pequeno, pois traços verticais finos vão vibrar e isso prejudicará a legibilidade. Fontes modernas com espessura de traço suficiente funcionam bem. Por exemplo, Helvetica e Arial parecem desalojadas e são legíveis HoloLens pesos regulares ou negritos.

**Para obter informações mais detalhadas sobre o cálculo de tamanho de texto no Unity, consulte [Texto no Unity](../develop/unity/text-in-unity.md)**

![Exibindo a ](images/Text_In_Unity_ViewingAngle.jpg)
 *distância de exibição de ângulo, ângulo e altura do texto*

<br>

---

## <a name="resources"></a>Recursos

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Fontes Segoe](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (Arquivo Zip)<br>
    ### <a name="hololens-fontbr"></a>[HoloLens fonte](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (Arquivo Zip)<br>
    <br>
    *Imagem: a HoloLens fonte fornece os glifos de símbolo usados Windows Mixed Reality.*
    :::column-end:::
        :::column:::
        ![A HoloLens fonte fornece os glifos de símbolo usados em Windows Mixed Reality](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>Confira também

* [Texto no Unity](../develop/unity/text-in-unity.md)
* [Cor, luz e materiais](./color-light-and-materials.md)