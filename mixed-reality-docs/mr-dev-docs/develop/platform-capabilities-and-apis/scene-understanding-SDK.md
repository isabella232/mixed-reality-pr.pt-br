---
title: SDK de compreensão de cena
description: Saiba como instalar e usar o SDK de Compreensão de Cena, incluindo componentes, malhas e objetos em aplicativos de realidade misturada.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Compreensão de cena, mapeamento espacial, Windows Mixed Reality, Unity
ms.openlocfilehash: dee561e49a9457aa35c44037f4573caaefd00f2a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449725"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="24da6-104">Visão geral do SDK de compreensão de cena</span><span class="sxs-lookup"><span data-stu-id="24da6-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="24da6-105">A compreensão de cena transforma os dados de sensor de ambiente não estruturados que seu dispositivo de Realidade Misturada captura e os converte em uma representação abstrata poderosa.</span><span class="sxs-lookup"><span data-stu-id="24da6-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="24da6-106">O SDK atua como a camada de comunicação entre seu aplicativo e o runtime de Compreensão de Cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="24da6-107">Ele tem como objetivo imitar constructos padrão existentes, como grafos de cena 3D para representações 3D e retângulos e painéis 2D para aplicativos 2D.</span><span class="sxs-lookup"><span data-stu-id="24da6-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="24da6-108">Embora os constructos de Noções básicas de cena mapeiem para estruturas concretas, em geral SceneUnderstanding é uma estrutura agnóstica, permitindo interoperabilidade entre estruturas variadas que interagem com ele.</span><span class="sxs-lookup"><span data-stu-id="24da6-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="24da6-109">À medida que o Entendimento de Cena evolui, a função do SDK é garantir que novas representações e funcionalidades continuem sendo expostas em uma estrutura unificada.</span><span class="sxs-lookup"><span data-stu-id="24da6-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="24da6-110">Neste documento, primeiro apresentaremos conceitos de alto nível que ajudarão você a se familiarizar com o ambiente/uso de desenvolvimento e, em seguida, fornecer uma documentação mais detalhada para classes e constructos específicos.</span><span class="sxs-lookup"><span data-stu-id="24da6-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="24da6-111">Onde posso obter o SDK?</span><span class="sxs-lookup"><span data-stu-id="24da6-111">Where do I get the SDK?</span></span>

