---
title: Codificando diretrizes
description: princípios de codificação e convenções a seguir ao contribuir com o MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, C#,
ms.openlocfilehash: 8887e248bd550bdd7a59f19c16df1ec3647ceff7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145241"
---
# <a name="coding-guidelines"></a><span data-ttu-id="87719-104">Diretrizes de codificação</span><span class="sxs-lookup"><span data-stu-id="87719-104">Coding guidelines</span></span>

<span data-ttu-id="87719-105">Este documento descreve os princípios e as convenções de codificação a seguir ao contribuir com o MRTK.</span><span class="sxs-lookup"><span data-stu-id="87719-105">This document outlines coding principles and conventions to follow when contributing to MRTK.</span></span>

---

## <a name="philosophy"></a><span data-ttu-id="87719-106">Filosofia</span><span class="sxs-lookup"><span data-stu-id="87719-106">Philosophy</span></span>

### <a name="be-concise-and-strive-for-simplicity"></a><span data-ttu-id="87719-107">Seja conciso e busque a simplicidade</span><span class="sxs-lookup"><span data-stu-id="87719-107">Be concise and strive for simplicity</span></span>

<span data-ttu-id="87719-108">A solução mais simples geralmente é a melhor.</span><span class="sxs-lookup"><span data-stu-id="87719-108">The simplest solution is often the best.</span></span> <span data-ttu-id="87719-109">Esse é um objetivo que substitui essas diretrizes e deve ser a meta de todas as atividades de codificação.</span><span class="sxs-lookup"><span data-stu-id="87719-109">This is an overriding aim of these guidelines and should be the goal of all coding activity.</span></span> <span data-ttu-id="87719-110">Parte de ser simples é ser conciso e consistente com o código existente.</span><span class="sxs-lookup"><span data-stu-id="87719-110">Part of being simple is being concise, and consistent with existing code.</span></span> <span data-ttu-id="87719-111">Tente manter seu código simples.</span><span class="sxs-lookup"><span data-stu-id="87719-111">Try to keep your code simple.</span></span>

<span data-ttu-id="87719-112">Os leitores só devem encontrar artefatos que forneçam informações úteis.</span><span class="sxs-lookup"><span data-stu-id="87719-112">Readers should only encounter artifacts that provide useful information.</span></span> <span data-ttu-id="87719-113">Por exemplo, comentários que restate o que é óbvio não fornecem informações adicionais e aumentam a taxa de ruído para sinal.</span><span class="sxs-lookup"><span data-stu-id="87719-113">For example, comments that restate what is obvious provide no extra information and increase the noise to signal ratio.</span></span>

<span data-ttu-id="87719-114">Mantenha a lógica de código simples.</span><span class="sxs-lookup"><span data-stu-id="87719-114">Keep code logic simple.</span></span> <span data-ttu-id="87719-115">Observe que essa não é uma instrução sobre como usar o menor número de linhas, minimizando o tamanho dos nomes de identificador ou o estilo da chave, mas sobre como reduzir o número de conceitos e maximizar a visibilidade deles por meio de padrões familiares.</span><span class="sxs-lookup"><span data-stu-id="87719-115">Note that this is not a statement about using the fewest number of lines, minimizing the size of identifier names or brace style, but about reducing the number of concepts and maximizing the visibility of those through familiar patterns.</span></span>

### <a name="produce-consistent-readable-code"></a><span data-ttu-id="87719-116">Produzir código consistente e acessível</span><span class="sxs-lookup"><span data-stu-id="87719-116">Produce consistent, readable code</span></span>

<span data-ttu-id="87719-117">A leitura do código está correlacionada com baixas taxas de defeito.</span><span class="sxs-lookup"><span data-stu-id="87719-117">Code readability is correlated with low defect rates.</span></span> <span data-ttu-id="87719-118">Busque criar um código que seja fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="87719-118">Strive to create code that is easy to read.</span></span> <span data-ttu-id="87719-119">Busque criar código que tenha lógica simples e re use componentes existentes, pois ele também ajudará a garantir a correção.</span><span class="sxs-lookup"><span data-stu-id="87719-119">Strive to create code that has simple logic and re-uses existing components as it will also help ensure correctness.</span></span>

<span data-ttu-id="87719-120">Todos os detalhes do código produzido são importantes, desde os detalhes mais básicos de correção até o estilo e a formatação consistentes.</span><span class="sxs-lookup"><span data-stu-id="87719-120">All details of the code you produce matter, from the most basic detail of correctness to consistent style and formatting.</span></span> <span data-ttu-id="87719-121">Mantenha seu estilo de codificação consistente com o que já existe, mesmo que ele não seja correspondente à sua preferência.</span><span class="sxs-lookup"><span data-stu-id="87719-121">Keep your coding style consistent with what already exists, even if it is not matching your preference.</span></span> <span data-ttu-id="87719-122">Isso aumenta a capacidade de leitura da base de código geral.</span><span class="sxs-lookup"><span data-stu-id="87719-122">This increases the readability of the overall codebase.</span></span>

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a><span data-ttu-id="87719-123">Suporte à configuração de componentes no editor e no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="87719-123">Support configuring components both in editor and at run-time</span></span>

<span data-ttu-id="87719-124">O MRTK dá suporte a um conjunto diversificado de usuários – pessoas que preferem configurar componentes no editor do Unity e carregar pré-fabricados e pessoas que precisam instanciar e configurar objetos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="87719-124">MRTK supports a diverse set of users – people who prefer to configure components in the Unity editor and load prefabs, and people who need to instantiate and configure objects at run-time.</span></span>

<span data-ttu-id="87719-125">Todo o seu código deve funcionar adicionando um componente a um gameobject em uma cena salva e instanciando esse componente no código.</span><span class="sxs-lookup"><span data-stu-id="87719-125">All your code should work by BOTH adding a component to a GameObject in a saved scene, and by instantiating that component in code.</span></span> <span data-ttu-id="87719-126">Os testes devem incluir um caso de teste para instanciar pré-fabricados e instanciar, configurando o componente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="87719-126">Tests should include a test case both for instantiating prefabs and instantiating, configuring the component at runtime.</span></span>

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a><span data-ttu-id="87719-127">O Play-in-editor é sua primeira e principal plataforma de destino</span><span class="sxs-lookup"><span data-stu-id="87719-127">Play-in-editor is your first and primary target platform</span></span>

