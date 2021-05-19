---
title: Configurações da câmera do Windows Mixed Reality
description: Documentação para usar Windows Mixed Reality câmera no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Câmera,
ms.openlocfilehash: 94e00f47dc565af0824ef6acf5c08a9e99d4529f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145163"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="d2f90-104">Windows Mixed Reality de configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="d2f90-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="d2f90-105">O Windows Mixed Reality de configurações de câmera determina o tipo de dispositivo no qual o aplicativo está em execução e aplica as definições de configuração apropriadas com base na exibição (transparente ou opaca).</span><span class="sxs-lookup"><span data-stu-id="d2f90-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="d2f90-106">Habilitando o provedor Windows Mixed Reality configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="d2f90-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="d2f90-107">As etapas a seguir presumem o uso do objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="d2f90-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="d2f90-108">As etapas necessárias para outros registradores de serviço podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="d2f90-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="d2f90-109">Selecione o objeto MixedRealityToolkit na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="d2f90-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="d2f90-111">Navegue pelo painel Inspetor até a seção sistema de câmeras e expanda a **seção Provedores de Configurações da** Câmera.</span><span class="sxs-lookup"><span data-stu-id="d2f90-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Expandir provedores de configurações](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="d2f90-113">Clique **em Adicionar Provedor de Configurações da Câmera** e expanda a entrada Novas **configurações de câmera recém-adicionada.**</span><span class="sxs-lookup"><span data-stu-id="d2f90-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Expandir novo provedor de configurações](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="d2f90-115">Selecione o provedor Windows Mixed Reality configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="d2f90-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![Selecione Windows Mixed Reality de configurações](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="d2f90-117">Ao usar os perfis padrão do Microsoft Mixed Reality Toolkit, o provedor Windows Mixed Reality configurações de câmera já estará habilitado e configurado.</span><span class="sxs-lookup"><span data-stu-id="d2f90-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="d2f90-118">Configurando o provedor Windows Mixed Reality configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="d2f90-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="d2f90-119">O Windows Mixed Reality configurações da câmera também dá suporte a um perfil.</span><span class="sxs-lookup"><span data-stu-id="d2f90-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="d2f90-120">Esse perfil fornece as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="d2f90-120">This profile provides the following options:</span></span>

![Windows Mixed Reality configurações da câmera](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="d2f90-122">Renderizar a captura de realidade misturada da câmera de foto/vídeo</span><span class="sxs-lookup"><span data-stu-id="d2f90-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="d2f90-123">Com essa configuração no HoloLens 2, você pode habilitar o alinhamento de holograma em suas capturas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="d2f90-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="d2f90-124">Se habilitada, a plataforma fornecerá um HolographicCamera adicional ao aplicativo quando uma foto ou vídeo de captura de realidade misturada for tirado.</span><span class="sxs-lookup"><span data-stu-id="d2f90-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="d2f90-125">Este HolographicCamera fornece matrizes de exibição correspondentes ao local da câmera de foto/vídeo e fornece matrizes de projeção usando o campo de exibição câmera de foto/vídeo.</span><span class="sxs-lookup"><span data-stu-id="d2f90-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="d2f90-126">Isso garantirá que os hologramas, como malhas à mão, permaneçam alinhados visivelmente na saída do vídeo.</span><span class="sxs-lookup"><span data-stu-id="d2f90-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="d2f90-127">Método de Reprojeção do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d2f90-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="d2f90-128">Define o método inicial para a Reprojeção do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d2f90-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="d2f90-129">A recomendação padrão é usar a Reprojeção de profundidade, pois todas as partes da cena serão estabilizadas independentemente com base em sua distância do usuário.</span><span class="sxs-lookup"><span data-stu-id="d2f90-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="d2f90-130">Se os hologramas ainda aparecerem instáveis, tente garantir que todos os objetos tenham enviado corretamente sua profundidade para o buffer de profundidade.</span><span class="sxs-lookup"><span data-stu-id="d2f90-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="d2f90-131">Essa é, às vezes, uma configuração de sombreador.</span><span class="sxs-lookup"><span data-stu-id="d2f90-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="d2f90-132">Se a profundidade parecer ser enviada corretamente e a instabilidade ainda estiver presente, tente estabilização do autoplanar, que usa o buffer de profundidade para calcular um plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="d2f90-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="d2f90-133">Se um aplicativo não puder enviar dados de profundidade suficientes para que qualquer uma dessas opções seja utilizável, a Reprojeção do planar será fornecida como um fallback.</span><span class="sxs-lookup"><span data-stu-id="d2f90-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="d2f90-134">Esse método será baseado nos dados de ponto de foco fornecidos por um aplicativo por meio de [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span><span class="sxs-lookup"><span data-stu-id="d2f90-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="d2f90-135">Para atualizar o método de Reprojeção em tempo de execução, acesse o `WindowsMixedRealityReprojectionUpdater` seguinte:</span><span class="sxs-lookup"><span data-stu-id="d2f90-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="d2f90-136">Isso só precisa ser atualizado uma vez e o valor é reutilizado para todos os quadros subsequentes.</span><span class="sxs-lookup"><span data-stu-id="d2f90-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="d2f90-137">Se o método for atualizado com frequência, é recomendável armazenar em cache o resultado do `EnsureComponent` em vez de chamá-lo com frequência.</span><span class="sxs-lookup"><span data-stu-id="d2f90-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2f90-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2f90-138">See also</span></span>

- [<span data-ttu-id="d2f90-139">Visão geral do sistema de câmera</span><span class="sxs-lookup"><span data-stu-id="d2f90-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="d2f90-140">Criando um provedor de configurações de câmera</span><span class="sxs-lookup"><span data-stu-id="d2f90-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="d2f90-141">Renderizando a captura de realidade misturada da câmera PV</span><span class="sxs-lookup"><span data-stu-id="d2f90-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="d2f90-142">Reprojeção de Holographic</span><span class="sxs-lookup"><span data-stu-id="d2f90-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)