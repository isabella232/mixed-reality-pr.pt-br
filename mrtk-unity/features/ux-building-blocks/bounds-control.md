---
title: Controle de limites
description: Visão geral sobre o controle de limites no MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, controle de limites,
ms.openlocfilehash: 3abefd142753c34c9126d71cde77ebca0b40f1f9b7a81b5815777b9e938e172a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217162"
---
# <a name="bounds-control"></a>Controle de limites

![Controle de limites](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl* é o novo componente para o comportamento de manipulação, encontrado anteriormente em *BoundingBox*. O controle de limites faz uma série de aprimoramentos e simplificações na instalação e adiciona novos recursos. Esse componente é uma substituição para a caixa delimitadora, que será preterida.

O [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fornece a funcionalidade básica para transformar objetos em realidade misturada. Um controle de limites mostrará uma caixa ao contrário do holograma para indicar que ele pode ser interagindo. As alças nos cantos e nas bordas da caixa permitem dimensionar, girar ou traduzir o objeto. O controle de limites também reage à entrada do usuário. no HoloLens 2, por exemplo, o controle de limites responde à proximidade do dedo, fornecendo comentários visuais para ajudar a perceber a distância do objeto. Todas as interações e visuais podem ser facilmente personalizados.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos de configurações de controle de limites na `BoundsControlExamples` cena.

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Propriedades do Inspetor

### <a name="target-object"></a>Objeto de destino

Esta propriedade especifica qual objeto será transformado pela manipulação de controle de limites. Se nenhum objeto for definido, o padrão será o objeto do proprietário.

### <a name="activation-behavior"></a>Comportamento de ativação

Há várias opções para ativar a interface de controle de limites.

* *Ativar ao iniciar*: o controle de limites se torna visível depois que a cena é iniciada.
* *Ativar por proximidade*: o controle de limites se torna visível quando uma mão articulada está perto do objeto.
* *Ativar por ponteiro*: o controle de limites se torna visível quando é direcionado por um ponteiro de raio à mão.
* *Ativar por proximidade e ponteiro*: o controle de limites se torna visível quando é direcionado por um ponteiro de raio à mão ou uma mão articulada é próxima ao objeto.
* *Ativar manualmente*: o controle de limites não se torna visível automaticamente. Você pode ativá-lo manualmente por meio de um script acessando a propriedade boundsControl. Active.

### <a name="bounds-override"></a>Substituição de limites

Define um colisor de caixa do objeto para computação de limites.

### <a name="box-padding"></a>Preenchimento de caixa

Adiciona um preenchimento aos limites do colisor usados para calcular as extensões do controle. Isso influenciará não apenas a interação, mas também afetará os visuais.

### <a name="flatten-axis"></a>Nivelar eixo

Indica se o controle é achatado em um dos eixos, tornando-o bidimensional e desautorizando a manipulação ao longo desse eixo. Esse recurso pode ser usado para objetos finos como slates.
Se o eixo achatado estiver definido como *automático achatado* , o script selecionará automaticamente o eixo com a menor extensão que o eixo achatado.

### <a name="smoothing"></a>Suavização

A seção suavização permite configurar o comportamento de suavização para dimensionar e girar o controle.

### <a name="visuals"></a>Visuais

A aparência do controle de limites pode ser configurada modificando uma das configurações visuais correspondentes.
As configurações visuais são objetos vinculados ou embutidos em script e são descritos mais detalhadamente na [seção objeto de configuração](#configuration-objects).

## <a name="configuration-objects"></a>Objetos de configuração

O controle vem com um conjunto de objetos de configuração que podem ser armazenados como objetos programáveis e compartilhados entre diferentes instâncias ou pré-fabricados. As configurações podem ser compartilhadas e vinculadas como arquivos de ativo programáveis por script ou ativos de script aninhados individuais dentro do pré-fabricados. Configurações adicionais também podem ser definidas diretamente na instância sem vínculo com um ativo com script aninhado ou externo.

O Inspetor de controle de limites indicará se uma configuração é compartilhada ou embutida como parte da instância atual, mostrando uma mensagem no Inspetor de propriedades. Além disso, as instâncias compartilhadas não serão editáveis diretamente na própria janela de propriedades de controle de limites, mas o ativo ao qual está vinculando precisará ser diretamente modificado para evitar alterações acidentais em configurações compartilhadas.

Atualmente, o controle de limites oferece opções de objetos de configuração para os seguintes recursos:

* Alças
  * [Alças de escala](#scale-handles-configuration)
  * [Alças de rotação](#rotation-handles-configuration)
  * [Identificadores de tradução](#translation-handles-configuration)
* [Links/wireframe](#links-configuration-wireframe)
* [Exibição da caixa](#box-configuration)
* [Efeito de proximidade](#proximity-effect-configuration)

### <a name="box-configuration"></a>Configuração de caixa

A configuração Box é responsável por renderizar uma caixa sólida com limites definidos por meio do tamanho do colisor e do preenchimento da caixa. As propriedades a seguir podem ser configuradas:

* **Material da caixa**: define o material aplicado à caixa renderizada quando nenhuma interação ocorre. Uma caixa só será renderizada se esse material estiver definido.
* **Material capturado de caixa**: material para a caixa quando o usuário interage com o controle, pegando por meio de interação próxima ou extrema.
* **Escala de exibição do eixo achatado**: uma escala aplicada à caixa é exibida se um dos eixos é [achatado](#flatten-axis).

### <a name="scale-handles-configuration"></a>Configuração de alças de escala

Essa gaveta de propriedade permite modificar o comportamento e a visualização de alças de escala do controle de limites.

* **Material de manuseio**: material aplicado às alças.
* **Tratar material capturado**: material aplicado ao identificador capturado.
* **Tratar pré-fabricado**: pré-fabricado opcional para a alça de dimensionamento. Se não for definido, MRTK usará um cubo como padrão.
* **Tamanho do identificador**: tamanho da alça de escala.
* **Preenchimento do colisor**: preenchimento a ser adicionado ao colisor do identificador.
* **Desenhar o compartilhamento de Internet ao manipular**: quando ativo, você desenhará uma linha de compartilhamento de Internet a partir do ponto de início da interação com a posição atual ou do ponteiro.
* Os **identificadores ignoram o colisor**: se um colisor estiver vinculado aqui, os identificadores ignorarão qualquer colisão com esse colisor.
* **Tratar pré-fabricado Slate**: pré-fabricado a ser usado para o identificador quando o controle for nivelado.
* **Mostrar alças de escala**: controla a visibilidade do identificador.
* **Comportamento de escala**: pode ser definido como dimensionamento uniforme ou não uniforme.

### <a name="rotation-handles-configuration"></a>Configuração de identificadores de rotação

Essa configuração define o comportamento do identificador de rotação.

* **Material de manuseio**: material aplicado às alças.
* **Tratar material capturado**: material aplicado ao identificador capturado.
* **Tratar pré-fabricado**: pré-fabricado opcional para o identificador. Se não for definido, MRTK usará uma esfera como padrão.
* **Tamanho do identificador**: tamanho do identificador.
* **Preenchimento do colisor**: preenchimento a ser adicionado ao colisor do identificador.
* **Desenhar o compartilhamento de Internet ao manipular**: quando ativo, você desenhará uma linha de compartilhamento de Internet a partir do ponto de início da interação com a posição atual ou do ponteiro.
* Os **identificadores ignoram o colisor**: se um colisor estiver vinculado aqui, os identificadores ignorarão qualquer colisão com esse colisor.
* **Manipular tipo de colisor pré-fabricado**: tipo de colisor a ser usado com o identificador criado.
* **Mostrar identificador de x**: controla a visibilidade do identificador para o eixo x.
* **Mostrar identificador para y**: controla a visibilidade do identificador para o eixo y.
* **Mostrar identificador para Z**: controla a visibilidade do identificador para o eixo Z.

### <a name="translation-handles-configuration"></a>Configuração de identificadores de tradução

Permite habilitar e configurar identificadores de tradução para controle de limites. Observe que os identificadores de tradução são desabilitados por padrão.

* **Material de manuseio**: material aplicado às alças.
* **Tratar material capturado**: material aplicado ao identificador capturado.
* **Tratar pré-fabricado**: pré-fabricado opcional para o identificador. Se não for definido, MRTK usará uma esfera como padrão.
* **Tamanho do identificador**: tamanho do identificador.
* **Preenchimento do colisor**: preenchimento a ser adicionado ao colisor do identificador.
* **Desenhar o compartilhamento de Internet ao manipular**: quando ativo, você desenhará uma linha de compartilhamento de Internet a partir do ponto de início da interação com a posição atual ou do ponteiro.
* **Alças ignoram colisor:** se um colisor for vinculado aqui, os alças ignorarão qualquer colisão com esse colisor.
* **Manipular o tipo de colisor de pré-fab**: tipo de colisor a ser usado com o identificador criado.
* **Mostrar o handle para X:** controla a visibilidade do alça para o eixo X.
* **Mostrar o handle para Y:** controla a visibilidade do alça para o eixo Y.
* **Mostrar o handle para Z:** controla a visibilidade do alça para o eixo Z.

### <a name="links-configuration-wireframe"></a>Configuração de links (wireframe)

A configuração de links habilita o recurso wireframe do controle de limites. As propriedades a seguir podem ser configuradas:

* **Material de wireframe:** o material aplicado à malha wireframe.
* **Raio de borda do wireframe:** a espessura do wireframe.
* **Forma de wireframe:** a forma do wireframe pode ser cúbica ou cilíndrica.
* **Mostrar wireframe:** controla a visibilidade do wireframe.

### <a name="proximity-effect-configuration"></a>Configuração do efeito de proximidade

Mostrar e ocultar os alças com animação com base na distância até as mãos. Ele tem animação de dimensionamento em duas etapas. Os padrões são definidos como HoloLens de estilo 2.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **Efeito de proximidade ativo:** habilitar a ativação de alça baseada em proximidade
* **Proximidade média do objeto:** distância para o dimensionamento da primeira etapa
* **Proximidade de fechamento do objeto:** distância para o dimensionamento da segunda etapa
* **Escala distante:** valor de escala padrão do ativo de alça quando as mãos estão fora do intervalo da interação de controle de limites (distância definida acima por "Tratar proximidade média". Usar 0 para ocultar o handle por padrão)
* **Escala média:** valor de escala do ativo de alça quando as mãos estão dentro do intervalo da interação de controle de limites (distância definida acima por "Lidar com proximidade próxima". Use 1 para mostrar o tamanho normal)
* **Escala de Fechamento:** valor de escala do ativo de alça quando as mãos estão dentro do intervalo da interação de captura (distância definida acima por "Lidar com proximidade próxima". Usar 1.x para mostrar um tamanho maior)
* **Taxa de crescimento distante:** a taxa de um objeto dimensionado por proximidade é dimensionada quando a mão se move de proximidade média para distante.
* **Taxa média de crescimento:** a taxa de um objeto dimensionado por proximidade é dimensionada quando a mão se move da média para a proximidade próxima.
* **Fechar Taxa de Crescimento:** a taxa de um objeto dimensionado por proximidade é dimensionada quando a mão se move da proximidade ao centro do objeto.

## <a name="constraint-system"></a>Sistema de restrição

O controle bounds dá suporte ao [uso](constraint-manager.md) do gerenciador de restrições para limitar ou modificar o comportamento de conversão, rotação ou dimensionamento ao usar alças de controle de limites.

O inspetor de propriedade mostrará todos os gerenciadores de restrição disponíveis anexados ao mesmo objeto de jogo em uma lista suspenso com a opção de rolar e realçar o gerenciador de restrições selecionado.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>Eventos

O controle bounds fornece os seguintes eventos. Este exemplo usa esses eventos para reproduzir comentários de áudio.

* **Rotação Iniciada:** acionado quando a rotação é iniciada.
* **Girar Parado:** acionado quando a rotação é interrompida.
* **Escala iniciada:** é a incêndio quando o dimensionamento é iniciado.
* **Escala interrompida:** é a incêndio quando o dimensionamento é interrompido.
* **Translate Started:** acionará quando a conversão for iniciada.
* **Translate Stopped:** acionará quando a conversão for interrompida.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Elástico (experimental)

Os elásticos podem ser usados ao manipular objetos por meio do controle de limites. Observe que o [sistema elástico ainda](../experimental/elastic-system.md) está em estado experimental. Para habilitar o elástico, vincule um componente existente do Elastics Manager ou crie e vincule um novo gerenciador de elásticos por meio do `Add Elastics Manager` botão.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>Manipular estilos

Por padrão, quando você apenas atribuir o script, ele mostrará o handle do estilo [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) HoloLens 1ª geração. Para usar HoloLens 2 alças de estilo, você precisa atribuir pré-fabs e materiais de alça adequados.

![Estilos de alça de controle de limites 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

Abaixo estão os pré-fabs, os materiais e os valores de dimensionamento para os HoloLens de controle de limites de estilo 2. Você pode encontrar este exemplo na `BoundsControlExamples` cena.

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

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

## <a name="transformation-changes-with-object-manipulator"></a>Alterações de transformação com o manipulador de objetos

Um controle de limites pode ser usado em combinação com [`ObjectManipulator.cs`](object-manipulator.md) para permitir determinados tipos de manipulação (por exemplo, movendo o objeto ) sem usar identificador. O manipulador de manipulação dá suporte a interações de uma e duas mãos. [O acompanhamento](../input/hand-tracking.md) de mão pode ser usado para interagir com um objeto de perto.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

Para que as bordas de controle de limites se comportem da mesma maneira ao movimentação usando a interação distante de , é aconselhável conectar seus eventos para On Manipulation Started On Manipulation Ended to respectivamente, conforme mostrado na captura de tela [`ObjectManipulator`](object-manipulator.md)   /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` acima.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Como adicionar e configurar um controle de limites usando o Inspetor do Unity

1. Adicionar Colisor de Caixa a um objeto
2. Atribuir `BoundsControl` script a um objeto
3. Configurar opções, como métodos de 'Ativação' (consulte [a seção Propriedades do](#inspector-properties) inspetor abaixo)
4. (Opcional) Atribuir pré-fabs e materiais para um controle HoloLens limites de estilo 2 (consulte a seção Manipular [estilos](#handle-styles) abaixo)

> [!NOTE]
> Use *o campo Objeto de* Destino e Substituição de Limites no inspetor para atribuir um objeto e *colisor* específicos no objeto com vários componentes filho.

![Controle de limites](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>Como adicionar e configurar um controle de limites no código

1. Insinuar gameObject de cubo

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Atribuir `BoundsControl` script a um objeto com colisor usando AddComponent<>()

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. Configure opções diretamente no controle ou por meio de uma das configurações de script (consulte a seção [Propriedades e](#inspector-properties) [configurações](#configuration-objects) do inspetor abaixo)

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. (Opcional) Atribua pré-requisitos e materiais para um HoloLens controle de limites de estilo 2. Isso ainda requer atribuições por meio do inspetor, pois os materiais e os pré-requisitos devem ser carregados dinamicamente.

> [!NOTE]
> Não é recomendável usar a pasta 'Recursos' do Unity ou o [Sombreador.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) para carregar dinamicamente sombreadores, pois as permutações do sombreador podem estar ausentes em runtime.

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>Exemplo: definir a escala de controle de limites mínimo e máximo usando MinMaxScaleConstraint

Para definir a escala mínima e máxima, anexe um [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) ao seu controle. À medida que o controle de limites anexar e ativar automaticamente o gerenciador de restrições, MinMaxScaleConstraint será aplicado automaticamente às alterações de transformação depois que ele for anexado e configurado.

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

## <a name="example-add-bounds-control-around-a-game-object"></a>Exemplo: Adicionar controle de limites em torno de um objeto de jogo

Para adicionar um controle de limites em torno de um objeto, basta adicionar um `BoundsControl` componente a ele:

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>Migrando da caixa delimitada

Os pré-requisitos e [](bounding-box.md) instâncias existentes que usam a caixa delimitatória podem ser atualizados para o novo controle de limites por meio da janela de migração, que faz parte do pacote de ferramentas do MRTK. [](../tools/migration-window.md)

Para atualizar instâncias individuais da caixa delimitador, também há uma opção de migração dentro do inspetor de propriedade do componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>Confira também

* [Manipulador de objetos](object-manipulator.md)
* [Gerenciador de restrição](constraint-manager.md)
* [Janela de migração](../tools/migration-window.md)
* [Sistema elástico (Experimental)](../experimental/elastic-system.md)