<span data-ttu-id="87719-128">O Play-in-editor é a maneira mais rápida de iterar no Unity.</span><span class="sxs-lookup"><span data-stu-id="87719-128">Play-In-Editor is the fastest way to iterate in Unity.</span></span> <span data-ttu-id="87719-129">Fornecer maneiras para que nossos clientes iterem rapidamente permite que eles desenvolvam soluções mais rapidamente e experimentem mais ideias.</span><span class="sxs-lookup"><span data-stu-id="87719-129">Providing ways for our customers to iterate quickly allows them to both develop solutions more quickly and try out more ideas.</span></span> <span data-ttu-id="87719-130">Em outras palavras, maximizar a velocidade da iteração permite que nossos clientes obtenham mais.</span><span class="sxs-lookup"><span data-stu-id="87719-130">In other words, maximizing the speed of iteration empowers our customers to achieve more.</span></span>

<span data-ttu-id="87719-131">Faça tudo funcionar no editor e, em seguida, faça com que ele funcione em qualquer outra plataforma.</span><span class="sxs-lookup"><span data-stu-id="87719-131">Make everything work in editor, then make it work on any other platform.</span></span> <span data-ttu-id="87719-132">Mantenha-o funcionando no editor.</span><span class="sxs-lookup"><span data-stu-id="87719-132">Keep it working in the editor.</span></span> <span data-ttu-id="87719-133">É fácil adicionar uma nova plataforma ao editor de reprodução.</span><span class="sxs-lookup"><span data-stu-id="87719-133">It is easy to add a new platform to Play-In-Editor.</span></span> <span data-ttu-id="87719-134">É muito difícil obter o editor de reprodução funcionando se seu aplicativo funciona apenas em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="87719-134">It is very difficult to get Play-In-Editor working if your app only works on a device.</span></span>

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a><span data-ttu-id="87719-135">Adicione novos campos públicos, propriedades, métodos e campos privados serializados com cuidado</span><span class="sxs-lookup"><span data-stu-id="87719-135">Add new public fields, properties, methods and serialized private fields with care</span></span>

<span data-ttu-id="87719-136">Sempre que você adiciona um método público, campo, propriedade, ele se torna parte da superfície da API pública do MRTK.</span><span class="sxs-lookup"><span data-stu-id="87719-136">Every time you add a public method, field, property, it becomes part of MRTK’s public API surface.</span></span> <span data-ttu-id="87719-137">Campos privados marcados com `[SerializeField]` também expõem campos ao editor e fazem parte da superfície da API pública.</span><span class="sxs-lookup"><span data-stu-id="87719-137">Private fields marked with `[SerializeField]` also expose fields to the editor and are part of the public API surface.</span></span> <span data-ttu-id="87719-138">Outras pessoas podem usar esse método público, configurar o pré-fabricados personalizado com seu campo público e assumir uma dependência dele.</span><span class="sxs-lookup"><span data-stu-id="87719-138">Other people might use that public method, configure custom prefabs with your public field, and take a dependency on it.</span></span>

<span data-ttu-id="87719-139">Novos membros públicos devem ser examinados cuidadosamente.</span><span class="sxs-lookup"><span data-stu-id="87719-139">New public members should be carefully examined.</span></span> <span data-ttu-id="87719-140">Qualquer campo público precisará ser mantido no futuro.</span><span class="sxs-lookup"><span data-stu-id="87719-140">Any public field will need to be maintained in the future.</span></span> <span data-ttu-id="87719-141">Lembre-se de que, se o tipo de um campo público (ou campo privado serializado) for alterado ou removido de um monocomportamento, isso poderá quebrar outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="87719-141">Remember that if the type of a public field (or serialized private field) changes or gets removed from a MonoBehaviour, that could break other people.</span></span> <span data-ttu-id="87719-142">O campo precisará primeiro ser preterido para uma versão e o código para migrar as alterações para as pessoas que tomaram dependências precisaria ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="87719-142">The field will need to first be deprecated for a release, and code to migrate changes for people that have taken dependencies would need to be provided.</span></span>

### <a name="prioritize-writing-tests"></a><span data-ttu-id="87719-143">Priorizar a escrita de testes</span><span class="sxs-lookup"><span data-stu-id="87719-143">Prioritize writing tests</span></span>

<span data-ttu-id="87719-144">O MRTK é um projeto da comunidade, modificado por uma variedade diversificada de colaboradores.</span><span class="sxs-lookup"><span data-stu-id="87719-144">MRTK is a community project, modified by a diverse range of contributors.</span></span> <span data-ttu-id="87719-145">Esses colaboradores podem não saber os detalhes de sua correção de bug/recurso e acidentalmente quebrar seu recurso.</span><span class="sxs-lookup"><span data-stu-id="87719-145">These contributors may not know the details of your bug fix / feature, and accidentally break your feature.</span></span> <span data-ttu-id="87719-146">[O MRTK executa testes de integração contínua](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) antes de concluir cada solicitação de pull.</span><span class="sxs-lookup"><span data-stu-id="87719-146">[MRTK runs continuous integration tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) before completing every pull request.</span></span> <span data-ttu-id="87719-147">As alterações que quebram os testes não podem ser verificadas.</span><span class="sxs-lookup"><span data-stu-id="87719-147">Changes that break tests cannot be checked in.</span></span> <span data-ttu-id="87719-148">Portanto, os testes são a melhor maneira de garantir que outras pessoas não violem seu recurso.</span><span class="sxs-lookup"><span data-stu-id="87719-148">Therefore, tests are the best way to ensure that other people do not break your feature.</span></span>

<span data-ttu-id="87719-149">Quando você corrigir um bug, escreva um teste para garantir que ele não regreda no futuro.</span><span class="sxs-lookup"><span data-stu-id="87719-149">When you fix a bug, write a test to ensure it does not regress in the future.</span></span> <span data-ttu-id="87719-150">Se adicionar um recurso, escreva testes que verifiquem se o recurso funciona.</span><span class="sxs-lookup"><span data-stu-id="87719-150">If adding a feature, write tests that verify your feature works.</span></span> <span data-ttu-id="87719-151">Isso é necessário para todos os recursos de UX, exceto recursos experimentais.</span><span class="sxs-lookup"><span data-stu-id="87719-151">This is required for all UX features except experimental features.</span></span>

