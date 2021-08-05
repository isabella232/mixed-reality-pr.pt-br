---
title: Visão geral de portabilidade
description: Uma visão geral das várias opções de porta para levar seus aplicativos existentes para a Realidade Misturada para HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portating, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 519dae088e689e0a6e617bf5e2b34f81cc2e265256c4844df7dd34e99172d536
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189416"
---
# <a name="porting-overview"></a>Visão geral de portabilidade

Quando se trata de portar ou atualizar seus projetos existentes para Realidade Misturada, seu percurso de portação depende se seu aplicativo é criado com o Unity ou o Unreal Engine e tem como destino HoloLens (1ª geração) ou HoloLens 2 ou SteamVR. Esta página de visão geral contém nossas recomendações atuais para cada plataforma e dispositivo– verifique novamente, pois esses processos estão sempre mudando.

Primeiro, configurar o destino do projeto com base em nossas recomendações do [Unity](#unity) e [do Unreal](#unreal) e, em seguida, siga um ou mais dos nossos cenários de portação:

- [HoloLens (1ª geração) para HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Headsets imersivos de VR](#immersive-vr-headsets)
- [Aplicativos UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinos de projeto recomendados

É importante manter seus projetos atualizados, independentemente de você estar portando um aplicativo para outro dispositivo de destino. Consulte os recursos baseados em mecanismo listados abaixo para ver nossas recomendações atuais.

### <a name="unity"></a>Unity

Consulte a [página Escolhendo uma versão do Unity](../unity/choosing-unity-version.md) para obter diretrizes atualizadas sobre as versões recomendadas do Unity e do MRTK.

### <a name="unreal"></a>Unreal

Consulte a [página Configurando seu projeto do Unreal](../unreal/unreal-project-setup.md) para obter diretrizes atualizadas sobre as versões recomendadas do Unreal e do MRTK.

## <a name="porting-scenarios"></a>Cenários de portação

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (1ª geração) do Unity para HoloLens 2

Se você tiver um aplicativo Unity HoloLens (1ª geração) existente que você gostaria de portar para um HoloLens 2, siga as instruções em nosso artigo de portabilidade HoloLens [.](./porting-hl1-hl2.md)

### <a name="immersive-vr-headsets"></a>Headsets imersivos de VR

Se você tiver criado conteúdo para outros dispositivos VR, precisará retarget quaisquer SDKs de VR específicos do fornecedor e, potencialmente, APIs de mapeamento de entrada. Você pode encontrar informações para cenários de portação do Unity e do Unreal em nosso [guia de portação de aplicativos imersivos.](porting-guides.md)

Para experiências do SteamVR que você deseja atualizar para headsets Windows Mixed Reality, consulte nosso guia de atualização [do SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="2d-universal-windows-applications"></a>Aplicativos de Windows 2D Universal

Se você tiver um aplicativo UWP 2D existente que gostaria de portar para um headset imersivo Windows Mixed Reality ou HoloLens, siga nossas instruções de portabilidade de aplicativos [UWP 2D para](building-2d-apps.md) Windows Mixed Reality.