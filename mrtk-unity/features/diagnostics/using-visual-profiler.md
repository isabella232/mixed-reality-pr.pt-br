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
# <a name="using-the-visual-profiler"></a>Usando o profiler visual

O VisualProfiler fornece uma exibição fácil de usar no aplicativo do desempenho de um aplicativo de realidade misturada. O profiler tem suporte em todas as plataformas do Kit de Ferramentas de Realidade Misturada, incluindo:

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
- [Gráfico de quadros](#frame-graph)
- [Utilização de memória](#memory-utilization)

### <a name="frame-rate"></a>Taxa de quadros

No canto superior esquerdo da interface está a taxa de quadros, medida em quadros por segundo. Para a melhor experiência e conforto do usuário, esse valor deve ser o mais alto possível.

A configuração específica de plataforma e hardware desempenhará uma função significativa na taxa máxima de quadros que pode ser alcançada. Alguns valores de destino comuns incluem:

- Microsoft HoloLens: 60
- Realidade mista do Windows ultra: 90

> [!NOTE]
> Devido à [limitação da taxa de quadros no HoloLens quando a MRC padrão está ativa](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), o criador de perfil Visual se oculta enquanto vídeos e fotos são capturados. Essa configuração pode ser substituída no perfil do sistema de diagnóstico.

### <a name="frame-time"></a>Hora do quadro

À direita da taxa de quadros está o tempo de quadro, em milissegundos, gasto na CPU. Para atingir as taxas de quadros de destino mencionadas anteriormente, um aplicativo pode gastar o seguinte período de tempo por quadro:

- 60 fps: 16,6 ms
- 90 FPS: 11,1 MS

A hora da GPU está planejada para ser adicionada em uma versão futura.

### <a name="frame-graph"></a>Gráfico de quadro

O gráfico de quadros fornece uma exibição gráfica do histórico de taxa de quadros do aplicativo.

![Grafo de quadro perdido do criador de perfil do Visual](../images/diagnostics/VisualProfilerMissedFrames.png)

Ao usar o aplicativo, procure quadros perdidos que indiquem que o aplicativo não está atingindo sua taxa de quadros de destino e pode precisar de trabalho de otimização.

### <a name="memory-utilization"></a>Utilização da memória

A exibição de utilização de memória permite uma compreensão fácil de como a exibição atual está afetando o consumo de memória de um aplicativo.

![Grafo de memória do criador de perfil do Visual](../images/diagnostics/VisualProfilerMemory.png)

Ao usar o aplicativo, procure o uso de memória total. Os principais indicadores incluem a proximidade do limite de memória e as alterações rápidas no uso.

## <a name="customizing-the-visual-profiler"></a>Personalizando o criador de perfil Visual

A aparência e o comportamento do criador de perfil do Visual são personalizáveis por meio do perfil do sistema de diagnóstico. Consulte [Configurando o sistema de diagnóstico](configuring-diagnostics.md) para obter mais informações.

## <a name="see-also"></a>Confira também

- [Sistema de diagnóstico](diagnostics-system-getting-started.md)
- [Configurando o sistema de diagnóstico](configuring-diagnostics.md)