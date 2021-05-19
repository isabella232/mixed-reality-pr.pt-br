---
title: Visão geral do sistema de câmera
description: Página de aterrissagem do sistema de câmeras no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Câmera,
ms.openlocfilehash: 1dc5328f2a6390246918063b6564837f150d28d8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144474"
---
# <a name="camera-system"></a><span data-ttu-id="e22a5-104">Sistema de câmeras</span><span class="sxs-lookup"><span data-stu-id="e22a5-104">Camera system</span></span>

<span data-ttu-id="e22a5-105">O sistema de câmeras permite que o Microsoft Mixed Reality Toolkit configure e otimize a câmera do aplicativo para uso em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e22a5-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="e22a5-106">Usando o sistema de câmeras, os aplicativos podem ser escritos para dar suporte a dispositivos opacos (por exemplo: realidade virtual) e transparentes (por exemplo: Microsoft HoloLens) sem a necessidade de escrever código para distinguir e acomodar cada tipo de exibição.</span><span class="sxs-lookup"><span data-stu-id="e22a5-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="e22a5-107">Habilitando o sistema de câmeras</span><span class="sxs-lookup"><span data-stu-id="e22a5-107">Enabling the camera system</span></span>

<span data-ttu-id="e22a5-108">O Sistema de Câmera é gerenciado pelo objeto MixedRealityToolkit (ou outro componente do registrador de serviços).</span><span class="sxs-lookup"><span data-stu-id="e22a5-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="e22a5-109">As etapas a seguir presumem o uso do objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="e22a5-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="e22a5-110">As etapas necessárias para outros registradores de serviço podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="e22a5-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="e22a5-111">Selecione o objeto MixedRealityToolkit na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="e22a5-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="e22a5-113">Navegue pelo painel Inspetor até a seção sistema de câmeras e verifique se **Habilitar Sistema de Câmera** está marcado.</span><span class="sxs-lookup"><span data-stu-id="e22a5-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![Habilitando o sistema de câmeras](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="e22a5-115">Selecione a implementação do sistema de câmera.</span><span class="sxs-lookup"><span data-stu-id="e22a5-115">Select the camera system implementation.</span></span> <span data-ttu-id="e22a5-116">A implementação de classe padrão fornecida pelo MRTK é o `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="e22a5-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![Selecionar a implementação do sistema de câmeras](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="e22a5-118">Selecione o perfil de configuração desejado</span><span class="sxs-lookup"><span data-stu-id="e22a5-118">Select the desired configuration profile</span></span>

    ![Selecionar perfil do sistema de câmera](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="e22a5-120">Configurando o sistema de câmeras</span><span class="sxs-lookup"><span data-stu-id="e22a5-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="e22a5-121">Provedores de configurações</span><span class="sxs-lookup"><span data-stu-id="e22a5-121">Settings providers</span></span>

![Provedores de configurações da câmera](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="e22a5-123">Os provedores de configuração da câmera habilitam a configuração específica da plataforma da câmera.</span><span class="sxs-lookup"><span data-stu-id="e22a5-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="e22a5-124">Essas configurações podem incluir etapas de configuração personalizadas e/ou componentes.</span><span class="sxs-lookup"><span data-stu-id="e22a5-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="e22a5-125">Os provedores podem ser adicionados clicando no botão **Adicionar provedor de configurações de câmera** .</span><span class="sxs-lookup"><span data-stu-id="e22a5-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="e22a5-126">Eles podem ser removidos clicando no **-** botão à direita do nome do provedor.</span><span class="sxs-lookup"><span data-stu-id="e22a5-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="e22a5-127">Nem todas as plataformas precisarão de um provedor de configurações de câmera.</span><span class="sxs-lookup"><span data-stu-id="e22a5-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="e22a5-128">Se não houver provedores compatíveis com a plataforma na qual o aplicativo está sendo executado, o kit de ferramentas do Microsoft Mixed Reality aplicará padrões básicos.</span><span class="sxs-lookup"><span data-stu-id="e22a5-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="e22a5-129">Configurações de vídeo</span><span class="sxs-lookup"><span data-stu-id="e22a5-129">Display settings</span></span>

![Configurações de vídeo da câmera](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="e22a5-131">As configurações de exibição são especificadas para exibições opacas (ex: virtual reality) e Transparent (ex: Microsoft HoloLens).</span><span class="sxs-lookup"><span data-stu-id="e22a5-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="e22a5-132">A câmera está configurada, em tempo de execução, usando essas configurações.</span><span class="sxs-lookup"><span data-stu-id="e22a5-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="e22a5-133">**Clipe próximo**</span><span class="sxs-lookup"><span data-stu-id="e22a5-133">**Near Clip**</span></span>

<span data-ttu-id="e22a5-134">O plano próximo é o mais próximo, em metros, que um objeto virtual pode ser para a câmera e ainda ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="e22a5-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="e22a5-135">Para maior conforto ao usuário, é recomendável tornar esse valor maior que zero.</span><span class="sxs-lookup"><span data-stu-id="e22a5-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="e22a5-136">A imagem anterior contém valores que foram considerados confortáveis em uma variedade de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e22a5-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="e22a5-137">**Clipe distante**</span><span class="sxs-lookup"><span data-stu-id="e22a5-137">**Far Clip**</span></span>

<span data-ttu-id="e22a5-138">O plano de clipe distante é o mais distante, em metros, que um objeto virtual pode ser para a câmera e ainda assim ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="e22a5-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="e22a5-139">Para dispositivos transparentes, é recomendável que esse valor seja relativamente próximo de exceder excessivamente o espaço real do mundo e interromper as qualidades de imersão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e22a5-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="e22a5-140">**Limpar sinalizadores**</span><span class="sxs-lookup"><span data-stu-id="e22a5-140">**Clear Flags**</span></span>

<span data-ttu-id="e22a5-141">O valor limpar sinalizadores indica como a exibição é limpa, pois é desenhada.</span><span class="sxs-lookup"><span data-stu-id="e22a5-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="e22a5-142">Para experiências de realidade virtual, esse valor é definido com mais frequência como Skybox.</span><span class="sxs-lookup"><span data-stu-id="e22a5-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="e22a5-143">Para exibições transparentes, é recomendável definir isso como Cor.</span><span class="sxs-lookup"><span data-stu-id="e22a5-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="e22a5-144">**Cor da tela de fundo**</span><span class="sxs-lookup"><span data-stu-id="e22a5-144">**Background Color**</span></span>

<span data-ttu-id="e22a5-145">Se os sinalizadores não definidos como Skybox, a propriedade de cor da tela de fundo será exibida.</span><span class="sxs-lookup"><span data-stu-id="e22a5-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="e22a5-146">**Configurações de Qualidade**</span><span class="sxs-lookup"><span data-stu-id="e22a5-146">**Quality Settings**</span></span>

<span data-ttu-id="e22a5-147">O valor de configurações de qualidade indica a qualidade dos gráficos que o Unity deve usar ao renderizar a cena.</span><span class="sxs-lookup"><span data-stu-id="e22a5-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="e22a5-148">O nível de qualidade é uma configuração de nível de projeto e não é específico para nenhuma câmera.</span><span class="sxs-lookup"><span data-stu-id="e22a5-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="e22a5-149">Para obter mais informações, consulte o [artigo Qualidade](https://docs.unity3d.com/Manual/class-QualitySettings.html) na documentação do Unity.</span><span class="sxs-lookup"><span data-stu-id="e22a5-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e22a5-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="e22a5-150">See also</span></span>

- [<span data-ttu-id="e22a5-151">Documentação da API do Sistema de Câmera</span><span class="sxs-lookup"><span data-stu-id="e22a5-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="e22a5-152">Criando um provedor de configurações de câmera</span><span class="sxs-lookup"><span data-stu-id="e22a5-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
