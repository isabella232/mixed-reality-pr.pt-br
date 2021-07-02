---
title: Guia de configuração do perfil MRTK
description: Documentação para configurar o MRTK no Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: b7ec8d9ca2213ff998f94a6a2d029900ff886a2f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176414"
---
# <a name="mrtk-profile-configuration-guide"></a><span data-ttu-id="c0e50-104">Guia de configuração do perfil MRTK</span><span class="sxs-lookup"><span data-stu-id="c0e50-104">MRTK profile configuration guide</span></span>

<span data-ttu-id="c0e50-105">a realidade misturada Toolkit centralizar a maior parte da configuração necessária para gerenciar o kit de ferramentas o mais possível (exceto para "coisas" de tempo de execução verdadeiras).</span><span class="sxs-lookup"><span data-stu-id="c0e50-105">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="c0e50-106">Este guia é uma explicação simples para cada uma das telas de perfil de configuração disponíveis atualmente para o kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="c0e50-106">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="c0e50-107">a principal realidade misturada Toolkit perfil de configuração</span><span class="sxs-lookup"><span data-stu-id="c0e50-107">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="c0e50-108">o principal perfil de configuração, que é anexado ao gameobject *MixedRealityToolkit* em sua cena, fornece o ponto de entrada principal para o Toolkit em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c0e50-108">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="c0e50-109">a realidade misturada Toolkit "bloqueia" as telas de configuração padrão para garantir que você sempre tenha um ponto de partida comum para seu projeto e seja incentivado a começar a definir suas próprias configurações à medida que seu projeto evolui.</span><span class="sxs-lookup"><span data-stu-id="c0e50-109">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="c0e50-110">A configuração MRTK não é editável durante o modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="c0e50-110">The MRTK configuration is not editable during play-mode.</span></span>

