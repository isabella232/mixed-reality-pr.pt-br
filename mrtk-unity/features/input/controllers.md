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
# <a name="controllers"></a>Controladores

Os controladores são criados e destruídos automaticamente pelos [**provedores de entrada**](input-providers.md). Cada tipo de controlador tem um número de *entradas físicas* definidas por um *tipo de eixo*, informando-nos o tipo de dados do valor de entrada (digital, eixo único, eixo duplo, seis DOF,...) e um tipo de *entrada* (pressionar botão, gatilho, Thumb Stick, ponteiro espacial,...) que descreve a origem da entrada. as entradas físicas são mapeadas para *ações de entrada* por meio do **perfil de mapeamento de entrada do controlador**, sob o perfil do *sistema de entrada* no componente de realidade misturada Toolkit.

![Mapeamento de entrada do controlador](../images/input/ControllerInputMapping.png)
