---
title: Formato do arquivo de animação de entrada
description: Documentação sobre a especificação de formato de arquivo binário de animação de entrada no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: bf77d976c9c894e6cf455a3a6b0e0c538912af2a9e8f8e2c7e847ba6e4657140
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222758"
---
# <a name="input-animation-file-format"></a>Formato do arquivo de animação de entrada

## <a name="overall-structure"></a>Estrutura geral

O arquivo binário de animação de entrada começa com um número mágico de inteiro de 64 bits. O valor desse número na notação hexadecimal é e pode ser `0x6a8faf6e0f9e42c6` usado para identificar arquivos de animação de entrada válidos.

Os próximos oito bytes são dois valores Int32 que declaram o número de versão principal e secundária do arquivo.

O restante do arquivo é feito pelos dados de animação, que podem ser alterados entre os números de versão.

| Seção | Tipo |
|---------|------|
| Número mágico | Int64 |
| Número de versão principal | Int32 |
| Número de versão secundária | Int32 |
| Dados de animação | _consulte a seção de versão_ |

## <a name="version-11"></a>Versão 1.1

Os dados de animação de entrada consistem em três valores boolianas que indicam se a animação contém dados de Câmera, Mão e Olhar, seguidos por uma sequência de curvas de animação. As curvas presentes dependem dos valores desses boolianas. Cada curva pode ter um número diferente de keyframes.

