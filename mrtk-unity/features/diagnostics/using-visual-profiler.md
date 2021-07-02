---
title: Usando o profiler visual
description: documentação para usar o Visual Profiler no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 018d6bf2087b73697a1e1f43e206c96ae25e1f21
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177224"
---
# <a name="using-the-visual-profiler"></a>Usando o profiler visual

O VisualProfiler fornece uma exibição fácil de usar no aplicativo do desempenho de um aplicativo de realidade misturada. O profiler tem suporte em todas as plataformas de Toolkit realidade misturada, incluindo:

- Microsoft HoloLens (1ª geração)
- Microsoft HoloLens 2
- Headsets imersivos do Windows Mixed Reality
- OpenVR

Ao desenvolver um aplicativo, concentre-se em várias partes da cena, pois o Visual Profiler exibe dados relativos à exibição atual.

> [!IMPORTANT]
> Concentre a atenção em partes da cena com objetos complexos, efeitos de partícula ou atividade. Esses e outros fatores geralmente contribuem para a redução no desempenho do aplicativo e uma experiência de usuário menor do que a ideal.

## <a name="visual-profiler-interface"></a>Interface do profiler visual

![Visual Profiler Interface](../images/diagnostics/VisualProfiler.png)

A interface do Visual Profiler inclui os seguintes componentes:

- [Taxa de quadros](#frame-rate)
- [Tempo do quadro](#frame-time)
- [Estrutura Graph](#frame-graph)
- [Utilização de Memória](#memory-utilization)

### <a name="frame-rate"></a>Taxa de quadros

No canto superior esquerdo da interface está a taxa de quadros, medida em quadros por segundo. Para a melhor experiência e conforto do usuário, esse valor deve ser o mais alto possível.

A configuração específica de plataforma e hardware desempenhará uma função significativa na taxa máxima de quadros que pode ser alcançada. Alguns valores de destino comuns incluem:

- Microsoft HoloLens: 60
- Windows Mixed Reality Ultra: 90

> [!NOTE]
> Devido à taxa de quadros que está HoloLens quando o [MRC](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)padrão está ativo, o profiler visual se oculta enquanto vídeos e fotos são capturados. Essa configuração pode ser substituído no perfil do sistema de diagnóstico.

### <a name="frame-time"></a>Tempo do quadro

À direita da taxa de quadros está o tempo do quadro, em milissegundos, gasto na CPU. Para atingir as taxas de quadros de destino mencionadas anteriormente, um aplicativo pode gastar a seguinte quantidade de tempo por quadro:

- 60 fps: 16,6 ms
- 90 fps: 11,1 ms

O tempo de GPU está planejado para ser adicionado em uma versão futura.

### <a name="frame-graph"></a>Grafo de quadro

O gráfico de quadros fornece uma exibição gráfica do histórico de taxa de quadros do aplicativo.

![Registro de quadro perdido do Visual Profiler Graph](../images/diagnostics/VisualProfilerMissedFrames.png)

Ao usar o aplicativo, procure quadros que indicam que o aplicativo não está atingindo sua taxa de quadros de destino e pode precisar de trabalho de otimização.

### <a name="memory-utilization"></a>Utilização da memória

A exibição de utilização de memória permite uma compreensão fácil de como a exibição atual está afetando o consumo de memória de um aplicativo.

![Visual Profiler Memory Graph](../images/diagnostics/VisualProfilerMemory.png)

Ao usar o aplicativo, procure o uso total de memória. Os indicadores-chave incluem a proximidade do limite de memória e as alterações rápidas no uso.

## <a name="customizing-the-visual-profiler"></a>Personalização do profiler visual

A aparência e o comportamento do Visual Profiler são personalizáveis por meio do perfil do sistema de diagnóstico. Confira [Configurando o sistema de diagnóstico para](configuring-diagnostics.md) obter mais informações.

## <a name="see-also"></a>Confira também

- [Sistema de diagnóstico](diagnostics-system-getting-started.md)
- [Configurando o sistema de diagnóstico](configuring-diagnostics.md)
