---
title: Compras no aplicativo
description: As compras no aplicativo têm suporte em aplicativos de realidade misturada, mas há algum trabalho para configurá-las.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras no aplicativo, hololens, XAML, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 905c1be72bf2a3d6fa167cab68a4cb71e6538acc
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757774"
---
# <a name="in-app-purchases"></a><span data-ttu-id="af78c-104">Compras no aplicativo</span><span class="sxs-lookup"><span data-stu-id="af78c-104">In-app purchases</span></span>

<span data-ttu-id="af78c-105">As compras no aplicativo têm suporte no HoloLens, mas há algum trabalho para configurá-las.</span><span class="sxs-lookup"><span data-stu-id="af78c-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="af78c-106">Para usar a funcionalidade de compra do aplicativo, você deve:</span><span class="sxs-lookup"><span data-stu-id="af78c-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="af78c-107">Criar uma [exibição XAML 2D](../design/app-views.md) para aparecer como um Slate</span><span class="sxs-lookup"><span data-stu-id="af78c-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="af78c-108">Alterne para a ti para ativar o posicionamento, o que deixa a exibição imersiva</span><span class="sxs-lookup"><span data-stu-id="af78c-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="af78c-109">Chame a API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="af78c-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="af78c-110">Essa API abrirá o pop-up do sistema operacional Windows de estoque que mostra o nome, a descrição e o preço da compra no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af78c-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="af78c-111">Em seguida, o usuário pode escolher opções de compra.</span><span class="sxs-lookup"><span data-stu-id="af78c-111">The user can then choose purchase options.</span></span> <span data-ttu-id="af78c-112">Quando a ação for concluída, o aplicativo precisará apresentar a interface do usuário, o que permite ao usuário voltar para sua [exibição de imersão](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="af78c-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="af78c-113">Para aplicativos destinados a headsets de imersão de realidade mista do Windows com base na área de trabalho, não é necessário alternar manualmente para uma exibição XAML antes de chamar a API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="af78c-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