<span data-ttu-id="24da6-112">O SDK SceneUnderstanding pode ser baixado por meio da [Ferramenta de Recursos de Realidade Misturada](../unity/welcome-to-mr-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="24da6-112">The SceneUnderstanding SDK is downloadable via the [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md).</span></span>

<span data-ttu-id="24da6-113">**Observação:** a versão mais recente depende dos pacotes de visualização e você precisará habilitar pacotes de pré-lançamento para vê-los.</span><span class="sxs-lookup"><span data-stu-id="24da6-113">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="24da6-114">Para a versão 0.5.2022-rc e posterior, o Scene Understanding dá suporte a projeções de linguagem para C# e C++, permitindo que aplicativos desenvolvam aplicativos para plataformas Win32 ou UWP.</span><span class="sxs-lookup"><span data-stu-id="24da6-114">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="24da6-115">A partir desta versão, o SceneUnderstanding dá suporte ao unity no editor, que é usado exclusivamente para se comunicar com o HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="24da6-115">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="24da6-116">SceneUnderstanding requer SDK do Windows versão 18362 ou superior.</span><span class="sxs-lookup"><span data-stu-id="24da6-116">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

## <a name="conceptual-overview"></a><span data-ttu-id="24da6-117">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="24da6-117">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="24da6-118">A cena</span><span class="sxs-lookup"><span data-stu-id="24da6-118">The Scene</span></span>

<span data-ttu-id="24da6-119">Seu dispositivo de realidade misturada está constantemente integrando informações sobre o que ele vê em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="24da6-119">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="24da6-120">O Entendimento de Cena funila todas essas fontes de dados e produz uma única abstração coesiva.</span><span class="sxs-lookup"><span data-stu-id="24da6-120">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="24da6-121">O Entendimento de Cena gera Cenas, que são uma composição de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representam uma instância de uma única coisa (por exemplo, uma parede/teto/piso.) Os próprios Objetos de Cena são uma composição de [SceneComponents, que representam partes mais granulares que compõe esse SceneObject.</span><span class="sxs-lookup"><span data-stu-id="24da6-121">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="24da6-122">Exemplos de componentes são quads e malhas, mas no futuro podem representar caixas delimitadores, malhas de colisão, metadados etc.</span><span class="sxs-lookup"><span data-stu-id="24da6-122">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="24da6-123">O processo de conversão dos dados brutos do sensor em uma cena é uma operação potencialmente cara que pode levar segundos para espaços médios (~10x10m) em minutos para espaços grandes (~50 x 50 m) e, portanto, não é algo que está sendo calculado pelo dispositivo sem solicitação de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24da6-123">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="24da6-124">Em vez disso, a geração de cena é disparada pelo aplicativo sob demanda.</span><span class="sxs-lookup"><span data-stu-id="24da6-124">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="24da6-125">A classe SceneObserver tem métodos estáticos que podem computar ou desserializar uma cena, com a qual você pode enumerar/interagir.</span><span class="sxs-lookup"><span data-stu-id="24da6-125">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="24da6-126">A ação "Computação" é executada sob demanda e executada na CPU, mas em um processo separado (o Driver de Realidade Misturada).</span><span class="sxs-lookup"><span data-stu-id="24da6-126">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="24da6-127">No entanto, enquanto fazemos a computação em outro processo, os dados de Cena resultantes são armazenados e mantidos em seu aplicativo no objeto Scene.</span><span class="sxs-lookup"><span data-stu-id="24da6-127">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="24da6-128">Veja abaixo um diagrama que ilustra esse fluxo de processo e mostra exemplos de dois aplicativos intercalando com o runtime de Compreensão de Cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-128">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagrama de processo](images/SU-ProcessFlow.png)

<span data-ttu-id="24da6-130">No lado esquerdo, há um diagrama do runtime de realidade misturada, que está sempre ligado e em execução em seu próprio processo.</span><span class="sxs-lookup"><span data-stu-id="24da6-130">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="24da6-131">Esse runtime é responsável por executar o rastreamento de dispositivos, o mapeamento espacial e outras operações que o Entendimento de Cena usa para entender e a razão sobre o mundo ao seu redor.</span><span class="sxs-lookup"><span data-stu-id="24da6-131">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="24da6-132">No lado direito do diagrama, mostramos dois aplicativos teóricos que usam o Entendimento de Cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-132">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="24da6-133">A primeira interface do aplicativo com o MRTK, que usa o SDK de Compreensão de Cena internamente, o segundo aplicativo calcula e usa duas instâncias de cena separadas.</span><span class="sxs-lookup"><span data-stu-id="24da6-133">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="24da6-134">Todas as três cenas neste diagrama geram instâncias distintas das cenas, o driver não está acompanhando o estado global que é compartilhado entre aplicativos e objetos de cena em uma cena não são encontrados em outra.</span><span class="sxs-lookup"><span data-stu-id="24da6-134">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="24da6-135">O Entendimento de Cena fornece um mecanismo para acompanhar ao longo do tempo, mas isso é feito usando o SDK.</span><span class="sxs-lookup"><span data-stu-id="24da6-135">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="24da6-136">O código de acompanhamento já está em execução no SDK no processo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24da6-136">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="24da6-137">Como cada Cena armazena seus dados no espaço de memória do aplicativo, você pode supor que todas as funções do objeto Scene ou seus dados internos sempre são executadas no processo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24da6-137">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="24da6-138">Layout</span><span class="sxs-lookup"><span data-stu-id="24da6-138">Layout</span></span>

<span data-ttu-id="24da6-139">Para trabalhar com o Entendimento de Cena, pode ser valioso saber e entender como o runtime representa componentes logicamente e fisicamente.</span><span class="sxs-lookup"><span data-stu-id="24da6-139">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="24da6-140">A Cena representa dados com um layout específico que foi escolhido para ser simples, mantendo uma estrutura subjacente que é responsável por atender aos requisitos futuros sem a necessidade de revisões principais.</span><span class="sxs-lookup"><span data-stu-id="24da6-140">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="24da6-141">A cena faz isso ao armazenar todos os Componentes (blocos de construção para todos os Objetos de Cena) em uma lista simples e definir hierarquia e composição por meio de referências em que componentes específicos referenciam outros.</span><span class="sxs-lookup"><span data-stu-id="24da6-141">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="24da6-142">Abaixo, apresentamos um exemplo de uma estrutura em sua forma simples e lógica.</span><span class="sxs-lookup"><span data-stu-id="24da6-142">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="24da6-143">Layout lógico</span><span class="sxs-lookup"><span data-stu-id="24da6-143">Logical Layout</span></span></th><th><span data-ttu-id="24da6-144">Layout Físico</span><span class="sxs-lookup"><span data-stu-id="24da6-144">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="24da6-145">Cena</span><span class="sxs-lookup"><span data-stu-id="24da6-145">Scene</span></span>
  <ul>
  <li><span data-ttu-id="24da6-146">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="24da6-146">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="24da6-147">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="24da6-147">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="24da6-148">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="24da6-148">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="24da6-149">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="24da6-149">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="24da6-150">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="24da6-150">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="24da6-151">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="24da6-151">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="24da6-152">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="24da6-152">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="24da6-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="24da6-153">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="24da6-154">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="24da6-154">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="24da6-155">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="24da6-155">SceneObject_1</span></span></li>
  <li><span data-ttu-id="24da6-156">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="24da6-156">SceneObject_2</span></span></li>
  <li><span data-ttu-id="24da6-157">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="24da6-157">SceneObject_3</span></span></li>
  <li><span data-ttu-id="24da6-158">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="24da6-158">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="24da6-159">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="24da6-159">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="24da6-160">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="24da6-160">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="24da6-161">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="24da6-161">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="24da6-162">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="24da6-162">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="24da6-163">Esta ilustração destaca a diferença entre o layout físico e lógico da cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-163">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="24da6-164">À esquerda, vemos o layout hierárquico dos dados que seu aplicativo vê ao enumerar a cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-164">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="24da6-165">À direita, vemos que a cena é composta por 12 componentes distintos que podem ser acessados individualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="24da6-165">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="24da6-166">Ao processar uma nova cena, esperamos que os aplicativos andem nessa hierarquia logicamente, no entanto, ao acompanhar entre atualizações de cena, alguns aplicativos só podem estar interessados em direcionar componentes específicos que são compartilhados entre duas cenas.</span><span class="sxs-lookup"><span data-stu-id="24da6-166">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="24da6-167">Visão geral da API</span><span class="sxs-lookup"><span data-stu-id="24da6-167">API overview</span></span>

<span data-ttu-id="24da6-168">A seção a seguir fornece uma visão geral de alto nível dos constructos no Entendimento de Cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-168">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="24da6-169">Ler esta seção lhe dará uma compreensão de como as cenas são representadas e para que os vários componentes fazem/são usados.</span><span class="sxs-lookup"><span data-stu-id="24da6-169">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="24da6-170">A próxima seção fornecerá exemplos de código concreto e detalhes adicionais que são relemplados nesta visão geral.</span><span class="sxs-lookup"><span data-stu-id="24da6-170">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="24da6-171">Todos os tipos descritos abaixo residem no `Microsoft.MixedReality.SceneUnderstanding` namespace .</span><span class="sxs-lookup"><span data-stu-id="24da6-171">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="24da6-172">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="24da6-172">SceneComponents</span></span>

<span data-ttu-id="24da6-173">Agora que você entende o layout lógico das cenas, agora podemos apresentar o conceito de SceneComponents e como eles são usados para compor a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="24da6-173">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="24da6-174">SceneComponents são as decomposições mais granulares em SceneUnderstanding representando uma única coisa de núcleo, por exemplo, uma malha ou um quad ou uma caixa delimitador.</span><span class="sxs-lookup"><span data-stu-id="24da6-174">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="24da6-175">SceneComponents são coisas que podem ser atualizadas independentemente e podem ser referenciadas por outros SceneComponents, portanto, eles têm uma única propriedade global uma ID exclusiva, que permitem esse tipo de mecanismo de acompanhamento/referência.</span><span class="sxs-lookup"><span data-stu-id="24da6-175">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="24da6-176">As IDs são usadas para a composição lógica da hierarquia de cena, bem como para persistência de objeto (o ato de atualizar uma cena em relação à outra.)</span><span class="sxs-lookup"><span data-stu-id="24da6-176">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="24da6-177">Se você estiver tratando cada cena computada recentemente como distinta e simplesmente enumerando todos os dados dentro dela, as IDs serão amplamente transparentes para você.</span><span class="sxs-lookup"><span data-stu-id="24da6-177">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="24da6-178">No entanto, se você estiver planejando acompanhar componentes em várias atualizações, usará as IDs para indexar e localizar SceneComponents entre objetos Scene.</span><span class="sxs-lookup"><span data-stu-id="24da6-178">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="24da6-179">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="24da6-179">SceneObjects</span></span>

<span data-ttu-id="24da6-180">Um SceneObject é um SceneComponent que representa uma instância de uma "coisa", por exemplo, uma parede, um piso, um teto etc.... expressa por sua propriedade Kind.</span><span class="sxs-lookup"><span data-stu-id="24da6-180">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="24da6-181">SceneObjects são geométricos e, portanto, têm funções e propriedades que representam sua localização no espaço, no entanto, eles não contêm nenhuma estrutura geométrica ou lógica.</span><span class="sxs-lookup"><span data-stu-id="24da6-181">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="24da6-182">Em vez disso, SceneObjects fazem referência a outros SceneComponents, especificamente SceneQuads e SceneMeshes, que fornecem as diversas representações com suporte pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="24da6-182">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="24da6-183">Quando uma nova cena é computada, seu aplicativo provavelmente enumerará os SceneObjects da cena para processar o que ele está interessado.</span><span class="sxs-lookup"><span data-stu-id="24da6-183">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="24da6-184">SceneObjects pode ter qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="24da6-184">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="24da6-185">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="24da6-185">SceneObjectKind</span></span></th> <th><span data-ttu-id="24da6-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="24da6-186">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="24da6-187">Segundo plano</span><span class="sxs-lookup"><span data-stu-id="24da6-187">Background</span></span></td><td><span data-ttu-id="24da6-188">O SceneObject é conhecido por não <b>ser</b> um dos outros tipos reconhecidos de objeto de cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-188">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="24da6-189">Essa classe não deve ser confundida com Desconhecido, em que Background é conhecido por não ser parede/piso/forro etc.... embora desconhecido ainda não seja categorizado.</span><span class="sxs-lookup"><span data-stu-id="24da6-189">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="24da6-190">Parede</span><span class="sxs-lookup"><span data-stu-id="24da6-190">Wall</span></span></td><td><span data-ttu-id="24da6-191">Uma parede física.</span><span class="sxs-lookup"><span data-stu-id="24da6-191">A physical wall.</span></span> <span data-ttu-id="24da6-192">Supõe-se que as paredes sejam estruturas ambientais removíveis.</span><span class="sxs-lookup"><span data-stu-id="24da6-192">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="24da6-193">Piso</span><span class="sxs-lookup"><span data-stu-id="24da6-193">Floor</span></span></td><td><span data-ttu-id="24da6-194">Os pisos são qualquer superfície na qual se pode andar.</span><span class="sxs-lookup"><span data-stu-id="24da6-194">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="24da6-195">Observação: os pisos não são pisos.</span><span class="sxs-lookup"><span data-stu-id="24da6-195">Note: stairs aren't floors.</span></span> <span data-ttu-id="24da6-196">Observe também que os pisos assumem qualquer superfície walkable e, portanto, não há suposição explícita de um piso singular.</span><span class="sxs-lookup"><span data-stu-id="24da6-196">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="24da6-197">Estruturas de vários níveis, rampas etc.... deve todos classificar como andar.</span><span class="sxs-lookup"><span data-stu-id="24da6-197">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="24da6-198">Ceiling</span><span class="sxs-lookup"><span data-stu-id="24da6-198">Ceiling</span></span></td><td><span data-ttu-id="24da6-199">A superfície superior de uma sala.</span><span class="sxs-lookup"><span data-stu-id="24da6-199">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="24da6-200">Plataforma</span><span class="sxs-lookup"><span data-stu-id="24da6-200">Platform</span></span></td><td><span data-ttu-id="24da6-201">Uma grande superfície plana na qual você pode colocar hologramas.</span><span class="sxs-lookup"><span data-stu-id="24da6-201">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="24da6-202">Elas tendem a representar tabelas, contratops e outras superfícies horizontais grandes.</span><span class="sxs-lookup"><span data-stu-id="24da6-202">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="24da6-203">World (Mundo)</span><span class="sxs-lookup"><span data-stu-id="24da6-203">World</span></span></td><td><span data-ttu-id="24da6-204">Um rótulo reservado para dados geométricos que é independente da rotulagem.</span><span class="sxs-lookup"><span data-stu-id="24da6-204">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="24da6-205">A malha gerada definindo o sinalizador de atualização EnableWorldMesh seria classificada como mundo.</span><span class="sxs-lookup"><span data-stu-id="24da6-205">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="24da6-206">Unknown</span><span class="sxs-lookup"><span data-stu-id="24da6-206">Unknown</span></span></td><td><span data-ttu-id="24da6-207">Esse objeto de cena ainda precisa ser classificado e atribuído a um tipo.</span><span class="sxs-lookup"><span data-stu-id="24da6-207">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="24da6-208">Isso não deve ser confundido com Background, pois esse objeto pode ser qualquer coisa, o sistema ainda não teve uma classificação forte o suficiente para ele.</span><span class="sxs-lookup"><span data-stu-id="24da6-208">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="24da6-209">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="24da6-209">SceneMesh</span></span>

<span data-ttu-id="24da6-210">Um SceneMesh é um SceneComponent que aproxima a geometria de objetos geométricos arbitrários usando uma lista de triângulos.</span><span class="sxs-lookup"><span data-stu-id="24da6-210">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="24da6-211">SceneMeshes são usadas em vários contextos diferentes, elas podem representar componentes da estrutura de célula com água ou como o WorldMesh, que representa a malha de mapeamento espacial não associada à Cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-211">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="24da6-212">Os dados de índice e vértice fornecidos com cada malha usam o mesmo layout familiar que os buffers de [vértice](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) e índice usados para renderizar malhas de triângulo em todas as APIs de renderização moderna.</span><span class="sxs-lookup"><span data-stu-id="24da6-212">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="24da6-213">No Entendimento de Cena, as malhas usam índices de 32 bits e podem precisar ser divididas em partes para determinados mecanismos de renderização.</span><span class="sxs-lookup"><span data-stu-id="24da6-213">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="24da6-214">Ordem de vento e sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="24da6-214">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="24da6-215">Espera-se que todas as malhas produzidas pelo Entendimento de Cena retornem malhas em um Right-Handed de coordenadas usando a ordem de vento no sentido horário.</span><span class="sxs-lookup"><span data-stu-id="24da6-215">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="24da6-216">Observação: os builds do sistema operacional anteriores a .191105 podem ter um bug conhecido em que as malhas "World" estavam retornando em uma ordem de Counter-Clockwise que foi corrigida posteriormente.</span><span class="sxs-lookup"><span data-stu-id="24da6-216">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="24da6-217">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="24da6-217">SceneQuad</span></span>

<span data-ttu-id="24da6-218">Um SceneQuad é um SceneComponent que representa superfícies 2d que ocupam o mundo 3d.</span><span class="sxs-lookup"><span data-stu-id="24da6-218">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="24da6-219">SceneQuads pode ser usado da mesma forma que os planos ARKit ARPlaneAnchor ou ARCore, mas oferecem mais funcionalidade de alto nível como telas 2d a serem usadas por aplicativos simples ou UX aumentada.</span><span class="sxs-lookup"><span data-stu-id="24da6-219">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="24da6-220">APIs específicas 2D são fornecidas para quads que fazem com que o posicionamento e o layout sejam simples de usar e o desenvolvimento (com exceção da renderização) com quads deve ser mais semelhante a trabalhar com telas 2d do que malhas 3d.</span><span class="sxs-lookup"><span data-stu-id="24da6-220">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="24da6-221">Forma SceneQuad</span><span class="sxs-lookup"><span data-stu-id="24da6-221">SceneQuad shape</span></span>

<span data-ttu-id="24da6-222">SceneQuads define uma superfície retangular limitada em 2d.</span><span class="sxs-lookup"><span data-stu-id="24da6-222">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="24da6-223">No entanto, SceneQuads está representando superfícies com formas arbitrárias e potencialmente complexas (por exemplo, uma tabela em forma de rosca).) Para representar a forma complexa da superfície de um quad, você pode usar a API GetSurfaceMask para renderizar a forma da superfície em um buffer de imagem que você fornecer.</span><span class="sxs-lookup"><span data-stu-id="24da6-223">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="24da6-224">Se o SceneObject que tem o quad também tiver uma malha, os triângulos de malha deverão ser equivalentes a essa imagem renderizada, ambos representarão a geometria real da superfície, em coordenadas 2d ou 3d.</span><span class="sxs-lookup"><span data-stu-id="24da6-224">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="24da6-225">Referência e detalhes do SDK de compreensão de cena</span><span class="sxs-lookup"><span data-stu-id="24da6-225">Scene understanding SDK details and reference</span></span>

