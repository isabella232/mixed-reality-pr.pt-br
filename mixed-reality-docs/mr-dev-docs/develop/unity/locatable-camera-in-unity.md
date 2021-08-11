---
title: Câmera de foto/vídeo no Unity
description: Saiba como capturar uma foto em um arquivo ou em um Texture2D, como capturar uma foto e interagir com os bytes brutos e como capturar um vídeo.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: foto, vídeo, hololens, câmera, unity, locatable, PVC, câmera de vídeo de foto, headset de realidade misturada, headset de realidade misturada do windows, headset de realidade virtual, webcam, captura de fotos, captura de vídeo
ms.openlocfilehash: 4fdf895e6b2b7ed1fc051b45b07ce49052f8a95587178caddfc71a0cfd364eee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193500"
---
# <a name="photo-video-camera-in-unity"></a>Câmera de foto/vídeo no Unity

## <a name="enabling-the-capability-for-camera-access"></a>Habilitando a funcionalidade para acesso à câmera

A funcionalidade "WebCam" deve ser declarada para que um aplicativo use a [câmera](../platform-capabilities-and-apis/locatable-camera.md).

1. No Editor do Unity, acesse as configurações do player navegando até a página "Editar > Project Configurações > Player"
2. Selecione a guia "Windows Store"
3. Na seção "Funcionalidades de Configurações > publicação", verifique as funcionalidades **de WebCam** **e Microfone**

Somente uma única operação pode ocorrer com a câmera por vez. Você pode verificar em qual modo a câmera está atualmente no Unity 2018 e anterior ou no `UnityEngine.XR.WSA.WebCam.Mode` `UnityEngine.Windows.WebCam.Mode` Unity 2019 e posterior. Os modos disponíveis são foto, vídeo ou nenhum.

## <a name="photo-capture"></a>Captura de fotos

**Namespace (antes do Unity 2019):** *UnityEngine.XR.WSA.WebCam*<br>
**Namespace (Unity 2019 e posterior):** *UnityEngine.Windows. WebCam*<br>
**Tipo:** *PhotoCapture*

O *tipo PhotoCapture* permite que você tire fotos ainda com a Câmera de Vídeo de Foto. O padrão geral para usar *o PhotoCapture* para tirar uma foto é o seguinte:

1. Criar um *objeto PhotoCapture*
2. Criar um *objeto CameraParameters* com as configurações que você deseja
3. Iniciar o modo de foto *por meio de StartPhotoModeAsync*
4. Tire a foto que você deseja
    * (opcional) Interagir com essa imagem
5. Parar o Modo de Foto e limpar recursos

### <a name="common-set-up-for-photocapture"></a>Configuração comum para PhotoCapture

Para todos os três usos, comece com as mesmas três primeiras etapas acima

Comece criando um *objeto PhotoCapture*

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

Em seguida, armazene seu objeto, de definir os parâmetros e inicie o Modo de Foto

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

Após essas etapas, você pode escolher qual tipo de foto capturar.

### <a name="capture-a-photo-to-a-file"></a>Capturar uma foto para um arquivo

A operação mais simples é capturar uma foto diretamente em um arquivo. A foto pode ser salva como um JPG ou um PNG.

Se você iniciou com êxito o modo de foto, tire uma foto e armazene-a em disco

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

Depois de capturar a foto no disco, saia do modo de foto e limpe seus objetos

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>Capturar uma foto em um Texture2D com localização

Ao capturar dados em um Texture2D, o processo é semelhante à captura em disco.

Siga o processo de instalação acima.

Em *OnPhotoModeStarted,* capture um quadro na memória.

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

Para colocar essa textura na cena e exibi-la usando as matrizes de câmeras locacionáveis, adicione o seguinte código a *OnCapturedPhotoToMemory* na `result.success` verificação:

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

[O Unity forneceu um código de exemplo](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) para aplicar a matriz de projeção a um sombreador específico em seus fóruns.

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Capturar uma foto e interagir com os bytes brutos

Para interagir com os bytes brutos de um quadro na memória, siga as mesmas etapas de configuração acima e *OnPhotoModeStarted* como na captura de uma foto para um Texture2D. A diferença está em *OnCapturedPhotoToMemory,* em que você pode obter os bytes brutos e interagir com eles.

Neste exemplo, você criará uma *Lista <Color>* para ser processada ou aplicada a uma textura por meio de *SetPixels()*

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

**Namespace (antes do Unity 2019):** *UnityEngine.XR.WSA.WebCam*<br>
**Namespace (Unity 2019 e posterior):** *UnityEngine.Windows. WebCam*<br>
**Tipo:** *VideoCapture*

*O VideoCapture* funciona de forma semelhante ao *PhotoCapture.* As únicas duas diferenças são que você deve especificar um valor FPS (Quadros por Segundo) e só pode salvar diretamente no disco como um arquivo .mp4 arquivo. As etapas para usar *o VideoCapture* são as seguintes:

1. Criar um *objeto VideoCapture*
2. Criar um *objeto CameraParameters* com as configurações que você deseja
3. Iniciar o modo de vídeo *por meio de StartVideoModeAsync*
4. Iniciar a gravação de vídeo
5. Stop recording vídeo
6. Parar o Modo de Vídeo e limpar recursos

Comece criando nosso objeto *VideoCapture* *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

Em seguida, configurar os parâmetros que você deseja para a gravação e iniciar.

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

Depois que a gravação tiver sido iniciada, você poderá atualizar a interface do usuário ou os comportamentos para habilitar a interrupção. Aqui, basta fazer logoff.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

Em um ponto posterior, você deseja interromper a gravação usando um temporizador ou entrada do usuário, por exemplo.

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

Depois que a gravação tiver parado, pare o modo de vídeo e limpe seus recursos.

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

* Nenhuma resolução está disponível
  * Verifique se **a funcionalidade webCam** está especificada em seu projeto.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso do ponto de verificação de desenvolvimento do Unity que lançamos, você está no meio da exploração das APIs e funcionalidades da plataforma de Realidade Misturada. Deste ponto, você pode prosseguir para o próximo tópico:

> [!div class="nextstepaction"]
> [Ponto de foco](focus-point-in-unity.md)

Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:

> [!div class="nextstepaction"]
> [Implantar em HoloLens ou Windows Mixed Reality headsets imersivos](../platform-capabilities-and-apis/using-visual-studio.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-advanced-features) a qualquer momento.

## <a name="see-also"></a>Consulte Também

* [Câmera localizável](../platform-capabilities-and-apis/locatable-camera.md)