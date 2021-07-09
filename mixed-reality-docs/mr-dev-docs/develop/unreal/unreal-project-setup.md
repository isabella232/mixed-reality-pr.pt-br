---
title: Configuração do projeto Unreal
description: Saiba como configurar seu projeto com a versão mais recente do Unreal Engine e a Ferramenta de recursos de Realidade Misturada.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, realidade misturada, desenvolvimento, recursos, novo projeto, emulador, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade misturada do windows, headset de realidade virtual
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394610"
---
# <a name="setting-up-your-unreal-project"></a><span data-ttu-id="b3f6a-104">Configuração do projeto Unreal</span><span class="sxs-lookup"><span data-stu-id="b3f6a-104">Setting up your Unreal project</span></span>

<span data-ttu-id="b3f6a-105">Recomendamos instalar o [Unreal Engine versão 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) ou posterior para aproveitar ao máximo o suporte interno ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b3f6a-105">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="b3f6a-106">Acesse a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** e clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="b3f6a-106">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="b3f6a-107">Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="b3f6a-107">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="b3f6a-108">![Opção de instalação do Unreal para HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="b3f6a-108">![Unreal Install Option HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span></span>

## <a name="import-mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="b3f6a-109">Importar Kit de Ferramentas de Realidade Misturada para Unreal</span><span class="sxs-lookup"><span data-stu-id="b3f6a-109">Import Mixed Reality Toolkit for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="b3f6a-111">O MRTK (Kit de Ferramentas de Realidade Misturada) é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b3f6a-111">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="b3f6a-112">O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="b3f6a-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="b3f6a-113">O kit de ferramentas destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="b3f6a-113">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="b3f6a-114">Para a instalação, recomendamos a conclusão da [seção Introdução](unreal-development-overview.md#1-getting-started) do nosso [percurso de desenvolvimento do Unreal](unreal-development-overview.md) estruturado.</span><span class="sxs-lookup"><span data-stu-id="b3f6a-114">For installation, we recommend completing the [Getting Started section](unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](unreal-development-overview.md).</span></span> <span data-ttu-id="b3f6a-115">Se você já está seguindo o percurso de desenvolvimento do Unreal, conclua o restante das etapas de instalação listadas abaixo e avance para os [tutoriais de Introdução do HoloLens 2](tutorials/unreal-uxt-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="b3f6a-115">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b3f6a-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Imagem do logotipo do Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="b3f6a-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="b3f6a-117">**Kit de Ferramentas de Realidade Misturada – Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="b3f6a-117">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="b3f6a-118">Se você não quiser usar o MRTK para o Unreal, precisará criar o script de todas as interações e todos os comportamentos por conta própria.</span><span class="sxs-lookup"><span data-stu-id="b3f6a-118">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>