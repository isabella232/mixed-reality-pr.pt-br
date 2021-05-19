---
title: Sombreador de pulso
description: descrição em Sombreadores de pulso no MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: e03c021689b6701b86ae25ba9fa253ece1368428
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144939"
---
# <a name="pulse-shader"></a>Sombreador de pulso

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Use o sombreador de pulso para animar um efeito de pulso visual sobre a reconstrução da superfície, malha de mão articulada ou qualquer outra malha.

## <a name="shader-and-material"></a>Sombreador e material

Os materiais a **seguir SR_Triangles** sombreador. Você pode configurar várias opções, como cor de preenchimento, cor da linha e cor do pulso.

- **MRTK_Pulse_SpatialMeshBlue.mat** 
- **MRTK_Pulse_SpatialMeshPurple.mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue.mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple.mat** 

## <a name="prerequisites"></a>Pré-requisitos

Para o exemplo de malha espacial, verifique se MRTK_Pulse_ArticulatedHandMeshBlue.mat ou MRTK_Pulse_ArticulatedHandMeshPurple.mat está atribuído em Configurações do MRTK -> Reconhecimento Espacial -configurações de exibição > -> Material Visível.

Para o exemplo de malha manual, verifique se MRTK_Pulse_SpatialMeshBlue.mat ou MRTK_Pulse_SpatialMeshPurple.mat está atribuído em ArticulatedHandMesh.prefab, que deve ser atribuído em Configurações do MRTK -> Entrada -> Hand Tracking -> Hand Mesh Prefab.

## <a name="how-it-works"></a>Como ele funciona

O sombreador de malha de mão usa UVs para mapear o pulso ao longo da malha da mão e esmaecer o pulso. O sombreador de reconstrução da superfície usa as posições de vértice para mapear o pulso.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Exemplo de malha espacial – PulseShaderSpatialMeshExample.unity

Semelhante à experiência de shell do HoloLens 2, você pode apontar e tocar no ar com o raio de mão para gerar um efeito pulsante na malha espacial. A cena de exemplo contém o objeto ExampleSpatialMesh, que é um teste de dados de malha espacial para o modo de jogo do Unity. Esse objeto será desabilitado e oculto no dispositivo.

O script **PulseShaderSpatialMeshHandler.cs** gerará o efeito de pulso na malha espacial na posição do ponto de acerto, se `PulseOnSelect` for true. A  `Auto Pulse` propriedade também pode ser definida como true no material em si para uma animação repetida.  Na cena de exemplo, esse script é anexado ao PulseShaderSpatialMeshParent pré-fabricado.  Esse pré-fabricado é referenciado no perfil de conscientização espacial por meio da propriedade pré-fabricado de malha espacial de tempo de execução. Durante o tempo de execução, o PulseShaderSpatialMeshParent pré-fabricado e é instanciado e adicionado à hierarquia de malha espacial (somente no dispositivo, esse comportamento não pode ser observado no editor).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Exemplo de malha à mão – PulseShaderHandMeshExample. Unity

Esta cena de exemplo demonstra a visualização de malha à mão usando o sombreador de pulso. Quando uma mão é detectada pelo dispositivo HoloLens, a animação Pulse será disparada uma vez. Esse comentário visual pode aumentar a confiança da interação do usuário. 

O script **PulseShaderHandMeshHandler. cs** gera um efeito de pulso no material atribuído. Por padrão, "pulso na mão detectada" está marcado.
