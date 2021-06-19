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
# <a name="qr-code-tracking"></a>Acompanhamento de código QR

O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código. Depois de habilitar a webcam do dispositivo, você poderá reconhecer códigos QR nas versões mais recentes de seus projetos do Unreal ou do Unity. Antes de ir para produção, recomendamos seguir [as práticas](#best-practices-for-qr-code-detection) recomendadas que estabelecemos no final do artigo.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (primeira geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Detecção de código QR</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>O acompanhamento de código QR com headsets Windows Mixed Reality imersivos em computadores desktop tem suporte Windows 10 versão 2004 e superior. Use a API Microsoft.MixedReality.QRCodeWatcher.IsSupported() para determinar se o recurso tem suporte no dispositivo atual.

## <a name="getting-the-qr-package"></a>Obter o pacote QR

Você pode baixar o pacote NuGet para detecção de código QR [aqui](https://nuget.org/Packages/Microsoft.MixedReality.QR).

## <a name="using-openxr"></a>Usando OpenXR

Ao usar o plug-in OpenXR, pegue o da [ `SpatialGraphNodeId` API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e use a `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API para localizar o código QR.

Para referência, temos um projeto de exemplo de acompanhamento de [QR no GitHub](https://github.com/yl-msft/QRTracking) com uma explicação de uso mais detalhada para a [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="detecting-qr-codes"></a>Detectando códigos QR

### <a name="adding-the-webcam-capability"></a>Adicionando a funcionalidade de webcam

Você precisará adicionar a funcionalidade ao manifesto para `webcam` detectar códigos QR. Essa funcionalidade é necessária, pois os dados dentro dos códigos detectados no ambiente do usuário podem conter informações confidenciais.

A permissão pode ser solicitada chamando `QRCodeWatcher.RequestAccessAsync()` :

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

A permissão deve ser solicitada antes de você construir um objeto QRCodeWatcher.

Embora a detecção de código QR `webcam` exija a funcionalidade, a detecção ocorre usando as câmeras de acompanhamento do dispositivo. Isso fornece uma FOV de detecção mais ampla e uma melhor vida útil da bateria em comparação com a detecção com a câmera de foto/vídeo (PV) do dispositivo.

### <a name="detecting-qr-codes-in-unity"></a>Detectando códigos QR no Unity

Você pode usar a API de detecção de código QR no Unity sem importar o MRTK instalando o pacote NuGet usando [o NuGet para Unity.](https://github.com/GlitchEnzo/NuGetForUnity) Se você quiser ter uma sensação de como ele funciona, baixe o aplicativo [unity de exemplo](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes). O aplicativo de exemplo tem exemplos para exibir um quadrado holográfico sobre códigos QR e dados associados, como GUID, tamanho físico, data/hora e dados decodificados.

### <a name="detecting-qr-codes-in-c"></a>Detectando códigos QR em C++

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Obter o sistema de coordenadas para um código QR

Cada código QR detectado [](../../design/coordinate-systems.md) expõe um sistema de coordenadas espaciais alinhado com o código QR no canto superior esquerdo do quadrado de detecção rápida no canto superior esquerdo:  

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

Ao usar diretamente o SDK do QR, o eixo Z está apontando para o papel (não mostrado) – quando convertido em coordenadas do Unity, o eixo Z aponta para fora do papel e é de esquerda.

SpatialCoordinateSystem de um código QR se alinha conforme mostrado. Você pode obter o sistema de coordenadas da plataforma chamando <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode e</a> passando SpatialGraphNodeId do código.

O código C++ abaixo mostra como criar um retângulo e º-lo usando o sistema de coordenadas do código QR:

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

Você pode usar o tamanho físico para criar o retângulo QR:

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas ao local:

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

No total, *seu QRCodeAddedHandler* pode ter esta aparência:

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

## <a name="best-practices-for-qr-code-detection"></a>Práticas recomendadas para detecção de código QR

### <a name="quiet-zones-around-qr-codes"></a>Zonas silenciosas em torno de códigos QR

Para serem lidos corretamente, os códigos QR exigem uma margem em todos os lados do código. Essa margem não deve conter nenhum conteúdo impresso e deve ter quatro módulos (um único quadrado preto no código) de largura. 

A [especificação QR](https://www.qrcode.com/en/howto/code.html) contém mais informações sobre zonas silenciosas.

### <a name="lighting-and-backdrop"></a>Iluminação e pano de fundo
A qualidade da detecção de código QR é suscetível a variações de iluminação e de pano de fundo. 

Em uma cena com iluminação brilhante, imprima um código preto em uma tela de fundo cinza. Caso contrário, imprima um código QR preto em uma tela de fundo branca.

Se o pano de fundo para o código estiver escuro, tente um código preto em cinza se a taxa de detecção for baixa. Se o pano de fundo for relativamente claro, um código regular deverá funcionar bem.

### <a name="size-of-qr-codes"></a>Tamanho dos códigos QR
Windows Mixed Reality dispositivos não funcionam com códigos QR com lados menores que 5 cm cada.

Para códigos QR entre os lados de comprimento de 5 cm e 10 cm, você deve estar bem próximo para detectar o código. Também levará mais tempo para detectar códigos nesse tamanho. 

O tempo exato para detectar códigos depende não apenas do tamanho dos códigos QR, mas da distância do código. Aproximar-se do código ajudará a deslocar problemas com o tamanho.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Distância e posição angular do código QR
As câmeras de acompanhamento só podem detectar um determinado nível de detalhes. Para códigos pequenos – < 10 cm ao longo dos lados – você deve estar bastante próximo. Para um código QR versão 1 variando de 10 cm a 25 cm de largura, a distância mínima de detecção varia de 0,15 metros a 0,5 metros. 

A distância de detecção para tamanho aumenta linearmente, mas também depende da versão de QR ou do tamanho do módulo. Quanto maior a versão, menor será o número de módulos, que só podem ser detectados de uma posição mais próxima. Você também pode experimentar códigos QR micro se quiser que a distância da detecção seja mais longa. A detecção de QR funciona com uma variedade de ângulos += 45 deg para garantir que temos a resolução adequada para detectar o código.

> [!IMPORTANT]
> Sempre certifique-se de que você tenha contraste suficiente e uma borda adequada.

### <a name="qr-codes-with-logos"></a>Códigos QR com logotipos
Códigos QR com logotipos não foram testados e não têm suporte no momento.

### <a name="managing-qr-code-data"></a>Gerenciando dados de código QR
Windows Mixed Reality dispositivos detectam códigos QR no nível do sistema no driver. Quando o dispositivo é reinicializado, os códigos QR detectados se foram e serão reprojetados como novos objetos na próxima vez.

É recomendável configurar seu aplicativo para ignorar códigos QR mais antigos do que um data/hora específico. Atualmente, a API não dá suporte à limpeza do histórico de código QR.

### <a name="qr-code-placement-in-a-space"></a>Posicionamento de código QR em um espaço
Para recomendações sobre onde e como colocar códigos QR, consulte [Considerações de ambiente para o HoloLens.](/hololens/hololens-environment-considerations)

## <a name="qr-api-reference"></a>Referência da API QR

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

## <a name="see-also"></a>Confira também
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a>