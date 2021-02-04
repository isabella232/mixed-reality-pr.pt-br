---
title: Como configurar a Ferramenta de Recursos de Realidade Misturada
description: Saiba como baixar e instalar os pacotes do Unity de Realidade Misturada por meio da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243856"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="48ce1-104">Como configurar a Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="48ce1-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="48ce1-105">Ao usar a Ferramenta de Recursos de Realidade Misturada, você tem acesso a três categorias de configurações diferentes que podem ser personalizadas conforme desejado:</span><span class="sxs-lookup"><span data-stu-id="48ce1-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="48ce1-106">Configurações de download</span><span class="sxs-lookup"><span data-stu-id="48ce1-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="48ce1-107">Configurações do recurso</span><span class="sxs-lookup"><span data-stu-id="48ce1-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="48ce1-108">Configurações de importação</span><span class="sxs-lookup"><span data-stu-id="48ce1-108">Import settings</span></span>](#import-settings)

![Configurações](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="48ce1-110">Configurações de download</span><span class="sxs-lookup"><span data-stu-id="48ce1-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="48ce1-111">Substituir arquivos de pacote existentes</span><span class="sxs-lookup"><span data-stu-id="48ce1-111">Overwrite existing package files</span></span>

<span data-ttu-id="48ce1-112">A habilitação dessa configuração faz com que os arquivos de pacote sejam baixados toda vez que são adquiridos.</span><span class="sxs-lookup"><span data-stu-id="48ce1-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="48ce1-113">**Recomendamos manter essa opção desabilitada para reduzir o uso de largura de banda da rede**</span><span class="sxs-lookup"><span data-stu-id="48ce1-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="48ce1-114">Por padrão, os arquivos de pacote adquiridos anteriormente não são baixados novamente</span><span class="sxs-lookup"><span data-stu-id="48ce1-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="48ce1-115">Cache de pacote</span><span class="sxs-lookup"><span data-stu-id="48ce1-115">Package cache</span></span>

<span data-ttu-id="48ce1-116">Altere essa configuração para atualizar o local de download dos pacotes de recursos.</span><span class="sxs-lookup"><span data-stu-id="48ce1-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="48ce1-117">Essa configuração é **somente leitura** nesta versão.</span><span class="sxs-lookup"><span data-stu-id="48ce1-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="48ce1-118">As versões futuras poderão torná-la configurável.</span><span class="sxs-lookup"><span data-stu-id="48ce1-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="48ce1-119">Configurações do recurso</span><span class="sxs-lookup"><span data-stu-id="48ce1-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="48ce1-120">Incluir versões prévias</span><span class="sxs-lookup"><span data-stu-id="48ce1-120">Include preview releases</span></span>

<span data-ttu-id="48ce1-121">Habilite essa configuração para adquirir as versões prévias.</span><span class="sxs-lookup"><span data-stu-id="48ce1-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="48ce1-122">Por padrão, as versões prévias não são mostradas na Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="48ce1-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="48ce1-123">Uma versão prévia é definida como contendo a designação **"-preview"** na versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="48ce1-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="48ce1-124">Configurações de importação</span><span class="sxs-lookup"><span data-stu-id="48ce1-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="48ce1-125">Substituir os arquivos de pacote existentes</span><span class="sxs-lookup"><span data-stu-id="48ce1-125">Replace existing package files</span></span>

<span data-ttu-id="48ce1-126">Por padrão, a Ferramenta de Recursos de Realidade Misturada remove as cópias anteriores dos pacotes que estão sendo importados para reduzir o tamanho do arquivo e as computações desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="48ce1-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="48ce1-127">Desmarque essa configuração para manter todas as versões</span><span class="sxs-lookup"><span data-stu-id="48ce1-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="48ce1-128">Caminho relativo de importação do projeto</span><span class="sxs-lookup"><span data-stu-id="48ce1-128">Project relative import path</span></span>

<span data-ttu-id="48ce1-129">Altere essa configuração para atualizar o caminho da pasta do projeto na qual os pacotes de recursos são copiados durante a importação.</span><span class="sxs-lookup"><span data-stu-id="48ce1-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="48ce1-130">Por exemplo, se a pasta do projeto for **C:\GalaxyExplorer**, o caminho de importação totalmente qualificado será **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="48ce1-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="48ce1-131">Essa configuração é **somente leitura** nesta versão.</span><span class="sxs-lookup"><span data-stu-id="48ce1-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="48ce1-132">As versões futuras poderão torná-la configurável.</span><span class="sxs-lookup"><span data-stu-id="48ce1-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="48ce1-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="48ce1-133">See also</span></span>

- [<span data-ttu-id="48ce1-134">Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="48ce1-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)