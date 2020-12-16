---
title: Âncoras espaciais compartilhadas no DirectX
description: Explica como sincronizar dois dispositivos HoloLens compartilhando âncoras espaciais.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, sincronizar, âncora espacial, transferência, vários participantes, exibição, cenário, passo a passos, código de exemplo, Azure, âncoras espaciais do Azure, ASA
ms.openlocfilehash: 4e41975a18c28cb2228b20ebb5d3a445774cca44
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530326"
---
# <a name="shared-experiences-in-directx"></a>Experiências compartilhadas no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herdadas.  Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](../native/openxr-getting-started.md)**.

Uma experiência compartilhada é aquela em que vários usuários têm seu próprio dispositivo HoloLens, iOS ou Android, exibem coletivamente e interagem com o mesmo holograma. O holograma é posicionado em um ponto fixo no espaço usando o compartilhamento de âncora espacial.

## <a name="azure-spatial-anchors"></a>Âncoras Espaciais do Azure

Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar âncoras espaciais duráveis com suporte de nuvem, que seu aplicativo pode localizar em vários dispositivos HoloLens, Ios e Android.  Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para a persistência de holograma assíncrona em dispositivos de HoloLens, Ios e Android.  Ao compartilhar uma âncora espacial de nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que esses dispositivos não estejam presentes juntos ao mesmo tempo.

Para começar a criar experiências compartilhadas em seu aplicativo de HoloLens, experimente o início rápido de 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">do Azure espaciais do hololens</a>.

Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">criar e localizar âncoras no HoloLens</a>.  Os passo a passos também estão disponíveis para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e Ios</a> , permitindo que você compartilhe as mesmas âncoras em todos os dispositivos.

## <a name="local-anchor-transfers"></a>Transferências de âncora local

Em situações em que você não pode usar âncoras espaciais do Azure, as [transferências de âncora local](../../out-of-scope/local-anchor-transfers-in-directx.md) permitem que um dispositivo de hololens exporte uma âncora a ser importada por um segundo dispositivo hololens.  Essa abordagem fornece uma recall de ancoragem menos robusta do que as âncoras espaciais do Azure, e os dispositivos iOS e Android não são compatíveis com essa abordagem.

## <a name="see-also"></a>Veja também
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">SDK de âncoras espaciais do Azure para HoloLens</a>