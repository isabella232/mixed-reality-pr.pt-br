---
title: Tutoriais de áudio espacial-3. Espacializar áudio de um vídeo
description: Importar um ativo de vídeo para seu projeto do Unity e espacialar o áudio do vídeo.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, importação de vídeo, player de vídeo
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712855"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Espacializar áudio de um vídeo

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a gerar uma espacial de áudio de uma fonte de vídeo e testá-la no editor do Unity e no HoloLens 2.

## <a name="objectives"></a>Objetivos

* Importar um vídeo e adicionar um player de vídeo
* Reproduza o vídeo em um Quadrangle
* Rotear áudio do vídeo para o Quadrangle e espacialar o áudio

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importar um vídeo e adicionar um player de vídeo à cena

Para este tutorial, use [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) do projeto de exemplo de áudio espacial.

Para importar o vídeo para o projeto do Unity. no menu do Unity, selecione **ativo**  >  **importar novo** ativo 
 ![ importando ativo](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

Na janela **importar novo ativo...** , selecione o arquivo de **som espacial do Microsoft HoloLens-PTPvx7mDon4** que você baixou e clique no botão **abrir** para importar o ativo para o projeto:

![Selecionando ativo](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

Ajustar as configurações de qualidade no clipe de vídeo pode garantir uma reprodução suave no HoloLens 2. Selecione o arquivo de vídeo na janela do **projeto** e, na janela Inspetor do arquivo de vídeo, **substitua** as configurações para **aplicativos da Windows Store** e:

* Habilitar **transcodificação**
* Definir o **codec** como H264
* Definir o **modo de taxa de bits** como baixo
* Definir **qualidade espacial** para qualidade espacial média

Após esses ajustes, clique em aplicar para alterar a configuração de qualidade no clipe de vídeo.

![Alteração de propriedade de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

Clique com o botão direito do mouse na hierarquia, selecione **Video**  >  **Player** de vídeo para adicionar o componente de player de vídeo.

![Adicionar player de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>Reproduzir vídeo em um Quadrangle

O objeto **player de vídeo** precisa de um objeto de jogo texturizado para renderizar o vídeo.

Clique com o botão direito do mouse na hierarquia, selecione **objeto 3D**  >  **Quad** para criar um quad e configure seu componente de **transformação** da seguinte maneira:

* **Posição**: X = 0, Y = 0, Z = 2
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1,28, Y = 0,72, Z = 1

![Adicionar um quad](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

Agora você precisa Texturizar o **Quad** com o vídeo, na janela do **projeto** , clique com o botão direito do mouse e escolha **criar**  >  **textura de renderização** para criar um componente de textura de renderização, insira um nome adequado para a textura de renderização, por exemplo, textura de _áudio espacial_:

![Criar textura de renderização](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

Selecione a **textura renderizar** e, na janela Inspetor, defina a propriedade **tamanho** para corresponder à resolução nativa do vídeo de 1280x720. Em seguida, para garantir um bom desempenho de renderização no HoloLens 2, defina a propriedade **buffer de profundidade** com **pelo menos 16 bits de profundidade**.

![Renderizar Propriedades de textura](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

Em seguida, use a textura de **áudio espacial** da textura de renderização criada como a textura para o **Quad**:

1. Arraste a **textura de áudio espacial** da janela do **projeto** até o **Quad** na hierarquia para adicionar a textura de renderização ao Quad
2. Para garantir um bom desempenho no HoloLens 2, selecione Quad na hierarquia e, na janela Inspetor para sombreador, selecione o sombreador standard do **Kit de ferramentas da realidade misturada**  >   .

![Propriedades de textura quádrupla](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

Para definir **o player de vídeo** e a textura de **renderização** para reproduzir o clipe de vídeo, selecione o **player de vídeo** na **hierarquia** e, na janela **Inspetor** ,

* Defina a propriedade **videoclipe** como o arquivo de vídeo baixado ' Microsoft HoloLens-Spatial Sound-PTPvx7mDon4 '
* Marque a caixa de seleção **loop**
* Definir textura de **destino** para sua nova **textura de áudio espacial** de textura de renderização

![Propriedades do player de vídeo](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>Esespacialr o áudio do vídeo

Na janela hierarquia, selecione **Quad** Object e, em seguida, na janela Inspetor, use o botão **Adicionar componente** para adicionar a **fonte de áudio** para a qual você encaminhará o áudio do vídeo.

Na **fonte de áudio**:

* Definir **saída** para o **mixer de áudio espacial**
* Marque a caixa **espacialize**
* Mover o controle deslizante de **mistura espacial** para 1 (3D)

![Inspetor de fonte de áudio quádruplo](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

Para definir o player de vídeo para rotear seu áudio para a **fonte de áudio**, selecione o **player de vídeo** na janela hierarquia e, no objeto player de vídeo do Inspetor, faça as alterações a seguir.

* Definir o **modo de saída de áudio** como **fonte de áudio**
* Definir a propriedade **fonte de áudio** para o **Quad**

![Fonte de áudio definida do player de vídeo](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a usar a espacial de áudio de uma fonte de vídeo experimentando seu aplicativo em um HoloLens 2 ou no editor do Unity. Você verá e ouvirá o vídeo e o áudio do vídeo será espacial.

No próximo tutorial, você aprenderá a habilitar e desabilitar a espacial em tempo de execução

> [!div class="nextstepaction"]
> [Próximo tutorial: 4. Habilitando e desabilitando a espacial em tempo de execução](unity-spatial-audio-ch4.md)
