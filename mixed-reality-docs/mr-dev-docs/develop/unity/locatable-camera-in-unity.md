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
# <a name="photo-video-camera-in-unity"></a><span data-ttu-id="639cc-104">Câmera de vídeo fotográfico no Unity</span><span class="sxs-lookup"><span data-stu-id="639cc-104">Photo Video camera in Unity</span></span>

## <a name="enabling-the-capability-for-camera-access"></a><span data-ttu-id="639cc-105">Habilitando a capacidade de acesso à câmera</span><span class="sxs-lookup"><span data-stu-id="639cc-105">Enabling the capability for camera access</span></span>

<span data-ttu-id="639cc-106">A capacidade de "WebCam" deve ser declarada para que um aplicativo use a [câmera](../platform-capabilities-and-apis/locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="639cc-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>

1. <span data-ttu-id="639cc-107">No editor do Unity, vá para as configurações do Player navegando até a página "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="639cc-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="639cc-108">Selecione a guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="639cc-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="639cc-109">Na seção "configurações de publicação > recursos", verifique os recursos de **webcam** e de **microfone**</span><span class="sxs-lookup"><span data-stu-id="639cc-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="639cc-110">Apenas uma única operação pode ocorrer com a câmera de cada vez.</span><span class="sxs-lookup"><span data-stu-id="639cc-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="639cc-111">Você pode verificar em qual modo a câmera está no momento `UnityEngine.XR.WSA.WebCam.Mode` no unity 2018 e versões anteriores ou `UnityEngine.Windows.WebCam.Mode` no Unity 2019 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="639cc-111">You can check which mode the camera is currently in with `UnityEngine.XR.WSA.WebCam.Mode` in Unity 2018 and earlier or `UnityEngine.Windows.WebCam.Mode` in Unity 2019  and later.</span></span> <span data-ttu-id="639cc-112">Os modos disponíveis são foto, vídeo ou nenhum.</span><span class="sxs-lookup"><span data-stu-id="639cc-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="639cc-113">Captura de fotos</span><span class="sxs-lookup"><span data-stu-id="639cc-113">Photo capture</span></span>

<span data-ttu-id="639cc-114">**Namespace (antes do Unity 2019):** *UnityEngine. XR. WSA. webcam*</span><span class="sxs-lookup"><span data-stu-id="639cc-114">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="639cc-115">**Namespace (Unity 2019 e posterior):** *UnityEngine. Windows. webcam*</span><span class="sxs-lookup"><span data-stu-id="639cc-115">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="639cc-116">**Tipo:** o *Capture*</span><span class="sxs-lookup"><span data-stu-id="639cc-116">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="639cc-117">O tipo de *captura* de imagem permite que você faça ainda fotografias com a câmera de vídeo de fotos.</span><span class="sxs-lookup"><span data-stu-id="639cc-117">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="639cc-118">O padrão geral para usar o *Capture* para tirar uma foto é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="639cc-118">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>

1. <span data-ttu-id="639cc-119">Criar um objeto do *Pocapture*</span><span class="sxs-lookup"><span data-stu-id="639cc-119">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="639cc-120">Crie um objeto *cameraparameters* com as configurações desejadas</span><span class="sxs-lookup"><span data-stu-id="639cc-120">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="639cc-121">Iniciar o modo de foto via *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="639cc-121">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="639cc-122">Tire a foto que você deseja</span><span class="sxs-lookup"><span data-stu-id="639cc-122">Take the photo you want</span></span>
    * <span data-ttu-id="639cc-123">adicional Interagir com essa imagem</span><span class="sxs-lookup"><span data-stu-id="639cc-123">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="639cc-124">Parar o modo de foto e limpar os recursos</span><span class="sxs-lookup"><span data-stu-id="639cc-124">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="639cc-125">Configuração comum para o Capture</span><span class="sxs-lookup"><span data-stu-id="639cc-125">Common set-up for PhotoCapture</span></span>

<span data-ttu-id="639cc-126">Para todos os três usos, comece com as mesmas três primeiras etapas acima</span><span class="sxs-lookup"><span data-stu-id="639cc-126">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="639cc-127">Comece criando um objeto do *Pocapture*</span><span class="sxs-lookup"><span data-stu-id="639cc-127">Start by creating a *PhotoCapture* object</span></span>

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

<span data-ttu-id="639cc-128">Em seguida, armazene seu objeto, defina seus parâmetros e inicie o modo de foto</span><span class="sxs-lookup"><span data-stu-id="639cc-128">Next, store your object, set your parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="639cc-129">No final, você também usará o mesmo código de limpeza apresentado aqui</span><span class="sxs-lookup"><span data-stu-id="639cc-129">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

<span data-ttu-id="639cc-130">Após essas etapas, você pode escolher o tipo de foto a ser capturado.</span><span class="sxs-lookup"><span data-stu-id="639cc-130">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="639cc-131">Capturar uma foto para um arquivo</span><span class="sxs-lookup"><span data-stu-id="639cc-131">Capture a photo to a file</span></span>

<span data-ttu-id="639cc-132">A operação mais simples é capturar uma foto diretamente em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="639cc-132">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="639cc-133">A foto pode ser salva como um JPG ou um PNG.</span><span class="sxs-lookup"><span data-stu-id="639cc-133">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="639cc-134">Se você iniciou o modo de foto com êxito, tire uma foto e armazene-a em disco</span><span class="sxs-lookup"><span data-stu-id="639cc-134">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="639cc-135">Depois de capturar a foto para o disco, saia do modo de foto e limpe os objetos</span><span class="sxs-lookup"><span data-stu-id="639cc-135">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a><span data-ttu-id="639cc-136">Capturar uma foto para um Texture2D com o local</span><span class="sxs-lookup"><span data-stu-id="639cc-136">Capture a photo to a Texture2D with location</span></span>

<span data-ttu-id="639cc-137">Ao capturar dados para um Texture2D, o processo é semelhante à captura para o disco.</span><span class="sxs-lookup"><span data-stu-id="639cc-137">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="639cc-138">Siga o processo de instalação acima.</span><span class="sxs-lookup"><span data-stu-id="639cc-138">Follow the setup process above.</span></span>

<span data-ttu-id="639cc-139">No *OnPhotoModeStarted*, Capture um quadro na memória.</span><span class="sxs-lookup"><span data-stu-id="639cc-139">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

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

<span data-ttu-id="639cc-140">Em seguida, você aplicará o resultado a uma textura e usará o código de limpeza comum acima.</span><span class="sxs-lookup"><span data-stu-id="639cc-140">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

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

#### <a name="locatable-camera"></a><span data-ttu-id="639cc-141">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="639cc-141">Locatable camera</span></span>

<span data-ttu-id="639cc-142">Para posicionar essa textura na cena e exibi-la usando as matrizes da câmera localizável, adicione o seguinte código a *OnCapturedPhotoToMemory* na `result.success` marca de seleção:</span><span class="sxs-lookup"><span data-stu-id="639cc-142">To place this texture in the scene and display it using the locatable camera matrices, add the following code to *OnCapturedPhotoToMemory* in the `result.success` check:</span></span>

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

<span data-ttu-id="639cc-143">O [Unity forneceu um código de exemplo](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) para aplicar a matriz de projeção a um sombreador específico em seus fóruns.</span><span class="sxs-lookup"><span data-stu-id="639cc-143">[Unity has provided sample code](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) for applying the projection matrix to a specific shader on their forums.</span></span>

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="639cc-144">Capture uma foto e interaja com os bytes brutos</span><span class="sxs-lookup"><span data-stu-id="639cc-144">Capture a photo and interact with the raw bytes</span></span>

<span data-ttu-id="639cc-145">Para interagir com os bytes brutos de um quadro na memória, siga as mesmas etapas de configuração descritas acima e *OnPhotoModeStarted* como em capturando uma foto para um Texture2D.</span><span class="sxs-lookup"><span data-stu-id="639cc-145">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="639cc-146">A diferença está em *OnCapturedPhotoToMemory* , em que você pode obter os bytes brutos e interagir com eles.</span><span class="sxs-lookup"><span data-stu-id="639cc-146">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="639cc-147">Neste exemplo, você criará uma *lista <Color>* para ser processada ou aplicada a uma textura por meio de *setPixels ()*</span><span class="sxs-lookup"><span data-stu-id="639cc-147">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="639cc-148">Captura de vídeo</span><span class="sxs-lookup"><span data-stu-id="639cc-148">Video capture</span></span>

<span data-ttu-id="639cc-149">**Namespace (antes do Unity 2019):** *UnityEngine. XR. WSA. webcam*</span><span class="sxs-lookup"><span data-stu-id="639cc-149">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="639cc-150">**Namespace (Unity 2019 e posterior):** *UnityEngine. Windows. webcam*</span><span class="sxs-lookup"><span data-stu-id="639cc-150">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="639cc-151">**Tipo:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="639cc-151">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="639cc-152">O *VideoCapture* funciona de forma semelhante ao *Capture*.</span><span class="sxs-lookup"><span data-stu-id="639cc-152">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="639cc-153">As duas únicas diferenças são que você deve especificar um valor de quadros por segundo (FPS) e só pode salvar diretamente no disco como um arquivo. mp4.</span><span class="sxs-lookup"><span data-stu-id="639cc-153">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="639cc-154">As etapas para usar o *VideoCapture* são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="639cc-154">The steps to use *VideoCapture* are as follows:</span></span>

1. <span data-ttu-id="639cc-155">Criar um objeto *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="639cc-155">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="639cc-156">Crie um objeto *cameraparameters* com as configurações desejadas</span><span class="sxs-lookup"><span data-stu-id="639cc-156">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="639cc-157">Iniciar o modo de vídeo via *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="639cc-157">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="639cc-158">Iniciar gravação de vídeo</span><span class="sxs-lookup"><span data-stu-id="639cc-158">Start recording video</span></span>
5. <span data-ttu-id="639cc-159">Parar de gravar vídeo</span><span class="sxs-lookup"><span data-stu-id="639cc-159">Stop recording video</span></span>
6. <span data-ttu-id="639cc-160">Parar o modo de vídeo e limpar os recursos</span><span class="sxs-lookup"><span data-stu-id="639cc-160">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="639cc-161">Comece criando nosso objeto *VideoCapture* *VideoCapture m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="639cc-161">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

<span data-ttu-id="639cc-162">Em seguida, configure os parâmetros desejados para a gravação e o início.</span><span class="sxs-lookup"><span data-stu-id="639cc-162">Next, set up the parameters you'll want for the recording and start.</span></span>

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

<span data-ttu-id="639cc-163">Depois de iniciado, inicie a gravação</span><span class="sxs-lookup"><span data-stu-id="639cc-163">Once started, begin the recording</span></span>

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

<span data-ttu-id="639cc-164">Após o início da gravação, você pode atualizar sua interface do usuário ou comportamentos para habilitar a interrupção.</span><span class="sxs-lookup"><span data-stu-id="639cc-164">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="639cc-165">Aqui você acabou de fazer logon.</span><span class="sxs-lookup"><span data-stu-id="639cc-165">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

<span data-ttu-id="639cc-166">Em um ponto posterior, você desejará parar a gravação usando uma entrada de temporizador ou de usuário, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="639cc-166">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

<span data-ttu-id="639cc-167">Depois que a gravação for interrompida, pare o modo de vídeo e limpe os recursos.</span><span class="sxs-lookup"><span data-stu-id="639cc-167">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="639cc-168">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="639cc-168">Troubleshooting</span></span>

* <span data-ttu-id="639cc-169">Não há resoluções disponíveis</span><span class="sxs-lookup"><span data-stu-id="639cc-169">No resolutions are available</span></span>
  * <span data-ttu-id="639cc-170">Verifique se a capacidade de **webcam** está especificada no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="639cc-170">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="639cc-171">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="639cc-171">Next Development Checkpoint</span></span>

<span data-ttu-id="639cc-172">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="639cc-172">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="639cc-173">Deste ponto, você pode prosseguir para o próximo tópico:</span><span class="sxs-lookup"><span data-stu-id="639cc-173">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="639cc-174">Ponto de foco</span><span class="sxs-lookup"><span data-stu-id="639cc-174">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="639cc-175">Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:</span><span class="sxs-lookup"><span data-stu-id="639cc-175">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="639cc-176">Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="639cc-176">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="639cc-177">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-advanced-features) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="639cc-177">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="639cc-178">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="639cc-178">See Also</span></span>

* [<span data-ttu-id="639cc-179">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="639cc-179">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)