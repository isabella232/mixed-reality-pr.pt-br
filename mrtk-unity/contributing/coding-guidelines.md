---
title: Diretrizes de codificação
description: Princípios e convenções de codificação a seguir ao contribuir com o MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, C#,
ms.openlocfilehash: c14f5f72d391c5474a01c798bfdaa5529700a509
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175328"
---
# <a name="coding-guidelines"></a>Diretrizes de codificação

Este documento descreve os princípios e as convenções de codificação a seguir ao contribuir com o MRTK.

---

## <a name="philosophy"></a>Filosofia

### <a name="be-concise-and-strive-for-simplicity"></a>Seja conciso e busque a simplicidade

A solução mais simples geralmente é a melhor. Esse é um objetivo que substitui essas diretrizes e deve ser a meta de todas as atividades de codificação. Parte de ser simples é ser conciso e consistente com o código existente. Tente manter seu código simples.

Os leitores só devem encontrar artefatos que forneçam informações úteis. Por exemplo, comentários que restate o que é óbvio não fornecem informações adicionais e aumentam a taxa de ruído para sinal.

Mantenha a lógica de código simples. Observe que essa não é uma instrução sobre como usar o menor número de linhas, minimizando o tamanho dos nomes de identificador ou o estilo da chave, mas sobre como reduzir o número de conceitos e maximizar a visibilidade deles por meio de padrões familiares.

### <a name="produce-consistent-readable-code"></a>Produzir código consistente e acessível

A leitura do código está correlacionada com baixas taxas de defeito. Busque criar um código que seja fácil de ler. Busque criar código que tenha lógica simples e re use componentes existentes, pois ele também ajudará a garantir a correção.

Todos os detalhes do código produzido são importantes, desde os detalhes mais básicos de correção até o estilo e a formatação consistentes. Mantenha seu estilo de codificação consistente com o que já existe, mesmo que ele não seja correspondente à sua preferência. Isso aumenta a capacidade de leitura da base de código geral.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>Suporte à configuração de componentes no editor e no tempo de run-time

O MRTK dá suporte a um conjunto diversificado de usuários – pessoas que preferem configurar componentes no editor do Unity e carregar pré-requisitos e pessoas que precisam criar uma inciação e configurar objetos em tempo de run-time.

Todo o código deve funcionar adicionando um componente a um GameObject em uma cena salva e instando esse componente no código. Os testes devem incluir um caso de teste para infiguração de pré-requisitos e insta instaência, configurando o componente em runtime.

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>Play-in-editor é sua primeira plataforma de destino e principal

O Play-In-Editor é a maneira mais rápida de iterar no Unity. Fornecer maneiras para nossos clientes iterar rapidamente permite que eles desenvolvam soluções mais rapidamente e experimentem mais ideias. Em outras palavras, maximizar a velocidade da iteração capacita nossos clientes a alcançarem mais.

Faça tudo funcionar no editor e, em seguida, faça com que funcione em qualquer outra plataforma. Mantenha-o funcionando no editor. É fácil adicionar uma nova plataforma ao Play-In-Editor. É muito difícil fazer com que o Play-In-Editor funcione se seu aplicativo funciona apenas em um dispositivo.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>Adicionar novos campos públicos, propriedades, métodos e campos privados serializados com cuidado

Sempre que você adiciona um método público, campo, propriedade, ele se torna parte da superfície de API pública do MRTK. Campos privados marcados `[SerializeField]` com também expõem campos ao editor e fazem parte da superfície de API pública. Outras pessoas podem usar esse método público, configurar pré-fabs personalizados com seu campo público e assumir uma dependência dele.

Novos membros públicos devem ser examinados cuidadosamente. Qualquer campo público precisará ser mantido no futuro. Lembre-se de que, se o tipo de um campo público (ou campo privado serializado) mudar ou for removido de um MonoBehaviour, isso poderá quebrar outras pessoas. O campo precisará primeiro ser preterido para uma versão e o código para migrar as alterações para as pessoas que têm dependências precisaria ser fornecido.

### <a name="prioritize-writing-tests"></a>Priorizar a escrita de testes

O MRTK é um projeto da comunidade, modificado por uma variedade diversificada de colaboradores. Esses colaboradores podem não saber os detalhes de sua correção de bug/recurso e acidentalmente quebrar seu recurso. [O MRTK executa testes de integração contínua](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) antes de concluir cada solicitação de pull. As alterações que quebram os testes não podem ser verificadas. Portanto, os testes são a melhor maneira de garantir que outras pessoas não violem seu recurso.

