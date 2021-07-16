---
title: Sombreador de pulso
description: Descrição em sombreadores de pulso em MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0b26242d71bbe080e440f9c52a009e29000ab00b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224204"
---
# <a name="pulse-shader"></a>Sombreador de pulso

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Use o sombreador de pulso para animar um efeito de pulso visual sobre a reconstrução da superfície, a malha da mão articulada ou qualquer outra malha.

## <a name="shader-and-material"></a>Sombreador e material

Os materiais a seguir usam o sombreador **SR_Triangles** . Você pode configurar várias opções, como cor de preenchimento, cor da linha e cor do pulso.

- **MRTK_Pulse_SpatialMeshBlue. passe-partout** 
- **MRTK_Pulse_SpatialMeshPurple. passe-partout** 
- **MRTK_Pulse_ArticulatedHandMeshBlue. passe-partout** 
- **MRTK_Pulse_ArticulatedHandMeshPurple. passe-partout** 

## <a name="prerequisites"></a>Pré-requisitos

para o exemplo de malha espacial, verifique se MRTK_Pulse_SpatialMeshBlue. esteira ou MRTK_Pulse_SpatialMeshPurple. passe-partout está atribuído em objeto MixedRealityToolkit-> perfil de conscientização espacial-> exibir Configurações Material visível.

para o exemplo de malha à mão, certifique-se de que MRTK_Pulse_ArticulatedHandMeshBlue. esteira ou MRTK_Pulse_ArticulatedHandMeshPurple. passe-partout seja atribuído em ArticulatedHandMesh. pré-fabricado, que deve ser atribuído em MRTK Configurações-> entrada-> mão > de malha.

## <a name="how-it-works"></a>Como ele funciona

O sombreador de malha à mão usa UVs para mapear o pulso ao longo da malha à mão e para esmaecer o pulso. O sombreador de reconstrução de superfície usa as posições de vértice para mapear o pulso.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Exemplo de malha espacial – PulseShaderSpatialMeshExample. Unity

semelhante à experiência de shell de HoloLens 2, você pode apontar e tocar o ar com a mão ray para gerar um efeito de pulsing na malha espacial. A cena de exemplo contém o objeto ExampleSpatialMesh, que é um teste de dados de malha espacial para o modo de jogo do Unity. Este objeto será desabilitado e oculto no dispositivo.

O script **PulseShaderSpatialMeshHandler. cs** gera o efeito de pulso na malha espacial na posição do ponto de acesso se `PulseOnSelect` for verdadeiro. A  `Auto Pulse` propriedade também pode ser definida como true no material em si para uma animação repetida.  Na cena de exemplo, esse script é anexado ao PulseShaderSpatialMeshParent pré-fabricado.  Esse pré-fabricado é referenciado no perfil de conscientização espacial por meio da propriedade pré-fabricado de malha espacial de tempo de execução. Durante o tempo de execução, o PulseShaderSpatialMeshParent pré-fabricado e é instanciado e adicionado à hierarquia de malha espacial (somente no dispositivo, esse comportamento não pode ser observado no editor).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Exemplo de malha à mão – PulseShaderHandMeshExample. Unity

Esta cena de exemplo demonstra a visualização de malha à mão usando o sombreador de pulso. quando uma mão for detectada pelo dispositivo HoloLens, a animação pulse será disparada uma vez. Esse comentário visual pode aumentar a confiança da interação do usuário. 

O script **PulseShaderHandMeshHandler. cs** gera um efeito de pulso no material atribuído. Por padrão, "pulso na mão detectada" está marcado.
