---
title: Visualização de ponta do dedo
description: Visão geral sobre a visualização de mãos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, ponta
ms.openlocfilehash: 1df1740692a2c24213f34ffa6e52c135c7e7d14f96e7d99668feab82f879f756
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193279"
---
# <a name="fingertip-visualization"></a>Visualização de ponta do dedo

![Main visualização principal](../images/fingertip/MRTK_FingertipVisualization_Main.png)

O direcionamento para a mão ajuda o usuário a reconhecer a distância do objeto de destino. O Visual forma de anel ajusta seu tamanho com base na distância do alcance até o objeto. A visualização de ponta é controlada principalmente pelo `FingerCursor` (assets/MRTK/SDK/Features/UX/pré-fabricados/Cursors/FingerCursor. pré-fabricado) (e script) que é gerado como o cursor pré-fabricado do *PokePointer*. Outros componentes da visualização incluem o script *ProximityLight* e o sombreador *MixedRealityStandard* .

## <a name="how-to-use-the-fingertip-visualization"></a>Como usar a visualização de mãos

Por padrão, a visualização de mãos funcionará em qualquer cena de Unity configurada para gerar um FingerCursor. A geração de FingerCursor ocorre no *DefaultMixedRealityToolkitConfigurationProfile* em:

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

Em um alto nível, a visualização de ponta funciona usando uma luz de proximidade para projetar um gradiente colorido em quaisquer superfícies vizinhas que aceitem luzes de proximidade. Em seguida, o cursor Finger procura por quaisquer superfícies interajantes próximas, que são determinadas pelo pai `IMixedRealityNearPointer(s)` , para alinhar o anel de dedo com uma superfície à medida que o dedo se move para uma superfície. Como um dedo se aproxima de uma superfície, o anel de dedo também é animado dinamicamente usando as propriedades do canto redondo do sombreador MixedRealityStandard.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos de visualização de ponta em quase qualquer cena que funcione com as mãos articuladas, mas é proeminente na [cena HandInteractionExample](../example-scenes/hand-interaction-examples.md).

![Estados de visualização de mãos](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Propriedades do Inspetor

**FingerCursor** Muitas das propriedades do cursor Finger são herdadas da classe de cursor base. As propriedades importantes incluem as margens de superfície distante/próxima e as larguras que orientam a animação de anel de dedo no sombreador MixedRealityStandard. Para outras propriedades, passe o mouse sobre as dicas de ferramenta do Inspetor.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** As configurações de luz de proximidade controlam a aparência da luz quando próxima e longe de uma superfície. As cores central, intermediária e externa controlam a aparência da luz do gradiente e podem ser personalizadas adaptadas para a paleta de cores do seu aplicativo. Observe que as cores são HDR (alto intervalo dinâmico) para permitir que os usuários claream a luz de proximidade para valores acima de um. Para outras propriedades, passe o mouse sobre as dicas de ferramenta do Inspetor.

**Sombreador MixedRealityStandard** O sombreador MixedRealityStandard é usado para muitos efeitos no MRTK. As duas configurações importantes para a visualização de mãos são "perto de desaparecer" e "luz de proximidade". Perto de desaparecer permite que os objetos apareçam/saem em uma câmera ou uma luz perto deles. Certifique-se de verificar "Light" para permitir que as luzes de proximidade conduzam o esmaecimento (em vez da câmera). Você pode reverter os valores de "Fade Begin" e "esmaecimento concluído" para reverter um esmaecimento. Marque "luz de proximidade" para qualquer superfície que você gostaria que a luz de proximidade clareasse. Para outras propriedades, passe o mouse sobre as dicas de ferramenta do Inspetor.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
