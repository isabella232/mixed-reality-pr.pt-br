---
title: Guia de configuração da realidade misturada
description: Documentação para configurar o MRTK no Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: fc97a2d7c6182b4836d644d91be237e2aef01feb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143573"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="460bc-104">Guia de configuração do perfil do reality Toolkit misto</span><span class="sxs-lookup"><span data-stu-id="460bc-104">Mixed Reality Toolkit profile configuration guide</span></span>

![Logotipo do MRTK](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="460bc-106">O kit de ferramentas de realidade misturada centraliza a maior parte da configuração necessária para gerenciar o kit de ferramentas o máximo possível (exceto para "coisas" de tempo de execução verdadeiras).</span><span class="sxs-lookup"><span data-stu-id="460bc-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="460bc-107">Este guia é uma explicação simples para cada uma das telas de perfil de configuração disponíveis atualmente para o kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="460bc-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="460bc-108">O principal Perfil de configuração do kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="460bc-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="460bc-109">O principal Perfil de configuração, que é anexado ao gameobject *MixedRealityToolkit* em sua cena, fornece o ponto de entrada principal para o kit de ferramentas em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="460bc-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="460bc-110">O kit de ferramentas de realidade misturada "bloqueia" as telas de configuração padrão para garantir que você sempre tenha um ponto de partida comum para seu projeto e seja incentivado a começar a definir suas próprias configurações à medida que seu projeto evolui.</span><span class="sxs-lookup"><span data-stu-id="460bc-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="460bc-111">A configuração MRTK não é editável durante o modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="460bc-111">The MRTK configuration is not editable during play-mode.</span></span>

![Perfil de configuração do MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="460bc-113">Todos os perfis "padrão" do kit de ferramentas de realidade misturada podem ser encontrados no projeto do SDK na pasta ativos/MRTK/SDK/perfis.</span><span class="sxs-lookup"><span data-stu-id="460bc-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="460bc-114">DefaultHoloLens2ConfigurationProfile é otimizado para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="460bc-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="460bc-115">Consulte [perfis](../features/profiles/profiles.md) para obter os detalhes.</span><span class="sxs-lookup"><span data-stu-id="460bc-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="460bc-116">Ao abrir o principal Perfil de configuração do kit de ferramentas de realidade misturada, você verá a tela a seguir no Inspetor:</span><span class="sxs-lookup"><span data-stu-id="460bc-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="460bc-117">Se você selecionar um ativo MixedRealityToolkitConfigurationProfile sem o MixedRealityToolkit na cena, ele perguntará se você deseja que o MRTK configure automaticamente a cena para você.</span><span class="sxs-lookup"><span data-stu-id="460bc-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="460bc-118">Isso é opcional, no entanto, deve haver um objeto MixedRealityToolkit ativo na cena para acessar todas as telas de configuração.</span><span class="sxs-lookup"><span data-stu-id="460bc-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="460bc-119">Isso abriga a configuração atual de tempo de execução ativo para o projeto.</span><span class="sxs-lookup"><span data-stu-id="460bc-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="460bc-120">A partir daqui, você pode navegar para todos os perfis de configuração para o MRTK, incluindo:</span><span class="sxs-lookup"><span data-stu-id="460bc-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="460bc-121">Guia de configuração do perfil do reality Toolkit misto</span><span class="sxs-lookup"><span data-stu-id="460bc-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="460bc-122">O principal Perfil de configuração do kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="460bc-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="460bc-123">Configurações da experiência</span><span class="sxs-lookup"><span data-stu-id="460bc-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="460bc-124">Configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="460bc-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="460bc-125">Configurações do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="460bc-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="460bc-126">Configurações de visualização de limite</span><span class="sxs-lookup"><span data-stu-id="460bc-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="460bc-127">Seleção do sistema de teletransporte</span><span class="sxs-lookup"><span data-stu-id="460bc-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="460bc-128">Configurações de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="460bc-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="460bc-129">Configurações de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="460bc-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="460bc-130">Configurações do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="460bc-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="460bc-131">Configurações de serviços adicionais</span><span class="sxs-lookup"><span data-stu-id="460bc-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="460bc-132">Configurações de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="460bc-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="460bc-133">Regras de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="460bc-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="460bc-134">Configuração do ponteiro</span><span class="sxs-lookup"><span data-stu-id="460bc-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="460bc-135">Configuração de gestos</span><span class="sxs-lookup"><span data-stu-id="460bc-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="460bc-136">Comandos de fala</span><span class="sxs-lookup"><span data-stu-id="460bc-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="460bc-137">Configuração de mapeamento do controlador</span><span class="sxs-lookup"><span data-stu-id="460bc-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="460bc-138">Configurações de visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="460bc-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="460bc-139">Utilitários do editor</span><span class="sxs-lookup"><span data-stu-id="460bc-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="460bc-140">Inspetores de serviço</span><span class="sxs-lookup"><span data-stu-id="460bc-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="460bc-141">Renderização de buffer de profundidade</span><span class="sxs-lookup"><span data-stu-id="460bc-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="460bc-142">Alterando perfis em runtime</span><span class="sxs-lookup"><span data-stu-id="460bc-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="460bc-143">Opção de perfil de inicialização do MRTK</span><span class="sxs-lookup"><span data-stu-id="460bc-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="460bc-144">Opção de perfil ativo</span><span class="sxs-lookup"><span data-stu-id="460bc-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="460bc-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="460bc-145">See also</span></span>](#see-also)

<span data-ttu-id="460bc-146">Esses perfis de configuração são detalhados abaixo em suas seções relevantes:</span><span class="sxs-lookup"><span data-stu-id="460bc-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="460bc-147">Configurações da experiência</span><span class="sxs-lookup"><span data-stu-id="460bc-147">Experience settings</span></span>

<span data-ttu-id="460bc-148">Localizada na página principal de configuração do kit de ferramentas de realidade misturada, essa configuração define a operação padrão da [escala de ambiente da realidade misturada](/windows/mixed-reality/coordinate-systems-in-unity) para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="460bc-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="460bc-149">Configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="460bc-149">Camera settings</span></span>

<span data-ttu-id="460bc-150">As configurações da câmera definem como a câmera será configurada para o projeto de realidade misturada, definindo as configurações de recorte genérico, qualidade e transparência.</span><span class="sxs-lookup"><span data-stu-id="460bc-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="460bc-151">Configurações do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="460bc-151">Input system settings</span></span>

<span data-ttu-id="460bc-152">O projeto de realidade misturada fornece um sistema de entrada robusto e bem treinado para rotear todos os eventos de entrada em relação ao projeto que é selecionado por padrão.</span><span class="sxs-lookup"><span data-stu-id="460bc-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="460bc-153">Por trás do sistema de entrada fornecido pelo MRTK são vários outros sistemas, eles ajudam a impulsionar e gerenciar o complexo weavings necessário para abstrair as complexidades de uma estrutura de realidade mista de várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="460bc-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="460bc-154">Cada um dos perfis individuais é detalhado abaixo:</span><span class="sxs-lookup"><span data-stu-id="460bc-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="460bc-155">Configurações de foco</span><span class="sxs-lookup"><span data-stu-id="460bc-155">Focus Settings</span></span>
- [<span data-ttu-id="460bc-156">Configurações de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="460bc-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="460bc-157">Regras de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="460bc-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="460bc-158">Configuração do ponteiro</span><span class="sxs-lookup"><span data-stu-id="460bc-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="460bc-159">Configuração de gestos</span><span class="sxs-lookup"><span data-stu-id="460bc-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="460bc-160">Comandos de fala</span><span class="sxs-lookup"><span data-stu-id="460bc-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="460bc-161">Configuração de mapeamento de controlador</span><span class="sxs-lookup"><span data-stu-id="460bc-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="460bc-162">Configurações de visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="460bc-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="460bc-163">Configurações de visualização de limite</span><span class="sxs-lookup"><span data-stu-id="460bc-163">Boundary visualization settings</span></span>

<span data-ttu-id="460bc-164">O sistema de limite traduz o limite percebido relatado pelo sistema de limite/guardião de plataformas subjacentes.</span><span class="sxs-lookup"><span data-stu-id="460bc-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="460bc-165">A configuração do Visualizador de limite fornece a capacidade de mostrar automaticamente o limite registrado em sua cena em relação à posição do usuário. O limite também reagirá/será atualizado com base em onde o usuário portará dentro da cena.</span><span class="sxs-lookup"><span data-stu-id="460bc-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="460bc-166">Seleção do sistema de teleportabilidade</span><span class="sxs-lookup"><span data-stu-id="460bc-166">Teleportation system selection</span></span>

<span data-ttu-id="460bc-167">O projeto de realidade mista fornece um sistema de teleportabilidade completo para gerenciar eventos de teleportação no projeto que é selecionado por padrão.</span><span class="sxs-lookup"><span data-stu-id="460bc-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="460bc-168">Configurações de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="460bc-168">Spatial awareness settings</span></span>

<span data-ttu-id="460bc-169">O projeto de realidade misturada fornece um sistema de conscientização espacial recriado para trabalhar com sistemas de verificação espacial no projeto que é selecionado por padrão.</span><span class="sxs-lookup"><span data-stu-id="460bc-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="460bc-170">A configuração de reconhecimento espacial do kit de ferramentas de realidade misturada permite que você personalize a forma como o sistema é iniciado, seja automaticamente quando o aplicativo é iniciado ou mais tarde de forma programática, bem como a definição das extensões para o campo de exibição.</span><span class="sxs-lookup"><span data-stu-id="460bc-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="460bc-171">Ele também permite que você defina as configurações de malha e superfície, personalizando ainda mais a forma como o seu projeto compreende o ambiente em relação a você.</span><span class="sxs-lookup"><span data-stu-id="460bc-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="460bc-172">Isso só é aplicável a dispositivos que podem fornecer um ambiente examinado.</span><span class="sxs-lookup"><span data-stu-id="460bc-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="460bc-173">Configurações de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="460bc-173">Diagnostics settings</span></span>

<span data-ttu-id="460bc-174">Um recurso opcional, mas altamente útil do MRTK, é a funcionalidade de diagnóstico de plug-in.</span><span class="sxs-lookup"><span data-stu-id="460bc-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="460bc-175">O perfil de diagnóstico fornece vários sistemas simples para monitorar enquanto o projeto está em execução, incluindo uma opção de ligar/desligar útil para habilitar/desabilitar o painel de exibição na cena.</span><span class="sxs-lookup"><span data-stu-id="460bc-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="460bc-176">Configurações do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="460bc-176">Scene system settings</span></span>

<span data-ttu-id="460bc-177">O MRTK fornece esse serviço opcional para ajudá-lo a gerenciar o carregamento/descarregamento de uma cena aditiva complexa.</span><span class="sxs-lookup"><span data-stu-id="460bc-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="460bc-178">Para decidir se o sistema de cena seria uma boa opção para seu projeto, leia o [Guia de introdução do sistema de cena.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="460bc-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="460bc-179">Configurações de serviços adicionais</span><span class="sxs-lookup"><span data-stu-id="460bc-179">Additional services settings</span></span>

<span data-ttu-id="460bc-180">Uma das áreas mais avançadas do kit de ferramentas de realidade misturada é sua implementação de [padrão de localizador de serviço](https://en.wikipedia.org/wiki/Service_locator_pattern) que permite o registro de qualquer "serviço" com a estrutura.</span><span class="sxs-lookup"><span data-stu-id="460bc-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="460bc-181">Isso permite que a estrutura seja estendida com novos recursos/sistemas facilmente, mas também permite que os projetos aproveitem esses recursos para registrar seus próprios componentes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="460bc-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="460bc-182">Qualquer serviço registrado ainda Obtém a vantagem total de todos os eventos do Unity, sem a sobrecarga e o custo da implementação de padrões de desajeitado ou monocomportamento.</span><span class="sxs-lookup"><span data-stu-id="460bc-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="460bc-183">Isso permite componentes C# puros sem sobrecarga de cena para executar processos em primeiro plano e em segundo plano, por exemplo, gerar sistemas, lógica de jogo de runtime ou praticamente qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="460bc-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="460bc-184">Configurações de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="460bc-184">Input actions settings</span></span>

<span data-ttu-id="460bc-185">As ações de entrada fornecem uma maneira de abstrair quaisquer interações físicas e entradas de um projeto de runtime.</span><span class="sxs-lookup"><span data-stu-id="460bc-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="460bc-186">Toda a entrada física (de controladores/mãos/mouse/etc) é convertida em em uma ação de entrada lógica para uso em seu projeto de runtime.</span><span class="sxs-lookup"><span data-stu-id="460bc-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="460bc-187">Isso garante que, independentemente de onde a entrada venha, seu projeto simplesmente implementa essas ações como "Coisas a fazer" ou "Interagir com" em suas cenas.</span><span class="sxs-lookup"><span data-stu-id="460bc-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="460bc-188">Para criar uma nova ação de entrada, basta clicar no botão "Adicionar uma nova ação" e inserir um nome de texto amigável para o que ela representa.</span><span class="sxs-lookup"><span data-stu-id="460bc-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="460bc-189">Em seguida, você só precisa selecionar um eixo (o tipo de dados) ao qual a ação deve ser transmitida ou, no caso de controladores físicos, o tipo de entrada física ao qual ele pode ser anexado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="460bc-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="460bc-190">Restrição de eixo</span><span class="sxs-lookup"><span data-stu-id="460bc-190">Axis Constraint</span></span> | <span data-ttu-id="460bc-191">Tipo de Dados</span><span class="sxs-lookup"><span data-stu-id="460bc-191">Data Type</span></span> | <span data-ttu-id="460bc-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="460bc-192">Description</span></span> | <span data-ttu-id="460bc-193">Uso de exemplo</span><span class="sxs-lookup"><span data-stu-id="460bc-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="460bc-194">Nenhum</span><span class="sxs-lookup"><span data-stu-id="460bc-194">None</span></span> | <span data-ttu-id="460bc-195">Sem dados</span><span class="sxs-lookup"><span data-stu-id="460bc-195">No data</span></span> | <span data-ttu-id="460bc-196">Usado para uma ação ou evento vazio</span><span class="sxs-lookup"><span data-stu-id="460bc-196">Used for an empty action or event</span></span> | <span data-ttu-id="460bc-197">Gatilho de evento</span><span class="sxs-lookup"><span data-stu-id="460bc-197">Event Trigger</span></span> |
| <span data-ttu-id="460bc-198">Bruto (reservado)</span><span class="sxs-lookup"><span data-stu-id="460bc-198">Raw (reserved)</span></span> | <span data-ttu-id="460bc-199">objeto</span><span class="sxs-lookup"><span data-stu-id="460bc-199">object</span></span> | <span data-ttu-id="460bc-200">Reservado para uso futuro</span><span class="sxs-lookup"><span data-stu-id="460bc-200">Reserved for future use</span></span> | <span data-ttu-id="460bc-201">N/D</span><span class="sxs-lookup"><span data-stu-id="460bc-201">N/A</span></span> |
| <span data-ttu-id="460bc-202">Digital</span><span class="sxs-lookup"><span data-stu-id="460bc-202">Digital</span></span> | <span data-ttu-id="460bc-203">bool</span><span class="sxs-lookup"><span data-stu-id="460bc-203">bool</span></span> | <span data-ttu-id="460bc-204">Um booliana em dados de tipo de ou para fora</span><span class="sxs-lookup"><span data-stu-id="460bc-204">A boolean on or off type data</span></span> | <span data-ttu-id="460bc-205">Um botão do controlador</span><span class="sxs-lookup"><span data-stu-id="460bc-205">A controller button</span></span> |
| <span data-ttu-id="460bc-206">Eixo único</span><span class="sxs-lookup"><span data-stu-id="460bc-206">Single Axis</span></span> | <span data-ttu-id="460bc-207">FLOAT</span><span class="sxs-lookup"><span data-stu-id="460bc-207">float</span></span> | <span data-ttu-id="460bc-208">Um único valor de dados de precisão</span><span class="sxs-lookup"><span data-stu-id="460bc-208">A single precision data value</span></span> | <span data-ttu-id="460bc-209">Uma entrada de intervalo, por exemplo, um gatilho</span><span class="sxs-lookup"><span data-stu-id="460bc-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="460bc-210">Eixo duplo</span><span class="sxs-lookup"><span data-stu-id="460bc-210">Dual Axis</span></span> | <span data-ttu-id="460bc-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="460bc-211">Vector2</span></span> | <span data-ttu-id="460bc-212">Uma data de tipo float duplo para vários eixos</span><span class="sxs-lookup"><span data-stu-id="460bc-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="460bc-213">Um Dpad ou thumbstick</span><span class="sxs-lookup"><span data-stu-id="460bc-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="460bc-214">Posição de três dof</span><span class="sxs-lookup"><span data-stu-id="460bc-214">Three Dof Position</span></span> | <span data-ttu-id="460bc-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="460bc-215">Vector3</span></span> | <span data-ttu-id="460bc-216">Dados de tipo posicional de com 3 eixos float</span><span class="sxs-lookup"><span data-stu-id="460bc-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="460bc-217">controlador de apenas estilo de posição 3D</span><span class="sxs-lookup"><span data-stu-id="460bc-217">3D position style only controller</span></span> |
| <span data-ttu-id="460bc-218">Rotação de três DOF</span><span class="sxs-lookup"><span data-stu-id="460bc-218">Three Dof Rotation</span></span> | <span data-ttu-id="460bc-219">Quatérnion</span><span class="sxs-lookup"><span data-stu-id="460bc-219">Quaternion</span></span> | <span data-ttu-id="460bc-220">Entrada somente rotacional com 4 eixos float</span><span class="sxs-lookup"><span data-stu-id="460bc-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="460bc-221">Um controlador de três graus estilo, por exemplo, Oculus go Controller</span><span class="sxs-lookup"><span data-stu-id="460bc-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="460bc-222">Seis DOF</span><span class="sxs-lookup"><span data-stu-id="460bc-222">Six Dof</span></span> | <span data-ttu-id="460bc-223">Pose de realidade misturada (Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="460bc-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="460bc-224">Uma entrada de estilo de posição e rotação com componentes Vector3 e Quaternion</span><span class="sxs-lookup"><span data-stu-id="460bc-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="460bc-225">Um ponteiro ou controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="460bc-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="460bc-226">Eventos que utilizam ações de entrada não são limitados a controladores físicos e ainda podem ser utilizados dentro do projeto para que os efeitos de tempo de execução gerem novas ações.</span><span class="sxs-lookup"><span data-stu-id="460bc-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="460bc-227">As ações de entrada são um dos poucos componentes que não são editáveis em tempo de execução, são apenas uma configuração de tempo de design.</span><span class="sxs-lookup"><span data-stu-id="460bc-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="460bc-228">Esse perfil não deve ser trocado enquanto o projeto está em execução devido à dependência da estrutura (e de seus projetos) na geração da ID para cada ação.</span><span class="sxs-lookup"><span data-stu-id="460bc-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="460bc-229">Regras de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="460bc-229">Input actions rules</span></span>

<span data-ttu-id="460bc-230">As regras de ação de entrada fornecem uma maneira de converter automaticamente um evento gerado para uma ação de entrada em ações diferentes com base em seu valor de dados.</span><span class="sxs-lookup"><span data-stu-id="460bc-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="460bc-231">Eles são gerenciados diretamente dentro da estrutura e não incorrem em custos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="460bc-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="460bc-232">Por exemplo, converter o único evento de entrada de eixo duplo de um DPad em para as 4 correspondentes às ações "Dpad up"/"DPad Down"/"Dpad Left"/"Dpad Right" (conforme mostrado na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="460bc-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="460bc-233">Isso também pode ser feito em seu próprio código.</span><span class="sxs-lookup"><span data-stu-id="460bc-233">This could also be done in your own code.</span></span> <span data-ttu-id="460bc-234">No entanto, visto que esse era um padrão muito comum, a estrutura fornece um mecanismo para fazer isso "pronto para uso"</span><span class="sxs-lookup"><span data-stu-id="460bc-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="460bc-235">As regras de ação de entrada podem ser configuradas para qualquer um dos eixos de entrada disponíveis.</span><span class="sxs-lookup"><span data-stu-id="460bc-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="460bc-236">No entanto, as ações de entrada de um tipo de eixo podem ser convertidas em outra ação de entrada do mesmo tipo de eixo.</span><span class="sxs-lookup"><span data-stu-id="460bc-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="460bc-237">Você pode mapear uma ação de eixo duplo para outra ação de eixo duplo, mas não para uma ação digital ou nenhuma.</span><span class="sxs-lookup"><span data-stu-id="460bc-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Perfil de regras de ação de entrada](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="460bc-239">Configuração do ponteiro</span><span class="sxs-lookup"><span data-stu-id="460bc-239">Pointer configuration</span></span>

<span data-ttu-id="460bc-240">Ponteiros são usados para impulsionar a interatividade na cena de qualquer dispositivo de entrada, dando uma direção e um teste de ocorrência com qualquer objeto em uma cena (que tem um colisor anexado ou é um componente da interface do usuário).</span><span class="sxs-lookup"><span data-stu-id="460bc-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="460bc-241">Os ponteiros são configurados automaticamente por padrão para controladores, headsets (foco/foco) e entrada de mouse/toque.</span><span class="sxs-lookup"><span data-stu-id="460bc-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="460bc-242">Os ponteiros também podem ser visualizados na cena ativa usando um dos muitos componentes de linha fornecidos pelo Kit de Ferramentas de Realidade Misturada ou qualquer um dos seus se implementarem a interface IMixedRealityPointer do MRTK.</span><span class="sxs-lookup"><span data-stu-id="460bc-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="460bc-243">Apontando extensão: determina a extensão de apontar global para todos os ponteiros, incluindo o olhar.</span><span class="sxs-lookup"><span data-stu-id="460bc-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="460bc-244">Apontando máscaras de camada raycast: determina em quais camadas os ponteiros serão raycast.</span><span class="sxs-lookup"><span data-stu-id="460bc-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="460bc-245">Depurar raios que apontam para desenho: um auxiliar de depuração para visualizar os raios usados para raycasting.</span><span class="sxs-lookup"><span data-stu-id="460bc-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="460bc-246">Cores dos raios de desenho de depuração: um conjunto de cores a ser usado para visualização.</span><span class="sxs-lookup"><span data-stu-id="460bc-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="460bc-247">Pré-fab do cursor de olhar: facilita a especificação de um cursor de olhar global para qualquer cena.</span><span class="sxs-lookup"><span data-stu-id="460bc-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="460bc-248">Há um botão auxiliar adicional para ir rapidamente para o Provedor de Foco para substituir alguns valores específicos para o Foco, se necessário.</span><span class="sxs-lookup"><span data-stu-id="460bc-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="460bc-249">Configuração de gestos</span><span class="sxs-lookup"><span data-stu-id="460bc-249">Gestures configuration</span></span>

<span data-ttu-id="460bc-250">Gestos são uma implementação específica do sistema que permite atribuir ações de entrada aos vários métodos de entrada "Gesto" fornecidos por vários SDKs (por exemplo, HoloLens).</span><span class="sxs-lookup"><span data-stu-id="460bc-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="460bc-251">A implementação atual de Gestos é apenas para o HoloLens e será aprimorada para outros sistemas à medida que eles são adicionados ao Kit de Ferramentas no futuro (ainda não há datas).</span><span class="sxs-lookup"><span data-stu-id="460bc-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="460bc-252">Comandos de fala</span><span class="sxs-lookup"><span data-stu-id="460bc-252">Speech commands</span></span>

<span data-ttu-id="460bc-253">Assim como os gestos, algumas plataformas de runtime também fornecem funcionalidades de "Conversão de Fala em Texto" inteligentes com a capacidade de gerar comandos que podem ser recebidos por um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="460bc-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="460bc-254">Esse perfil de configuração permite que você configure o seguinte:</span><span class="sxs-lookup"><span data-stu-id="460bc-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="460bc-255">Configurações gerais – "comportamento inicial" definido como início automático ou início manual determina se o KeywordRecognizer deve ser inicializado na inicialização do sistema de entrada ou permite que o projeto decida quando inicializar o KeywordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="460bc-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="460bc-256">"Nível de confiança de reconhecimento" é usado para inicializar a [API KeywordRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) do Unity</span><span class="sxs-lookup"><span data-stu-id="460bc-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="460bc-257">Comandos de fala – registra "palavras" e as converte em ações de entrada que podem ser recebidas pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="460bc-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="460bc-258">Eles também podem ser anexados a ações de teclado, se necessário.</span><span class="sxs-lookup"><span data-stu-id="460bc-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="460bc-259">Atualmente, o sistema só dá suporte à fala quando executado em plataformas Windows 10, por exemplo, HoloLens e Windows 10 desktop e será aprimorado para outros sistemas à medida que eles forem adicionados ao MRTK no futuro (sem datas ainda).</span><span class="sxs-lookup"><span data-stu-id="460bc-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="460bc-260">Configuração de mapeamento de controlador</span><span class="sxs-lookup"><span data-stu-id="460bc-260">Controller mapping configuration</span></span>

<span data-ttu-id="460bc-261">Uma das telas principais de configuração do kit de ferramentas de realidade misturada é a capacidade de configurar e mapear os vários tipos de controladores que podem ser utilizados pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="460bc-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="460bc-262">A tela de configuração abaixo permite que você configure qualquer um dos controladores atualmente reconhecidos pelo kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="460bc-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="460bc-263">O MRTK fornece uma configuração padrão para os seguintes controladores/sistemas:</span><span class="sxs-lookup"><span data-stu-id="460bc-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="460bc-264">Mouse (incluindo suporte a mouse espacial 3D)</span><span class="sxs-lookup"><span data-stu-id="460bc-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="460bc-265">Tela touch</span><span class="sxs-lookup"><span data-stu-id="460bc-265">Touch Screen</span></span>
- <span data-ttu-id="460bc-266">Controladores do Xbox</span><span class="sxs-lookup"><span data-stu-id="460bc-266">Xbox controllers</span></span>
- <span data-ttu-id="460bc-267">Controladores de realidade do Windows Mixed</span><span class="sxs-lookup"><span data-stu-id="460bc-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="460bc-268">Gestos do HoloLens</span><span class="sxs-lookup"><span data-stu-id="460bc-268">HoloLens Gestures</span></span>
- <span data-ttu-id="460bc-269">Controladores de varinha Naopak do HTC</span><span class="sxs-lookup"><span data-stu-id="460bc-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="460bc-270">Controladores de toque Oculus</span><span class="sxs-lookup"><span data-stu-id="460bc-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="460bc-271">Controlador remoto Oculus</span><span class="sxs-lookup"><span data-stu-id="460bc-271">Oculus Remote controller</span></span>
- <span data-ttu-id="460bc-272">Dispositivos OpenVR genéricos (somente para usuários avançados)</span><span class="sxs-lookup"><span data-stu-id="460bc-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="460bc-273">Clicar na imagem para qualquer um dos sistemas de controlador pré-criados permite que você configure uma única ação de entrada para todas as suas entradas correspondentes, por exemplo, consulte a tela de configuração do Oculus Touch Controller abaixo:</span><span class="sxs-lookup"><span data-stu-id="460bc-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="460bc-274">Também há uma tela avançada para configurar outros controladores de entrada OpenVR ou Unity que não são identificados acima.</span><span class="sxs-lookup"><span data-stu-id="460bc-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="460bc-275">Configurações de visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="460bc-275">Controller visualization settings</span></span>

<span data-ttu-id="460bc-276">Além do mapeamento do controlador, um perfil de configuração separado é fornecido para personalizar como os controladores são apresentados em suas cenas.</span><span class="sxs-lookup"><span data-stu-id="460bc-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="460bc-277">Isso pode ser configurado em um "Global" (todas as instâncias de um controlador para uma mão específica) ou específico para um tipo/mão de controlador individual.</span><span class="sxs-lookup"><span data-stu-id="460bc-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="460bc-278">O MRTK também dá suporte a modelos nativos de controlador do SDK para Windows Mixed Reality e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="460bc-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="460bc-279">Eles são carregados como GameObjects em sua cena e posicionados usando o acompanhamento do controlador da plataforma.</span><span class="sxs-lookup"><span data-stu-id="460bc-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="460bc-280">Se a representação do controlador na cena precisar ser deslocada da posição do controlador físico, basta definir esse deslocamento em relação ao pré-padrão do modelo do controlador (por exemplo, definir a posição de transformação do pré-padrão do controlador com uma posição de deslocamento).</span><span class="sxs-lookup"><span data-stu-id="460bc-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="460bc-281">Utilitários do editor</span><span class="sxs-lookup"><span data-stu-id="460bc-281">Editor utilities</span></span>

<span data-ttu-id="460bc-282">Os utilitários a seguir funcionam somente no editor e são úteis para melhorar a produtividade do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="460bc-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Utilitários de configuração do Editor do MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="460bc-284">Inspetores de serviço</span><span class="sxs-lookup"><span data-stu-id="460bc-284">Service inspectors</span></span>

<span data-ttu-id="460bc-285">Os Inspetores de Serviço são um recurso somente editor que gera objetos na cena que representam serviços ativos.</span><span class="sxs-lookup"><span data-stu-id="460bc-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="460bc-286">Selecionar esses objetos exibe inspetores que oferecem links de documentação, controle sobre visualizações do editor e insights sobre o estado do serviço.</span><span class="sxs-lookup"><span data-stu-id="460bc-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="460bc-287">Você pode habilitar inspetores de serviço marcando *Usar Inspetores de Serviço* em *Configurações do Editor* no Perfil de Configuração.</span><span class="sxs-lookup"><span data-stu-id="460bc-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="460bc-288">Renderização de buffer de profundidade</span><span class="sxs-lookup"><span data-stu-id="460bc-288">Depth buffer renderer</span></span>

<span data-ttu-id="460bc-289">Compartilhar o buffer de profundidade com algumas plataformas de realidade misturada pode melhorar a [estabilização do holograma.](../performance/hologram-stabilization.md)</span><span class="sxs-lookup"><span data-stu-id="460bc-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="460bc-290">Por exemplo, a Windows Mixed Reality pode modificar a cena renderizada por pixel para levar em conta os movimentos sutis de cabeça durante o tempo necessário para renderizar um quadro.</span><span class="sxs-lookup"><span data-stu-id="460bc-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="460bc-291">No entanto, essas técnicas exigem buffers de profundidade com dados precisos para saber onde e a distância da geometria do usuário.</span><span class="sxs-lookup"><span data-stu-id="460bc-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="460bc-292">Para garantir que uma cena renderiza todos os dados *necessários* para o buffer de profundidade, os desenvolvedores podem alternar o recurso *Buffer* de Profundidade de Renderização em Configurações do Editor no Perfil de Configuração.</span><span class="sxs-lookup"><span data-stu-id="460bc-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="460bc-293">Isso usará o buffer de profundidade atual e o processará como cor para a exibição de cena aplicando um efeito de pós-processamento, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , à câmera principal.</span><span class="sxs-lookup"><span data-stu-id="460bc-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="460bc-294">![Utilitário ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>de buffer de profundidade de renderização o cilindro azul na cena tem um material com ZWrite desativado, portanto, nenhum dado de profundidade é gravado</sup></span><span class="sxs-lookup"><span data-stu-id="460bc-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="460bc-295">Alterando perfis em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="460bc-295">Changing profiles at runtime</span></span>

<span data-ttu-id="460bc-296">É possível atualizar perfis em tempo de execução e, em geral, há dois cenários e horários diferentes nos quais isso é útil:</span><span class="sxs-lookup"><span data-stu-id="460bc-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="460bc-297">**Opção de perfil de inicialização MRTK**: na inicialização, antes que o MRTK seja inicializado e o perfil se torne ativo, substituindo o perfil ainda não utilizado para habilitar/desabilitar recursos diferentes com base nos recursos do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="460bc-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="460bc-298">Por exemplo, se a experiência estiver em execução em VR que não tem um hardware de mapeamento espacial, provavelmente não fará sentido ter o componente de mapeamento espacial habilitado.</span><span class="sxs-lookup"><span data-stu-id="460bc-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="460bc-299">**Opção de perfil ativo**: após a inicialização, depois que o MRTK for inicializado e um perfil se tornar ativo, alternando o perfil atualmente em uso para alterar a forma com que determinados recursos se comportam.</span><span class="sxs-lookup"><span data-stu-id="460bc-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="460bc-300">Por exemplo, pode haver uma subexperiência específica no aplicativo que desejasse os ponteiros de extrema mão completamente removidos.</span><span class="sxs-lookup"><span data-stu-id="460bc-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="460bc-301">Opção de perfil de inicialização MRTK</span><span class="sxs-lookup"><span data-stu-id="460bc-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="460bc-302">Isso pode ser feito anexando um monocomportamento (exemplo abaixo), que é executado antes da inicialização do MRTK (ou seja, ativo ()).</span><span class="sxs-lookup"><span data-stu-id="460bc-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="460bc-303">Observe que o script (ou seja, chamada para `SetProfileBeforeInitialization` ) precisa ser executado antes do `MixedRealityToolkit` script, o que pode ser obtido definindo [as configurações de ordem de execução de script](https://docs.unity3d.com/Manual/class-MonoManager.html).</span><span class="sxs-lookup"><span data-stu-id="460bc-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="460bc-304">Em vez de "profileToUse", é possível ter algum conjunto arbitrário de perfis que se aplicam a plataformas específicas (por exemplo, um para o HoloLens 1, um para VR, um para o HoloLens 2, etc.).</span><span class="sxs-lookup"><span data-stu-id="460bc-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="460bc-305">É possível usar vários outros indicadores (por exemplo https://docs.unity3d.com/ScriptReference/SystemInfo.html , ou se a câmera é opaca/transparente), para descobrir qual perfil deve ser carregado.</span><span class="sxs-lookup"><span data-stu-id="460bc-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="460bc-306">Opção de perfil ativo</span><span class="sxs-lookup"><span data-stu-id="460bc-306">Active profile switch</span></span>

<span data-ttu-id="460bc-307">Isso pode ser feito definindo a `MixedRealityToolkit.Instance.ActiveProfile` propriedade para um novo perfil, substituindo o perfil ativo.</span><span class="sxs-lookup"><span data-stu-id="460bc-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="460bc-308">Observe que, ao definir durante o runtime, a destruição dos serviços em execução no momento ocorrerá após o último LateUpdate() de todos os serviços, e a insta instaência e a inicialização dos serviços associados ao novo perfil ocorrerão antes da primeira Atualização() de todos os `ActiveProfile` serviços.</span><span class="sxs-lookup"><span data-stu-id="460bc-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="460bc-309">Um aplicativo perceptível pode ocorrer durante esse processo.</span><span class="sxs-lookup"><span data-stu-id="460bc-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="460bc-310">Além disso, qualquer script com prioridade mais alta do `MixedRealityToolkit` que o script pode inserir sua Atualização antes que o novo perfil seja configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="460bc-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="460bc-311">Confira [Configurações de Ordem de Execução de](https://docs.unity3d.com/Manual/class-MonoManager.html) Script para obter mais informações sobre a prioridade do script.</span><span class="sxs-lookup"><span data-stu-id="460bc-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="460bc-312">No processo de alternação de perfil, a câmera da interface do usuário existente permanecerá inalterada, garantindo que os componentes da interface do usuário do Unity que exigem tela ainda funcionem após a opção.</span><span class="sxs-lookup"><span data-stu-id="460bc-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="460bc-313">Confira também</span><span class="sxs-lookup"><span data-stu-id="460bc-313">See also</span></span>

- [<span data-ttu-id="460bc-314">Estabilização de holograma</span><span class="sxs-lookup"><span data-stu-id="460bc-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)