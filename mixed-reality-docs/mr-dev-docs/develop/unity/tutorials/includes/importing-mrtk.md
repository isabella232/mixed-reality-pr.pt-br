---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175765"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="d218a-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="d218a-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="d218a-102">Quando o **MixedRealityFeatureTool** for aberto, clique em **Iniciar** para começar a usar a Ferramenta de Recursos da Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="d218a-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="d218a-103">A primeira etapa é apontar a Ferramenta Recurso de Realidade Misturada para o **caminho de Projeto** usando o botão de **reticências**, clicar no botão de reticências de três pontos ao lado do caminho de Projeto e navegar até a pasta do projeto no explorador, por exemplo _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="d218a-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="d218a-104">Quando você tiver localizado a pasta do projeto, clique no botão Abrir para retornar à Ferramenta Recurso de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="d218a-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="d218a-105">Em seguida, clique em **Descobrir Recursos**.</span><span class="sxs-lookup"><span data-stu-id="d218a-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="d218a-106">A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d218a-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="d218a-107">É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.</span><span class="sxs-lookup"><span data-stu-id="d218a-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="d218a-108">A Ferramenta de Recursos da Realidade Misturada executa a validação para garantir que ela tenha sido direcionada para uma pasta de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="d218a-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="d218a-109">A pasta deve conter pastas de Ativos, Pacotes e Configurações do Projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="d218a-110">Os recursos são agrupados por categoria para que seja mais fácil encontrar o que você quer. Clique na lista suspensa **Kit de Ferramentas de Realidade Misturada** para encontrar pacotes relacionados ao Kit de Ferramentas de Realidade Misturada e clique na lista suspensa **Suporte de Plataforma** para encontrar pacotes relacionados a diversas plataformas de suporte.</span><span class="sxs-lookup"><span data-stu-id="d218a-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="d218a-111">Verifique a **Mixed Reality Toolkit Foundation** e clique na lista suspensa ao lado para selecionar **MRTK 2.7.2**. Selecione também o **Plug-In OpenXR de Realidade Misturada 1.0.0** e clique na lista suspensa ao lado para selecionar a versão mais recente disponível e, em seguida, clique no botão **Obter recursos** para baixar os pacotes selecionados.</span><span class="sxs-lookup"><span data-stu-id="d218a-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="d218a-112">Em seguida, clique no botão **Validar** para validar o pacote selecionado. Você receberá um pop-up com a mensagem **Não foi detectado nenhum problema de validação**, clique em **OK** para fechar o pop-up e clique no botão **Importar**.</span><span class="sxs-lookup"><span data-stu-id="d218a-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="d218a-113">Clique no botão **Aprovar** para adicionar o **Kit de Ferramentas de Realidade Misturada** ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="d218a-114">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="d218a-114">Configuring the Unity project</span></span>

<span data-ttu-id="d218a-115">Depois que o Unity terminar de importar o pacote da seção anterior, uma mensagem de aviso será exibida para reiniciar o editor do Unity para habilitar os back-ends para o novo sistema de plug-ins, clique em **Sim**</span><span class="sxs-lookup"><span data-stu-id="d218a-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="d218a-116">Após a reinicialização do Unity, o Configurador de Projeto do MRTK deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="d218a-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d218a-117">Caso contrário, você pode abri-lo manualmente acessando **Kit de Ferramentas** > **de Realidade Misturada** > **Utilitários**  > **Configurar Projeto para MRTK**:</span><span class="sxs-lookup"><span data-stu-id="d218a-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Abrir a janela do configurador de projeto do MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="d218a-119">Clique em **Plug-in OpenXR do Unity** para Habilitar o Gerenciamento de Plug-In XR e adicione seus pacotes necessários ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="d218a-120">Adicionar Plug-in OpenXR do Unity</span><span class="sxs-lookup"><span data-stu-id="d218a-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="d218a-121">Isso resultará na importação dos pacotes do Unity necessários para o Gerenciamento de Plug-in XR. Após concluir, clique em **Mostrar Configurações de Gerenciamento de Plug-In XR** no Configurador do projeto do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d218a-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="d218a-122">Mostrar as Configurações de Gerenciamento do Plug-In XR</span><span class="sxs-lookup"><span data-stu-id="d218a-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="d218a-123">Isso abrirá a **janela de Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="d218a-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="d218a-124">Na janela Configurações do Projeto em **Gerenciamento de Plug-in XR**, verifique se você está nas configurações da Plataforma Universal do Windows (guia do logotipo do Windows).</span><span class="sxs-lookup"><span data-stu-id="d218a-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="d218a-125">Verifique também se **Inicializar XR na Inicialização** está marcado e, em seguida, clique nas caixas de seleção **OpenXR** e **Conjunto de recursos do Microsoft HoloLens** para habilita-los.</span><span class="sxs-lookup"><span data-stu-id="d218a-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![Habilitar Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="d218a-127">Após selecionar a caixa de seleção OpenXR, a janela Configurador de Projeto do MRTK exibirá a mensagem atualizada com o botão **Aplicar Configurações**.</span><span class="sxs-lookup"><span data-stu-id="d218a-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="d218a-128">Clique no botão **Aplicar Configurações**.</span><span class="sxs-lookup"><span data-stu-id="d218a-128">Click **Apply Settings** button.</span></span> 

