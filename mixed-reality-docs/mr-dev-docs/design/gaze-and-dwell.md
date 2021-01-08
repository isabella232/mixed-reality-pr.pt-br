---
title: Focar e esperar
description: Obtenha uma visão geral do modelo de entrada de olho e de olhar e de cabeça para aplicativos de realidade misturada.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade misturada, olhar, pesquisa, interação, design, controle de cabeça, acompanhamento de cabeçalho, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 2daeea996251b1220ee4753567b42117fbb2126c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007636"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="d8bd1-104">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="d8bd1-104">Gaze and dwell</span></span>

<span data-ttu-id="d8bd1-105">Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="d8bd1-106">Os comandos de voz também podem não ser confiáveis em determinados contextos, por exemplo, sob condições excessivamente alta.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="d8bd1-107">A olhar e a pesquisa oferecem um mecanismo familiar e fácil de dominar para as cabeças de trabalho e as mãos gratuitas no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="d8bd1-108">Além disso, o olhar e a pesquisa são um ótimo fallback, o que é independente da interferência de ruído ou restrições de silêncio no ambiente operacional.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-108">Additionally, gaze and dwell is a great fallback, which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="d8bd1-109">Distinguimos duas variantes de _olhar e de duração_: [Head-olhar e de pesquisa](gaze-and-dwell-head.md) e [olho-olhar e a pesquisa](gaze-and-dwell-eyes.md).</span><span class="sxs-lookup"><span data-stu-id="d8bd1-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="d8bd1-110">Cenários</span><span class="sxs-lookup"><span data-stu-id="d8bd1-110">Scenarios</span></span>

<span data-ttu-id="d8bd1-111">A olhar e a pesquisa são Excel em cenários em que as mãos de uma pessoa estão ocupadas com outras tarefas, e a voz não é 100% confiável ou está disponível devido a restrições de ambiente ou sociais.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="d8bd1-112">Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="d8bd1-113">Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="d8bd1-114">O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="d8bd1-115">A olhar e a pesquisa permitem que a pessoa que usa o HoloLens Navegue com confiança no material de referência sem interromper o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d8bd1-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="d8bd1-116">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="d8bd1-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d8bd1-117"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="d8bd1-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="d8bd1-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d8bd1-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d8bd1-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d8bd1-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d8bd1-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="d8bd1-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d8bd1-121">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="d8bd1-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="d8bd1-122">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="d8bd1-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="d8bd1-123">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="d8bd1-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="d8bd1-124">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="d8bd1-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d8bd1-125">Focar com o olhar e esperar</span><span class="sxs-lookup"><span data-stu-id="d8bd1-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="d8bd1-126">❌ Não disponível</span><span class="sxs-lookup"><span data-stu-id="d8bd1-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="d8bd1-127">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="d8bd1-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="d8bd1-128">❌ Não disponível</span><span class="sxs-lookup"><span data-stu-id="d8bd1-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="d8bd1-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="d8bd1-129">See also</span></span>

* [<span data-ttu-id="d8bd1-130">Interação ocular</span><span class="sxs-lookup"><span data-stu-id="d8bd1-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="d8bd1-131">Acompanhamento ocular no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d8bd1-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="d8bd1-132">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="d8bd1-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d8bd1-133">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="d8bd1-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d8bd1-134">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="d8bd1-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="d8bd1-135">Mãos – Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="d8bd1-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="d8bd1-136">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="d8bd1-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="d8bd1-137">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="d8bd1-137">Voice input</span></span>](voice-input.md)
