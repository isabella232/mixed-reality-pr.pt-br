---
title: Publicar na Microsoft Store
description: ''
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, documentação, guias, recursos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, publicação, distribuição, Microsoft Store
ms.openlocfilehash: 37a17ba4a691ca8db6ce447abd485293454b8ae3
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96583878"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="95827-103">Publicar na Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="95827-103">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="95827-104">Quando estiver pronto para divulgar seu aplicativo Unreal para o mundo, haverá algumas configurações de projeto que precisam ser atualizadas antes de você enviá-lo à Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="95827-104">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="95827-105">Todas essas configurações têm valores padrão, mas devem ser alteradas para produção a fim de melhor representar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95827-105">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="95827-106">Configurações de projeto para o empacotamento da loja</span><span class="sxs-lookup"><span data-stu-id="95827-106">Project settings for the store packaging</span></span>

1. <span data-ttu-id="95827-107">Primeiro, selecione **Configurações de Projeto > Descrição** e atualize as informações do jogo e do editor:</span><span class="sxs-lookup"><span data-stu-id="95827-107">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="95827-108">O **Nome do Jogo** será exibido no bloco do aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="95827-108">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="95827-109">O **Nome Diferenciado da Empresa** é usado ao gerar o certificado do projeto e deve estar no formato:</span><span class="sxs-lookup"><span data-stu-id="95827-109">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="95827-110">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span><span class="sxs-lookup"><span data-stu-id="95827-110">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Captura de tela do editor do Unreal com a seção Descrição expandida em Configurações de Projeto](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="95827-112">Expanda a seção **HoloLens** das configurações de projeto e atualize os recursos de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="95827-112">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="95827-113">Esses nomes de recursos serão mostrados na página da loja do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="95827-113">These resource names will be shown on the application’s store page:</span></span>

![Captura de tela do editor do Unreal com a seção Empacotamento expandida em Configurações de Projeto](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="95827-115">Expanda a seção **Imagens** e atualize as imagens da loja padrão com texturas que representam o aplicativo da loja.</span><span class="sxs-lookup"><span data-stu-id="95827-115">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="95827-116">Opcionalmente, marque a caixa de seleção **Logotipo 3D** para carregar um arquivo glb e usá-lo como um cubo 3D ao iniciar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="95827-116">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Captura de tela do editor do Unreal com a seção Imagens expandida em Configurações de Projeto](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="95827-118">Por fim, selecione **Gerar Novo** para gerar um certificado de autenticação com base no nome do projeto e no nome diferenciado da empresa</span><span class="sxs-lookup"><span data-stu-id="95827-118">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="95827-119">Defina uma **Cor da Tela de Fundo do Bloco**, que será exibida no lugar dos pixels transparentes nas imagens da loja.</span><span class="sxs-lookup"><span data-stu-id="95827-119">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="95827-120">Expanda a lista suspensa e habilite a opção **Usar o Ambiente da Microsoft Store de varejo** para execução em dispositivos bloqueados para varejo e não desbloqueados para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="95827-120">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Captura de tela do editor do Unreal com a seção Geração de certificado expandida em Configurações de Projeto](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="95827-122">Instalador de Aplicativo opcional</span><span class="sxs-lookup"><span data-stu-id="95827-122">Optional App Installer</span></span>

<span data-ttu-id="95827-123">Um arquivo do Instalador de Aplicativo pode ser criado em **Configurações de Projeto > HoloLens**, que pode ser usado para distribuir o aplicativo fora da loja.</span><span class="sxs-lookup"><span data-stu-id="95827-123">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="95827-124">Habilite a caixa de seleção **Deve Criar Instalador de Aplicativo** e defina uma URL ou um caminho de rede no qual deseja que o appxbundle do jogo seja armazenado.</span><span class="sxs-lookup"><span data-stu-id="95827-124">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Captura de tela do editor do Unreal com a seção Instalador de Aplicativo expandida em Configurações de Projeto](images/unreal-publishing-img-05.png)

<span data-ttu-id="95827-126">Quando o aplicativo estiver sendo empacotado, o appxbundle e o appinstaller serão gerados.</span><span class="sxs-lookup"><span data-stu-id="95827-126">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="95827-127">Carregue o appxbundle na URL de instalação e inicie o appinstaller para instalar o aplicativo por meio da localização de rede.</span><span class="sxs-lookup"><span data-stu-id="95827-127">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="95827-128">Kit de Certificação de Aplicativos Windows</span><span class="sxs-lookup"><span data-stu-id="95827-128">Windows App Certification Kit</span></span>

<span data-ttu-id="95827-129">O SDK do Windows 10 é fornecido com o WACK (Kit de Certificação de Aplicativos Windows) para validar problemas comuns que possam afetar o upload de um pacote na loja.</span><span class="sxs-lookup"><span data-stu-id="95827-129">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="95827-130">Encontre o WACK no diretório Kits do Windows, geralmente no seguinte caminho:</span><span class="sxs-lookup"><span data-stu-id="95827-130">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="95827-131">Depois que o arquivo appx for empacotado para publicação, execute **appcertui.exe** e siga os avisos para verificar o appx:</span><span class="sxs-lookup"><span data-stu-id="95827-131">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Captura de tela do aplicativo sendo selecionado para validação no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="95827-133">Selecione **Validar Aplicativo da Loja**:</span><span class="sxs-lookup"><span data-stu-id="95827-133">Select **Validate Store App**:</span></span>

![Captura de tela da seleção de validação no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="95827-135">Procure o appx na seção superior e selecione **Avançar**:</span><span class="sxs-lookup"><span data-stu-id="95827-135">Browse for the appx in the top section and select **Next**:</span></span>

![Captura de tela da seleção de teste no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="95827-137">Selecione **Avançar** para executar os testes e criar um relatório:</span><span class="sxs-lookup"><span data-stu-id="95827-137">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="95827-138">Todos os testes disponíveis que podem ser executados no PC host serão habilitados por padrão</span><span class="sxs-lookup"><span data-stu-id="95827-138">All available tests that can be run on the host PC will be enabled by default</span></span>

![Captura de tela do progresso de validação do aplicativo no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="95827-140">Aguarde a conclusão dos testes.</span><span class="sxs-lookup"><span data-stu-id="95827-140">Wait for the tests to finish.</span></span> <span data-ttu-id="95827-141">Depois que os testes forem concluídos, a janela final mostrará um resultado de aprovação ou reprovação, que pode ser exibido no relatório salvo.</span><span class="sxs-lookup"><span data-stu-id="95827-141">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Captura de tela dos resultados do relatório final no Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="95827-143">Falha conhecida do WACK na versão 4.25</span><span class="sxs-lookup"><span data-stu-id="95827-143">Known WACK failure with 4.25</span></span>

<span data-ttu-id="95827-144">O plug-in do Windows Mixed Reality no Unreal 4.25 causará uma falha no WACK devido à inclusão de alguns binários x64 durante o empacotamento para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="95827-144">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="95827-145">A falha terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="95827-145">The failure will look like this:</span></span>

![Captura de tela de um resultado com falha devido ao analisador binário e às APIs compatíveis do Kit de Certificação de Aplicativos Windows](images/unreal-publishing-img-11.png)

<span data-ttu-id="95827-147">Para corrigir o problema:</span><span class="sxs-lookup"><span data-stu-id="95827-147">To fix the issue:</span></span>
1. <span data-ttu-id="95827-148">Procure a raiz do diretório de origem ou da instalação do Unreal abrindo um projeto do Unreal e clique com o botão direito do mouse no ícone do Unreal na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="95827-148">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="95827-149">Clique com o botão direito do mouse em UE4Editor, selecione Propriedades e procure o caminho na entrada **Localização**:</span><span class="sxs-lookup"><span data-stu-id="95827-149">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="95827-150">Em **WindowsMixedRealityHMD.Build.cs**, modifique a linha **32** de:</span><span class="sxs-lookup"><span data-stu-id="95827-150">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="95827-151">para:</span><span class="sxs-lookup"><span data-stu-id="95827-151">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="95827-152">Feche o Unreal, reabra o projeto e recrie o pacote para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="95827-152">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="95827-153">Execute o WACK novamente e o erro deixará de ser exibido.</span><span class="sxs-lookup"><span data-stu-id="95827-153">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="95827-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="95827-154">See also</span></span>
* [<span data-ttu-id="95827-155">Como enviar um aplicativo para a Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="95827-155">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="95827-156">Kit de Certificação de Aplicativos Windows</span><span class="sxs-lookup"><span data-stu-id="95827-156">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="95827-157">Criar manualmente um arquivo do Instalador de Aplicativo</span><span class="sxs-lookup"><span data-stu-id="95827-157">Create an App Installer file manually</span></span>](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)