---
title: Compras no aplicativo
description: Saiba como usar compras no aplicativo em seus aplicativos de realidade misturada com exibições XAML 2D e pop-up de Windows do sistema operacional.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras no aplicativo, hololens, XAML, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: fbb957d1044a5c76c19691b875de8f9513bfc4b49bc4cb0dbb98d045d615f1a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196144"
---
# <a name="in-app-purchases"></a>Compras no aplicativo

Há suporte para compras no aplicativo HoloLens, mas há algum trabalho para defini-las.

Para usar a funcionalidade na compra de aplicativo, você deve:
* Criar uma exibição [XAML 2D](../design/app-views.md) para aparecer como um slate
* Alternar para ele para ativar o posicionamento, o que deixa a exibição imersiva
* Chame a API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Essa API abrirá o pop-up de Windows do sistema operacional que mostra o nome, a descrição e o preço da compra no aplicativo. Em seguida, o usuário pode escolher opções de compra. Depois que a ação for concluída, o aplicativo precisará apresentar a interface do usuário, o que permite que o usuário volte para sua [exibição imersiva](../design/app-views.md).

Para aplicativos destinados a headsets imersivos baseados em Windows Mixed Reality desktop, não é necessário alternar manualmente para uma exibição XAML antes de chamar a API RequestProductPurchaseAsync.