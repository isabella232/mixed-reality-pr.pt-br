---
title: Controle de limites
description: Visão geral sobre o controle de limites no MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Controle de Limites,
ms.openlocfilehash: f5f5e1f463f741eb23f75c9826034b8974baf947
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176466"
---
# <a name="bounds-control"></a>Controle de limites

![Controle de limites](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl* é o novo componente para o comportamento de manipulação, encontrado anteriormente *em BoundingBox.* O controle de limites faz várias melhorias e simplificações na instalação e adiciona novos recursos. Esse componente é uma substituição para a caixa delimitada, que será preterida.

O [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fornece funcionalidade básica para transformar objetos em realidade misturada. Um controle de limites mostrará uma caixa ao redor do holograma para indicar que ele pode ser interagido. As alças nos cantos e bordas da caixa permitem dimensionamento, rotação ou tradução do objeto. O controle de limites também reage à entrada do usuário. No HoloLens 2, por exemplo, o controle de limites responde à proximidade do dedo, fornecendo comentários visuais para ajudar a perceber a distância do objeto. Todas as interações e visuais podem ser facilmente personalizados.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos de configurações de controle de limites na `BoundsControlExamples` cena.

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Propriedades do inspetor

### <a name="target-object"></a>Objeto de destino

Essa propriedade especifica qual objeto será transformado pela manipulação de controle de limites. Se nenhum objeto for definido, o padrão será o objeto proprietário.

### <a name="activation-behavior"></a>Comportamento de ativação

Há várias opções para ativar a interface de controle de limites.

* *Ativar Ao Iniciar:* o controle de limites fica visível depois que a cena é iniciada.
* *Ativar por proximidade:* o controle de limites fica visível quando uma mão articulada está perto do objeto.
* *Ativar por ponteiro:* o controle de limites fica visível quando é direcionado por um ponteiro de raio de mão.
* *Ativar por proximidade e ponteiro:* o controle de limites fica visível quando é direcionado por um ponteiro de raio de mão ou uma mão articulada está perto do objeto.
* *Ativar Manualmente:* o controle de limites não fica visível automaticamente. Você pode ativá-lo manualmente por meio de um script acessando a propriedade boundsControl.Active.

### <a name="bounds-override"></a>Substituição de limites

Define um colisor de caixa do objeto para computação de limites.

### <a name="box-padding"></a>Preenchimento de caixa

Adiciona um preenchimento aos limites do colisor usados para calcular as extensão do controle. Isso influenciará não apenas a interação, mas também afetará os visuais.

### <a name="flatten-axis"></a>Eixo de nivelar

Indica se o controle é nivelado em um dos eixos, tornando-o bidimensional e não permite a manipulação ao longo desse eixo. Esse recurso pode ser usado para objetos finos, como slates.
Se o eixo nivelado estiver definido como *Nivelar Automaticamente,* o script escolherá automaticamente o eixo com a menor extensão como eixo nivelado.

### <a name="smoothing"></a>Suavização

A seção de suavização permite configurar o comportamento de suavização para escala e rotação do controle.

### <a name="visuals"></a>Visuais

A aparência do controle de limites pode ser configurada modificando uma das configurações de visuais correspondentes.
As configurações visuais são objetos vinculados ou inlinados que podem ser scripts e são descritas mais detalhadamente na seção [do objeto de configuração](#configuration-objects).

## <a name="configuration-objects"></a>Objetos de configuração

O controle vem com um conjunto de objetos de configuração que podem ser armazenados como objetos que podem ser scripts e compartilhados entre diferentes instâncias ou pré-fabs. As configurações podem ser compartilhadas e vinculadas como arquivos de ativos individuais com script ou ativos aninhados que podem ser script dentro de pré-requisitos. Outras configurações também podem ser definidas diretamente na instância sem vincular a um ativo externo ou aninhado que pode ser script.

O inspetor de controle de limites indicará se uma configuração é compartilhada ou emlinada como parte da instância atual mostrando uma mensagem no inspetor de propriedade. Além disso, as instâncias compartilhadas não serão editáveis diretamente na própria janela de propriedades de controle de limites, mas, em vez disso, o ativo ao que está vinculando precisa ser diretamente modfiado para evitar alterações acidentais em configurações compartilhadas.

Atualmente, o controle de limites oferece opções de objetos de configuração para os seguintes recursos:

* Alças
  * [Alças de escala](#scale-handles-configuration)
  * [Alças de rotação](#rotation-handles-configuration)
  * [Alças de tradução](#translation-handles-configuration)
* [Links/Wireframe](#links-configuration-wireframe)
* [Exibição de caixa](#box-configuration)
* [Efeito de proximidade](#proximity-effect-configuration)

### <a name="box-configuration"></a>Configuração de caixa

A configuração da caixa é responsável por renderizar uma caixa sólida com limites definidos por meio do tamanho do colisor e preenchimento de caixa. As propriedades a seguir podem ser configuradas:

* **Material da** caixa : define o material aplicado à caixa renderizada quando nenhuma interação ocorre. Uma caixa só será renderizada se esse material estiver definido.
* **Material capturado por** caixa: material para a caixa quando o usuário interage com o controle, segurando por meio de interação próxima ou distante.
* **Escala de exibição do** eixo de nivelar: uma escala aplicada à caixa exibida se um dos eixos for [nivelado.](#flatten-axis)

### <a name="scale-handles-configuration"></a>Configuração de alças de escala

Essa gaveta de propriedades permite modificar o comportamento e a visualização de alças de escala do controle de limites.

* **Material do** handle: material aplicado aos alças.
* **Manipular material capturado:** material aplicado à alça de segurar.
* **Tratar pré-fab**: pré-fab opcional para o alça de escala. Se non for definido, o MRTK usará um cubo como padrão.
* **Tamanho do handle:** tamanho do alça de escala.
* **Preenchimento do colisor:** preenchimento para adicionar ao colisor de alça.
* **Desenhar ao manipular**: quando ativo desenhará uma linha de tether do ponto de início da interação até a posição atual da mão ou do ponteiro.
* **Alças ignoram colisor:** se um colisor for vinculado aqui, os alças ignorarão qualquer colisão com esse colisor.
* **Lidar com o pré-fab slate**: pré-fab a ser usado para o alça quando o controle é nivelado.
* **Mostrar alças de escala:** controla a visibilidade do alça.
* **Comportamento de escala:** pode ser definido como dimensionamento uniforme ou não uniforme.

### <a name="rotation-handles-configuration"></a>Configuração de alças de rotação

Essa configuração define o comportamento do alça de rotação.

* **Material do** handle: material aplicado aos alças.
* **Manipular material capturado:** material aplicado à alça de segurar.
* **Tratar pré-fab**: pré-fab opcional para o alça. Se non for definido, o MRTK usará uma esfera como padrão.
* **Tamanho do handle:** tamanho do alça.
* **Preenchimento do colisor:** preenchimento para adicionar ao colisor de alça.
* **Desenhar ao manipular**: quando ativo desenhará uma linha de tether do ponto de início da interação até a posição atual da mão ou do ponteiro.
* **Alças ignoram colisor:** se um colisor for vinculado aqui, os alças ignorarão qualquer colisão com esse colisor.
* **Manipular o tipo de colisor de pré-fab**: tipo de colisor a ser usado com o identificador criado.
* **Mostrar o handle para X:** controla a visibilidade do alça para o eixo X.
* **Mostrar o handle para Y:** controla a visibilidade do alça para o eixo Y.
* **Mostrar o handle para Z:** controla a visibilidade do alça para o eixo Z.

### <a name="translation-handles-configuration"></a>Configuração de alças de tradução

Permite habilenciar e configurar os alças de tradução para o controle de limites. Observe que os alças de tradução estão desabilitados por padrão.

* **Material do** handle: material aplicado aos alças.
* **Manipular material capturado:** material aplicado à alça de segurar.
* **Tratar pré-fab**: pré-fab opcional para o alça. Se non for definido, o MRTK usará uma esfera como padrão.
* **Tamanho do handle:** tamanho do alça.
* **Preenchimento do colisor:** preenchimento para adicionar ao colisor de alça.
* **Desenhar ao manipular**: quando ativo desenhará uma linha de tether do ponto de início da interação até a posição atual da mão ou do ponteiro.
* Os **identificadores ignoram o colisor**: se um colisor estiver vinculado aqui, os identificadores ignorarão qualquer colisão com esse colisor.
* **Manipular tipo de colisor pré-fabricado**: tipo de colisor a ser usado com o identificador criado.
* **Mostrar identificador de x**: controla a visibilidade do identificador para o eixo x.
* **Mostrar identificador para y**: controla a visibilidade do identificador para o eixo y.
* **Mostrar identificador para Z**: controla a visibilidade do identificador para o eixo Z.

### <a name="links-configuration-wireframe"></a>Configuração de links (wireframe)

A configuração de links habilita o recurso de wireframe do controle de limites. As seguintes propriedades podem ser configuradas:

* **Material de wireframe**: o material aplicado à malha de wireframe.
* **Raio da borda do wireframe**: a espessura do wireframe.
* **Forma de wireframe**: a forma do Wireframe pode ser por cúbico ou cilíndrico.
* **Mostrar wireframe**: controla a visibilidade do wireframe.

### <a name="proximity-effect-configuration"></a>Configuração de efeito de proximidade

Mostrar e ocultar os identificadores com animação com base na distância para as mãos. Ele tem uma animação de dimensionamento em duas etapas. os padrões são definidos para o comportamento de estilo HoloLens 2.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **Efeito de proximidade ativo**: habilitar a ativação de identificador baseado em proximidade
* **Proximidade da mídia do objeto**: distância para o dimensionamento da 1ª etapa
* **Proximidade do objeto**: distância para o dimensionamento da 2ª etapa
* **Escala extrema**: o valor de escala padrão do ativo de identificador quando as mãos estão fora do intervalo da interação de controle de limites (distância definida acima por ' tratar a proximidade média '. Use 0 para ocultar o identificador por padrão)
* **Escala média**: o valor de escala do ativo de identificador quando as mãos estão dentro do intervalo da interação de controle de limites (distância definida acima por ' manipular proximidades à próxima '. Use 1 para mostrar o tamanho normal)
* **Fechar escala**: o valor de escala do ativo de identificador quando as mãos estão dentro do intervalo da interação de captura (distância definida acima por ' manipular proximidades à próxima '. Use 1. x para mostrar um tamanho maior)
* **Taxa de crescimento distante**: Classifique uma escala de objetos dimensionados de proximidade quando a mão passa de uma distância média para a extrema.
* **Taxa de crescimento médio**: Classifique uma escala de objetos dimensionados de proximidade quando a mão passa de uma proximidade para a próxima.
* **Fechar taxa de crescimento**: taxa um objeto escalado de proximidade é dimensionado quando a mão passa do próximo proximidade para a central de objetos.

## <a name="constraint-system"></a>Sistema de restrição

O controle de limites dá suporte ao uso do [Gerenciador de restrição](constraint-manager.md) para limitar ou modificar o comportamento de conversão, rotação ou dimensionamento ao usar identificadores de controle de limites.

O Inspetor de propriedades mostrará todos os gerenciadores de restrição disponíveis anexados ao mesmo objeto de jogo em uma lista suspensa com uma opção para rolar e realçar o Gerenciador de restrição selecionado.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>Eventos

O controle de limites fornece os seguintes eventos. Este exemplo usa esses eventos para reproduzir comentários de áudio.

* **Rotação iniciada**: acionada quando a rotação é iniciada.
* **Rotação interrompida**: acionada quando a rotação para.
* **Escala iniciada**: acionada quando o dimensionamento é iniciado.
* **Escala interrompida**: acionada quando o dimensionamento é interrompido.
* **Conversão iniciada**: dispara quando a tradução é iniciada.
* **Traduzir parado**: é acionado quando a tradução para.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Elásticos (experimental)

Os elásticos podem ser usados ao manipular objetos por meio de controle de limites. Observe que o [sistema elásticos](../experimental/elastic-system.md) ainda está em estado experimental. Para habilitar os elásticos, vincule um componente do Gerenciador de elásticos existente ou crie e vincule um novo Gerenciador de elásticos por meio do `Add Elastics Manager` botão.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>Estilos de identificador

por padrão, quando você apenas atribui o [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, ele mostrará o identificador do estilo de HoloLens 1ª gen. para usar os identificadores de estilo HoloLens 2, você precisa atribuir o identificador adequado pré-fabricados e materiais.

![Estilos de alça de controle de limites 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

abaixo estão os valores de pré-fabricados, materiais e dimensionamento para os identificadores de controle de limites de estilo HoloLens 2. Você pode encontrar este exemplo na `BoundsControlExamples` cena.

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

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

## <a name="transformation-changes-with-object-manipulator"></a>Alterações de transformação com o objeto manipulador

Um controle de limites pode ser usado em combinação com [`ObjectManipulator.cs`](object-manipulator.md) para permitir certos tipos de manipulação (por exemplo, movendo o objeto) sem usar identificadores. O manipulador de manipulação dá suporte a interações de uma e de duas mãos. O [rastreamento manual](../input/hand-tracking.md) pode ser usado para interagir com um objeto de perto.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

Para que as bordas de controle de limites se comportem da mesma maneira ao movê-lo usando a [`ObjectManipulator`](object-manipulator.md) interação de longe, é aconselhável conectar seus eventos para a *manipulação iniciada*  /  *na manipulação encerrada* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` , conforme mostrado na captura de tela acima.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Como adicionar e configurar um controle de limites usando o Inspetor do Unity

1. Adicionar Colisor de caixa a um objeto
2. Atribuir `BoundsControl` script a um objeto
3. Configurar opções, como métodos de ' ativação ' (consulte a seção [Propriedades do Inspetor](#inspector-properties) abaixo)
4. Adicional atribuir pré-fabricados e materiais para um controle de limites de estilo de HoloLens 2 (consulte a seção de [estilos de identificador](#handle-styles) abaixo)

> [!NOTE]
> Use o *objeto de destino* e o campo de substituição de *limites* no Inspetor para atribuir um objeto específico e um colisor no objeto com vários componentes filho.

![Controle de limites](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>Como adicionar e configurar um controle de limites no código

1. Criar instância de gameobject do cubo

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Atribuir `BoundsControl` script a um objeto com o colisor, usando o addComponent<> ()

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. Configure as opções diretamente no controle ou por meio de uma das configurações programáveis (consulte a seção Propriedades e [configurações](#configuration-objects) do [Inspetor](#inspector-properties) abaixo)

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. Adicional atribua pré-fabricados e materiais para um controle de limites de estilo de HoloLens 2. Isso ainda requer atribuições por meio do Inspetor, pois os materiais e pré-fabricados devem ser carregados dinamicamente.

> [!NOTE]
> O uso da pasta ' recursos ' ou do [sombreador]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) do Unity. não é recomendável localizar sombreadores dinamicamente, pois as permutações do sombreador podem estar ausentes no tempo de execução.

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>Exemplo: definir a escala de controle de limites mínimos máximos usando MinMaxScaleConstraint

Para definir a escala mínima e máxima, anexe uma [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) ao seu controle. Como o controle limites anexa automaticamente e ativa o Gerenciador de restrição, o MinMaxScaleConstraint será aplicado automaticamente à transformação é alterada quando ela é anexada e configurada.

Você também pode usar MinMaxScaleConstraint para definir a escala mínima e máxima para [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>Exemplo: Adicionar controle de limites em um objeto Game

Para adicionar um controle de limites em um objeto, basta adicionar um `BoundsControl` componente a ele:

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>Migrando da caixa delimitadora

Pré-fabricados e instâncias existentes usando a [caixa delimitadora](bounding-box.md) podem ser atualizados para o novo controle de limites por meio da [janela de migração](../tools/migration-window.md) que faz parte do pacote de ferramentas do MRTK.

Para atualizar instâncias individuais da caixa delimitadora também há uma opção de migração dentro do Inspetor de propriedades do componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>Confira também

* [Manipulador de objeto](object-manipulator.md)
* [Gerenciador de restrição](constraint-manager.md)
* [Janela de migração](../tools/migration-window.md)
* [Sistema elásticos (experimental)](../experimental/elastic-system.md)
