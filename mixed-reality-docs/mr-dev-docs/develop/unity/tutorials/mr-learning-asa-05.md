---
title: Âncoras Espaciais do Azure para o Android e o iOS
description: Conclua este curso para aprender a implantar um projeto do Unity com o MRTK (Kit de Ferramentas de Realidade Misturada) e as Âncoras Espaciais do Azure para Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, android, ios, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6e9ae377a11d74fd9cdfca7ddb0379542d365e3365bdf07319bc8580b2e87420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215742"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Âncoras Espaciais do Azure para o Android e o iOS

Neste tutorial, você aprenderá a criar seu projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.

## <a name="objectives"></a>Objetivos

* Saiba como criar o projeto para seu dispositivo Android usando o Plug-in ARCore XR e o AR Foundation do Unity
* Saiba como criar o projeto para seu dispositivo iOS usando o Plug-in ARKit XR e o AR Foundation do Unity

## <a name="installing-inbuilt-unity-packages"></a>Instalar pacotes internos do Unity

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Configurar o MRTK para a Câmera do AR Foundation

Nesta seção, você aprenderá a configurar o MRTK para implantação em um dispositivo móvel.

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**. Em seguida, na janela Inspetor, selecione a guia **Câmera**, clone o perfil da câmera e dê a ele um nome adequado, por exemplo, **AzureSpatialAnchors_ARCameraProfile**:

![Unity com o ARCameraProfile recém-criado selecionado](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do Kit de Ferramentas de Realidade Misturada](mr-learning-base-03.md).

Com a guia **Câmera** ainda selecionada na janela Inspetor, expanda os **Provedores de Configuração da Câmera** e, clicando em "-", remova a **Configuração da Câmera do Windows Mixed Reality** ou a **Configuração da Câmera XR SDK do Windows Mixed Reality**:

![ARCameraProfile do Unity com o novo provedor de dados adicionado ](images/mr-learning-asa/asa-05-section2-step1-2.png)

e clique em **+ Adicionar Provedor de Configurações da Câmera** e expanda o **Novo provedor de dados** recém-adicionado:

![Câmera AR adicionada para Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

Usando a lista suspensa **Tipo**, altere o tipo para **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![ARCameraProfile do Unity com o caminho para a seleção do tipo de provedor de dados](images/mr-learning-asa/asa-05-section2-step1-4.png)

Atualize as definições de script do UnityAR do MRTK invocando o item de menu: **Realidade Misturada** > **Kit de ferramentas** > **Utilitários** > **UnityAR** > Atualizar as definições de script

## <a name="building-your-application-to-your-android-device"></a>Compilar o aplicativo para seu dispositivo Android

Nesta seção, você aprenderá a configurar seu projeto para compilá-lo e implantá-lo em um dispositivo Android.

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build e, em seguida, alterne a plataforma para Android:

![Janela Configurações de Build do Unity com a plataforma Android selecionada](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Para lembrar como mudar a plataforma de build, consulte as instruções em [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform).

Feche a janela Configurações de Build.

No menu do Unity, selecione **Realidade Misturada** > **Kit de Ferramentas** > **Utilitários** > **Configurar projeto do MRTK** para abrir a janela do **Configurador de projeto do MRTK**. Confirme se todas as opções estão selecionadas e clique em **Aplicar** para aplicar as configurações:

![Configurador de projeto do MRTK no Unity 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Outras Configurações**, selecione **Vulkan** e remova-o clicando no símbolo de **"-"** :

![Outras Configurações do Unity com o Vulcan selecionado](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**. Em seguida, use um cabo USB, conecte seu dispositivo Android ao seu computador e selecione-o na lista suspensa **Executar Dispositivo**:

![Janela Configurações de Build do Unity com a cena adicionada e a opção Executar Dispositivo selecionada](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Se o dispositivo não aparecer na lista suspensa Executar Dispositivo, pode ser necessário pressionar o botão Atualizar ao lado do menu suspenso.

Na janela Configurações de Build, clique no botão **Compilar e Executar** para abrir a janela Compilar Android.

Escolha um local adequado para armazenar o build, por exemplo, _D:\MixedRealityLearning\Builds_ e dê ao APK um nome adequado, por exemplo, _MRTKTutorials-AzureSpatialAnchors_ e clique no botão **Salvar** para iniciar o processo de build:

![Janela Configurações de Build do Unity com a janela de prompt Salvar para Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> Se você receber algum erro na janela do Console do Unity relacionado aos módulos SDK, NDK ou JDK do Android, será necessário abrir o Hub do Unity e instalar os módulos de Suporte de Build do Android associados.

Quando o processo de build for concluído, os aplicativos deverão ser carregados automaticamente em seu dispositivo Android.

## <a name="building-your-application-to-your-ios-device"></a>Compilar o aplicativo para seu dispositivo iOS

Nesta seção, você aprenderá a configurar seu projeto para compilá-lo e implantá-lo em seu dispositivo iOS.

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build e alterne a plataforma para iOS:

![Janela Configurações de Build do Unity com o iOS selecionado](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Para lembrar como mudar a plataforma de build, consulte as instruções em [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform).

Feche a janela Configurações de Build.

No menu do Unity, selecione **Realidade Misturada** > **Kit de Ferramentas** > **Utilitários** > **Configurar projeto do MRTK** para abrir a janela do **Configurador de projeto do MRTK**. Confirme se todas as opções estão selecionadas e clique em **Aplicar** para aplicar as configurações:

![Janela Configurador de Projeto do MRTK no Unity para iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Outras Configurações**, desmarque a caixa de seleção **Remover Código do Mecanismo** para desabilitá-la:

![Outras Configurações do Unity com a opção Remover Código do Mecanismo desabilitada](images/mr-learning-asa/asa-05-section4-step1-3.png)

Feche a janela Configurações do Player e abra a janela **Configurações de Build** novamente.

Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**:

![Janela Configurações de Build do Unity com a cena adicionada](images/mr-learning-asa/asa-05-section4-step1-4.png)

Na janela Configurações de Build, clique no botão **Compilar** para abrir a janela Compilar iOS.

Escolha um local adequado para armazenar o projeto do Xcode, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma pasta e dê a ela um nome adequado, por exemplo, _MRTKTutorials-AzureSpatialAnchors_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:

![Janela Configurações de Build do Unity com a janela de prompt Salvar para iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

Quando o processo de build for concluído, siga as instruções de [Exportar o projeto do Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implantar o projeto do Xcode em seu dispositivo iOS.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar o projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.
