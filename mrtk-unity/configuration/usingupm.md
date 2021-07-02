---
title: Como usar o Gerenciador de Pacotes do Unity
description: Usando o MRTK no Unity Gerenciador de Pacotes
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, Pacotes MRTK,
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177318"
---
# <a name="using-the-unity-package-manager"></a><span data-ttu-id="3b7c0-104">Como usar o Gerenciador de Pacotes do Unity</span><span class="sxs-lookup"><span data-stu-id="3b7c0-104">Using the Unity Package Manager</span></span>

<span data-ttu-id="3b7c0-105">A partir da versão 2.5.0, usando a Ferramenta de Recursos de Realidade Misturada [,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)o Microsoft Mixed Reality Toolkit se integra ao UNITY Gerenciador de Pacotes (UPM) ao usar o Unity 2019.4 e mais recente.</span><span class="sxs-lookup"><span data-stu-id="3b7c0-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="3b7c0-106">Como usar a Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="3b7c0-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="3b7c0-107">Conforme descrito em [Bem-vindo à Ferramenta de Recursos de Realidade](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) Misturada, você pode baixar a ferramenta usando este [link](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="3b7c0-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3b7c0-108">Se o manifesto do projeto tiver uma `Microsoft Mixed Reality` entrada na seção , é `scopedRegistries` recomendável que ele seja removido.</span><span class="sxs-lookup"><span data-stu-id="3b7c0-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="3b7c0-109">Para remover um registro com escopo configurado, acesse `Edit`  >  `Project Settings`  >  `Package Manager` .</span><span class="sxs-lookup"><span data-stu-id="3b7c0-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![Removendo o registro com escopo](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="3b7c0-111">Os pacotes do MRTK aparecem sob `Mixed Reality Toolkit` o título ao descobrir recursos.</span><span class="sxs-lookup"><span data-stu-id="3b7c0-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![Descobrir recursos](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="3b7c0-113">Ao selecionar recursos, não é necessário se preocupar com as dependências necessárias, a ferramenta baixará e as integrará automaticamente ao projeto.</span><span class="sxs-lookup"><span data-stu-id="3b7c0-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![Dependências necessárias](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="3b7c0-115">Gerenciando recursos de Realidade Misturada com o Gerenciador de Pacotes</span><span class="sxs-lookup"><span data-stu-id="3b7c0-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="3b7c0-116">Depois que um pacote Toolkit de Realidade Misturada tiver sido adicionado ao manifesto do pacote, ele poderá ser gerenciado usando a interface do usuário Gerenciador de Pacotes Unity.</span><span class="sxs-lookup"><span data-stu-id="3b7c0-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![Pacote UPM do MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="3b7c0-118">Se um pacote de Toolkit realidade misturada for removido usando o Gerenciador de Pacotes Unity, ele terá que ser adicionado de novo usando as etapas [descritas anteriormente.](#using-the-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="3b7c0-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="3b7c0-119">Usando exemplos de Toolkit realidade misturada</span><span class="sxs-lookup"><span data-stu-id="3b7c0-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="3b7c0-120">Ao contrário de usar arquivos de pacote de ativos (.unitypackage) e `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` não importar automaticamente as cenas de exemplo e os ativos.</span><span class="sxs-lookup"><span data-stu-id="3b7c0-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="3b7c0-121">Para utilizar um ou mais exemplos, use as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="3b7c0-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="3b7c0-122">No Editor do Unity, navegue até `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="3b7c0-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="3b7c0-123">Na lista de pacotes, selecione `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="3b7c0-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="3b7c0-124">Localizar os exemplos desejados na `Samples` lista</span><span class="sxs-lookup"><span data-stu-id="3b7c0-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="3b7c0-125">Clique em `Import into Project`</span><span class="sxs-lookup"><span data-stu-id="3b7c0-125">Click `Import into Project`</span></span>

![Importando exemplos](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="3b7c0-127">Quando um pacote de exemplo é atualizado, o Unity fornece a opção de atualizar exemplos importados.</span><span class="sxs-lookup"><span data-stu-id="3b7c0-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="3b7c0-128">Atualizar um exemplo importado substituirá as alterações feitas nesse exemplo e nos ativos associados.</span><span class="sxs-lookup"><span data-stu-id="3b7c0-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b7c0-129">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3b7c0-129">See Also</span></span>

- [<span data-ttu-id="3b7c0-130">Pacotes de Toolkit realidade misturada</span><span class="sxs-lookup"><span data-stu-id="3b7c0-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)
