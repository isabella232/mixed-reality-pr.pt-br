---
title: Caixa delimitadora
description: Visão geral sobre caixa delimitada no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Caixa Delimitada
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177540"
---
# <a name="bounding-box"></a><span data-ttu-id="e6e8d-104">Caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="e6e8d-104">Bounding box</span></span>

![Caixa delimitadora](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="e6e8d-106">A caixa delimitada é preterida e substituída por seu controle de [limites de sucesso.](bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="e6e8d-107">Use [uma das opções de migração para](#migrating-to-bounds-control) atualizar objetos de jogo existentes.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="e6e8d-108">O [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornece funcionalidade básica para transformar objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="e6e8d-109">Uma caixa delimitada mostrará um cubo ao redor do holograma para indicar que ele pode ser interagido.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="e6e8d-110">As alças nos cantos e bordas do cubo permitem dimensionar ou girar o objeto.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="e6e8d-111">A caixa delimitada também reage à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="e6e8d-112">No HoloLens 2, por exemplo, a caixa delimitada responde à proximidade do dedo, fornecendo comentários visuais para ajudar a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="e6e8d-113">Todas as interações e visuais podem ser facilmente personalizados.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="e6e8d-114">Para obter mais informações, consulte [Caixa delimitada e Barra de](/windows/mixed-reality/app-bar-and-bounding-box) aplicativos no Windows Centro de Desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-114">For more information, see [Bounding box and App bar](/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="e6e8d-115">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="e6e8d-115">Example scene</span></span>

<span data-ttu-id="e6e8d-116">Você pode encontrar exemplos de configurações de caixa delimitadores na `BoundingBoxExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="e6e8d-117">Como adicionar e configurar uma caixa delimitador usando o Inspetor do Unity</span><span class="sxs-lookup"><span data-stu-id="e6e8d-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="e6e8d-118">Adicionar Colisor de Caixa a um objeto</span><span class="sxs-lookup"><span data-stu-id="e6e8d-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="e6e8d-119">Atribuir `BoundingBox` script a um objeto</span><span class="sxs-lookup"><span data-stu-id="e6e8d-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="e6e8d-120">Configurar opções, como métodos de 'Ativação' (consulte [a seção Propriedades do](#inspector-properties) inspetor abaixo)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="e6e8d-121">(Opcional) Atribuir pré-fabs e materiais para uma HoloLens delimitação de estilo 2 (consulte a [seção Manipular estilos](#handle-styles) abaixo)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="e6e8d-122">Use *o campo Objeto de* Destino e Substituição de Limites no inspetor para atribuir um objeto e *colisor* específicos no objeto com vários componentes filho.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Caixa delimitada 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="e6e8d-124">Como adicionar e configurar uma caixa delimitada no código</span><span class="sxs-lookup"><span data-stu-id="e6e8d-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="e6e8d-125">Insinuar gameObject de cubo</span><span class="sxs-lookup"><span data-stu-id="e6e8d-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="e6e8d-126">Atribuir `BoundingBox` script a um objeto com colisor usando AddComponent<>()</span><span class="sxs-lookup"><span data-stu-id="e6e8d-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="e6e8d-127">Configurar opções (consulte [a seção Propriedades do](#inspector-properties) inspetor abaixo)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="e6e8d-128">(Opcional) Atribua pré-fabs e materiais para uma HoloLens delimitação de estilo 2.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="e6e8d-129">Isso ainda requer atribuições por meio do inspetor, pois os materiais e os pré-requisitos devem ser carregados dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="e6e8d-130">Não é recomendável usar a pasta 'Recursos' do Unity ou o [Sombreador.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) para carregar dinamicamente sombreadores, pois as permutações do sombreador podem estar ausentes em runtime.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="e6e8d-131">Exemplo: definir a escala mínima e máxima da caixa delimitadora usando MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="e6e8d-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="e6e8d-132">Para definir a escala mínima e máxima, use o [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) .</span><span class="sxs-lookup"><span data-stu-id="e6e8d-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="e6e8d-133">Você também pode usar MinMaxScaleConstraint para definir a escala mínima e máxima para [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="e6e8d-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="e6e8d-134">Exemplo: Adicionar caixa delimitada em torno de um objeto de jogo</span><span class="sxs-lookup"><span data-stu-id="e6e8d-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="e6e8d-135">Para adicionar uma caixa delimitada em torno de um objeto, basta adicionar um `BoundingBox` componente a ele:</span><span class="sxs-lookup"><span data-stu-id="e6e8d-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="e6e8d-136">Propriedades do inspetor</span><span class="sxs-lookup"><span data-stu-id="e6e8d-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="e6e8d-137">Objeto de destino</span><span class="sxs-lookup"><span data-stu-id="e6e8d-137">Target object</span></span>

<span data-ttu-id="e6e8d-138">Essa propriedade especifica qual objeto será transformado pela manipulação de caixa delimitada.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="e6e8d-139">Se nenhum objeto for definido, a caixa delimitada assume como padrão o objeto proprietário.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="e6e8d-140">Substituição de limites</span><span class="sxs-lookup"><span data-stu-id="e6e8d-140">Bounds override</span></span>

<span data-ttu-id="e6e8d-141">Define um colisor de caixa do objeto para computação de limites.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="e6e8d-142">Comportamento de ativação</span><span class="sxs-lookup"><span data-stu-id="e6e8d-142">Activation behavior</span></span>

<span data-ttu-id="e6e8d-143">Há várias opções para ativar a interface da caixa delimitada.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="e6e8d-144">*Ativar Ao Iniciar:* a caixa delimitação fica visível depois que a cena é iniciada.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="e6e8d-145">*Ativar por proximidade:* a caixa delimitador fica visível quando uma mão articulada está próxima ao objeto.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="e6e8d-146">*Ativar por ponteiro:* a caixa delimitada fica visível quando é direcionada por um ponteiro de raio de mão.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="e6e8d-147">*Ativar Manualmente:* a caixa delimitada não fica visível automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="e6e8d-148">Você pode ativá-lo manualmente por meio de um script acessando a propriedade boundingBox.Active.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="e6e8d-149">Dimensionar o mínimo</span><span class="sxs-lookup"><span data-stu-id="e6e8d-149">Scale minimum</span></span>

<span data-ttu-id="e6e8d-150">A escala mínima permitida.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-150">The minimum allowed scale.</span></span> <span data-ttu-id="e6e8d-151">Essa propriedade foi preterida e é preferível adicionar um [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="e6e8d-152">Se esse script for adicionado, a escala mínima será retirada dele em vez da caixa delimitada.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="e6e8d-153">Dimensionar o máximo</span><span class="sxs-lookup"><span data-stu-id="e6e8d-153">Scale maximum</span></span>

<span data-ttu-id="e6e8d-154">A escala máxima permitida.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-154">The maximum allowed scale.</span></span> <span data-ttu-id="e6e8d-155">Essa propriedade foi preterida e é preferível adicionar um [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="e6e8d-156">Se esse script for adicionado, a escala máxima será retirada dele em vez da caixa delimitada.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="e6e8d-157">Exibição de caixa</span><span class="sxs-lookup"><span data-stu-id="e6e8d-157">Box display</span></span>

<span data-ttu-id="e6e8d-158">Várias opções de visualização de caixa delimitada.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="e6e8d-159">Se o Eixo Nivelar estiver definido como *Nivelar Automaticamente,* o script não permitirá a manipulação ao longo do eixo com a menor extensão.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="e6e8d-160">Isso resulta em uma caixa delimitada 2D, que geralmente é usada para objetos finos.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="e6e8d-161">Alças</span><span class="sxs-lookup"><span data-stu-id="e6e8d-161">Handles</span></span>

<span data-ttu-id="e6e8d-162">Você pode atribuir o material e o pré-fab para substituir o estilo de alça.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="e6e8d-163">Se nenhum handle for atribuído, eles serão exibidos no estilo padrão.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="e6e8d-164">Eventos</span><span class="sxs-lookup"><span data-stu-id="e6e8d-164">Events</span></span>

<span data-ttu-id="e6e8d-165">A caixa delimitada fornece os seguintes eventos.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-165">Bounding box provides the following events.</span></span> <span data-ttu-id="e6e8d-166">Este exemplo usa esses eventos para reproduzir comentários de áudio.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="e6e8d-167">**Rotação Iniciada:** acionado quando a rotação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="e6e8d-168">**Rotação Encerrada:** acionado quando a rotação termina.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="e6e8d-169">**Escala iniciada:** é a incêndio quando o dimensionamento é iniciado.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="e6e8d-170">**Escala encerrada:** é a incêndio quando o dimensionamento termina.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="e6e8d-171">Manipular estilos</span><span class="sxs-lookup"><span data-stu-id="e6e8d-171">Handle styles</span></span>

<span data-ttu-id="e6e8d-172">Por padrão, quando você apenas atribuir o script, ele mostrará o handle do estilo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) HoloLens 1ª geração.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="e6e8d-173">Para usar HoloLens 2 alças de estilo, você precisa atribuir pré-fabs e materiais de alça adequados.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Estilos de alça de caixa delimitação](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="e6e8d-175">Abaixo estão os pré-fabs, os materiais e os valores de dimensionamento para os HoloLens de caixa delimitada de estilo 2.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="e6e8d-176">Você pode encontrar este exemplo na `BoundingBoxExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="e6e8d-177">Alças (instalação para HoloLens estilo 2)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="e6e8d-178">**Material do handle:** BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="e6e8d-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="e6e8d-179">**Material de alça ressalvado:** BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="e6e8d-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="e6e8d-180">**Pré-fab de alça de escala:** MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="e6e8d-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="e6e8d-181">**Pré-fab de Slate do Alça de** Escala: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="e6e8d-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="e6e8d-182">**Tamanho do alça de** escala: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="e6e8d-183">**Preenchimento do Colisor de Alça** de Escala: 0,016 (torna o colisor acessível um pouco maior do que o visual de alça)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="e6e8d-184">**Pré-fab de alça de** rotação: MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="e6e8d-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="e6e8d-185">**Tamanho do alça de** rotação: 0,016</span><span class="sxs-lookup"><span data-stu-id="e6e8d-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="e6e8d-186">**Preenchimento do Colisor de** Alça de Rotação : 0,016 (torna o colisor acessível um pouco maior do que o visual de alça)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="e6e8d-187">Proximidade (instalação para HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="e6e8d-188">Mostrar e ocultar os alças com animação com base na distância até as mãos.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="e6e8d-189">Ele tem animação de dimensionamento em duas etapas.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="e6e8d-190">**Efeito de proximidade ativo:** habilitar a ativação de alça baseada em proximidade</span><span class="sxs-lookup"><span data-stu-id="e6e8d-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="e6e8d-191">**Lidar com a proximidade média:** distância para o dimensionamento da primeira etapa</span><span class="sxs-lookup"><span data-stu-id="e6e8d-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="e6e8d-192">**Lidar com proximidade próxima:** distância para o dimensionamento da segunda etapa</span><span class="sxs-lookup"><span data-stu-id="e6e8d-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="e6e8d-193">**Escala distante:** valor de escala padrão do ativo de alça quando as mãos estão fora do intervalo da interação da caixa delimitada (distância definida acima por "Manipular proximidade média".</span><span class="sxs-lookup"><span data-stu-id="e6e8d-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="e6e8d-194">Usar 0 para ocultar o handle por padrão)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="e6e8d-195">**Escala média:** valor de escala do ativo de alça quando as mãos estão dentro do intervalo da interação da caixa delimitada (distância definida acima por "Lidar com proximidade próxima".</span><span class="sxs-lookup"><span data-stu-id="e6e8d-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="e6e8d-196">Use 1 para mostrar o tamanho normal)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="e6e8d-197">**Escala de Fechamento:** valor de escala do ativo de alça quando as mãos estão dentro do intervalo da interação de captura (distância definida acima por "Lidar com proximidade próxima".</span><span class="sxs-lookup"><span data-stu-id="e6e8d-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="e6e8d-198">Usar 1.x para mostrar um tamanho maior)</span><span class="sxs-lookup"><span data-stu-id="e6e8d-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="e6e8d-199">Tornar um objeto móvel com o manipulador de manipulação</span><span class="sxs-lookup"><span data-stu-id="e6e8d-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="e6e8d-200">Uma caixa delimitada pode ser combinada com [`ManipulationHandler.cs`](manipulation-handler.md) para tornar o objeto móvel usando interação distante.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="e6e8d-201">O manipulador de manipulação dá suporte a interações de uma e de duas mãos.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="e6e8d-202">O [rastreamento manual](../input/hand-tracking.md) pode ser usado para interagir com um objeto de perto.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="e6e8d-203">Para que as bordas da caixa delimitadora se comportem da mesma maneira ao movê-la usando a [`ManipulationHandler`](manipulation-handler.md) interação de longe, é aconselhável conectar seus eventos para a *manipulação iniciada*  /  *na manipulação finalizada* `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` , conforme mostrado na captura de tela acima.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="e6e8d-204">Migrando para controle de limites</span><span class="sxs-lookup"><span data-stu-id="e6e8d-204">Migrating to bounds control</span></span>

<span data-ttu-id="e6e8d-205">Pré-fabricados e instâncias existentes usando a [caixa delimitadora](bounding-box.md) podem ser atualizados para o novo controle de limites por meio da [janela de migração](../tools/migration-window.md) que faz parte do pacote de ferramentas do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="e6e8d-206">Para atualizar instâncias individuais da caixa delimitadora também há uma opção de migração dentro do Inspetor de propriedades do componente.</span><span class="sxs-lookup"><span data-stu-id="e6e8d-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
