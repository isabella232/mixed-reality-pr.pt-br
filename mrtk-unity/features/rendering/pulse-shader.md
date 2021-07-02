---
title: Sombreador de pulso
description: descrição em Sombreadores de pulso no MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 087806d48c7304d43f8383285cbaa2a12d8bf99a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176314"
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

Para o exemplo de malha espacial, verifique se MRTK_Pulse_ArticulatedHandMeshBlue.mat ou MRTK_Pulse_ArticulatedHandMeshPurple.mat está atribuído em MrTK Configurações -> Spatial Awareness -> Display Configurações -> Visible Material.

Para o exemplo de malha manual, verifique se MRTK_Pulse_SpatialMeshBlue.mat ou MRTK_Pulse_SpatialMeshPurple.mat está atribuído em ArticulatedHandMesh.prefab, que deve ser atribuído no MRTK Configurações -> Input -> Hand Tracking -> Hand Mesh Prefab.

## <a name="how-it-works"></a>Como ele funciona

O sombreador de malha de mão usa UVs para mapear o pulso ao longo da malha da mão e esmaecer o pulso. O sombreador de reconstrução da superfície usa as posições de vértice para mapear o pulso.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Exemplo de malha espacial – PulseShaderSpatialMeshExample.unity

Semelhante à HoloLens shell do 2, você pode apontar e tocar no ar com o raio de mão para gerar um efeito pulsante na malha espacial. A cena de exemplo contém o objeto ExampleSpatialMesh, que é um teste de dados de malha espacial para o modo de jogo do Unity. Esse objeto será desabilitado e oculto no dispositivo.

O script **PulseShaderSpatialMeshHandler.cs** gerará o efeito de pulso na malha espacial na posição do ponto de acerto, se `PulseOnSelect` for true. A  `Auto Pulse` propriedade também pode ser definida como true no próprio material para uma animação repetida.  Na cena de exemplo, esse script é anexado ao pré-fab PulseShaderSpatialMeshParent.  Esse pré-fab é referenciado no Perfil de Reconhecimento Espacial por meio da propriedade Pré-fab de Malha Espacial de Runtime. Durante o runtime, o pré-fab PulseShaderSpatialMeshParent é instanciado e adicionado à hierarquia de malha espacial (somente no dispositivo, esse comportamento não pode ser observado no editor).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Exemplo de malha manual – PulseShaderHandMeshExample.unity

Esta cena de exemplo demonstra a visualização de malha manual usando o sombreador de pulso. Quando uma mão é detectada pelo dispositivo HoloLens, a animação de pulso será disparada uma vez. Os comentários visuais podem aumentar a confiança de interação do usuário. 

O script **PulseShaderHandMeshHandler.cs** gera efeito de pulso no material atribuído. Por padrão, 'Pulse On Hand Detected' é verificado.
