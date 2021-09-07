---
title: Experiências compartilhadas no Unity
description: Saiba como compartilhar os mesmos hologramas entre vários usuários em um aplicativo Unity com Âncoras Espaciais do Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Compartilhamento, Âncora, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Âncoras Espaciais do Azure, ASA, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: f7725c8282d1b5a93d555ac0f55ee936b910ff6c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244190"
---
# <a name="shared-experiences-in-unity"></a>Experiências compartilhadas no Unity

Uma experiência compartilhada permite que vários usuários, cada um com seus próprios HoloLens, iOS ou Android, vistam e interajam coletivamente com o mesmo holograma. Hologramas são posicionados em um ponto fixo no espaço por meio do compartilhamento de âncora espacial.

## <a name="azure-spatial-anchors"></a>Âncoras Espaciais do Azure

### <a name="automated-with-world-locking-tools"></a>Automatizado com Ferramentas de Bloqueio Mundial

Assim como nas âncoras locais, as Ferramentas de Bloqueio Mundial podem usar um grupo de Âncoras Espaciais do Azure para bloquear espaços de coordenadas inteiros em relação ao mundo físico, em vez de usar âncoras individuais para bloquear objetos individuais. O bloqueio mundial de todo o espaço não só fornece um ambiente mais propício ao layout preciso, mas também é mais eficiente em recursos de runtime e tempo de desenvolvedor.

Para obter mais informações e exemplos que aproveitando as Âncoras Espaciais do Azure para compartilhar sistemas de coordenadas entre dispositivos HoloLens, Android e iOS, bem como persistir espaços entre sessões, consulte a documentação das Ferramentas de Bloqueio Mundial [.](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html)

### <a name="manual-configuration-of-azure-spatial-anchors"></a>Configuração manual de Âncoras Espaciais do Azure

As Âncoras Espaciais do <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> criam âncoras espaciais duráveis com suporte de nuvem que seu aplicativo pode localizar em vários HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial comum entre vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.

Você também pode usar as Âncoras Espaciais do <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> para persistência de holograma assíncrona em HoloLens, iOS e Dispositivos Android.  Ao compartilhar uma âncora espacial de nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo se esses dispositivos não estão presentes juntos ao mesmo tempo.

Para começar a criar experiências compartilhadas no Unity, experimente os <a href="/azure/spatial-anchors/unity-overview" target="_blank">inícios rápidos</a>do Unity das Âncoras Espaciais do Azure de 5 minutos.

Depois que as Âncoras Espaciais do Azure são configuradas, você pode <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity.</a>

## <a name="local-anchor-transfers"></a>Transferências de âncora local

Em situações em que você não pode usar Âncoras Espaciais do Azure, as [transferências](../../out-of-scope/local-anchor-transfers-in-unity.md) de âncora local permitem que um dispositivo HoloLens exporte uma âncora para que uma segunda HoloLens possa importá-la.  Essa abordagem não tem suporte em dispositivos iOS e Android e fornece recall de âncora menos robusto do que as Âncoras Espaciais do Azure.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que lançamos, você está no meio da exploração das APIs e funcionalidades da plataforma de Realidade Misturada. A partir daqui, você pode continuar para a próxima seção:

> [!div class="nextstepaction"]
> [Câmera localizável](locatable-camera-in-unity.md)

Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:

> [!div class="nextstepaction"]
> [Implantar em HoloLens ou Windows Mixed Reality headsets imersivos](../platform-capabilities-and-apis/using-visual-studio.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-advanced-features) a qualquer momento.

## <a name="see-also"></a>Confira também
* [Experiências compartilhadas em realidade misturada](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de Âncoras Espaciais do Azure para Unity</a>