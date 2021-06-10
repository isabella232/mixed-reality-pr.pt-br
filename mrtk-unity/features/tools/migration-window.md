---
title: Janela de migração
description: Documentação sobre como migrar para uma atualização no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647119"
---
# <a name="migration-window"></a><span data-ttu-id="a49bd-104">Janela de migração</span><span class="sxs-lookup"><span data-stu-id="a49bd-104">Migration window</span></span>

<span data-ttu-id="a49bd-105">À medida que o MRTK passa por alterações, alguns componentes podem ser preterido e as substituições serão introduzidas.</span><span class="sxs-lookup"><span data-stu-id="a49bd-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="a49bd-106">A janela de migração é uma ferramenta que ajuda os usuários a migrar automaticamente um subconjunto desses componentes preterido para as novas substituições.</span><span class="sxs-lookup"><span data-stu-id="a49bd-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![Janela de migração](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="a49bd-108">Uso</span><span class="sxs-lookup"><span data-stu-id="a49bd-108">Usage</span></span>

<span data-ttu-id="a49bd-109">Para abrir a janela, selecione Janela **de** Migração de Utilitários do Kit de Ferramentas de Realidade  >    >    >  **Misturada**.</span><span class="sxs-lookup"><span data-stu-id="a49bd-109">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Migration Window**.</span></span> <span data-ttu-id="a49bd-110">Depois que a janela de migração for aberta, as guias de navegação do modo de seleção poderão ser habilitadas escolhendo a implementação específica do componente do manipulador de migração.</span><span class="sxs-lookup"><span data-stu-id="a49bd-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Modos de seleção de migração](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="a49bd-112">Modo de objeto</span><span class="sxs-lookup"><span data-stu-id="a49bd-112">Object mode</span></span>

<span data-ttu-id="a49bd-113">Selecionar a guia objetos permite que o objeto Campo para o qual o usuário possa arrastar e soltar qualquer objeto Game da cena aberta no momento ou pré-requisitos da pasta do projeto a ser migrado.</span><span class="sxs-lookup"><span data-stu-id="a49bd-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="a49bd-114">Pressionar o botão *remover (-)* exibido no lado direito do objeto listado remove o objeto da lista de seleção.</span><span class="sxs-lookup"><span data-stu-id="a49bd-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="a49bd-115">Depois que todos os objetos desejados estão na lista, pressionar o botão *Migrar* aplicará as alterações exigidas pela implementação do manipulador de migração escolhido a todos os componentes na seleção que corresponderem à implementação.</span><span class="sxs-lookup"><span data-stu-id="a49bd-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Migração de seleção](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="a49bd-117">Modo de cena</span><span class="sxs-lookup"><span data-stu-id="a49bd-117">Scene mode</span></span>

<span data-ttu-id="a49bd-118">Permite que o usuário arraste e solte os ativos de cena que contêm objetos a serem migrados.</span><span class="sxs-lookup"><span data-stu-id="a49bd-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Selecionando cenas para migração](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="a49bd-120">Modo de projeto</span><span class="sxs-lookup"><span data-stu-id="a49bd-120">Project mode</span></span>

<span data-ttu-id="a49bd-121">Pressionar o *botão Migrar* atualizará o componente direcionado pela implementação do manipulador de migração para todos os pré-requisitos e cenas no projeto.</span><span class="sxs-lookup"><span data-stu-id="a49bd-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Migrando um projeto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="a49bd-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="a49bd-123">See also</span></span>

- [<span data-ttu-id="a49bd-124">Atualização de versões anteriores</span><span class="sxs-lookup"><span data-stu-id="a49bd-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="a49bd-125">Versões do Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a49bd-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="a49bd-126">Roteiro do MRTK</span><span class="sxs-lookup"><span data-stu-id="a49bd-126">MRTK roadmap</span></span>](../../roadmap.md)
