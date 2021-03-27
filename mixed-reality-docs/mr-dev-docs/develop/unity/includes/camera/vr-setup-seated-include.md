---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636251"
---
# <a name="mrtk"></a>[<span data-ttu-id="dc0b1-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="dc0b1-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="dc0b1-102">Use a classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity e defina a **escala de destino** como **encaixada**:</span><span class="sxs-lookup"><span data-stu-id="dc0b1-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="dc0b1-104">MRTK deve tratar a posição da Playspace e da câmera automaticamente, mas é bom fazer uma verificação dupla:</span><span class="sxs-lookup"><span data-stu-id="dc0b1-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="dc0b1-106">No painel **hierarquia** , expanda o **MixedRealityPlayspace** gameobject e localize o objeto filho da **câmera principal**</span><span class="sxs-lookup"><span data-stu-id="dc0b1-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="dc0b1-107">No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="dc0b1-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="dc0b1-108">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="dc0b1-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="dc0b1-109">Defina o modo de origem de rastreamento no [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="dc0b1-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="dc0b1-110">Depois de obter o subsistema, chame [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="dc0b1-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="dc0b1-111">E trabalhar com o [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)do Unity.</span><span class="sxs-lookup"><span data-stu-id="dc0b1-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Dispositivo XR na hierarquia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="dc0b1-113">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="dc0b1-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="dc0b1-114">Ir para **outra** seção de configurações das **configurações do Windows Store Player**</span><span class="sxs-lookup"><span data-stu-id="dc0b1-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="dc0b1-115">Escolha a **realidade mista do Windows** como o dispositivo, que pode ser listado como **Holographic do Windows** em versões mais antigas do Unity</span><span class="sxs-lookup"><span data-stu-id="dc0b1-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="dc0b1-116">Selecione a **realidade virtual com suporte**</span><span class="sxs-lookup"><span data-stu-id="dc0b1-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="dc0b1-117">Como o objeto da câmera principal é marcado automaticamente como a câmera, o Unity alimenta todo o movimento e a tradução.</span><span class="sxs-lookup"><span data-stu-id="dc0b1-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="dc0b1-118">Essas configurações precisam ser aplicadas à câmera em cada cena do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc0b1-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="dc0b1-119">Por padrão, quando você cria uma nova cena no Unity, ela conterá uma câmara de jogo principal na hierarquia que inclui o componente da câmera, mas não tem as configurações abaixo aplicadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="dc0b1-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="dc0b1-120">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="dc0b1-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="dc0b1-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="dc0b1-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="dc0b1-122">Para criar uma experiência **somente de orientação** ou **de escala assentada**, você precisa definir o Unity para o tipo de espaço de rastreamento estacionário.</span><span class="sxs-lookup"><span data-stu-id="dc0b1-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="dc0b1-123">O espaço de acompanhamento fixo define o sistema de coordenadas mundiais do Unity para acompanhar o [quadro de referência](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="dc0b1-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="dc0b1-124">No modo de rastreamento estacionário, o conteúdo colocado no editor apenas na frente do local padrão da câmera (Forward is-Z) aparecerá na frente do usuário quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="dc0b1-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="dc0b1-125">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="dc0b1-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="dc0b1-126">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="dc0b1-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="dc0b1-127">Para uma **experiência pura somente de orientação** , como um visualizador de vídeo de 360 graus (em que as atualizações de cabeça posicional poderiam arruinar a ilusão), você pode então definir a [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) para true:</span><span class="sxs-lookup"><span data-stu-id="dc0b1-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="dc0b1-128">Para uma **experiência em escala**, para permitir que o usuário recentralize a origem encaixada novamente, você pode chamar a [XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="dc0b1-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="dc0b1-129">Se você estiver criando uma [experiência de escala](../../../../design/coordinate-systems.md)em posição, poderá recentralizar a origem mundial da unidade na posição de cabeçalho atual do usuário chamando o **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .</span><span class="sxs-lookup"><span data-stu-id="dc0b1-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>