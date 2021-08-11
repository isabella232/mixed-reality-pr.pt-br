---
title: Escolha do seu mecanismo
description: seja apresentado às opções de mecanismo disponíveis para o desenvolvimento de realidade misturada para HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, Unity
ms.openlocfilehash: 14235852f8c90e7ccc4f105f2938ce514ae2933973469db9a0e01bd03d2c1b6d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227543"
---
# <a name="choosing-your-engine"></a>Escolha do seu mecanismo

Há vários caminhos de desenvolvimento que você pode adotar por meio da nossa documentação. A primeira etapa é encontrar a tecnologia certa para você. Se você já tiver uma em mente, vá em frente e vá direto para a respectiva guia abaixo. Se estiver indeciso ou apenas começando, dê uma olhada em cada uma delas e entenda o que oferecem, as plataformas e as ferramentas disponíveis, e comece a criar.

> [!IMPORTANT]
> Dê uma olhada em nossa **[visão geral dos guias de portabilidade](porting-apps/porting-overview.md)** se você tiver projetos existentes que deseja trazer para o HoloLens 2 ou headsets de VR imersivos, como o Reverb G2. Temos guias de projetos que usam HTK, MRTK v1, SteamVR ou que foram desenvolvidos para headsets imersivos, como o Oculus Rift ou HTC Vive.

## <a name="engine-overview"></a>Visão geral do mecanismo

* O **Unity** é uma das principais plataformas de desenvolvimento em tempo real do mercado, com código de tempo de execução subjacente escrito em C++ e todos os scripts de desenvolvimento são feitos em C#. Se você está buscando criar jogos, filmes e cinemática de animação ou, até mesmo, renderizar conceitos de arquitetura ou engenharia em um mundo virtual, o Unity tem a infraestrutura certa para ajudar você.

* O **mecanismo do inreal 4** é um poderoso mecanismo de criação de software livre com suporte total para realidade misturada em C++ e em plantas. Desde o Unreal Engine 4.25, o suporte ao HoloLens é completo e pronto para produção. Com funcionalidades como o sistema de Script Visual de Blueprints flexível, os designers podem praticamente usar a gama completa de conceitos e ferramentas que geralmente estão disponíveis apenas para programadores. Os criadores de vários setores podem aproveitar a liberdade e o controle para oferecer conteúdo de ponta, experiências interativas e mundos virtuais de imersão.

* Desenvolvedores **nativos** com experiência em escrever seus próprios renderizadores 3D podem criar um mecanismo personalizado usando o OpenXR. O OpenXR é um padrão aberto de API isento de royalties da Khronos, que fornece aos mecanismos o acesso nativo a uma ampla variedade de dispositivos de fornecedores em toda a gama de realidade misturada. Faça o desenvolvimento com o OpenXR em um headset imersivo do HoloLens 2 ou do Windows Mixed Reality na área de trabalho.

* Os desenvolvedores **da Web** que criam experiências atraentes na Web de ar/VR entre navegadores podem usar o **WebXR**.

    > [!NOTE]
    > **Babylon.js** para o desenvolvimento de HoloLens está em andamento no momento. Confira as [últimas notícias e participe da Comunidade](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)!

<!-- Babylon is a Javascript-based, open source, 3D graphics engine capable of powering 3D scenes in a web browser. Babylon.js 4.2+ includes support for WebXR. With Babylon React Native, you can even build cross-platform native     applications for PC, mobile, and mixed reality devices. -->

## <a name="features-and-devices"></a>Recursos e dispositivos

<br>

| Logística | Unity | Unreal | JavaScript | Mecanismo personalizado <br>(usando OpenXR) |
|---|---|---|---|---|
| Idioma | C# | C++ | JavaScript | C/C++ |
| Preços | [Preços do Unity](https://store.unity.com/#plans-individual) | [Preço inreal](https://www.unrealengine.com/download) | Gratuita | Gratuita |

<br>

| Recursos de dispositivo | Unity | Unreal | JavaScript | Mecanismo personalizado <br>(usando OpenXR) |
|---|---|---|---|---|
| Rastreamento de dispositivo/vídeo | ✔️ | ✔️ | ✔️ | ✔️ |
| Entrada à mão | ✔️ | ✔️ | ✔️ | ✔️ |
| Entrada de olho | ✔️ | ✔️ | ❌ | ✔️ |
| Entrada de voz | ✔️ | ✔️ | ✔️ | ✔️ |
| Controladores de movimento | ✔️ | ✔️ | ✔️ | ✔️ |
| Teste de colisão de plano/malha | ✔️ | ✔️ | ✔️ | ✔️ |
| Reconhecimento de cena | ✔️ | ✔️ | ❌ | ✔️ |
| som espacial | ✔️ | ✔️ | ✔️ | ✔️ |
| Detecção de código QR | ✔️ | ✔️ | ❌ | ✔️ |

<br>

| Hardware | Unity | Unreal | JavaScript | Mecanismo personalizado <br>(usando OpenXR) |
|---|---|---|---|---|
| HoloLens 2 | ✔️ | ✔️ | ✔️ | ✔️ |
| HoloLens (1ª geração) | ✔️ | ✔️ | ❌ | Somente WinRT (Herdado) |
| [Headsets do Windows Mixed Reality](../discover/immersive-headset-hardware-details.md) | ✔️ | ✔️ | ✔️ | ✔️ |
| Headsets SteamVR | ✔️ | ✔️ | ✔️ | ✔️ |
| Oculus Quest/Rift | ✔️ | ✔️ | ✔️ | ✔️ |
| Móvel (ARCore/ARKit) | ✔️ | ✔️ | ✔️ | ❌ |

<br>

| Ferramentas | Unity | Unreal | JavaScript | Mecanismo personalizado <br>(usando OpenXR) |
|---|---|---|---|---|
| Kit de ferramentas de realidade misturada | ✔️ | ✔️ | ❌  | ❌ |
| Ferramentas de bloqueio mundial | ✔️ | ❌ | ❌  | ❌ |
<!-- | Malha | ❌ | ❌ | ❌ | ❌ | -->

<br>

| Serviços de Nuvem | Unity | Unreal | JavaScript | Mecanismo personalizado <br>(usando OpenXR) |
|---|---|---|---|---|
| Âncoras Espaciais do Azure | ✔️ | ✔️ | ❌ | ✔️ |
| Âncoras de Objeto do Azure | ✔️ | ❌ | ❌ | ✔️ |
| Azure Remote Rendering | ✔️ * | ❌ | ❌ | ✔️ * |

> [!NOTE]
> * atualmente, a renderização remota do Azure tem suporte em aplicativos que usam as APIs do WinRT herdadas (plug-in Windows XR no Unity). O suporte do ARR para aplicativos OpenXR estará disponível em breve.

## <a name="next-steps"></a>Próximas etapas

[!INCLUDE[](includes/tools-next-steps.md)]