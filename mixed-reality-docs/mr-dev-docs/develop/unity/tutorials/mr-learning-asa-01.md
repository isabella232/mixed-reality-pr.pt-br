---
title: Introdução aos Tutoriais das Âncoras Espaciais do Azure
description: Conclua este curso para aprender a implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, ios, android, Windows 10, ARCore, macOS, Suporte de Build do Android, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 4d753546fd8fd0779e7614ca11e4668e359d8f9dcdc8db9d62e95267747471db
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197356"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a>1. Introdução aos Tutoriais das Âncoras Espaciais do Azure

Bem-vindo(a) aos tutoriais de Âncoras Espaciais do Azure! Nesta série de tutoriais, você aprenderá os conceitos básicos de <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">ASA</a> (Âncoras Espaciais do Azure) e como ancorar uma experiência de realidade misturada completa no mundo real. Você também aprenderá a implantar o projeto no Android e no iOS.

Tutoriais desta série:

1. [Introdução](mr-learning-asa-01.md) (Você já está aqui)
2. [Introdução às Âncoras Espaciais do Azure](mr-learning-asa-02.md)
3. [Salvar, recuperar e compartilhar Âncoras Espaciais do Azure](mr-learning-asa-03.md)
4. [Exibir os comentários da Âncora Espacial do Azure](mr-learning-asa-04.md)
5. [Âncoras Espaciais do Azure para Android e o iOS](mr-learning-asa-05.md)

## <a name="objectives"></a>Objetivos

* Saber como criar âncoras espaciais e buscá-las no Azure
* Saber como obter o alinhamento espacial entre sessões do aplicativo
* Saber como obter alinhamento espacial entre vários dispositivos
* Saber como preparar, compilar e implantar seu projeto no Android e iOS

## <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou versão posterior
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020/2019 LTS instalado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado
* Conclua a seção [Criar um recurso de Âncoras Espaciais](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Início Rápido: Criar um aplicativo HoloLens do Unity que usa as Âncoras Espaciais do Azure](/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* Ter concluído a série de [Tutoriais de introdução](mr-learning-base-01.md) ou ter alguma experiência anterior básica com o Unity e o MRTK
* Se você pretende implantar no Android, bem como no HoloLens
  * Um <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">desenvolvedor habilitado</a> e um dispositivo Android <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">com capacidade para ARCore</a> com conexão USB para o seu computador com Windows ou macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020/2019 LTS instalado e o módulo de Suporte de Build do Android adicionado
* Se você pretende implantar no iOS, bem como no HoloLens
  * Um computador macOS com a versão mais recente do <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e do <a href="https://cocoapods.org" target="_blank">CocoaPods</a> instaladas
  * Um dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatível com ARKit</a> com conexão USB para seu computador macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020/2019 LTS instalado e o módulo de Suporte de Build do iOS adicionado

> [!Important]
> Essa série de tutoriais suporta o Unity 2020 LTS (atualmente 2020.3.x) se você estiver usando o plug-in Open XR ou Windows XR, e também o Unity 2019 LTS (atualmente 2019.4.x) se estiver usando o Legacy WSA. Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.

> [!div class="nextstepaction"]
> [Próximo tutorial: 2. Introdução às Âncoras Espaciais do Azure](mr-learning-asa-02.md)
