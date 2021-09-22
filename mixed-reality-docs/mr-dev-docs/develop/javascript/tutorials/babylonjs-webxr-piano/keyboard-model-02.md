---
title: Criar um modelo de piano em 3D
description: Saiba como criar um modelo de piano em 3D codificando com o Babylon.js
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: realidade misturada, javascript, tutorial, BabylonJS, hololens, realidade misturada, UWP, Windows 10, WebXR, web de imersão
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932502"
---
# <a name="tutorial-build-a-3d-piano-model"></a>Tutorial: Criar um modelo de piano em 3D

No tutorial anterior da série, configuramos uma página da Web contendo uma cena do Babylon.js com uma câmera e uma luz. Neste tutorial, criaremos e adicionaremos um modelo de piano à cena.

![Malha de piano vertical](./images/standup-piano-mesh.png)

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
> * Criar, posicionar e mesclar malhas
> * Criar um teclado de piano usando malhas de caixa
> * Importar um modelo 3D de uma estrutura de piano

## <a name="before-you-begin"></a>Antes de começar

Verifique se você passou pelo [tutorial anterior da série](introduction-01.md) e se já pode continuar adicionando ao código.

*index.html*

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

*scene.js*

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

## <a name="getting-started"></a>Introdução

Vamos começar criando um teclado de piano simples que tem esta estrutura:

![Descrição do registro do piano](./images/piano-register.jpg)

Nesta imagem, há 7 teclas brancas e 5 pretas, cada uma rotulada com o nome da nota. Um teclado completo de 88 teclas contém 7 repetições dessa seleção de teclas (também chamada de registro) e 4 teclas extras. Cada registro tem o dobro da frequência do registro anterior. Por exemplo, a frequência de tom de C5 (que indica a nota C no quinto registro) é o dobro da de C4, a frequência de tom de D5 é o dobro da de D4 e assim por diante.

Visualmente, todos os registros são exatamente iguais, de modo que podemos começar investigando como criar um teclado de piano simples com essa seleção de teclas. Mais tarde, podemos encontrar uma forma de expandir o escopo para um teclado de piano completo com 88 teclas.

## <a name="build-a-simple-piano-keyboard"></a>Criar um teclado de piano simples

> [!NOTE]
> Embora seja possível encontrar em fontes online modelos 3D prontos de teclados de piano e importá-los para a página da Web, criaremos o teclado do zero neste tutorial para ter o máximo de personalização e para demonstrar como é possível criar modelos 3D usando o Babylon.js.

1. Antes de começarmos a criar malhas para a criação do teclado, observe que cada tecla preta não fica perfeitamente alinhada ao meio das duas teclas brancas em volta dela e que nem todas as teclas têm a mesma largura. Ou seja, precisamos criar e posicionar a malha de cada tecla individualmente.

    ![Alinhamento das teclas pretas](./images/black-key-position.png)

1. Quanto às teclas brancas, podemos observar que cada uma delas é composta por duas partes: (1) a parte inferior abaixo das teclas pretas e (2) a parte superior ao lado das teclas pretas. As duas partes têm dimensões diferentes, mas são empilhadas para criar uma tecla branca completa.

    ![Forma das teclas brancas](./images/white-key-shape-label.png)

