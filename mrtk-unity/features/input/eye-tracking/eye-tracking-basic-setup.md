---
title: Configuração básica de acompanhamento ocular
description: Como configurar o Acompanhamento Ocular no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Acompanhamento Ocular,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144090"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="5a1f6-104">Como começar a acompanhar o acompanhamento ocular no MRTK</span><span class="sxs-lookup"><span data-stu-id="5a1f6-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="5a1f6-105">Esta página aborda como configurar sua cena do MRTK do Unity para usar o acompanhamento ocular em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="5a1f6-106">O exemplo a seguir pressu que você está começando com uma nova cena.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="5a1f6-107">Como alternativa, você pode conferir nossos exemplos de acompanhamento ocular do [MRTK](../../example-scenes/eye-tracking-examples-overview.md) já configurados com vários exemplos excelentes nos quais você pode se basear diretamente.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="5a1f6-108">Lista de verificação de requisitos de acompanhamento ocular</span><span class="sxs-lookup"><span data-stu-id="5a1f6-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="5a1f6-109">Para que o acompanhamento ocular funcione corretamente, os requisitos a seguir devem ser atendidos.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="5a1f6-110">Se você for novo no acompanhamento ocular no HoloLens 2 e em como o acompanhamento ocular está definido no MRTK, não se preocupe!</span><span class="sxs-lookup"><span data-stu-id="5a1f6-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="5a1f6-111">Entraremos em detalhes sobre como abordar cada um deles mais adiante.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="5a1f6-112">Um _'Eye Gaze Provedor de Dados'_ deve ser adicionado ao sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="5a1f6-113">Isso fornece dados de acompanhamento ocular da plataforma.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="5a1f6-114">A _funcionalidade 'GazeInput'_ deve ser habilitada no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="5a1f6-115">**Essa funcionalidade pode ser definida no Unity 2019, mas no Unity 2018 e anterior, essa funcionalidade só está disponível no Visual Studio e por meio da ferramenta de build do MRTK**</span><span class="sxs-lookup"><span data-stu-id="5a1f6-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="5a1f6-116">O HoloLens **deve** ser calibrado com o olhar para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="5a1f6-117">Confira nosso exemplo [para detectar se um usuário está calibrado com o olhar ou não.](eye-tracking-is-user-calibrated.md)</span><span class="sxs-lookup"><span data-stu-id="5a1f6-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="5a1f6-118">Uma observação sobre a funcionalidade GazeInput</span><span class="sxs-lookup"><span data-stu-id="5a1f6-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="5a1f6-119">As ferramentas de build fornecidas pelo MRTK (ou seja, Kit de Ferramentas de Realidade Misturada -> Utilities -> Build Window) podem habilitar automaticamente a funcionalidade GazeInput para você.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="5a1f6-120">Para fazer isso, você precisa verificar se a 'Funcionalidade de Entrada do Olhar' está marcada na guia 'Opções de Build do Appx':</span><span class="sxs-lookup"><span data-stu-id="5a1f6-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![Ferramentas de build do MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="5a1f6-122">Essa ferramenta encontrará o manifesto do AppX após a conclusão da compilação do Unity e adicionará manualmente o recurso GazeInput.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="5a1f6-123">**Antes do Unity 2019, essas ferramentas não estão ativas ao usar a janela de compilação interna do Unity** (ou seja, configurações de compilação de > de arquivo).</span><span class="sxs-lookup"><span data-stu-id="5a1f6-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="5a1f6-124">Antes do Unity 2019, ao usar a janela de compilação do Unity, a capacidade precisará ser adicionada manualmente após a compilação do Unity, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5a1f6-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="5a1f6-125">Abra seu projeto do Visual Studio compilado e, em seguida, abra o _' Package. appxmanifest '_ em sua solução.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="5a1f6-126">Certifique-se de marcar a caixa de seleção _' GazeInput '_ em _recursos_.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="5a1f6-127">Se você não vir uma funcionalidade _' GazeInput '_ , verifique se o seu sistema atende aos [pré-requisitos para usar o MRTK](/windows/mixed-reality/develop/install-the-tools) (em particular a versão de SDK do Windows).</span><span class="sxs-lookup"><span data-stu-id="5a1f6-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="5a1f6-128">_Observação:_ Você só precisa fazer isso se criar uma nova pasta de compilação.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="5a1f6-129">Isso significa que, se você já tiver criado seu projeto do Unity e configurado o appxmanifest antes e agora direcionar a mesma pasta novamente, não será necessário reaplicar as alterações.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="5a1f6-130">Configurando passo a passo de acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="5a1f6-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="5a1f6-131">Configurando a cena</span><span class="sxs-lookup"><span data-stu-id="5a1f6-131">Setting up the scene</span></span>

<span data-ttu-id="5a1f6-132">Configure o _MixedRealityToolkit_ simplesmente clicando em _' Mixed Reality Toolkit-> configurar... '_</span><span class="sxs-lookup"><span data-stu-id="5a1f6-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="5a1f6-133">na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-133">in the menu bar.</span></span>

![Configurar MRTK](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="5a1f6-135">Configurando os perfis de MRTK necessários para acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="5a1f6-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="5a1f6-136">Depois de configurar sua cena do MRTK, você será solicitado a escolher um perfil para MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="5a1f6-137">Você pode simplesmente selecionar _DefaultMixedRealityToolkitConfigurationProfile_ e, em seguida, selecionar a opção _' Copy & Custom '_ .</span><span class="sxs-lookup"><span data-stu-id="5a1f6-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![Perfil de MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="5a1f6-139">Criar um "provedor de dados olhar de olho"</span><span class="sxs-lookup"><span data-stu-id="5a1f6-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="5a1f6-140">Clique na guia _' entrada '_ em seu perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="5a1f6-141">Para editar um padrão ( _' DefaultMixedRealityInputSystemProfile '_ ), clique no botão _' clonar '_ ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="5a1f6-142">Um menu _'Clonar Perfil'_ é exibido.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="5a1f6-143">Basta clicar _em "Clonar"_ na parte inferior desse menu.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="5a1f6-144">Clique duas vezes em seu novo perfil de entrada, expanda _"Provedores_ de Dados de Entrada" e selecione _'+ Adicionar Provedor de Dados'._</span><span class="sxs-lookup"><span data-stu-id="5a1f6-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="5a1f6-145">Crie um novo provedor de dados:</span><span class="sxs-lookup"><span data-stu-id="5a1f6-145">Create a new data provider:</span></span>
  - <span data-ttu-id="5a1f6-146">Em **Tipo,** _selecione 'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_  ->  _'WindowsMixedRealityEyeGazeDataProvider'_</span><span class="sxs-lookup"><span data-stu-id="5a1f6-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="5a1f6-147">Para **Plataformas,** selecione _'Windows Universal'._</span><span class="sxs-lookup"><span data-stu-id="5a1f6-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![Provedor de dados do MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="5a1f6-149">Simulando o acompanhamento ocular no Editor do Unity</span><span class="sxs-lookup"><span data-stu-id="5a1f6-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="5a1f6-150">Você pode simular a entrada de acompanhamento ocular no Editor do Unity para garantir que os eventos sejam disparados corretamente antes de implantar o aplicativo no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="5a1f6-151">O sinal de olhar é simulado simplesmente usando a localização da câmera como origem do olhar e o vetor de avanço da câmera como direção do olhar.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="5a1f6-152">Embora isso seja ótimo para testes iniciais, observe que ele não é uma boa ideia para movimentos de olho rápidos.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="5a1f6-153">Para isso, é melhor garantir testes frequentes de suas interações com base no olhar no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="5a1f6-154">**Habilitar o acompanhamento ocular simulado:**</span><span class="sxs-lookup"><span data-stu-id="5a1f6-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="5a1f6-155">Clique na guia _"Entrada"_ no perfil de configuração do MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="5a1f6-156">A partir daí, navegue até _'Provedores de Dados de Entrada'_  ->  _'Serviço de Simulação de Entrada'._</span><span class="sxs-lookup"><span data-stu-id="5a1f6-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="5a1f6-157">Clone _o 'DefaultMixedRealityInputSimpulationProfile'_ para fazer alterações nele.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="5a1f6-158">Marque a _caixa de seleção 'Simular posição ocular'._</span><span class="sxs-lookup"><span data-stu-id="5a1f6-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![Simular os olhos do MRTK](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="5a1f6-160">**Desabilitar o cursor** de olhar para a cabeça padrão: em geral, é recomendável evitar mostrar um cursor de olhar ou, se absolutamente necessário, torná-lo _muito_ sutil.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="5a1f6-161">É recomendável ocultar o cursor de olhar para a cabeça padrão anexado ao perfil do ponteiro de olhar do MRTK por padrão.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="5a1f6-162">Navegue até o perfil de configuração do MRTK-> _'_  ->  _ponteiros_ ' de entrada '</span><span class="sxs-lookup"><span data-stu-id="5a1f6-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="5a1f6-163">Clone o _' DefaultMixedRealityInputPointerProfile '_ para fazer alterações nele.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="5a1f6-164">Na parte superior das _' configurações do ponteiro '_, você deve atribuir um cursor invisível pré-fabricado ao _' GazeCursor '_.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="5a1f6-165">Você pode fazer isso selecionando o pré-fabricado _' EyeGazeCursor '_ do MRTK Foundation.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="5a1f6-166">Habilitando olhar com base nos olhos no provedor olhar</span><span class="sxs-lookup"><span data-stu-id="5a1f6-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="5a1f6-167">No HoloLens v1, o Head olhar foi usado como uma técnica apontadora primária.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="5a1f6-168">Embora o Head olhar ainda esteja disponível por meio do _GazeProvider_ no MRTK que está anexado à sua [câmera](https://docs.unity3d.com/ScriptReference/Camera.html), você pode marcar para usar o olho olhar em vez disso, marcando a caixa de seleção _' IsEyeTrackingEnabled '_ nas configurações de olhar do perfil de ponteiro de entrada.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="5a1f6-169">Os desenvolvedores podem alternar entre olhar com base nos olhos e olhars baseados em cabeçalho no código, alterando a propriedade _' IsEyeTrackingEnabled '_ de _' GazeProvider '_.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="5a1f6-170">Se qualquer um dos requisitos de acompanhamento de olho não for atendido, o aplicativo voltará automaticamente para o olhar baseado em cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="5a1f6-171">Acessando dados de olhar de olho</span><span class="sxs-lookup"><span data-stu-id="5a1f6-171">Accessing eye gaze data</span></span>

<span data-ttu-id="5a1f6-172">Agora que sua cena está configurada para usar o acompanhamento de olho, vamos dar uma olhada em como acessá-la em seus scripts: [acessar dados de controle de olho por meio de EyeGazeProvider](eye-tracking-eye-gaze-provider.md) e [seleções de destino com suporte de olho](eye-tracking-target-selection.md).</span><span class="sxs-lookup"><span data-stu-id="5a1f6-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="5a1f6-173">Testando seu aplicativo Unity em um HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5a1f6-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="5a1f6-174">Criar seu aplicativo com acompanhamento de olho deve ser semelhante a como você compilaria outros aplicativos do HoloLens 2 MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="5a1f6-175">Verifique se você habilitou a funcionalidade *' entrada olhar '* , conforme descrito acima na seção [*uma observação sobre o recurso GazeInput*](#a-note-on-the-gazeinput-capability).</span><span class="sxs-lookup"><span data-stu-id="5a1f6-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="5a1f6-176">Calibragem de olho</span><span class="sxs-lookup"><span data-stu-id="5a1f6-176">Eye calibration</span></span>

<span data-ttu-id="5a1f6-177">Por fim, não se esqueça de executar a calibragem de olho no seu HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="5a1f6-178">O sistema de controle de olho não retornará nenhuma entrada se o usuário não for calibrado.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="5a1f6-179">A maneira mais fácil de chegar à calibragem é folhear o visor e fazer o backup.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="5a1f6-180">Uma notificação do sistema deve aparecer de boas-vindas como um novo usuário e pedindo que você passe pela calibragem de olho.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="5a1f6-181">Como alternativa, você pode encontrar a calibragem de olho nas configurações do sistema: configurações > sistema > calibragem > executar calibragem de olhos.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="5a1f6-182">Permissão de acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="5a1f6-182">Eye tracking permission</span></span>

<span data-ttu-id="5a1f6-183">Ao iniciar o aplicativo no seu HoloLens 2 pela primeira vez, um prompt deve ser exibido solicitando ao usuário a permissão para usar o controle ocular.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="5a1f6-184">Se não estiver aparecendo, isso geralmente é uma indicação de que a funcionalidade _' GazeInput '_ não foi definida.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="5a1f6-185">Depois que o prompt de permissão for mostrado uma vez, ele não será exibido automaticamente de novo.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="5a1f6-186">Se você _"negou a permissão de acompanhamento de olho"_, poderá redefinir isso em configurações-> privacidade-> aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="5a1f6-187">Isso deve ajudá-lo a começar a usar o acompanhamento de olho em seu aplicativo do MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="5a1f6-188">Não se esqueça de conferir [nossos tutoriais e exemplos de acompanhamento de olho do MRTK](../../example-scenes/eye-tracking-examples-overview.md) demonstrando como usar a entrada de controle de olho e fornecer convenientemente os scripts que podem ser reutilizados em seus projetos.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="5a1f6-189">Voltar para "acompanhamento de olho no MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="5a1f6-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)