| Seção | Type | Observações |
|---------|------|------|
| Tem pose de câmera | Boolean | |
| Tem dados de mão | Boolean | |
| Tem o olhar fixo| Boolean | |
| Câmera | [Curvas de pose](#pose-curves) | Somente se a Pose da Câmera for verdadeira |
| Esquerda controlada à mão | [Curva booliana](#boolean-curve) | Somente se Tem Dados de Mão for true |
| Direita controlada à mão | [Curva booliana](#boolean-curve) | Somente se Tem Dados de Mão for true |
| Pinçar a mão para a esquerda | [Curva booliana](#boolean-curve) | Somente se Tem Dados de Mão for true |
| Direita de pinçamento de mão | [Curva booliana](#boolean-curve) | Somente se Tem Dados de Mão for true |
| Junções à esquerda | [Curvas de pose conjunta](#joint-pose-curves) | Somente se Tem Dados de Mão for true |
| Junções de mão à direita | [Curvas de pose conjunta](#joint-pose-curves) | Somente se Tem Dados de Mão for true |
| Olhar fixo | [Curvas de raio](#ray-curves)] | Somente se Tem o Olhar é verdadeiro |

## <a name="version-10"></a>Versão 1.0

Os dados de animação de entrada consistem em uma sequência de curvas de animação. O número e o significado das curvas de animação são fixos, mas cada curva pode ter um número diferente de keyframes.

| Seção | Tipo |
|---------|------|
| Câmera | [Curvas de pose](#pose-curves) |
| Esquerda controlada à mão | [Curva booliana](#boolean-curve) |
| Direita controlada à mão | [Curva booliana](#boolean-curve) |
| Pinçar a mão para a esquerda | [Curva booliana](#boolean-curve) |
| Direita de pinçamento de mão | [Curva booliana](#boolean-curve) |
| Junções à esquerda | [Curvas de pose conjunta](#joint-pose-curves) |
| Junções de mão à direita | [Curvas de pose conjunta](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>Curvas de pose conjunta

Para cada mão, uma sequência de curvas de animação conjuntas é armazenada. O número de junções é fixo e um conjunto de curvas de pose é armazenado para cada junção.

| Seção | Tipo |
|---------|------|
| Nenhum | [Curvas de pose](#pose-curves) |
| Pulso | [Curvas de pose](#pose-curves) |
| Palm | [Curvas de pose](#pose-curves) |
| ThumbMetacarpalJoint | [Curvas de pose](#pose-curves) |
| ThumbProximalJoint | [Curvas de pose](#pose-curves) |
| ThumbDistalJoint | [Curvas de pose](#pose-curves) |
| Dica digital | [Curvas de pose](#pose-curves) |
| IndexMetacarpal | [Curvas de pose](#pose-curves) |
| IndexKnuckle | [Curvas de pose](#pose-curves) |
| IndexMiddleJoint | [Curvas de pose](#pose-curves) |
| IndexDistalJoint | [Curvas de pose](#pose-curves) |
| IndexTip | [Curvas de pose](#pose-curves) |
| MiddleMetacarpal | [Curvas de pose](#pose-curves) |
| MiddleKnuckle | [Curvas de pose](#pose-curves) |
| MiddleMiddleJoint | [Curvas de pose](#pose-curves) |
| MiddleDistalJoint | [Curvas de pose](#pose-curves) |
| MiddleTip | [Curvas de pose](#pose-curves) |
| RingMetacarpal | [Curvas de pose](#pose-curves) |
| RingKnuckle | [Curvas de pose](#pose-curves) |
| RingMiddleJoint | [Curvas de pose](#pose-curves) |
| RingDistalJoint | [Curvas de pose](#pose-curves) |
| RingTip | [Curvas de pose](#pose-curves) |
| PinkyMetacarpal | [Curvas de pose](#pose-curves) |
| PinkyKnuckle | [Curvas de pose](#pose-curves) |
| PinkyMiddleJoint | [Curvas de pose](#pose-curves) |
| PinkyDistalJoint | [Curvas de pose](#pose-curves) |
| PinkyTip | [Curvas de pose](#pose-curves) |

### <a name="pose-curves"></a>Curvas de pose

As curvas de pose são uma sequência de três curvas de animação para o vetor de posição, seguida por quatro curvas de animação para o quaternion de rotação.

| Seção | Tipo |
|---------|------|
| Posição X | [Curva de flutuação](#float-curve) |
| Posição Y | [Curva de flutuação](#float-curve) |
| Posição Z | [Curva de flutuação](#float-curve) |
| Rotação X | [Curva de flutuação](#float-curve) |
| Rotação Y | [Curva de flutuação](#float-curve) |
| Rotação Z | [Curva de flutuação](#float-curve) |
| Rotação W | [Curva de flutuação](#float-curve) |

### <a name="ray-curves"></a>Curvas de raio

As curvas de Ray são uma sequência de 3 curvas de animação para o vetor de origem, seguida por três curvas de animação para o vetor de direção.

| Seção | Tipo |
|---------|------|
| Origem X | [Curva de flutuação](#float-curve) |
| Origem Y | [Curva de flutuação](#float-curve) |
| Origem Z | [Curva de flutuação](#float-curve) |
| Direção X | [Curva de flutuação](#float-curve) |
| Direção Y | [Curva de flutuação](#float-curve) |
| Direção Z | [Curva de flutuação](#float-curve) |

### <a name="float-curve"></a>Curva de flutuação

As curvas de ponto flutuante são curvas Bézier totalmente compostas com um número variável de quadros-chave. Cada quadro-chave armazena um valor de hora e de curva, bem como as tangentes e os pesos no lado esquerdo e direito de cada quadro.

| Seção | Tipo |
|---------|------|
| Modo de pré-encapsulamento | Int32, [modo de encapsulamento](#wrap-mode) |
| Modo pós-encapsulamento | Int32, [modo de encapsulamento](#wrap-mode) |
| Número de quadros-chave | Int32 |
| Quadros chave | [Barra-chave flutuante](#float-keyframe) |

### <a name="float-keyframe"></a>Barra-chave flutuante

Um quadro-chave float armazena valores tangentes e de peso junto com o tempo e o valor básicos.

| Seção | Tipo |
|---------|------|
| Hora | Float32 |
| Valor | Float32 |
| Intangente | Float32 |
| Ditangente | Float32 |
| Inpeso | Float32 |
| De peso | Float32 |
| WeightedMode | Int32, [modo ponderado](#weighted-mode) |

### <a name="boolean-curve"></a>Curva booliana

As curvas boolianas são sequências simples de valores de ativas/desligados. Em cada keyframe, o valor da curva muda imediatamente.

| Seção | Tipo |
|---------|------|
| Modo de pré-quebra | Int32, modo [de quebra](#wrap-mode) |
| Modo pós-quebra | Int32, modo [de quebra](#wrap-mode) |
| Número de keyframes | Int32 |
| Quadros chave | [Keyframe booliana](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>Keyframe booliana

Um keyframe booliana armazena apenas uma hora e um valor.

| Seção | Tipo |
|---------|------|
| Hora | Float32 |
| Valor | Float32 |

### <a name="wrap-mode"></a>Modo de wrap

A semântica dos modos Pré e Pós-Wrap segue a [definição wrapMode do Unity.](https://docs.unity3d.com/ScriptReference/WrapMode.html) Eles são uma combinação dos seguintes bits:

| Valor | Significado |
|-------|---------|
| 0 | Padrão: lê a configuração mais alta do modo de repetição padrão. |
| 1 | Uma vez: quando o tempo atingir o fim do clipe de animação, o clipe será automaticamente parado e a hora será redefinida para o início do clipe. |
| 2 | Loop: quando o tempo atingir o fim do clipe de animação, o tempo continuará no início. |
| 4 | PingPong: quando o tempo atingir o fim do clipe de animação, o tempo fará ping entre o início e o fim. |
| 8 | ClampForever: reproduz a animação. Quando chegar ao final, ele continuará a tocar o último quadro e nunca mais interromperá a reprodução. |

### <a name="weighted-mode"></a>Modo ponderado

A semântica do modo Ponderado segue a [definição weightedMode do Unity.](https://docs.unity3d.com/ScriptReference/WeightedMode.html)

| Valor | Significado |
|-------|---------|
| 0 | Nenhum: exclua inWeight ou outWeight ao calcular segmentos de curva. |
| 1 | Em: inclua inWeight ao calcular o segmento de curva anterior. |
| 2 | Out: inclua outWeight ao calcular o próximo segmento de curva. |
| 3 | Ambos: inclua inWeight e outWeight ao calcular segmentos de curva. |
