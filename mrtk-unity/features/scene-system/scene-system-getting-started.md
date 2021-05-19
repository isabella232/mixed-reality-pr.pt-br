---
title: Introdução ao sistema de cena
description: Página de aterrissagem do sistema de cena com o MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144306"
---
# <a name="scene-system-overview"></a><span data-ttu-id="ccbf7-104">Visão geral do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="ccbf7-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="ccbf7-105">Quando usar o sistema de cena</span><span class="sxs-lookup"><span data-stu-id="ccbf7-105">When to use the scene system</span></span>

<span data-ttu-id="ccbf7-106">Se o projeto consistir em uma única cena, o Sistema de Cena provavelmente não será necessário.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="ccbf7-107">É mais útil quando um ou mais dos seguintes são verdadeiros:</span><span class="sxs-lookup"><span data-stu-id="ccbf7-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="ccbf7-108">Seu projeto tem várias cenas.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="ccbf7-109">Você está acostumado com o carregamento de cena única, mas não gosta da maneira como ela destrói a instância do MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="ccbf7-110">Você deseja uma maneira simples de carregar aditivamente várias cenas para construir sua experiência.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="ccbf7-111">Você deseja uma maneira simples de acompanhar as operações de carga em andamento ou uma maneira simples de controlar a ativação de cena para várias cenas sendo carregadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="ccbf7-112">Você deseja manter a iluminação consistente e previsível em todas as suas cenas.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="ccbf7-113">Recursos do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="ccbf7-113">Scene System Resources</span></span>

<span data-ttu-id="ccbf7-114">Por padrão, o Sistema de Cena utiliza um par de objetos de cena (cena DefaultManagerScene e DefaultLighting).</span><span class="sxs-lookup"><span data-stu-id="ccbf7-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="ccbf7-115">Se qualquer uma dessas cenas não puder ser localizada, uma mensagem será exibida no inspetor de perfil do Sistema de Cena.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Mensagem de recursos padrão](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="ccbf7-117">! [Observação] Se o projeto estiver usando o gerenciador personalizado e as cenas de iluminação, essa mensagem poderá ser ignorada com segurança.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="ccbf7-118">As seções a seguir descrevem agora para resolver essa mensagem, com base em qual método foi usado para importar o Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="ccbf7-119">Unity Gerenciador de Pacotes (UPM)</span><span class="sxs-lookup"><span data-stu-id="ccbf7-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="ccbf7-120">Nos pacotes UPM do Kit de Ferramentas de Realidade Misturada, os recursos do sistema de cena são empacotados como um exemplo.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="ccbf7-121">Devido a pacotes UPM serem imutáveis, o Unity não poderá abrir o arquivo de cena necessário, a menos que eles sejam explicitamente importados para o projeto.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="ccbf7-122">Para importar, use as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ccbf7-122">To import use the following steps:</span></span>

- <span data-ttu-id="ccbf7-123">Selecionar   >  **Gerenciador de pacotes** do Windows</span><span class="sxs-lookup"><span data-stu-id="ccbf7-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="ccbf7-124">Selecione **Mixed Reality Toolkit Foundation**</span><span class="sxs-lookup"><span data-stu-id="ccbf7-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="ccbf7-125">Localizar **recursos do sistema de cena** na seção de **exemplos**</span><span class="sxs-lookup"><span data-stu-id="ccbf7-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Importar recursos do sistema de cena](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="ccbf7-127">Selecionar **importação**</span><span class="sxs-lookup"><span data-stu-id="ccbf7-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="ccbf7-128">Arquivos de ativo (. unitypackage)</span><span class="sxs-lookup"><span data-stu-id="ccbf7-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="ccbf7-129">Se a pasta SceneSystemResources tiver sido excluída ou tiver sido desmarcada durante a importação, ela poderá ser recuperada usando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ccbf7-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="ccbf7-130">Selecione os **ativos** pacote de  >  **importação** pacote  >  **personalizado**</span><span class="sxs-lookup"><span data-stu-id="ccbf7-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="ccbf7-131">Abra o pacote **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="ccbf7-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="ccbf7-132">Verifique se os **Serviços/SceneSystem/SceneSystemResources** e todas as opções filho estão selecionadas</span><span class="sxs-lookup"><span data-stu-id="ccbf7-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Reimportar recursos do sistema de cena](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="ccbf7-134">Selecionar **importação**</span><span class="sxs-lookup"><span data-stu-id="ccbf7-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="ccbf7-135">Como usar o sistema de cena</span><span class="sxs-lookup"><span data-stu-id="ccbf7-135">How to use the scene system</span></span>

- [<span data-ttu-id="ccbf7-136">Tipos de cena</span><span class="sxs-lookup"><span data-stu-id="ccbf7-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="ccbf7-137">Carregamento de cena de conteúdo</span><span class="sxs-lookup"><span data-stu-id="ccbf7-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="ccbf7-138">Monitorando o carregamento de conteúdo</span><span class="sxs-lookup"><span data-stu-id="ccbf7-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="ccbf7-139">Carregamento da cena de iluminação</span><span class="sxs-lookup"><span data-stu-id="ccbf7-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="ccbf7-140">Configurações do editor</span><span class="sxs-lookup"><span data-stu-id="ccbf7-140">Editor settings</span></span>

<span data-ttu-id="ccbf7-141">Por padrão, o sistema de cena impõe vários comportamentos no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="ccbf7-142">Se você encontrar qualquer um desses comportamentos de alta mão, eles poderão ser desabilitados na seção **configurações do editor** do seu perfil de sistema de cena.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="ccbf7-143">`Editor Manage Build Settings:` Se for true, o serviço atualizará as configurações de Build automaticamente, garantindo que todas as cenas de gerente, iluminação e conteúdo sejam adicionadas.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="ccbf7-144">Desabilite-o se desejar ter controle total sobre as configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="ccbf7-145">`Editor Enforce Scene Order:` Se for true, o serviço garantirá que a cena do gerente seja exibida primeiro na hierarquia de cena, seguida da iluminação e do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="ccbf7-146">Desabilite-o se desejar ter controle total sobre a hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="ccbf7-147">`Editor Manage Loaded Scenes:` Se for verdadeiro, o serviço garantirá que os bastidores gerente, conteúdo e iluminação sempre sejam carregados.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="ccbf7-148">Desabilite se você quiser o controle total sobre quais cenas são carregadas no editor.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="ccbf7-149">`Editor Enforce Lighting Scene Types:` Se for true, o serviço garantirá que apenas os componentes relacionados à iluminação definidos no `PermittedLightingSceneComponentTypes` sejam permitidos em cenas de iluminação.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="ccbf7-150">Desabilite se você quiser controle total sobre o conteúdo de cenas de iluminação.</span><span class="sxs-lookup"><span data-stu-id="ccbf7-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Configurações do editor do sistema de cena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