> [!NOTE] 
> <span data-ttu-id="24da6-226">Ao usar o MRTK, observe que você interagirá com o MRTK e, portanto, poderá ignorar esta seção [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) na maioria das circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="24da6-226">When using MRTK, please note you will be interacting with MRTK's [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) and thus may skip this section under most circumstances.</span></span> <span data-ttu-id="24da6-227">Consulte os documentos de [Compreensão de cena do MRTK para](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="24da6-227">Please refer to the [MRTK Scene Understanding docs](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) for more information.</span></span>

<span data-ttu-id="24da6-228">A seção a seguir ajudará você a se familiarizar com os conceitos básicos de SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="24da6-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="24da6-229">Esta seção deve fornecer os conceitos básicos, em que ponto você deve ter contexto suficiente para navegar pelos aplicativos de exemplo para ver como SceneUnderstanding é usado holisticamente.</span><span class="sxs-lookup"><span data-stu-id="24da6-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="24da6-230">Inicialização</span><span class="sxs-lookup"><span data-stu-id="24da6-230">Initialization</span></span>

<span data-ttu-id="24da6-231">A primeira etapa para trabalhar com SceneUnderstanding é que seu aplicativo obtenha referência a um objeto Scene.</span><span class="sxs-lookup"><span data-stu-id="24da6-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="24da6-232">Isso pode ser feito de uma das duas maneiras, uma Cena pode ser calculada pelo driver ou uma cena existente que foi computada no passado pode ser des serializada.</span><span class="sxs-lookup"><span data-stu-id="24da6-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="24da6-233">O último é útil para trabalhar com SceneUnderstanding durante o desenvolvimento, em que aplicativos e experiências podem ser protótipos rapidamente sem um dispositivo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="24da6-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="24da6-234">As cenas são computadas usando um SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="24da6-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="24da6-235">Antes de criar uma Cena, seu aplicativo deve consultar seu dispositivo para garantir que ele seja compatível com SceneUnderstanding, bem como solicitar acesso ao usuário para obter informações de que SceneUnderstanding precisa.</span><span class="sxs-lookup"><span data-stu-id="24da6-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="24da6-236">Se RequestAccessAsync() não for chamado, a computação de uma nova cena falhará.</span><span class="sxs-lookup"><span data-stu-id="24da6-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="24da6-237">Em seguida, calcularemos uma nova cena que está enraizada em torno do headset de Realidade Misturada e tem um raio de 10 metros.</span><span class="sxs-lookup"><span data-stu-id="24da6-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="24da6-238">Inicialização de dados (também conhecida como .</span><span class="sxs-lookup"><span data-stu-id="24da6-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="24da6-239">o Caminho do PC)</span><span class="sxs-lookup"><span data-stu-id="24da6-239">the PC Path)</span></span>

