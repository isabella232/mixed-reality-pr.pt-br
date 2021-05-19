---
title: Teclado de realidade misturada
description: descrição sobre Como usar o teclado de realidade misturada
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 9fa81db9a71f1d0ce32bdd80a123eb072fc26fc5
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143395"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="15ad1-104">Classes auxiliares de teclado do HoloLens e realidade misturada</span><span class="sxs-lookup"><span data-stu-id="15ad1-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="15ad1-105">O MRTK fornece vários componentes auxiliares experimentais para ajudar a iniciar e ler texto do [Teclado do Sistema.](../ux-building-blocks/system-keyboard.md)</span><span class="sxs-lookup"><span data-stu-id="15ad1-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="15ad1-106">Observe que o teclado do sistema se comportará de acordo com os recursos da plataforma de destino, por exemplo, o teclado no HoloLens 2 dará suporte a interações diretas à mão, enquanto o teclado no HoloLens (1ª geração) dará suporte ao GGV<sup>[1.](/windows/mixed-reality/gaze)</sup></span><span class="sxs-lookup"><span data-stu-id="15ad1-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="15ad1-107">Além disso, o teclado do sistema não será aparecer ao executar a [Remoting do Unity](../tools/holographic-remoting.md) do editor para um HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15ad1-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="15ad1-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="15ad1-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="15ad1-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) é um componente que fornece métodos para iniciar e fechar um teclado do sistema, bem como interagir com o texto inserido pelo teclado.</span><span class="sxs-lookup"><span data-stu-id="15ad1-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="15ad1-110">Como usar</span><span class="sxs-lookup"><span data-stu-id="15ad1-110">How to Use</span></span>

1. <span data-ttu-id="15ad1-111">Anexe [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) o componente a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="15ad1-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="15ad1-112">Chame para mostrar e ocultar o teclado e manipular os eventos e para manipular quando o teclado for mostrado, oculto e quando a `Show()` `Hide()` tecla Enter for `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` pressionada.</span><span class="sxs-lookup"><span data-stu-id="15ad1-112">Call `Show()` `Hide()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="15ad1-113">Campos de entrada TMP_KeyboardInputField e UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="15ad1-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="15ad1-114">As classes e são componentes que podem ser adicionados aos campos de entrada de texto para invocar automaticamente o teclado do sistema quando clicado e atualizar o conteúdo do campo de entrada de texto à medida que o usuário ins dá entrada [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) de texto.</span><span class="sxs-lookup"><span data-stu-id="15ad1-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="15ad1-115">Como usar</span><span class="sxs-lookup"><span data-stu-id="15ad1-115">How to use</span></span>

1. <span data-ttu-id="15ad1-116">Crie um campo de entrada para UnityUI ou TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="15ad1-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="15ad1-117">Adicione o componente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) ou correspondente ao objeto do jogo de campo de [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) entrada.</span><span class="sxs-lookup"><span data-stu-id="15ad1-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="15ad1-118">Os pré-requisitos para os campos de entrada do UnityUI e os campos de entrada TextMeshPro (TMPro) estão disponíveis em "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span><span class="sxs-lookup"><span data-stu-id="15ad1-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="15ad1-119">Um exemplo de como usar TMP_KeyboardInputField e UI_KeyboardInputField está em "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span><span class="sxs-lookup"><span data-stu-id="15ad1-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>