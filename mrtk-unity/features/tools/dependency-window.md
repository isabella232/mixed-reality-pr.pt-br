---
title: Janela de dependência
description: Documentação sobre o uso da janela de dependência no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176666"
---
# <a name="dependency-window"></a><span data-ttu-id="55c76-104">Janela de dependência</span><span class="sxs-lookup"><span data-stu-id="55c76-104">Dependency window</span></span>

<span data-ttu-id="55c76-105">No Unity, geralmente é difícil gleam quais ativos estão sendo usados e o que está fazendo referência a eles.</span><span class="sxs-lookup"><span data-stu-id="55c76-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="55c76-106">A opção "localizar referências na cena" funciona muito bem quando você está preocupado apenas com a cena atual, mas e quanto a todo o seu projeto de Unity?</span><span class="sxs-lookup"><span data-stu-id="55c76-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="55c76-107">É aí que a **janela de dependência** (assets/MRTK/Tools/DependencyWindow) pode ser útil.</span><span class="sxs-lookup"><span data-stu-id="55c76-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="55c76-108">A janela dependência exibe como a referência de ativos depende uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="55c76-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="55c76-109">As dependências são calculadas pela análise de GUIDs nos arquivos do Project YAML (Observe que as dependências de script para script não são consideradas).</span><span class="sxs-lookup"><span data-stu-id="55c76-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="55c76-110">Uso</span><span class="sxs-lookup"><span data-stu-id="55c76-110">Usage</span></span>

<span data-ttu-id="55c76-111">para abrir a janela, selecione Toolkit janela de dependência de utilitários de **realidade misturada**  >    >    >   que abrirá a janela e começará automaticamente a criar o grafo de dependência do projeto.</span><span class="sxs-lookup"><span data-stu-id="55c76-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="55c76-112">Depois que o grafo de dependência for criado, você poderá selecionar ativos na guia projeto para inspecionar suas dependências.</span><span class="sxs-lookup"><span data-stu-id="55c76-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![Janela de dependência](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="55c76-114">A janela exibe uma lista de ativos dos quais o ativo atualmente selecionado depende e uma lista hierárquica de ativos que dependem dele.</span><span class="sxs-lookup"><span data-stu-id="55c76-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="55c76-115">Se nada depender do ativo selecionado no momento, você poderá considerar excluí-lo do seu projeto (Observe que alguns ativos são carregados programaticamente por meio de APIs como shader. Find () e não podem ser capturados pelo rastreador de dependências).</span><span class="sxs-lookup"><span data-stu-id="55c76-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="55c76-116">A janela também pode exibir apenas uma lista de todos os ativos que não são referenciados por outros ativos e podem ser considerados para exclusão:</span><span class="sxs-lookup"><span data-stu-id="55c76-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![Janela de dependência mostrando ativos não referenciados](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="55c76-118">Se os ativos forem modificados, adicionados ou removidos enquanto a janela de dependência estiver em uso, é aconselhável atualizar o grafo de dependência para os resultados mais "atualizados".</span><span class="sxs-lookup"><span data-stu-id="55c76-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
