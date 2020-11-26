---
title: 1. Introdução
description: Parte 1 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: aa6d90bebbbfc10b108b97d05931a9926118ba7c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679855"
---
# <a name="1-getting-started"></a><span data-ttu-id="301a9-104">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="301a9-104">1. Getting started</span></span>

<span data-ttu-id="301a9-105">Seja você alguém pouco familiarizado com a realidade misturada ou um profissional experiente, esse é o lugar para iniciar seu percurso com o [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) e o [Unreal Engine](https://www.unrealengine.com/en-US/).</span><span class="sxs-lookup"><span data-stu-id="301a9-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="301a9-106">Esta série de tutoriais fornecerá um guia passo a passo sobre como criar um aplicativo de xadrez interativo com o [plug-in de Ferramentas de UX](https://github.com/microsoft/MixedReality-UXTools-Unreal), parte do [Kit de Ferramentas de Realidade Misturada para o Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="301a9-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="301a9-107">O plug-in ajudará você a adicionar recursos comuns de UX a seus projetos pelo uso de código, blueprints e exemplos.</span><span class="sxs-lookup"><span data-stu-id="301a9-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="301a9-109">Ao final da série, você terá experiência prática em:</span><span class="sxs-lookup"><span data-stu-id="301a9-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="301a9-110">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="301a9-110">Starting a new project</span></span>
* <span data-ttu-id="301a9-111">Configurar a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="301a9-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="301a9-112">Trabalhar com a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="301a9-112">Working with user input</span></span>
* <span data-ttu-id="301a9-113">Adicionar botões</span><span class="sxs-lookup"><span data-stu-id="301a9-113">Adding buttons</span></span>
* <span data-ttu-id="301a9-114">Jogar em um emulador ou dispositivo</span><span class="sxs-lookup"><span data-stu-id="301a9-114">Playing on an emulator or device</span></span>


## <a name="prerequisites"></a><span data-ttu-id="301a9-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="301a9-115">Prerequisites</span></span>
<span data-ttu-id="301a9-116">Verifique se você instalou o seguinte antes de começar:</span><span class="sxs-lookup"><span data-stu-id="301a9-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="301a9-117">Windows 10 1809 ou posterior</span><span class="sxs-lookup"><span data-stu-id="301a9-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="301a9-118">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="301a9-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="301a9-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 ou posterior</span><span class="sxs-lookup"><span data-stu-id="301a9-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="301a9-120">Dispositivo do Microsoft HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) ou Emulador</span><span class="sxs-lookup"><span data-stu-id="301a9-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="301a9-121">Visual Studio 2019 com as cargas de trabalho abaixo</span><span class="sxs-lookup"><span data-stu-id="301a9-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="301a9-122">Instalação do Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="301a9-122">Installing Visual Studio 2019</span></span>
<span data-ttu-id="301a9-123">Há algumas etapas para garantir que você tenha todos os pacotes do Visual Studio necessários:</span><span class="sxs-lookup"><span data-stu-id="301a9-123">There are a few steps to ensure you have all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="301a9-124">Instale a versão mais recente do [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="301a9-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="301a9-125">Instale as seguintes [cargas de trabalho](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span><span class="sxs-lookup"><span data-stu-id="301a9-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="301a9-126">Desenvolvimento para desktop com C++</span><span class="sxs-lookup"><span data-stu-id="301a9-126">Desktop development with C++</span></span>
    * <span data-ttu-id="301a9-127">Desenvolvimento para área de trabalho com .NET</span><span class="sxs-lookup"><span data-stu-id="301a9-127">.NET desktop development</span></span>
    * <span data-ttu-id="301a9-128">Desenvolvimento para a Plataforma Universal do Windows</span><span class="sxs-lookup"><span data-stu-id="301a9-128">Universal Windows Platform development</span></span>

3. <span data-ttu-id="301a9-129">Instale os seguintes [componentes](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span><span class="sxs-lookup"><span data-stu-id="301a9-129">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="301a9-130">Compiladores, ferramentas de build e runtimes > ferramentas de build MSVC v142 – VS 2019 C++ ARM64 (versão mais recente)</span><span class="sxs-lookup"><span data-stu-id="301a9-130">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="301a9-131">Pronto!</span><span class="sxs-lookup"><span data-stu-id="301a9-131">That's it!</span></span> <span data-ttu-id="301a9-132">Você está pronto para prosseguir para a inicialização do projeto de xadrez.</span><span class="sxs-lookup"><span data-stu-id="301a9-132">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="301a9-133">Próxima seção: 2. Inicializar o seu projeto e o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="301a9-133">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)