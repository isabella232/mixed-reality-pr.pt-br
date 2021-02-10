---
title: Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada
description: Conheça os conceitos básicos da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 0aad81ddd625467dd9159232d590b1a4bf68d06b
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570249"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="b00de-104">Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="b00de-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Imagem da faixa da Ferramenta de Recursos de Realidade Misturada](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="b00de-106">No momento, a Ferramenta de Recursos de Realidade Misturada só está disponível para o Unity.</span><span class="sxs-lookup"><span data-stu-id="b00de-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="b00de-107">Se você estiver realizando o desenvolvimento no Unreal, veja a documentação de [instalação das ferramentas](../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="b00de-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="b00de-108">A Ferramenta de Recursos de Realidade Misturada é uma nova maneira para os desenvolvedores descobrirem, atualizarem e adicionarem pacotes de recursos de Realidade Misturada em projetos do Unity.</span><span class="sxs-lookup"><span data-stu-id="b00de-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="b00de-109">Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="b00de-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="b00de-110">Se você nunca trabalhou com um arquivo de manifesto antes, é um arquivo JSON que contém todos os seus pacotes de projetos.</span><span class="sxs-lookup"><span data-stu-id="b00de-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="b00de-111">Depois de validar os pacotes desejados, a ferramenta Recurso de Realidade Misturada os baixará no projeto de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="b00de-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="b00de-112">Requisitos de sistema</span><span class="sxs-lookup"><span data-stu-id="b00de-112">System requirements</span></span>

<span data-ttu-id="b00de-113">Para executar a Ferramenta de Recursos de Realidade Misturada, você precisará do seguinte:</span><span class="sxs-lookup"><span data-stu-id="b00de-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="b00de-114">Runtime do .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b00de-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="b00de-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="b00de-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="b00de-116">Atualmente, a Ferramenta de Recursos de Realidade Misturada só é executada no Windows, mas o suporte ao macOS estará disponível em breve.</span><span class="sxs-lookup"><span data-stu-id="b00de-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="b00de-117">Baixar</span><span class="sxs-lookup"><span data-stu-id="b00de-117">Download</span></span> 

<span data-ttu-id="b00de-118">Depois de configurar seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="b00de-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="b00de-119">[Baixe a última versão da Ferramenta de Recursos da Realidade Misturada](https://aka.ms/MRFeatureTool) no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b00de-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="b00de-120">Quando o download for concluído, descompacte o arquivo e salve-o na área de trabalho</span><span class="sxs-lookup"><span data-stu-id="b00de-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="b00de-121">Recomendamos criar um atalho para o arquivo executável para obter acesso mais rápido</span><span class="sxs-lookup"><span data-stu-id="b00de-121">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="b00de-122">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="b00de-122">1. Getting started</span></span>

<span data-ttu-id="b00de-123">Inicie a Ferramenta de Recursos de Realidade Misturada por meio do arquivo executável, que exibe a página inicial na primeira inicialização:</span><span class="sxs-lookup"><span data-stu-id="b00de-123">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Introdução](images/FeatureToolStart.png)

<span data-ttu-id="b00de-125">Na página inicial, você poderá:</span><span class="sxs-lookup"><span data-stu-id="b00de-125">From the start page, you can:</span></span>

* <span data-ttu-id="b00de-126">[Definir](configuring-feature-tool.md) as configurações da ferramenta usando o botão de **ícone de engrenagem**</span><span class="sxs-lookup"><span data-stu-id="b00de-126">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="b00de-127">Usar o botão de **ponto de interrogação** para iniciar o navegador da Web padrão e ver nossa documentação</span><span class="sxs-lookup"><span data-stu-id="b00de-127">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="b00de-128">Selecione **Iniciar** para começar a descobrir os pacotes de recursos</span><span class="sxs-lookup"><span data-stu-id="b00de-128">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="b00de-129">2. Como descobrir e adquirir pacotes de recursos</span><span class="sxs-lookup"><span data-stu-id="b00de-129">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="b00de-130">O catálogo do pacote de recursos é recuperado assim que você clica em Iniciar.</span><span class="sxs-lookup"><span data-stu-id="b00de-130">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="b00de-131">Os recursos são agrupados por categoria para facilitar a localização dos itens.</span><span class="sxs-lookup"><span data-stu-id="b00de-131">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="b00de-132">Por exemplo, a categoria **Kit de Ferramentas de Realidade Misturada** traz vários recursos para sua escolha:</span><span class="sxs-lookup"><span data-stu-id="b00de-132">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Descoberta e aquisição](images/FeatureToolDiscovery.png)

