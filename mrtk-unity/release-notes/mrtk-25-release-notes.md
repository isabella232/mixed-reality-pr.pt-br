---
title: Notas de versão do MRTK 2,5
description: Notas de versão do MRTK versão 2,5
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: c9458e5236cc7de18eb27c3c3e13221a366c89a4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177514"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a><span data-ttu-id="ae3c9-104">notas de versão do Microsoft Mixed reality Toolkit 2,5</span><span class="sxs-lookup"><span data-stu-id="ae3c9-104">Microsoft Mixed Reality Toolkit 2.5 release notes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae3c9-105">há um problema de compilador conhecido que afeta os aplicativos criados para Microsoft HoloLens 2 usando ARM64.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-105">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="ae3c9-106">esse problema é corrigido atualizando Visual Studio 2019 para a versão 16,8 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-106">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="ae3c9-107">se não for possível atualizar Visual Studio, importe o `com.microsoft.mixedreality.toolkit.tools` pacote para aplicar uma solução alternativa.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-107">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new-in-254"></a><span data-ttu-id="ae3c9-108">O que há de novo no 2.5.4</span><span class="sxs-lookup"><span data-stu-id="ae3c9-108">What's new in 2.5.4</span></span>

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a><span data-ttu-id="ae3c9-109">Corrige um bug com a integração do Oculus ao usar o UPM</span><span class="sxs-lookup"><span data-stu-id="ae3c9-109">Fixes a bug with Oculus Integration when using UPM</span></span>

