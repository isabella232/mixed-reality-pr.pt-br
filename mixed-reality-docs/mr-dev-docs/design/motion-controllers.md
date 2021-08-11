---
title: Controladores de movimento
description: Saiba como configurar, emparelhar e gerenciador interações de entrada usando controladores de movimento de Realidade Misturada em seus aplicativos.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof controllers, motion controllers, pairing, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, scrolling, grip, state
ms.openlocfilehash: bced0115eee5e753ef01d129ae10910acdca2b7b91020117f53b2ebf8833a130
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224862"
---
# <a name="motion-controllers"></a>Controladores de movimento

:::row:::
    :::column:::
        Os controladores de movimento [são acessórios de hardware](../discover/hardware-accessories.md) que permitem aos usuários tomar medidas na realidade misturada. Uma vantagem dos controladores de movimento em relação aos [gestos](gaze-and-commit.md#composite-gestures) é que os controladores têm uma posição precisa no espaço, permitindo uma interação fina com objetos digitais. Por Windows Mixed Reality headsets imersivos, os controladores de movimento são a principal maneira como os usuários tomarão medidas em seu mundo.<br>
        <br>
        *Imagem: um controlador Windows Mixed Reality de movimento*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality de movimento](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

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
     <td>Controladores de movimento</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Detalhes do hardware

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality de movimento oferecem acompanhamento de movimento preciso e responsivo em seu campo de exibição usando os sensores no headset imersivo. Não é necessário instalar o hardware nas paredes em seu espaço. Esses controladores de movimento oferecerão a mesma facilidade de configuração e portabilidade que Windows Mixed Reality headsets imersivos. Nossos parceiros de dispositivo planejam comercializar e vender esses controladores em prateleiras de varejo neste feriado.

![Conheça seu controlador](images/controllerimage-750px.png)<br>
*Conheça seu controlador*

**Recursos:**
* Acompanhamento óptico
* Gatilho
* Botão Segurar
* Manípulo
* Touchpad

## <a name="setup"></a>Instalação

### <a name="before-you-begin"></a>Antes de começar

**Você precisará do seguinte:**
* Um conjunto de dois controladores de movimento.
* Quatro baterias AA.
* Um computador com suporte Bluetooth 4.0.

**Verificar se Windows, Unity e atualizações de driver**
* Visite [Instalar as ferramentas para](../develop/install-the-tools.md) as versões preferenciais do Windows, Unity e assim por diante, para desenvolvimento de realidade misturada.
* Certifique-se de ter os drivers de headset e controlador de movimento mais [atualizados.](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)

### <a name="pairing-controllers"></a>Controladores de emparelhamento

Os controladores de movimento podem ser conectados ao computador host usando Windows configurações como qualquer outro Bluetooth dispositivo.

1. Insira duas baterias AA na parte traseira do controlador. Deixe a tampa da bateria desligada por enquanto.
2. Se você estiver usando um Adaptador de Bluetooth USB externo em vez de um rádio Bluetooth interno, revise as práticas recomendadas Bluetooth [antes](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) de continuar. Para a configuração da área de trabalho com rádio interna, verifique se a antena está conectada.
3. Abra **Windows Configurações** Dispositivos Adicionar Bluetooth ou outro dispositivo Bluetooth e remova quaisquer instâncias anteriores de "Controlador de movimento – Direita" e "Controlador de movimento  ->    ->    ->   – Esquerda". Verifique também a categoria Outros dispositivos na parte inferior da lista.
4. Selecione **Adicionar Bluetooth ou outro dispositivo e** veja-o começando a descobrir Bluetooth dispositivos.
5. Pressione e segure o botão de Windows controlador para ativar o controlador, solte-o quando ele tocar.
6. Pressione e mantenha pressionado o botão de emparelhamento (guia no compartimento da bateria) até que os LEDs comecem a pulsar.

:::row:::
    :::column:::
7. Aguarde "Controlador de movimento – Esquerda" ou "Controlador de movimento – Direita" para aparecer na parte inferior da lista. Selecione para emparelhar. O controlador vibrará uma vez quando conectado.<br>
        <br>
        *Imagem: selecione "Controlador de movimento" para emparelhar; se houver várias instâncias, selecione uma na parte inferior da lista*
    :::column-end:::
        :::column:::
       ![Selecione Controlador de movimento para emparelhar, se várias instâncias selecionarem uma na parte inferior da lista](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. Você verá o controlador aparecer nas configurações Bluetooth **"Mouse, teclado e & caneta"** como **Conectado.** Neste ponto, você pode obter uma atualização de firmware – consulte a [próxima seção](motion-controllers.md#updating-controller-firmware).
9. Reatta a tampa da bateria.
10. Repita as etapas de 1 a 9 para o segundo controlador.

<br>

:::row:::
    :::column:::
        Depois de emparelhar com êxito os dois controladores, suas configurações deverão ser a seguinte, na categoria **"Mouse, teclado e & caneta"** <br>
        <br>
        *Imagem: controladores de movimento conectados*
    :::column-end:::
        :::column:::
       ![Controladores de movimento conectados](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

Se os controladores são desligados após o emparelhamento, seu status aparece como Emparelhado. Para controladores permanentemente na categoria "Outros dispositivos", o emparelhamento pode ter sido concluído apenas parcialmente. Nesse caso, execute as etapas de emparelhamento novamente para obter o controlador funcional.

### <a name="updating-controller-firmware"></a>Atualizando o firmware do controlador

* Se um headset imersivo estiver conectado ao seu computador com o novo firmware do controlador estiver disponível, o firmware será enviado automaticamente aos controladores de movimento na próxima vez que você a ligar. As atualizações de firmware do controlador são indicadas por um padrão de quadrantes de LED em movimento circular e levam de 1 a 2 minutos.


:::row:::
    :::column:::
* Depois que a atualização de firmware for concluída, os controladores serão reinicializados e reconectados. Ambos os controladores devem estar conectados agora. <br>
        <br>
        *Imagem: controladores conectados Bluetooth configurações*
    :::column-end:::
        :::column:::
       ![Controladores conectados](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* Verifique se os controladores funcionam corretamente:
    1. Iniciar **Portal de Realidade Misturada** e inserir sua Página Início da Realidade Misturada.
    2. Mova seus controladores e verifique se o acompanhamento, os botões de teste e a verificação de que a [operação funciona.](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Se não, confira solução de problemas do [controlador de movimento.](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)

## <a name="gazing-and-pointing"></a>Olhando e apontando

Windows Mixed Reality dá suporte a dois modelos principais para interação; **ata e commit** **e aponte e commit**:
* Com **o olhar e** a confirmação [](gaze-and-commit.md), os usuários direcionam um objeto com seu olhar e, em seguida, selecionam objetos com toques de ar à mão, um gamepad, um clicker ou sua voz.
* Com **o ponto e** a confirmação , um usuário pode apontar um controlador de movimento com capacidade de apontar para o objeto de destino e, em seguida, selecionar objetos com o gatilho do controlador.

Os aplicativos que dão suporte a apontar com controladores de movimento também devem habilitar interações controladas por olhar sempre que possível, para dar aos usuários uma opção em quais dispositivos de entrada eles usam.

### <a name="managing-recoil-when-pointing"></a>Gerenciando o recuo ao apontar

Ao usar controladores de movimento para apontar e fazer commit, os usuários usarão o controlador para direcionar e interagir ao efetuar o gatilho. Os usuários que efetuarem pull do gatilho podem acabar visando o controlador mais alto no final do pull do gatilho do que o esperado.

Para gerenciar qualquer tal recoil que possa ocorrer quando os usuários efetuarem pull do gatilho, seu aplicativo poderá ajustar seu raio de destino quando o valor do eixo análogo do gatilho ficar acima de 0,0. Em seguida, você pode tomar medidas usando esse raio de destino alguns quadros posteriormente depois que o valor do gatilho atingir 1,0, desde que a pressão final ocorra em uma janela de tempo curto. Ao usar o gesto de toque composto de nível [superior,](gaze-and-commit.md#composite-gestures)Windows gerenciará essa captura de raio de direcionamento e o tempo de vida para você.

## <a name="grip-pose-vs-pointing-pose"></a>Pose da mão versus pose apontando

Windows Mixed Reality dá suporte a controladores de movimento em diferentes fatores forma, com o design de cada controlador diferente em sua relação entre a posição da mão do usuário e a direção natural de "avançar" que os aplicativos devem usar para apontar ao renderizar o controlador.

Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada fonte de interação; a **pose de segurar** e o ponteiro **representam**.

### <a name="grip-pose"></a>Pose da mão

A **pose de mão** representa o local da mão de uma mão detectada por um HoloLens ou da mão que mantém um controlador de movimento.

Em headsets imersivos, a pose de segurar é mais bem usada para **renderizar** a mão do usuário ou um objeto mantido na mão do **usuário,** como um capacete ou umaada. A pose de mão também é usada ao visualizar um controlador de movimento, pois o modelo **renderizável** fornecido pelo Windows para um controlador de movimento usa a pose de mão como sua origem e centro de rotação.

A pose da mão é definida especificamente da seguinte forma:
* A **posição da mão:** o centroide da mão ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralar a posição dentro da mão. No controlador Windows Mixed Reality de movimento, essa posição geralmente se alinha ao botão Compreender.
* Eixo direito da orientação da **mão:** quando você abre completamente a mão para formar uma pose de cinco dedos simples, o raio que é normal para sua mão (para frente da mão esquerda, para trás da mão direita)
* Eixo **de** avanço da orientação da mão: quando você fecha a mão parcialmente (como se estivesse segurando o controlador), o raio que aponta para "para frente" pelo sinal formado pelos dedos não polegares.
* Eixo **para cima da orientação da** mão: o eixo Para cima implícito nas definições Direita e Avanço.

### <a name="pointer-pose"></a>Pose de ponteiro

A **pose do ponteiro** representa a ponta do controlador que está apontando para frente.

A pose de ponteiro fornecida pelo sistema é mais bem usada para Raycast quando você está **renderizando o próprio modelo de controlador**. Se você estiver renderizando algum outro objeto virtual no lugar do controlador, como uma arma virtual, você deve apontar com um raio mais natural para esse objeto virtual, como um Ray que viaja ao longo do cilindro do modelo de pressão definido pelo aplicativo. Como os usuários podem ver o objeto virtual e não o controlador físico, apontar com o objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.

## <a name="controller-tracking-state"></a>Estado de controle do controlador

como os headsets, o controlador de movimento de Windows Mixed Reality não requer nenhuma configuração de sensores de controle externo. Em vez disso, os controladores são acompanhados por sensores no próprio headset.

se o usuário mover os controladores para fora do campo de exibição do headset, na maioria dos casos Windows continuará inferir posições do controlador e fornecê-las ao aplicativo. Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.

Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna. Muitos aplicativos que usam controladores para apontar e ativar elementos de interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>Raciocínio sobre o estado de rastreamento explicitamente

Os aplicativos que desejam tratar as posições de forma diferente com base no estado de controle podem ir além e inspecionar as propriedades no estado do controlador, como SourceLossRisk e PositionAccuracy:

<table>
<tr>
<th> Estado de acompanhamento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisão</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Alta precisão (com risco de perda)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Precisão aproximada</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Sem posição</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> false</td>
</tr>
</table>

Esses Estados de acompanhamento do controlador de movimento são definidos da seguinte maneira:
* **Alta precisão:** Embora o controlador de movimento esteja dentro do campo de exibição do headset, ele geralmente fornecerá posições de alta precisão, com base no rastreamento visual. Um controlador móvel que deixa momentaneamente o campo de exibição ou que é momentaneamente obscurecido dos sensores do headset (por exemplo, pelo outro lado do usuário) continuará retornando poses de alta precisão por um curto período, com base no acompanhamento inércia do próprio controlador.
* **Alta precisão (com risco de perda):** Quando o usuário move o controlador de movimento para cima da borda do campo de exibição do headset, o headset em breve não será capaz de rastrear visualmente a posição do controlador. O aplicativo sabe quando o controlador atingiu esse limite de FOV vendo o **SourceLossRisk** REACH 1,0. Nesse ponto, o aplicativo pode optar por pausar gestos do controlador que exigem um fluxo constante de poses de alta qualidade.
* **Precisão aproximada:** Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada. Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna. Muitos aplicativos que usam controladores para apontar para e ativar elementos da interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba. Os aplicativos com requisitos de entrada mais pesados podem optar por detectar essa queda de **alta** precisão à precisão **aproximada** inspecionando a propriedade **PositionAccuracy** , por exemplo, para dar ao usuário um hitbox mais generosa em destinos fora da tela durante esse tempo.
* **Sem posição:** Embora o controlador possa operar com precisão aproximada por um longo tempo, às vezes o sistema sabe que até mesmo uma posição bloqueada pelo corpo não é significativa no momento. Por exemplo, um controlador que foi ativado pode nunca ter sido observado visualmente ou um usuário pode colocar um controlador selecionado por outra pessoa. Naqueles momentos, o sistema não fornecerá nenhuma posição ao aplicativo e **TryGetPosition** retornará false.

## <a name="interactions-low-level-spatial-input"></a>Interações: entrada espacial de nível baixo

As interações principais entre os controladores de mãos e de movimento são **Select**, **menu**, **Segure**, **Touchpad**, **Thumbstick** e **Home**.
* **Select** é a principal interação para ativar um holograma, que consiste em uma prensa seguida por uma versão. Para os controladores de movimento, você executa uma operação SELECT usando o gatilho do controlador. Outras maneiras de executar uma seleção são falando sobre o [comando de voz](voice-input.md) "Select". A mesma interação SELECT pode ser usada em qualquer aplicativo. Considere Select como o equivalente a um clique do mouse; uma ação universal que você aprende uma vez e, em seguida, se aplica em todos os seus aplicativos.
* O **menu** é a interação secundária para atuar em um objeto, usado para efetuar pull de um menu de contexto ou executar alguma outra ação secundária. Com os controladores de movimento, você pode executar uma ação de menu usando o botão de *menu* do controlador. (ou seja, o botão com o ícone de "menu" de "e".
* **Segure** é como os usuários podem agir diretamente em objetos à sua disposição para manipulá-los. Com os controladores de movimento, você pode fazer uma ação compreender apertando seu punho. Um controlador de movimento pode detectar um entendimento com um botão de captura, um gatilho de Palm ou outro sensor.
* O **Touchpad** permite que o usuário ajuste uma ação em duas dimensões ao longo da superfície do Touchpad de um controlador de movimento, confirmando a ação clicando no Touchpad. Os touchpads fornecem um estado pressionado, um estado tocado e coordenadas XY normalizadas. Intervalo X e Y de-1 a 1 no intervalo do Touchpad circular, com um centro em (0, 0). Para X,-1 está à esquerda e 1 está à direita. Para Y,-1 está na parte inferior e 1 está na parte superior.
* O **Thumbstick** permite que o usuário ajuste uma ação em duas dimensões movendo o Thumbstick de um controlador de movimento dentro de seu intervalo circular, confirmando a ação clicando em baixo no Thumbstick. Thumbsticks também fornece um estado pressionado e coordenadas XY normalizadas. Intervalo X e Y de-1 a 1 no intervalo do Touchpad circular, com um centro em (0, 0). Para X,-1 está à esquerda e 1 está à direita. Para Y,-1 está na parte inferior e 1 está na parte superior.
* **Home** é uma ação especial do sistema que é usada para voltar ao menu iniciar. é semelhante a pressionar a tecla Windows em um teclado ou o botão xbox em um controlador xbox. você pode ir para casa pressionando o botão Windows em um controlador de movimento. observe que você sempre pode retornar para começar dizendo "ei Cortana, Go Home". Os aplicativos não podem reagir especificamente às ações domésticas, pois elas são manipuladas pelo sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Gestos compostos: entrada espacial de alto nível

Os [gestos à mão](gaze-and-commit.md#composite-gestures) e os controladores de movimento podem ser acompanhados ao longo do tempo para detectar um conjunto comum de **[gestos compostos](gaze-and-commit.md#composite-gestures)** de alto nível. Isso permite que seu aplicativo detecte gestos de **toque**, **retenção**, **manipulação** e **navegação** de alto nível, se os usuários acabarem usando mãos ou controladores.

## <a name="rendering-the-motion-controller-model"></a>Renderizando o modelo do controlador de movimento

os **modelos de controlador 3d** Windows tornam disponíveis para aplicativos um modelo renderizado de cada controlador de movimento atualmente ativo no sistema. Ao fazer com que seu aplicativo carregue e articule dinamicamente esses modelos de controlador fornecidos pelo sistema em tempo de execução, você pode garantir que seu aplicativo seja compatível com todos os designs futuros do controlador.

É recomendável renderizar todos os modelos renderizados na **pose da alça** do controlador, uma vez que a origem do modelo é alinhada com esse ponto no mundo físico. Se você estiver renderizando modelos de controlador, você pode querer Raycast em sua cena na **pose do ponteiro**, que representa o raio ao longo do qual os usuários serão naturalmente informados, considerando o design físico do controlador.

Para obter mais informações sobre como carregar modelos de controlador dinamicamente no Unity, consulte a seção [renderizando o modelo de controlador de movimento no Unity](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) .

**arte de linhas do controlador 2D** Embora seja recomendável anexar as dicas e comandos do controlador no aplicativo aos próprios modelos do App Controller, alguns desenvolvedores podem querer usar representações de arte de linha 2D dos controladores de movimento em interface "tutorial" simples ou "instruções". Para esses desenvolvedores, fizemos .png arquivos de arte de linha do controlador de movimento disponíveis em preto e branco abaixo (clique com o botão direito do mouse para salvar).

![Visualização da arte de linhas de controladores de movimento](images/motioncontrollers-black-preview-300px.png)

[Controladores de movimento de resolução completa de linha artística em ' ' ' branco ' ' '](images/motioncontrollers-white.png)
 
[Controladores de movimento de resolução completa de linha artística em ' ' ' preto ' ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>Perguntas frequentes

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>Posso emparelhar os controladores de movimento com vários PCs?

Os controladores de movimento dão suporte ao emparelhamento com um único PC. Siga as instruções na [configuração do controlador de movimento](motion-controllers.md#setup) para emparelhar seus controladores.

### <a name="how-do-i-update-motion-controller-firmware"></a>Como fazer atualizar o firmware do controlador de movimento?

O firmware do controlador de movimento faz parte do driver do headset e será atualizado automaticamente na conexão, se necessário. as atualizações de Firmware normalmente levam 1-2 minutos, dependendo do Bluetooth a qualidade de link e de rádio. em casos raros, as atualizações de firmware do controlador podem levar até 10 minutos, o que pode indicar uma conectividade de Bluetooth deficiente ou interferência de rádio. consulte [Bluetooth práticas recomendadas no guia de entusiastas](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) para solucionar problemas de conectividade. Depois de uma atualização de firmware, os controladores serão reinicializados e reconectados ao PC host (você pode notar que os LEDs são mais brilhantes para acompanhamento). Se uma atualização de firmware for interrompida (por exemplo, os controladores perderão energia), ela será tentada novamente na próxima vez em que os controladores estiverem ligados.

### <a name="how-i-can-check-battery-level"></a>Como posso verificar o nível da bateria?

Na página [Windows Mixed Reality ,](../discover/navigating-the-windows-mixed-reality-home.md)você pode ligar o controlador para ver o nível da bateria no lado inverso do modelo virtual. Não há nenhum indicador de nível de bateria físico.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Você pode usar esses controladores sem um headset? Apenas para a entrada de gatilho/gatilho/etc?

Não para aplicativos Windows Universal.

## <a name="troubleshooting"></a>Solução de problemas

Confira [solução de problemas do controlador de](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) movimento no Guia de Enthusiast.

## <a name="filing-motion-controller-feedbackbugs"></a>Arquivar comentários/bugs do controlador de movimento

[Dê-nos comentários](/hololens/hololens-feedback) no Hub de Comentários, usando a categoria "Entrada > Realidade Misturada".

## <a name="see-also"></a>Confira também

* [Controladores de movimento no Unity](../develop/unity/motion-controllers-in-unity.md)
* [Controladores de mãos e emovimento no DirectX](../develop/native/hands-and-motion-controllers-in-directx.md)
* [Gestos](gaze-and-commit.md#composite-gestures)
* [Guia do enthusiast: sua Windows Mixed Reality página](/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guia do enthusiast: usando jogos & aplicativos no Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Como funciona o acompanhamento interno](/windows/mixed-reality/enthusiast-guide/tracking-system)