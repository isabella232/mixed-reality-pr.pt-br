---
title: Tutorial do Babylon.js para preparar uma cena com objetos 3D básicos
description: Saiba como usar babylon.js e adicionar objetos 3D básicos a uma cena.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidade misturada, javascript, tutorial, BabylonJS, hololens, realidade misturada, UWP, Windows 10, WebXR, web de imersão
ms.localizationpriority: high
ms.openlocfilehash: 9d74104924aa859f5ab18248a487a7e80392809adb09361e84c5ad386f1321c4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212374"
---
# <a name="tutorial-prepare-a-scene"></a>Tutorial: preparar uma cena

Saiba como preparar uma cena e adicionar alguns elementos 3D básicos a ela.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
> * Criar uma cena
> * Adicionar uma câmera
> * Adicionar luz
> * Adicionar elementos 3D básicos

## <a name="before-you-begin"></a>Antes de começar

Na etapa anterior do tutorial, uma página da Web básica foi criada. Abra a página da Web para edição.

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

## <a name="create-a-scene"></a>Criar uma cena

Uma cena é onde todo o conteúdo será exibido. Pode haver várias cenas, e é possível alternar entre cenas. Leia mais sobre [Cena do babylon.js](https://doc.babylonjs.com/divingDeeper/scene).

1. Adicione a marcação de scripts após o elemento HTML de tela, e adicione o seguinte código para criar uma cena preenchida com a cor preta:

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    No código acima, precisamos criar uma instância do mecanismo de renderização da Web do babylon.js, que processa uma cena e conecta eventos na tela. Para obter mais informações sobre o mecanismo, consulte a página de documentação [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)

1. A cena não é renderizada por padrão. Lembre-se, pode haver várias cenas e você pode controlar qual cena é exibida. Para renderizar a cena repetidamente em cada quadro, execute o seguinte código após a chamada para a função *createscene*:

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>Adicionar elemento 3D básico

1. Vamos adicionar nossa primeira forma 3D. No mundo virtual 3D, as formas são criadas a partir de *malhas*, muitas facetas triangulares unidas, cada faceta sendo feita a partir de três vértices. Você pode usar uma malha predefinida ou criar sua própria malha personalizada. Aqui, usaremos uma malha de caixa predefinida, ou seja, um cubo. Para criar a caixa, use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box). Os parâmetros são name e options (as opções são diferentes de acordo com o tipo de malha). Acrescente o seguinte código à função *createScene*:

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. Abra a página da Web no navegador Microsoft Edge e verifique a saída. A janela do navegador mostra uma página em branco. Abra DevTools usando o teclado e selecione F12 ou Control+Shift+I (Windows, Linux) ou Command+Option+I (macOS). Após abrir a guia *Console*, você pode começar a procurar erros. Um erro será exibido: 'Erro Não Identificado: nenhuma câmera foi definida'. Agora, precisamos adicionar uma câmera à cena.

## <a name="add-a-camera"></a>Adicionar uma câmera

1. Para exibir o mundo virtual e interagir com ele, uma câmera deve ser anexada à tela. Vamos adicionar a câmera do tipo [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), que pode ser girada ao redor de um alvo. Os parâmetros necessários para criar uma instância da câmera são:
    1. **name**: nome da câmera
    1. **alpha**: posição angular ao longo do eixo longitudinal (em radianos)
    1. **beta**: posição angular ao longo do eixo latitudinal (em radianos)
    1. **radius**: distância do alvo
    1. **target**: o ponto para o qual a câmera sempre se vira (definido pelas coordenadas x-y-z)
    1. **scene**: a cena na qual a câmera está

    Alpha, beta, radius e target, juntos, definem a posição da câmera no espaço, conforme mostrado no diagrama abaixo:

    ![Camera Alpha Beta Radius](../images/camera-alpha-beta-radius.jpg)

    Adicione o seguinte código à função *createScene*:

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. Se você verificar a saída no navegador, você verá uma tela preta. Falta a luz.

## <a name="add-light"></a>Adicionar luz

1. Há quatro tipos de luzes que podem ser usadas com uma gama de propriedades de iluminação: Ponto de Luz, Luz Direcional, Spot Light e Luz Hemisférica. Vamos adicionar a luz ambiente[HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight) da seguinte maneira:

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. O código final da página da Web será semelhante ao seguinte:

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. Verifique a saída no navegador. Você deve ver o cubo e, usando o mouse, você pode girar a câmera ao redor do cubo e ver as diferentes faces do cubo:

![Cena básica com cubo](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Próximo Tutorial: 3. Interagir com um objeto 3D](interact-03.md)