<span data-ttu-id="24da6-240">Embora cenas possam ser computadas para consumo direto, elas também podem ser computadas em formato serializado para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="24da6-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="24da6-241">Isso se mostrou útil para o desenvolvimento, pois permite que os desenvolvedores trabalhem e testem o Entendimento de Cena sem a necessidade de um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="24da6-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="24da6-242">O ato de serializar uma cena é quase idêntico ao computá-la, os dados são retornados ao seu aplicativo em vez de serem desserlizados localmente pelo SDK.</span><span class="sxs-lookup"><span data-stu-id="24da6-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="24da6-243">Em seguida, você pode deserializá-lo por conta própria ou salvá-lo para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="24da6-243">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="24da6-244">Enumeração SceneObject</span><span class="sxs-lookup"><span data-stu-id="24da6-244">SceneObject Enumeration</span></span>

<span data-ttu-id="24da6-245">Agora que seu aplicativo tem uma cena, seu aplicativo estará observando e interagindo com SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="24da6-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="24da6-246">Isso é feito acessando a **propriedade SceneObjects:**</span><span class="sxs-lookup"><span data-stu-id="24da6-246">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="24da6-247">Componentes de atualização e refinação</span><span class="sxs-lookup"><span data-stu-id="24da6-247">Component update and refinding components</span></span>

