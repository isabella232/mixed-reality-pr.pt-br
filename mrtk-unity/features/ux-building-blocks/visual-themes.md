---
title: Temas visuais
description: Visão geral dos temas visuais controle flexível dos ativos de UX no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, temas de MRTK,
ms.openlocfilehash: d97c470bf1d77299c6848990cdc69d886d432ecb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177168"
---
# <a name="visual-themes"></a><span data-ttu-id="11a01-104">Temas visuais</span><span class="sxs-lookup"><span data-stu-id="11a01-104">Visual themes</span></span>

<span data-ttu-id="11a01-105">Os temas permitem o controle flexível dos ativos de UX em resposta a várias transições de Estados.</span><span class="sxs-lookup"><span data-stu-id="11a01-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="11a01-106">Isso pode envolver a alteração da cor de um botão, o redimensionamento de um elemento em resposta ao foco, etc. A estrutura visual Themes é composta de duas partes principais: 1) configuração e 2) mecanismos de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="11a01-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="11a01-107">[As configurações de tema](#theme-configuration) são definições de propriedades e tipos, enquanto os [mecanismos de tema](#theme-engines) são classes que consomem as configurações e implementam a lógica para atualizar transformações, materiais e muito mais no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="11a01-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="11a01-108">Configuração de tema</span><span class="sxs-lookup"><span data-stu-id="11a01-108">Theme configuration</span></span>

<span data-ttu-id="11a01-109">As configurações de tema são [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) que definem como os mecanismos de tema serão inicializados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="11a01-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="11a01-110">Eles definem quais propriedades e valores utilizar em resposta à entrada ou outras alterações de estado quando o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="11a01-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="11a01-111">Como ativos [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , as configurações de tema podem ser definidas uma vez e, em seguida, reutilizadas em diferentes componentes de UX.</span><span class="sxs-lookup"><span data-stu-id="11a01-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="11a01-112">Para criar um novo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ativo:</span><span class="sxs-lookup"><span data-stu-id="11a01-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="11a01-113">clique com o botão direito do mouse na *janela Project*</span><span class="sxs-lookup"><span data-stu-id="11a01-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="11a01-114">selecione **criar**  >  **realidade misturada Toolkit**  >  **tema**</span><span class="sxs-lookup"><span data-stu-id="11a01-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="11a01-115">Os ativos de configuração de tema de exemplo podem ser encontrados em `MRTK/SDK/Features/UX/Interactable/Themes` .</span><span class="sxs-lookup"><span data-stu-id="11a01-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Exemplo de ScriptableObject de tema no Inspetor](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="11a01-117">Estados</span><span class="sxs-lookup"><span data-stu-id="11a01-117">States</span></span>

<span data-ttu-id="11a01-118">Ao criar um novo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , a primeira coisa a ser definida é que os Estados estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="11a01-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="11a01-119">A propriedade *States* indica quantos valores uma configuração de tema precisa definir, pois haverá um valor por Estado.</span><span class="sxs-lookup"><span data-stu-id="11a01-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="11a01-120">Na imagem de exemplo acima, os [Estados padrão definidos para o componente interagir](interactable.md#general-input-settings) são *padrão*, *foco*, *pressionado* e *desabilitado*.</span><span class="sxs-lookup"><span data-stu-id="11a01-120">In the example image above, the [default states defined for the Interactable](interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="11a01-121">Eles são definidos no `DefaultInteractableStates` arquivo de ativo (assets/MRTK/SDK/Features/UX/interagible/States).</span><span class="sxs-lookup"><span data-stu-id="11a01-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="11a01-122">Para criar um novo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ativo:</span><span class="sxs-lookup"><span data-stu-id="11a01-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="11a01-123">clique com o botão direito do mouse na *janela Project*</span><span class="sxs-lookup"><span data-stu-id="11a01-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="11a01-124">selecione **criar**  >  **realidade misturada Toolkit**  >  **estado**</span><span class="sxs-lookup"><span data-stu-id="11a01-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![Exemplo de Estados ScriptableObject no Inspetor](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="11a01-126">Um [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject define a lista de Estados, bem como o tipo de *StateModel* a ser criado para esses Estados.</span><span class="sxs-lookup"><span data-stu-id="11a01-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="11a01-127">Um *StateModel* é uma classe que estende [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) e implementa a lógica da máquina de estado para gerar o estado atual em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="11a01-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="11a01-128">O estado atual dessa classe geralmente é usado pelos mecanismos de tema no tempo de execução para ditar quais valores definir em relação a propriedades de material, transformações gameobject e muito mais.</span><span class="sxs-lookup"><span data-stu-id="11a01-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="11a01-129">Propriedades do mecanismo de tema</span><span class="sxs-lookup"><span data-stu-id="11a01-129">Theme engine properties</span></span>

<span data-ttu-id="11a01-130">Fora dos *Estados*, um [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ativo também define uma lista de mecanismos de tema e as propriedades associadas para esses mecanismos.</span><span class="sxs-lookup"><span data-stu-id="11a01-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="11a01-131">Um [mecanismo de tema](#theme-engines) novamente define a lógica para definir os valores corretos em relação a um gameobject no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="11a01-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="11a01-132">Um [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ativo pode definir vários mecanismos de tema para obter transições de Estados visuais sofisticados direcionando várias propriedades gameobject.</span><span class="sxs-lookup"><span data-stu-id="11a01-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="11a01-133">**Tempo de execução do tema**</span><span class="sxs-lookup"><span data-stu-id="11a01-133">**Theme Runtime**</span></span>

<span data-ttu-id="11a01-134">Define o tipo de classe do mecanismo de tema que será criado</span><span class="sxs-lookup"><span data-stu-id="11a01-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="11a01-135">**Facilitar**</span><span class="sxs-lookup"><span data-stu-id="11a01-135">**Easing**</span></span>

<span data-ttu-id="11a01-136">Alguns *mecanismos de tema*, se definirem sua propriedade [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) como true, dão suporte a atenuação entre Estados.</span><span class="sxs-lookup"><span data-stu-id="11a01-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="11a01-137">Por exemplo, lerping entre duas cores quando ocorre uma alteração de estado.</span><span class="sxs-lookup"><span data-stu-id="11a01-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="11a01-138">A *duração* define, em segundos, o tempo de vida do valor inicial para o valor final e a *curva de animação* define a taxa de alteração durante esse período de tempo.</span><span class="sxs-lookup"><span data-stu-id="11a01-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="11a01-139">**Propriedades do sombreador**</span><span class="sxs-lookup"><span data-stu-id="11a01-139">**Shader properties**</span></span>

<span data-ttu-id="11a01-140">Alguns *mecanismos de tema*, se definirem sua propriedade [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) como true, modificarão Propriedades de sombreador específicas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="11a01-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="11a01-141">Os campos *sombreador* e *Propriedade* definem a propriedade Shader como Target.</span><span class="sxs-lookup"><span data-stu-id="11a01-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="11a01-142">Criar uma configuração de tema por meio de código</span><span class="sxs-lookup"><span data-stu-id="11a01-142">Create a theme configuration via code</span></span>

<span data-ttu-id="11a01-143">Em geral, é mais fácil criar configurações de tema por meio do Inspetor do Unity, mas há casos em que os temas devem ser gerados dinamicamente em tempo de execução por meio de código.</span><span class="sxs-lookup"><span data-stu-id="11a01-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="11a01-144">O trecho de código abaixo fornece um exemplo de como realizar essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="11a01-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="11a01-145">Para ajudar a agilizar o desenvolvimento, os métodos auxiliares a seguir são úteis para simplificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="11a01-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="11a01-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -Cria um novo ScriptableObject de Estados com os quatro valores de estado padrão usados no componente de [interação](interactable.md) .</span><span class="sxs-lookup"><span data-stu-id="11a01-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](interactable.md) component.</span></span>

<span data-ttu-id="11a01-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -Cada mecanismo de tema define uma configuração padrão com as propriedades corretas necessárias para esse tipo de tempo de execução de tema.</span><span class="sxs-lookup"><span data-stu-id="11a01-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="11a01-148">Esse auxiliar cria uma definição para o tipo de mecanismo de tema determinado.</span><span class="sxs-lookup"><span data-stu-id="11a01-148">This helper creates a definition for the given Theme Engine type.</span></span>

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a><span data-ttu-id="11a01-149">Mecanismos de tema</span><span class="sxs-lookup"><span data-stu-id="11a01-149">Theme engines</span></span>

<span data-ttu-id="11a01-150">Um [mecanismo de tema](#theme-engines) é uma classe que se estende da [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe.</span><span class="sxs-lookup"><span data-stu-id="11a01-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="11a01-151">Essas classes são instanciadas em tempo de execução e configuradas com um [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objeto conforme descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="11a01-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="11a01-152">Mecanismos de tema padrão</span><span class="sxs-lookup"><span data-stu-id="11a01-152">Default theme engines</span></span>

<span data-ttu-id="11a01-153">O MRTK é fornecido com um conjunto padrão de mecanismos de tema listados abaixo:</span><span class="sxs-lookup"><span data-stu-id="11a01-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

<span data-ttu-id="11a01-154">Os mecanismos de tema padrão podem ser encontrados em `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .</span><span class="sxs-lookup"><span data-stu-id="11a01-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="11a01-155">Mecanismos de tema personalizados</span><span class="sxs-lookup"><span data-stu-id="11a01-155">Custom theme engines</span></span>

<span data-ttu-id="11a01-156">Como mencionado, um mecanismo de tema é definido como uma classe que se estende da [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe.</span><span class="sxs-lookup"><span data-stu-id="11a01-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="11a01-157">Assim, o novo mecanismo de tema só precisa estender essa classe e implementar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="11a01-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="11a01-158">Implementações obrigatórias</span><span class="sxs-lookup"><span data-stu-id="11a01-158">Mandatory implementations</span></span>

<span data-ttu-id="11a01-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref: Microsoft. MixedReality. Toolkit. Conectável. InteractableThemeBase. SetValue)</span><span class="sxs-lookup"><span data-stu-id="11a01-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="11a01-160">Para a propriedade fornecida, que pode ser identificada pelo `ThemeStateProperty.Name` , defina seu valor de estado atual no host gameobject de destino (ou seja,</span><span class="sxs-lookup"><span data-stu-id="11a01-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="11a01-161">Defina a cor do material, etc.).</span><span class="sxs-lookup"><span data-stu-id="11a01-161">set the material color, etc).</span></span> <span data-ttu-id="11a01-162">O *índice* indica o valor de estado atual a ser acessado e a *porcentagem*, um float entre 0 e 1, é usado para atenuar/lerping entre valores.</span><span class="sxs-lookup"><span data-stu-id="11a01-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="11a01-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref: Microsoft. MixedReality. Toolkit. Conectável. InteractableThemeBase. GetProperty)</span><span class="sxs-lookup"><span data-stu-id="11a01-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="11a01-164">Para a propriedade fornecida, que pode ser identificada pelo `ThemeStateProperty.Name` , retorne o valor atual definido no host de destino gameobject (ou seja,</span><span class="sxs-lookup"><span data-stu-id="11a01-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="11a01-165">a cor do material atual, o deslocamento da posição local atual, etc.).</span><span class="sxs-lookup"><span data-stu-id="11a01-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="11a01-166">Isso é usado principalmente para armazenar em cache o valor inicial ao facilitar a atenuação entre Estados.</span><span class="sxs-lookup"><span data-stu-id="11a01-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="11a01-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref: Microsoft. MixedReality. Toolkit. Conectável. InteractableThemeBase.GetDefaultThemeDefinition)</span><span class="sxs-lookup"><span data-stu-id="11a01-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="11a01-168">Retorna um [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objeto que define as propriedades padrão e a configuração necessárias para o tema personalizado</span><span class="sxs-lookup"><span data-stu-id="11a01-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="11a01-169">Variante protegida da definição pública `SetValue()` , exceto pelo ThemePropertyValue fornecido para definir em vez de direcionar para usar a configuração de índice e/ou porcentagem.</span><span class="sxs-lookup"><span data-stu-id="11a01-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="11a01-170">Substituições recomendadas</span><span class="sxs-lookup"><span data-stu-id="11a01-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="11a01-171">Execute todas as etapas de inicialização aqui direcionando o parâmetro *gameobject* fornecido e usando as propriedades e configurações definidas no parâmetro *ThemeDefinition* .</span><span class="sxs-lookup"><span data-stu-id="11a01-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="11a01-172">É recomendável chamar `base.Init(host, settings)` no início de uma substituição.</span><span class="sxs-lookup"><span data-stu-id="11a01-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="11a01-173">Se o mecanismo de tema personalizado puder dar suporte à atenuação entre valores configurados por meio da [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) propriedade.</span><span class="sxs-lookup"><span data-stu-id="11a01-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="11a01-174">Se o mecanismo de tema personalizado puder dar suporte a propriedades de sombreador de destino.</span><span class="sxs-lookup"><span data-stu-id="11a01-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="11a01-175">É recomendável estender de [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) para se beneficiar da infraestrutura existente para definir/obter propriedades do sombreador com eficiência via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span><span class="sxs-lookup"><span data-stu-id="11a01-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="11a01-176">As informações de Propriedade do sombreador são armazenadas em cada [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) por meio [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) de e [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .</span><span class="sxs-lookup"><span data-stu-id="11a01-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="11a01-177">Se estiver estendendo [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) , também poderá ser útil substituir o [InteractableShaderTheme. defaultshaderproperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) por meio de *New*.</span><span class="sxs-lookup"><span data-stu-id="11a01-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="11a01-178">Código de exemplo: `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="11a01-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="11a01-179">Além disso, as seguintes classes abaixo estendem a [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) classe que usa novamente [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) para modificar os valores de Propriedade do sombreador.</span><span class="sxs-lookup"><span data-stu-id="11a01-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="11a01-180">Essa abordagem [ajuda o desempenho](https://docs.unity3d.com/Manual/DrawCallBatching.html) porque o *MaterialPropertyBlocks* não cria novos materiais de instância quando os valores são alterados.</span><span class="sxs-lookup"><span data-stu-id="11a01-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="11a01-181">No entanto, o acesso às propriedades típicas da classe [material](https://docs.unity3d.com/ScriptReference/Material.html) não retornará os valores esperados.</span><span class="sxs-lookup"><span data-stu-id="11a01-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="11a01-182">Use *MaterialPropertyBlocks* para obter e validar os valores de propriedade de material atuais (ou seja,</span><span class="sxs-lookup"><span data-stu-id="11a01-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="11a01-183">*_Color* ou *_MainTex*).</span><span class="sxs-lookup"><span data-stu-id="11a01-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="11a01-184">Direciona o tema para redefinir quaisquer propriedades modificadas de volta para seus valores originais que foram definidos no host gameobject quando este mecanismo de tema foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="11a01-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="11a01-185">Exemplo de mecanismo de tema personalizado</span><span class="sxs-lookup"><span data-stu-id="11a01-185">Custom theme engine example</span></span>

<span data-ttu-id="11a01-186">A classe a seguir é um exemplo de um novo mecanismo de tema personalizado.</span><span class="sxs-lookup"><span data-stu-id="11a01-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="11a01-187">Essa implementação encontrará um componente [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) no objeto de host inicializado e controlará sua visibilidade com base no estado atual.</span><span class="sxs-lookup"><span data-stu-id="11a01-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a><span data-ttu-id="11a01-188">Exemplo de ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="11a01-188">End-to-end example</span></span>

<span data-ttu-id="11a01-189">Estendendo do mecanismo de tema personalizado definido na seção anterior, o exemplo de código a seguir demonstra como controlar esse tema em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="11a01-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="11a01-190">Em particular, como definir o estado atual no tema para que a visibilidade de MeshRenderer seja atualizada adequadamente.</span><span class="sxs-lookup"><span data-stu-id="11a01-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="11a01-191">`theme.OnUpdate(state,force)` deve ser geralmente chamado no método Update () para dar suporte a mecanismos de tema que utilizam a atenuação/lerping entre valores.</span><span class="sxs-lookup"><span data-stu-id="11a01-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="11a01-192">Confira também</span><span class="sxs-lookup"><span data-stu-id="11a01-192">See also</span></span>

- [<span data-ttu-id="11a01-193">Interativo</span><span class="sxs-lookup"><span data-stu-id="11a01-193">Interactable</span></span>](interactable.md)
