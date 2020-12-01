---
title: Escrevendo um aplicativo remoto de comunicação remota do Holographic (OpenXR)
description: Ao criar um aplicativo remoto de comunicação remota do Holographic, o conteúdo remoto, que é processado em um computador remoto, pode ser transmitido para o HoloLens 2. Este artigo descreve como isso pode ser feito.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, comunicação remota Holographic, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, NuGet
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469489"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="dfd7f-105">Escrevendo um aplicativo remoto de comunicação remota do Holographic usando a API do OpenXR</span><span class="sxs-lookup"><span data-stu-id="dfd7f-105">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="dfd7f-106">Este documento descreve a criação de um aplicativo remoto para os headsets do HoloLens 2 e do Windows Mixed Reality usando a [API OpenXR](../native/openxr.md).</span><span class="sxs-lookup"><span data-stu-id="dfd7f-106">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="dfd7f-107">Os aplicativos remotos para o **HoloLens (1º gen)** devem usar o pacote NuGet versão **1. x**. x.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="dfd7f-108">Isso significa que os aplicativos remotos escritos para o HoloLens 2 não são compatíveis com o HoloLens 1 e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="dfd7f-109">A documentação do HoloLens 1 pode ser encontrada [aqui](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="dfd7f-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="dfd7f-110">Ao criar um aplicativo remoto de comunicação remota do Holographic, o conteúdo remoto que é processado em um computador remoto pode ser transmitido para dispositivos HoloLens 2 e de imersão, como headsets de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2 and immersive devices like Windows Mixed Reality headsets.</span></span> <span data-ttu-id="dfd7f-111">Este artigo descreve como isso pode ser feito.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="dfd7f-112">Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="dfd7f-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="dfd7f-113">A comunicação remota do Holographic permite que um aplicativo direcione fones de ouvido 2 e Windows Mixed Realm headsets com conteúdo Holographic processado em um PC desktop ou em um dispositivo UWP, como o Xbox, permitindo o acesso a mais recursos do sistema e possibilitando a integração de [exibições de imersão](../../design/app-views.md) remotas ao software de PC desktop existente.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-113">Holographic remoting allows an app to target HoloLens 2 and Windows Mixed Reality headsets with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="dfd7f-114">Um aplicativo remoto recebe um fluxo de dados de entrada do HoloLens 2, renderiza o conteúdo em uma exibição de imersão virtual e transmite os quadros de conteúdo de volta para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="dfd7f-115">A conexão é feita usando Wi-Fi padrão.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="dfd7f-116">A comunicação remota do Holographic é adicionada a um aplicativo de desktop ou UWP por meio de um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="dfd7f-117">É necessário um código adicional que manipula a conexão e é renderizado em uma exibição de imersão.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="dfd7f-118">Uma conexão de comunicação remota típica terá um mínimo de 50 ms de latência.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="dfd7f-119">O aplicativo de player pode relatar a latência em tempo real.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dfd7f-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dfd7f-120">Prerequisites</span></span>

