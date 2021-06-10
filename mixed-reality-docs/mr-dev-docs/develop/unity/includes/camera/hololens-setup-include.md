---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748515"
---
# <a name="mrtk"></a>[<span data-ttu-id="7b61a-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="7b61a-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7b61a-102">Siga este [tutorial passo a passo para](../../tutorials/mr-learning-base-01.md) adicionar e configurar automaticamente o Kit de Ferramentas de Realidade Misturada em seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="7b61a-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="7b61a-103">Também é possível trabalhar diretamente com a [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) do MRTK para Unity e definir a **Escala** de Destino como **Mundo:**</span><span class="sxs-lookup"><span data-stu-id="7b61a-103">It's also possible to work directly with the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="7b61a-105">O MRTK deve lidar com a posição do playspace e da câmera automaticamente, mas é bom verificar duas vezes:</span><span class="sxs-lookup"><span data-stu-id="7b61a-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Playspace do MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="7b61a-107">No painel **Hierarquia,** expanda **MixedRealityPlayspace** GameObject e encontre o **objeto filho da Câmera** Principal</span><span class="sxs-lookup"><span data-stu-id="7b61a-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="7b61a-108">No painel **Inspetor,** encontre o **componente Transformar** e altere a **Posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="7b61a-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="7b61a-109">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="7b61a-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7b61a-110">De definir o modo de origem de acompanhamento [no XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="7b61a-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="7b61a-111">Depois de obter o subsistema, chame [TrySetTrackingOriginMode:](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)</span><span class="sxs-lookup"><span data-stu-id="7b61a-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="7b61a-112">Você pode usar [ARSession para aplicativos](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) HoloLens, que funciona melhor com âncoras e ARKit/ARCore.</span><span class="sxs-lookup"><span data-stu-id="7b61a-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![Sessão AR na hierarquia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="7b61a-114">A Sessão de RA e os recursos relacionados precisam do AR Foundation instalado.</span><span class="sxs-lookup"><span data-stu-id="7b61a-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="7b61a-115">Também é possível aplicar as alterações da câmera manualmente sem usar ARSession:</span><span class="sxs-lookup"><span data-stu-id="7b61a-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="7b61a-116">Selecione **Câmera Principal** no painel **Hierarquia**</span><span class="sxs-lookup"><span data-stu-id="7b61a-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="7b61a-117">No painel **Inspetor,** encontre o **componente Transformar** e altere a **Posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="7b61a-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="7b61a-118">![Câmera no painel Inspetor no Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="7b61a-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="7b61a-119">*Câmera no painel Inspetor no Unity*</span><span class="sxs-lookup"><span data-stu-id="7b61a-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="7b61a-120">Adicionar um **TrackedPoseDriver** à **Câmera Principal**</span><span class="sxs-lookup"><span data-stu-id="7b61a-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="7b61a-121">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="7b61a-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="7b61a-122">Selecione **Câmera Principal** no painel **Hierarquia**</span><span class="sxs-lookup"><span data-stu-id="7b61a-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="7b61a-123">No painel **Inspetor,** encontre o **componente Transformar** e altere a **Posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="7b61a-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="7b61a-124">![Câmera no painel Inspetor no Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="7b61a-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="7b61a-125">*Câmera no painel Inspetor no Unity*</span><span class="sxs-lookup"><span data-stu-id="7b61a-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="7b61a-126">Vá para **a seção Outras Configurações** das **Configurações do Player da Windows Store**</span><span class="sxs-lookup"><span data-stu-id="7b61a-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="7b61a-127">Escolha **Windows Mixed Reality** como o dispositivo, que pode ser listado como **Windows Holographic** em versões mais antigas do Unity</span><span class="sxs-lookup"><span data-stu-id="7b61a-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="7b61a-128">Selecione **Realidade Virtual Com Suporte**</span><span class="sxs-lookup"><span data-stu-id="7b61a-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="7b61a-129">Como o objeto Câmera Principal é marcado automaticamente como a câmera, o Unity acionará toda a movimentação e a tradução.</span><span class="sxs-lookup"><span data-stu-id="7b61a-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="7b61a-130">Essas configurações precisam ser aplicadas à Câmera em cada cena do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b61a-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="7b61a-131">Por padrão, quando você cria uma nova cena no Unity, ela conterá um GameObject da Câmera Principal na Hierarquia que inclui o componente Câmera, mas pode não ter as configurações aplicadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="7b61a-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>