Quando você corrigir um bug, escreva um teste para garantir que ele não regreda no futuro. Se adicionar um recurso, escreva testes que verifiquem se o recurso funciona. Isso é necessário para todos os recursos de UX, exceto recursos experimentais.

## <a name="c-coding-conventions"></a>Convenções de codificação em C#

### <a name="script-license-information-headers"></a>Headers de informações de licença de script

Todos os funcionários da Microsoft que contribuem com novos arquivos devem adicionar o seguinte header de Licença padrão na parte superior de todos os novos arquivos, exatamente como mostrado abaixo:

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>Headers de resumo de função/método

Todas as classes públicas, structs, enums, funções, propriedades, campos postados no MRTK devem ser descritos como para sua finalidade e uso, exatamente como mostrado abaixo:

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

Isso garante que a documentação seja gerada e difundida corretamente para todas as classes, métodos e propriedades.

Todos os arquivos de script enviados sem marcas de resumo adequadas serão rejeitados.

### <a name="mrtk-namespace-rules"></a>Regras de namespace do MRTK

A Toolkit realidade misturada usa um modelo de namespace baseado em recursos, em que todos os namespaces fundamentais começam com "Microsoft.MixedReality. Toolkit". Em geral, você não precisa especificar a camada do kit de ferramentas (por ex. Core, Provedores, Serviços) em seus namespaces.

Os namespaces definidos no momento são:

- Microsoft.MixedReality. Toolkit
- Microsoft.MixedReality. Toolkit. Limite
- Microsoft.MixedReality. Toolkit. Diagnostics
- Microsoft.MixedReality. Toolkit. Editor
- Microsoft.MixedReality. Toolkit. Entrada
- Microsoft.MixedReality. Toolkit. SpatialAwareness
- Microsoft.MixedReality. Toolkit. Teleport
- Microsoft.MixedReality. Toolkit. Utilitários

Para namespaces com uma grande quantidade de tipos, é aceitável criar um número limitado de sub-namespaces para auxiliar no uso do scoping.

Omitir o namespace para uma interface, classe ou tipo de dados fará com que a alteração seja bloqueada.

### <a name="adding-new-monobehaviour-scripts"></a>Adicionando novos scripts MonoBehaviour

Ao adicionar novos scripts MonoBehaviour com uma solicitação de pull, verifique se o atributo é aplicado a [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) todos os arquivos aplicáveis. Isso garante que o componente seja facilmente descoberto no editor sob o *botão Adicionar* Componente. O sinalizador de atributo não será necessário se o componente não puder aparecer no editor, como uma classe abstrata.

No exemplo a seguir, o *pacote aqui* deve ser preenchido com o local do pacote do componente. Se colocar um item na pasta *MRTK/SDK,* o pacote será *SDK*.

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>Adicionando novos scripts de inspetor do Unity

Em geral, tente evitar a criação de scripts de inspetor personalizados para componentes do MRTK. Ele adiciona sobrecarga adicional e gerenciamento da base de código que pode ser manipulada pelo mecanismo do Unity.

Se uma classe inspetor for necessária, tente usar o [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) do Unity. Isso simplifica novamente a classe inspetor e deixa grande parte do trabalho para o Unity.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

Se a renderização personalizada for necessária na classe inspetor, tente utilizar [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) e [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) . Isso garantirá que o Unity lida corretamente com a renderização de pré-fabs aninhados e valores modificados.

Se [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) não puder ser usado devido a um requisito na lógica personalizada, verifique se todo o uso está envolvido em torno de um [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) . Isso garantirá que o Unity renderiza o inspetor corretamente para pré-fabs aninhados e valores modificados com a propriedade determinada.

Além disso, tente decorar a classe de inspetor personalizado com um [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) . Essa marca garante que vários objetos com esse componente na cena possam ser selecionados e modificados juntos. As novas classes de inspetor devem testar se o código funciona nessa situação na cena.

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a>Adicionando novos ScriptableObjects

Ao adicionar novos scripts ScriptableObject, verifique se [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) o atributo é aplicado a todos os arquivos aplicáveis. Isso garante que o componente seja facilmente descoberto no editor por meio dos menus de criação de ativos. O sinalizador de atributo não será necessário se o componente não puder aparecer no editor, como uma classe abstrata.

