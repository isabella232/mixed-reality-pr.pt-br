---
title: Como usar o Gerenciador de Pacotes do Unity
description: Usando o MRTK no Gerenciador de pacotes do Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, pacotes MRTK,
ms.openlocfilehash: e3e7a2d06cd38d7a9e8daf579f1a312904a86280
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345069"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a><span data-ttu-id="400c5-104">Kit de ferramentas de realidade misturada e Gerenciador de pacotes do Unity</span><span class="sxs-lookup"><span data-stu-id="400c5-104">Mixed Reality Toolkit and Unity Package Manager</span></span>

<span data-ttu-id="400c5-105">A partir da versão 2.5.0, usando a [ferramenta de funcionalidade Mixed Reality](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), o Microsoft Mixed Reality Toolkit integra-se com o UPM (Gerenciador de pacotes do Unity) ao usar o Unity 2019,4 e mais recente.</span><span class="sxs-lookup"><span data-stu-id="400c5-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="400c5-106">Como usar a Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="400c5-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="400c5-107">Conforme descrito em [Bem-vindo à ferramenta de funcionalidade de realidade misturada](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) , você pode baixar a ferramenta usando [esse link](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="400c5-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="400c5-108">Se o manifesto do projeto tiver uma `Microsoft Mixed Reality` entrada na `scopedRegistries` seção, é recomendável que ele seja removido.</span><span class="sxs-lookup"><span data-stu-id="400c5-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="400c5-109">Para remover um registro com escopo configurado, acesse para `Edit`  >  `Project Settings`  >  `Package Manager` .</span><span class="sxs-lookup"><span data-stu-id="400c5-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![Removendo registro com escopo](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="400c5-111">Os pacotes MRTK aparecem sob o `Mixed Reality Toolkit` título ao descobrir recursos.</span><span class="sxs-lookup"><span data-stu-id="400c5-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![Descobrir recursos](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="400c5-113">Ao selecionar recursos, não há necessidade de se preocupar com as dependências necessárias, a ferramenta irá baixá-las e integrá-las automaticamente no projeto.</span><span class="sxs-lookup"><span data-stu-id="400c5-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![Dependências necessárias](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="400c5-115">Gerenciando recursos mistos de realidade com o Gerenciador de pacotes do Unity</span><span class="sxs-lookup"><span data-stu-id="400c5-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="400c5-116">Depois que um pacote do kit de ferramentas da realidade misturada tiver sido adicionado ao manifesto do pacote, ele poderá ser gerenciado usando a interface do usuário do Gerenciador de pacotes do Unity.</span><span class="sxs-lookup"><span data-stu-id="400c5-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![Pacote UPM do MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="400c5-118">Se um pacote do kit de ferramentas da realidade misturada for removido usando o Gerenciador de pacotes do Unity, ele precisará ser adicionado novamente usando as [etapas descritas anteriormente](#using-the-mixed-reality-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="400c5-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="400c5-119">Usando exemplos do kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="400c5-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="400c5-120">Ao contrário do uso de arquivos de pacote de ativos (. unitypackage) `com.microsoft.mixedreality.toolkit.examples` e `com.microsoft.mixedreality.toolkit.handphysicsservice` não importam automaticamente as cenas de exemplo e os ativos.</span><span class="sxs-lookup"><span data-stu-id="400c5-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="400c5-121">Para utilizar um ou mais dos exemplos, use as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="400c5-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="400c5-122">No editor do Unity, navegue até `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="400c5-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="400c5-123">Na lista de pacotes, selecione `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="400c5-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="400c5-124">Localize os exemplos desejados na `Samples` lista</span><span class="sxs-lookup"><span data-stu-id="400c5-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="400c5-125">Clique em `Import into Project`</span><span class="sxs-lookup"><span data-stu-id="400c5-125">Click `Import into Project`</span></span>

![Importando amostras](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="400c5-127">Quando um pacote de exemplo é atualizado, o Unity fornece a opção de atualizar amostras importadas.</span><span class="sxs-lookup"><span data-stu-id="400c5-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="400c5-128">A atualização de um exemplo importado substituirá as alterações feitas nesse exemplo e nos ativos associados.</span><span class="sxs-lookup"><span data-stu-id="400c5-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="400c5-129">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="400c5-129">See Also</span></span>

- [<span data-ttu-id="400c5-130">Pacotes do kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="400c5-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)