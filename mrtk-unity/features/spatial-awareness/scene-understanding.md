---
title: Noções básicas sobre a cena
description: descreve a compreensão de cena no MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Compreensão de cena
ms.openlocfilehash: 1ed6f93216fc90e7c6332f2b9c40911d25d96d2a
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743548"
---
# <a name="scene-understanding"></a><span data-ttu-id="788b7-104">Noções básicas sobre a cena</span><span class="sxs-lookup"><span data-stu-id="788b7-104">Scene Understanding</span></span>

<span data-ttu-id="788b7-105">[O Entendimento de](/windows/mixed-reality/scene-understanding) Cena retorna uma representação semântica de entidades de cena, bem como suas formas __geométricas no HoloLens 2__ (não há suporte para o HoloLens 1st Gen).</span><span class="sxs-lookup"><span data-stu-id="788b7-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="788b7-106">Alguns casos de uso esperados dessa tecnologia são:</span><span class="sxs-lookup"><span data-stu-id="788b7-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="788b7-107">Colocar objetos na superfície mais próxima de um determinado tipo (por exemplo, parede e piso)</span><span class="sxs-lookup"><span data-stu-id="788b7-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="788b7-108">Construir nav-mesh para jogos de estilo de plataforma</span><span class="sxs-lookup"><span data-stu-id="788b7-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="788b7-109">Fornecer geometria amigável do mecanismo de física como quads</span><span class="sxs-lookup"><span data-stu-id="788b7-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="788b7-110">Acelerar o desenvolvimento evitando a necessidade de escrever algoritmos semelhantes</span><span class="sxs-lookup"><span data-stu-id="788b7-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="788b7-111">O Entendimento de Cena é introduzido __como um recurso experimental__ no MRTK 2.6.</span><span class="sxs-lookup"><span data-stu-id="788b7-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="788b7-112">Ele é integrado ao MRTK como um [observador espacial](spatial-awareness-getting-started.md#register-observers) chamado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="788b7-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="788b7-113">O Entendimento de Cena funciona com o pipeline XR herdado e o pipeline do SDK do XR (tanto o OpenXR (a partir do MRTK 2.7) quanto o Plug-in do Windows XR.</span><span class="sxs-lookup"><span data-stu-id="788b7-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="788b7-114">Em ambos os `WindowsSceneUnderstandingObserver` casos, o é usado.</span><span class="sxs-lookup"><span data-stu-id="788b7-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="788b7-115">Não há suporte para o uso da Compreensão de Cena em Remoting.</span><span class="sxs-lookup"><span data-stu-id="788b7-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="788b7-116">Visão geral do observador</span><span class="sxs-lookup"><span data-stu-id="788b7-116">Observer overview</span></span>

<span data-ttu-id="788b7-117">Quando solicitado, o [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) retornará [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) com atributos úteis para o aplicativo entender seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="788b7-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="788b7-118">A frequência de observação, o tipo de objeto retornado (por exemplo, parede, piso) e outros comportamentos de observador dependem da configuração do observador por meio do perfil.</span><span class="sxs-lookup"><span data-stu-id="788b7-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="788b7-119">Por exemplo, se a máscara de oclusão for desejada, o observador deverá ser configurado para gerar quads.</span><span class="sxs-lookup"><span data-stu-id="788b7-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="788b7-120">A cena observada pode ser salva como um arquivo serializado que pode ser carregado posteriormente para recriar a cena no modo de reprodução do editor.</span><span class="sxs-lookup"><span data-stu-id="788b7-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="788b7-121">Instalação</span><span class="sxs-lookup"><span data-stu-id="788b7-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="788b7-122">O Entendimento de Cena só tem suporte no HoloLens 2 e no Unity 2019.4 e superior.</span><span class="sxs-lookup"><span data-stu-id="788b7-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="788b7-123">Verifique se a plataforma está definida como UWP nas configurações de build.</span><span class="sxs-lookup"><span data-stu-id="788b7-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="788b7-124">Adquira o pacote de Compreensão de Cena por meio [da Ferramenta de Recursos de Realidade Misturada](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="788b7-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="788b7-125">Usando a compreensão de cena</span><span class="sxs-lookup"><span data-stu-id="788b7-125">Using Scene Understanding</span></span>

<span data-ttu-id="788b7-126">A maneira mais rápida de começar a entender a cena é conferir a cena de exemplo.</span><span class="sxs-lookup"><span data-stu-id="788b7-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="788b7-127">Cena de exemplo de Compreensão de Cena</span><span class="sxs-lookup"><span data-stu-id="788b7-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="788b7-128">No Unity, use o Explorador de Projeto para abrir o arquivo de cena no `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e pressione Reproduzir!</span><span class="sxs-lookup"><span data-stu-id="788b7-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="788b7-129">Aplica-se somente ao MRTK 2.6.0 – ao usar a Ferramenta de Recursos de Realidade Misturada ou importar por meio de UPM, importe o exemplo Demonstrações – SpatialAwareness antes de importar a amostra Experimental - SceneUnderstanding devido a um problema de dependência.</span><span class="sxs-lookup"><span data-stu-id="788b7-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="788b7-130">Confira este [problema do GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="788b7-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="788b7-131">A cena demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="788b7-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="788b7-132">Visualização de objetos de cena observados com na interface do usuário do aplicativo para configurar o observador</span><span class="sxs-lookup"><span data-stu-id="788b7-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="788b7-133">Script `DemoSceneUnderstandingController` de exemplo que mostra como alterar as configurações do observador e escutar eventos relevantes</span><span class="sxs-lookup"><span data-stu-id="788b7-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="788b7-134">Salvando dados de cena no dispositivo para desenvolvimento offline</span><span class="sxs-lookup"><span data-stu-id="788b7-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="788b7-135">Carregando dados de cena salvos anteriormente (arquivos .bytes) para dar suporte ao fluxo de trabalho de desenvolvimento no editor</span><span class="sxs-lookup"><span data-stu-id="788b7-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="788b7-136">Por padrão, `ShouldLoadFromFile` a propriedade do observador é definida como false.</span><span class="sxs-lookup"><span data-stu-id="788b7-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="788b7-137">Para ver a visualização de uma sala de exemplo serializada, consulte a seção configurando o serviço [observador](#configuring-the-observer-service) abaixo e de definir a propriedade como true no editor.</span><span class="sxs-lookup"><span data-stu-id="788b7-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="788b7-138">A cena de exemplo é baseada no pipeline XR herdado.</span><span class="sxs-lookup"><span data-stu-id="788b7-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="788b7-139">Se você estiver usando o pipeline do SDK do XR, deverá modificar os perfis de acordo.</span><span class="sxs-lookup"><span data-stu-id="788b7-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="788b7-140">O perfil do Sistema de Reconhecimento Espacial de Reconhecimento de Cena fornecido ( ) e os perfis de Observador de Reconhecimento de Cena ( e `DemoSceneUnderstandingSystemProfile` ) funcionam para ambos os `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` pipelines.</span><span class="sxs-lookup"><span data-stu-id="788b7-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="788b7-141">A cena de exemplo registra um `There is no active AsyncCoroutineRunner when an action is posted.` aviso sob determinada circunstância devido à ordem de inicialização/execução do thread.</span><span class="sxs-lookup"><span data-stu-id="788b7-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="788b7-142">Se você puder confirmar que o componente está anexado ao GameObject "Controlador de Demonstração" e o `AsyncCoroutineRunner` componente/GameObject permanecer habilitado/ativo na cena (o caso padrão), o aviso poderá ser ignorado com segurança.</span><span class="sxs-lookup"><span data-stu-id="788b7-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="788b7-143">Configurando o serviço observador</span><span class="sxs-lookup"><span data-stu-id="788b7-143">Configuring the observer service</span></span>

<span data-ttu-id="788b7-144">Selecione o objeto de jogo 'MixedRealityToolkit' e verifique o inspetor.</span><span class="sxs-lookup"><span data-stu-id="788b7-144">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![local de compreensão de cena na hierarquia](../images/spatial-awareness/MRTKHierarchy.png)

![Local do MRTK no inspetor](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="788b7-147">Essas opções permitirão que um configure o `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="788b7-147">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="788b7-148">Script de exemplo</span><span class="sxs-lookup"><span data-stu-id="788b7-148">Example script</span></span>

<span data-ttu-id="788b7-149">O script de _exemplo DemoSceneUnderstandingController.cs_ demonstra os principais conceitos em trabalhar com o serviço de Compreensão de Cena.</span><span class="sxs-lookup"><span data-stu-id="788b7-149">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="788b7-150">Assinando eventos de Compreensão de Cena</span><span class="sxs-lookup"><span data-stu-id="788b7-150">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="788b7-151">Manipulando eventos de Compreensão de Cena</span><span class="sxs-lookup"><span data-stu-id="788b7-151">Handling Scene Understanding events</span></span>
* <span data-ttu-id="788b7-152">Configurando o `WindowsSceneUnderstandingObserver` em runtime</span><span class="sxs-lookup"><span data-stu-id="788b7-152">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="788b7-153">As alternâncias no painel na cena alteram o comportamento do observador de compreensão da cena chamando funções públicas deste script de exemplo.</span><span class="sxs-lookup"><span data-stu-id="788b7-153">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="788b7-154">A *acionamento de Pré-fabs* de Instanência demonstrará a criação de objetos desse tamanho para se ajustarem a todos [os SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), coletados perfeitamente em um objeto pai.</span><span class="sxs-lookup"><span data-stu-id="788b7-154">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![opções do controlador de demonstração](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="788b7-156">Notas de aplicativo criadas</span><span class="sxs-lookup"><span data-stu-id="788b7-156">Built app notes</span></span>

<span data-ttu-id="788b7-157">Crie e implante no HoloLens da maneira padrão.</span><span class="sxs-lookup"><span data-stu-id="788b7-157">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="788b7-158">Uma vez em execução, vários botões devem parecer reproduzir com os recursos.</span><span class="sxs-lookup"><span data-stu-id="788b7-158">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="788b7-159">Observe que há algumas quedas na busca de consultas para o observador.</span><span class="sxs-lookup"><span data-stu-id="788b7-159">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="788b7-160">A configuração inefigurada de uma solicitação de busca resulta na falta de conteúdo do evento que contém os dados esperados.</span><span class="sxs-lookup"><span data-stu-id="788b7-160">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="788b7-161">Por exemplo, se um não solicitar quads, nenhuma textura de máscara de oclusão estará presente.</span><span class="sxs-lookup"><span data-stu-id="788b7-161">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="788b7-162">Da mesma forma, nenhuma malha mundial será exibida se o observador não estiver configurado para solicitar malhas.</span><span class="sxs-lookup"><span data-stu-id="788b7-162">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="788b7-163">O `DemoSceneUnderstandingController` script cuida de algumas dessas dependências, mas não de todas.</span><span class="sxs-lookup"><span data-stu-id="788b7-163">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="788b7-164">Os arquivos de cena salvos podem ser acessados por meio do [portal do dispositivo](/windows/mixed-reality/using-the-windows-device-portal) em `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="788b7-164">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="788b7-165">Esses arquivos de cena podem ser usados no editor especificando-os no perfil de observador encontrado no inspetor.</span><span class="sxs-lookup"><span data-stu-id="788b7-165">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Portal de Dispositivos local do arquivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de cena serializados no observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="788b7-168">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="788b7-168">See Also</span></span>

* [<span data-ttu-id="788b7-169">Visão geral do Entendimento de Cena</span><span class="sxs-lookup"><span data-stu-id="788b7-169">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="788b7-170">Visão geral do SDK de Compreensão de Cena</span><span class="sxs-lookup"><span data-stu-id="788b7-170">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)