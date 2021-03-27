---
title: Configuração da câmera no Unity
description: Saiba como configurar e usar a câmera principal do Unity para o desenvolvimento de realidade mista do Windows para fazer a renderização Holographic.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Holographic Rendering, Holographic, imersão, ponto de foco, buffer de profundidade, somente orientação, posicional, opaco, transparente, clipe, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636238"
---
# <a name="camera-setup-in-unity"></a><span data-ttu-id="16d9c-104">Configuração da câmera no Unity</span><span class="sxs-lookup"><span data-stu-id="16d9c-104">Camera setup in Unity</span></span>

<span data-ttu-id="16d9c-105">Quando você gasta um headset de realidade misturada, ele se torna o centro do seu Holographic World.</span><span class="sxs-lookup"><span data-stu-id="16d9c-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="16d9c-106">O componente da [câmera](https://docs.unity3d.com/Manual/class-Camera.html) do Unity manipulará automaticamente a renderização de estereoscópico e seguirá a rotação e o movimento da cabeça.</span><span class="sxs-lookup"><span data-stu-id="16d9c-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="16d9c-107">No entanto, para otimizar totalmente a qualidade visual e a [estabilidade do holograma](../platform-capabilities-and-apis/hologram-stability.md), você deve definir as configurações de câmera descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="16d9c-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="hololens-vs-vr-immersive-headsets"></a><span data-ttu-id="16d9c-108">Fone de ouvido do HoloLens versus VR de imersão</span><span class="sxs-lookup"><span data-stu-id="16d9c-108">HoloLens vs VR immersive headsets</span></span>

