---
title: Visão geral da programação
description: Saiba como acessar objetos e interfaces do maquette com scripts.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realidade mista do Windows, maquette, protótipoing, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935318"
---
# <a name="programming-overview"></a><span data-ttu-id="11b15-104">Visão geral da programação</span><span class="sxs-lookup"><span data-stu-id="11b15-104">Programming overview</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logotipo](../images/MaquetteIcon.png) <span data-ttu-id="11b15-106">Visão geral da programação</span><span class="sxs-lookup"><span data-stu-id="11b15-106">Programming Overview</span></span>

<span data-ttu-id="11b15-107">O Microsoft maquette usa JavaScript (ECMAScript 5,1 com extensões) com base no interpretador do [Jint](https://github.com/sebastienros/jint) .</span><span class="sxs-lookup"><span data-stu-id="11b15-107">Microsoft Maquette uses JavaScript (ECMAScript 5.1 with extensions) based on the [Jint](https://github.com/sebastienros/jint) interpreter.</span></span> <span data-ttu-id="11b15-108">A extensão `.mqjs` é usada para distinguir arquivos JavaScript maquette do JavaScript normal.</span><span class="sxs-lookup"><span data-stu-id="11b15-108">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
<span data-ttu-id="11b15-109">Os objetos e as interfaces do maquette são acessíveis e programáveis por meio do `Maquette` objeto.</span><span class="sxs-lookup"><span data-stu-id="11b15-109">Maquette objects and interfaces are accessible and scriptable via the `Maquette` Object.</span></span> <span data-ttu-id="11b15-110">A documentação sobre objetos e interfaces maquette é fornecida na referência de API do maquette.</span><span class="sxs-lookup"><span data-stu-id="11b15-110">Documentation on Maquette Objects and interfaces are provided in Maquette's API Reference.</span></span>

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
<span data-ttu-id="11b15-111">MaquetteScript é uma nova adição e, no fluxo, para que as alterações sejam esperadas.</span><span class="sxs-lookup"><span data-stu-id="11b15-111">MaquetteScript is a new addition and in flux so changes should be expected.</span></span> <span data-ttu-id="11b15-112">Documentação e atualizações mais detalhadas disponíveis em breve.</span><span class="sxs-lookup"><span data-stu-id="11b15-112">More detailed documentation and updates available soon.</span></span>

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a><span data-ttu-id="11b15-113">Destaques sobre scripts</span><span class="sxs-lookup"><span data-stu-id="11b15-113">Spotlights on Scripting</span></span>

* <span data-ttu-id="11b15-114">TBD-destaques de scripts focados como exemplos/tutoriais</span><span class="sxs-lookup"><span data-stu-id="11b15-114">TBD - Scripting Spotlights focused as Samples/Tutorials</span></span>
  * <span data-ttu-id="11b15-115">2x imagens/legendas – link para página de destaque</span><span class="sxs-lookup"><span data-stu-id="11b15-115">2x Images/Caption – link to spotlight page</span></span>

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a><span data-ttu-id="11b15-116">Introdução ao MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="11b15-116">Getting started with MaquetteScript</span></span>

* <span data-ttu-id="11b15-117">Mqjs vs. JS</span><span class="sxs-lookup"><span data-stu-id="11b15-117">Mqjs vs. JS</span></span>
* <span data-ttu-id="11b15-118">Modelo de Programação</span><span class="sxs-lookup"><span data-stu-id="11b15-118">Programming Model</span></span>
  * <span data-ttu-id="11b15-119">Editando vs. em execução</span><span class="sxs-lookup"><span data-stu-id="11b15-119">Editing vs. Running</span></span>
* <span data-ttu-id="11b15-120">Link para fluxo de trabalho de programação</span><span class="sxs-lookup"><span data-stu-id="11b15-120">Link to Programming Workflow</span></span>
* <span data-ttu-id="11b15-121">Link para compartilhar resultados</span><span class="sxs-lookup"><span data-stu-id="11b15-121">Link to Sharing Results</span></span>

## <a name="programming-workflow"></a><span data-ttu-id="11b15-122">Fluxo de trabalho de programação</span><span class="sxs-lookup"><span data-stu-id="11b15-122">Programming workflow</span></span>

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
<span data-ttu-id="11b15-123">TBD</span><span class="sxs-lookup"><span data-stu-id="11b15-123">TBD</span></span>
* <span data-ttu-id="11b15-124">REPL</span><span class="sxs-lookup"><span data-stu-id="11b15-124">REPL</span></span>
* <span data-ttu-id="11b15-125">Operação de script</span><span class="sxs-lookup"><span data-stu-id="11b15-125">Scripting operation</span></span>
* <span data-ttu-id="11b15-126">Operação do depurador</span><span class="sxs-lookup"><span data-stu-id="11b15-126">Debugger operation</span></span>
* <span data-ttu-id="11b15-127">Loop de depuração</span><span class="sxs-lookup"><span data-stu-id="11b15-127">Debugging loop</span></span>
* <span data-ttu-id="11b15-128">Copiar/colar código?</span><span class="sxs-lookup"><span data-stu-id="11b15-128">Copy/Paste of code?</span></span>

## <a name="running-mqjs-scripts"></a><span data-ttu-id="11b15-129">Executando scripts. mqjs</span><span class="sxs-lookup"><span data-stu-id="11b15-129">Running .mqjs scripts</span></span>

<!-- TODO(Stefan): Need screenshot -->
<span data-ttu-id="11b15-130">Para executar um arquivo MaquetteScript. mqjs, vá para as janelas complementares do maquette e abra a guia script para localizar scripts.</span><span class="sxs-lookup"><span data-stu-id="11b15-130">To run a MaquetteScript .mqjs file, go to the companion windows of Maquette and open the scripting tab to locate scripts.</span></span>

> [!NOTE] 
> <span data-ttu-id="11b15-131">Algumas opções ainda não funcionarão, pois não enviamos os scripts.</span><span class="sxs-lookup"><span data-stu-id="11b15-131">Some options will not work yet because we have not ship the scripts.</span></span>

## <a name="vscode-editor-workflow"></a><span data-ttu-id="11b15-132">Fluxo de trabalho do editor de VSCode</span><span class="sxs-lookup"><span data-stu-id="11b15-132">VSCode Editor Workflow</span></span>

<span data-ttu-id="11b15-133">Para avaliar o script em maquette de dentro de VSCode, o usuário precisa saber dois comandos:</span><span class="sxs-lookup"><span data-stu-id="11b15-133">To evaluate script in Maquette from within VSCode, the user needs to know two commands:</span></span>

   <span data-ttu-id="11b15-134">`CTRL-5` avalia o texto selecionado ou a linha inteira onde o cursor está localizado.</span><span class="sxs-lookup"><span data-stu-id="11b15-134">`CTRL-5` evaluates the selected text or the entire line where the cursor is located.</span></span> 

   <span data-ttu-id="11b15-135">`CTRL-SHIFT-5` avalia o arquivo inteiro.</span><span class="sxs-lookup"><span data-stu-id="11b15-135">`CTRL-SHIFT-5` evaluates the entire file.</span></span>

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
<span data-ttu-id="11b15-136">O texto é enviado para maquette, avaliado no ambiente JavaScript e o resultado é enviado de volta para o console de saída do VSCode.</span><span class="sxs-lookup"><span data-stu-id="11b15-136">Text is sent to Maquette, evaluated in the JavaScript environment, and the result is sent back to the output console of VSCode.</span></span> <span data-ttu-id="11b15-137">Isso pode ser usado como um REPL (Read-eval-Print-loop).</span><span class="sxs-lookup"><span data-stu-id="11b15-137">This can be used as a REPL (read-eval-print-loop).</span></span>

## <a name="example-first-step"></a><span data-ttu-id="11b15-138">Primeira etapa de exemplo</span><span class="sxs-lookup"><span data-stu-id="11b15-138">Example First Step</span></span>

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
<span data-ttu-id="11b15-139">Copie o código a seguir em um arquivo em VSCode:</span><span class="sxs-lookup"><span data-stu-id="11b15-139">Copy the following code into a file in VSCode:</span></span>

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
<span data-ttu-id="11b15-140">Selecione o código ou apenas as seções e clique `CTRL-5` para executar.</span><span class="sxs-lookup"><span data-stu-id="11b15-140">Select the code or just sections and hit `CTRL-5` to execute.</span></span> <span data-ttu-id="11b15-141">Isso deve criar um cubo, colocá-lo na frente e alterar sua cor.</span><span class="sxs-lookup"><span data-stu-id="11b15-141">This should create a cube, place it in front of you and change its color.</span></span>

<span data-ttu-id="11b15-142">Há mais exemplos para localizar por meio da extensão.</span><span class="sxs-lookup"><span data-stu-id="11b15-142">There are more examples to find through the extension.</span></span>

## <a name="sharing-results"></a><span data-ttu-id="11b15-143">Compartilhando resultados</span><span class="sxs-lookup"><span data-stu-id="11b15-143">Sharing Results</span></span>

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
<span data-ttu-id="11b15-144">Como compartilhar entre usuários/equipes</span><span class="sxs-lookup"><span data-stu-id="11b15-144">How to share between users/teams</span></span>
* <span data-ttu-id="11b15-145">Projeto zip no diretório documentos</span><span class="sxs-lookup"><span data-stu-id="11b15-145">Zip project in documents directory</span></span>
* <span data-ttu-id="11b15-146">Copiar projeto para compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="11b15-146">Copy project to file share</span></span>
* <span data-ttu-id="11b15-147">Adicionando o local do arquivo de envios de compartilhamento de equipe à equipe do maquette</span><span class="sxs-lookup"><span data-stu-id="11b15-147">Adding file location of team share Submissions to Maquette Team</span></span>

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
<span data-ttu-id="11b15-148">TBD</span><span class="sxs-lookup"><span data-stu-id="11b15-148">TBD</span></span>
* <span data-ttu-id="11b15-149">Inclui, referência a código em outro lugar com caminhos relativos/absolutos, módulos</span><span class="sxs-lookup"><span data-stu-id="11b15-149">Includes, reference to code elsewhere with relative/absolute paths, modules</span></span>
* <span data-ttu-id="11b15-150">DLLs?</span><span class="sxs-lookup"><span data-stu-id="11b15-150">Libraries?</span></span>
* <span data-ttu-id="11b15-151">Suporte de runtime</span><span class="sxs-lookup"><span data-stu-id="11b15-151">Runtime support</span></span>
* <span data-ttu-id="11b15-152">Externas não resolvidas-comportamento quando as entradas estão ausentes/falhando</span><span class="sxs-lookup"><span data-stu-id="11b15-152">Unresolved Externals - Behavior when entries missing/crashing</span></span>
* <span data-ttu-id="11b15-153">Podemos adicionar/editar/observar o script associado a objetos específicos?</span><span class="sxs-lookup"><span data-stu-id="11b15-153">Can we add/edit/observe script associated with specific objects?</span></span>
  * <span data-ttu-id="11b15-154">Podemos copiar/colar este script em outro lugar?</span><span class="sxs-lookup"><span data-stu-id="11b15-154">Can we copy/paste this script elsewhere?</span></span>
  * <span data-ttu-id="11b15-155">E quanto às propriedades do objeto?</span><span class="sxs-lookup"><span data-stu-id="11b15-155">What about object properties?</span></span>
  * <span data-ttu-id="11b15-156">Nomeando objetos em minha cena?</span><span class="sxs-lookup"><span data-stu-id="11b15-156">Naming objects in my scene?</span></span> <span data-ttu-id="11b15-157">(renomeando script com ele)</span><span class="sxs-lookup"><span data-stu-id="11b15-157">(renaming script with it)</span></span>
  * <span data-ttu-id="11b15-158">Esta palavra-chave ou SELF para o script associado a um objeto</span><span class="sxs-lookup"><span data-stu-id="11b15-158">THIS or SELF keyword for script associated with an object</span></span>
  * <span data-ttu-id="11b15-159">Se eu clicar com o botão direito do mouse em um objeto, posso ver o código associado a ele (e a sua hierarquia)</span><span class="sxs-lookup"><span data-stu-id="11b15-159">If I right click on an object, can I see code associated with it (and all it's hierarchy)</span></span>
  * <span data-ttu-id="11b15-160">Posso selecionar na interface do usuário e ser colocado no código em VSCode?</span><span class="sxs-lookup"><span data-stu-id="11b15-160">Can I select in UI and be brought up at the code in VSCode?</span></span>
  * <span data-ttu-id="11b15-161">Mantendo o código associado a um objeto "juntos" no arquivo de origem do script?</span><span class="sxs-lookup"><span data-stu-id="11b15-161">Keeping code associated with an object "together" in the script source file?</span></span>
  * <span data-ttu-id="11b15-162">Trazer a janela de propriedades para cima de um objeto quando eu clicar nele?</span><span class="sxs-lookup"><span data-stu-id="11b15-162">Bring property window up of an object when I click on it?</span></span> <span data-ttu-id="11b15-163">Em VR e na guia principal?</span><span class="sxs-lookup"><span data-stu-id="11b15-163">In VR and in main tab?</span></span>
* <span data-ttu-id="11b15-164">Problemas de segurança</span><span class="sxs-lookup"><span data-stu-id="11b15-164">Security Issues</span></span>
* <span data-ttu-id="11b15-165">Teste – pode ser TBD, mas poderíamos sugerir a captura de vídeo ou quadro por script</span><span class="sxs-lookup"><span data-stu-id="11b15-165">Testing – might be TBD but we could suggest video or frame grab by script</span></span>
* <span data-ttu-id="11b15-166">Se tivermos um mecanismo de relatório de bugs, poderemos torná-lo acessível por meio de script para outros (?)... outro</span><span class="sxs-lookup"><span data-stu-id="11b15-166">If we have a bug reporting mechanism, we might make that accessible via script for others (?) …later</span></span>
* <span data-ttu-id="11b15-167">Implantação – como "compartilhar" o resultado, pacote como EXE</span><span class="sxs-lookup"><span data-stu-id="11b15-167">Deployment – how to “share” the result, package as EXE</span></span>
* <span data-ttu-id="11b15-168">Executando/controlando uma demonstração ou spectating/monitoramento</span><span class="sxs-lookup"><span data-stu-id="11b15-168">Running/controlling a demo or spectating/monitoring</span></span>
* <span data-ttu-id="11b15-169">Modo de jogador</span><span class="sxs-lookup"><span data-stu-id="11b15-169">Player mode</span></span>
* <span data-ttu-id="11b15-170">Podemos ter um segmento sobre como fazer "componentes" para compartilhamento?</span><span class="sxs-lookup"><span data-stu-id="11b15-170">We might have a segment on how to make “components” for sharing?</span></span> <span data-ttu-id="11b15-171">(pode ser TBD)</span><span class="sxs-lookup"><span data-stu-id="11b15-171">(might  be tbd)</span></span>
  * <span data-ttu-id="11b15-172">Há #include?</span><span class="sxs-lookup"><span data-stu-id="11b15-172">Is there #include?</span></span> <span data-ttu-id="11b15-173">Isso lida com o JS puro que eu suponhai, mas pode ter conflitos de namespace.</span><span class="sxs-lookup"><span data-stu-id="11b15-173">This handles pure JS I suppose but may have namespace conflicts.</span></span>
  * <span data-ttu-id="11b15-174">Há algo que poderíamos fazer para um maquette incorporar algum outro maquette com objetos nomeados para coincidir com o código JS?</span><span class="sxs-lookup"><span data-stu-id="11b15-174">Is there anything we could do for a maquette to incorporate some other maquette with named objects to match JS code?</span></span>
