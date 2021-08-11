---
title: Experiências compartilhadas no Unity
description: Saiba como compartilhar os mesmos hologramas entre vários usuários em um aplicativo do Unity com âncoras espaciais do Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Compartilhamento, ancoragem, WorldAnchor, Sr Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, âncoras espaciais do Azure, ASA, headset de realidade misturada, headset de realidade misturada do Windows, headset da realidade virtual
ms.openlocfilehash: b9fdd09740dc6197c46a2d017f61e97898f213cd44bb504cbbf306f6a7ae21ec
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195918"
---
# <a name="shared-experiences-in-unity"></a>Experiências compartilhadas no Unity

uma experiência compartilhada permite que vários usuários, cada um com seus próprios dispositivos HoloLens, iOS ou Android, exibam e interajam coletivamente com o mesmo holograma. Hologramas estão posicionadas em um ponto fixo no espaço por meio do compartilhamento de âncora espacial.

## <a name="azure-spatial-anchors"></a>Âncoras Espaciais do Azure

as <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> criam âncoras espaciais duráveis com suporte de nuvem, que seu aplicativo pode localizar em vários dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico. 

você também pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para persistência de holograma assíncrona em dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial de nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que esses dispositivos não estejam presentes juntos ao mesmo tempo.

Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.

Depois que as âncoras espaciais do Azure estiverem configuradas, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.

## <a name="local-anchor-transfers"></a>Transferências de âncora local

em situações em que você não pode usar âncoras espaciais do Azure, as [transferências de âncora local](../../out-of-scope/local-anchor-transfers-in-unity.md) permitem que um dispositivo de HoloLens exporte uma âncora para que uma segunda HoloLens possa importá-la.  Essa abordagem não tem suporte em dispositivos iOS e Android e fornece uma recall de ancoragem menos robusta do que as âncoras espaciais do Azure.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada. A partir daqui, você pode continuar para a próxima seção:

> [!div class="nextstepaction"]
> [Câmera localizável](locatable-camera-in-unity.md)

Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:

> [!div class="nextstepaction"]
> [implantar HoloLens ou Windows Mixed Reality headsets de imersão](../platform-capabilities-and-apis/using-visual-studio.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-advanced-features) a qualquer momento.

## <a name="see-also"></a>Confira também
* [Experiências compartilhadas em realidade misturada](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a>