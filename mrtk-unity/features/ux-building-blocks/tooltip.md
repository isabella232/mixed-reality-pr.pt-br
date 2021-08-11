---
title: Dica de ferramenta
description: Visão geral da dica de ferramenta no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, dica de ferramenta,
ms.openlocfilehash: af848db0962948b1f2ada73066c4ae90730b09a99dea231ebf468a05441b85ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193238"
---
# <a name="tooltip"></a>Dica de ferramenta

![Dica de ferramenta principal](../images/tooltip/MRTK_Tooltip_Main.png)

As dicas de ferramenta geralmente são usadas para transmitir uma dica ou informações extras sobre a inspeção mais detalhada de um objeto. Dicas de ferramenta podem ser usadas para anotar objetos no ambiente físico.

## <a name="how-to-use-a-tooltip"></a>Como usar uma dica de ferramenta

Uma dica de ferramenta pode ser adicionada diretamente à hierarquia e direcionada a um objeto.

Para usar esse método, basta adicionar um objeto de jogo e uma das dicas de ferramenta pré-fabricados (ativos/MRTK/SDK/recursos/UX/pré-fabricados/tooltips) à hierarquia de cena. No painel Inspetor do pré-fabricado, expanda o [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) script. Selecione um estado Tip e configure a dica de ferramenta.  Insira o respectivo texto para a dica de ferramenta no campo de texto. Expanda o [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) script e arraste o objeto que deve ter a dica de ferramenta da hierarquia para o campo rotulado como *destino*. Isso anexa a dica de ferramenta ao objeto.
![Conector de dica de ferramenta](../images/tooltip/MRTK_Tooltip_Connector.png)

Esse uso pressupõe uma dica de ferramenta que sempre está sendo exibida ou que é mostrada/ocultada por meio de script, alterando a propriedade de estado da dica de ferramenta do componente ToolTip.

## <a name="dynamically-spawning-tooltips"></a>Dicas de ferramentas de geração dinâmica

Uma dica de ferramenta pode ser adicionada dinamicamente a um objeto em tempo de execução, bem como predefinida para mostrar e ocultar em um toque ou foco. Basta adicionar o [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) script a qualquer objeto de jogo. Os atrasos para aparecer e desaparecimento podem ser definidos no Inspetor de scripts, bem como um tempo de vida para que a dica de ferramenta desapareça após uma duração definida. As dicas de ferramenta também apresentam propriedades de estilo como visuais de segundo plano no script de geração. Por padrão, a dica de ferramenta será ancorada ao objeto com o script de gerador. Isso pode ser alterado atribuindo um gameobject ao campo de âncora.

## <a name="example-scene"></a>Cena de exemplo

Nos bastidores de exemplo (ativos/MRTK/exemplos/demonstrações/UX/tooltips/cenas), você poderá encontrar vários exemplos de dicas de ferramenta.

![Exemplos de dica de ferramenta](../images/tooltip/MRTK_Tooltip_Examples.png)
