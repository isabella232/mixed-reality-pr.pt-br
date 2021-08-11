---
title: Botões
description: Visão geral sobre os botões em MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, botões de MRTK
ms.openlocfilehash: 7d1c141981ec402d85e1e2004739e9ab9f0ebe9da5361e4e3100b43a2b5b4129
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228860"
---
# <a name="buttons"></a>Botões

![Botão principal](../images/button/MRTK_Button_Main.png)

Um botão dá ao usuário uma forma de acionar uma ação imediata. É um dos componentes mais fundamentais da realidade misturada. O MRTK fornece vários tipos de pré-fabricados de botão.

## <a name="button-prefabs-in-mrtk"></a>Botão pré-fabricados em MRTK

Exemplos do botão pré-fabricados na ``MRTK/SDK/Features/UX/Interactable/Prefabs`` pasta

### <a name="unity-ui-imagegraphic-based-buttons"></a>Imagem da interface do usuário do Unity/botões baseados em gráficos

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Botões baseados em Colisor

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    botão de estilo de shell de HoloLens 2 com placa de frente que dá suporte a vários comentários visuais, como luz de borda, luz de proximidade e placa frontal compactada
    :::column-end:::
    :::column:::
    botão de estilo de shell do HoloLens 2 sem placa traseira
    :::column-end:::
    :::column:::
    botão estilo de shell de HoloLens 2 com forma circular
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    botão de estilo de shell de larga HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    barra de botões Horizontal HoloLens 2 com placa traseira compartilhada
    :::column-end:::
    :::column:::
    barra de botões Vertical HoloLens 2 com placa traseira compartilhada
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    caixa de seleção estilo de shell do HoloLens 2 32x32mm
    :::column-end:::
    :::column:::
    opção de estilo de shell do HoloLens 2 32x32mm 
    :::column-end:::
    :::column:::
    32x32mm de rádio em estilo de shell 2 do HoloLens
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    caixa de seleção estilo de shell do HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    opção de estilo de shell do HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    32x96mm de rádio em estilo de shell 2 do HoloLens
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![](../images/button/MRTK_Button_Radial.png) **Radial** radial
    :::column-end:::
    :::column:::
    ![Caixa de seleção CheckBox ](../images/button/MRTK_Button_Checkbox.png) 
    :::column-end:::
    :::column:::
    ![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Botão radial 
    :::column-end:::
    :::column:::
    Caixa de seleção 
    :::column-end:::
    :::column:::
    Switch de alternância
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**
    :::column-end:::
    :::column:::
    ![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton** 
    :::column-end:::
    :::column:::
    ![Botão base do botão ](../images/button/MRTK_Button_Base.png) 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    botão de estilo de shell da 1ª gen HoloLens
    :::column-end:::
    :::column:::
    Botão de ação de forma arredondada
    :::column-end:::
    :::column:::
    Botão básico
    :::column-end:::
:::row-end:::

O `Button` (assets/MRTK/SDK/Features/UX/interagible/pré-fabricados/Button. pré-fabricado) baseia-se no conceito [interagindo](interactable.md) para fornecer controles de interface do usuário fáceis para botões ou outros tipos de superfícies interativas. O botão linha de base dá suporte a todos os métodos de entrada disponíveis, incluindo a entrada de mão articulada para as interações de near, bem como olhar + Air-TAP para as interações distantes. Você também pode usar o comando de voz para disparar o botão.

`PressableButtonHoloLens2`(assets/MRTK/SDK/Features/UX/interajaable/pré-fabricados/PressableButtonHoloLens2. pré-fabricado) é HoloLens botão de estilo de shell 2 que dá suporte à movimentação precisa do botão para a entrada de rastreamento direto. Ele combina `Interactable` script com `PressableButton` script.

para HoloLens 2, é recomendável usar botões com uma chapa traseira opaca. Botões transparentes não são recomendados devido a esses problemas de usabilidade e estabilidade:

* O ícone e o texto são difíceis de ler com o ambiente físico
* É difícil entender quando o evento é disparado
* Hologramas que são exibidos por meio de um plano transparente podem ser instáveis com estabilização LSR de profundidade HoloLens 2

![Botão folheado](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Como usar botões prensais

### <a name="unity-ui-based-buttons"></a>Botões baseados na interface do usuário do Unity

Crie uma tela em sua cena (gameobject-> interface do usuário > tela). No painel do inspetor para sua tela:

* Clique em "converter para tela do MRTK"
* Clique em "Adicionar NearInteractionTouchableUnityUI"
* Defina a escala X, Y e Z do componente de transformação Rect como 0, 1

Em seguida, arraste `PressableButtonUnityUI` (assets/MRTK/SDK/Features/UX/interagir/pré-fabricados/PressableButtonUnityUI. pré-fabricado), `PressableButtonUnityUICircular` (assets/MRTK/SDK/Features/UX/interajable/pré-fabricados/PressableButtonUnityUICircular. pré-fabricado) ou `PressableButtonHoloLens2UnityUI` (assets/MRTK/SDK/Features/UX/interajable/pré-fabricados/PressableButtonHoloLens2UnityUI. pré-fabricado) na tela.

### <a name="collider-based-buttons"></a>Botões baseados em Colisor

Basta arrastar `PressableButtonHoloLens2` (assets/MRTK/SDK/Features/UX/interajaable/pré-fabricados/PressableButtonHoloLens2. pré-fabricado) ou `PressableButtonHoloLens2Unplated` (assets/MRTK/SDK/Features/UX/interajable/pré-fabricados/PressableButtonHoloLens2Unplated. pré-fabricado) para a cena. Essas pré-fabricados de botão já estão configuradas para ter comentários visuais de áudio para os vários tipos de entradas, incluindo entrada de mão articulada e olhar.

Os eventos expostos no próprio pré-fabricado, bem como o componente que pode [interagir](interactable.md) , podem ser usados para disparar ações adicionais. Os botões pressionáveis na [cena HandInteractionExample](../example-scenes/hand-interaction-examples.md) usam o evento *onclick* de interagir para disparar uma alteração na cor de um cubo. Esse evento é disparado para diferentes tipos de métodos de entrada, como olhar, toque de ar, mão-raio, bem como pressionamentos de botão físico por meio do script de botão prensado.

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

Você pode configurar quando o botão pressionável aciona o evento *onclick* por meio do `PhysicalPressEventRouter` no botão. Por exemplo, você pode definir *onclick* para acionar quando o botão é pressionado pela primeira vez, em oposição a ser pressionado e liberado, definindo interagir com o *evento* de *clique* para ao pressionar.

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

Para aproveitar informações de estado de entrada articuladas específicas, você pode usar eventos de botões que podem ser prensados – *início do toque*, *fim do toque*, *botão pressionado*, *botão liberado*. No entanto, esses eventos não serão disparados em resposta às entradas do toque, do lado do ar ou do raio. **Para dar suporte a interações próximas e distantes, é recomendável usar o evento *onclick* de interagir.**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>Estados de interação

No estado ocioso, a placa frontal do botão não é visível. Como as abordagens de um dedo ou um cursor da entrada olhar tem como alvo a superfície, a borda brilhante da placa frontal torna-se visível. Há um realce adicional da posição de alcance na superfície da placa frontal. Quando enviado por push com um dedo, a placa frontal se move com a ponta. Quando o ponto atinge a superfície da placa frontal, ele mostra um efeito de pulso sutil para dar comentários visuais sobre o toque.

no botão estilo de shell HoloLens 2, há muitas indicações visuais e capacidades para aumentar a confiança do usuário na interação.

|  ![Luz de proximidade](../images/button/ux_button_affordance_proximitylight.jpg) | ![Realce de foco](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compactando o compartimento](../images/button/ux_button_affordance_compression.jpg) | ![Pulso no gatilho](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| Luz de proximidade | Realce de foco | Compactando o compartimento | Pulso no gatilho |

O efeito de pulso sutil é disparado pelo botão pressionável, que procura *ProximityLight (s)* que residem no ponteiro que está interagindo atualmente. Se alguma luz de proximidade for encontrada, o `ProximityLight.Pulse` método será chamado, que anima automaticamente os parâmetros do sombreador para exibir um pulso.

## <a name="inspector-properties"></a>Propriedades do Inspetor

![Estrutura do botão](../images/button/MRTK_Button_Structure.png)

 
 Colisor `Box Collider` de caixa para a placa frontal do botão.

**Botão pressionável** A lógica do botão de movimentação com a interação de pressionar à mão.

**Roteador de evento de prensa física** Esse script envia eventos da interação de pressionar mão para [interagir](interactable.md).

**Interagir** 
 [Interagir](interactable.md) manipula vários tipos de Estados de interação e eventos. HoloLens olhar, gesto e entrada de voz e entrada do controlador de movimento de headset de imersão são tratados diretamente por esse script.

**Fonte de áudio** Fonte de áudio do Unity para os clipes de comentários de áudio.

*NearInteractionTouchable. cs* necessário para tornar qualquer objeto tocável com entrada de mão articulada.

## <a name="prefab-layout"></a>Layout de pré-fabricado

O objeto *ButtonContent* contém a placa frontal, o rótulo de texto e o ícone. O *FrontPlate* responde à proximidade do índice usando o sombreador de *Button_Box* . Ele mostra bordas brilhantes, luz de proximidade e um efeito de pulso sobre toque. O rótulo de texto é feito com textmesh Pro. A visibilidade do *SeeItSayItLabel* é controlada pelo tema de [interação](interactable.md).

![Layout do botão](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>Como alterar o ícone e o texto

Os botões MRTK usam um `ButtonConfigHelper` componente para ajudá-lo a alterar o ícone, o texto e o rótulo do botão. (Observe que alguns campos podem estar ausentes se os elementos não estiverem presentes no botão selecionado.)

![Auxiliar de configuração de botão](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>Criando e modificando conjuntos de ícones

Um **conjunto de ícones** é um conjunto compartilhado de ativos de ícone usado pelo `ButtonConfigHelper` componente. Há suporte para três *estilos* de ícone.

* Ícones **quádruplos** são renderizados em um quad usando um `MeshRenderer` . Esse é o estilo de ícone padrão.
* Os ícones de **Sprite** são renderizados usando um `SpriteRenderer` . Isso será útil se você preferir importar os ícones como uma folha de Sprite ou se quiser que os ativos de ícone sejam compartilhados com os componentes da interface do usuário do Unity. para usar esse estilo, você precisará instalar o pacote do Editor Sprite **(Windows-> Gerenciador de Pacotes-> 2d Sprite)**
* Ícones de **caracteres** são renderizados usando um `TextMeshPro` componente. Isso será útil se você preferir usar uma fonte de ícone. para usar a fonte do ícone de HoloLens, você precisará criar um `TextMeshPro` ativo de fonte.

Para alterar o estilo que seu botão usa, expanda a lista suspensa *ícones* no ButtonConfigHelper e selecione na lista suspensa *estilo de ícone* .

você pode criar um novo ícone de botão definido com o menu ativo: **criar > realidade misturada Toolkit ícone > conjunto.** Para adicionar ícones de quatro e Sprite, basta arrastá-los para suas respectivas matrizes. Para adicionar ícones de caracteres, você deve primeiro criar e atribuir um ativo de fonte.

No MRTK 2,4 e posterior, recomendamos que as texturas do ícone personalizado sejam movidas para um ícone do.
Para atualizar os ativos em todos os botões de um projeto para o novo formato recomendado, use o ButtonConfigHelperMigrationHandler.
(Toolkit de realidade misturada-> utilitários-> janela de migração-> seleção do manipulador de migração-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)

Importando o pacote Microsoft. MixedRealityToolkit. Unity. Tools necessário para atualizar os botões.

![Caixa de diálogo atualizar janela](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Se um ícone não for encontrado no conjunto de ícones padrão durante a migração, um conjunto de ícones personalizado será criado em MixedRealityToolkit. Generated/CustomIconSets. Uma caixa de diálogo indicará que isso foi realizado.

![Notificação de ícone personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>criando um ativo de fonte de ícone de HoloLens

Primeiro, importe a fonte do ícone para o Unity. em computadores Windows, você pode encontrar a fonte de HoloLens padrão em *Windows/Fonts/holomdl2.ttf.* Copie e cole esse arquivo em sua pasta de ativos.

Em seguida, abra o criador de ativos de fonte TextMeshPro por meio da **janela > TextMeshPro > criador de ativos de fonte.** aqui estão as configurações recomendadas para gerar um HoloLens atlas de fontes. Para incluir todos os ícones, Cole o seguinte intervalo Unicode no campo de *sequência de caracteres* :

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Criação de botão 1](../images/button/MRTK_Font_Asset_Creation_1.png)

Depois que o ativo de fonte for gerado, salve-o em seu projeto e atribua-o ao campo de *fonte ícone de caractere* do conjunto de ícones. O menu suspenso *ícones disponíveis* agora será populado. Para tornar um ícone disponível para ser usado por um botão, clique nele. Ele será adicionado à lista suspensa *ícones selecionados* e agora será exibido no, `ButtonConfigHelper.` opcionalmente, você pode dar ao ícone uma marca. Isso habilita a definição do ícone em tempo de execução.

![Criação de botão 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Criação de botão 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

Para usar o conjunto de ícones, selecione um botão, expanda o menu suspenso ícones no `ButtonConfigHelper` e atribua-o ao campo *conjunto de ícones* .

![Conjunto de ícones de botão](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>Como alterar o tamanho de um botão

o tamanho do botão do estilo de shell do HoloLens 2 é 32x32mm. Para personalizar a dimensão, altere o tamanho desses objetos no botão pré-fabricado:

1. **FrontPlate**
2. **Quado** sob placa traseira
3. **Colisor de caixa** na raiz

Em seguida, clique no botão **corrigir limites** no script NearInteractionTouchable que está na raiz do botão.

Atualizar o tamanho do botão FrontPlate ![ personalização 1](../images/button/MRTK_Button_SizeCustomization1.png)

Atualizar o tamanho da personalização do ![ tamanho do botão quádruplo 2](../images/button/MRTK_Button_SizeCustomization2.png)

Atualizar a personalização do tamanho do botão conflitante de caixa ![ 3](../images/button/MRTK_Button_SizeCustomization3.png)

Clique no botão "corrigir limites" ![ personalização de tamanho 4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it"></a>Comando de voz (' see-it, digamos-it ')

**Manipulador de entrada de fala** O script de [interação](interactable.md) no botão pressionável já implementa `IMixedRealitySpeechHandler` . Uma palavra-chave de comando de voz pode ser definida aqui.

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**Perfil de entrada de fala** Além disso, você precisa registrar a palavra-chave do comando de voz no *perfil de comandos de fala* global.

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**Consulte-it, rótulo-it** o botão pressionável pré-fabricado tem um espaço reservado para Pro o rótulo do timemesh no objeto *SeeItSayItLabel* . Você pode usar esse rótulo para comunicar a palavra-chave de comando de voz para o botão para o usuário.

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>Como fazer um botão do zero

Você pode encontrar os exemplos desses botões na cena **PressableButtonExample** .

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. criando um botão pressionável com Cube (somente interação próxima)

1. Criar um cubo do Unity (gameobject > objeto 3D > cubo)
2. Adicionar `PressableButton.cs` script
3. Adicionar `NearInteractionTouchable.cs` script

No `PressableButton` painel Inspetor, atribua o objeto de cubo aos visuais do **botão de movimentação**.

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

Ao selecionar o cubo, você verá várias camadas coloridas no objeto. isso visualiza os valores de distância em **pressionar Configurações**. Usando as alças, você pode configurar quando começar a pressionar (mover o objeto) e quando disparar o evento.

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

Quando você pressiona o botão, ele será movido e gerará eventos apropriados expostos no `PressableButton.cs` script, como TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased ().

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>Solução de problemas

Se o seu botão estiver executando um pressionamento duplo, verifique se a propriedade **impor Push frontal** está ativa e se o plano de **distância de início de envio** é colocado na frente do plano de **toque próximo da interação** . O plano de **toque próximo à interação** é indicado pelo plano azul colocado na frente da origem da seta branca no gif abaixo:

![Componente de script de botão pressionável com impor propriedade de push frontal realçada](../images/button/MRTK_Button_Enforce_Push.png)

![Exemplo animado de mover a distância de envio por push na frente do plano de toque da interação próxima](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. adicionando comentários visuais ao botão do cubo básico

O sombreador standard do MRTK fornece vários recursos que facilitam a adição de comentários visuais. Crie um material e selecione sombreador `Mixed Reality Toolkit/Standard` . Ou você pode usar ou duplicar um dos materiais existentes sob o `/SDK/StandardAssets/Materials/` que usa o sombreador padrão MRTK.

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

verifique `Hover Light` e `Proximity Light` em **opções de Fluent**. Isso habilita os comentários visuais para interações de ponteiro (luz de proximidade) e ponto de flutuação distantes.

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. adicionando comentários de áudio ao botão do cubo básico

Como `PressableButton.cs` o script expõe eventos como TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased (), podemos atribuir facilmente Comentários de áudio. Basta adicionar Unity `Audio Source` ao objeto Cube e, em seguida, atribuir clipes de áudio selecionando audioname. PlayOneShot (). Você pode usar MRTK_Select_Main e MRTK_Select_Secondary clipes de áudio na `/SDK/StandardAssets/Audio/` pasta .

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. Adicionar estados visuais e manipular eventos de interação distantes

[Interajante](interactable.md) é um script que facilita a criação de um estado visual para os vários tipos de interações de entrada. Ele também lida com eventos de interação distantes. Adicione `Interactable.cs` e arraste e solte o objeto de cubo no **campo** Destino em **Perfis**. Em seguida, crie um novo Tema com um tipo **ScaleOffsetColorTheme**. Nesse tema, você pode especificar a cor do objeto para os estados de interação específicos, como **Foco** **e Pressionado.** Você também pode controlar Escala e Deslocamento. Verifique **Easing e** de definir a duração para tornar a transição visual suave.

![Selecionar tema de perfil](../images/button/mrtk_button_profiles.gif)

Você verá o objeto responder a interações distantes (raio de mão ou cursor de olhar) e próximas (mão).

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>Exemplos de botão personalizados

Na cena [HandInteractionExample](../example-scenes/hand-interaction-examples.md), consulte os exemplos de botão round e de round que estão usando `PressableButton` .

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

Cada chave de grupo tem `PressableButton` um e um script `NearInteractionTouchable` atribuídos. É importante verificar se a direção *de Encaminhamento Local* de está `NearInteractionTouchable` correta. Ele é representado por uma seta branca no editor. Certifique-se de que a seta aponta para fora da face frontal do botão:

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>Confira também

* [Interativo](interactable.md)
* [Temas visuais](visual-themes.md)
