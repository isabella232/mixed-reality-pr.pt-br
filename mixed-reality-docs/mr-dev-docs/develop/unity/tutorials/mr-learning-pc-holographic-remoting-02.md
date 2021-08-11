---
title: Criar um aplicativo de Comunicação Remota Holográfica para PC
description: Conclua este curso para aprender a criar um aplicativo de PC para uma experiência de realidade misturada do seu PC para o HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, comunicação remota holográfica do PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: d395801c20d95ee0fdddc144b4e28c841554fb5116f847574ec4a931d116026e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197900"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Como criar um aplicativo de Comunicação Remota Holográfica para PC

Neste tutorial, você aprenderá a criar um aplicativo de PC que usa a comunicação remota do Holographic para transmitir seu trabalho em andamento para o HoloLens e exibi-lo sem a necessidade de compilação anterior.

[Conheça os conceitos básicos da comunicação remota do Holographic.](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

## <a name="objectives"></a>Objetivos

* Configurar o Unity para Comunicação Remota Holográfica
* Saber como criar e implantar o aplicativo com o Visual Studio
* Desenvolver um aplicativo de comunicação remota do Holographic e conectar-se com o HoloLens

## <a name="configuring-the-capabilities"></a>Como configurar as funcionalidades

Na janela **Configurações do projeto**, expanda as **Configurações de publicação**, role para baixo até a seção Funcionalidades e selecione a caixa de seleção de funcionalidades mostrada abaixo, além das funcionalidades existentes.

* Servidor Cliente da Internet
* Servidor Cliente de Redes Privadas

![habilitando recursos](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a>Criar o aplicativo para PC

O seu aplicativo de Comunicação Remota Holográfica agora está pronto para ser criado no PC. Siga as etapas abaixo e faça estas alterações para criar esse aplicativo no seu PC.

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a>Como testar o aplicativo remoto de Comunicação Remota Holográfica

Para conectar o seu aplicativo para PC ao seu HoloLens 2, siga o processo abaixo:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Instale o aplicativo de Player de Comunicação Remota no dispositivo HoloLens 2

* No seu HoloLens 2, visite a Loja de aplicativos e pesquise por "**Player de Comunicação Remota**".
* Selecione o aplicativo **Player de Comunicação Remota**.
* Toque em **Instalar** para baixar e instalar o aplicativo.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Conectar o aplicativo de Comunicação Remota Holográfica para PC ao Player de Comunicação Remota

* Inicie o **Player de Comunicação Remota** no seu HoloLens.
* Anote o **endereço IP** do HoloLens. Ele será exibido como um holograma pelo **Player de Comunicação Remota** assim que for iniciado.
* Abra um aplicativo de Comunicação Remota Holográfica para PC no seu PC.
* Depois que o aplicativo for iniciado, insira o **endereço IP** e clique no botão **Conectar** para se conectar.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como criar um aplicativo remoto para PC de Comunicação Remota Holográfica e a conectar-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo em 3D na realidade misturada. Depois que o HoloLens estiver conectado ao aplicativo de Comunicação Remota Holográfica para PC, você deverá ver a transmissão da experiência de realidade misturada no seu dispositivo de HoloLens 2.
