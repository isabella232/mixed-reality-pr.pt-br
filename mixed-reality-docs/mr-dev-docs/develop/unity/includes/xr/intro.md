---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603697"
---
# <a name="openxr"></a>[<span data-ttu-id="afc0e-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="afc0e-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="afc0e-102">O plug-in OpenXR de Realidade Misturada é a recomendação da **Microsoft** para **Unity 2020 LTS** ou posterior.</span><span class="sxs-lookup"><span data-stu-id="afc0e-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="afc0e-103">À medida que novos recursos são desenvolvidos no futuro, eles só serão incluídos no plug-in OpenXR de Realidade Misturada no futuro.</span><span class="sxs-lookup"><span data-stu-id="afc0e-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="afc0e-104">O plug-in OpenXR de Realidade Misturada dá suporte total ao AR Foundation 4.0, fornecendo implementações ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="afc0e-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="afc0e-105">Isso permite que você escreva um código de raycasting uma vez que, em seguida, abrange HoloLens e telefones e tablets ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="afc0e-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="afc0e-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="afc0e-106">Prerequisites</span></span> 

* <span data-ttu-id="afc0e-107">Ferramentas [mais recentes para HoloLens desenvolvimento 2](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="afc0e-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="afc0e-108">Unity 2020.3 LTS mais recente: versão 2020.3.8f1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="afc0e-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="afc0e-109">Versões de pacote recomendadas</span><span class="sxs-lookup"><span data-stu-id="afc0e-109">Recommended package versions</span></span>

<span data-ttu-id="afc0e-110">As instruções nesta página configurarão você com os principais pacotes OpenXR do Unity necessários para implantar HoloLens 2 ou Windows Mixed Reality aplicativos:</span><span class="sxs-lookup"><span data-stu-id="afc0e-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="afc0e-111">Plug-in do Unity OpenXR: versão 1.2 ou posterior</span><span class="sxs-lookup"><span data-stu-id="afc0e-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="afc0e-112">Plug-in openXR de Realidade Misturada: versão 1.0.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="afc0e-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="afc0e-113">Se você usar os seguintes pacotes em seu projeto, precisará garantir que use pelo menos as versões mínimas listadas abaixo:</span><span class="sxs-lookup"><span data-stu-id="afc0e-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="afc0e-114">MRTK: versão 2.7.2 ou posterior</span><span class="sxs-lookup"><span data-stu-id="afc0e-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="afc0e-115">AR Foundation: versão 4.1.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="afc0e-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="afc0e-116">URP (Pipeline de Renderização Universal): versão 10.5.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="afc0e-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="afc0e-117">Âncoras Espaciais do Azure: versão 2.10 ou posterior</span><span class="sxs-lookup"><span data-stu-id="afc0e-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="afc0e-118">Azure Remote Rendering: versão 1.0.15 ou posterior</span><span class="sxs-lookup"><span data-stu-id="afc0e-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="afc0e-119">Se você estiver criando aplicativos de VR no Windows PC, o plug-in OpenXR de Realidade Misturada não será estritamente necessário.</span><span class="sxs-lookup"><span data-stu-id="afc0e-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="afc0e-120">No entanto, você deseja instalar o plug-in se estiver configurando vinculações de entrada para controladores HP Reverb G2 ou criando aplicativos que funcionam em headsets HoloLens 2 e VR.</span><span class="sxs-lookup"><span data-stu-id="afc0e-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="afc0e-121">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="afc0e-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="afc0e-122">A Microsoft não recomenda usar o plug-in Windows XR para novos projetos no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="afc0e-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="afc0e-123">Em vez disso, você deve usar o plug-in OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="afc0e-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="afc0e-124">No entanto, se você estiver usando o Unity 2019 e precisar do AR Foundation 2.0 para compatibilidade com dispositivos ARCore/ARKit, esse plug-in habilita esse suporte.</span><span class="sxs-lookup"><span data-stu-id="afc0e-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="afc0e-125">O uso desse plug-in no Unity 2019 não é compatível com as Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="afc0e-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="afc0e-126">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="afc0e-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="afc0e-127">Se você ainda estiver no **Unity 2019** ou anterior, a Microsoft recomenda o uso do suporte a **XR integrado herdado.**</span><span class="sxs-lookup"><span data-stu-id="afc0e-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="afc0e-128">Embora o plug-in Windows XR seja funcional no Unity 2019, não é recomendável porque esse plug-in não é compatível com âncoras espaciais do Azure no Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="afc0e-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="afc0e-129">Se você estiver iniciando um novo projeto, recomendamos instalar o [Unity 2020](../../choosing-unity-version.md) e usar o plug-in OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="afc0e-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>