<span data-ttu-id="24da6-248">Há outra função que recupera componentes na cena chamada ***FindComponent***.</span><span class="sxs-lookup"><span data-stu-id="24da6-248">There's another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="24da6-249">Essa função é útil ao atualizar objetos de rastreamento e encontrá-los em cenas posteriores.</span><span class="sxs-lookup"><span data-stu-id="24da6-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="24da6-250">O código a seguir calculará uma nova cena em relação a uma cena anterior e, em seguida, encontrará o chão na nova cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="24da6-251">Acessando malhas e quads de objetos de cena</span><span class="sxs-lookup"><span data-stu-id="24da6-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="24da6-252">Depois que SceneObjects for encontrado, seu aplicativo provavelmente deseja acessar os dados contidos nos quads/malhas dos que ele é composto.</span><span class="sxs-lookup"><span data-stu-id="24da6-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="24da6-253">Esses dados são acessados com as propriedades \***Quads** _ e _ \*_Malhas_\*\*.</span><span class="sxs-lookup"><span data-stu-id="24da6-253">This data is accessed with the ***Quads** _ and _ *_Meshes_** properties.</span></span> <span data-ttu-id="24da6-254">O código a seguir enumerará todos os quads e malhas de nosso objeto de piso.</span><span class="sxs-lookup"><span data-stu-id="24da6-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="24da6-255">Observe que é o SceneObject que tem a transformação relativa à origem da cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="24da6-256">Isso porque SceneObject representa uma instância de uma "coisa" e é localizado no espaço, os quads e malhas representam a geometria que é transformada em relação ao pai.</span><span class="sxs-lookup"><span data-stu-id="24da6-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="24da6-257">É possível que SceneObjects separados referenciam o mesmo SceneMesh/SceneQuad SceneComponents e também é possível que um SceneObject tenha mais de um SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="24da6-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="24da6-258">Lidando com as transformação</span><span class="sxs-lookup"><span data-stu-id="24da6-258">Dealing with Transforms</span></span>

