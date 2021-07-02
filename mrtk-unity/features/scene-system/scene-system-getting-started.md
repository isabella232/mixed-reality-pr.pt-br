---
title: Começar a trabalhar com o sistema de cena
description: Página de aterrissagem do sistema de cena com o MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 16adf431498f8146ca2cc60565e59dc8ae03fd92
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177569"
---
# <a name="scene-system-getting-started"></a><span data-ttu-id="f23da-104">Começar a trabalhar com o sistema de cena</span><span class="sxs-lookup"><span data-stu-id="f23da-104">Scene system getting started</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="f23da-105">Quando usar o sistema de cena</span><span class="sxs-lookup"><span data-stu-id="f23da-105">When to use the scene system</span></span>

<span data-ttu-id="f23da-106">Se o projeto consistir em uma única cena, o Sistema de Cena provavelmente não será necessário.</span><span class="sxs-lookup"><span data-stu-id="f23da-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="f23da-107">É mais útil quando um ou mais dos seguintes são verdadeiros:</span><span class="sxs-lookup"><span data-stu-id="f23da-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="f23da-108">Seu projeto tem várias cenas.</span><span class="sxs-lookup"><span data-stu-id="f23da-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="f23da-109">Você está acostumado com o carregamento de cena única, mas não gosta da maneira como ela destrói a instância do MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="f23da-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="f23da-110">Você deseja uma maneira simples de carregar aditivamente várias cenas para construir sua experiência.</span><span class="sxs-lookup"><span data-stu-id="f23da-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="f23da-111">Você deseja uma maneira simples de acompanhar as operações de carga em andamento ou uma maneira simples de controlar a ativação de cena para várias cenas sendo carregadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="f23da-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="f23da-112">Você deseja manter a iluminação consistente e previsível em todas as suas cenas.</span><span class="sxs-lookup"><span data-stu-id="f23da-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="f23da-113">Recursos do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="f23da-113">Scene System Resources</span></span>