![Janela 1 das Configurações do Projeto](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="d218a-130">Ao clicar em Aplicar Configurações, você poderá ver essa mensagem de erro no Console.</span><span class="sxs-lookup"><span data-stu-id="d218a-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="d218a-131">Você pode prosseguir se esse for o único erro ou se não houver nenhum erro.</span><span class="sxs-lookup"><span data-stu-id="d218a-131">You can proceed if this is the only error or there is no error.</span></span>

![Mensagem de Erro de Comunicação Remota do OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="d218a-133">Para validar a configuração do OpenXR, clique em **OpenXR** em **Gerenciamento de Plug-in XR**, e marque estes itens:</span><span class="sxs-lookup"><span data-stu-id="d218a-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="d218a-134">Modo de Envio de Intensidade: **Intensidade de 16 Bits**</span><span class="sxs-lookup"><span data-stu-id="d218a-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="d218a-135">Perfis de Interação: **Perfil de Interação à Mão da Microsoft**</span><span class="sxs-lookup"><span data-stu-id="d218a-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![Janela 2 das Configurações do Projeto](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="d218a-137">A redução do formato de profundidade para 16 bits é opcional, mas pode ajudar a aprimorar o desempenho gráfico no projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="d218a-138">Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação Desempenho do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d218a-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="d218a-139">Na janela **Configurador do Projeto do MRTK** clique em **Próximo** e, em seguida, clique no botão **Aplicar** para aplicar as configurações.</span><span class="sxs-lookup"><span data-stu-id="d218a-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="d218a-140">(Se você tiver fechado, você pode abri-lo manualmente acessando **Kit de Ferramentas** > **de Realidade Misturada** > **Utilitários**  > **Configurar Projeto para MRTK**)</span><span class="sxs-lookup"><span data-stu-id="d218a-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![Janela 3 das Configurações do Projeto](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Janela 4 das Configurações do Projeto](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="d218a-143">Após clicar em Aplicar, o Unity tentará reiniciar para que o sistema de entrada entre em vigor. Clique em **Aplicar** para reiniciar o editor do Unity</span><span class="sxs-lookup"><span data-stu-id="d218a-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="d218a-144">Definir configurações adicionais do projeto</span><span class="sxs-lookup"><span data-stu-id="d218a-144">Configure additional project settings</span></span>

<span data-ttu-id="d218a-145">No menu do Unity, selecione **Editar** > **Configurações do projeto...** para abrir a janela Configurações do Projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="d218a-146">Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="d218a-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configurações de Publicação do Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="d218a-149">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d218a-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="d218a-150">Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d218a-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="d218a-151">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d218a-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="d218a-152">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="d218a-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="d218a-153">Unity 2019/2020 + Plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="d218a-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="d218a-154">Quando o **MixedRealityFeatureTool** for aberto, clique em **Iniciar** para começar a usar a Ferramenta de Recursos da Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="d218a-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="d218a-155">A primeira etapa é apontar a Ferramenta Recurso de Realidade Misturada para o **caminho de Projeto** usando o botão de **reticências**, clicar no botão de reticências de três pontos ao lado do caminho de Projeto e navegar até a pasta do projeto no explorador, por exemplo _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="d218a-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="d218a-156">Quando você tiver localizado a pasta do projeto, clique no botão Abrir para retornar à Ferramenta Recurso de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="d218a-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="d218a-157">Em seguida, clique em **Descobrir Recursos**.</span><span class="sxs-lookup"><span data-stu-id="d218a-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="d218a-158">A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d218a-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="d218a-159">É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.</span><span class="sxs-lookup"><span data-stu-id="d218a-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="d218a-160">A Ferramenta de Recursos da Realidade Misturada executa a validação para garantir que ela tenha sido direcionada para uma pasta de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="d218a-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="d218a-161">A pasta deve conter pastas de Ativos, Pacotes e Configurações do Projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="d218a-162">Os recursos são agrupados por categoria para que seja mais fácil encontrar o que você quer. Clique na lista suspensa **Kit de Ferramentas de Realidade Misturada** para encontrar pacotes relacionados ao Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="d218a-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="d218a-163">Selecione a caixa **Mixed Reality Toolkit Foundation**, clique na lista suspensa ao lado para selecionar **MRTK 2.7.0**, e clique no botão **Obter recursos** para baixar os pacotes selecionados.</span><span class="sxs-lookup"><span data-stu-id="d218a-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="d218a-164">Em seguida, clique no botão **Validar** para validar o pacote selecionado. Você receberá um pop-up com a mensagem **Não foi detectado nenhum problema de validação**, clique em **OK** para fechar o pop-up e clique no botão **Importar**.</span><span class="sxs-lookup"><span data-stu-id="d218a-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="d218a-165">Clique no botão **Aprovar** para adicionar o **Kit de Ferramentas de Realidade Misturada** ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="d218a-166">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="d218a-166">Configuring the Unity project</span></span>

<span data-ttu-id="d218a-167">Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="d218a-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d218a-168">Caso contrário, você pode abri-lo manualmente acessando **Kit de Ferramentas** > **de Realidade Misturada** > **Utilitários**  > **Configurar Projeto para MRTK**:</span><span class="sxs-lookup"><span data-stu-id="d218a-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![abrindo a ferramenta de configurador do MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="d218a-170">Clique em **Plug-in Interno do Unity (não OpenXR)** para Habilitar o Gerenciamento de Plug-In XR e adicione seus pacotes necessários ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="d218a-171">Ferramenta de configurador do MRTK</span><span class="sxs-lookup"><span data-stu-id="d218a-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="d218a-172">A captura de tela acima é do Unity 2020. Se você estiver usando o Unity 2019, selecione **Gerenciamento de XR SDK/XR**</span><span class="sxs-lookup"><span data-stu-id="d218a-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="d218a-173">Isso resultará na importação dos pacotes do Unity necessários para o Gerenciamento de Plug-in XR. Após concluir, clique em **Mostrar Configurações** no Configurador do projeto do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d218a-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![Janela configurações do player](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="d218a-175">Isso abre a **janela Configurações do Projeto** na janela Configurações do Projeto em **Gerenciamento do Plug-in XR** Verifique se você está nas configurações da Plataforma Universal do Windows e Verifique se **Inicializar XR na Inicialização** está selecionado, e selecione a caixa de seleção **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="d218a-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![Janela configurações do player Habilitar Realidade Misturada-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="d218a-177">Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente.</span><span class="sxs-lookup"><span data-stu-id="d218a-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="d218a-178">Se ela não aparecer, use o menu do Unity para abri-la.</span><span class="sxs-lookup"><span data-stu-id="d218a-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="d218a-179">Na janela Configurador de Projeto do MRTK, clique em **próximo**, e, em seguida, use a lista suspensa Espacializador de áudio para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="d218a-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Configurador de projeto do MRTK-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="d218a-181">A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:</span><span class="sxs-lookup"><span data-stu-id="d218a-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="d218a-182">Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho.</span><span class="sxs-lookup"><span data-stu-id="d218a-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="d218a-183">Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) da documentação [Desempenho](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d218a-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="d218a-184">Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial.</span><span class="sxs-lookup"><span data-stu-id="d218a-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="d218a-185">Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="d218a-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="d218a-186">A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="d218a-187">Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="d218a-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="d218a-188">Para saber mais sobre este tópico, veja os <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="d218a-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="d218a-189">Clique em **Próximo** e clique em **Concluído** na janela Configurador de Projeto do MRTK para concluir a configuração de projeto do Unity para XRSDK.</span><span class="sxs-lookup"><span data-stu-id="d218a-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="d218a-190">Definir configurações adicionais do projeto</span><span class="sxs-lookup"><span data-stu-id="d218a-190">Configure additional project settings</span></span>

<span data-ttu-id="d218a-191">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="d218a-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="d218a-192">Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-in do XR** > **Windows Mixed Reality** > **Configurações de Tempo de Execução** e use a lista suspensa **Formato de Buffer de Profundidade** para selecionar a **intensidade de 16 bits**:</span><span class="sxs-lookup"><span data-stu-id="d218a-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Habilitação da profundidade de 16 bits do Unity](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="d218a-194">A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="d218a-195">Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação Desempenho do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d218a-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="d218a-196">Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="d218a-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configurações de Publicação do Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="d218a-199">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d218a-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="d218a-200">Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d218a-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="d218a-201">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d218a-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="d218a-202">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="d218a-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="d218a-203">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="d218a-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="d218a-204">Quando o **MixedRealityFeatureTool** for aberto, clique em **Iniciar** para começar a usar a Ferramenta de Recursos da Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="d218a-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="d218a-205">A primeira etapa é apontar a Ferramenta Recurso de Realidade Misturada para o **caminho de Projeto** usando o botão de **reticências**, clicar no botão de reticências de três pontos ao lado do caminho de Projeto e navegar até a pasta do projeto no explorador, por exemplo _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="d218a-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="d218a-206">Quando você tiver localizado a pasta do projeto, clique no botão Abrir para retornar à Ferramenta Recurso de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="d218a-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="d218a-207">Em seguida, clique em **Descobrir Recursos**.</span><span class="sxs-lookup"><span data-stu-id="d218a-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="d218a-208">A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d218a-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="d218a-209">É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.</span><span class="sxs-lookup"><span data-stu-id="d218a-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="d218a-210">A Ferramenta de Recursos da Realidade Misturada executa a validação para garantir que ela tenha sido direcionada para uma pasta de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="d218a-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="d218a-211">A pasta deve conter pastas de Ativos, Pacotes e Configurações do Projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="d218a-212">Os recursos são agrupados por categoria para que seja mais fácil encontrar o que você quer. Clique na lista suspensa **Kit de Ferramentas de Realidade Misturada** para encontrar pacotes relacionados ao Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="d218a-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="d218a-213">selecione **Mixed Reality Toolkit Foundation**, clique na lista suspensa ao lado para selecionar **MRTK 2.7.0**, e clique no botão **Obter recursos** para baixar os pacotes selecionados.</span><span class="sxs-lookup"><span data-stu-id="d218a-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="d218a-214">Em seguida, clique no botão **Validar** para validar o pacote selecionado. Você receberá um pop-up com a mensagem **Não foi detectado nenhum problema de validação**, clique em **OK** para fechar o pop-up e clique no botão **Importar**.</span><span class="sxs-lookup"><span data-stu-id="d218a-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="d218a-215">Clique no botão **Aprovar** para adicionar o **Kit de Ferramentas de Realidade Misturada** ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="d218a-216">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="d218a-216">Configuring the Unity project</span></span>

<span data-ttu-id="d218a-217">Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="d218a-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d218a-218">Caso contrário, você pode abri-lo manualmente acessando **Kit de Ferramentas** > **de Realidade Misturada** > **Utilitários**  > **Configurar Projeto para MRTK**:</span><span class="sxs-lookup"><span data-stu-id="d218a-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Caminho do menu Configurar Projeto do Unity no Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="d218a-220">Clique em **XR Herdado** para habilitar o XR Herdado e adicionar seus pacotes necessários ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="d218a-222">Clique no botão próximo para habilitar as configurações de pipeline XR para XR Herdado.</span><span class="sxs-lookup"><span data-stu-id="d218a-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Janela de Configuração do MRTK do Unity](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="d218a-224">Na janela Configurador de Projeto do MRTK, verifique se todas as opções estão marcadas e use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="d218a-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Janela de configuração do MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="d218a-226">A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:</span><span class="sxs-lookup"><span data-stu-id="d218a-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="d218a-227">Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho.</span><span class="sxs-lookup"><span data-stu-id="d218a-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="d218a-228">Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) da documentação [Desempenho](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d218a-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="d218a-229">Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial.</span><span class="sxs-lookup"><span data-stu-id="d218a-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="d218a-230">Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="d218a-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="d218a-231">A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="d218a-232">Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="d218a-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="d218a-233">Para saber mais sobre este tópico, veja os <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="d218a-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="d218a-234">Clique em **Próximo** e clique no botão **Concluído** na janela Configurador de Projeto do MRTK para concluir a configuração de projeto do Unity para XR Herdado.</span><span class="sxs-lookup"><span data-stu-id="d218a-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="d218a-235">Definir configurações adicionais do projeto</span><span class="sxs-lookup"><span data-stu-id="d218a-235">Configure additional project settings</span></span>

<span data-ttu-id="d218a-236">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="d218a-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="d218a-237">Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e, em seguida, use a lista suspensa **Formato de Profundidade** para selecionar a **Profundidade de 16 bits**:</span><span class="sxs-lookup"><span data-stu-id="d218a-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Habilitação da profundidade de 16 bits do Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="d218a-239">A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto.</span><span class="sxs-lookup"><span data-stu-id="d218a-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="d218a-240">Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação Desempenho do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d218a-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="d218a-241">Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="d218a-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configurações de Publicação do Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="d218a-244">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d218a-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="d218a-245">Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d218a-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="d218a-246">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d218a-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="d218a-247">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="d218a-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