<span data-ttu-id="24da6-259">O Entendimento de Cena fez uma tentativa deliberada de alinhar-se com representações de cena 3D tradicionais ao lidar com as transformação.</span><span class="sxs-lookup"><span data-stu-id="24da6-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="24da6-260">Portanto, cada cena é limitada a um único sistema de coordenadas, assim como as representações ambientais 3D mais comuns.</span><span class="sxs-lookup"><span data-stu-id="24da6-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="24da6-261">Cada SceneObjects fornece sua localização em relação a esse sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="24da6-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="24da6-262">Se seu aplicativo estiver lidando com Cenas que estendem o limite do que uma única origem fornece, ele poderá ancorar SceneObjects a SpatialAnchors ou gerar várias cenas e mesclá-las, mas, para simplificar, pressupomos que as cenas de water watereger existam em sua própria origem localizada por um NodeId definido por Scene.OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="24da6-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="24da6-263">O código do Unity a seguir, por exemplo, mostra como usar o Windows Perception e as APIs do Unity para alinhar sistemas de coordenadas juntos.</span><span class="sxs-lookup"><span data-stu-id="24da6-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="24da6-264">Consulte [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) para obter detalhes sobre as APIs do Windows Perception e objetos nativos de Realidade Misturada no [Unity](/windows/mixed-reality/unity-xrdevice-advanced) para obter detalhes sobre como obter um SpatialCoordinateSystem que corresponde à origem do mundo do Unity.</span><span class="sxs-lookup"><span data-stu-id="24da6-264">See [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](/windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

