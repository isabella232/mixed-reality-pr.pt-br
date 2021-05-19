---
title: Compreensão da cena
description: Descreve a compreensão da cena no MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, compreensão da cena
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143881"
---
# <a name="scene-understanding"></a><span data-ttu-id="82529-104">Compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="82529-104">Scene Understanding</span></span>

<span data-ttu-id="82529-105">O [entendimento da cena](/windows/mixed-reality/scene-understanding) retorna uma representação semântica das entidades de cena, bem como suas formas geométricas no __hololens 2__ (não há suporte para o hololens 1ª gen).</span><span class="sxs-lookup"><span data-stu-id="82529-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="82529-106">Alguns casos de uso esperados dessa tecnologia são:</span><span class="sxs-lookup"><span data-stu-id="82529-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="82529-107">Coloque objetos na superfície mais próxima de um determinado tipo (por exemplo, parede e piso)</span><span class="sxs-lookup"><span data-stu-id="82529-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="82529-108">Construir NAV-malha para jogos de estilo de plataforma</span><span class="sxs-lookup"><span data-stu-id="82529-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="82529-109">Fornecer geometria amigável do mecanismo de física como quatro processadores</span><span class="sxs-lookup"><span data-stu-id="82529-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="82529-110">Acelere o desenvolvimento, evitando a necessidade de escrever algoritmos semelhantes</span><span class="sxs-lookup"><span data-stu-id="82529-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="82529-111">A compreensão da cena está disponível como um recurso __experimental__ a partir do MRTK 2,6.</span><span class="sxs-lookup"><span data-stu-id="82529-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="82529-112">Ele é integrado ao MRTK como um [observador espacial](spatial-awareness-getting-started.md#register-observers) chamado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="82529-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="82529-113">A compreensão da cena funciona tanto com o pipeline de XR herdado quanto com o pipeline do SDK do XR.</span><span class="sxs-lookup"><span data-stu-id="82529-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="82529-114">Em ambos os casos, o `WindowsSceneUnderstandingObserver` é usado.</span><span class="sxs-lookup"><span data-stu-id="82529-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="82529-115">Visão geral do observador</span><span class="sxs-lookup"><span data-stu-id="82529-115">Observer overview</span></span>

<span data-ttu-id="82529-116">Quando solicitado, o retornará [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) com atributos úteis para que o aplicativo entenda seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="82529-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="82529-117">A frequência de observação, o tipo de objeto retornado (por exemplo, parede, piso) e outros comportamentos de observador dependem da configuração do observador por meio do perfil.</span><span class="sxs-lookup"><span data-stu-id="82529-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="82529-118">Por exemplo, se a máscara oclusão for desejada, o observador deverá ser configurado para gerar quatro processadores.</span><span class="sxs-lookup"><span data-stu-id="82529-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="82529-119">A cena observada pode ser salva como um arquivo serializado que pode ser carregado posteriormente para recriar a cena no modo de reprodução do editor.</span><span class="sxs-lookup"><span data-stu-id="82529-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="82529-120">Instalação</span><span class="sxs-lookup"><span data-stu-id="82529-120">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82529-121">Só há suporte para a compreensão da cena no HoloLens 2 e no Unity 2019,4 e superior.</span><span class="sxs-lookup"><span data-stu-id="82529-121">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="82529-122">Verifique se a plataforma está definida como UWP nas configurações de build.</span><span class="sxs-lookup"><span data-stu-id="82529-122">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="82529-123">Adquira o pacote de Compreensão de Cena por meio [da Ferramenta de Recursos de Realidade Misturada](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="82529-123">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="82529-124">Usando a compreensão de cena</span><span class="sxs-lookup"><span data-stu-id="82529-124">Using Scene Understanding</span></span>

<span data-ttu-id="82529-125">A maneira mais rápida de começar a entender a cena é conferir a cena de exemplo.</span><span class="sxs-lookup"><span data-stu-id="82529-125">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="82529-126">Cena de exemplo de Compreensão de Cena</span><span class="sxs-lookup"><span data-stu-id="82529-126">Scene Understanding sample scene</span></span>

