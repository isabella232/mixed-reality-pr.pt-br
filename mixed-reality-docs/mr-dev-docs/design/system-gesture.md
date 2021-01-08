---
title: Iniciar gesto
description: Saiba como usar o gesto de início para chamar o menu iniciar no HoloLens e nos headsets de imersão de realidade mista do Windows.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidade misturada, gestos, interação, design, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas da realidade misturada, flor
ms.openlocfilehash: 9e29d483375db103cebc30be9117e40899a9f81f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009426"
---
# <a name="start-gesture"></a><span data-ttu-id="c2742-104">Iniciar gesto</span><span class="sxs-lookup"><span data-stu-id="c2742-104">Start gesture</span></span>

<span data-ttu-id="c2742-105">O gesto de início é um gesto de mão usado para invocar o menu iniciar.</span><span class="sxs-lookup"><span data-stu-id="c2742-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="c2742-106">É o equivalente a pressionar a tecla Windows em teclados, o botão Xbox em controladores Xbox ou o botão Windows em controladores de movimento de headsets de imersão.</span><span class="sxs-lookup"><span data-stu-id="c2742-106">It's the equivalent of pressing the Windows key on keyboards, the Xbox button on Xbox controllers, or the Windows button on immersive headset motion controllers.</span></span> <span data-ttu-id="c2742-107">Preste atenção especial aos gestos do sistema reservado em cada dispositivo de realidade misturada para evitar conflitos quando estiver criando interações.</span><span class="sxs-lookup"><span data-stu-id="c2742-107">Pay special attention to reserved system gestures on each Mixed Reality device to prevent conflicts when you're designing interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="c2742-108">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="c2742-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c2742-109"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="c2742-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c2742-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c2742-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c2742-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c2742-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c2742-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c2742-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c2742-113">Bloom</span><span class="sxs-lookup"><span data-stu-id="c2742-113">Bloom</span></span></td>
        <td><span data-ttu-id="c2742-114">✔️</span><span class="sxs-lookup"><span data-stu-id="c2742-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="c2742-115">Botão do pulso</span><span class="sxs-lookup"><span data-stu-id="c2742-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c2742-116">✔️</span><span class="sxs-lookup"><span data-stu-id="c2742-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="c2742-117">Olho olhar e Palm up pinçar</span><span class="sxs-lookup"><span data-stu-id="c2742-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c2742-118">✔️</span><span class="sxs-lookup"><span data-stu-id="c2742-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="c2742-119">Bloom</span><span class="sxs-lookup"><span data-stu-id="c2742-119">Bloom</span></span>

<span data-ttu-id="c2742-120">Projetamos "cair" para abrir o menu iniciar no HoloLens (1º gen), que é um gesto simbólico imitando um Blossom de flor.</span><span class="sxs-lookup"><span data-stu-id="c2742-120">We designed “Bloom” to bring up the start menu in HoloLens (1st gen), which is a symbolic gesture mimicking a flower blossom.</span></span> <span data-ttu-id="c2742-121">É distintivo para uma interação com o pé, fácil de usar e rápida de se lembrar.</span><span class="sxs-lookup"><span data-stu-id="c2742-121">It's distinctive for sure-footed interaction, easy of use, and quick to recall.</span></span> <span data-ttu-id="c2742-122">Para usar o gesto, mantenha a mão com seu Palm up e mãos, em seguida, abra sua mão distribuindo os dedos.</span><span class="sxs-lookup"><span data-stu-id="c2742-122">To use the gesture, hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c2742-123">![Fechamento de flor](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="c2742-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="c2742-124">**Etapa 1: Palm juntos**</span><span class="sxs-lookup"><span data-stu-id="c2742-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2742-125">![Flor aberta](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="c2742-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="c2742-126">**Etapa 2: Palm up com as mãos espalhadas**</span><span class="sxs-lookup"><span data-stu-id="c2742-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="c2742-127">Iniciar gesto</span><span class="sxs-lookup"><span data-stu-id="c2742-127">Start gesture</span></span>

<span data-ttu-id="c2742-128">No HoloLens 2, substituímos o gesto de cair com um botão de pulso virtual, que é mais instinctual para os usuários.</span><span class="sxs-lookup"><span data-stu-id="c2742-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button, which is more instinctual for users.</span></span> <span data-ttu-id="c2742-129">Ao mostrar os usuários o botão no pulso, eles podem acessá-lo intuitivamente e pressioná-lo com a outra mão.</span><span class="sxs-lookup"><span data-stu-id="c2742-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c2742-130">![Botão do punho pronto](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="c2742-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="c2742-131">**Etapa 1: Palm up para mostrar o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="c2742-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2742-132">![Botão do pulso pressionado](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="c2742-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="c2742-133">**Etapa 2: Pressione o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="c2742-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a><span data-ttu-id="c2742-134">Gesto de início de uma mão</span><span class="sxs-lookup"><span data-stu-id="c2742-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2742-135">Para que o gesto de início de uma mão funcione:</span><span class="sxs-lookup"><span data-stu-id="c2742-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="c2742-136">Você deve atualizar para a atualização de novembro de 2019 (Build 18363,1039) ou posterior.</span><span class="sxs-lookup"><span data-stu-id="c2742-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="c2742-137">Seus olhos devem ser calibrados no dispositivo para que o acompanhamento de olho funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="c2742-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="c2742-138">Se você não vir pontos de an-órbita em volta do ícone iniciar quando olhar para ele, seus olhos não serão calibrados no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c2742-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="c2742-139">Você também pode usar o gesto de início com apenas uma mão.</span><span class="sxs-lookup"><span data-stu-id="c2742-139">You can also use the Start gesture with only one hand.</span></span> <span data-ttu-id="c2742-140">Mantenha sua mão em frente com seu Palm e veja o **ícone iniciar** no pulso interno.</span><span class="sxs-lookup"><span data-stu-id="c2742-140">Hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="c2742-141">**Enquanto mantém seu olho no ícone**, aperte seu polegar e indexe o dedo em conjunto.</span><span class="sxs-lookup"><span data-stu-id="c2742-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="c2742-142">![Botão do punho pronto](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="c2742-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="c2742-143">**Etapa 1: Palm up para mostrar o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="c2742-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2742-144">![Botão do pulso pinçar](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="c2742-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="c2742-145">**Etapa 2: olho olhar no botão e, em seguida, aperte**</span><span class="sxs-lookup"><span data-stu-id="c2742-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="c2742-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="c2742-146">See also</span></span>

* [<span data-ttu-id="c2742-147">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="c2742-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="c2742-148">Olho-olhar</span><span class="sxs-lookup"><span data-stu-id="c2742-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="c2742-149">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="c2742-149">Voice input</span></span>](voice-input.md)
