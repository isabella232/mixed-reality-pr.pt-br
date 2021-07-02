---
title: Visão geral do sistema de diagnóstico
description: Documentação para habilitar e desabilitar o diagnóstico no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: a31b88f661c141941cae2d0b01668b26c0bed7d7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177241"
---
# <a name="diagnostics-system-overview"></a>Visão geral do sistema de diagnóstico

O Sistema de Diagnóstico Toolkit Mixed Reality fornece ferramentas de diagnóstico que são executados dentro do aplicativo para habilitar a análise de problemas do aplicativo.

A primeira versão do Sistema de Diagnóstico contém o [Visual Profiler](using-visual-profiler.md) para permitir a análise de problemas de desempenho ao usar o aplicativo.

## <a name="getting-started"></a>Introdução

> [!IMPORTANT]
> É altamente **_recomendável_** que o Sistema de Diagnóstico seja habilitado em todo o ciclo de desenvolvimento do produto e desabilitado como a última alteração antes de criar e liberar a versão final.

Há duas etapas principais para começar a usar o Sistema de Diagnóstico.

1. [Habilitar](#enable-diagnostics) o sistema de diagnóstico
2. [Configurar opções](#configure-diagnostic-options) de diagnóstico

### <a name="enable-diagnostics"></a>Habilitar diagnósticos

O sistema de diagnóstico é gerenciado pelo objeto MixedRealityToolkit (ou outro [componente do registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) serviços).

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Navegue pelo painel Inspetor até a seção Sistema de Diagnóstico e marque Habilitar
1. Selecione a implementação do Sistema de Diagnóstico

    ![Selecione a implementação do sistema de diagnóstico](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> Os usuários do perfil padrão, `DefaultMixedRealityToolkitConfigurationProfile` (Ativos/MRTK/SDK/Perfis), terão o sistema de diagnóstico pré-configurado para usar o [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) objeto .

### <a name="configure-diagnostic-options"></a>Configurar opções de diagnóstico

O sistema de diagnóstico usa um perfil de configuração para especificar quais componentes devem ser exibidos e definir suas configurações. Consulte [Configurando o sistema de diagnóstico para](configuring-diagnostics.md) obter mais informações referentes às configurações de componente disponíveis.

> [!IMPORTANT]
> Embora seja possível usar o Modo de Reprodução do Unity ao desenvolver aplicativos sem exigir as etapas de build e implantação, é importante avaliar os resultados do sistema de diagnóstico usando um aplicativo compilado em execução no hardware e na plataforma de destino.
>
> O diagnóstico de desempenho, como o [Visual Profiler,](using-visual-profiler.md)pode não refletir com precisão o desempenho real do aplicativo quando executado de dentro do editor.

## <a name="see-also"></a>Confira também

- [Documentação da API de Diagnóstico](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Configurando o sistema de diagnóstico](configuring-diagnostics.md)
- [Usando o Visual Profiler](using-visual-profiler.md)
