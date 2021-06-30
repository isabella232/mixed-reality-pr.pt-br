---
title: Recursos experimentais
description: Documento relacionado a recursos experimentais no MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 341ba0ee3e5900cc52f1ef715232f49064102309
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121374"
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
> Considerámos não ter uma única pasta raiz experimental e, em vez disso, colocar Experimental em digamos `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` . Decidimos usar pastas na base para facilitar a descoberta dos recursos experimentais.

### <a name="experimental-code-should-be-in-a-special-namespace"></a>O código experimental deve estar em um namespace especial

Verifique se o código experimental reside em um namespace experimental que corresponde ao local não experimental. Por exemplo, se o componente faz parte dos solucionadores em `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , seu namespace deve ser `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .

Consulte [esta PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) para ver um exemplo.

### <a name="experimental-features-should-have-an-experimental-attribute"></a>Os recursos experimentais devem ter um atributo [Experimental]

Adicione um atributo acima de um de seus campos para que uma pequena caixa de diálogo apareça no editor de componentes que menciona que seu recurso é experimental e está sujeito `[Experimental]` a alterações significativas.

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>Menus para recursos experimentais devem estar no sub menu "Experimental"

Verifique se os recursos experimentais estão em sub-menus "experimentais" ao adicionar comandos aos menus no editor. Veja alguns exemplos:

Adicionando um comando de menu de nível superior:

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

Adicionando um menu de componente:

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>Documentação

Siga estas etapas para adicionar a documentação do recurso experimental:

1. Qualquer documentação para um recurso experimental deve estar em `readme.md` um arquivo na pasta experimental. Por exemplo, MRTK/SDK/Experimental/PulseShader/readme.md.

1. Em *Visão geral do recurso,* adicione um link na seção *Experimental* em [`Documentation/toc.yml`](../toc.yml) .

### <a name="minimize-impact-to-mrtk-code"></a>Minimizar o impacto no código do MRTK

Embora a alteração do MRTK possa fazer com que seu experimento funcione, isso pode afetar outras pessoas de maneiras que você não espera.
Todas as regressões que você fizer ao código principal do MRTK resultariam na reversão da solicitação de pull.

O objetivo é ter zero alterações em pastas que não são experimentais. Aqui está uma lista de pastas que podem ter alterações experimentais:

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

Se um recurso acabar vendo muita utilização, devemos agredá-lo no código principal do MRTK. Para fazer isso, o recurso deve ter testes, documentação e uma cena de exemplo.

Quando você estiver pronto para formar o RECURSO MRTK, crie um problema para verificar sua PR. A PR deve incluir todas as coisas necessárias para tornar isso um recurso principal: testes, documentação e uma cena de exemplo mostrando o uso.

Além disso, não se esqueça de atualizar os namespaces para remover o subespaço "Experimental".
