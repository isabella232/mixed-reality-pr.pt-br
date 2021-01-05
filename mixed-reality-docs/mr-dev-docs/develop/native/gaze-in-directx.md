---
title: Olhar fixo com cabeça e olhos no DirectX
description: Saiba como usar o Head olhar e o acompanhamento de olho em aplicativos nativos do DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: olho-olhar, cabeça olhar, controle de cabeça, controle ocular, DirectX, entrada, hologramas, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 4d7ed9b735b5f3cd7029e42ccc75bc539e3c4f4b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848087"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="3a0b9-104">Cabeça-olhar e olho-olhar entrada no DirectX</span><span class="sxs-lookup"><span data-stu-id="3a0b9-104">Head-gaze and eye-gaze input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="3a0b9-105">Este artigo está relacionado às APIs nativas do WinRT herdadas.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="3a0b9-106">Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="3a0b9-107">No Windows Mixed Reality, os olhos e a entrada olhar de cabeça são usados para determinar o que o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-107">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="3a0b9-108">Você pode usar os dados para direcionar modelos de entrada primários, como [Head-olhar e commit](../../design/gaze-and-commit.md), e fornecer contexto para diferentes tipos de interação.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-108">You can use the data to drive primary input models like [head-gaze and commit](../../design/gaze-and-commit.md), and provide context for different interaction types.</span></span> <span data-ttu-id="3a0b9-109">Há dois tipos de vetores olhar disponíveis por meio da API: Head-olhar e olho-olhar.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-109">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="3a0b9-110">Ambos são fornecidos como um raio tridimensional com uma origem e uma direção.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-110">Both are provided as a three-dimensional ray with an origin and direction.</span></span> <span data-ttu-id="3a0b9-111">Os aplicativos podem então raycastr em suas cenas ou no mundo real e determinar o que o usuário está direcionando.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-111">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="3a0b9-112">**Head-olhar** representa a direção na qual a cabeça do usuário é apontada.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-112">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="3a0b9-113">Imagine olhar como a posição e direção de encaminhamento do próprio dispositivo, com a posição como o ponto central entre as duas exibições.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-113">Think of head-gaze as the position and forward direction of the device itself, with the position as the center point between the two displays.</span></span> <span data-ttu-id="3a0b9-114">O Head-olhar está disponível em todos os dispositivos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-114">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="3a0b9-115">**Olho-olhar** representa a direção que os olhos do usuário estão procurando.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-115">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="3a0b9-116">A origem está localizada entre os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-116">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="3a0b9-117">Ele está disponível em dispositivos com realidade misturada que incluem um sistema de controle de olho.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-117">It's available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="3a0b9-118">Os raios de cabeça e olho-olhar podem ser acessados por meio da API do  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="3a0b9-118">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="3a0b9-119">Chame [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose no [sistema](coordinate-systems-in-directx.md)de carimbo de data e hora especificado.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-119">Call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="3a0b9-120">Este SpatialPointerPose contém uma origem e direção olhar.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-120">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="3a0b9-121">Ele também contém uma origem e direção olhar, se o acompanhamento dos olhos estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-121">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="3a0b9-122">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="3a0b9-122">Device support</span></span>
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="3a0b9-123"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="3a0b9-123"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="3a0b9-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3a0b9-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="3a0b9-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3a0b9-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="3a0b9-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="3a0b9-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="3a0b9-127">Foco com a cabeça</span><span class="sxs-lookup"><span data-stu-id="3a0b9-127">Head-gaze</span></span></td>
     <td><span data-ttu-id="3a0b9-128">✔️</span><span class="sxs-lookup"><span data-stu-id="3a0b9-128">✔️</span></span></td>
     <td><span data-ttu-id="3a0b9-129">✔️</span><span class="sxs-lookup"><span data-stu-id="3a0b9-129">✔️</span></span></td>
     <td><span data-ttu-id="3a0b9-130">✔️</span><span class="sxs-lookup"><span data-stu-id="3a0b9-130">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="3a0b9-131">Olho-olhar</span><span class="sxs-lookup"><span data-stu-id="3a0b9-131">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="3a0b9-132">✔️</span><span class="sxs-lookup"><span data-stu-id="3a0b9-132">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="3a0b9-133">Usando Head-olhar</span><span class="sxs-lookup"><span data-stu-id="3a0b9-133">Using head-gaze</span></span>

