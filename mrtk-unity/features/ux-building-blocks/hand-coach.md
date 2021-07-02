---
title: Orientador de mão
description: Descrição e exemplos para o direito à mão.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f6042fce7c95c106de9c72adc854e2b7112da63c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177156"
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

## <a name="hand-3d-assets"></a>Mãos de ativos 3D

Você pode encontrar os ativos em: [MixedRealityToolkit. SDK/experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Qualidade

Se você perceber distorções na malha com revestimento, precisará ter certeza de que seu projeto está usando a quantidade adequada de junções.
vá para editar > do Unity Project Configurações > qualidade > outros pesos de mesclagem >. Verifique se "4 Bones" estão selecionados para ver as junções suaves.
![Project Configuração](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>Scripts

### <a name="interaction-hint"></a>Dica de interação

O `InteractionHint.cs` script fornece a funcionalidade de wrapper para disparar animações e esmaecer para o Rig à mão.

#### <a name="how-to-set-up-an-interaction-hint"></a>Como configurar uma dica de interação

Para configurar uma dica de interação, é recomendável usar o pré-fabricados fornecido "StaticHandCoachRoot_L. pré-fabricado" e "StaticHandCoachRoot_R. pré-fabricado". Esse pré-fabricado contém o script InteractionHint e o Rig mão, bem como a hierarquia apropriada para garantir que as animações de dica fornecidas funcionem conforme o esperado.
Caso contrário, você precisará colocar o script em um gameobject um nível pai do seu Rig com Animator.

#### <a name="inspector-properties"></a>Propriedades do Inspetor

- **HideIfHandTracked** Esse booliano especifica se o estado de acompanhamento manual deve ser usado para ocultar visuais quando as mãos de um usuário estão sendo rastreadas. Se isso for definido como false, somente a propriedade de script "customShouldHideVisuals" será usada para determinar se a dica deve ser ocultada.

- **MinDelay** Esta propriedade especifica o atraso mínimo para mostrar os elementos visuais. Por padrão, os visuais para a mão aparecerão após esse número de segundos se as mãos do usuário não estiverem sendo rastreadas.

- **MaxDelay** Esta propriedade especifica o atraso máximo para mostrar os elementos visuais. Por padrão, os visuais para a mão aparecerão após esse número de segundos, mesmo se as mãos do usuário estiverem sendo rastreadas.

- **UseMaxTimer** Se esse booliano for definido como false, ele desabilitará o timer máximo e só permitirá que a dica de mão seja mostrada quando as mãos do usuário estiverem fora de exibição ou a condição personalizada retornar false.

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

O Animator e o script foram configurados de forma a tornar a instalação o mais simples possível. Para adicionar novos Estados de animação, simplesmente importe seu FBX, verifique se o nome da animação está definido com um nome distinto e arraste essa animação para o Animator.

### <a name="movetotarget"></a>MoveToTarget

O script MoveToTarget. cs fornece a funcionalidade para mover a dica de mão de uma posição de rastreamento para uma posição de destino ao longo do tempo.

#### <a name="how-to-set-up-movetotarget"></a>Como configurar o MoveToTarget

O pré-fabricados "MovingHandCoachRoot_L. pré-fabricado" e "MovingHandCoachRoot_R. pré-fabricado" fornecidos contêm um MoveToTarget em suas hierarquias. Se você quiser usar esse script em sua própria configuração, precisará colocá-lo no gameobject raiz que contém o Animator para seu Rig.

#### <a name="inspector-properties"></a>Propriedades do Inspetor

- **Trackingobject** Defina isso com o objeto que você deseja que o Rig acompanhe antes de iniciar seu movimento. É recomendável criar um gameobject vazio e movê-lo para uma posição específica para ajudá-lo a identificar o controle.
- **TargetObject** Defina isso com o objeto que você deseja que o Rig mova durante seu movimento. É recomendável criar um gameobject vazio e movê-lo para uma posição específica para ajudá-lo a identificar o controle.
- **RootObject** Defina isso para um pai compartilhado entre o rastreamento e o objeto de destino para que as posições relativas possam ser calculadas corretamente. O pré-fabricado incluído tem objetos de rastreamento e de destino em sua hierarquia, mas você pode definir o objeto de destino como um gameobject fora do pré-fabricado e alterar o objeto raiz para um pai compartilhado.
- **Duração** A quantidade de tempo que deve levar (em segundos) para passar de Trackingobject para TargetObject em segundos.
- **TargetOffset** Um deslocamento ajustável para obter o gameobject para chegar à posição de destino correta. Isso será útil se a sua animação incluir um deslocamento de posição durante a animação.
- **AnimationCurve** Isso é padronizado para uma curva linear, mas você pode alterar a curva para fornecer a atenuação de entrada/saída ao iniciar e parar o caminho de movimento.

#### <a name="controlling-movetotarget-via-script"></a>Controlando MoveToTarget por meio de script

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

Em seu script personalizado, faça uma chamada para RotateToTarget () quando você quiser que o Rig de mão comece sua rotação em volta do CenteredParent. Quando desejar que a posição seja redefinida para o PivotPosition original, faça uma chamada para ResetAndDeterminePivot ().

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Controlando o RotateAroundPoint por meio de animações

Na animação que precisa ser movida, defina dois eventos: um com uma chamada para ResetAndDeterminePivot () e outro com uma chamada para RotateToTarget (). ResetAndDeterminePivot deve ser definido no primeiro quadro-chave, pois faz com que o Rig de mão redefina para o PivotPosition. RotateToTarget deve ser definido no quadro-chave onde você deseja que o Rig comece a girar em volta do CenteredParent. É assim que a funcionalidade de script é usada no pré-fabricados fornecido.
