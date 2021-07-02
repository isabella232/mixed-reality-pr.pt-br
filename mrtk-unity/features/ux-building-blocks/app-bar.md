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
# <a name="app-bar"></a><span data-ttu-id="eade8-104">Barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="eade8-104">App bar</span></span>

![Barra de aplicativos](../images/app-bar/MRTK_AppBar_Main.png)

<span data-ttu-id="eade8-106">A barra de aplicativos é um componente de interface do usuário que é usado junto com o script de [controle de limites](bounds-control.md) .</span><span class="sxs-lookup"><span data-stu-id="eade8-106">App bar is a UI component that is used together with the [bounds control](bounds-control.md) script.</span></span> <span data-ttu-id="eade8-107">Ele adiciona controles de botão a um objeto com a intenção de manipulá-lo.</span><span class="sxs-lookup"><span data-stu-id="eade8-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="eade8-108">Usando o botão ' ajustar ', a interface de controle de limites para um objeto pode ser desativada.</span><span class="sxs-lookup"><span data-stu-id="eade8-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="eade8-109">O botão "remover" deve remover o objeto da cena.</span><span class="sxs-lookup"><span data-stu-id="eade8-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="eade8-110">Como usar a barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="eade8-110">How to use app bar</span></span>

<span data-ttu-id="eade8-111">Arraste e solte `AppBar` (assets/MRTK/SDK/Features/UX/pré-fabricados/AppBar/AppBar. pré-fabricado) na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="eade8-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="eade8-112">No painel de Inspetor do componente, atribua qualquer objeto com um controle de limites como a *caixa delimitadora de destino* para adicionar a barra de aplicativo a ele.</span><span class="sxs-lookup"><span data-stu-id="eade8-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="eade8-113">**Importante:** A opção de ativação de controle de limites para o objeto de destino deve ser ' Ativar manualmente '.</span><span class="sxs-lookup"><span data-stu-id="eade8-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
