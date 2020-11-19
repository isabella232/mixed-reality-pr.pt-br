---
title: Idioma principal
description: Saiba mais sobre os detalhes da linguagem principal do maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realidade mista do Windows, maquette, protótipoing, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935357"
---
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="52b82-104">Detalhes da linguagem MaquetteScript Core</span><span class="sxs-lookup"><span data-stu-id="52b82-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="52b82-105">![Detalhes do ](../images/MaquetteIcon.png) idioma principal do maquette logo MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="52b82-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="52b82-106">Acessando `Maquette` objeto e namespace</span><span class="sxs-lookup"><span data-stu-id="52b82-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="52b82-107">O maquette expõe objetos internos e interfaces em JavaScript por meio do `Maquette` objeto e de seus filhos.</span><span class="sxs-lookup"><span data-stu-id="52b82-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="52b82-108">Essa funcionalidade é descrita no [objeto maquette e](https://www.maquette.ms/doc_staging/objects/Maquette.html) na documentação do namespace.</span><span class="sxs-lookup"><span data-stu-id="52b82-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="52b82-109">O `Maquette` objeto tem funções de nível superior para facilitar a interação com o próprio maquette e facilitar a solução de problemas repetitivos.</span><span class="sxs-lookup"><span data-stu-id="52b82-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="52b82-110">Isso é descrito na documentação do [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span><span class="sxs-lookup"><span data-stu-id="52b82-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="52b82-111">Inicialização e carregamento do maquette</span><span class="sxs-lookup"><span data-stu-id="52b82-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="52b82-112">O maquette carregará e avaliará arquivos JavaScript específicos para habilitar a configuração, a instalação e a inicialização nos seguintes horários:</span><span class="sxs-lookup"><span data-stu-id="52b82-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="52b82-113">Durante a inicialização do maquette:</span><span class="sxs-lookup"><span data-stu-id="52b82-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="52b82-114">Sempre que qualquer projeto for carregado:</span><span class="sxs-lookup"><span data-stu-id="52b82-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="52b82-115">Os projetos carregam seus respectivos scripts de projeto:</span><span class="sxs-lookup"><span data-stu-id="52b82-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="52b82-116">Implementação de JavaScript</span><span class="sxs-lookup"><span data-stu-id="52b82-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="52b82-117">O interpretador JavaScript usado em maquette é baseado em [Jint](https://github.com/sebastienros/jint).</span><span class="sxs-lookup"><span data-stu-id="52b82-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="52b82-118">O Jint é compatível com ECMAScript 5,1 e dá suporte a [extensões adicionais do ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span><span class="sxs-lookup"><span data-stu-id="52b82-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="52b82-119">A extensão `.mqjs` é usada para distinguir arquivos JavaScript maquette do JavaScript normal.</span><span class="sxs-lookup"><span data-stu-id="52b82-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="52b82-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="52b82-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->