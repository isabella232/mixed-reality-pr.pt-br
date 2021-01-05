---
title: Modos de exibição do aplicativo
description: Os dois tipos de exibições em aplicativos de realidade mista do Windows são exibições de imersão e exibições 2D.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: exibição de imersão, exibição 2D, Slate, aplicativo, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 0c6127427d5af118bb18aea5c19ddaef6fe8d5eb
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848071"
---
# <a name="app-views"></a>Modos de exibição do aplicativo

Os aplicativos do Windows podem conter dois tipos de exibições: **exibições de imersão** e **exibições 2D**. Os aplicativos podem alternar entre as várias exibições de imersão e 2D, mostrando suas exibições 2D em um monitor como uma janela ou um headset como um Slate. Os aplicativos que têm pelo menos uma exibição de imersão são categorizados como **aplicativos de realidade misturada**. Já os que não têm uma exibição imersiva são **aplicativos 2D**.

## <a name="immersive-views"></a>Exibições de imersão

Uma exibição imersiva dá ao aplicativo a capacidade de criar hologramas no mundo ao seu redor ou inserir o usuário em um ambiente virtual. Quando um aplicativo está desenhando na exibição de imersão, nenhum outro aplicativo está desenhando ao mesmo tempo que os &mdash; hologramas de vários aplicativos não são compostos juntos. Ao ajustar continuamente a perspectiva da qual seu [aplicativo renderiza](../develop/platform-capabilities-and-apis/rendering.md) sua cena para corresponder aos movimentos de cabeça do usuário, seu aplicativo pode renderizar hologramas [trancados para o mundo](coordinate-systems.md) . Os hologramas bloqueados pelo mundo permanecem em um ponto fixo no mundo real ou podem renderizar um mundo virtual que mantém sua posição à medida que um usuário se move.

![Quando estiver em uma exibição de imersão, os hologramas podem ser colocados no mundo todo.](images/designoverview-940px.jpg)<br>
*Quando estiver em uma exibição de imersão, os hologramas podem ser colocados no mundo todo*

No [HoloLens](https://docs.microsoft.com/hololens/hololens1-hardware), seu aplicativo renderiza seus hologramas sobre os arredores do mundo real do usuário. Em um [headset de imersão de realidade mista do Windows](../discover/immersive-headset-hardware-details.md), o usuário não consegue ver o mundo real e, portanto, seu aplicativo deve renderizar tudo o que o usuário verá.

O [Windows Mixed Reality Home](../discover/navigating-the-windows-mixed-reality-home.md) (incluindo o menu iniciar e os hologramas que você colocou em todo o ambiente) não é renderizado enquanto está em uma exibição de imersão. No HoloLens, a Cortana retransmite todas as notificações do sistema que ocorrem enquanto uma exibição imersiva é mostrada, à qual o usuário pode responder com entrada de voz.

Enquanto estiver em uma exibição de imersão, seu aplicativo também será responsável por lidar com todas as entradas. A entrada na realidade mista do Windows é composta de [olhar](gaze-and-commit.md), [gesto](gaze-and-commit.md#composite-gestures) (somente HoloLens), [voz e [controladores de movimento](motion-controllers.md) (somente headsets de imersão).

## <a name="2d-views"></a>exibições 2D

![Vários modos de exibição 2D dispostos em toda a página inicial do Windows Mixed Reality](images/teleportation-940px.png)<br>
*Vários aplicativos com uma exibição 2D posicionada em toda a página inicial do Windows Mixed Reality*

Um aplicativo com uma exibição 2D é exibido na [página inicial do Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) (às vezes chamada de "Shell") como um Slate virtual, renderizado junto com os iniciadores de aplicativo e outros hologramas que o usuário colocou em seu mundo. O usuário pode ajustar esse Slate para movê-lo e dimensioná-lo, embora permaneça em uma resolução fixa, seja qual for seu tamanho. Se o primeiro modo de exibição do seu aplicativo for uma exibição 2D, seu conteúdo 2D preencherá o mesmo Tablet usado para iniciar o aplicativo.

Em um headset de área de trabalho, você pode executar qualquer aplicativo Plataforma Universal do Windows (UWP) que seja executado no seu monitor de área de trabalho hoje. Esses aplicativos já estão renderizando exibições 2D hoje, e seu conteúdo aparecerá automaticamente em um Slate no mundo do usuário quando for iniciado. os aplicativos UWP 2D podem direcionar a família de dispositivos **Windows. universal** para execução nos headsets da área de trabalho e no HoloLens como slates.

Um uso principal de exibições 2D é mostrar um formulário de entrada de texto que usa o teclado do sistema. Como o shell não pode renderizar na parte superior de uma exibição de imersão, o aplicativo precisa alternar para uma exibição 2D para mostrar o teclado do sistema. Os aplicativos que desejam aceitar a entrada de texto precisam alternar para um modo de exibição 2D com uma caixa de texto. Enquanto essa caixa de texto tiver foco, o sistema mostrará o teclado do sistema, permitindo que o usuário insira texto.

Um aplicativo pode ter exibições 2D no monitor da área de trabalho e em um headset conectado em um PC desktop. Por exemplo, você pode procurar o Edge no monitor de sua área de trabalho usando sua exibição 2D principal para encontrar um vídeo de 360 graus. Quando você reproduzir esse vídeo, o Edge iniciará uma exibição de imersão secundária dentro do headset para exibir o conteúdo de vídeo imersiva.

## <a name="see-also"></a>Consulte também

* [Modelo de aplicativo](app-model.md)
* [Como atualizar aplicativos UWP 2D para realidade misturada](../develop/porting-apps/building-2d-apps.md)
* [Como obter um HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [Como navegar na página inicial do Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)
* [Tipos de aplicativos de realidade misturada](types-of-mixed-reality-apps.md)
