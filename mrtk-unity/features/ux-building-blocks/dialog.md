---
title: caixa de diálogo
description: Descrição para controles de caixa de diálogo.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489186"
---
# <a name="dialog"></a>caixa de diálogo

![caixa de diálogo](../images/dialog/MRTK_UX_Dialog_Main.png)

Controles de caixa de diálogo são sobreposições de interface do usuário que fornecem informações contextuais do aplicativo. Elas muitas vezes solicitam algum tipo de ação do usuário. Use caixas de diálogo para notificar os usuários sobre informações importantes, ou para solicitar a confirmação ou informações adicionais antes de uma ação ser concluída.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos na cena **DialogExample** em: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>Como usar o controle Dialog

O MRTK fornece três pré-requisitos de caixa de diálogo:

- DialogSmall_192x96.prefab
- DialogMedium_192x128.prefab
- DialogLarge_192x192.prefab

Use Dialog.Open() para abrir uma nova caixa de diálogo. Especifique o pré-fab da caixa de diálogo, o número de botões, o texto do título, o texto da mensagem, a distância do posicionamento (próximo ou distante), variáveis adicionais. A caixa de diálogo fornece as opções de caixa de diálogo 'Confirmação(botão único)' e 'Escolha(dois botões)'.

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Exemplo de abertura de uma caixa de diálogo Grande com um único botão 'OK', colocado no intervalo de interação distante (olhar, raio de mão, controlador de movimento)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>Exemplo de abertura de uma caixa de diálogo Pequena que contém uma mensagem de escolha para o usuário, colocada no intervalo de interação próxima (interação direta à mão)

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Para obter mais detalhes, confira `DialogExampleController.cs` a cena DialogExample.unity.
