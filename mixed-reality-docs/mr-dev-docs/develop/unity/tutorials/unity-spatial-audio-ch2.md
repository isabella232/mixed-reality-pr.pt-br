---
title: Tutoriais de áudio espacial-2. Espacializar sons de interação de botão
description: Adicione um botão ao seu projeto e espaciale os sons de interação do botão.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, pré-fabricados, curva de volume
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590758"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Espacializar sons de interação de botão

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a gerar os sons de interação do botão e também aprenderá a usar um clipe de áudio para testar a interação do botão espacialed.  

## <a name="objectives"></a>Objetivos

* Adicionar e Espacialar o botão clique em sons

## <a name="add-a-button"></a>Adicionar um botão

Para adicionar o botão pré-fabricado, na janela do **projeto** , selecione **pacotes** e digite "PressableButtonHoloLens2" na barra de pesquisa.

![Botão pré-fabricado em ativos](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

O botão pré-fabricado é a entrada representada por um ícone azul. Clique e arraste o **PressableButtonHoloLens2** pré-fabricado para a hierarquia. Com o objeto **PressableButtonHoloLens2** ainda selecionado, na janela Inspetor, configure o componente **transformação** da seguinte maneira:

* **Posição**: X = 0, Y =-0,4, Z = 2
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Transformação de botão](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

Para se concentrar nos objetos na cena, você pode clicar duas vezes no objeto **PressableButtonHoloLens2** e, em seguida, reduzir um pouco o zoom novamente:

## <a name="spatialize-button-feedback"></a>Comentar o botão espacial

Nesta etapa, você causará a espacial dos comentários de áudio para o botão. Para obter sugestões de design relacionadas, consulte [design de som espacial](../../../design/spatial-sound-design.md).

Na janela do **mixer de áudio** , você definirá destinos chamados grupos de **mixers** para reprodução de áudio de componentes de **fonte de áudio** .

Para abrir a janela do **mixer de áudio** , no menu do Unity, selecione **janela**  >  mixer de áudio de **áudio**  >  : ![ Abrir janela do mixer de áudio](images/spatial-audio/spatial-audio-02-section2-step1-1.png)

 Crie um **mixer** clicando no botão ' + ' ao lado de **mixers** e insira um nome adequado para o mixer, por exemplo, _mixer de áudio espacial_. O novo mixer incluirá um **grupo** padrão chamado **Master**.

![Painel do mixer com o primeiro mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> Até que o verbo de reverberação esteja habilitado no [quinto capítulo: usando o reverberar para adicionar distância ao áudio espacial](unity-spatial-audio-ch5.md), o medidor de volume do mixer não mostra a atividade de sons reproduzidos por meio do Microsoft Spatializer

Na janela hierarquia, selecione o **PressableButtonHoloLens2** , em seguida, na janela Inspetor, localize o componente **fonte de áudio** e configure o componente fonte de áudio da seguinte maneira:

1. Para a propriedade **saída** , clique no seletor e escolha o **mixer** que você criou.
2. Marque a caixa de seleção **espacialize** .
3. Mova o controle deslizante de **mistura espacial** para 3D (1).

![Fonte de áudio do botão](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> Se você mover a **mistura espacial** para 1 (3D) sem marcar a caixa de seleção **espacialize** , o Unity usará seu spatializer panorâmico, em vez do **Microsoft spatializer** com HRTFs.

## <a name="adjust-the-volume-curve"></a>Ajustar a curva de volume

Por padrão, o Unity atenua os sons espaciais à medida que eles ficam mais distantes do ouvinte. Quando essa atenuação é aplicada aos sons de comentários de interação, a interface pode ser mais difícil de usar.

Para desabilitar essa atenuação, você precisa ajustar a curva de **volume** no componente **fonte de áudio** .

Na janela hierarquia, selecione o **PressableButtonHoloLens2** , em seguida, na janela Inspetor, navegue até **fonte de áudio**  >  **3D configurações de som** e configure da seguinte maneira:

1. Defina a propriedade **volume rolloff** como linear rolloff
2. Arraste o ponto de extremidade na curva de **volume** (a curva vermelha) de ' 0 ' no eixo y até ' 1 '
3. Para ajustar a forma da curva de **volume** para ser simples, arraste o controle forma de curva de branco para ser paralelo ao eixo X

![Configurações de som 3D do botão](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a>Testando o áudio espacial

Para testar o áudio espacial no editor do Unity, você precisa adicionar um clipe de áudio na opção o componente de **origem de áudio** com **loop** com check-in no objeto **PressableButtonHoloLens2** .

No modo de reprodução, mova o objeto **PressableButtonHoloLens2** da esquerda para a direita e compare com e sem áudio espacial habilitado em sua estação de trabalho. Você também pode alterar as configurações de fonte de áudio para teste:

* Movendo a propriedade de **mistura espacial** entre 0-1 (2D sem espacial e um som espacial 3D)
* Verificando e desmarcando a propriedade **espacialize**

Experimente o aplicativo no HoloLens 2. No aplicativo, você pode clicar no botão e ouvir os sons de interação do botão espacialado.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprenderá a espacialar os sons de interação do botão e a usar um clipe de áudio para testar a interação do botão espacialed. No próximo tutorial, você aprenderá a gerar uma espacial de áudio de uma fonte de vídeo.

> [!div class="nextstepaction"]
> [Próximo tutorial: 3. disespacial de áudio de um vídeo](unity-spatial-audio-ch3.md)
