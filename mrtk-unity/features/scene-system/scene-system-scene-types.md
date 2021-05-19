---
title: Tipos de cena do sistema de cena
description: Documentação sobre diferentes tipos de cena no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144578"
---
# <a name="scene-types"></a><span data-ttu-id="77b4a-104">Tipos de cena</span><span class="sxs-lookup"><span data-stu-id="77b4a-104">Scene types</span></span>

<span data-ttu-id="77b4a-105">As cenas foram divididas em três tipos e cada tipo tem uma função diferente.</span><span class="sxs-lookup"><span data-stu-id="77b4a-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![Sistema de cena na hierarquia](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="77b4a-107">Cenas de conteúdo</span><span class="sxs-lookup"><span data-stu-id="77b4a-107">Content scenes</span></span>

<span data-ttu-id="77b4a-108">Essas são as cenas com as que você está acostumado a lidar.</span><span class="sxs-lookup"><span data-stu-id="77b4a-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="77b4a-109">Qualquer tipo de conteúdo pode ser armazenado neles e pode ser carregado ou descarregado em qualquer combinação.</span><span class="sxs-lookup"><span data-stu-id="77b4a-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="77b4a-110">As cenas de conteúdo são habilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="77b4a-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="77b4a-111">Todas as cenas incluídas na matriz do `Content Scenes` seu perfil podem ser carregadas/descarregadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="77b4a-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="77b4a-112">Cenas do gerente</span><span class="sxs-lookup"><span data-stu-id="77b4a-112">Manager scenes</span></span>

<span data-ttu-id="77b4a-113">Uma única cena com uma instância mixedRealityToolkit necessária.</span><span class="sxs-lookup"><span data-stu-id="77b4a-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="77b4a-114">Essa cena será carregada primeiro no lançamento e permanecerá carregada durante o tempo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="77b4a-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="77b4a-115">A cena do gerente também pode hospedar outros objetos que nunca devem ser destruídos.</span><span class="sxs-lookup"><span data-stu-id="77b4a-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="77b4a-116">Essa é a alternativa preferencial para DontDestroyOnLoad.</span><span class="sxs-lookup"><span data-stu-id="77b4a-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="77b4a-117">Para habilitar esse recurso, verifique `Use Manager Scene` seu perfil e arraste um objeto de cena para o campo `Manager Scene` .</span><span class="sxs-lookup"><span data-stu-id="77b4a-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="77b4a-118">Cenas de iluminação</span><span class="sxs-lookup"><span data-stu-id="77b4a-118">Lighting scenes</span></span>

<span data-ttu-id="77b4a-119">Um conjunto de cenas que armazenam informações de iluminação e objetos de iluminação.</span><span class="sxs-lookup"><span data-stu-id="77b4a-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="77b4a-120">Somente uma pode ser carregada por vez e suas configurações podem ser mescladas durante as cargas para transições de iluminação suave.</span><span class="sxs-lookup"><span data-stu-id="77b4a-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="77b4a-121">As configurações de iluminação do Unity – luz ambiente, skyboxes etc. – podem ser complicadas de gerenciar ao usar o carregamento aditivo porque estão vinculadas a cenas individuais e o comportamento de substituição não é simples.</span><span class="sxs-lookup"><span data-stu-id="77b4a-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="77b4a-122">Na prática, isso pode causar confusão quando os ativos são autores em condições de iluminação que não são obtidas em runtime.</span><span class="sxs-lookup"><span data-stu-id="77b4a-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![Configurações de iluminação do sistema de cena](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="77b4a-124">O sistema de cena usa cenas de iluminação para garantir que essas configurações permaneçam consistentes, independentemente de quais cenas são carregadas ou ativas, tanto no modo de edição quanto no modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="77b4a-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="77b4a-125">Para habilitar esse recurso, faça check- `Use Lighting Scene` in do seu perfil e preencha a `Lighting Scenes` matriz.</span><span class="sxs-lookup"><span data-stu-id="77b4a-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="77b4a-126">Configurações de iluminação em cache</span><span class="sxs-lookup"><span data-stu-id="77b4a-126">Cached lighting settings</span></span>

<span data-ttu-id="77b4a-127">Seu perfil armazena cópias em cache das configurações de iluminação mantidas em suas cenas de iluminação.</span><span class="sxs-lookup"><span data-stu-id="77b4a-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="77b4a-128">Se essas configurações forem alteradas nos bastidores de iluminação, você precisará atualizar seu cache para garantir que a iluminação apareça como esperado no modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="77b4a-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="77b4a-129">Seu perfil exibirá um aviso quando suspeitar de que as configurações armazenadas em cache estão desatualizadas.</span><span class="sxs-lookup"><span data-stu-id="77b4a-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="77b4a-130">Clicar em `Update Cached Lighting Settings` carregará cada uma de suas cenas de iluminação, extrairá suas configurações e, em seguida, as armazenará em seu perfil.</span><span class="sxs-lookup"><span data-stu-id="77b4a-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![Configurações de iluminação em cache do sistema de cena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="77b4a-132">Comportamento do editor</span><span class="sxs-lookup"><span data-stu-id="77b4a-132">Editor behavior</span></span>

<span data-ttu-id="77b4a-133">Um benefício de usar cenas de iluminação é saber que o conteúdo está aceso corretamente durante a edição.</span><span class="sxs-lookup"><span data-stu-id="77b4a-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="77b4a-134">Para esse fim, o serviço de cena manterá uma cena de iluminação carregada em todos os momentos e copiará as configurações de iluminação dessa cena para a cena ativa atual.\*</span><span class="sxs-lookup"><span data-stu-id="77b4a-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="77b4a-135">Você pode alterar qual cena de iluminação é carregada abrindo o [Inspetor de serviço](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) do sistema de cena.</span><span class="sxs-lookup"><span data-stu-id="77b4a-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="77b4a-136">No modo de edição, você pode fazer a transição instantânea entre os bastidores de iluminação.</span><span class="sxs-lookup"><span data-stu-id="77b4a-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="77b4a-137">No modo de reprodução, você pode visualizar as transições.</span><span class="sxs-lookup"><span data-stu-id="77b4a-137">In play mode, you can preview transitions.</span></span>

![Inspetor do sistema de cena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="77b4a-139">\**Observação: normalmente, a cena ativa determina as configurações de iluminação no editor. No entanto, optamos por não usar esse recurso para impor as configurações de iluminação, pois a cena ativa também é onde os objetos recém-criados são colocados por padrão, e cenas de iluminação só são permitidas para conter componentes de iluminação. Em vez disso, as configurações da cena de iluminação atual são automaticamente copiadas para as configurações da cena ativa. Tenha em mente que isso fará com que as configurações de iluminação de sua cena de conteúdo sejam sobrescritas.*</span><span class="sxs-lookup"><span data-stu-id="77b4a-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
