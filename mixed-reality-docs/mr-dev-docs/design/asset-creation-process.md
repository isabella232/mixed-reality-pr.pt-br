---
title: Processo de criação do ativo
description: Saiba como criar, comprar e portar ativos para experiências de realidade misturada.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: ativo, criação, processo, orçamento, polígonos, texturas, sombreadores, desempenho, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, ativos
ms.openlocfilehash: a5f4271de522111b0ef994869b9ecf4910582562
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009609"
---
# <a name="asset-creation-process"></a>Processo de criação do ativo

O Windows Mixed Reality se baseia em décadas de investimento que a Microsoft fez no DirectX. Toda a experiência e os desenvolvedores de habilidades com a criação de gráficos 3D continuam a ser valiosos com o HoloLens.

Os ativos que você cria para um projeto vêm em muitas formas e formulários. Eles podem ser compostos por uma série de texturas/imagens, áudio, vídeo, modelos 3D e animações. Não podemos começar a abordar todas as ferramentas disponíveis para criar os diferentes tipos de ativos usados em um projeto. Neste artigo, nos concentraremos nos métodos de criação de ativos 3D.

![Conceito, criação, integração e fluxo de iteração](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*O conceito, a criação, a integração e o fluxo de iteração*

## <a name="things-to-consider"></a>Itens a serem considerados

Ao examinar a experiência, você está tentando criar, imagine-a como um **orçamento** que pode ser gasto para tentar criar a melhor experiência. Não há necessariamente nenhum limite rígido no número de **polígonos** ou **tipos de material** que você pode usar em seus ativos. Considere isso mais como um conjunto orçado de compensações.

Veja abaixo um orçamento de exemplo para sua experiência. O desempenho não é um ponto único de falha, mas a morte de mil cortes.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Ativos</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Memória</th>
</tr><tr>
<td> Polígonos</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> Texturas</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> Sombreadores</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Física</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> Iluminação em tempo real</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> Mídia (áudio/vídeo)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> Script/lógica</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> Sobrecarga geral</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>Total</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Número total de ativos**
* Quantos ativos estão ativos na cena?

**Complexidade dos ativos**
* Quantos triângulos/polígonos?
* Quão complexo é o sombreador? Ao usar o kit de ferramentas de realidade misturada, é recomendável usar o [sombreador standard do kit de ferramentas do reality](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) para reduzir a complexidade do sombreador.

Os desenvolvedores e os artistas precisam considerar os recursos do dispositivo e o mecanismo de gráficos. O Microsoft HoloLens tem todo o cálculo e os gráficos incorporados ao dispositivo. Ele compartilha os recursos que os desenvolvedores encontraria em uma plataforma móvel.

O processo de criação de ativos é o mesmo se sua experiência tiver como alvo um [dispositivo Holographic ou um dispositivo de imersão](../discover/mixed-reality.md#the-mixed-reality-spectrum). A coisa principal a ser observada é a capacidade e a escala do dispositivo. Você pode ver o mundo real em realidade misturada, portanto, convém manter a escala correta com base na experiência.

## <a name="authoring-assets"></a>Criando ativos

Vamos começar com as maneiras de obter ativos para seu projeto:
1. Criando ativos (ferramentas de criação e captura de objeto)
2. Comprando ativos (comprando ativos online)
3. Portando ativos (obtendo ativos existentes)
4. Terceirizar ativos (importando ativos de terceiros)

### <a name="creating-assets"></a>Criando ativos

**Ferramentas de criação**<br>
Primeiro, você pode criar seus próprios ativos de várias maneiras diferentes. os artistas 3D usam vários aplicativos e ferramentas para criar modelos, que consistem em **malhas**, **texturas** e **materiais**. Isso é salvo em um formato de arquivo que pode ser importado ou usado pelo mecanismo de gráficos usado pelo aplicativo, como **. FBX** ou **. OBJ**. Qualquer ferramenta que gera um modelo que o mecanismo gráfico escolhido suporta funcionará no **HoloLens**. Entre artistas 3D, muitos optam por usar o [Maya do Autodesk porque ele pode usar o HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar a maneira como os ativos são criados. Se você quiser obter algo em rápido, também poderá usar o [Construtor 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) que vem com o Windows para exportar. OBJ para uso em seu aplicativo.

**Captura de objeto**<br>
Também há a opção de capturar objetos em 3D. Capturar objetos inanimados em 3D e editá-los com o software de criação de conteúdo digital é cada vez mais popular com o aumento da impressão 3D. Usando o sensor **Kinect 2** e o [Construtor 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) , você pode usar o recurso de captura para criar ativos de objetos do mundo real. Esse também é um [conjunto de ferramentas](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) para fazer o mesmo com **Photogrammetry** processando várias imagens para unir e malhar e texturas.

### <a name="purchasing-assets"></a>Comprando ativos

Outra opção excelente é comprar ativos para sua experiência. Há uma infinidade de ativos disponíveis por meio de serviços como o [repositório de ativos de Unity](https://www.assetstore.unity3d.com/) ou o [TurboSquid](https://www.turbosquid.com/) entre outros.

Ao comprar ativos de terceiros, você sempre deseja verificar as seguintes propriedades:
* **O que é o número de polylines?**
  * Ele se encaixa em seu orçamento?
* **Há níveis de detalhes (LODs) para o modelo?**
  * Um nível de detalhe dos modelos permite que você dimensione os detalhes de um modelo para o desempenho.
* **O arquivo de origem está disponível?**
  * Não incluído no [repositório de ativos do Unity](https://www.assetstore.unity3d.com/) , mas sempre incluído com serviços como [TurboSquid](https://www.turbosquid.com/).
  * Sem o arquivo de origem, você não pode modificar o ativo.
  * Verifique se o arquivo de origem fornecido pode ser importado por suas ferramentas 3D.
* **Saiba o que você está obtendo**
  * As animações são fornecidas?
  * Certifique-se de verificar a lista de conteúdo do ativo que você está comprando.

### <a name="porting-assets"></a>Portando ativos

Em alguns casos, você receberá ativos existentes que foram originalmente criados para outros dispositivos e aplicativos diferentes. Na maioria dos casos, esses ativos podem ser convertidos em formatos compatíveis com o mecanismo de gráficos que seu aplicativo está usando.

Ao portar ativos para uso em seu aplicativo do HoloLens, você deverá fazer as seguintes perguntas:
* **Você pode importar diretamente ou precisa ser convertido em outro formato?** Verifique o formato que você está importando com o mecanismo de gráficos que você está usando.
* **Se a conversão em um formato compatível for algo perdido?** Às vezes, os detalhes podem ser perdidos ou a importação pode causar artefatos que precisam ser limpos em uma ferramenta de criação 3D.
* **Qual é a contagem de triângulos/polígonos para o ativo?** Com base no orçamento para seu aplicativo, você pode usar [Simplygon](https://www.simplygon.com/) ou ferramentas semelhantes para DECIMATE (de forma manual ou reduzir a contagem de Polyline) o ativo original para se ajustar ao seu orçamento de aplicativos.

### <a name="outsourcing-assets"></a>Ativos de terceirização

Outra opção para projetos maiores que exigem mais ativos do que sua equipe está equipada para criar é terceirizar a criação de ativos. O processo de terceirização envolve encontrar o estúdio ou a Agência certa que é especializada em ativos de terceirização. Essa pode ser a opção mais cara, mas também a mais flexível no que você obtém.
* **Defina claramente o que você está solicitando**
  * Forneça o máximo de detalhes possível
  * Imagens de conceito frontal, lateral e de volta
  * Arte de referência mostrando o ativo no contexto
  * Escala de objeto (geralmente especificada em centímetros)
* **Fornecer um orçamento**
  * Intervalo de contagem de Polyline
  * Número de texturas
  * Tipo de sombreador (para Unity e HoloLens, você deve sempre padrão para sombreadores móveis primeiro)
* **Entender os custos**
  * Qual é a política de terceirização para solicitações de alteração?

A terceirização pode funcionar bem com base na linha do tempo de seus projetos, mas requer mais supervisão para garantir que você obtenha os ativos certos de que precisa na primeira vez.
