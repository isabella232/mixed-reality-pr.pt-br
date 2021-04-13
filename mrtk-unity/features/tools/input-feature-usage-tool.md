---
title: InputFeatureUsageTool
description: Ferramenta de InputFeatureUsage de documentação no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 35b28557df37abee19a0c950b362117eb6a120b0
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300191"
---
# <a name="inputfeatureusage-tool"></a>Ferramenta InputFeatureUsage

A ferramenta InputFeatureUsage é uma ferramenta de tempo de execução (no dispositivo ou na editor) que permite aos desenvolvedores determinar rapidamente o InputFeatureUsages do Unity disponível para uma fonte de entrada detectada (por exemplo: controlador de movimento ou mão articulada).

> [!NOTE]
> Essa cena funciona apenas no Unity 2019,3 ou posterior.

Essa ferramenta é muito útil ao desenvolver suporte para um novo controlador de hardware. Ele também pode ajudar a confirmar um problema de mapeamento de controle suspeito na classe de suporte para um controlador existente.

![Ferramenta InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Usando a ferramenta InputFeatureUsage

Para começar a usar a ferramenta InputFeatureUsage, navegue até **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** e abra a cena **InputFeatureUsageTool** . Depois que a cena for carregada, o projeto poderá ser executado no editor, usando o modo de reprodução ou compilado e executado em um dispositivo.

Para examinar os mapeamentos do Unity para um controlador:

- Conectar o controlador
- Pressione cada botão e mova cada eixo
- Observe os usos de recurso na exibição
- Atualizar os mapeamentos de controle no provedor de dados do sistema de entrada para o controlador

> [!NOTE]
> A ferramenta InputFeatureUsage não faz uso dos componentes do kit de ferramentas do Microsoft Mixed Reality. Ele se comunica diretamente com o Unity para determinar e exibir os usos de recursos.

### <a name="panels"></a>Painéis

Os painéis exibem o estado atual de todos os InputFeatureUsages relatados em todas as fontes de entrada do Unity detectadas.

O painel menor na parte superior lista os nomes de todas as fontes detectadas.

## <a name="see-also"></a>Confira também

- [Criando um provedor de dados do sistema de entrada](../input/create-data-provider.md)
- [Ferramenta de mapeamento de controlador](controller-mapping-tool.md)
