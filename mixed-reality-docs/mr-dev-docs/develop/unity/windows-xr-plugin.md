---
title: Como usar o plug-in de XR do Windows
description: Saiba como configurar seus projetos do Unity com e sem MRTK usando o suporte do Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto, realidade do Windows Mixed, UWP, XR, desempenho, herdado, mrtk, Windows
ms.openlocfilehash: 5d2d27a7ac5ea30515907a08eab6f6bfe70e6686
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906952"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="f1c87-104">Usando o plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="f1c87-104">Using Windows XR plugin</span></span>

<span data-ttu-id="f1c87-105">Para desenvolvedores direcionados para o Unity 2020, o plug-in do Windows XR permite o acesso a recursos mistos de realidade em headsets do HoloLens 2 e do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f1c87-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="f1c87-106">Esse plug-in também tem suporte no Unity 2019, embora haja algumas incompatibilidades conhecidas com âncoras espaciais do Azure ao usar esse plug-in nessa versão.</span><span class="sxs-lookup"><span data-stu-id="f1c87-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="f1c87-107">Embora a Microsoft e a Comunidade tenham criado ferramentas abertas como o [MRTK (Mixed Reality Toolkit)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) que configurará automaticamente o ambiente WMR, muitos desenvolvedores desejam criar suas experiências desde o início.</span><span class="sxs-lookup"><span data-stu-id="f1c87-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="f1c87-108">A documentação a seguir demonstrará como configurar corretamente um projeto para o desenvolvimento de realidade misturada se você estiver usando MRTK ou não.</span><span class="sxs-lookup"><span data-stu-id="f1c87-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="f1c87-109">As configurações que você precisa alterar são divididas em duas categorias: configurações por projeto e configurações por cena.</span><span class="sxs-lookup"><span data-stu-id="f1c87-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="f1c87-110">Configurando seu projeto com o MRTK</span><span class="sxs-lookup"><span data-stu-id="f1c87-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="f1c87-111">O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="f1c87-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="f1c87-112">A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="f1c87-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="f1c87-113">O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="f1c87-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1c87-114">Experimente os nossos tutoriais do MRTK</span><span class="sxs-lookup"><span data-stu-id="f1c87-114">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="f1c87-115">Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.</span><span class="sxs-lookup"><span data-stu-id="f1c87-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="f1c87-116">Configuração manual sem MRTK</span><span class="sxs-lookup"><span data-stu-id="f1c87-116">Manual setup without MRTK</span></span>

<span data-ttu-id="f1c87-117">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="f1c87-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

<span data-ttu-id="f1c87-119">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="f1c87-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="f1c87-120">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="f1c87-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="f1c87-121">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="f1c87-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="f1c87-122">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="f1c87-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="f1c87-123">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="f1c87-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="f1c87-124">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="f1c87-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="f1c87-125">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="f1c87-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="f1c87-126">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="f1c87-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

<span data-ttu-id="f1c87-128">Depois de definir sua plataforma, você precisa permitir que o Unity saiba como criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada:</span><span class="sxs-lookup"><span data-stu-id="f1c87-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="f1c87-129">No editor do Unity, navegue até **editar > configurações do projeto** e selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="f1c87-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="f1c87-130">Selecione **instalar o gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="f1c87-130">Select **Install XR Plugin Management**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-5.png)

3. <span data-ttu-id="f1c87-132">Selecione **inicializar XR na inicialização** e **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="f1c87-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-7.png)

4. <span data-ttu-id="f1c87-134">Expanda a seção **Gerenciamento de plug-ins do XR** e selecione **Universal guia Configurações da plataforma Windows**</span><span class="sxs-lookup"><span data-stu-id="f1c87-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="f1c87-135">Se você estiver usando o Unity 2020 ou posterior, verá as opções para verificar a realidade do **OpenXR** ou do **Windows Mixed**.</span><span class="sxs-lookup"><span data-stu-id="f1c87-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="f1c87-136">Você pode escolher qualquer tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f1c87-136">You can choose either runtime.</span></span>  <span data-ttu-id="f1c87-137">Se você estiver desenvolvendo especificamente para o HoloLens 2 ou para a HP reverbs G2 e decidir experimentar o **OpenXR**, selecione a caixa OpenXR e examine nosso guia para [usar o plug-in de realidade misturada do OpenXR para](./xr-project-setup.md) que o Unity se prepare corretamente para esses dispositivos antes de retornar a este tutorial</span><span class="sxs-lookup"><span data-stu-id="f1c87-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](./xr-project-setup.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="f1c87-138">A partir do Unity 2020 LTS, a Microsoft está adotando o desenvolvimento com o OpenXR.</span><span class="sxs-lookup"><span data-stu-id="f1c87-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="f1c87-139">À medida que migramos para esse caminho, no Unity 2021,1, o plug-in do Windows XR será preterido e removido em 2021,2, tornando OpenXR o único caminho com suporte.</span><span class="sxs-lookup"><span data-stu-id="f1c87-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="f1c87-140">Você pode encontrar mais informações sobre como [usar o plug-in OpenXR de realidade misturada](./xr-project-setup.md).</span><span class="sxs-lookup"><span data-stu-id="f1c87-140">You can find more information in [Using the Mixed Reality OpenXR plugin](./xr-project-setup.md).</span></span>

6. <span data-ttu-id="f1c87-141">Se você decidir escolher o plug-in de **realidade mista do Windows** , marque todas as caixas e defina o **modo de envio de profundidade** como profundidade de **16 bits**</span><span class="sxs-lookup"><span data-stu-id="f1c87-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção realidade mista do Windows realçada](images/wmr-config-img-8.png)