<span data-ttu-id="3a0b9-134">Para acessar o Head-olhar, comece chamando  [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-134">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="3a0b9-135">Passe os parâmetros a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-135">Pass the following parameters.</span></span>
 - <span data-ttu-id="3a0b9-136">Um [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa o sistema de coordenadas que você deseja para o olhar.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-136">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the coordinate system you want for the head-gaze.</span></span> <span data-ttu-id="3a0b9-137">Isso é representado pela variável *coordinateSystem* no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-137">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="3a0b9-138">Para obter mais informações, visite nosso guia do desenvolvedor de [sistemas de coordenadas](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="3a0b9-138">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="3a0b9-139">Um [carimbo de data/](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) hora que representa o tempo exato necessário para a pose de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-139">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="3a0b9-140">Normalmente, você usará um carimbo de data/hora que corresponde ao horário em que o quadro atual será exibido.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-140">Typically, you'll use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="3a0b9-141">Você pode obter esse carimbo de data/hora de exibição previsto de um objeto  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que é acessível por meio do [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)atual.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-141">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="3a0b9-142">Esse objeto HolographicFramePrediction é representado pela variável de *previsão* no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-142">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="3a0b9-143">Quando você tiver um SpatialPointerPose válido, a posição de cabeçalho e a direção de encaminhamento serão acessíveis como propriedades.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-143">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="3a0b9-144">O código a seguir mostra como acessá-los.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-144">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="3a0b9-145">Usando os olhos-olhar</span><span class="sxs-lookup"><span data-stu-id="3a0b9-145">Using eye-gaze</span></span>

<span data-ttu-id="3a0b9-146">Para que os usuários usem a entrada olhar, cada usuário precisa passar por uma [calibragem de usuário com acompanhamento de olho](../../calibration.md) na primeira vez que usar o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-146">For your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](../../calibration.md) the first time they use the device.</span></span> <span data-ttu-id="3a0b9-147">A API de olho-olhar é semelhante ao olhar.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-147">The eye-gaze API is similar to head-gaze.</span></span>
<span data-ttu-id="3a0b9-148">Ele usa a mesma API [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , que fornece uma Ray Origin e uma direção que você pode Raycast em sua cena.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-148">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="3a0b9-149">A única diferença é que você precisa habilitar explicitamente o controle de olho antes de usá-lo:</span><span class="sxs-lookup"><span data-stu-id="3a0b9-149">The only difference is that you need to explicitly enable eye tracking before using it:</span></span>
1. <span data-ttu-id="3a0b9-150">Solicite permissão do usuário para usar o acompanhamento de olho em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-150">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="3a0b9-151">Habilite a funcionalidade de "entrada olhar" no manifesto do pacote.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-151">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="3a0b9-152">Solicitando acesso à entrada de olhar de olho</span><span class="sxs-lookup"><span data-stu-id="3a0b9-152">Requesting access to eye-gaze input</span></span>

<span data-ttu-id="3a0b9-153">Quando seu aplicativo estiver sendo inicializado, chame [EyesPose:: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acesso ao controle ocular.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-153">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="3a0b9-154">O sistema solicitará o usuário se necessário e retornará [GazeInputAccessStatus:: allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) depois que o acesso tiver sido concedido.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-154">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="3a0b9-155">Essa é uma chamada assíncrona, portanto, requer um pouco de gerenciamento extra.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-155">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="3a0b9-156">O exemplo a seguir gira um std:: thread desanexado para aguardar o resultado, que ele armazena em uma variável de membro chamada *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-156">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="3a0b9-157">Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-157">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="3a0b9-158">Você também pode usar a nova funcionalidade [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) com suporte do C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-158">You could also use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="3a0b9-159">Aqui está outro exemplo para solicitar permissão de usuário:</span><span class="sxs-lookup"><span data-stu-id="3a0b9-159">Here's another example for asking for user permission:</span></span>
-   <span data-ttu-id="3a0b9-160">EyesPose:: IsSupported () permite que o aplicativo dispare a caixa de diálogo de permissão somente se houver um rastreador ocular.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-160">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there's an eye tracker.</span></span>
-   <span data-ttu-id="3a0b9-161">GazeInputAccessStatus m_gazeInputAccessStatus; Isso é para evitar o pop-up do prompt de permissão repetidamente.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-161">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="3a0b9-162">Declarando o recurso de *entrada olhar*</span><span class="sxs-lookup"><span data-stu-id="3a0b9-162">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="3a0b9-163">Clique duas vezes no arquivo appxmanifest em *Gerenciador de soluções*.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-163">Double-click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="3a0b9-164">Em seguida, navegue até a seção de *recursos* e verifique o recurso de *entrada olhar* .</span><span class="sxs-lookup"><span data-stu-id="3a0b9-164">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Funcionalidade de entrada do olhar](images/gaze-input-capability.png)

<span data-ttu-id="3a0b9-166">Isso adiciona as seguintes linhas à seção *Package* no arquivo appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="3a0b9-166">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="3a0b9-167">Obtendo o olhar Ray</span><span class="sxs-lookup"><span data-stu-id="3a0b9-167">Getting the eye-gaze ray</span></span>

<span data-ttu-id="3a0b9-168">Depois de ter recebido o acesso ao ET, você fica livre para pegar o olhar Ray a cada quadro.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-168">Once you have received access to ET, you're free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="3a0b9-169">Como com o Head-olhar, obtenha o [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com um carimbo de data/hora desejado e sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-169">As with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="3a0b9-170">O SpatialPointerPose contém um objeto [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) por meio da propriedade [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="3a0b9-170">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="3a0b9-171">Isso será não nulo somente se o controle de olho estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-171">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="3a0b9-172">A partir daí, você pode verificar se o usuário no dispositivo tem uma calibragem de acompanhamento de olho chamando [EyesPose:: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="3a0b9-172">From there, you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="3a0b9-173">Em seguida, use a propriedade [olhar](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obter o [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) que contém a posição e a direção do olhar de olho.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-173">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="3a0b9-174">Às vezes, a propriedade olhar pode ser nula, portanto certifique-se de verificar isso.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-174">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="3a0b9-175">Isso pode acontecer se um usuário calibrado fechar temporariamente seus olhos.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-175">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="3a0b9-176">O código a seguir mostra como acessar o olhar Ray.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-176">The following code shows how to access the eye-gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a><span data-ttu-id="3a0b9-177">Fallback quando o controle de olho não está disponível</span><span class="sxs-lookup"><span data-stu-id="3a0b9-177">Fallback when eye tracking isn't available</span></span>

<span data-ttu-id="3a0b9-178">Conforme mencionado em nossos [documentos de design de acompanhamento de olho](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), os designers e desenvolvedores devem estar cientes das instâncias em que os dados de controle de olho podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-178">As mentioned in our [eye tracking design docs](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), both designers and developers should be aware of instances where eye tracking data may not be available.</span></span>

<span data-ttu-id="3a0b9-179">Há várias razões para os dados estarem indisponíveis:</span><span class="sxs-lookup"><span data-stu-id="3a0b9-179">There are various reasons for data being unavailable:</span></span>
* <span data-ttu-id="3a0b9-180">Um usuário não está sendo calibrado</span><span class="sxs-lookup"><span data-stu-id="3a0b9-180">A user not being calibrated</span></span>
* <span data-ttu-id="3a0b9-181">Um usuário negou o acesso do aplicativo aos seus dados de controle de olho</span><span class="sxs-lookup"><span data-stu-id="3a0b9-181">A user has denied the app access to his/her eye tracking data</span></span>
* <span data-ttu-id="3a0b9-182">As interferências temporárias, como manchas no visor do HoloLens ou cabelo occluding os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-182">Temporary interferences, such as smudges on the HoloLens visor or hair occluding the user's eyes.</span></span> 

<span data-ttu-id="3a0b9-183">Embora algumas das APIs já tenham sido mencionadas neste documento, a seguir, fornecemos um resumo de como detectar que o acompanhamento de olho está disponível como uma referência rápida:</span><span class="sxs-lookup"><span data-stu-id="3a0b9-183">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="3a0b9-184">Verifique se o sistema dá suporte a acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-184">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="3a0b9-185">Chame o seguinte *método*: [Windows. percepção. Peoples. EyesPose. IsSupported ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="3a0b9-185">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="3a0b9-186">Verifique se o usuário está calibrado.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-186">Check that the user is calibrated.</span></span> <span data-ttu-id="3a0b9-187">Chame a seguinte *Propriedade*: [Windows. percepção. People. EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="3a0b9-187">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="3a0b9-188">Verifique se o usuário recebeu a permissão do seu aplicativo para usar seus dados de acompanhamento de olho: recupere o _' GazeInputAccessStatus '_ atual.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-188">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="3a0b9-189">Um exemplo de como fazer isso é explicado em [solicitando acesso à entrada olhar](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span><span class="sxs-lookup"><span data-stu-id="3a0b9-189">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="3a0b9-190">Você também pode querer verificar se os dados de controle de olho não estão obsoletos adicionando um tempo limite entre atualizações de dados de acompanhamento de olho recebido e, de outra forma, fallback para o Head-olhar, conforme discutido abaixo.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-190">You may also want to check that your eye tracking data isn't stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>   
<span data-ttu-id="3a0b9-191">Visite nossas [considerações de design de fallback](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-191">Visit our [fallback design considerations](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="3a0b9-192">Correlacionando olhar com outras entradas</span><span class="sxs-lookup"><span data-stu-id="3a0b9-192">Correlating gaze with other inputs</span></span>

<span data-ttu-id="3a0b9-193">Às vezes, você pode achar que precisa de um [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) que corresponda a um evento no passado.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-193">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="3a0b9-194">Por exemplo, se o usuário fizer um toque de ar, seu aplicativo poderá querer saber o que ele estava observando.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-194">For example, if the user does an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="3a0b9-195">Para essa finalidade, simplesmente usar [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com o tempo de quadro previsto não seria preciso devido à latência entre o processamento de entrada do sistema e o tempo de exibição.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-195">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="3a0b9-196">Além disso, se estiver usando olhar de olho para direcionamento, nossos olhos tendem a se mover até mesmo antes de concluir uma ação de confirmação.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-196">Also, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="3a0b9-197">Isso é menos um problema para um toque simples de ar, mas se torna mais crítico ao combinar comandos de voz longos com movimentos de olho rápido.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-197">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="3a0b9-198">Uma maneira de lidar com esse cenário é fazer uma chamada adicional para  [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando um carimbo de data/hora histórico que corresponde ao evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-198">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="3a0b9-199">No entanto, para entrada que roteiam o SpatialInteractionManager, há um método mais fácil.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-199">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="3a0b9-200">O [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tem sua própria função [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="3a0b9-200">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="3a0b9-201">Chamar isso fornecerá um [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) perfeitamente correlacionado sem as suposições.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-201">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="3a0b9-202">Para saber mais sobre como trabalhar com o SpatialInteractionSourceStates, confira os [controladores de mãos e de movimento na documentação do DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="3a0b9-202">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="3a0b9-203">Calibragem</span><span class="sxs-lookup"><span data-stu-id="3a0b9-203">Calibration</span></span>

<span data-ttu-id="3a0b9-204">Para que o acompanhamento de olho funcione com precisão, cada usuário precisa passar por uma [calibragem do usuário com acompanhamento de olho](../../calibration.md).</span><span class="sxs-lookup"><span data-stu-id="3a0b9-204">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](../../calibration.md).</span></span> <span data-ttu-id="3a0b9-205">Isso permite que o dispositivo ajuste o sistema para uma experiência de exibição de qualidade mais confortável e mais segura para o usuário e para garantir o acompanhamento preciso do controle de olho ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-205">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="3a0b9-206">Os desenvolvedores não precisam fazer nada em sua extremidade para gerenciar a calibragem do usuário.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-206">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="3a0b9-207">O sistema garantirá que o usuário receba uma solicitação para calibrar o dispositivo nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="3a0b9-207">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="3a0b9-208">O usuário está usando o dispositivo pela primeira vez</span><span class="sxs-lookup"><span data-stu-id="3a0b9-208">The user is using the device for the first time</span></span>
* <span data-ttu-id="3a0b9-209">O usuário optou anteriormente pelo processo de calibragem</span><span class="sxs-lookup"><span data-stu-id="3a0b9-209">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="3a0b9-210">O processo de calibragem não teve sucesso na última vez em que o usuário usava o dispositivo</span><span class="sxs-lookup"><span data-stu-id="3a0b9-210">The calibration process didn't succeed the last time the user used the device</span></span>

<span data-ttu-id="3a0b9-211">Os desenvolvedores devem certificar-se de fornecer suporte adequado para usuários onde os dados de acompanhamento de olho podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3a0b9-211">Developers should make sure to provide adequate support for users where eye tracking data may not be available.</span></span> <span data-ttu-id="3a0b9-212">Saiba mais sobre considerações para soluções de fallback em [acompanhamento de olho no HoloLens 2](../../design/eye-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="3a0b9-212">Learn more about considerations for fallback solutions at [Eye tracking on HoloLens 2](../../design/eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="3a0b9-213">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a0b9-213">See also</span></span>

* [<span data-ttu-id="3a0b9-214">Calibragem</span><span class="sxs-lookup"><span data-stu-id="3a0b9-214">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="3a0b9-215">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="3a0b9-215">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="3a0b9-216">Olho-olhar no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3a0b9-216">Eye-gaze on HoloLens 2</span></span>](../../design/eye-tracking.md)
* [<span data-ttu-id="3a0b9-217">Olhar e confirmar modelo de entrada</span><span class="sxs-lookup"><span data-stu-id="3a0b9-217">Gaze and commit input model</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="3a0b9-218">Controladores de mãos e emovimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="3a0b9-218">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="3a0b9-219">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="3a0b9-219">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
