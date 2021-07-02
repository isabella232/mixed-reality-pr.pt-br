---
title: Indicador de progresso
description: Visão geral do indicador de progresso no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 268d13d00bc0bcf1d522eaa6809dab9892624e11
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176570"
---
# <a name="progress-indicator"></a><span data-ttu-id="fc943-104">Indicador de progresso</span><span class="sxs-lookup"><span data-stu-id="fc943-104">Progress indicator</span></span>

![Indicadores de progresso](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="fc943-106">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="fc943-106">Example scene</span></span>

<span data-ttu-id="fc943-107">Exemplos de como usar indicadores de progresso podem ser encontrados na `ProgressIndicatorExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="fc943-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="fc943-108">Essa cena demonstra cada um dos indicadores de progresso pré-fabricados incluídos no SDK.</span><span class="sxs-lookup"><span data-stu-id="fc943-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="fc943-109">Ele também demonstra como usar indicadores de progresso em conjunto com algumas tarefas assíncronas comuns como carregamento de cena.</span><span class="sxs-lookup"><span data-stu-id="fc943-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="fc943-110">Exemplo: abrir, atualizar & fechar um indicador de progresso</span><span class="sxs-lookup"><span data-stu-id="fc943-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="fc943-111">Os indicadores de progresso implementam a [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span><span class="sxs-lookup"><span data-stu-id="fc943-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="fc943-112">Essa interface pode ser recuperada de um gameobject usando `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="fc943-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="fc943-113">Os `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` métodos e retornam [tarefas](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="fc943-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="fc943-114">É recomendável aguardar essas tarefas em um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="fc943-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="fc943-115">O indicador de progresso padrão do MRTK pré-fabricados deve estar inativo quando colocado em uma cena.</span><span class="sxs-lookup"><span data-stu-id="fc943-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="fc943-116">Quando seus `IProgressIndicator.OpenAsync()` métodos são chamados, os indicadores de progresso ativam e desativam seus Gameobjects automaticamente.</span><span class="sxs-lookup"><span data-stu-id="fc943-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="fc943-117">(Esse padrão não é um requisito da interface IProgressIndicator.)</span><span class="sxs-lookup"><span data-stu-id="fc943-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="fc943-118">Defina a propriedade do indicador `Progress` com um valor de 0-1 para atualizar seu progresso exibido.</span><span class="sxs-lookup"><span data-stu-id="fc943-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="fc943-119">Defina sua `Message` propriedade para atualizar sua mensagem exibida.</span><span class="sxs-lookup"><span data-stu-id="fc943-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="fc943-120">Implementações diferentes podem exibir esse conteúdo de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="fc943-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="fc943-121">Estados do indicador</span><span class="sxs-lookup"><span data-stu-id="fc943-121">Indicator states</span></span>

<span data-ttu-id="fc943-122">A propriedade de um indicador `State` determina quais operações são válidas.</span><span class="sxs-lookup"><span data-stu-id="fc943-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="fc943-123">Chamar um método inválido normalmente fará com que o indicador relate um erro e não execute nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="fc943-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="fc943-124">Estado</span><span class="sxs-lookup"><span data-stu-id="fc943-124">State</span></span> | <span data-ttu-id="fc943-125">Operações válidas</span><span class="sxs-lookup"><span data-stu-id="fc943-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="fc943-126">`AwaitTransitionAsync()` pode ser usado para ter certeza de que um indicador está totalmente aberto ou fechado antes de ser usado.</span><span class="sxs-lookup"><span data-stu-id="fc943-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
