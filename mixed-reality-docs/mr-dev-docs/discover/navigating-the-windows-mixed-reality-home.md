---
title: Como navegar na página inicial do Windows Mixed Reality
description: saiba como navegar na Windows Mixed Reality página inicial em HoloLens e Windows Mixed Reality headsets.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, so, plataforma, Cliff House, casa, casa, ambiente, iniciar, menu Iniciar, menu início, Pins, aplicativo, iniciar aplicativos, colocar aplicativos, teleport, mover, navegar, headset de realidade misturada, headset de realidade virtual, o que é realidade virtual
ms.openlocfilehash: 39ca5e974e242019d7eb14fba0362151213c6558cce7f13328390712b3642901
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190242"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Como navegar na página inicial do Windows Mixed Reality

assim como a experiência do Windows PC começa com a área de trabalho, Windows Mixed Reality começa com a casa. o Windows Mixed Reality home usa nossa capacidade de inato de entender e navegar por locais 3d. com o HoloLens, sua casa é seu espaço físico, mas com headsets de imersão, sua casa é um local virtual.

sua casa também é onde você usará o menu Iniciar para abrir e colocar aplicativos e conteúdo. Você pode preencher sua casa com conteúdo misto de realidade e multitarefas usando vários aplicativos ao mesmo tempo. As coisas que você coloca em casa ficam lá, mesmo se você reiniciar o dispositivo.

## <a name="start-menu"></a>Menu Iniciar

![Menu iniciar no Microsoft HoloLens](images/start-500px.png)

o menu Iniciar consiste em:
* Informações do sistema (status da rede, porcentagem da bateria, hora atual e volume)
* Cortana (em headsets de imersão, um bloco inicial; em HoloLens, na parte superior do início)
* Aplicativos fixados
* O botão todos os aplicativos (sinal de adição)
* Botões de foto e vídeo para [captura de realidade misturada](/hololens/holographic-photos-and-videos)

Alterne entre os modos de exibição aplicativos fixados e todos os aplicativos selecionando os botões mais ou menos. para abrir o menu Iniciar em HoloLens, use o gesto de flor. em um headset de imersão, pressione o botão Windows em seu controlador.

## <a name="launching-apps"></a>Iniciando aplicativos

Para iniciar um aplicativo, selecione-o em Iniciar. o menu Iniciar desaparecerá e o aplicativo será aberto no modo de posicionamento, como uma janela 2d ou um [modelo 3d](../distribute/implementing-3d-app-launchers.md).

Para executar o aplicativo, você precisará colocá-lo em sua página inicial:
1. Use seu [olhar](../design/gaze-and-commit.md) ou controlador para posicionar o aplicativo onde desejar. Ele será ajustado automaticamente (em tamanho e posição) para estar em conformidade com o espaço onde você o coloca.
2. coloque o aplicativo usando o air-tap (HoloLens) ou o botão de seleção (headsets de imersão). para cancelar e retornar o menu Iniciar, use o gesto de flor ou o botão Windows.

os [aplicativos 2D](../develop/porting-apps/building-2d-apps.md), criados para desktop, móvel ou Xbox, podem ser modificados para serem executados como aplicativos de imersão de realidade misturada usando a [API HolographicSpace](/uwp/api/Windows.Graphics.Holographic.HolographicSpace). Um aplicativo de imersão retira o usuário da casa e em uma experiência de imersão. os usuários podem retornar a página inicial com o gesto de flor (HoloLens) ou pressionando o botão Windows em seu controlador (headsets de imersão).

Os aplicativos também podem ser iniciados por meio de uma API de aplicativo para aplicativo ou por meio de Cortana.

