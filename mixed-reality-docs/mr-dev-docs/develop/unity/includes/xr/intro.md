---
ms.openlocfilehash: 550ad2b9fa92894cdf4dad86def4cd3a9b450fb1
ms.sourcegitcommit: e9a1510984d00dc40ffd39239349e500f5737a0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113103895"
---
# <a name="openxr"></a>[<span data-ttu-id="a6645-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="a6645-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="a6645-102">O plug-in Mixed Reality OpenXR é a **recomendação da Microsoft para o** Unity 2020 LTS ou posterior.</span><span class="sxs-lookup"><span data-stu-id="a6645-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="a6645-103">À medida que novos recursos forem desenvolvidos no futuro, eles só serão incluídos no plug-in Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a6645-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="a6645-104">O plug-in Mixed Reality OpenXR dá suporte total ao AR Foundation 4,0, fornecendo implementações ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="a6645-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="a6645-105">Isso permite que você escreva o código raycasting uma vez que se estenda por telefones 2 e ARCore/ARKit celulares e tablets.</span><span class="sxs-lookup"><span data-stu-id="a6645-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a6645-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a6645-106">Prerequisites</span></span> 

* <span data-ttu-id="a6645-107">Ferramentas mais recentes [para o desenvolvimento do HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="a6645-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="a6645-108">LTS do Unity 2020,3 mais recente, (recomendamos o 2020.3.8 F1 ou superior)</span><span class="sxs-lookup"><span data-stu-id="a6645-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="a6645-109">Versões mínimas</span><span class="sxs-lookup"><span data-stu-id="a6645-109">Minimum versions</span></span>

<span data-ttu-id="a6645-110">As instruções nesta página o configurarão com os melhores e mais recentes requisitos de Unity e OpenXR listados abaixo:</span><span class="sxs-lookup"><span data-stu-id="a6645-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="a6645-111">Plug-in mais recente do Unity OpenXR (Recomendamos 1,2 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="a6645-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="a6645-112">Plugin OpenXR de realidade mista mais recente, (recomendamos a versão 1.0.0 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="a6645-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="a6645-113">Se seu projeto usar MRTK, recomendamos a versão 2.7.2 ou posterior</span><span class="sxs-lookup"><span data-stu-id="a6645-113">If your project uses MRTK, we recommend version 2.7.2 or later</span></span>
* <span data-ttu-id="a6645-114">Se o seu projeto usa o pacote do pipeline de renderização universal (URP), recomendamos a versão 10.5.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="a6645-114">If your project uses Universal Render Pipeline (URP) package, we recommend version 10.5.1 or later</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="a6645-115">Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário.</span><span class="sxs-lookup"><span data-stu-id="a6645-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="a6645-116">No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.</span><span class="sxs-lookup"><span data-stu-id="a6645-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="a6645-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="a6645-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="a6645-118">A Microsoft não recomenda usar o plug-in do Windows XR para novos projetos no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="a6645-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="a6645-119">No entanto, se você estiver usando o Unity 2019 e precisar do AR Foundation 2,0 para compatibilidade com dispositivos ARCore/ARKit, esse plug-in permitirá esse suporte.</span><span class="sxs-lookup"><span data-stu-id="a6645-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6645-120">O uso desse plug-in no Unity 2019 não oferece suporte a âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="a6645-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="a6645-121">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="a6645-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="a6645-122">Se você ainda estiver no Unity 2019 ou anterior, a Microsoft recomenda usar o suporte interno a XR herdado.</span><span class="sxs-lookup"><span data-stu-id="a6645-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="a6645-123">Embora o plug-in do Windows XR seja funcional no Unity 2019, não é recomendável porque as âncoras espaciais do Azure não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="a6645-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>