---
title: Entrada do teclado no Unity
description: O Unity fornece a classe TouchScreenKeyboard para aceitar a entrada de teclado quando não há nenhum teclado físico disponível.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: teclado, entrada, Unity, touchscreenkeyboard, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, HoloLens, HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098268"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="34e46-104">Entrada do teclado no Unity</span><span class="sxs-lookup"><span data-stu-id="34e46-104">Keyboard input in Unity</span></span>

<span data-ttu-id="34e46-105">**Namespace:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="34e46-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="34e46-106">**Tipo**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="34e46-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="34e46-107">Embora o HoloLens dê suporte a muitas formas de entrada, incluindo teclados Bluetooth, a maioria dos aplicativos não pode pressupor que todos os usuários terão uma Keyboard física disponível.</span><span class="sxs-lookup"><span data-stu-id="34e46-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="34e46-108">Se seu aplicativo requer entrada de texto, alguma forma de teclado na tela deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="34e46-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="34e46-109">O Unity fornece a classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceitar a entrada de teclado quando não há nenhum teclado físico disponível.</span><span class="sxs-lookup"><span data-stu-id="34e46-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="34e46-110">Comportamento do teclado do sistema do HoloLens no Unity</span><span class="sxs-lookup"><span data-stu-id="34e46-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="34e46-111">No HoloLens, o *TouchScreenKeyboard* aproveita o teclado na tela do sistema e se sobrepõe diretamente à exibição do volumétricos do seu aplicativo Mr.</span><span class="sxs-lookup"><span data-stu-id="34e46-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="34e46-112">A experiência é semelhante ao uso do teclado nos aplicativos internos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="34e46-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="34e46-113">Observe que o teclado do sistema se comportará de acordo com os recursos da plataforma de destino, por exemplo, o teclado no HoloLens 2 dará suporte a interações diretas, enquanto o teclado no HoloLens (1º gen) dará suporte a GGV (olhar, gesto e voz).</span><span class="sxs-lookup"><span data-stu-id="34e46-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="34e46-114">Além disso, o teclado do sistema não aparecerá ao executar a comunicação remota do Unity do editor para um HoloLens.</span><span class="sxs-lookup"><span data-stu-id="34e46-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="34e46-115">Usando o teclado do sistema em seu aplicativo do Unity</span><span class="sxs-lookup"><span data-stu-id="34e46-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="34e46-116">Declarar o teclado</span><span class="sxs-lookup"><span data-stu-id="34e46-116">Declare the keyboard</span></span>

<span data-ttu-id="34e46-117">Na classe, declare uma variável para armazenar o *TouchScreenKeyboard* e uma variável para conter a cadeia de caracteres que o teclado retorna.</span><span class="sxs-lookup"><span data-stu-id="34e46-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="34e46-118">Invocar o teclado</span><span class="sxs-lookup"><span data-stu-id="34e46-118">Invoke the keyboard</span></span>

<span data-ttu-id="34e46-119">Quando ocorrer um evento solicitando entrada de teclado, use o seguinte para mostrar o teclado.</span><span class="sxs-lookup"><span data-stu-id="34e46-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="34e46-120">Você pode usar parâmetros adicionais passados para a `TouchScreenKeyboard.Open` função para controlar o comportamento do teclado (por exemplo, definir o texto do espaço reservado ou dar suporte à correção automática).</span><span class="sxs-lookup"><span data-stu-id="34e46-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="34e46-121">Para obter a lista completa de parâmetros, consulte a [documentação do Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span><span class="sxs-lookup"><span data-stu-id="34e46-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="34e46-122">Recuperar conteúdo digitado</span><span class="sxs-lookup"><span data-stu-id="34e46-122">Retrieve typed contents</span></span>

<span data-ttu-id="34e46-123">O conteúdo pode simplesmente ser recuperado chamando `keyboard.text` .</span><span class="sxs-lookup"><span data-stu-id="34e46-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="34e46-124">Talvez você queira recuperar o conteúdo por quadro ou apenas quando o teclado for fechado.</span><span class="sxs-lookup"><span data-stu-id="34e46-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="34e46-125">Opções de teclado alternativas</span><span class="sxs-lookup"><span data-stu-id="34e46-125">Alternative keyboard options</span></span>

<span data-ttu-id="34e46-126">Além de usar a classe *TouchScreenKeyboard* diretamente, você também pode obter a entrada do usuário usando o campo de entrada da *interface do usuário* do Unity ou o *campo de entrada TextMeshPro*.</span><span class="sxs-lookup"><span data-stu-id="34e46-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="34e46-127">Além disso, há uma implementação baseada em *TouchScreenKeyboard* na [cena HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) de [MRTK](/windows/mixed-reality/mrtk-unity) (há um exemplo de interação de teclado no lado esquerdo).</span><span class="sxs-lookup"><span data-stu-id="34e46-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="34e46-128">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="34e46-128">Next Development Checkpoint</span></span>

<span data-ttu-id="34e46-129">Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="34e46-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="34e46-130">A partir daqui, você pode continuar com qualquer [tópico](unity-development-overview.md#3-advanced-features) ou ir diretamente para a implantação de seu aplicativo em um dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="34e46-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34e46-131">Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="34e46-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
