---
title: Tutorial do Babylon.js para interagir com objetos 3D
description: Saiba como usar o babylon.js e interagir com objetos 3D.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidade misturada, javascript, tutorial, BabylonJS, hololens, realidade misturada, UWP, Windows 10, WebXR, web de imersão
ms.localizationpriority: high
ms.openlocfilehash: 9aa044789c5d9d331677206dbc7ef7170bfa592075819ae73bd46aa14116122a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196866"
---
# <a name="tutorial-interact-with-3d-object"></a>Tutorial: Interagir com um objeto 3D

Saiba como criar objetos 3D e interações para uma experiência de Realidade Misturada usando babylon.js. Nesta seção, você começará com algo simples, como pintar os lados de um cubo ao selecionar o objeto.

Este tutorial abrange os seguintes tópicos:

> [!div class="checklist"]
> * Como adicionar interações
> * Habilitar o modo imersivo do WebXR
> * Executar o aplicativo no Simulador do Windows Mixed Reality
> * Executar e depurar o aplicativo no Chrome para Android

## <a name="before-you-begin"></a>Antes de começar

Na etapa anterior do tutorial, uma página da Web básica com uma cena foi criada. Abra a página da Web de hospedagem para edição.

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

## <a name="add-interaction"></a>Adicionar interação