No exemplo a seguir, a *Subpasta* deve ser preenchida com a subpasta do MRTK, se aplicável. Se colocar um item na pasta *MRTK/Provedores,* o pacote será *Provedores*. Se você colocar um item na pasta *MRTK/Core,* de definido como "Perfis".

No exemplo abaixo, o *arquivo MyNewService | MyNewProvider* deve ser preenchido com o nome da nova classe, se aplicável. Se colocar um item na pasta *MixedRealityToolkit,* deixe essa cadeia de caracteres de fora.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>Log

Ao adicionar novos recursos ou atualizar recursos existentes, considere adicionar logs DebugUtilities.LogVerbose a um código interessante que pode ser útil para futura depuração. Há uma diferença entre a adição de registro em log e o ruído adicionado e o registro em log não suficiente (o que dificulta o diagnóstico).

Um exemplo interessante em que o registro em log é útil (juntamente com o payload interessante):

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

Esse tipo de registro em log pode ajudar a capturar problemas como , que foram causados por eventos de origem [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) incompatibilidade detectados e perda de origem.

Evite adicionar logs para dados e eventos que estão ocorrendo em cada quadro – o ideal é registrar em log eventos "interessantes" orientados por entradas de usuário distintas (ou seja, um "clique" por um usuário e o conjunto de alterações e eventos que são interessantes para o log). O estado contínuo de "o usuário ainda está mantendo um gesto" registrado em cada quadro não é interessante e sobrecarrega os logs.

Observe que esse log detalhado não está ativado por padrão (ele deve ser habilitado nas configurações [do Sistema de Diagnóstico](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))

### <a name="spaces-vs-tabs"></a>Espaços versus guias

Certifique-se de usar 4 espaços em vez de guias ao contribuir com este projeto.

### <a name="spacing"></a>Espaçamento

Não adicione espaços adicionais entre colchetes e parênteses:

#### <a name="dont"></a>O que não fazer

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>O que fazer

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>Convenções de nomenclatura

Sempre use `PascalCase` para propriedades. Use `camelCase` para a maioria dos campos, exceto para os campos e `PascalCase` `static readonly` `const` . A única exceção a isso é para estruturas de dados que exigem que os campos sejam serializados pelo `JsonUtility` .

#### <a name="dont"></a>O que não fazer

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>O que fazer

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>Modificadores de acesso

Sempre declare um modificador de acesso para todos os campos, propriedades e métodos.

- Todos os Métodos de API do Unity devem ser por padrão, a menos que você precise `private` substituí-los em uma classe derivada. Nesse caso, `protected` deve ser usado.

- Os campos sempre devem ser `private` , com `public` ou `protected` acessadores de propriedade.

- Usar [membros aptos para expressão e](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) propriedades [automáticas](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) sempre que possível

#### <a name="dont"></a>O que não fazer

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>O que fazer

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>Usar chaves

Sempre use chaves após cada bloco de instrução e coloque-as na próxima linha.

#### <a name="dont"></a>O que não fazer

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>O que não fazer

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>O que fazer

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>Classes públicas, structs e enums devem entrar em seus próprios arquivos

Se a classe, struct ou enum puder ser privada, não há problema em ser incluído no mesmo arquivo.  Isso evita problemas de compilação com o Unity e garante que a abstração de código adequada ocorra, ele também reduz conflitos e alterações significativas quando o código precisa mudar.

#### <a name="dont"></a>O que não fazer

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>O que fazer

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>O que fazer

MyStruct.cs

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

MyEnumType.cs

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

Myclass.cs

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>Inicializar enums

Para garantir que todas as enums sejam inicializadas corretamente a partir de 0, o .NET fornece um atalho organizado para inicializar automaticamente a enum apenas adicionando o primeiro valor (starter). (por exemplo, Valor 1 = 0 Valores restantes não são necessários)

#### <a name="dont"></a>O que não fazer

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>O que fazer

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>Ordenar enums para a extensão apropriada

É essencial que, se uma Enum provavelmente for estendida no futuro, para ordenar padrões na parte superior da Enum, isso garantirá que os índices Enum não sejam afetados com novas adições.

#### <a name="dont"></a>O que não fazer

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a>O que fazer

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a>Revisar o uso de enum para bitfields

Se houver uma possibilidade de uma enum exigir vários estados como um valor, por exemplo, Handedness = Left & Right. Em seguida, a Enum precisa ser decorada corretamente com BitFlags para permitir que ele seja usado corretamente

