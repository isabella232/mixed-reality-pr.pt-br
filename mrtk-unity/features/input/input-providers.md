---
title: Provedores de entrada
description: Documentação sobre diferentes tipos de provedores de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176755"
---
# <a name="input-providers"></a><span data-ttu-id="c57b4-104">Provedores de entrada</span><span class="sxs-lookup"><span data-stu-id="c57b4-104">Input providers</span></span>

<span data-ttu-id="c57b4-105">Os provedores de entrada são registrados no **Perfil de Provedores de Serviços Registrados**, encontrado no componente Toolkit Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="c57b4-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="c57b4-106">Esses são os provedores de entrada disponíveis imediatamente, juntamente com seus controladores correspondentes:</span><span class="sxs-lookup"><span data-stu-id="c57b4-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="c57b4-107">Provedor de Entrada</span><span class="sxs-lookup"><span data-stu-id="c57b4-107">Input Provider</span></span> | <span data-ttu-id="c57b4-108">Controladores</span><span class="sxs-lookup"><span data-stu-id="c57b4-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="c57b4-109">Mão simulada</span><span class="sxs-lookup"><span data-stu-id="c57b4-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="c57b4-110">Mouse</span><span class="sxs-lookup"><span data-stu-id="c57b4-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="c57b4-111">Generic OpenVR, Vive Ltd, Vive Então, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="c57b4-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="c57b4-112">Generic Joystick</span><span class="sxs-lookup"><span data-stu-id="c57b4-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="c57b4-113">Controlador de toque do Unity</span><span class="sxs-lookup"><span data-stu-id="c57b4-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="c57b4-114">*Nenhuma*</span><span class="sxs-lookup"><span data-stu-id="c57b4-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="c57b4-115">Mão articulada wmr, controlador WMR, wmr GGV (olhar, gesto e voz) mão</span><span class="sxs-lookup"><span data-stu-id="c57b4-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="c57b4-116">*Nenhuma*</span><span class="sxs-lookup"><span data-stu-id="c57b4-116">*None*</span></span> |

<span data-ttu-id="c57b4-117">Os provedores de Ditado e Fala não criam controladores, eles geram seus próprios eventos de entrada especializados diretamente.</span><span class="sxs-lookup"><span data-stu-id="c57b4-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="c57b4-118">Provedores de entrada personalizados podem ser criados implementando a [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface .</span><span class="sxs-lookup"><span data-stu-id="c57b4-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="c57b4-119">Para obter mais informações, consulte [criando um provedor de dados do sistema de entrada](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c57b4-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
