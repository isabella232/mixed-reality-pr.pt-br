---
title: Como usar o suporte para XR interno do Legacy
description: Saiba como configurar seus projetos do Unity com e sem o MRTK usando o suporte a XR herdado.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidade misturada, desenvolvimento, começar, novo projeto, Windows Mixed Reality, UWP, XR, desempenho, herdado, mrtk
ms.openlocfilehash: b5faa48ec913c5095b12361318729b6f14276f30
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743506"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="f8a93-104">Usando o suporte de XR herddo</span><span class="sxs-lookup"><span data-stu-id="f8a93-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="f8a93-105">Configurando seu projeto com o MRTK</span><span class="sxs-lookup"><span data-stu-id="f8a93-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="f8a93-106">O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="f8a93-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="f8a93-107">A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="f8a93-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="f8a93-108">O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="f8a93-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f8a93-109">Experimente os nossos tutoriais do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8a93-109">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=wsa)

<span data-ttu-id="f8a93-110">Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.</span><span class="sxs-lookup"><span data-stu-id="f8a93-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="f8a93-111">Configuração manual sem MRTK</span><span class="sxs-lookup"><span data-stu-id="f8a93-111">Manual setup without MRTK</span></span>

<span data-ttu-id="f8a93-112">Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="f8a93-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

<span data-ttu-id="f8a93-114">Se você estiver direcionando o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="f8a93-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="f8a93-115">Selecione **Arquivo > Configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="f8a93-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="f8a93-116">Selecione **Plataforma Universal do Windows** na lista Plataforma e selecione **Alternar Plataforma**</span><span class="sxs-lookup"><span data-stu-id="f8a93-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="f8a93-117">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="f8a93-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="f8a93-118">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="f8a93-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="f8a93-119">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="f8a93-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="f8a93-120">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="f8a93-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="f8a93-121">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="f8a93-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity Plataforma Universal do Windows realçada](images/wmr-config-img-4.png)

<span data-ttu-id="f8a93-123">Depois de configurar sua plataforma, você precisa permitir que o Unity saiba para criar uma [exibição](../../design/app-views.md) imersiva em vez de uma exibição 2D quando exportada.</span><span class="sxs-lookup"><span data-stu-id="f8a93-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="f8a93-124">O XR herdado foi preterido no Unity 2019 e removido no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="f8a93-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="f8a93-125">Abra **Configurações do Player...** nas **Configurações de Build... janela** e expanda o **grupo Configurações XR**</span><span class="sxs-lookup"><span data-stu-id="f8a93-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="f8a93-126">Na seção **Configurações do XR,** selecione **Realidade Virtual Com** Suporte para adicionar a lista Dispositivos de Realidade Virtual</span><span class="sxs-lookup"><span data-stu-id="f8a93-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="f8a93-127">Definir **Formato de Profundidade** como Profundidade de **16 bits e** habilitar o **Compartilhamento de Buffer de Profundidade**</span><span class="sxs-lookup"><span data-stu-id="f8a93-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="f8a93-128">Definir **o modo de renderização estéreo** como instância de passagem **única**</span><span class="sxs-lookup"><span data-stu-id="f8a93-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="f8a93-129">Selecione **WSA Holographic Remoting Supported** se você quiser usar a remoting holográfica</span><span class="sxs-lookup"><span data-stu-id="f8a93-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com a seção Configurações do player realçada](images/wmr-config-img-9.png)