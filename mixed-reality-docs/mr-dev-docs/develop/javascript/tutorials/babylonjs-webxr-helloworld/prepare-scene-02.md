---
title: Tutorial do Babylon.js para preparar uma cena com objetos 3D básicos
description: Saiba como usar babylon.js e adicionar objetos 3D básicos a uma cena.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidade misturada, javascript, tutorial, BabylonJS, hololens, realidade misturada, UWP, Windows 10, WebXR, web de imersão
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584496"
---
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="644cf-104">Tutorial: preparar uma cena</span><span class="sxs-lookup"><span data-stu-id="644cf-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="644cf-105">Saiba como preparar uma cena e adicionar alguns elementos 3D básicos a ela.</span><span class="sxs-lookup"><span data-stu-id="644cf-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="644cf-106">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="644cf-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="644cf-107">Criar uma cena</span><span class="sxs-lookup"><span data-stu-id="644cf-107">Create a scene</span></span>
> * <span data-ttu-id="644cf-108">Adicionar uma câmera</span><span class="sxs-lookup"><span data-stu-id="644cf-108">Add a camera</span></span>
> * <span data-ttu-id="644cf-109">Adicionar luz</span><span class="sxs-lookup"><span data-stu-id="644cf-109">Add light</span></span>
> * <span data-ttu-id="644cf-110">Adicionar elementos 3D básicos</span><span class="sxs-lookup"><span data-stu-id="644cf-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="644cf-111">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="644cf-111">Before you begin</span></span>

<span data-ttu-id="644cf-112">Na etapa anterior do tutorial, uma página da Web básica foi criada.</span><span class="sxs-lookup"><span data-stu-id="644cf-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="644cf-113">Abra a página da Web para edição.</span><span class="sxs-lookup"><span data-stu-id="644cf-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="644cf-114">Criar uma cena</span><span class="sxs-lookup"><span data-stu-id="644cf-114">Create a scene</span></span>