1. Em primeiro lugar, vamos atualizar nosso código que cria o cubo, para que o cubo seja pintado com uma cor aleatória. Para fazer isso, vamos adicionar [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) ao cubo. O material nos permite especificar cores e texturas, e pode ser usado para cobrir outros objetos. A forma como um material é exibido depende da luz ou das luzes usadas na cena e de como ele está definido para reagir. Por exemplo, diffuseColor propaga a cor por toda a malha à qual está anexada. Adicione os códigos a seguir:

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. Agora que o cubo está pintado com uma cor aleatória, vamos adicionar uma interação para:

    * Alterar a cor ao clicar no cubo
    * Mover o cubo depois que a cor for alterada

    Para adicionar interações, devemos usar [ações](https://doc.babylonjs.com/divingDeeper/events/actions). Uma ação é lançada em resposta ao gatilho de evento. Por exemplo, quando o usuário clica no cubo. Para isso, precisamos, apenas, criar uma instância BABYLON.ActionManager e registrar uma ação para um gatilho específico. O [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) executará nossa função JavaScript quando alguém clicar no cubo:

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a>Habilitar a experiência imersiva do WebXR

Agora que nosso cubo está mudando as cores, estamos prontos para tentar a experiência imersiva.

1. Nesta etapa, apresentaremos uma [área](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground). O cubo será suspenso no ar e veremos uma base na parte inferior. Adicione a área da seguinte forma:

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    Isso cria uma base simples de 4x4 metros.

1. Para adicionar suporte a WebXR, precisamos chamar *createDefaultXRExperienceAsync*, que tem *Promessa* como resultado. Adicione esse código no final da função *createScene* em vez da *cena de retorno;* :

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. Como a função *createScene* retorna uma promessa ao invés de uma cena, precisamos modificar como *createScene* e *engine.runRenderLoop* são chamados. Substitua as chamadas atuais dessas funções, que estão localizadas antes da marca *\</script>* , pelo código abaixo:

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. O código acima gera a seguinte saída na janela do navegador: ![ cena do WebXR](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>Executar em um simulador do Windows Mixed Reality

1. [Habilite o Simulador do Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) caso você ainda não tenha feito isso.

1. Selecione o botão VR Imersiva no canto inferior direito: ![ Botão VR Imersiva](../images/immersive-vr-button.png)

1. Essa ação iniciará a janela Simulador do Windows Mixed Reality, conforme mostrado abaixo: ![ Portal de Realidade Misturada](../images/mixed-reality-portal.png)

1. Use as teclas W, A, S e D no teclado para avançar, voltar para a esquerda e para a direita de forma correspondente. Use a mão simulada para direcionar o cubo e pressione a tecla Enter no teclado para executar a ação de clicar. O cubo alterará sua cor e passará para uma nova posição.

> [!NOTE]
> Ao direcionar o cubo, certifique-se de que o fim do raio de mão (círculo branco) cruze com o cubo, conforme mostrado na imagem acima. Saiba mais sobre [Apontar e confirmar com as mãos](../../../../design/point-and-commit.md).

## <a name="run-and-debug-on-android-device"></a>Executar e depurar no dispositivo Android

Execute as seguintes etapas para habilitar a depuração em seu dispositivo Android:

### <a name="prerequisites"></a>Pré-requisitos

* Um servidor Web que funciona como uma página HTML estática no contexto seguro (https:// ou por meio do encaminhamento de porta no localhost) no computador de desenvolvimento. Por exemplo, aproveite o pacote npm de *serviço* como um servidor Web leve e simples que fornece arquivos HTML estáticos, saiba mais em [serviço npm](https://github.com/vercel/serve#readme)
* O dispositivo originalmente fornecido com o Google Play Store e deve estar executando o Android 7.0 ou mais recente
* A versão mais recente do [Google Chrome](https://support.google.com/chrome/answer/95346) na estação de trabalho de desenvolvimento e no dispositivo
* Para verificar se o dispositivo está configurado corretamente para executar o WebXR, navegue até uma [página WebXR de exemplo](https://immersive-web.github.io/webxr-samples/) no dispositivo. Você deverá ver uma mensagem como:

    > Seu navegador dá suporte ao WebXR e pode executar experiências de Realidade Virtual e Realidade Aumentada se você tiver o hardware apropriado.

1. Habilite o modo de desenvolvedor e a depuração USB em um dispositivo Android. Veja como fazer isso para sua versão do Android na página da documentação oficial [Configurar opções de desenvolvedor no dispositivo](https://developer.android.com/studio/debug/dev-options)
1. Em seguida, conecte o dispositivo Android ao computador de desenvolvimento ou laptop com o cabo USB
1. Verifique se o servidor Web no computador de desenvolvimento está em execução. Por exemplo, navegue até a pasta raiz que contém sua página de hospedagem da Web (index.html) e execute o seguinte código (supondo que você use o pacote npm de serviço):

    ```bash
    serve
    ```

1. Abra o Google Chrome em seu computador de desenvolvimento e insira o seguinte texto na barra de endereços:
    > chrome://inspect#devices ![Janela de depuração USB do Chrome](../images/chrome-usb-debug.png)
1. Verifique se a caixa de seleção *Descobrir dispositivos USB* está habilitada
1. Clique no botão *Encaminhamento de porta* e verifique se o *Encaminhamento de porta* está habilitado e contém uma entrada *localhost:5000* conforme mostrado abaixo: ![janela Encaminhamento de Porta do Chrome](../images/chrome-port-forwarding.png)
1. No dispositivo Android conectado, abra uma janela do Google Chrome e navegue até *http://localhost:5000* e você deverá ver o cubo
1. No computador de desenvolvimento, no Chrome, você verá seu dispositivo e uma lista de páginas da Web abertas: ![janela Inspeção do Chrome](../images/chrome-inspect.png)
1. Clique no botão *Inspecionar* ao lado de uma entrada *http://localhost:5000* :  ![ janela Depuração do DevTools do Chrome](../images/chrome-debug.png)
1. Usar o [DevTools do Chrome](https://developers.google.com/web/tools/chrome-devtools) para depurar a página

## <a name="takeaways"></a>Observações

A seguir estão as conclusões mais importantes deste tutorial:
* Babylon.js facilita a criação de experiências imersivas usando JavaScript
* Para criar cenas virtuais, você não precisa escrever código de baixo nível nem aprender uma nova tecnologia
* Você pode criar aplicativos de Realidade Misturada com o navegador compatível com WebXR sem a necessidade de comprar um headset

## <a name="next-steps"></a>Próximas etapas

Parabéns! Você concluiu nossa série de tutoriais babylon.js e aprendeu a:
> [!div class="checklist"]
> * Configurar um ambiente de desenvolvimento
> * Criar uma nova página Web para exibir resultados
> * API babylon.js para criar e interagir com elementos 3D básicos
> * Executar e testar o aplicativo em um Simulador do Windows Mixed Reality

Para obter mais informações sobre o desenvolvimento de JavaScript de Realidade Misturada, consulte [Visão geral do desenvolvimento do JavaScript](/javascript-development-overview.md).
