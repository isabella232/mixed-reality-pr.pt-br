---
title: 1. Introdução
description: Parte 1 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: efa0bc210fc20b9e639954a06e97eb78661d87e5
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712575"
---
# <a name="1-getting-started"></a><span data-ttu-id="d85fa-104">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="d85fa-104">1. Getting started</span></span>

<span data-ttu-id="d85fa-105">Se você está começando a usar a realidade misturada agora ou já é um profissional experiente, você está no lugar certo para iniciar seu percurso do [HoloLens 2](../../../index.yml) e do [Unreal Engine](https://www.unrealengine.com/en-US/).</span><span class="sxs-lookup"><span data-stu-id="d85fa-105">Whether you're new to mixed reality or a seasoned pro, you're in the right place to start your [HoloLens 2](../../../index.yml) and [Unreal Engine](https://www.unrealengine.com/en-US/) journey.</span></span> <span data-ttu-id="d85fa-106">Esta série de tutoriais fornecerá um guia passo a passo sobre como criar um aplicativo de xadrez interativo com o [plug-in de Ferramentas de Experiência de Usuário](https://github.com/microsoft/MixedReality-UXTools-Unreal), parte do [Kit de Ferramentas de Realidade Misturada para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="d85fa-106">This tutorial series will give you a step-by-step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="d85fa-107">O plug-in ajudará você a adicionar recursos comuns de UX a seus projetos pelo uso de código, blueprints e exemplos.</span><span class="sxs-lookup"><span data-stu-id="d85fa-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="d85fa-109">Ao final da série, você terá experiência em:</span><span class="sxs-lookup"><span data-stu-id="d85fa-109">By the end of the series you'll have experience with:</span></span>
* <span data-ttu-id="d85fa-110">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="d85fa-110">Starting a new project</span></span>
* <span data-ttu-id="d85fa-111">Configurar a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="d85fa-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="d85fa-112">Trabalhar com a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="d85fa-112">Working with user input</span></span>
* <span data-ttu-id="d85fa-113">Adicionar botões</span><span class="sxs-lookup"><span data-stu-id="d85fa-113">Adding buttons</span></span>
* <span data-ttu-id="d85fa-114">Jogar em um emulador ou dispositivo</span><span class="sxs-lookup"><span data-stu-id="d85fa-114">Playing on an emulator or device</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d85fa-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d85fa-115">Prerequisites</span></span>

<span data-ttu-id="d85fa-116">Verifique se você instalou o seguinte antes de começar:</span><span class="sxs-lookup"><span data-stu-id="d85fa-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="d85fa-117">Windows 10 1809 ou posterior</span><span class="sxs-lookup"><span data-stu-id="d85fa-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="d85fa-118">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="d85fa-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="d85fa-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.26 ou posterior</span><span class="sxs-lookup"><span data-stu-id="d85fa-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.26 or later</span></span>
* <span data-ttu-id="d85fa-120">Dispositivo do Microsoft HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) ou [Emulador](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span><span class="sxs-lookup"><span data-stu-id="d85fa-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or [Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span></span>
* <span data-ttu-id="d85fa-121">Visual Studio 2019 com as cargas de trabalho abaixo</span><span class="sxs-lookup"><span data-stu-id="d85fa-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="d85fa-122">Instalação do Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d85fa-122">Installing Visual Studio 2019</span></span>

<span data-ttu-id="d85fa-123">Primeiro, verifique a configuração com todos os pacotes do Visual Studio necessários:</span><span class="sxs-lookup"><span data-stu-id="d85fa-123">First, make sure your setup with all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="d85fa-124">Instale a versão mais recente do [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="d85fa-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
1. <span data-ttu-id="d85fa-125">Instale as seguintes [cargas de trabalho](/visualstudio/install/modify-visual-studio#modify-workloads):</span><span class="sxs-lookup"><span data-stu-id="d85fa-125">Install the following [workloads](/visualstudio/install/modify-visual-studio#modify-workloads):</span></span>
    * <span data-ttu-id="d85fa-126">Desenvolvimento para desktop com C++</span><span class="sxs-lookup"><span data-stu-id="d85fa-126">Desktop development with C++</span></span>
    * <span data-ttu-id="d85fa-127">Desenvolvimento para área de trabalho com .NET</span><span class="sxs-lookup"><span data-stu-id="d85fa-127">.NET desktop development</span></span>
    * <span data-ttu-id="d85fa-128">Desenvolvimento para a Plataforma Universal do Windows</span><span class="sxs-lookup"><span data-stu-id="d85fa-128">Universal Windows Platform development</span></span>
1. <span data-ttu-id="d85fa-129">Expanda o desenvolvimento da Plataforma Universal do Windows e selecione:</span><span class="sxs-lookup"><span data-stu-id="d85fa-129">Expand Universal Windows Platform development and select:</span></span> 
    * <span data-ttu-id="d85fa-130">Conectividade de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="d85fa-130">USB Device Connectivity</span></span>
    * <span data-ttu-id="d85fa-131">Ferramentas da Plataforma Universal do Windows do C++ (v142)</span><span class="sxs-lookup"><span data-stu-id="d85fa-131">C++ (v142) Universal Windows Platform tools</span></span>

1. <span data-ttu-id="d85fa-132">Instale os seguintes [componentes](/visualstudio/install/modify-visual-studio#modify-individual-components):</span><span class="sxs-lookup"><span data-stu-id="d85fa-132">Install the following [components](/visualstudio/install/modify-visual-studio#modify-individual-components):</span></span>
    * <span data-ttu-id="d85fa-133">Compiladores, ferramentas de build e runtimes > ferramentas de build MSVC v142 – VS 2019 C++ ARM64 (versão mais recente)</span><span class="sxs-lookup"><span data-stu-id="d85fa-133">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="d85fa-134">Confirme a instalação com a imagem a seguir</span><span class="sxs-lookup"><span data-stu-id="d85fa-134">You can confirm the installation with the following picture</span></span>

![Tiques importantes no instalador do VS](images/unreal-uxt/1-install-the-tools.png)

<span data-ttu-id="d85fa-136">Pronto!</span><span class="sxs-lookup"><span data-stu-id="d85fa-136">That's it!</span></span> <span data-ttu-id="d85fa-137">Você está pronto para prosseguir para a inicialização do projeto de xadrez.</span><span class="sxs-lookup"><span data-stu-id="d85fa-137">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="d85fa-138">Próxima seção: 2. Inicializar o seu projeto e o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="d85fa-138">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)