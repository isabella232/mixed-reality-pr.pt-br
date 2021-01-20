---
title: Focar e esperar
description: Obtenha uma visão geral do modelo de entrada de olho e de olhar e de cabeça para aplicativos de realidade misturada.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade misturada, olhar, pesquisa, interação, design, controle de cabeça, acompanhamento de cabeçalho, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: aa4fceeb8875da89fd7f84c3709ff6db07fd96f4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582132"
---
# <a name="gaze-and-dwell"></a>Focar e esperar

Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis.
Os comandos de voz também podem não ser confiáveis em determinados contextos, por exemplo, sob condições excessivamente alta.
A olhar e a pesquisa oferecem um mecanismo familiar e fácil de dominar para as cabeças de trabalho e as mãos gratuitas no HoloLens.
Além disso, o olhar e a pesquisa são um ótimo fallback, o que é independente da interferência de ruído ou restrições de silêncio no ambiente operacional.
Distinguimos duas variantes de _olhar e de duração_: [Head-olhar e de pesquisa](gaze-and-dwell-head.md) e [olho-olhar e a pesquisa](gaze-and-dwell-eyes.md).

## <a name="scenarios"></a>Cenários

A olhar e a pesquisa são Excel em cenários em que as mãos de uma pessoa estão ocupadas com outras tarefas, e a voz não é 100% confiável ou está disponível devido a restrições de ambiente ou sociais.
Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro.
Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor.
O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz.
A olhar e a pesquisa permitem que a pessoa que usa o HoloLens Navegue com confiança no material de referência sem interromper o fluxo de trabalho.

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