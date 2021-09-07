---
title: Âncoras espaciais compartilhadas no DirectX
description: saiba como sincronizar dois dispositivos HoloLens compartilhando âncoras espaciais locais e do Azure em aplicativos do DirectX.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, sincronizar, âncora espacial, transferência, vários participantes, exibição, cenário, passo a passos, código de exemplo, azure, âncoras espaciais do azure, ASA
ms.openlocfilehash: 6b1b98539c05849064f1c33ed859bc925ed5fd31
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244331"
---
<!--Unity Note: No Unity specific content in this article. -->
# <a name="shared-experiences-in-directx"></a>Experiências compartilhadas no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herdadas.  Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](../native/openxr-getting-started.md)**.

uma experiência compartilhada é aquela em que vários usuários com seu próprio dispositivo HoloLens, iOS ou Android, exibem coletivamente e interagem com o mesmo holograma. O holograma é posicionado em um ponto fixo no espaço usando o compartilhamento de âncora espacial.

## <a name="azure-spatial-anchors"></a>Âncoras Espaciais do Azure

você pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar âncoras espaciais duráveis com suporte de nuvem, que seu aplicativo pode localizar em vários dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

você também pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para persistência de holograma assíncrona em dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial de nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que esses dispositivos não estejam presentes juntos ao mesmo tempo.

para começar a criar experiências compartilhadas em seu aplicativo HoloLens, experimente as <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">âncoras espaciais do Azure de 5 minutos HoloLens início rápido</a>.

Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">criar e localizar âncoras em HoloLens</a>.  Os passo a passos também estão disponíveis para <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e Ios</a> , permitindo que você compartilhe as mesmas âncoras em todos os dispositivos.

## <a name="local-anchor-transfers"></a>Transferências de âncora local

em situações em que você não pode usar âncoras espaciais do Azure, as [transferências de âncora local](../../out-of-scope/local-anchor-transfers-in-directx.md) permitem que um dispositivo de HoloLens exporte uma âncora a ser importada por um segundo dispositivo de HoloLens.  Essa abordagem fornece uma recall de ancoragem menos robusta do que as âncoras espaciais do Azure, e os dispositivos iOS e Android não são compatíveis com essa abordagem.

## <a name="see-also"></a>Confira também

* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">SDK de âncoras espaciais do Azure para HoloLens</a>