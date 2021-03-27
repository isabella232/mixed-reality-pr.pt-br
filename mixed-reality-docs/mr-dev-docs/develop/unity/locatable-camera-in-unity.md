---
title: Câmera de vídeo fotográfico no Unity
description: Saiba como capturar uma foto em um arquivo ou em um Texture2D, como capturar uma foto e interagir com os bytes brutos e como capturar um vídeo.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: foto, vídeo, hololens, câmera, Unity, localizável, PVC, câmera de vídeo fotográfico, headset de realidade misturada, headset de realidade mista do Windows, Headset virtual realismo, webcam, captura de foto, captura de vídeo
ms.openlocfilehash: 1cae796a793036ed59c1d0805df76cb8ac143027
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636208"
---
# <a name="photo-video-camera-in-unity"></a>Câmera de vídeo fotográfico no Unity

## <a name="enabling-the-capability-for-camera-access"></a>Habilitando a capacidade de acesso à câmera

A capacidade de "WebCam" deve ser declarada para que um aplicativo use a [câmera](../platform-capabilities-and-apis/locatable-camera.md).

1. No editor do Unity, vá para as configurações do Player navegando até a página "Editar configurações do projeto > > Player"
2. Selecione a guia "Windows Store"
3. Na seção "configurações de publicação > recursos", verifique os recursos de **webcam** e de **microfone**

Apenas uma única operação pode ocorrer com a câmera de cada vez. Você pode verificar em qual modo a câmera está no momento `UnityEngine.XR.WSA.WebCam.Mode` no unity 2018 e versões anteriores ou `UnityEngine.Windows.WebCam.Mode` no Unity 2019 e versões posteriores. Os modos disponíveis são foto, vídeo ou nenhum.

## <a name="photo-capture"></a>Captura de fotos

**Namespace (antes do Unity 2019):** *UnityEngine. XR. WSA. webcam*<br>
**Namespace (Unity 2019 e posterior):** *UnityEngine. Windows. webcam*<br>
**Tipo:** o *Capture*

O tipo de *captura* de imagem permite que você faça ainda fotografias com a câmera de vídeo de fotos. O padrão geral para usar o *Capture* para tirar uma foto é o seguinte:

1. Criar um objeto do *Pocapture*
2. Crie um objeto *cameraparameters* com as configurações desejadas
3. Iniciar o modo de foto via *StartPhotoModeAsync*
4. Tire a foto que você deseja
    * adicional Interagir com essa imagem
5. Parar o modo de foto e limpar os recursos

### <a name="common-set-up-for-photocapture"></a>Configuração comum para o Capture

Para todos os três usos, comece com as mesmas três primeiras etapas acima

Comece criando um objeto do *Pocapture*

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

Em seguida, armazene seu objeto, defina seus parâmetros e inicie o modo de foto

```cs
private PhotoCapture photoCaptureObject = null;

void OnPhotoCaptureCreated(PhotoCapture captureObject)
{
    photoCaptureObject = captureObject;

    Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

    CameraParameters c = new CameraParameters();
    c.hologramOpacity = 0.0f;
    c.cameraResolutionWidth = cameraResolution.width;
    c.cameraResolutionHeight = cameraResolution.height;
    c.pixelFormat = CapturePixelFormat.BGRA32;

    captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
}
```

No final, você também usará o mesmo código de limpeza apresentado aqui

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

Após essas etapas, você pode escolher o tipo de foto a ser capturado.

### <a name="capture-a-photo-to-a-file"></a>Capturar uma foto para um arquivo

A operação mais simples é capturar uma foto diretamente em um arquivo. A foto pode ser salva como um JPG ou um PNG.

Se você iniciou o modo de foto com êxito, tire uma foto e armazene-a em disco

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
        string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

