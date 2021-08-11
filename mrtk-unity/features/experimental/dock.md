---
title: Dock
description: descrição para Controles de Encaixe.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226568"
---
# <a name="dock"></a>Dock

![Dock](../images/dock/MRTK_UX_Dock_Main.png)

Esse controle permite mover objetos para dentro e para fora de posições predeterminadas, para criar paletas, prateleiras e barras de navegação.

## <a name="features"></a>Recursos

- Dá suporte a qualquer número de posições de encaixe e layouts (funciona muito bem com [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) )
- Objetos encaixados se movem automaticamente para deixar espaço para novos objetos
- Os objetos são dimensionados para se ajustarem ao espaço encaixado e, em seguida, reizem para sua posição original quando arrastados para fora.

## <a name="getting-started-with-dock"></a>Como começar a trabalhar com o Dock

- Crie um GameObject com o componente Dock e adicione alguns gameObjects filhos a ele.
- Adicione o componente DockPosition a cada um dos filhos.
- Adicione o componente Dockable a qualquer número de objetos na cena para permitir que eles sejam encaixados. Eles também devem ter [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) o componente e um Colisor.
- *Opcional:* use um [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) para o Dock para estabelecer automaticamente as DockPositions.

### <a name="prerequisites"></a>Pré-requisitos

- Cada objeto encaixado deve ter um colisor com [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) um ou [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .
- Se você quiser que um objeto inicie Encaixado quando a cena for carregada, atribua-o a qualquer propriedade de objeto encaixado do DockPosition.

## <a name="how-it-works"></a>Como ele funciona

O componente Dockable se baseia em eventos de manipulação para permitir que objetos arrastados sejam encaixados e desencaixados em posições específicas. O posicionamento é determinado pelo DockPosition disparado sobreposto mais próximo ao objeto arrastado, portanto, ambos os objetos precisam ter Colisores para que o gatilho seja ativado.
