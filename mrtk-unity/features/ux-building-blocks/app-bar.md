---
title: Barra de aplicativos
description: Visão geral sobre a barra de aplicativos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, barra de aplicativos,
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175696"
---
# <a name="app-bar"></a>Barra de aplicativos

![Barra de aplicativos](../images/app-bar/MRTK_AppBar_Main.png)

A barra de aplicativos é um componente de interface do usuário que é usado junto com o script de [controle de limites](bounds-control.md) . Ele adiciona controles de botão a um objeto com a intenção de manipulá-lo. Usando o botão ' ajustar ', a interface de controle de limites para um objeto pode ser desativada. O botão "remover" deve remover o objeto da cena.

## <a name="how-to-use-app-bar"></a>Como usar a barra de aplicativos

Arraste e solte `AppBar` (assets/MRTK/SDK/Features/UX/pré-fabricados/AppBar/AppBar. pré-fabricado) na hierarquia de cena. No painel de Inspetor do componente, atribua qualquer objeto com um controle de limites como a *caixa delimitadora de destino* para adicionar a barra de aplicativo a ele.

**Importante:** A opção de ativação de controle de limites para o objeto de destino deve ser ' Ativar manualmente '.

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
