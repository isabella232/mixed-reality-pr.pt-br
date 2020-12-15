---
title: Como usar o simulador do Windows Mixed Reality
description: O simulador de realidade mista do Windows permite que você teste aplicativos de realidade misturados em seu computador sem um headset de imersão de realidade mista do Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Realidade mista do Windows, simulador, teste
ms.openlocfilehash: 4ed3355df242f1df35c009e53149d834ea113e1f
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530293"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Como usar o simulador do Windows Mixed Reality

O simulador de realidade mista do Windows permite que você teste aplicativos de realidade misturados em seu computador sem um headset de imersão de realidade mista do Windows. O simulador está disponível com a atualização do Windows 10 para criadores. O simulador é semelhante ao [emulador do HoloLens](using-the-hololens-emulator.md), embora o simulador não use uma máquina virtual. Os aplicativos simulados são executados em sua sessão de usuário do Windows 10 desktop, assim como fariam se você estivesse usando um headset de imersão. As entradas humanas e ambientais lidas pelos sensores em um headset de imersão são, em vez disso, simuladas usando o teclado, o mouse ou o controlador Xbox. Os aplicativos não precisam de nenhuma modificação para serem executados no simulador e não sabem que não estão em execução em um headset de imersão.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Habilitando o simulador de realidade mista do Windows

1. **Habilitar o modo de desenvolvedor** de configurações-> Update e Security-> para desenvolvedores
2. Inicie o **portal de realidade misturada** na área de trabalho
3. Se esta for a primeira vez que você inicia o portal, você precisará passar pela experiência de instalação
   1. Selecione **introdução**
   2. Selecione **concordo** para aceitar o contrato
   3. Selecione **Configurar para simulação (para desenvolvedores)** para continuar a instalação sem um dispositivo físico
   4. Selecione **Configurar** para confirmar sua escolha
4. Selecione o botão **para desenvolvedores** no lado esquerdo do portal da realidade misturada
5. Ative a opção de alternância de simulação para **ativado**
   * Habilitar a simulação instala e habilita o controlador 6 DOF simulado à esquerda por padrão.  Antes que a atualização do Windows 10 seja 2019, a instalação de um controlador simulado de 6 DOF requer permissões de administrador.  Aceite a caixa de diálogo controle de conta de usuário se ela for exibida.

Agora você deve estar executando com a simulação!

Se você quiser desabilitar o modo de desenvolvedor em configurações, primeiro você deve ativar a opção de alternância de simulação para **desativado** na seção **para desenvolvedores** do portal da realidade misturada.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Implantando aplicativos no simulador de realidade misturada

Como o simulador é executado em seu PC local sem uma máquina virtual, você pode implantar seus aplicativos universais do Windows no **computador local** durante a depuração.

## <a name="basic-simulator-input"></a>Entrada do simulador básico

Controlar o simulador é semelhante a muitos jogos de vídeo 3D comuns e ao [emulador do HoloLens](using-the-hololens-emulator.md). Há opções de entrada disponíveis usando o teclado, o mouse ou o controle Xbox.

Você controla o simulador direcionando as ações de um usuário simulado utilizando um headset de imersão. Suas ações movem o usuário simulado e causam interações com aplicativos que respondem como em um headset de imersão.
* **Andar para a frente, para trás, para a esquerda e para a direita** – use as teclas W, A, S e D no teclado ou o joystick esquerdo em um controle Xbox.
* **Pesquisar, para baixo, à esquerda e** selecionar com o botão direito do mouse e arrastá-lo, use as teclas de direção do teclado ou o botão direito em um controlador Xbox.
* **Pressione o botão de ação no controlador** -clique com o botão direito do mouse, pressione a tecla Enter no teclado ou use o botão a em um controlador Xbox.
* **Pressione o botão página inicial no controlador** -pressione a tecla Windows ou a tecla F2 no teclado ou pressione o botão B em um controlador Xbox.
* **Movimentação do controlador para rolagem** – mantenha pressionada a tecla Alt e o botão direito do mouse e arraste o mouse para cima/para baixo. Em um controlador Xbox, mantenha o gatilho direito e um botão e mova o botão direito para cima e para baixo.

## <a name="tracked-controllers"></a>Controladores rastreados

O simulador de realidade misturada pode simular até dois controladores de movimento acompanhados por mão. Habilite-os usando as opções de alternância no portal de realidade misturada. Cada controlador simulado tem:
* Posição e orientação no espaço
* Botão Página Inicial
* Botão Menu
* Botão de fixação
* Touchpad
* Thumbstick
* Nível da bateria

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity, você está no meio do estágio de implantação. A partir daqui, você pode continuar para o próximo [tópico](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) ou ir diretamente para a adição de serviços avançados.

> [!div class="nextstepaction"]
> [Serviços avançados](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Veja também
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Entrada do simulador de realidade mista avançada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mapeamento espacial no Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Mapeamento espacial no DirectX](../../develop/native/spatial-mapping-in-directx.md)
