---
title: Visão geral de portabilidade
description: Uma visão geral das várias opções de portabilidade para trazer os aplicativos existentes para a realidade misturada para o HoloLens e o VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portabilidade, Unity, middleware, mecanismo, UWP, Win32
ms.openlocfilehash: 693891d67ae26098f0810a539059da8d34f4731c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759107"
---
# <a name="porting-overview"></a>Visão geral de portabilidade

Quando se trata de portar ou atualizar seus projetos existentes para realidade misturada, sua jornada de portabilidade depende de o seu aplicativo ser criado com o Unity ou o mecanismo inreal e tem como alvo o HoloLens (1º gen) ou o HoloLens 2 ou o SteamVR. Esta página de visão geral contém nossas recomendações atuais para cada plataforma e dispositivo. Verifique novamente, pois esses processos estão sempre mudando.

Primeiro, configure o destino do projeto com base em nossas recomendações de [Unity](#unity) e [inreals](#unreal) e siga um ou mais dos nossos cenários de portabilidade:

- [HoloLens (1º gen) para o HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Headsets do Windows Mixed Reality](#windows-mixed-reality-headsets)
- [Aplicativos SteamVR](#steamvr-applications)
- [aplicativos UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinos de projeto recomendados

É importante manter seus projetos atualizados, seja a porta de um aplicativo para outro dispositivo de destino. Consulte os recursos baseados em mecanismo listados abaixo para nossas recomendações atuais.

### <a name="unity"></a>Unity

Nossa recomendação atual para o desenvolvimento do Unity com realidade misturada é **o Unity 2019 LTS usando o pacote XR herdado**. Se o seu projeto usa o kit de ferramentas de realidade misturada, verifique se você está na versão mais recente, que atualmente é **MRTK-Unity 2,5**.

> [!CAUTION]
> Embora o XR SDK esteja disponível com esta versão do Unity, as âncoras espaciais do Azure não são atualmente compatíveis com essa configuração. Essa recomendação será atualizada com uma versão futura do pacote de âncoras espaciais do Azure para o Unity. 
> 
> * Se você não precisar de âncoras espaciais do Azure, poderá [configurar seu projeto do Unity para XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) e começar a usar o [MRTK e o XR SDK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md).
> 
> * Se você estiver usando atualmente o SDK do XR em seu projeto e quiser usar âncoras espaciais do Azure, desinstale o SDK do XR e reinstale o pacote de XR herdado para reverter as configurações do projeto.


### <a name="unreal"></a>Unreal 

Nossa recomendação atual para desenvolvimento inreal com realidade misturada é o **mecanismo inreal 4,26**. Se seu projeto usa as ferramentas de UX do kit de ferramentas da realidade misturada, verifique se você está usando a versão mais recente, que atualmente é **UXT 0,10**.

## <a name="porting-scenarios"></a>Cenários de portabilidade

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Aplicativos do HoloLens (1ª gen) Unity para o HoloLens 2

Se você tiver um aplicativo de HoloLens (1ª gen) da Unity existente que você gostaria de portar para um HoloLens 2, siga as instruções em nosso [artigo portador do hololens](./porting-hl1-hl2.md).

### <a name="windows-mixed-reality-headsets"></a>Headsets do Windows Mixed Reality

Se você tiver criado conteúdo para outros dispositivos, como o Oculus Rift ou o HP reverbs G2, será necessário redirecionar SDKs de VR específicos do fornecedor e APIs de mapeamento de entrada potencialmente. Você pode encontrar informações para cenários de porta inreal e Unity em nosso [Guia de portabilidade de aplicativos de imersão](porting-guides.md).

### <a name="steamvr-applications"></a>Aplicativos SteamVR

Para qualquer experiência de SteamVR que você deseja atualizar para headsets de realidade mista do Windows, consulte nosso [Guia de atualização do SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>aplicativos universais do Windows 2D

Se você tiver um aplicativo UWP 2D existente que você gostaria de portar para um headset ou um HoloLens de imersão de realidade do Windows, siga nossas instruções [de portabilidade 2D de aplicativos UWP para Windows Mixed Reality](building-2d-apps.md) .