---
title: Definindo sua configuração do XR
description: Mantenha-se atualizado sobre as recomendações mais recentes de configuração do Unity XR para HoloLens desenvolvimento de aplicativos.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603699"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="3b738-104">Definindo sua configuração do XR</span><span class="sxs-lookup"><span data-stu-id="3b738-104">Setting up your XR configuration</span></span>

<span data-ttu-id="3b738-105">Depois de escolher uma [versão do Unity, a](choosing-unity-version.md)próxima etapa é selecionar a configuração de XR que você usará para criar seu aplicativo de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="3b738-105">Once you've [chosen a Unity version](choosing-unity-version.md), the next step is to select the XR configuration you'll use to build your mixed reality app:</span></span>

## <a name="choosing-an-xr-configuration"></a><span data-ttu-id="3b738-106">Escolhendo uma configuração de XR</span><span class="sxs-lookup"><span data-stu-id="3b738-106">Choosing an XR configuration</span></span>

<span data-ttu-id="3b738-107">Ao iniciar um novo projeto do Unity, você tem várias configurações de XR que podem ser selecionadas: o **plug-in OpenXR** do Mixed Reality, o **plug-in XR** do Windows e o **XR integrado herdado.**</span><span class="sxs-lookup"><span data-stu-id="3b738-107">When you start a new Unity project, you have various XR configurations you can select from: the **Mixed Reality OpenXR plugin**, the **Windows XR plugin** and **Legacy Built-in XR**.</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="3b738-108">Configurando seu projeto com o MRTK</span><span class="sxs-lookup"><span data-stu-id="3b738-108">Setting up your project with MRTK</span></span>

<span data-ttu-id="3b738-109">A maneira mais fácil de configurar seu projeto do Unity para realidade misturada é com o MRTK (Mixed Reality Toolkit).</span><span class="sxs-lookup"><span data-stu-id="3b738-109">The easiest way to get your Unity project set up for mixed reality is with the Mixed Reality Toolkit (MRTK).</span></span>  <span data-ttu-id="3b738-110">O MRTK para Unity é um kit de desenvolvimento de plataforma cruzada de software livre projetado para tornar mais fácil criar aplicativos incríveis de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3b738-110">MRTK for Unity is an open-source, cross-platform development kit designed to make it easy to build amazing mixed reality applications.</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="3b738-112">O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="3b738-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span>  <span data-ttu-id="3b738-113">Com o MRTK versão 2, você pode acelerar o desenvolvimento de aplicativos para Microsoft HoloLens, headsets Windows Mixed Reality imersivos (VR) e muitos outros dispositivos VR/AR.</span><span class="sxs-lookup"><span data-stu-id="3b738-113">With MRTK version 2, you can speed up your application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and many other VR/AR devices.</span></span> <span data-ttu-id="3b738-114">O projeto destina-se a reduzir as barreiras de entrada, permitindo que todos criem aplicativos de realidade misturada e contribuam de volta para a comunidade à medida que todos crescem.</span><span class="sxs-lookup"><span data-stu-id="3b738-114">The project is aimed at reducing barriers to entry, enabling everyone to build mixed reality applications and contribute back to the community as we all grow.</span></span>

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

<span data-ttu-id="3b738-115">Para saber mais sobre o Toolkit Realidade Misturada, confira a [documentação do MRTK](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="3b738-115">To learn more about the Mixed Reality Toolkit, check out the [MRTK documentation](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="3b738-116">Configuração manual sem MRTK</span><span class="sxs-lookup"><span data-stu-id="3b738-116">Manual setup without MRTK</span></span>

<span data-ttu-id="3b738-117">Embora a Microsoft e a comunidade tenham criado ferramentas de software livre, como [o MRTK (Mixed Reality Toolkit),](/windows/mixed-reality/mrtk-unity) que configurará automaticamente seu ambiente para realidade misturada, alguns desenvolvedores talvez desejem criar suas experiências desde o zero.</span><span class="sxs-lookup"><span data-stu-id="3b738-117">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) that will automatically set up your environment for mixed reality, some developers may wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]