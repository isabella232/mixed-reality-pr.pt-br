---
title: Extensões do editor no Unreal
description: Saiba como estender o editor do Unreal Engine com os scripts personalizados, as ações com script e os widgets de utilitário.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, extensões do editor, editor do Unreal, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, documentação, guias, recursos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, portabilidade, atualização
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584702"
---
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="61eeb-104">Extensões do editor no Unreal</span><span class="sxs-lookup"><span data-stu-id="61eeb-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="61eeb-105">O Unreal fornece um amplo conjunto de recursos que permitem que você personalize o mecanismo para as suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="61eeb-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="61eeb-106">Os recursos variam de simples, mas limitados, a muito potentes, mas complexos.</span><span class="sxs-lookup"><span data-stu-id="61eeb-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="61eeb-107">As etapas a seguir são listadas em ordem crescente de complexidade.</span><span class="sxs-lookup"><span data-stu-id="61eeb-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="61eeb-108">Em geral, você deve buscar soluções mais simples para o problema e esgotar as opções antes de passar para uma opção mais complexa.</span><span class="sxs-lookup"><span data-stu-id="61eeb-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="61eeb-109">Por exemplo, descobrimos que o Script de Construção básico pode ser usado no lugar de plug-ins na maioria das vezes.</span><span class="sxs-lookup"><span data-stu-id="61eeb-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="61eeb-110">Scripts de construção</span><span class="sxs-lookup"><span data-stu-id="61eeb-110">Construction scripts</span></span>

<span data-ttu-id="61eeb-111">Você pode usar scripts de construção para executar ações de inicialização, que são executadas quando a instância do Blueprint é criada.</span><span class="sxs-lookup"><span data-stu-id="61eeb-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="61eeb-112">Script de Construções do usuário</span><span class="sxs-lookup"><span data-stu-id="61eeb-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="61eeb-113">Exemplo de blueprint</span><span class="sxs-lookup"><span data-stu-id="61eeb-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="61eeb-114">Tutorial em vídeo</span><span class="sxs-lookup"><span data-stu-id="61eeb-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="61eeb-115">Ações com script</span><span class="sxs-lookup"><span data-stu-id="61eeb-115">Scripted actions</span></span>

<span data-ttu-id="61eeb-116">As ações com script são blueprints do utilitário do editor.</span><span class="sxs-lookup"><span data-stu-id="61eeb-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="61eeb-117">Você pode iniciá-las no Editor do Unreal ao:</span><span class="sxs-lookup"><span data-stu-id="61eeb-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="61eeb-118">Clicar com o botão direito do mouse em **Ativos** no Navegador de Conteúdo</span><span class="sxs-lookup"><span data-stu-id="61eeb-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="61eeb-119">Ou clicando com o botão direito do mouse em **Atores** no Visor de Nível ou no Contorno do Mundo</span><span class="sxs-lookup"><span data-stu-id="61eeb-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="61eeb-120">As Ações com Script são exclusivamente adequadas para momentos em que você precisa que a sua lógica de Blueprint tenha consciência contextual sobre conjuntos de Ativos ou Atores.</span><span class="sxs-lookup"><span data-stu-id="61eeb-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="61eeb-121">Normalmente, uma Ação com Script obtém uma lista de Ativos ou Atores que você selecionou quando a ação foi executada e, em seguida, modifica esses objetos ou os considera no grafo.</span><span class="sxs-lookup"><span data-stu-id="61eeb-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="61eeb-122">Ações com script</span><span class="sxs-lookup"><span data-stu-id="61eeb-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="61eeb-123">Como executar ações com script na inicialização do projeto</span><span class="sxs-lookup"><span data-stu-id="61eeb-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="61eeb-124">Widgets do utilitário do editor</span><span class="sxs-lookup"><span data-stu-id="61eeb-124">Editor utility widgets</span></span>

<span data-ttu-id="61eeb-125">Você pode usar os [Widgets do Utilitário do Editor](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) sempre que desejar adicionar novos elementos da interface do usuário para modificar a IU (interface do usuário) do Editor do Unreal.</span><span class="sxs-lookup"><span data-stu-id="61eeb-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="61eeb-126">Os Widgets do Utilitário do Editor são baseados em UMG (Unreal Motion Graphics), para que você possa configurar os Widgets em um Blueprint da mesma forma que faria em qualquer outro Blueprint de Widget do UMG.</span><span class="sxs-lookup"><span data-stu-id="61eeb-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="61eeb-127">Esses Widgets são especificamente para a Interface do Usuário do Editor e você pode usá-los para criar guias personalizadas do Editor.</span><span class="sxs-lookup"><span data-stu-id="61eeb-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="61eeb-128">Você pode selecionar essas guias personalizadas no menu do Windows, como você selecionaria as guias do Editor existentes.</span><span class="sxs-lookup"><span data-stu-id="61eeb-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="61eeb-129">Plug-ins</span><span class="sxs-lookup"><span data-stu-id="61eeb-129">Plugins</span></span>

<span data-ttu-id="61eeb-130">O Unreal permite que você desenvolva e gerencie os próprios [plug-ins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) personalizados para uso com runtime e ferramentas do UE4.</span><span class="sxs-lookup"><span data-stu-id="61eeb-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="61eeb-131">Você pode habilitar ou desabilitar os seus plug-ins a qualquer momento no Editor do Unreal.</span><span class="sxs-lookup"><span data-stu-id="61eeb-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="61eeb-132">Os plug-ins podem adicionar funcionalidade de jogo de runtime, modificar recursos internos do Engine, criar tipos de arquivo e estender as funcionalidades do Editor.</span><span class="sxs-lookup"><span data-stu-id="61eeb-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

