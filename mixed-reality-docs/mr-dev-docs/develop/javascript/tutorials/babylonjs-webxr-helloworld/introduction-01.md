---
title: Introdução aos tutoriais babylon.js e WebXR
description: Conclua este curso para aprender a usar o babylon.js e criar um aplicativo básico de Realidade Misturada.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidade misturada, javascript, tutorial, BabylonJS, hololens, realidade misturada, UWP, Windows 10, WebXR, web de imersão
ms.localizationpriority: high
ms.openlocfilehash: e2006e911ad9dae00252c929c7739ff2209f4bf7796f1c49e713cfaf53267cd2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196820"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>Tutorial: Crie seu primeiro aplicativo WebXR usando babylon.js

Este tutorial mostrará como criar um aplicativo básico de Realidade Misturada usando o babylon.js e Visual Studio Code. O aplicativo que você irá criar renderizará um cubo, permitirá que você o gire para exibir as outras faces e adicionar interações. Neste tutorial, você aprenderá como:

> [!div class="checklist"]
> * Configurar um ambiente de desenvolvimento
> * API babylon.js para criar elementos 3D básicos  
> * Criar uma página da Web
> * Interagir com elementos 3D
> * Executar o aplicativo em um Simulador do Windows Mixed Reality

## <a name="prerequisites"></a>Pré-requisitos

* Navegador com suporte para WebXR, por [exemplo, Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 ou superior
* [NodeJS](https://nodejs.org/)
* Opcional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) se você quiser usar um Simulador do Windows Mixed Reality
* Opcional: [Simulador do Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="getting-started"></a>Introdução

Para criar esse projeto do zero, comece com um projeto do Visual Studio Code (VSCode).

> [!NOTE]
> O uso do VSCode não é obrigatório, mas o utilizaremos para sua conveniência ao longo do tutorial. Desenvolvedores JavaScript mais experientes podem usar qualquer outro editor de sua escolha, até mesmo os Bloco de Notas mais simples.

1. Baixe o arquivo único [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) ou use uma versão online que pode ser encontrada no [site oficial do babylon.js.](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) Você também pode clonar todo o projeto babylon.js do [GitHub](https://github.com/BabylonJS/Babylon.js)
1. Crie um arquivo vazio e salve-o como uma página HTML, por exemplo, index.html
1. Crie uma marcação HTML básica e faça referência ao arquivo JavaScript babylon.js. O código final é mostrado abaixo:

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

1. Adicione um elemento HTML de *tela* dentro do corpo para renderizar o conteúdo do babylon.js. Observe que a tela tem um atributo ID, que permite que você acesse esse elemento HTML do JavaScript posteriormente.

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

1. A tela ocupa toda a página da Web. Isso conclui nossa página da Web. Neste ponto, a página da Web está pronta. Você pode abri-la em qualquer navegador e garantir que não sejam exibidos erros, embora ainda não haja nenhuma experiência imersiva.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Próximo Tutorial: 2. Preparar uma cena](prepare-scene-02.md)