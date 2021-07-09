---
title: Introdução aos tutoriais babylon.js e WebXR
description: Conclua este curso para aprender a usar o babylon.js e criar um aplicativo básico de Realidade Misturada.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidade misturada, javascript, tutorial, BabylonJS, hololens, realidade misturada, UWP, Windows 10, WebXR, web de imersão
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600115"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="20a1b-104">Tutorial: Crie seu primeiro aplicativo WebXR usando babylon.js</span><span class="sxs-lookup"><span data-stu-id="20a1b-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="20a1b-105">Este tutorial mostrará como criar um aplicativo básico de Realidade Misturada usando o babylon.js e Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="20a1b-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="20a1b-106">O aplicativo que você irá criar renderizará um cubo, permitirá que você o gire para exibir as outras faces e adicionar interações.</span><span class="sxs-lookup"><span data-stu-id="20a1b-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="20a1b-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="20a1b-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="20a1b-108">Configurar um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="20a1b-108">Set up a development environment</span></span>
> * <span data-ttu-id="20a1b-109">API babylon.js para criar elementos 3D básicos</span><span class="sxs-lookup"><span data-stu-id="20a1b-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="20a1b-110">Criar uma página da Web</span><span class="sxs-lookup"><span data-stu-id="20a1b-110">Create a new web page</span></span>
> * <span data-ttu-id="20a1b-111">Interagir com elementos 3D</span><span class="sxs-lookup"><span data-stu-id="20a1b-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="20a1b-112">Executar o aplicativo em um Simulador do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="20a1b-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20a1b-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="20a1b-113">Prerequisites</span></span>

* <span data-ttu-id="20a1b-114">Navegador com suporte para WebXR, por [exemplo, Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span><span class="sxs-lookup"><span data-stu-id="20a1b-114">WebXR-supported browser, for example [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span></span>
* <span data-ttu-id="20a1b-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 ou superior</span><span class="sxs-lookup"><span data-stu-id="20a1b-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="20a1b-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="20a1b-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="20a1b-117">Opcional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) se você quiser usar um Simulador do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="20a1b-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="20a1b-118">Opcional: [Simulador do Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="20a1b-118">Optional: [Windows Mixed Reality simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="getting-started"></a><span data-ttu-id="20a1b-119">Introdução</span><span class="sxs-lookup"><span data-stu-id="20a1b-119">Getting started</span></span>

<span data-ttu-id="20a1b-120">Para criar esse projeto do zero, comece com um projeto do Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="20a1b-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="20a1b-121">O uso do VSCode não é obrigatório, mas o utilizaremos para sua conveniência ao longo do tutorial.</span><span class="sxs-lookup"><span data-stu-id="20a1b-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="20a1b-122">Desenvolvedores JavaScript mais experientes podem usar qualquer outro editor de sua escolha, até mesmo os Bloco de Notas mais simples.</span><span class="sxs-lookup"><span data-stu-id="20a1b-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="20a1b-123">Baixe o arquivo único [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) ou use uma versão online que pode ser encontrada no [site oficial do babylon.js.](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers)</span><span class="sxs-lookup"><span data-stu-id="20a1b-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="20a1b-124">Você também pode clonar todo o projeto babylon.js do [GitHub](https://github.com/BabylonJS/Babylon.js)</span><span class="sxs-lookup"><span data-stu-id="20a1b-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="20a1b-125">Crie um arquivo vazio e salve-o como uma página HTML, por exemplo, index.html</span><span class="sxs-lookup"><span data-stu-id="20a1b-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="20a1b-126">Crie uma marcação HTML básica e faça referência ao arquivo JavaScript babylon.js.</span><span class="sxs-lookup"><span data-stu-id="20a1b-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="20a1b-127">O código final é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="20a1b-127">The final code is as shown below:</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. <span data-ttu-id="20a1b-128">Adicione um elemento HTML de *tela* dentro do corpo para renderizar o conteúdo do babylon.js.</span><span class="sxs-lookup"><span data-stu-id="20a1b-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="20a1b-129">Observe que a tela tem um atributo ID, que permite que você acesse esse elemento HTML do JavaScript posteriormente.</span><span class="sxs-lookup"><span data-stu-id="20a1b-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
    <body>
        <canvas id="renderCanvas"></canvas>
    </body>
    </html>
    ```

1. <span data-ttu-id="20a1b-130">A tela ocupa toda a página da Web.</span><span class="sxs-lookup"><span data-stu-id="20a1b-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="20a1b-131">Isso conclui nossa página da Web.</span><span class="sxs-lookup"><span data-stu-id="20a1b-131">That completes our web page.</span></span> <span data-ttu-id="20a1b-132">Neste ponto, a página da Web está pronta.</span><span class="sxs-lookup"><span data-stu-id="20a1b-132">At this point, the web page is ready.</span></span> <span data-ttu-id="20a1b-133">Você pode abri-la em qualquer navegador e garantir que não sejam exibidos erros, embora ainda não haja nenhuma experiência imersiva.</span><span class="sxs-lookup"><span data-stu-id="20a1b-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="20a1b-134">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="20a1b-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20a1b-135">Próximo Tutorial: 2. Preparar uma cena</span><span class="sxs-lookup"><span data-stu-id="20a1b-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)