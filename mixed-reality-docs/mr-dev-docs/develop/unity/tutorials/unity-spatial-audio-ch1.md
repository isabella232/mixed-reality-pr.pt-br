---
title: Tutoriais de áudio espacial – 1. Adicionando áudio espacial ao seu projeto
description: Adicione o plug-in Microsoft Spatializer ao seu projeto do Unity para acessar HoloLens de hardware 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade misturada, UWP, Windows 10, HRTF, função de transferência relacionada à cabeça, reverb, Microsoft Spatializer
ms.openlocfilehash: a61e709f24c2162bc6e6e1248de658128674d49e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175376"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Adicionando áudio espacial ao seu projeto do Unity

## <a name="overview"></a>Visão geral

Bem-vindo ao tutorial de áudio espacial do Unity no HoloLens2. Por meio desta série de tutoriais, você aprenderá a usar o descarregado de HRTF (função de transferência relacionada à cabeça) no HoloLens 2 e Como habilitar o reverb ao usar o descarregado HRTF.

O [repositório microsoft spatializer GitHub tem](https://github.com/microsoft/spatialaudio-unity) um projeto do Unity concluído desta sequência de tutoriais.

Para entender o que significa espacializar sons usando tecnologias de espacialização baseadas em HRTF e recomendações para quando pode ser útil, confira Design [de som espacial](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>O que é o descarregado de HRTF?

O processamento de áudio usando algoritmos baseados em HRTF requer uma grande quantidade de computação especializada. HoloLens 2 inclui hardware dedicado que pode ser utilizado para evitar sobrecarregar o processador do aplicativo, "descarregando" o processamento de algoritmos baseados em HRTF.  O plug-in do Espacializador da Microsoft fornece uma maneira fácil para seu aplicativo aproveitar o hardware HRTF dedicado para que seu aplicativo possa usar mais do processador de aplicativos para operações diferentes do áudio espacial.

## <a name="objectives"></a>Objetivos

* Importando e habilitando o plug-in do Espacializador da Microsoft
* Habilitando o áudio espacial em sua estação de trabalho do desenvolvedor

## <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)
* Conhecimento básico de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com Unity 2020/2019 LTS montado e o módulo Suporte ao Build da Plataforma Universal Windows adicionado

É **recomendável concluir a** série de tutoriais de Introdução ou ter alguma experiência anterior básica com o Unity e o MRTK antes de continuar. [](mr-learning-base-01.md)

> [!Important]
> Esta série de tutoriais dá suporte ao Unity 2020 LTS (atualmente 2020.3.x) se você estiver usando o Plug-in XR ou Windows XR do Open XR e também o Unity 2019 LTS (atualmente 2019.4.x) se você estiver usando o WSA herdado ou o plug-in XR do Windows. Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*
2. [Como alternar a plataforma de build](mr-learning-base-02.md#configuring-the-unity-project)
3. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importando o ambiente de Toolkit e configurando o projeto do Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Criar e configurar a cena e](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) dar à cena um nome adequado, por exemplo, *SpatialAudio*

Em seguida, siga as instruções Alterando a Opção de Exibição de Reconhecimento Espacial para garantir que o perfil de configuração do MRTK para sua cena **seja DefaultHoloLens2ConfigurationProfile** e altere as opções de exibição da malha de reconhecimento espacial para **Oclusão**. [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)

## <a name="adding-microsoft-spatializer-to-the-project"></a>Adicionar o Microsoft Spatializer ao Project

Baixar e importar o Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a>

>[!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Como importar os ativos de tutorial](mr-learning-base-04.md#importing-the-tutorial-assets).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Habilitar o plug-in Microsoft Spatializer

Depois de importar o Microsoft Spatializer para seu projeto do **Unity, Project janela configurador do MRTK** será exibido, use a lista suspenso **Espacializador** de áudio para selecionar o **Microsoft Spatializer** e clique no botão Aplicar para aplicar a configuração:

![Configurador de Project MRTK](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

você também pode habilitar manualmente o Microsoft Spatializer: Abra **Editar -> Project Configurações -> Áudio** e altere o Plug-in do **Spatializer** para "Microsoft Spatializer".

![Project Configurações mostrando o plug-in do spatializer](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>Habilitar áudio espacial em sua estação de trabalho

Em versões da área de Windows, o áudio espacial é desabilitado por padrão. Habilita-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas. Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **Som espacial -> Windows Sonic para Fones de Ouvido**.

![Configurações de áudio espacial da área de trabalho](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> Essa configuração só será necessária se você planeja testar seu projeto no editor do Unity.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a Importar e habilitar o plug-in do Microsoft Spatializer e também a habilitar o áudio espacial em sua estação de trabalho.
No próximo tutorial, você aprenderá a adicionar áudio espacial ao projeto do Unity.

> [!div class="nextstepaction"]
> [Próximo Tutorial: 2. Espacializar sons de interação do botão](unity-spatial-audio-ch2.md)