1. Este é o código para criar uma tecla branca referente à nota C (não se preocupe em adicioná-lo a *scene.js* ainda):

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    Aqui, criamos duas malhas de [Caixa](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh), uma para a parte inferior e outra para a superior da tecla branca. Depois, modificamos a posição da parte superior para empilhá-la sobre a inferior e movê-la para a esquerda a fim de deixar espaço para a tecla preta vizinha (C#).

    Por fim, essas duas partes foram mescladas usando a função [MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes), para que se tornassem uma tecla branca completa. Esta é a malha resultante que o código produziria:

    ![Tecla C branca](./images/white-key-c.png)

1. A criação de uma tecla preta é mais simples. Como todas as teclas pretas têm a forma de uma caixa, podemos criar uma tecla preta criando apenas uma malha de caixa com um [StandardMaterial](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color) de cor preta.

    > [!NOTE]
    > Como a cor da malha padrão é um cinza claro que se assemelha ao branco, este tutorial não inclui as etapas para adicionar material branco às teclas brancas. No entanto, fique à vontade para adicionar o material por conta própria se quiser que as teclas tenham uma cor branca clara e brilhante.

    Este é o código para criar a tecla C# preta (não se preocupe em adicioná-lo a *scene.js* também):

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    A tecla preta produzida pelo código (juntamente com a tecla branca anterior) teria esta aparência:

    ![Tecla C# preta](./images/black-key-csharp.png)

1. Como você pode ver, a criação de cada tecla pode gerar bastante código semelhante, uma vez que precisamos especificar as dimensões e a posição de cada uma delas. Vamos tentar tornar o processo de criação mais eficiente na próxima seção.

## <a name="build-a-simple-piano-keyboard-efficiently"></a>Criar um teclado de piano simples de maneira eficiente

1. Embora as teclas brancas tenham formas ligeiramente diferentes umas das outras, todas elas podem ser criadas combinando uma parte superior e uma inferior. Vamos implementar uma função genérica para criar e posicionar qualquer tecla branca.

    Adicione a função abaixo a *scene.js*, fora da função `createScene()`:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    Nesse bloco de código, criamos uma função chamada `buildKey()`, que compila e retorna uma tecla branca quando `props.type` é `"white"`. Identificando o tipo da tecla no parâmetro `props`, podemos criar teclas pretas e brancas na mesma função criando uma ramificação usando uma instrução if.

    Os parâmetros de `buildKey()` são:
    * **scene**: a cena em que a tecla se encontra
    * **parent**: o elemento pai da malha (isso nos permite agrupar todas as teclas em um só pai)
    * **props**: as propriedades da tecla que será criada

    O `props` de uma tecla branca conterá estes itens:
    * **type**: "white"
    * **name**: o nome da nota que a tecla representa
    * **topWidth**: a largura da parte superior
    * **bottomWidth**: a largura da parte inferior
    * **topPositionX**: a posição x da parte superior relativa à parte inferior
    * **wholePositionX**: a posição x da tecla inteira em relação ao ponto final do registro (a borda direita da tecla B).
    * **register**: o registro a que a tecla pertence (um número entre 0 e 8)
    * **referencePositionX**: a coordenada x do ponto final do registro (usada como ponto de referência).

    Ao separar `wholePositionX` e `referencePositionX`, podemos inicializar os parâmetros de `props` necessários para criar um tipo específico de tecla (por exemplo, C) em qualquer registro e, depois, adicionar `register` e `referencePositionX` a `props` ao criar essa tecla em um registro específico (por exemplo, C4 ou C5).

1. De maneira semelhante, também podemos escrever uma função genérica para criar uma tecla preta. Vamos expandir a função `buildKey()` para incluir essa lógica:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    O `props` de uma tecla preta contém os seguintes itens:

    * **type**: "black"
    * **name**: o nome da nota que a tecla representa
    * **wholePositionX**: a posição x da tecla inteira em relação ao ponto final do registro (a borda direita da tecla B)
    * **register**: o registro a que a tecla pertence (um número entre 0 e 8)
    * **referencePositionX**: a coordenada x do ponto final do registro (usada como ponto de referência).

    O `props` para criar uma tecla preta é muito mais simples porque a criação de uma tecla preta envolve somente a criação de uma caixa, e a largura e a posição z de todas as teclas pretas são iguais.

1. Agora que temos uma forma mais eficiente de criar as teclas, vamos inicializar uma matriz que armazena o `props` de cada tecla que corresponde a uma nota em um registro e chamar a função `buildKey()` com cada um deles para criar um teclado simples no quarto registro.

    Também criaremos um [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode) chamado `keyboard` para atuar como [pai](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent) de todas as teclas do piano. Como qualquer alteração de posição ou de escala aplicada ao pai também seria aplicada aos filhos, agrupar as teclas dessa maneira nos permitirá dimensionar ou movê-las como um todo.

    Acrescente as seguintes linhas de código à função `createScene()`:

    ```javascript
    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    Como você já deve ter notado, nesse bloco de código, estamos posicionando todas as teclas em relação à origem do espaço.

1. Este é o código que *scene.js* contém até agora:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]

        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. Esta seria a aparência do teclado resultante:

    ![Teclado de piano com um registro](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>Expandindo para um piano de 88 teclas

Nesta seção, vamos expandir o uso das funções de criação de teclas para gerar um teclado de piano completo com 88 teclas.

1. Conforme mencionado, um teclado de piano completo com 88 teclas contém 7 registros repetidos e 4 outras notas. Dessas notas adicionais, 3 estão no registro 0 (extremidade esquerda do teclado) e 1 está no registro 8 (extremidade direita do teclado).

    ![Layout do piano de 88 teclas](./images/88-key-piano-keyboard-layout.jpg)

1. Primeiro, trabalharemos na criação das 7 repetições completas adicionando mais um loop em torno do loop que escrevemos anteriormente. Substitua o loop anterior da função `buildKey()` pelo seguinte código:

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    Nesse loop, criamos as teclas dos registros 1 a 7 e incrementamos a posição de referência toda vez que passamos para o próximo registro.

1. Em seguida, vamos criar o restante das teclas. Adicione o seguinte trecho à função `createScene()`:

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    Observe que as teclas nas extremidades esquerda e direita do teclado do piano não se ajustam às dimensões das propriedades definidas em `keyParams` (porque elas não estão ao lado de uma tecla preta na extremidade), portanto, precisamos definir um novo objeto `props` para cada uma delas para especificar sua forma especial.

1. O teclado produzido deverá ser semelhante a este após as alterações serem feitas:

    ![Malha do teclado de piano completo](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>Adicionando uma estrutura de piano

1. A cena fica um pouco estranha com apenas um teclado flutuando no espaço. Vamos adicionar uma estrutura de piano ao redor do teclado para criar a aparência de um piano vertical.

1. Assim como criamos as teclas, também podemos criar a estrutura posicionando e combinando um grupo de malhas de caixa.

    No entanto, deixaremos esse desafio para você enfrentar por conta própria e usaremos [BABYLON.SceneLoader.ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh) para importar uma malha já criada de uma estrutura de piano vertical. Acrescente este trecho de código a `createScene()`:

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    Observe que estamos, mais uma vez, criando um `TransformNode` pai chamado `piano` para agrupar o teclado e a estrutura como um todo. Isso facilitará muito a movimentação ou o dimensionamento do piano inteiro caso venha a ser necessário fazer isso.

1. Após a estrutura ser importada, observe que o teclado fica posicionado na parte inferior dela (pois as coordenadas y das teclas são 0 por padrão). Vamos elevar o teclado para que ele se encaixe na estrutura do piano vertical:

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    Como `keyboard` é pai de todas as teclas do piano, podemos elevar todas as teclas alterando apenas a posição y de `keyboard`.

1. O código final de *scene.js* deve ter a seguinte aparência:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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

        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        // Register 1 through 7
        var referencePositionX = -2.4*14;
        for (let register = 1; register <= 7; register++) {
            keyParams.forEach(key => {
                buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
            })
            referencePositionX += 2.4*7;
        }
    
        // Register 0
        buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
        keyParams.slice(10, 12).forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
        })
    
        // Register 8
        buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    
        // Transform node that acts as the parent of all piano components
        const piano = new BABYLON.TransformNode("piano");
        keyboard.parent = piano;
    
        // Import and scale piano frame
        BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
            const frame = meshes[0];
            frame.parent = piano;
        });
    
        // Lift the piano keyboard
        keyboard.position.y += 80;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Agora, devemos ter um piano vertical semelhante a este: ![Malha de piano vertical](./images/standup-piano-mesh.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Próximo tutorial: Tocar o piano 3D](keyboard-interaction-03.md)
