---
title: Gesto de Iniciar
description: saiba como usar o gesto de início para chamar o Menu iniciar em HoloLens e Windows Mixed Reality headsets de imersão.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: realidade misturada, gestos, interação, design, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, flor
ms.openlocfilehash: f3ad9309c7232f20a25060b1d98d7374272ceea00f24be18d7263b8ec7002fb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213720"
---
# <a name="start-gesture"></a>Gesto de Iniciar

O gesto de início é um gesto de mão usado para invocar o menu iniciar. é o equivalente a pressionar a tecla Windows em teclados, o botão Xbox em controladores xbox ou o botão Windows em controladores de movimento de headsets de imersão. Preste atenção especial aos gestos do sistema reservado em cada dispositivo de realidade misturada para evitar conflitos quando estiver criando interações.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Bloom</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Botão do pulso</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Olho olhar e Palm up pinçar</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Bloom

projetamos "cair" para abrir o menu iniciar no HoloLens (1ª gen), que é um gesto simbólico imitando um blossom de flor. É distintivo para uma interação com o pé, fácil de usar e rápida de se lembrar. Para usar o gesto, mantenha a mão com seu Palm up e mãos, em seguida, abra sua mão distribuindo os dedos.

:::row:::
    :::column:::
        ![Fechamento de flor](images/bloom-close.png)<br>
        **Etapa 1: Palm juntos**<br>
    :::column-end:::
    :::column:::
        ![Flor aberta](images/bloom-open.png)<br>
        **Etapa 2: Palm up com as mãos espalhadas**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Gesto de Iniciar

no HoloLens 2, substituímos o gesto de cair com um botão de pulso virtual, que é mais instinctual para os usuários. Ao mostrar os usuários o botão no pulso, eles podem acessá-lo intuitivamente e pressioná-lo com a outra mão.

:::row:::
    :::column:::
        ![Botão do punho pronto](images/wrist-button-ready.png)<br>
        **Etapa 1: Palm up para mostrar o botão do pulso**<br>
    :::column-end:::
    :::column:::
        ![Botão do pulso pressionado](images/wrist-button-press.png)<br>
        **Etapa 2: Pressione o botão do pulso**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>Gesto de Iniciar de uma mão

> [!IMPORTANT]
> Para que o gesto de Iniciar de uma mão funcione:
>
> 1. Você deve atualizar para a atualização de novembro de 2019 (build 18363.1039) ou posterior.
> 1. Seus olhos devem ser calibrados no dispositivo para que o rastreamento ocular funcione corretamente. Se você não vir pontos orbitando em torno do ícone Iniciar quando olhar para ele, seus olhos não estarão calibrados no dispositivo.

Você também pode usar o gesto de início com apenas uma mão. Mantenha sua mão em frente com seu Palm e veja o **ícone iniciar** no pulso interno. **Enquanto mantém o olhar no ícone**, aperte seu polegar e o dedo indicador juntos.<br>
:::row:::
    :::column:::
        ![Botão do punho pronto](images/wrist-button-ready.png)<br>
        **Etapa 1: Palm up para mostrar o botão do pulso**<br>
    :::column-end:::
    :::column:::
        ![Botão do pulso pinçar](images/wrist-button-pinch.png)<br>
        **Etapa 2: olho olhar no botão e, em seguida, aperte**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Confira também

* [Interações instinctuais](interaction-fundamentals.md)
* [Olho-olhar](eye-tracking.md)
* [Entrada de voz](voice-input.md)