---
title: Introdução aos tutoriais do MRTK
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada do zero.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, solucionadores, acompanhamento do olho, comandos de voz
ms.localizationpriority: high
ms.openlocfilehash: abee2163c3b92897396ea35cc43ae025e8e7b804
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175503"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="97ed2-104">1. Introdução aos tutoriais do MRTK</span><span class="sxs-lookup"><span data-stu-id="97ed2-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="97ed2-105">Bem-vindo(a) à série de tutoriais d Introdução!</span><span class="sxs-lookup"><span data-stu-id="97ed2-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="97ed2-106">No decorrer destes tutoriais, você aprenderá sobre o MRTK (Kit de ferramentas de realidade misturada) e alguns dos recursos que ele tem a oferecer.</span><span class="sxs-lookup"><span data-stu-id="97ed2-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="97ed2-107">Você também criará uma experiência de realidade misturada na qual o usuário pode explorar um holograma modelado conforme o Mars Rover da NASA.</span><span class="sxs-lookup"><span data-stu-id="97ed2-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="97ed2-108">Ao final desta série, você terá uma noção do MRTK e como ele pode acelerar seu processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="97ed2-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="97ed2-109">Os tutoriais desta série foram concebidos de modo sequencial, portanto, siga-os na ordem correta:</span><span class="sxs-lookup"><span data-stu-id="97ed2-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="97ed2-110">[Introdução](mr-learning-base-01.md) (Você já está aqui)</span><span class="sxs-lookup"><span data-stu-id="97ed2-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="97ed2-111">Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="97ed2-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="97ed2-112">Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="97ed2-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="97ed2-113">Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="97ed2-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="97ed2-114">Criar conteúdo dinâmico usando Solucionadores</span><span class="sxs-lookup"><span data-stu-id="97ed2-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="97ed2-115">Como criar interfaces do usuário</span><span class="sxs-lookup"><span data-stu-id="97ed2-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="97ed2-116">Como interagir com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="97ed2-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="97ed2-117">Como usar o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="97ed2-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="97ed2-118">Como usar comandos de voz</span><span class="sxs-lookup"><span data-stu-id="97ed2-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="97ed2-119">Objetivos</span><span class="sxs-lookup"><span data-stu-id="97ed2-119">Objectives</span></span>

* <span data-ttu-id="97ed2-120">Saiba como configurar o Unity para MRTK</span><span class="sxs-lookup"><span data-stu-id="97ed2-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="97ed2-121">Saiba como criar e implantar em seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="97ed2-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="97ed2-122">Saiba como usar alguns dos principais recursos do MRTK</span><span class="sxs-lookup"><span data-stu-id="97ed2-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="97ed2-123">Criar uma experiência de realidade misturada completa</span><span class="sxs-lookup"><span data-stu-id="97ed2-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="97ed2-124">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="97ed2-124">Prerequisites</span></span>

* <span data-ttu-id="97ed2-125">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="97ed2-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="97ed2-126">[SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="97ed2-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="97ed2-127">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="97ed2-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="97ed2-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> com Unity 2020.3 LTS ou Unity 2019.4 LTS instalado (**OpenXR requer 2020.3.8 ou posterior para evitar bugs**)</span><span class="sxs-lookup"><span data-stu-id="97ed2-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020.3 LTS or Unity 2019.4 LTS installed (**OpenXR requires 2020.3.8 or later to prevent bugs**)</span></span>

<span data-ttu-id="97ed2-129">Ao instalar o Unity, certifique-se de verificar os componentes a seguir em **'Plataformas'** .</span><span class="sxs-lookup"><span data-stu-id="97ed2-129">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>

* <span data-ttu-id="97ed2-130">**Suporte de build da Plataforma Universal do Windows**</span><span class="sxs-lookup"><span data-stu-id="97ed2-130">**Universal Windows Platform Build Support**</span></span>
* <span data-ttu-id="97ed2-131">**Suporte de build do Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="97ed2-131">**Windows Build Support (IL2CPP)**</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

<span data-ttu-id="97ed2-132">Se você instalou o Unity sem essas opções, poderá adicioná-las por meio do menu **'Adicionar Módulos'** no Hub do Unity.</span><span class="sxs-lookup"><span data-stu-id="97ed2-132">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> <span data-ttu-id="97ed2-133">A versão recomendada do MRTK para esta série de tutoriais é a MRTK 2.7.2</span><span class="sxs-lookup"><span data-stu-id="97ed2-133">The recommended MRTK version for this tutorial series is MRTK 2.7.2</span></span>

> [!Important]
> <span data-ttu-id="97ed2-134">Essa série de tutoriais suporta o Unity 2020 LTS (atualmente 2020.3.x) se você estiver usando o Open XR ou o Windows XR Plugin, e também o Unity 2019 LTS (atualmente 2019.4.x) se estiver usando o Legacy WSA ou o Windows XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="97ed2-134">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="97ed2-135">Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="97ed2-135">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="97ed2-136">Próximo tutorial: 2. Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="97ed2-136">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
