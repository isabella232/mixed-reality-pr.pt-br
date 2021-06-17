---
title: ProgressIndicator
description: Visão geral do indicador de progresso no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 9170a376812901cb063038a5513d4fbf79ad0a28
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110127"
---
# <a name="progress-indicators"></a><span data-ttu-id="1994c-104">Indicadores de progresso</span><span class="sxs-lookup"><span data-stu-id="1994c-104">Progress Indicators</span></span>

![Indicadores de progresso](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="1994c-106">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="1994c-106">Example scene</span></span>

<span data-ttu-id="1994c-107">Exemplos de como usar indicadores de progresso podem ser encontrados na `ProgressIndicatorExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="1994c-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="1994c-108">Esta cena demonstra cada um dos pré-requisitos de indicador de progresso incluídos no SDK.</span><span class="sxs-lookup"><span data-stu-id="1994c-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="1994c-109">Ele também demonstra como usar indicadores de progresso em conjunto com algumas tarefas assíncronas comuns, como o carregamento de cena.</span><span class="sxs-lookup"><span data-stu-id="1994c-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="1994c-110">Exemplo: Abrir, atualizar & fechar um indicador de progresso</span><span class="sxs-lookup"><span data-stu-id="1994c-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="1994c-111">Os indicadores de progresso implementam a [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface .</span><span class="sxs-lookup"><span data-stu-id="1994c-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="1994c-112">Essa interface pode ser recuperada de um GameObject usando `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="1994c-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="1994c-113">Os `IProgressIndicator.OpenAsync()` métodos `IProgressIndicator.CloseAsync()` e retornam [Tarefas](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="1994c-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="1994c-114">É recomendável aguardar essas Tarefas em um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="1994c-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="1994c-115">Os pré-padrões do indicador de progresso padrão do MRTK devem estar inativos quando colocados em uma cena.</span><span class="sxs-lookup"><span data-stu-id="1994c-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="1994c-116">Quando seus `IProgressIndicator.OpenAsync()` métodos são chamados, os indicadores de progresso ativarão e desativarão seus gameobjects automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1994c-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="1994c-117">(Esse padrão não é um requisito da interface IProgressIndicator.)</span><span class="sxs-lookup"><span data-stu-id="1994c-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="1994c-118">De definir a propriedade do `Progress` indicador como um valor de 0 a 1 para atualizar seu progresso exibido.</span><span class="sxs-lookup"><span data-stu-id="1994c-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="1994c-119">De definir `Message` sua propriedade para atualizar sua mensagem exibida.</span><span class="sxs-lookup"><span data-stu-id="1994c-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="1994c-120">Implementações diferentes podem exibir esse conteúdo de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="1994c-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="1994c-121">Estados indicadores</span><span class="sxs-lookup"><span data-stu-id="1994c-121">Indicator states</span></span>

<span data-ttu-id="1994c-122">A propriedade de um `State` indicador determina quais operações são válidas.</span><span class="sxs-lookup"><span data-stu-id="1994c-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="1994c-123">Chamar um método inválido normalmente fará com que o indicador reporte um erro e não tome nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="1994c-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="1994c-124">Estado</span><span class="sxs-lookup"><span data-stu-id="1994c-124">State</span></span> | <span data-ttu-id="1994c-125">Operações válidas</span><span class="sxs-lookup"><span data-stu-id="1994c-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="1994c-126">`AwaitTransitionAsync()` pode ser usado para ter certeza de que um indicador está totalmente aberto ou fechado antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="1994c-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
