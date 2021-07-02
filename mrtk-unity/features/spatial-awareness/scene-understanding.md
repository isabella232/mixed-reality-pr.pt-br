---
title: Observador de compreensão da cena
description: Descreve a compreensão da cena no MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, compreensão da cena
ms.openlocfilehash: d5430e7885055a550347c4ccebc1452f68125922
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176228"
---
# <a name="scene-understanding-observer"></a><span data-ttu-id="cd7ff-104">Observador de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="cd7ff-104">Scene understanding observer</span></span>

<span data-ttu-id="cd7ff-105">o [entendimento da cena](/windows/mixed-reality/scene-understanding) retorna uma representação semântica das entidades de cena, bem como suas formas geométricas no __HoloLens 2__ (HoloLens 1ª Gen não tem suporte).</span><span class="sxs-lookup"><span data-stu-id="cd7ff-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="cd7ff-106">Alguns casos de uso esperados dessa tecnologia são:</span><span class="sxs-lookup"><span data-stu-id="cd7ff-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="cd7ff-107">Coloque objetos na superfície mais próxima de um determinado tipo (por exemplo, parede e piso)</span><span class="sxs-lookup"><span data-stu-id="cd7ff-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="cd7ff-108">Construir NAV-malha para jogos de estilo de plataforma</span><span class="sxs-lookup"><span data-stu-id="cd7ff-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="cd7ff-109">Fornecer geometria amigável do mecanismo de física como quatro processadores</span><span class="sxs-lookup"><span data-stu-id="cd7ff-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="cd7ff-110">Acelere o desenvolvimento, evitando a necessidade de escrever algoritmos semelhantes</span><span class="sxs-lookup"><span data-stu-id="cd7ff-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="cd7ff-111">A compreensão da cena é introduzida como um recurso __experimental__ no MRTK 2,6.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="cd7ff-112">Ele é integrado ao MRTK como um [observador espacial](spatial-awareness-getting-started.md#register-observers) chamado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="cd7ff-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="cd7ff-113">a compreensão da cena funciona tanto com o pipeline do xr herdado quanto com o pipeline do SDK do xr (OpenXR (a partir do MRTK 2,7) e o plug-in Windows xr).</span><span class="sxs-lookup"><span data-stu-id="cd7ff-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="cd7ff-114">Em ambos os casos, o `WindowsSceneUnderstandingObserver` é usado.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="cd7ff-115">Não há suporte para o uso da compreensão da cena em comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="cd7ff-116">Visão geral do observador</span><span class="sxs-lookup"><span data-stu-id="cd7ff-116">Observer overview</span></span>

<span data-ttu-id="cd7ff-117">Quando solicitado, o retornará [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) com atributos úteis para que o aplicativo entenda seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="cd7ff-118">A frequência de observação, o tipo de objeto retornado (por exemplo, parede, piso) e outros comportamentos de observador dependem da configuração do observador por meio do perfil.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="cd7ff-119">Por exemplo, se a máscara oclusão for desejada, o observador deverá ser configurado para gerar quatro processadores.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="cd7ff-120">A cena observada pode ser salva como um arquivo serializado que pode ser carregado posteriormente para recriar a cena no modo de reprodução do editor.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="cd7ff-121">Instalação</span><span class="sxs-lookup"><span data-stu-id="cd7ff-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd7ff-122">só há suporte para a compreensão da cena no HoloLens 2 e no Unity 2019,4 e superior.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="cd7ff-123">Verifique se a plataforma está definida para UWP nas configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="cd7ff-124">Adquira o pacote de compreensão da cena por meio da [ferramenta de funcionalidade de realidade misturada](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="cd7ff-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="cd7ff-125">Usando a compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="cd7ff-125">Using Scene Understanding</span></span>

<span data-ttu-id="cd7ff-126">A maneira mais rápida de começar a entender a cena é conferir a cena de exemplo.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="cd7ff-127">Exemplo de cena de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="cd7ff-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="cd7ff-128">no Unity, use o Project Explorer para abrir o arquivo de cena no `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e pressione reproduzir!</span><span class="sxs-lookup"><span data-stu-id="cd7ff-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="cd7ff-129">Aplica-se somente a MRTK 2.6.0-ao usar a ferramenta de funcionalidade Mixed Reality ou, de outra forma, importar por meio de UPM, importe o exemplo de demonstrações-SpatialAwareness antes de importar o exemplo experimental-SceneUnderstanding devido a um problema de dependência.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="cd7ff-130">consulte [este GitHub problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="cd7ff-131">A cena demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cd7ff-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="cd7ff-132">Visualização de objetos de cena observados com o na interface do usuário do aplicativo para configurar o observador</span><span class="sxs-lookup"><span data-stu-id="cd7ff-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="cd7ff-133">Exemplo de `DemoSceneUnderstandingController` script que mostra como alterar as configurações de observador e ouvir eventos relevantes</span><span class="sxs-lookup"><span data-stu-id="cd7ff-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="cd7ff-134">Salvando dados de cena no dispositivo para desenvolvimento offline</span><span class="sxs-lookup"><span data-stu-id="cd7ff-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="cd7ff-135">Carregando dados de cena salvos anteriormente (arquivos. bytes) para dar suporte ao fluxo de trabalho de desenvolvimento no editor</span><span class="sxs-lookup"><span data-stu-id="cd7ff-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd7ff-136">Por padrão, a `ShouldLoadFromFile` Propriedade do observador é definida como false.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="cd7ff-137">Para ver a visualização de uma sala de amostra serializada, consulte a seção [Configurando o serviço observador](#configuring-the-observer-service) abaixo e defina a propriedade como true no editor.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="cd7ff-138">A cena de exemplo se baseia no pipeline de XR herdado.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="cd7ff-139">Se você estiver usando o pipeline do SDK do XR, deverá modificar os perfis de acordo.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="cd7ff-140">A cena fornecida compreendendo o perfil do sistema de conscientização espacial ( `DemoSceneUnderstandingSystemProfile` ) e a cena que entende os perfis de observadores ( `DefaultSceneUnderstandingObserverProfile` e `DemoSceneUnderstandingObserverProfile` ) funciona para ambos os pipelines.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="cd7ff-141">A cena de exemplo registra um `There is no active AsyncCoroutineRunner when an action is posted.` aviso em determinadas circunstâncias devido à ordem de execução do thread/inicialização.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="cd7ff-142">Se você puder confirmar se o `AsyncCoroutineRunner` componente está anexado ao gameobject "controlador de demonstração" e o componente/gameobject permanecer habilitado/ativo na cena (o caso padrão), o aviso poderá ser ignorado com segurança.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span> <span data-ttu-id="cd7ff-143">**No entanto, ao criar uma nova cena com a compreensão da cena, certifique-se de criar um gameobject vazio na raiz e anexar o `AsyncCoroutineRunner` script a ele, caso contrário, a compreensão da cena pode não funcionar corretamente.**</span><span class="sxs-lookup"><span data-stu-id="cd7ff-143">**However, when creating a new scene with Scene Understanding please make sure to create an empty GameObject at root and attach the `AsyncCoroutineRunner` script to it, otherwise Scene Understanding may not function properly.**</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="cd7ff-144">Configurando o serviço observador</span><span class="sxs-lookup"><span data-stu-id="cd7ff-144">Configuring the observer service</span></span>

<span data-ttu-id="cd7ff-145">Selecione o objeto de jogo ' MixedRealityToolkit ' e verifique o Inspetor.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-145">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![local de compreensão da cena na hierarquia](../images/spatial-awareness/MRTKHierarchy.png)

![Local do MRTK no Inspetor](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="cd7ff-148">Essas opções permitirão que um configure o `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="cd7ff-148">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="cd7ff-149">Script de exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7ff-149">Example script</span></span>

<span data-ttu-id="cd7ff-150">O script de exemplo _DemoSceneUnderstandingController. cs_ demonstra os principais conceitos do trabalho com o serviço de compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-150">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="cd7ff-151">Inscrevendo-se nos eventos de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="cd7ff-151">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="cd7ff-152">Lidando com eventos de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="cd7ff-152">Handling Scene Understanding events</span></span>
* <span data-ttu-id="cd7ff-153">Configurando o `WindowsSceneUnderstandingObserver` em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="cd7ff-153">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="cd7ff-154">As alternâncias no painel na cena alteram o comportamento do observador de compreensão da cena chamando funções públicas deste script de exemplo.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-154">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="cd7ff-155">Ativar a *instanciação de pré-fabricados*, demonstrará a criação de objetos cujo tamanho se ajusta a todos os [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), coletados de forma organizada em um objeto pai.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-155">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![opções do controlador de demonstração](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="cd7ff-157">Notas de aplicativo criadas</span><span class="sxs-lookup"><span data-stu-id="cd7ff-157">Built app notes</span></span>

<span data-ttu-id="cd7ff-158">crie e implante o HoloLens da maneira padrão.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-158">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="cd7ff-159">Uma vez em execução, vários botões devem aparecer para brincar com os recursos.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-159">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="cd7ff-160">Observe que há algum pit que está fazendo consultas ao observador.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-160">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="cd7ff-161">A configuração incorreta de um resultado de solicitação de busca na carga do evento que não contém os dados esperados.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-161">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="cd7ff-162">Por exemplo, se um não solicitar quádruplos, nenhuma textura de máscara oclusão estará presente.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-162">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="cd7ff-163">Como inteligente, nenhuma malha do mundo será exibida se o observador não estiver configurado para solicitar malhas.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-163">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="cd7ff-164">O `DemoSceneUnderstandingController` script cuida de algumas dessas dependências, mas nem todas.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-164">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="cd7ff-165">Os arquivos de cena salvos podem ser acessados por meio do [portal do dispositivo](/windows/mixed-reality/using-the-windows-device-portal) em `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="cd7ff-165">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="cd7ff-166">Esses arquivos de cena podem ser usados no editor especificando-os no perfil observador encontrado no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="cd7ff-166">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Local do portal do dispositivo-arquivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de cena serializados no observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="cd7ff-169">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="cd7ff-169">See Also</span></span>

* [<span data-ttu-id="cd7ff-170">Visão geral de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="cd7ff-170">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="cd7ff-171">Visão geral do SDK de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="cd7ff-171">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)
