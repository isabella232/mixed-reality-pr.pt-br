---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636252"
---
# <a name="mrtk"></a>[<span data-ttu-id="0bfec-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="0bfec-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="0bfec-102">Use a classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity e defina a **escala de destino** como **sala** ou **posição**:</span><span class="sxs-lookup"><span data-stu-id="0bfec-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="0bfec-104">MRTK deve tratar a posição da Playspace e da câmera automaticamente, mas é bom fazer uma verificação dupla:</span><span class="sxs-lookup"><span data-stu-id="0bfec-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="0bfec-106">No painel **hierarquia** , expanda o **MixedRealityPlayspace** gameobject e localize o objeto filho da **câmera principal**</span><span class="sxs-lookup"><span data-stu-id="0bfec-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="0bfec-107">No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="0bfec-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="0bfec-108">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="0bfec-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="0bfec-109">Defina o modo de origem de rastreamento no [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="0bfec-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="0bfec-110">Depois de obter o subsistema, chame [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="0bfec-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="0bfec-111">E trabalhar com o [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)do Unity.</span><span class="sxs-lookup"><span data-stu-id="0bfec-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Dispositivo XR na hierarquia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="0bfec-113">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="0bfec-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="0bfec-114">Ir para **outra** seção de configurações das **configurações do Windows Store Player**</span><span class="sxs-lookup"><span data-stu-id="0bfec-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="0bfec-115">Escolha a **realidade mista do Windows** como o dispositivo, que pode ser listado como **Holographic do Windows** em versões mais antigas do Unity</span><span class="sxs-lookup"><span data-stu-id="0bfec-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="0bfec-116">Selecione a **realidade virtual com suporte**</span><span class="sxs-lookup"><span data-stu-id="0bfec-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="0bfec-117">Como o objeto da câmera principal é marcado automaticamente como a câmera, o Unity alimenta todo o movimento e a tradução.</span><span class="sxs-lookup"><span data-stu-id="0bfec-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="0bfec-118">Essas configurações precisam ser aplicadas à câmera em cada cena do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0bfec-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="0bfec-119">Por padrão, quando você cria uma nova cena no Unity, ela conterá uma câmara de jogo principal na hierarquia que inclui o componente da câmera, mas não tem as configurações abaixo aplicadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="0bfec-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="0bfec-120">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="0bfec-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="0bfec-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="0bfec-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="0bfec-122">Para uma experiência **de escala de** colocação ou de escala de **espaço**, você precisará colocar o conteúdo em relação ao andar.</span><span class="sxs-lookup"><span data-stu-id="0bfec-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="0bfec-123">Você se deparar com o andar do usuário usando o **[estágio espacial](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa a origem definida do nível de chão do usuário e o limite de sala opcional, configurado durante a primeira execução.</span><span class="sxs-lookup"><span data-stu-id="0bfec-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="0bfec-124">Para garantir que o Unity esteja operando com seu sistema de coordenadas mundiais no nível de piso, você pode definir e testar se o Unity está usando o tipo de espaço de rastreamento RoomScale:</span><span class="sxs-lookup"><span data-stu-id="0bfec-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

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

* <span data-ttu-id="0bfec-125">Se SetTrackingSpaceType retornar true, o Unity alternará com êxito seu sistema de coordenadas mundiaI para acompanhar o [quadro de referência de estágio](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="0bfec-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="0bfec-126">Se SetTrackingSpaceType retornar false, o Unity não poderá alternar para o quadro de referência de estágio, provavelmente porque o usuário não configurou um andar em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="0bfec-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="0bfec-127">Embora um valor falso de retorno não seja comum, isso pode acontecer se o estágio estiver configurado em uma sala diferente e o dispositivo for movido para o espaço atual sem que o usuário configure um novo estágio.</span><span class="sxs-lookup"><span data-stu-id="0bfec-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="0bfec-128">Depois que o aplicativo definir o tipo de espaço de acompanhamento RoomScale com êxito, o conteúdo colocado no plano y = 0 aparecerá no chão.</span><span class="sxs-lookup"><span data-stu-id="0bfec-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="0bfec-129">A origem em 0, 0, será o local específico no andar em que o usuário se deparava durante a configuração da sala, com-Z representando a direção de encaminhamento que ele estava enfrentando durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="0bfec-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>