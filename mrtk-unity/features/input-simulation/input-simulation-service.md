---
title: Serviço de simulação de entrada
description: Documentação sobre o serviço de simulação de entrada no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f329cceded5e510d3d4fc1a1c13b5a504f1f3669ad408b733267595e77dd15a6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227562"
---
# <a name="input-simulation-service"></a>Serviço de simulação de entrada

![Simulação de entrada do MRTK](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

Com a simulação de entrada do MRTK, você pode testar vários tipos de interações no editor do Unity sem compilar e implantar em um dispositivo. Isso permite que você itere rapidamente suas ideias no processo de design e desenvolvimento. Use combinações de teclado e mouse para controlar as entradas simuladas.

O Serviço de Simulação de Entrada emula o comportamento de dispositivos e plataformas que podem não estar disponíveis no editor do Unity. Os exemplos incluem:

* HoloLens ou controle de cabeça do dispositivo VR
* HoloLens gestos de mão
* HoloLens 2 acompanhamento de mão articulado
* HoloLens acompanhamento ocular 2
* Controladores de dispositivo VR

> [!WARNING]
> Isso não funciona ao usar a Emulação Holográfica XR do Unity > Modo de Emulação = "Simular no Editor". A simulação no editor do Unity assumirá o controle da simulação de entrada do MRTK. Para usar o serviço de simulação de entrada do MRTK, você precisará definir a Emulação Holográfica do XR para o Modo de Emulação = *"Nenhum"*

## <a name="how-to-use-mrtk-input-simulation"></a>Como usar a simulação de entrada do MRTK 

A simulação de entrada é habilitada por padrão nos perfis que são fornecidas com o MRTK. Você pode simplesmente clicar **no botão Reproduzir** para executar a cena com suporte à simulação de entrada.

* Pressione as teclas **W, A, S, D, Q, E** para mover a câmera.
* Mantenha o **Botão direito do mouse** pressionado e mova o mouse para examinar.
* Para exibir as mãos simuladas, pressione **Barra de espaço (à direita)** ou **tecla SHIFT esquerda**
* Para manter as mãos simuladas no modo de exibição, pressione as teclas **T** ou **Y**
* Para girar as mãos simuladas, pressione e mantenha pressionada a **tecla Ctrl e** mova o mouse

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a>Folha de ida e saída da simulação de entrada do editor

Pressione **Ctrl esquerdo + H** na cena HandInteractionExamples para abrir uma folha de reprodução com controles de simulação de entrada.

> ![Folha de dados de simulação de entrada do MRTK](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a>Habilitando o serviço de simulação de entrada

Na configuração do provedor de dados do sistema de entrada, o serviço de Simulação de Entrada pode ser configurado com o seguinte.

* **O** tipo deve *ser Microsoft.MixedReality.Toolkit. Entrada > InputSimulationService*.
* **As plataformas com suporte por** padrão incluem todas as plataformas *do Editor,* pois o serviço usa a entrada do teclado e do mouse.

> [!NOTE]
> O serviço de Simulação de Entrada pode ser usado em outros pontos de extremidade de plataforma, como autônomos, alterando a propriedade **Plataformas** com Suporte para incluir os destinos desejados.
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a>Controle de câmera

O movimento de cabeça pode ser emulado pelo Serviço de Simulação de Entrada.

### <a name="rotating-the-camera"></a>Girar a câmera

1. Passe o mouse sobre a janela do editor do viewport.
    *Talvez seja necessário clicar na janela para dar a ela o foco de entrada se as teclas de botão não funcionarem.*
1. Pressione e mantenha pressionado o **Botão de Aparência do Mouse** (padrão: botão direito do mouse).
1. Mova o mouse na janela do viewport para girar a câmera.
1. Use a roda de rolagem para rolar a câmera em torno da direção da exibição.

A velocidade de rotação da câmera pode ser configurada alterando a **configuração Velocidade** de Aparência do Mouse no perfil de simulação de entrada.

Como alternativa, use os eixos Vertical de Aparência **Horizontal** para girar a câmera (padrão: miniatura direita do /  controlador de jogo).

### <a name="moving-the-camera"></a>Movimentação da câmera

Use os **eixos Mover** / **Horizontalmente Verticalmente** para mover a câmera (padrão: chaves WASD ou o controle de jogo à esquerda).

Os ângulos de posição e rotação da câmera também podem ser definidos explicitamente na janela de ferramentas. A câmera pode ser redefinida para seu padrão usando o **botão Redefinir.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>Simulação do controlador

A simulação de entrada dá suporte a dispositivos controladores emulados (ou seja, controladores de movimento e mãos). Esses controladores virtuais podem interagir com qualquer objeto que dá suporte a controladores regulares, como botões ou objetos que podem ser capturados.

### <a name="controller-simulation-mode"></a>Modo de simulação do controlador

Na janela ferramentas [de simulação de entrada,](#input-simulation-tools-window) a **configuração Modo de** Simulação do Controlador Padrão alterna entre três modelos de entrada distintos. Esse modo padrão também pode ser definido no perfil de simulação de entrada.

* *Mãos articuladas:* simula um dispositivo de mão totalmente articulado com dados de posição conjunta.

   Emula HoloLens modelo de interação 2.

   As interações baseadas no posicionamento preciso da mão ou no toque de uso podem ser simuladas nesse modo.

* *Gestos de mão:* simula um modelo de mão simplificado com toque de ar e gestos básicos.

   Emula HoloLens [de interação.](/windows/mixed-reality/gestures)

   O foco é controlado usando o ponteiro De foco. O *gesto de toque* de ar é usado para interagir com botões.

* *Controlador de Movimento:* simula um controlador de movimento usado com headsets vr que funciona de forma semelhante a interações distantes com mãos articuladas.

   Emula o headset VR com o modelo de interação de controladores.

   As teclas de gatilho, de captura e de menu são simuladas por meio da entrada do teclado e do mouse.

### <a name="simulating-controller-movement"></a>Simulando a movimentação do controlador

Pressione e mantenha pressionada a Tecla de Manipulação do  Controlador **esquerdo/direito** (padrão:  Deslocamento para a esquerda para o controlador esquerdo e Espaço para o controlador direito) para obter controle de qualquer controlador. Enquanto a tecla de manipulação é pressionada, o controlador aparecerá no viewport. Depois que a chave de manipulação for liberada, os controladores desaparecerão depois de um curto Tempo de O tempo **de ocultação do controlador.**

Os controladores podem ser alternados e congelados em relação à câmera na janela de ferramentas de simulação de entrada ou pressionando a tecla Alternar Para a **esquerda/direita** do controlador (padrão: [](#input-simulation-tools-window) *T* para a esquerda e *Y* para a direita). Pressione a tecla de alternância novamente para ocultar os controladores novamente. Para manipular os controladores, a chave de manipulação do controlador **esquerdo/direito** precisa ser mantida. Tocar duas vezes **na Tecla de Manipulação do** Controlador Para a Esquerda/Direita também pode alternar os controladores para cima/para fora.

O movimento do mouse move o controlador no plano de exibição. Os controladores podem ser movidos para mais ou mais perto da câmera usando a roda **do mouse**.

Para girar controladores usando o mouse, mantenha a Tecla de Manipulação do Controlador **esquerdo/direito** *(Deslocamento* à Esquerda ou Espaço) e o Botão Girar do Controlador **(padrão:** botão *Ctrl* à Esquerda) e mova o mouse para girar o controlador.   A velocidade de rotação do controlador pode ser configurada alterando a configuração Velocidade de Rotação do Controlador do **Mouse** no perfil de simulação de entrada.

Todo o posicionamento de mão também pode ser alterado na janela [de ferramentas de simulação de entrada](#input-simulation-tools-window), incluindo a redefinição de mãos para o padrão.

### <a name="additional-profile-settings"></a>Configurações de perfil adicionais

* **O Multiplicador de Profundidade do Controlador** controla a sensibilidade do movimento de profundidade da roda de rolagem do mouse. Um número maior acelerará o zoom do controlador.
* **A distância padrão do** controlador é a distância inicial dos controladores da câmera. Clicar nos **controladores** de botão Redefinir também colocará os controladores a essa distância.
* **A Quantidade de Tremeia** do Controlador adiciona movimento aleatório aos controladores. Esse recurso pode ser usado para simular o acompanhamento impreciso do controlador no dispositivo e garantir que as interações funcionem bem com entrada com barulhento.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>Gestos de mão

Gestos de mão, como pinçar, segurar, a pinçar etc. também podem ser simulados.

1. Habilitar o controle de mão usando a tecla de manipulação do **controlador esquerdo/direito** (*deslocamento à esquerda* ou *espaço*)

2. Ao manipular, pressione e segure um botão do mouse para executar um gesto de mão.

Cada um dos botões do mouse pode ser mapeado para transformar a forma da mão em um gesto diferente usando as configurações de Gesto da Mão *esquerda/intermediária/direita* do mouse. O *Gesto de Mão* Padrão é a forma da mão quando nenhum botão é pressionado.

> [!NOTE]
> O *gesto de* pinçar é o único gesto que executa a ação "Selecionar" neste ponto.

### <a name="one-hand-manipulation"></a>Manipulação de uma mão

1. Pressione e mantenha **pressionada a tecla de manipulação do controlador esquerdo/direito** *(deslocamento à esquerda* ou *espaço)*
2. Objeto ponto a ponto
3. Mantenha o botão do mouse pressionado para pinçar
4. Use o mouse para mover o objeto
5. Liberar o botão do mouse para interromper a interação

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>Manipulação de duas mãos

Para manipular objetos com duas mãos ao mesmo tempo, o modo de mão persistente é recomendado.

1. Alterne em ambas as mãos pressionando as teclas de alternância (*T/Y*).
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

para gerar o evento teleport na simulação de entrada, configure o gesto de mão Configurações no perfil de simulação de entrada para que um execute o gesto de **início teleport** enquanto o outro executa o gesto de **término teleport** . O gesto de **início de teleport** abrirá o ponteiro teleport, enquanto o Gesure **teleport end** concluirá a ação teleport e moverá o usuário.

A posição y de seu teleport resultante depende do deslocamento da câmera ao longo do eixo y. No editor, isso é 0 por padrão. portanto, use as teclas **Q** e **e** para ajustá-la à altura apropriada.

![Configurações de simulação de entrada Teleport](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>Interação do controlador de movimento

Os controladores de movimento simulados podem ser manipulados da mesma forma que as mãos articuladas. O modelo de interação é semelhante à interação extrema da mão articulada enquanto o gatilho, as teclas de captura e de menu são mapeadas para o *botão esquerdo do mouse*, a tecla *G* e *M* , respectivamente.

### <a name="eye-tracking"></a>Acompanhamento ocular

A [simulação de acompanhamento de olho](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) pode ser habilitada verificando a opção **simular posição de olho** no perfil de simulação de [entrada](#enabling-the-input-simulation-service). Isso não deve ser usado com interações de estilo de controlador de movimento ou GGV (portanto, certifique-se de que o **modo de simulação de controlador padrão** esteja definido para a *mão articulada*).

## <a name="input-simulation-tools-window"></a>Janela de ferramentas de simulação de entrada

habilite a janela ferramentas de simulação de entrada do menu de simulação de entrada da **realidade misturada**  >  **Toolkit**  >  **Utilities**  >   . Esta janela fornece acesso ao estado da simulação de entrada durante o modo de reprodução.

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
