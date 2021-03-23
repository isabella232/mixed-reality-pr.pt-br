---
title: Como importar recursos
description: Saiba como importar e instalar recursos da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230799"
---
# <a name="importing-features"></a><span data-ttu-id="94fb7-104">Como importar recursos</span><span class="sxs-lookup"><span data-stu-id="94fb7-104">Importing features</span></span>

<span data-ttu-id="94fb7-105">Depois que os recursos forem baixados, eles poderão ser examinados e importados para o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="94fb7-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="94fb7-106">Nesta etapa, a janela do aplicativo será parecida com a seguinte imagem:</span><span class="sxs-lookup"><span data-stu-id="94fb7-106">At this step, your application window should look like the following image:</span></span>

![Como importar recursos](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="94fb7-108">Lista de recursos</span><span class="sxs-lookup"><span data-stu-id="94fb7-108">Features list</span></span>

<span data-ttu-id="94fb7-109">A lista **Recursos** contém a coleção de pacotes selecionados durante a descoberta.</span><span class="sxs-lookup"><span data-stu-id="94fb7-109">The **Features** list contains the collection of packages selected during discovery.</span></span> <span data-ttu-id="94fb7-110">Cada recurso pode ser selecionado ou desmarcado antes da importação.</span><span class="sxs-lookup"><span data-stu-id="94fb7-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="94fb7-111">Os detalhes do pacote podem ser exibidos por meio do link **Detalhes** mostrado abaixo</span><span class="sxs-lookup"><span data-stu-id="94fb7-111">Package details can be viewed using the **Details** link shown below</span></span>

![Lista de recursos](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="94fb7-113">Lista de dependências necessárias</span><span class="sxs-lookup"><span data-stu-id="94fb7-113">Required dependencies list</span></span>

<span data-ttu-id="94fb7-114">A lista **Dependências necessárias** contém os pacotes que um ou mais dos recursos selecionados exigem para funcionar.</span><span class="sxs-lookup"><span data-stu-id="94fb7-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="94fb7-115">Essa lista também conterá dependências de dependências.</span><span class="sxs-lookup"><span data-stu-id="94fb7-115">This list will also contain dependencies of dependencies.</span></span> <span data-ttu-id="94fb7-116">Cada dependência pode ser selecionada ou desmarcada antes da importação.</span><span class="sxs-lookup"><span data-stu-id="94fb7-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="94fb7-117">Os detalhes do pacote podem ser exibidos por meio do link **Detalhes** mostrado abaixo</span><span class="sxs-lookup"><span data-stu-id="94fb7-117">Package details can be viewed using the **Details** link shown below</span></span>

![Lista de dependências](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="94fb7-119">Se você desmarcar as dependências necessárias, um ou mais erros de dependência ausente serão exibidos ao carregar o projeto no Unity.</span><span class="sxs-lookup"><span data-stu-id="94fb7-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="94fb7-120">Esses recursos não poderão ser usados no projeto.</span><span class="sxs-lookup"><span data-stu-id="94fb7-120">These features won't be usable in the project.</span></span>

## <a name="validating-selections"></a><span data-ttu-id="94fb7-121">Como validar as seleções</span><span class="sxs-lookup"><span data-stu-id="94fb7-121">Validating selections</span></span>

<span data-ttu-id="94fb7-122">Recomendamos expressamente validar as seleções de recursos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="94fb7-122">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="94fb7-123">Esta etapa vai gerar todos os problemas que provavelmente impedem o desenvolvimento bem-sucedido do projeto.</span><span class="sxs-lookup"><span data-stu-id="94fb7-123">This step will raise any issues that are likely to impede successful project development.</span></span>

![Problemas de validação](images/ValidationIssues.png)

<span data-ttu-id="94fb7-125">A Ferramenta de Recursos de Realidade Misturada fornece duas resoluções de problemas automáticas (descritas nas seções a seguir) e a opção de cancelar e resolver problemas manualmente.</span><span class="sxs-lookup"><span data-stu-id="94fb7-125">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="94fb7-126">Habilitar dependências</span><span class="sxs-lookup"><span data-stu-id="94fb7-126">Enable dependencies</span></span>

<span data-ttu-id="94fb7-127">O botão **Habilitar dependências** selecionará automaticamente as dependências ausentes.</span><span class="sxs-lookup"><span data-stu-id="94fb7-127">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="94fb7-128">Isso é verdadeiro para as dependências que foram selecionadas explicitamente (exibidas na lista **Recursos**) e para aquelas selecionadas implicitamente com base nos requisitos dos recursos escolhidos.</span><span class="sxs-lookup"><span data-stu-id="94fb7-128">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="94fb7-129">Desabilitar recursos</span><span class="sxs-lookup"><span data-stu-id="94fb7-129">Disable features</span></span>

<span data-ttu-id="94fb7-130">A seleção de **Desabilitar recursos** desmarcará automaticamente qualquer recurso que dependa de uma ou mais das dependências que foram desmarcadas.</span><span class="sxs-lookup"><span data-stu-id="94fb7-130">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="94fb7-131">Isso é verdadeiro para pacotes de dependência selecionados implicitamente e recursos selecionados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="94fb7-131">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="94fb7-132">Importação</span><span class="sxs-lookup"><span data-stu-id="94fb7-132">Importing</span></span>

<span data-ttu-id="94fb7-133">Selecione **Importar** para adicionar os recursos selecionados e conceder [aprovação final](reviewing-changes.md) antes de atualizar o projeto de destino.</span><span class="sxs-lookup"><span data-stu-id="94fb7-133">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94fb7-134">Se um problema de validação permanecer durante a importação, uma mensagem de aviso será exibida.</span><span class="sxs-lookup"><span data-stu-id="94fb7-134">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="94fb7-135">Recomendamos selecionar Não, clicar em **Validar** e resolver os problemas apresentados.</span><span class="sxs-lookup"><span data-stu-id="94fb7-135">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Continuar com problemas de validação](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="94fb7-137">Como voltar à etapa anterior</span><span class="sxs-lookup"><span data-stu-id="94fb7-137">Going back to the previous step</span></span>

<span data-ttu-id="94fb7-138">Em **Importar recursos**, a Ferramenta de Recursos de Realidade Misturada permite navegar de volta à [descoberta](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="94fb7-138">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="94fb7-139">Selecione **Voltar** para baixar outros pacotes de recursos.</span><span class="sxs-lookup"><span data-stu-id="94fb7-139">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="94fb7-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="94fb7-140">See also</span></span>

- [<span data-ttu-id="94fb7-141">Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="94fb7-141">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="94fb7-142">Descoberta e aquisição</span><span class="sxs-lookup"><span data-stu-id="94fb7-142">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="94fb7-143">Como exibir detalhes do pacote de recursos</span><span class="sxs-lookup"><span data-stu-id="94fb7-143">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="94fb7-144">Como examinar e aprovar as modificações do projeto</span><span class="sxs-lookup"><span data-stu-id="94fb7-144">Reviewing and approving project modifications</span></span>](reviewing-changes.md)