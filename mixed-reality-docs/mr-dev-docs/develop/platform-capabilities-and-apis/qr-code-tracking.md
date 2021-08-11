---
title: Acompanhamento de código QR
description: saiba como detectar códigos QR, adicionar recursos de webcam e gerenciar sistemas de coordenadas em aplicativos de realidade misturada no HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: VR, LBE, entretenimento baseado na localização, VR de los, de los, de imersão, QR, QR Code, hololens2
ms.openlocfilehash: f6d2f224b9f477cf78ba4f0a5b6ce362f629d06988e966d71ed03bc48eda41d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193702"
---
# <a name="qr-code-tracking"></a>Acompanhamento de código QR

O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código. Depois de habilitar a webcam do dispositivo, você poderá reconhecer códigos QR nas versões mais recentes de seus projetos não reais ou do Unity. Antes de ir para a produção, recomendamos seguir as [práticas recomendadas](#best-practices-for-qr-code-detection) que apresentamos no final do artigo.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (primeira gen)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Detecção de código QR</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>o controle de código QR com alto Windows Mixed Reality headsets em computadores desktop tem suporte na versão Windows 10 2004 e superior. Use a API Microsoft. MixedReality. QRCodeWatcher. IsSupported () para determinar se o recurso tem suporte no dispositivo atual.

## <a name="getting-the-qr-package"></a>Obtendo o pacote QR

você pode baixar o pacote de NuGet para detecção de código QR [aqui](https://nuget.org/Packages/Microsoft.MixedReality.QR).

## <a name="using-openxr"></a>Usando OpenXR

Ao usar o plug-in OpenXR, pegue o [ `SpatialGraphNodeId` da API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e use a `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API para localizar o código QR.

para referência, temos um [projeto de exemplo de acompanhamento QR em GitHub](https://github.com/yl-msft/QRTracking) com mais uma explicação de uso detalhada para a [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="detecting-qr-codes"></a>Detectando códigos QR

### <a name="adding-the-webcam-capability"></a>Adicionando o recurso de webcam

Você precisará adicionar a capacidade `webcam` ao seu manifesto para detectar códigos QR. Esse recurso é necessário, pois os dados dentro de códigos detectados no ambiente do usuário podem conter informações confidenciais.

A permissão pode ser solicitada chamando `QRCodeWatcher.RequestAccessAsync()` :

_C#_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

A permissão deve ser solicitada antes de construir um objeto QRCodeWatcher.

Embora a detecção de código QR exija o `webcam` recurso, a detecção ocorre usando as câmeras de rastreamento do dispositivo. Isso fornece uma FOV de detecção mais ampla e uma melhor vida útil da bateria em comparação com a detecção com a câmera de foto/vídeo (PV) do dispositivo.

### <a name="detecting-qr-codes-in-unity"></a>Detectando códigos QR no Unity

você pode usar a API de detecção de código QR no Unity sem importar MRTK instalando o pacote de NuGet usando [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity). Se você quiser ter uma ideia de como funciona, baixe o aplicativo do [Unity de exemplo](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes). O aplicativo de exemplo tem exemplos para exibir um Holographic quadrado sobre códigos QR e dados associados, como GUID, tamanho físico, carimbo de data/hora e dados decodificados.

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Obtendo o sistema de coordenadas para um código QR

Cada código QR detectado expõe um [sistema de coordenadas espaciais](../../design/coordinate-systems.md) alinhado com o código QR no canto superior esquerdo do quadrado de detecção rápida na parte superior esquerda:  

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

Ao usar o SDK QR diretamente, o eixo Z está apontando para o papel (não mostrado)-quando convertido em coordenadas do Unity, o eixo Z aponta para fora do papel e é canhoto.

Um SpatialCoordinateSystem de código QR é alinhado conforme mostrado. Você pode obter o sistema de coordenadas da plataforma chamando <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> e passando o SpatialGraphNodeId do código.

O código C++ abaixo mostra como criar um retângulo e colocá-lo usando o sistema de coordenadas do código QR:

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

Totalmente, seu *QRCodeAddedHandler* pode ser semelhante a este:

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

### <a name="quiet-zones-around-qr-codes"></a>Zonas silenciosas em cerca de códigos QR

Para ser lido corretamente, os códigos QR exigem uma margem em volta de todos os lados do código. Essa margem não deve conter nenhum conteúdo impresso e deve ter quatro módulos (um único quadrado preto no código) de largura. 

A [especificação QR](https://www.qrcode.com/en/howto/code.html) contém mais informações sobre zonas silenciosas.

### <a name="lighting-and-backdrop"></a>Iluminação e pano de fundo
A qualidade de detecção de código QR é suscetível à iluminação e ao pano de fundo variadas. 

Em uma cena com iluminação brilhante, imprima um código preto em um plano de fundo cinza. Caso contrário, imprima um código QR preto em um plano de fundo branco.

Se o pano de fundo para o código for escuro, experimente um preto no código cinza se a taxa de detecção for baixa. Se o pano de fundo for relativamente claro, um código regular deverá funcionar bem.

### <a name="size-of-qr-codes"></a>Tamanho dos códigos QR
Windows Mixed Reality dispositivos não funcionam com códigos QR com lados menores que 5 cm cada.

Para códigos QR entre lados de comprimento de 5 cm e 10 cm, você deve estar bastante perto de detectar o código. Também levará mais tempo para detectar códigos nesse tamanho. 

O tempo exato para detectar códigos depende não apenas do tamanho dos códigos QR, mas o quanto você está longe do código. Avançar para o código ajudará a deslocar os problemas com o tamanho.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Distância e posição angular do código QR
As câmeras de rastreamento só podem detectar um determinado nível de detalhe. Para códigos pequenos – < 10 cm ao longo dos lados-você deve estar bem próximo. Para um código QR da versão 1 variando de 10 cm a 25 cm de largura, a distância mínima de detecção varia de 0,15 metros a 0,5 metros. 

A distância de detecção para o tamanho aumenta linearmente, mas também depende da versão QR ou do tamanho do módulo. Quanto maior a versão, menores os módulos, que só podem ser detectados em uma posição mais próxima. Você também pode experimentar os códigos micro QR se quiser que a distância da detecção seja maior. A detecção QR funciona com um intervalo de ângulos + = 45 graus para garantir que tenhamos a resolução adequada para detectar o código.

> [!IMPORTANT]
> Sempre verifique se você tem contraste suficiente e uma borda adequada.

### <a name="qr-codes-with-logos"></a>Códigos QR com logotipos
Códigos QR com logotipos não foram testados e não têm suporte no momento.

### <a name="managing-qr-code-data"></a>Gerenciando dados de código QR
Windows Mixed Reality dispositivos detectam códigos QR no nível do sistema no driver. Quando o dispositivo é reinicializado, os códigos QR detectados são desfeitos e serão detectados novamente como novos objetos da próxima vez.

É recomendável configurar seu aplicativo para ignorar códigos QR anteriores a um carimbo de data/hora específico. Atualmente, a API não dá suporte à limpeza do histórico de código QR.

### <a name="qr-code-placement-in-a-space"></a>Posicionamento de código QR em um espaço
Para obter recomendações sobre onde e como inserir códigos QR, consulte [considerações de ambiente para HoloLens](/hololens/hololens-environment-considerations).

## <a name="qr-api-reference"></a>Referência de API QR

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