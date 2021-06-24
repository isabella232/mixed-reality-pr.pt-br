---
title: Serviços de simulação de entrada
description: Documentação sobre o serviço de simulação de entrada no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 5420f3f2d20d07585007a58f5cf70d8e2027efc6
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588840"
---
# <a name="input-simulation-service"></a>Serviço de simulação de entrada

![Simulação de entrada MRTK](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

Com a simulação de entrada do MRTK, você pode testar vários tipos de interações no editor do Unity sem compilar e implantar em um dispositivo. Isso permite que você itere rapidamente suas ideias no processo de design e desenvolvimento. Use combinações de teclado e mouse para controlar as entradas simuladas.

O serviço de simulação de entrada emula o comportamento de dispositivos e plataformas que podem não estar disponíveis no editor do Unity. Os exemplos incluem:

* Rastreamento de cabeça do dispositivo HoloLens ou VR
* Gestos do HoloLens Hand
* Acompanhamento de mão articulada 2 do HoloLens
* Acompanhamento de olho do HoloLens 2
* Controladores de dispositivo VR

> [!WARNING]
> Isso não funciona ao usar o modo de emulação de > de emulação de Holographic do Unity = "simular no editor". A simulação no editor do Unity assumirá o controle da simulação de entrada do MRTK. Para usar o serviço de simulação de entrada do MRTK, você precisará definir a emulação de Holographic de XR para o modo de emulação = *"nenhum"*

## <a name="how-to-use-mrtk-input-simulation"></a>Como usar a simulação de entrada do MRTK 

A simulação de entrada é habilitada por padrão nos perfis fornecidos com MRTK. Você pode simplesmente clicar no botão **executar** para executar a cena com suporte à simulação de entrada.

* Pressione **W, A, S, D, Q e** as teclas e para mover a câmera.
* Mantenha o **botão direito do mouse** e mova o mouse para examinar.
* Para exibir as mãos simuladas, pressione a **barra de espaço (à direita)** ou a **tecla SHIFT esquerda (à esquerda)**
* Para manter as mãos simuladas na exibição, pressione **T** ou a tecla **Y**
* Para girar as mãos simuladas, pressione e segure a **tecla CTRL** e mova o mouse

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a>Na folha de consulta de simulação de entrada do editor

Pressione **Ctrl + H** na cena HandInteractionExamples para abrir uma folha de consulta com controles de simulação de entrada.

> ![Roteiro de MRTK de simulação de entrada](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a>Habilitando o serviço de simulação de entrada

Na configuração do provedor de dados do sistema de entrada, o serviço de simulação de entrada pode ser configurado com o seguinte.

* O **tipo** deve ser *Microsoft. MixedReality. Toolkit. Input > InputSimulationService*.
* As **plataformas com suporte** por padrão incluem todas as plataformas do *Editor* , já que o serviço usa teclado e entrada do mouse.

> [!NOTE]
> O serviço de simulação de entrada pode ser usado em outros pontos de extremidade de plataforma, como autônomo, alterando a propriedade de **plataforma (s) com suporte** para incluir os destinos desejados.
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a>Controle de câmera

A movimentação de cabeçalho pode ser emulada pelo serviço de simulação de entrada.

### <a name="rotating-the-camera"></a>Girando a câmera

1. Passe o mouse sobre a janela do editor do visor.
    *Talvez seja necessário clicar na janela para dar um foco de entrada se os pressionamentos de botão não funcionarem.*
1. Pressione e segure o **botão de aparência do mouse** (padrão: botão direito do mouse).
1. Mova o mouse na janela do visor para girar a câmera.
1. Use a roda de rolagem para rolar a câmera pela direção da exibição.

A velocidade de rotação da câmera pode ser configurada alterando a configuração de **velocidade de aparência do mouse** no perfil de simulação de entrada.

Como alternativa, use a aparência **horizontal** / com eixos **verticais** para girar a câmera (padrão: Game Controller Right Thumbstick).

### <a name="moving-the-camera"></a>Movimentação da câmera

Use os eixos verticais mover **horizontalmente** /  para mover a câmera (padrão: WASD chaves ou controlador de jogo para a esquerda Thumbstick).

A posição da câmera e os ângulos de rotação também podem ser definidos explicitamente na janela ferramentas. A câmera pode ser redefinida para o padrão usando o botão **Redefinir** .

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>Simulação de controlador

A simulação de entrada dá suporte a dispositivos de controlador emulados (ou seja, controladores de movimento e mãos). Esses controladores virtuais podem interagir com qualquer objeto que ofereça suporte a controladores regulares, como botões ou objetos que podem ser capturados.

### <a name="controller-simulation-mode"></a>Modo de simulação do controlador

Na [janela ferramentas de simulação de entrada](#input-simulation-tools-window) , a configuração do modo de simulação do **controlador padrão** alterna entre três modelos de entrada distintos. Esse modo padrão também pode ser definido no perfil de simulação de entrada.

* *Mãos articuladas*: simula um dispositivo de mão totalmente articulado com dados de posição conjunta.

   Emula o modelo de interação do HoloLens 2.

   As interações que se baseiam no posicionamento preciso da mão ou usam o toque podem ser simuladas nesse modo.

* *Gestos de mão*: simula um modelo de mão simplificado com toque de ar e gestos básicos.

   Emula o [modelo de interação do HoloLens](/windows/mixed-reality/gestures).

   O foco é controlado usando o ponteiro olhar. O gesto de *toque do ar* é usado para interagir com botões.

* *Controlador de movimento*: simula um controlador de movimento usado com headsets VR que funciona de forma semelhante a interações com mãos articuladas.

   Emula o headset de VR com o modelo de interação de controladores.

   O gatilho, as teclas de captura e de menu são simuladas por meio de entrada de teclado e mouse.

### <a name="simulating-controller-movement"></a>Simulando a movimentação do controlador

Pressione e segure a **tecla de manipulação do controlador à esquerda/direita** (padrão: *deslocamento à* esquerda para o controlador esquerdo e o *espaço* para o controlador direito) para obter o controle de qualquer controlador. Enquanto a tecla de manipulação for pressionada, o controlador aparecerá no visor. Depois que a chave de manipulação for liberada, os controladores desaparecerão após um curto **tempo limite de ocultar controlador**.

Os controladores podem ser ativados e congelados em relação à câmera na [janela ferramentas de simulação de entrada](#input-simulation-tools-window) ou pressionando a **tecla ativar/desativar chave do controlador** (padrão: *T* para esquerda e *Y* para direita). Pressione a tecla de alternância novamente para ocultar os controladores novamente. Para manipular os controladores, a **chave de manipulação do controlador à esquerda/direita** precisa ser mantida. Tocar duas vezes na **tecla de manipulação do controlador à esquerda/direita** também pode ativar/desativar os controladores.

O movimento do mouse moverá o controlador no plano de exibição. Os controladores podem ser movidos mais ou mais perto da câmera usando a **roda do mouse**.

Para girar os controladores usando o mouse, mantenha a **tecla de manipulação do controlador à esquerda/direita** (*deslocamento à esquerda* ou o *espaço*) *e* o **botão de rotação do controlador** (padrão: botão *CTRL esquerda* ) e, em seguida, mova o mouse para girar o controlador. A velocidade de rotação do controlador pode ser configurada alterando a configuração de **velocidade de rotação do controlador do mouse** no perfil de simulação de entrada.

Todo o posicionamento manual também pode ser alterado na [janela ferramentas de simulação de entrada](#input-simulation-tools-window), incluindo redefinição de mãos para padrão.

### <a name="additional-profile-settings"></a>Configurações de perfil adicionais

* O **multiplicador de profundidade do controlador** controla a sensibilidade da movimentação de profundidade da roda de rolagem do mouse. Um número maior acelerará o zoom do controlador.
* A **distância do controlador padrão** é a distância inicial dos controladores da câmera. Clicar nos controladores de botão **Redefinir** também irá posicionar os controladores nessa distância.
* O **valor de Tremulação do controlador** adiciona movimento aleatório aos controladores. Esse recurso pode ser usado para simular o controle de controlador impreciso no dispositivo e garantir que as interações funcionem bem com entradas ruidosas.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>Gestos de mão

Gestos de mão como pinçagem, captura, investigar, etc. também podem ser simulados.

1. Habilitar o controle de mão usando a **tecla de manipulação do controlador à esquerda/direita** (*deslocamento à esquerda* ou *espaço*)

2. Durante a manipulação, pressione e mantenha pressionado um botão do mouse para executar um gesto de mão.

Cada um dos botões do mouse pode ser mapeado para transformar a forma mão em um gesto diferente usando as configurações de *gesto esquerdo/médio/direito do mouse* . O *gesto de mão padrão* é a forma da mão quando nenhum botão é pressionado.

> [!NOTE]
> O gesto de *pinçar* é o único gesto que executa a ação "selecionar" neste ponto.

### <a name="one-hand-manipulation"></a>Manipulação unidirecional

1. Pressione e mantenha a **tecla de manipulação da controladora esquerda/direita** (*SHIFT esquerda* ou *espaço*)
2. Ponto no objeto
3. Mantenha o botão do mouse para pinçar
4. Use o mouse para mover o objeto
5. Solte o botão do mouse para parar a interação

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>Manipulação de duas mãos

Para manipular objetos com duas mãos ao mesmo tempo, o modo de mão persistente é recomendado.

1. Ative as duas mãos pressionando as teclas de alternância (*T/Y*).
1. Manipule uma mão por vez:
    1. Mantenha **espaço** para controlar a mão direita
    1. Mover a mão para onde você deseja obter o objeto
    1. Pressione o **botão esquerdo do mouse** para ativar o gesto de *pinçar* .
    1. Liberar **espaço** para parar de controlar a mão direita. A mão será congelada no local e ficará bloqueada no gesto de *pinçar* , já que ele não está mais sendo manipulado.
1. Repita o processo com a outra mão, capturando o mesmo objeto em um segundo ponto.
1. Agora que ambas as mãos estão captando o mesmo objeto, você pode mover qualquer um deles para executar a manipulação de duas mãos.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>Interação de GGV (olhar, gesto e voz)

Por padrão, a interação GGV é habilitada no editor enquanto não há nenhuma mão articulada presente na cena.

1. Girar a câmera para apontar o cursor olhar no objeto que interage (botão direito do mouse)
1. Clique e mantenha o **botão esquerdo do mouse** para interagir
1. Gire a câmera novamente para manipular o objeto

Você pode desativar isso alternando a opção *é mão habilitada para entrada livre* dentro do perfil de simulação de entrada.

Além disso, você pode usar as mãos simuladas para a interação GGV

1. Habilitar a simulação de GGV alternando o **modo de simulação** para *gestos* no [perfil de simulação de entrada](#enabling-the-input-simulation-service)
1. Girar a câmera para apontar o cursor olhar no objeto que interage (botão direito do mouse)
1. Mantenha **espaço** para controlar a mão direita
1. Clique e mantenha o **botão esquerdo do mouse** para interagir
1. Use o mouse para mover o objeto
1. Solte o botão do mouse para parar a interação

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>Gerando eventos teleport

Para gerar o evento teleport na simulação de entrada, defina as configurações de gesto da mão no perfil de simulação de entrada para que um execute o gesto de **início teleport** enquanto o outro executa o gesto de **término teleport** . O gesto de **início de teleport** abrirá o ponteiro teleport, enquanto o Gesure **teleport end** concluirá a ação teleport e moverá o usuário.

A posição y de seu teleport resultante depende do deslocamento da câmera ao longo do eixo y. No editor, isso é 0 por padrão. portanto, use as teclas **Q** e **e** para ajustá-la à altura apropriada.

![Configurações de teleport de simulação de entrada](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>Interação do controlador de movimento

Os controladores de movimento simulados podem ser manipulados da mesma forma que as mãos articuladas. O modelo de interação é semelhante à interação extrema da mão articulada enquanto o gatilho, as teclas de captura e de menu são mapeadas para o *botão esquerdo do mouse*, a tecla *G* e *M* , respectivamente.

### <a name="eye-tracking"></a>Acompanhamento ocular

A [simulação de acompanhamento de olho](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) pode ser habilitada verificando a opção **simular posição de olho** no perfil de simulação de [entrada](#enabling-the-input-simulation-service). Isso não deve ser usado com interações de estilo de controlador de movimento ou GGV (portanto, certifique-se de que o **modo de simulação de controlador padrão** esteja definido para a *mão articulada*).

## <a name="input-simulation-tools-window"></a>Janela de ferramentas de simulação de entrada

Habilite a janela ferramentas de simulação de entrada do menu de simulação de entrada do kit de ferramentas da **realidade misturada**  >    >    >   . Esta janela fornece acesso ao estado da simulação de entrada durante o modo de reprodução.

## <a name="viewport-buttons-optional"></a>Botões do visor (opcional)

Um pré-fabricado para botões no editor para controlar o posicionamento básico pode ser especificado no perfil de simulação de entrada em **indicadores pré-fabricado**. Esse é um utilitário opcional, os mesmos recursos podem ser acessados na [janela ferramentas de simulação de entrada](#input-simulation-tools-window).

> [!NOTE]
> Os indicadores do visor são desabilitados por padrão, pois eles podem, às vezes, interferir nas interações da interface do usuário do Unity. Consulte o problema [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106). Para habilitar, adicione InputSimulationIndicators pré-fabricado aos **indicadores pré-fabricado**.

Os ícones de mão mostram o estado das mãos simuladas:

* ![Ícone de mão não controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) A mão não está acompanhando. Clique para habilitar a mão.
* ![Ícone de mão controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Ícone de mão controlada") A mão é controlada, mas não é controlada pelo usuário. Clique para ocultar a mão.
* ![Ícone de mão controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Ícone de mão controlada") A mão é controlada e controlada pelo usuário. Clique para ocultar a mão.
* ![Ícone de redefinir mão](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Ícone de redefinir mão") Clique para redefinir a mão para a posição padrão.


## <a name="see-also"></a>Confira também

* [Perfil do sistema de entrada](../input/input-providers.md).