---
title: Introdução aos Tutoriais de funcionalidades de vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, funcionalidades de multiusuários, Photon, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure
ms.localizationpriority: high
ms.openlocfilehash: 3db488cc31d6ef7746aae67b3a84c42dc91985b586e907d2172346fe0952876f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197690"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1. Introdução aos Tutoriais de funcionalidades de vários usuários

Bem-vindo(a) aos tutoriais de funcionalidades de vários usuários! Nesta série de tutoriais, você aprenderá os conceitos básicos da criação de uma experiência multiusuário usando a PUN (<a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a>). O PUN é uma das várias opções de rede disponíveis para os desenvolvedores de realidade misturada criarem experiências compartilhadas.

Tutoriais desta série:

* [Configurar o Photon Unity Networking](mr-learning-sharing-02.md)
* [Como conectar vários usuários](mr-learning-sharing-03.md)
* [Compartilhar movimentações de objeto com vários usuários](mr-learning-sharing-04.md)
* [Integrar Âncoras Espaciais do Azure a uma experiência compartilhada](mr-learning-sharing-05.md)

## <a name="objectives"></a>Objetivos

* Saiba como criar um aplicativo PUN e conectar seu projeto do Unity a ele
* Saiba como conectar vários usuários em uma experiência compartilhada
* Saiba como compartilhar os movimentos de objeto com outros usuários
* Saber como obter alinhamento espacial entre vários dispositivos

## <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020 LTS instalado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado
* Conclua a seção [Criar um recurso de Âncoras Espaciais](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Início Rápido: Criar um aplicativo HoloLens do Unity que usa as Âncoras Espaciais do Azure](/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* Ter concluído a série de [Tutoriais de introdução](mr-learning-base-01.md) ou ter alguma experiência anterior básica com o Unity e o MRTK
* Ter concluído a série de [Tutoriais de Âncoras Espaciais do Azure](mr-learning-asa-01.md) ou experiência anterior criando uma conta de Âncoras Espaciais do Azure
* Se você pretende implantar no Android, bem como no HoloLens
  * Um <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">desenvolvedor habilitado</a> e um dispositivo Android <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">com capacidade para ARCore</a> com conexão USB para o seu computador com Windows ou macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020 LTS instalado e o módulo de Suporte de Build do Android adicionado
* Se você pretende implantar no iOS, bem como no HoloLens
  * Um computador macOS com a versão mais recente do <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e do <a href="https://cocoapods.org" target="_blank">CocoaPods</a> instaladas
  * Um dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatível com ARKit</a> com conexão USB para seu computador macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020 LTS instalado e o módulo de Suporte de Build do iOS adicionado

> [!IMPORTANT]
> A versão recomendada do Kit de Ferramentas de Realidade Misturada para esta série de tutoriais é o MRTK 2.7.

> [!IMPORTANT]
> A versão recomendada do Unity para esta série de tutoriais é o Unity 2020 LTS. Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.

> [!div class="nextstepaction"]
> [Próximo tutorial: 2. Configurar uma rede Unity Photon](mr-learning-sharing-02.md)