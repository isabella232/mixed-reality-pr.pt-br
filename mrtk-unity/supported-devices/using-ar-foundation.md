---
title: UsingARFoundation
description: Documentação para usar ARFoundation no Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, AR Core, AR Kit
ms.openlocfilehash: d96c5cab2439b581c0de9d59a1a349abccf34fb5
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852303"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="133d4-104">Como configurar o MRTK para iOS e Android [Experimental]</span><span class="sxs-lookup"><span data-stu-id="133d4-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="133d4-105">Instalar os pacotes necessários</span><span class="sxs-lookup"><span data-stu-id="133d4-105">Install required packages</span></span>

1. <span data-ttu-id="133d4-106">Baixe e importe o **pacote Microsoft.MixedReality.Toolkit.Unity.Foundation,** do [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) ou do [Gerenciador de Pacotes](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="133d4-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="133d4-107">No UPM (Gerenciador de Pacotes Unity), instale os seguintes pacotes:</span><span class="sxs-lookup"><span data-stu-id="133d4-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="133d4-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="133d4-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="133d4-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="133d4-109">**Android**</span></span> | <span data-ttu-id="133d4-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="133d4-110">**iOS**</span></span> | <span data-ttu-id="133d4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="133d4-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="133d4-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="133d4-112">AR Foundation</span></span>  <br/> <span data-ttu-id="133d4-113">Versão: 1.5.0 – versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="133d4-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="133d4-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="133d4-114">AR Foundation</span></span>  <br/> <span data-ttu-id="133d4-115">Versão: 1.5.0 – versão prévia 6</span><span class="sxs-lookup"><span data-stu-id="133d4-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="133d4-116">Para o Unity 2018.4, esse pacote é incluído como uma versão prévia.</span><span class="sxs-lookup"><span data-stu-id="133d4-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="133d4-117">Para exibir o pacote: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="133d4-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="133d4-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="133d4-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="133d4-119">Versão: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="133d4-119">Version: 2.1.2</span></span> | <span data-ttu-id="133d4-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="133d4-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="133d4-121">Versão: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="133d4-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="133d4-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="133d4-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="133d4-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="133d4-123">**Android**</span></span> | <span data-ttu-id="133d4-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="133d4-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="133d4-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="133d4-125">AR Foundation</span></span>  <br/> <span data-ttu-id="133d4-126">Versão: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="133d4-126">Version: 2.1.8</span></span> |  <span data-ttu-id="133d4-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="133d4-127">AR Foundation</span></span>  <br/> <span data-ttu-id="133d4-128">Versão: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="133d4-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="133d4-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="133d4-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="133d4-130">Versão: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="133d4-130">Version: 2.1.11</span></span> | <span data-ttu-id="133d4-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="133d4-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="133d4-132">Versão: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="133d4-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="133d4-133">**Unity 2020.1.x (atualmente sem suporte formal, incluído apenas para fins informacionais)**</span><span class="sxs-lookup"><span data-stu-id="133d4-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="133d4-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="133d4-134">**Android**</span></span> | <span data-ttu-id="133d4-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="133d4-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="133d4-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="133d4-136">AR Foundation</span></span>  <br/> <span data-ttu-id="133d4-137">Versão: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="133d4-137">Version: 3.1.3</span></span> |  <span data-ttu-id="133d4-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="133d4-138">AR Foundation</span></span>  <br/> <span data-ttu-id="133d4-139">Versão: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="133d4-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="133d4-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="133d4-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="133d4-141">Versão: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="133d4-141">Version: 3.1.4</span></span> | <span data-ttu-id="133d4-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="133d4-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="133d4-143">Versão: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="133d4-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="133d4-144">Atualize o script UnityAR do MRTK definido invocando o item de menu: Utilitários do > do Kit de Ferramentas de Realidade Misturada **> UnityAR >** Script de Atualização define</span><span class="sxs-lookup"><span data-stu-id="133d4-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="133d4-145">Habilitando o provedor de configurações de câmera ar do Unity</span><span class="sxs-lookup"><span data-stu-id="133d4-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="133d4-146">As etapas a seguir presumem o uso do objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="133d4-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="133d4-147">As etapas necessárias para outros registradores de serviço podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="133d4-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="133d4-148">Selecione o objeto MixedRealityToolkit na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="133d4-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hierarquia de cena configurada do MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="133d4-150">Selecione **copiar e personalizar** para clonar o perfil MRTK para habilitar a configuração personalizada.</span><span class="sxs-lookup"><span data-stu-id="133d4-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clonar perfil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="133d4-152">Selecione **clonar** ao lado do perfil da câmera.</span><span class="sxs-lookup"><span data-stu-id="133d4-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Clonar perfil da câmera MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="133d4-154">Navegue pelo painel Inspetor até a seção sistema de câmera e expanda a seção **provedores de configurações da câmera** .</span><span class="sxs-lookup"><span data-stu-id="133d4-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Expandir provedores de configurações](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="133d4-156">Clique em **Adicionar provedor de configurações de câmera** e expanda a nova entrada de configurações de **câmera** recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="133d4-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Expandir novo provedor de configurações](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="133d4-158">Selecione o provedor de configurações da câmera do Unity AR</span><span class="sxs-lookup"><span data-stu-id="133d4-158">Select the Unity AR Camera Settings provider</span></span>

    ![Selecionar provedor de configurações do Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="133d4-160">Para obter mais informações sobre como configurar o provedor de configurações da câmera do Unity AR: [provedor de configurações da câmera do Unity ar](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="133d4-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="133d4-161">Essa instalação verifica (quando o aplicativo é iniciado) se os componentes do AR Foundation estão na cena.</span><span class="sxs-lookup"><span data-stu-id="133d4-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="133d4-162">Caso contrário, eles serão adicionados automaticamente para que funcionem com ARCore e ARKit.</span><span class="sxs-lookup"><span data-stu-id="133d4-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="133d4-163">Se você precisar definir um comportamento específico, deverá adicionar os componentes necessários por conta própria.</span><span class="sxs-lookup"><span data-stu-id="133d4-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="133d4-164">Para obter mais informações sobre os componentes e a instalação do AR Foundation, consulte esta [documentação](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="133d4-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="133d4-165">Criando uma cena para dispositivos Android e iOS</span><span class="sxs-lookup"><span data-stu-id="133d4-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="133d4-166">Verifique se você adicionou o provedor de configurações da câmera UnityAR à sua cena.</span><span class="sxs-lookup"><span data-stu-id="133d4-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="133d4-167">Mudar a plataforma para Android ou iOS nas configurações de Build do Unity</span><span class="sxs-lookup"><span data-stu-id="133d4-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="133d4-168">Quando você alternar a plataforma, deverá ver a janela configuradora do projeto MRTK com as configurações da sua plataforma escolhida.</span><span class="sxs-lookup"><span data-stu-id="133d4-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="133d4-169">Clique em aplicar para habilitar as configurações específicas da plataforma.</span><span class="sxs-lookup"><span data-stu-id="133d4-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="133d4-170">Configurações do Configurador de Projeto do iOS</span><span class="sxs-lookup"><span data-stu-id="133d4-170">iOS Project Configurator Settings</span></span>

    ![Configurador de Projeto do iOS](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="133d4-172">Não há etapas adicionais depois de alternar a plataforma para Android.</span><span class="sxs-lookup"><span data-stu-id="133d4-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="133d4-173">Se a plataforma for iOS, Editar > Configurações do Projeto > Player > Outras Configurações,  no header Otimização, desmarque o Código do Mecanismo de Distribuição</span><span class="sxs-lookup"><span data-stu-id="133d4-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Configurações do iOS](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="133d4-175">Desmarcar Código do Mecanismo de Faixa é a solução de curto prazo para um erro no Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="133d4-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="133d4-176">Estamos trabalhando em uma solução de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="133d4-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="133d4-177">Criar e executar a cena</span><span class="sxs-lookup"><span data-stu-id="133d4-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="133d4-178">Confira também</span><span class="sxs-lookup"><span data-stu-id="133d4-178">See also</span></span>

- [<span data-ttu-id="133d4-179">Configurações de câmera ar do Unity</span><span class="sxs-lookup"><span data-stu-id="133d4-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