<span data-ttu-id="ae3c9-110">Ao usar UPM, o OculusXRSDKDeviceManagerProfile sempre teria seu [pré-fabricados definido como None na inicialização](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-110">When using UPM, the OculusXRSDKDeviceManagerProfile would always have its [prefabs set to None on startup](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span></span> <span data-ttu-id="ae3c9-111">Esta versão configura o Gerenciador de Dispositivos para apontar para um conjunto de trabalho de pré-fabricados na inicialização.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-111">This release configures the Device Manager to point to a working set of prefabs on startup.</span></span>

### <a name="fixes-an-issue-with-openxr-via-upm"></a><span data-ttu-id="ae3c9-112">Corrige um problema com o OpenXR via UPM</span><span class="sxs-lookup"><span data-stu-id="ae3c9-112">Fixes an issue with OpenXR via UPM</span></span>

<span data-ttu-id="ae3c9-113">corrige um problema em que os provedores de OpenXR não foram adicionados ao link.xml por padrão, fazendo com que novos projetos falhem na execução no dispositivo ao usar OpenXR e MRTK por meio do Gerenciador de Pacotes do Unity.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-113">Fixes an issue where the OpenXR providers weren't added to the link.xml by default, causing new projects to fail to run on-device when using OpenXR and MRTK via Unity's Package Manager.</span></span> <span data-ttu-id="ae3c9-114">Os projetos existentes que são atualizados ainda precisarão ser adicionados manualmente.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-114">Existing projects that are upgraded will still need this added manually.</span></span>

## <a name="whats-new-in-253"></a><span data-ttu-id="ae3c9-115">O que há de novo no 2.5.3</span><span class="sxs-lookup"><span data-stu-id="ae3c9-115">What's new in 2.5.3</span></span>

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a><span data-ttu-id="ae3c9-116">Corrige uma regressão com o Oculus introduzido no 2.5.2</span><span class="sxs-lookup"><span data-stu-id="ae3c9-116">Fixes a regression with Oculus introduced in 2.5.2</span></span>

<span data-ttu-id="ae3c9-117">o 2.5.2 introduziu [um problema de compilação ao integrar o SDK do Oculus](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-117">2.5.2 introduced [a build issue when integrating the Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span></span> <span data-ttu-id="ae3c9-118">Essa versão reverte esse problema.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-118">This release reverts that issue.</span></span>

## <a name="whats-new-in-252"></a><span data-ttu-id="ae3c9-119">O que há de novo no 2.5.2</span><span class="sxs-lookup"><span data-stu-id="ae3c9-119">What's new in 2.5.2</span></span>

### <a name="add-support-for-openxr"></a><span data-ttu-id="ae3c9-120">Adicionar suporte para OpenXR</span><span class="sxs-lookup"><span data-stu-id="ae3c9-120">Add support for OpenXR</span></span>

<span data-ttu-id="ae3c9-121">Foi adicionado o suporte inicial para o pacote de visualização do OpenXR da Unity e o pacote OpenXR da realidade misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-121">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="ae3c9-122">Consulte [a página Introdução ao MRTK/XRSDK, a](../configuration/getting-started-with-mrtk-and-xrsdk.md) [postagem do fórum do Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)ou a [documentação da Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-122">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](/windows/mixed-reality/develop/unity/openxr-getting-started) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae3c9-123">O OpenXR no Unity só tem suporte no Unity 2020,3 e superior.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-123">OpenXR in Unity is only supported on Unity 2020.3 and higher.</span></span>
> <span data-ttu-id="ae3c9-124">Ele também dá suporte apenas a compilações de x64, ARM e ARM64.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-124">It also only supports x64, ARM, and ARM64 builds.</span></span>

### <a name="boundary-visualization-errors-fixed"></a><span data-ttu-id="ae3c9-125">Erros de visualização de limite corrigidos</span><span class="sxs-lookup"><span data-stu-id="ae3c9-125">Boundary visualization errors fixed</span></span>

<span data-ttu-id="ae3c9-126">As visualizações de limite, como o piso ou as paredes, agora serão configuradas e visíveis corretamente em tempo de execução de acordo com o perfil de limite.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-126">Boundary visualizations, like the floor or walls, will now be properly configured and visible at runtime according to the boundary profile.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="ae3c9-127">MSBuild para suporte do Unity</span><span class="sxs-lookup"><span data-stu-id="ae3c9-127">MSBuild for Unity support</span></span>

<span data-ttu-id="ae3c9-128">o suporte para MSBuild para Unity foi removido da versão 2.5.2, para se alinhar com a [nova orientação de pacote do Unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-128">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="whats-new-in-251"></a><span data-ttu-id="ae3c9-129">O que há de novo na 2.5.1</span><span class="sxs-lookup"><span data-stu-id="ae3c9-129">What's new in 2.5.1</span></span>

### <a name="package-dependency-errors-fixed"></a><span data-ttu-id="ae3c9-130">Erros de dependência de pacote corrigidos</span><span class="sxs-lookup"><span data-stu-id="ae3c9-130">Package dependency errors fixed</span></span>

<span data-ttu-id="ae3c9-131">Esta versão corrige dependências de arquivo entre pacotes incorretas (por exemplo: arquivos em ativos padrão não referenciam mais arquivos na base).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-131">This release fixes incorrect inter-package file dependencies (ex: files in Standard Assets no longer incorrectly reference files in Foundation).</span></span> <span data-ttu-id="ae3c9-132">A versão 2.5.1 também adiciona uma dependência explícita na Pro de malha de texto.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-132">Version 2.5.1 also adds an explicit dependency on Text Mesh Pro.</span></span>

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a><span data-ttu-id="ae3c9-133">Sombreadores de pacote de ativos padrão copiados para ativos/MRTK/sombreadores</span><span class="sxs-lookup"><span data-stu-id="ae3c9-133">Standard Assets package shaders copied to Assets/MRTK/Shaders</span></span>

<span data-ttu-id="ae3c9-134">Quando o pacote de ativos padrão for instalado por meio do UPM, os sombreadores serão copiados para a pasta assets/MRTK/shaders para que eles não sejam mais imutáveis.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-134">When the Standard Assets package is installed via UPM, the shaders will be copied to the Assets/MRTK/Shaders folder so that they will no longer be immutable.</span></span> <span data-ttu-id="ae3c9-135">Isso resolve o problema de sombreadores atualizados para o pipeline de processamento universal (URP) para reverter o comportamento herdado na próxima vez que o projeto for carregado.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-135">This resolves the issue of shaders updated for the Universal Render Pipeline (URP) reverting the legacy behavior the next time the project is loaded.</span></span>

### <a name="fixed-teleport-cursor-sticking-to-hands"></a><span data-ttu-id="ae3c9-136">Correção do cursor teleport com mãos</span><span class="sxs-lookup"><span data-stu-id="ae3c9-136">Fixed teleport cursor sticking to hands</span></span>

<span data-ttu-id="ae3c9-137">Esta versão corrige um [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) em que o cursor de destino teleport pode ficar com os visuais à mão.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-137">This release fixes an [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) where the teleport destination cursor can stick to hand visuals.</span></span>

## <a name="whats-new-in-250"></a><span data-ttu-id="ae3c9-138">O que há de novo no 2.5.0</span><span class="sxs-lookup"><span data-stu-id="ae3c9-138">What's new in 2.5.0</span></span>

### <a name="unity-package-manager-upm-support"></a><span data-ttu-id="ae3c9-139">suporte a Gerenciador de Pacotes do Unity (UPM)</span><span class="sxs-lookup"><span data-stu-id="ae3c9-139">Unity Package Manager (UPM) support</span></span>

<span data-ttu-id="ae3c9-140">a realidade misturada Toolkit agora pode ser gerenciada usando o Gerenciador de Pacotes do Unity.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-140">The Mixed Reality Toolkit can now be managed using the Unity Package Manager.</span></span>

![Pacote UPM do MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="ae3c9-142">Há algumas etapas manuais necessárias para importar os pacotes MRTK UPM.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-142">There are some manual steps required to import the MRTK UPM packages.</span></span> <span data-ttu-id="ae3c9-143">examine a [realidade misturada Toolkit e Gerenciador de Pacotes do Unity](../configuration/usingupm.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-143">Please review [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md) for more information.</span></span>

### <a name="oculus-quest-xr-sdk-support"></a><span data-ttu-id="ae3c9-144">Suporte ao SDK do Oculus Quest XR</span><span class="sxs-lookup"><span data-stu-id="ae3c9-144">Oculus Quest XR SDK support</span></span>

<span data-ttu-id="ae3c9-145">O MRTK agora dá suporte à execução de headsets e controladores do Oculus Quest usando o pipeline do SDK do XR nativo.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-145">MRTK now supports running Oculus Quest Headsets and Controllers using the native XR SDK pipeline.</span></span> <span data-ttu-id="ae3c9-146">O acompanhamento à mão também tem suporte com o [pacote de integração do Oculus da Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) graças ao trabalho [de Eric Provencher](https://twitter.com/prvncher) no MRTK-Quest!</span><span class="sxs-lookup"><span data-stu-id="ae3c9-146">Hand tracking is also supported with the [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) thanks to [Eric Provencher's](https://twitter.com/prvncher) work on MRTK-Quest!</span></span>

<span data-ttu-id="ae3c9-147">Para obter instruções sobre como implantar seu dispositivo no Oculus Quest usando o novo pipeline, consulte o [Guia de instalação do Oculus Quest](../supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="ae3c9-147">For instructions on how to deploy your device on the Oculus Quest using the new pipeline, see the [Oculus Quest Setup Guide](../supported-devices/oculus-quest-mrtk.md)</span></span>

### <a name="scrolling-object-collection"></a><span data-ttu-id="ae3c9-148">Rolagem da coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="ae3c9-148">Scrolling Object Collection</span></span>

<span data-ttu-id="ae3c9-149">O componente MRTK UX foi atualizado a partir de um recurso experimental e oferece mais liberdade para o layout de conteúdo 3D de tamanhos diferentes com suporte adicional para objetos que não têm colisor anexados.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-149">The MRTK UX component has been upgraded from an experimental feature and offers more freedom for layouting 3D content of different sizes with added support for objects that have no colliders attached.</span></span> <span data-ttu-id="ae3c9-150">Uma nova opção para desabilitar a máscara de conteúdo também foi adicionada, facilitando a criação de protótipos.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-150">A new option for disabling content masking was also added, making prototyping easier.</span></span>

<span data-ttu-id="ae3c9-151">Consulte [rolagem de coleção de objetos](../features/ux-building-blocks/scrolling-object-collection.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-151">See [Scrolling Object Collection](../features/ux-building-blocks/scrolling-object-collection.md) for more information.</span></span>

![Rolagem da coleção de objetos](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a><span data-ttu-id="ae3c9-153">Animação de ponteiro teleport, manipulação e melhorias de som</span><span class="sxs-lookup"><span data-stu-id="ae3c9-153">Teleport pointer animation, handling, and sound improvements</span></span>

<span data-ttu-id="ae3c9-154">O ponteiro teleport agora tem animações e comentários de áudio aprimorados.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-154">The teleport pointer now has improved animations and audio feedback.</span></span> <span data-ttu-id="ae3c9-155">Também melhoramos a manipulação do ponteiro teleport para que ele lide mais suave ao fazer a transição para o ponto em superfícies próximas até as superfícies distantes.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-155">We also improved the handling of the teleport pointer so it handles smoother when transitioning from pointing at nearby surfaces to farther away surfaces.</span></span>

### <a name="input-simulation-cheat-sheet"></a><span data-ttu-id="ae3c9-156">Roteiro de simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="ae3c9-156">Input simulation cheat sheet</span></span>

<span data-ttu-id="ae3c9-157">A cena HandInteractionExamples agora tem um atalho configurável para mostrar uma página de ajuda para a simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="ae3c9-157">The HandInteractionExamples scene now has a configurable shortcut to show a help page for input simulation</span></span>

![Roteiro de simulação de entrada](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a><span data-ttu-id="ae3c9-159">Olhar de olho de simulação de entrada com o mouse</span><span class="sxs-lookup"><span data-stu-id="ae3c9-159">Input simulation eye gaze with mouse</span></span>

<span data-ttu-id="ae3c9-160">Agora, os usuários podem usar o mouse para simular o controle de olho.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-160">Users can now use the Mouse for simulating eye tracking.</span></span> <span data-ttu-id="ae3c9-161">Consulte o `Eye Simulation Mode` campo no perfil de simulação de entrada e defina-o como mouse.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-161">See the `Eye Simulation Mode` field in the input simulation profile and set it to Mouse.</span></span> <span data-ttu-id="ae3c9-162">Isso substitui o `Simulate Eye Position` campo anterior.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-162">This replaces the previous `Simulate Eye Position` field.</span></span>

![Mouse de olho olhar](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a><span data-ttu-id="ae3c9-164">Controlador de movimento de simulação de entrada no modo de reprodução do editor</span><span class="sxs-lookup"><span data-stu-id="ae3c9-164">Input simulation motion controller in editor Play Mode</span></span>

<span data-ttu-id="ae3c9-165">Agora, os usuários podem simular o controle de movimento como as mãos no modo de reprodução do editor.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-165">Users can now simulate motion controller just like hands in editor play mode.</span></span> <span data-ttu-id="ae3c9-166">No momento, há suporte para os botões gatilho, captura e menu.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-166">The trigger, grab and menu buttons are currently supported.</span></span>

### <a name="conical-grab-pointer"></a><span data-ttu-id="ae3c9-167">Ponteiro de captura cônica</span><span class="sxs-lookup"><span data-stu-id="ae3c9-167">Conical grab pointer</span></span>

<span data-ttu-id="ae3c9-168">Os ponteiros de captura agora podem ser configurados para consultar objetos próximos usando um cone do ponto de captura em vez de uma esfera.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-168">Grab pointers can now be configured to query for nearby objects using a cone from the grab point rather than a sphere.</span></span> <span data-ttu-id="ae3c9-169">isso é mais parecido com o comportamento da interface padrão HoloLens 2, que consulta objetos próximos usando um cone.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-169">This more closely resembles the behavior from the default HoloLens 2 interface, which queries for nearby objects using a cone.</span></span> <span data-ttu-id="ae3c9-170">O DefaultHoloLens2InputSystemProfile também foi ajustado para usar o novo `ConicalGrabPointer` .</span><span class="sxs-lookup"><span data-stu-id="ae3c9-170">The DefaultHoloLens2InputSystemProfile has also been adjusted to use the new `ConicalGrabPointer`.</span></span>

![Ponteiro de captura cônica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a><span data-ttu-id="ae3c9-172">Pacote TestUtilities</span><span class="sxs-lookup"><span data-stu-id="ae3c9-172">TestUtilities package</span></span>

<span data-ttu-id="ae3c9-173">Agora há um pacote (Microsoft. MixedReality. Toolkit. Unity. TestUtilities. 2.5.0. unitypackage) que contém a infraestrutura de teste PlayMode e testmode que o MRTK usa para criar testes de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-173">There is now a package (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage) that contains the PlayMode and TestMode test infrastructure that the MRTK uses to create end-to-end tests.</span></span> <span data-ttu-id="ae3c9-174">Essa infraestrutura foi extremamente útil para a equipe de MRTK em si, e estamos empolgados em ter consumidores que o utilizam para adicionar cobertura de teste a seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-174">This infrastructure has been extremely handy for the MRTK team itself, and we're excited to have consumers use this to add test coverage to their own projects.</span></span>

<span data-ttu-id="ae3c9-175">O código a seguir mostra como criar uma mão de teste, mostrá-la em um determinado local, movê-la e, em seguida, pinçar e abrir.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-175">The following code shows how to create a test hand, show it at a certain location, move it around, and then pinch and open.</span></span>

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

<span data-ttu-id="ae3c9-176">Para obter instruções sobre como escrever um teste usando esses TestUtilities, consulte esta seção sobre como [escrever testes](../contributing/unit-tests.md#writing-tests).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-176">For instructions on how to write a test using these TestUtilities, see this section on [writing tests](../contributing/unit-tests.md#writing-tests).</span></span>

<span data-ttu-id="ae3c9-177">Para obter exemplos de testes existentes que usam essa infraestrutura, consulte [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)da MRTK.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-177">For examples of existing tests that use this infrastructure, see MRTK's [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests).</span></span>

### <a name="support-for-the-leap-motion-451-unity-modules"></a><span data-ttu-id="ae3c9-178">Suporte para os módulos do movimento Leap 4.5.1 Unity</span><span class="sxs-lookup"><span data-stu-id="ae3c9-178">Support for the Leap Motion 4.5.1 Unity Modules</span></span>

<span data-ttu-id="ae3c9-179">O suporte para os módulos do Unity de movimento Leap versão 4.5.1 foi adicionado e o suporte para os ativos 4.4.0 foi removido.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-179">Support for the Leap Motion Unity Modules version 4.5.1 has been added and support for the 4.4.0 assets has been removed.</span></span> <span data-ttu-id="ae3c9-180">As versões atuais com suporte dos módulos do movimento bissexto do Unity são 4.5.0 e 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-180">The current supported versions of the Leap Motion Unity Modules are 4.5.0 and 4.5.1.</span></span>

<span data-ttu-id="ae3c9-181">Também há uma etapa adicional para a integração inicial do movimento Leap, consulte [como configurar o acompanhamento da mão de movimento Leap no MRTK](../supported-devices/leap-motion-mrtk.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-181">There is also an additional step for initial Leap Motion integration, see [How to Configure the Leap Motion Hand Tracking in MRTK](../supported-devices/leap-motion-mrtk.md) for more information.</span></span>

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a><span data-ttu-id="ae3c9-182">O observador de malha de conscientização espacial lida melhor com a personalização de materiais</span><span class="sxs-lookup"><span data-stu-id="ae3c9-182">Spatial Awareness Mesh Observer better handles customization of materials</span></span>

<span data-ttu-id="ae3c9-183">Com esta versão, o `Windows Mixed Reality Spatial Mesh Observer` e os `Generic XR SDK Spatial Mesh Observer` componentes melhoraram o manuseio de material visual.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-183">With this release, the `Windows Mixed Reality Spatial Mesh Observer` and the `Generic XR SDK Spatial Mesh Observer` components have improved visual material handling.</span></span> <span data-ttu-id="ae3c9-184">Os materiais agora são preservados quando uma malha é atualizada pelo observador, onde, anteriormente, eram redefinidos para o VisibleMaterial padrão, conforme configurado no perfil.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-184">Materials are now preserved when a mesh has been updated by the observer where, previously, they were reset to the default VisibleMaterial as configured in the profile.</span></span>

<span data-ttu-id="ae3c9-185">Isso permite que os desenvolvedores alterem o material de malha e não tenham as alterações substituídas inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-185">This enables developers to alter the mesh material and not have the changes overwritten unexpectedly.</span></span>

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a><span data-ttu-id="ae3c9-186">Link.xml criado na pasta MixedRealityToolkit. Generated</span><span class="sxs-lookup"><span data-stu-id="ae3c9-186">Link.xml created in the MixedRealityToolkit.Generated folder</span></span>

<span data-ttu-id="ae3c9-187">Com a introdução do Gerenciador de pacotes do Unity MRTK, o MRTK agora grava um `link.xml` arquivo na `Assets/MixedRealityToolkit.Generated` pasta, se nenhum estiver presente.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-187">With the introduction of Unity Package Manger MRTK, MRTK now writes a `link.xml` file to the `Assets/MixedRealityToolkit.Generated` folder, if none is present.</span></span> <span data-ttu-id="ae3c9-188">É recomendável adicionar esse arquivo (e `link.xml.meta` ) ser adicionado ao controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-188">It is recommended to add this file (and `link.xml.meta`) be added to source control.</span></span> <span data-ttu-id="ae3c9-189">Link.xml é usado para influenciar a funcionalidade de [remoção de código gerenciado](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) do vinculador do Unity.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-189">Link.xml is used to influence the [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) functionality of the Unity linker.</span></span>

<span data-ttu-id="ae3c9-190">Mais informações sobre o arquivo de link.xml MRTK podem ser encontradas no artigo [MRTK e a remoção de código gerenciado](../updates-deployment/mrtk-and-managed-code-stripping.md) .</span><span class="sxs-lookup"><span data-stu-id="ae3c9-190">More information on the MRTK link.xml file can be found in the [MRTK and managed code stripping](../updates-deployment/mrtk-and-managed-code-stripping.md) article.</span></span>

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a><span data-ttu-id="ae3c9-191">Unity 2019.3 +: a caixa de diálogo de configuração MRTK não tenta mais habilitar o suporte a XR herdado</span><span class="sxs-lookup"><span data-stu-id="ae3c9-191">Unity 2019.3+: MRTK configuration dialog no longer attempts to enable legacy XR support</span></span>

<span data-ttu-id="ae3c9-192">Para evitar possíveis conflitos ao usar a plataforma XR da Unity, a opção para habilitar o suporte a XR herdado foi removida da caixa de diálogo de configuração do MRTK.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-192">To avoid potential conflicts when using Unity's XR Platform, the option to enable legacy XR support has been removed from the MRTK configuration dialog.</span></span> <span data-ttu-id="ae3c9-193">se desejar, o suporte a XR herdado poderá ser habilitado, no Unity 2019, usando a realidade de **editar**  >  **Project Configurações**  >
 **Player**  >  **XR Configurações**  >  **com suporte**.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-193">If desired, legacy XR support can be enabled, in Unity 2019, using **Edit** > **Project Settings** >
**Player** > **XR Settings** > **Virtual Reality Supported**.</span></span>

### <a name="reduction-in-initializeonload-overhead"></a><span data-ttu-id="ae3c9-194">Redução na sobrecarga de InitializeOnLoad</span><span class="sxs-lookup"><span data-stu-id="ae3c9-194">Reduction in InitializeOnLoad overhead</span></span>

<span data-ttu-id="ae3c9-195">Estamos trabalhando para reduzir a quantidade de trabalho que é executada em manipuladores InitializeOnLoad, o que deve levar a melhorias na velocidade de desenvolvimento do loop interno.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-195">We've been doing work to reduce the amount of work that runs in InitializeOnLoad handlers, which should lead to improvements in inner loop development speed.</span></span> <span data-ttu-id="ae3c9-196">Os manipuladores InitializeOnLoad são executados toda vez que um script é compilado, antes da inserção do modo de reprodução e também na inicialização do editor.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-196">InitializeOnLoad handlers run every time a script is compiled, prior to entering play mode, and also at editor launch.</span></span> <span data-ttu-id="ae3c9-197">Esses manipuladores agora são executados em muito menos casos, resultando em melhorias gerais de capacidade de resposta do Unity.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-197">These handlers now run in far fewer cases, resulting in general Unity responsiveness improvements.</span></span>

<span data-ttu-id="ae3c9-198">Em alguns casos, houve uma compensação que tinha que ser feita:</span><span class="sxs-lookup"><span data-stu-id="ae3c9-198">In some cases there was a tradeoff that had to be made:</span></span>

- <span data-ttu-id="ae3c9-199">Confira [configuração de acompanhamento da mão de movimento Leap](../supported-devices/leap-motion-mrtk.md) para obter a etapa de integração extra.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-199">See [Leap Motion Hand Tracking Configuration](../supported-devices/leap-motion-mrtk.md) for the extra integration step.</span></span>
- <span data-ttu-id="ae3c9-200">Para aqueles que estão usando o ARFoundation, agora há uma etapa manual adicional em suas etapas de introdução.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-200">For those who are using ARFoundation, there's now an additional manual step in its getting started steps.</span></span>
  <span data-ttu-id="ae3c9-201">Consulte [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) para obter as novas etapas.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-201">See [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) for the new steps.</span></span>
- <span data-ttu-id="ae3c9-202">para aqueles que usarão a [comunicação remota do Holographic com o pipeline do XR herdado](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) no HoloLens 2, agora há uma [etapa manual](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) a ser executada.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-202">For those who will be using [Holographic Remoting with legacy XR pipeline](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) on HoloLens 2, there is now a [manual step](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) to perform.</span></span>

### <a name="bounds-control-graduated"></a><span data-ttu-id="ae3c9-203">Controle de limites graduado</span><span class="sxs-lookup"><span data-stu-id="ae3c9-203">Bounds control graduated</span></span>

![Controle de limites](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="ae3c9-205">O [controle de limites](../features/ux-building-blocks/bounds-control.md) foi graduado de forma experimental e vem com vários novos recursos e toneladas de correções de bugs.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-205">[Bounds control](../features/ux-building-blocks/bounds-control.md) graduated out of experimental and comes with a bunch of new features and tons of bug fixes.</span></span>
<span data-ttu-id="ae3c9-206">Aqui está uma lista dos destaques desta atualização:</span><span class="sxs-lookup"><span data-stu-id="ae3c9-206">Here a list of the highlights of this update:</span></span>

- <span data-ttu-id="ae3c9-207">as propriedades são divididas em configurações, o que torna mais fácil configurar o controle de limites</span><span class="sxs-lookup"><span data-stu-id="ae3c9-207">properties are split into configurations which makes it easier to set up bounds control</span></span>
- <span data-ttu-id="ae3c9-208">as configurações podem ser compartilhadas por meio de objetos programáveis</span><span class="sxs-lookup"><span data-stu-id="ae3c9-208">configurations can be shared through scriptable objects</span></span>
- <span data-ttu-id="ae3c9-209">cada propriedade de propriedade/script é configurável pelo tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ae3c9-209">every property / scriptable property is runtime configurable</span></span>
- <span data-ttu-id="ae3c9-210">o dispositivo de controle de limites não é mais recriado nas alterações de propriedade</span><span class="sxs-lookup"><span data-stu-id="ae3c9-210">bounds control rig isn't recreated on property changes anymore</span></span>
- <span data-ttu-id="ae3c9-211">suporte a identificadores de tradução</span><span class="sxs-lookup"><span data-stu-id="ae3c9-211">translation handles support</span></span>
- <span data-ttu-id="ae3c9-212">suporte completo a restrições por meio do Gerenciador de restrições</span><span class="sxs-lookup"><span data-stu-id="ae3c9-212">full constraint support through constraint manager</span></span>
- <span data-ttu-id="ae3c9-213">integração do sistema elásticos (experimental)</span><span class="sxs-lookup"><span data-stu-id="ae3c9-213">elastics system integration (experimental)</span></span>

<span data-ttu-id="ae3c9-214">A caixa delimitadora antiga foi preterida e os objetos de jogo existentes usando a caixa delimitadora podem ser [atualizados usando a ferramenta de migração](../features/tools/migration-window.md) ou o [inspetor da caixa delimitadora](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-214">The old bounding box is now deprecated and existing game objects using bounding box can be [upgraded using the migration tool](../features/tools/migration-window.md) or the [bounding box inspector](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control).</span></span>

### <a name="constraint-manager-component"></a><span data-ttu-id="ae3c9-215">Componente do Gerenciador de restrição</span><span class="sxs-lookup"><span data-stu-id="ae3c9-215">Constraint manager component</span></span>

<span data-ttu-id="ae3c9-216">As restrições agora podem ser usadas por ambos, controle de limites e objeto manipulador por meio do novo [componente Gerenciador de restrição](../features/ux-building-blocks/constraint-manager.md).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-216">Constraints can now be used by both, bounds control and object manipulator via the new [constraint manager component](../features/ux-building-blocks/constraint-manager.md).</span></span> <span data-ttu-id="ae3c9-217">Os dois componentes criarão um Gerenciador de restrição por padrão e processarão quaisquer restrições anexadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-217">Both components will create a constraint manager per default and process any attached constraints automatically.</span></span>

<span data-ttu-id="ae3c9-218">Além disso, o Gerenciador de restrição de comportamento automático também vem com um modo manual que permite aos usuários decidir qual restrição deve ser processada.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-218">Additionally to the automatic behavior constraint manager also comes with a manual mode that lets users decide which constraint should be processed.</span></span>
<span data-ttu-id="ae3c9-219">Por esse motivo, a maneira como exibimos restrições no Inspetor de propriedades mudou um pouco.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-219">For this reason the way we display constraints in the property inspector changed a bit.</span></span>

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

<span data-ttu-id="ae3c9-220">As restrições que são aplicadas ao componente agora são mostradas como uma lista no componente Gerenciador de restrição, enquanto o componente usando o Gerenciador de restrição ( [controle de limites](../features/ux-building-blocks/bounds-control.md#constraint-system) ou manipulador de [objeto](../features/ux-building-blocks/object-manipulator.md#constraint-manager)) agora mostrará o Gerenciador e o modo de restrição selecionado (automático ou manual).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-220">The constraints that are applied to the component are now shown as a list in the constraint manager component whereas the component using the constraint manager (either [bounds control](../features/ux-building-blocks/bounds-control.md#constraint-system) or [object manipulator](../features/ux-building-blocks/object-manipulator.md#constraint-manager)) will now show the selected constraint manager and mode (auto or manual).</span></span>
<span data-ttu-id="ae3c9-221">Para obter mais informações, leia a seção [Gerenciador de restrição](../features/ux-building-blocks/constraint-manager.md) em nossos documentos.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-221">For more information read the [constraint manager](../features/ux-building-blocks/constraint-manager.md) section in our docs.</span></span>

### <a name="hololens-2-button-material-update"></a><span data-ttu-id="ae3c9-222">atualização de material de botão HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ae3c9-222">HoloLens 2 button material update</span></span>

<span data-ttu-id="ae3c9-223">atualizado o material do compartimento frontal do botão HoloLens 2 para remover a cor preta na MRC.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-223">Updated HoloLens 2 button's front cage material to remove black color in MRC.</span></span>

![atualização de material de botão HoloLens 2](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a><span data-ttu-id="ae3c9-225">Atualização do painel de descrição, cena de exemplo móvel</span><span class="sxs-lookup"><span data-stu-id="ae3c9-225">Description panel update, movable example scene</span></span>

<span data-ttu-id="ae3c9-226">Painel de descrição atualizado.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-226">Updated description panel.</span></span> <span data-ttu-id="ae3c9-227">(SceneDescriptionPanelRev. pré-fabricado) o novo design fornece uma barra superior de captura que permite ao usuário ajustar/mover toda a cena.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-227">(SceneDescriptionPanelRev.prefab) New design provides a grabbable top bar which allows the user to adjust/move the entire scene.</span></span>

![Atualização do painel de descrição](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a><span data-ttu-id="ae3c9-229">Visualização de malha espacial-pulso no ar-toque</span><span class="sxs-lookup"><span data-stu-id="ae3c9-229">Spatial mesh visualization - pulse on air-tap</span></span>

<span data-ttu-id="ae3c9-230">exemplo atualizado de sombreador de pulso para a malha espacial para corresponder ao comportamento do shell do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-230">Updated pulse shader example for the spatial mesh to match HoloLens 2's shell behavior.</span></span>

![Pulso no ar-toque](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a><span data-ttu-id="ae3c9-232">Sistema elástico (experimental)</span><span class="sxs-lookup"><span data-stu-id="ae3c9-232">Elastic system (experimental)</span></span>

![System2 elástico](../features/images/elastics/Elastics_Main.gif)

<span data-ttu-id="ae3c9-234">O MRTK agora vem com um [sistema de simulação elástica](../features/experimental/elastic-system.md) que inclui uma ampla variedade de subclasses extensíveis e flexíveis, oferecendo associações para molas de quaternions bidimensionais, molas de volume tridimensionais e sistemas Spring lineares simples.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-234">MRTK now comes with an [elastic simulation system](../features/experimental/elastic-system.md) that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="ae3c9-235">Atualmente, os seguintes componentes do MRTK que dão suporte ao [Gerenciador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) podem aproveitar a funcionalidade de elásticos:</span><span class="sxs-lookup"><span data-stu-id="ae3c9-235">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="ae3c9-236">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="ae3c9-236">Bounds control</span></span>](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [<span data-ttu-id="ae3c9-237">Manipulador de objeto</span><span class="sxs-lookup"><span data-stu-id="ae3c9-237">Object manipulator</span></span>](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a><span data-ttu-id="ae3c9-238">Joystick (experimental)</span><span class="sxs-lookup"><span data-stu-id="ae3c9-238">Joystick (experimental)</span></span>

<span data-ttu-id="ae3c9-239">Um exemplo de interface de joystick que pode controlar um objeto de destino grande.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-239">An example of joystick interface that can control a large target object.</span></span>

![Botões](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a><span data-ttu-id="ae3c9-241">Seletor de cores (experimental)</span><span class="sxs-lookup"><span data-stu-id="ae3c9-241">Color picker (experimental)</span></span>

<span data-ttu-id="ae3c9-242">Um controle experimental que facilita a alteração de cores de material em qualquer objeto no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-242">An experimental control that makes it easy to change material colors on any object at runtime.</span></span>

![Três métodos diferentes de controle de seletor de cor](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![Quatro métodos diferentes de controle do seletor de cores](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a><span data-ttu-id="ae3c9-245">Alterações de quebra</span><span class="sxs-lookup"><span data-stu-id="ae3c9-245">Breaking changes</span></span>

### <a name="assembly-definition-files-changes"></a><span data-ttu-id="ae3c9-246">Alterações de arquivos de definição de assembly</span><span class="sxs-lookup"><span data-stu-id="ae3c9-246">Assembly definition files changes</span></span>

<span data-ttu-id="ae3c9-247">Alguns arquivos asmdef são alterados e agora têm suporte apenas para o Unity 2018.4.13 F1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-247">Some asmdef files are changed and are now only supporting Unity 2018.4.13f1 or later.</span></span> <span data-ttu-id="ae3c9-248">Erros de compilação serão exibidos ao atualizar para o MRTK 2,5 em versões anteriores do Unity.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-248">Compilation errors will show up when updating to MRTK 2.5 in earlier versions of Unity.</span></span> <span data-ttu-id="ae3c9-249">Isso pode ser corrigido acessando `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` na janela do projeto e removendo a referência ausente no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-249">This can be fixed by going to `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` in the project window and removing the missing reference in the inspector.</span></span> <span data-ttu-id="ae3c9-250">Repita essas etapas com `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` e `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` .</span><span class="sxs-lookup"><span data-stu-id="ae3c9-250">Repeat those steps with `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` and `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef`.</span></span> <span data-ttu-id="ae3c9-251">Observação Você deve reverter as alterações substituindo esses três arquivos asmdef por aqueles originais (ou seja, não modificados) ao atualizar para o Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-251">Note you must revert the changes by replacing those three asmdef files with original (i.e. unmodified) ones when upgrading to Unity 2019.</span></span>

### <a name="imixedrealitypointermediator"></a><span data-ttu-id="ae3c9-252">IMixedRealityPointerMediator</span><span class="sxs-lookup"><span data-stu-id="ae3c9-252">IMixedRealityPointerMediator</span></span>

<span data-ttu-id="ae3c9-253">Esta interface foi atualizada para ter uma nova função:</span><span class="sxs-lookup"><span data-stu-id="ae3c9-253">This interface has been updated to have a new function:</span></span>

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

<span data-ttu-id="ae3c9-254">Se você tiver um ponteiro personalizado mediador que não seja subclasse DefaultPointerMediator, será necessário implementar essa nova função.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-254">If you have a custom pointer mediator that doesn't subclass DefaultPointerMediator, you will need to implement this new function.</span></span> <span data-ttu-id="ae3c9-255">Consulte [esse problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) para obter mais informações sobre por que isso foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-255">See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) for more background on why this was added.</span></span> <span data-ttu-id="ae3c9-256">Isso foi adicionado para garantir que as preferências de ponteiro sejam passadas explicitamente para o mediador, em vez de terem sido feitas implicitamente com base na presença de um construtor que tirou um IPointerPreferences.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-256">This was added to ensure that pointer preferences would be explicitly passed to the mediator, rather than having it be implicitly done based on the presence of a constructor that took a IPointerPreferences.</span></span>

### <a name="rest--device-portal-api"></a><span data-ttu-id="ae3c9-257">API do portal do dispositivo/REST</span><span class="sxs-lookup"><span data-stu-id="ae3c9-257">Rest / Device Portal API</span></span>

<span data-ttu-id="ae3c9-258">A `UseSSL` propriedade estática foi movida de `Rest` para `DevicePortal` .</span><span class="sxs-lookup"><span data-stu-id="ae3c9-258">The `UseSSL` static property has been moved from `Rest` to `DevicePortal`.</span></span>

<span data-ttu-id="ae3c9-259">Se você fez isso anteriormente...</span><span class="sxs-lookup"><span data-stu-id="ae3c9-259">If you did this previously...</span></span>

```csharp
Rest.UseSSL = true
```

<span data-ttu-id="ae3c9-260">Faça isso agora...</span><span class="sxs-lookup"><span data-stu-id="ae3c9-260">Do this now...</span></span>

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a><span data-ttu-id="ae3c9-261">Link.xml</span><span class="sxs-lookup"><span data-stu-id="ae3c9-261">Link.xml</span></span>

<span data-ttu-id="ae3c9-262">se um aplicativo estava usando anteriormente a distribuição de NuGet do MRTK, o `link.xml` arquivo foi removido do pacote base.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-262">If an application was previously using the NuGet distribution of the MRTK, the `link.xml` file has been removed from the Foundation package.</span></span> <span data-ttu-id="ae3c9-263">Para restaurar as regras de preservação de código, abrir o projeto no Unity uma vez criará um `link.xml` arquivo padrão no `Assets/MixedRealityToolkit.Generated` .</span><span class="sxs-lookup"><span data-stu-id="ae3c9-263">To restore code preservation rules, opening the project in Unity once will create a default `link.xml` file in `Assets/MixedRealityToolkit.Generated`.</span></span> <span data-ttu-id="ae3c9-264">É recomendável que esse arquivo (e `link.xml.meta` ) seja adicionado ao controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-264">It is recommended that this file (and `link.xml.meta`) be added to source control.</span></span>

### <a name="transform-constraint-changes"></a><span data-ttu-id="ae3c9-265">Transformar alterações de restrição</span><span class="sxs-lookup"><span data-stu-id="ae3c9-265">Transform Constraint changes</span></span>

<span data-ttu-id="ae3c9-266">A propriedade TargetTransform foi marcada como obsoleta, pois não foi usada pelo sistema de restrição.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-266">TargetTransform property has been marked as obsolete as it wasn't used by constraint system.</span></span> <span data-ttu-id="ae3c9-267">A lógica de restrição se baseia na transformação passada para os métodos Initialize e Apply.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-267">Constraint logic is based on the transform passed into Initialize and Apply methods.</span></span> <span data-ttu-id="ae3c9-268">As restrições de usuário derivadas que dependem dessa propriedade podem armazenar em cache o TargetTransform em sua implementação armazenando a transformação do componente de restrição para obter o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-268">Derived user constraints that rely on this property can cache the TargetTransform in their implementation by storing the transform of the constraint component to achieve the same behavior.</span></span>

<span data-ttu-id="ae3c9-269">O tipo de dados de pose do mundo inicial armazenado foi `worldPoseOnManipulationStart` alterado de MixedRealityPose para MixedRealityTransform, que inclui o valor de escala local do objeto manipulado.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-269">The stored initial world pose `worldPoseOnManipulationStart` data type has been changed from MixedRealityPose to MixedRealityTransform, which includes the local scale value of the manipulated object.</span></span> <span data-ttu-id="ae3c9-270">Com essa alteração, não é mais necessário armazenar em cache separadamente quaisquer valores iniciais de escala.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-270">With this change it's not necessary to separately cache any initial scale values anymore.</span></span>

### <a name="new-property-in-imixedrealitydictationsystem"></a><span data-ttu-id="ae3c9-271">Nova propriedade em IMixedRealityDictationSystem</span><span class="sxs-lookup"><span data-stu-id="ae3c9-271">New property in IMixedRealityDictationSystem</span></span>

<span data-ttu-id="ae3c9-272">Uma nova propriedade foi `AudioClip` adicionada à interface IMixedRealityDictationSystem.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-272">A new property `AudioClip` has been added to the IMixedRealityDictationSystem interface.</span></span> <span data-ttu-id="ae3c9-273">A `AudioClip` Propriedade habilita o acesso ao clipe de áudio associado à sessão de ditado atual.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-273">The `AudioClip` property enables access to the audio clip associated with the current dictation session.</span></span> <span data-ttu-id="ae3c9-274">Os usuários devem implementar a propriedade em seus scripts que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-274">Users must implement the property in their scripts implementing the interface.</span></span>

### <a name="service-facades-turn-down"></a><span data-ttu-id="ae3c9-275">Desativação do serviço fachadas</span><span class="sxs-lookup"><span data-stu-id="ae3c9-275">Service facades turn down</span></span>

<span data-ttu-id="ae3c9-276">Os serviços fachadas estão sendo desativados em 2,5.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-276">Services facades are being turned down in 2.5.</span></span> <span data-ttu-id="ae3c9-277">Esse recurso foi originalmente adicionado para tornar a configuração dos perfis MRTK mais fácil (criando GameObjects falsificados na cena que representavam cada um dos serviços de MRTK).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-277">This feature was originally added to make configuration of the MRTK profiles easier (by creating fake in-scene GameObjects that represented each of MRTK's services).</span></span> <span data-ttu-id="ae3c9-278">A longo prazo, queremos evitar a criação de objetos falsos no jogo e tentar mantê-los em sincronia (como a sincronização de dados e os problemas de "origem de verdade" são notoriamente difíceis de dimensionar e chegar à direita).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-278">In the long run, we want to avoid creating fake in-game objects and trying to keep them in sync (as data sync and "source of truth" issues are notoriously difficult to scale and get right).</span></span>

<span data-ttu-id="ae3c9-279">Em 2,5, os manipuladores de fachada de serviço são mantidos para garantir que a atualização do projeto seja tranqüila. qualquer fachadas que exista no projeto será excluído pelo manipulador de fachada de serviço para garantir que as cenas abertas no 2,5 sejam corrigidas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-279">In 2.5, the service facade handlers are kept around to ensure that project upgrade goes smoothly - any facades that exist in the project will be deleted by the service facade handler to ensure that scenes opened up in 2.5 get automatically fixed.</span></span>

<span data-ttu-id="ae3c9-280">O código restante associado ao recurso de fachada do serviço será removido em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-280">The remaining code associated with the service facade feature will be removed in a future release.</span></span>

### <a name="addition-of-motion-controller-to-input-simulation-service"></a><span data-ttu-id="ae3c9-281">Adição de controlador de movimento ao serviço de simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="ae3c9-281">Addition of motion controller to input simulation service</span></span>

<span data-ttu-id="ae3c9-282">A simulação do controlador de movimento agora é oferecida no modo de reprodução do editor ao longo da simulação de mão existente.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-282">Motion controller simulation is now offered in editor play mode along side the existing hand simulation.</span></span> <span data-ttu-id="ae3c9-283">Para habilitar essa alteração, muitas funções/campos/propriedades atuais agora estão marcados como obsoletos, com `InputSimulationService.cs` e `MixedRealityInputSimulationProfile.cs` obtendo as alterações mais significativas.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-283">To enable this change, many current functions/fields/properties are now marked obsolete, with `InputSimulationService.cs` and `MixedRealityInputSimulationProfile.cs` getting the most significant changes.</span></span> <span data-ttu-id="ae3c9-284">A lógica e o comportamento do código relevante permanecem os mesmos amplamente, e a maioria das funções obsoletas, etc., estão relacionadas à substituição da referência a "mãos" para o termo mais genérico "Controller" (por exemplo, de `DefaultHandSimulationMode` para `DefaultControllerSimulationMode` ).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-284">The logic and behavior of relevant code largely remain the same, and the majority of obsoleted functions etc. are related to replacing reference to "hand" to the more generic term "controller" (e.g. from `DefaultHandSimulationMode` to `DefaultControllerSimulationMode`).</span></span> <span data-ttu-id="ae3c9-285">Além de obter novos nomes, o tipo de retorno de determinadas funções novas é atualizado para corresponder à alteração de nome/comportamento (por exemplo, `GetControllerDevice` com base no original `GetHandDevice` retornado `BaseController` , em vez de `SimulatedHand` ).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-285">Besides getting new names, the return type of certain new functions are updated to match the name/behavior change (e.g. `GetControllerDevice` based on the original `GetHandDevice` now returns `BaseController` instead of `SimulatedHand`).</span></span>

<span data-ttu-id="ae3c9-286">`IInputSimulationService` Agora tem novas propriedades `MotionControllerDataLeft` e `MotionControllerDataRight` .</span><span class="sxs-lookup"><span data-stu-id="ae3c9-286">`IInputSimulationService` now has new properties `MotionControllerDataLeft` and `MotionControllerDataRight`.</span></span> <span data-ttu-id="ae3c9-287">`MixedRealityInputSimulationProfile` Agora inclui novos campos para o mapeamento de teclado de certos botões do controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-287">`MixedRealityInputSimulationProfile` now includes new fields for the keyboard mapping of certain motion controller buttons.</span></span>

## <a name="known-issues"></a><span data-ttu-id="ae3c9-288">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="ae3c9-288">Known issues</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="ae3c9-289">CameraCache pode criar uma nova câmera ao desligar</span><span class="sxs-lookup"><span data-stu-id="ae3c9-289">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="ae3c9-290">Em algumas situações (por exemplo, ao usar o provedor LeapMotion no editor do Unity), é possível que o CameraCache recrie o MainCamera no desligamento.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-290">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="ae3c9-291">Consulte [este problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-291">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="ae3c9-292">FileNotFoundException quando exemplos são importados por meio do Unity Gerenciador de Pacotes</span><span class="sxs-lookup"><span data-stu-id="ae3c9-292">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="ae3c9-293">dependendo do tamanho do caminho do projeto, a importação de exemplos por meio do Unity Gerenciador de Pacotes poderá gerar mensagens FileNotFoundException no Console do Unity.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-293">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="ae3c9-294">A causa disso é o caminho para o arquivo "Missing" ter mais de MAX_PATH (256 caracteres).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-294">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="ae3c9-295">Para resolver, reduza o tamanho do caminho do projeto.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-295">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="ae3c9-296">Nenhum spatializer foi especificado.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-296">No spatializer was specified.</span></span> <span data-ttu-id="ae3c9-297">O aplicativo não dará suporte a som espacial</span><span class="sxs-lookup"><span data-stu-id="ae3c9-297">The application will not support Spatial Sound</span></span>

<span data-ttu-id="ae3c9-298">Um aviso "nenhum spatializer foi especificado" será exibido se um spatializer de áudio não estiver configurado.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-298">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="ae3c9-299">Isso pode ocorrer se nenhum pacote do XR estiver instalado, pois o Unity inclui spatializers nesses pacotes.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-299">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="ae3c9-300">Para resolver, verifique se:</span><span class="sxs-lookup"><span data-stu-id="ae3c9-300">To resolve, please ensure that:</span></span>

- <span data-ttu-id="ae3c9-301">**Janela**  >  do **Gerenciador de Pacotes** tem um ou mais pacotes XR instalados</span><span class="sxs-lookup"><span data-stu-id="ae3c9-301">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="ae3c9-302">**Realidade misturada Toolkit**  >  **Utilitários**  >  do **configurar Project do Unity** e fazer uma seleção para **Spatializer de áudio**</span><span class="sxs-lookup"><span data-stu-id="ae3c9-302">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![Selecionar áudio Spatializer](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="ae3c9-304">NullReferenceException: referência de objeto não definida para uma instância de um objeto (SceneTransitionService.Initialize)</span><span class="sxs-lookup"><span data-stu-id="ae3c9-304">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="ae3c9-305">Em algumas situações, `EyeTrackingDemo-00-RootScene` a abertura pode causar uma NullReferenceException no método Initialize da classe SceneTransitionService.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-305">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="ae3c9-306">Esse erro ocorre devido à desdefinição do perfil de configuração do serviço de transição de cena.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-306">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="ae3c9-307">Para resolver, use as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ae3c9-307">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="ae3c9-308">Navegar até o `MixedRealityToolkit` objeto na hierarquia</span><span class="sxs-lookup"><span data-stu-id="ae3c9-308">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="ae3c9-309">Na janela Inspetor, selecione `Extensions`</span><span class="sxs-lookup"><span data-stu-id="ae3c9-309">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="ae3c9-310">Se não for expandido, expanda `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="ae3c9-310">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="ae3c9-311">Defina o valor de `Configuration Profile` como **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="ae3c9-311">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![Corrigir transição de cena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="ae3c9-313">Solicitação Oculus</span><span class="sxs-lookup"><span data-stu-id="ae3c9-313">Oculus Quest</span></span>

<span data-ttu-id="ae3c9-314">Atualmente, há um problema conhecido para usar o [plug-in OCULUS XR com o direcionamento de plataformas autônomas](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span><span class="sxs-lookup"><span data-stu-id="ae3c9-314">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span> <span data-ttu-id="ae3c9-315">Verifique o Oculus Bug Tracker/fóruns/notas de versão para obter atualizações.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-315">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="ae3c9-316">O bug é representado com esse conjunto de três erros:</span><span class="sxs-lookup"><span data-stu-id="ae3c9-316">The bug is signified with this set of 3 errors:</span></span>

![Erro de plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="ae3c9-318">UnityUI e TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="ae3c9-318">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="ae3c9-319">Há um problema conhecido para as versões mais recentes do TextMeshPro (1.5.0 + ou 2.1.1 +), em que o tamanho da fonte padrão para os menus suspensos e o espaçamento de caracteres de fonte em negrito foi alterado.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-319">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![Imagem TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="ae3c9-321">Isso pode ser solucionado por meio do downgrade para uma versão anterior do TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-321">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="ae3c9-322">Consulte o [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="ae3c9-322">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
