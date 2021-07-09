---
title: Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada
description: Conheça os conceitos básicos da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772409"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="f5c7d-104">Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="f5c7d-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Imagem da faixa da Ferramenta de Recursos de Realidade Misturada](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="f5c7d-106">No momento, a Ferramenta de Recursos de Realidade Misturada só está disponível para o Unity.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="f5c7d-107">Se você estiver realizando o desenvolvimento no Unreal, veja a documentação de [instalação das ferramentas](../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="f5c7d-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="f5c7d-108">A Ferramenta de Recursos de Realidade Misturada é uma nova maneira para os desenvolvedores descobrirem, atualizarem e adicionarem pacotes de recursos de Realidade Misturada em projetos do Unity.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="f5c7d-109">Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="f5c7d-110">Se você nunca trabalhou com um arquivo de manifesto antes, é um arquivo JSON que contém todos os seus pacotes de projetos.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="f5c7d-111">Depois de validar os pacotes desejados, a ferramenta Recurso de Realidade Misturada os baixará no projeto de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="f5c7d-112">Requisitos de sistema</span><span class="sxs-lookup"><span data-stu-id="f5c7d-112">System requirements</span></span>

<span data-ttu-id="f5c7d-113">Para executar a Ferramenta de Recursos de Realidade Misturada, você precisará do seguinte:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="f5c7d-114">Runtime do .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f5c7d-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="f5c7d-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="f5c7d-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="f5c7d-116">Atualmente, a Ferramenta de Recursos de Realidade Misturada só é executada no Windows, mas o suporte ao macOS estará disponível em breve.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="f5c7d-117">Baixar</span><span class="sxs-lookup"><span data-stu-id="f5c7d-117">Download</span></span>

<span data-ttu-id="f5c7d-118">Depois de configurar seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="f5c7d-119">[Baixe a última versão da Ferramenta de Recursos da Realidade Misturada](https://aka.ms/MRFeatureTool) no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="f5c7d-120">Quando o download for concluído, descompacte o arquivo e salve-o na área de trabalho</span><span class="sxs-lookup"><span data-stu-id="f5c7d-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="f5c7d-121">Recomendamos criar um atalho para o arquivo executável para obter acesso mais rápido</span><span class="sxs-lookup"><span data-stu-id="f5c7d-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="f5c7d-122">Se não estiver usando o Gerenciador de Pacotes do Unity, siga nossas [instruções do UPM](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span><span class="sxs-lookup"><span data-stu-id="f5c7d-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="f5c7d-123">Alterações nessa versão</span><span class="sxs-lookup"><span data-stu-id="f5c7d-123">Changes in this release</span></span>

<span data-ttu-id="f5c7d-124">A versão 1.0.2103 Beta inclui as seguintes correções:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="f5c7d-125">Melhorias no download de detecção de erros.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="f5c7d-126">Atualizações sobre como os manifestos são gravados para evitar falhas na atualização correta.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="f5c7d-127">O Escpaing foi removido dos caminhos de arquivo no manifesto do projeto.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="f5c7d-128">Os seguintes recursos foram adicionados nesta atualização:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="f5c7d-129">O catálogo de recursos agora é armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-129">The feature catalog is now cached.</span></span> <span data-ttu-id="f5c7d-130">Para verificar se há novos recursos e atualizações, use o botão Atualizar na Descoberta.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="f5c7d-131">A seleção de projeto foi transferida da etapa Importar para antes da Descoberta.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="f5c7d-132">Os pacotes disponíveis são filtrados pela versão especificada do Unity do projeto.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="f5c7d-133">A exibição de descoberta agora mostra os pacotes instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="f5c7d-134">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="f5c7d-134">1. Getting started</span></span>

<span data-ttu-id="f5c7d-135">Inicie a Ferramenta de Recursos de Realidade Misturada por meio do arquivo executável, que exibe a página inicial na primeira inicialização:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Introdução](images/FeatureToolStart.png)

<span data-ttu-id="f5c7d-137">Na página inicial, você poderá:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-137">From the start page, you can:</span></span>

* <span data-ttu-id="f5c7d-138">[Definir](configuring-feature-tool.md) as configurações da ferramenta usando o botão de **ícone de engrenagem**</span><span class="sxs-lookup"><span data-stu-id="f5c7d-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="f5c7d-139">Usar o botão de **ponto de interrogação** para iniciar o navegador da Web padrão e ver nossa documentação</span><span class="sxs-lookup"><span data-stu-id="f5c7d-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="f5c7d-140">Selecione **Iniciar** para começar a descobrir os pacotes de recursos</span><span class="sxs-lookup"><span data-stu-id="f5c7d-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="f5c7d-141">2. Como selecionar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="f5c7d-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="f5c7d-142">Para garantir que todos os recursos descobertos são compatíveis com a versão do Unity do seu projeto, o primeiro passo é apontar a Ferramenta de Recursos de Realidade Misturada para seu projeto usando o botão de **elipse** (à direita do campo de caminho do projeto).</span><span class="sxs-lookup"><span data-stu-id="f5c7d-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the right of the project path field).</span></span>

![Selecionar o projeto do Unity](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="f5c7d-144">A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="f5c7d-145">É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="f5c7d-146">Depois de localizar a pasta do projeto, clique em Abrir para retornar à Ferramenta de Recursos de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5c7d-147">A Ferramenta de Recursos de Realidade Misturada executa a validação para garantir que ela tenha sido direcionada para a pasta do projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="f5c7d-148">A pasta deve conter as pastas `Assets`, `Packages` e `Project Settings`.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="f5c7d-149">3. Como descobrir e adquirir pacotes de recursos</span><span class="sxs-lookup"><span data-stu-id="f5c7d-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="f5c7d-150">A versão 1.0.2103 Beta agora armazena em cache o conteúdo do catálogo de recursos sempre que o servidor é acessado.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="f5c7d-151">Essa alteração permite o acesso rápido aos recursos disponíveis, em detrimento da exibição dos dados absolutos mais recentes.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="f5c7d-152">Para atualizar o catálogo, use o botão **Atualizar**.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="f5c7d-153">Os recursos são agrupados por categoria para facilitar a localização dos itens.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="f5c7d-154">Por exemplo, a categoria **Kit de Ferramentas de Realidade Misturada** traz vários recursos para sua escolha:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Descoberta e aquisição](images/FeatureToolDiscovery.png)

<span data-ttu-id="f5c7d-156">Quando a Ferramenta de Recursos de Realidade Misturada reconhece os recursos importados anteriormente, ela exibe uma mensagem de notificação para cada um.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![Notificação do recurso importado](images/feature-tool-imported-note.png)


<span data-ttu-id="f5c7d-158">Depois de fazer suas escolhas, selecione **Obter recursos** para buscar todos os pacotes necessários do catálogo.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="f5c7d-159">Para obter mais informações, confira [Como descobrir e adquirir recursos](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="f5c7d-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="f5c7d-160">4. Como importar pacotes de recursos</span><span class="sxs-lookup"><span data-stu-id="f5c7d-160">4. Importing feature packages</span></span>

<span data-ttu-id="f5c7d-161">Após a aquisição, o conjunto completo de pacotes é apresentado, juntamente com uma lista de dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="f5c7d-162">Caso você precise alterar qualquer seleção de recurso ou pacote, esta é a hora:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-162">If you need to change any feature or package selections, this is the time:</span></span>

![Importando pacotes](images/FeatureToolImport.png)

<span data-ttu-id="f5c7d-164">Recomendamos expressamente usar o botão **Validar** para garantir que o projeto do Unity possa importar os recursos selecionados com êxito.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="f5c7d-165">Após a validação, você verá uma caixa de diálogo pop-up com uma mensagem de êxito ou uma lista dos problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="f5c7d-166">Escolha **Importar** para continuar.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="f5c7d-167">Depois que você clicar no botão **Importar**, se algum problema persistir, uma mensagem simples será exibida.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="f5c7d-168">A recomendação é clicar em Não e usar o botão **Validar** para ver e resolver os problemas.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="f5c7d-169">Para obter mais informações, confira [Como importar recursos](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="f5c7d-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="f5c7d-170">5. Como examinar e aprovar as alterações do projeto</span><span class="sxs-lookup"><span data-stu-id="f5c7d-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="f5c7d-171">A etapa final é examinar e aprovar as alterações propostas para os arquivos de manifesto e de projeto:</span><span class="sxs-lookup"><span data-stu-id="f5c7d-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="f5c7d-172">As alterações propostas no manifesto são exibidas à esquerda</span><span class="sxs-lookup"><span data-stu-id="f5c7d-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="f5c7d-173">Os arquivos a serem adicionados ao projeto são listados à direita</span><span class="sxs-lookup"><span data-stu-id="f5c7d-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="f5c7d-174">O botão **Comparar** permite a exibição lado a lado do manifesto atual e das alterações propostas</span><span class="sxs-lookup"><span data-stu-id="f5c7d-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Autorização](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="f5c7d-176">Para obter mais informações, confira [Como examinar e aprovar as modificações do projeto](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="f5c7d-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="f5c7d-177">6. Projeto atualizado</span><span class="sxs-lookup"><span data-stu-id="f5c7d-177">6. Project updated</span></span>

<span data-ttu-id="f5c7d-178">Quando as alterações propostas forem aprovadas, o projeto de destino do Unity será atualizado para referenciar os recursos de Realidade Misturada selecionados.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![Projeto atualizado](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="f5c7d-180">A pasta **Pacotes** do projeto do Unity agora tem uma subpasta **MixedReality** com os arquivos do pacote de recursos e o manifesto conterá as referências apropriadas.</span><span class="sxs-lookup"><span data-stu-id="f5c7d-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="f5c7d-181">Volte ao Unity, aguarde até que os novos recursos selecionados sejam carregados e comece a criar!</span><span class="sxs-lookup"><span data-stu-id="f5c7d-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="f5c7d-182">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5c7d-182">See also</span></span>

- [<span data-ttu-id="f5c7d-183">Como configurar a ferramenta de recursos</span><span class="sxs-lookup"><span data-stu-id="f5c7d-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="f5c7d-184">Descoberta e aquisição</span><span class="sxs-lookup"><span data-stu-id="f5c7d-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="f5c7d-185">Como exibir detalhes do pacote de recursos</span><span class="sxs-lookup"><span data-stu-id="f5c7d-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="f5c7d-186">Como importar os pacotes selecionados</span><span class="sxs-lookup"><span data-stu-id="f5c7d-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="f5c7d-187">Como examinar e aprovar as modificações do projeto</span><span class="sxs-lookup"><span data-stu-id="f5c7d-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)