![aplicativos na página inicial do Windows Mixed Reality](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Movendo e ajustando aplicativos

Selecione **ajustar** na barra de aplicativos para revelar os controles que movem, dimensionam e giram o conteúdo da realidade misturada. Quando tiver terminado, selecione **concluído**.

![O Slate da loja no modo de ajuste (quadro azul). Observe que a barra de aplicativos (superior) foi alterada para incluir os botões ' Concluído ' e ' remover '.](images/adjust-500px.png)

Aplicativos diferentes podem ter outras opções na barra de aplicativos. por exemplo, Microsoft Edge tem opções de *rolar*, *arrastar* e *Zoom* . 

![Barra de aplicativos para aplicativos 2D em execução no HoloLens](images/holobar-500px.png)

O botão **voltar** navega de volta para as telas exibidas anteriormente no aplicativo. Ele será interrompido quando você alcançar o início das experiências mostradas no aplicativo e não navegará para outros aplicativos.

## <a name="getting-around-your-home"></a>Entrando em casa

com o **HoloLens**, você passa por espaço físico para se mover em casa.

Com **headsets de imersão**, você pode se familiarizar em seu Playspace para se mover em uma área semelhante no mundo virtual. Para mover-se entre distâncias mais longas, use o Thumbstick em seu controlador para praticamente "andar" ou use a *teleportação* para saltar imediatamente as distâncias mais longas.

![teleportação na página inicial do Windows Mixed Reality](images/teleportation-500px.png)

**Para teleport:**
1. Abrir o reticle de teleportação.
   * Usando [controladores de movimento](../design/motion-controllers.md): Pressione o Thumbstick para frente e segure-o nessa posição.
   * Usando um controlador Xbox: Pressione a Thumbstick esquerda para frente e segure-a nessa posição.
   * Usando um mouse: mantenha pressionado o botão com o botão direito do mouse (e use a roda de rolagem para girar a direção que você deseja enfrentar quando teleport).
2. Coloque o reticle onde você deseja teleport.
   * Usando [controladores de movimento](../design/motion-controllers.md): Incline o controlador (no qual você está mantendo o Thumbstick Forward) para mover o reticle.
   * Usando um controlador Xbox: Use seu [olhar](../design/gaze-and-commit.md) para mover o reticle.
   * Usando um mouse: Mova o mouse para mover o reticle.
3. Solte o botão para teleport onde o reticle foi colocado.

**Para praticamente "Walk:"**
* Usando os [controladores de movimento](../design/motion-controllers.md): clique no botão de Thumbstick e segure e, em seguida, mova o Thumbstick na direção que você deseja "andar".
* Usando um controlador Xbox: clique com o botão esquerdo do Thumbstick e segure e, em seguida, mova o Thumbstick na direção que você deseja "percorrer".

## <a name="immersive-headset-input-support"></a>Suporte de entrada de headset de imersão

[Windows Mixed Reality headsets de imersão](immersive-headset-hardware-details.md) dão suporte a vários tipos de entrada para navegar na página inicial do Windows Mixed Reality. o HoloLens não dá suporte a entradas de acessório para navegação, pois você acompanha fisicamente e vê seu ambiente. no entanto, HoloLens [oferece suporte a entradas](hardware-accessories.md) para interagir com aplicativos.

### <a name="motion-controllers"></a>Controladores de movimento

a melhor experiência de Windows Mixed Reality será com Windows Mixed Reality os [controladores de movimento](../design/motion-controllers.md) que dão suporte ao acompanhamento de seis graus de liberdade usando apenas os sensores em seu headset-nenhuma câmera ou marcador externo é necessário!

Comandos de navegação em breve.

### <a name="gamepad"></a>Gamepad
* **Thumbstick esquerdo:**
  * Pressione e mantenha o Thumbstick à esquerda para abrir o reticle de [Teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .
  * Toque em Thumbstick à esquerda, à direita ou voltar para mover para a esquerda, para a direita ou de volta em pequenos incrementos.
  * Clique no botão esquerdo Thumbstick e mantenha pressionado e, em seguida, mova o Thumbstick para a direção que você deseja [praticamente "andar".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Toque na **Thumbstick direita** ou à direita para girar a direção que você está enfrentando em 45 graus.
* Pressionar o **botão a** seleciona e atua como o gesto de [toque do ar](../design/gaze-and-commit.md#composite-gestures) .
* pressionar o botão **guia** abre o [menu Iniciar](navigating-the-windows-mixed-reality-home.md#start-menu) e atua como o gesto de [cair](../design/system-gesture.md#bloom) .
* Pressionar os **gatilhos esquerdo e direito** permite ampliar e reduzir um aplicativo de área de trabalho 2D com o qual você está interagindo em casa.

### <a name="keyboard-and-mouse"></a>Teclado e mouse

**Observação:** Use **Windows chave + Y** para alternar o mouse entre o controle da área de trabalho do seu PC e a página inicial do Windows Mixed Reality.

na página inicial do Windows Mixed Reality:
* Pressionar o botão **esquerdo** do mouse seleciona e atua como o gesto de [toque do ar](../design/gaze-and-commit.md#composite-gestures) .
* Manter o botão **direito** do mouse abre o reticle de [teleportação](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .
* pressionar a tecla **Windows** no teclado abre o [Menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu) e age como o gesto de [cair](../design/system-gesture.md#bloom) .
* Quando [nuvens](../design/gaze-and-commit.md) em um aplicativo de área de trabalho 2D, você pode **clicar** para selecionar, clicar com o **botão direito do mouse** para exibir menus de contexto e usar a **roda de rolagem** para rolar (assim como na área de trabalho do seu PC).

## <a name="cortana"></a>Cortana

[Cortana](../design/voice-input.md#hey-cortana) é seu assistente pessoal no Windows Mixed Reality, assim como no PC e no telefone. HoloLens tem um microfone interno, mas os headsets de imersão podem exigir hardware extra. Use Cortana para abrir aplicativos, reiniciar o dispositivo, procurar coisas online e muito mais. os desenvolvedores também podem optar por [integrar Cortana](https://dev.windows.com/cortana) em suas experiências.

Você também pode usar comandos de voz para colocar em sua casa. Por exemplo, aponte para um botão (usando [olhar](../design/gaze-and-commit.md) ou um controlador, dependendo do dispositivo) e diga "Select". Outros comandos de voz incluem "ir para a casa", "maior", "menor", "fechar" e "entrar em frente".

## <a name="store-settings-and-system-apps"></a>aplicativos de armazenamento, Configurações e de sistema

Windows Mixed Reality tem vários aplicativos internos, como:
* **Microsoft Store** para obter aplicativos e jogos
* **Hub de comentários** para enviar comentários sobre o sistema e os aplicativos do sistema
* **Configurações** definir configurações do sistema ([incluindo](/hololens/hololens-network) atualizações de sistema e de rede)
* **Microsoft Edge** procurar sites
* **Fotos** para exibir e compartilhar fotos e vídeos
* **calibragem** (somente HoloLens) para ajustar a experiência de HoloLens ao usuário atual
* **aprenda gestos** (HoloLens) ou **Aprender Realidade Misturada** (headsets de imersão) para saber mais sobre como usar seu dispositivo
* **visualizador 3D** para decorar seu mundo com conteúdo de realidade misturada
* **Portal de realidade misturada** (Desktop) para configurar e gerenciar o headset de imersão e transmitir uma visualização dinâmica de sua exibição no Headset para que outras pessoas vejam.
* **Filmes e TV** para exibir vídeos 360 e os filmes e programas de TV mais recentes
* **Cortana** para todas as suas necessidades de assistente virtual
* **Área de trabalho** (headsets de imersão) para exibir seu monitor de área de trabalho enquanto estiver em um headset de imersão
* **Explorador de arquivos** Acessar arquivos e pastas localizados em seu dispositivo

## <a name="see-also"></a>Confira também
* [Modos de exibição do aplicativo](../design/app-views.md)
* [Controladores de movimentos](../design/motion-controllers.md)
* [Acessórios de hardware](hardware-accessories.md)
* [Considerações sobre o ambiente para HoloLens](/hololens/hololens-environment-considerations)
* [Implementar inicializadores de aplicativos 3D](../distribute/implementing-3d-app-launchers.md)
* [criando modelos 3d para uso no Windows Mixed Reality página inicial](../distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)