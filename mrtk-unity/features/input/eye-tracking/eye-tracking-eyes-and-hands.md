---
title: Olhos e mãos
description: Como usar o foco de olho como um ponteiro principal em combinação com movimentos de mão no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: ff464c6f2381a9df020a9ccf807672d4463d662c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175109"
---
# <a name="eyes-and-hands"></a><span data-ttu-id="3544b-104">Olhos e mãos</span><span class="sxs-lookup"><span data-stu-id="3544b-104">Eyes and hands</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="3544b-105">Como dar suporte a _movimentos de aparência + mão_ (olho olhar & mão)</span><span class="sxs-lookup"><span data-stu-id="3544b-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="3544b-106">Esta página explica como usar o direcionamento de olho como um ponteiro principal em combinação com movimentos de mão.</span><span class="sxs-lookup"><span data-stu-id="3544b-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="3544b-107">Em nossas [demonstrações de acompanhamento de olho do MRTK](../../example-scenes/eye-tracking-examples-overview.md), descrevemos vários exemplos para usar os olhos + Hands, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3544b-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="3544b-108">[Seleção](eye-tracking-target-selection.md): olhando para o botão de Holographic distante e simplesmente executando um gesto de pinçar para selecioná-lo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="3544b-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="3544b-109">**Posicionamento (este artigo)**: movimente-se fluentmente um holograma em sua cena simplesmente olhando para ele, Pinçando o dedo do índice e o polegar para pegar e, em seguida, movê-lo usando sua mão.</span><span class="sxs-lookup"><span data-stu-id="3544b-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="3544b-110">[Navegação](eye-tracking-navigation.md): basta examinar um local em que você deseja ampliar, pinçar o dedo do índice e aplicar polegar e _puxar_ sua mão para ampliar.</span><span class="sxs-lookup"><span data-stu-id="3544b-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="3544b-111">Observe que o MRTK está atualmente projetado de forma que, a partir de raios de distância, atuam como ponteiros de foco priorizado.</span><span class="sxs-lookup"><span data-stu-id="3544b-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="3544b-112">Isso significa que os ponteiros de olhar de cabeça e olho serão automaticamente suprimidos quando uma mão for detectada e ficarão visíveis novamente depois de dizer "selecionar".</span><span class="sxs-lookup"><span data-stu-id="3544b-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="3544b-113">No entanto, essa pode não ser a maneira como você gostaria de interagir em uma distância e, em vez disso, favorecer uma interação simples de _' olhar e confirmar '_ , independentemente da presença de mãos em sua exibição.</span><span class="sxs-lookup"><span data-stu-id="3544b-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="3544b-114">Como desabilitar a disposição de raio</span><span class="sxs-lookup"><span data-stu-id="3544b-114">How to disable the hand ray</span></span>

<span data-ttu-id="3544b-115">Para desabilitar o ponteiro de raio à mão, basta remover o _' DefaultControllerPointer '_ em sua definição de configuração _de ponteiro de > de entrada_ MRTK.</span><span class="sxs-lookup"><span data-stu-id="3544b-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="3544b-116">Para usar os olhos e as mãos conforme descrito acima em seu aplicativo, verifique também se você atende a todos os [requisitos para usar o acompanhamento de olho](eye-tracking-basic-setup.md).</span><span class="sxs-lookup"><span data-stu-id="3544b-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![Como remover a disposição do raio](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="3544b-118">Você também pode fazer check-out, como o perfil de entrada _EyeTrackingDemoPointerProfile_ do pacote de exemplo de acompanhamento de olho é configurado como uma referência.</span><span class="sxs-lookup"><span data-stu-id="3544b-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="3544b-119">Como manter o ponteiro do olhar sempre ligado</span><span class="sxs-lookup"><span data-stu-id="3544b-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="3544b-120">Para evitar que os ponteiros de olhar de cabeça ou olho sejam suprimidos automaticamente quando uma mão for detectada, o olhar [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) poderá ser especificado para controlar se ele deve estar ativado ou desativado.</span><span class="sxs-lookup"><span data-stu-id="3544b-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="3544b-121">Confira [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="3544b-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="3544b-122">Voltar para "acompanhamento de olho no MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="3544b-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
