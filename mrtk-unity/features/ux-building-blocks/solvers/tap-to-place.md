---
title: Toque para posicionar
description: Documentação do MRTK do TapToPlace
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Toque para Posicionar,
ms.openlocfilehash: 98408312ec2637dc3fa137e7d51cce1f37e816f9a21b703ec9216bf90251661f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198298"
---
# <a name="tap-to-place"></a>Toque para posicionar

![TapToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

Toque para Posicionar é um componente de interação distante usado para colocar um objeto de jogo na superfície. Esse componente é útil para colocar objetos em uma malha espacial. Toque para Posicionar usa uma combinação de dois cliques e movimento da cabeça para posicionar um objeto. Um clique para iniciar o posicionamento, movimento da cabeça para controlar a posição do objeto e um clique para posicionar o objeto na cena.

## <a name="using-tap-to-place"></a>Usando o Toque para Posicionar

1. Configurar a cena
    - Criar uma nova cena do Unity
    - Adicione o MRTK à cena navegando até o **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar**
    > [!NOTE]
    > O Toque para Posicionar usa cliques controlados pelo Sistema de Entrada do MRTK, mas também pode ser controlado sem cliques, consulte a seção Capacidade de Configuração de Código do Toque para Posicionar abaixo.
    - Adicione um cubo à cena e altere a escala para 0,2 e altere a posição para (0, 0, 0,7).
1. Anexar [Toque para Posicionar](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) a um objeto de jogo com um colisor

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - Quando o componente Toque para Posicionar for adicionado, um Manipulador do Solucionador também será anexado. O Toque para Posicionar deriva da classe [Solucionador](solver.md) que requer um Manipulador do Solucionador. A posição de um objeto Toque para Posicionar é calculada em relação ao `TrackedTargetType` no Manipulador do Solucionador. Por padrão, Cabeça é `TrackedTargetType`, ou seja, quando a cabeça se move, o objeto segue se estiver selecionado.  `TrackedTargetType` também pode ser definido como Raio do Controlador, que faz com que o objeto siga o controlador. O primeiro grupo de propriedades no inspetor do Toque para Posicionar são as [Propriedades Comuns do Solucionador](solver.md#common-solver-properties).  
    > [!IMPORTANT]
    > Toque para Posicionar é um Solucionador autônomo e não pode ser encadeado com outros Solucionadores. Ele não pode ser encadeado pois SolverHandler.UpdateSolvers é usado para atualizar a posição do objeto enquanto ele está sendo posicionado.
    - Propriedades do Toque para Posicionar:
        - `Auto Start`: se verdadeiro, o solucionador do Toque para Posicionar começará a controlar a posição do objeto de jogo a ser posicionado. O objeto começará imediatamente a seguir o TrackedTargetType (Cabeça ou Raio do Controlador). Esse valor deve ser modificado antes que Start() seja invocado para ter efeito.
        - `Default Placement Distance`: a distância padrão (em metros) que um objeto será posicionado em relação ao trackedTargetType para frente no SolverHandler. O objeto do jogo será posicionado na distância de posicionamento padrão se uma superfície não for atingida pelo raycast.
        - `Max Raycast Distance`: a distância máxima (metros) para o raycast com base na origem 'TrackedTargetType'. Esse raycast procura uma superfície para posicionar um objeto selecionado.
        - `UseDefaultSurfaceNormalOffset`: essa propriedade é verdadeira por padrão, ela garante que o objeto que está sendo posicionado esteja alinhado em uma superfície. Se essa propriedade for verdadeira, o deslocamento normal da superfície padrão será aplicado em vez de qualquer valor especificado para a propriedade `SurfaceNormalOffset`. Se falso, o valor de `SurfaceNormalOffset` será aplicado. O deslocamento normal da superfície padrão são as extensão do colisor ao longo do eixo z.
        - `Surface Normal Offset`: a distância entre o centro do objeto do jogo a ser posicionado e uma superfície ao longo da superfície normal, se o raycast atingir uma superfície. Essa propriedade só será aplicada a um objeto se `UseDefaultSurfaceNormalOffset` for falso.
        - `Keep Orientation Vertical`: se verdadeiro, o objeto de jogo a ser posicionado permanecerá na vertical e alinhado com Vector3.up.
        - `Rotate According to Surface`: se falso, o objeto do jogo a ser posicionado não alterará sua rotação de acordo com a superfície atingida.  O objeto permanecerá voltado para a câmera enquanto IsBeingPlaced for verdadeiro.
        - `Magnetic Surfaces`: uma matriz de LayerMasks a ser executada da prioridade mais alta para a mais baixa. A primeira máscara de camada a fornecer um clique de raycast será usada para os cálculos de posição.
        - `Debug Enabled`: se verdadeiro e no Editor do Unity, o clique de raycast normal será desenhado em amarelo. A depuração habilitada é útil quando `RotateAccordingToSurface` for verdadeiro, pois ela desenha a superfície atingida normal, o que explica visualmente por que o objeto é definido em sua orientação atual.
        - `On Placing Started`: esse evento é disparado uma vez quando o objeto de jogo a ser posicionado é selecionado.
        - `On Placing Stopped`: esse evento é disparado uma vez quando o objeto de jogo a ser posicionado tem a seleção cancelada.

1. Testando o comportamento do Toque para Posicionar no editor
    - Pressione executar e segure a barra de espaço para mostrar uma mão de simulação de entrada.
    - Mova a mão até que o cubo esteja em foco e simule um clique com a mão de simulação de entrada clicando com o botão esquerdo do mouse.
        - Se os colisores não estiverem presentes na cena, o objeto seguirá `TrackedTargetType` o no `Default Placement Distance` definido.
    - O objeto seguirá o movimento de `TrackedTargetType` após a seleção. Para simular o movimento da cabeça no editor, pressione as teclas WASD. Altere a rotação da cabeça clicando e segurando o botão direito do mouse.
    - Para parar de posicionar o objeto, clique novamente.  O objeto não precisa estar em foco para o clique de parar posicionamento. O foco só é necessário para o clique inicial que inicia o processo de posicionamento.

    `TrackedTargetType`: Cabeça (Padrão) |  `TrackedTargetType`: Raio do Controlador
    :-------------------------:|:-------------------------:
    ![Toque para Posicionar Simulação de Entrada Cabeça Raio de controle](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![Toque para Posicionar Simulação de Entrada Raio do Controlador 2](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>Toque para Posicionar Capacidade de Configuração de Código

O tempo de seleção de objeto do Toque para Posicionar também pode ser controlado por `StartPlacement()` e `StopPlacement()`em vez de exigir um evento de clique. Essa funcionalidade é útil para escrever testes e fornece um método alternativo para posicionar um objeto no editor sem usar o Sistema de Entrada do MRTK.

1. Criar um objeto de jogo vazio
1. Criar e anexar o script de exemplo a seguir ao objeto de jogo vazio

    ```c#
    using UnityEngine;
    using Microsoft.MixedReality.Toolkit.Utilities.Solvers;

    public class TapToPlaceInputExample : MonoBehaviour
    {
        private GameObject cube;
        private TapToPlace tapToPlace;

        void Start()
        {
            cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
            cube.transform.localScale = Vector3.one * 0.2f;
            cube.transform.position = Vector3.forward * 0.7f;

            tapToPlace = cube.AddComponent<TapToPlace>();
        }

        void Update()
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                tapToPlace.StartPlacement();
            }
            if (Input.GetKeyDown(KeyCode.I))
            {
                tapToPlace.StopPlacement();
            }
        }
    }
    ```

1. No modo de reprodução, pressione a *tecla U* para começar a posicionar o cubo
1. Pressione a *tecla I* para interromper o posicionamento

## <a name="tap-to-place-example-scene"></a>Cena de Exemplo do Toque para Posicionar

A cena de exemplo do Toque para Posicionar consiste em 4 objetos posicionáveis, cada um com uma configuração diferente. A cena de exemplo contém paredes para mostrar o comportamento do posicionamento da superfície desabilitado por padrão na hierarquia. A cena de exemplo pode ser encontrada no pacote do Unity Microsoft.MixedReality.Toolkit.Unity.Examples, encontrado na [Página de Versão](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases). O local da cena é: *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*

![Exemplo de Toque para Posicionar](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>Confira também

- [Solucionadores](solver.md)
- [Conscientização Espacial](../../spatial-awareness/spatial-awareness-getting-started.md)
- [Simulação de entrada](../../input-simulation/input-simulation-service.md)
- [Acompanhamento da Mão](../../input/hand-tracking.md)
- [Foco](../../input/gaze.md)
