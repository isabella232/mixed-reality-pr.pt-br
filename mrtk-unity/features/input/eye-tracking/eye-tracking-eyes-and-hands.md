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
# <a name="eyes--hand-interaction"></a>Olhos + interação com a mão

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Como dar suporte _à aparência + movimentos de mão_ (o olhar & gestos de mão)

Esta página explica como usar o direcionamento ocular como um ponteiro primário em combinação com movimentos de mão.
Em nossas demonstrações de acompanhamento ocular do [MRTK,](../../example-scenes/eye-tracking-examples-overview.md)descrevemos vários exemplos para usar olhos + mãos, por exemplo:

- [Seleção:](eye-tracking-target-selection.md)observando o botão holográfico distante e simplesmente executando um gesto de pinçar para selecioná-lo rapidamente.
- **Posicionamento (este artigo)**: mova fluentemente um holograma pela cena simplesmente observando-o, pinçando o dedo indicador e o dedo indicador juntos para agarrá-lo e, em seguida, movê-lo usando sua mão.
- [Navegação:](eye-tracking-navigation.md)basta olhar para uma localização que você deseja ampliar, pinçar o dedo indicador e o polegar juntos e apontar a mão para você para ampliar. 

Observe que o MRTK foi projetado atualmente de uma maneira que raios de mão à distância atuem como ponteiros de foco priorizados.
Isso significa que os ponteiros de olhar e de cabeça serão suprimidos automaticamente depois que uma mão for detectada e se tornarão visíveis novamente depois de dizer "Selecionar".
No entanto, essa pode não ser a maneira que você gostaria de interagir à distância e, em vez disso, favorecer uma interação simples de "olhar e _confirmação",_ independentemente da presença de mãos em sua exibição.

### <a name="how-to-disable-the-hand-ray"></a>Como desabilitar o raio de mão

Para desabilitar o ponteiro de raio de mão, basta remover _o 'DefaultControllerPointer'_ em sua configuração de MRTK de ponteiro de entrada _>_ ponteiro.
Para usar olhos e mãos, conforme descrito acima em seu aplicativo, certifique-se também de atender a todos os requisitos para usar [o acompanhamento ocular.](eye-tracking-basic-setup.md)

![Como remover o raio da mão](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

Você também pode conferir como o perfil de entrada _EyeTrackingDemoPointerProfile_ do pacote de exemplo de acompanhamento ocular é definido como uma referência.

### <a name="how-to-keep-gaze-pointer-always-on"></a>Como manter o ponteiro de olhar sempre em

Para evitar que os ponteiros de olhar de cabeça ou olho sejam suprimidos automaticamente quando uma mão for detectada, o olhar [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) poderá ser especificado para controlar se ele deve estar ativado ou desativado.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Confira [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)

---
[Voltar para "acompanhamento de olho no MixedRealityToolkit"](eye-tracking-main.md)
