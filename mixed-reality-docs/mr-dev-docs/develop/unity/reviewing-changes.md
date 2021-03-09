---
title: Como autorizar as alterações de projeto
description: Saiba como autorizar as alterações de projeto na Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230748"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="8f6ce-104">Como autorizar as alterações de projeto</span><span class="sxs-lookup"><span data-stu-id="8f6ce-104">Authorizing project changes</span></span>

<span data-ttu-id="8f6ce-105">Antes da modificação do projeto do Unity, as alterações nos arquivos de projeto e de manifesto precisam ser examinadas e aprovadas:</span><span class="sxs-lookup"><span data-stu-id="8f6ce-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![Como solicitar a autorização](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="8f6ce-107">Manifest</span><span class="sxs-lookup"><span data-stu-id="8f6ce-107">Manifest</span></span>

<span data-ttu-id="8f6ce-108">As alterações de manifesto propostas podem ser exibidas na coluna **Manifesto** à esquerda.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="8f6ce-109">O conteúdo é exatamente o que será gravado no manifesto do projeto (**Packages/manifest.json**):</span><span class="sxs-lookup"><span data-stu-id="8f6ce-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![Visualização do manifesto](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="8f6ce-111">Arquivos a serem copiados para o projeto</span><span class="sxs-lookup"><span data-stu-id="8f6ce-111">Files to be copied into the project</span></span>

<span data-ttu-id="8f6ce-112">A seção **Arquivos a serem copiados para o projeto** à direita lista os arquivos do pacote de recursos específicos que serão copiados para o projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="8f6ce-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![Visualização do manifesto com os arquivos a serem copiados](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="8f6ce-114">Comparar manifestos</span><span class="sxs-lookup"><span data-stu-id="8f6ce-114">Compare manifests</span></span>

<span data-ttu-id="8f6ce-115">Você pode ver uma comparação detalhada lado a lado de todas as alterações propostas selecionando **Comparar**:</span><span class="sxs-lookup"><span data-stu-id="8f6ce-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![Comparar manifestos](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="8f6ce-117">Como aprovar as alterações</span><span class="sxs-lookup"><span data-stu-id="8f6ce-117">Approving changes</span></span>

<span data-ttu-id="8f6ce-118">Quando as alterações propostas forem aprovadas, os arquivos listados serão copiados para o projeto do Unity e o manifesto será atualizado com referências a esses arquivos.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="8f6ce-119">Os arquivos do pacote de recursos (\*.tgz) devem ser adicionados ao controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="8f6ce-120">Eles são referenciados usando um caminho relativo para permitir que as equipes de desenvolvimento compartilhem os recursos e as alterações de manifesto com facilidade.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="8f6ce-121">Como parte das modificações, o arquivo **manifest.json** atual será copiado em backup.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f6ce-122">Ao exibir os backups de manifesto, o mais antigo será chamado **manifest.json.backup**.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="8f6ce-123">Os backups mais recentes serão anotados com um valor numérico, começando com zero (0).</span><span class="sxs-lookup"><span data-stu-id="8f6ce-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="8f6ce-124">Como voltar à etapa anterior</span><span class="sxs-lookup"><span data-stu-id="8f6ce-124">Going back to the previous step</span></span>

<span data-ttu-id="8f6ce-125">Caso você precise fazer alterações às seleções de recursos, use **Voltar** para retornar à etapa [Importar](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="8f6ce-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f6ce-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="8f6ce-126">See also</span></span>

- [<span data-ttu-id="8f6ce-127">Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="8f6ce-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="8f6ce-128">Como importar os pacotes selecionados</span><span class="sxs-lookup"><span data-stu-id="8f6ce-128">Importing selected packages</span></span>](importing-features.md)
