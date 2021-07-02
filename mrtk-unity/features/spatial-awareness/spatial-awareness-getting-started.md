---
title: Início da conscientização espacial
description: descreve o Reconhecimento espacial no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176709"
---
# <a name="spatial-awareness-getting-started"></a><span data-ttu-id="05fde-104">Início da conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="05fde-104">Spatial awareness getting started</span></span>

![Conscientização espacial](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="05fde-106">O sistema de Reconhecimento Espacial fornece reconhecimento ambiental do mundo real em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="05fde-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="05fde-107">Quando introduzido no Microsoft HoloLens, o Reconhecimento Espacial forneceu uma coleção de malhas, representando a geometria do ambiente, o que permitia interações atraentes entre hologramas e o mundo real.</span><span class="sxs-lookup"><span data-stu-id="05fde-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="05fde-108">Neste momento, a Toolkit realidade misturada não é fornecidas com algoritmos de Compreensão Espacial como originalmente empacotados no HoloToolkit.</span><span class="sxs-lookup"><span data-stu-id="05fde-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="05fde-109">A Compreensão Espacial geralmente envolve transformar dados de Malha Espacial para criar dados de Malha simplificados e/ou agrupados, como planos, paredes, pisos, limites etc.</span><span class="sxs-lookup"><span data-stu-id="05fde-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="05fde-110">Introdução</span><span class="sxs-lookup"><span data-stu-id="05fde-110">Getting started</span></span>

<span data-ttu-id="05fde-111">A adição de suporte para o Reconhecimento Espacial requer dois componentes principais do Toolkit Realidade Misturada: o sistema de Reconhecimento Espacial e um provedor de plataforma com suporte.</span><span class="sxs-lookup"><span data-stu-id="05fde-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="05fde-112">[Habilitar](#enable-the-spatial-awareness-system) o sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="05fde-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="05fde-113">[Registrar](#register-observers) e [configurar](configuring-spatial-awareness-mesh-observer.md) um ou mais observadores espaciais para fornecer dados de malha</span><span class="sxs-lookup"><span data-stu-id="05fde-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="05fde-114">[Criar e implantar em](#build-and-deploy) uma plataforma que dá suporte ao Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="05fde-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="05fde-115">Habilitar o sistema de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="05fde-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="05fde-116">O sistema de Reconhecimento Espacial é gerenciado pelo objeto MixedRealityToolkit (ou outro componente [do registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) serviços).</span><span class="sxs-lookup"><span data-stu-id="05fde-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="05fde-117">Siga as etapas abaixo para habilitar ou desabilitar o sistema *de Reconhecimento Espacial* no perfil *MixedRealityToolkit.*</span><span class="sxs-lookup"><span data-stu-id="05fde-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="05fde-118">O Toolkit realidade misturada é lançado com alguns perfis pré-configurados padrão.</span><span class="sxs-lookup"><span data-stu-id="05fde-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="05fde-119">Alguns deles têm o sistema de Reconhecimento Espacial habilitado ou desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="05fde-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="05fde-120">A intenção dessa pré-configuração, especialmente para quando desabilitada, é evitar a sobrecarga visual de calcular e renderizar as malhas.</span><span class="sxs-lookup"><span data-stu-id="05fde-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="05fde-121">Perfil</span><span class="sxs-lookup"><span data-stu-id="05fde-121">Profile</span></span> | <span data-ttu-id="05fde-122">Sistema habilitado por padrão</span><span class="sxs-lookup"><span data-stu-id="05fde-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="05fde-123">`DefaultHoloLens1ConfigurationProfile` (Ativos/MRTK/SDK/Perfis/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="05fde-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="05fde-124">Falso</span><span class="sxs-lookup"><span data-stu-id="05fde-124">False</span></span> |
| <span data-ttu-id="05fde-125">`DefaultHoloLens2ConfigurationProfile` (Ativos/MRTK/SDK/Perfis/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="05fde-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="05fde-126">Falso</span><span class="sxs-lookup"><span data-stu-id="05fde-126">False</span></span> |
| <span data-ttu-id="05fde-127">`DefaultMixedRealityToolkitConfigurationProfile` (Ativos/MRTK/SDK/Perfis)</span><span class="sxs-lookup"><span data-stu-id="05fde-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="05fde-128">True</span><span class="sxs-lookup"><span data-stu-id="05fde-128">True</span></span> |

1. <span data-ttu-id="05fde-129">Selecione o objeto MixedRealityToolkit na hierarquia de cena para abrir no Painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="05fde-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="05fde-131">Navegue até a *seção Sistema de Reconhecimento Espacial* e marque *Habilitar Sistema de Reconhecimento Espacial*</span><span class="sxs-lookup"><span data-stu-id="05fde-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![Habilitar o Reconhecimento Espacial](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="05fde-133">Selecione o tipo de implementação do sistema de Reconhecimento Espacial desejado.</span><span class="sxs-lookup"><span data-stu-id="05fde-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="05fde-134">O [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) é o padrão fornecido.</span><span class="sxs-lookup"><span data-stu-id="05fde-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![Selecione a implementação do sistema de reconhecimento espacial](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="05fde-136">Registrar observadores</span><span class="sxs-lookup"><span data-stu-id="05fde-136">Register observers</span></span>

<span data-ttu-id="05fde-137">Os serviços na plataforma de Toolkit podem ter Provedor de Dados [serviços](../../architecture/systems-extensions-providers.md) que complementam o serviço principal com controles de implementação e dados específicos da plataforma.</span><span class="sxs-lookup"><span data-stu-id="05fde-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="05fde-138">Um exemplo disso é o Sistema de Entrada de Realidade Misturada que tem vários provedores de dados para obter o controlador e outras informações de entrada relacionadas de várias APIs [específicas](../input/input-providers.md) da plataforma.</span><span class="sxs-lookup"><span data-stu-id="05fde-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="05fde-139">O sistema de Reconhecimento Espacial é semelhante, já que os provedores de dados fornecem ao sistema dados de malha sobre o mundo real.</span><span class="sxs-lookup"><span data-stu-id="05fde-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="05fde-140">O perfil de Reconhecimento Espacial deve ter pelo menos um Observador Espacial registrado.</span><span class="sxs-lookup"><span data-stu-id="05fde-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="05fde-141">Observadores Espaciais geralmente são componentes específicos da plataforma que atuam como o provedor para a busca de vários tipos de dados de malha de um ponto de extremidade específico da plataforma (ou seja,</span><span class="sxs-lookup"><span data-stu-id="05fde-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="05fde-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="05fde-142">HoloLens).</span></span>

1. <span data-ttu-id="05fde-143">Abrir ou expandir o perfil *do Sistema de Reconhecimento Espacial*</span><span class="sxs-lookup"><span data-stu-id="05fde-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![Perfil do Sistema de Reconhecimento Espacial](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="05fde-145">Clique no *botão "Adicionar Observador Espacial"*</span><span class="sxs-lookup"><span data-stu-id="05fde-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="05fde-146">Selecione o tipo de *implementação do Observador Espacial desejado*</span><span class="sxs-lookup"><span data-stu-id="05fde-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![Selecione a Implementação do Observador Espacial](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="05fde-148">[Modificar as propriedades de configuração no observador](configuring-spatial-awareness-mesh-observer.md) conforme necessário</span><span class="sxs-lookup"><span data-stu-id="05fde-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="05fde-149">Os usuários do `DefaultMixedRealityToolkitConfigurationProfile` (Ativos/MRTK/SDK/Perfis) terão o sistema de Reconhecimento Espacial pré-configurado para a plataforma Windows Mixed Reality que usa a [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe .</span><span class="sxs-lookup"><span data-stu-id="05fde-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="05fde-150">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="05fde-150">Build and deploy</span></span>

<span data-ttu-id="05fde-151">Depois que o sistema de Reconhecimento Espacial estiver configurado com os observadores desejados, o projeto poderá ser criado e implantado na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="05fde-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05fde-152">Se estiver direcionando a plataforma Windows Mixed Reality (por ex. HoloLens), é [](/windows/mixed-reality/spatial-mapping-in-unity) importante garantir que a funcionalidade de Percepção Espacial seja habilitada para usar o sistema de Reconhecimento Espacial no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="05fde-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="05fde-153">Algumas plataformas, incluindo Microsoft HoloLens, fornecem suporte para execução remota de dentro do Unity.</span><span class="sxs-lookup"><span data-stu-id="05fde-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="05fde-154">Esse recurso permite o desenvolvimento e o teste rápidos sem exigir a etapa de build e implantação.</span><span class="sxs-lookup"><span data-stu-id="05fde-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="05fde-155">Certifique-se de fazer o teste de aceitação final usando uma versão criada e implantada do aplicativo, em execução no hardware e na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="05fde-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="05fde-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="05fde-156">Next steps</span></span>

<span data-ttu-id="05fde-157">Depois de seguir os procedimentos acima para habilitar o sistema de Reconhecimento Espacial, o sistema pode ser configurado e controlado com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="05fde-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="05fde-158">Informações para configurar observadores no inspetor:</span><span class="sxs-lookup"><span data-stu-id="05fde-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="05fde-159">Configurando observadores para no uso do dispositivo</span><span class="sxs-lookup"><span data-stu-id="05fde-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="05fde-160">Configurando observadores para uso no editor</span><span class="sxs-lookup"><span data-stu-id="05fde-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="05fde-161">Informações para controlar e estender observadores por meio de código:</span><span class="sxs-lookup"><span data-stu-id="05fde-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="05fde-162">Configurando observadores por meio de código</span><span class="sxs-lookup"><span data-stu-id="05fde-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="05fde-163">Criando um Observador personalizado</span><span class="sxs-lookup"><span data-stu-id="05fde-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="05fde-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="05fde-164">See also</span></span>

- [<span data-ttu-id="05fde-165">Documentação da API de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="05fde-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="05fde-166">Visão geral do WMR do mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="05fde-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="05fde-167">Mapeamento espacial no WmR do Unity</span><span class="sxs-lookup"><span data-stu-id="05fde-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)
