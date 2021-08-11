---
title: Como usar o simulador do Windows Mixed Reality
description: O Windows Mixed Reality simulador permite que você teste aplicativos de realidade misturada em seu computador sem um headset Windows Mixed Reality imersivo.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, simulador, teste
ms.openlocfilehash: 0a6ff0cb0cd893c40e354c0590437201fb97e75c67421a638e47897b19a8f688
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220923"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Como usar o simulador do Windows Mixed Reality

O Windows Mixed Reality simulador permite que você teste aplicativos de realidade misturada em seu computador sem um headset Windows Mixed Reality imersivo. O simulador está disponível com o Atualização do Windows 10 para Criadores. O simulador é semelhante ao [HoloLens Emulator](using-the-hololens-emulator.md), embora o simulador não use uma máquina virtual. Os aplicativos simulados são executados em sua Windows 10 de usuário da área de trabalho, assim como faria se você estivesse usando um headset imersivo. As entradas humanas e ambientais lidas pelos sensores em um headset imersivo são simuladas usando o teclado, o mouse ou o controlador Xbox. Os aplicativos não precisam de nenhuma modificação para execução no simulador e não sabem que não estão em execução em um headset imersivo.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Habilitando o Windows Mixed Reality simulador

1. **Habilitar o modo** de desenvolvedor Configurações -> atualização e segurança -> para desenvolvedores
2. Iniciar o **Portal de Realidade Misturada** da área de trabalho
3. Se esta for a primeira vez que você iniciar o portal, você precisará passar pela experiência de instalação
   1. Selecione **Começar**
   2. Selecione **Concordo em** aceitar o contrato
   3. Selecione **Configurar para simulação (para desenvolvedores)** para continuar com a instalação sem um dispositivo físico
   4. Selecione **Configurar para** confirmar sua escolha
4. Selecione o **botão Para** desenvolvedores no lado esquerdo do Portal de Realidade Misturada
5. Ativar a alternância  simulação
   * Habilitar a simulação instala e habilita o controlador 6-DOF simulado à esquerda por padrão.  Antes da Windows 10 de maio de 2019, a instalação de um controlador simulado de 6 DOF requer permissões de administrador.  Aceite a caixa de diálogo Controle de Conta de Usuário se uma for exibida.

Agora você deve estar executando com simulação!

Se você quiser desabilitar o modo de desenvolvedor no Configurações, primeiro  você  deverá ativar a opção de alternância Simulação para Desligado na seção Para desenvolvedores do Portal de Realidade Misturada.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Implantando aplicativos no simulador de Realidade Misturada

Como o simulador é executado no computador local sem uma Máquina Virtual, você pode implantar seus aplicativos Windows Universal no Computador **Local** durante a depuração.

## <a name="basic-simulator-input"></a>Entrada básica do simulador

Controlar o simulador é semelhante a muitos jogos de vídeo 3D comuns e ao [HoloLens emulador.](using-the-hololens-emulator.md) Há opções de entrada disponíveis usando o teclado, o mouse ou o controle Xbox.

Você controla o simulador direcionando as ações de um usuário simulado usando um headset imersivo. Suas ações movem o usuário simulado e causam interações com aplicativos que respondem como em um headset imersivo.
* **Andar para a frente, para trás, para a esquerda e para a direita** – use as teclas W, A, S e D no teclado ou o joystick esquerdo em um controle Xbox.
* **Olhar para cima, para baixo, para** a esquerda e para a direita – selecione e arraste o mouse, use as teclas de seta no teclado ou o stick direito em um controlador Xbox.
* **Pressionar botão de ação no controlador** – clique com o botão direito do mouse, pressione a tecla Enter no teclado ou use o botão A em um controlador Xbox.
* **Pressionar o botão Início no controlador** – pressione a tecla Windows tecla F2 no teclado ou pressione o botão B em um controlador Xbox.
* **Movimento do controlador para rolagem** – mantenha a tecla Alt e o botão direito do mouse pressionados e arraste o mouse para cima/para baixo. Em um controlador Xbox, mantenha pressionado o gatilho direito e o botão A e mova o direcional analógico direito para cima e para baixo.

## <a name="tracked-controllers"></a>Controladores rastreados

O simulador de Realidade Misturada pode simular até dois controladores de movimento rastreados. Habilita-os usando as opções de alternância no Portal de Realidade Misturada. Cada controlador simulado tem:
* Posição e orientação no espaço
* Botão Página Inicial
* Botão Menu
* Botão de segurar
* Touchpad
* Manípulo
* Nível da bateria

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity, você está no meio do estágio de implantação. A partir daqui, você pode continuar para o próximo [tópico ou](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) ir diretamente para a adição de serviços avançados.

> [!div class="nextstepaction"]
> [Serviços avançados](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Confira também
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Entrada avançada do simulador de realidade misturada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mapeamento espacial no Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Mapeamento espacial no DirectX](../../develop/native/spatial-mapping-in-directx.md)
