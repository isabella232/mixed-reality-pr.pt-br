---
ms.openlocfilehash: bcd9ae057f289d85d1f12d5cb79258bc3bb87ace
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443705"
---
# <a name="425"></a>[4.25](#tab/425)

Não há etapas adicionais de habilitação específicas do UE 4.25.

# <a name="426"></a>[4.26](#tab/426)

Se você está usando o UE 4.26, recomendamos usar a seguinte configuração de blueprint para adicionar um pequeno atraso, pois o controle de código QR precisa ser inicializado APÓS o início de uma sessão de RA:

![Blueprint da função Alternar ARCapture com atraso](../images/qr-codes-img-01.png)
