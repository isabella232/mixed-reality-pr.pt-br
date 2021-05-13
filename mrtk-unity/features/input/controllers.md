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
# <a name="controllers"></a><span data-ttu-id="4b1d8-104">Controladores</span><span class="sxs-lookup"><span data-stu-id="4b1d8-104">Controllers</span></span>

<span data-ttu-id="4b1d8-105">Os controladores são criados e destruídos automaticamente pelos [**provedores de entrada**](input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="4b1d8-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="4b1d8-106">Cada tipo de controlador tem um número de *entradas físicas* definidas por um *tipo de eixo*, informando-nos o tipo de dados do valor de entrada (digital, eixo único, eixo duplo, seis DOF,...) e um tipo de *entrada* (pressionar botão, gatilho, Thumb Stick, ponteiro espacial,...) que descreve a origem da entrada.</span><span class="sxs-lookup"><span data-stu-id="4b1d8-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="4b1d8-107">As entradas físicas são mapeadas para *ações de entrada* por meio do **perfil de mapeamento de entrada do controlador**, no perfil do *sistema de entrada* no componente do kit de ferramentas da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="4b1d8-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

<span data-ttu-id="4b1d8-108">O MRTK detectará automaticamente os controladores do WMR e os exibirá quando o pacote [**Microsoft. MixedReality. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="4b1d8-108">MRTK will automatically detect WMR controllers and display them when the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package is installed.</span></span> <span data-ttu-id="4b1d8-109">Os modelos de controladores só aparecerão no editor ao usar o pipeline OpenXR.</span><span class="sxs-lookup"><span data-stu-id="4b1d8-109">Controllers models will only show up in the editor when using the OpenXR pipeline.</span></span> <span data-ttu-id="4b1d8-110">Para visualizar os modelos do controlador oculus, siga as [instruções de implantação do Oculus Quest](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="4b1d8-110">To visualize Oculus controller models, follow the [Oculus Quest deployment instructions](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span></span>

![Mapeamento de entrada do controlador](../images/input/ControllerInputMapping.png)