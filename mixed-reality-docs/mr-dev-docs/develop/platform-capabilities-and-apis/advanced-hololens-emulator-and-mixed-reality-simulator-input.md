---
title: Emulator de HoloLens avançado e simulador de realidade misturada
description: instruções detalhadas para usar o teclado, o mouse e o controlador Xbox para simular a entrada para o HoloLens Emulator e o Windows Mixed Reality simulator.
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: HoloLens, Emulator, simulação, Windows Mixed Reality, headset de realidade mista, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: a4e66b2738d5f89949b14fd6f901e2b30dc38cd9e02072f640345d374b9eb9fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217122"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Entrada avançada do Emulador do HoloLens e do Simulador de Realidade Misturada

a maioria dos usuários do emulador só precisará usar os controles de entrada básicos para o [HoloLens Emulator](using-the-hololens-emulator.md#basic-emulator-input) ou o [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Os detalhes a seguir são para usuários avançados que encontraram uma necessidade de simular tipos de entrada mais complexos.

## <a name="concepts"></a>Conceitos

para começar a controlar a entrada virtual para o HoloLens Emulator e o simulador de Windows Mixed Reality, você deve primeiro entender alguns conceitos.

O movimento se refere ao controle e à alteração da posição e da orientação de algo na cena. Para um objeto controlável direcionado, o movimento é controlado com rotação e conversão (movimento) em três eixos.
* **Guinada**: virada para a esquerda ou para a direita.
* **Pitch**: Ative ou diminua.
* **Roll**: distribuição lado a lado.
* **X**: mover para a esquerda ou para a direita.
* **Y**: mover para cima ou para baixo.
* **Z**: avançar ou retroceder.

As entradas do controlador de gesto e movimento são mapeadas de acordo com os dispositivos físicos:
* **Ação**: simula a ação de pressionar o dedo indicador para o polegar ou extrair o botão de ação em um controlador. Por exemplo, a entrada da ação pode ser usada para simular o gesto de toque de ar, para rolar pelo conteúdo e para pressionar e manter pressionado.
* **[](../../design/system-gesture.md#bloom)/estadoe o gesto ou a página inicial**: o gesto de HoloLens/cair do sistema ou o botão página inicial de um controlador é usado para retornar ao shell e disparar ações do sistema.

as mãos têm uma representação rica no HoloLens 2.  Além de ser acompanhado/não acompanhado e utilizável para gestos de condução, as mãos agora têm um modelo de esqueleto articulado que se ajusta a eles e expostos ao desenvolvedor.  O modelo de esqueleto tem 26 pontos rastreados em cada mão.  
* **Conjunto**: uma das 20 posições rastreadas para um determinado controle acompanhado com um ponto associado no espaço 3D.
* **Pose**: uma coleção completa de todas as junções em uma mão controlada, 26 junções em todos. 

Atualmente, não expõemos o controle direto de posições conjuntas individuais por meio do emulador, mas você pode defini-las por meio da API de simulação. Temos um conjunto de representações úteis que o emulador permite que você alterne entre.

Você também pode controlar o estado da entrada simulada do sensor:
* **Redefinir**: retorna todos os sensores simulados para seus valores padrão.  a partir da Emulator HoloLens 2, uma redefinição pode ser definida como escopo para uma ou ambas as mãos. Envolva as mãos desejadas usando as chaves (s) modificadores ou botão (s) (Alt e/ou direita, ou o amortecedor esquerdo e/ou direito no gamepad).
* **Acompanhamento**: percorre os modos de controle posicional, incluindo:
  * **Padrão**: o sistema operacional escolhe o melhor modo de controle com base nas solicitações feitas do sistema.
   * **Orientação**: força o controle somente de orientação, independentemente das solicitações do sistema.
   * **Posicional**: força o controle posicional, não importa as solicitações do sistema.

## <a name="types-of-input"></a>Tipos de entrada

A tabela a seguir mostra como cada tipo de entrada é mapeada para o teclado, o mouse e o controlador Xbox. Cada tipo tem um mapeamento diferente, dependendo do modo de controle de entrada. Você pode encontrar mais informações sobre modos de controle de entrada mais adiante neste documento.

| Entrada |  Keyboard |  Mouse |  Controlador Xbox | 
|----------|----------|----------|----------|
|  Yaw |  Setas à esquerda/direita |  Arrastar para a esquerda/direita |  Direita Thumbstick esquerda/direita | 
|  Densidade |  Setas para cima/para baixo |  Arrastar para cima/para baixo |  Thumbstick direita/para baixo | 
|  Roll |  P/E |  |  DPad esquerda/direita | 
|  X |  A/D |  |  Esquerda Thumbstick esquerda/direita | 
|  Y |  Page up/Page Down |  |  DPad para cima/para baixo | 
|  Z |  W/S |  |  Esquerda Thumbstick para cima/para baixo | 
|  Ação |  Inserir ou espaço |  Botão direito |  Um botão ou um gatilho | 
|  Flor/sistema |  tecla F2 ou Windows |  |  Botão B | 
|  Botão de alça do controlador/mão |  G  |  |  | 
|  Botão de menu do controlador |  M  |  |  | 
|  Touch Touch do controlador |  U  |  |  | 
|  Pressione o controlador Touchpad |  P  |  |  | 
|  Thumbstick do controlador |  K  |  |  | 
|  Estado de controle do controlador esquerdo |  F9 |  |  | 
|  Estado de controle do controlador correto |  F10 |  |  | 
|  A mão ' fechar ' da pose | 7 |  |  |
|  ' Abrir ' da pose (padrão) | 8 |  |  |
|  Pose ' Point ' de mão | 9 |  |  |
|  "Pinça" pose | 0 |  |  |
|  Redefinir |  Tecla de escape |  |  botão Iniciar | 
|  Acompanhamento |  T ou F3 |  |  Botão X | 


Observação: os botões do controlador podem ser direcionados a um único lado/controlador ou ao outro usando os modificadores de destino da mão.

## <a name="targeting"></a>Configurando destinos 

Alguns dos conceitos de entrada acima estão por conta própria.  Action, Bloom/System, Reset e Tracking são conceitos completos, não precisam e não são afetados por nenhum modificador adicional para direcionamento.  Os conceitos restantes podem ser aplicados a um dos vários destinos. Apresentamos maneiras de especificar a qual destino pretendido seu comando deve ser aplicado.  Em todos os casos, é possível especificar por meio da interface do usuário ou por meio de pressionamentos de teclado, qual objeto direcionar.  Em alguns casos, também é possível especificar com o controlador xbox diretamente. 

A tabela a seguir descreve as opções de direcionamento e a maneira de ativar cada uma delas.

| Objeto | Modificador de teclado | Modificador do controlador | Emulator Modificador de interface do usuário |
|----------|----------|----------|----------|
| Corpo | (padrão) | (padrão) | (padrão) |
| Head | Manter H | (Não disponível) | (Não disponível) |
| Mão esquerda/controlador | Mantenha o botão Alt esquerdo pressionado | Botão Manter o Mento Esquerdo | Left-Hand pushpin | 
| Lado direito/controlador | Mantenha o botão Alt pressionado para a direita | Botão Manter o Mento Direito | Right-Hand pushpin |
| Olhos | Manter Y | (Não disponível) | Pushpin de olhos |
  
A tabela a seguir mostra como cada modificador de destino mapeia cada um dos principais conceitos de entrada de movimento

| Entrada | Padrão (Corpo) |  Controle/mão (mantenha a tecla Alt pressionada, mantenha o botão de responsabilidade do gamepad pressionado ou o botão de alternância da interface do usuário) |  Head (Hold H)  |  Olhos (mantenha Y ou alterne o alfinete da interface do usuário) |
|----------|----------|----------|----------|----------|
|  Yaw |  Girar o corpo para a esquerda/direita |  Mover a mão para a esquerda/para a direita |  Girar a cabeça para a esquerda/direita | O olhar se parece com a esquerda/direita |
|  Densidade |  Ativar/desativar a cabeça |  Mover a mão para cima/para baixo |  Girar a cabeça para cima/para baixo | O olhar fica para cima/para baixo | 
|  Roll |  Rolar a cabeça para a esquerda/direita |  |  Rolar a cabeça para a esquerda/direita | (Nenhuma ação) |
|  X |  Corpo do slide para a esquerda/direita |  Mover a mão/controlador para a esquerda/direita |  Girar a cabeça para a esquerda/direita | (Sem ação) |
|  Y |  Mover o corpo para cima/para baixo |  Mover a mão/controlador para cima/para baixo |  Ativar/desativar a cabeça | (Sem ação) |
|  Z |  Mover o corpo para frente/para trás |  Mover a mão/controlador para frente/para trás |  Ativar/desativar a cabeça | (Sem ação) |
 
 
## <a name="controlling-an-app"></a>Controlando um aplicativo

O seguinte conjunto de controles é sugerido para uso do dia a dia:

|  Operação |  Teclado e mouse |  Controller | 
|----------|----------|----------|
|  Corpo X |  A/D |  Left thumbstick left/right | 
|  Corpo Y |  Page up/página para baixo |  DPad para cima/para baixo | 
|  Corpo Z |  W/S |  Thumbstick esquerdo para cima/para baixo | 
|  Yaw de corpo |  Arraste o mouse para a esquerda/direita |  Thumbstick direito para a esquerda/direita | 
|  Yaw de cabeça |  H + arrastar o mouse para a esquerda/direita |  H (no Teclado) + thumbstick direito para a esquerda/direita | 
|  Tom de cabeça |  Arrastar o mouse para cima/para baixo |  Miniatura direita para cima/para baixo | 
|  Rolagem de cabeça |  P/E |  DPad para a esquerda/direita | 
|  Mão/Controlador X |  Alt + A/D |  Soquete + a esquerda/direita do thumbstick esquerdo | 
|  Mão/Controlador Y |  Alt + Page up/página para baixo |  Altura + DPad para cima/para baixo | 
|  Mão/Controlador Z |  Alt + W/S |  1000000011111111111111111 | 
|  Yaw de mão/controlador |  Alt + arrastar o mouse para a esquerda/direita |  Soquete + thumbstick direito esquerdo/direito | 
|  Tom de mão/controlador |  Alt + arrastar o mouse para cima/para baixo |  Responsabilidade + miniatura direita para cima/para baixo | 
|  Roll de mão/controlador |  Alt + P/E |  Lateral + DPad à esquerda/direita | 
|  Ação |  Botão direito do mouse |  Gatilho | 
|  Bloom/System/Home |  F2 ou Windows chave |  Botão B | 
|  Redefinir |  Escape |  botão Iniciar | 
|  Acompanhamento |  T |  Botão X | 
|  Rolagem |  Alt + botão direito do mouse + arrastar o mouse para cima/para baixo |  Altura + gatilho + thumbstick direito para cima/para baixo | 
|  Mover/girar mais rapidamente | Tecla Shift para a esquerda ou direita | Pressione e segure o thumbstick direito |
|  Mover/girar lentamente | Tecla Ctrl esquerda ou direita | Pressione e segure o thumbstick esquerdo |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Usando controladores de movimentos e o headset imersivo do Windows Mixed Reality com o Emulador do HoloLens 2

Ao usar um headset Windows Mixed Reality imersivo com o HoloLens 2 Emulator, a movimentação e a rotação são mapeadas automaticamente para movimentação e rotação do headset.  A posição e a orientação do controlador de movimento são mapeadas automaticamente para a posição e a orientação da mão no emulador.  A tabela a seguir lista as ações adicionais disponíveis ao usar um controlador de movimento.

> [!NOTE]
> Ao usar um headset, os controles de teclado padrão, mouse e gamepad são ignorados automaticamente.

|  Operação |  Ação |  Observações | 
|----------|----------|----------|
|  Corpo X |  Thumbstick Left/Right |   | 
|  Corpo Z |  Thumbstick Forward/Back |   | 
|  Corpo Y |  Página de teclado para cima/para baixo | Verifique se Windows Mixed Reality tem foco.  Pressione Win+Y se o foco estiver no Windows Desktop para retornar o foco Windows Mixed Reality. |
|  Os olhos parecem para a esquerda/direita |  DPad Left/Right | |
|  Olhos para cima/para baixo | DPad para cima/para baixo | |
|  Toque | Gatilho | |
|  Pinçar/segurar | Botão de segurar | |
|  Gesto do sistema | Botão Menu | |
|  Redefinir posição | Clique em thumbstick | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Simulação de percepção Painel de Controle atalhos de teclado

Você pode acessar o painel Controle de Simulação de Percepção e habilitar ou desabilitar dispositivos de entrada do computador com os atalhos de teclado a seguir.

| Operação | Atalho | Descrição/observações |
|-----------|----------|-------------|
| Alternar 'Usar teclado para simulação' | F4 | Quando desligada, a entrada do teclado vai para o HoloLens ou Windows Mixed Reality aplicativo. |
| Alternar 'Usar o mouse para simulação' | F5 | Quando desligado, a entrada do mouse vai para o ambiente de Realidade Misturada (Windows Mixed Reality somente) |
| Alternar 'Usar gamepad para simulação' | F6 | Quando desligada, a entrada do gamepad é ignorada por simulação |
| Mostrar ou ocultar o painel de controle | F7 | |
| Definir o foco do teclado para o painel de controle | F8 | Se o painel não estiver visível no momento, ele será mostrado primeiro. |
| Encaixar ou desencaixar o painel de/para o emulador ou Portal de Realidade Misturada janela | F9 | Se a janela for fechada quando desencaixada, ela será encaixada e oculta. |

## <a name="see-also"></a>Veja também
* [Instalar as ferramentas](../install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como usar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
