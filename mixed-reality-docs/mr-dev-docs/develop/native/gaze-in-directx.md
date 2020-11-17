---
title: Olhar fixo com cabeça e olhos no DirectX
description: Guia do desenvolvedor para usar o Head olhar e o acompanhamento de olho em aplicativos nativos do DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: olho-olhar, cabeça olhar, controle de cabeça, controle ocular, DirectX, entrada, hologramas, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 9ec54f5db33346c499582b54a0b3e36c129bf7ab
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678075"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="7d610-104">Cabeça-olhar e olho-olhar entrada no DirectX</span><span class="sxs-lookup"><span data-stu-id="7d610-104">Head-gaze and eye-gaze input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="7d610-105">Este artigo está relacionado às APIs nativas do WinRT herdadas.</span><span class="sxs-lookup"><span data-stu-id="7d610-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="7d610-106">Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="7d610-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="7d610-107">No Windows Mixed Reality, os olhos e a entrada olhar de cabeça são usados para determinar o que o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="7d610-107">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="7d610-108">Isso pode ser usado para direcionar modelos de entrada primários, como [Head-olhar e commit](../../design/gaze-and-commit.md), e também para fornecer contexto para tipos de interações.</span><span class="sxs-lookup"><span data-stu-id="7d610-108">This can be used to drive primary input models such as [head-gaze and commit](../../design/gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="7d610-109">Há dois tipos de vetores olhar disponíveis por meio da API: Head-olhar e olho-olhar.</span><span class="sxs-lookup"><span data-stu-id="7d610-109">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="7d610-110">Ambos são fornecidos como um raio de três dimensões com uma origem e uma direção.</span><span class="sxs-lookup"><span data-stu-id="7d610-110">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="7d610-111">Os aplicativos podem então raycastr em suas cenas ou no mundo real e determinar o que o usuário está direcionando.</span><span class="sxs-lookup"><span data-stu-id="7d610-111">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="7d610-112">**Head-olhar** representa a direção na qual a cabeça do usuário é apontada.</span><span class="sxs-lookup"><span data-stu-id="7d610-112">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="7d610-113">Considere isso como a posição e direção de encaminhamento do próprio dispositivo, com a posição que representa o ponto central entre as duas exibições.</span><span class="sxs-lookup"><span data-stu-id="7d610-113">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="7d610-114">O Head-olhar está disponível em todos os dispositivos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7d610-114">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="7d610-115">**Olho-olhar** representa a direção que os olhos do usuário estão procurando.</span><span class="sxs-lookup"><span data-stu-id="7d610-115">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="7d610-116">A origem está localizada entre os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="7d610-116">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="7d610-117">Ele está disponível em dispositivos com realidade misturada que incluem um sistema de controle de olho.</span><span class="sxs-lookup"><span data-stu-id="7d610-117">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="7d610-118">Os raios de cabeça e olho-olhar podem ser acessados por meio da API do  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="7d610-118">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="7d610-119">Basta chamar [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose no carimbo de data/hora e no [sistema de coordenadas](coordinate-systems-in-directx.md)especificado.</span><span class="sxs-lookup"><span data-stu-id="7d610-119">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="7d610-120">Este SpatialPointerPose contém uma origem e direção olhar.</span><span class="sxs-lookup"><span data-stu-id="7d610-120">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="7d610-121">Ele também contém uma origem e direção olhar, se o acompanhamento dos olhos estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="7d610-121">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="7d610-122">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="7d610-122">Device support</span></span>
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="7d610-123"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="7d610-123"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="7d610-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7d610-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="7d610-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7d610-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="7d610-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="7d610-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="7d610-127">Foco com a cabeça</span><span class="sxs-lookup"><span data-stu-id="7d610-127">Head-gaze</span></span></td>
     <td><span data-ttu-id="7d610-128">✔️</span><span class="sxs-lookup"><span data-stu-id="7d610-128">✔️</span></span></td>
     <td><span data-ttu-id="7d610-129">✔️</span><span class="sxs-lookup"><span data-stu-id="7d610-129">✔️</span></span></td>
     <td><span data-ttu-id="7d610-130">✔️</span><span class="sxs-lookup"><span data-stu-id="7d610-130">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="7d610-131">Olho-olhar</span><span class="sxs-lookup"><span data-stu-id="7d610-131">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="7d610-132">✔️</span><span class="sxs-lookup"><span data-stu-id="7d610-132">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="7d610-133">Usando Head-olhar</span><span class="sxs-lookup"><span data-stu-id="7d610-133">Using head-gaze</span></span>

<span data-ttu-id="7d610-134">Para acessar o Head-olhar, comece chamando  [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="7d610-134">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="7d610-135">Você precisa passar os parâmetros a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d610-135">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="7d610-136">Um [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa o sistema de coordenadas desejado para o Head-olhar.</span><span class="sxs-lookup"><span data-stu-id="7d610-136">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="7d610-137">Isso é representado pela variável *coordinateSystem* no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d610-137">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="7d610-138">Para obter mais informações, visite nosso guia do desenvolvedor de [sistemas de coordenadas](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="7d610-138">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="7d610-139">Um [carimbo de data/](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) hora que representa o tempo exato necessário para a pose de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="7d610-139">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="7d610-140">Normalmente, você usará um carimbo de data/hora que corresponde ao horário em que o quadro atual será exibido.</span><span class="sxs-lookup"><span data-stu-id="7d610-140">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="7d610-141">Você pode obter esse carimbo de data/hora de exibição previsto de um objeto  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que é acessível por meio do [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)atual.</span><span class="sxs-lookup"><span data-stu-id="7d610-141">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="7d610-142">Esse objeto HolographicFramePrediction é representado pela variável de *previsão* no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d610-142">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="7d610-143">Quando você tiver um SpatialPointerPose válido, a posição de cabeçalho e a direção de encaminhamento serão acessíveis como propriedades.</span><span class="sxs-lookup"><span data-stu-id="7d610-143">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="7d610-144">O código a seguir mostra como acessá-los.</span><span class="sxs-lookup"><span data-stu-id="7d610-144">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="7d610-145">Usando os olhos-olhar</span><span class="sxs-lookup"><span data-stu-id="7d610-145">Using eye-gaze</span></span>

<span data-ttu-id="7d610-146">Observe que, para os usuários usarem a entrada olhar, cada usuário precisa passar por uma [calibragem de usuário com acompanhamento de olho](../../calibration.md) na primeira vez que usar o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d610-146">Please note that for your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](../../calibration.md) the first time they use the device.</span></span> <span data-ttu-id="7d610-147">A API de olho-olhar é muito semelhante à olhar.</span><span class="sxs-lookup"><span data-stu-id="7d610-147">The eye-gaze API is very similar to head-gaze.</span></span>
<span data-ttu-id="7d610-148">Ele usa a mesma API [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , que fornece uma Ray Origin e uma direção que você pode Raycast em sua cena.</span><span class="sxs-lookup"><span data-stu-id="7d610-148">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="7d610-149">A única diferença é que você precisa habilitar explicitamente o controle de olho antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="7d610-149">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="7d610-150">Para isso, você precisa executar duas etapas:</span><span class="sxs-lookup"><span data-stu-id="7d610-150">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="7d610-151">Solicite permissão do usuário para usar o acompanhamento de olho em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7d610-151">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="7d610-152">Habilite a funcionalidade de "entrada olhar" no manifesto do pacote.</span><span class="sxs-lookup"><span data-stu-id="7d610-152">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="7d610-153">Solicitando acesso à entrada de olhar de olho</span><span class="sxs-lookup"><span data-stu-id="7d610-153">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="7d610-154">Quando seu aplicativo estiver sendo inicializado, chame [EyesPose:: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acesso ao controle ocular.</span><span class="sxs-lookup"><span data-stu-id="7d610-154">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="7d610-155">O sistema solicitará o usuário se necessário e retornará [GazeInputAccessStatus:: allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) depois que o acesso tiver sido concedido.</span><span class="sxs-lookup"><span data-stu-id="7d610-155">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="7d610-156">Essa é uma chamada assíncrona, portanto, requer um pouco de gerenciamento extra.</span><span class="sxs-lookup"><span data-stu-id="7d610-156">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="7d610-157">O exemplo a seguir gira um std:: thread desanexado para aguardar o resultado, que ele armazena em uma variável de membro chamada *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="7d610-157">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="7d610-158">Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="7d610-158">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="7d610-159">Como alternativa, você pode usar a nova funcionalidade de [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) com suporte do C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="7d610-159">Alternatively, you could use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="7d610-160">Aqui está outro exemplo para solicitar permissão de usuário:</span><span class="sxs-lookup"><span data-stu-id="7d610-160">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="7d610-161">EyesPose:: IsSupported () permite que o aplicativo dispare a caixa de diálogo de permissão somente se houver um rastreador ocular.</span><span class="sxs-lookup"><span data-stu-id="7d610-161">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="7d610-162">GazeInputAccessStatus m_gazeInputAccessStatus; Isso é para evitar o pop-up do prompt de permissão repetidamente.</span><span class="sxs-lookup"><span data-stu-id="7d610-162">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="7d610-163">Declarando o recurso de *entrada olhar*</span><span class="sxs-lookup"><span data-stu-id="7d610-163">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="7d610-164">Clique duas vezes no arquivo appxmanifest em *Gerenciador de soluções*.</span><span class="sxs-lookup"><span data-stu-id="7d610-164">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="7d610-165">Em seguida, navegue até a seção de *recursos* e verifique o recurso de *entrada olhar* .</span><span class="sxs-lookup"><span data-stu-id="7d610-165">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Funcionalidade de entrada do olhar](images/gaze-input-capability.png)

<span data-ttu-id="7d610-167">Isso adiciona as seguintes linhas à seção *Package* no arquivo appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="7d610-167">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="7d610-168">Obtendo o olhar Ray</span><span class="sxs-lookup"><span data-stu-id="7d610-168">Getting the eye-gaze ray</span></span>
<span data-ttu-id="7d610-169">Depois de ter recebido o acesso ao ET, você fica livre para pegar o olhar Ray a cada quadro.</span><span class="sxs-lookup"><span data-stu-id="7d610-169">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="7d610-170">Assim como acontece com o Head-olhar, obtenha o [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com um carimbo de data/hora desejado e sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="7d610-170">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="7d610-171">O SpatialPointerPose contém um objeto [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) por meio da propriedade [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="7d610-171">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="7d610-172">Isso será não nulo somente se o controle de olho estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="7d610-172">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="7d610-173">A partir daí, você pode verificar se o usuário no dispositivo tem uma calibragem de acompanhamento de olho chamando [EyesPose:: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="7d610-173">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="7d610-174">Em seguida, use a propriedade [olhar](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obter o [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) que contém a posição e a direção dos olhos-olhar.</span><span class="sxs-lookup"><span data-stu-id="7d610-174">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="7d610-175">Às vezes, a propriedade olhar pode ser nula, portanto certifique-se de verificar isso.</span><span class="sxs-lookup"><span data-stu-id="7d610-175">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="7d610-176">Isso pode acontecer se um usuário calibrado fechar temporariamente seus olhos.</span><span class="sxs-lookup"><span data-stu-id="7d610-176">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="7d610-177">O código a seguir mostra como acessar o olhar Ray.</span><span class="sxs-lookup"><span data-stu-id="7d610-177">The following code shows how to access the eye-gaze ray.</span></span>

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

## <a name="fallback-when-eye-tracking-is-not-available"></a><span data-ttu-id="7d610-178">Fallback quando o controle de olho não está disponível</span><span class="sxs-lookup"><span data-stu-id="7d610-178">Fallback when eye tracking is not available</span></span>
<span data-ttu-id="7d610-179">Conforme mencionado em nossos [documentos de design de acompanhamento de olho](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), ambos os designers, bem como os desenvolvedores, devem estar cientes de que pode haver instâncias nas quais os dados de acompanhamento de olho podem não estar disponíveis para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7d610-179">As mentioned in our [eye tracking design docs](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), both designers as well as developers should be aware that there may be instances in which eye tracking data may not be available to your app.</span></span>
<span data-ttu-id="7d610-180">Há vários motivos para isso, desde que um usuário não esteja sendo calibrado, o usuário que negou o acesso do aplicativo aos seus dados de controle de olho ou simplesmente as interferências temporárias (como manchas no visor do HoloLens ou cabelo occluding os olhos do usuário).</span><span class="sxs-lookup"><span data-stu-id="7d610-180">There are various reasons for this ranging from a user not being calibrated, the user having denied the app access to his/her eye tracking data or simply temporary interferences (such as smudges on the HoloLens visor or hair occluding the user's eyes).</span></span> <span data-ttu-id="7d610-181">Embora algumas das APIs já tenham sido mencionadas neste documento, a seguir, fornecemos um resumo de como detectar que o acompanhamento de olho está disponível como uma referência rápida:</span><span class="sxs-lookup"><span data-stu-id="7d610-181">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="7d610-182">Verifique se o sistema dá suporte a acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="7d610-182">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="7d610-183">Chame o seguinte *método*: [Windows. percepção. Peoples. EyesPose. IsSupported ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="7d610-183">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="7d610-184">Verifique se o usuário está calibrado.</span><span class="sxs-lookup"><span data-stu-id="7d610-184">Check that the user is calibrated.</span></span> <span data-ttu-id="7d610-185">Chame a seguinte *Propriedade*: [Windows. percepção. People. EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="7d610-185">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="7d610-186">Verifique se o usuário recebeu a permissão do seu aplicativo para usar seus dados de acompanhamento de olho: recupere o _' GazeInputAccessStatus '_ atual.</span><span class="sxs-lookup"><span data-stu-id="7d610-186">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="7d610-187">Um exemplo de como fazer isso é explicado em [solicitando acesso à entrada olhar](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span><span class="sxs-lookup"><span data-stu-id="7d610-187">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="7d610-188">Além disso, talvez você queira verificar se os dados de acompanhamento de olho não estão obsoletos adicionando um tempo limite entre atualizações de dados de acompanhamento de olho recebido e, caso contrário, fallback para o Head-olhar, conforme discutido abaixo.</span><span class="sxs-lookup"><span data-stu-id="7d610-188">In addition, you may want to check that your eye tracking data is not stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>  
<span data-ttu-id="7d610-189">Visite nossas [considerações de design de fallback](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="7d610-189">Please visit our [fallback design considerations](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="7d610-190">Correlacionando olhar com outras entradas</span><span class="sxs-lookup"><span data-stu-id="7d610-190">Correlating gaze with other inputs</span></span>
<span data-ttu-id="7d610-191">Às vezes, você pode achar que precisa de um [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) que corresponda a um evento no passado.</span><span class="sxs-lookup"><span data-stu-id="7d610-191">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="7d610-192">Por exemplo, se o usuário executar um toque de ar, seu aplicativo poderá querer saber o que ele estava observando.</span><span class="sxs-lookup"><span data-stu-id="7d610-192">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="7d610-193">Para essa finalidade, simplesmente usar [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com o tempo de quadro previsto não seria preciso devido à latência entre o processamento de entrada do sistema e o tempo de exibição.</span><span class="sxs-lookup"><span data-stu-id="7d610-193">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="7d610-194">Além disso, se estiver usando olhar para direcionamento, nossos olhos tendem a se mover até mesmo antes de concluir uma ação de confirmação.</span><span class="sxs-lookup"><span data-stu-id="7d610-194">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="7d610-195">Isso é menos um problema para um toque simples de ar, mas se torna mais crítico ao combinar comandos de voz longos com movimentos de olho rápido.</span><span class="sxs-lookup"><span data-stu-id="7d610-195">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="7d610-196">Uma maneira de lidar com esse cenário é fazer uma chamada adicional para  [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando um carimbo de data/hora histórico que corresponde ao evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="7d610-196">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="7d610-197">No entanto, para entrada que roteiam o SpatialInteractionManager, há um método mais fácil.</span><span class="sxs-lookup"><span data-stu-id="7d610-197">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="7d610-198">O [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tem sua própria função [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="7d610-198">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="7d610-199">Chamar isso fornecerá um [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) perfeitamente correlacionado sem as suposições.</span><span class="sxs-lookup"><span data-stu-id="7d610-199">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="7d610-200">Para saber mais sobre como trabalhar com o SpatialInteractionSourceStates, confira os [controladores de mãos e de movimento na documentação do DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="7d610-200">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="7d610-201">Calibragem</span><span class="sxs-lookup"><span data-stu-id="7d610-201">Calibration</span></span>
<span data-ttu-id="7d610-202">Para que o acompanhamento de olho funcione com precisão, cada usuário precisa passar por uma [calibragem do usuário com acompanhamento de olho](../../calibration.md).</span><span class="sxs-lookup"><span data-stu-id="7d610-202">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](../../calibration.md).</span></span> <span data-ttu-id="7d610-203">Isso permite que o dispositivo ajuste o sistema para uma experiência de exibição de qualidade mais confortável e mais segura para o usuário e para garantir o acompanhamento preciso do controle de olho ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="7d610-203">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="7d610-204">Os desenvolvedores não precisam fazer nada em sua extremidade para gerenciar a calibragem do usuário.</span><span class="sxs-lookup"><span data-stu-id="7d610-204">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="7d610-205">O sistema garantirá que o usuário receba uma solicitação para calibrar o dispositivo nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="7d610-205">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="7d610-206">O usuário está usando o dispositivo pela primeira vez</span><span class="sxs-lookup"><span data-stu-id="7d610-206">The user is using the device for the first time</span></span>
* <span data-ttu-id="7d610-207">O usuário optou anteriormente pelo processo de calibragem</span><span class="sxs-lookup"><span data-stu-id="7d610-207">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="7d610-208">O processo de calibragem não teve sucesso na última vez em que o usuário usou o dispositivo</span><span class="sxs-lookup"><span data-stu-id="7d610-208">The calibration process did not succeed the last time the user used the device</span></span>

<span data-ttu-id="7d610-209">Os desenvolvedores devem certificar-se de fornecer suporte adequado para usuários para os quais os dados de controle de olho podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7d610-209">Developers should make sure to provide adequate support for users for whom eye tracking data may not be available.</span></span> <span data-ttu-id="7d610-210">Saiba mais sobre considerações para soluções de fallback em [acompanhamento de olho no Hololens 2](../../design/eye-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="7d610-210">Learn more about considerations for fallback solutions at [Eye tracking on Hololens 2](../../design/eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="7d610-211">Veja também</span><span class="sxs-lookup"><span data-stu-id="7d610-211">See also</span></span>
* [<span data-ttu-id="7d610-212">Calibragem</span><span class="sxs-lookup"><span data-stu-id="7d610-212">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="7d610-213">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="7d610-213">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="7d610-214">Olho-olhar no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d610-214">Eye-gaze on HoloLens 2</span></span>](../../design/eye-tracking.md)
* [<span data-ttu-id="7d610-215">Olhar e confirmar modelo de entrada</span><span class="sxs-lookup"><span data-stu-id="7d610-215">Gaze and commit input model</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="7d610-216">Controladores de mãos e emovimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="7d610-216">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="7d610-217">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="7d610-217">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
