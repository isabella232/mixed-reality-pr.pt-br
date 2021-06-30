---
title: Usando o profiler visual
description: documentação para usar o Visual Profiler no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: c3238aed60f6bbf824c74c034ddf506f49f436c7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121644"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="51469-104">Usando o profiler visual</span><span class="sxs-lookup"><span data-stu-id="51469-104">Using the visual profiler</span></span>

<span data-ttu-id="51469-105">O VisualProfiler fornece uma exibição fácil de usar no aplicativo do desempenho de um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="51469-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="51469-106">O profiler tem suporte em todas as plataformas do Kit de Ferramentas de Realidade Misturada, incluindo:</span><span class="sxs-lookup"><span data-stu-id="51469-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="51469-107">Microsoft HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="51469-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="51469-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="51469-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="51469-109">Headsets imersivos do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="51469-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="51469-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="51469-110">OpenVR</span></span>

<span data-ttu-id="51469-111">Ao desenvolver um aplicativo, concentre-se em várias partes da cena, pois o Visual Profiler exibe dados relativos à exibição atual.</span><span class="sxs-lookup"><span data-stu-id="51469-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51469-112">Concentre a atenção em partes da cena com objetos complexos, efeitos de partícula ou atividade.</span><span class="sxs-lookup"><span data-stu-id="51469-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="51469-113">Esses e outros fatores geralmente contribuem para a redução no desempenho do aplicativo e uma experiência de usuário menor do que a ideal.</span><span class="sxs-lookup"><span data-stu-id="51469-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="51469-114">Interface do profiler visual</span><span class="sxs-lookup"><span data-stu-id="51469-114">Visual profiler interface</span></span>

![Visual Profiler Interface](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="51469-116">A interface do Visual Profiler inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="51469-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="51469-117">Taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="51469-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="51469-118">Tempo do quadro</span><span class="sxs-lookup"><span data-stu-id="51469-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="51469-119">Gráfico de quadros</span><span class="sxs-lookup"><span data-stu-id="51469-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="51469-120">Utilização de Memória</span><span class="sxs-lookup"><span data-stu-id="51469-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="51469-121">Taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="51469-121">Frame rate</span></span>

<span data-ttu-id="51469-122">No canto superior esquerdo da interface está a taxa de quadros, medida em quadros por segundo.</span><span class="sxs-lookup"><span data-stu-id="51469-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="51469-123">Para a melhor experiência e conforto do usuário, esse valor deve ser o mais alto possível.</span><span class="sxs-lookup"><span data-stu-id="51469-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="51469-124">A configuração específica de plataforma e hardware desempenhará uma função significativa na taxa máxima de quadros que pode ser alcançada.</span><span class="sxs-lookup"><span data-stu-id="51469-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="51469-125">Alguns valores de destino comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="51469-125">Some common target values include:</span></span>

- <span data-ttu-id="51469-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="51469-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="51469-127">Windows Mixed Reality Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="51469-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="51469-128">Devido à reação da taxa de quadros no [HoloLens](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)quando o MRC padrão está ativo, o profiler visual se oculta enquanto vídeos e fotos são capturados.</span><span class="sxs-lookup"><span data-stu-id="51469-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="51469-129">Essa configuração pode ser substituído no perfil do sistema de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="51469-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="51469-130">Tempo do quadro</span><span class="sxs-lookup"><span data-stu-id="51469-130">Frame time</span></span>

<span data-ttu-id="51469-131">À direita da taxa de quadros está o tempo do quadro, em milissegundos, gasto na CPU.</span><span class="sxs-lookup"><span data-stu-id="51469-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="51469-132">Para atingir as taxas de quadros de destino mencionadas anteriormente, um aplicativo pode gastar a seguinte quantidade de tempo por quadro:</span><span class="sxs-lookup"><span data-stu-id="51469-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="51469-133">60 fps: 16,6 ms</span><span class="sxs-lookup"><span data-stu-id="51469-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="51469-134">90 fps: 11,1 ms</span><span class="sxs-lookup"><span data-stu-id="51469-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="51469-135">O tempo de GPU está planejado para ser adicionado em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="51469-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="51469-136">Grafo de quadro</span><span class="sxs-lookup"><span data-stu-id="51469-136">Frame graph</span></span>

<span data-ttu-id="51469-137">O gráfico de quadros fornece uma exibição gráfica do histórico de taxa de quadros do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51469-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Grafo de Quadro Perdido do Visual Profiler](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="51469-139">Ao usar o aplicativo, procure quadros que indicam que o aplicativo não está atingindo sua taxa de quadros de destino e pode precisar de trabalho de otimização.</span><span class="sxs-lookup"><span data-stu-id="51469-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="51469-140">Utilização da memória</span><span class="sxs-lookup"><span data-stu-id="51469-140">Memory utilization</span></span>

<span data-ttu-id="51469-141">A exibição de utilização de memória permite uma compreensão fácil de como a exibição atual está afetando o consumo de memória de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51469-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Visual Profiler Memory Graph](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="51469-143">Ao usar o aplicativo, procure o uso total de memória.</span><span class="sxs-lookup"><span data-stu-id="51469-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="51469-144">Os indicadores-chave incluem a proximidade do limite de memória e as alterações rápidas no uso.</span><span class="sxs-lookup"><span data-stu-id="51469-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="51469-145">Personalização do profiler visual</span><span class="sxs-lookup"><span data-stu-id="51469-145">Customizing the visual profiler</span></span>

<span data-ttu-id="51469-146">A aparência e o comportamento do Visual Profiler são personalizáveis por meio do perfil do sistema de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="51469-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="51469-147">Confira [Configurando o sistema de diagnóstico para](configuring-diagnostics.md) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="51469-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="51469-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="51469-148">See also</span></span>

- [<span data-ttu-id="51469-149">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="51469-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="51469-150">Configurando o sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="51469-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)