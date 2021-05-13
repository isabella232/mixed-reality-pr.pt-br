---
title: Controladores
description: Como usar controladores no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, controladores,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850332"
---
# <a name="controllers"></a>Controladores

Os controladores são criados e destruídos automaticamente pelos [**provedores de entrada**](input-providers.md). Cada tipo de controlador tem um número de *entradas físicas* definidas por um *tipo de eixo*, informando-nos o tipo de dados do valor de entrada (digital, eixo único, eixo duplo, seis DOF,...) e um tipo de *entrada* (pressionar botão, gatilho, Thumb Stick, ponteiro espacial,...) que descreve a origem da entrada. As entradas físicas são mapeadas para *ações de entrada* por meio do **perfil de mapeamento de entrada do controlador**, no perfil do *sistema de entrada* no componente do kit de ferramentas da realidade misturada.

O MRTK detectará automaticamente os controladores do WMR e os exibirá quando o pacote [**Microsoft. MixedReality. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) estiver instalado. Os modelos de controladores só aparecerão no editor ao usar o pipeline OpenXR. Para visualizar os modelos do controlador oculus, siga as [instruções de implantação do Oculus Quest](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)

![Mapeamento de entrada do controlador](../images/input/ControllerInputMapping.png)