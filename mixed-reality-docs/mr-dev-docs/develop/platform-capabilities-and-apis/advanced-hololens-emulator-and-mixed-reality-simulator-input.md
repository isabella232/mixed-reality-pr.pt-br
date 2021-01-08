---
title: Emulador de HoloLens avançado e simulador de realidade misturada
description: Instruções detalhadas para usar o teclado, o mouse e o controlador Xbox para simular a entrada para o emulador do HoloLens e o simulador de realidade mista do Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: HoloLens, emulador, simulação, realidade mista do Windows, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: ff8a2830630b73266fe7348eee5459bcad98e2e0
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006676"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Entrada avançada do Emulador do HoloLens e do Simulador de Realidade Misturada

A maioria dos usuários do emulador só precisará usar os controles de entrada básicos para o [emulador do HoloLens](using-the-hololens-emulator.md#basic-emulator-input) ou o [simulador de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Os detalhes a seguir são para usuários avançados que encontraram uma necessidade de simular tipos de entrada mais complexos.

## <a name="concepts"></a>Conceitos

Para começar a controlar a entrada virtual para o emulador do HoloLens e o simulador de realidade do Windows Mixed, você deve primeiro entender alguns conceitos.

O movimento se refere ao controle e à alteração da posição e da orientação de algo na cena. Para um objeto controlável direcionado, o movimento é controlado com rotação e conversão (movimento) em três eixos.
* **Guinada**: virada para a esquerda ou para a direita.
* **Pitch**: Ative ou diminua.
* **Roll**: distribuição lado a lado.
* **X**: mover para a esquerda ou para a direita.
* **Y**: mover para cima ou para baixo.
* **Z**: avançar ou retroceder.

As entradas do controlador de gesto e movimento são mapeadas de acordo com os dispositivos físicos:
* **Ação**: simula a ação de pressionar o dedo indicador para o polegar ou extrair o botão de ação em um controlador. Por exemplo, a entrada da ação pode ser usada para simular o gesto de toque de ar, para rolar pelo conteúdo e para pressionar e manter pressionado.
* **[](../../design/system-gesture.md#bloom)/Estado gesto ou Home**: o gesto de cair/sistema do HoloLens ou o botão página inicial de um controlador é usado para retornar ao shell e disparar ações do sistema.

As mãos têm uma representação rica no HoloLens 2.  Além de ser acompanhado/não acompanhado e utilizável para gestos de condução, as mãos agora têm um modelo de esqueleto articulado que se ajusta a eles e expostos ao desenvolvedor.  O modelo de esqueleto tem 26 pontos rastreados em cada mão.  
* **Conjunto**: uma das 20 posições rastreadas para um determinado controle acompanhado com um ponto associado no espaço 3D.
* **Pose**: uma coleção completa de todas as junções em uma mão controlada, 26 junções em todos. 

Atualmente, não expõemos o controle direto de posições conjuntas individuais por meio do emulador, mas você pode defini-las por meio da API de simulação. Temos um conjunto de representações úteis que o emulador permite que você alterne entre.

Você também pode controlar o estado da entrada simulada do sensor:
* **Redefinir**: retorna todos os sensores simulados para seus valores padrão.  A partir do emulador do HoloLens 2, uma redefinição pode ser definida como escopo para uma ou ambas as mãos. Envolva as mãos desejadas usando as chaves (s) modificadores ou botão (s) (Alt e/ou direita, ou o amortecedor esquerdo e/ou direito no gamepad).
* **Acompanhamento**: percorre os modos de controle posicional, incluindo:
  * **Padrão**: o sistema operacional escolhe o melhor modo de controle com base nas solicitações feitas do sistema.
   * **Orientação**: força o controle somente de orientação, independentemente das solicitações do sistema.
   * **Posicional**: força o controle posicional, não importa as solicitações do sistema.

## <a name="types-of-input"></a>Tipos de entrada

A tabela a seguir mostra como cada tipo de entrada é mapeada para o teclado, o mouse e o controlador Xbox. Cada tipo tem um mapeamento diferente, dependendo do modo de controle de entrada. Você pode encontrar mais informações sobre modos de controle de entrada mais adiante neste documento.

| Entrada |  Teclado |  Mouse |  Controlador Xbox | 
|----------|----------|----------|----------|
|  Yaw |  Setas à esquerda/direita |  Arrastar para a esquerda/direita |  Direita Thumbstick esquerda/direita | 
|  Densidade |  Setas para cima/para baixo |  Arrastar para cima/para baixo |  Thumbstick direita/para baixo | 
|  Roll |  P/E |  |  DPad esquerda/direita | 
|  X |  A/D |  |  Esquerda Thumbstick esquerda/direita | 
|  Y |  Page up/Page Down |  |  DPad para cima/para baixo | 
|  Z |  W/S |  |  Esquerda Thumbstick para cima/para baixo | 
|  Ação |  Inserir ou espaço |  Botão direito |  Um botão ou um gatilho | 
|  Flor/sistema |  F2 ou tecla do Windows |  |  Botão B | 
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

Alguns dos conceitos de entrada acima têm por conta própria.  A ação, a flor/sistema, a redefinição e o acompanhamento são conceitos completos, não são necessários e não são afetados por nenhum modificador adicional para direcionamento.  Os conceitos restantes podem ser aplicados a um de vários destinos. Apresentamos maneiras de especificar a qual destino pretendido seu comando deve ser aplicado.  Em todos os casos, é possível especificar por meio da interface do usuário ou por meio de pressionamentos de teclado, que objeto deve ser direcionado.  Em alguns casos, também é possível especificar com o controlador Xbox diretamente. 

A tabela a seguir descreve as opções de direcionamento e a maneira de ativar cada uma delas.

| Objeto | Modificador de teclado | Modificador de controlador | Modificador de IU do emulador |
|----------|----------|----------|----------|
| Corpo | (padrão) | (padrão) | (padrão) |
| Head | Manter H | (Não disponível) | (Não disponível) |
| À esquerda/controlador | Pressionar o botão Alt esquerdo | Botão manter à esquerda | Left-Hand pino | 
| À direita/controlador | Manter botão Alt direito | Botão manter à direita | Right-Hand pino |
| Mal | Reter Y | (Não disponível) | Pino de olhos |
  
A tabela a seguir mostra como cada modificador de destino mapeia cada um dos conceitos de entrada de movimento principal

| Entrada | Padrão (corpo) |  Mão/controlador (Mantenha Alt, pressione o botão de controle do gamepad ou alterne o pino da interface do usuário) |  Cabeça (Hold H)  |  Olhos (manter Y ou alternar o pino da interface do usuário) |
|----------|----------|----------|----------|----------|
|  Yaw |  Girar corpo para a esquerda/direita |  Mover para a esquerda/direita |  Transformar cabeçalho à esquerda/direita | Olhar de olho parece esquerda/direita |
|  Densidade |  Girar para cima/para baixo |  Mover para cima/para baixo |  Girar para cima/para baixo | Olho olhar pesquisa | 
|  Roll |  Rolar cabeçalho para a esquerda/direita |  |  Rolar cabeçalho para a esquerda/direita | (Nenhuma ação) |
|  X |  Corpo do slide à esquerda/direita |  Mover mão/controlador para a esquerda/direita |  Transformar cabeçalho à esquerda/direita | (Nenhuma ação) |
|  Y |  Mover corpo para cima/para baixo |  Mover mão/controlador para cima/para baixo |  Girar para cima/para baixo | (Nenhuma ação) |
|  Z |  Mover corpo para frente/para trás |  Mover mão/avançar/voltar do controlador |  Girar para cima/para baixo | (Nenhuma ação) |
 
 
## <a name="controlling-an-app"></a>Controlando um aplicativo

O seguinte conjunto de controles é sugerido para uso do dia a dia:

|  Operação |  Teclado e mouse |  Controller | 
|----------|----------|----------|
|  Corpo X |  A/D |  Esquerda Thumbstick esquerda/direita | 
|  Corpo Y |  Page up/Page Down |  DPad para cima/para baixo | 
|  Corpo Z |  W/S |  Esquerda Thumbstick para cima/para baixo | 
|  Guinada do corpo |  Arrastar mouse para a esquerda/direita |  Direita Thumbstick esquerda/direita | 
|  Desvio de cabeça |  H + arrastar mouse para a esquerda/direita |  H (no teclado) + direita Thumbstick esquerda/direita | 
|  Inclinação do cabeçalho |  Arrastar o mouse para cima/para baixo |  Thumbstick direita/para baixo | 
|  Rolo de cabeçalho |  P/E |  DPad esquerda/direita | 
|  Mão/controlador X |  ALT + A/D |  Tiracolo + esquerda Thumbstick esquerda/direita | 
|  Mão/controlador Y |  Alt + Page up/Page Down |  Tiracolo + DPad para cima/para baixo | 
|  Mão/controlador Z |  ALT + W/S |  Tiracolo + esquerdo Thumbstick para cima/para baixo | 
|  Desvio da mão/controlador |  Alt + arrastar mouse para a esquerda/direita |  Tiracolo + direita Thumbstick esquerda/direita | 
|  Densidade da mão/controlador |  Alt + arrastar mouse para cima/para baixo |  Tiracolo + direita Thumbstick para cima/para baixo | 
|  Distribuição à mão/controlador |  ALT + Q/E |  Tiracolo + DPad à esquerda/direita | 
|  Ação |  Botão direito do mouse |  Gatilho | 
|  Flor/sistema/página inicial |  F2 ou tecla do Windows |  Botão B | 
|  Redefinir |  Escape |  botão Iniciar | 
|  Acompanhamento |  T |  Botão X | 
|  Rolagem |  Alt + botão direito do mouse + arrastar o mouse para cima/para baixo |  Tiracolo + gatilho + Thumbstick direita/inativo | 
|  Mover/girar mais rápido | Tecla SHIFT esquerda ou direita | Pressione e segure a Thumbstick correta |
|  Mover/girar lentamente | Tecla CTRL esquerda ou direita | Pressionar e manter o Thumbstick esquerdo |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Usando controladores de movimentos e o headset imersivo do Windows Mixed Reality com o Emulador do HoloLens 2

Ao usar um headset de imersão de realidade mista do Windows com o emulador do HoloLens 2, a movimentação e a rotação são mapeadas automaticamente para movimento e rotação do headset.  A posição e a orientação do controlador de movimento são mapeadas automaticamente para a posição e orientação da mão no emulador.  A tabela a seguir lista as ações adicionais disponíveis ao usar um controlador de movimento.

> [!NOTE]
> Ao usar um headset, os controles teclado padrão, mouse e gamepad são ignorados automaticamente.

|  Operação |  Ação |  Observações | 
|----------|----------|----------|
|  Corpo X |  Thumbstick esquerda/direita |   | 
|  Corpo Z |  Avançar/voltar Thumbstick |   | 
|  Corpo Y |  /Down de página de teclado para cima | Verifique se o Windows Mixed Reality tem foco.  Pressione Win + Y se o foco estiver na área de trabalho do Windows para retornar o foco para a realidade mista do Windows. |
|  Olhos olhar para a esquerda/direita |  DPad esquerda/direita | |
|  Olhar para cima/para baixo | DPad para cima/para baixo | |
|  Toque | Gatilho | |
|  Pinçar/entender | Botão de fixação | |
|  Gesto do sistema | Botão Menu | |
|  Redefinir posição | Thumbstick clique em | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Atalhos de teclado do painel de controle da simulação de percepção

Você pode acessar o painel de controle de simulação de percepção e habilitar ou desabilitar dispositivos de entrada do PC com os seguintes atalhos de teclado.

| Operação | Atalho | Descrição/observações |
|-----------|----------|-------------|
| Alternar ' usar teclado para simulação ' | F4 | Quando desativado, a entrada do teclado vai para o aplicativo do HoloLens ou do Windows Mixed Reality. |
| Alternar ' usar o mouse para simulação ' | F5 | Quando desativado, a entrada do mouse vai para o ambiente de realidade misturada (apenas para a realidade mista do Windows) |
| Alternar ' usar o gamepad para simulação ' | F6 | Quando desativado, a entrada de gamepad é ignorada por simulação |
| Mostrar ou ocultar o painel de controle | F7 | |
| Definir o foco do teclado para o painel de controle | F8 | Se o painel não estiver visível no momento, ele será mostrado primeiro. |
| Encaixar ou desencaixar o painel de/para o emulador ou a janela do portal da realidade misturada | F9 | Se a janela for fechada quando desencaixada, ela será encaixada e ocultada. |

## <a name="see-also"></a>Veja também
* [Instalar as ferramentas](../install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como usar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