<span data-ttu-id="82529-127">No Unity, use o Explorador de Projeto para abrir o arquivo de cena no `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e pressione Reproduzir!</span><span class="sxs-lookup"><span data-stu-id="82529-127">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82529-128">Ao usar a Ferramenta de Recursos de Realidade Misturada ou importar por meio de UPM, importe o exemplo Demonstrações – SpatialAwareness antes de importar o exemplo Experimental - SceneUnderstanding devido a um problema de dependência.</span><span class="sxs-lookup"><span data-stu-id="82529-128">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="82529-129">Confira este [problema do GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="82529-129">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

<span data-ttu-id="82529-130">A cena demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="82529-130">The scene demonstrates the following:</span></span>

* <span data-ttu-id="82529-131">Visualização de objetos de cena observados com na interface do usuário do aplicativo para configurar o observador</span><span class="sxs-lookup"><span data-stu-id="82529-131">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="82529-132">Script `DemoSceneUnderstandingController` de exemplo que mostra como alterar as configurações do observador e escutar eventos relevantes</span><span class="sxs-lookup"><span data-stu-id="82529-132">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="82529-133">Salvando dados de cena no dispositivo para desenvolvimento offline</span><span class="sxs-lookup"><span data-stu-id="82529-133">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="82529-134">Carregando dados de cena salvos anteriormente (arquivos .bytes) para dar suporte ao fluxo de trabalho de desenvolvimento no editor</span><span class="sxs-lookup"><span data-stu-id="82529-134">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="82529-135">A cena de exemplo é baseada no pipeline XR herdado.</span><span class="sxs-lookup"><span data-stu-id="82529-135">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="82529-136">Se você estiver usando o pipeline do SDK do XR, deverá modificar os perfis de acordo.</span><span class="sxs-lookup"><span data-stu-id="82529-136">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="82529-137">O perfil do Sistema de Reconhecimento Espacial de Reconhecimento de Cena fornecido ( ) e os perfis de Observador de Reconhecimento de Cena ( e `DemoSceneUnderstandingSystemProfile` ) funcionam para ambos os `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` pipelines.</span><span class="sxs-lookup"><span data-stu-id="82529-137">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="82529-138">Configurando o serviço observador</span><span class="sxs-lookup"><span data-stu-id="82529-138">Configuring the observer service</span></span>

<span data-ttu-id="82529-139">Selecione o objeto de jogo 'MixedRealityToolkit' e verifique o inspetor.</span><span class="sxs-lookup"><span data-stu-id="82529-139">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![local de compreensão de cena na hierarquia](../images/spatial-awareness/MRTKHierarchy.png)

![Local do MRTK no inspetor](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="82529-142">Essas opções permitirão que um configure o `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="82529-142">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="82529-143">Script de exemplo</span><span class="sxs-lookup"><span data-stu-id="82529-143">Example script</span></span>

<span data-ttu-id="82529-144">O script de exemplo _DemoSceneUnderstandingController. cs_ demonstra os principais conceitos do trabalho com o serviço de compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="82529-144">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="82529-145">Inscrevendo-se nos eventos de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="82529-145">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="82529-146">Lidando com eventos de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="82529-146">Handling Scene Understanding events</span></span>
* <span data-ttu-id="82529-147">Configurando o `WindowsSceneUnderstandingObserver` em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="82529-147">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="82529-148">As alternâncias no painel na cena alteram o comportamento do observador de compreensão da cena chamando funções públicas deste script de exemplo.</span><span class="sxs-lookup"><span data-stu-id="82529-148">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="82529-149">Ativar a *instanciação de pré-fabricados*, demonstrará a criação de objetos cujo tamanho se ajusta a todos os [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), coletados de forma organizada em um objeto pai.</span><span class="sxs-lookup"><span data-stu-id="82529-149">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![opções do controlador de demonstração](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="82529-151">Notas de aplicativo criadas</span><span class="sxs-lookup"><span data-stu-id="82529-151">Built app notes</span></span>

<span data-ttu-id="82529-152">Crie e implante no HoloLens da maneira padrão.</span><span class="sxs-lookup"><span data-stu-id="82529-152">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="82529-153">Uma vez em execução, vários botões devem aparecer para brincar com os recursos.</span><span class="sxs-lookup"><span data-stu-id="82529-153">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="82529-154">Observe que há algum pit que está fazendo consultas ao observador.</span><span class="sxs-lookup"><span data-stu-id="82529-154">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="82529-155">A configuração incorreta de um resultado de solicitação de busca na carga do evento que não contém os dados esperados.</span><span class="sxs-lookup"><span data-stu-id="82529-155">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="82529-156">Por exemplo, se um não solicitar quádruplos, nenhuma textura de máscara oclusão estará presente.</span><span class="sxs-lookup"><span data-stu-id="82529-156">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="82529-157">Como inteligente, nenhuma malha do mundo será exibida se o observador não estiver configurado para solicitar malhas.</span><span class="sxs-lookup"><span data-stu-id="82529-157">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="82529-158">O `DemoSceneUnderstandingController` script cuida de algumas dessas dependências, mas nem todas.</span><span class="sxs-lookup"><span data-stu-id="82529-158">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="82529-159">Os arquivos de cena salvos podem ser acessados por meio do [portal do dispositivo](/windows/mixed-reality/using-the-windows-device-portal) em `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="82529-159">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="82529-160">Esses arquivos de cena podem ser usados no editor especificando-os no perfil observador encontrado no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="82529-160">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Local do portal do dispositivo-arquivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de cena serializados no observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="82529-163">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="82529-163">See Also</span></span>

* [<span data-ttu-id="82529-164">Visão geral do WMR do mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="82529-164">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="82529-165">Visão geral do WMR do mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="82529-165">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding-sdk)