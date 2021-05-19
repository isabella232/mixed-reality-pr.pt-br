---
title: Formato de arquivo de animação de entrada
description: Documentação sobre especificação de formato de arquivo binário de animação de entrada em MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: ba232818c0a49d803ca6fae0b5adbc64e6deefa8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145121"
---
# <a name="input-animation-binary-file-format-specification"></a>Especificação de formato de arquivo binário de animação de entrada

## <a name="overall-structure"></a>Estrutura geral

O arquivo binário da animação de entrada começa com um número mágico de inteiro de 64 bits. O valor desse número em notação hexadecimal é `0x6a8faf6e0f9e42c6` e pode ser usado para identificar arquivos de animação de entrada válidos.

Os próximos oito bytes são dois valores Int32 declarando o número de versão principal e secundária do arquivo.

O restante do arquivo é retirado por dados de animação, que podem ser alterados entre os números de versão.

| Seção | Tipo |
|---------|------|
| Número mágico | Int64 |
| Número de versão principal | Int32 |
| Número de versão secundária | Int32 |
| Dados de animação | _consulte a seção versão_ |

## <a name="version-11"></a>Versão 1.1

Os dados de animação de entrada consistem em três valores Boolianos que indicam se a animação contém dados de câmera, mão e olho olhar, seguidos por uma sequência de curvas de animação. As curvas presentes dependem dos valores desses boolianos. Cada curva pode ter um número diferente de quadros-chave.

| Seção | Type | Observações |
|---------|------|------|
| Tem pose de câmera | Boolean | |
| Tem dados à mão | Boolean | |
| Tem olho olhar| Boolean | |
| Câmera | [Curvas de pose](#pose-curves) | Somente se a placa de câmera for verdadeira |
| Esquerda controlada à mão | [Curva booliana](#boolean-curve) | Somente se Tem Dados de Mão for true |
| Direita controlada à mão | [Curva booliana](#boolean-curve) | Somente se Tem Dados de Mão for true |
| Pinçar a mão para a esquerda | [Curva booliana](#boolean-curve) | Somente se Tem Dados de Mão for true |
| Direita de pinçamento de mão | [Curva booliana](#boolean-curve) | Somente se Tem Dados de Mão for true |
| Junções à esquerda | [Curvas de pose conjunta](#joint-pose-curves) | Somente se Tem Dados de Mão for true |
| Junções de mão à direita | [Curvas de pose conjunta](#joint-pose-curves) | Somente se Tem Dados de Mão for true |
| Olhar fixo | [Curvas de raio](#ray-curves)] | Somente se o olho olhar for true |

## <a name="version-10"></a>Versão 1.0

Os dados de animação de entrada consistem em uma sequência de curvas de animação. O número e o significado das curvas de animação são fixos, mas cada curva pode ter um número diferente de quadros-chave.

| Seção | Tipo |
|---------|------|
| Câmera | [Curvas de pose](#pose-curves) |
| Mão rastreada à esquerda | [Curva booliana](#boolean-curve) |
| Mão controlada à direita | [Curva booliana](#boolean-curve) |
| Apertar à esquerda | [Curva booliana](#boolean-curve) |
| Apertar à direita | [Curva booliana](#boolean-curve) |
| Junções à esquerda | [Curvas de pose conjuntas](#joint-pose-curves) |
| Junções à direita | [Curvas de pose conjuntas](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>Curvas de pose conjuntas

Para cada mão, uma sequência de curvas de animação conjunta é armazenada. O número de junções é fixo e um conjunto de curvas de pose é armazenado para cada conjunto.

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
| RosinhaMetacarpal | [Curvas de pose](#pose-curves) |
| Rosinha | [Curvas de pose](#pose-curves) |
| RosinhaMiddleJoint | [Curvas de pose](#pose-curves) |
| RosárioDistalJoint | [Curvas de pose](#pose-curves) |
| Dica de Rosa | [Curvas de pose](#pose-curves) |

### <a name="pose-curves"></a>Curvas de pose

Curvas de pose são uma sequência de três curvas de animação para o vetor de posição, seguidas por 4 curvas de animação para o quatternion de rotação.

| Seção | Tipo |
|---------|------|
| Posição X | [Curva float](#float-curve) |
| Posição Y | [Curva float](#float-curve) |
| Posição Z | [Curva float](#float-curve) |
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
| Direção Z | [Curva float](#float-curve) |

### <a name="float-curve"></a>Curva float

As curvas de ponto flutuante são curvas bézier completas com um número variável de keyframes. Cada keyframe armazena uma hora e um valor de curva, bem como tangentes e pesos no lado esquerdo e direito de cada keyframe.

| Seção | Tipo |
|---------|------|
| Modo de pré-quebra | Int32, modo [de quebra](#wrap-mode) |
| Modo pós-quebra | Int32, modo [de quebra](#wrap-mode) |
| Número de keyframes | Int32 |
| Quadros chave | [Estrutura de chaves float](#float-keyframe) |

### <a name="float-keyframe"></a>Estrutura de chaves float

Um keyframe float armazena valores tangentes e de peso junto com o valor e a hora básicas.

| Seção | Tipo |
|---------|------|
| Hora | Float32 |
| Valor | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| De peso | Float32 |
| WeightedMode | Int32, [modo ponderado](#weighted-mode) |

### <a name="boolean-curve"></a>Curva booliana

As curvas boolianas são sequências simples de valores on/off. Em cada quadro-chave, o valor da curva é invertido imediatamente.

| Seção | Tipo |
|---------|------|
| Modo de pré-encapsulamento | Int32, [modo de encapsulamento](#wrap-mode) |
| Modo pós-encapsulamento | Int32, [modo de encapsulamento](#wrap-mode) |
| Número de quadros-chave | Int32 |
| Quadros chave | [Quadro-chave booliano](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>Quadro-chave booliano

Um quadro chave booliano armazena apenas uma hora e um valor.

| Seção | Tipo |
|---------|------|
| Hora | Float32 |
| Valor | Float32 |

### <a name="wrap-mode"></a>Modo de encapsulamento

A semântica dos modos pré e pós-encapsulamento segue a definição de [WrapMode do Unity](https://docs.unity3d.com/ScriptReference/WrapMode.html) . Eles são uma combinação dos seguintes bits:

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
