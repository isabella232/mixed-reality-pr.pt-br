---
title: Testes de Unidade
description: UnitTests para verificar do de MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, UnitTest,
ms.openlocfilehash: 76d246634cf190787fcfd78c849a0bd6da3a2135
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144717"
---
# <a name="writing-and-running-tests-in-mrtk"></a><span data-ttu-id="9d3e9-104">Escrevendo e executando testes em MRTK</span><span class="sxs-lookup"><span data-stu-id="9d3e9-104">Writing and running tests in MRTK</span></span>

<span data-ttu-id="9d3e9-105">Para garantir que o MRTK seja confiável, o MRTK tem um conjunto de testes para garantir que as alterações no código não retenha o comportamento existente.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="9d3e9-106">Ter boa cobertura de teste em uma grande base de código como MRTK é crucial para a estabilidade e ter confiança ao fazer alterações.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="9d3e9-107">O MRTK usa o [executor de teste do Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) , que usa uma integração do Unity do [NUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="9d3e9-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="9d3e9-108">Este guia fornecerá um ponto de partida sobre como adicionar testes ao MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="9d3e9-109">Ele não explicará o [executor de teste do Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) e o [NUnit](https://nunit.org/) , que pode ser pesquisado nos links fornecidos.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="9d3e9-110">Antes de enviar uma solicitação de pull, certifique-se de:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="9d3e9-111">Execute os testes localmente para que suas alterações não retenham o comportamento existente (concluir PRs não será permitido se algum teste falhar).</span><span class="sxs-lookup"><span data-stu-id="9d3e9-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="9d3e9-112">Se estiver corrigindo um bug, escreva um teste para testar a correção e certifique-se de que as modificações futuras no código não o quebrem novamente.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="9d3e9-113">Se estiver escrevendo um recurso, grave novos testes para evitar que alterações de código futuras quebrem esse recurso.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="9d3e9-114">Os testes do PlayMode no momento devem ser executados no Unity 2018,4 e podem falhar em outras versões do Unity</span><span class="sxs-lookup"><span data-stu-id="9d3e9-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="9d3e9-115">Executando testes</span><span class="sxs-lookup"><span data-stu-id="9d3e9-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="9d3e9-116">Editor do Unity</span><span class="sxs-lookup"><span data-stu-id="9d3e9-116">Unity editor</span></span>

<span data-ttu-id="9d3e9-117">O [corredor de teste do Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) pode ser encontrado em **janela**  >    >  de teste geral de **testes** e mostrará todos os testes de modo de reprodução e de MRTK disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="9d3e9-118">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="9d3e9-118">Command line</span></span>

<span data-ttu-id="9d3e9-119">Os testes também podem ser executados por um script do [PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) localizado em `Scripts\test\run_playmode_tests.ps1` .</span><span class="sxs-lookup"><span data-stu-id="9d3e9-119">Tests can also be run by a [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="9d3e9-120">Isso executará os testes PlayMode exatamente como são executados no GitHub/CI (veja abaixo) e imprimirá os resultados.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="9d3e9-121">Aqui estão alguns exemplos de como executar o script</span><span class="sxs-lookup"><span data-stu-id="9d3e9-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="9d3e9-122">Execute os testes no projeto localizado em H:\mrtk.dev, com o Unity 2018,4 (por exemplo, Unity 2018.4.26 F1)</span><span class="sxs-lookup"><span data-stu-id="9d3e9-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="9d3e9-123">Execute os testes no projeto localizado em H:\mrtk.dev, com o Unity 2018,4, resultados de saída para C:\ playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="9d3e9-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="9d3e9-124">Também é possível executar os testes PlayMode várias vezes por meio do `run_repeat_tests.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="9d3e9-125">Todos os parâmetros usados no `run_playmode_tests.ps1` podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="9d3e9-126">Validação de solicitação de pull</span><span class="sxs-lookup"><span data-stu-id="9d3e9-126">Pull request validation</span></span>

<span data-ttu-id="9d3e9-127">A CI do MRTK criará o MRTK em todas as configurações e executará todos os testes de modo de edição e reprodução.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="9d3e9-128">A CI pode ser disparada postando um comentário no github PR `/azp run mrtk_pr` se o usuário tiver direitos suficientes.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="9d3e9-129">As executações de CI podem ser vistas na guia "verificações" da PR.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="9d3e9-130">Somente depois que todos os testes foram aprovados com êxito, a PR pode ser mesclada em main.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-130">Only after all of the tests have passed successfully can the PR be merged into main.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="9d3e9-131">Testes de estresse/testes em massa</span><span class="sxs-lookup"><span data-stu-id="9d3e9-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="9d3e9-132">Às vezes, os testes só falharão ocasionalmente, o que pode ser frustrante para depurar.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="9d3e9-133">Para que vários testes são executados localmente, modifique os scripts de teste de acordo.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="9d3e9-134">O script Python a seguir deve tornar esse cenário mais conveniente.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="9d3e9-135">O pré-requisito para executar o script Python é ter [o Python 3.X instalado.](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="9d3e9-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="9d3e9-136">Para um único teste que precisa ser executado várias vezes:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="9d3e9-137">Execute o seguinte em uma linha de comando ([o PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) é recomendado)</span><span class="sxs-lookup"><span data-stu-id="9d3e9-137">Run the following from a command line ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="9d3e9-138">Copie e copie a saída no arquivo de teste.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="9d3e9-139">O script a seguir é para executar vários testes em sequência:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="9d3e9-140">O novo arquivo de teste agora deve conter</span><span class="sxs-lookup"><span data-stu-id="9d3e9-140">The new test file should now contain</span></span>

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="9d3e9-141">Abra o test runner e observe os novos testes que agora podem ser chamados repetidamente.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="9d3e9-142">Escrevendo testes</span><span class="sxs-lookup"><span data-stu-id="9d3e9-142">Writing tests</span></span>

<span data-ttu-id="9d3e9-143">Há dois tipos de testes que podem ser adicionados para o novo código</span><span class="sxs-lookup"><span data-stu-id="9d3e9-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="9d3e9-144">Testes de modo de reprodução</span><span class="sxs-lookup"><span data-stu-id="9d3e9-144">Play mode tests</span></span>
* <span data-ttu-id="9d3e9-145">Testes do modo de edição</span><span class="sxs-lookup"><span data-stu-id="9d3e9-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="9d3e9-146">Testes do modo de reprodução</span><span class="sxs-lookup"><span data-stu-id="9d3e9-146">Play mode tests</span></span>

<span data-ttu-id="9d3e9-147">Os testes do modo Play MRTK têm a capacidade de testar como o novo recurso responde a diferentes fontes de entrada, como mãos ou olhos.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="9d3e9-148">Novos testes do modo de reprodução podem herdar [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) ou o esqueleto abaixo pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) or the skeleton below can be used.</span></span>

<span data-ttu-id="9d3e9-149">Para criar um novo teste de modo de reprodução:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-149">To create a new play mode test:</span></span>

* <span data-ttu-id="9d3e9-150">Navegue até ativos > MRTK > testes > PlayModeTests</span><span class="sxs-lookup"><span data-stu-id="9d3e9-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="9d3e9-151">Clique com o botão direito do mouse em criar > teste > script de teste C#</span><span class="sxs-lookup"><span data-stu-id="9d3e9-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="9d3e9-152">Substitua o modelo padrão pelo esqueleto abaixo</span><span class="sxs-lookup"><span data-stu-id="9d3e9-152">Replace the default template with the skeleton below</span></span>

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a><span data-ttu-id="9d3e9-153">Testes do modo de edição</span><span class="sxs-lookup"><span data-stu-id="9d3e9-153">Edit mode tests</span></span>

<span data-ttu-id="9d3e9-154">Os testes do modo de edição são executados no modo de edição do Unity e podem ser adicionados na pasta **MRTK**  >  **tests**  >  **EditModeTests** no repositório do kit de ferramentas do reality Mixed.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="9d3e9-155">Para criar um novo teste, o seguinte modelo pode ser usado:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-155">To create a new test the following template can be used:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a><span data-ttu-id="9d3e9-156">Convenções de nomenclatura de teste</span><span class="sxs-lookup"><span data-stu-id="9d3e9-156">Test naming conventions</span></span>

<span data-ttu-id="9d3e9-157">Os testes devem geralmente ser nomeados com base na classe que estão sendo testada ou no cenário em que estão sendo testados.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="9d3e9-158">Por exemplo, dada uma classe a ser testada:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="9d3e9-159">Considere nomear o teste</span><span class="sxs-lookup"><span data-stu-id="9d3e9-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="9d3e9-160">Considere colocar o teste em uma hierarquia de pastas semelhante ao arquivo que não é de teste correspondente.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="9d3e9-161">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="9d3e9-162">Isso é para garantir que há uma maneira óbvia de localizar a classe de teste correspondente de cada classe, se existir uma classe de teste.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="9d3e9-163">O posicionamento de testes baseados em cenários é menos definido-se o teste exercitar o sistema de entrada geral, por exemplo, considere colocá-lo em uma pasta "InputSystem" na pasta de teste do modo de edição ou modo de reprodução correspondente.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="9d3e9-164">Ícones de script de teste</span><span class="sxs-lookup"><span data-stu-id="9d3e9-164">Test script icons</span></span>

<span data-ttu-id="9d3e9-165">Ao adicionar um novo teste, modifique o script para que ele tenha o ícone de MRTK correto.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="9d3e9-166">Há uma ferramenta de MRTK fácil para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="9d3e9-167">Acesse o item de menu Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="9d3e9-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="9d3e9-168">Clique em Utilitários, em Atualizar e em Ícones</span><span class="sxs-lookup"><span data-stu-id="9d3e9-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="9d3e9-169">Clique em Testes e o atualizador será executado automaticamente, atualizando todos os scripts de teste que não têm seus ícones</span><span class="sxs-lookup"><span data-stu-id="9d3e9-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="9d3e9-170">Métodos do Utilitário do MRTK</span><span class="sxs-lookup"><span data-stu-id="9d3e9-170">MRTK Utility methods</span></span>

<span data-ttu-id="9d3e9-171">Esta seção mostra alguns dos snippets de código/métodos comumente usados ao escrever testes para o MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="9d3e9-172">Há duas classes de Utilitário que ajudam a configurar o MRTK e testar interações com componentes no MRTK</span><span class="sxs-lookup"><span data-stu-id="9d3e9-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="9d3e9-173">TestUtilities fornece os seguintes métodos para configurar sua cena do MRTK e GameObjects:</span><span class="sxs-lookup"><span data-stu-id="9d3e9-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

<span data-ttu-id="9d3e9-174">Consulte os documentos de API do e para obter mais métodos dessas classes util à medida que elas são estendidas regularmente enquanto novos testes são [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) adicionados ao MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d3e9-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>