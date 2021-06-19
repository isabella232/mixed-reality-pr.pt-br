---
title: Acompanhamento de código QR
description: Saiba como detectar códigos QR, adicionar funcionalidades de webcam e gerenciar sistemas de coordenadas em aplicativos de realidade misturada no HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr, lbe, entretenimento baseado em localização, vr, vr, imersivo, qr, qr code, hololens2
ms.openlocfilehash: 9d3a5d9696fbf875b2e6a890ed837efc055a9e6e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394330"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="04192-104">Acompanhamento de código QR</span><span class="sxs-lookup"><span data-stu-id="04192-104">QR code tracking</span></span>

<span data-ttu-id="04192-105">O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código.</span><span class="sxs-lookup"><span data-stu-id="04192-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="04192-106">Depois de habilitar a webcam do dispositivo, você poderá reconhecer códigos QR nas versões mais recentes de seus projetos do Unreal ou do Unity.</span><span class="sxs-lookup"><span data-stu-id="04192-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="04192-107">Antes de ir para produção, recomendamos seguir [as práticas](#best-practices-for-qr-code-detection) recomendadas que estabelecemos no final do artigo.</span><span class="sxs-lookup"><span data-stu-id="04192-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="04192-108">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="04192-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="04192-109">Recurso</span><span class="sxs-lookup"><span data-stu-id="04192-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="04192-110"><a href="/hololens/hololens1-hardware">HoloLens (primeira geração)</a></span><span class="sxs-lookup"><span data-stu-id="04192-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="04192-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="04192-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="04192-112"><a href="../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="04192-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="04192-113">Detecção de código QR</span><span class="sxs-lookup"><span data-stu-id="04192-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="04192-114">️</span><span class="sxs-lookup"><span data-stu-id="04192-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="04192-115">✔️</span><span class="sxs-lookup"><span data-stu-id="04192-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="04192-116">✔️</span><span class="sxs-lookup"><span data-stu-id="04192-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="04192-117">O acompanhamento de código QR com headsets Windows Mixed Reality imersivos em computadores desktop tem suporte Windows 10 versão 2004 e superior.</span><span class="sxs-lookup"><span data-stu-id="04192-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="04192-118">Use a API Microsoft.MixedReality.QRCodeWatcher.IsSupported() para determinar se o recurso tem suporte no dispositivo atual.</span><span class="sxs-lookup"><span data-stu-id="04192-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="04192-119">Obter o pacote QR</span><span class="sxs-lookup"><span data-stu-id="04192-119">Getting the QR package</span></span>

<span data-ttu-id="04192-120">Você pode baixar o pacote NuGet para detecção de código QR [aqui](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span><span class="sxs-lookup"><span data-stu-id="04192-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="using-openxr"></a><span data-ttu-id="04192-121">Usando OpenXR</span><span class="sxs-lookup"><span data-stu-id="04192-121">Using OpenXR</span></span>

<span data-ttu-id="04192-122">Ao usar o plug-in OpenXR, pegue o da [ `SpatialGraphNodeId` API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e use a `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API para localizar o código QR.</span><span class="sxs-lookup"><span data-stu-id="04192-122">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="04192-123">Para referência, temos um projeto de exemplo de acompanhamento de [QR no GitHub](https://github.com/yl-msft/QRTracking) com uma explicação de uso mais detalhada para a [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span><span class="sxs-lookup"><span data-stu-id="04192-123">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="04192-124">Detectando códigos QR</span><span class="sxs-lookup"><span data-stu-id="04192-124">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="04192-125">Adicionando a funcionalidade de webcam</span><span class="sxs-lookup"><span data-stu-id="04192-125">Adding the webcam capability</span></span>

<span data-ttu-id="04192-126">Você precisará adicionar a funcionalidade ao manifesto para `webcam` detectar códigos QR.</span><span class="sxs-lookup"><span data-stu-id="04192-126">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="04192-127">Essa funcionalidade é necessária, pois os dados dentro dos códigos detectados no ambiente do usuário podem conter informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="04192-127">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="04192-128">A permissão pode ser solicitada chamando `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="04192-128">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="04192-129">_C#:_</span><span class="sxs-lookup"><span data-stu-id="04192-129">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="04192-130">_C++:_</span><span class="sxs-lookup"><span data-stu-id="04192-130">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="04192-131">A permissão deve ser solicitada antes de você construir um objeto QRCodeWatcher.</span><span class="sxs-lookup"><span data-stu-id="04192-131">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="04192-132">Embora a detecção de código QR `webcam` exija a funcionalidade, a detecção ocorre usando as câmeras de acompanhamento do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="04192-132">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="04192-133">Isso fornece uma FOV de detecção mais ampla e uma melhor vida útil da bateria em comparação com a detecção com a câmera de foto/vídeo (PV) do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="04192-133">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="04192-134">Detectando códigos QR no Unity</span><span class="sxs-lookup"><span data-stu-id="04192-134">Detecting QR codes in Unity</span></span>

<span data-ttu-id="04192-135">Você pode usar a API de detecção de código QR no Unity sem importar o MRTK instalando o pacote NuGet usando [o NuGet para Unity.](https://github.com/GlitchEnzo/NuGetForUnity)</span><span class="sxs-lookup"><span data-stu-id="04192-135">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="04192-136">Se você quiser ter uma sensação de como ele funciona, baixe o aplicativo [unity de exemplo](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span><span class="sxs-lookup"><span data-stu-id="04192-136">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="04192-137">O aplicativo de exemplo tem exemplos para exibir um quadrado holográfico sobre códigos QR e dados associados, como GUID, tamanho físico, data/hora e dados decodificados.</span><span class="sxs-lookup"><span data-stu-id="04192-137">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="04192-138">Detectando códigos QR em C++</span><span class="sxs-lookup"><span data-stu-id="04192-138">Detecting QR codes in C++</span></span>

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="04192-139">Obter o sistema de coordenadas para um código QR</span><span class="sxs-lookup"><span data-stu-id="04192-139">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="04192-140">Cada código QR detectado [](../../design/coordinate-systems.md) expõe um sistema de coordenadas espaciais alinhado com o código QR no canto superior esquerdo do quadrado de detecção rápida no canto superior esquerdo:</span><span class="sxs-lookup"><span data-stu-id="04192-140">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="04192-142">Ao usar diretamente o SDK do QR, o eixo Z está apontando para o papel (não mostrado) – quando convertido em coordenadas do Unity, o eixo Z aponta para fora do papel e é de esquerda.</span><span class="sxs-lookup"><span data-stu-id="04192-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="04192-143">SpatialCoordinateSystem de um código QR se alinha conforme mostrado.</span><span class="sxs-lookup"><span data-stu-id="04192-143">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="04192-144">Você pode obter o sistema de coordenadas da plataforma chamando <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode e</a> passando SpatialGraphNodeId do código.</span><span class="sxs-lookup"><span data-stu-id="04192-144">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="04192-145">O código C++ abaixo mostra como criar um retângulo e º-lo usando o sistema de coordenadas do código QR:</span><span class="sxs-lookup"><span data-stu-id="04192-145">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="04192-146">Você pode usar o tamanho físico para criar o retângulo QR:</span><span class="sxs-lookup"><span data-stu-id="04192-146">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="04192-147">O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas ao local:</span><span class="sxs-lookup"><span data-stu-id="04192-147">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="04192-148">No total, *seu QRCodeAddedHandler* pode ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="04192-148">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="04192-149">Práticas recomendadas para detecção de código QR</span><span class="sxs-lookup"><span data-stu-id="04192-149">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="04192-150">Zonas silenciosas em torno de códigos QR</span><span class="sxs-lookup"><span data-stu-id="04192-150">Quiet zones around QR Codes</span></span>

<span data-ttu-id="04192-151">Para serem lidos corretamente, os códigos QR exigem uma margem em todos os lados do código.</span><span class="sxs-lookup"><span data-stu-id="04192-151">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="04192-152">Essa margem não deve conter nenhum conteúdo impresso e deve ter quatro módulos (um único quadrado preto no código) de largura.</span><span class="sxs-lookup"><span data-stu-id="04192-152">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="04192-153">A [especificação QR](https://www.qrcode.com/en/howto/code.html) contém mais informações sobre zonas silenciosas.</span><span class="sxs-lookup"><span data-stu-id="04192-153">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="04192-154">Iluminação e pano de fundo</span><span class="sxs-lookup"><span data-stu-id="04192-154">Lighting and backdrop</span></span>
<span data-ttu-id="04192-155">A qualidade da detecção de código QR é suscetível a variações de iluminação e de pano de fundo.</span><span class="sxs-lookup"><span data-stu-id="04192-155">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="04192-156">Em uma cena com iluminação brilhante, imprima um código preto em uma tela de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="04192-156">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="04192-157">Caso contrário, imprima um código QR preto em uma tela de fundo branca.</span><span class="sxs-lookup"><span data-stu-id="04192-157">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="04192-158">Se o pano de fundo para o código estiver escuro, tente um código preto em cinza se a taxa de detecção for baixa.</span><span class="sxs-lookup"><span data-stu-id="04192-158">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="04192-159">Se o pano de fundo for relativamente claro, um código regular deverá funcionar bem.</span><span class="sxs-lookup"><span data-stu-id="04192-159">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="04192-160">Tamanho dos códigos QR</span><span class="sxs-lookup"><span data-stu-id="04192-160">Size of QR codes</span></span>
<span data-ttu-id="04192-161">Windows Mixed Reality dispositivos não funcionam com códigos QR com lados menores que 5 cm cada.</span><span class="sxs-lookup"><span data-stu-id="04192-161">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="04192-162">Para códigos QR entre os lados de comprimento de 5 cm e 10 cm, você deve estar bem próximo para detectar o código.</span><span class="sxs-lookup"><span data-stu-id="04192-162">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="04192-163">Também levará mais tempo para detectar códigos nesse tamanho.</span><span class="sxs-lookup"><span data-stu-id="04192-163">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="04192-164">O tempo exato para detectar códigos depende não apenas do tamanho dos códigos QR, mas da distância do código.</span><span class="sxs-lookup"><span data-stu-id="04192-164">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="04192-165">Aproximar-se do código ajudará a deslocar problemas com o tamanho.</span><span class="sxs-lookup"><span data-stu-id="04192-165">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="04192-166">Distância e posição angular do código QR</span><span class="sxs-lookup"><span data-stu-id="04192-166">Distance and angular position from the QR code</span></span>
<span data-ttu-id="04192-167">As câmeras de acompanhamento só podem detectar um determinado nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="04192-167">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="04192-168">Para códigos pequenos – < 10 cm ao longo dos lados – você deve estar bastante próximo.</span><span class="sxs-lookup"><span data-stu-id="04192-168">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="04192-169">Para um código QR versão 1 variando de 10 cm a 25 cm de largura, a distância mínima de detecção varia de 0,15 metros a 0,5 metros.</span><span class="sxs-lookup"><span data-stu-id="04192-169">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="04192-170">A distância de detecção para tamanho aumenta linearmente, mas também depende da versão de QR ou do tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="04192-170">The detection distance for size increases linearly, but also depends on QR version or module size.</span></span> <span data-ttu-id="04192-171">Quanto maior a versão, menor será o número de módulos, que só podem ser detectados de uma posição mais próxima.</span><span class="sxs-lookup"><span data-stu-id="04192-171">The higher the version, the smaller the modules, which can only be detected from a closer position.</span></span> <span data-ttu-id="04192-172">Você também pode experimentar códigos QR micro se quiser que a distância da detecção seja mais longa.</span><span class="sxs-lookup"><span data-stu-id="04192-172">You can also try micro QR codes if you want the distance of detection to be longer.</span></span> <span data-ttu-id="04192-173">A detecção de QR funciona com uma variedade de ângulos += 45 deg para garantir que temos a resolução adequada para detectar o código.</span><span class="sxs-lookup"><span data-stu-id="04192-173">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04192-174">Sempre certifique-se de que você tenha contraste suficiente e uma borda adequada.</span><span class="sxs-lookup"><span data-stu-id="04192-174">Always make sure you have enough contrast and a proper border.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="04192-175">Códigos QR com logotipos</span><span class="sxs-lookup"><span data-stu-id="04192-175">QR codes with logos</span></span>
<span data-ttu-id="04192-176">Códigos QR com logotipos não foram testados e não têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="04192-176">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="04192-177">Gerenciando dados de código QR</span><span class="sxs-lookup"><span data-stu-id="04192-177">Managing QR code data</span></span>
<span data-ttu-id="04192-178">Windows Mixed Reality dispositivos detectam códigos QR no nível do sistema no driver.</span><span class="sxs-lookup"><span data-stu-id="04192-178">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="04192-179">Quando o dispositivo é reinicializado, os códigos QR detectados se foram e serão reprojetados como novos objetos na próxima vez.</span><span class="sxs-lookup"><span data-stu-id="04192-179">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="04192-180">É recomendável configurar seu aplicativo para ignorar códigos QR mais antigos do que um data/hora específico.</span><span class="sxs-lookup"><span data-stu-id="04192-180">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="04192-181">Atualmente, a API não dá suporte à limpeza do histórico de código QR.</span><span class="sxs-lookup"><span data-stu-id="04192-181">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="04192-182">Posicionamento de código QR em um espaço</span><span class="sxs-lookup"><span data-stu-id="04192-182">QR code placement in a space</span></span>
<span data-ttu-id="04192-183">Para recomendações sobre onde e como colocar códigos QR, consulte [Considerações de ambiente para o HoloLens.](/hololens/hololens-environment-considerations)</span><span class="sxs-lookup"><span data-stu-id="04192-183">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="04192-184">Referência da API QR</span><span class="sxs-lookup"><span data-stu-id="04192-184">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="04192-185">Confira também</span><span class="sxs-lookup"><span data-stu-id="04192-185">See also</span></span>
* [<span data-ttu-id="04192-186">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="04192-186">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="04192-187"><a href="/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="04192-187"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>