---
title: Configurando o sistema de diagnóstico
description: Documentação para configurar o diagnóstico no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: d81b441cd9bcd40846eb94320f6f7de1bbd2f0a8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177251"
---
# <a name="configuring-the-diagnostics-system"></a>Configurando o sistema de diagnóstico

## <a name="general-settings"></a>Configurações gerais

![diagnóstico geral Configurações](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>Habilitar o log detalhado

Indica se o log de MRTK detalhado será habilitado ou não. Esse padrão é false, mas pode ser ativado para fazer rastreamentos detalhados que permitem que a equipe de MRTK depure/aprofunde os problemas. Por exemplo, ao arquivar um problema, anexar os logs do Player do Unity (do editor ou do Player) pode ajudar a restringir a origem de bugs e problemas.

Observe que essa opção é independente de o sistema de diagnóstico estar habilitado ou não, que aparece no sistema de diagnóstico porque é uma opção de log, mas, por fim, opera em um nível mais alto, pois afeta o registro em log em toda a base de código MRTK.

### <a name="show-diagnostics"></a>Mostrar diagnósticos

Indica se o sistema de diagnóstico deve ou não exibir as opções de diagnóstico configuradas.

Quando desabilitado, todas as opções de diagnóstico configuradas serão ocultas.

## <a name="profiler-settings"></a>Configurações do criador de perfil

![Configurações do criador de perfil de diagnóstico](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>Mostrar criador de perfil

Indica se o criador de perfil do Visual deve ser exibido ou não.

### <a name="frame-sample-rate"></a>Taxa de amostra de quadro

A quantidade de tempo, em segundos, para coletar quadros para cálculo de taxa de quadros. O intervalo é de 0 a 5 segundos.

### <a name="window-anchor"></a>Âncora de janela

Para qual parte da porta de exibição a janela do criador de perfil deve ser ancorada. O valor padrão é inferior centro.

### <a name="window-offset"></a>Deslocamento da janela

O deslocamento, do centro da porta de exibição, para posicionar o Visual Profiler. O deslocamento estará na direção da propriedade âncora da *janela* .

### <a name="window-scale"></a>Escala da janela

Multiplicador de tamanho aplicado à janela do criador de perfil. Por exemplo, definir o valor como 2 dobrará o tamanho da janela.

### <a name="window-follow-speed"></a>Velocidade da janela

A velocidade na qual mover a janela do criador de perfil para manter a visibilidade dentro da porta de exibição.

## <a name="programmatically-controlling-the-diagnostics-system"></a>Controlando programaticamente o sistema de diagnóstico

Também é possível alternar a visibilidade do sistema de diagnóstico e o criador de perfil em tempo de execução. Por exemplo, o código a seguir ocultará o sistema de diagnóstico e o criador de perfil.

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>Confira também

- [Sistema de diagnóstico](diagnostics-system-getting-started.md)
- [Usando o criador de perfil Visual](using-visual-profiler.md)
