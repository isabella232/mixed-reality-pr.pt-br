---
title: Usando o suporte interno a XR herdado
description: Saiba como configurar seus projetos do Unity com e sem MRTK usando o suporte interno a XR herdado.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto, realidade do Windows Mixed, UWP, XR, desempenho, herdado, mrtk
ms.openlocfilehash: 0860154034a63d5058da09a3b842e70bc3775dc5
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938094"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="481e1-104">Usando o suporte interno a XR herdado</span><span class="sxs-lookup"><span data-stu-id="481e1-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="481e1-105">Configurando seu projeto com o MRTK</span><span class="sxs-lookup"><span data-stu-id="481e1-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="481e1-106">O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="481e1-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="481e1-107">A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="481e1-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="481e1-108">O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="481e1-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="481e1-109">Experimente os nossos tutoriais do MRTK</span><span class="sxs-lookup"><span data-stu-id="481e1-109">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="481e1-110">Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.</span><span class="sxs-lookup"><span data-stu-id="481e1-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="481e1-111">Configuração manual sem MRTK</span><span class="sxs-lookup"><span data-stu-id="481e1-111">Manual setup without MRTK</span></span>

<span data-ttu-id="481e1-112">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="481e1-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

<span data-ttu-id="481e1-114">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="481e1-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="481e1-115">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="481e1-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="481e1-116">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="481e1-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="481e1-117">Definir a **arquitetura** para o **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="481e1-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="481e1-118">Definir o **dispositivo de destino** para o **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="481e1-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="481e1-119">Definir **tipo de compilação** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="481e1-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="481e1-120">Definir o **SDK do UWP** para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="481e1-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="481e1-121">Definir a **configuração de Build** como **Release** porque há problemas de desempenho conhecidos com a depuração</span><span class="sxs-lookup"><span data-stu-id="481e1-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

<span data-ttu-id="481e1-123">Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada.</span><span class="sxs-lookup"><span data-stu-id="481e1-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="481e1-124">O XR herdado é preterido no Unity 2019 e removido no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="481e1-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="481e1-125">Abra **as configurações do Player...** nas **configurações de compilação... e expandir o grupo de** **configurações XR**</span><span class="sxs-lookup"><span data-stu-id="481e1-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="481e1-126">Na seção **configurações de XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual</span><span class="sxs-lookup"><span data-stu-id="481e1-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="481e1-127">Definir o **formato de profundidade** como profundidade de **16 bits** e habilitar o **compartilhamento de buffer de profundidade**</span><span class="sxs-lookup"><span data-stu-id="481e1-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="481e1-128">Definir **modo de renderização estéreo** para **instância de passagem única**</span><span class="sxs-lookup"><span data-stu-id="481e1-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="481e1-129">Selecione **WSA Holographic Remoting com suporte** se você quiser usar o Holographic de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="481e1-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações do Player realçada](images/wmr-config-img-9.png)