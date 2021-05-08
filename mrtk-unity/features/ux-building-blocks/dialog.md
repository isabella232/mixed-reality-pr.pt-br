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
# <a name="dialog"></a><span data-ttu-id="78025-104">caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="78025-104">Dialog</span></span>

![caixa de diálogo](../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="78025-106">Controles de caixa de diálogo são sobreposições de interface do usuário que fornecem informações contextuais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="78025-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="78025-107">Elas muitas vezes solicitam algum tipo de ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="78025-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="78025-108">Use caixas de diálogo para notificar os usuários sobre informações importantes, ou para solicitar a confirmação ou informações adicionais antes de uma ação ser concluída.</span><span class="sxs-lookup"><span data-stu-id="78025-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="78025-109">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="78025-109">Example scene</span></span>

<span data-ttu-id="78025-110">Você pode encontrar exemplos na cena **DialogExample** em: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span><span class="sxs-lookup"><span data-stu-id="78025-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="78025-111">Como usar o controle Dialog</span><span class="sxs-lookup"><span data-stu-id="78025-111">How to use Dialog control</span></span>

<span data-ttu-id="78025-112">O MRTK fornece três pré-requisitos de caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="78025-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="78025-113">DialogSmall_192x96.prefab</span><span class="sxs-lookup"><span data-stu-id="78025-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="78025-114">DialogMedium_192x128.prefab</span><span class="sxs-lookup"><span data-stu-id="78025-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="78025-115">DialogLarge_192x192.prefab</span><span class="sxs-lookup"><span data-stu-id="78025-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="78025-116">Use Dialog.Open() para abrir uma nova caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="78025-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="78025-117">Especifique o pré-fab da caixa de diálogo, o número de botões, o texto do título, o texto da mensagem, a distância do posicionamento (próximo ou distante), variáveis adicionais.</span><span class="sxs-lookup"><span data-stu-id="78025-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="78025-118">A caixa de diálogo fornece as opções de caixa de diálogo 'Confirmação(botão único)' e 'Escolha(dois botões)'.</span><span class="sxs-lookup"><span data-stu-id="78025-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="78025-119">Exemplo de abertura de uma caixa de diálogo Grande com um único botão 'OK', colocado no intervalo de interação distante (olhar, raio de mão, controlador de movimento)</span><span class="sxs-lookup"><span data-stu-id="78025-119">Example of opening a Large dialog with a single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="78025-120">Exemplo de abertura de uma caixa de diálogo Pequena que contém uma mensagem de escolha para o usuário, colocada no intervalo de interação próxima (interação direta à mão)</span><span class="sxs-lookup"><span data-stu-id="78025-120">Example of opening a Small dialog containing a choice message for the user, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="78025-121">Para obter mais detalhes, confira `DialogExampleController.cs` a cena DialogExample.unity.</span><span class="sxs-lookup"><span data-stu-id="78025-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>
