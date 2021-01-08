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
# <a name="in-app-purchases"></a>Compras no aplicativo

As compras no aplicativo têm suporte no HoloLens, mas há algum trabalho para configurá-las.

Para usar a funcionalidade de compra do aplicativo, você deve:
* Criar uma [exibição XAML 2D](../design/app-views.md) para aparecer como um Slate
* Alterne para a ti para ativar o posicionamento, o que deixa a exibição imersiva
* Chame a API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Essa API abrirá o pop-up do sistema operacional Windows de estoque que mostra o nome, a descrição e o preço da compra no aplicativo. Em seguida, o usuário pode escolher opções de compra. Quando a ação for concluída, o aplicativo precisará apresentar a interface do usuário, o que permite ao usuário voltar para sua [exibição de imersão](../design/app-views.md).

Para aplicativos destinados a headsets de imersão de realidade mista do Windows com base na área de trabalho, não é necessário alternar manualmente para uma exibição XAML antes de chamar a API RequestProductPurchaseAsync.
