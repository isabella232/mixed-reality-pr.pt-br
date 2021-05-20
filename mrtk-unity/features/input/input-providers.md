---
title: Provedores de entrada
description: Documentação sobre diferentes tipos de provedores de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145267"
---
# <a name="input-providers"></a><span data-ttu-id="a2724-104">Provedores de entrada</span><span class="sxs-lookup"><span data-stu-id="a2724-104">Input providers</span></span>

<span data-ttu-id="a2724-105">Os provedores de entrada são registrados no **Perfil de Provedores de Serviços Registrados**, encontrado no componente Kit de Ferramentas de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="a2724-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="a2724-106">Esses são os provedores de entrada disponíveis imediatamente, juntamente com seus controladores correspondentes:</span><span class="sxs-lookup"><span data-stu-id="a2724-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="a2724-107">Provedor de Entrada</span><span class="sxs-lookup"><span data-stu-id="a2724-107">Input Provider</span></span> | <span data-ttu-id="a2724-108">Controladores</span><span class="sxs-lookup"><span data-stu-id="a2724-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="a2724-109">Mão simulada</span><span class="sxs-lookup"><span data-stu-id="a2724-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="a2724-110">Mouse</span><span class="sxs-lookup"><span data-stu-id="a2724-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="a2724-111">Generic OpenVR, Vive Ltd, Vive Então, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="a2724-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="a2724-112">Generic Joystick</span><span class="sxs-lookup"><span data-stu-id="a2724-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="a2724-113">Controlador de toque do Unity</span><span class="sxs-lookup"><span data-stu-id="a2724-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="a2724-114">*Nenhuma*</span><span class="sxs-lookup"><span data-stu-id="a2724-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="a2724-115">Mão articulada wmr, controlador WMR, wmr GGV (olhar, gesto e voz) mão</span><span class="sxs-lookup"><span data-stu-id="a2724-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="a2724-116">*Nenhuma*</span><span class="sxs-lookup"><span data-stu-id="a2724-116">*None*</span></span> |

<span data-ttu-id="a2724-117">Os provedores de Ditado e Fala não criam controladores, eles geram seus próprios eventos de entrada especializados diretamente.</span><span class="sxs-lookup"><span data-stu-id="a2724-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="a2724-118">Provedores de entrada personalizados podem ser criados implementando a [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface .</span><span class="sxs-lookup"><span data-stu-id="a2724-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="a2724-119">Para obter mais informações, consulte [criando um provedor de dados do sistema de entrada](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a2724-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
