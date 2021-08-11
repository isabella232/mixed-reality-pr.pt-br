---
title: Introdução aos tutoriais do MRTK
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada do zero.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, solucionadores, acompanhamento do olho, comandos de voz
ms.localizationpriority: high
ms.openlocfilehash: e8eb878e7ab2fecf27defc5f28e045c4d4768682e95a3a42cda7f324a21617e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224782"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1. Introdução aos tutoriais do MRTK

Bem-vindo(a) à série de tutoriais d Introdução! No decorrer destes tutoriais, você aprenderá sobre o MRTK (Kit de ferramentas de realidade misturada) e alguns dos recursos que ele tem a oferecer. Você também criará uma experiência de realidade misturada na qual o usuário pode explorar um holograma modelado conforme o Mars Rover da NASA. Ao final desta série, você terá uma noção do MRTK e como ele pode acelerar seu processo de desenvolvimento.

Os tutoriais desta série foram concebidos de modo sequencial, portanto, siga-os na ordem correta:

1. [Introdução](mr-learning-base-01.md) (Você já está aqui)
2. [Como inicializar o seu projeto e implantar o primeiro aplicativo](mr-learning-base-02.md)
3. [Como configurar os perfis do MRTK](mr-learning-base-03.md)
4. [Como posicionar objetos na cena](mr-learning-base-04.md)
5. [Criar conteúdo dinâmico usando Solucionadores](mr-learning-base-05.md)
6. [Como criar interfaces do usuário](mr-learning-base-06.md)
7. [Como interagir com objetos 3D](mr-learning-base-07.md)
8. [Como usar o acompanhamento de olho](mr-learning-base-08.md)
9. [Como usar comandos de voz](mr-learning-base-09.md)

## <a name="objectives"></a>Objetivos

* Saiba como configurar o Unity para MRTK
* Saiba como criar e implantar em seu dispositivo
* Saiba como usar alguns dos principais recursos do MRTK
* Criar uma experiência de realidade misturada completa

## <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)
* [SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 ou posterior
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> com Unity 2020.3 LTS ou Unity 2019.4 LTS instalado (**OpenXR requer 2020.3.8 ou posterior para evitar bugs**)

Ao instalar o Unity, certifique-se de verificar os componentes a seguir em **'Plataformas'** .

* **Suporte de build da Plataforma Universal do Windows**
* **Suporte de build do Windows (IL2CPP)**

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

Se você instalou o Unity sem essas opções, poderá adicioná-las por meio do menu **'Adicionar Módulos'** no Hub do Unity.

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> A versão recomendada do MRTK para esta série de tutoriais é a MRTK 2.7.2

> [!Important]
> Essa série de tutoriais suporta o Unity 2020 LTS (atualmente 2020.3.x) se você estiver usando o Open XR ou o Windows XR Plugin, e também o Unity 2019 LTS (atualmente 2019.4.x) se estiver usando o Legacy WSA ou o Windows XR Plugin. Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.

> [!div class="nextstepaction"]
> [Próximo tutorial: 2. Como inicializar o seu projeto e implantar o primeiro aplicativo](mr-learning-base-02.md)
