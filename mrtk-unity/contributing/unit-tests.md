---
title: UnitTests
description: UnitTests para verificar a reliablidade do MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, UnitTest,
ms.openlocfilehash: 51a485ff258ceafb8841ff1b86e715b1623f3255
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489236"
---
# <a name="writing-and-running-tests-in-mrtk"></a>Escrevendo e executando testes no MRTK

Para garantir que o MRTK seja confiável, o MRTK tem um conjunto de testes para garantir que as alterações no código não regredam o comportamento existente. Ter uma boa cobertura de teste em uma grande base de código, como o MRTK, é crucial para a estabilidade e a confiança ao fazer alterações.

O MRTK usa o [Test Runner do Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) que usa uma integração do Unity do [NUnit.](https://nunit.org/) Este guia fornecerá um ponto de partida sobre como adicionar testes ao MRTK. Ele não explicará o [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) e o [NUnit,](https://nunit.org/) que podem ser procurados nos links fornecidos.

Antes de enviar uma solicitação de pull, certifique-se de:

1. Execute os testes localmente para que suas alterações não regredissem o comportamento existente (a conclusão de PRs não será permitida se algum teste falhar).

1. Se estiver corrigindo um bug, escreva um teste para testar a correção e verifique se as modificações futuras de código não a quebrarão novamente.

1. Se estiver escrevendo um recurso, escreva novos testes para evitar alterações de código futuras quebrando esse recurso.

Atualmente, os testes de playmode devem ser executados no Unity 2018.4 e podem falhar em outras versões do Unity

## <a name="running-tests"></a>Executando testes

### <a name="unity-editor"></a>Editor do Unity

O [Test Runner do Unity pode](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) ser encontrado em **Window** General Test Runner e mostrará todos os testes de modo de reprodução e edição do  >    >   MRTK disponíveis.

### <a name="command-line"></a>Linha de comando

Os testes também podem ser executados por um script [do PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) localizado em `Scripts\test\run_playmode_tests.ps1` . Isso executará os testes de playmode exatamente como eles são executados no github/CI (veja abaixo) e imprimirá os resultados. Aqui estão alguns exemplos de como executar o script

Execute os testes no projeto localizado em H:\mrtk.dev, com o Unity 2018.4 (por exemplo, Unity 2018.4.26f1)

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Execute os testes no projeto localizado em H:\mrtk.dev, com o Unity 2018.4, saída de resultados para C:\playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

Também é possível executar os testes de playmode várias vezes por meio do `run_repeat_tests.ps1` script. Todos os parâmetros usados em `run_playmode_tests.ps1` podem ser usados.

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>Validação de solicitação pull

O CI do MRTK criará MRTK em todas as configurações e executará todos os testes do modo de edição e reprodução. O CI pode ser disparado por meio da postagem de um comentário na PR do GitHub `/azp run mrtk_pr` se o usuário tiver direitos suficientes. As execuções de CI podem ser vistas na guia ' verificações ' da PR.

Somente depois que todos os testes forem aprovados com êxito, a PR poderá ser mesclada no principal.

### <a name="stress-tests--bulk-tests"></a>Testes de estresse/testes em massa

Às vezes, os testes só falharão ocasionalmente, o que pode ser frustrante para depurar.

Para que vários testes sejam executados localmente, modifique os scripts de teste de acordo. O script Python a seguir deve tornar esse cenário mais conveniente.

O pré-requisito para executar o script Python é ter o [Python 3. X instalado](https://www.python.org/downloads/).

Para um único teste que precisa ser executado várias vezes:

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

Execute o seguinte em uma linha de comando (o[PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) é recomendado)

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

Copie e cole a saída em seu arquivo de teste. O script a seguir é para executar vários testes em sequência:

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

O novo arquivo de teste agora deve conter

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

Abra o executor de teste e observe os novos testes que agora podem ser chamados repetidamente.

## <a name="writing-tests"></a>Escrevendo testes

Há dois tipos de testes que podem ser adicionados para o novo código

* Testes do modo de reprodução
* Editar testes de modo

### <a name="play-mode-tests"></a>Testes de modo de reprodução

Os testes de modo de reprodução do MRTK têm a capacidade de testar como o novo recurso responde a diferentes fontes de entrada, como mãos ou olhos.

Novos testes de modo de reprodução podem [herdar BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) ou o esqueleto abaixo pode ser usado.

Para criar um novo teste de modo de reprodução:

* Navegue até Ativos > mrtk > testes > PlayModeTests
* Clique com o botão direito do mouse em Criar > teste > script de teste do C#
* Substitua o modelo padrão pelo esqueleto abaixo

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

### <a name="edit-mode-tests"></a>Editar testes de modo

Os testes de modo de edição são executados no modo de edição do Unity e podem ser adicionados na pasta  >    >  **EditModeTests** de Testes do MRTK no repo do Kit de Ferramentas de Realidade Misturada.
Para criar um novo teste, o seguinte modelo pode ser usado:

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

### <a name="test-naming-conventions"></a>Testar convenções de nomen entre

Os testes geralmente devem ser nomeados com base na classe que estão testando ou no cenário em que estão testando.
Por exemplo, dada uma classe a ser testada:

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

Considere nomear o teste

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

Considere colocar o teste em uma hierarquia de pastas semelhante ao arquivo não de teste correspondente.
Por exemplo:

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

Isso é para garantir que haja uma maneira clara de localizar a classe de teste correspondente de cada classe, se tal classe de teste existir.

O posicionamento de testes baseados em cenário é menos definido – se o teste exercícios do sistema de entrada geral, por exemplo, considere colocá-lo em uma pasta "InputSystem" no modo de edição correspondente ou na pasta de teste do modo de reprodução.

### <a name="test-script-icons"></a>Ícones de script de teste

Ao adicionar um novo teste, modifique o script para ter o ícone correto do MRTK. Há uma ferramenta fácil de MRTK para fazer isso:

1. Vá para o item de menu do kit de ferramentas da realidade misturada
1. Clique em utilitários, depois em atualizar e em ícones
1. Clique em testes e o atualizador será executado automaticamente, atualizando os scripts de teste que não têm seus ícones

### <a name="mrtk-utility-methods"></a>Métodos do utilitário MRTK

Esta seção mostra alguns dos métodos/trechos de código usados com frequência ao escrever testes para MRTK.

Há duas classes utilitárias que ajudam na configuração de interações de teste e MRTK com componentes no MRTK

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities fornecem os seguintes métodos para configurar sua cena MRTK e GameObjects:

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

Consulte os documentos da API do [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) e [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) para obter mais métodos dessas classes do util, uma vez que elas são estendidas regularmente, enquanto novos testes são adicionados ao MRTK.