## <a name="c-coding-conventions"></a><span data-ttu-id="87719-152">Convenções de codificação em C#</span><span class="sxs-lookup"><span data-stu-id="87719-152">C# Coding conventions</span></span>

### <a name="script-license-information-headers"></a><span data-ttu-id="87719-153">Headers de informações de licença de script</span><span class="sxs-lookup"><span data-stu-id="87719-153">Script license information headers</span></span>

<span data-ttu-id="87719-154">Todos os funcionários da Microsoft que contribuem com novos arquivos devem adicionar o seguinte header de Licença padrão na parte superior de todos os novos arquivos, exatamente como mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="87719-154">All Microsoft employees contributing new files should add the following standard License header at the top of any new files, exactly as shown below:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a><span data-ttu-id="87719-155">Headers de resumo de função/método</span><span class="sxs-lookup"><span data-stu-id="87719-155">Function / method summary headers</span></span>

<span data-ttu-id="87719-156">Todas as classes públicas, structs, enums, funções, propriedades, campos postados no MRTK devem ser descritos como para sua finalidade e uso, exatamente como mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="87719-156">All public classes, structs, enums, functions, properties, fields posted to the MRTK should be described as to its purpose and use, exactly as shown below:</span></span>

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

<span data-ttu-id="87719-157">Isso garante que a documentação seja gerada e difundida corretamente para todas as classes, métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="87719-157">This ensures documentation is properly generated and disseminated for all all classes, methods, and properties.</span></span>

<span data-ttu-id="87719-158">Todos os arquivos de script enviados sem marcas de resumo adequadas serão rejeitados.</span><span class="sxs-lookup"><span data-stu-id="87719-158">Any script files submitted without proper summary tags will be rejected.</span></span>

### <a name="mrtk-namespace-rules"></a><span data-ttu-id="87719-159">Regras de namespace do MRTK</span><span class="sxs-lookup"><span data-stu-id="87719-159">MRTK namespace rules</span></span>

<span data-ttu-id="87719-160">O Kit de Ferramentas de Realidade Misturada usa um modelo de namespace baseado em recurso, em que todos os namespaces fundamentais começam com "Microsoft.MixedReality.Toolkit".</span><span class="sxs-lookup"><span data-stu-id="87719-160">The Mixed Reality Toolkit uses a feature based namespace model, where all foundational namespaces begin with "Microsoft.MixedReality.Toolkit".</span></span> <span data-ttu-id="87719-161">Em geral, você não precisa especificar a camada do kit de ferramentas (por ex. Core, Provedores, Serviços) em seus namespaces.</span><span class="sxs-lookup"><span data-stu-id="87719-161">In general, you need not specify the toolkit layer (ex: Core, Providers, Services) in your namespaces.</span></span>

<span data-ttu-id="87719-162">Os namespaces definidos no momento são:</span><span class="sxs-lookup"><span data-stu-id="87719-162">The currently defined namespaces are:</span></span>

- <span data-ttu-id="87719-163">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="87719-163">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="87719-164">Microsoft.MixedReality.Toolkit.Boundary</span><span class="sxs-lookup"><span data-stu-id="87719-164">Microsoft.MixedReality.Toolkit.Boundary</span></span>
- <span data-ttu-id="87719-165">Microsoft.MixedReality.Toolkit.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="87719-165">Microsoft.MixedReality.Toolkit.Diagnostics</span></span>
- <span data-ttu-id="87719-166">Microsoft.MixedReality.Toolkit.Editor</span><span class="sxs-lookup"><span data-stu-id="87719-166">Microsoft.MixedReality.Toolkit.Editor</span></span>
- <span data-ttu-id="87719-167">Microsoft.MixedReality.Toolkit.Input</span><span class="sxs-lookup"><span data-stu-id="87719-167">Microsoft.MixedReality.Toolkit.Input</span></span>
- <span data-ttu-id="87719-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span><span class="sxs-lookup"><span data-stu-id="87719-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span></span>
- <span data-ttu-id="87719-169">Microsoft.MixedReality.Toolkit.Ltd</span><span class="sxs-lookup"><span data-stu-id="87719-169">Microsoft.MixedReality.Toolkit.Teleport</span></span>
- <span data-ttu-id="87719-170">Microsoft.MixedReality.Toolkit.Utilities</span><span class="sxs-lookup"><span data-stu-id="87719-170">Microsoft.MixedReality.Toolkit.Utilities</span></span>

<span data-ttu-id="87719-171">Para namespaces com uma grande quantidade de tipos, é aceitável criar um número limitado de sub-namespaces para auxiliar no uso do scoping.</span><span class="sxs-lookup"><span data-stu-id="87719-171">For namespaces with a large amount of types, it is acceptable to create a limited number of sub-namespaces to aid in scoping usage.</span></span>

<span data-ttu-id="87719-172">Omitir o namespace para uma interface, classe ou tipo de dados fará com que a alteração seja bloqueada.</span><span class="sxs-lookup"><span data-stu-id="87719-172">Omitting the namespace for an interface, class or data type will cause your change to be blocked.</span></span>

### <a name="adding-new-monobehaviour-scripts"></a><span data-ttu-id="87719-173">Adicionando novos scripts MonoBehaviour</span><span class="sxs-lookup"><span data-stu-id="87719-173">Adding new MonoBehaviour scripts</span></span>

