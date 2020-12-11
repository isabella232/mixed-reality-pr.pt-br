---
ms.openlocfilehash: bcd9ae057f289d85d1f12d5cb79258bc3bb87ace
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443705"
---
# <a name="425"></a>[<span data-ttu-id="65de5-101">4.25</span><span class="sxs-lookup"><span data-stu-id="65de5-101">4.25</span></span>](#tab/425)

<span data-ttu-id="65de5-102">Não há etapas adicionais de habilitação específicas do UE 4.25.</span><span class="sxs-lookup"><span data-stu-id="65de5-102">There are no additional enabling steps specific to UE 4.25.</span></span>

# <a name="426"></a>[<span data-ttu-id="65de5-103">4.26</span><span class="sxs-lookup"><span data-stu-id="65de5-103">4.26</span></span>](#tab/426)

<span data-ttu-id="65de5-104">Se você está usando o UE 4.26, recomendamos usar a seguinte configuração de blueprint para adicionar um pequeno atraso, pois o controle de código QR precisa ser inicializado APÓS o início de uma sessão de RA:</span><span class="sxs-lookup"><span data-stu-id="65de5-104">If you're using UE 4.26, we recommend using the following blueprint setup to add a small delay, because QR code tracking must be initialized AFTER starting an AR Session:</span></span>

![Blueprint da função Alternar ARCapture com atraso](../images/qr-codes-img-01.png)
