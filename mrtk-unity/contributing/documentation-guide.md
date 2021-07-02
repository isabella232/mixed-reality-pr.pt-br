---
title: Diretrizes da documentação
description: Diretrizes e padrões de documentação para o MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 95af19b71a9fe06dabad058e75f78d951262ba4a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175354"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="7b396-104">Diretrizes da documentação</span><span class="sxs-lookup"><span data-stu-id="7b396-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

<span data-ttu-id="7b396-105">este documento descreve as diretrizes e os padrões de documentação para a realidade misturada Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="7b396-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="7b396-106">Isso fornece uma introdução aos aspectos técnicos de escrita e geração de documentação, para destacar armadilhas comuns e para descrever o estilo de escrita recomendado.</span><span class="sxs-lookup"><span data-stu-id="7b396-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="7b396-107">A página em si deve servir como exemplo, portanto, ela usa o estilo pretendido e os recursos de marcação mais comuns da documentação.</span><span class="sxs-lookup"><span data-stu-id="7b396-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="7b396-108">Origem</span><span class="sxs-lookup"><span data-stu-id="7b396-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="7b396-109">Instruções</span><span class="sxs-lookup"><span data-stu-id="7b396-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="7b396-110">Projetar</span><span class="sxs-lookup"><span data-stu-id="7b396-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="7b396-111">Notas de desempenho</span><span class="sxs-lookup"><span data-stu-id="7b396-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="7b396-112">Alterações da falha</span><span class="sxs-lookup"><span data-stu-id="7b396-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="7b396-113">Funcionalidade e marcação</span><span class="sxs-lookup"><span data-stu-id="7b396-113">Functionality and markup</span></span>

<span data-ttu-id="7b396-114">Esta seção descreve os recursos frequentemente necessários.</span><span class="sxs-lookup"><span data-stu-id="7b396-114">This section describes frequently needed features.</span></span> <span data-ttu-id="7b396-115">Para ver como eles funcionam, examine o código-fonte da página.</span><span class="sxs-lookup"><span data-stu-id="7b396-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="7b396-116">Listas numeradas</span><span class="sxs-lookup"><span data-stu-id="7b396-116">Numbered lists</span></span>
   1. <span data-ttu-id="7b396-117">Listas numeradas aninhadas com pelo menos 3 espaços em branco à esquerda</span><span class="sxs-lookup"><span data-stu-id="7b396-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="7b396-118">O número real no código é irrelevante; a análise cuidará da definição do número de item correto.</span><span class="sxs-lookup"><span data-stu-id="7b396-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="7b396-119">Listas de pontos de marcador</span><span class="sxs-lookup"><span data-stu-id="7b396-119">Bullet point lists</span></span>
  - <span data-ttu-id="7b396-120">Listas de pontos de marcador aninhados</span><span class="sxs-lookup"><span data-stu-id="7b396-120">Nested bullet point lists</span></span>
