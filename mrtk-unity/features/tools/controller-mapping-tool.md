---
title: Ferramenta de mapeamento de controlador
description: Documentação sobre a ferramenta de mapeamento do controlador no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176176"
---
# <a name="controller-mapping-tool"></a>Ferramenta de mapeamento de controlador

A ferramenta de mapeamento de controlador é uma ferramenta de tempo de execução (no dispositivo ou na editor) que permite aos desenvolvedores determinar rapidamente o eixo de entrada do Unity e os mapeamentos de botão para um controlador de hardware (por exemplo: controlador de movimento).

Essa ferramenta é muito útil ao desenvolver suporte para um novo controlador de hardware. Ele também pode ajudar a confirmar um problema de mapeamento de controle suspeito na classe de suporte para um controlador existente.

![Ferramenta de mapeamento de controlador](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Usando a ferramenta de mapeamento de controlador

Para começar a usar a ferramenta de mapeamento de controlador, navegue até **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** e abra a cena **ControllerMappingTool** . Depois que a cena for carregada, o projeto poderá ser executado no editor, usando o modo de reprodução ou compilado e executado em um dispositivo.

Para examinar os mapeamentos do Unity para um controlador:

- Conexão controlador
- Pressione cada botão e mova cada eixo
- Observe os mapeamentos na exibição
- Atualizar os mapeamentos de controle no provedor de dados do sistema de entrada para o controlador

> [!NOTE]
> a ferramenta de mapeamento de controlador não faz uso do Microsoft Mixed reality Toolkit components. Ele se comunica diretamente com o Unity para determinar e exibir os mapeamentos de controle.

### <a name="all-controls-display"></a>Todos os controles são exibidos

O painel de exibição grande relata o estado de todos os eixos de entrada e botões de Unity definidos (por exemplo: eixo 10, botão 3). Esse painel fornece uma exibição completa do estado do controlador.

![Todos os controles são exibidos](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Exibição de controles ativos

O painel de exibição menor e estreito mostra o axed de entrada do Unity e os botões que estão em um estado ativo (por exemplo: um botão é pressionado). A exibição de controles ativos fornece uma exibição resumida fácil de ler do estado do controlador.

![Exibição de controles ativos](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Confira também

- [Criando um provedor de dados do sistema de entrada](../input/create-data-provider.md)
- [Ferramenta InputFeatureUsage](input-feature-usage-tool.md)
