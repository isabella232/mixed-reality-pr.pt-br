---
title: Como usar o Visual Profiler
description: documentação para usar o Visual Profiler no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 4830615fd55a39614dd775dd7628938ee3af1c3b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143713"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="28a6f-104">Usando o profiler visual</span><span class="sxs-lookup"><span data-stu-id="28a6f-104">Using the visual profiler</span></span>

<span data-ttu-id="28a6f-105">O VisualProfiler fornece uma exibição fácil de usar no aplicativo do desempenho de um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="28a6f-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="28a6f-106">O profiler tem suporte em todas as plataformas do Kit de Ferramentas de Realidade Misturada, incluindo:</span><span class="sxs-lookup"><span data-stu-id="28a6f-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="28a6f-107">Microsoft HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="28a6f-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="28a6f-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="28a6f-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="28a6f-109">Headsets imersivos do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="28a6f-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="28a6f-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="28a6f-110">OpenVR</span></span>

<span data-ttu-id="28a6f-111">Ao desenvolver um aplicativo, concentre-se em várias partes da cena, pois o Visual Profiler exibe dados relativos à exibição atual.</span><span class="sxs-lookup"><span data-stu-id="28a6f-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="28a6f-112">Concentre a atenção em partes da cena com objetos complexos, efeitos de partícula ou atividade.</span><span class="sxs-lookup"><span data-stu-id="28a6f-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="28a6f-113">Esses e outros fatores geralmente contribuem para a redução no desempenho do aplicativo e uma experiência de usuário menor do que a ideal.</span><span class="sxs-lookup"><span data-stu-id="28a6f-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="28a6f-114">Interface do profiler visual</span><span class="sxs-lookup"><span data-stu-id="28a6f-114">Visual profiler interface</span></span>

![Visual Profiler Interface](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="28a6f-116">A interface do Visual Profiler inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="28a6f-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="28a6f-117">Taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="28a6f-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="28a6f-118">Tempo do quadro</span><span class="sxs-lookup"><span data-stu-id="28a6f-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="28a6f-119">Gráfico de quadros</span><span class="sxs-lookup"><span data-stu-id="28a6f-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="28a6f-120">Utilização de memória</span><span class="sxs-lookup"><span data-stu-id="28a6f-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="28a6f-121">Taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="28a6f-121">Frame rate</span></span>

<span data-ttu-id="28a6f-122">No canto superior esquerdo da interface está a taxa de quadros, medida em quadros por segundo.</span><span class="sxs-lookup"><span data-stu-id="28a6f-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="28a6f-123">Para a melhor experiência e conforto do usuário, esse valor deve ser o mais alto possível.</span><span class="sxs-lookup"><span data-stu-id="28a6f-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="28a6f-124">A configuração específica de plataforma e hardware desempenhará uma função significativa na taxa máxima de quadros que pode ser alcançada.</span><span class="sxs-lookup"><span data-stu-id="28a6f-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="28a6f-125">Alguns valores de destino comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="28a6f-125">Some common target values include:</span></span>

- <span data-ttu-id="28a6f-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="28a6f-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="28a6f-127">Realidade mista do Windows ultra: 90</span><span class="sxs-lookup"><span data-stu-id="28a6f-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="28a6f-128">Devido à [limitação da taxa de quadros no HoloLens quando a MRC padrão está ativa](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), o criador de perfil Visual se oculta enquanto vídeos e fotos são capturados.</span><span class="sxs-lookup"><span data-stu-id="28a6f-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="28a6f-129">Essa configuração pode ser substituída no perfil do sistema de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="28a6f-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="28a6f-130">Hora do quadro</span><span class="sxs-lookup"><span data-stu-id="28a6f-130">Frame time</span></span>

<span data-ttu-id="28a6f-131">À direita da taxa de quadros está o tempo de quadro, em milissegundos, gasto na CPU.</span><span class="sxs-lookup"><span data-stu-id="28a6f-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="28a6f-132">Para atingir as taxas de quadros de destino mencionadas anteriormente, um aplicativo pode gastar o seguinte período de tempo por quadro:</span><span class="sxs-lookup"><span data-stu-id="28a6f-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="28a6f-133">60 fps: 16,6 ms</span><span class="sxs-lookup"><span data-stu-id="28a6f-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="28a6f-134">90 FPS: 11,1 MS</span><span class="sxs-lookup"><span data-stu-id="28a6f-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="28a6f-135">A hora da GPU está planejada para ser adicionada em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="28a6f-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="28a6f-136">Gráfico de quadro</span><span class="sxs-lookup"><span data-stu-id="28a6f-136">Frame graph</span></span>

<span data-ttu-id="28a6f-137">O gráfico de quadros fornece uma exibição gráfica do histórico de taxa de quadros do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28a6f-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Grafo de quadro perdido do criador de perfil do Visual](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="28a6f-139">Ao usar o aplicativo, procure quadros perdidos que indiquem que o aplicativo não está atingindo sua taxa de quadros de destino e pode precisar de trabalho de otimização.</span><span class="sxs-lookup"><span data-stu-id="28a6f-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="28a6f-140">Utilização da memória</span><span class="sxs-lookup"><span data-stu-id="28a6f-140">Memory utilization</span></span>

<span data-ttu-id="28a6f-141">A exibição de utilização de memória permite uma compreensão fácil de como a exibição atual está afetando o consumo de memória de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28a6f-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Grafo de memória do criador de perfil do Visual](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="28a6f-143">Ao usar o aplicativo, procure o uso de memória total.</span><span class="sxs-lookup"><span data-stu-id="28a6f-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="28a6f-144">Os principais indicadores incluem a proximidade do limite de memória e as alterações rápidas no uso.</span><span class="sxs-lookup"><span data-stu-id="28a6f-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="28a6f-145">Personalizando o criador de perfil Visual</span><span class="sxs-lookup"><span data-stu-id="28a6f-145">Customizing the visual profiler</span></span>

<span data-ttu-id="28a6f-146">A aparência e o comportamento do criador de perfil do Visual são personalizáveis por meio do perfil do sistema de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="28a6f-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="28a6f-147">Consulte [Configurando o sistema de diagnóstico](configuring-diagnostics.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="28a6f-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="28a6f-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="28a6f-148">See also</span></span>

- [<span data-ttu-id="28a6f-149">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="28a6f-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="28a6f-150">Configurando o sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="28a6f-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)