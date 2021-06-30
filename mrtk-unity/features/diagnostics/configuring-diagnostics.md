---
title: Configurando o diagnóstico
description: Documentação para configurar o diagnóstico no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 211ee2ed06ba9b13bd90169bcc7ee50da4594034
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121794"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="7b32c-104">Configurando o sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7b32c-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="7b32c-105">Configurações gerais</span><span class="sxs-lookup"><span data-stu-id="7b32c-105">General settings</span></span>

![Configurações gerais de diagnóstico](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="7b32c-107">Habilitar o log detalhado</span><span class="sxs-lookup"><span data-stu-id="7b32c-107">Enable verbose logging</span></span>

<span data-ttu-id="7b32c-108">Indica se o log de MRTK detalhado será habilitado ou não.</span><span class="sxs-lookup"><span data-stu-id="7b32c-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="7b32c-109">Esse padrão é false, mas pode ser ativado para fazer rastreamentos detalhados que permitem que a equipe de MRTK depure/aprofunde os problemas.</span><span class="sxs-lookup"><span data-stu-id="7b32c-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="7b32c-110">Por exemplo, ao arquivar um problema, anexar os logs do Player do Unity (do editor ou do Player) pode ajudar a restringir a origem de bugs e problemas.</span><span class="sxs-lookup"><span data-stu-id="7b32c-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="7b32c-111">Observe que essa opção é independente de o sistema de diagnóstico estar habilitado ou não, que aparece no sistema de diagnóstico porque é uma opção de log, mas, por fim, opera em um nível mais alto, pois afeta o registro em log em toda a base de código MRTK.</span><span class="sxs-lookup"><span data-stu-id="7b32c-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="7b32c-112">Mostrar diagnósticos</span><span class="sxs-lookup"><span data-stu-id="7b32c-112">Show diagnostics</span></span>

<span data-ttu-id="7b32c-113">Indica se o sistema de diagnóstico deve ou não exibir as opções de diagnóstico configuradas.</span><span class="sxs-lookup"><span data-stu-id="7b32c-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="7b32c-114">Quando desabilitado, todas as opções de diagnóstico configuradas serão ocultas.</span><span class="sxs-lookup"><span data-stu-id="7b32c-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="7b32c-115">Configurações do criador de perfil</span><span class="sxs-lookup"><span data-stu-id="7b32c-115">Profiler settings</span></span>

![Configurações do diagnóstico Profiler](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="7b32c-117">Mostrar criador de perfil</span><span class="sxs-lookup"><span data-stu-id="7b32c-117">Show profiler</span></span>

<span data-ttu-id="7b32c-118">Indica se o criador de perfil do Visual deve ser exibido ou não.</span><span class="sxs-lookup"><span data-stu-id="7b32c-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="7b32c-119">Taxa de amostra de quadro</span><span class="sxs-lookup"><span data-stu-id="7b32c-119">Frame sample rate</span></span>

<span data-ttu-id="7b32c-120">A quantidade de tempo, em segundos, para coletar quadros para cálculo de taxa de quadros.</span><span class="sxs-lookup"><span data-stu-id="7b32c-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="7b32c-121">O intervalo é de 0 a 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="7b32c-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="7b32c-122">Âncora de janela</span><span class="sxs-lookup"><span data-stu-id="7b32c-122">Window anchor</span></span>

<span data-ttu-id="7b32c-123">Para qual parte da porta de exibição a janela do criador de perfil deve ser ancorada.</span><span class="sxs-lookup"><span data-stu-id="7b32c-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="7b32c-124">O valor padrão é inferior centro.</span><span class="sxs-lookup"><span data-stu-id="7b32c-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="7b32c-125">Deslocamento da janela</span><span class="sxs-lookup"><span data-stu-id="7b32c-125">Window offset</span></span>

<span data-ttu-id="7b32c-126">O deslocamento, do centro da porta de exibição, para posicionar o Visual Profiler.</span><span class="sxs-lookup"><span data-stu-id="7b32c-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="7b32c-127">O deslocamento estará na direção da propriedade âncora da *janela* .</span><span class="sxs-lookup"><span data-stu-id="7b32c-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="7b32c-128">Escala da janela</span><span class="sxs-lookup"><span data-stu-id="7b32c-128">Window scale</span></span>

<span data-ttu-id="7b32c-129">Multiplicador de tamanho aplicado à janela do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="7b32c-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="7b32c-130">Por exemplo, definir o valor como 2 dobrará o tamanho da janela.</span><span class="sxs-lookup"><span data-stu-id="7b32c-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="7b32c-131">Velocidade da janela</span><span class="sxs-lookup"><span data-stu-id="7b32c-131">Window follow speed</span></span>

<span data-ttu-id="7b32c-132">A velocidade na qual mover a janela do criador de perfil para manter a visibilidade dentro da porta de exibição.</span><span class="sxs-lookup"><span data-stu-id="7b32c-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="7b32c-133">Controlando programaticamente o sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7b32c-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="7b32c-134">Também é possível alternar a visibilidade do sistema de diagnóstico e o criador de perfil em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7b32c-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="7b32c-135">Por exemplo, o código a seguir ocultará o sistema de diagnóstico e o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="7b32c-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="7b32c-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b32c-136">See also</span></span>

- [<span data-ttu-id="7b32c-137">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7b32c-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="7b32c-138">Usando o criador de perfil Visual</span><span class="sxs-lookup"><span data-stu-id="7b32c-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
