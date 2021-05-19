---
title: Serviço de acompanhamento perdido
description: Visão geral sobre o serviço LostTracking no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 96090b05c60cfaa6ff5d8c5e1dc7a58cc2658b71
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144522"
---
# <a name="lost-tracking-visualization"></a>Visualização de rastreamento perdida

![Controle perdido](../images/lost-tracking/LostTrackingVisualization.jpg)

O serviço de extensão de rastreamento perdido fornece o Visual animado de estilo de shell do HoloLens para o estado de rastreamento perdido.

## <a name="how-to-use-lost-tracking-extensions"></a>Como usar as extensões de rastreamento perdidas

No perfil do MRTK, adicione o **serviço de rastreamento perdido** às extensões. Atribua **DefaultLostTrackingServiceProfile** que inclui **LostTrackingVisualPrefab**.

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
