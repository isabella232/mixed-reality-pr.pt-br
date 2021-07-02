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
# <a name="eyes-and-hands"></a>Olhos e mãos

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Como dar suporte a _movimentos de aparência + mão_ (olho olhar & mão)

Esta página explica como usar o direcionamento de olho como um ponteiro principal em combinação com movimentos de mão.
Em nossas [demonstrações de acompanhamento de olho do MRTK](../../example-scenes/eye-tracking-examples-overview.md), descrevemos vários exemplos para usar os olhos + Hands, por exemplo:

- [Seleção](eye-tracking-target-selection.md): olhando para o botão de Holographic distante e simplesmente executando um gesto de pinçar para selecioná-lo rapidamente.
- **Posicionamento (este artigo)**: movimente-se fluentmente um holograma em sua cena simplesmente olhando para ele, Pinçando o dedo do índice e o polegar para pegar e, em seguida, movê-lo usando sua mão.
- [Navegação](eye-tracking-navigation.md): basta examinar um local em que você deseja ampliar, pinçar o dedo do índice e aplicar polegar e _puxar_ sua mão para ampliar.

Observe que o MRTK está atualmente projetado de forma que, a partir de raios de distância, atuam como ponteiros de foco priorizado.
Isso significa que os ponteiros de olhar de cabeça e olho serão automaticamente suprimidos quando uma mão for detectada e ficarão visíveis novamente depois de dizer "selecionar".
No entanto, essa pode não ser a maneira como você gostaria de interagir em uma distância e, em vez disso, favorecer uma interação simples de _' olhar e confirmar '_ , independentemente da presença de mãos em sua exibição.

### <a name="how-to-disable-the-hand-ray"></a>Como desabilitar a disposição de raio

Para desabilitar o ponteiro de raio à mão, basta remover o _' DefaultControllerPointer '_ em sua definição de configuração _de ponteiro de > de entrada_ MRTK.
Para usar os olhos e as mãos conforme descrito acima em seu aplicativo, verifique também se você atende a todos os [requisitos para usar o acompanhamento de olho](eye-tracking-basic-setup.md).

![Como remover a disposição do raio](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

Você também pode fazer check-out, como o perfil de entrada _EyeTrackingDemoPointerProfile_ do pacote de exemplo de acompanhamento de olho é configurado como uma referência.

### <a name="how-to-keep-gaze-pointer-always-on"></a>Como manter o ponteiro do olhar sempre ligado

Para evitar que os ponteiros de olhar de cabeça ou olho sejam suprimidos automaticamente quando uma mão for detectada, o olhar [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) poderá ser especificado para controlar se ele deve estar ativado ou desativado.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Confira [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)

---
[Voltar para "acompanhamento de olho no MixedRealityToolkit"](eye-tracking-main.md)
