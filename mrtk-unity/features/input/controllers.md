---
title: Controladores
description: Como usar controladores no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Controladores,
ms.openlocfilehash: bc6aea1abda85567ab1b0db2616b529a92b4165e9b9cbcbc4b8b3cecd8a34c9f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224743"
---
# <a name="controllers"></a>Controladores

Os controladores são criados e destruídos automaticamente pelos [**provedores de entrada**](input-providers.md). Cada tipo de controlador tem várias entradas *físicas definidas* por um tipo de eixo *,* que nos dizem o tipo de dados do valor de entrada (Digital, Eixo Único, Eixo Duplo, Seis Dof, ...) e um tipo de entrada *(Pressionamento* de Botão, Gatilho, Thumb Stick, Ponteiro Espacial, ...) que descreve a origem da entrada. As entradas físicas  são mapeadas para ações de  entrada por meio do no Perfil de Mapeamento de Entrada do **Controlador,** no Perfil do Sistema de Entrada no componente de Toolkit Mixed Reality.

![Mapeamento de entrada do controlador](../images/input/ControllerInputMapping.png)
