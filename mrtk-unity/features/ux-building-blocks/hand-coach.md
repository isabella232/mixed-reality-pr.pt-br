---
title: README_HandCoach
description: Descrição e exemplos para o direito à mão.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 8b4069f25692c4058c912ccd06ae678d67882fcd
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489266"
---
# <a name="hand-coach"></a>Orientador de mão

![Menu direito do](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

A mão da direita é a mão com modelo 3D, que é disparada quando o sistema não detecta as mãos do usuário. Isso é implementado como um componente "ensinando" que ajuda a orientar o usuário quando o gesto não foi ensinado. Se os usuários não tiverem feito o gesto especificado por um período, as mãos entrarão em loop com um atraso. A mão da direita pode ser usada para representar o pressionamento de um botão ou a seleção de um holograma.

O modelo de interação atual representa uma ampla variedade de controles de gesto, como rolagem, seleção extrema e quase toque. Veja abaixo uma lista completa dos exemplos de a com do preço de mão existentes:

- Próximo toque – usado para botões ou fechar objetos que interagem
- Seleção distante – usada para objetos que estão muito distantes
- Mover – usado para mover um holograma no espaço
- Girar – usado para mostrar como girar os hologramas ou objetos
- Escala – usada para mostrar como manipular hologramas para serem maiores ou menores
- Inverter mão – usado para abrir um painel de início da interface do usuário ou menus à mão
- Palm up – usado para o Hummingbird no momento em uma experiência pronta para uso. Outra sugestão seria abrir um painel de início da interface do usuário
- Scroll – usado para rolar uma lista ou um documento longo

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos na cena **HandCoachExample** em: [MixedRealityToolkit. examples/experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>Ativos 3D de mão

Você pode encontrar os ativos em: [MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Qualidade

Se você observar distorções na malha ressalvada, precisará certificar-se de que seu projeto está usando a quantidade adequada de junções.
Vá para Editar configurações > projeto do Unity > qualidade > outros > Pesos do Blend. Certifique-se de que "4 animais" estão selecionados para ver Smooth Joints.
![Configuração do projeto](../images/hand-coach/MRTK_ProjectSettings.png)

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

- **Repetições** Essa propriedade controla quantas vezes a animação de dica é reproduzida quando o temporizador mínimo ou máximo passou. Em seguida, a dica é ocultada e aguarda o atraso novamente.

- **Ativar** automaticamente Quando esse booliano for definido como true, a dica será executada automaticamente por meio da lógica do temporizador quando o gameobject do script estiver ativo na hierarquia e o script estiver habilitado. Isso só deve ser definido como false se você pretende controlar manualmente a aparência da dica e a desapareceção por meio de código.

- **Animaçãostate** O nome do estado de animação que deve ser tocado quando a dica está ativa. Isso deve ser definido antes que a função StartHintLoop () seja chamada (durante OnEnable se AutoActivate estiver marcado).

#### <a name="controlling-interactionhint-via-script"></a>Controlando InteractionHint por meio de script

- **StartHintLoop** Essa função inicia o loop de mostrar/ocultar que, caso contrário, inicia OnEnable se o sinalizador de ativação ativa for definido como true.
- **StopHintLoop** Essa função chamará o estado de animação fade out se não estiver sendo executada no momento, desativará o loop de mostrar/ocultar e definirá o dispositivo de mão inativo na hierarquia.
- **Animaçãostate** Essa cadeia de caracteres determina qual estado de animação é tocado durante o loop. Você pode alterar essa cadeia de caracteres para alterar o estado que é reproduzido, mas deve fazer isso depois de chamar StopHintLoop, e você deve chamar StartHintLoop novamente depois de ter alterado o estado.
- **CustomShouldHideVisuals** Você pode definir isso com sua própria função, que deve retornar true quando você quiser ocultar os visuais da mão (tenha em mente o MinMaxTimer, especificamente o parâmetro Max)

#### <a name="custom-animation-considerations"></a>Considerações sobre animação personalizada

Os fade-out são padronizados para 0,5 segundos, portanto, qualquer animação personalizada criada para uso com o Rig deve ser de 1,5 segundos para que todas as informações significativas sejam transmitidas

Os Estados de fade in e fade out padrão fornecidos, Fade_In e Fade_Out podem ser ajustados alterando o carimbo de data/hora do segundo quadro-chave para definir o comprimento de esmaecimento.

O Animator e o script foram configurados de forma a tornar a instalação o mais simples possível. Para adicionar novos estados de animação, basta importar seu fbx, garantir que o nome da animação seja definido com um nome distinto e arraste essa animação para o animador.

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

Em seu script personalizado, faça uma chamada a follow () enquanto você quiser que o Rig de mão esteja seguindo o Trackingobject e, em seguida, faça uma chamada para MoveToTargetPosition () quando desejar que o Rig mão comece seu movimento com o TargetObject.

#### <a name="controlling-movetotarget-via-animations"></a>Controlando o MoveToTarget por meio de animações

Na animação que precisa ser movida, defina dois eventos: um com uma chamada para follow () e outro com uma chamada para MoveToTargetPosition (). A seguir deve ser definido no primeiro quadro-chave, já que faz com que o Rig de mão siga o Trackingobject. MoveToTargetPosition deve ser definido no quadro-chave onde você deseja que o Rig comece a mudar para o destino. É assim que a funcionalidade de script é usada no pré-fabricados fornecido.

### <a name="rotatearoundpoint"></a>RotateAroundPoint

O script RotateAroundPoint. cs fornece a funcionalidade para girar a dica de mão em um ponto dinâmico ao longo do tempo.

#### <a name="how-to-set-up-rotatearoundpoint"></a>Como configurar o RotateAroundPoint

O pré-fabricados "RotatingHandCoachRoot_L. pré-fabricado" e "RotatingHandCoachRoot_R. pré-fabricado" fornecidos contêm um RotateAroundPoint em suas hierarquias. Se você quiser usar esse script em sua própria configuração, precisará colocá-lo no gameobject raiz que contém o Animator para seu Rig.

#### <a name="inspector-properties"></a>Propriedades do Inspetor

- **CenteredParent** Defina isso com o objeto pai em que você deseja que o Rig seja dinamizado.
- **InverseParent** Defina isso com o pai para girar inversamente para centeredParent a fim de manter a mesma orientação. Em geral, esse será o objeto pai com o script InteractionHint.
- **PivotPosition** Defina isso para um ponto em que você deseja que a dica comece a ser movimentada.
- **Duração** A quantidade de tempo que deve levar (em segundos) para girar em volta do CenteredParent.
- **AnimationCurve** Isso é padronizado para uma curva linear, mas você pode alterar a curva para fornecer a atenuação de entrada/saída ao iniciar e parar o caminho de movimento.
- **RotationVector** Quantos graus girar ao longo de cada eixo.

#### <a name="controlling-rotatearoundpoint-via-script"></a>Controlando RotateAroundPoint por meio de script

No script personalizado, faça uma chamada para RotateToTarget() quando quiser que o equipamento de mão inicie sua rotação em torno do CenteredParent. Quando você quiser que a posição seja redefinida para o PivotPosition original, faça uma chamada para ResetAndDeterminePivot().

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Controlando RotateAroundPoint por meio de animações

Na animação que precisa ser movimentada, defina dois eventos: um com uma chamada para ResetAndDeterminePivot() e outro com uma chamada para RotateToTarget(). ResetAndDeterminePivot deve ser definido no primeiro keyframe, pois faz com que o equipamento de mão seja redefinido para o PivotPosition. RotateToTarget deve ser definido no keyframe em que você deseja que o equipamento comece a girar em torno do CenteredParent. É assim que a funcionalidade de script é usada nos pré-requisitos fornecidos.
