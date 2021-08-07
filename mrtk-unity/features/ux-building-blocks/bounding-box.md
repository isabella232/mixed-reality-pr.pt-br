---
title: Caixa delimitadora
description: Visão geral na caixa delimitadora em MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, caixa delimitadora
ms.openlocfilehash: fa1ace9d7aaf547ee677accfc4254ce9c64aebdfa6a01f11962812b058bc9ceb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214190"
---
# <a name="bounding-box"></a>Caixa delimitadora

![Caixa delimitadora](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> A caixa delimitadora foi preterida e substituída por seu [controle de limites](bounds-control.md)de sucessora. Use [uma das opções de migração](#migrating-to-bounds-control) para atualizar os objetos de jogo existentes.

O [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornece a funcionalidade básica para transformar objetos em realidade misturada. Uma caixa delimitadora mostrará um cubo ao direcionar o holograma para indicar que ele pode ser interagindo. As alças nos cantos e nas bordas do cubo permitem dimensionar ou girar o objeto. A caixa delimitadora também reage à entrada do usuário. no HoloLens 2, por exemplo, a caixa delimitadora responde à proximidade do dedo, fornecendo comentários visuais para ajudar a perceber a distância do objeto. Todas as interações e visuais podem ser facilmente personalizados.

para obter mais informações, consulte [caixa delimitadora e barra de aplicativos](/windows/mixed-reality/app-bar-and-bounding-box) no Centro de Desenvolvimento Windows.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos de configurações de caixa delimitadora na `BoundingBoxExamples` cena.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Como adicionar e configurar uma caixa delimitadora usando o Inspetor do Unity

1. Adicionar Colisor de caixa a um objeto
2. Atribuir `BoundingBox` script a um objeto
3. Configurar opções, como métodos de ' ativação ' (consulte a seção [Propriedades do Inspetor](#inspector-properties) abaixo)
4. Adicional atribua pré-fabricados e materiais para uma caixa delimitadora de estilo de HoloLens 2 (consulte a seção de [estilos de identificador](#handle-styles) abaixo)

> [!NOTE]
> Use o *objeto de destino* e o campo de substituição de *limites* no Inspetor para atribuir um objeto específico e um colisor no objeto com vários componentes filho.

![Caixa delimitadora 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Como adicionar e configurar uma caixa delimitadora no código

1. Criar instância de gameobject do cubo

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Atribuir `BoundingBox` script a um objeto com o colisor, usando o addComponent<> ()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Configurar opções (consulte a seção [Propriedades do Inspetor](#inspector-properties) abaixo)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. Adicional atribua pré-fabricados e materiais para uma caixa delimitadora de estilo de HoloLens 2. Isso ainda requer atribuições por meio do Inspetor, pois os materiais e pré-fabricados devem ser carregados dinamicamente.

> [!NOTE]
> O uso da pasta ' recursos ' ou do [sombreador]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) do Unity. não é recomendável localizar sombreadores dinamicamente, pois as permutações do sombreador podem estar ausentes no tempo de execução.

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

## <a name="example-add-bounding-box-around-a-game-object"></a>Exemplo: adicionar uma caixa delimitadora em um objeto de jogo

Para adicionar uma caixa delimitadora em um objeto, basta adicionar um `BoundingBox` componente a ela:

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Propriedades do Inspetor

### <a name="target-object"></a>Objeto de destino

Esta propriedade especifica qual objeto será transformado pela manipulação da caixa delimitadora. Se nenhum objeto for definido, a caixa delimitadora definirá como padrão o objeto do proprietário.

### <a name="bounds-override"></a>Substituição de limites

Define um colisor de caixa do objeto para computação de limites.

### <a name="activation-behavior"></a>Comportamento de ativação

Há várias opções para ativar a interface da caixa delimitadora.

* *Ativar ao iniciar*: a caixa delimitadora fica visível quando a cena é iniciada.
* *Ativar por proximidade*: a caixa delimitadora fica visível quando uma mão articulada está perto do objeto.
* *Ativar por ponteiro*: a caixa delimitadora torna-se visível quando é direcionada por um ponteiro de raio à mão.
* *Ativar manualmente*: a caixa delimitadora não se torna visível automaticamente. Você pode ativá-lo manualmente por meio de um script acessando a propriedade boundingBox. Active.

### <a name="scale-minimum"></a>Mínimo de escala

A escala mínima permitida. Essa propriedade é preterida e é preferível adicionar um [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se esse script for adicionado, a escala mínima será retirada dele, em vez da caixa delimitadora.

### <a name="scale-maximum"></a>Máximo de escala

A escala máxima permitida. Essa propriedade é preterida e é preferível adicionar um [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se esse script for adicionado, a escala máxima será retirada dele, em vez da caixa delimitadora.

### <a name="box-display"></a>Exibição da caixa

Várias opções de visualização de caixa delimitadora.

Se o eixo achatado for definido como *automático achatado*, o script não permitirá a manipulação ao longo do eixo com a menor extensão. Isso resulta em uma caixa delimitadora de 2D, que geralmente é usada para objetos finos.

### <a name="handles"></a>Alças

Você pode atribuir o material e o pré-fabricado para substituir o estilo do identificador. Se nenhum identificador for atribuído, ele será exibido no estilo padrão.

## <a name="events"></a>Eventos

A caixa delimitadora fornece os seguintes eventos. Este exemplo usa esses eventos para reproduzir comentários de áudio.

* **Rotação iniciada**: acionada quando a rotação é iniciada.
* **Rotação encerrada**: acionada quando a rotação termina.
* **Escala iniciada**: acionada quando o dimensionamento é iniciado.
* **Escala encerrada**: acionada quando o dimensionamento termina.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Estilos de identificador

por padrão, quando você apenas atribui o [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, ele mostrará o identificador do estilo de HoloLens 1ª gen. para usar os identificadores de estilo HoloLens 2, você precisa atribuir o identificador adequado pré-fabricados e materiais.

![Estilos de identificador de caixa delimitadora](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

abaixo estão os valores de pré-fabricados, materiais e dimensionamento para os identificadores de caixa delimitadora de HoloLens 2. Você pode encontrar este exemplo na `BoundingBoxExamples` cena.

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>identificadores (instalação para HoloLens estilo 2)

* **Material de tratamento**: BoundingBoxHandleWhite. passe-partout
* **Tratar material capturado**: BoundingBoxHandleBlueGrabbed. passe-partout
* **Identificador de escala pré-fabricado**: MRTK_BoundingBox_ScaleHandle. pré-fabricado
* **Alça de escala Slate pré-fabricado**: MRTK_BoundingBox_ScaleHandle_Slate. pré-fabricado
* **Tamanho do identificador de escala**: 0, 16 (1.6 cm)
* **Enchimento do Colisador da alça de escala**: 0, 16 (torna o colisor de captura ligeiramente maior que o Visual do manipulador)
* **Identificador de rotação pré-fabricado**: MRTK_BoundingBox_RotateHandle. pré-fabricado
* **Tamanho da alça de rotação**: 0, 16
* **Enchimento do Colisador da alça de rotação**: 0, 16 (torna o colisor de captura ligeiramente maior que o Visual do manipulador)

### <a name="proximity-setup-for-hololens-2-style"></a>proximidade (configuração para o estilo HoloLens 2)

Mostrar e ocultar os identificadores com animação com base na distância para as mãos. Ele tem uma animação de dimensionamento em duas etapas.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Efeito de proximidade ativo**: habilitar a ativação de identificador baseado em proximidade
* **Lidar com a proximidade média**: distância para o dimensionamento da 1ª etapa
* **Lidar com proximidades próximas**: distância para o dimensionamento da 2ª etapa
* **Escala extrema**: o valor de escala padrão do ativo de identificador quando as mãos estão fora do intervalo da interação da caixa delimitadora (distância definida acima por ' tratar a proximidade média '. Use 0 para ocultar o identificador por padrão)
* **Escala média**: o valor de escala do ativo de identificador quando as mãos estão dentro do intervalo da interação da caixa delimitadora (distância definida acima por ' manipular proximidades '. Use 1 para mostrar o tamanho normal)
* **Fechar escala**: o valor de escala do ativo de identificador quando as mãos estão dentro do intervalo da interação de captura (distância definida acima por ' manipular proximidades à próxima '. Use 1. x para mostrar um tamanho maior)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Tornando um objeto móvel com o manipulador de manipulação

Uma caixa delimitadora pode ser combinada com [`ManipulationHandler.cs`](manipulation-handler.md) o para tornar o objeto móvel usando a interação distante. O manipulador de manipulação dá suporte a interações de uma e de duas mãos. O [rastreamento manual](../input/hand-tracking.md) pode ser usado para interagir com um objeto de perto.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Para que as bordas da caixa delimitadora se comportem da mesma maneira ao movê-la usando a [`ManipulationHandler`](manipulation-handler.md) interação de longe, é aconselhável conectar seus eventos para a *manipulação iniciada*  /  *na manipulação finalizada* `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` , conforme mostrado na captura de tela acima.

## <a name="migrating-to-bounds-control"></a>Migrando para controle de limites

Pré-fabricados e instâncias existentes usando a [caixa delimitadora](bounding-box.md) podem ser atualizados para o novo controle de limites por meio da [janela de migração](../tools/migration-window.md) que faz parte do pacote de ferramentas do MRTK.

Para atualizar instâncias individuais da caixa delimitadora também há uma opção de migração dentro do Inspetor de propriedades do componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
