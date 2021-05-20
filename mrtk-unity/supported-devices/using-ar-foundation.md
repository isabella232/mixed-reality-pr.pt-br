---
title: Como usar o AR Foundation
description: Documentação para usar o ARFoundation no Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 0f02eb94d95c2900348adaa9e1a02c3e54832a96
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207438"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="eee21-104">Como configurar o MRTK para iOS e Android [experimental]</span><span class="sxs-lookup"><span data-stu-id="eee21-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="eee21-105">Instalar os pacotes necessários</span><span class="sxs-lookup"><span data-stu-id="eee21-105">Install required packages</span></span>

1. <span data-ttu-id="eee21-106">Baixe e importe o pacote **Microsoft. MixedReality. Toolkit. Unity. Foundation** , do [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) ou do [Gerenciador de pacotes do Unity](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="eee21-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="eee21-107">No Gerenciador de pacotes do Unity (UPM), instale os seguintes pacotes:</span><span class="sxs-lookup"><span data-stu-id="eee21-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="eee21-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="eee21-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="eee21-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="eee21-109">**Android**</span></span> | <span data-ttu-id="eee21-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="eee21-110">**iOS**</span></span> | <span data-ttu-id="eee21-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="eee21-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="eee21-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="eee21-112">AR Foundation</span></span>  <br/> <span data-ttu-id="eee21-113">Versão: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="eee21-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="eee21-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="eee21-114">AR Foundation</span></span>  <br/> <span data-ttu-id="eee21-115">Versão: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="eee21-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="eee21-116">Para o Unity 2018,4, esse pacote é incluído como uma visualização.</span><span class="sxs-lookup"><span data-stu-id="eee21-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="eee21-117">Para exibir o pacote: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="eee21-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="eee21-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="eee21-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="eee21-119">Versão: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="eee21-119">Version: 2.1.2</span></span> | <span data-ttu-id="eee21-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="eee21-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="eee21-121">Versão: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="eee21-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="eee21-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="eee21-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="eee21-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="eee21-123">**Android**</span></span> | <span data-ttu-id="eee21-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="eee21-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="eee21-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="eee21-125">AR Foundation</span></span>  <br/> <span data-ttu-id="eee21-126">Versão: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="eee21-126">Version: 2.1.8</span></span> |  <span data-ttu-id="eee21-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="eee21-127">AR Foundation</span></span>  <br/> <span data-ttu-id="eee21-128">Versão: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="eee21-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="eee21-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="eee21-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="eee21-130">Versão: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="eee21-130">Version: 2.1.11</span></span> | <span data-ttu-id="eee21-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="eee21-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="eee21-132">Versão: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="eee21-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="eee21-133">**Unity 2020.1.x (atualmente sem suporte formal, incluído apenas para fins informacionais)**</span><span class="sxs-lookup"><span data-stu-id="eee21-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="eee21-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="eee21-134">**Android**</span></span> | <span data-ttu-id="eee21-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="eee21-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="eee21-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="eee21-136">AR Foundation</span></span>  <br/> <span data-ttu-id="eee21-137">Versão: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="eee21-137">Version: 3.1.3</span></span> |  <span data-ttu-id="eee21-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="eee21-138">AR Foundation</span></span>  <br/> <span data-ttu-id="eee21-139">Versão: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="eee21-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="eee21-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="eee21-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="eee21-141">Versão: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="eee21-141">Version: 3.1.4</span></span> | <span data-ttu-id="eee21-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="eee21-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="eee21-143">Versão: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="eee21-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="eee21-144">Atualize os scripts unityAR do MRTK definidos invocando o item de menu: Definições de scripts do Kit de Ferramentas > > de > > > Utilitários > **UnityAR > Script de** Atualização</span><span class="sxs-lookup"><span data-stu-id="eee21-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Definições de script de atualização](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="eee21-146">Habilitando o provedor de configurações de câmera ar do Unity</span><span class="sxs-lookup"><span data-stu-id="eee21-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="eee21-147">As etapas a seguir presumem o uso do objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="eee21-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="eee21-148">As etapas necessárias para outros registradores de serviço podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="eee21-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="eee21-149">Selecione o objeto MixedRealityToolkit na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="eee21-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hierarquia de cena configurada do MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="eee21-151">Selecione **copiar e personalizar** para clonar o perfil MRTK para habilitar a configuração personalizada.</span><span class="sxs-lookup"><span data-stu-id="eee21-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clonar perfil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="eee21-153">Selecione **clonar** ao lado do perfil da câmera.</span><span class="sxs-lookup"><span data-stu-id="eee21-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Clonar perfil da câmera MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="eee21-155">Navegue pelo painel Inspetor até a seção sistema de câmera e expanda a seção **provedores de configurações da câmera** .</span><span class="sxs-lookup"><span data-stu-id="eee21-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Expandir provedores de configurações](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="eee21-157">Clique em **Adicionar provedor de configurações de câmera** e expanda a nova entrada de configurações de **câmera** recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="eee21-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Expandir novo provedor de configurações](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="eee21-159">Selecione o provedor de configurações da câmera do Unity AR</span><span class="sxs-lookup"><span data-stu-id="eee21-159">Select the Unity AR Camera Settings provider</span></span>

    ![Selecionar provedor de configurações do Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="eee21-161">Para obter mais informações sobre como configurar o provedor de configurações da câmera do Unity AR: [provedor de configurações da câmera do Unity ar](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="eee21-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="eee21-162">Essa instalação verifica (quando o aplicativo é iniciado) se os componentes do AR Foundation estão na cena.</span><span class="sxs-lookup"><span data-stu-id="eee21-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="eee21-163">Caso contrário, eles serão adicionados automaticamente para que funcionem com ARCore e ARKit.</span><span class="sxs-lookup"><span data-stu-id="eee21-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="eee21-164">Se você precisar definir um comportamento específico, deverá adicionar os componentes necessários por conta própria.</span><span class="sxs-lookup"><span data-stu-id="eee21-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="eee21-165">Para obter mais informações sobre os componentes e a instalação do AR Foundation, consulte esta [documentação](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="eee21-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="eee21-166">Criando uma cena para dispositivos Android e iOS</span><span class="sxs-lookup"><span data-stu-id="eee21-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="eee21-167">Verifique se você adicionou o provedor de configurações da câmera UnityAR à sua cena.</span><span class="sxs-lookup"><span data-stu-id="eee21-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="eee21-168">Mudar a plataforma para Android ou iOS nas configurações de Build do Unity</span><span class="sxs-lookup"><span data-stu-id="eee21-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="eee21-169">Verifique se o provedor de gerenciamento de plug-in do XR associado está habilitado</span><span class="sxs-lookup"><span data-stu-id="eee21-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="eee21-170">Gerenciamento de plug-ins do iOS XR:  ![ Ios de gerenciamento de plug-in de XR](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="eee21-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="eee21-171">Criar e executar a cena</span><span class="sxs-lookup"><span data-stu-id="eee21-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="eee21-172">Confira também</span><span class="sxs-lookup"><span data-stu-id="eee21-172">See also</span></span>

- [<span data-ttu-id="eee21-173">Configurações de câmera ar do Unity</span><span class="sxs-lookup"><span data-stu-id="eee21-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
