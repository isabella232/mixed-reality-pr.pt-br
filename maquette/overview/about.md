---
title: Sobre o maquette
description: Introdução ao maquette e a seus recursos.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realidade mista do Windows, maquette, protótipoing, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935326"
---
# <a name="about-maquette"></a><span data-ttu-id="10f93-104">Sobre o maquette</span><span class="sxs-lookup"><span data-stu-id="10f93-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="10f93-105">![Introdução do logotipo ](../images/MaquetteIcon.png) MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="10f93-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="10f93-106">O maquette integra o JavaScript padrão ECMA 5,1 para habilitar o investimento de interatividade em cenas de maquette e objetos que podem ser editados e executados no VSCode.</span><span class="sxs-lookup"><span data-stu-id="10f93-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="10f93-107">As propriedades de objetos são expostas para leitura e configuração de dentro do script, métodos de objeto chamados e eventos de objeto e sistema.</span><span class="sxs-lookup"><span data-stu-id="10f93-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="10f93-108">O script também pode interagir com o maquette em si por meio de objetos do sistema acessíveis por meio de script.</span><span class="sxs-lookup"><span data-stu-id="10f93-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="10f93-109">Vários controles de interface de usuário com os quais o usuário pode interagir fazem parte do sistema.</span><span class="sxs-lookup"><span data-stu-id="10f93-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="10f93-110">Eles podem ser adicionados durante a criação no maquette ou criados e gerenciados de dentro do script.</span><span class="sxs-lookup"><span data-stu-id="10f93-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="10f93-111">Eventos de interação do usuário com esses elementos (entrada de dados, cliques, etc) também são expostos a scripts como eventos.</span><span class="sxs-lookup"><span data-stu-id="10f93-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="10f93-112">Com essas adições, podem ser criadas cenas simples de complexas, desde experimentos até visualização de dados até explorações de cenários de usuário de realidade misturada até experiências totalmente percebidas em AR ou VR.</span><span class="sxs-lookup"><span data-stu-id="10f93-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="10f93-113">vídeo de 60 second'ish</span><span class="sxs-lookup"><span data-stu-id="10f93-113">60 second'ish video</span></span>
* <span data-ttu-id="10f93-114">Cartão de título de entrada</span><span class="sxs-lookup"><span data-stu-id="10f93-114">Entry Title Card</span></span>
  * <span data-ttu-id="10f93-115">Criação de conteúdo interativo de realidade misturada no maquette</span><span class="sxs-lookup"><span data-stu-id="10f93-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="10f93-116">Script/sistema de interface do usuário/interatividade</span><span class="sxs-lookup"><span data-stu-id="10f93-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="10f93-117">O VO Welcome por legendas de equipe ou de vídeo?</span><span class="sxs-lookup"><span data-stu-id="10f93-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="10f93-118">explicando</span><span class="sxs-lookup"><span data-stu-id="10f93-118">explaining:</span></span>
  * <span data-ttu-id="10f93-119">raciocínio por trás do script para habilitar a criação de conteúdo interativo de MR</span><span class="sxs-lookup"><span data-stu-id="10f93-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="10f93-120">toque em como ele pode ser usado em traços de pincel muito amplos</span><span class="sxs-lookup"><span data-stu-id="10f93-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="10f93-121">Vingette de scripts em ação</span><span class="sxs-lookup"><span data-stu-id="10f93-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="10f93-122">Caixa de diálogo de composição</span><span class="sxs-lookup"><span data-stu-id="10f93-122">Composing dialog box</span></span>
  * <span data-ttu-id="10f93-123">Criando aplicativo a partir da estrutura de tópicos (demonstração do aplicativo de culinária)</span><span class="sxs-lookup"><span data-stu-id="10f93-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="10f93-124">Composição no modelo Photogrammetry</span><span class="sxs-lookup"><span data-stu-id="10f93-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="10f93-125">Interagindo com o guia de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="10f93-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="10f93-126">Exibição de tela da depuração de scripts no VSCode</span><span class="sxs-lookup"><span data-stu-id="10f93-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="10f93-127">Obtendo acesso ao script de um objeto em cena</span><span class="sxs-lookup"><span data-stu-id="10f93-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="10f93-128">Etc...</span><span class="sxs-lookup"><span data-stu-id="10f93-128">Etc...</span></span>
* <span data-ttu-id="10f93-129">Cartão de título de resumo no final</span><span class="sxs-lookup"><span data-stu-id="10f93-129">Summary Title card at end</span></span>
  * <span data-ttu-id="10f93-130">Link para maquette</span><span class="sxs-lookup"><span data-stu-id="10f93-130">Link to Maquette</span></span>
  * <span data-ttu-id="10f93-131">Onde ir para introdução ao script</span><span class="sxs-lookup"><span data-stu-id="10f93-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="10f93-132">Comunicados/status/Comunidade</span><span class="sxs-lookup"><span data-stu-id="10f93-132">Announcements/status/community</span></span>
  * <span data-ttu-id="10f93-133">Aguardar para ver o que você pode fazer/envios (?)</span><span class="sxs-lookup"><span data-stu-id="10f93-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="10f93-134">Comentários e como podemos atendê-lo melhor</span><span class="sxs-lookup"><span data-stu-id="10f93-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="10f93-135">Introdução</span><span class="sxs-lookup"><span data-stu-id="10f93-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="10f93-136">Exemplos e aplicativos de exemplo</span><span class="sxs-lookup"><span data-stu-id="10f93-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="10f93-137">Suporte</span><span class="sxs-lookup"><span data-stu-id="10f93-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="10f93-138">Enviar seus comentários</span><span class="sxs-lookup"><span data-stu-id="10f93-138">Send us feedback</span></span>

<span data-ttu-id="10f93-139">Estamos ansiosos por ouvir suas experiências e resultados.</span><span class="sxs-lookup"><span data-stu-id="10f93-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="10f93-140">Comentários, sugestões e relatórios de bugs sempre são bem-vindos!</span><span class="sxs-lookup"><span data-stu-id="10f93-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="10f93-141"><Link? ></span><span class="sxs-lookup"><span data-stu-id="10f93-141"><Link?></span></span>