![Perfil de configuração do MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="c0e50-112">todos os perfis "padrão" para a realidade misturada Toolkit podem ser encontrados no projeto do SDK na pasta ativos/MRTK/SDK/perfis.</span><span class="sxs-lookup"><span data-stu-id="c0e50-112">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0e50-113">DefaultHoloLens2ConfigurationProfile é otimizado para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c0e50-113">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="c0e50-114">Consulte [perfis](../features/profiles/profiles.md) para obter os detalhes.</span><span class="sxs-lookup"><span data-stu-id="c0e50-114">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="c0e50-115">ao abrir a realidade mista principal Toolkit perfil de configuração, você verá a seguinte tela no inspetor:</span><span class="sxs-lookup"><span data-stu-id="c0e50-115">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="c0e50-116">Se você selecionar um ativo MixedRealityToolkitConfigurationProfile sem o MixedRealityToolkit na cena, ele perguntará se você deseja que o MRTK configure automaticamente a cena para você.</span><span class="sxs-lookup"><span data-stu-id="c0e50-116">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="c0e50-117">Isso é opcional, no entanto, deve haver um objeto MixedRealityToolkit ativo na cena para acessar todas as telas de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e50-117">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="c0e50-118">Isso abriga a configuração atual de tempo de execução ativo para o projeto.</span><span class="sxs-lookup"><span data-stu-id="c0e50-118">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="c0e50-119">A partir daqui, você pode navegar para todos os perfis de configuração para o MRTK, incluindo:</span><span class="sxs-lookup"><span data-stu-id="c0e50-119">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="c0e50-120">guia de configuração do perfil da realidade mista Toolkit</span><span class="sxs-lookup"><span data-stu-id="c0e50-120">Mixed Reality Toolkit profile configuration guide</span></span>](#mrtk-profile-configuration-guide)
  - [<span data-ttu-id="c0e50-121">a principal realidade misturada Toolkit perfil de configuração</span><span class="sxs-lookup"><span data-stu-id="c0e50-121">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="c0e50-122">Configurações da experiência</span><span class="sxs-lookup"><span data-stu-id="c0e50-122">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="c0e50-123">Configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="c0e50-123">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="c0e50-124">Configurações do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="c0e50-124">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="c0e50-125">Configurações de visualização de limite</span><span class="sxs-lookup"><span data-stu-id="c0e50-125">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="c0e50-126">Seleção do sistema de teleportabilidade</span><span class="sxs-lookup"><span data-stu-id="c0e50-126">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="c0e50-127">Configurações de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="c0e50-127">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="c0e50-128">Configurações de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="c0e50-128">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="c0e50-129">Configurações do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="c0e50-129">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="c0e50-130">Configurações de serviços adicionais</span><span class="sxs-lookup"><span data-stu-id="c0e50-130">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="c0e50-131">Configurações de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="c0e50-131">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="c0e50-132">Regras de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="c0e50-132">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="c0e50-133">Configuração do ponteiro</span><span class="sxs-lookup"><span data-stu-id="c0e50-133">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="c0e50-134">Configuração de gestos</span><span class="sxs-lookup"><span data-stu-id="c0e50-134">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="c0e50-135">Comandos de fala</span><span class="sxs-lookup"><span data-stu-id="c0e50-135">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="c0e50-136">Configuração de mapeamento de controlador</span><span class="sxs-lookup"><span data-stu-id="c0e50-136">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="c0e50-137">Configurações de visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="c0e50-137">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="c0e50-138">Utilitários do editor</span><span class="sxs-lookup"><span data-stu-id="c0e50-138">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="c0e50-139">Inspetores de serviço</span><span class="sxs-lookup"><span data-stu-id="c0e50-139">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="c0e50-140">Renderizador de buffer de profundidade</span><span class="sxs-lookup"><span data-stu-id="c0e50-140">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="c0e50-141">Alterando perfis em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c0e50-141">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="c0e50-142">Opção de perfil de inicialização MRTK</span><span class="sxs-lookup"><span data-stu-id="c0e50-142">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="c0e50-143">Opção de perfil ativo</span><span class="sxs-lookup"><span data-stu-id="c0e50-143">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="c0e50-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0e50-144">See also</span></span>](#see-also)

<span data-ttu-id="c0e50-145">Esses perfis de configuração são detalhados abaixo em suas seções relevantes:</span><span class="sxs-lookup"><span data-stu-id="c0e50-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="c0e50-146">Configurações da experiência</span><span class="sxs-lookup"><span data-stu-id="c0e50-146">Experience settings</span></span>

<span data-ttu-id="c0e50-147">localizada na página principal de configuração Toolkit reality, essa configuração define a operação padrão da [escala de ambiente da realidade misturada](/windows/mixed-reality/coordinate-systems-in-unity) para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c0e50-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="c0e50-148">Configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="c0e50-148">Camera settings</span></span>

<span data-ttu-id="c0e50-149">As configurações da câmera definem como a câmera será configurada para o projeto de realidade misturada, definindo as configurações de recorte genérico, qualidade e transparência.</span><span class="sxs-lookup"><span data-stu-id="c0e50-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="c0e50-150">Configurações do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="c0e50-150">Input system settings</span></span>

<span data-ttu-id="c0e50-151">a realidade misturada Project fornece um sistema de entrada robusto e bem treinado para rotear todos os eventos de entrada em todo o projeto que é selecionado por padrão.</span><span class="sxs-lookup"><span data-stu-id="c0e50-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="c0e50-152">Por trás do sistema de entrada fornecido pelo MRTK são vários outros sistemas, eles ajudam a impulsionar e gerenciar o complexo weavings necessário para abstrair as complexidades de uma estrutura de realidade mista de várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="c0e50-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="c0e50-153">Cada um dos perfis individuais é detalhado abaixo:</span><span class="sxs-lookup"><span data-stu-id="c0e50-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="c0e50-154">Configurações de foco</span><span class="sxs-lookup"><span data-stu-id="c0e50-154">Focus Settings</span></span>
- [<span data-ttu-id="c0e50-155">Configurações de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="c0e50-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="c0e50-156">Regras de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="c0e50-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="c0e50-157">Configuração do ponteiro</span><span class="sxs-lookup"><span data-stu-id="c0e50-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="c0e50-158">Configuração de gestos</span><span class="sxs-lookup"><span data-stu-id="c0e50-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="c0e50-159">Comandos de fala</span><span class="sxs-lookup"><span data-stu-id="c0e50-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="c0e50-160">Configuração de mapeamento de controlador</span><span class="sxs-lookup"><span data-stu-id="c0e50-160">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="c0e50-161">Configurações de visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="c0e50-161">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="c0e50-162">Configurações de visualização de limite</span><span class="sxs-lookup"><span data-stu-id="c0e50-162">Boundary visualization settings</span></span>

<span data-ttu-id="c0e50-163">O sistema de limite traduz o limite percebido relatado pelo sistema de limite/guardião de plataformas subjacentes.</span><span class="sxs-lookup"><span data-stu-id="c0e50-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="c0e50-164">A configuração do Visualizador de limite fornece a capacidade de mostrar automaticamente o limite registrado em sua cena em relação à posição do usuário. O limite também reagirá/será atualizado com base em onde o usuário portará dentro da cena.</span><span class="sxs-lookup"><span data-stu-id="c0e50-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="c0e50-165">Seleção do sistema de teleportabilidade</span><span class="sxs-lookup"><span data-stu-id="c0e50-165">Teleportation system selection</span></span>

<span data-ttu-id="c0e50-166">a realidade misturada Project fornece um sistema de teleportabilidade completo para gerenciar eventos de teleportação no projeto que é selecionado por padrão.</span><span class="sxs-lookup"><span data-stu-id="c0e50-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="c0e50-167">Configurações de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="c0e50-167">Spatial awareness settings</span></span>

<span data-ttu-id="c0e50-168">a realidade misturada Project fornece um sistema de conscientização espacial recriado para trabalhar com sistemas de verificação espacial no projeto que é selecionado por padrão.</span><span class="sxs-lookup"><span data-stu-id="c0e50-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="c0e50-169">a realidade misturada Toolkit configuração de conscientização espacial permite que você personalize a forma como o sistema é iniciado, se ele é automaticamente quando o aplicativo inicia ou posteriormente de forma programática, bem como a definição das extensões para o campo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c0e50-169">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="c0e50-170">Ele também permite que você defina as configurações de malha e superfície, personalizando ainda mais a forma como o seu projeto compreende o ambiente em relação a você.</span><span class="sxs-lookup"><span data-stu-id="c0e50-170">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="c0e50-171">Isso só é aplicável a dispositivos que podem fornecer um ambiente examinado.</span><span class="sxs-lookup"><span data-stu-id="c0e50-171">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="c0e50-172">Configurações de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="c0e50-172">Diagnostics settings</span></span>

<span data-ttu-id="c0e50-173">Um recurso opcional, mas altamente útil do MRTK, é a funcionalidade de diagnóstico de plug-in.</span><span class="sxs-lookup"><span data-stu-id="c0e50-173">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="c0e50-174">O perfil de diagnóstico fornece vários sistemas simples para monitorar enquanto o projeto está em execução, incluindo uma opção de ligar/desligar útil para habilitar/desabilitar o painel de exibição na cena.</span><span class="sxs-lookup"><span data-stu-id="c0e50-174">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="c0e50-175">Configurações do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="c0e50-175">Scene system settings</span></span>

<span data-ttu-id="c0e50-176">O MRTK fornece esse serviço opcional para ajudá-lo a gerenciar o carregamento/descarregamento de uma cena aditiva complexa.</span><span class="sxs-lookup"><span data-stu-id="c0e50-176">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="c0e50-177">Para decidir se o sistema de cena seria uma boa opção para seu projeto, leia o [Guia de introdução do sistema de cena.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="c0e50-177">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="c0e50-178">Configurações de serviços adicionais</span><span class="sxs-lookup"><span data-stu-id="c0e50-178">Additional services settings</span></span>

<span data-ttu-id="c0e50-179">uma das áreas mais avançadas da realidade misturada Toolkit é sua implementação de [padrão de localizador de serviço](https://en.wikipedia.org/wiki/Service_locator_pattern) que permite o registro de qualquer "serviço" com a estrutura.</span><span class="sxs-lookup"><span data-stu-id="c0e50-179">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="c0e50-180">Isso permite que a estrutura seja estendida com novos recursos/sistemas facilmente, mas também permite que os projetos aproveitem esses recursos para registrar seus próprios componentes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c0e50-180">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="c0e50-181">Qualquer serviço registrado ainda Obtém a vantagem total de todos os eventos do Unity, sem a sobrecarga e o custo da implementação de padrões de desajeitado ou monocomportamento.</span><span class="sxs-lookup"><span data-stu-id="c0e50-181">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="c0e50-182">Isso permite componentes puros do C# sem sobrecarga de cena para a execução de processos em primeiro plano e em segundo plano, por exemplo, sistemas de geração, lógica de jogo em tempo de execução ou praticamente qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="c0e50-182">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="c0e50-183">Configurações de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="c0e50-183">Input actions settings</span></span>

<span data-ttu-id="c0e50-184">As ações de entrada fornecem uma maneira de abstrair quaisquer interações físicas e entradas de um projeto de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c0e50-184">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="c0e50-185">Todas as entradas físicas (de controladores/mãos/mouse/etc.) são convertidas em uma ação de entrada lógica para uso em seu projeto de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c0e50-185">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="c0e50-186">Isso garante que, independentemente de onde venha a entrada, seu projeto simplesmente implemente essas ações como "coisas para fazer" ou "interagir com" em seus bastidores.</span><span class="sxs-lookup"><span data-stu-id="c0e50-186">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="c0e50-187">Para criar uma nova ação de entrada, basta clicar no botão "adicionar uma nova ação" e inserir um nome de texto amigável para o que ele representa.</span><span class="sxs-lookup"><span data-stu-id="c0e50-187">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="c0e50-188">Em seguida, você só precisa selecionar um eixo (o tipo de dados) que a ação deve transmitir, ou no caso de controladores físicos, o tipo de entrada física ao qual ele pode ser anexado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c0e50-188">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="c0e50-189">Restrição de eixo</span><span class="sxs-lookup"><span data-stu-id="c0e50-189">Axis Constraint</span></span> | <span data-ttu-id="c0e50-190">Tipo de Dados</span><span class="sxs-lookup"><span data-stu-id="c0e50-190">Data Type</span></span> | <span data-ttu-id="c0e50-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e50-191">Description</span></span> | <span data-ttu-id="c0e50-192">Uso de exemplo</span><span class="sxs-lookup"><span data-stu-id="c0e50-192">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="c0e50-193">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c0e50-193">None</span></span> | <span data-ttu-id="c0e50-194">Sem dados</span><span class="sxs-lookup"><span data-stu-id="c0e50-194">No data</span></span> | <span data-ttu-id="c0e50-195">Usado para uma ação ou evento vazio</span><span class="sxs-lookup"><span data-stu-id="c0e50-195">Used for an empty action or event</span></span> | <span data-ttu-id="c0e50-196">Gatilho de evento</span><span class="sxs-lookup"><span data-stu-id="c0e50-196">Event Trigger</span></span> |
| <span data-ttu-id="c0e50-197">Bruto (reservado)</span><span class="sxs-lookup"><span data-stu-id="c0e50-197">Raw (reserved)</span></span> | <span data-ttu-id="c0e50-198">object</span><span class="sxs-lookup"><span data-stu-id="c0e50-198">object</span></span> | <span data-ttu-id="c0e50-199">Reservado para uso futuro</span><span class="sxs-lookup"><span data-stu-id="c0e50-199">Reserved for future use</span></span> | <span data-ttu-id="c0e50-200">N/D</span><span class="sxs-lookup"><span data-stu-id="c0e50-200">N/A</span></span> |
| <span data-ttu-id="c0e50-201">Digital</span><span class="sxs-lookup"><span data-stu-id="c0e50-201">Digital</span></span> | <span data-ttu-id="c0e50-202">bool</span><span class="sxs-lookup"><span data-stu-id="c0e50-202">bool</span></span> | <span data-ttu-id="c0e50-203">Um booliana em dados de tipo de ou para fora</span><span class="sxs-lookup"><span data-stu-id="c0e50-203">A boolean on or off type data</span></span> | <span data-ttu-id="c0e50-204">Um botão do controlador</span><span class="sxs-lookup"><span data-stu-id="c0e50-204">A controller button</span></span> |
| <span data-ttu-id="c0e50-205">Eixo único</span><span class="sxs-lookup"><span data-stu-id="c0e50-205">Single Axis</span></span> | <span data-ttu-id="c0e50-206">FLOAT</span><span class="sxs-lookup"><span data-stu-id="c0e50-206">float</span></span> | <span data-ttu-id="c0e50-207">Um único valor de dados de precisão</span><span class="sxs-lookup"><span data-stu-id="c0e50-207">A single precision data value</span></span> | <span data-ttu-id="c0e50-208">Uma entrada de intervalo, por exemplo, um gatilho</span><span class="sxs-lookup"><span data-stu-id="c0e50-208">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="c0e50-209">Eixo duplo</span><span class="sxs-lookup"><span data-stu-id="c0e50-209">Dual Axis</span></span> | <span data-ttu-id="c0e50-210">Vector2</span><span class="sxs-lookup"><span data-stu-id="c0e50-210">Vector2</span></span> | <span data-ttu-id="c0e50-211">Uma data de tipo float duplo para vários eixos</span><span class="sxs-lookup"><span data-stu-id="c0e50-211">A dual float type date for multiple axis</span></span> | <span data-ttu-id="c0e50-212">Um Dpad ou thumbstick</span><span class="sxs-lookup"><span data-stu-id="c0e50-212">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="c0e50-213">Posição de três dof</span><span class="sxs-lookup"><span data-stu-id="c0e50-213">Three Dof Position</span></span> | <span data-ttu-id="c0e50-214">Vector3</span><span class="sxs-lookup"><span data-stu-id="c0e50-214">Vector3</span></span> | <span data-ttu-id="c0e50-215">Dados de tipo posicional de com 3 eixos flutuantes</span><span class="sxs-lookup"><span data-stu-id="c0e50-215">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="c0e50-216">Controlador somente de estilo de posição 3D</span><span class="sxs-lookup"><span data-stu-id="c0e50-216">3D position style only controller</span></span> |
| <span data-ttu-id="c0e50-217">Rotação de três dof</span><span class="sxs-lookup"><span data-stu-id="c0e50-217">Three Dof Rotation</span></span> | <span data-ttu-id="c0e50-218">Quatérnion</span><span class="sxs-lookup"><span data-stu-id="c0e50-218">Quaternion</span></span> | <span data-ttu-id="c0e50-219">Entrada somente rotacional com quatro eixos flutuantes</span><span class="sxs-lookup"><span data-stu-id="c0e50-219">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="c0e50-220">Um controlador de estilo de três graus, por exemplo, o controlador Oculus Go</span><span class="sxs-lookup"><span data-stu-id="c0e50-220">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="c0e50-221">Seis Dof</span><span class="sxs-lookup"><span data-stu-id="c0e50-221">Six Dof</span></span> | <span data-ttu-id="c0e50-222">Pose de realidade misturada (Vector3, Quatternion)</span><span class="sxs-lookup"><span data-stu-id="c0e50-222">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="c0e50-223">Uma entrada de estilo de posição e rotação com componentes Vector3 e Quaternion</span><span class="sxs-lookup"><span data-stu-id="c0e50-223">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="c0e50-224">Um controlador de movimento ou ponteiro</span><span class="sxs-lookup"><span data-stu-id="c0e50-224">A motion controller or Pointer</span></span> |

<span data-ttu-id="c0e50-225">Eventos que utilizam ações de entrada não são limitados a controladores físicos e ainda podem ser utilizados dentro do projeto para que os efeitos de runtime gerem novas ações.</span><span class="sxs-lookup"><span data-stu-id="c0e50-225">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="c0e50-226">As ações de entrada são um dos poucos componentes que não são editáveis em runtime, são apenas uma configuração de tempo de design.</span><span class="sxs-lookup"><span data-stu-id="c0e50-226">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="c0e50-227">Esse perfil não deve ser trocado enquanto o projeto estiver em execução devido à dependência da estrutura (e seus projetos) nas IDs geradas para cada ação.</span><span class="sxs-lookup"><span data-stu-id="c0e50-227">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="c0e50-228">Regras de ações de entrada</span><span class="sxs-lookup"><span data-stu-id="c0e50-228">Input actions rules</span></span>

<span data-ttu-id="c0e50-229">As regras de ação de entrada fornecem uma maneira de converter automaticamente um evento gerado para uma ação de entrada em para ações diferentes com base em seu valor de dados.</span><span class="sxs-lookup"><span data-stu-id="c0e50-229">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="c0e50-230">Eles são gerenciados perfeitamente dentro da estrutura e não incorrem em custos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="c0e50-230">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="c0e50-231">Por exemplo, convertendo o único evento de entrada de eixo duplo de um DPad em para as quatro ações correspondentes "Dpad Up" /"DPad Down" /"Dpad Left" /"Dpad Right" (conforme mostrado na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="c0e50-231">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="c0e50-232">Isso também pode ser feito em seu próprio código.</span><span class="sxs-lookup"><span data-stu-id="c0e50-232">This could also be done in your own code.</span></span> <span data-ttu-id="c0e50-233">No entanto, como esse era um padrão muito comum, a estrutura fornece um mecanismo para fazer isso "fora da caixa"</span><span class="sxs-lookup"><span data-stu-id="c0e50-233">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="c0e50-234">As regras de ação de entrada podem ser configuradas para qualquer um dos eixos de entrada disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c0e50-234">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="c0e50-235">No entanto, as ações de entrada de um tipo de eixo podem ser convertida em outra ação de entrada do mesmo tipo de eixo.</span><span class="sxs-lookup"><span data-stu-id="c0e50-235">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="c0e50-236">Você pode mapear uma ação de eixo duplo para outra ação de eixo duplo, mas não para uma ação digital ou nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c0e50-236">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Perfil de regras de ação de entrada](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="c0e50-238">Configuração do ponteiro</span><span class="sxs-lookup"><span data-stu-id="c0e50-238">Pointer configuration</span></span>

<span data-ttu-id="c0e50-239">Ponteiros são usados para impulsionar a interatividade na cena de qualquer dispositivo de entrada, dando uma direção e um teste de ocorrência com qualquer objeto em uma cena (que tem um colisor anexado ou é um componente da interface do usuário).</span><span class="sxs-lookup"><span data-stu-id="c0e50-239">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="c0e50-240">Os ponteiros são configurados automaticamente por padrão para controladores, headsets (foco/foco) e entrada de mouse/toque.</span><span class="sxs-lookup"><span data-stu-id="c0e50-240">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="c0e50-241">Os ponteiros também podem ser visualizados na cena ativa usando um dos muitos componentes de linha fornecidos pelo Toolkit de Realidade Misturada ou qualquer um dos seus se implementarem a interface IMixedRealityPointer do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c0e50-241">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="c0e50-242">Apontando extensão: determina a extensão de apontar global para todos os ponteiros, incluindo o olhar.</span><span class="sxs-lookup"><span data-stu-id="c0e50-242">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="c0e50-243">Apontando máscaras de camada raycast: determina em quais camadas os ponteiros serão raycast.</span><span class="sxs-lookup"><span data-stu-id="c0e50-243">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="c0e50-244">Depurar raios que apontam para desenho: um auxiliar de depuração para visualizar os raios usados para raycasting.</span><span class="sxs-lookup"><span data-stu-id="c0e50-244">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="c0e50-245">Cores dos raios de desenho de depuração: um conjunto de cores a ser usado para visualização.</span><span class="sxs-lookup"><span data-stu-id="c0e50-245">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="c0e50-246">Pré-fab do cursor de olhar: facilita a especificação de um cursor de olhar global para qualquer cena.</span><span class="sxs-lookup"><span data-stu-id="c0e50-246">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="c0e50-247">Há um botão auxiliar adicional para ir rapidamente para o Provedor de Foco para substituir alguns valores específicos para o Foco, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c0e50-247">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="c0e50-248">Configuração de gestos</span><span class="sxs-lookup"><span data-stu-id="c0e50-248">Gestures configuration</span></span>

<span data-ttu-id="c0e50-249">Gestos são uma implementação específica do sistema que permite atribuir ações de entrada aos vários métodos de entrada "Gesto" fornecidos por vários SDKs (por exemplo, HoloLens).</span><span class="sxs-lookup"><span data-stu-id="c0e50-249">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="c0e50-250">A implementação atual de Gestos é apenas para o HoloLens e será aprimorada para outros sistemas à medida que eles são adicionados ao Toolkit no futuro (ainda não há datas).</span><span class="sxs-lookup"><span data-stu-id="c0e50-250">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="c0e50-251">Comandos de fala</span><span class="sxs-lookup"><span data-stu-id="c0e50-251">Speech commands</span></span>

<span data-ttu-id="c0e50-252">Assim como os gestos, algumas plataformas de runtime também fornecem funcionalidades de "Conversão de Fala em Texto" inteligentes com a capacidade de gerar comandos que podem ser recebidos por um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="c0e50-252">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="c0e50-253">Esse perfil de configuração permite que você configure o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0e50-253">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="c0e50-254">Geral Configurações – "Comportamento de Início" definido como Início Automático ou Início Manual determina se é preciso inicializar KeywordRecognizer na inicialização do sistema de entrada ou permitir que o projeto decida quando inicializar o KeywordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="c0e50-254">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="c0e50-255">O "Nível de Confiança de Reconhecimento" é usado para inicializar a [API KeywordRecognizer do](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity</span><span class="sxs-lookup"><span data-stu-id="c0e50-255">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="c0e50-256">Comandos de Fala – registra "palavras" e as converte em ações de entrada que podem ser recebidas pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c0e50-256">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="c0e50-257">Eles também podem ser anexados às ações de teclado, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c0e50-257">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0e50-258">Atualmente, o sistema dá suporte apenas à fala durante a execução em plataformas Windows 10, por exemplo, HoloLens e Windows 10 desktop e será aprimorado para outros sistemas à medida que eles são adicionados ao MRTK no futuro (ainda não há datas).</span><span class="sxs-lookup"><span data-stu-id="c0e50-258">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="c0e50-259">Configuração de mapeamento do controlador</span><span class="sxs-lookup"><span data-stu-id="c0e50-259">Controller mapping configuration</span></span>

<span data-ttu-id="c0e50-260">Uma das principais telas de configuração para o Toolkit realidade misturada é a capacidade de configurar e mapear os vários tipos de controladores que podem ser utilizados pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c0e50-260">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="c0e50-261">A tela de configuração abaixo permite que você configure qualquer um dos controladores atualmente reconhecidos pelo kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="c0e50-261">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="c0e50-262">O MRTK fornece uma configuração padrão para os seguintes controladores/sistemas:</span><span class="sxs-lookup"><span data-stu-id="c0e50-262">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="c0e50-263">Mouse (incluindo suporte ao mouse espacial 3D)</span><span class="sxs-lookup"><span data-stu-id="c0e50-263">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="c0e50-264">Tela touch</span><span class="sxs-lookup"><span data-stu-id="c0e50-264">Touch Screen</span></span>
- <span data-ttu-id="c0e50-265">Controladores Xbox</span><span class="sxs-lookup"><span data-stu-id="c0e50-265">Xbox controllers</span></span>
- <span data-ttu-id="c0e50-266">Windows Mixed Reality controladores</span><span class="sxs-lookup"><span data-stu-id="c0e50-266">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="c0e50-267">HoloLens Gestos</span><span class="sxs-lookup"><span data-stu-id="c0e50-267">HoloLens Gestures</span></span>
- <span data-ttu-id="c0e50-268">Controladores de controladores HTC Vive</span><span class="sxs-lookup"><span data-stu-id="c0e50-268">HTC Vive wand controllers</span></span>
- <span data-ttu-id="c0e50-269">Controladores touch do Oculus</span><span class="sxs-lookup"><span data-stu-id="c0e50-269">Oculus Touch controllers</span></span>
- <span data-ttu-id="c0e50-270">Controlador remoto do Oculus</span><span class="sxs-lookup"><span data-stu-id="c0e50-270">Oculus Remote controller</span></span>
- <span data-ttu-id="c0e50-271">Dispositivos OpenVR genéricos (somente usuários avançados)</span><span class="sxs-lookup"><span data-stu-id="c0e50-271">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="c0e50-272">Clicar na Imagem para qualquer um dos sistemas de controlador pré-criado permite configurar uma única ação de entrada para todas as suas entradas correspondentes, por exemplo, consulte a tela de configuração do controlador Oculus Touch abaixo:</span><span class="sxs-lookup"><span data-stu-id="c0e50-272">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="c0e50-273">Também há uma tela avançada para configurar outros controladores de entrada OpenVR ou Unity que não são identificados acima.</span><span class="sxs-lookup"><span data-stu-id="c0e50-273">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="c0e50-274">Configurações de visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="c0e50-274">Controller visualization settings</span></span>

<span data-ttu-id="c0e50-275">Além do mapeamento do controlador, um perfil de configuração separado é fornecido para personalizar como os controladores são apresentados em suas cenas.</span><span class="sxs-lookup"><span data-stu-id="c0e50-275">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="c0e50-276">Isso pode ser configurado em um "Global" (todas as instâncias de um controlador para uma mão específica) ou específico para um tipo/mão de controlador individual.</span><span class="sxs-lookup"><span data-stu-id="c0e50-276">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="c0e50-277">O MRTK também dá suporte a modelos de controlador SDK nativos para Windows Mixed Reality e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="c0e50-277">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="c0e50-278">Eles são carregados como GameObjects em sua cena e posicionados usando o acompanhamento do controlador da plataforma.</span><span class="sxs-lookup"><span data-stu-id="c0e50-278">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="c0e50-279">Se a representação do controlador na cena precisar ser deslocada da posição do controlador físico, basta definir esse deslocamento em relação ao pré-padrão do modelo do controlador (por exemplo, definir a posição de transformação do pré-padrão do controlador com uma posição de deslocamento).</span><span class="sxs-lookup"><span data-stu-id="c0e50-279">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="c0e50-280">Utilitários do editor</span><span class="sxs-lookup"><span data-stu-id="c0e50-280">Editor utilities</span></span>

<span data-ttu-id="c0e50-281">Os utilitários a seguir funcionam somente no editor e são úteis para melhorar a produtividade do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c0e50-281">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Utilitários de configuração do Editor do MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="c0e50-283">Inspetores de serviço</span><span class="sxs-lookup"><span data-stu-id="c0e50-283">Service inspectors</span></span>

<span data-ttu-id="c0e50-284">Os Inspetores de Serviço são um recurso somente editor que gera objetos na cena que representam serviços ativos.</span><span class="sxs-lookup"><span data-stu-id="c0e50-284">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="c0e50-285">Selecionar esses objetos exibe inspetores que oferecem links de documentação, controle sobre visualizações do editor e insights sobre o estado do serviço.</span><span class="sxs-lookup"><span data-stu-id="c0e50-285">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="c0e50-286">Você pode habilitar inspetores de serviço verificando *Usar Inspetores de Serviço* em Editor *Configurações* no Perfil de Configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e50-286">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="c0e50-287">Renderização de buffer de profundidade</span><span class="sxs-lookup"><span data-stu-id="c0e50-287">Depth buffer renderer</span></span>

<span data-ttu-id="c0e50-288">Compartilhar o buffer de profundidade com algumas plataformas de realidade misturada pode melhorar a [estabilização do holograma.](../performance/hologram-stabilization.md)</span><span class="sxs-lookup"><span data-stu-id="c0e50-288">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="c0e50-289">Por exemplo, a Windows Mixed Reality pode modificar a cena renderizada por pixel para levar em conta os movimentos sutis de cabeça durante o tempo necessário para renderizar um quadro.</span><span class="sxs-lookup"><span data-stu-id="c0e50-289">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="c0e50-290">No entanto, essas técnicas exigem buffers de profundidade com dados precisos para saber onde e a distância da geometria do usuário.</span><span class="sxs-lookup"><span data-stu-id="c0e50-290">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="c0e50-291">Para garantir que uma cena renderiza todos os dados necessários para o buffer de profundidade, os desenvolvedores podem alternar o recurso *Buffer* de Profundidade de Renderização em *Editor Configurações* no Perfil de Configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e50-291">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="c0e50-292">Isso pegará o buffer de profundidade atual e o renderizará como cor para a exibição da cena aplicando um efeito pós-processamento, , à [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) câmera principal.</span><span class="sxs-lookup"><span data-stu-id="c0e50-292">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="c0e50-293">![Utilitário de buffer de profundidade de renderização O cilindro azul na cena tem um material com ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>ZWrite desligado para</sup> que nenhum dado de profundidade seja gravado</span><span class="sxs-lookup"><span data-stu-id="c0e50-293">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="c0e50-294">Alterando perfis em runtime</span><span class="sxs-lookup"><span data-stu-id="c0e50-294">Changing profiles at runtime</span></span>

<span data-ttu-id="c0e50-295">É possível atualizar perfis em runtime e geralmente há dois cenários e horas diferentes nos quais isso é útil:</span><span class="sxs-lookup"><span data-stu-id="c0e50-295">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="c0e50-296">Opção de perfil de inicialização do **MRTK** anterior: na inicialização, antes que o MRTK seja inicializado e o perfil se torne ativo, substituindo o perfil ainda não em uso para habilitar/desabilitar diferentes recursos com base nas funcionalidades do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c0e50-296">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="c0e50-297">Por exemplo, se a experiência estiver em execução em VR que não tem hardware de mapeamento espacial, provavelmente não fará sentido ter o componente de mapeamento espacial habilitado.</span><span class="sxs-lookup"><span data-stu-id="c0e50-297">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="c0e50-298">**Opção de perfil ativo:** após a inicialização, depois que o MRTK for inicializado e um perfil tiver se tornado ativo, alternar o perfil atualmente em uso para alterar a maneira como determinados recursos se comportam.</span><span class="sxs-lookup"><span data-stu-id="c0e50-298">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="c0e50-299">Por exemplo, pode haver uma sub-experiência específica no aplicativo que deseja que os ponteiros de mão distante sejam completamente removidos.</span><span class="sxs-lookup"><span data-stu-id="c0e50-299">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="c0e50-300">Opção de perfil de inicialização do MRTK</span><span class="sxs-lookup"><span data-stu-id="c0e50-300">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="c0e50-301">Isso pode ser feito anexando um monocomportamento (exemplo abaixo), que é executado antes da inicialização do MRTK (ou seja, ativo ()).</span><span class="sxs-lookup"><span data-stu-id="c0e50-301">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="c0e50-302">Observe que o script (ou seja, chamada para `SetProfileBeforeInitialization` ) precisa ser executado antes do `MixedRealityToolkit` script, o que pode ser obtido definindo [as configurações de ordem de execução de script](https://docs.unity3d.com/Manual/class-MonoManager.html).</span><span class="sxs-lookup"><span data-stu-id="c0e50-302">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

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

<span data-ttu-id="c0e50-303">em vez de "profileToUse", é possível ter algum conjunto arbitrário de perfis que se aplicam a plataformas específicas (por exemplo, um para HoloLens 1, um para VR, um para HoloLens 2, etc.).</span><span class="sxs-lookup"><span data-stu-id="c0e50-303">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="c0e50-304">É possível usar vários outros indicadores (por exemplo https://docs.unity3d.com/ScriptReference/SystemInfo.html , ou se a câmera é opaca/transparente), para descobrir qual perfil deve ser carregado.</span><span class="sxs-lookup"><span data-stu-id="c0e50-304">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="c0e50-305">Opção de perfil ativo</span><span class="sxs-lookup"><span data-stu-id="c0e50-305">Active profile switch</span></span>

<span data-ttu-id="c0e50-306">Isso pode ser feito definindo a `MixedRealityToolkit.Instance.ActiveProfile` propriedade para um novo perfil, substituindo o perfil ativo.</span><span class="sxs-lookup"><span data-stu-id="c0e50-306">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="c0e50-307">Observação ao definir `ActiveProfile` durante o tempo de execução, a destruição dos serviços em execução no momento ocorrerá após o último LateUpdate () de todos os serviços, e a instanciação e a inicialização dos serviços associados ao novo perfil ocorrerão antes da primeira atualização () de todos os serviços.</span><span class="sxs-lookup"><span data-stu-id="c0e50-307">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="c0e50-308">Uma hesitação de aplicativo perceptível pode ocorrer durante esse processo.</span><span class="sxs-lookup"><span data-stu-id="c0e50-308">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="c0e50-309">Além disso, qualquer script com prioridade mais alta do que o `MixedRealityToolkit` script pode inserir sua atualização antes que o novo perfil seja configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="c0e50-309">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="c0e50-310">Consulte [configurações de ordem de execução de script](https://docs.unity3d.com/Manual/class-MonoManager.html) para obter mais informações sobre a prioridade do script.</span><span class="sxs-lookup"><span data-stu-id="c0e50-310">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="c0e50-311">No processo de alternância de perfil, a câmera de interface do usuário existente permanecerá inalterada, garantindo que os componentes da interface do usuário do Unity que exigem Canvas ainda funcionem após a mudança.</span><span class="sxs-lookup"><span data-stu-id="c0e50-311">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0e50-312">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0e50-312">See also</span></span>

- [<span data-ttu-id="c0e50-313">Estabilização de holograma</span><span class="sxs-lookup"><span data-stu-id="c0e50-313">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)