<span data-ttu-id="16d9c-109">As configurações padrão no componente câmera do Unity são para aplicativos 3D tradicionais, que precisam de um plano de fundo Skybox, pois não têm um mundo real.</span><span class="sxs-lookup"><span data-stu-id="16d9c-109">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="16d9c-110">Ao executar em um **[headset de imersão](../../discover/immersive-headset-hardware-details.md)**, você está renderizando tudo o que o usuário vê e, portanto, provavelmente desejará manter o Skybox.</span><span class="sxs-lookup"><span data-stu-id="16d9c-110">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="16d9c-111">No entanto, ao executar em um **Headset Holographic** como o [HoloLens](/hololens/hololens2-hardware), o mundo real deve aparecer atrás de tudo que a câmera renderiza.</span><span class="sxs-lookup"><span data-stu-id="16d9c-111">However, when running on a **holographic headset** like [HoloLens](/hololens/hololens2-hardware), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="16d9c-112">Defina o plano de fundo da câmera como transparente (no HoloLens, o preto é renderizado como transparente) em vez de uma textura Skybox:</span><span class="sxs-lookup"><span data-stu-id="16d9c-112">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="16d9c-113">Selecione a câmera principal no painel hierarquia</span><span class="sxs-lookup"><span data-stu-id="16d9c-113">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="16d9c-114">No painel Inspetor, localize o componente câmera e altere a lista suspensa limpar sinalizadores de Skybox para cor sólida</span><span class="sxs-lookup"><span data-stu-id="16d9c-114">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="16d9c-115">Selecione o seletor de cor do plano de fundo e altere os valores de RGBA para (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="16d9c-115">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>
        1. <span data-ttu-id="16d9c-116">Se estiver configurando a partir do código, você poderá usar o [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span><span class="sxs-lookup"><span data-stu-id="16d9c-116">If setting this from code, you can use Unity's [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span></span>

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a><span data-ttu-id="16d9c-117">Instalação da câmera</span><span class="sxs-lookup"><span data-stu-id="16d9c-117">Camera setup</span></span>

<span data-ttu-id="16d9c-118">Seja qual for o tipo de experiência que você está desenvolvendo, a câmera principal é sempre o principal componente de renderização estéreo anexado à tela de montagem de cabeçalho do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="16d9c-118">Whatever kind of experience you're developing, the Main Camera is always the primary stereo rendering component attached to your device's head-mounted display.</span></span> <span data-ttu-id="16d9c-119">Será mais fácil definir o layout do seu aplicativo se você imaginar a posição inicial do usuário como (X: 0, Y: 0, Z: 0).</span><span class="sxs-lookup"><span data-stu-id="16d9c-119">It'll be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="16d9c-120">Como a câmera principal está acompanhando a movimentação do cabeçalho do usuário, a posição inicial do usuário pode ser definida definindo a posição inicial da câmera principal.</span><span class="sxs-lookup"><span data-stu-id="16d9c-120">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

<span data-ttu-id="16d9c-121">A opção central que você precisa fazer é se você está desenvolvendo para headsets de imersão ou VR.</span><span class="sxs-lookup"><span data-stu-id="16d9c-121">The central choice you need to make is whether you're developing for HoloLens or VR immersive headsets.</span></span> <span data-ttu-id="16d9c-122">Depois de fazer isso, pule para qualquer seção de instalação aplicável.</span><span class="sxs-lookup"><span data-stu-id="16d9c-122">Once you've got that, skip to whichever setup section applies.</span></span>

### <a name="hololens-camera-setup"></a><span data-ttu-id="16d9c-123">Instalação da câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="16d9c-123">HoloLens camera setup</span></span>

<span data-ttu-id="16d9c-124">Para aplicativos do HoloLens, você precisa usar âncoras para todos os objetos que deseja bloquear para o ambiente de cena.</span><span class="sxs-lookup"><span data-stu-id="16d9c-124">For HoloLens apps, you need to use anchors for any objects you want to lock to the scene environment.</span></span> <span data-ttu-id="16d9c-125">É recomendável usar espaço não associado para maximizar a estabilidade e criar âncoras em várias salas.</span><span class="sxs-lookup"><span data-stu-id="16d9c-125">We recommend using unbounded space to maximize stability and create anchors in multiple rooms.</span></span>

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a><span data-ttu-id="16d9c-126">Configuração da câmera VR</span><span class="sxs-lookup"><span data-stu-id="16d9c-126">VR camera setup</span></span>

<span data-ttu-id="16d9c-127">O Windows Mixed Reality dá suporte a aplicativos em uma ampla variedade de [escalas de experiência](../../design/coordinate-systems.md#mixed-reality-experience-scales), desde aplicativos de dimensionamento e de orientação e escalados até aplicativos em escala de sala.</span><span class="sxs-lookup"><span data-stu-id="16d9c-127">Windows Mixed Reality supports apps across a wide range of [experience scales](../../design/coordinate-systems.md#mixed-reality-experience-scales), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="16d9c-128">No HoloLens, você pode ir além e criar aplicativos de escala mundial que permitem que os usuários passem além de 5 metros, explorando um andar inteiro de um edifício e além disso.</span><span class="sxs-lookup"><span data-stu-id="16d9c-128">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="16d9c-129">Sua primeira etapa na criação de uma experiência de realidade mista no Unity é determinar qual [escala de experiência](../../design/coordinate-systems.md) seu aplicativo será direcionada:</span><span class="sxs-lookup"><span data-stu-id="16d9c-129">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](../../design/coordinate-systems.md) your app will target:</span></span>

* [<span data-ttu-id="16d9c-130">Orientação ou escala colocada</span><span class="sxs-lookup"><span data-stu-id="16d9c-130">Orientation or seated-scale</span></span>](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [<span data-ttu-id="16d9c-131">Escala de espaço ou em pé</span><span class="sxs-lookup"><span data-stu-id="16d9c-131">Standing or room-scale</span></span>](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [<span data-ttu-id="16d9c-132">Escala mundial</span><span class="sxs-lookup"><span data-stu-id="16d9c-132">World-scale</span></span>](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a><span data-ttu-id="16d9c-133">Experiência em escala ou em posição de sala</span><span class="sxs-lookup"><span data-stu-id="16d9c-133">Room-scale or standing experiences</span></span>

> [!NOTE]
> <span data-ttu-id="16d9c-134">Se você estiver criando para HL2, é recomendável criar uma experiência de nível de olho ou considerar o uso da [compreensão em cena](../platform-capabilities-and-apis/scene-understanding-sdk.md) em relação ao andar da sua cena.</span><span class="sxs-lookup"><span data-stu-id="16d9c-134">If you're building for HL2, we recommend creating an eye-level experience, or consider using [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) to reason about the floor of your scene.</span></span>

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a><span data-ttu-id="16d9c-135">Experiências enfeitas</span><span class="sxs-lookup"><span data-stu-id="16d9c-135">Seated experiences</span></span>

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a><span data-ttu-id="16d9c-136">Configurando o plano de fundo da câmera</span><span class="sxs-lookup"><span data-stu-id="16d9c-136">Setting up the camera background</span></span>

<span data-ttu-id="16d9c-137">Se você estiver usando o MRTK, o plano de fundo da câmera será automaticamente configurado e gerenciado.</span><span class="sxs-lookup"><span data-stu-id="16d9c-137">If you're using MRTK, the camera's background is automatically configured and managed.</span></span> <span data-ttu-id="16d9c-138">Para projetos do XR SDK ou de WSA herdados, é recomendável definir o plano de fundo da câmera como preto sólido no HoloLens e manter o Skybox para VR.</span><span class="sxs-lookup"><span data-stu-id="16d9c-138">For XR SDK or Legacy WSA projects, we recommend setting the camera's background to solid black on HoloLens and keeping the skybox for VR.</span></span>

## <a name="using-multiple-cameras"></a><span data-ttu-id="16d9c-139">Usando várias câmeras</span><span class="sxs-lookup"><span data-stu-id="16d9c-139">Using multiple cameras</span></span>

<span data-ttu-id="16d9c-140">Quando há vários componentes de câmera na cena, o Unity sabe qual câmera usar para a renderização estereoscópico com base em qual gameobject tem a marca MainCamera.</span><span class="sxs-lookup"><span data-stu-id="16d9c-140">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering based on which GameObject has the MainCamera tag.</span></span> <span data-ttu-id="16d9c-141">Em Legacy XR, ele também usa essa marca para o rastreamento de cabeçalho de sincronização.</span><span class="sxs-lookup"><span data-stu-id="16d9c-141">In legacy XR, it also uses this tag to sync head tracking.</span></span> <span data-ttu-id="16d9c-142">No XR SDK, o acompanhamento de cabeçalho é orientado por um script TrackedPoseDriver anexado à câmera.</span><span class="sxs-lookup"><span data-stu-id="16d9c-142">In XR SDK, head tracking is driven by a TrackedPoseDriver script attached to the camera.</span></span>

## <a name="sharing-depth-buffers"></a><span data-ttu-id="16d9c-143">Compartilhamento de buffers de profundidade</span><span class="sxs-lookup"><span data-stu-id="16d9c-143">Sharing depth buffers</span></span>

<span data-ttu-id="16d9c-144">Compartilhar o buffer de profundidade do seu aplicativo para o Windows cada quadro dará ao seu aplicativo um dos dois aumentos na estabilidade do holograma, com base no tipo de headset que você está renderizando:</span><span class="sxs-lookup"><span data-stu-id="16d9c-144">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="16d9c-145">Os **headsets de imersão de VR** podem cuidar da Reprojeção posicional quando um buffer de profundidade é fornecido, ajustando os hologramas para uma previsão incorreta na posição e na orientação.</span><span class="sxs-lookup"><span data-stu-id="16d9c-145">**VR immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="16d9c-146">Os **headsets do HoloLens** têm alguns métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="16d9c-146">**HoloLens headsets** have a few different methods.</span></span> <span data-ttu-id="16d9c-147">O HoloLens 1 selecionará automaticamente um [ponto de foco](focus-point-in-unity.md) quando um buffer de profundidade for fornecido, otimizando a estabilidade do holograma ao longo do plano que intercepta a maior parte do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="16d9c-147">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="16d9c-148">O HoloLens 2 irá estabilizar o conteúdo usando [LSR de profundidade (consulte comentários)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span><span class="sxs-lookup"><span data-stu-id="16d9c-148">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a><span data-ttu-id="16d9c-149">Usando planos de recorte</span><span class="sxs-lookup"><span data-stu-id="16d9c-149">Using clipping planes</span></span>

<span data-ttu-id="16d9c-150">O processamento de conteúdo muito próximo ao usuário pode ser desconfortável em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="16d9c-150">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="16d9c-151">Você pode ajustar os [planos de corte próximo e longe](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) no componente da câmera.</span><span class="sxs-lookup"><span data-stu-id="16d9c-151">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="16d9c-152">Selecione a **câmera principal** no painel **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="16d9c-152">Select the **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="16d9c-153">No painel **Inspetor** , localize os **planos de recorte** do componente da **câmera** e altere a caixa de texto **próximo** de **0,3** para **0,85**.</span><span class="sxs-lookup"><span data-stu-id="16d9c-153">In the **Inspector** panel, find the **Camera** component **Clipping Planes** and change the **Near** textbox from **0.3** to **0.85**.</span></span> <span data-ttu-id="16d9c-154">O conteúdo renderizado ainda mais próximo pode levar ao usuário discomfort e deve ser evitado de acordo com as [diretrizes de distância de renderização](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span><span class="sxs-lookup"><span data-stu-id="16d9c-154">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="recentering-the-camera"></a><span data-ttu-id="16d9c-155">Recentralizando a câmera</span><span class="sxs-lookup"><span data-stu-id="16d9c-155">Recentering the camera</span></span>

<span data-ttu-id="16d9c-156">Se você estiver criando uma [experiência de escala](../../design/coordinate-systems.md)em posição, poderá recentralizar a origem mundial da unidade na posição de cabeçalho atual do usuário chamando o **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** em Legacy XR ou o método **[XRInputSubsystem. TRYRECENTER](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** no XR SDK.</span><span class="sxs-lookup"><span data-stu-id="16d9c-156">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method in legacy XR or the **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** method in XR SDK.</span></span>

## <a name="teleportation"></a><span data-ttu-id="16d9c-157">Portabilidade</span><span class="sxs-lookup"><span data-stu-id="16d9c-157">Teleportation</span></span>

<span data-ttu-id="16d9c-158">Esse recurso é normalmente reservado para experiências de VR:</span><span class="sxs-lookup"><span data-stu-id="16d9c-158">This feature is typically reserved for VR experiences:</span></span>

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a><span data-ttu-id="16d9c-159">Modos de Reprojeção</span><span class="sxs-lookup"><span data-stu-id="16d9c-159">Reprojection modes</span></span>

<span data-ttu-id="16d9c-160">Os headsets de HoloLens e de imersão reprojetarão cada quadro que seu aplicativo renderiza para se ajustar para qualquer previsão incorreta da posição de cabeçalho real do usuário quando fótons são emitidos.</span><span class="sxs-lookup"><span data-stu-id="16d9c-160">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="16d9c-161">Por padrão:</span><span class="sxs-lookup"><span data-stu-id="16d9c-161">By default:</span></span>

* <span data-ttu-id="16d9c-162">Os **headsets de imersão de VR** se encarregarão da Reprojeção de posição, se o aplicativo fornecer um buffer de profundidade para um determinado quadro.</span><span class="sxs-lookup"><span data-stu-id="16d9c-162">**VR immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="16d9c-163">Os headsets de imersão também ajustarão os hologramas para uma previsão incorreta na posição e na orientação.</span><span class="sxs-lookup"><span data-stu-id="16d9c-163">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="16d9c-164">Se um buffer de profundidade não for fornecido, o sistema corrigirá apenas as previsões incorretas na orientação.</span><span class="sxs-lookup"><span data-stu-id="16d9c-164">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="16d9c-165">Os **fones de ouvido Holographic** , como o HoloLens 2, cuidam da Reprojeção posicional se o aplicativo fornece seu buffer de profundidade ou não.</span><span class="sxs-lookup"><span data-stu-id="16d9c-165">**Holographic headsets** like HoloLens 2 will take care of positional reprojection whether the app provides its depth buffer or not.</span></span> <span data-ttu-id="16d9c-166">A Reprojeção posicional é possível sem buffers de profundidade no HoloLens, pois a renderização costuma ser esparsa com um plano de fundo estável fornecido pelo mundo real.</span><span class="sxs-lookup"><span data-stu-id="16d9c-166">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="16d9c-167">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="16d9c-167">Next Development Checkpoint</span></span>

<span data-ttu-id="16d9c-168">Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="16d9c-168">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="16d9c-169">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="16d9c-169">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16d9c-170">Foco</span><span class="sxs-lookup"><span data-stu-id="16d9c-170">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="16d9c-171">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="16d9c-171">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16d9c-172">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="16d9c-172">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="16d9c-173">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="16d9c-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="16d9c-174">Confira também</span><span class="sxs-lookup"><span data-stu-id="16d9c-174">See also</span></span>

* [<span data-ttu-id="16d9c-175">Estabilidade do holograma</span><span class="sxs-lookup"><span data-stu-id="16d9c-175">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="16d9c-176">Escalas de experiência</span><span class="sxs-lookup"><span data-stu-id="16d9c-176">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="16d9c-177">Estágio espacial</span><span class="sxs-lookup"><span data-stu-id="16d9c-177">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="16d9c-178">Como controlar a perda no Unity</span><span class="sxs-lookup"><span data-stu-id="16d9c-178">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="16d9c-179">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="16d9c-179">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="16d9c-180">Persistência no Unity</span><span class="sxs-lookup"><span data-stu-id="16d9c-180">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="16d9c-181">Experiências compartilhadas no Unity</span><span class="sxs-lookup"><span data-stu-id="16d9c-181">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="16d9c-182">Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="16d9c-182">Azure Spatial Anchors</span></span>](/azure/spatial-anchors)
* [<span data-ttu-id="16d9c-183">SDK de âncoras espaciais do Azure para Unity</span><span class="sxs-lookup"><span data-stu-id="16d9c-183">Azure Spatial Anchors SDK for Unity</span></span>](/dotnet/api/Microsoft.Azure.SpatialAnchors)