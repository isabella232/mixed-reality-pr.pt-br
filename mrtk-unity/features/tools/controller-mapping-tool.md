---
title: Ferramenta de mapeamento de controlador
description: Documentação sobre a ferramenta de mapeamento do controlador no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f00dc01555ef158dab21334761bd23ef6a70dba4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144081"
---
# <a name="controller-mapping-tool"></a>Ferramenta de mapeamento de controlador

A ferramenta de mapeamento de controlador é uma ferramenta de tempo de execução (no dispositivo ou na editor) que permite aos desenvolvedores determinar rapidamente o eixo de entrada do Unity e os mapeamentos de botão para um controlador de hardware (por exemplo: controlador de movimento).

Essa ferramenta é muito útil ao desenvolver suporte para um novo controlador de hardware. Ele também pode ajudar a confirmar um problema de mapeamento de controle suspeito na classe de suporte para um controlador existente.

![Ferramenta de mapeamento de controlador](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Usando a ferramenta de mapeamento de controlador

Para começar a usar a ferramenta de mapeamento de controlador, navegue até **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** e abra a cena **ControllerMappingTool** . Depois que a cena for carregada, o projeto poderá ser executado no editor, usando o modo de reprodução ou compilado e executado em um dispositivo.

Para examinar os mapeamentos do Unity para um controlador:

- Conectar o controlador
- Pressione cada botão e mova cada eixo
- Observe os mapeamentos na exibição
- Atualizar os mapeamentos de controle no provedor de dados do sistema de entrada para o controlador

> [!NOTE]
> A ferramenta de mapeamento de controlador não faz uso dos componentes do kit de ferramentas do Microsoft Mixed Reality. Ele se comunica diretamente com o Unity para determinar e exibir os mapeamentos de controle.

### <a name="all-controls-display"></a>Todos os controles são exibidos

O painel de exibição grande relata o estado de todos os eixos de entrada e botões de Unity definidos (por exemplo: eixo 10, botão 3). Esse painel fornece uma exibição completa do estado do controlador.

![Todos os controles são exibidos](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Exibição de controles ativos

O painel de exibição menor e estreito mostra o eixo de entrada do Unity e os botões que estão em um estado ativo (por exemplo: um botão é pressionado). A exibição de controles ativos fornece uma exibição resumida fácil de ler do estado do controlador.

![Exibição de controles ativos](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Confira também

- [Criando um provedor de dados do sistema de entrada](../input/create-data-provider.md)
- [Ferramenta InputFeatureUsage](input-feature-usage-tool.md)