<span data-ttu-id="dfd7f-121">Um bom ponto de partida é um aplicativo de desktop ou UWP baseado em OpenXR de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-121">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="dfd7f-122">Para obter detalhes, consulte [introdução ao OpenXR](../native/openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="dfd7f-122">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="dfd7f-123">Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-123">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="dfd7f-124">O uso de um [apartamento de thread único](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-124">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="dfd7f-125">Ao usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-125">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="dfd7f-126">Obter o pacote NuGet de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="dfd7f-126">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="dfd7f-127">As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-127">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="dfd7f-128">Abra o projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-128">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="dfd7f-129">Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="dfd7f-129">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="dfd7f-130">No painel que aparece, clique em **procurar** e procure "comunicação remota do Holographic".</span><span class="sxs-lookup"><span data-stu-id="dfd7f-130">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="dfd7f-131">Selecione **Microsoft. Holographic. Remoting. OpenXr**, certifique-se de escolher a versão mais recente do **2. x. x** e clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-131">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="dfd7f-132">Se a caixa de diálogo **Visualizar** for exibida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-132">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="dfd7f-133">A próxima caixa de diálogo exibida é o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-133">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="dfd7f-134">Clique em **aceito** para aceitar o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-134">Click on **I Accept** to accept the license agreement.</span></span>
7. <span data-ttu-id="dfd7f-135">Repita as etapas de 3 a 6 para os seguintes pacotes NuGet: OpenXR. Headers, OpenXR. Loader</span><span class="sxs-lookup"><span data-stu-id="dfd7f-135">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="dfd7f-136">A versão **1. x. x** do pacote NuGet ainda está disponível para desenvolvedores que desejam direcionar para o HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="dfd7f-137">Para obter detalhes, consulte [Add Holographic Remoting (HoloLens (1º gen))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="dfd7f-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="dfd7f-138">Selecione o tempo de execução do Holographic Remoting OpenXR</span><span class="sxs-lookup"><span data-stu-id="dfd7f-138">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="dfd7f-139">A primeira etapa que você precisa fazer em seu aplicativo remoto é selecionar o tempo de execução do Holographic Remoting OpenXR que faz parte do pacote NuGet Microsoft. Holographic. Remoting. OpenXr.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-139">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="dfd7f-140">Você pode fazer isso definindo a ```XR_RUNTIME_JSON``` variável de ambiente para o caminho do RemotingXR.jsno arquivo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-140">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="dfd7f-141">Essa variável de ambiente é usada pelo carregador OpenXR para não usar o tempo de execução OpenXR padrão do sistema, mas em vez disso, redirecionar para o tempo de execução do Holographic Remoting OpenXR.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-141">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="dfd7f-142">Ao usar o pacote NuGet Microsoft. Holographic. Remoting. OpenXr, o RemotingXR.jsno arquivo é copiado automaticamente durante a compilação para a pasta de saída, portanto, a seleção do OpenXR Runtime geralmente tem a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-142">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, thus the OpenXR runtime selection typically looks as follows.</span></span>

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="dfd7f-143">Criar XrInstance com a extensão de comunicação remota Holographic</span><span class="sxs-lookup"><span data-stu-id="dfd7f-143">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="dfd7f-144">A primeira etapa que um aplicativo OpenXR típico deve fazer é selecionar extensões OpenXR e criar um XrInstance.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-144">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create a XrInstance.</span></span> <span data-ttu-id="dfd7f-145">A especificação OpenXR Core não fornece nenhuma API específica de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-145">The OpenXR core specification does not provide any remoting specific API.</span></span> <span data-ttu-id="dfd7f-146">Por esse motivo, a comunicação remota Holographic introduz sua própria extensão OpenXR chamada ```XR_MSFT_holographic_remoting``` .</span><span class="sxs-lookup"><span data-stu-id="dfd7f-146">For that reason Holographic Remoting introduces it's own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="dfd7f-147">Certifique-se de que, quando você chamar xrCreateInstance, o ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` esteja incluído no XrInstanceCreateInfo.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-147">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="dfd7f-148">Por padrão, o conteúdo renderizado de seu aplicativo é transmitido somente para o player de comunicação remota Holographic em execução em um HoloLens 2 ou em headsets de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-148">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="dfd7f-149">Para exibir também o conteúdo renderizado no PC remoto, por meio de uma cadeia de troca de uma janela por exemplo, a comunicação remota do Holographic fornece uma segunda extensão OpenXR chamada ```XR_MSFT_holographic_remoting_frame_mirroring``` .</span><span class="sxs-lookup"><span data-stu-id="dfd7f-149">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="dfd7f-150">Certifique-se também de habilitar essa extensão usando o ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` caso queira usar essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-150">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="dfd7f-151">Para saber mais sobre a API de extensão de OpenXR de comunicação remota Holographic, confira a [especificação](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) que pode ser encontrada no [repositório GitHub de exemplos de comunicação remota Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="dfd7f-151">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="dfd7f-152">Conectar-se ao dispositivo</span><span class="sxs-lookup"><span data-stu-id="dfd7f-152">Connect to the device</span></span>

<span data-ttu-id="dfd7f-153">Depois que seu aplicativo remoto tiver criado o XrInstance e consultado o XrSystemId por meio do xrGetSystem, uma conexão com o dispositivo do Player poderá ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-153">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="dfd7f-154">O tempo de execução do Holographic Remoting OpenXR só é capaz de fornecer dados específicos do dispositivo, como configurações de exibição ou modos de mistura de ambiente depois que uma conexão é estabelecida.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-154">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="dfd7f-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` e fornecerão ```xrGetSystemProperties``` valores padrão, correspondendo ao que você normalmente obteria se você se conectar a um player em execução em um HoloLens 2, antes de ser totalmente conectado.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="dfd7f-156">É altamente recomendável não chamar esses métodos antes que uma conexão seja estabelecida.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-156">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="dfd7f-157">A sugestão é usar esses métodos depois que o XrSession tiver sido criado com êxito e o estado da sessão for pelo menos XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-157">The suggestion is use these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="dfd7f-158">As propriedades gerais, como taxa de bits máxima, habilitação de áudio, codec de vídeo ou resolução de fluxo de buffer de profundidade, podem ser configuradas ```xrRemotingSetContextPropertiesMSFT``` da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-158">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="dfd7f-159">A conexão pode ser feita de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-159">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="dfd7f-160">O aplicativo remoto se conecta ao Player em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-160">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="dfd7f-161">O Player em execução no dispositivo se conecta ao aplicativo remoto.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-161">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="dfd7f-162">Para estabelecer uma conexão do aplicativo remoto com o dispositivo do Player, chame o ```xrRemotingConnectMSFT``` método que especifica o nome do host e a porta por meio da  ```XrRemotingConnectInfoMSFT``` estrutura.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-162">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="dfd7f-163">A porta usada pelo Holographic Remoting Player é **8265**.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-163">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="dfd7f-164">A escuta de conexões de entrada no aplicativo remoto pode ser feita chamando o ```xrRemotingListenMSFT``` método.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-164">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="dfd7f-165">A porta de handshake e a porta de transporte podem ser especificadas por meio da ```XrRemotingListenInfoMSFT``` estrutura.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-165">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="dfd7f-166">A porta de handshake é usada para o handshake inicial.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-166">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="dfd7f-167">Os dados são enviados pela porta de transporte.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-167">The data is then send over the transport port.</span></span> <span data-ttu-id="dfd7f-168">Por padrão, **8265** e **8266** são usados.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-168">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="dfd7f-169">O estado da conexão deve ser desconectado quando você chama ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="dfd7f-169">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="dfd7f-170">Você pode obter o estado da conexão a qualquer momento depois de ter criado um XrInstance e consultado para o XrSystemId por meio de ```xrRemotingGetConnectionStateMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="dfd7f-170">You can get the connection state at any point after you have created a XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="dfd7f-171">Os Estados de conexão disponíveis são:</span><span class="sxs-lookup"><span data-stu-id="dfd7f-171">Available connection states are:</span></span>
- <span data-ttu-id="dfd7f-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="dfd7f-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="dfd7f-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="dfd7f-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="dfd7f-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="dfd7f-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="dfd7f-175">```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` deve ser chamado antes de tentar criar um XrSession via xrCreateSession.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-175">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="dfd7f-176">Se você tentar criar um XrSession enquanto o estado da conexão for ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` a criação da sessão terá sucesso, mas o estado da sessão passará imediatamente para XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-176">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="dfd7f-177">A implementação de comunicação remota Holographic do ```xrCreateSession``` dá suporte à espera de uma conexão ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-177">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="dfd7f-178">Você pode chamar ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` imediatamente seguido por uma chamada para a ```xrCreateSession``` qual bloqueará e aguardará que uma conexão seja estabelecida.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-178">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to ```xrCreateSession``` which will block and wait for a connection to be established.</span></span> <span data-ttu-id="dfd7f-179">O tempo limite é fixo para 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-179">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="dfd7f-180">Se uma conexão puder ser estabelecida dentro dessa hora, a criação do XrSession terá sucesso e o estado da sessão passará para XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-180">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="dfd7f-181">Caso nenhuma conexão possa ser estabelecida, a criação da sessão também é bem sucedido, mas imediatamente faz a transição para XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-181">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="dfd7f-182">Em geral, o estado de conexão é combinado com o estado XrSession.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-182">In general the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="dfd7f-183">Qualquer alteração no estado da conexão também afeta o estado da sessão.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-183">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="dfd7f-184">Por exemplo, se o estado de conexão mudar de `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` para ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` o estado de sessão também fará a transição para XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-184">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="dfd7f-185">Manipulando eventos específicos de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="dfd7f-185">Handling Remoting specific events</span></span>

<span data-ttu-id="dfd7f-186">O tempo de execução de OpenXR de comunicação remota do Holographic expõe três eventos que são importantes para monitorar o estado de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-186">The Holographic Remoting OpenXR runtime exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="dfd7f-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Disparado quando uma conexão com o dispositivo foi estabelecida com êxito.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="dfd7f-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Disparado se uma conexão estabelecida é fechada ou uma conexão não pôde ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection could not be established.</span></span>
3) <span data-ttu-id="dfd7f-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Quando a escuta de conexões de entrada é iniciada.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="dfd7f-190">Esses eventos são colocados em uma fila e seu aplicativo remoto deve ler a partir da fila com regularidade via ```xrPollEvent``` .</span><span class="sxs-lookup"><span data-stu-id="dfd7f-190">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="dfd7f-191">Visualizar conteúdo transmitido localmente</span><span class="sxs-lookup"><span data-stu-id="dfd7f-191">Preview streamed content locally</span></span>

<span data-ttu-id="dfd7f-192">Para exibir o mesmo conteúdo no aplicativo remoto que é enviado para o dispositivo, a ```XR_MSFT_holographic_remoting_frame_mirroring``` extensão pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-192">To display the same content in the remote app that is send to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="dfd7f-193">Com essa extensão, você pode enviar uma textura para xrEndFrame.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-193">With this extension you can submit a texture to xrEndFrame.</span></span> <span data-ttu-id="dfd7f-194">Isso é feito usando a ```XrRemotingFrameMirrorImageInfoMSFT``` estrutura que é encadeada ao XrFrameEndInfo da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-194">This is done by using the ```XrRemotingFrameMirrorImageInfoMSFT``` structure which is chained to the XrFrameEndInfo as follows.</span></span>

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

<span data-ttu-id="dfd7f-195">O exemplo acima usa uma textura de cadeia de permuta DX11 e apresenta a janela imediatamente após a chamada para xrEndFrame.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-195">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="dfd7f-196">O uso não é restrito a texturas de cadeia de permuta e nenhuma sincronização de GPU adicional é necessária.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-196">The usage is not restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="dfd7f-197">Para obter detalhes sobre o uso e as restrições, confira a [especificação de extensão](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span><span class="sxs-lookup"><span data-stu-id="dfd7f-197">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="dfd7f-198">Se seu aplicativo remoto estiver usando o DX12, use XrRemotingFrameMirrorImageD3D12MSFT em vez de XrRemotingFrameMirrorImageD3D11MSFT.</span><span class="sxs-lookup"><span data-stu-id="dfd7f-198">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfd7f-199">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="dfd7f-199">See Also</span></span>
* [<span data-ttu-id="dfd7f-200">Como escrever um aplicativo personalizado do Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="dfd7f-200">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="dfd7f-201">Como estabelecer uma conexão segura com o Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="dfd7f-201">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="dfd7f-202">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="dfd7f-202">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="dfd7f-203">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="dfd7f-203">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="dfd7f-204">Política de Privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="dfd7f-204">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
