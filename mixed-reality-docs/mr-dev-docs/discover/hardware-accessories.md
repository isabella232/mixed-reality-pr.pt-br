---
title: Acessórios de hardware
description: Descreve os tipos de acessórios disponíveis para uso com a realidade mista do Windows e como configurá-los.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: instruções, acessórios, Bluetooth, BT, controlador, gamepad, clico, Xbox, hardware, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual e controlador de movimento
ms.openlocfilehash: aaed865f3fd2f722ce287bd2362299f785af05dc
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757714"
---
# <a name="hardware-accessories"></a>Acessórios de hardware

Os dispositivos Windows Mixed Reality dão suporte a acessórios. Você pode usar portas Bluetooth ou USB para emparelhar os acessórios com suporte para um headset de imersão do seu PC.

Para obter informações sobre como usar os acessórios Bluetooth com o HoloLens, consulte [conectar-se a dispositivos Bluetooth e USB-C](https://docs.microsoft.com/hololens/hololens-connect-devices).

Os headsets de imersão de realidade mista do Windows exigem acessórios para entrada além de [olhar](../design/gaze-and-commit.md) e [voz](../design/voice-input.md). Os acessórios com suporte incluem **teclado e mouse**, **gamepad** e **[controladores de movimento](../design/motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Emparelhamento de acessórios Bluetooth

Emparelhar um periférico Bluetooth com um headset de imersão é semelhante a emparelhar um periférico Bluetooth com um dispositivo Windows 10 desktop ou móvel:

1. No menu Iniciar, abra o aplicativo **configurações**
2. Ir para **dispositivos**
3. Ligue o rádio Bluetooth se ele estiver desativado usando a opção Slider
4. Coloque seu dispositivo Bluetooth no modo de emparelhamento. Esse processo varia de dispositivo para dispositivo, mas na maioria dos dispositivos Bluetooth, pressione e segure um ou mais botões.
5. Aguarde até que o nome do dispositivo apareça na lista de dispositivos Bluetooth. Quando tiver, selecione o dispositivo e, em seguida, selecione o botão **emparelhar** . Se você tiver muitos dispositivos Bluetooth próximos, talvez seja necessário rolar para a parte inferior da lista de dispositivos Bluetooth para ver o dispositivo que você está tentando emparelhar.
6. Ao emparelhar periféricos Bluetooth com capacidade de entrada (por exemplo: teclados Bluetooth), um PIN de 6 ou 8 dígitos pode ser exibido. Certifique-se de digitar esse PIN no periférico e pressione ENTER para concluir o emparelhamento com o headset.

## <a name="motion-controllers"></a>Controladores de movimento

Os controladores de [movimento](../design/motion-controllers.md) de realidade mista do Windows têm suporte por headsets de imersão, mas não com o HoloLens. Esses controladores oferecem controle de movimento preciso e responsivo em seu campo de exibição. Os sensores no headset de imersão fazem o acompanhamento, o que significa que não há necessidade de instalar o hardware nas paredes no seu espaço. Cada controlador apresenta vários métodos de entrada.

![Controladores de movimento do Windows Mixed Reality](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>Teclados Bluetooth

Os teclados Bluetooth do idioma inglês QWERTY podem ser emparelhados e usados em qualquer lugar que você possa usar o Holographic Keyboard. Obter um teclado de qualidade faz uma diferença, portanto, recomendamos o [teclado Microsoft Universal dobrável](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) ou a [área de trabalho do Microsoft designer Bluetooth](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Gamepads Bluetooth

Você pode usar um controlador com aplicativos e jogos que habilitam especificamente o suporte a gamepad. Os gamepads não podem ser usados para controlar a interface do usuário do HoloLens.

Os controladores sem fio do Xbox que acompanham o Xbox One ou vendidos como acessórios para a conectividade Bluetooth um recurso do Xbox One S, para que você possa usá-los com o HoloLens e o headsets de imersão. O controlador sem fio do Xbox [deve ser atualizado](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) para que possa ser usado com o HoloLens.

Outras marcas de gamepads Bluetooth podem funcionar com dispositivos Windows Mixed Reality, mas o suporte irá variar por aplicativo.

## <a name="other-bluetooth-accessories"></a>Outros acessórios Bluetooth

Desde que o periférico dê suporte aos perfis HID ou GATT Bluetooth, ele pode emparelhar com o HoloLens. Outros dispositivos Bluetooth HID e GATT além do teclado, mouse e o clicador do HoloLens podem exigir que um aplicativo complementar no Microsoft HoloLens seja totalmente funcional.

Os periféricos sem suporte incluem:

* Não há suporte para os periféricos nos perfis de áudio Bluetooth.
* Dispositivos de áudio Bluetooth, como alto-falantes e headsets, podem estar disponíveis no aplicativo configurações, mas não têm suporte com o Microsoft HoloLens como um ponto de extremidade de áudio.
* Telefones e computadores habilitados para Bluetooth não têm suporte para emparelhamento e transferências de arquivos.

## <a name="unpairing-a-bluetooth-peripheral"></a>Desemparelhando um periférico Bluetooth

1. No menu Iniciar, abra o aplicativo **configurações**
2. Ir para **dispositivos**
3. Ligue o rádio Bluetooth se ele estiver desativado
4. Localize seu dispositivo na lista de dispositivos Bluetooth disponíveis
5. Selecione o dispositivo na lista e, em seguida, selecione o botão **remover**
