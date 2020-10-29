---
title: Compras no aplicativo
description: As compras no aplicativo têm suporte em aplicativos de realidade misturada, mas há algum trabalho para configurá-las.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras no aplicativo, hololens
ms.openlocfilehash: 7174fe555322216b7e547055aaaf7879c01d8f23
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675281"
---
# <a name="in-app-purchases"></a>Compras no aplicativo

As compras no aplicativo têm suporte no HoloLens, mas há algum trabalho para configurá-las.

Para aproveitar a funcionalidade de compra de aplicativo, você deve:
* Criar uma [exibição XAML 2D](../design/app-views.md) para aparecer como um Slate
* Alterne para a ti para ativar o posicionamento, o que deixa a exibição imersiva
* Chame a API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Essa API abrirá o pop-up do sistema operacional Windows de estoque que mostra o nome, a descrição e o preço da compra no aplicativo. Em seguida, o usuário pode escolher opções de compra. Depois que a ação for concluída, o aplicativo precisará apresentar a interface do usuário, o que permitirá que ele volte para sua [exibição de imersão](../design/app-views.md).

Para aplicativos destinados a headsets de imersão de realidade mista do Windows com base na área de trabalho, não é necessário alternar manualmente para uma exibição XAML antes de chamar a API RequestProductPurchaseAsync.
