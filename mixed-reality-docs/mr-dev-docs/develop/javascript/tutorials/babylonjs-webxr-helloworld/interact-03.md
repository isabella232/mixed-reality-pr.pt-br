---
title: Tutorial do Babylon.js para interagir com objetos 3D
description: Saiba como usar o babylon.js e interagir com objetos 3D.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidade misturada, javascript, tutorial, BabylonJS, hololens, realidade misturada, UWP, Windows 10, WebXR, web de imersão
ms.localizationpriority: high
ms.openlocfilehash: a3dbab0572cd50105dac3d877a0d72c5cbc504b6
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584515"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="38c8f-104">Tutorial: Interagir com um objeto 3D</span><span class="sxs-lookup"><span data-stu-id="38c8f-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="38c8f-105">Saiba como criar objetos 3D e interações para uma experiência de Realidade Misturada usando babylon.js.</span><span class="sxs-lookup"><span data-stu-id="38c8f-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="38c8f-106">Nesta seção, você começará com algo simples, como pintar os lados de um cubo ao selecionar o objeto.</span><span class="sxs-lookup"><span data-stu-id="38c8f-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="38c8f-107">Este tutorial abrange os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="38c8f-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="38c8f-108">Como adicionar interações</span><span class="sxs-lookup"><span data-stu-id="38c8f-108">How to add interactions</span></span>
> * <span data-ttu-id="38c8f-109">Habilitar o modo imersivo do WebXR</span><span class="sxs-lookup"><span data-stu-id="38c8f-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="38c8f-110">Executar o aplicativo no Simulador do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="38c8f-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="38c8f-111">Executar e depurar o aplicativo no Chrome para Android</span><span class="sxs-lookup"><span data-stu-id="38c8f-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="38c8f-112">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="38c8f-112">Before you begin</span></span>

<span data-ttu-id="38c8f-113">Na etapa anterior do tutorial, uma página da Web básica com uma cena foi criada.</span><span class="sxs-lookup"><span data-stu-id="38c8f-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="38c8f-114">Abra a página da Web de hospedagem para edição.</span><span class="sxs-lookup"><span data-stu-id="38c8f-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="38c8f-115">Adicionar interação</span><span class="sxs-lookup"><span data-stu-id="38c8f-115">Add interaction</span></span>

1. <span data-ttu-id="38c8f-116">Em primeiro lugar, vamos atualizar nosso código que cria o cubo, para que o cubo seja pintado com uma cor aleatória.</span><span class="sxs-lookup"><span data-stu-id="38c8f-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="38c8f-117">Para fazer isso, vamos adicionar [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) ao cubo.</span><span class="sxs-lookup"><span data-stu-id="38c8f-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="38c8f-118">O material nos permite especificar cores e texturas, e pode ser usado para cobrir outros objetos.</span><span class="sxs-lookup"><span data-stu-id="38c8f-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="38c8f-119">A forma como um material é exibido depende da luz ou das luzes usadas na cena e de como ele está definido para reagir.</span><span class="sxs-lookup"><span data-stu-id="38c8f-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="38c8f-120">Por exemplo, diffuseColor propaga a cor por toda a malha à qual está anexada.</span><span class="sxs-lookup"><span data-stu-id="38c8f-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="38c8f-121">Adicione os códigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="38c8f-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="38c8f-122">Agora que o cubo está pintado com uma cor aleatória, vamos adicionar uma interação para:</span><span class="sxs-lookup"><span data-stu-id="38c8f-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="38c8f-123">Alterar a cor ao clicar no cubo</span><span class="sxs-lookup"><span data-stu-id="38c8f-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="38c8f-124">Mover o cubo depois que a cor for alterada</span><span class="sxs-lookup"><span data-stu-id="38c8f-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="38c8f-125">Para adicionar interações, devemos usar [ações](https://doc.babylonjs.com/divingDeeper/events/actions).</span><span class="sxs-lookup"><span data-stu-id="38c8f-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="38c8f-126">Uma ação é lançada em resposta ao gatilho de evento.</span><span class="sxs-lookup"><span data-stu-id="38c8f-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="38c8f-127">Por exemplo, quando o usuário clica no cubo.</span><span class="sxs-lookup"><span data-stu-id="38c8f-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="38c8f-128">Para isso, precisamos, apenas, criar uma instância BABYLON.ActionManager e registrar uma ação para um gatilho específico.</span><span class="sxs-lookup"><span data-stu-id="38c8f-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="38c8f-129">O [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) executará nossa função JavaScript quando alguém clicar no cubo:</span><span class="sxs-lookup"><span data-stu-id="38c8f-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

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