Depois de capturar a foto para o disco, saia do modo de foto e limpe os objetos

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        Debug.Log("Saved Photo to disk!");
        photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
    }
    else
    {
        Debug.Log("Failed to save Photo to disk");
    }
}
```

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>Capturar uma foto para um Texture2D com o local

Ao capturar dados para um Texture2D, o processo é semelhante à captura para o disco.

Siga o processo de instalação acima.

No *OnPhotoModeStarted*, Capture um quadro na memória.

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

Em seguida, você aplicará o resultado a uma textura e usará o código de limpeza comum acima.

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        // Create our Texture2D for use and set the correct resolution
        Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
        // Copy the raw image data into our target texture
        photoCaptureFrame.UploadImageDataToTexture(targetTexture);
        // Do as we wish with the texture such as apply it to a material, etc.
    }
    // Clean up
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

#### <a name="locatable-camera"></a>Câmera localizável

Para posicionar essa textura na cena e exibi-la usando as matrizes da câmera localizável, adicione o seguinte código a *OnCapturedPhotoToMemory* na `result.success` marca de seleção:

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

O [Unity forneceu um código de exemplo](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) para aplicar a matriz de projeção a um sombreador específico em seus fóruns.

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Capture uma foto e interaja com os bytes brutos

Para interagir com os bytes brutos de um quadro na memória, siga as mesmas etapas de configuração descritas acima e *OnPhotoModeStarted* como em capturando uma foto para um Texture2D. A diferença está em *OnCapturedPhotoToMemory* , em que você pode obter os bytes brutos e interagir com eles.

Neste exemplo, você criará uma *lista <Color>* para ser processada ou aplicada a uma textura por meio de *setPixels ()*

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        List<byte> imageBufferList = new List<byte>();
        // Copy the raw IMFMediaBuffer data into our empty byte list.
        photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

        // In this example, we captured the image using the BGRA32 format.
        // So our stride will be 4 since we have a byte for each rgba channel.
        // The raw image data will also be flipped so we access our pixel data
        // in the reverse order.
        int stride = 4;
        float denominator = 1.0f / 255.0f;
        List<Color> colorArray = new List<Color>();
        for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
        {
            float a = (int)(imageBufferList[i - 0]) * denominator;
            float r = (int)(imageBufferList[i - 1]) * denominator;
            float g = (int)(imageBufferList[i - 2]) * denominator;
            float b = (int)(imageBufferList[i - 3]) * denominator;

            colorArray.Add(new Color(r, g, b, a));
        }
        // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
    }
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

## <a name="video-capture"></a>Captura de vídeo

**Namespace (antes do Unity 2019):** *UnityEngine. XR. WSA. webcam*<br>
**Namespace (Unity 2019 e posterior):** *UnityEngine. Windows. webcam*<br>
**Tipo:** *VideoCapture*

O *VideoCapture* funciona de forma semelhante ao *Capture*. As duas únicas diferenças são que você deve especificar um valor de quadros por segundo (FPS) e só pode salvar diretamente no disco como um arquivo. mp4. As etapas para usar o *VideoCapture* são as seguintes:

1. Criar um objeto *VideoCapture*
2. Crie um objeto *cameraparameters* com as configurações desejadas
3. Iniciar o modo de vídeo via *StartVideoModeAsync*
4. Iniciar gravação de vídeo
5. Parar de gravar vídeo
6. Parar o modo de vídeo e limpar os recursos

Comece criando nosso objeto *VideoCapture* *VideoCapture m_VideoCapture = NULL;*

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

Em seguida, configure os parâmetros desejados para a gravação e o início.

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
{
    if (videoCapture != null)
    {
        m_VideoCapture = videoCapture;

        Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

        CameraParameters cameraParameters = new CameraParameters();
        cameraParameters.hologramOpacity = 0.0f;
        cameraParameters.frameRate = cameraFramerate;
        cameraParameters.cameraResolutionWidth = cameraResolution.width;
        cameraParameters.cameraResolutionHeight = cameraResolution.height;
        cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

        m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                            VideoCapture.AudioState.None,
                                            OnStartedVideoCaptureMode);
    }
    else
    {
        Debug.LogError("Failed to create VideoCapture Instance!");
    }
}
```

Depois de iniciado, inicie a gravação

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format("MyVideo_{0}.mp4", Time.time);
        string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
    }
}
```

Após o início da gravação, você pode atualizar sua interface do usuário ou comportamentos para habilitar a interrupção. Aqui você acabou de fazer logon.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

Em um ponto posterior, você desejará parar a gravação usando uma entrada de temporizador ou de usuário, por exemplo.

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

Depois que a gravação for interrompida, pare o modo de vídeo e limpe os recursos.

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Stopped Recording Video!");
    m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
}

void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    m_VideoCapture.Dispose();
    m_VideoCapture = null;
}
```

## <a name="troubleshooting"></a>Solução de problemas

* Não há resoluções disponíveis
  * Verifique se a capacidade de **webcam** está especificada no seu projeto.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada. Deste ponto, você pode prosseguir para o próximo tópico:

> [!div class="nextstepaction"]
> [Ponto de foco](focus-point-in-unity.md)

Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:

> [!div class="nextstepaction"]
> [Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows](../platform-capabilities-and-apis/using-visual-studio.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-advanced-features) a qualquer momento.

## <a name="see-also"></a>Consulte Também

* [Câmera localizável](../platform-capabilities-and-apis/locatable-camera.md)