<span data-ttu-id="24da6-265">Cada `SceneObject` tem uma transformação, que é aplicada a esse objeto.</span><span class="sxs-lookup"><span data-stu-id="24da6-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="24da6-266">No Unity, convertemos em coordenadas à direita e atribuímos as transformação locais da mesma forma:</span><span class="sxs-lookup"><span data-stu-id="24da6-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a><span data-ttu-id="24da6-267">Quad</span><span class="sxs-lookup"><span data-stu-id="24da6-267">Quad</span></span>

<span data-ttu-id="24da6-268">Os quads foram projetados para ajudar cenários de posicionamento 2D e devem ser pensados como extensões para elementos de UX de tela 2D.</span><span class="sxs-lookup"><span data-stu-id="24da6-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="24da6-269">Embora Os quads sejam componentes de SceneObjects e possam ser renderizados em 3D, as PRÓPRIAS APIs Quad pressupom que Quads são estruturas 2D.</span><span class="sxs-lookup"><span data-stu-id="24da6-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="24da6-270">Eles oferecem informações como extensão, forma e fornecem APIs para posicionamento.</span><span class="sxs-lookup"><span data-stu-id="24da6-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="24da6-271">Quads têm extensão retangular, mas representam superfícies 2D formaadas arbitrariamente.</span><span class="sxs-lookup"><span data-stu-id="24da6-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="24da6-272">Para habilitar o posicionamento nessas superfícies 2D que interagem com os quads de ambiente 3D oferecem utilitários para tornar essa interação possível.</span><span class="sxs-lookup"><span data-stu-id="24da6-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="24da6-273">Atualmente, o Reconhecimento de Cena fornece duas dessas funções, **FindCentermostPlacement** e **GetSurfaceMask.**</span><span class="sxs-lookup"><span data-stu-id="24da6-273">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetSurfaceMask**.</span></span> <span data-ttu-id="24da6-274">FindCentermostPlacement é uma API de alto nível que localiza uma posição no quad em que um objeto pode ser colocado e tentará encontrar o melhor local para o objeto, garantindo que a caixa delimitada que você fornecer permaneça na superfície subjacente.</span><span class="sxs-lookup"><span data-stu-id="24da6-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="24da6-275">As coordenadas da saída são relativas ao quad em "espaço quad" com o canto superior esquerdo sendo (x = 0, y = 0), assim como seria com outros tipos de Rect do Windows.</span><span class="sxs-lookup"><span data-stu-id="24da6-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="24da6-276">Certifique-se de levar isso em conta ao trabalhar com as origens de seus próprios objetos.</span><span class="sxs-lookup"><span data-stu-id="24da6-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="24da6-277">O exemplo a seguir mostra como localizar o local mais centralizável e ancorar um holograma no quad.</span><span class="sxs-lookup"><span data-stu-id="24da6-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="24da6-278">As etapas 1 a 4 são altamente dependentes de sua estrutura/implementação específica, mas os temas devem ser semelhantes.</span><span class="sxs-lookup"><span data-stu-id="24da6-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="24da6-279">É importante observar que o Quad simplesmente representa um plano 2D limitado localizado no espaço.</span><span class="sxs-lookup"><span data-stu-id="24da6-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="24da6-280">Ao fazer com que seu mecanismo/estrutura saiba onde o quad está e raiz de seus objetos em relação ao quad, seus hologramas estarão localizados corretamente em relação ao mundo real.</span><span class="sxs-lookup"><span data-stu-id="24da6-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="24da6-281">Malha</span><span class="sxs-lookup"><span data-stu-id="24da6-281">Mesh</span></span>

<span data-ttu-id="24da6-282">Malhas representam representações geométricas de objetos ou ambientes.</span><span class="sxs-lookup"><span data-stu-id="24da6-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="24da6-283">Assim como o mapeamento espacial [,](../../design/spatial-mapping.md)os dados de índice de malha e vértice fornecidos com cada malha de superfície espacial usam o mesmo layout familiar que os buffers de vértice e índice usados para renderizar malhas de triângulo em todas as APIs de renderização moderna.</span><span class="sxs-lookup"><span data-stu-id="24da6-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="24da6-284">As posições de vértice são fornecidas no sistema de coordenadas do `Scene` .</span><span class="sxs-lookup"><span data-stu-id="24da6-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="24da6-285">As APIs específicas usadas para referenciar esses dados são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="24da6-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="24da6-286">O código a seguir fornece um exemplo de geração de uma lista de triângulos da estrutura de malha:</span><span class="sxs-lookup"><span data-stu-id="24da6-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="24da6-287">Os buffers de índice/vértice devem ser >= as contagens de índice/vértice, mas, caso contrário, podem ser dimensionadas arbitrariamente, permitindo a reutilização eficiente de memória.</span><span class="sxs-lookup"><span data-stu-id="24da6-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="24da6-288">ColisorMesh</span><span class="sxs-lookup"><span data-stu-id="24da6-288">ColliderMesh</span></span>

