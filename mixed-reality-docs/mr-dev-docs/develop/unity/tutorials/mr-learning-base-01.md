---
title: Introdução aos tutoriais do MRTK
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada do zero.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, solucionadores, acompanhamento do olho, comandos de voz
ms.localizationpriority: high
ms.openlocfilehash: 27a5f2cae4f08fbc142c8b872c22d23ab41cdc62
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008076"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="192ac-104">1. Introdução aos tutoriais do MRTK</span><span class="sxs-lookup"><span data-stu-id="192ac-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="192ac-105">Bem-vindo(a) à série de tutoriais d Introdução!</span><span class="sxs-lookup"><span data-stu-id="192ac-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="192ac-106">No decorrer destes tutoriais, você aprenderá sobre o MRTK (Kit de ferramentas de realidade misturada) e alguns dos recursos que ele tem a oferecer.</span><span class="sxs-lookup"><span data-stu-id="192ac-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="192ac-107">Você também criará uma experiência de realidade misturada na qual o usuário pode explorar um holograma modelado conforme o Mars Rover da NASA.</span><span class="sxs-lookup"><span data-stu-id="192ac-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="192ac-108">Ao final desta série, você terá uma noção do MRTK e como ele pode acelerar seu processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="192ac-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="192ac-109">Os tutoriais desta série foram concebidos de modo sequencial, portanto, siga-os na ordem correta:</span><span class="sxs-lookup"><span data-stu-id="192ac-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="192ac-110">[Introdução](mr-learning-base-01.md) (Você já está aqui)</span><span class="sxs-lookup"><span data-stu-id="192ac-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="192ac-111">Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="192ac-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="192ac-112">Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="192ac-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="192ac-113">Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="192ac-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="192ac-114">Criar conteúdo dinâmico usando Solucionadores</span><span class="sxs-lookup"><span data-stu-id="192ac-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="192ac-115">Como criar interfaces do usuário</span><span class="sxs-lookup"><span data-stu-id="192ac-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="192ac-116">Como interagir com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="192ac-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="192ac-117">Como usar o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="192ac-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="192ac-118">Como usar comandos de voz</span><span class="sxs-lookup"><span data-stu-id="192ac-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="192ac-119">Objetivos</span><span class="sxs-lookup"><span data-stu-id="192ac-119">Objectives</span></span>

* <span data-ttu-id="192ac-120">Saiba como configurar o Unity para MRTK</span><span class="sxs-lookup"><span data-stu-id="192ac-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="192ac-121">Saiba como criar e implantar em seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="192ac-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="192ac-122">Saiba como usar alguns dos principais recursos do MRTK</span><span class="sxs-lookup"><span data-stu-id="192ac-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="192ac-123">Criar uma experiência de realidade misturada completa</span><span class="sxs-lookup"><span data-stu-id="192ac-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="192ac-124">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="192ac-124">Prerequisites</span></span>

* <span data-ttu-id="192ac-125">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="192ac-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="192ac-126">[SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="192ac-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="192ac-127">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="192ac-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="192ac-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019 LTS instalado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="192ac-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="192ac-129">A versão recomendada do MRTK para esta série de tutoriais é a MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="192ac-129">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="192ac-130">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="192ac-130">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="192ac-131">Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="192ac-131">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="192ac-132">Próximo tutorial: 2. Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="192ac-132">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)

