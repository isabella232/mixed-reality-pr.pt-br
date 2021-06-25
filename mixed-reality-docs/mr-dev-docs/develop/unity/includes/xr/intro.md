---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906933"
---
# <a name="openxr"></a>[<span data-ttu-id="167b8-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="167b8-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="167b8-102">O plug-in OpenXR de Realidade Misturada é a recomendação da **Microsoft** para Unity 2020 LTS ou posterior.</span><span class="sxs-lookup"><span data-stu-id="167b8-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="167b8-103">À medida que novos recursos são desenvolvidos no futuro, eles só serão incluídos no plug-in OpenXR de Realidade Misturada no futuro.</span><span class="sxs-lookup"><span data-stu-id="167b8-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="167b8-104">O plug-in OpenXR de Realidade Misturada dá suporte total ao AR Foundation 4.0, fornecendo implementações ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="167b8-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="167b8-105">Isso permite que você escreva um código de raycasting uma vez que abrange os telefones e tablets holoLens 2 e ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="167b8-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="167b8-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="167b8-106">Prerequisites</span></span> 

* <span data-ttu-id="167b8-107">Ferramentas [mais recentes para desenvolvimento do HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="167b8-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="167b8-108">Unity 2020.3 LTS mais recente, (recomendamos 2020.3.8f1 ou superior)</span><span class="sxs-lookup"><span data-stu-id="167b8-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="167b8-109">Versões mínimas</span><span class="sxs-lookup"><span data-stu-id="167b8-109">Minimum versions</span></span>

<span data-ttu-id="167b8-110">As instruções nesta página configurarão você com os requisitos mais recentes e mais recentes do Unity e do OpenXR listados abaixo:</span><span class="sxs-lookup"><span data-stu-id="167b8-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="167b8-111">Plug-in do Unity OpenXR mais recente (recomendamos 1.2 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="167b8-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="167b8-112">Plug-in OpenXR de Realidade Misturada mais recente (recomendamos a versão 1.0.0 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="167b8-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="167b8-113">**(Opcional)** MRTK mais recente(recomendamos a versão 2.7 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="167b8-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="167b8-114">**(Opcional)** Pacote de Pipeline de Renderização Universal mais recente (recomendamos a versão 10.5.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="167b8-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="167b8-115">Se você estiver criando aplicativos de VR no computador Windows, o plug-in OpenXR de Realidade Misturada não será necessariamente necessário.</span><span class="sxs-lookup"><span data-stu-id="167b8-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="167b8-116">No entanto, você deseja instalar o plug-in se estiver personalização do mapeamento do controlador para controladores HP Reverb G2 ou criação de aplicativos que funcionam em headsets HoloLens 2 e VR.</span><span class="sxs-lookup"><span data-stu-id="167b8-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="167b8-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="167b8-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="167b8-118">A Microsoft não recomenda usar o plug-in do Windows XR para novos projetos no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="167b8-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="167b8-119">No entanto, se você estiver usando o Unity 2019 e precisar do AR Foundation 2.0 para compatibilidade com dispositivos ARCore/ARKit, esse plug-in habilita esse suporte.</span><span class="sxs-lookup"><span data-stu-id="167b8-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="167b8-120">O uso desse plug-in no Unity 2019 não dá suporte a Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="167b8-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="167b8-121">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="167b8-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="167b8-122">Se você ainda estiver no Unity 2019 ou anterior, a Microsoft recomenda o uso do suporte a XR integrado herdado.</span><span class="sxs-lookup"><span data-stu-id="167b8-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="167b8-123">Embora o plug-in do Windows XR seja funcional no Unity 2019, não é recomendável porque não há suporte para Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="167b8-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>