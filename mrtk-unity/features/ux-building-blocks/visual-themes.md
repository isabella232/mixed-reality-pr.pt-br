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
# <a name="visual-themes"></a>Temas visuais

Os temas permitem o controle flexível dos ativos de UX em resposta a várias transições de Estados. Isso pode envolver a alteração da cor de um botão, o redimensionamento de um elemento em resposta ao foco, etc. A estrutura visual Themes é composta de duas partes principais: 1) configuração e 2) mecanismos de tempo de execução.

[As configurações de tema](#theme-configuration) são definições de propriedades e tipos, enquanto os [mecanismos de tema](#theme-engines) são classes que consomem as configurações e implementam a lógica para atualizar transformações, materiais e muito mais no tempo de execução.

## <a name="theme-configuration"></a>Configuração de tema

As configurações de tema são [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) que definem como os mecanismos de tema serão inicializados em tempo de execução. Eles definem quais propriedades e valores utilizar em resposta à entrada ou outras alterações de estado quando o aplicativo está em execução. Como ativos [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , as configurações de tema podem ser definidas uma vez e, em seguida, reutilizadas em diferentes componentes de UX.

Para criar um novo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ativo:

1) clique com o botão direito do mouse na *janela Project*
1) selecione **criar**  >  **realidade misturada Toolkit**  >  **tema**

Os ativos de configuração de tema de exemplo podem ser encontrados em `MRTK/SDK/Features/UX/Interactable/Themes` .

![Exemplo de ScriptableObject de tema no Inspetor](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>Estados

Ao criar um novo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , a primeira coisa a ser definida é que os Estados estão disponíveis. A propriedade *States* indica quantos valores uma configuração de tema precisa definir, pois haverá um valor por Estado. Na imagem de exemplo acima, os [Estados padrão definidos para o componente interagir](interactable.md#general-input-settings) são *padrão*, *foco*, *pressionado* e *desabilitado*. Eles são definidos no `DefaultInteractableStates` arquivo de ativo (assets/MRTK/SDK/Features/UX/interagible/States).

Para criar um novo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ativo:

1) clique com o botão direito do mouse na *janela Project*
1) selecione **criar**  >  **realidade misturada Toolkit**  >  **estado**

![Exemplo de Estados ScriptableObject no Inspetor](../images/interactable/DefaultInteractableStates.png)

