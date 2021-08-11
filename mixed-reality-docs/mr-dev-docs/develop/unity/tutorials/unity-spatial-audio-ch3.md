---
title: Tutoriais de áudio espacial – 3. Espacializar áudio de um vídeo
description: Importe um ativo de vídeo para seu projeto do Unity e espacialize o áudio do vídeo.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade misturada, UWP, Windows 10, HRTF, função de transferência relacionada à cabeça, reverb, Microsoft Spatializer, importação de vídeo, Player de Vídeo
ms.openlocfilehash: 2926301aac9db67d3e72b0511600720c24e5965f52a23faa1230c381a47c9b90
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202874"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Espacializar áudio de um vídeo

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a espacializar o áudio de uma fonte de vídeo e testá-lo no editor do Unity e HoloLens 2.

## <a name="objectives"></a>Objetivos

* Importar um vídeo e adicionar um Player de Vídeo
* Reproduzir o vídeo em um quadrática
* Rotear o áudio do vídeo para o quadrática e espacializar o áudio

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importar um vídeo e adicionar um Player de Vídeo à cena

Para este tutorial, use Você pode usar [este vídeo do](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) projeto de exemplo de áudio espacial.

Para importar o Vídeo para o projeto do Unity. no menu do Unity, selecione **Importação de**  >  **Ativos Novo Ativo** 
 ![ Importando Ativo](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

Na janela **Importar Novo Ativo...,** selecione o arquivo **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** baixado e clique no botão Abrir para importar o ativo para o projeto: 

![Selecionando Ativo](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

Ajustar as configurações de qualidade no clipe de vídeo pode garantir uma reprodução suave HoloLens 2. Selecione o arquivo de vídeo **na janela Project** e, na  janela Inspetor do arquivo de vídeo, substitua as configurações para aplicativos da **Windows Store** e:

* **Habilitar Transcode**
* Definir **Codec** como H264
* Definir **o modo de taxa de bits** como Baixo
* Definir **qualidade espacial** como qualidade espacial média

Após esses ajustes, clique em Aplicar para alterar a configuração de qualidade no clipe de vídeo.

![Alteração da propriedade de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

Clique com o botão direito do mouse na Hierarquia, selecione **Player**  >  **de Vídeo** para adicionar o componente Player de Vídeo.

![Adicionar Player de Vídeo](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>Reproduzir vídeo em um quadrática

O **objeto Video Player** precisa de um objeto de jogo com textura para renderizar o vídeo.

Clique com o botão direito do mouse na Hierarquia , **selecione 3D Object** Quad para criar um quad e configurar seu  >   componente **Transformar** da seguinte maneira:

* **Posição:** X = 0, Y = 0, Z = 2
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala:** X = 1,28, Y = 0,72, Z = 1

![Adicionar um quad](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

Agora você precisa textura do **Quad** com o vídeo, na janela **Project,** clique com o botão direito do mouse e escolha Criar Textura de Renderização para criar um componente Renderizar Textura, insira um nome adequado para a Textura de Renderização, por   >   exemplo, Textura de Áudio Espacial : 

![Criar textura de renderização](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

Selecione a **Textura de Renderização** e, na janela Inspetor, de definir a propriedade **Tamanho** para corresponder à resolução nativa do vídeo de 1280 x 720. Em seguida, para garantir um bom desempenho de renderização no HoloLens 2, de definir a propriedade **Buffer** de Profundidade como Pelo menos **16 bits de profundidade.**

![Renderizar propriedades de textura](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

Em seguida, use a Textura de Áudio **Espacial de Textura de Renderização** criada como a textura para o **Quad**:

1. Arraste a **Textura de Áudio** Espacial da janela **Project** para o **Quad** na Hierarquia para adicionar a Textura de Renderização ao Quad
2. Para garantir um bom desempenho HoloLens 2, selecione Quad na Hierarquia e, na janela Inspetor do sombreador, selecione a opção Realidade **Misturada** Toolkit  >  **Sombreador** Padrão.

![Propriedades de textura quádruplo](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

Para definir **o Player de Vídeo** e a **Textura** de Renderização para reproduzir o clipe de vídeo, selecione o Player de **Vídeo** na **Hierarquia** e na **janela Inspetor,**

* Definir a **propriedade Video Clip** como o arquivo de vídeo baixado 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'
* Marque a **caixa de seleção Loop**
* Definir **Textura de Destino** para a nova textura de renderização Textura de Áudio **Espacial**

![Propriedades do player de vídeo](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>Espacializar o áudio do vídeo

Na janela Hierarquia, selecione **Objeto Quad** e, na  janela Inspetor,  use o botão Adicionar Componente para adicionar Fonte de Áudio à qual você roteia o áudio do vídeo.

Na fonte **de áudio**:

* Definir **Saída** para o **sistema de Mixer**
* Marque a **caixa Espacializar**
* Mover o **controle deslizante do Spatial Blend** para 1 (3D)

![Inspetor de fonte de áudio quad](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

Para definir o Player de Vídeo para rotear seu áudio para a Fonte de **Áudio,** selecione o Player de Vídeo na janela Hierarquia e, no objeto Player de Vídeo no Inspetor, faça as alterações a seguir. 

* Definir o **modo de saída de áudio** como fonte de **áudio**
* Definir a **propriedade Fonte de** Áudio como o **Quad**

![Fonte de áudio do conjunto de player de vídeo](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a espacializar o áudio de uma fonte de vídeo Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity. Você verá e ouvirá o vídeo e o áudio do vídeo será espacializado.

No próximo tutorial, você aprenderá a Habilitar e desabilitar a espacialização em tempo de executar

> [!div class="nextstepaction"]
> [Próximo Tutorial: 4. Habilitando e desabilitando a espacialização em tempo de executar](unity-spatial-audio-ch4.md)
