---
title: Compras no aplicativo
description: Saiba como usar compras no aplicativo em seus aplicativos de realidade misturada com exibições de XAML 2D e pop-up de ações do SO Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras no aplicativo, hololens, XAML, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: a87cc68f67def1d46a3a6ba352e723d356f51fa2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008666"
---
# <a name="in-app-purchases"></a><span data-ttu-id="0de0a-104">Compras no aplicativo</span><span class="sxs-lookup"><span data-stu-id="0de0a-104">In-app purchases</span></span>

<span data-ttu-id="0de0a-105">As compras no aplicativo têm suporte no HoloLens, mas há algum trabalho para configurá-las.</span><span class="sxs-lookup"><span data-stu-id="0de0a-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="0de0a-106">Para usar a funcionalidade de compra do aplicativo, você deve:</span><span class="sxs-lookup"><span data-stu-id="0de0a-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="0de0a-107">Criar uma [exibição XAML 2D](../design/app-views.md) para aparecer como um Slate</span><span class="sxs-lookup"><span data-stu-id="0de0a-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="0de0a-108">Alterne para a ti para ativar o posicionamento, o que deixa a exibição imersiva</span><span class="sxs-lookup"><span data-stu-id="0de0a-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="0de0a-109">Chame a API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="0de0a-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="0de0a-110">Essa API abrirá o pop-up do sistema operacional Windows de estoque que mostra o nome, a descrição e o preço da compra no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0de0a-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="0de0a-111">Em seguida, o usuário pode escolher opções de compra.</span><span class="sxs-lookup"><span data-stu-id="0de0a-111">The user can then choose purchase options.</span></span> <span data-ttu-id="0de0a-112">Quando a ação for concluída, o aplicativo precisará apresentar a interface do usuário, o que permite ao usuário voltar para sua [exibição de imersão](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="0de0a-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="0de0a-113">Para aplicativos destinados a headsets de imersão de realidade mista do Windows com base na área de trabalho, não é necessário alternar manualmente para uma exibição XAML antes de chamar a API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="0de0a-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
