---
title: Orientador de mão
description: descrição e exemplos para o técnico de mão.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 3e5a56f7498288e79963acea6fca223421fee2607004a9a2bae639f81441e0d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209016"
---
# <a name="hand-coach"></a>Orientador de mão

![Hand Coach Menu](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

O técnico de mão é uma mão modelada em 3D que é disparada quando o sistema não detecta as mãos do usuário. Isso é implementado como um componente de "ensino" que ajuda a orientar o usuário quando o gesto não foi ministrado. Se os usuários não fizeram o gesto especificado por um período, as mãos terão um loop com um atraso. O técnico de mão pode ser usado para representar pressionar um botão ou escolher um holograma.

O modelo de interação atual representa uma ampla variedade de controles de gesto, como rolagem, seleção distante e toque próximo. Abaixo está uma lista completa de exemplos de técnico de mão existentes:

- Toque próximo – usado para botões ou fechar objetos interagidos
- Seleção distante – usada para objetos que estão longe
- Mover – usado para mover um holograma no espaço
- Girar – usado para mostrar como girar hologramas ou objetos
- Escala – usado para mostrar como manipular hologramas para serem maiores ou menores
- Hand flip – usado para abrir um painel inicial da interface do usuário ou menus de mão
- Palm up – usado para a experiência de momento do cadamingbird in-the-box. Outra sugestão pode ser abrir um painel de início da interface do usuário
- Rolagem – usada para rolar uma lista ou um documento longo

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos na cena **HandCoachExample** em: [MixedRealityToolkit.Examples/Experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>Ativos 3D de mão

Você pode encontrar os ativos em: [MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Qualidade

Se você observar distorções na malha ressalvada, precisará certificar-se de que seu projeto está usando a quantidade adequada de junções.
Vá para Editar > Project Configurações > Qualidade > outros > Blend Weights. Certifique-se de que "4 animais" estão selecionados para ver Smooth Joints.
![Project Configuração](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>Scripts

### <a name="interaction-hint"></a>Dica de interação

O `InteractionHint.cs` script fornece funcionalidade de wrapper para disparar animações e esmaecer para o equipamento de mão.

#### <a name="how-to-set-up-an-interaction-hint"></a>Como configurar uma dica de interação

Para configurar uma dica de interação, é recomendável usar os pré-fabs fornecidos "StaticHandCoachRoot_L.prefab" e "StaticHandCoachRoot_R.prefab". Esse pré-fab contém o script InteractionHint e o equipamento de mão, bem como a hierarquia adequada para garantir que as animações de dica fornecidas funcionem conforme o esperado.
Caso contrário, você precisará colocar o script em um gameObject um nível pai acima do seu equipamento de mão com animador.

#### <a name="inspector-properties"></a>Propriedades do inspetor

- **HideIfHandTracked** Esse booliana especifica se o estado de acompanhamento de mão deve ser usado para ocultar visuais quando as mãos de um usuário estão sendo rastreadas. Se isso for definido como false, somente a propriedade de script "customShouldHideVisuals" será usada para determinar se a dica deve ser ocultada.

- **MinDelay** Essa propriedade especifica o atraso mínimo para mostrar os visuais. Por padrão, os visuais da mão serão exibidos após esse número de segundos se as mãos do usuário não estão sendo rastreadas.

- **MaxDelay** Essa propriedade especifica o atraso máximo para mostrar os visuais. Por padrão, os visuais da mão serão exibidos após esse número de segundos, mesmo que as mãos do usuário sejam rastreadas.

- **UseMaxTimer** Se esse booliana for definido como false, ele desabilitará o temporizador máximo e só permitirá que a dica de mão seja mostrada quando as mãos do usuário estão fora de exibição ou a condição personalizada retornará false.

- **Repetições** Essa propriedade controla quantas vezes a animação de dica é reproduzida quando o temporizador mínimo ou máximo foi passado. Em seguida, a dica oculta e aguarda o atraso novamente.

- **AutoActivate** Quando esse booliana for definido como true, a dica será automaticamente executado pela lógica do temporizador quando o GameObject do script estiver ativo na hierarquia e o script estiver habilitado. Isso só deverá ser definido como false se você pretende controlar manualmente a aparência da dica e o mal-estar por meio do código.

- **AnimationState** O nome do estado de animação que deve ser reproduzir quando a dica estiver ativa. Isso deve ser definido antes que a função StartHintLoop() seja chamada (durante OnEnable se AutoActivate estiver marcada).

#### <a name="controlling-interactionhint-via-script"></a>Controlando InteractionHint por meio de script

- **StartHintLoop** Essa função iniciará o loop show/hide que, caso contrário, iniciará OnEnable se o sinalizador AutoActivate estiver definido como true.
- **StopHintLoop** Essa função chamará o estado de animação de esmaeçando se ele não estiver em reprodução no momento, desativará o loop show/hide e definirá o equipamento de mão inativo na hierarquia.
- **AnimationState** Essa cadeia de caracteres determina qual estado de animação é tocada durante o loop. Você pode alterar essa cadeia de caracteres para alterar qual estado é reproduzindo, mas você deve fazer isso depois de chamar StopHintLoop e chamar StartHintLoop novamente depois de alterar o estado.
- **CustomShouldHideVisuals** Você pode definir isso com sua própria função, que deve retornar true quando quiser ocultar os visuais da mão (tenha em mente o MinMaxTimer, especificamente o parâmetro max)

#### <a name="custom-animation-considerations"></a>Considerações sobre animação personalizada

Os esmaeçamentos têm o padrão de 0,5 segundos, portanto, todas as animações personalizadas criadas para uso com o equipamento devem ser, no mínimo, 1,5 segundos para que qualquer informação significativa seja transmitida

Os estados padrão fornecidos esmaecem e esmaecem, Fade_In e Fade_Out podem ser ajustados alterando o timestamp do segundo keyframe para definir o comprimento do esmaeçamento.

O animador e o script foram configurados de uma maneira que deve tornar a instalação o mais simples possível. Para adicionar novos estados de animação, basta importar seu fbx, garantir que o nome da animação seja definido com um nome distinto e arraste essa animação para o animador.

### <a name="movetotarget"></a>MoveToTarget

O script MoveToTarget.cs fornece funcionalidade para mover a dica de mão de uma posição de acompanhamento para uma posição de destino ao longo do tempo.

#### <a name="how-to-set-up-movetotarget"></a>Como configurar o MoveToTarget

Os pré-fabs "MovingHandCoachRoot_L.prefab" e "MovingHandCoachRoot_R.prefab" fornecidos contêm um MoveToTarget em suas hierarquias. Se você quiser usar esse script em sua própria configuração, será necessário coloque-o no gameobject raiz que contém o Animator para o seu equipamento.

#### <a name="inspector-properties"></a>Propriedades do inspetor

- **TrackingObject** De definido com o objeto que você deseja que o equipamento siga antes de iniciar seu movimento. É recomendável criar um GameObject vazio e movê-lo para uma posição específica para ajudá-lo a identificar o rastreamento.
- **TargetObject** De definir isso com o objeto para o que você deseja que o equipamento se mova durante seu movimento. É recomendável criar um GameObject vazio e movê-lo para uma posição específica para ajudá-lo a identificar o rastreamento.
- **RootObject** De definido como um pai compartilhado entre o controle e o objeto de destino para que as posições relativas possam ser calculadas corretamente. O pré-fab incluído tem objetos de acompanhamento e de destino em sua hierarquia, mas você pode definir o objeto de destino como um gameObject fora do pré-fab e alterar o objeto raiz para um pai compartilhado.
- **Duração** A quantidade de tempo que deve levar (em segundos) para passar de TrackingObject para TargetObject em segundos.
- **TargetOffset** Um deslocamento acessível para fazer com que o GameObject chegue à posição de destino correta. Isso será útil se a animação incluir um deslocamento de posição durante a animação.
- **AnimationCurve** Isso é padrão para uma curva linear, mas você pode alterar a curva para fornecer easing in/out ao iniciar e parar o caminho de movimento.

#### <a name="controlling-movetotarget-via-script"></a>Controlando o MoveToTarget por meio de script

Em seu script personalizado, faça uma chamada para Follow() enquanto você deseja que o equipamento de mão siga o TrackingObject e, em seguida, faça uma chamada para MoveToTargetPosition() quando quiser que o equipamento de mão inicie seu movimento para o TargetObject.

#### <a name="controlling-movetotarget-via-animations"></a>Controlando MoveToTarget por meio de animações

Na animação que precisa ser movimentada, de definir dois eventos: um com uma chamada para Follow() e outro com uma chamada para MoveToTargetPosition(). Siga o conjunto de chaves no primeiro keyframe, pois ele faz com que o equipamento de mão siga seu TrackingObject. MoveToTargetPosition deve ser definido no keyframe em que você deseja que o equipamento comece a mover para o destino. É assim que a funcionalidade de script é usada nos pré-requisitos fornecidos.

### <a name="rotatearoundpoint"></a>RotateAroundPoint

O script RotateAroundPoint.cs fornece funcionalidade para girar a dica de mão em torno de um ponto pivô ao longo do tempo.

#### <a name="how-to-set-up-rotatearoundpoint"></a>Como configurar o RotateAroundPoint

Os pré-fabs "RotatingHandCoachRoot_L.prefab" e "RotatingHandCoachRoot_R.prefab" fornecidos contêm um RotateAroundPoint em suas hierarquias. Se você quiser usar esse script em sua própria configuração, será necessário coloque-o no gameobject raiz que contém o Animator para o seu equipamento.

#### <a name="inspector-properties"></a>Propriedades do inspetor

- **CenteredParent** De definir isso com o objeto pai que você deseja que o equipamento gire.
- **InverseParent** Depare isso com o pai para girar o inverso para centeredParent para manter a orientação da mão da mesma maneira. Em geral, esse será o objeto pai com o script InteractionHint nele.
- **PivotPosition** De definido como um ponto em que você deseja que a dica inicie a movimentação.
- **Duração** A quantidade de tempo que deve levar (em segundos) para girar em torno do CenteredParent.
- **AnimationCurve** Isso é padrão para uma curva linear, mas você pode alterar a curva para fornecer easing in/out ao iniciar e parar o caminho de movimento.
- **RotationVector** Quantos graus girar ao longo de cada eixo.

#### <a name="controlling-rotatearoundpoint-via-script"></a>Controlando RotateAroundPoint por meio de script

No script personalizado, faça uma chamada para RotateToTarget() quando quiser que o equipamento de mão inicie sua rotação em torno do CenteredParent. Quando você quiser que a posição seja redefinida para o PivotPosition original, faça uma chamada para ResetAndDeterminePivot().

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Controlando RotateAroundPoint por meio de animações

Na animação que precisa ser movimentada, defina dois eventos: um com uma chamada para ResetAndDeterminePivot() e outro com uma chamada para RotateToTarget(). ResetAndDeterminePivot deve ser definido no primeiro keyframe, pois faz com que o equipamento de mão seja redefinido para o PivotPosition. RotateToTarget deve ser definido no keyframe em que você deseja que o equipamento comece a girar em torno do CenteredParent. É assim que a funcionalidade de script é usada nos pré-requisitos fornecidos.