<span data-ttu-id="24da6-289">Os objetos de cena fornecem acesso a dados de malha e colisor por meio das propriedades Malhas e ColisorMeshes.</span><span class="sxs-lookup"><span data-stu-id="24da6-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="24da6-290">Essas malhas sempre corresponderão, o que significa que o índice i'th da propriedade Malhas representa a mesma geometria que o índice i'th da propriedade ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="24da6-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="24da6-291">Se o runtime/objeto dá suporte a malhas de colisor, você tem a garantia de obter o polígono mais baixo, aproximação de ordem mais alta e é uma boa prática usar Colisores sempre que seu aplicativo usar colisores.</span><span class="sxs-lookup"><span data-stu-id="24da6-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="24da6-292">Se o sistema não dá suporte a colisores, o objeto Mesh retornado em ColisoresMeshes será o mesmo objeto que a malha reduzindo restrições de memória.</span><span class="sxs-lookup"><span data-stu-id="24da6-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="24da6-293">Desenvolvendo com a compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="24da6-293">Developing with scene understanding</span></span>

<span data-ttu-id="24da6-294">Neste ponto, você deve entender os principais blocos de construção do runtime e do SDK de compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="24da6-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="24da6-295">A maior parte da potência e da complexidade está em padrões de acesso, interação com estruturas 3D e ferramentas que podem ser escritas sobre essas APIs para realizar tarefas mais avançadas, como planejamento espacial, análise de sala, navegação, física e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="24da6-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="24da6-296">Esperamos capturá-los em exemplos que devem, esperamos, orientá-lo na direção adequada para fazer com que seus cenários brilhem.</span><span class="sxs-lookup"><span data-stu-id="24da6-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="24da6-297">Se houver exemplos ou cenários que não estamos abordando, nos avise e tentaremos documentar/protótipo do que você precisa.</span><span class="sxs-lookup"><span data-stu-id="24da6-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="24da6-298">Onde posso obter o código de exemplo?</span><span class="sxs-lookup"><span data-stu-id="24da6-298">Where can I get sample code?</span></span>

<span data-ttu-id="24da6-299">O código de exemplo de Compreensão de Cena para Unity pode ser encontrado em nossa [página página de exemplo do Unity.](https://github.com/sceneunderstanding-microsoft/unitysample)</span><span class="sxs-lookup"><span data-stu-id="24da6-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="24da6-300">Esse aplicativo permitirá que você se comunique com seu dispositivo e renderizar os vários objetos de cena ou permitirá que você carregue uma cena serializada em seu computador e permita que você experimente o Entendimento de Cena sem um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="24da6-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="24da6-301">Onde posso obter exemplos de cenas?</span><span class="sxs-lookup"><span data-stu-id="24da6-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="24da6-302">Se você tiver um HoloLens2, poderá salvar qualquer cena capturada salvando a saída de ComputeSerializedAsync em arquivo e desserializando-a de sua própria conveniência.</span><span class="sxs-lookup"><span data-stu-id="24da6-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="24da6-303">Se você não tiver um dispositivo HoloLens2, mas quiser brincar com a compreensão da cena, você precisará baixar uma cena previamente capturada.</span><span class="sxs-lookup"><span data-stu-id="24da6-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="24da6-304">A amostra de compreensão da cena é fornecida atualmente com cenas serializadas que podem ser baixadas e usadas por sua própria conveniência.</span><span class="sxs-lookup"><span data-stu-id="24da6-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="24da6-305">Você pode encontrá-los aqui:</span><span class="sxs-lookup"><span data-stu-id="24da6-305">You can find them here:</span></span>

[<span data-ttu-id="24da6-306">Cenas de exemplo de compreensão de cena</span><span class="sxs-lookup"><span data-stu-id="24da6-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a><span data-ttu-id="24da6-307">Veja também</span><span class="sxs-lookup"><span data-stu-id="24da6-307">See also</span></span>

* [<span data-ttu-id="24da6-308">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="24da6-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="24da6-309">Reconhecimento de cena</span><span class="sxs-lookup"><span data-stu-id="24da6-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="24da6-310">Exemplo de Unity</span><span class="sxs-lookup"><span data-stu-id="24da6-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)