1. <span data-ttu-id="38c8f-130">O código final da página da Web será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="38c8f-130">The final code of the web page will look as follows:</span></span>

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="38c8f-131">Habilitar a experiência imersiva do WebXR</span><span class="sxs-lookup"><span data-stu-id="38c8f-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="38c8f-132">Agora que nosso cubo está mudando as cores, estamos prontos para tentar a experiência imersiva.</span><span class="sxs-lookup"><span data-stu-id="38c8f-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="38c8f-133">Nesta etapa, apresentaremos uma [área](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span><span class="sxs-lookup"><span data-stu-id="38c8f-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="38c8f-134">O cubo será suspenso no ar e veremos uma base na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="38c8f-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="38c8f-135">Adicione a área da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="38c8f-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="38c8f-136">Isso cria uma base simples de 4x4 metros.</span><span class="sxs-lookup"><span data-stu-id="38c8f-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="38c8f-137">Para adicionar suporte a WebXR, precisamos chamar *createDefaultXRExperienceAsync*, que tem *Promessa* como resultado.</span><span class="sxs-lookup"><span data-stu-id="38c8f-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="38c8f-138">Adicione esse código no final da função *createScene* em vez da *cena de retorno;* :</span><span class="sxs-lookup"><span data-stu-id="38c8f-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="38c8f-139">Como a função *createScene* retorna uma promessa ao invés de uma cena, precisamos modificar como *createScene* e *engine.runRenderLoop* são chamados.</span><span class="sxs-lookup"><span data-stu-id="38c8f-139">Since the *createScene* function is now returning a promise instead of a scene, we need to modify how *createScene* and *engine.runRenderLoop* are called.</span></span> <span data-ttu-id="38c8f-140">Substitua as chamadas atuais dessas funções, que estão localizadas antes da marca *\</script>* , pelo código abaixo:</span><span class="sxs-lookup"><span data-stu-id="38c8f-140">Replace the current calls of these functions, which are located right before the *\</script>* tag, with the code below:</span></span>

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. <span data-ttu-id="38c8f-141">O código final da página da Web será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="38c8f-141">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="38c8f-142">O código acima gera a seguinte saída na janela do navegador: ![ cena do WebXR](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="38c8f-142">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="38c8f-143">Executar em um simulador do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="38c8f-143">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="38c8f-144">[Habilite o Simulador do Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) caso você ainda não tenha feito isso.</span><span class="sxs-lookup"><span data-stu-id="38c8f-144">[Enable the Windows Mixed Reality Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) if you have not done so in the past.</span></span>

1. <span data-ttu-id="38c8f-145">Selecione o botão VR Imersiva no canto inferior direito: ![ Botão VR Imersiva](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="38c8f-145">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="38c8f-146">Essa ação iniciará a janela Simulador do Windows Mixed Reality, conforme mostrado abaixo: ![ Portal de Realidade Misturada](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="38c8f-146">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="38c8f-147">Use as teclas W, A, S e D no teclado para avançar, voltar para a esquerda e para a direita de forma correspondente.</span><span class="sxs-lookup"><span data-stu-id="38c8f-147">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="38c8f-148">Use a mão simulada para direcionar o cubo e pressione a tecla Enter no teclado para executar a ação de clicar.</span><span class="sxs-lookup"><span data-stu-id="38c8f-148">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="38c8f-149">O cubo alterará sua cor e passará para uma nova posição.</span><span class="sxs-lookup"><span data-stu-id="38c8f-149">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="38c8f-150">Ao direcionar o cubo, certifique-se de que o fim do raio de mão (círculo branco) cruze com o cubo, conforme mostrado na imagem acima.</span><span class="sxs-lookup"><span data-stu-id="38c8f-150">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="38c8f-151">Saiba mais sobre [Apontar e confirmar com as mãos](../../../../design/point-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="38c8f-151">Learn more about [Point and commit with hands](../../../../design/point-and-commit.md).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="38c8f-152">Executar e depurar no dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="38c8f-152">Run and debug on Android device</span></span>

<span data-ttu-id="38c8f-153">Execute as seguintes etapas para habilitar a depuração em seu dispositivo Android:</span><span class="sxs-lookup"><span data-stu-id="38c8f-153">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="38c8f-154">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="38c8f-154">Prerequisites</span></span>

* <span data-ttu-id="38c8f-155">Um servidor Web que funciona como uma página HTML estática no contexto seguro (https:// ou por meio do encaminhamento de porta no localhost) no computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="38c8f-155">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="38c8f-156">Por exemplo, aproveite o pacote npm de *serviço* como um servidor Web leve e simples que fornece arquivos HTML estáticos, saiba mais em [serviço npm](https://github.com/vercel/serve#readme)</span><span class="sxs-lookup"><span data-stu-id="38c8f-156">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="38c8f-157">O dispositivo originalmente fornecido com o Google Play Store e deve estar executando o Android 7.0 ou mais recente</span><span class="sxs-lookup"><span data-stu-id="38c8f-157">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="38c8f-158">A versão mais recente do [Google Chrome](https://support.google.com/chrome/answer/95346) na estação de trabalho de desenvolvimento e no dispositivo</span><span class="sxs-lookup"><span data-stu-id="38c8f-158">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="38c8f-159">Para verificar se o dispositivo está configurado corretamente para executar o WebXR, navegue até uma [página WebXR de exemplo](https://immersive-web.github.io/webxr-samples/) no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38c8f-159">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="38c8f-160">Você deverá ver uma mensagem como:</span><span class="sxs-lookup"><span data-stu-id="38c8f-160">You should see the message, such as:</span></span>

    > <span data-ttu-id="38c8f-161">Seu navegador dá suporte ao WebXR e pode executar experiências de Realidade Virtual e Realidade Aumentada se você tiver o hardware apropriado.</span><span class="sxs-lookup"><span data-stu-id="38c8f-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="38c8f-162">Habilite o modo de desenvolvedor e a depuração USB em um dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="38c8f-162">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="38c8f-163">Veja como fazer isso para sua versão do Android na página da documentação oficial [Configurar opções de desenvolvedor no dispositivo](https://developer.android.com/studio/debug/dev-options)</span><span class="sxs-lookup"><span data-stu-id="38c8f-163">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="38c8f-164">Em seguida, conecte o dispositivo Android ao computador de desenvolvimento ou laptop com o cabo USB</span><span class="sxs-lookup"><span data-stu-id="38c8f-164">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="38c8f-165">Verifique se o servidor Web no computador de desenvolvimento está em execução.</span><span class="sxs-lookup"><span data-stu-id="38c8f-165">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="38c8f-166">Por exemplo, navegue até a pasta raiz que contém sua página de hospedagem da Web (index.html) e execute o seguinte código (supondo que você use o pacote npm de serviço):</span><span class="sxs-lookup"><span data-stu-id="38c8f-166">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="38c8f-167">Abra o Google Chrome em seu computador de desenvolvimento e insira o seguinte texto na barra de endereços:</span><span class="sxs-lookup"><span data-stu-id="38c8f-167">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="38c8f-168">chrome://inspect#devices ![Janela de depuração USB do Chrome](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="38c8f-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="38c8f-169">Verifique se a caixa de seleção *Descobrir dispositivos USB* está habilitada</span><span class="sxs-lookup"><span data-stu-id="38c8f-169">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="38c8f-170">Clique no botão *Encaminhamento de porta* e verifique se o *Encaminhamento de porta* está habilitado e contém uma entrada *localhost:5000* conforme mostrado abaixo: ![janela Encaminhamento de Porta do Chrome](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="38c8f-170">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="38c8f-171">No dispositivo Android conectado, abra uma janela do Google Chrome e navegue até *http://localhost:5000* e você deverá ver o cubo</span><span class="sxs-lookup"><span data-stu-id="38c8f-171">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="38c8f-172">No computador de desenvolvimento, no Chrome, você verá seu dispositivo e uma lista de páginas da Web abertas: ![janela Inspeção do Chrome](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="38c8f-172">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="38c8f-173">Clique no botão *Inspecionar* ao lado de uma entrada *http://localhost:5000* :  ![ janela Depuração do DevTools do Chrome](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="38c8f-173">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="38c8f-174">Usar o [DevTools do Chrome](https://developers.google.com/web/tools/chrome-devtools) para depurar a página</span><span class="sxs-lookup"><span data-stu-id="38c8f-174">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="38c8f-175">Observações</span><span class="sxs-lookup"><span data-stu-id="38c8f-175">Takeaways</span></span>

<span data-ttu-id="38c8f-176">A seguir estão as conclusões mais importantes deste tutorial:</span><span class="sxs-lookup"><span data-stu-id="38c8f-176">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="38c8f-177">Babylon.js facilita a criação de experiências imersivas usando JavaScript</span><span class="sxs-lookup"><span data-stu-id="38c8f-177">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="38c8f-178">Para criar cenas virtuais, você não precisa escrever código de baixo nível nem aprender uma nova tecnologia</span><span class="sxs-lookup"><span data-stu-id="38c8f-178">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="38c8f-179">Você pode criar aplicativos de Realidade Misturada com o navegador compatível com WebXR sem a necessidade de comprar um headset</span><span class="sxs-lookup"><span data-stu-id="38c8f-179">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="38c8f-180">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="38c8f-180">Next steps</span></span>

<span data-ttu-id="38c8f-181">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="38c8f-181">Congratulations!</span></span> <span data-ttu-id="38c8f-182">Você concluiu nossa série de tutoriais babylon.js e aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="38c8f-182">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="38c8f-183">Configurar um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="38c8f-183">Set up a development environment</span></span>
> * <span data-ttu-id="38c8f-184">Criar uma nova página Web para exibir resultados</span><span class="sxs-lookup"><span data-stu-id="38c8f-184">Create a new web page to display results</span></span>
> * <span data-ttu-id="38c8f-185">API babylon.js para criar e interagir com elementos 3D básicos</span><span class="sxs-lookup"><span data-stu-id="38c8f-185">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="38c8f-186">Executar e testar o aplicativo em um Simulador do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="38c8f-186">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="38c8f-187">Para obter mais informações sobre o desenvolvimento de JavaScript de Realidade Misturada, consulte [Visão geral do desenvolvimento do JavaScript](/javascript-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="38c8f-187">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
