---
title: Tutoriais de áudio espacial – 2. Espacializar sons de interação de botão
description: Adicione um botão ao projeto e espacialize os sons de interação do botão.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade misturada, UWP, Windows 10, HRTF, função de transferência relacionada à cabeça, reverb, Microsoft Spatializer, prefabs, curva de volume
ms.openlocfilehash: e0f916ecf8cd8da81e0738b082021c76c55a7f2031517a37b959575e1b21ce16
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209816"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Espacializar sons de interação de botão

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a espacializar os sons de interação do botão e também a usar um clipe de áudio para testar a interação espacializada do botão.  

## <a name="objectives"></a>Objetivos

* Adicionar e espacializar os sons de clique do botão

## <a name="add-a-button"></a>Adicionar um botão

Para adicionar o pré-fab Botão, na  janela **Project,** selecione Pacotes e digite "PressableButtonHoloLens2" na barra de pesquisa.

![Prefab do botão em Ativos](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

O prefab do botão é a entrada representada por um ícone azul. Clique e arraste o pré-fab **PressableButtonHoloLens2** para a Hierarquia. Com o **objeto PressableButtonHoloLens2** ainda selecionado, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:

* **Posição:** X = 0, Y = -0,4, Z = 2
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Transformação de botão](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

Para se concentrar nos objetos na cena, você pode clicar duas vezes no objeto **PressableButtonHoloLens2** e ampliar um pouco novamente:

## <a name="spatialize-button-feedback"></a>Comentários sobre o botão Espacializar

Nesta etapa, você espacializará os comentários de áudio para o botão. Para sugestões de design relacionadas, consulte [design de som espacial](../../../design/spatial-sound-design.md).

Na janela **Mixer** áudio, você definirá destinos **chamados grupos Mixer**, para reprodução de áudio de componentes de Fonte **de** Áudio.

Para abrir a **janela Mixer** áudio, no menu do Unity, selecione Janela Áudio  >    >  **Mixer:** Abrir Janela Mixer ![ Áudio](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)

 Crie um **Mixer** clicando no '+' ao lado de **Mixers** e insira um nome adequado para o Mixer, por exemplo, Áudio _Espacial Mixer_. O novo mixer incluirá um Grupo **padrão** chamado **Mestre.**

![Mixer com o primeiro mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> Até que o reverb seja habilitado no [5º Capítulo:](unity-spatial-audio-ch5.md)Usando o reverb para adicionar distância ao áudio espacial, o medidor de volume do mixer não mostra a atividade de sons tocadas por meio do Microsoft Spatializer

Na janela Hierarquia, selecione **PressableButtonHoloLens2** e, na  janela Inspetor, encontre o componente Fonte de Áudio e Configure o componente Fonte de Áudio da seguinte forma:

1. Para a **propriedade** Saída, clique no seletor e escolha a **Mixer** que você criou.
2. Marque a **caixa de seleção Espacializar.**
3. Mova o **controle deslizante do Spatial Blend** para 3D (1).

![Fonte de áudio do botão](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> Se você mover **o Spatial Blend** para 1  (3D) sem verificar a caixa de seleção Espacializar, o Unity usará seu espacializador de panorâmico, em vez do **Microsoft Spatializer** com HRTFs.

## <a name="adjust-the-volume-curve"></a>Ajustar a curva volume

Por padrão, o Unity atenua os sons espacializados à medida que eles ficam mais distantes do ouvinte. Quando essa atenuação é aplicada aos sons de comentários de interação, a interface pode se tornar mais difícil de usar.

Para desabilitar essa atenuação, você precisa ajustar a curva **volume** no componente **Fonte de** Áudio.

Na janela Hierarquia, selecione **PressableButtonHoloLens2** e, em seguida, na janela Inspetor, navegue até a fonte de áudio Configurações som  >  **3D** e Configure da seguinte forma:

1. Definir a **propriedade Volume Rolloff** como Rolloff Linear
2. Arraste o ponto de extremidade na curva **volume** (a curva vermelha) de '0' no eixo y até '1'
3. Para ajustar a forma da curva **volume** a ser plana, arraste o controle de forma de curva branca para ser paralelo ao eixo X

![Configurações de som 3D do botão](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a>Testando o áudio de espacialização

Para testar o áudio espacializado no editor do Unity,  você precisa adicionar um clipe de áudio no componente Fonte de Áudio com a opção **Loop** marcada no objeto **PressableButtonHoloLens2.**

No modo de reprodução, mova o objeto **PressableButtonHoloLens2** da esquerda para a direita e compare com e sem áudio espacial habilitado em sua estação de trabalho. Você também pode alterar as configurações da Fonte de Áudio para teste:

* Movendo a **propriedade Spatial Blend** entre 0 e 1 (som espacializado 2D não espacializado e 3D)
* Verificando e desmarcando a **propriedade Spatialize**

Experimente o aplicativo no HoloLens 2. No aplicativo, você pode clicar no botão e ouvir os sons de interação do botão espacializado.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a espacializar os sons de interação do botão e a usar um clipe de áudio para testar a interação espacializada do botão. No próximo tutorial, você aprenderá a espacializar o áudio de uma fonte de vídeo.

> [!div class="nextstepaction"]
> [Próximo Tutorial: 3. Espacializando o áudio de um vídeo](unity-spatial-audio-ch3.md)
