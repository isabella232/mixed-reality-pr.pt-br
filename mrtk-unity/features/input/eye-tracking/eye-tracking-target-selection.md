---
title: Seleção de destino de acompanhamento de olho
description: Como acessar dados olhars de olho e olho olhar eventos específicos para selecionar destinos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144189"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="9a188-104">Seleção de destino com suporte de olho</span><span class="sxs-lookup"><span data-stu-id="9a188-104">Eye-supported target selection</span></span>

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="9a188-106">Esta página discute diferentes opções para acessar dados olhars de olho e olho olhar eventos específicos para selecionar destinos em MRTK.</span><span class="sxs-lookup"><span data-stu-id="9a188-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="9a188-107">O acompanhamento de olho permite seleções de destino rápidas e sem esforço usando uma combinação de informações sobre o que um usuário está vendo com entradas adicionais, como o _rastreamento manual_ e os _comandos de voz_:</span><span class="sxs-lookup"><span data-stu-id="9a188-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="9a188-108">Procure & diga _"Select"_ (comando de voz padrão)</span><span class="sxs-lookup"><span data-stu-id="9a188-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="9a188-109">Procure & diga _"explodir"_ ou _"pop"_ (comandos de voz personalizados)</span><span class="sxs-lookup"><span data-stu-id="9a188-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="9a188-110">Procurar & botão Bluetooth</span><span class="sxs-lookup"><span data-stu-id="9a188-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="9a188-111">Olhe & pinça (ou seja, mantenha sua mão na frente e traga seu polegar e um índice para o dedo)</span><span class="sxs-lookup"><span data-stu-id="9a188-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="9a188-112">Observe que, para que isso funcione, os [raios à mão precisam ser desabilitados](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="9a188-112">Please note that for this to work, the [hand rays need to be disabled](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="9a188-113">Para selecionar o conteúdo do Holographic usando olho olhar, há várias opções:</span><span class="sxs-lookup"><span data-stu-id="9a188-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="9a188-114">**1. Use o ponteiro de foco principal:**</span><span class="sxs-lookup"><span data-stu-id="9a188-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="9a188-115">Isso pode ser compreendido como o cursor de prioridade.</span><span class="sxs-lookup"><span data-stu-id="9a188-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="9a188-116">Por padrão, se as mãos estiverem no modo de exibição, isso seria raios de mão.</span><span class="sxs-lookup"><span data-stu-id="9a188-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="9a188-117">Se nenhuma mão estiver na exibição, o ponteiro priorizado será de cabeça ou olho olhar.</span><span class="sxs-lookup"><span data-stu-id="9a188-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="9a188-118">Portanto, observe que, com base no cabeçalho de design atual ou no olhar de olho, é suprimido como uma entrada de cursor se os raios à mão forem usados.</span><span class="sxs-lookup"><span data-stu-id="9a188-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="9a188-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9a188-119">For example:</span></span>

<span data-ttu-id="9a188-120">Um usuário deseja selecionar um botão de Holographic distante.</span><span class="sxs-lookup"><span data-stu-id="9a188-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="9a188-121">Como desenvolvedor, você deseja fornecer uma solução flexível que permita ao usuário obter essas tarefas em várias condições:</span><span class="sxs-lookup"><span data-stu-id="9a188-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="9a188-122">Ir para o botão e examiná-lo</span><span class="sxs-lookup"><span data-stu-id="9a188-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="9a188-123">Examine-o de uma distância e diga "Select"</span><span class="sxs-lookup"><span data-stu-id="9a188-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="9a188-124">Direcione o botão usando um raio de mão e realizando um pinça nesse caso, a solução mais flexível é usar o manipulador de foco principal, pois ele o notificará sempre que o ponteiro de foco principal priorizado atualmente disparar um evento.</span><span class="sxs-lookup"><span data-stu-id="9a188-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="9a188-125">Observe que, se os raios à mão estiverem habilitados, o ponteiro de foco olhar de cabeça ou olho será desabilitado assim que as mãos entrarem em vista.</span><span class="sxs-lookup"><span data-stu-id="9a188-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a188-126">Observe que, se os raios à mão estiverem habilitados, o ponteiro de foco olhar de cabeça ou olho será desabilitado assim que as mãos entrarem em vista.</span><span class="sxs-lookup"><span data-stu-id="9a188-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="9a188-127">Se você quiser dar suporte a uma interação de [ _' aparência e pinçar '_ , será necessário desabilitar a disposição de raio](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span><span class="sxs-lookup"><span data-stu-id="9a188-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="9a188-128">Em nossos bastidores de exemplo de acompanhamento de olho, desabilitamos o conjunto de posicionamento à mão para permitir interações mais ricas usando movimentos de olhos e outros-consulte para obter exemplos com [suporte](eye-tracking-eyes-and-hands.md).</span><span class="sxs-lookup"><span data-stu-id="9a188-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span></span>

[<span data-ttu-id="9a188-129">**2. Use o foco ocular e os raios à mão ao mesmo tempo:**</span><span class="sxs-lookup"><span data-stu-id="9a188-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="9a188-130">Pode haver instâncias em que você deseja ser mais específico que o tipo de ponteiros de foco possa disparar determinados eventos e permitir simultaneamente usando várias técnicas de interação distantes.</span><span class="sxs-lookup"><span data-stu-id="9a188-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="9a188-131">Por exemplo: em seu aplicativo, um usuário pode usar raios de longe para manipular alguma configuração mecânica Holographic-por exemplo, pegar e manter algumas partes de mecanismo de Holographic distantes e mantê-las em vigor.</span><span class="sxs-lookup"><span data-stu-id="9a188-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="9a188-132">Ao fazer isso, o usuário precisa passar por várias instruções e registrar seu andamento marcando algumas caixas de seleção.</span><span class="sxs-lookup"><span data-stu-id="9a188-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="9a188-133">Se o usuário tiver suas mãos _não ocupadas_, seria instinctual simplesmente tocar na caixa de seleção ou selecioná-la usando um raio de mão.</span><span class="sxs-lookup"><span data-stu-id="9a188-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="9a188-134">No entanto, se o usuário tiver suas mãos, como em nosso caso, mantendo algumas partes do mecanismo Holographic em vigor, você deseja permitir que o usuário percorra diretamente as instruções usando suas olhar de olho e simplesmente examine uma caixa de seleção e diga "check-in!".</span><span class="sxs-lookup"><span data-stu-id="9a188-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="9a188-135">Para habilitar isso, você precisa usar um script EyeTrackingTarget específico para os olhos que é independente do MRTK de FocusHandlers principal e será discutido mais adiante.</span><span class="sxs-lookup"><span data-stu-id="9a188-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="9a188-136">1. usar manipuladores de foco e ponteiro genérico</span><span class="sxs-lookup"><span data-stu-id="9a188-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="9a188-137">Se o acompanhamento ocular estiver configurado corretamente (consulte Configuração básica do [MRTK](eye-tracking-basic-setup.md)para usar o acompanhamento ocular), permitir que os usuários selecionem hologramas usando os olhos será o mesmo que qualquer outra entrada de foco (por exemplo, foco com a cabeça ou raio de mão). Isso oferece a grande vantagem de uma maneira flexível de interagir com seus hologramas definindo o tipo de foco principal em seu Perfil de Ponteiro de Entrada do MRTK, dependendo das necessidades do usuário, deixando seu código inalterado.</span><span class="sxs-lookup"><span data-stu-id="9a188-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="9a188-138">Isso permite alternar entre o olhar ou a cabeça sem alterar uma linha de código ou substituir raios de mão por direcionamento ocular para interações distantes.</span><span class="sxs-lookup"><span data-stu-id="9a188-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="9a188-139">Concentrando-se em um holograma</span><span class="sxs-lookup"><span data-stu-id="9a188-139">Focusing on a hologram</span></span>

<span data-ttu-id="9a188-140">Para detectar quando um holograma está focalizado, use a interface _'IMixedRealityFocusHandler'_ que fornece dois membros de interface: _OnFocusEnter_ e _OnFocusExit_.</span><span class="sxs-lookup"><span data-stu-id="9a188-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="9a188-141">Aqui está um exemplo simples de [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) para alterar a cor de um holograma ao ser procurado.</span><span class="sxs-lookup"><span data-stu-id="9a188-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="9a188-142">Selecionando um holograma focalizado</span><span class="sxs-lookup"><span data-stu-id="9a188-142">Selecting a focused hologram</span></span>

<span data-ttu-id="9a188-143">Para selecionar um holograma focalizado, use _PointerHandler_ para escutar eventos de entrada para confirmar uma seleção.</span><span class="sxs-lookup"><span data-stu-id="9a188-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="9a188-144">Por exemplo, adicionar _o IMixedRealityPointerHandler_ fará com que eles reajam à entrada de ponteiro simples.</span><span class="sxs-lookup"><span data-stu-id="9a188-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="9a188-145">A interface _IMixedRealityPointerHandler_ requer a implementação dos três membros de interface a seguir: _OnPointerUp,_ _OnPointerDown_ e _OnPointerClicked_.</span><span class="sxs-lookup"><span data-stu-id="9a188-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="9a188-146">No exemplo a seguir, alteramos a cor de um holograma observando-o e pinçando ou dizendo "selecionar".</span><span class="sxs-lookup"><span data-stu-id="9a188-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="9a188-147">A ação necessária para disparar o evento é definida pelo qual podemos definir o tipo de no Editor do Unity – por padrão, é a `eventData.MixedRealityInputAction == selectAction` `selectAction` ação "Selecionar".</span><span class="sxs-lookup"><span data-stu-id="9a188-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="9a188-148">Os tipos de [MixedRealityInputActions](../input-actions.md) disponíveis podem ser configurados no Perfil do MRTK por meio das Ações de Entrada de Entrada do Perfil de Configuração do _MRTK._  ->    ->  </span><span class="sxs-lookup"><span data-stu-id="9a188-148">The types of available [MixedRealityInputActions](../input-actions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="9a188-149">BaseEyeFocusHandler específica do foco com o olhar</span><span class="sxs-lookup"><span data-stu-id="9a188-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="9a188-150">Considerando que o foco com o olhar pode ser muito diferente de outras entradas de  ponteiro, talvez você queira garantir que reaja apenas à entrada de foco se ele for foco com o olhar e ele for atualmente o ponteiro de entrada primário.</span><span class="sxs-lookup"><span data-stu-id="9a188-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="9a188-151">Para essa finalidade, você usaria o [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) que é específico para acompanhamento de olho e que deriva do [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .</span><span class="sxs-lookup"><span data-stu-id="9a188-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="9a188-152">Como mencionado anteriormente, ele só será disparado se o foco olhar direcionamento for a entrada do ponteiro principal (ou seja, não há um raio de disposição ativo).</span><span class="sxs-lookup"><span data-stu-id="9a188-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="9a188-153">Para obter mais informações, consulte [como dar suporte a gestos de olho olhar + Hand](eye-tracking-eyes-and-hands.md).</span><span class="sxs-lookup"><span data-stu-id="9a188-153">For more information, see [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).</span></span>

<span data-ttu-id="9a188-154">Aqui está um exemplo de `EyeTrackingDemo-03-Navigation` (ativos/MRTK/exemplos/demos/EyeTracking/cenas).</span><span class="sxs-lookup"><span data-stu-id="9a188-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="9a188-155">Nesta demonstração, há dois hologramas 3D que serão ativados dependendo de qual parte do objeto é examinada: se o usuário olhar para o lado esquerdo do holograma, essa parte se moverá lentamente para a frente do usuário.</span><span class="sxs-lookup"><span data-stu-id="9a188-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="9a188-156">Se o lado direito for examinado, essa parte será movida lentamente para a frente.</span><span class="sxs-lookup"><span data-stu-id="9a188-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="9a188-157">Esse é um comportamento que você talvez não queira que seja sempre ativo e também algo que talvez você não queira disparar acidentalmente por um olhar de raio ou cabeça.</span><span class="sxs-lookup"><span data-stu-id="9a188-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="9a188-158">Tendo o [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) anexo, um gameobject será girado enquanto estiver sendo examinado.</span><span class="sxs-lookup"><span data-stu-id="9a188-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

<span data-ttu-id="9a188-159">Consulte a documentação da API para obter uma lista completa dos eventos disponíveis do [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :</span><span class="sxs-lookup"><span data-stu-id="9a188-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="9a188-160">**OnEyeFocusStart:** Disparado quando o olho olhar Ray *começa* a se Interseccionar com o colisor de destino.</span><span class="sxs-lookup"><span data-stu-id="9a188-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="9a188-161">**OnEyeFocusStay:** Disparado *enquanto* o olho olhar Ray está interseccionando com o colisor de destino.</span><span class="sxs-lookup"><span data-stu-id="9a188-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="9a188-162">**OnEyeFocusStop:** Disparado quando o olho olhar Ray *pára* de interseção com o colisor de destino.</span><span class="sxs-lookup"><span data-stu-id="9a188-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="9a188-163">**OnEyeFocusDwell:** Disparado quando o olho olhar Ray se cruzou com o colisor de destino por um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="9a188-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="9a188-164">2. olho independente – EyeTrackingTarget específico do olhar</span><span class="sxs-lookup"><span data-stu-id="9a188-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="9a188-165">Por fim, fornecemos uma solução que permite que você trate a entrada baseada em olho completamente independente de outros ponteiros de foco por meio do [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span><span class="sxs-lookup"><span data-stu-id="9a188-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="9a188-166">Isso tem três _vantagens_:</span><span class="sxs-lookup"><span data-stu-id="9a188-166">This has three _advantages_:</span></span>

- <span data-ttu-id="9a188-167">Você pode se certificar de que o holograma está apenas se reagindo ao olhar de olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="9a188-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="9a188-168">Isso é independente da entrada primária ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="9a188-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="9a188-169">Portanto, você pode processar várias entradas de uma só vez– por exemplo, combinando direcionamento de olho rápido com gestos de mão.</span><span class="sxs-lookup"><span data-stu-id="9a188-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="9a188-170">Vários eventos do Unity já foram definidos para torná-lo rápido e conveniente para lidar e reutilizar comportamentos existentes de dentro do Editor do Unity ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="9a188-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="9a188-171">Também há algumas _desvantagens:_</span><span class="sxs-lookup"><span data-stu-id="9a188-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="9a188-172">Mais esforço para lidar com entradas separadas individualmente.</span><span class="sxs-lookup"><span data-stu-id="9a188-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="9a188-173">Nenhuma degradação elegante: ele dá suporte apenas ao direcionamento ocular.</span><span class="sxs-lookup"><span data-stu-id="9a188-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="9a188-174">Se o acompanhamento ocular não estiver funcionando, você exigirá algum fallback adicional.</span><span class="sxs-lookup"><span data-stu-id="9a188-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="9a188-175">Semelhante ao _BaseFocusHandler_, o _EyeTrackingTarget_ vem pronto com vários eventos específicos do Unity que você pode escutar convenientemente por meio do Editor do Unity (veja o exemplo abaixo) ou usando _AddListener()_ no código:</span><span class="sxs-lookup"><span data-stu-id="9a188-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="9a188-176">OnLookAtStart()</span><span class="sxs-lookup"><span data-stu-id="9a188-176">OnLookAtStart()</span></span>
- <span data-ttu-id="9a188-177">WhileLookingAtTarget()</span><span class="sxs-lookup"><span data-stu-id="9a188-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="9a188-178">OnLookAway()</span><span class="sxs-lookup"><span data-stu-id="9a188-178">OnLookAway()</span></span>
- <span data-ttu-id="9a188-179">OnDwell()</span><span class="sxs-lookup"><span data-stu-id="9a188-179">OnDwell()</span></span>
- <span data-ttu-id="9a188-180">OnSelected()</span><span class="sxs-lookup"><span data-stu-id="9a188-180">OnSelected()</span></span>

<span data-ttu-id="9a188-181">A seguir, explicamos alguns exemplos de como usar _EyeTrackingTarget._</span><span class="sxs-lookup"><span data-stu-id="9a188-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="9a188-182">Exemplo #1: notificações inteligentes com suporte ocular</span><span class="sxs-lookup"><span data-stu-id="9a188-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="9a188-183">Em `EyeTrackingDemo-02-TargetSelection` (Ativos/MRTK/Exemplos/Demonstrações/EyeTracking/Scenes), você pode encontrar um exemplo de _'notificações_ inteligentes de notificação de notificação' que reagem ao seu olhar.</span><span class="sxs-lookup"><span data-stu-id="9a188-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="9a188-184">Essas são caixas de texto 3D que podem ser colocadas na cena e que aumentarão suavemente e se voltarão para o usuário ao serem olhadas para facilitar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="9a188-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="9a188-185">Enquanto o usuário estiver lendo a notificação, as informações continuarão sendo exibidas claras e claras.</span><span class="sxs-lookup"><span data-stu-id="9a188-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="9a188-186">Depois de lê-la e olhar para fora da notificação, a notificação será automaticamente descartada e esmaeça. Para fazer tudo isso, há alguns scripts de comportamento genéricos que não são específicos do acompanhamento ocular, como:</span><span class="sxs-lookup"><span data-stu-id="9a188-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="9a188-187">A vantagem dessa abordagem é que os mesmos scripts podem ser reutilizado por vários eventos.</span><span class="sxs-lookup"><span data-stu-id="9a188-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="9a188-188">Por exemplo, um holograma pode começar a ser voltado para o usuário com base em comandos de voz ou depois de pressionar um botão virtual.</span><span class="sxs-lookup"><span data-stu-id="9a188-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="9a188-189">Para disparar esses eventos, você pode simplesmente referenciar os métodos que devem ser executados no [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script que está anexado ao gameobject.</span><span class="sxs-lookup"><span data-stu-id="9a188-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="9a188-190">Para o exemplo de _' notificações do Smart cuidadosa '_, acontece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9a188-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="9a188-191">**OnLookAtStart ()**: a notificação começa...</span><span class="sxs-lookup"><span data-stu-id="9a188-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="9a188-192">*FaceUser. envolver:* ... Mude para o usuário.</span><span class="sxs-lookup"><span data-stu-id="9a188-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="9a188-193">*Alterações. envolver:* ... aumento de tamanho _(até uma escala máxima especificada)_.</span><span class="sxs-lookup"><span data-stu-id="9a188-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="9a188-194">*Blendout. entrave:* ... começa a misturar em mais _(depois de estar em um estado ocioso mais sutil)_.</span><span class="sxs-lookup"><span data-stu-id="9a188-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="9a188-195">**()**: Informa ao script _blendout_ que a notificação foi examinada de forma suficiente.</span><span class="sxs-lookup"><span data-stu-id="9a188-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="9a188-196">**OnLookAway ()**: a notificação começa...</span><span class="sxs-lookup"><span data-stu-id="9a188-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="9a188-197">*FaceUser. Solte:* ... retorne à sua orientação original.</span><span class="sxs-lookup"><span data-stu-id="9a188-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="9a188-198">*ChangeSize. Solte:* ... diminuir de volta para seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="9a188-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="9a188-199">*Blendout. Solte:* ... começa a Mesclar-se o _()_ foi disparado, mesclar completamente e destruir, de outra forma, de volta ao estado ocioso.</span><span class="sxs-lookup"><span data-stu-id="9a188-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="9a188-200">**Consideração de design:** A chave para uma experiência agradável aqui é ajustar cuidadosamente a velocidade de qualquer um desses comportamentos para evitar a causa de discomfort, reagindo ao olho do usuário olhar muito rápido o tempo todo.</span><span class="sxs-lookup"><span data-stu-id="9a188-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="9a188-201">Caso contrário, isso pode rapidamente ser extremamente impressionante.</span><span class="sxs-lookup"><span data-stu-id="9a188-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="9a188-202">Exemplo #2: o gem Holographic gira lentamente ao olhar para ele</span><span class="sxs-lookup"><span data-stu-id="9a188-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="9a188-203">Semelhante ao exemplo #1, podemos criar facilmente um comentário em foco para nossos Holographic Gems na `EyeTrackingDemo-02-TargetSelection` cena (ativos/MRTK/exemplos/demos/EyeTracking/cenas) que irão girar lentamente em uma direção constante e em uma velocidade constante (em oposição ao exemplo de rotação acima) quando examinado.</span><span class="sxs-lookup"><span data-stu-id="9a188-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="9a188-204">Tudo o que você precisa é disparar a rotação do GEM Holographic do evento _WhileLookingAtTarget ()_ do _EyeTrackingTarget_.</span><span class="sxs-lookup"><span data-stu-id="9a188-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="9a188-205">Aqui estão alguns detalhes:</span><span class="sxs-lookup"><span data-stu-id="9a188-205">Here are a few more details:</span></span>

1. <span data-ttu-id="9a188-206">Crie um script genérico que inclua uma função pública para girar o gameobject ao qual ele está anexado.</span><span class="sxs-lookup"><span data-stu-id="9a188-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="9a188-207">Veja abaixo um exemplo de _RotateWithConstSpeedDir. cs_ , onde podemos ajustar a direção e a velocidade da rotação do editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="9a188-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. <span data-ttu-id="9a188-208">Adicione o [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script ao gameobject de destino e faça referência à função _RotateTarget ()_ no gatilho UnityEvent, conforme mostrado na captura de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="9a188-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![Exemplo de EyeTrackingTarget](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="9a188-210">Exemplo #3: pop essas Gems que _têm o olho multimodal-olhar-seleção de destino com suporte_</span><span class="sxs-lookup"><span data-stu-id="9a188-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="9a188-211">No exemplo anterior, mostramos como é fácil detectar se um destino é examinado e como disparar uma reação a isso.</span><span class="sxs-lookup"><span data-stu-id="9a188-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="9a188-212">Em seguida, vamos fazer o detalhamento das Gems usando o evento _OnSelected ()_ do [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) .</span><span class="sxs-lookup"><span data-stu-id="9a188-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="9a188-213">A parte interessante é *como* a seleção é disparada.</span><span class="sxs-lookup"><span data-stu-id="9a188-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="9a188-214">O [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) permite atribuir rapidamente maneiras diferentes de invocar uma seleção:</span><span class="sxs-lookup"><span data-stu-id="9a188-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="9a188-215">_Gesto de pinçar_: a configuração de ' Selecionar ação ' como ' selecionar ' usa o gesto de mão padrão para disparar a seleção.</span><span class="sxs-lookup"><span data-stu-id="9a188-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="9a188-216">Isso significa que o usuário pode simplesmente aumentar sua mão e pinçar seu polegar e indexar o dedo para confirmar a seleção.</span><span class="sxs-lookup"><span data-stu-id="9a188-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="9a188-217">Diga _"Select"_: Use o comando de voz padrão _"Select"_ para selecionar um holograma.</span><span class="sxs-lookup"><span data-stu-id="9a188-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="9a188-218">Diga _"explosão"_ ou _"pop"_: para usar comandos de voz personalizados, você precisa seguir duas etapas:</span><span class="sxs-lookup"><span data-stu-id="9a188-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="9a188-219">Configurar uma ação personalizada, como _"DestroyTarget"_</span><span class="sxs-lookup"><span data-stu-id="9a188-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="9a188-220">Navegue até _MRTK-> entrada-> ações de entrada_</span><span class="sxs-lookup"><span data-stu-id="9a188-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="9a188-221">Clique em "adicionar uma nova ação"</span><span class="sxs-lookup"><span data-stu-id="9a188-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="9a188-222">Configurar os comandos de voz que disparam essa ação, como _"explodir"_ ou _"pop"_</span><span class="sxs-lookup"><span data-stu-id="9a188-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="9a188-223">Navegue até _MRTK-> de entrada-> fala_</span><span class="sxs-lookup"><span data-stu-id="9a188-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="9a188-224">Clique em "adicionar um novo comando de fala"</span><span class="sxs-lookup"><span data-stu-id="9a188-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="9a188-225">Associar a ação que você acabou de criar</span><span class="sxs-lookup"><span data-stu-id="9a188-225">Associate the action you just created</span></span>
            - <span data-ttu-id="9a188-226">Atribuir um _código_ de Key-prima para permitir o acionamento da ação por meio de um pressionamento de botão</span><span class="sxs-lookup"><span data-stu-id="9a188-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![Exemplo de Comandos de voz EyeTrackingTarget](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="9a188-228">Quando uma gema é selecionada, ela vai estourar, fazendo um som e desaparecendo.</span><span class="sxs-lookup"><span data-stu-id="9a188-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="9a188-229">Isso é tratado pelo [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span><span class="sxs-lookup"><span data-stu-id="9a188-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="9a188-230">Você tem duas opções:</span><span class="sxs-lookup"><span data-stu-id="9a188-230">You have two options:</span></span>

- <span data-ttu-id="9a188-231">**No Editor do Unity:** Você pode simplesmente vincular o script anexado a cada um dos nossos modelos gem ao evento OnSelected() Unity no Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="9a188-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="9a188-232">**No código:** Se você não quiser arrastar e soltar GameObjects, também poderá simplesmente adicionar um ouvinte de eventos diretamente ao script.</span><span class="sxs-lookup"><span data-stu-id="9a188-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="9a188-233">Veja um exemplo de como fizemos isso no [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span><span class="sxs-lookup"><span data-stu-id="9a188-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="9a188-234">Exemplo #4: usar raios de mão e entrada de olhar juntos</span><span class="sxs-lookup"><span data-stu-id="9a188-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="9a188-235">Os raios de mão têm prioridade sobre o direcionamento do olhar e da cabeça.</span><span class="sxs-lookup"><span data-stu-id="9a188-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="9a188-236">Isso significa que, se os raios de mão estão habilitados, no momento em que as mãos são vistas, o raio de mão atuará como o ponteiro primário.</span><span class="sxs-lookup"><span data-stu-id="9a188-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="9a188-237">No entanto, pode haver situações em que você deseja usar raios de mão enquanto ainda detecta se um usuário está olhando para um determinado holograma.</span><span class="sxs-lookup"><span data-stu-id="9a188-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="9a188-238">Muito fácil.</span><span class="sxs-lookup"><span data-stu-id="9a188-238">Easy!</span></span> <span data-ttu-id="9a188-239">Essencialmente, você precisa de duas etapas:</span><span class="sxs-lookup"><span data-stu-id="9a188-239">Essentially you require two steps:</span></span>

<span data-ttu-id="9a188-240">**1. Habilitar o** raio de mão: para habilitar o raio de mão, acesse Kit de Ferramentas de Realidade Misturada _-> Entrada -> Ponteiros_.</span><span class="sxs-lookup"><span data-stu-id="9a188-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="9a188-241">No _EyeTrackingDemo-00-RootScene_ em que o Kit de Ferramentas de Realidade Misturada é configurado uma vez para todas as cenas de demonstração de acompanhamento ocular, você deve ver _o EyeTrackingDemoPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="9a188-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="9a188-242">Você pode criar um novo Perfil _de Entrada do_ zero ou adaptar o acompanhamento ocular atual:</span><span class="sxs-lookup"><span data-stu-id="9a188-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="9a188-243">**Do zero:** Na guia _Ponteiros,_ selecione _DefaultMixedRealityInputPointerProfile_ no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="9a188-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="9a188-244">Esse é o perfil de ponteiro padrão que já tem o raio de mão habilitado!</span><span class="sxs-lookup"><span data-stu-id="9a188-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="9a188-245">Para alterar o cursor padrão (um ponto branco opaco), basta clonar o perfil e criar seu próprio perfil de ponteiro personalizado.</span><span class="sxs-lookup"><span data-stu-id="9a188-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="9a188-246">Em seguida, _substitua DefaultCursor_ por _EyeGazeCursor em_ _Prefab do Cursor de_ Olhar.</span><span class="sxs-lookup"><span data-stu-id="9a188-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="9a188-247">**Com base no _EyeTrackingDemoPointerProfile_ existente:** clique duas vezes no _EyeTrackingDemoPointerProfile_ e adicione a seguinte entrada em Opções _de Ponteiro:_</span><span class="sxs-lookup"><span data-stu-id="9a188-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="9a188-248">**Tipo de controlador:** "Mão articulada", "realidade misturada do Windows"</span><span class="sxs-lookup"><span data-stu-id="9a188-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="9a188-249">**Destromente:** Outro</span><span class="sxs-lookup"><span data-stu-id="9a188-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="9a188-250">**Pré-fabricado do ponteiro:** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="9a188-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="9a188-251">**2. detecte que um holograma é examinado:** use o [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script para habilitar a detecção de um holograma examinado conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="9a188-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="9a188-252">Você também pode dar uma olhada no `FollowEyeGaze` script de exemplo para inspiração, pois isso mostra um holograma seguindo o olhar de olho (por exemplo, um cursor) se os raios à mão estão habilitados ou não.</span><span class="sxs-lookup"><span data-stu-id="9a188-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="9a188-253">Agora, ao iniciar os bastidores de demonstração de controle de olho, você verá um raio vindo de suas mãos.</span><span class="sxs-lookup"><span data-stu-id="9a188-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="9a188-254">Por exemplo, na demonstração de seleção de destino de acompanhamento de olho, o círculo semitransparente ainda está seguindo seus olhos olhar e as Gems respondem se eles são examinados ou não, enquanto os botões de menu de cena superior usam o ponteiro de entrada primário (suas mãos) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9a188-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="9a188-255">Voltar para "acompanhamento de olho no MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="9a188-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
