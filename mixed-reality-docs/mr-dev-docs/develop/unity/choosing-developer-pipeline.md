---
title: Escolhendo seu pipeline de desenvolvedor
description: Mantenha-se atualizado sobre as recomendações de pipeline de desenvolvimento do Unity mais recentes para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, Unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394550"
---
# <a name="choosing-your-developer-pipeline"></a><span data-ttu-id="f3e2a-104">Escolhendo seu pipeline de desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="f3e2a-104">Choosing your developer pipeline</span></span>

![Faixa do logotipo do Unity](../images/unity_logo_banner.png)<br>

<span data-ttu-id="f3e2a-106">Embora, no momento, **recomendamos a instalação do Unity 2019,4 LTS e o uso da XR interna herdada** para o desenvolvimento de realidade misturada, você também pode criar aplicativos com outras configurações do Unity.</span><span class="sxs-lookup"><span data-stu-id="f3e2a-106">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="mixed-reality-toolkit-recommended"></a><span data-ttu-id="f3e2a-107">Kit de ferramentas de realidade mista (recomendado)</span><span class="sxs-lookup"><span data-stu-id="f3e2a-107">Mixed Reality Toolkit (Recommended)</span></span>

<span data-ttu-id="f3e2a-108">A configuração atual do Unity recomendada pela Microsoft para o HoloLens 2 é o kit de ferramentas de realidade misturada...</span><span class="sxs-lookup"><span data-stu-id="f3e2a-108">Microsoft’s current recommended Unity configuration for HoloLens 2 is the Mixed Reality Toolkit...</span></span>

### <a name="install-the-mixed-reality-feature-tool"></a><span data-ttu-id="f3e2a-109">Instalar a ferramenta de funcionalidade de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f3e2a-109">Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="f3e2a-110">A [Ferramenta de Recursos de Realidade Misturada](welcome-to-mr-feature-tool.md) é uma nova maneira para os desenvolvedores descobrirem e adicionarem pacotes de recursos de Realidade Misturada em projetos do Unity.</span><span class="sxs-lookup"><span data-stu-id="f3e2a-110">The [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="f3e2a-111">Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="f3e2a-111">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="f3e2a-112">Depois de validar os pacotes desejados, a ferramenta Recurso de Realidade Misturada os baixará no projeto de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="f3e2a-112">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f3e2a-113">Importando o kit de ferramentas de realidade misturada para o Unity</span><span class="sxs-lookup"><span data-stu-id="f3e2a-113">Importing the Mixed Reality Toolkit for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="f3e2a-115">O [MRTK](mrtk-getting-started.md) (Kit de Ferramentas de Realidade Misturada) é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="f3e2a-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="f3e2a-116">Instale o pacote do Kit de Ferramentas de Realidade Misturada seguindo as [instruções de instalação e uso](welcome-to-mr-feature-tool.md#system-requirements) e selecionando o pacote do **Mixed Reality Toolkit Foundation**.</span><span class="sxs-lookup"><span data-stu-id="f3e2a-116">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="f3e2a-117">Recomendamos a conclusão da seção de introdução dos nossos percursos de desenvolvimento do [HoloLens](unity-development-overview.md#1-getting-started) ou de [VR](unity-development-wmr-overview.md#1-getting-started).</span><span class="sxs-lookup"><span data-stu-id="f3e2a-117">We recommend completing the getting started section in our curated [HoloLens](unity-development-overview.md#1-getting-started) or [VR](unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="f3e2a-118">Se você já estiver seguindo o percurso de desenvolvimento do Unity para HoloLens, conclua o restante das etapas de instalação listadas abaixo e avance para os [tutoriais de Introdução do HoloLens 2](tutorials/mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="f3e2a-118">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3e2a-119">Observe que as instruções de instalação são destinadas à combinação estável mais recente das versões do MRTK e do Unity, que são as versões **MRTK 2.6.1** e **Unity 2019.4 LTS**.</span><span class="sxs-lookup"><span data-stu-id="f3e2a-119">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="f3e2a-120">Se você não quiser usar o MRTK para o Unity, precisará [criar o script de todas as interações e todos os comportamentos por conta própria](configure-unity-project.md).</span><span class="sxs-lookup"><span data-stu-id="f3e2a-120">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f3e2a-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Faixa do Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="f3e2a-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="f3e2a-122">**Kit de Ferramentas de Realidade Misturada – Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="f3e2a-122">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a><span data-ttu-id="f3e2a-123">Manual</span><span class="sxs-lookup"><span data-stu-id="f3e2a-123">Manual</span></span> 

<span data-ttu-id="f3e2a-124">TBD...</span><span class="sxs-lookup"><span data-stu-id="f3e2a-124">TBD...</span></span>