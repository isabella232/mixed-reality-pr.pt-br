---
title: Implantando no Android e iOS (AR Foundation) [experimental]
description: Documentação para configurar o MRTK para Android e iOS (ARFoundation) no Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, ar Core, ar Kit, ios, ios, Android, ar Foundation
ms.openlocfilehash: d127b9b39cbaa90f0c8c5a8a6ac7955f33404cbf
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281943"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a><span data-ttu-id="f1916-104">Implantando no Android e iOS (AR Foundation) [experimental]</span><span class="sxs-lookup"><span data-stu-id="f1916-104">Deploying to Android and iOS (AR Foundation) [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="f1916-105">Instalar os pacotes necessários</span><span class="sxs-lookup"><span data-stu-id="f1916-105">Install required packages</span></span>

1. <span data-ttu-id="f1916-106">Baixe e importe o **Microsoft. MixedReality. Toolkit. pacote do unity. Foundation** , do [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) ou do [Gerenciador de Pacotes do unity](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="f1916-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="f1916-107">no Gerenciador de Pacotes do Unity (UPM), instale os seguintes pacotes:</span><span class="sxs-lookup"><span data-stu-id="f1916-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="f1916-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="f1916-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="f1916-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="f1916-109">**Android**</span></span> | <span data-ttu-id="f1916-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="f1916-110">**iOS**</span></span> | <span data-ttu-id="f1916-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1916-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="f1916-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f1916-112">AR Foundation</span></span>  <br/> <span data-ttu-id="f1916-113">Versão: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="f1916-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="f1916-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f1916-114">AR Foundation</span></span>  <br/> <span data-ttu-id="f1916-115">Versão: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="f1916-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="f1916-116">Para o Unity 2018,4, esse pacote é incluído como uma visualização.</span><span class="sxs-lookup"><span data-stu-id="f1916-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="f1916-117">Para exibir o pacote: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="f1916-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="f1916-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="f1916-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="f1916-119">Versão: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="f1916-119">Version: 2.1.2</span></span> | <span data-ttu-id="f1916-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="f1916-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="f1916-121">Versão: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="f1916-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="f1916-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="f1916-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="f1916-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="f1916-123">**Android**</span></span> | <span data-ttu-id="f1916-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="f1916-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="f1916-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f1916-125">AR Foundation</span></span>  <br/> <span data-ttu-id="f1916-126">Versão: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="f1916-126">Version: 2.1.8</span></span> |  <span data-ttu-id="f1916-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f1916-127">AR Foundation</span></span>  <br/> <span data-ttu-id="f1916-128">Versão: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="f1916-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="f1916-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="f1916-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="f1916-130">Versão: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="f1916-130">Version: 2.1.11</span></span> | <span data-ttu-id="f1916-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="f1916-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="f1916-132">Versão: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="f1916-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="f1916-133">**Unity 2020.3. x**</span><span class="sxs-lookup"><span data-stu-id="f1916-133">**Unity 2020.3.x**</span></span>

    | <span data-ttu-id="f1916-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="f1916-134">**Android**</span></span> | <span data-ttu-id="f1916-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="f1916-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="f1916-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f1916-136">AR Foundation</span></span>  <br/> <span data-ttu-id="f1916-137">Versão: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="f1916-137">Version: 3.1.3</span></span> |  <span data-ttu-id="f1916-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f1916-138">AR Foundation</span></span>  <br/> <span data-ttu-id="f1916-139">Versão: 4.0.12</span><span class="sxs-lookup"><span data-stu-id="f1916-139">Version: 4.0.12</span></span> |
    | <span data-ttu-id="f1916-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="f1916-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="f1916-141">Versão: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="f1916-141">Version: 3.1.4</span></span> | <span data-ttu-id="f1916-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="f1916-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="f1916-143">Versão: 4.1.7</span><span class="sxs-lookup"><span data-stu-id="f1916-143">Version: 4.1.7</span></span> |

1. <span data-ttu-id="f1916-144">atualize o MRTK UnityAR scripting define invocando o item de menu: **realidade misturada > Toolkit > Utilities > UnityAR > atualizar script define**</span><span class="sxs-lookup"><span data-stu-id="f1916-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Atualizar definições de script](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="f1916-146">Habilitando o provedor de configurações da câmera do Unity AR</span><span class="sxs-lookup"><span data-stu-id="f1916-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="f1916-147">As etapas a seguir presumem o uso do objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="f1916-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="f1916-148">As etapas necessárias para outros registradores de serviço podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="f1916-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="f1916-149">Selecione o objeto MixedRealityToolkit na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="f1916-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK hierarquia de cena configurada](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="f1916-151">Selecione **copiar e personalizar** para clonar o perfil MRTK para habilitar a configuração personalizada.</span><span class="sxs-lookup"><span data-stu-id="f1916-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clonar perfil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="f1916-153">Selecione **clonar** ao lado do perfil da câmera.</span><span class="sxs-lookup"><span data-stu-id="f1916-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Clonar perfil da câmera MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="f1916-155">navegue pelo painel inspetor até a seção sistema de câmera e expanda a seção **câmera Configurações provedores** .</span><span class="sxs-lookup"><span data-stu-id="f1916-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Expandir provedores de configurações](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="f1916-157">clique em **adicionar câmera Configurações provedor** e expanda a **nova** entrada de configurações de câmera recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="f1916-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Expandir novo provedor de configurações](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="f1916-159">selecione o provedor de Configurações da câmera do Unity AR</span><span class="sxs-lookup"><span data-stu-id="f1916-159">Select the Unity AR Camera Settings provider</span></span>

    ![Selecionar provedor de configurações do Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="f1916-161">Para obter mais informações sobre como configurar o provedor de configurações da câmera do Unity AR: [provedor de configurações da câmera do Unity ar](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f1916-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f1916-162">Essa instalação verifica (quando o aplicativo é iniciado) se os componentes do AR Foundation estão na cena.</span><span class="sxs-lookup"><span data-stu-id="f1916-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="f1916-163">Caso contrário, eles serão adicionados automaticamente para que funcionem com ARCore e ARKit.</span><span class="sxs-lookup"><span data-stu-id="f1916-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="f1916-164">Se você precisar definir um comportamento específico, deverá adicionar os componentes necessários por conta própria.</span><span class="sxs-lookup"><span data-stu-id="f1916-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="f1916-165">Para obter mais informações sobre os componentes e a instalação do AR Foundation, consulte esta [documentação](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="f1916-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="f1916-166">Criando uma cena para dispositivos Android e iOS</span><span class="sxs-lookup"><span data-stu-id="f1916-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="f1916-167">verifique se você adicionou o provedor de Configurações de câmera UnityAR à sua cena.</span><span class="sxs-lookup"><span data-stu-id="f1916-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="f1916-168">alterne a plataforma para Android ou iOS no Build do Unity Configurações</span><span class="sxs-lookup"><span data-stu-id="f1916-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="f1916-169">Verifique se o provedor de gerenciamento de plug-in do XR associado está habilitado</span><span class="sxs-lookup"><span data-stu-id="f1916-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="f1916-170">Gerenciamento de plug-ins do iOS XR:  ![ Ios de gerenciamento de plug-in de XR](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="f1916-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="f1916-171">Compilar e executar a cena</span><span class="sxs-lookup"><span data-stu-id="f1916-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="f1916-172">Confira também</span><span class="sxs-lookup"><span data-stu-id="f1916-172">See also</span></span>

- [<span data-ttu-id="f1916-173">Configurações de câmera do Unity AR</span><span class="sxs-lookup"><span data-stu-id="f1916-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