<span data-ttu-id="644cf-115">Uma cena é onde todo o conteúdo será exibido.</span><span class="sxs-lookup"><span data-stu-id="644cf-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="644cf-116">Pode haver várias cenas, e é possível alternar entre cenas.</span><span class="sxs-lookup"><span data-stu-id="644cf-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="644cf-117">Leia mais sobre [Cena do babylon.js](https://doc.babylonjs.com/divingDeeper/scene).</span><span class="sxs-lookup"><span data-stu-id="644cf-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="644cf-118">Adicione a marcação de scripts após o elemento HTML de tela, e adicione o seguinte código para criar uma cena preenchida com a cor preta:</span><span class="sxs-lookup"><span data-stu-id="644cf-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

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

    <span data-ttu-id="644cf-119">No código acima, precisamos criar uma instância do mecanismo de renderização da Web do babylon.js, que processa uma cena e conecta eventos na tela.</span><span class="sxs-lookup"><span data-stu-id="644cf-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="644cf-120">Para obter mais informações sobre o mecanismo, consulte a página de documentação [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span><span class="sxs-lookup"><span data-stu-id="644cf-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="644cf-121">A cena não é renderizada por padrão.</span><span class="sxs-lookup"><span data-stu-id="644cf-121">The scene is not rendered by default.</span></span> <span data-ttu-id="644cf-122">Lembre-se, pode haver várias cenas e você pode controlar qual cena é exibida.</span><span class="sxs-lookup"><span data-stu-id="644cf-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="644cf-123">Para renderizar a cena repetidamente em cada quadro, execute o seguinte código após a chamada para a função *createscene*:</span><span class="sxs-lookup"><span data-stu-id="644cf-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="644cf-124">Adicionar elemento 3D básico</span><span class="sxs-lookup"><span data-stu-id="644cf-124">Add basic 3D element</span></span>

1. <span data-ttu-id="644cf-125">Vamos adicionar nossa primeira forma 3D.</span><span class="sxs-lookup"><span data-stu-id="644cf-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="644cf-126">No mundo virtual 3D, as formas são criadas a partir de *malhas*, muitas facetas triangulares unidas, cada faceta sendo feita a partir de três vértices.</span><span class="sxs-lookup"><span data-stu-id="644cf-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="644cf-127">Você pode usar uma malha predefinida ou criar sua própria malha personalizada.</span><span class="sxs-lookup"><span data-stu-id="644cf-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="644cf-128">Aqui, usaremos uma malha de caixa predefinida, ou seja, um cubo.</span><span class="sxs-lookup"><span data-stu-id="644cf-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="644cf-129">Para criar a caixa, use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span><span class="sxs-lookup"><span data-stu-id="644cf-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="644cf-130">Os parâmetros são name e options (as opções são diferentes de acordo com o tipo de malha).</span><span class="sxs-lookup"><span data-stu-id="644cf-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="644cf-131">Acrescente o seguinte código à função *createScene*:</span><span class="sxs-lookup"><span data-stu-id="644cf-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="644cf-132">Abra a página da Web no navegador Microsoft Edge e verifique a saída.</span><span class="sxs-lookup"><span data-stu-id="644cf-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="644cf-133">A janela do navegador mostra uma página em branco.</span><span class="sxs-lookup"><span data-stu-id="644cf-133">The browser window shows a blank page.</span></span> <span data-ttu-id="644cf-134">Abra DevTools usando o teclado e selecione F12 ou Control+Shift+I (Windows, Linux) ou Command+Option+I (macOS).</span><span class="sxs-lookup"><span data-stu-id="644cf-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="644cf-135">Após abrir a guia *Console*, você pode começar a procurar erros.</span><span class="sxs-lookup"><span data-stu-id="644cf-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="644cf-136">Um erro será exibido: 'Erro Não Identificado: nenhuma câmera foi definida'.</span><span class="sxs-lookup"><span data-stu-id="644cf-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="644cf-137">Agora, precisamos adicionar uma câmera à cena.</span><span class="sxs-lookup"><span data-stu-id="644cf-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="644cf-138">Adicionar uma câmera</span><span class="sxs-lookup"><span data-stu-id="644cf-138">Add a camera</span></span>

1. <span data-ttu-id="644cf-139">Para exibir o mundo virtual e interagir com ele, uma câmera deve ser anexada à tela.</span><span class="sxs-lookup"><span data-stu-id="644cf-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="644cf-140">Vamos adicionar a câmera do tipo [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), que pode ser girada ao redor de um alvo.</span><span class="sxs-lookup"><span data-stu-id="644cf-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="644cf-141">Os parâmetros necessários para criar uma instância da câmera são:</span><span class="sxs-lookup"><span data-stu-id="644cf-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="644cf-142">**name**: nome da câmera</span><span class="sxs-lookup"><span data-stu-id="644cf-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="644cf-143">**alpha**: posição angular ao longo do eixo longitudinal (em radianos)</span><span class="sxs-lookup"><span data-stu-id="644cf-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="644cf-144">**beta**: posição angular ao longo do eixo latitudinal (em radianos)</span><span class="sxs-lookup"><span data-stu-id="644cf-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="644cf-145">**radius**: distância do alvo</span><span class="sxs-lookup"><span data-stu-id="644cf-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="644cf-146">**target**: o ponto para o qual a câmera sempre se vira (definido pelas coordenadas x-y-z)</span><span class="sxs-lookup"><span data-stu-id="644cf-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="644cf-147">**scene**: a cena na qual a câmera está</span><span class="sxs-lookup"><span data-stu-id="644cf-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="644cf-148">Alpha, beta, radius e target, juntos, definem a posição da câmera no espaço, conforme mostrado no diagrama abaixo:</span><span class="sxs-lookup"><span data-stu-id="644cf-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![Camera Alpha Beta Radius](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="644cf-150">Adicione o seguinte código à função *createScene*:</span><span class="sxs-lookup"><span data-stu-id="644cf-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="644cf-151">Se você verificar a saída no navegador, você verá uma tela preta.</span><span class="sxs-lookup"><span data-stu-id="644cf-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="644cf-152">Falta a luz.</span><span class="sxs-lookup"><span data-stu-id="644cf-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="644cf-153">Adicionar luz</span><span class="sxs-lookup"><span data-stu-id="644cf-153">Add light</span></span>

1. <span data-ttu-id="644cf-154">Há quatro tipos de luzes que podem ser usadas com uma gama de propriedades de iluminação: Ponto de Luz, Luz Direcional, Spot Light e Luz Hemisférica.</span><span class="sxs-lookup"><span data-stu-id="644cf-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="644cf-155">Vamos adicionar a luz ambiente[HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="644cf-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="644cf-156">O código final da página da Web será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="644cf-156">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="644cf-157">Verifique a saída no navegador.</span><span class="sxs-lookup"><span data-stu-id="644cf-157">Check the output in the browser.</span></span> <span data-ttu-id="644cf-158">Você deve ver o cubo e, usando o mouse, você pode girar a câmera ao redor do cubo e ver as diferentes faces do cubo:</span><span class="sxs-lookup"><span data-stu-id="644cf-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![Cena básica com cubo](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="644cf-160">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="644cf-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="644cf-161">Próximo Tutorial: 3. Interagir com um objeto 3D</span><span class="sxs-lookup"><span data-stu-id="644cf-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)