<span data-ttu-id="b00de-134">Depois de fazer suas escolhas, selecione **Obter recursos** para buscar todos os pacotes necessários do catálogo.</span><span class="sxs-lookup"><span data-stu-id="b00de-134">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="b00de-135">Para obter mais informações, confira [Como descobrir e adquirir recursos](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="b00de-135">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="b00de-136">3. Como importar pacotes de recursos</span><span class="sxs-lookup"><span data-stu-id="b00de-136">3. Importing feature packages</span></span>

<span data-ttu-id="b00de-137">Após a aquisição, o conjunto completo de pacotes é apresentado, juntamente com uma lista de dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="b00de-137">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="b00de-138">Caso você precise alterar qualquer seleção de recurso ou pacote, esta é a hora:</span><span class="sxs-lookup"><span data-stu-id="b00de-138">If you need to change any feature or package selections, this is the time:</span></span>

![Importando pacotes](images/FeatureToolImport.png)

<span data-ttu-id="b00de-140">Recomendamos expressamente usar o botão **Validar** para garantir que o projeto do Unity possa importar os recursos selecionados com êxito.</span><span class="sxs-lookup"><span data-stu-id="b00de-140">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="b00de-141">Após a validação, você verá uma caixa de diálogo pop-up com uma mensagem de êxito ou uma lista dos problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="b00de-141">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="b00de-142">Você também precisará definir a localização do projeto de destino do Unity antes da importação.</span><span class="sxs-lookup"><span data-stu-id="b00de-142">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="b00de-143">Use o botão de **reticências** à esquerda do campo do caminho do projeto para a busca.</span><span class="sxs-lookup"><span data-stu-id="b00de-143">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="b00de-144">Quando terminar de navegar no sistema de arquivos, abra a pasta que contém o projeto de destino do Unity.</span><span class="sxs-lookup"><span data-stu-id="b00de-144">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="b00de-145">A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="b00de-145">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="b00de-146">É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.</span><span class="sxs-lookup"><span data-stu-id="b00de-146">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="b00de-147">Escolha **Importar** para continuar.</span><span class="sxs-lookup"><span data-stu-id="b00de-147">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="b00de-148">Depois que você clicar no botão **Importar**, se algum problema persistir, uma mensagem simples será exibida.</span><span class="sxs-lookup"><span data-stu-id="b00de-148">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="b00de-149">A recomendação é clicar em Não e usar o botão **Validar** para ver e resolver os problemas.</span><span class="sxs-lookup"><span data-stu-id="b00de-149">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="b00de-150">Para obter mais informações, confira [Como importar recursos](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="b00de-150">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="b00de-151">4. Como examinar e aprovar as alterações do projeto</span><span class="sxs-lookup"><span data-stu-id="b00de-151">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="b00de-152">A etapa final é examinar e aprovar as alterações propostas para os arquivos de manifesto e de projeto:</span><span class="sxs-lookup"><span data-stu-id="b00de-152">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="b00de-153">As alterações propostas no manifesto são exibidas à esquerda</span><span class="sxs-lookup"><span data-stu-id="b00de-153">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="b00de-154">Os arquivos a serem adicionados ao projeto são listados à direita</span><span class="sxs-lookup"><span data-stu-id="b00de-154">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="b00de-155">O botão **Comparar** permite a exibição lado a lado do manifesto atual e das alterações propostas</span><span class="sxs-lookup"><span data-stu-id="b00de-155">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Autorização](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="b00de-157">Para obter mais informações, confira [Como examinar e aprovar as modificações do projeto](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="b00de-157">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="b00de-158">5. Projeto atualizado</span><span class="sxs-lookup"><span data-stu-id="b00de-158">5. Project updated</span></span>

<span data-ttu-id="b00de-159">Quando as alterações propostas forem aprovadas, o projeto de destino do Unity será atualizado para referenciar os recursos de Realidade Misturada selecionados:</span><span class="sxs-lookup"><span data-stu-id="b00de-159">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![Projeto atualizado](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="b00de-161">A pasta **Pacotes** do projeto do Unity agora tem uma subpasta **MixedReality** com os arquivos do pacote de recursos e o manifesto conterá as referências apropriadas.</span><span class="sxs-lookup"><span data-stu-id="b00de-161">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="b00de-162">Volte ao Unity, aguarde até que os novos recursos selecionados sejam carregados e comece a criar!</span><span class="sxs-lookup"><span data-stu-id="b00de-162">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="b00de-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="b00de-163">See also</span></span>

- [<span data-ttu-id="b00de-164">Como configurar a ferramenta de recursos</span><span class="sxs-lookup"><span data-stu-id="b00de-164">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="b00de-165">Descoberta e aquisição</span><span class="sxs-lookup"><span data-stu-id="b00de-165">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="b00de-166">Como exibir detalhes do pacote de recursos</span><span class="sxs-lookup"><span data-stu-id="b00de-166">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="b00de-167">Como importar os pacotes selecionados</span><span class="sxs-lookup"><span data-stu-id="b00de-167">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="b00de-168">Como examinar e aprovar as modificações do projeto</span><span class="sxs-lookup"><span data-stu-id="b00de-168">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
