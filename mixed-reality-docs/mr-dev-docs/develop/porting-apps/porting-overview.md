---
title: Visão geral de portabilidade
description: Uma visão geral das várias opções de porta para levar seus aplicativos existentes para Realidade Misturada para HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portating, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600495"
---
# <a name="porting-overview"></a>Visão geral de portabilidade

Quando se trata de portar ou atualizar seus projetos existentes para Realidade Misturada, seu percurso de portação depende se o aplicativo é criado com o Unity ou o Unreal Engine e tem como alvo o HoloLens (1ª geração) ou o HoloLens 2 ou o SteamVR. Esta página de visão geral contém nossas recomendações atuais para cada plataforma e dispositivo– verifique novamente, pois esses processos estão sempre mudando.

Primeiro, configurar o destino do projeto com base em nossas recomendações do [Unity](#unity) e [do Unreal](#unreal) e, em seguida, siga um ou mais dos nossos cenários de portação:

- [HoloLens (1ª geração) para HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Headsets do Windows Mixed Reality](#windows-mixed-reality-headsets)
- [Aplicativos SteamVR](#steamvr-applications)
- [Aplicativos UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinos de projeto recomendados

É importante manter seus projetos atualizados, independentemente de você estar portando um aplicativo para outro dispositivo de destino. Consulte os recursos baseados em mecanismo listados abaixo para ver nossas recomendações atuais.

### <a name="unity"></a>Unity

Nossa recomendação atual para o desenvolvimento do Unity com Realidade Misturada é **o Unity 2019 LTS usando o pacote XR herdado.** Se seu projeto usar o Kit de Ferramentas de Realidade Misturada, verifique se você está na versão mais recente, que atualmente é **o MRTK-Unity 2.5.**

> [!CAUTION]
> Embora o SDK do XR está disponível com esta versão do Unity, as Âncoras Espaciais do Azure não são compatíveis com essa configuração no momento. Essa recomendação será atualizada com uma versão futura do pacote âncoras espaciais do Azure para Unity.
> 
> * Se você não precisar de Âncoras Espaciais do Azure, poderá configurar seu projeto do Unity para [XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) e começar a usar o [MRTK e o SDK do XR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)
> 
> * Se você estiver usando o SDK XR em seu projeto e quiser usar Âncoras Espaciais do Azure, desinstale o SDK do XR e reinstale o pacote XR herdado para reverter as configurações do projeto.

### <a name="unreal"></a>Unreal

Nossa recomendação atual para o desenvolvimento do Unreal com Realidade Misturada é **o Unreal Engine 4.26.** Se seu projeto usar as Ferramentas de UX do Kit de Ferramentas de Realidade Misturada, certifique-se de que você está usando a versão mais recente, que atualmente é **UXT 0.10**.

## <a name="porting-scenarios"></a>Cenários de portação

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Aplicativos Unity do HoloLens (1ª geração) para o HoloLens 2

Se você tiver um aplicativo Unity do HoloLens (1ª geração) existente que gostaria de portar para um HoloLens 2, siga as instruções em nosso artigo de [portabilidade do HoloLens.](./porting-hl1-hl2.md)

### <a name="windows-mixed-reality-headsets"></a>Headsets do Windows Mixed Reality

Se você tiver criado conteúdo para outros dispositivos, como o Oculus Dimensional ou o HP Reverb G2, precisará retarget de SDKs de VR específicos do fornecedor e, potencialmente, APIs de mapeamento de entrada. Você pode encontrar informações para cenários de portação do Unity e do Unreal em nosso [guia de portação de aplicativos imersivos.](porting-guides.md)

### <a name="steamvr-applications"></a>Aplicativos SteamVR

Para qualquer experiência do SteamVR que você deseja atualizar para headsets Windows Mixed Reality, consulte nosso guia de atualização [do SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="2d-universal-windows-applications"></a>Aplicativos Universais do Windows 2D

Se você tiver um aplicativo UWP 2D existente que gostaria de portar para um headset imersivo Windows Mixed Reality ou HoloLens, siga nossas instruções de portabilidade de aplicativos [UWP 2D](building-2d-apps.md) para Windows Mixed Reality.