---
title: Visão geral do sistema de diagnóstico
description: Documentação para habilitar e desabilitar o diagnóstico no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0de7b904a48453d6021cf7aed5835412c19b7884
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121774"
---
# <a name="diagnostic-system"></a>Sistema de diagnóstico

O sistema de diagnóstico do kit de ferramentas de realidade misturada fornece ferramentas de diagnóstico que são executadas dentro do aplicativo para habilitar a análise de problemas de aplicativos.

A primeira versão do sistema de diagnóstico contém o [criador de perfil do Visual](using-visual-profiler.md) para permitir a análise de problemas de desempenho durante o uso do aplicativo.

## <a name="getting-started"></a>Introdução

> [!IMPORTANT]
> É **_altamente_** recomendável que o sistema de diagnóstico seja habilitado durante todo o ciclo de desenvolvimento do produto e seja desabilitado como a última alteração antes de compilar e liberar a versão final.

Há duas etapas principais para começar a usar o sistema de diagnóstico.

1. [Habilitar](#enable-diagnostics) o sistema de diagnóstico
2. [Configurar](#configure-diagnostic-options) opções de diagnóstico

### <a name="enable-diagnostics"></a>Habilitar diagnósticos

O sistema de diagnóstico é gerenciado pelo objeto MixedRealityToolkit (ou outro componente [registrador de serviço](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![MRTK hierarquia de cena configurada](../images/MRTK_ConfiguredHierarchy.png)

1. Navegue pelo painel Inspetor até a seção sistema de diagnóstico e marque Habilitar
1. Selecionar a implementação do sistema de diagnóstico

    ![Selecionar a implementação do sistema de diagnóstico](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> Os usuários do perfil padrão `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles) terão o sistema de diagnóstico pré-configurado para usar o [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) objeto.

### <a name="configure-diagnostic-options"></a>Configurar opções de diagnóstico

O sistema de diagnóstico usa um perfil de configuração para especificar quais componentes devem ser exibidos e para definir suas configurações. Consulte [Configurando o sistema de diagnóstico](configuring-diagnostics.md) para obter mais informações referentes às configurações de componente disponíveis.

> [!IMPORTANT]
> Embora seja possível usar o modo de reprodução do Unity ao desenvolver aplicativos sem exigir as etapas de compilação e implantação, é importante avaliar os resultados do sistema de diagnóstico usando um aplicativo compilado em execução no hardware e na plataforma de destino.
>
> O diagnóstico de desempenho, como o [Visual Profiler](using-visual-profiler.md), pode não refletir com precisão o desempenho real do aplicativo quando executado de dentro do editor.

## <a name="see-also"></a>Confira também

- [Documentação da API de diagnóstico](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Configurando o sistema de diagnóstico](configuring-diagnostics.md)
- [Usando o criador de perfil Visual](using-visual-profiler.md)
