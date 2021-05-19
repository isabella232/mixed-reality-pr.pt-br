---
title: Ferramenta de uso de recursos de entrada
description: Entrada da documentaçãoA ferramenta InputFeatureUsage no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145013"
---
# <a name="inputfeatureusage-tool"></a>Ferramenta InputFeatureUsage

A ferramenta InputFeatureUsage é uma ferramenta de runtime (no dispositivo ou no editor) que permite aos desenvolvedores determinar rapidamente a InputFeatureUsages do Unity disponível para uma fonte de entrada detectada (por exemplo: controlador de movimento ou mão articulada).

> [!NOTE]
> Essa cena só funciona no Unity 2019.3 ou posterior.

Essa ferramenta é muito útil ao desenvolver suporte para um novo controlador de hardware. Ele também pode ajudar a confirmar um problema de mapeamento de controle suspeito na classe de suporte para um controlador existente.

![Ferramenta InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Usando a ferramenta InputFeatureUsage

Para começar com a ferramenta InputFeatureUsage, navegue até **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** e abra a cena **InputFeatureUsageTool.** Depois que a cena tiver sido carregada, o projeto poderá ser executado no editor, usando o modo de reprodução ou criado e executado em um dispositivo.

Para examinar os mapeamentos do Unity para um controlador:

- Conectar o controlador
- Pressione cada botão e mova cada eixo
- Observe os usos de recursos na exibição
- Atualizar os mapeamentos de controle no provedor de dados do sistema de entrada para o controlador

> [!NOTE]
> A ferramenta InputFeatureUsage não usa componentes do Microsoft Mixed Reality Toolkit. Ele se comunica diretamente com o Unity para determinar e exibir os usos de recursos.

### <a name="panels"></a>Painéis

Os painéis exibem o estado atual de todas as InputFeatureUsages relatadas em todas as fontes de entrada do Unity detectadas.

O painel menor na parte superior lista os nomes de todas as fontes detectadas.

## <a name="see-also"></a>Confira também

- [Criando um provedor de dados do sistema de entrada](../input/create-data-provider.md)
- [Ferramenta de mapeamento de controlador](controller-mapping-tool.md)
