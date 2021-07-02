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
# <a name="bounding-box"></a>Caixa delimitadora

![Caixa delimitadora](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> A caixa delimitada é preterida e substituída por seu controle de [limites de sucesso.](bounds-control.md) Use [uma das opções de migração para](#migrating-to-bounds-control) atualizar objetos de jogo existentes.

O [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornece funcionalidade básica para transformar objetos em realidade misturada. Uma caixa delimitada mostrará um cubo ao redor do holograma para indicar que ele pode ser interagido. As alças nos cantos e bordas do cubo permitem dimensionar ou girar o objeto. A caixa delimitada também reage à entrada do usuário. No HoloLens 2, por exemplo, a caixa delimitada responde à proximidade do dedo, fornecendo comentários visuais para ajudar a perceber a distância do objeto. Todas as interações e visuais podem ser facilmente personalizados.

Para obter mais informações, consulte [Caixa delimitada e Barra de](/windows/mixed-reality/app-bar-and-bounding-box) aplicativos no Windows Centro de Desenvolvimento.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos de configurações de caixa delimitadores na `BoundingBoxExamples` cena.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Como adicionar e configurar uma caixa delimitador usando o Inspetor do Unity

1. Adicionar Colisor de Caixa a um objeto
2. Atribuir `BoundingBox` script a um objeto
3. Configurar opções, como métodos de 'Ativação' (consulte [a seção Propriedades do](#inspector-properties) inspetor abaixo)
4. (Opcional) Atribuir pré-fabs e materiais para uma HoloLens delimitação de estilo 2 (consulte a [seção Manipular estilos](#handle-styles) abaixo)

> [!NOTE]
> Use *o campo Objeto de* Destino e Substituição de Limites no inspetor para atribuir um objeto e *colisor* específicos no objeto com vários componentes filho.

![Caixa delimitada 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Como adicionar e configurar uma caixa delimitada no código

1. Insinuar gameObject de cubo

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Atribuir `BoundingBox` script a um objeto com colisor usando AddComponent<>()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Configurar opções (consulte [a seção Propriedades do](#inspector-properties) inspetor abaixo)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. (Opcional) Atribua pré-fabs e materiais para uma HoloLens delimitação de estilo 2. Isso ainda requer atribuições por meio do inspetor, pois os materiais e os pré-requisitos devem ser carregados dinamicamente.

> [!NOTE]
> Não é recomendável usar a pasta 'Recursos' do Unity ou o [Sombreador.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) para carregar dinamicamente sombreadores, pois as permutações do sombreador podem estar ausentes em runtime.

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>Exemplo: definir a escala mínima e máxima da caixa delimitadora usando MinMaxScaleConstraint

Para definir a escala mínima e máxima, use o [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . Você também pode usar MinMaxScaleConstraint para definir a escala mínima e máxima para [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>Exemplo: Adicionar caixa delimitada em torno de um objeto de jogo

Para adicionar uma caixa delimitada em torno de um objeto, basta adicionar um `BoundingBox` componente a ele:

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Propriedades do inspetor

### <a name="target-object"></a>Objeto de destino

Essa propriedade especifica qual objeto será transformado pela manipulação de caixa delimitada. Se nenhum objeto for definido, a caixa delimitada assume como padrão o objeto proprietário.

### <a name="bounds-override"></a>Substituição de limites

Define um colisor de caixa do objeto para computação de limites.

### <a name="activation-behavior"></a>Comportamento de ativação

Há várias opções para ativar a interface da caixa delimitada.

* *Ativar Ao Iniciar:* a caixa delimitação fica visível depois que a cena é iniciada.
* *Ativar por proximidade:* a caixa delimitador fica visível quando uma mão articulada está próxima ao objeto.
* *Ativar por ponteiro:* a caixa delimitada fica visível quando é direcionada por um ponteiro de raio de mão.
* *Ativar Manualmente:* a caixa delimitada não fica visível automaticamente. Você pode ativá-lo manualmente por meio de um script acessando a propriedade boundingBox.Active.

### <a name="scale-minimum"></a>Dimensionar o mínimo

A escala mínima permitida. Essa propriedade foi preterida e é preferível adicionar um [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se esse script for adicionado, a escala mínima será retirada dele em vez da caixa delimitada.

### <a name="scale-maximum"></a>Dimensionar o máximo

A escala máxima permitida. Essa propriedade foi preterida e é preferível adicionar um [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se esse script for adicionado, a escala máxima será retirada dele em vez da caixa delimitada.

### <a name="box-display"></a>Exibição de caixa

Várias opções de visualização de caixa delimitada.

Se o Eixo Nivelar estiver definido como *Nivelar Automaticamente,* o script não permitirá a manipulação ao longo do eixo com a menor extensão. Isso resulta em uma caixa delimitada 2D, que geralmente é usada para objetos finos.

### <a name="handles"></a>Alças

Você pode atribuir o material e o pré-fab para substituir o estilo de alça. Se nenhum handle for atribuído, eles serão exibidos no estilo padrão.

## <a name="events"></a>Eventos

A caixa delimitada fornece os seguintes eventos. Este exemplo usa esses eventos para reproduzir comentários de áudio.

* **Rotação Iniciada:** acionado quando a rotação é iniciada.
* **Rotação Encerrada:** acionado quando a rotação termina.
* **Escala iniciada:** é a incêndio quando o dimensionamento é iniciado.
* **Escala encerrada:** é a incêndio quando o dimensionamento termina.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Manipular estilos

Por padrão, quando você apenas atribuir o script, ele mostrará o handle do estilo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) HoloLens 1ª geração. Para usar HoloLens 2 alças de estilo, você precisa atribuir pré-fabs e materiais de alça adequados.

![Estilos de alça de caixa delimitação](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

Abaixo estão os pré-fabs, os materiais e os valores de dimensionamento para os HoloLens de caixa delimitada de estilo 2. Você pode encontrar este exemplo na `BoundingBoxExamples` cena.

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>Alças (instalação para HoloLens estilo 2)

* **Material do handle:** BoundingBoxHandleWhite.mat
* **Material de alça ressalvado:** BoundingBoxHandleBlueGrabbed.mat
* **Pré-fab de alça de escala:** MRTK_BoundingBox_ScaleHandle.prefab
* **Pré-fab de Slate do Alça de** Escala: MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **Tamanho do alça de** escala: 0,016 (1,6 cm)
* **Preenchimento do Colisor de Alça** de Escala: 0,016 (torna o colisor acessível um pouco maior do que o visual de alça)
* **Pré-fab de alça de** rotação: MRTK_BoundingBox_RotateHandle.prefab
* **Tamanho do alça de** rotação: 0,016
* **Preenchimento do Colisor de** Alça de Rotação : 0,016 (torna o colisor acessível um pouco maior do que o visual de alça)

### <a name="proximity-setup-for-hololens-2-style"></a>Proximidade (instalação para HoloLens 2)

Mostrar e ocultar os alças com animação com base na distância até as mãos. Ele tem animação de dimensionamento em duas etapas.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Efeito de proximidade ativo:** habilitar a ativação de alça baseada em proximidade
* **Lidar com a proximidade média:** distância para o dimensionamento da primeira etapa
* **Lidar com proximidade próxima:** distância para o dimensionamento da segunda etapa
* **Escala distante:** valor de escala padrão do ativo de alça quando as mãos estão fora do intervalo da interação da caixa delimitada (distância definida acima por "Manipular proximidade média". Usar 0 para ocultar o handle por padrão)
* **Escala média:** valor de escala do ativo de alça quando as mãos estão dentro do intervalo da interação da caixa delimitada (distância definida acima por "Lidar com proximidade próxima". Use 1 para mostrar o tamanho normal)
* **Escala de Fechamento:** valor de escala do ativo de alça quando as mãos estão dentro do intervalo da interação de captura (distância definida acima por "Lidar com proximidade próxima". Usar 1.x para mostrar um tamanho maior)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Tornar um objeto móvel com o manipulador de manipulação

Uma caixa delimitada pode ser combinada com [`ManipulationHandler.cs`](manipulation-handler.md) para tornar o objeto móvel usando interação distante. O manipulador de manipulação dá suporte a interações de uma e de duas mãos. O [rastreamento manual](../input/hand-tracking.md) pode ser usado para interagir com um objeto de perto.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Para que as bordas da caixa delimitadora se comportem da mesma maneira ao movê-la usando a [`ManipulationHandler`](manipulation-handler.md) interação de longe, é aconselhável conectar seus eventos para a *manipulação iniciada*  /  *na manipulação finalizada* `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` , conforme mostrado na captura de tela acima.

## <a name="migrating-to-bounds-control"></a>Migrando para controle de limites

Pré-fabricados e instâncias existentes usando a [caixa delimitadora](bounding-box.md) podem ser atualizados para o novo controle de limites por meio da [janela de migração](../tools/migration-window.md) que faz parte do pacote de ferramentas do MRTK.

Para atualizar instâncias individuais da caixa delimitadora também há uma opção de migração dentro do Inspetor de propriedades do componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
