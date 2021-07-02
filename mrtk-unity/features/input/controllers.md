---
title: Controladores
description: Como usar controladores no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, controladores,
ms.openlocfilehash: ea3dbd11baa669750f3bccc09d6cd7ab3eb7688f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176925"
---
# <a name="controllers"></a><span data-ttu-id="ad33e-104">Controladores</span><span class="sxs-lookup"><span data-stu-id="ad33e-104">Controllers</span></span>

<span data-ttu-id="ad33e-105">Os controladores são criados e destruídos automaticamente pelos [**provedores de entrada**](input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="ad33e-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="ad33e-106">Cada tipo de controlador tem um número de *entradas físicas* definidas por um *tipo de eixo*, informando-nos o tipo de dados do valor de entrada (digital, eixo único, eixo duplo, seis DOF,...) e um tipo de *entrada* (pressionar botão, gatilho, Thumb Stick, ponteiro espacial,...) que descreve a origem da entrada.</span><span class="sxs-lookup"><span data-stu-id="ad33e-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="ad33e-107">as entradas físicas são mapeadas para *ações de entrada* por meio do **perfil de mapeamento de entrada do controlador**, sob o perfil do *sistema de entrada* no componente de realidade misturada Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ad33e-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

![Mapeamento de entrada do controlador](../images/input/ControllerInputMapping.png)