Um [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject define a lista de Estados, bem como o tipo de *StateModel* a ser criado para esses Estados. Um *StateModel* é uma classe que estende [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) e implementa a lógica da máquina de estado para gerar o estado atual em tempo de execução. O estado atual dessa classe geralmente é usado pelos mecanismos de tema no tempo de execução para ditar quais valores definir em relação a propriedades de material, transformações gameobject e muito mais.

### <a name="theme-engine-properties"></a>Propriedades do mecanismo de tema

Fora dos *Estados*, um [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ativo também define uma lista de mecanismos de tema e as propriedades associadas para esses mecanismos. Um [mecanismo de tema](#theme-engines) novamente define a lógica para definir os valores corretos em relação a um gameobject no tempo de execução.

Um [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ativo pode definir vários mecanismos de tema para obter transições de Estados visuais sofisticados direcionando várias propriedades gameobject.

**Tempo de execução do tema**

Define o tipo de classe do mecanismo de tema que será criado

**Facilitar**

Alguns *mecanismos de tema*, se definirem sua propriedade [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) como true, dão suporte a atenuação entre Estados. Por exemplo, lerping entre duas cores quando ocorre uma alteração de estado. A *duração* define, em segundos, o tempo de vida do valor inicial para o valor final e a *curva de animação* define a taxa de alteração durante esse período de tempo.

**Propriedades do sombreador**

Alguns *mecanismos de tema*, se definirem sua propriedade [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) como true, modificarão Propriedades de sombreador específicas em tempo de execução. Os campos *sombreador* e *Propriedade* definem a propriedade Shader como Target.

### <a name="create-a-theme-configuration-via-code"></a>Criar uma configuração de tema por meio de código

Em geral, é mais fácil criar configurações de tema por meio do Inspetor do Unity, mas há casos em que os temas devem ser gerados dinamicamente em tempo de execução por meio de código. O trecho de código abaixo fornece um exemplo de como realizar essa tarefa.

Para ajudar a agilizar o desenvolvimento, os métodos auxiliares a seguir são úteis para simplificar a instalação.

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -Cria um novo ScriptableObject de Estados com os quatro valores de estado padrão usados no componente de [interação](interactable.md) .

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -Cada mecanismo de tema define uma configuração padrão com as propriedades corretas necessárias para esse tipo de tempo de execução de tema. Esse auxiliar cria uma definição para o tipo de mecanismo de tema determinado.

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

## <a name="theme-engines"></a>Mecanismos de tema

Um [mecanismo de tema](#theme-engines) é uma classe que se estende da [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe. Essas classes são instanciadas em tempo de execução e configuradas com um [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objeto conforme descrito anteriormente.

### <a name="default-theme-engines"></a>Mecanismos de tema padrão

O MRTK é fornecido com um conjunto padrão de mecanismos de tema listados abaixo:

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

Os mecanismos de tema padrão podem ser encontrados em `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .

### <a name="custom-theme-engines"></a>Mecanismos de tema personalizados

Como mencionado, um mecanismo de tema é definido como uma classe que se estende da [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe. Assim, o novo mecanismo de tema só precisa estender essa classe e implementar o seguinte:

#### <a name="mandatory-implementations"></a>Implementações obrigatórias

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref: Microsoft. MixedReality. Toolkit. Conectável. InteractableThemeBase. SetValue)

Para a propriedade fornecida, que pode ser identificada pelo `ThemeStateProperty.Name` , defina seu valor de estado atual no host gameobject de destino (ou seja, Defina a cor do material, etc.). O *índice* indica o valor de estado atual a ser acessado e a *porcentagem*, um float entre 0 e 1, é usado para atenuar/lerping entre valores.

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref: Microsoft. MixedReality. Toolkit. Conectável. InteractableThemeBase. GetProperty)

Para a propriedade fornecida, que pode ser identificada pelo `ThemeStateProperty.Name` , retorne o valor atual definido no host de destino gameobject (ou seja, a cor do material atual, o deslocamento da posição local atual, etc.). Isso é usado principalmente para armazenar em cache o valor inicial ao facilitar a atenuação entre Estados.

`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref: Microsoft. MixedReality. Toolkit. Conectável. InteractableThemeBase.GetDefaultThemeDefinition)

Retorna um [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objeto que define as propriedades padrão e a configuração necessárias para o tema personalizado

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

Variante protegida da definição pública `SetValue()` , exceto pelo ThemePropertyValue fornecido para definir em vez de direcionar para usar a configuração de índice e/ou porcentagem.

#### <a name="recommended-overrides"></a>Substituições recomendadas

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

Execute todas as etapas de inicialização aqui direcionando o parâmetro *gameobject* fornecido e usando as propriedades e configurações definidas no parâmetro *ThemeDefinition* . É recomendável chamar `base.Init(host, settings)` no início de uma substituição.

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

Se o mecanismo de tema personalizado puder dar suporte à atenuação entre valores configurados por meio da [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) propriedade.

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

Se o mecanismo de tema personalizado puder dar suporte a propriedades de sombreador de destino. É recomendável estender de [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) para se beneficiar da infraestrutura existente para definir/obter propriedades do sombreador com eficiência via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html). As informações de Propriedade do sombreador são armazenadas em cada [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) por meio [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) de e [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .

> [!NOTE]
> Se estiver estendendo [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) , também poderá ser útil substituir o [InteractableShaderTheme. defaultshaderproperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) por meio de *New*.
>
> Código de exemplo: `protected new const string DefaultShaderProperty = "_Color";`
>
> Além disso, as seguintes classes abaixo estendem a [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) classe que usa novamente [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) para modificar os valores de Propriedade do sombreador. Essa abordagem [ajuda o desempenho](https://docs.unity3d.com/Manual/DrawCallBatching.html) porque o *MaterialPropertyBlocks* não cria novos materiais de instância quando os valores são alterados. No entanto, o acesso às propriedades típicas da classe [material](https://docs.unity3d.com/ScriptReference/Material.html) não retornará os valores esperados. Use *MaterialPropertyBlocks* para obter e validar os valores de propriedade de material atuais (ou seja, *_Color* ou *_MainTex*).
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

Direciona o tema para redefinir quaisquer propriedades modificadas de volta para seus valores originais que foram definidos no host gameobject quando este mecanismo de tema foi inicializado.  

### <a name="custom-theme-engine-example"></a>Exemplo de mecanismo de tema personalizado

A classe a seguir é um exemplo de um novo mecanismo de tema personalizado. Essa implementação encontrará um componente [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) no objeto de host inicializado e controlará sua visibilidade com base no estado atual.

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

## <a name="end-to-end-example"></a>Exemplo de ponta a ponta

Estendendo do mecanismo de tema personalizado definido na seção anterior, o exemplo de código a seguir demonstra como controlar esse tema em tempo de execução. Em particular, como definir o estado atual no tema para que a visibilidade de MeshRenderer seja atualizada adequadamente.

> [!NOTE]
> `theme.OnUpdate(state,force)` deve ser geralmente chamado no método Update () para dar suporte a mecanismos de tema que utilizam a atenuação/lerping entre valores.

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

## <a name="see-also"></a>Confira também

- [Interativo](interactable.md)