- <span data-ttu-id="7b396-121">Texto em **negrito** com \* \* asterisco duplo\*\*</span><span class="sxs-lookup"><span data-stu-id="7b396-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="7b396-122"> *texto* em itálico com \_ sublinhado \_ ou \* asterisco único\*</span><span class="sxs-lookup"><span data-stu-id="7b396-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="7b396-123">Texto `highlighted as code` dentro de uma frase \` usando aspas revertidas\`</span><span class="sxs-lookup"><span data-stu-id="7b396-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="7b396-124">Links para páginas de docs [MRTK diretrizes de documentação](documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="7b396-124">Links to docs pages [MRTK documentation guidelines](documentation-guide.md)</span></span>
- <span data-ttu-id="7b396-125">Links para [âncoras em uma página](#style); as âncoras são formadas com a substituição de espaços por traços e a conversão em minúsculas</span><span class="sxs-lookup"><span data-stu-id="7b396-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="7b396-126">Para exemplos de código, usamos os blocos com três marcas de escala \` \` \` e especificamos *Csharp* como o idioma para realce de sintaxe:</span><span class="sxs-lookup"><span data-stu-id="7b396-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="7b396-127">Ao mencionar o código dentro de uma frase `use a single backtick` .</span><span class="sxs-lookup"><span data-stu-id="7b396-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="7b396-128">TODOs</span><span class="sxs-lookup"><span data-stu-id="7b396-128">TODOs</span></span>

<span data-ttu-id="7b396-129">Evite usar todos no docs, assim como esses TODO (como TODO o código) tendem a se acumular e informações sobre como eles devem ser atualizados e por que são perdidos.</span><span class="sxs-lookup"><span data-stu-id="7b396-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="7b396-130">Se for absolutamente necessário adicionar um TODO, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="7b396-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="7b396-131">Execute um novo problema no GitHub que descreve o contexto por trás do TODO e forneça um plano de fundo suficiente que outro colaborador possa entender e, em seguida, abordar o TODO.</span><span class="sxs-lookup"><span data-stu-id="7b396-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="7b396-132">Referencie a URL do problema no todo no docs.</span><span class="sxs-lookup"><span data-stu-id="7b396-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="7b396-133">Seções realçadas</span><span class="sxs-lookup"><span data-stu-id="7b396-133">Highlighted sections</span></span>

<span data-ttu-id="7b396-134">Para realçar pontos específicos para o leitor, use *> [!NOTE]* , *> [!WARNING]* e *> [!IMPORTANT]* para produzir os seguintes estilos.</span><span class="sxs-lookup"><span data-stu-id="7b396-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="7b396-135">É recomendável usar observações para pontos gerais e pontos de aviso/importantes somente para casos especiais relevantes.</span><span class="sxs-lookup"><span data-stu-id="7b396-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="7b396-136">Exemplo de uma observação</span><span class="sxs-lookup"><span data-stu-id="7b396-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="7b396-137">Exemplo de um aviso</span><span class="sxs-lookup"><span data-stu-id="7b396-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b396-138">Exemplo de um comentário importante</span><span class="sxs-lookup"><span data-stu-id="7b396-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="7b396-139">Layout de página</span><span class="sxs-lookup"><span data-stu-id="7b396-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="7b396-140">Introdução</span><span class="sxs-lookup"><span data-stu-id="7b396-140">Introduction</span></span>

<span data-ttu-id="7b396-141">A parte logo após o título do capítulo principal deve servir como uma breve introdução sobre o que é o capítulo.</span><span class="sxs-lookup"><span data-stu-id="7b396-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="7b396-142">Não torne isso muito longo, em vez disso, adicione subtítulos.</span><span class="sxs-lookup"><span data-stu-id="7b396-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="7b396-143">Elas permitem vincular a seções e podem ser salvas como indicadores.</span><span class="sxs-lookup"><span data-stu-id="7b396-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="7b396-144">Corpo principal</span><span class="sxs-lookup"><span data-stu-id="7b396-144">Main body</span></span>

<span data-ttu-id="7b396-145">Use manchetes de dois níveis e de três níveis para estruturar o restante.</span><span class="sxs-lookup"><span data-stu-id="7b396-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="7b396-146">**Mini seções**</span><span class="sxs-lookup"><span data-stu-id="7b396-146">**Mini Sections**</span></span>

<span data-ttu-id="7b396-147">Use uma linha em negrito de texto para blocos que devem ser destacados. Podemos substituir isso por manchetes de quatro níveis em algum momento.</span><span class="sxs-lookup"><span data-stu-id="7b396-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="7b396-148">Seção ' Veja também '</span><span class="sxs-lookup"><span data-stu-id="7b396-148">'See also' section</span></span>

<span data-ttu-id="7b396-149">A maioria das páginas deve terminar com um capítulo chamado *Ver também*.</span><span class="sxs-lookup"><span data-stu-id="7b396-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="7b396-150">Este capítulo é simplesmente uma lista com marcadores de links para páginas relacionadas a este tópico.</span><span class="sxs-lookup"><span data-stu-id="7b396-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="7b396-151">Esses links também podem aparecer dentro do texto da página quando apropriado, mas isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="7b396-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="7b396-152">Da mesma forma, o texto da página pode conter links para páginas que não estão relacionadas ao tópico principal, eles não devem ser incluídos na lista *Consulte também* .</span><span class="sxs-lookup"><span data-stu-id="7b396-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="7b396-153">Consulte o [capítulo ' ' Veja também ' ' da página](#see-also) como um exemplo para a escolha de links.</span><span class="sxs-lookup"><span data-stu-id="7b396-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="7b396-154">Sumário (TOC)</span><span class="sxs-lookup"><span data-stu-id="7b396-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="7b396-155">Os arquivos de Sumário são usados para gerar as barras de navegação na documentação do MRTK github.io.</span><span class="sxs-lookup"><span data-stu-id="7b396-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="7b396-156">Sempre que um novo arquivo de documentação for adicionado, verifique se há uma entrada para esse arquivo em um dos arquivos TOC. yml da pasta de documentação.</span><span class="sxs-lookup"><span data-stu-id="7b396-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="7b396-157">Somente os artigos listados nos arquivos de Sumário serão exibidos na navegação dos documentos do desenvolvedor. Pode haver um arquivo de Sumário para cada subpasta na pasta de documentação que pode ser vinculada a qualquer arquivo de Sumário existente para adicioná-lo como uma subseção à parte correspondente da navegação.</span><span class="sxs-lookup"><span data-stu-id="7b396-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="7b396-158">Estilo</span><span class="sxs-lookup"><span data-stu-id="7b396-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="7b396-159">Estilo de escrita</span><span class="sxs-lookup"><span data-stu-id="7b396-159">Writing style</span></span>

<span data-ttu-id="7b396-160">Regra geral: Tente **soar profissional**.</span><span class="sxs-lookup"><span data-stu-id="7b396-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="7b396-161">Isso geralmente significa evitar um ' Tom de conversação '.</span><span class="sxs-lookup"><span data-stu-id="7b396-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="7b396-162">Além disso, tente evitar o hiperbólico e o sensationalism.</span><span class="sxs-lookup"><span data-stu-id="7b396-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="7b396-163">Não tente ser (excessivamente) engraçado.</span><span class="sxs-lookup"><span data-stu-id="7b396-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="7b396-164">Nunca gravar ' I '</span><span class="sxs-lookup"><span data-stu-id="7b396-164">Never write 'I'</span></span>
3. <span data-ttu-id="7b396-165">Evite ' nós '.</span><span class="sxs-lookup"><span data-stu-id="7b396-165">Avoid 'we'.</span></span> <span data-ttu-id="7b396-166">Normalmente, isso pode ser reformulado facilmente, usando ' MRTK ' em vez disso.</span><span class="sxs-lookup"><span data-stu-id="7b396-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="7b396-167">Exemplo: "damos suporte a esse recurso"-> "o MRTK" dá suporte a esse recurso "ou" há suporte para os recursos a seguir... ".</span><span class="sxs-lookup"><span data-stu-id="7b396-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="7b396-168">Da mesma forma, tente evitar ' você '.</span><span class="sxs-lookup"><span data-stu-id="7b396-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="7b396-169">Exemplo: "com essa alteração simples seu sombreador se torna configurável!"</span><span class="sxs-lookup"><span data-stu-id="7b396-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="7b396-170">-> "os sombreadores podem se tornar configuráveis com pouco esforço".</span><span class="sxs-lookup"><span data-stu-id="7b396-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="7b396-171">Não use ' impreciso frases '.</span><span class="sxs-lookup"><span data-stu-id="7b396-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="7b396-172">Evite parecer muito empolgado, não precisamos vender nada.</span><span class="sxs-lookup"><span data-stu-id="7b396-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="7b396-173">Da mesma forma, evite ser muito expressivos.</span><span class="sxs-lookup"><span data-stu-id="7b396-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="7b396-174">Os pontos de exclamação raramente são necessários.</span><span class="sxs-lookup"><span data-stu-id="7b396-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="7b396-175">Uso de maiúsculas</span><span class="sxs-lookup"><span data-stu-id="7b396-175">Capitalization</span></span>

- <span data-ttu-id="7b396-176">Use o **caso de sentença para manchetes**.</span><span class="sxs-lookup"><span data-stu-id="7b396-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="7b396-177">Ie.</span><span class="sxs-lookup"><span data-stu-id="7b396-177">Ie.</span></span> <span data-ttu-id="7b396-178">colocar a primeira letra e os nomes em maiúsculas, mas nada mais.</span><span class="sxs-lookup"><span data-stu-id="7b396-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="7b396-179">Use o inglês regular para todo o resto.</span><span class="sxs-lookup"><span data-stu-id="7b396-179">Use regular English for everything else.</span></span> <span data-ttu-id="7b396-180">Isso significa que não **coloque palavras arbitrárias em maiúsculas**, mesmo que elas contenham um significado especial nesse contexto.</span><span class="sxs-lookup"><span data-stu-id="7b396-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="7b396-181">Prefira *texto em itálico* para realçar determinadas palavras, [Veja abaixo](#emphasis-and-highlighting).</span><span class="sxs-lookup"><span data-stu-id="7b396-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="7b396-182">Quando um link é inserido em uma sentença (que é o método preferencial), o nome do capítulo padrão sempre usa letras maiúsculas, dividindo, assim, a regra sem maiúsculas e minúsculas arbitrárias dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="7b396-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="7b396-183">Portanto, use um nome de link personalizado para corrigir a capitalização.</span><span class="sxs-lookup"><span data-stu-id="7b396-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="7b396-184">Por exemplo, aqui está um link para a documentação de [controle de limites](../features/ux-building-blocks/bounds-control.md) .</span><span class="sxs-lookup"><span data-stu-id="7b396-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/bounds-control.md) documentation.</span></span>
- <span data-ttu-id="7b396-185">Fazer maiúsculas nomes, como o *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7b396-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="7b396-186">Não colocar "Editor" em maiúscula ao escrever o *Editor Unity*.</span><span class="sxs-lookup"><span data-stu-id="7b396-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="7b396-187">Ênfase e realce</span><span class="sxs-lookup"><span data-stu-id="7b396-187">Emphasis and highlighting</span></span>

<span data-ttu-id="7b396-188">Há duas maneiras de enfatizar ou realçar palavras, torná-las em negrito ou torná-las em itálico.</span><span class="sxs-lookup"><span data-stu-id="7b396-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="7b396-189">O efeito do texto em negrito é que o **texto em negrito** fica inativo e, portanto, pode ser facilmente notado enquanto espiada uma parte do texto ou até mesmo apenas rolando uma página.</span><span class="sxs-lookup"><span data-stu-id="7b396-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="7b396-190">O negrito é ótimo para realçar frases que as pessoas devem lembrar.</span><span class="sxs-lookup"><span data-stu-id="7b396-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="7b396-191">No entanto, **use o texto em negrito raramente**, pois ele geralmente é confuso.</span><span class="sxs-lookup"><span data-stu-id="7b396-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="7b396-192">Muitas vezes, você deseja "agrupar" algo que pertença logicamente ao mesmo tempo ou realce um termo específico, pois ele tem um significado especial.</span><span class="sxs-lookup"><span data-stu-id="7b396-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="7b396-193">Essas coisas não precisam destacar o texto geral.</span><span class="sxs-lookup"><span data-stu-id="7b396-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="7b396-194">Use texto em itálico como um *método leve* para realçar algo.</span><span class="sxs-lookup"><span data-stu-id="7b396-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="7b396-195">Da mesma forma, quando um nome de arquivo, um caminho ou uma entrada de menu é mencionado em texto, prefira deixá-lo em itálico para agrupá-lo logicamente, sem atrapalhar.</span><span class="sxs-lookup"><span data-stu-id="7b396-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="7b396-196">Em geral, tente **evitar o realce de texto desnecessário**.</span><span class="sxs-lookup"><span data-stu-id="7b396-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="7b396-197">Os termos especiais podem ser realçados uma vez para facilitar o reconhecimento do leitor, não repita o realce em todo o texto, quando ele não tem mais nenhuma finalidade e apenas uma distração.</span><span class="sxs-lookup"><span data-stu-id="7b396-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="7b396-198">Mencionando entradas de menu</span><span class="sxs-lookup"><span data-stu-id="7b396-198">Mentioning menu entries</span></span>

<span data-ttu-id="7b396-199">ao mencionar uma entrada de menu que um usuário deve clicar, a convenção atual é: *Project > arquivos > criar > folha*</span><span class="sxs-lookup"><span data-stu-id="7b396-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="7b396-200">Links</span><span class="sxs-lookup"><span data-stu-id="7b396-200">Links</span></span>

<span data-ttu-id="7b396-201">Insira o máximo possível de links úteis para outras páginas, mas cada link apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="7b396-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="7b396-202">Suponha que um leitor clique em cada link na página e pense no quão entediante seria se a mesma página fosse aberta 20 vezes.</span><span class="sxs-lookup"><span data-stu-id="7b396-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="7b396-203">Prefira links inseridos em uma frase:</span><span class="sxs-lookup"><span data-stu-id="7b396-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="7b396-204">BAD: as diretrizes são úteis.</span><span class="sxs-lookup"><span data-stu-id="7b396-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="7b396-205">Confira [este capítulo para](../contributing/documentation-guide.md) obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="7b396-205">See [this chapter](../contributing/documentation-guide.md) for details.</span></span>
- <span data-ttu-id="7b396-206">BOM: [as diretrizes](documentation-guide.md) são úteis.</span><span class="sxs-lookup"><span data-stu-id="7b396-206">GOOD: [Guidelines](documentation-guide.md) are useful.</span></span>

<span data-ttu-id="7b396-207">Evite links externos, eles podem ficar desatualizados ou conter conteúdo protegido por direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="7b396-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="7b396-208">Ao adicionar um link, considere se ele também deve ser listado na [seção](#see-also) Ver também.</span><span class="sxs-lookup"><span data-stu-id="7b396-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="7b396-209">Da mesma forma, verifique se um link para a nova página deve ser adicionado à página vinculada.</span><span class="sxs-lookup"><span data-stu-id="7b396-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="7b396-210">Imagens/capturas de tela</span><span class="sxs-lookup"><span data-stu-id="7b396-210">Images / screenshots</span></span>

<span data-ttu-id="7b396-211">**Use capturas de tela com moderação.**</span><span class="sxs-lookup"><span data-stu-id="7b396-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="7b396-212">Manter imagens na documentação é muito trabalho, pequenas alterações na interface do usuário podem tornar muitas capturas de tela desatualizadas.</span><span class="sxs-lookup"><span data-stu-id="7b396-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="7b396-213">As regras a seguir reduzirão o esforço de manutenção:</span><span class="sxs-lookup"><span data-stu-id="7b396-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="7b396-214">Não use capturas de tela para coisas que podem ser descritas no texto.</span><span class="sxs-lookup"><span data-stu-id="7b396-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="7b396-215">Especialmente, **nunca captura de tela de uma grade de** propriedades com a única finalidade de mostrar valores e nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="7b396-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="7b396-216">Não inclua coisas em uma captura de tela irrelevantes para o que é mostrado.</span><span class="sxs-lookup"><span data-stu-id="7b396-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="7b396-217">Por exemplo, quando um efeito de renderização é mostrado, faça uma captura de tela do viewport, mas exclua qualquer interface do usuário ao redor dele.</span><span class="sxs-lookup"><span data-stu-id="7b396-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="7b396-218">Mostrando alguma interface do usuário, tente mover janelas de forma que apenas essa parte importante está na imagem.</span><span class="sxs-lookup"><span data-stu-id="7b396-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="7b396-219">Ao incluir a interface do usuário de captura de tela, mostre apenas as partes importantes.</span><span class="sxs-lookup"><span data-stu-id="7b396-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="7b396-220">Por exemplo, ao falar sobre botões em uma barra de ferramentas, faça uma imagem pequena que mostre os botões importantes da barra de ferramentas, mas exclua tudo ao redor dela.</span><span class="sxs-lookup"><span data-stu-id="7b396-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="7b396-221">Use apenas imagens fáceis de reproduzir.</span><span class="sxs-lookup"><span data-stu-id="7b396-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="7b396-222">Isso significa que não pintar marcadores ou realça em capturas de tela.</span><span class="sxs-lookup"><span data-stu-id="7b396-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="7b396-223">Primeiro, não há regras consistentes sobre como elas devem ser, de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="7b396-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="7b396-224">Em segundo lugar, reproduzir essa captura de tela é um esforço adicional.</span><span class="sxs-lookup"><span data-stu-id="7b396-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="7b396-225">Em vez disso, descreva as partes importantes no texto.</span><span class="sxs-lookup"><span data-stu-id="7b396-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="7b396-226">Há exceções a essa regra, mas elas são raras.</span><span class="sxs-lookup"><span data-stu-id="7b396-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="7b396-227">Obviamente, é muito mais esforço recriar um GIF animado.</span><span class="sxs-lookup"><span data-stu-id="7b396-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="7b396-228">Espere ser responsável por recriá-lo até o fim do tempo ou esperar que as pessoas o lancem, se não quiserem gastar esse tempo.</span><span class="sxs-lookup"><span data-stu-id="7b396-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="7b396-229">Mantenha o número de imagens em um artigo baixo.</span><span class="sxs-lookup"><span data-stu-id="7b396-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="7b396-230">Geralmente, um bom método é fazer uma captura de tela geral de alguma ferramenta, que mostra tudo e, em seguida, descrever o restante em texto.</span><span class="sxs-lookup"><span data-stu-id="7b396-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="7b396-231">Isso facilita a substituição da captura de tela quando necessário.</span><span class="sxs-lookup"><span data-stu-id="7b396-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="7b396-232">Alguns outros aspectos:</span><span class="sxs-lookup"><span data-stu-id="7b396-232">Some other aspects:</span></span>

- <span data-ttu-id="7b396-233">A interface do usuário do editor para capturas de tela deve usar o editor de tema cinza claro, pois nem todos os usuários têm acesso ao tema escuro e queremos manter as coisas o mais consistente possível.</span><span class="sxs-lookup"><span data-stu-id="7b396-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="7b396-234">A largura padrão da imagem é de 500 pixels, pois isso é exibido bem na maioria dos monitores.</span><span class="sxs-lookup"><span data-stu-id="7b396-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="7b396-235">Tente não desviar muito dele.</span><span class="sxs-lookup"><span data-stu-id="7b396-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="7b396-236">A largura de 800 pixels deve ser a máxima.</span><span class="sxs-lookup"><span data-stu-id="7b396-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="7b396-237">Use PNGs para capturas de tela da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7b396-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="7b396-238">Use PNGs ou JPGs para capturas de tela do viewport 3D.</span><span class="sxs-lookup"><span data-stu-id="7b396-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="7b396-239">Prefira a qualidade em vez da taxa de compactação.</span><span class="sxs-lookup"><span data-stu-id="7b396-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="7b396-240">Lista de propriedades do componente</span><span class="sxs-lookup"><span data-stu-id="7b396-240">List of component properties</span></span>

<span data-ttu-id="7b396-241">Ao documentar uma lista de propriedades, use texto em negrito para realça o nome da propriedade e, em seguida, quebras de linha e texto regular para descrevê-las.</span><span class="sxs-lookup"><span data-stu-id="7b396-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="7b396-242">Não use sub capítulos ou listas de pontos de marcador.</span><span class="sxs-lookup"><span data-stu-id="7b396-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="7b396-243">Além disso, não se esqueça de concluir todas as frases com um ponto final.</span><span class="sxs-lookup"><span data-stu-id="7b396-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="7b396-244">Lista de verificação de conclusão da página</span><span class="sxs-lookup"><span data-stu-id="7b396-244">Page completion checklist</span></span>

1. <span data-ttu-id="7b396-245">Verifique se as diretrizes deste documento foram seguidas.</span><span class="sxs-lookup"><span data-stu-id="7b396-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="7b396-246">Procure a estrutura do documento e veja se o novo documento pode ser mencionado na [seção Ver também](#see-also) de outras páginas.</span><span class="sxs-lookup"><span data-stu-id="7b396-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="7b396-247">Se disponível, tenha alguém com conhecimento do tópico que leia a página para ver se há correção técnica.</span><span class="sxs-lookup"><span data-stu-id="7b396-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="7b396-248">Fazer com que alguém leia a página com prova para estilo e formatação.</span><span class="sxs-lookup"><span data-stu-id="7b396-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="7b396-249">Isso pode ser alguém que não está familiarizado com o tópico, o que também é uma boa ideia para obter comentários sobre como a documentação é compreensível.</span><span class="sxs-lookup"><span data-stu-id="7b396-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="7b396-250">Documentação de origem</span><span class="sxs-lookup"><span data-stu-id="7b396-250">Source documentation</span></span>

<span data-ttu-id="7b396-251">A documentação da API será gerada automaticamente dos arquivos de origem do MRTK.</span><span class="sxs-lookup"><span data-stu-id="7b396-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="7b396-252">Para facilitar isso, os arquivos de origem são necessários para conter o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7b396-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="7b396-253">Blocos de resumo de classe, struct, enum</span><span class="sxs-lookup"><span data-stu-id="7b396-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="7b396-254">Blocos de propriedade, método, resumo de eventos</span><span class="sxs-lookup"><span data-stu-id="7b396-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="7b396-255">Versão e dependências de introdução de recursos</span><span class="sxs-lookup"><span data-stu-id="7b396-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="7b396-256">Campos serializados</span><span class="sxs-lookup"><span data-stu-id="7b396-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="7b396-257">Valores de enumeração</span><span class="sxs-lookup"><span data-stu-id="7b396-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="7b396-258">Além do acima, o código deve ser bem comentado para permitir manutenção, correções de bugs e facilidade de personalização.</span><span class="sxs-lookup"><span data-stu-id="7b396-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="7b396-259">Blocos de resumo de classe, struct, enum</span><span class="sxs-lookup"><span data-stu-id="7b396-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="7b396-260">Se uma classe, struct ou enum estiver sendo adicionado ao MRTK, sua finalidade deverá ser descrita.</span><span class="sxs-lookup"><span data-stu-id="7b396-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="7b396-261">Isso é para assumir a forma de um bloco de resumo acima da classe .</span><span class="sxs-lookup"><span data-stu-id="7b396-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="7b396-262">Se houver dependências de nível de classe, elas deverão ser documentadas em um bloco de comentários, imediatamente abaixo do resumo.</span><span class="sxs-lookup"><span data-stu-id="7b396-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="7b396-263">Solicitações de pull enviadas sem resumos para classes, estruturas ou enums não serão aprovadas.</span><span class="sxs-lookup"><span data-stu-id="7b396-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="7b396-264">Blocos de propriedade, método, resumo de eventos</span><span class="sxs-lookup"><span data-stu-id="7b396-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="7b396-265">Propriedades, métodos e eventos (PMEs), bem como campos, devem ser documentados com blocos de resumo, independentemente da visibilidade do código (pública, privada, protegida e interna).</span><span class="sxs-lookup"><span data-stu-id="7b396-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="7b396-266">A ferramenta de geração de documentação é responsável por filtrar e publicar apenas os recursos públicos e protegidos.</span><span class="sxs-lookup"><span data-stu-id="7b396-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="7b396-267">OBSERVAÇÃO: um bloco de resumo **não é** necessário para métodos do Unity (por exemplo: Ativas, Iniciar, Atualizar).</span><span class="sxs-lookup"><span data-stu-id="7b396-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="7b396-268">A documentação do PME **é necessária** para que uma solicitação de pull seja aprovada.</span><span class="sxs-lookup"><span data-stu-id="7b396-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="7b396-269">Como parte de um bloco de resumo do PME, o significado e a finalidade dos parâmetros e dos dados retornados são necessários.</span><span class="sxs-lookup"><span data-stu-id="7b396-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="7b396-270">Versão e dependências de introdução de recursos</span><span class="sxs-lookup"><span data-stu-id="7b396-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="7b396-271">Como parte da documentação de resumo da API, as informações sobre a versão do MRTK na qual o recurso foi introduzido e quaisquer dependências devem ser documentadas em um bloco de comentários.</span><span class="sxs-lookup"><span data-stu-id="7b396-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="7b396-272">As dependências devem incluir dependências de extensão e/ou plataforma.</span><span class="sxs-lookup"><span data-stu-id="7b396-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="7b396-273">Campos serializados</span><span class="sxs-lookup"><span data-stu-id="7b396-273">Serialized fields</span></span>

<span data-ttu-id="7b396-274">É uma boa prática usar o atributo de dica de ferramenta do Unity para fornecer documentação de runtime para os campos de um script no inspetor.</span><span class="sxs-lookup"><span data-stu-id="7b396-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="7b396-275">Para que as opções de configuração sejam incluídas  na documentação da API, os scripts são necessários para incluir pelo menos o conteúdo da dica de ferramenta em um bloco de resumo.</span><span class="sxs-lookup"><span data-stu-id="7b396-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="7b396-276">Valores de enumeração</span><span class="sxs-lookup"><span data-stu-id="7b396-276">Enumeration values</span></span>

<span data-ttu-id="7b396-277">Ao definir e enumerar, o código também deve documentar o significado dos valores de enumeração usando um bloco de resumo.</span><span class="sxs-lookup"><span data-stu-id="7b396-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="7b396-278">Opcionalmente, os blocos de comentários podem ser usados para fornecer detalhes adicionais para aprimorar a compreensão.</span><span class="sxs-lookup"><span data-stu-id="7b396-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="7b396-279">Documentação de como fazer</span><span class="sxs-lookup"><span data-stu-id="7b396-279">How-to documentation</span></span>

<span data-ttu-id="7b396-280">Muitos usuários do Toolkit realidade misturada podem não precisar usar a documentação da API.</span><span class="sxs-lookup"><span data-stu-id="7b396-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="7b396-281">Esses usuários aproveitarão nossos pré-requisitos e scripts pré-feitos e reutilizáveis para criar suas experiências.</span><span class="sxs-lookup"><span data-stu-id="7b396-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="7b396-282">Cada área de recurso conterá um ou mais arquivos markdown (.md) que descrevem em um nível bastante alto, o que é fornecido.</span><span class="sxs-lookup"><span data-stu-id="7b396-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="7b396-283">Dependendo do tamanho e/ou da complexidade de uma determinada área de recurso, pode haver necessidade de arquivos adicionais, até um por recurso fornecido.</span><span class="sxs-lookup"><span data-stu-id="7b396-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="7b396-284">Quando um recurso é adicionado (ou o uso é alterado), a documentação de visão geral deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="7b396-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="7b396-285">Como parte desta documentação, as seções de ida e volta, incluindo ilustrações, devem ser fornecidas para ajudar os clientes novos a um recurso ou conceito de começar.</span><span class="sxs-lookup"><span data-stu-id="7b396-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="7b396-286">Documentação de design</span><span class="sxs-lookup"><span data-stu-id="7b396-286">Design documentation</span></span>

<span data-ttu-id="7b396-287">A Realidade Misturada oferece uma oportunidade de criar mundos totalmente novos.</span><span class="sxs-lookup"><span data-stu-id="7b396-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="7b396-288">Parte disso provavelmente envolverá a criação de ativos personalizados para uso com o MRTK.</span><span class="sxs-lookup"><span data-stu-id="7b396-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="7b396-289">Para tornar isso o mais claro possível para os clientes, os componentes devem fornecer documentação de design que descreve qualquer formatação ou outros requisitos para ativos de arte.</span><span class="sxs-lookup"><span data-stu-id="7b396-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="7b396-290">Alguns exemplos em que a documentação de design pode ser útil:</span><span class="sxs-lookup"><span data-stu-id="7b396-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="7b396-291">Modelos de cursor</span><span class="sxs-lookup"><span data-stu-id="7b396-291">Cursor models</span></span>
- <span data-ttu-id="7b396-292">Visualizações de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="7b396-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="7b396-293">Arquivos de efeito de som</span><span class="sxs-lookup"><span data-stu-id="7b396-293">Sound effect files</span></span>

<span data-ttu-id="7b396-294">Esse tipo de documentação **é altamente** recomendável e **pode** ser solicitado como parte de uma revisão de solicitação de pull.</span><span class="sxs-lookup"><span data-stu-id="7b396-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="7b396-295">Isso pode ou não ser diferente da recomendação de design no [site do Desenvolvedor do MS](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="7b396-295">This may or may not be different from the design recommendation on the [MS Developer site](/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="7b396-296">Notas de desempenho</span><span class="sxs-lookup"><span data-stu-id="7b396-296">Performance notes</span></span>

<span data-ttu-id="7b396-297">Alguns recursos importantes vêm com um custo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="7b396-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="7b396-298">Geralmente, esse código dependerá muito de como eles são configurados.</span><span class="sxs-lookup"><span data-stu-id="7b396-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="7b396-299">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7b396-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="7b396-300">As notas de desempenho são recomendadas para  componentes de CPU e/ou GPU pesada e podem ser solicitadas como parte de uma revisão de solicitação de pull.</span><span class="sxs-lookup"><span data-stu-id="7b396-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="7b396-301">Todas as notas de desempenho aplicáveis devem ser incluídas na API e **na documentação de visão** geral.</span><span class="sxs-lookup"><span data-stu-id="7b396-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="7b396-302">Alterações de quebra</span><span class="sxs-lookup"><span data-stu-id="7b396-302">Breaking changes</span></span>

<span data-ttu-id="7b396-303">A documentação de alterações significativas é composta por um arquivo de nível [superior](../contributing/breaking-changes.md) que se vincula ao arquivo individual de cada área de breaking-changes.md.</span><span class="sxs-lookup"><span data-stu-id="7b396-303">Breaking changes documentation is to consist of a top level [file](../contributing/breaking-changes.md) which links to each feature area's individual breaking-changes.md.</span></span>

<span data-ttu-id="7b396-304">A área de breaking-changes.md arquivos deve conter a lista de todas  as alterações de quebra conhecidas para uma determinada versão, bem como o histórico de alterações significativas de versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="7b396-304">The feature area breaking-changes.md files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="7b396-305">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7b396-305">For example:</span></span>

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

<span data-ttu-id="7b396-306">As informações contidas no nível do recurso breaking-changes.md arquivos serão agregadas às notas de versão de cada nova versão do MRTK.</span><span class="sxs-lookup"><span data-stu-id="7b396-306">The information contained within the feature level breaking-changes.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="7b396-307">Todas as alterações significativas que fazem parte de uma alteração **devem** ser documentadas como parte de uma solicitação de pull.</span><span class="sxs-lookup"><span data-stu-id="7b396-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="7b396-308">Ferramentas para editar MarkDown</span><span class="sxs-lookup"><span data-stu-id="7b396-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="7b396-309">[Visual Studio Code](https://code.visualstudio.com/) é uma ótima ferramenta para editar arquivos markdown que fazem parte da documentação do MRTK.</span><span class="sxs-lookup"><span data-stu-id="7b396-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="7b396-310">Ao escrever a documentação, instalar as duas extensões a seguir também é altamente recomendável:</span><span class="sxs-lookup"><span data-stu-id="7b396-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="7b396-311">Extensão Markdown do Docs para Visual Studio Code – use Alt+M para abrir um menu de opções de autor de documentos.</span><span class="sxs-lookup"><span data-stu-id="7b396-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="7b396-312">Verificador Ortônico de Código – palavras com ortagem inoclinada serão sublinhadas; Clique com o botão direito do mouse em uma palavra com o botão direito do mouse para alterá-la ou salvá-la no dicionário.</span><span class="sxs-lookup"><span data-stu-id="7b396-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="7b396-313">Ambos são empacotados no Pacote de Autorização do Docs publicado pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7b396-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b396-314">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b396-314">See also</span></span>

- [<span data-ttu-id="7b396-315">Exemplo de link "consulte também" para documentação</span><span class="sxs-lookup"><span data-stu-id="7b396-315">Example "see also" link for documentation</span></span>](https://www.microsoft.com)
