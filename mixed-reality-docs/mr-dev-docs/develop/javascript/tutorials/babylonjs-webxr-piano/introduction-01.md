---
title: Criando um piano no WebXR usando o BabylonJS
description: Conclua esta série de tutoriais para aprender a criar um teclado de piano funcional com 88 teclas no WebXR usando o BabylonJS
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: realidade misturada, javascript, tutorial, BabylonJS, hololens, realidade misturada, UWP, Windows 10, WebXR, web de imersão
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932485"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>Tutorial: Criar um piano no WebXR usando o Babylon.js

Construir um piano no mundo real exige muito em termos de tempo, habilidades e materiais. E a criação de um para o mundo de VR/RA?

Nesta série de tutoriais, você aprenderá a usar o Babylon.js para criar um aplicativo Web de Realidade Misturada que contém um piano vertical funcional com 88 teclas no mundo virtual. No aplicativo pronto, você poderá se teletransportar para o piano e tocar as teclas usando seus controladores de Realidade Misturada.

Nesta série de tutoriais, você aprenderá a:

> [!div class="checklist"]
> * Criar, posicionar e mesclar malhas para criar um teclado de piano
> * Importar um modelo do Babylon.js de uma estrutura de piano vertical
> * Adicionar interações de ponteiro a cada tecla do piano
> * Habilitar o teletransporte e o suporte para vários ponteiros no WebXR

## <a name="prerequisites"></a>Pré-requisitos

* Um computador conectado à Internet
* Conhecimento básico de JavaScript
* [Tutorial Olá, Mundo de JavaScript para WebXR](../babylonjs-webxr-helloworld/introduction-01.md)
* Navegador com suporte para WebXR, por [exemplo, Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 ou superior
* Qualquer [headset de VR](../../../../discover/immersive-headset-hardware-details.md) ou um [simulador do Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)
* Opcional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) se você quiser usar um Simulador do Windows Mixed Reality

## <a name="getting-started"></a>Introdução

Vamos começar configurando a página da Web HTML que conterá a cena do Babylon.js.

1. Crie uma pasta chamada *babylonjs-piano-tutorial* e abra essa pasta no Visual Studio Code.

    > [!NOTE]
    > Embora você possa usar qualquer editor de código para acompanhar, usaremos o Visual Studio Code neste tutorial por conveniência.

1. Na pasta, crie um arquivo chamado *index.html* e insira o modelo abaixo nele:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    Se precisar de mais explicações sobre o conteúdo deste modelo, confira o [Tutorial Olá, Mundo](../babylonjs-webxr-helloworld/introduction-01.md), que é um pré-requisito deste tutorial.

1. Se você tentar abrir o arquivo em um navegador, o console mostrará um erro indicando que a função `createScene()` não foi encontrada. Vamos resolver esse erro implementando a função `createScene()` na próxima seção.

## <a name="setup-the-scene"></a>Configurar a cena

1. Na mesma pasta em que se encontra *index.html*, crie outro arquivo chamado *scene.js*. Armazenaremos todo o código JavaScript relacionado à configuração da cena e à criação do piano nesse arquivo.

1. Vamos adicionar a função `createScene()` a *scene.js*:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    Observe que estamos fazendo de `createScene()` uma função assíncrona. Preste atenção para descobrir por quê.

1. Em seguida, precisaremos de uma luz e de uma câmera para tornar a cena visível para nós. Atualize a função `createScene()`:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    Aqui, criamos uma [ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), que aponta quase completamente para baixo e está direcionada para o ponto de origem do espaço. A luz que criamos é uma [HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light) que aponta para o céu e é útil para simular um espaço ambiente. Também esmaecemos um pouco a luz diminuindo sua intensidade.

    Se precisar de um lembrete sobre como criar uma câmera e uma luz, reveja a [seção Preparar cena da série de tutoriais Olá, Mundo](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera) antes de seguir para a próxima etapa.

1. Por fim, como estamos desenvolvendo para uma plataforma WebXR, precisaremos [habilitar a experiência de XR](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR) na cena inserindo a seguinte linha antes de `return scene;`:

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    No JavaScript, para usar o teclado `await` em uma função `async` dentro de uma função, a função pai também teria que ser `async`. Por isso definimos a função `createScene` como assíncrona anteriormente. Mais adiante nesta série de tutoriais, usaremos esse `xrHelper` para habilitar e configurar diferentes recursos do WebXR com suporte do Babylon.js.

1. O arquivo *scene.js* concluído deve ser semelhante a este:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Agora que temos uma função `createScene()` funcional, vamos fazer com que *index.html* carregue o arquivo *scene.js* como um script para que a função `createScene()` seja reconhecida em *index.html*. Adicione esta linha de código dentro da seção `<header>` do arquivo HTML:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. Abra *index.html* no navegador e você descobrirá que a mensagem de erro que vimos anteriormente não está mais presente e que temos uma cena do Babylon.js vazia na página.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Próximo tutorial: Criar um modelo de piano em 3D](keyboard-model-02.md)
