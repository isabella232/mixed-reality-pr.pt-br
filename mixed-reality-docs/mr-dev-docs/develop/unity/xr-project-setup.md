---
title: Definindo sua configuração do XR
description: Mantenha-se atualizado sobre as recomendações mais recentes de configuração do Unity XR para HoloLens desenvolvimento de aplicativos.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: 72f17ec9fc74143a2ae6cc51e1ffed0c73d13ef04ef5c4004537be70d1daaaca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202695"
---
# <a name="setting-up-your-xr-configuration"></a>Definindo sua configuração do XR

Depois de escolher uma [versão do Unity, a](choosing-unity-version.md)próxima etapa é selecionar a configuração de XR que você usará para criar seu aplicativo de realidade misturada:

## <a name="choosing-an-xr-configuration"></a>Escolhendo uma configuração de XR

Ao iniciar um novo projeto do Unity, você tem várias configurações de XR que podem ser selecionadas: o **plug-in OpenXR** do Mixed Reality, o **plug-in XR** do Windows e o **XR integrado herdado.**

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

A maneira mais fácil de configurar seu projeto do Unity para realidade misturada é com o MRTK (Mixed Reality Toolkit).  O MRTK para Unity é um kit de desenvolvimento de plataforma cruzada de software livre projetado para tornar mais fácil criar aplicativos incríveis de realidade misturada.

![MRTK](../../design/images/MRTK_UX_Hero.png)

O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.  Com o MRTK versão 2, você pode acelerar o desenvolvimento de aplicativos para Microsoft HoloLens, headsets Windows Mixed Reality imersivos (VR) e muitos outros dispositivos VR/AR. O projeto destina-se a reduzir as barreiras de entrada, permitindo que todos criem aplicativos de realidade misturada e contribuam de volta para a comunidade à medida que todos crescem.

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

Para saber mais sobre o Toolkit Realidade Misturada, confira a [documentação do MRTK](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

Embora a Microsoft e a comunidade tenham criado ferramentas de software livre, como [o MRTK (Mixed Reality Toolkit),](/windows/mixed-reality/mrtk-unity) que configurará automaticamente seu ambiente para realidade misturada, alguns desenvolvedores talvez desejem criar suas experiências desde o zero.

[!INCLUDE[](includes/xr/manual-setup.md)]