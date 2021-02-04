---
title: Como importar recursos
description: Saiba como importar e instalar recursos da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: a82eea93a07b662314f3a718eef0c1bd18a4ca4e
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243848"
---
# <a name="importing-features"></a><span data-ttu-id="00e23-104">Como importar recursos</span><span class="sxs-lookup"><span data-stu-id="00e23-104">Importing features</span></span>

<span data-ttu-id="00e23-105">Depois que os recursos forem baixados, eles poderão ser examinados e importados para o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="00e23-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="00e23-106">Nesta etapa, a janela do aplicativo será parecida com a seguinte imagem:</span><span class="sxs-lookup"><span data-stu-id="00e23-106">At this step, your application window should look like the following image:</span></span>

![Como importar recursos](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="00e23-108">Lista de recursos</span><span class="sxs-lookup"><span data-stu-id="00e23-108">Features list</span></span>

<span data-ttu-id="00e23-109">A lista **Recursos** contém a coleção de pacotes selecionados durante a descoberta.</span><span class="sxs-lookup"><span data-stu-id="00e23-109">The **Features** list contains the collection of packages selected during discovery.</span></span> 
* <span data-ttu-id="00e23-110">Cada recurso pode ser selecionado ou desmarcado antes da importação.</span><span class="sxs-lookup"><span data-stu-id="00e23-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="00e23-111">Os detalhes do pacote podem ser exibidos por meio do link **Detalhes** mostrado abaixo</span><span class="sxs-lookup"><span data-stu-id="00e23-111">Package details can be viewed using the **Details** link shown below</span></span>

![Lista de recursos](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="00e23-113">Lista de dependências necessárias</span><span class="sxs-lookup"><span data-stu-id="00e23-113">Required dependencies list</span></span>

<span data-ttu-id="00e23-114">A lista **Dependências necessárias** contém os pacotes que um ou mais dos recursos selecionados exigem para funcionar.</span><span class="sxs-lookup"><span data-stu-id="00e23-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="00e23-115">Essa lista também conterá dependências de dependências.</span><span class="sxs-lookup"><span data-stu-id="00e23-115">This list will also contain dependencies of dependencies.</span></span>
* <span data-ttu-id="00e23-116">Cada dependência pode ser selecionada ou desmarcada antes da importação.</span><span class="sxs-lookup"><span data-stu-id="00e23-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="00e23-117">Os detalhes do pacote podem ser exibidos por meio do link **Detalhes** mostrado abaixo</span><span class="sxs-lookup"><span data-stu-id="00e23-117">Package details can be viewed using the **Details** link shown below</span></span>

![Lista de dependências](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="00e23-119">Se você desmarcar as dependências necessárias, um ou mais erros de dependência ausente serão exibidos ao carregar o projeto no Unity.</span><span class="sxs-lookup"><span data-stu-id="00e23-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="00e23-120">Esses recursos não poderão ser usados no projeto.</span><span class="sxs-lookup"><span data-stu-id="00e23-120">These features won't be usable in the project.</span></span>

## <a name="specifying-the-unity-project-path"></a><span data-ttu-id="00e23-121">Como especificar o caminho do projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="00e23-121">Specifying the Unity project path</span></span>

<span data-ttu-id="00e23-122">A fim de importar os recursos para o projeto, você precisará registrar o caminho na Ferramenta de Recursos de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="00e23-122">Before features can be imported into the project, you need to register the path with the Mixed Reality Feature Tool.</span></span>

![Como definir o caminho do projeto](images/ProjectPath.png)

## <a name="validating-selections"></a><span data-ttu-id="00e23-124">Como validar as seleções</span><span class="sxs-lookup"><span data-stu-id="00e23-124">Validating selections</span></span>

<span data-ttu-id="00e23-125">Recomendamos expressamente validar as seleções de recursos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="00e23-125">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="00e23-126">Esta etapa vai gerar todos os problemas que provavelmente impedem o desenvolvimento bem-sucedido do projeto.</span><span class="sxs-lookup"><span data-stu-id="00e23-126">This step will raise any issues that are likely to impede successful project development.</span></span>

![Problemas de validação](images/ValidationIssues.png)

<span data-ttu-id="00e23-128">A Ferramenta de Recursos de Realidade Misturada fornece duas resoluções de problemas automáticas (descritas nas seções a seguir) e a opção de cancelar e resolver problemas manualmente.</span><span class="sxs-lookup"><span data-stu-id="00e23-128">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00e23-129">A Ferramenta de Recursos de Realidade Misturada não pode resolver automaticamente os problemas relacionados às versões obrigatórias do Unity.</span><span class="sxs-lookup"><span data-stu-id="00e23-129">The Mixed Reality Feature Tool cannot automatically resolve issues related to required versions of Unity.</span></span> <span data-ttu-id="00e23-130">Esses problemas precisam ser tratados manualmente pela atualização da versão do Unity usada pelo projeto ou pela desabilitação dos recursos que exigem uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="00e23-130">These issues must be handled manually by upgrading the version of Unity used by the project or disabling the feature(s) requiring a newer version.</span></span>
>
> <span data-ttu-id="00e23-131">Uma versão futura da Ferramenta de Recursos de Realidade Misturada fornecerá uma melhor filtragem de recursos com base na versão do Unity que está sendo usada pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="00e23-131">A future release of the Mixed Reality Feature Tool will provide better filtering of features based upon the version of Unity being used by the project.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="00e23-132">Habilitar dependências</span><span class="sxs-lookup"><span data-stu-id="00e23-132">Enable dependencies</span></span>

<span data-ttu-id="00e23-133">O botão **Habilitar dependências** selecionará automaticamente as dependências ausentes.</span><span class="sxs-lookup"><span data-stu-id="00e23-133">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="00e23-134">Isso é verdadeiro para as dependências que foram selecionadas explicitamente (exibidas na lista **Recursos**) e para aquelas selecionadas implicitamente com base nos requisitos dos recursos escolhidos.</span><span class="sxs-lookup"><span data-stu-id="00e23-134">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="00e23-135">Desabilitar recursos</span><span class="sxs-lookup"><span data-stu-id="00e23-135">Disable features</span></span>

<span data-ttu-id="00e23-136">A seleção de **Desabilitar recursos** desmarcará automaticamente qualquer recurso que dependa de uma ou mais das dependências que foram desmarcadas.</span><span class="sxs-lookup"><span data-stu-id="00e23-136">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="00e23-137">Isso é verdadeiro para pacotes de dependência selecionados implicitamente e recursos selecionados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="00e23-137">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="00e23-138">Importação</span><span class="sxs-lookup"><span data-stu-id="00e23-138">Importing</span></span>

<span data-ttu-id="00e23-139">Selecione **Importar** para adicionar os recursos selecionados e conceder [aprovação final](reviewing-changes.md) antes de atualizar o projeto de destino.</span><span class="sxs-lookup"><span data-stu-id="00e23-139">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00e23-140">Se um problema de validação permanecer durante a importação, uma mensagem de aviso será exibida.</span><span class="sxs-lookup"><span data-stu-id="00e23-140">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="00e23-141">Recomendamos selecionar Não, clicar em **Validar** e resolver os problemas apresentados.</span><span class="sxs-lookup"><span data-stu-id="00e23-141">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Continuar com problemas de validação](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="00e23-143">Como voltar à etapa anterior</span><span class="sxs-lookup"><span data-stu-id="00e23-143">Going back to the previous step</span></span>

<span data-ttu-id="00e23-144">Em **Importar recursos**, a Ferramenta de Recursos de Realidade Misturada permite navegar de volta à [descoberta](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="00e23-144">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="00e23-145">Selecione **Voltar** para baixar outros pacotes de recursos.</span><span class="sxs-lookup"><span data-stu-id="00e23-145">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="00e23-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="00e23-146">See also</span></span>

- [<span data-ttu-id="00e23-147">Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="00e23-147">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="00e23-148">Descoberta e aquisição</span><span class="sxs-lookup"><span data-stu-id="00e23-148">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="00e23-149">Como exibir detalhes do pacote de recursos</span><span class="sxs-lookup"><span data-stu-id="00e23-149">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="00e23-150">Como examinar e aprovar as modificações do projeto</span><span class="sxs-lookup"><span data-stu-id="00e23-150">Reviewing and approving project modifications</span></span>](reviewing-changes.md)