---
title: Focar e esperar
description: Obter uma visão geral do modelo de entrada de olhar e de olhar e de cabeça para aplicativos de realidade misturada.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade Misturada, olhar, duração, interação, design, acompanhamento ocular, acompanhamento de cabeça, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Realidade Misturada Toolkit
ms.openlocfilehash: c65c13b06df70ed5471b283ad349dd72e1575018a98913177983d7a13571d666
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213670"
---
# <a name="gaze-and-dwell"></a>Focar e esperar

Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis.
Os comandos de voz também podem não ser confiáveis em determinados contextos, por exemplo, em condições excessivamente altas.
O olhar e a vida oferecem um mecanismo familiar e fácil de dominar para trabalhar de cabeça para cima e mãos livres em HoloLens.
Além disso, o olhar e a suspensão são um excelente fallback, que é independente das restrições de interferência de ruído ou silêncio no ambiente operacional.
Distinguemos duas variantes do olhar _e da cabeça:_ com o olhar [com a](gaze-and-dwell-head.md) cabeça e a cabeça e com o olhar e com [a cabeça.](gaze-and-dwell-eyes.md)

## <a name="scenarios"></a>Cenários

O olhar e a atenção se destaca em cenários em que as mãos de uma pessoa estão ocupadas com outras tarefas e a voz não é 100% confiável ou disponível devido a restrições ambientais ou sociais.
Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro.
Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor.
O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz.
O olhar e a facilidade permitem que a pessoa que usa o HoloLens navegue com confiança no material de referência sem interromper seu fluxo de trabalho.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Focar com a cabeça e esperar</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
     <tr>
        <td>Focar com o olhar e esperar</td>
        <td>❌ Não disponível</td>
        <td>✔️ Recomendado</td>
        <td>❌ Não disponível</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>Confira também

* [Interação ocular](eye-gaze-interaction.md)
* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)