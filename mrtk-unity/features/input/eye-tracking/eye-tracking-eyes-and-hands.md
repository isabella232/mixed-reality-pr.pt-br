---
title: Olhos e mãos de acompanhamento ocular
description: Como usar o direcionamento ocular como um ponteiro primário em combinação com movimentos de mão no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143992"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="de1e1-104">Olhos + interação com a mão</span><span class="sxs-lookup"><span data-stu-id="de1e1-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="de1e1-105">Como dar suporte _à aparência + movimentos de mão_ (o olhar & gestos de mão)</span><span class="sxs-lookup"><span data-stu-id="de1e1-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="de1e1-106">Esta página explica como usar o direcionamento ocular como um ponteiro primário em combinação com movimentos de mão.</span><span class="sxs-lookup"><span data-stu-id="de1e1-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="de1e1-107">Em nossas demonstrações de acompanhamento ocular do [MRTK,](../../example-scenes/eye-tracking-examples-overview.md)descrevemos vários exemplos para usar olhos + mãos, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="de1e1-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="de1e1-108">[Seleção:](eye-tracking-target-selection.md)observando o botão holográfico distante e simplesmente executando um gesto de pinçar para selecioná-lo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="de1e1-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="de1e1-109">**Posicionamento (este artigo)**: mova fluentemente um holograma pela cena simplesmente observando-o, pinçando o dedo indicador e o dedo indicador juntos para agarrá-lo e, em seguida, movê-lo usando sua mão.</span><span class="sxs-lookup"><span data-stu-id="de1e1-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="de1e1-110">[Navegação:](eye-tracking-navigation.md)basta olhar para uma localização que você deseja ampliar, pinçar o dedo indicador e o polegar juntos e apontar a mão para você para ampliar. </span><span class="sxs-lookup"><span data-stu-id="de1e1-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="de1e1-111">Observe que o MRTK foi projetado atualmente de uma maneira que raios de mão à distância atuem como ponteiros de foco priorizados.</span><span class="sxs-lookup"><span data-stu-id="de1e1-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="de1e1-112">Isso significa que os ponteiros de olhar e de cabeça serão suprimidos automaticamente depois que uma mão for detectada e se tornarão visíveis novamente depois de dizer "Selecionar".</span><span class="sxs-lookup"><span data-stu-id="de1e1-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="de1e1-113">No entanto, essa pode não ser a maneira que você gostaria de interagir à distância e, em vez disso, favorecer uma interação simples de "olhar e _confirmação",_ independentemente da presença de mãos em sua exibição.</span><span class="sxs-lookup"><span data-stu-id="de1e1-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="de1e1-114">Como desabilitar o raio de mão</span><span class="sxs-lookup"><span data-stu-id="de1e1-114">How to disable the hand ray</span></span>

<span data-ttu-id="de1e1-115">Para desabilitar o ponteiro de raio de mão, basta remover _o 'DefaultControllerPointer'_ em sua configuração de MRTK de ponteiro de entrada _>_ ponteiro.</span><span class="sxs-lookup"><span data-stu-id="de1e1-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="de1e1-116">Para usar olhos e mãos, conforme descrito acima em seu aplicativo, certifique-se também de atender a todos os requisitos para usar [o acompanhamento ocular.](eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="de1e1-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![Como remover o raio da mão](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="de1e1-118">Você também pode conferir como o perfil de entrada _EyeTrackingDemoPointerProfile_ do pacote de exemplo de acompanhamento ocular é definido como uma referência.</span><span class="sxs-lookup"><span data-stu-id="de1e1-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="de1e1-119">Como manter o ponteiro de olhar sempre em</span><span class="sxs-lookup"><span data-stu-id="de1e1-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="de1e1-120">Para evitar que os ponteiros de olhar de cabeça ou olho sejam suprimidos automaticamente quando uma mão for detectada, o olhar [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) poderá ser especificado para controlar se ele deve estar ativado ou desativado.</span><span class="sxs-lookup"><span data-stu-id="de1e1-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="de1e1-121">Confira [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="de1e1-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="de1e1-122">Voltar para "acompanhamento de olho no MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="de1e1-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
