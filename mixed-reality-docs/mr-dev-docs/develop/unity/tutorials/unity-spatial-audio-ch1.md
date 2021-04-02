---
title: Tutoriais de áudio espacial-1. Adicionando áudio espacial ao seu projeto
description: Adicione o plug-in do Microsoft Spatializer ao seu projeto do Unity para acessar o descarregamento de hardware do HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer
ms.openlocfilehash: 7964ecdc8adee7c61c4c7086b8d04983f6e3903f
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982789"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. adicionando áudio espacial ao seu projeto do Unity

## <a name="overview"></a>Visão geral

Bem-vindo ao tutorial de áudio espacial do Unity no HoloLens2. Nesta série de tutoriais, você aprenderá a usar o descarregamento de HRTF (função de transferência relacionada ao cabeçalho) no HoloLens 2 e como habilitar o reverberador ao usar o descarregamento do HRTF.

O [repositório GitHub do Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tem um projeto de Unity concluído desta sequência de tutorial.

Para entender o que isso significa para espacialar sons usando tecnologias de espacial com base em HRTF e recomendações para quando puder ser útil, consulte [design de som espacial](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>O que é descarregamento de HRTF?

O processamento de áudio usando algoritmos baseados em HRTF exige uma grande quantidade de computação especializada. O HoloLens 2 inclui um hardware dedicado que pode ser utilizado para evitar sobrecarregar o processador de aplicativos, portanto, "descarregando" o processamento de algoritmos baseados em HRTF.  O plug-in do Microsoft spatializer fornece uma maneira fácil de seu aplicativo aproveitar o hardware dedicado do HRTF para que seu aplicativo possa usar mais do processador de aplicativos para operações que não sejam de áudio espacial.

## <a name="objectives"></a>Objetivos

* Importando e habilitando o plug-in Microsoft spatializer
* Habilitando o áudio espacial em sua estação de trabalho do desenvolvedor

## <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)
* Conhecimento básico de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019 LTS montado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado

É **altamente recomendável** concluir a série de tutoriais de [introdução](mr-learning-base-01.md) ou ter alguma experiência prévia básica com o Unity e o MRTK antes de continuar.

> [!IMPORTANT]
>
> * A versão recomendada do Unity para esta série de tutoriais é o Unity 2019 LTS. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*

1. [Como alternar a plataforma de build](mr-learning-base-02.md#configuring-the-unity-project)

1. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Como configurar o projeto do Unity](mr-learning-base-02.md#configuring-the-unity-project)

1. [Criar e definir a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar à cena um nome adequado, por exemplo, *SpatialAudio*

Em seguida, siga as instruções de [alteração da opção de exibição de conscientização espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para garantir que o perfil de configuração MRTK para sua cena seja **DefaultHoloLens2ConfigurationProfile** e altere as opções de exibição para a malha de conscientização espacial para **oclusão**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Adicionando o Microsoft Spatializer ao projeto

Baixe e importe o Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. unitypackage </a>

>[!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Como importar os ativos de tutorial](mr-learning-base-02.md#importing-the-tutorial-assets).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Habilitar o plug-in Microsoft Spatializer

Depois de importar o **Microsoft Spatializer** , você precisa habilitá-lo. Abra o **editar > configurações do projeto-> áudio** e altere o **plug-in Spatializer** para "Microsoft Spatializer".

![Configurações do projeto mostrando o plug-in spatializer](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Habilitar áudio espacial em sua estação de trabalho

Em versões de área de trabalho do Windows, o áudio espacial é desabilitado por padrão. Habilite-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas. Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **som espacial-> Windows Sonic para fones de ouvido**.

![Configurações de áudio espacial da área de trabalho](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> Essa configuração só será necessária se você planeja testar seu projeto no editor do Unity.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprenderá a importar e habilitar o plug-in Microsoft Spatializer e também a habilitar o áudio espacial em sua estação de trabalho.
No próximo tutorial, você aprenderá a adicionar áudio espacial no projeto do Unity.

> [!div class="nextstepaction"]
> [Próximo tutorial: 2. isespacialando sons de interação do botão](unity-spatial-audio-ch2.md)
