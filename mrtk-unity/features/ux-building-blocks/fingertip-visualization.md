---
title: Visualização do dedo
description: Visão geral sobre visualização de dica de dedo no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Ponta do Dedo
ms.openlocfilehash: af23fdb9b618e276b7442405e54b7dccd141e4ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177530"
---
# <a name="fingertip-visualization"></a>Visualização do dedo

![Visualização do dedo principal](../images/fingertip/MRTK_FingertipVisualization_Main.png)

A tecnologia de ponta do dedo ajuda o usuário a reconhecer a distância do objeto de destino. O visual de forma de anel ajusta seu tamanho com base na distância da ponta do dedo para o objeto. A visualização do dedo é controlada principalmente pelo `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (e script) que é gerado como o pré-fab do cursor *doPointer*. Outros componentes da visualização incluem o script *ProximityLight* e *o sombreador MixedRealityStandard.*

## <a name="how-to-use-the-fingertip-visualization"></a>Como usar a visualização da ponta do dedo

Por padrão, a visualização do dedo funcionará em qualquer cena do Unity configurada para gerar um FingerCursor. A geração do FingerCursor ocorre *no DefaultMixedRealityToolkitConfigurationProfile* em:

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > Pointer > FingerCursor*

Em um alto nível, a visualização do dedo funciona usando uma luz de proximidade para projetar um gradiente colorido em superfícies próximas que aceitam luzes de proximidade. Em seguida, o cursor do dedo procura superfícies interagindo próximas, que são determinadas pelo pai, para alinhar o anel do dedo com uma superfície à medida que o dedo se move para `IMixedRealityNearPointer(s)` uma superfície. À medida que um dedo se aproxima de uma superfície, o anel do dedo também é dinamicamente animado usando as propriedades de canto arredondado do sombreador MixedRealityStandard.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos de visualização de ponta do dedo em quase qualquer cena que funcione com mãos articuladas, mas é proeminente na [cena HandInteractionExample](../example-scenes/hand-interaction-examples.md).

![Estados de visualização da ponta do dedo](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Propriedades do inspetor

**FingerCursor** Muitas das propriedades do cursor de dedo são herdadas da classe de cursor base. Propriedades importantes incluem as margens e as larguras da superfície próxima/distante que impulsionam a animação do anel do dedo no sombreador MixedRealityStandard. Para outras propriedades, passe o mouse sobre as dicas de ferramenta do inspetor.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** As configurações de luz de proximidade controlam a aparência da luz quando próxima e distante de uma superfície. As cores central, intermediária e externa controlam a aparência gradiente da luz e podem ser personalizadas para a paleta de cores do seu aplicativo. Observe que as cores são HDR (Alto Alcance Dinâmico) para permitir que os usuários aumentem a luz de proximidade para valores acima de um. Para outras propriedades, passe o mouse sobre as dicas de ferramenta do inspetor.

**Sombreador MixedRealityStandard** O sombreador MixedRealityStandard é usado para muitos efeitos no MRTK. As duas configurações importantes para a visualização da ponta do dedo são "Near Fade" e "Luz de Proximidade". Near Fade permite que os objetos esmaeçam/se esmaeçam conforme uma câmera ou luz se aproxima deles. Certifique-se de verificar "Light" para permitir que as luzes de proximidade conduzam o esmaeçando (em vez da câmera). Você pode reverter os valores de "Fade Begin" e "Fade Complete" para reverter um esmaeçando. Verifique a "Luz de Proximidade" para qualquer superfície que você gostaria que a luz de proximidade fosse brilhante. Para outras propriedades, passe o mouse sobre as dicas de ferramenta do inspetor.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
