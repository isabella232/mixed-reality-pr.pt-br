---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636241"
---
# <a name="mrtk"></a>[<span data-ttu-id="fe936-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="fe936-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="fe936-102">Siga este [tutorial](../../tutorials/mr-learning-base-01.md) passo a passo para adicionar e configurar automaticamente o kit de ferramentas de realidade misturada em seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="fe936-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="fe936-103">Também é possível trabalhar diretamente com a classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity e definir a escala de **destino** como **mundo**:</span><span class="sxs-lookup"><span data-stu-id="fe936-103">It's also possible to work directly with the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="fe936-105">MRTK deve tratar a posição da Playspace e da câmera automaticamente, mas é bom fazer uma verificação dupla:</span><span class="sxs-lookup"><span data-stu-id="fe936-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="fe936-107">No painel **hierarquia** , expanda o **MixedRealityPlayspace** gameobject e localize o objeto filho da **câmera principal**</span><span class="sxs-lookup"><span data-stu-id="fe936-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="fe936-108">No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="fe936-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="fe936-109">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="fe936-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="fe936-110">Defina o modo de origem de rastreamento no [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="fe936-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="fe936-111">Depois de obter o subsistema, chame [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="fe936-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="fe936-112">Você pode usar o [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) para aplicativos do HoloLens, que funciona melhor com âncoras e ARKit/ARCore.</span><span class="sxs-lookup"><span data-stu-id="fe936-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![Sessão AR na hierarquia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="fe936-114">A sessão AR e os recursos relacionados precisam do AR Foundation instalado.</span><span class="sxs-lookup"><span data-stu-id="fe936-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="fe936-115">Também é possível aplicar as alterações da câmera manualmente sem usar ARSession:</span><span class="sxs-lookup"><span data-stu-id="fe936-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="fe936-116">Selecione a **câmera principal** no painel **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="fe936-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="fe936-117">No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="fe936-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="fe936-118">![Câmera no painel de Inspetor no Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="fe936-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="fe936-119">*Câmera no painel de Inspetor no Unity*</span><span class="sxs-lookup"><span data-stu-id="fe936-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="fe936-120">Adicionar um **TrackedPoseDriver** à **câmera principal**</span><span class="sxs-lookup"><span data-stu-id="fe936-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="fe936-121">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="fe936-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="fe936-122">Selecione a **câmera principal** no painel **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="fe936-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="fe936-123">No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="fe936-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="fe936-124">![Câmera no painel de Inspetor no Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="fe936-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="fe936-125">*Câmera no painel de Inspetor no Unity*</span><span class="sxs-lookup"><span data-stu-id="fe936-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="fe936-126">Ir para **outra** seção de configurações das **configurações do Windows Store Player**</span><span class="sxs-lookup"><span data-stu-id="fe936-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="fe936-127">Escolha a **realidade mista do Windows** como o dispositivo, que pode ser listado como **Holographic do Windows** em versões mais antigas do Unity</span><span class="sxs-lookup"><span data-stu-id="fe936-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="fe936-128">Selecione a **realidade virtual com suporte**</span><span class="sxs-lookup"><span data-stu-id="fe936-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="fe936-129">Como o objeto da câmera principal é marcado automaticamente como a câmera, o Unity alimenta todo o movimento e a tradução.</span><span class="sxs-lookup"><span data-stu-id="fe936-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="fe936-130">Essas configurações precisam ser aplicadas à câmera em cada cena do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe936-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="fe936-131">Por padrão, quando você cria uma nova cena no Unity, ela conterá uma câmara de jogo principal na hierarquia que inclui o componente da câmera, mas pode não ter as configurações aplicadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="fe936-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>