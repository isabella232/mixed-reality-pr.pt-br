---
title: Pesquisa
description: Interação de duração
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Pesquisa, Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647737"
---
# <a name="dwell"></a>Pesquisa

![Herói de pesquisa](../images/dwell/MRTK_UX_Dwell.png)

O Head-olhar e a pesquisa são ótimos em cenários nos quais as mãos de uma pessoa estão ocupadas com outras tarefas. O recurso também é útil quando a voz não é 100% confiável ou está disponível devido a restrições de ambiente ou sociais.
Os exemplos de pesquisa de MRTK demonstram tipos diferentes de componentes de interface do usuário com tempo de resposta configurável e comentários visuais.

Consulte a página de [diretrizes Head-olhar e de duração](/windows/mixed-reality/design/gaze-and-dwell-head) para obter as recomendações de design.

## <a name="dwell-scripts"></a>Scripts de duração

- **DwellHandler**: adiciona uma modalidade de pesquisa ao destino da interface do usuário.
- **DwellStateType**: os Estados do manipulador de duração.
- Evento **DwellUnityEvent**: Unity para um evento de duração de pesquisa. Contém a referência do ponteiro.
- **BaseDwellPressableButton. cs** : um script que dispara o evento OnClick () em `Interactable` PressableButtonHoloLens2 pré-fabricados.
- **ToggleDwellPressableButton. cs** : esse script modifica `_BorderWidth` a propriedade do `dwellVisualImage` que está usando o sombreador padrão do MRTK.

## <a name="dwell-profiles"></a>Perfis de duração
Os perfis de duração são usados pelo **manipulador de duração** para configurar os vários limites.
- **ButtonDwellProfile. Asset**
- **InstandDwellProfile. Asset**
- **DwellProfileWithDecay. Asset**

## <a name="prefabs"></a>Pré-fabricados

Esses pré-fabricados são variantes do pré-fabricados de botão pressionável de estilo do HoloLens 2 que têm componentes adicionais para dar suporte a interações de duração de pesquisa.

- **PressableButtonHoloLens2_Dwell. pré-fabricado**
- **PressableButtonHoloLens2_32x96_Dwell. pré-fabricado**
- **PressableButtonHoloLens2ToggleDwell. pré-fabricado**
- **PressableButtonHoloLens2Toggle_32x96_Dwell. pré-fabricado**

Esses pré-fabricados têm um componente de placa traseira adicional **QuadDwellVisual** para visualizar o estado de entrada de duração. Ele tem o material **HolographicBackPlateDwellVisual. enquadrable** atribuído. **ToggleDwellPressableButton. cs** atualiza a propriedade **_BorderWidth** do sombreador padrão MRTK para visualizar a entrada de duração da pesquisa.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos na `DwellExample` cena. A cena de exemplo mostra os exemplos de interface do usuário do volumétricos e exemplos da interface do usuário do Unity

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>Confira também

- [**Botões**](button.md)
- [**Interativo**](interactable.md)
