---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748483"
---
# <a name="mrtk"></a>[<span data-ttu-id="fa3ca-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="fa3ca-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="fa3ca-102">Use a [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) do MRTK para Unity e de definir a Escala de **Destino** como **Sala** ou **Em Espera:**</span><span class="sxs-lookup"><span data-stu-id="fa3ca-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="fa3ca-104">O MRTK deve lidar com a posição do playspace e da câmera automaticamente, mas é bom verificar duas vezes:</span><span class="sxs-lookup"><span data-stu-id="fa3ca-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Playspace do MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="fa3ca-106">No painel **Hierarquia,** expanda **MixedRealityPlayspace** GameObject e encontre o **objeto filho da Câmera** Principal</span><span class="sxs-lookup"><span data-stu-id="fa3ca-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="fa3ca-107">No painel **Inspetor,** encontre o **componente Transformar** e altere a **Posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="fa3ca-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="fa3ca-108">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="fa3ca-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="fa3ca-109">De definir o modo de origem de acompanhamento [no XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="fa3ca-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="fa3ca-110">Depois de obter o subsistema, chame [TrySetTrackingOriginMode:](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)</span><span class="sxs-lookup"><span data-stu-id="fa3ca-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="fa3ca-111">E trabalhe com o [XRRig do](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)Unity.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Plataforma XR na hierarquia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="fa3ca-113">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="fa3ca-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="fa3ca-114">Vá para **a seção Outras Configurações** das **Configurações do Player da Windows Store**</span><span class="sxs-lookup"><span data-stu-id="fa3ca-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="fa3ca-115">Escolha **Windows Mixed Reality** como o dispositivo, que pode ser listado como **Windows Holographic** em versões mais antigas do Unity</span><span class="sxs-lookup"><span data-stu-id="fa3ca-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="fa3ca-116">Selecione **Realidade Virtual Com Suporte**</span><span class="sxs-lookup"><span data-stu-id="fa3ca-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="fa3ca-117">Como o objeto Câmera Principal é marcado automaticamente como a câmera, o Unity acionará toda a movimentação e a tradução.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="fa3ca-118">Essas configurações precisam ser aplicadas à Câmera em cada cena do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="fa3ca-119">Por padrão, quando você cria uma nova cena no Unity, ela conterá um GameObject da Câmera Principal na Hierarquia que inclui o componente Câmera, mas não tem as configurações abaixo aplicadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="fa3ca-120">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="fa3ca-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="fa3ca-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="fa3ca-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="fa3ca-122">Para uma **experiência de escala permanente** ou de escala **de** espaço, você precisará colocar o conteúdo em relação ao chão.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="fa3ca-123">Você se preocupa com o piso do usuário usando o estágio espacial **[,](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** que representa a origem definida no nível do piso do usuário e o limite de sala opcional, configurada durante a primeira operação.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="fa3ca-124">Para garantir que o Unity está operando com seu sistema de coordenadas mundial no nível do chão, você pode definir e testar se o Unity está usando o tipo de espaço de acompanhamento RoomScale:</span><span class="sxs-lookup"><span data-stu-id="fa3ca-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* <span data-ttu-id="fa3ca-125">Se SetTrackingSpaceType retornar true, o Unity alterna com êxito seu sistema de coordenadas mundial para acompanhar o quadro [de estágio de referência](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="fa3ca-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="fa3ca-126">Se SetTrackingSpaceType retornar false, o Unity não poderá alternar para o quadro de estágio de referência, provavelmente porque o usuário não tiver definido um andar em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="fa3ca-127">Embora um valor de retorno falso não seja comum, isso pode acontecer se o estágio estiver definido em uma sala diferente e o dispositivo for movido para a sala atual sem que o usuário configurar um novo estágio.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="fa3ca-128">Depois que o aplicativo define com êxito o tipo de espaço de acompanhamento RoomScale, o conteúdo colocado no plano y=0 será exibido no chão.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="fa3ca-129">A origem em 0, 0, 0 será o local específico no chão em que o usuário se juntou durante a instalação da sala, com -Z representando a direção para frente que ele estava enfrentando durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="fa3ca-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>