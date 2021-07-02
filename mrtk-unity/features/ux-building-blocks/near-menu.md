---
title: Menu próximo
description: Visão geral ao lado de tipos de menu no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Menu próximo,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175652"
---
# <a name="near-menu"></a>Menu próximo

![Menu próximo](../images/near-menu/MRTK_UX_NearMenu.png)

O menu Near é um controle UX que fornece uma coleção de botões ou outros componentes de interface do usuário. Ele está flutuando pelo corpo do usuário e facilmente acessível a qualquer momento. Como ele está acoplado livremente ao usuário, ele não perturba a interação do usuário com o conteúdo de destino. O usuário pode usar o botão ' fixar ' para bloquear/desbloquear o menu do mundo. O menu pode ser capturado e colocado em uma posição específica.

## <a name="interaction-behavior"></a>Comportamento de interação

- **Marcação**: o menu segue você e permanece dentro do intervalo de 30 60cm do usuário para as interações próximas.
- **PIN**: usando o botão ' fixar ', o menu pode ser bloqueado e liberado pelo mundo.
- **Pegar e mover**: o menu é sempre captado e móvel. Independentemente do estado anterior, o menu será fixado (bloqueado pelo mundo) quando capturado e liberado. Há indicações visuais para a área de captura. Eles são revelados à proximidade.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Pré-fabricados

O menu Near pré-fabricados foi projetado para demonstrar como usar os vários componentes do MRTK para criar menus para interações próximas.

- **NearMenu2x4. pré-fabricado**
- **NearMenu3x1. pré-fabricado**
- **NearMenu3x2. pré-fabricado**
- **NearMenu3x3. pré-fabricado**
- **NearMenu4x1. pré-fabricado**
- **NearMenu4x2. pré-fabricado**

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos de pré-fabricados de menu próximo na `NearMenuExamples` cena.

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>Estrutura

O menu Near pré-fabricados é feito com os seguintes componentes do MRTK.

- [**PressableButtonHoloLens2**](button.md) pré-fabricado
- [**Coleção de objetos de grade**](object-collection.md): layout de vários botões na grade
- [**Manipulador de manipulação**](manipulation-handler.md): Pegue e mova o menu
- [**RadialView Solver**](solvers/solver.md): Siga o comportamento (marcação)

![Menu Near pré-fabricado](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Como personalizar

**1. Adicionar/remover botões**

Em `ButtonCollection` objeto, adicione ou remova botões.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. atualizar a coleção de objetos de grade**

Clique `Update Collection` no botão no Inspetor do `ButtonCollection` objeto. O layout da grade será atualizado.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

Você pode configurar o número de linhas usando `Rows` a propriedade da coleção de objetos de grade.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. ajustar o tamanho da placa de cima**

Ajuste o tamanho do `Quad` objeto em `Backplate` . A largura e a altura da chapa de backdevem ser `0.032 * [Number of the buttons + 1]` . Por exemplo, se você tiver três botões x 2, a largura da chapa de backfica `0.032 * 4` e a altura será `0.032 * 3` . Você pode colocar essa expressão diretamente no campo do Unity.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- o tamanho padrão do botão HoloLens 2 é 3,2 x 3.2 cm (0.032 m)

## <a name="see-also"></a>Confira também

- [**Botões**](button.md)
- [**Controle de limites**](bounds-control.md)
- [**Controle deslizante**](sliders.md)
- [**Coleção de objetos de grade**](object-collection.md)
- [**Manipulador de manipulação**](manipulation-handler.md)
- [**Solucionador de RadialView**](solvers/solver.md)
