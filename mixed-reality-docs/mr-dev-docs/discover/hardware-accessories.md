---
title: Acessórios de hardware
description: Descreve os tipos de acessórios disponíveis para uso com Windows Mixed Reality e como defini-los.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: how-to, accessories, bluetooth, bt, controller, gamepad, clicker, xbox, hardware, mixed reality headset, windows mixed reality headset, headset de realidade virtual, controlador de movimento
ms.openlocfilehash: a6776df9374fce3f1399de944be06c93ff6fdcb3e6f4a38dcc92453556857376
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188446"
---
# <a name="hardware-accessories"></a>Acessórios de hardware

Windows Mixed Reality dispositivos compatíveis com acessórios. Você pode usar Bluetooth usb ou usb para emparelhar acessórios com suporte a um headset imersivo do seu computador.

Para obter informações sobre como Bluetooth acessórios com HoloLens, consulte Conexão para Bluetooth [dispositivos USB-C e](/hololens/hololens-connect-devices).

Windows Mixed Reality headsets imersivos exigem acessórios para entrada além do [olhar e](../design/gaze-and-commit.md) [da voz.](../design/voice-input.md) Os acessórios com suporte incluem **teclado e mouse,** **gamepad** e **[controladores de movimento](../design/motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Emparelhamento Bluetooth acessórios

Emparelhar um periférico Bluetooth com um headset imersivo é semelhante ao emparelhamento de um periférico Bluetooth com um Windows 10 desktop ou dispositivo móvel:

1. No Menu Iniciar, abra o aplicativo **Configurações** aplicativo
2. Ir para **Dispositivos**
3. Ativar o Bluetooth se ele estiver desligado usando a opção de controle deslizante
4. Coloque seu Bluetooth no modo de emparelhamento. Esse processo varia de dispositivo para dispositivo, mas na maioria Bluetooth os dispositivos pressionam e seguram um ou mais botões.
5. Aguarde o nome do dispositivo aparecer na lista de Bluetooth dispositivos. Quando isso acontecer, selecione o dispositivo e, em seguida, selecione o **botão** Emparelhar. Se você tiver muitos Bluetooth próximos, talvez seja necessário rolar até a parte inferior da lista Bluetooth de dispositivos para ver o dispositivo que você está tentando emparelhar.
6. Ao emparelhar Bluetooth periféricos com a capacidade de entrada (por exemplo: teclados Bluetooth), um pino de 6 dígitos ou de 8 dígitos pode ser exibido. Certifique-se de digitar esse pino no periférico e pressione Enter para concluir o emparelhamento com o headset.

## <a name="motion-controllers"></a>Controladores de movimento

Windows Mixed Reality [controladores de](../design/motion-controllers.md) movimento têm suporte por headsets imersivos, mas não por HoloLens. Esses controladores oferecem acompanhamento de movimento preciso e responsivo em seu campo de exibição. Os sensores no headset imersivo fazem o acompanhamento, o que significa que não há necessidade de instalar o hardware nas paredes em seu espaço. Cada controlador apresenta vários métodos de entrada.

![Windows Mixed Reality de movimento](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>Bluetooth teclados

Os teclados Qwerty Bluetooth inglês podem ser emparelhados e usados em qualquer lugar em que você possa usar o teclado holográfico. Obter um teclado de qualidade faz diferença, portanto, recomendamos o [Teclado Universal Dobrável](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) da Microsoft ou o [Microsoft Designer Bluetooth Desktop.](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)

## <a name="bluetooth-gamepads"></a>Bluetooth gamepads

Você pode usar um controlador com aplicativos e jogos que habilitam especificamente o suporte ao gamepad. Os gamepads não podem ser usados para controlar a HoloLens do usuário.

Os controladores sem fio do Xbox que vêm com o Xbox One S ou vendidos como acessórios para Xbox One S recursos Bluetooth conectividade, para que você possa usá-los com HoloLens headsets imersivos e imersivos. O controlador sem fio Xbox [deve ser atualizado](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes de poder ser usado com HoloLens.

Outras marcas de Bluetooth gamepads podem funcionar com Windows Mixed Reality dispositivos, mas o suporte varia de acordo com o aplicativo.

## <a name="other-bluetooth-accessories"></a>Outros Bluetooth acessórios

Desde que o periférico seja compatível com os perfis BLUETOOTH HID ou GATT, ele poderá emparelhar com HoloLens. Outros Bluetooth dispositivos HID e GATT além de teclado, mouses e o HoloLens Clicker podem exigir que um aplicativo de Microsoft HoloLens seja totalmente funcional.

Os periféricos sem suporte incluem:

* Não há suporte para periféricos Bluetooth perfis de áudio.
* Bluetooth de áudio, como alto-falantes e headsets, podem estar disponíveis no aplicativo Configurações, mas não têm suporte com Microsoft HoloLens como um ponto de extremidade de áudio.
* Bluetooth e PCs habilitados para Bluetooth não têm suporte para emparelhamento e transferências de arquivos.

## <a name="unpairing-a-bluetooth-peripheral"></a>Como desempacar um periférico Bluetooth trabalho

1. No Menu Iniciar, abra o aplicativo **Configurações** aplicativo
2. Ir para **Dispositivos**
3. Ativar o Bluetooth se ele estiver desligado
4. Encontre seu dispositivo na lista de dispositivos Bluetooth disponíveis
5. Selecione seu dispositivo na lista e, em seguida, selecione o **botão** Remover