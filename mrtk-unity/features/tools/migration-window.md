---
title: Janela de migração
description: Documentação sobre como migrar para uma atualização no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 9d960d01e738736edd452a124db5c306b5d752ce
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176132"
---
# <a name="migration-window"></a><span data-ttu-id="bf99b-104">Janela de migração</span><span class="sxs-lookup"><span data-stu-id="bf99b-104">Migration window</span></span>

<span data-ttu-id="bf99b-105">À medida que o MRTK passa por alterações, alguns componentes podem ser preteridos e substituições serão introduzidas.</span><span class="sxs-lookup"><span data-stu-id="bf99b-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="bf99b-106">A janela de migração é uma ferramenta que ajuda os usuários a migrar automaticamente um subconjunto desses componentes preteridos para as novas substituições.</span><span class="sxs-lookup"><span data-stu-id="bf99b-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![Janela de migração](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="bf99b-108">Uso</span><span class="sxs-lookup"><span data-stu-id="bf99b-108">Usage</span></span>

<span data-ttu-id="bf99b-109">para abrir a janela, selecione a janela de migração da **realidade mista**  >  **Toolkit**  >  **Utilities**  >  .</span><span class="sxs-lookup"><span data-stu-id="bf99b-109">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Migration Window**.</span></span> <span data-ttu-id="bf99b-110">Quando a janela de migração estiver aberta, as guias de navegação do modo de seleção poderão ser habilitadas escolhendo a implementação específica do componente do manipulador de migração.</span><span class="sxs-lookup"><span data-stu-id="bf99b-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Modos de seleção de migração](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="bf99b-112">Modo de objeto</span><span class="sxs-lookup"><span data-stu-id="bf99b-112">Object mode</span></span>

<span data-ttu-id="bf99b-113">A seleção da guia objetos habilita o campo objeto para onde o usuário pode arrastar e soltar qualquer objeto de jogo da cena aberta no momento ou pré-fabricados da pasta do projeto a ser migrada.</span><span class="sxs-lookup"><span data-stu-id="bf99b-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="bf99b-114">Pressionar o botão Remover *(-)* exibido no lado direito do objeto listado remove o objeto da lista de seleção.</span><span class="sxs-lookup"><span data-stu-id="bf99b-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="bf99b-115">Depois que todos os objetos desejados estiverem na lista, pressionar o botão *migrar* aplicará as alterações exigidas pela implementação do manipulador de migração escolhido para todos os componentes na seleção que correspondam à implementação.</span><span class="sxs-lookup"><span data-stu-id="bf99b-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Migração de seleção](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="bf99b-117">Modo de cena</span><span class="sxs-lookup"><span data-stu-id="bf99b-117">Scene mode</span></span>

<span data-ttu-id="bf99b-118">Permite que o usuário arraste e solte ativos de cena contendo objetos a serem migrados.</span><span class="sxs-lookup"><span data-stu-id="bf99b-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Selecionando cenas para migração](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="bf99b-120">modo de Project</span><span class="sxs-lookup"><span data-stu-id="bf99b-120">Project mode</span></span>

<span data-ttu-id="bf99b-121">Pressionar o botão *migrar* atualizará o componente direcionado pela implementação do manipulador de migração para todos os pré-fabricados e cenas no projeto.</span><span class="sxs-lookup"><span data-stu-id="bf99b-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Migrando um projeto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="bf99b-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf99b-123">See also</span></span>

- [<span data-ttu-id="bf99b-124">Atualizando de versões anteriores</span><span class="sxs-lookup"><span data-stu-id="bf99b-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="bf99b-125">Microsoft Mixed reality Toolkit versões</span><span class="sxs-lookup"><span data-stu-id="bf99b-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="bf99b-126">Roteiro do MRTK</span><span class="sxs-lookup"><span data-stu-id="bf99b-126">MRTK roadmap</span></span>](../../roadmap.md)
