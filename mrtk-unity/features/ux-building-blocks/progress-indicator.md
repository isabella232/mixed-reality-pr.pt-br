---
title: Indicador de progresso
description: Visão geral do indicador de progresso no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: b5147e5c592b80ab100a7cf7ce2487d971299832fec11f7ca57b1fdeef530900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202574"
---
# <a name="progress-indicator"></a>Indicador de progresso

![Indicadores de progresso](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>Cena de exemplo

Exemplos de como usar indicadores de progresso podem ser encontrados na `ProgressIndicatorExamples` cena. Esta cena demonstra cada um dos pré-requisitos de indicador de progresso incluídos no SDK. Ele também demonstra como usar indicadores de progresso em conjunto com algumas tarefas assíncronas comuns, como o carregamento de cena.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>Exemplo: Abrir, atualizar & fechar um indicador de progresso

Os indicadores de progresso implementam a [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface . Essa interface pode ser recuperada de um GameObject usando `GetComponent` .

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

Os `IProgressIndicator.OpenAsync()` métodos `IProgressIndicator.CloseAsync()` e retornam [Tarefas](xref:System.Threading.Tasks.Task). É recomendável aguardar essas Tarefas em um método assíncrono.

Os pré-padrões do indicador de progresso padrão do MRTK devem estar inativos quando colocados em uma cena. Quando seus `IProgressIndicator.OpenAsync()` métodos são chamados, os indicadores de progresso ativarão e desativarão seus gameobjects automaticamente. (Esse padrão não é um requisito da interface IProgressIndicator.)

De definir a propriedade do `Progress` indicador como um valor de 0 a 1 para atualizar seu progresso exibido. De definir `Message` sua propriedade para atualizar sua mensagem exibida. Implementações diferentes podem exibir esse conteúdo de maneiras diferentes.

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a>Estados indicadores

A propriedade de um `State` indicador determina quais operações são válidas. Chamar um método inválido normalmente fará com que o indicador reporte um erro e não tome nenhuma ação.

Estado | Operações válidas
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` pode ser usado para ter certeza de que um indicador está totalmente aberto ou fechado antes de usá-lo.

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
