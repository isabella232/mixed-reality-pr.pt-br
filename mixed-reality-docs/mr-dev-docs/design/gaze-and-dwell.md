---
title: Focar e esperar
description: Obtenha uma visão geral do modelo de entrada de olho e de olhar e de cabeça para aplicativos de realidade misturada.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade misturada, olhar, pesquisa, interação, design, controle de cabeça, acompanhamento de cabeçalho, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: aa4fceeb8875da89fd7f84c3709ff6db07fd96f4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582132"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="2b435-104">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="2b435-104">Gaze and dwell</span></span>

<span data-ttu-id="2b435-105">Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis.</span><span class="sxs-lookup"><span data-stu-id="2b435-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="2b435-106">Os comandos de voz também podem não ser confiáveis em determinados contextos, por exemplo, sob condições excessivamente alta.</span><span class="sxs-lookup"><span data-stu-id="2b435-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="2b435-107">A olhar e a pesquisa oferecem um mecanismo familiar e fácil de dominar para as cabeças de trabalho e as mãos gratuitas no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2b435-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="2b435-108">Além disso, o olhar e a pesquisa são um ótimo fallback, o que é independente da interferência de ruído ou restrições de silêncio no ambiente operacional.</span><span class="sxs-lookup"><span data-stu-id="2b435-108">Additionally, gaze and dwell is a great fallback, which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="2b435-109">Distinguimos duas variantes de _olhar e de duração_: [Head-olhar e de pesquisa](gaze-and-dwell-head.md) e [olho-olhar e a pesquisa](gaze-and-dwell-eyes.md).</span><span class="sxs-lookup"><span data-stu-id="2b435-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="2b435-110">Cenários</span><span class="sxs-lookup"><span data-stu-id="2b435-110">Scenarios</span></span>

<span data-ttu-id="2b435-111">A olhar e a pesquisa são Excel em cenários em que as mãos de uma pessoa estão ocupadas com outras tarefas, e a voz não é 100% confiável ou está disponível devido a restrições de ambiente ou sociais.</span><span class="sxs-lookup"><span data-stu-id="2b435-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="2b435-112">Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro.</span><span class="sxs-lookup"><span data-stu-id="2b435-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="2b435-113">Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor.</span><span class="sxs-lookup"><span data-stu-id="2b435-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="2b435-114">O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="2b435-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="2b435-115">A olhar e a pesquisa permitem que a pessoa que usa o HoloLens Navegue com confiança no material de referência sem interromper o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2b435-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="2b435-116">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="2b435-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2b435-117"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="2b435-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="2b435-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2b435-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2b435-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2b435-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2b435-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="2b435-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2b435-121">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="2b435-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="2b435-122">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="2b435-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="2b435-123">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="2b435-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="2b435-124">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="2b435-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2b435-125">Focar com o olhar e esperar</span><span class="sxs-lookup"><span data-stu-id="2b435-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="2b435-126">❌ Não disponível</span><span class="sxs-lookup"><span data-stu-id="2b435-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="2b435-127">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="2b435-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="2b435-128">❌ Não disponível</span><span class="sxs-lookup"><span data-stu-id="2b435-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="2b435-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="2b435-129">See also</span></span>

* [<span data-ttu-id="2b435-130">Interação ocular</span><span class="sxs-lookup"><span data-stu-id="2b435-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="2b435-131">Acompanhamento ocular no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2b435-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="2b435-132">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="2b435-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2b435-133">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="2b435-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2b435-134">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="2b435-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="2b435-135">Mãos – Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="2b435-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="2b435-136">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="2b435-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="2b435-137">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="2b435-137">Voice input</span></span>](voice-input.md)