<span data-ttu-id="f23da-114">Por padrão, o Sistema de Cena utiliza um par de objetos de cena (cena DefaultManagerScene e DefaultLighting).</span><span class="sxs-lookup"><span data-stu-id="f23da-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="f23da-115">Se qualquer uma dessas cenas não puder ser localizada, uma mensagem será exibida no inspetor de perfil do Sistema de Cena.</span><span class="sxs-lookup"><span data-stu-id="f23da-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Mensagem de recursos padrão](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="f23da-117">! [Observação] Se o projeto estiver usando o gerenciador personalizado e as cenas de iluminação, essa mensagem poderá ser ignorada com segurança.</span><span class="sxs-lookup"><span data-stu-id="f23da-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="f23da-118">As seções a seguir descrevem agora para resolver essa mensagem, com base em qual método foi usado para importar o Toolkit.</span><span class="sxs-lookup"><span data-stu-id="f23da-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="f23da-119">Unity Gerenciador de Pacotes (UPM)</span><span class="sxs-lookup"><span data-stu-id="f23da-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="f23da-120">Nos pacotes upm Toolkit realidade misturada, os recursos do sistema de cena são empacotados como um exemplo.</span><span class="sxs-lookup"><span data-stu-id="f23da-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="f23da-121">Devido a pacotes UPM serem imutáveis, o Unity não poderá abrir o arquivo de cena necessário, a menos que eles sejam explicitamente importados para o projeto.</span><span class="sxs-lookup"><span data-stu-id="f23da-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="f23da-122">Para importar, use as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="f23da-122">To import use the following steps:</span></span>

- <span data-ttu-id="f23da-123">Selecione **Janela**  >  **Gerenciador de Pacotes**</span><span class="sxs-lookup"><span data-stu-id="f23da-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="f23da-124">Selecione **Realidade Misturada Toolkit Foundation**</span><span class="sxs-lookup"><span data-stu-id="f23da-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="f23da-125">Localizar **recursos do sistema de** cena na seção **Exemplos**</span><span class="sxs-lookup"><span data-stu-id="f23da-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Importar recursos do sistema de cena](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="f23da-127">Selecione **Importar**</span><span class="sxs-lookup"><span data-stu-id="f23da-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="f23da-128">Arquivos de ativo (.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="f23da-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="f23da-129">Se a pasta SceneSystemResources tiver sido excluída ou tiver sido deseleitada durante a importação, ela poderá ser recuperada usando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="f23da-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="f23da-130">Selecionar **Pacote** Personalizado  >  **de Importação de**  >  **Ativos**</span><span class="sxs-lookup"><span data-stu-id="f23da-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="f23da-131">Abra o **Microsoft.MixedReality.Toolkit. Pacote foundation**</span><span class="sxs-lookup"><span data-stu-id="f23da-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="f23da-132">Verifique se **Services/SceneSystem/SceneSystemResources** e todas as opções filho estão selecionadas</span><span class="sxs-lookup"><span data-stu-id="f23da-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Reimporte recursos do sistema de cena](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="f23da-134">Selecione **Importar**</span><span class="sxs-lookup"><span data-stu-id="f23da-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="f23da-135">Como usar o sistema de cena</span><span class="sxs-lookup"><span data-stu-id="f23da-135">How to use the scene system</span></span>

- [<span data-ttu-id="f23da-136">Tipos de cena</span><span class="sxs-lookup"><span data-stu-id="f23da-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="f23da-137">Carregamento de cena de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f23da-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="f23da-138">Monitorando o carregamento de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f23da-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="f23da-139">Carregamento de cena de iluminação</span><span class="sxs-lookup"><span data-stu-id="f23da-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="f23da-140">Configurações do editor</span><span class="sxs-lookup"><span data-stu-id="f23da-140">Editor settings</span></span>

<span data-ttu-id="f23da-141">Por padrão, o Sistema de Cena impõe vários comportamentos no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="f23da-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="f23da-142">Se você encontrar qualquer um desses comportamentos com muita mão, eles poderão ser desabilitados na seção **Editor Configurações** do seu perfil do Sistema de Cena.</span><span class="sxs-lookup"><span data-stu-id="f23da-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="f23da-143">`Editor Manage Build Settings:` Se true, o serviço atualizará suas configurações de build automaticamente, garantindo que todas as cenas de gerenciador, iluminação e conteúdo sejam adicionadas.</span><span class="sxs-lookup"><span data-stu-id="f23da-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="f23da-144">Desabilite isso se você quiser ter controle total sobre as configurações de build.</span><span class="sxs-lookup"><span data-stu-id="f23da-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="f23da-145">`Editor Enforce Scene Order:` Se true, o serviço garantirá que a cena do gerente seja exibida primeiro na hierarquia de cena, seguida pela iluminação e, em seguida, pelo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f23da-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="f23da-146">Desabilite isso se você quiser ter controle total sobre a hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="f23da-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="f23da-147">`Editor Manage Loaded Scenes:` Se true, o serviço garantirá que o gerenciador, o conteúdo e as cenas de iluminação sejam sempre carregados.</span><span class="sxs-lookup"><span data-stu-id="f23da-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="f23da-148">Desabilite se você quiser ter controle total sobre quais cenas são carregadas no editor.</span><span class="sxs-lookup"><span data-stu-id="f23da-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="f23da-149">`Editor Enforce Lighting Scene Types:` Se true, o serviço garantirá que somente os componentes relacionados à iluminação definidos em `PermittedLightingSceneComponentTypes` sejam permitidos em cenas de iluminação.</span><span class="sxs-lookup"><span data-stu-id="f23da-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="f23da-150">Desabilite se você quiser controle total sobre o conteúdo das cenas de iluminação.</span><span class="sxs-lookup"><span data-stu-id="f23da-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Configurações do editor do sistema de cena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
