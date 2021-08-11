---
title: Barra de aplicativos
description: Visão geral sobre a Barra de Aplicativos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Barra de aplicativos,
ms.openlocfilehash: 1ecb43d25a4353ff4c3bd8350efaab877900a5b979cd42d2c8d1cb91ce32ae0c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198258"
---
# <a name="app-bar"></a>Barra de aplicativos

![Barra de aplicativos](../images/app-bar/MRTK_AppBar_Main.png)

A barra de aplicativos é um componente de interface do usuário usado junto com o script [de controle de](bounds-control.md) limites. Ele adiciona controles de botão a um objeto com a intenção de manipulá-lo. Usando o botão 'Ajustar', a interface de controle de limites para um objeto pode ser desativada/ativada. O botão "Remover" deve remover o objeto da cena.

## <a name="how-to-use-app-bar"></a>Como usar a barra de aplicativos

Arraste e solte `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) na hierarquia de cena. No painel inspetor do componente, atribua qualquer objeto com um controle de limites como a Caixa Delimitador de *Destino* para adicionar a barra de aplicativos a ele.

**Importante:** A opção de ativação de controle de limites para o objeto de destino deve ser "Ativar Manualmente".

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
