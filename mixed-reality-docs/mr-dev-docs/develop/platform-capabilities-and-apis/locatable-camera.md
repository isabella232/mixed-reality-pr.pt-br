---
title: Câmera localizável
description: Informações gerais sobre o HoloLens câmera frontal, como ela funciona e os perfis e resoluções disponíveis para desenvolvedores.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: camera, hololens, color camera, front-facing, hololens 2, cv, computer vision, fiducial, markers, qr code, qr, photo, video
ms.openlocfilehash: 33faa4107c6b44041958f422329d8967958a666606a474949184628abcd12544
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217092"
---
# <a name="locatable-camera"></a>Câmera localizável

HoloLens inclui uma câmera voltada para o mundo montada na frente do dispositivo, o que permite que os aplicativos vejam o que o usuário vê. Os desenvolvedores têm acesso e controle da câmera, assim como faria para câmeras coloridas em smartphones, portáteis ou áreas de trabalho. A mesma captura de mídia universal do Windows [e](/uwp/api/Windows.Media.Capture.MediaCapture) APIs do Windows Media Foundation que funcionam em dispositivos móveis e desktop funcionam em HoloLens. O Unity [empacotou essas APIs do Windows](../unity/locatable-camera-in-unity.md) para abstrair os recursos de uso da câmera HoloLens. As tarefas de recurso incluem tirar fotos e vídeos regulares (com ou sem hologramas) e localizar a posição e a perspectiva da câmera na cena.

## <a name="device-camera-information"></a>Informações da câmera do dispositivo

### <a name="hololens-first-generation"></a>HoloLens (primeira geração)

* Corrigida a câmera de foto/vídeo (PV) de foco com o balanceamento automático de branco, a exposição automática e o pipeline de processamento de imagem completo.
* O LED de privacidade branco voltado para o mundo será a luz sempre que a câmera estiver ativa
* A câmera dá suporte aos seguintes modos (todos os modos têm proporção de 16:9) a 30, 24, 20, 15 e 5 fps:

  |  Vídeo  |  Versão Prévia  |  Ainda  |  Campo de exibição horizontal (H-FOV) |  Uso sugerido | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45 deg  |  (modo padrão com estabilização de vídeo) | 
  |  N/D |  N/D |  2048x1152 |  67 deg |  Imagem ainda de resolução mais alta | 
  |  1408x792 |  1408x792 |  1408x792 |  48 deg |  Resolução overscan (preenchimento) antes da estabilização do vídeo | 
  |  1344x756 |  1344x756 |  1344x756 |  67 deg |  Modo de vídeo FOV grande com varredura em excesso | 
  |  896x504 |  896x504 |  896x504 |  48 deg |  Modo de baixa potência/baixa resolução para tarefas de processamento de imagem | 

### <a name="hololens-2"></a>HoloLens 2

* Câmera PV (foto/vídeo de foco automático) com balanceamento automático de branco, exposição automática e pipeline de processamento de imagem completo.
* O LED de privacidade branco voltado para o mundo será a luz sempre que a câmera estiver ativa.
* HoloLens 2 dá suporte a perfis de câmera diferentes. Saiba como descobrir [e selecionar recursos de câmera.](/windows/uwp/audio-video-camera/camera-profiles)
* A câmera dá suporte aos seguintes perfis e resoluções (todos os modos de vídeo têm proporção de 16:9):
  
  | Perfil                                         | Vídeo     | Versão Prévia   | Ainda     | Taxas de quadros | Campo de exibição horizontal (H-FOV) | Uso sugerido                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0 BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15.30       | 64.69                            | Gravação de vídeo de alta qualidade                |
  | Legacy,0 BalancedVideoAndPhoto,100             | 896x504   | 896x504   |           | 15.30       | 64.69                            | Fluxo de visualização para captura de fotos de alta qualidade |
  | Legacy,0 BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | Captura de fotos de alta qualidade                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15.30       | 64.69                            | Cenários de duração longa                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15.30       | 64.69                            | Cenários de duração longa                     |
  | VideoConferencing,100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferência,100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1280 x 720  | 1280 x 720  | 1280 x 720  | 15,30       | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1128x636  |           |           | 15,30       | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 960 x 540   |           |           | 15,30       | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 760x428   |           |           | 15,30       | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 640 x 360   |           |           | 15,30       | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 500 x 282   |           |           | 15,30       | 64.69                            | Videoconferência, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 424x240   |           |           | 15,30       | 64.69                            | Videoconferência, cenários de longa duração |

