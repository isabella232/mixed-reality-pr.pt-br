---
title: Processo de criação do ativo
description: Saiba como criar, comprar e portuar ativos para experiências de realidade misturada.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: asset, creation, process, budget, polygons, textures, shaders, performance, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, mixed reality Toolkit, assets
ms.openlocfilehash: 5c5dcdbe24a8028bb8a3c57e57b9d95079f9e832954d12aa31421dd75f1b6982
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214100"
---
# <a name="asset-creation-process"></a>Processo de criação do ativo

Windows Mixed Reality se baseia nas décadas de investimento que a Microsoft fez no DirectX. Toda a experiência e as habilidades que os desenvolvedores têm com a criação de gráficos 3D continuam sendo valiosas com HoloLens.

Os ativos que você cria para um projeto vêm em várias formas e formulários. Eles podem ser compostos por uma série de texturas/imagens, áudio, vídeo, modelos 3D e animações. Não podemos começar a abranger todas as ferramentas disponíveis para criar os diferentes tipos de ativos usados em um projeto. Para este artigo, vamos nos concentrar nos métodos de criação de ativos 3D.

![Conceito, criação, integração e fluxo de iteração](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Conceito, criação, integração e fluxo de iteração*

## <a name="things-to-consider"></a>Itens a serem considerados

Ao olhar para **a** experiência, você está tentando criar, pense nisso como um orçamento que você pode gastar para tentar criar a melhor experiência. Não há necessariamente limites rígidos no número de **polígonos** ou tipos **de material** que você pode usar em seus ativos. Pense mais nisso como um conjunto orçado de negociações.

Veja abaixo um exemplo de orçamento para sua experiência. O desempenho não é um único ponto de falha, mas a morte por mil reduções.
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
* Qual é a complexidade do sombreador? Ao usar o Toolkit realidade misturada, é recomendável usar o sombreador Toolkit Standard de Realidade Misturada para reduzir [a](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) complexidade do sombreador.

Os desenvolvedores e os criadores têm que considerar os recursos do dispositivo e o mecanismo de elementos gráficos. Microsoft HoloLens tem todos os elementos computacionais e gráficos integrados ao dispositivo. Ele compartilha os recursos que os desenvolvedores encontrariam em uma plataforma móvel.

O processo de criação de ativos é o mesmo se sua experiência tem como destino um [dispositivo holográfico ou um dispositivo imersivo.](../discover/mixed-reality.md#the-mixed-reality-spectrum) O principal a observar é a capacidade e a escala do dispositivo. Você pode ver o mundo real na realidade misturada, portanto, será melhor manter a escala correta com base na experiência.

## <a name="authoring-assets"></a>Ativos de autor

Vamos começar com as maneiras de obter ativos para seu projeto:
1. Criando ativos (ferramentas de criação e captura de objeto)
2. Comprando ativos (compra de ativos online)
3. Portando ativos (pegar ativos existentes)
4. Terceirizando ativos (importando ativos de terceiros)

### <a name="creating-assets"></a>Criando ativos

**Ferramentas de autor**<br>
Primeiro, você pode criar seus próprios ativos de várias maneiras diferentes. Os artista 3D usam vários aplicativos e ferramentas para criar modelos, que consistem em **malhas,** **texturas** e **materiais**. Em seguida, isso é salvo em um formato de arquivo que pode ser importado ou usado pelo mecanismo de elementos gráficos usado pelo aplicativo, como **. FBX** ou **. OBJ**. Qualquer ferramenta que gere um modelo compatível com o mecanismo gráfico escolhido funcionará no **HoloLens**. Entre os artista 3D, muitos optam por usar o Maya da [Autodesk](https://www.youtube.com/watch?v=q0K3n0Gf8mA) porque ele pode usar HoloLens transformar a maneira como os ativos são criados. Se você quiser obter algo rapidamente, também poderá usar 3D Builder [que](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) vem com Windows para exportar . OBJ para uso em seu aplicativo.

**Captura de objeto**<br>
Também há a opção de capturar objetos em 3D. Capturar objetos inanimados em 3D e editá-los com o software de criação de conteúdo digital é cada vez mais popular com o aumento da impressão 3D. Usando o **sensor Kinect 2** e 3D Builder você pode usar o recurso de captura para criar ativos de objetos do mundo real. [](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) Esse também é um [conjunto de](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) ferramentas para fazer o mesmo com **a fotogramametria** processando várias imagens para unir malha e texturas.

### <a name="purchasing-assets"></a>Comprando ativos

Outra excelente opção é comprar ativos para sua experiência. Há uma grande parte dos ativos disponíveis por meio de serviços como o [Unity Asset Store](https://www.assetstore.unity3d.com/) ou o [TurboSquid,](https://www.turbosquid.com/) entre outros.

Ao comprar ativos de terceiros, você sempre deseja verificar as seguintes propriedades:
* **Qual é a contagem de poliesportais?**
  * Ele se ajusta ao seu orçamento?
* **Há níveis de detalhes (LODs) para o modelo?**
  * Um nível de detalhes de modelos permite dimensionar os detalhes de um modelo para desempenho.
* **O arquivo de origem está disponível?**
  * Não incluído no [Unity Asset Store,](https://www.assetstore.unity3d.com/) mas sempre incluído com serviços como [TurboSquid](https://www.turbosquid.com/).
  * Sem o arquivo de origem, você não pode modificar o ativo.
  * Certifique-se de que o arquivo de origem fornecido possa ser importado por suas ferramentas 3D.
* **Saber o que você está recebendo**
  * As animações são fornecidas?
  * Verifique a lista de conteúdo do ativo que você está comprando.

### <a name="porting-assets"></a>Portando ativos

Em alguns casos, você terá ativos existentes que foram originalmente construídos para outros dispositivos e aplicativos diferentes. Na maioria dos casos, esses ativos podem ser convertidos em formatos compatíveis com o mecanismo gráfico que seu aplicativo está usando.

Ao portar ativos para usar em seu aplicativo HoloLens, você deve fazer as seguintes perguntas:
* **Você pode importar diretamente ou precisa ser convertido em outro formato?** Verifique o formato que você está importando com o mecanismo de gráficos que você está usando.
* **Se a conversão em um formato compatível for algo perdido?** Às vezes, os detalhes podem ser perdidos ou a importação pode causar artefatos que precisam ser limpos em uma ferramenta de autor 3D.
* **Qual é a contagem de triângulo/polígono para o ativo?** Com base no orçamento do seu aplicativo, você pode usar [o Simplygon](https://www.simplygon.com/) ou ferramentas semelhantes para dizimar (de forma procedimentamente ou reduzir manualmente a contagem de poly) do ativo original para se ajustar ao orçamento de seus aplicativos.

### <a name="outsourcing-assets"></a>Terceirizando ativos

Outra opção para projetos maiores que exigem mais ativos do que sua equipe está equipado para criar é terceirizar a criação de ativos. O processo de terceirização envolve encontrar o estúdio ou a agência certo especializado em terceirizar ativos. Essa pode ser a opção mais cara, mas também a mais flexível no que você obter.
* **Definir claramente o que você está solicitando**
  * Forneça o máximo de detalhes possível
  * Imagens de conceito de front, side e back
  * Arte de referência mostrando ativo no contexto
  * Escala do objeto (geralmente especificado em centímetros)
* **Fornecer um orçamento**
  * Intervalo de contagem de poly
  * Número de texturas
  * Tipo de sombreador (para Unity e HoloLens você sempre deve padrão para sombreadores móveis primeiro)
* **Entender os custos**
  * Qual é a política de terceirização para solicitações de alteração?

A terceirização pode funcionar bem com base na linha do tempo de seus projetos, mas requer mais supervisão para garantir que você receba os ativos corretos necessários na primeira vez.
