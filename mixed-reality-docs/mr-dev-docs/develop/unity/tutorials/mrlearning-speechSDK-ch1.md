---
title: Tutoriais de Serviços de Fala do Azure – 1. Integrar e usar a transcrição e o reconhecimento de fala
description: Conclua este curso para saber como implementar o SDK de Fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, reconhecimento de fala, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: a12163dda0a6bf961c6c34ebc35b6e00f491d6ca59c08dfba7c5126e797d089a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214575"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Integrar e usar a transcrição e o reconhecimento de fala

## <a name="overview"></a>Visão geral

Nesta série de tutoriais, você criará um aplicativo de realidade misturada que explora o uso dos Serviços de Fala do Azure com o HoloLens 2. Ao concluir esta série de tutoriais, você poderá usar o microfone do dispositivo para transcrever a conversão de fala em texto em tempo real, traduzir sua fala em outras linguagens e aproveitar o recurso de reconhecimento de Intenção para entender os comandos de voz usando inteligência artificial.

## <a name="objectives"></a>Objetivos

* Saiba como integrar os Serviços de Fala do Azure com um aplicativo do HoloLens 2
* Saiba como usar o reconhecimento de fala para transcrever texto

## <a name="prerequisites"></a>Pré-requisitos

>[!TIP]
>Se você ainda não concluiu a série de [Tutoriais de introdução](mr-learning-base-01.md), recomendamos que você a conclua primeiro.

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020/2019 LTS instalado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado

> [!Important]
> Essa série de tutoriais suporta o Unity 2020 LTS (atualmente 2020.3.x) se você estiver usando o Open XR ou o Windows XR Plugin, e também o Unity 2019 LTS (atualmente 2019.4.x) se estiver usando o Legacy WSA ou o Windows XR Plugin. Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*
2. [Como alternar a plataforma de build](mr-learning-base-02.md#configuring-the-unity-project)
3. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Como importar o Kit de ferramentas de Realidade Misturada e configurar o projeto do Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Criar e configurar a cena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e dar um nome adequado à cena, por exemplo, *AzureSpeechServices*

Em seguida, siga as instruções em [Alterar a Opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para verificar se o perfil de configuração do MRTK da sua cena é o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição da malha de reconhecimento espacial para **Oclusão**.

## <a name="configuring-the-speech-commands-start-behavior"></a>Como configurar o comportamento de início dos comandos de fala

Como você usará o SDK de Fala para reconhecimento de fala e transcrição, será necessário configurar os comandos de fala MRTK para que eles não interfiram na funcionalidade do SDK de Fala. Para conseguir isso, você pode alterar o comportamento de início dos comandos de fala de Início Automático para Início Manual.

Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, na janela Inspetor, selecione a guia **Entrada**, clone o **DefaultHoloLens2InputSystemProfile** e o **DefaultMixedRealitySpeechCommandsProfile** e, em seguida, altere o **Comportamento de Início** dos comandos de fala para **Início Manual**:

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a>Como configurar as funcionalidades

No menu do Unity, selecione **Editar** > **Configurações de projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Configurações de Publicação**:

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

Em **Configurações de publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas. Em seguida, habilite as funcionalidades **InternetClientServer** e **PrivateNetworkClientServer**:

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versão mais recente)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções em [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-04.md#importing-the-tutorial-assets).

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

Você precisa configurar o projeto do Unity para publicar os plug-ins de Fala do Azure para ARM64. Para fazer isso na janela do Projeto, navegue até **Ativos** > **SpeechSDK** > **Plug-ins** > **WSA** > **ARM64** e selecione o plug-in **Microsoft.CognitiveServices.Speech.core**.

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

com o plug-in **Microsoft.CognitiveServices.Speech.core** ainda selecionado, na janela inspetor Ativar **WSA Player** em **Configurações da plataforma**, selecione **UWP** para SDK, **ARM64** para CPU e clique em Aplicar para aplicar essas configurações ao plug-in.

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

Repita essas etapas para cada um dos plug-ins restantes:

* **Microsoft.CognitiveServices.Speech.extension.audio.sys**
* **Microsoft.CognitiveServices.Speech.extension.kws**
* **Microsoft.CognitiveServices.Speech.extension.lu**
* **Microsoft.CognitiveServices.Speech.extension.silk_codec**

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você vai preparar a cena adicionando o tutorial pré-fabricado e configurar o componente do Controlador Lunarcom (Script) para controlar sua cena.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.AzureSpeechServices** > **Pré-fabricados** e arraste o pré-fabricado **Lunarcom** para a janela Hierarquia para adicioná-lo à sua cena:

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

Com o objeto **Lunarcom** ainda selecionado na janela Hierarquia, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Controlador do Lunarcom (Script)** ao objeto Lunarcom:

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> O componente Controlador do Lunarcom (Script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

Com o objeto **Lunarcom** ainda selecionado, expanda-o para revelar seus objetos filho e, em seguida, arraste o objeto **Terminal** para o campo **Terminal** do componente Controlador do Lunarcom (Script):

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

Com o objeto **Lunarcom** ainda selecionado, expanda o objeto Terminal para revelar seus objetos filho e, em seguida, arraste o objeto **ConnectionLight** para o campo **Luz de Conexão** do componente Controlador do Lunarcom (Script) e o objeto **OutputText** para o campo **Texto de Saída**:

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

Com o objeto **Lunarcom** ainda selecionado, expanda o objeto Botões para revelar seus objetos filho e, em seguida, na janela Inspetor, expanda a lista **Botões**, defina seu **Tamanho** como 3 e arraste os objetos **MicButton**, **SatelliteButton** e **RocketButton** para os campos 0, 1 e 2 do **Elemento**, respectivamente:

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Como conectar o projeto do Unity ao recurso do Azure

Para usar os Serviços de Fala do Azure, você precisa criar um recurso do Azure e obter uma chave de API para o Serviço de Fala. Siga as instruções de [Experimentar o serviço de Fala gratuitamente](/azure/cognitive-services/speech-service/get-started) e tome nota da sua região de serviço (também conhecida como Localização) e a chave de API (também conhecida como Key1 ou Key2).

Na janela Hierarquia, selecione o objeto **Lunarcom**, então, na janela Inspetor, localize a seção **Credenciais do SDK de Fala** do componente **Controlador do Lunarcom (Script)** e configure-a da seguinte maneira:

* No campo **Chave de API do Serviço de Fala**, insira sua chave de API (Key1 ou Key2)
* No campo **Região do Serviço de Fala**, insira sua região de serviço (Localização) usando letras minúsculas e espaços removidos

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>Como usar o reconhecimento de fala para transcrever a fala

Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Fala do Lunarcom (Script)** ao objeto Lunarcom:

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> O componente Reconhecedor de Fala do Lunarcom (Script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

Se agora você entrar no modo de Jogo, poderá testar o reconhecimento de fala pressionando primeiro o botão de microfone:

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

Em seguida, supondo que o computador tenha um microfone, quando você disser algo, sua fala será transcrita no painel do terminal:

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.

## <a name="congratulations"></a>Parabéns

Você implementou o reconhecimento de fala da plataforma Azure. Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.

No próximo tutorial, você aprenderá a executar comandos usando o reconhecimento de fala do Azure.

> [!div class="nextstepaction"]
> [Próximo tutorial: 2. Executar comandos usando o reconhecimento de fala do Azure](mrlearning-speechSDK-ch2.md)