> [!NOTE]
> Os clientes podem aproveitar [a captura de realidade](/hololens/holographic-photos-and-videos) misturada para tirar vídeos ou fotos do seu aplicativo, que incluem hologramas e estabilização de vídeo.
>
>Como desenvolvedor, há considerações que você deve levar em conta ao criar seu aplicativo se quiser que ele pareça o melhor possível quando um cliente captura conteúdo. Você também pode habilitar (e personalizar) a captura de realidade misturada diretamente em seu aplicativo. Saiba mais em Captura [de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Localizando a câmera do dispositivo no mundo

Quando HoloLens tira fotos e vídeos, os quadros capturados incluem a localização da câmera no mundo e o modelo de lente da câmera. Isso permite que os aplicativos lógicos sobre a posição da câmera no mundo real para cenários de imagens aumentadas. Os desenvolvedores podem lançar seus próprios cenários de forma criativo usando seu processamento de imagem favorito ou bibliotecas de visão computacional personalizadas.

"Câmera" em outro lugar HoloLens documentação pode se referir à "câmera do jogo virtual" (a que o aplicativo renderiza). A menos que seja anotado de outra forma, a "câmera" nesta página refere-se à câmera de cores RGB do mundo real.

### <a name="using-unity"></a>Usando o Unity

Para ir dos 'CameraIntrinsics' e 'CameraCoordinateSystem' para o sistema de coordenadas do aplicativo/mundo, siga as instruções no artigo Câmera locacionável no [Unity.](../unity/locatable-camera-in-unity.md)  CameraToWorldMatrix é fornecido automaticamente pela classe PhotoCaptureFrame e, portanto, você não precisa se preocupar com as transformação CameraCoordinateSystem discutidas abaixo.

### <a name="using-mediaframereference"></a>Usando MediaFrameReference

Essas instruções se aplicam se você estiver usando a [classe MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) para ler quadros de imagem da câmera.

Cada quadro de imagem (seja foto ou vídeo) inclui um [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) com raiz na câmera no momento da captura, que pode ser acessado usando a propriedade [CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) de [seu MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Cada quadro contém uma descrição do modelo de lente da câmera, que pode ser encontrada na propriedade [CameraIntrinsics.](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) Juntas, essas transformação definem para cada pixel um raio no espaço 3D que representa o caminho feito pelos fótons que produziram o pixel. Esses raios podem estar relacionados [a](../../design/coordinate-systems.md#stationary-frame-of-reference)outro conteúdo no aplicativo obtendo a transformação do sistema de coordenadas do quadro para algum outro sistema de coordenadas (por exemplo, de um quadro de referência estacionário). 

Cada quadro de imagem fornece o seguinte:
* Dados de pixel (no formato RGB/NV12/JPEG/etc.)
* Um [SpatialCoordinateSystem do](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) local da captura
* Uma [classe CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) que contém o modo de lente da câmera

O [exemplo HolographicFaceTracking](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) mostra a maneira bastante simples de consultar a transformação entre o sistema de coordenadas da câmera e seus próprios sistemas de coordenadas de aplicativo.

### <a name="using-media-foundation"></a>Usando Media Foundation

Se você estiver usando o Media Foundation diretamente para ler quadros de imagem da câmera, poderá usar o atributo [MFSampleExtension_CameraExtrinsics](/windows/win32/medfound/mfsampleextension-cameraextrinsics) e o atributo MFSampleExtension_PinholeCameraIntrinsics de cada quadro para localizar quadros da câmera em relação [aos](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) outros sistemas de coordenadas do aplicativo, conforme mostrado neste código de exemplo:

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>Erro de distorção

No HoloLens, os fluxos de vídeo e de imagem ainda são não distorcidos no pipeline de processamento de imagem do sistema antes que os quadros sejam disponibilizados para o aplicativo (o fluxo de visualização contém os quadros distorcidos originais). Como apenas a CameraIntrinsics é disponibilizada, os aplicativos devem assumir que os quadros de imagem representam uma câmera de pino perfeita.

No HoloLens (primeira geração), a função undistortion no processador de imagem ainda pode deixar um erro de até 10 pixels ao usar a CameraIntrinsics nos metadados do quadro. Em muitos casos de uso, esse erro não importa, mas se você estiver alinhando hologramas a cartazes/marcadores do mundo real, por exemplo, e você observar um deslocamento de 10 px do <(aproximadamente 11 mm para hologramas posicionados a 2 metros de distância), esse erro de distorção poderá ser a causa. 

## <a name="locatable-camera-usage-scenarios"></a>Cenários de uso de câmeras localizados

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostrar uma foto ou vídeo no mundo em que ela foi capturada

Os quadros da Câmera do Dispositivo vêm com uma transformação "Câmera para o Mundo", que pode ser usada para mostrar exatamente onde o dispositivo estava quando a imagem foi tirada. Por exemplo, você pode posicionar um pequeno ícone holográfico nesse local (CameraToWorld.MultiplyPoint(Vector3.zero)) e até mesmo desenhar uma pequena seta na direção em que a câmera estava voltada (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Marcação/padrão/cartaz/acompanhamento de objeto

Muitos aplicativos de realidade misturada usam uma imagem reconhecível ou um padrão visual para criar um ponto rastreável no espaço. Em seguida, isso é usado para renderizar objetos relativos a esse ponto ou criar um local conhecido. Alguns usos para HoloLens incluem localizar um objeto do mundo real marcado com fiduciais (por exemplo, um monitor de TV com um código QR), colocar hologramas sobre fiduciais e emparelhar visualmente com dispositivos não HoloLens, como tablets que foram definidos para se comunicar com HoloLens via Wi-Fi.

Você precisará de algumas coisas para reconhecer um padrão visual e colocar um objeto no espaço do mundo dos aplicativos:
1. Um kit de ferramentas de reconhecimento de padrão de imagem, como código QR, marcas AR, localizador de face, rastreadores de círculo, OCR etc.
2. Coletar quadros de imagem em runtime e passá-los para a camada de reconhecimento
3. Desprojete seus locais de imagem de volta para posições do mundo ou provavelmente raios do mundo. 
4. Posicionar seus modelos virtuais nesses locais do mundo

Alguns links importantes de processamento de imagem:
* [OpenCV](https://opencv.org/)
* [Marcas QR](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Manter uma taxa de quadros de aplicativo interativo é essencial, especialmente ao lidar com algoritmos de reconhecimento de imagem de execução longa. Por esse motivo, normalmente usamos o seguinte padrão:
1. Thread Principal: gerencia o objeto da câmera
2. Thread Principal: solicita novos quadros (assíncrono)
3. Thread Principal: passar novos quadros para o thread de acompanhamento
4. Thread de Acompanhamento: processa a imagem para coletar pontos-chave
5. Thread Principal: move o modelo virtual para corresponder aos pontos-chave encontrados
6. Thread Principal: repita da etapa 2

Alguns sistemas de marcador de imagem fornecem apenas um único local de pixel (outros fornecem a transformação completa, caso em que essa seção não será necessária), o que equivale a um raio de possíveis locais. Para chegar a um único local 3d, podemos aproveitar vários raios e localizar o resultado final por sua interseção aproximada. Para fazer isso, você precisará:
1. Obter um loop que vai coletar várias imagens de câmera
2. Encontrar os pontos de recurso associados e seus raios de mundo
3. Quando você tiver um dicionário de recursos, cada um com vários raios do mundo, poderá usar o código a seguir para resolver a interseção desses raios:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Considerando dois ou mais locais de marcação rastreados, você pode posicionar uma cena modelada para se ajustar ao cenário atual do usuário. Se você não puder assumir a gravidade, precisará de três locais de marca. Em muitos casos, usamos um esquema de cores em que as esferas brancas representam locais de marca rastreados em tempo real e as esferas azuis representam locais de marca modelados. Isso permite que o usuário mede visualmente a qualidade do alinhamento. Pressupomos a seguinte configuração em todos os nossos aplicativos:
* Dois ou mais locais de marcação modelados
* Um 'espaço de calibragem', que na cena é o pai das marcas
* Identificador de recurso da câmera
* Comportamento, que move o espaço de calibragem para alinhar as marcas modeladas com as marcas em tempo real (temos cuidado para mover o espaço pai, não os marcadores modelados em si, porque outras se conectam são posições relativas a eles).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Rastrear ou identificar objetos/faces do mundo real marcados ou móveis usando LEDs ou outras bibliotecas de reconhecedor

Exemplos:
* Robô industriais com LEDs (ou códigos QR para objetos de movimentação mais lentos)
* Identificar e reconhecer objetos na sala
* Identificar e reconhecer pessoas na sala, por exemplo, colocando cartões de contato holográficos sobre rostos

## <a name="see-also"></a>Confira também
* [Exemplo de câmera localizador](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Câmera localizável no Unity](../unity/locatable-camera-in-unity.md)
* [Captura de realidade mista](/hololens/holographic-photos-and-videos)
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Introdução à captura de mídia](/windows/uwp/audio-video-camera/)
* [Exemplo de acompanhamento facial holográfico](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)