O arquivo Handedness.cs tem uma implementação concreta para isso

### <a name="dont"></a>O que não fazer

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>O que fazer

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a>Caminhos de arquivo em código

Ao gerar caminhos de arquivo de cadeia de caracteres e, em particular, escrever caminhos de cadeia de caracteres codificados, faça o seguinte:

1. Use as APIs do [ `Path` C#sempre](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) que possível, como `Path.Combine` ou `Path.GetFullPath` .
1. Use / ou [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) em vez de \ ou \\ \\ .

Essas etapas garantem que o MRTK funcione em sistemas Windows e unix.

### <a name="dont"></a>O que não fazer

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>O que fazer

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>Práticas recomendadas, incluindo recomendações do Unity

Algumas das plataformas de destino deste projeto precisam levar em consideração o desempenho. Com isso em mente, sempre tenha cuidado ao alocar memória no código chamado com frequência em loops de atualização ou algoritmos rígidos.

### <a name="encapsulation"></a>Encapsulamento

Sempre use campos privados e propriedades públicas se o acesso ao campo for necessário de fora da classe ou struct.  Certifique-se de co-localizar o campo privado e a propriedade pública. Isso torna mais fácil ver, rapidamente, o que dá o retorno da propriedade e que o campo é modificável pelo script.

> [!NOTE]
> A única exceção a isso é para estruturas de dados que exigem que os campos sejam serializados pelo , em que uma classe de dados é necessária para ter todos os campos públicos para `JsonUtility` que a serialização funcione.

#### <a name="dont"></a>O que não fazer

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a>O que fazer

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>Armazenar valores em cache e serializá-los na cena/pré-fab sempre que possível

Com o HoloLens em mente, é melhor otimizar para referências de desempenho e cache na cena ou pré-fab para limitar as alocações de memória de runtime.

#### <a name="dont"></a>O que não fazer

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>O que fazer

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>Referências de cache a materiais, não chame o ".material" toda vez

O Unity criará um novo material sempre que você usar ".material", o que causará uma perda de memória se não for limpo corretamente.

#### <a name="dont"></a>O que não fazer

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a>O que fazer

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> Como alternativa, use a propriedade "SharedMaterial" do Unity que não cria um novo material sempre que ele é referenciado.

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>Use [a compilação dependente da](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) plataforma para garantir Toolkit não quebrará o build em outra plataforma

- Use para usar APIs não Unity específicas da `WINDOWS_UWP` UWP. Isso impedirá que eles tentarem ser executados no Editor ou em plataformas sem suporte. Isso é equivalente a `UNITY_WSA && !UNITY_EDITOR` e deve ser usado em favor de .
- Use `UNITY_WSA` para usar APIs do Unity específicas da UWP, como o `UnityEngine.XR.WSA` namespace . Isso será executado no Editor quando a plataforma for definida como UWP, bem como em aplicativos UWP integrados.

Esse gráfico pode ajudá-lo a decidir qual usar, dependendo dos casos de uso e `#if` das configurações de build esperadas.

|Plataforma | UWP IL2CPP | UWP .NET | Editor |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | Falso | Falso | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | Falso |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | Falso |
| `ENABLE_WINMD_SUPPORT` | True | True | Falso |
| `NETFX_CORE` | Falso | True | Falso |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>Preferir DateTime.UtcNow em vez de DateTime.Now

DateTime.UtcNow é mais rápido do que DateTime.Now. Em investigações de desempenho anteriores, descobrimos que o uso de DateTime.Now adiciona sobrecarga significativa, especialmente quando usado no loop Update(). [Outros atingiram o mesmo problema.](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)

Prefira usar DateTime.UtcNow, a menos que você realmente precise dos horários localizados (um motivo legítimo pode ser que você queira mostrar a hora atual no fuso horário do usuário). Se você estiver lidando com tempos relativos (ou seja, o delta entre alguma última atualização e agora), é melhor usar DateTime.UtcNow para evitar a sobrecarga de fazer conversões de timezone.

## <a name="powershell-coding-conventions"></a>Convenções de codificação do PowerShell

Um subconjunto da base de código do MRTK usa o PowerShell para infraestrutura de pipeline e vários scripts e utilitários. O novo código do PowerShell deve seguir o [estilo PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).

## <a name="see-also"></a>Confira também

 [Convenções de codificação em C# do MSDN](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