<span data-ttu-id="87719-174">Ao adicionar novos scripts MonoBehaviour com uma solicitação de pull, verifique se o atributo é aplicado a [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) todos os arquivos aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="87719-174">When adding new MonoBehaviour scripts with a pull request, ensure the [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="87719-175">Isso garante que o componente seja facilmente descoberto no editor sob o *botão Adicionar* Componente.</span><span class="sxs-lookup"><span data-stu-id="87719-175">This ensures the component is easily discoverable in the editor under the *Add Component* button.</span></span> <span data-ttu-id="87719-176">O sinalizador de atributo não será necessário se o componente não puder aparecer no editor, como uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="87719-176">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="87719-177">No exemplo a seguir, o *pacote aqui* deve ser preenchido com o local do pacote do componente.</span><span class="sxs-lookup"><span data-stu-id="87719-177">In the example below, the *Package here* should be filled with the package location of the component.</span></span> <span data-ttu-id="87719-178">Se colocar um item na pasta *MRTK/SDK,* o pacote será *SDK*.</span><span class="sxs-lookup"><span data-stu-id="87719-178">If placing an item in *MRTK/SDK* folder, then the package will be *SDK*.</span></span>

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a><span data-ttu-id="87719-179">Adicionando novos scripts de inspetor do Unity</span><span class="sxs-lookup"><span data-stu-id="87719-179">Adding new Unity inspector scripts</span></span>

<span data-ttu-id="87719-180">Em geral, tente evitar a criação de scripts de inspetor personalizados para componentes do MRTK.</span><span class="sxs-lookup"><span data-stu-id="87719-180">In general, try to avoid creating custom inspector scripts for MRTK components.</span></span> <span data-ttu-id="87719-181">Ele adiciona sobrecarga adicional e gerenciamento da base de código que pode ser manipulada pelo mecanismo do Unity.</span><span class="sxs-lookup"><span data-stu-id="87719-181">It adds additional overhead and management of the codebase that could be handled by the Unity engine.</span></span>

<span data-ttu-id="87719-182">Se uma classe inspetor for necessária, tente usar o [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) do Unity.</span><span class="sxs-lookup"><span data-stu-id="87719-182">If an inspector class is necessary, try to use Unity's [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html).</span></span> <span data-ttu-id="87719-183">Isso simplifica novamente a classe inspetor e deixa grande parte do trabalho para o Unity.</span><span class="sxs-lookup"><span data-stu-id="87719-183">This again simplifies the inspector class and leaves much of the work to Unity.</span></span>

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

<span data-ttu-id="87719-184">Se a renderização personalizada for necessária na classe inspetor, tente utilizar [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) e [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) .</span><span class="sxs-lookup"><span data-stu-id="87719-184">If custom rendering is required in the inspector class, try to utilize [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) and [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html).</span></span> <span data-ttu-id="87719-185">Isso garantirá que o Unity lida corretamente com a renderização de pré-fabs aninhados e valores modificados.</span><span class="sxs-lookup"><span data-stu-id="87719-185">This will ensure Unity correctly handles rendering nested prefabs and modified values.</span></span>

<span data-ttu-id="87719-186">Se [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) não puder ser usado devido a um requisito na lógica personalizada, verifique se todo o uso está envolvido em torno de um [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) .</span><span class="sxs-lookup"><span data-stu-id="87719-186">If [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) cannot be used due to a requirement in custom logic, ensure all usage is wrapped around a [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html).</span></span> <span data-ttu-id="87719-187">Isso garantirá que o Unity renderiza o inspetor corretamente para pré-fabs aninhados e valores modificados com a propriedade determinada.</span><span class="sxs-lookup"><span data-stu-id="87719-187">This will ensure Unity renders the inspector correctly for nested prefabs and modified values with the given property.</span></span>

<span data-ttu-id="87719-188">Além disso, tente decorar a classe de inspetor personalizado com um [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) .</span><span class="sxs-lookup"><span data-stu-id="87719-188">Furthermore, try to decorate the custom inspector class with a [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html).</span></span> <span data-ttu-id="87719-189">Essa marca garante que vários objetos com esse componente na cena possam ser selecionados e modificados juntos.</span><span class="sxs-lookup"><span data-stu-id="87719-189">This tag ensure multiple objects with this component in the scene can be selected and modified together.</span></span> <span data-ttu-id="87719-190">As novas classes de inspetor devem testar se o código funciona nessa situação na cena.</span><span class="sxs-lookup"><span data-stu-id="87719-190">Any new inspector classes should test that their code works in this situation in the scene.</span></span>

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

### <a name="adding-new-scriptableobjects"></a><span data-ttu-id="87719-191">Adicionando novos ScriptableObjects</span><span class="sxs-lookup"><span data-stu-id="87719-191">Adding new ScriptableObjects</span></span>

<span data-ttu-id="87719-192">Ao adicionar novos scripts ScriptableObject, verifique se [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) o atributo é aplicado a todos os arquivos aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="87719-192">When adding new ScriptableObject scripts, ensure the [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="87719-193">Isso garante que o componente seja facilmente descoberto no editor por meio dos menus de criação de ativos.</span><span class="sxs-lookup"><span data-stu-id="87719-193">This ensures the component is easily discoverable in the editor via the asset creation menus.</span></span> <span data-ttu-id="87719-194">O sinalizador de atributo não será necessário se o componente não puder aparecer no editor, como uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="87719-194">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="87719-195">No exemplo a seguir, a *Subpasta* deve ser preenchida com a subpasta do MRTK, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="87719-195">In the example below, the *Subfolder* should be filled with the MRTK subfolder, if applicable.</span></span> <span data-ttu-id="87719-196">Se colocar um item na pasta *MRTK/Provedores,* o pacote será *Provedores*.</span><span class="sxs-lookup"><span data-stu-id="87719-196">If placing an item in *MRTK/Providers* folder, then the package will be *Providers*.</span></span> <span data-ttu-id="87719-197">Se você colocar um item na pasta *MRTK/Core,* de definido como "Perfis".</span><span class="sxs-lookup"><span data-stu-id="87719-197">If placing an item in the *MRTK/Core* folder, set this to "Profiles".</span></span>

<span data-ttu-id="87719-198">No exemplo abaixo, o *arquivo MyNewService | MyNewProvider* deve ser preenchido com o nome da nova classe, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="87719-198">In the example below, the *MyNewService | MyNewProvider* should be filled with the your new class' name, if applicable.</span></span> <span data-ttu-id="87719-199">Se colocar um item na pasta *MixedRealityToolkit,* deixe essa cadeia de caracteres de fora.</span><span class="sxs-lookup"><span data-stu-id="87719-199">If placing an item in the *MixedRealityToolkit* folder, leave this string out.</span></span>

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a><span data-ttu-id="87719-200">Log</span><span class="sxs-lookup"><span data-stu-id="87719-200">Logging</span></span>

<span data-ttu-id="87719-201">Ao adicionar novos recursos ou atualizar recursos existentes, considere adicionar logs DebugUtilities.LogVerbose a um código interessante que pode ser útil para futura depuração.</span><span class="sxs-lookup"><span data-stu-id="87719-201">When adding new features or updating existing features, consider adding DebugUtilities.LogVerbose logs to interesting code that may be useful for future debugging.</span></span> <span data-ttu-id="87719-202">Há uma diferença entre a adição de registro em log e o ruído adicionado e o registro em log não suficiente (o que dificulta o diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="87719-202">There's a tradeoff here between adding logging and the added noise and not enough logging (which makes diagnosis difficult).</span></span>

<span data-ttu-id="87719-203">Um exemplo interessante em que o registro em log é útil (juntamente com o payload interessante):</span><span class="sxs-lookup"><span data-stu-id="87719-203">An interesting example where having logging is useful (along with interesting payload):</span></span>

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

<span data-ttu-id="87719-204">Esse tipo de log pode ajudar a detectar problemas como [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) , que foram causados por eventos de origem incompatíveis detectados e perdidos de origem.</span><span class="sxs-lookup"><span data-stu-id="87719-204">This type of logging can help catch issues like [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016), which were caused by mismatched source detected and source lost events.</span></span>

<span data-ttu-id="87719-205">Evite adicionar logs para dados e eventos que estão ocorrendo em cada quadro-o registro em log ideal deve abranger eventos "interessantes" controlados por entradas de usuário distintas (ou seja, um "clique" por um usuário e o conjunto de alterações e eventos provenientes do que são interessantes para log).</span><span class="sxs-lookup"><span data-stu-id="87719-205">Avoid adding logs for data and events that are occurring on every frame - ideally logging should cover "interesting" events driven by distinct user inputs (i.e. a "click" by a user and the set of changes and events that come from that are interesting to log).</span></span> <span data-ttu-id="87719-206">O estado em andamento do "o usuário ainda está mantendo um gesto" registrado em todos os quadros não é interessante e sobrecarregará os logs.</span><span class="sxs-lookup"><span data-stu-id="87719-206">The ongoing state of "user is still holding a gesture" logged every frame is not interesting and will overwhelm the logs.</span></span>

<span data-ttu-id="87719-207">Observe que esse log detalhado não é ativado por padrão (ele deve ser habilitado nas configurações do [sistema de diagnóstico](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span><span class="sxs-lookup"><span data-stu-id="87719-207">Note that this verbose logging is not turned on by default (it must be enabled in the [Diagnostic System settings](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span></span>

### <a name="spaces-vs-tabs"></a><span data-ttu-id="87719-208">Espaços versus guias</span><span class="sxs-lookup"><span data-stu-id="87719-208">Spaces vs tabs</span></span>

<span data-ttu-id="87719-209">Certifique-se de usar quatro espaços em vez de guias ao contribuir para este projeto.</span><span class="sxs-lookup"><span data-stu-id="87719-209">Please be sure to use 4 spaces instead of tabs when contributing to this project.</span></span>

### <a name="spacing"></a><span data-ttu-id="87719-210">Espaçamento</span><span class="sxs-lookup"><span data-stu-id="87719-210">Spacing</span></span>

<span data-ttu-id="87719-211">Não adicione espaços adicionais entre colchetes e parênteses:</span><span class="sxs-lookup"><span data-stu-id="87719-211">Do not to add additional spaces between square brackets and parenthesis:</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-212">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-212">Don't</span></span>

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a><span data-ttu-id="87719-213">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-213">Do</span></span>

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a><span data-ttu-id="87719-214">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="87719-214">Naming conventions</span></span>

<span data-ttu-id="87719-215">Sempre use `PascalCase` para propriedades.</span><span class="sxs-lookup"><span data-stu-id="87719-215">Always use `PascalCase` for properties.</span></span> <span data-ttu-id="87719-216">Use `camelCase` para a maioria dos campos, exceto o uso `PascalCase` de `static readonly` `const` campos e.</span><span class="sxs-lookup"><span data-stu-id="87719-216">Use `camelCase` for most fields, except use `PascalCase` for `static readonly` and `const` fields.</span></span> <span data-ttu-id="87719-217">A única exceção a isso é para estruturas de dados que exigem que os campos sejam serializados pelo `JsonUtility` .</span><span class="sxs-lookup"><span data-stu-id="87719-217">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`.</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-218">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-218">Don't</span></span>

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a><span data-ttu-id="87719-219">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-219">Do</span></span>

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a><span data-ttu-id="87719-220">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="87719-220">Access modifiers</span></span>

<span data-ttu-id="87719-221">Sempre declare um modificador de acesso para todos os campos, propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="87719-221">Always declare an access modifier for all fields, properties and methods.</span></span>

- <span data-ttu-id="87719-222">Todos os métodos de API do Unity devem ser `private` por padrão, a menos que você precise substituí-los em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="87719-222">All Unity API Methods should be `private` by default, unless you need to override them in a derived class.</span></span> <span data-ttu-id="87719-223">Nesse caso, `protected` deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="87719-223">In this case `protected` should be used.</span></span>

- <span data-ttu-id="87719-224">Os campos devem ser sempre `private` , com `public` ou `protected` acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="87719-224">Fields should always be `private`, with `public` or `protected` property accessors.</span></span>

- <span data-ttu-id="87719-225">Usar [membros do Expression-apto para](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) e [Propriedades automáticas](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) sempre que possível</span><span class="sxs-lookup"><span data-stu-id="87719-225">Use [expression-bodied members](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) and [auto properties](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) where possible</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-226">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-226">Don't</span></span>

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a><span data-ttu-id="87719-227">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-227">Do</span></span>

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a><span data-ttu-id="87719-228">Usar chaves</span><span class="sxs-lookup"><span data-stu-id="87719-228">Use braces</span></span>

<span data-ttu-id="87719-229">Sempre use chaves após cada bloco de instrução e coloque-as na próxima linha.</span><span class="sxs-lookup"><span data-stu-id="87719-229">Always use braces after each statement block, and place them on the next line.</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-230">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-230">Don't</span></span>

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a><span data-ttu-id="87719-231">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-231">Don't</span></span>

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a><span data-ttu-id="87719-232">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-232">Do</span></span>

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

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a><span data-ttu-id="87719-233">As classes públicas, as estruturas e as enumerações devem estar em seus próprios arquivos</span><span class="sxs-lookup"><span data-stu-id="87719-233">Public classes, structs, and enums should all go in their own files</span></span>

<span data-ttu-id="87719-234">Se a classe, a struct ou a enumeração puderem ser tornadas privadas, não haverá problema em ser incluído no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="87719-234">If the class, struct, or enum can be made private then it's okay to be included in the same file.</span></span>  <span data-ttu-id="87719-235">Isso evita problemas de compilação com o Unity e garante que a abstração de código adequada ocorra, além de reduzir conflitos e alterações significativas quando o código precisar ser alterado.</span><span class="sxs-lookup"><span data-stu-id="87719-235">This avoids compilations issues with Unity and ensure that proper code abstraction occurs, it also reduces conflicts and breaking changes when code needs to change.</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-236">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-236">Don't</span></span>

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="87719-237">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-237">Do</span></span>

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="87719-238">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-238">Do</span></span>

<span data-ttu-id="87719-239">MyStruct.cs</span><span class="sxs-lookup"><span data-stu-id="87719-239">MyStruct.cs</span></span>

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

<span data-ttu-id="87719-240">MyEnumType.cs</span><span class="sxs-lookup"><span data-stu-id="87719-240">MyEnumType.cs</span></span>

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

<span data-ttu-id="87719-241">Myclass.cs</span><span class="sxs-lookup"><span data-stu-id="87719-241">MyClass.cs</span></span>

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a><span data-ttu-id="87719-242">Inicializar enums</span><span class="sxs-lookup"><span data-stu-id="87719-242">Initialize enums</span></span>

<span data-ttu-id="87719-243">Para garantir que todas as enums sejam inicializadas corretamente a partir de 0, o .NET fornece um atalho organizado para inicializar automaticamente a enum apenas adicionando o primeiro valor (starter).</span><span class="sxs-lookup"><span data-stu-id="87719-243">To ensure all enums are initialized correctly starting at 0, .NET gives you a tidy shortcut to automatically initialize the enum by just adding the first (starter) value.</span></span> <span data-ttu-id="87719-244">(por exemplo, Valor 1 = 0 Valores restantes não são necessários)</span><span class="sxs-lookup"><span data-stu-id="87719-244">(e.g Value 1 = 0 Remaining values are not required)</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-245">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-245">Don't</span></span>

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a><span data-ttu-id="87719-246">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-246">Do</span></span>

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a><span data-ttu-id="87719-247">Ordenar enums para a extensão apropriada</span><span class="sxs-lookup"><span data-stu-id="87719-247">Order enums for appropriate extension</span></span>

<span data-ttu-id="87719-248">É essencial que, se uma Enum provavelmente for estendida no futuro, para ordenar padrões na parte superior da Enum, isso garantirá que os índices Enum não sejam afetados com novas adições.</span><span class="sxs-lookup"><span data-stu-id="87719-248">It is critical that if an Enum is likely to be extended in the future, to order defaults at the top of the Enum, this ensures Enum indexes are not affected with new additions.</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-249">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-249">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="87719-250">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-250">Do</span></span>

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

### <a name="review-enum-use-for-bitfields"></a><span data-ttu-id="87719-251">Revisar o uso de enum para bitfields</span><span class="sxs-lookup"><span data-stu-id="87719-251">Review enum use for bitfields</span></span>

<span data-ttu-id="87719-252">Se houver uma possibilidade de uma enum exigir vários estados como um valor, por exemplo, Handedness = Left & Right.</span><span class="sxs-lookup"><span data-stu-id="87719-252">If there is a possibility for an enum to require multiple states as a value, e.g. Handedness = Left & Right.</span></span> <span data-ttu-id="87719-253">Em seguida, a Enum precisa ser decorada corretamente com BitFlags para permitir que ele seja usado corretamente</span><span class="sxs-lookup"><span data-stu-id="87719-253">Then the Enum needs to be decorated correctly with BitFlags to enable it to be used correctly</span></span>

<span data-ttu-id="87719-254">O arquivo Handedness.cs tem uma implementação concreta para isso</span><span class="sxs-lookup"><span data-stu-id="87719-254">The Handedness.cs file has a concrete implementation for this</span></span>

### <a name="dont"></a><span data-ttu-id="87719-255">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-255">Don't</span></span>

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a><span data-ttu-id="87719-256">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-256">Do</span></span>

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

### <a name="hard-coded-file-paths"></a><span data-ttu-id="87719-257">Caminhos de arquivo em código</span><span class="sxs-lookup"><span data-stu-id="87719-257">Hard-coded file paths</span></span>

<span data-ttu-id="87719-258">Ao gerar caminhos de arquivo de cadeia de caracteres e, em particular, escrever caminhos de cadeia de caracteres codificados, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="87719-258">When generating string file paths, and in particular writing hard-coded string paths, do the following:</span></span>

1. <span data-ttu-id="87719-259">Use as APIs do [ `Path` C#sempre](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) que possível, como `Path.Combine` ou `Path.GetFullPath` .</span><span class="sxs-lookup"><span data-stu-id="87719-259">Use C#'s [`Path` APIs](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) whenever possible such as `Path.Combine` or `Path.GetFullPath`.</span></span>
1. <span data-ttu-id="87719-260">Use / ou [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) em vez de \ ou \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="87719-260">Use / or [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) instead of \ or \\\\.</span></span>

<span data-ttu-id="87719-261">Essas etapas garantem que o MRTK funcione em sistemas baseados em Windows e Unix.</span><span class="sxs-lookup"><span data-stu-id="87719-261">These steps ensure that MRTK works on both Windows and Unix-based systems.</span></span>

### <a name="dont"></a><span data-ttu-id="87719-262">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-262">Don't</span></span>

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a><span data-ttu-id="87719-263">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-263">Do</span></span>

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a><span data-ttu-id="87719-264">Práticas recomendadas, incluindo recomendações do Unity</span><span class="sxs-lookup"><span data-stu-id="87719-264">Best practices, including Unity recommendations</span></span>

<span data-ttu-id="87719-265">Algumas das plataformas de destino deste projeto precisam levar em consideração o desempenho.</span><span class="sxs-lookup"><span data-stu-id="87719-265">Some of the target platforms of this project require to take performance into consideration.</span></span> <span data-ttu-id="87719-266">Com isso em mente, sempre tenha cuidado ao alocar memória no código chamado com frequência em loops de atualização ou algoritmos rígidos.</span><span class="sxs-lookup"><span data-stu-id="87719-266">With this in mind always be careful when allocating memory in frequently called code in tight update loops or algorithms.</span></span>

### <a name="encapsulation"></a><span data-ttu-id="87719-267">Encapsulamento</span><span class="sxs-lookup"><span data-stu-id="87719-267">Encapsulation</span></span>

<span data-ttu-id="87719-268">Sempre use campos privados e propriedades públicas se o acesso ao campo for necessário de fora da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="87719-268">Always use private fields and public properties if access to the field is needed from outside the class or struct.</span></span>  <span data-ttu-id="87719-269">Certifique-se de colocalizar o campo privado e a propriedade pública.</span><span class="sxs-lookup"><span data-stu-id="87719-269">Be sure to co-locate the private field and the public property.</span></span> <span data-ttu-id="87719-270">Isso facilita a visualização, em um relance, o que faz o backup da propriedade e que o campo é modificável por script.</span><span class="sxs-lookup"><span data-stu-id="87719-270">This makes it easier to see, at a glance, what backs the property and that the field is modifiable by script.</span></span>

> [!NOTE]
> <span data-ttu-id="87719-271">A única exceção a isso é para as estruturas de dados que exigem que os campos sejam serializados pelo `JsonUtility` , onde uma classe de dados precisa ter todos os campos públicos para que a serialização funcione.</span><span class="sxs-lookup"><span data-stu-id="87719-271">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`, where a data class is required to have all public fields for the serialization to work.</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-272">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-272">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="87719-273">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-273">Do</span></span>

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

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a><span data-ttu-id="87719-274">Armazenar valores em cache e serializá-los na cena/pré-fabricado sempre que possível</span><span class="sxs-lookup"><span data-stu-id="87719-274">Cache values and serialize them in the scene/prefab whenever possible</span></span>

<span data-ttu-id="87719-275">Com o HoloLens em mente, é melhor otimizar o desempenho e as referências de cache na cena ou pré-fabricado para limitar as alocações de memória de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="87719-275">With the HoloLens in mind, it's best to optimize for performance and cache references in the scene or prefab to limit runtime memory allocations.</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-276">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-276">Don't</span></span>

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a><span data-ttu-id="87719-277">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-277">Do</span></span>

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

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a><span data-ttu-id="87719-278">Referências de cache aos materiais, não chame o ". material" a cada vez</span><span class="sxs-lookup"><span data-stu-id="87719-278">Cache references to materials, do not call the ".material" each time</span></span>

<span data-ttu-id="87719-279">O Unity criará um novo material sempre que você usar ". material", o que provocará um vazamento de memória se ele não for limpo corretamente.</span><span class="sxs-lookup"><span data-stu-id="87719-279">Unity will create a new material each time you use ".material", which will cause a memory leak if not cleaned up properly.</span></span>

#### <a name="dont"></a><span data-ttu-id="87719-280">O que não fazer</span><span class="sxs-lookup"><span data-stu-id="87719-280">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="87719-281">O que fazer</span><span class="sxs-lookup"><span data-stu-id="87719-281">Do</span></span>

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
> <span data-ttu-id="87719-282">Como alternativa, use a propriedade "SharedMaterial" do Unity que não cria um novo material sempre que ele é referenciado.</span><span class="sxs-lookup"><span data-stu-id="87719-282">Alternatively, use Unity's "SharedMaterial" property which does not create a new material each time it is referenced.</span></span>

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a><span data-ttu-id="87719-283">Use a [compilação dependente de plataforma](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) para garantir que o kit de ferramentas não interrompa a compilação em outra plataforma</span><span class="sxs-lookup"><span data-stu-id="87719-283">Use [platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) to ensure the Toolkit won't break the build on another platform</span></span>

- <span data-ttu-id="87719-284">Use `WINDOWS_UWP` para usar APIs não Unity específicas de UWP.</span><span class="sxs-lookup"><span data-stu-id="87719-284">Use `WINDOWS_UWP` in order to use UWP-specific, non-Unity APIs.</span></span> <span data-ttu-id="87719-285">Isso irá impedi-lo de tentar executar no editor ou em plataformas sem suporte.</span><span class="sxs-lookup"><span data-stu-id="87719-285">This will prevent them from trying to run in the Editor or on unsupported platforms.</span></span> <span data-ttu-id="87719-286">Isso é equivalente a `UNITY_WSA && !UNITY_EDITOR` e deve ser usado em favor do.</span><span class="sxs-lookup"><span data-stu-id="87719-286">This is equivalent to `UNITY_WSA && !UNITY_EDITOR` and should be used in favor of.</span></span>
- <span data-ttu-id="87719-287">Use `UNITY_WSA` para usar APIs do Unity específicas de UWP, como o `UnityEngine.XR.WSA` namespace.</span><span class="sxs-lookup"><span data-stu-id="87719-287">Use `UNITY_WSA` to use UWP-specific Unity APIs, such as the `UnityEngine.XR.WSA` namespace.</span></span> <span data-ttu-id="87719-288">Isso será executado no editor quando a plataforma for definida como UWP, bem como em aplicativos UWP criados.</span><span class="sxs-lookup"><span data-stu-id="87719-288">This will run in the Editor when the platform is set to UWP, as well as in built UWP apps.</span></span>

<span data-ttu-id="87719-289">Este gráfico pode ajudá-lo a decidir qual `#if` usar, dependendo de seus casos de uso e das configurações de compilação que você espera.</span><span class="sxs-lookup"><span data-stu-id="87719-289">This chart can help you decide which `#if` to use, depending on your use cases and the build settings you expect.</span></span>

|<span data-ttu-id="87719-290">Plataforma</span><span class="sxs-lookup"><span data-stu-id="87719-290">Platform</span></span> | <span data-ttu-id="87719-291">IL2CPP UWP</span><span class="sxs-lookup"><span data-stu-id="87719-291">UWP IL2CPP</span></span> | <span data-ttu-id="87719-292">UWP .NET</span><span class="sxs-lookup"><span data-stu-id="87719-292">UWP .NET</span></span> | <span data-ttu-id="87719-293">Editor</span><span class="sxs-lookup"><span data-stu-id="87719-293">Editor</span></span> |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | <span data-ttu-id="87719-294">Falso</span><span class="sxs-lookup"><span data-stu-id="87719-294">False</span></span> | <span data-ttu-id="87719-295">Falso</span><span class="sxs-lookup"><span data-stu-id="87719-295">False</span></span> | <span data-ttu-id="87719-296">True</span><span class="sxs-lookup"><span data-stu-id="87719-296">True</span></span> |
| `UNITY_WSA` | <span data-ttu-id="87719-297">True</span><span class="sxs-lookup"><span data-stu-id="87719-297">True</span></span> | <span data-ttu-id="87719-298">True</span><span class="sxs-lookup"><span data-stu-id="87719-298">True</span></span> | <span data-ttu-id="87719-299">True</span><span class="sxs-lookup"><span data-stu-id="87719-299">True</span></span> |
| `WINDOWS_UWP` | <span data-ttu-id="87719-300">True</span><span class="sxs-lookup"><span data-stu-id="87719-300">True</span></span> | <span data-ttu-id="87719-301">True</span><span class="sxs-lookup"><span data-stu-id="87719-301">True</span></span> | <span data-ttu-id="87719-302">Falso</span><span class="sxs-lookup"><span data-stu-id="87719-302">False</span></span> |
| `UNITY_WSA && !UNITY_EDITOR` | <span data-ttu-id="87719-303">True</span><span class="sxs-lookup"><span data-stu-id="87719-303">True</span></span> | <span data-ttu-id="87719-304">True</span><span class="sxs-lookup"><span data-stu-id="87719-304">True</span></span> | <span data-ttu-id="87719-305">Falso</span><span class="sxs-lookup"><span data-stu-id="87719-305">False</span></span> |
| `ENABLE_WINMD_SUPPORT` | <span data-ttu-id="87719-306">True</span><span class="sxs-lookup"><span data-stu-id="87719-306">True</span></span> | <span data-ttu-id="87719-307">True</span><span class="sxs-lookup"><span data-stu-id="87719-307">True</span></span> | <span data-ttu-id="87719-308">Falso</span><span class="sxs-lookup"><span data-stu-id="87719-308">False</span></span> |
| `NETFX_CORE` | <span data-ttu-id="87719-309">Falso</span><span class="sxs-lookup"><span data-stu-id="87719-309">False</span></span> | <span data-ttu-id="87719-310">True</span><span class="sxs-lookup"><span data-stu-id="87719-310">True</span></span> | <span data-ttu-id="87719-311">Falso</span><span class="sxs-lookup"><span data-stu-id="87719-311">False</span></span> |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a><span data-ttu-id="87719-312">Prefira DateTime. UtcNow sobre DateTime. Now</span><span class="sxs-lookup"><span data-stu-id="87719-312">Prefer DateTime.UtcNow over DateTime.Now</span></span>

<span data-ttu-id="87719-313">DateTime. UtcNow é mais rápido que DateTime. Now.</span><span class="sxs-lookup"><span data-stu-id="87719-313">DateTime.UtcNow is faster than DateTime.Now.</span></span> <span data-ttu-id="87719-314">Em investigações de desempenho anteriores, descobrimos que o uso de DateTime.Now adiciona sobrecarga significativa, especialmente quando usado no loop Update().</span><span class="sxs-lookup"><span data-stu-id="87719-314">In previous performance investigations we've found that using DateTime.Now adds significant overhead especially when used in the Update() loop.</span></span> <span data-ttu-id="87719-315">[Outros atingiram o mesmo problema.](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)</span><span class="sxs-lookup"><span data-stu-id="87719-315">[Others have hit the same issue](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span></span>

<span data-ttu-id="87719-316">Prefira usar DateTime.UtcNow, a menos que você realmente precise dos horários localizados (um motivo legítimo pode ser que você queira mostrar a hora atual no fuso horário do usuário).</span><span class="sxs-lookup"><span data-stu-id="87719-316">Prefer using DateTime.UtcNow unless you actually need the localized times (a legitimate reason may be you wanting to show the current time in the user's time zone).</span></span> <span data-ttu-id="87719-317">Se você estiver lidando com tempos relativos (ou seja, o delta entre alguma última atualização e agora), é melhor usar DateTime.UtcNow para evitar a sobrecarga de fazer conversões de timezone.</span><span class="sxs-lookup"><span data-stu-id="87719-317">If you are dealing with relative times (i.e. the delta between some last update and now), it's best to use DateTime.UtcNow to avoid the overhead of doing timezone conversions.</span></span>

## <a name="powershell-coding-conventions"></a><span data-ttu-id="87719-318">Convenções de codificação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="87719-318">PowerShell coding conventions</span></span>

<span data-ttu-id="87719-319">Um subconjunto da base de código do MRTK usa o PowerShell para infraestrutura de pipeline e vários scripts e utilitários.</span><span class="sxs-lookup"><span data-stu-id="87719-319">A subset of the MRTK codebase uses PowerShell for pipeline infrastructure and various scripts and utilities.</span></span> <span data-ttu-id="87719-320">O novo código do PowerShell deve seguir o [estilo PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span><span class="sxs-lookup"><span data-stu-id="87719-320">New PowerShell code should follow the [PoshCode style](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span></span>

## <a name="see-also"></a><span data-ttu-id="87719-321">Confira também</span><span class="sxs-lookup"><span data-stu-id="87719-321">See also</span></span>

 [<span data-ttu-id="87719-322">Convenções de codificação em C# do MSDN</span><span class="sxs-lookup"><span data-stu-id="87719-322">C# coding conventions from MSDN</span></span>](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)