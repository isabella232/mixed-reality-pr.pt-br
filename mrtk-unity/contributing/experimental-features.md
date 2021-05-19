---
title: Recursos experimentais
description: Documento relacionado a recursos experimentais no MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 705b7ab96d22c5c94c04476de30e5524095c1ce2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144781"
---
# <a name="experimental-features"></a>Recursos experimentais

Alguns recursos em que a equipe do MRTK trabalha parecem ter muito valor inicial, mesmo que ainda não tenhamos completado os detalhes. Para esses tipos de recursos, queremos que a comunidade receba a oportunidade de vê-los mais cedo. Como eles estão no início do ciclo, os rotularemos como experimentais para indicar que ainda estão evoluindo e sujeitos a alterações ao longo do tempo.

## <a name="what-to-expect-from-an-experimental-feature"></a>O que esperar de um recurso experimental

Se um componente for marcado como experimental, você poderá esperar o seguinte:

- Uma cena de exemplo que demonstra o uso, localizada `MRTK/Examples/Experimental` na sub pasta
- Os recursos experimentais podem não ter documentos.
- Provavelmente, eles não têm testes.
- Os recursos experimentais estão sujeitos a alterações.

## <a name="experimental-feature-guidelines"></a>Diretrizes de recursos experimentais

### <a name="experimental-code-should-live-in-a-separate-folder"></a>O código experimental deve residir em uma pasta separada

O código experimental deve entrar em uma pasta experimental de nível superior seguida pelo nome do recurso experimental. Por exemplo, se estiver tentando contribuir com um novo recurso FooBar, coloque o código no seguinte:

- Cenas de exemplo, os scripts vão para `MRTK/Examples/Experimental/FooBar/`
- Scripts de componente, pré-requisitos para `MRTK/SDK/Experimental/FooBar/`
- Os inspetores de componentes vão para `MRTK/SDK/Inspectors/Experimental/FooBar`

Ao usar sub pastas sob o nome do recurso experimental, tente espelhar a mesma estrutura de pastas do MRTK.

Por exemplo, os solucionadores entrariam em `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

Mantenha cenas em uma pasta de cena perto da parte superior: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> Consideramos não ter uma única pasta raiz experimental e, em vez disso, colocar o experimental sob digamos `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` . Decidimos usar as pastas na base para facilitar a descoberta dos recursos experimentais.

### <a name="experimental-code-should-be-in-a-special-namespace"></a>O código experimental deve estar em um namespace especial

Verifique se o código experimental reside em um namespace experimental que corresponde ao local não experimental. Por exemplo, se o componente fizer parte de solveres em `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , seu namespace deverá ser `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .

Consulte [esta PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) para obter um exemplo.

### <a name="experimental-features-should-have-an-experimental-attribute"></a>Os recursos experimentais devem ter um atributo [experimental]

Adicione um `[Experimental]` atributo acima de um dos campos para que uma pequena caixa de diálogo apareça no editor de componentes que mencione que o recurso é experimental e esteja sujeito a alterações significativas.

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>Os menus para recursos experimentais devem estar no submenu "experimental"

Verifique se os recursos experimentais estão em submenus "experimentais" ao adicionar comandos aos menus no editor. Veja alguns exemplos:

Adicionando um comando de menu de nível superior:

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

Adicionando um menu de componentes:

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>Documentação

Siga estas etapas para adicionar a documentação para seu recurso experimental:

1. Qualquer documentação para um recurso experimental deve estar em um `readme.md` arquivo na pasta experimental. Por exemplo, MRTK/SDK/experimental/PulseShader/README. MD.

1. Em *visões gerais de recurso* , adicione um link na seção *experimental* em [`Documentation/toc.yml`](../toc.yml) .

### <a name="minimize-impact-to-mrtk-code"></a>Minimizar o impacto no código MRTK

Embora sua alteração MRTK possa fazer com que seu experimento funcione, isso pode afetar outras pessoas de maneiras que você não espera.
Quaisquer regressões feitas ao código do MRTK Core resultarão na reversão da sua solicitação pull.

O objetivo de ter zero alterações em pastas diferentes das pastas experimentais. Aqui está uma lista de pastas que podem ter alterações experimentais:

- MRTK/SDK/Experimental
- MRTK/SDK/Inspetores/Experimental
- MRTK/Examples/Experimental

As alterações fora dessas pastas devem ser tratadas com muito cuidado. Se o recurso experimental deve incluir alterações no código principal do MRTK, considere dividir as alterações do MRTK em uma solicitação pull separada que inclui testes e documentação.

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>Usar seu recurso experimental não deve afetar a capacidade das pessoas de usar controles principais

A maioria das pessoas usa componentes de experiência do usuário principais, como o botão ManipulationHandler e o Interactable com muita frequência. Provavelmente, eles não usarão seu recurso experimental se impedirem o uso de botões.

O uso do componente não deve quebrar botões, ManipulationHandler, BoundingBox ou interaja.

Por exemplo, nesta [PR ScrollableObjectCollection](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), a adição de um ScrollableObjectCollection fez com que as pessoas não fosse capazes de usar os pré-fabs de botão do HoloLens. Embora isso não tenha sido causado por um bug na PR (mas, em vez disso, expôs um bug existente), ele impediu que a PR fosse verificada.

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>Forneça uma cena de exemplo que demonstra como usar o recurso

As pessoas precisam ver como usar seu recurso e como testá-lo.

Forneça um exemplo em MRTK/Examples/Experimental/YOUR_FEATURE

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>Minimizar falhas visíveis do usuário em recursos experimentais

Outros não usarão o recurso experimental se ele não funcionar, ele não será formado para um recurso.

Teste sua cena de exemplo em sua plataforma de destino, certifique-se de que ela funciona conforme o esperado. Certifique-se de que seu recurso também funcione no editor, para que as pessoas possam iterar rapidamente e ver seu recurso, mesmo que não tenham a plataforma de destino.

## <a name="graduating-experimental-code-into-mrtk-code"></a>Como transformar código experimental em código MRTK

Se um recurso acabar vendo muito uso, devemos gradua-lo no código principal de MRTK. Para fazer isso, o recurso deve ter testes, documentação e uma cena de exemplo.

Quando estiver pronto para graduar o recurso MRTK, crie um problema para fazer check-in do seu PR em relação ao. A PR deve incluir todas as coisas necessárias para tornar esse recurso principal: testes, documentação e uma cena de exemplo mostrando o uso.

Além disso, não se esqueça de atualizar os namespaces para remover o subespaço "experimental".
