---
title: Como configurar a Ferramenta de Recursos de Realidade Misturada
description: Saiba como baixar e instalar os pacotes do Unity de Realidade Misturada por meio da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731928"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="031a5-104">Como configurar a Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="031a5-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="031a5-105">Ao usar a Ferramenta de Recursos de Realidade Misturada, você tem acesso a três categorias de configurações diferentes que podem ser personalizadas conforme desejado:</span><span class="sxs-lookup"><span data-stu-id="031a5-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="031a5-106">Configurações de download</span><span class="sxs-lookup"><span data-stu-id="031a5-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="031a5-107">Configurações do recurso</span><span class="sxs-lookup"><span data-stu-id="031a5-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="031a5-108">Configurações de importação</span><span class="sxs-lookup"><span data-stu-id="031a5-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="031a5-109">Configurações de download</span><span class="sxs-lookup"><span data-stu-id="031a5-109">Download settings</span></span>

![Configurações de download](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="031a5-111">Substituir arquivos de pacote existentes</span><span class="sxs-lookup"><span data-stu-id="031a5-111">Overwrite existing package files</span></span>

<span data-ttu-id="031a5-112">A habilitação dessa configuração faz com que os arquivos de pacote sejam baixados toda vez que são adquiridos.</span><span class="sxs-lookup"><span data-stu-id="031a5-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="031a5-113">**Recomendamos manter essa opção desabilitada para reduzir o uso de largura de banda da rede**</span><span class="sxs-lookup"><span data-stu-id="031a5-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="031a5-114">Por padrão, os arquivos de pacote adquiridos anteriormente não são baixados novamente</span><span class="sxs-lookup"><span data-stu-id="031a5-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="031a5-115">Cache de pacote</span><span class="sxs-lookup"><span data-stu-id="031a5-115">Package cache</span></span>

<span data-ttu-id="031a5-116">Altere essa configuração para atualizar o local de download dos pacotes de recursos.</span><span class="sxs-lookup"><span data-stu-id="031a5-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="031a5-117">Essa configuração é **somente leitura** nesta versão.</span><span class="sxs-lookup"><span data-stu-id="031a5-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="031a5-118">As versões futuras poderão torná-la configurável.</span><span class="sxs-lookup"><span data-stu-id="031a5-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="031a5-119">Configurações do recurso</span><span class="sxs-lookup"><span data-stu-id="031a5-119">Feature settings</span></span>

![Configurações do recurso](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="031a5-121">Mostrar versões prévias</span><span class="sxs-lookup"><span data-stu-id="031a5-121">Show preview releases</span></span>

<span data-ttu-id="031a5-122">Habilite essa configuração para adquirir as versões prévias.</span><span class="sxs-lookup"><span data-stu-id="031a5-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="031a5-123">Por padrão, as versões prévias não são mostradas na Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="031a5-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="031a5-124">Uma versão prévia é definida como contendo a designação **"-preview"** na versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="031a5-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="031a5-125">Mostrar recursos do programa de acesso antecipado</span><span class="sxs-lookup"><span data-stu-id="031a5-125">Show early access program features</span></span>

<span data-ttu-id="031a5-126">Habilite essa configuração para adquirir recursos de versões dos programas de acesso antecipado registrados.</span><span class="sxs-lookup"><span data-stu-id="031a5-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="031a5-127">Por padrão, os recursos de acesso antecipado não são mostrados na Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="031a5-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="031a5-128">A habilitação de `Show early access program features` sem `Show preview releases` pode fazer com que os pacotes de acesso antecipado não sejam exibidos na Descoberta.</span><span class="sxs-lookup"><span data-stu-id="031a5-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="031a5-129">Configurações de importação</span><span class="sxs-lookup"><span data-stu-id="031a5-129">Import settings</span></span>

![Configurações de importação](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="031a5-131">Substituir os arquivos de pacote existentes</span><span class="sxs-lookup"><span data-stu-id="031a5-131">Replace existing package files</span></span>

<span data-ttu-id="031a5-132">Por padrão, a Ferramenta de Recursos de Realidade Misturada remove as cópias anteriores dos pacotes que estão sendo importados para reduzir o tamanho do arquivo e as computações desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="031a5-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="031a5-133">Desmarque essa configuração para manter todas as versões</span><span class="sxs-lookup"><span data-stu-id="031a5-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="031a5-134">Caminho relativo de importação do projeto</span><span class="sxs-lookup"><span data-stu-id="031a5-134">Project relative import path</span></span>

<span data-ttu-id="031a5-135">Altere essa configuração para atualizar o caminho da pasta do projeto na qual os pacotes de recursos são copiados durante a importação.</span><span class="sxs-lookup"><span data-stu-id="031a5-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="031a5-136">Por exemplo, se a pasta do projeto for **C:\GalaxyExplorer**, o caminho de importação totalmente qualificado será **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="031a5-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="031a5-137">Essa configuração é **somente leitura** nesta versão.</span><span class="sxs-lookup"><span data-stu-id="031a5-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="031a5-138">As versões futuras poderão torná-la configurável.</span><span class="sxs-lookup"><span data-stu-id="031a5-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="031a5-139">Configurações de acesso antecipado</span><span class="sxs-lookup"><span data-stu-id="031a5-139">Early Access settings</span></span>

![Configurações de acesso antecipado](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="031a5-141">Solicitar confirmação antes de remover um programa de acesso antecipado</span><span class="sxs-lookup"><span data-stu-id="031a5-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="031a5-142">Essa configuração determina se um aviso será exibido toda vez que um programa de acesso antecipado for removido.</span><span class="sxs-lookup"><span data-stu-id="031a5-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="031a5-143">Minhas versões prévias</span><span class="sxs-lookup"><span data-stu-id="031a5-143">My previews</span></span>

<span data-ttu-id="031a5-144">A lista de programas de acesso antecipado registrados.</span><span class="sxs-lookup"><span data-stu-id="031a5-144">The list of registered early access programs.</span></span> <span data-ttu-id="031a5-145">Use `Add`, `Edit` e `Remove` para gerenciar a coleção de programas registrados.</span><span class="sxs-lookup"><span data-stu-id="031a5-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="031a5-146">Configurações de Diagnóstico</span><span class="sxs-lookup"><span data-stu-id="031a5-146">Diagnostic settings</span></span>

![Configurações de Diagnóstico](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="031a5-148">Arquivo de log</span><span class="sxs-lookup"><span data-stu-id="031a5-148">Log file</span></span>

<span data-ttu-id="031a5-149">Exibe o caminho para o arquivo de log de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="031a5-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="031a5-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="031a5-150">See also</span></span>

- [<span data-ttu-id="031a5-151">Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="031a5-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)