---
title: Visão geral do solucionador
description: Visão geral do Solucionadores no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Solucionadores,
ms.openlocfilehash: 28e961aa20fb15b533f369ed436e2d8178d682801f6f6ce6a703e53a0c26ac01
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206852"
---
# <a name="solver-overview"></a>Visão geral do solucionador

![Solucionador Principal](../../images/solver/MRTK_Solver_Main.png)

Os solucionadores são componentes que facilitam a forma de calcular a posição e orientação de um objeto de acordo com um algoritmo predefinido. Um exemplo pode ser a colocação de um objeto na superfície que o raycast do olhar do usuário atinge no momento.

Além disso, o sistema Solucionador define, de forma determinista, uma ordem de operações para esses cálculos de transformação, pois não há nenhuma maneira confiável de especificar ao Unity a ordem de atualização dos componentes.

Os solucionadores oferecem diversos comportamentos para anexar objetos a outros objetos ou sistemas. Um outro exemplo seria um objeto de marcação que focalize na frente do usuário (com base na câmera). Um solucionador também pode ser anexado a um controlador e a um objeto para que o objeto seja marcado no controlador. Todos os solucionadores podem ser empilhados com segurança, por exemplo, um comportamento de marcação + magnetismo de superfície + impulso.

## <a name="how-to-use-a-solver"></a>Como usar um solucionador

O sistema Solucionador consiste em três categorias de scripts:

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver): a classe abstrata de base da qual todos os solucionadores derivam. Ela fornece acompanhamento de estado, suavização de parâmetros e implementação, integração automática do sistema do solucionador e ordem de atualização.
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler): define o objeto de referência a ser rastreado (por exemplo: a transformação da câmera principal, o raio de mão etc.), lida com a coleta de componentes do solucionador e os atualiza na ordem adequada.

A terceira categoria é o próprio solucionador. Os seguintes solucionadores fornecem os blocos de construção para o comportamento básico:

* [`Orbital`](#orbital): bloqueia em uma posição e deslocamento específicos do objeto referenciado.
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize): dimensiona para manter um tamanho constante em relação à exibição do objeto referenciado.
* [`RadialView`](#radialview): mantém o objeto em uma conversão de cone de exibição pelo objeto referenciado.
* [`Follow`](#follow): mantém o objeto dentro de um conjunto de limites definidos pelo usuário do objeto referenciado.
* [`InBetween`](#inbetween): mantém um objeto entre dois objetos rastreados.
* [`SurfaceMagnetism`](#surfacemagnetism): lança raios em superfícies no mundo e alinha o objeto a essa superfície.
* [`DirectionalIndicator`](#directionalindicator): determina a posição e a orientação de um objeto como um indicador direcional. Do ponto de referência do Destino Controlado do SolverHandler, esse indicador ficará em direção ao DirectionalTarget fornecido.
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum): aplica aceleração/velocidade/atrito para simular o impulso e a elasticidade de um objeto que está sendo movido por outros solucionadores/componentes.
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup): restringe o objeto seguindo as mãos em uma região que não cruza o GameObject com as mãos. Útil para conteúdo interativo restrito à mão, como menus etc. Esse solucionador destina-se a trabalhar com [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand), mas também funciona com [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController).
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup): deriva do HandConstraint, mas inclui lógica para testar se a palma da mão está voltada para o usuário antes da ativação. Esse solucionador funciona apenas com controladores [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand). Com outros tipos de controlador, esse solucionador se comportará exatamente como sua classe base.

Para usar o sistema do Solucionador, basta adicionar um dos componentes listados acima a um GameObject. Como todos os Solucionadores exigem [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler), um será criado automaticamente pelo Unity.

> [!NOTE]
> Exemplos de como usar o sistema de Solucionadores podem ser encontrados no arquivo **SolverExamples.scene**.

## <a name="how-to-change-tracking-reference"></a>Como alterar a referência de acompanhamento

A propriedade *Tipo de Destino Controlado* do componente [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) define o ponto de referência que todos os solucionadores usarão para calcular seus algoritmos. Por exemplo, um tipo de valor de [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) com um componente [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) simples, resultará em um raycast da cabeça e na direção do olhar do usuário para resolver qual superfície é atingida. Valores potenciais para a propriedade `TrackedTargetType` são:

* *Head*: o ponto de referência é a transformação da câmera principal
* *ControllerRay*: o ponto de referência é a transformação [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) em um controlador (ou seja, origem do ponteiro em um controlador de movimentos ou controlador de mão) apontando na direção do raio de linha
  * Use a propriedade `TrackedHandedness` para selecionar a preferência de destro/canhoto (ou seja, Esquerda, Direita, Ambas)
* *HandJoint*: o ponto de referência é a transformação de uma articulação da mão específica
  * Use a propriedade `TrackedHandedness` para selecionar a preferência de destro/canhoto (ou seja, Esquerda, Direita, Ambas)
  * Use a propriedade `TrackedHandJoint` para determinar a transformação da articulação a ser utilizada
* *CustomOverride*: ponto de referência do `TransformOverride` atribuído

> [!NOTE]
> Para os tipos *ControllerRay* e *HandJoint,* o manipulador do solucionador tentará fornecer primeiro a transformação do controlador/mão esquerda e, em seguida, a direita se a primeira não estiver disponível ou a menos que a propriedade `TrackedHandedness` especifique o contrário.

![Objeto Acompanhado do Solucionador](../../images/solver/TrackedObjectType-Example.gif) 
*Exemplo de várias propriedades associadas a cada TrackedTargetType*

> [!IMPORTANT]
> A maioria dos solucionadores usa o vetor de destino da transformação acompanhada fornecido por `SolverHandler`. Ao usar um tipo de destino acompanhado da *Articulação da Mão*, o vetor de avanço da articulação da palma da mão pode apontar pelos dedos e não pela palma da mão. Isso depende da plataforma que fornece os dados da articulação da mão. Para simulação de entrada e Windows Mixed Reality, o *vetor de ascensão* aponta para cima através da palma da mão (ou seja, vetor verde para cima, vetor azul para frente).
>
> ![Vetor de ascensão de avanço](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> Para resolver isso, atualize a propriedade de *Rotação Adicional* no `SolverHandler` para **<90, 0, 0>** . Isso garantirá que o vetor de avanço fornecido aos solucionadores está apontando pela palma da mão e para fora na direção contrária da mão.
>
> ![Rotação Adicional](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> Como alternativa, use o tipo de destino controlado *Raio do Controlador* para obter um comportamento semelhante ao apontar com as mãos.

## <a name="how-to-chain-solvers"></a>Como encadear solucionadores

É possível adicionar vários componentes `Solver` ao mesmo GameObject encadeando seus algoritmos. Os componentes `SolverHandler` lidam com a atualização de todos os solucionadores no mesmo GameObject. Por padrão, as `SolverHandler` chamadas `GetComponents<Solver>()` em Iniciar retornarão os Solucionadores na ordem em que aparecem no inspetor.

Além disso, definir a propriedade *Transformação Vinculada Atualizada* como verdadeiro, instrui `Solver` a salvar sua posição calculada, orientação e escala em uma variável intermediária acessível por todos os Solucionadores (ou seja, `GoalPosition`). Se definida como falso, `Solver` atualizará a transformação do GameObject diretamente. Ao salvar as propriedades de transformação em um local intermediário, outros Solucionadores podem executar seus cálculos começando na variável intermediária. Isso acontece porque o Unity não permite que as atualizações no gameObject.transform sejam empilhadas dentro do mesmo quadro.

> [!NOTE]
> Os desenvolvedores podem modificar a ordem de execução dos Solucionadores definindo a propriedade `SolverHandler.Solvers` diretamente.

## <a name="how-to-create-a-new-solver"></a>Como criar um novo solucionador

Todos os solucionadores devem herdar da classe base abstrata, [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver). Os principais requisitos de uma extensão do Solucionador envolvem a substituição do método `SolverUpdate`. Nesse método, os desenvolvedores devem atualizar as propriedades herdadas `GoalPosition`, `GoalRotation` e `GoalScale` para os valores desejados. Além disso, geralmente é valioso aproveitar `SolverHandler.TransformTarget` como o quadro de referência desejado pelo consumidor.

O código fornecido abaixo fornece um exemplo de um novo componente Solucionador chamado `InFront` que coloca o objeto anexado 2m na frente do `SolverHandler.TransformTarget`. Se `SolverHandler.TrackedTargetType` for definido pelo consumidor como [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), o `SolverHandler.TransformTarget` será a transformação da câmera e, portanto, esse Solucionador colocará o GameObject anexado a 2m na frente do olhar dos usuários a cada quadro.

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>Guias de implementação do solucionador

### <a name="common-solver-properties"></a>Propriedades comuns do solucionador

Cada componente do Solucionador tem um conjunto principal de propriedades idênticas que controlam o comportamento principal do Solucionador.

Se a *Suavização* estiver habilitada, o Solucionador atualizará gradualmente a transformação do GameObject ao longo do tempo de acordo com os valores calculados. A velocidade dessa alteração é determinada pela propriedade *LerpTime* de cada componente da transformação. Por exemplo, um valor *MoveLerpTime* mais alto resultará em incrementos mais lentos na movimentação entre quadros.

Se *MaintainScale* estiver habilitado, o Solucionador utilizará a escala local padrão do GameObject.

![Propriedades do Solucionador Principal](../../images/solver/GeneralSolverProperties.png)  
*Propriedades comuns herdadas por todos os componentes do Solucionador*

### <a name="orbital"></a>Orbital

A classe [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) é um componente de marcação que se comporta como planetas em um sistema solar. Esse Solucionador garantirá que o GameObject anexado orbite ao redor da transformação acompanhada. Portanto, se o *Tipo de Destino Acompanhado* do [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) estiver definido como [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), o GameObject irá orbitar ao redor da cabeça do usuário com um deslocamento fixo aplicado.

Os desenvolvedores podem modificar esse deslocamento fixo para manter os menus ou outros componentes de cena ao nível dos olhos ou ao nível da inclinação etc. em torno de um usuário. Isso é feito modificando as propriedades *Deslocamento Local* e *Deslocamento Mundial*. A propriedade *Tipo de Orientação* determina a rotação aplicada ao objeto se ele mantiver sua rotação original ou sempre ficar voltado para a câmera ou para qualquer transformação que estiver impulsionando sua posição etc.

![Exemplo do Orbital](../../images/solver/OrbitalExample.png)  
*Exemplo do Orbital*

### <a name="radialview"></a>RadialView

O [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) é outro componente de marcação que mantém uma parte específica de um GameObject dentro do tronco de exibição do usuário.

As propriedades *Grau de Exibição Mínimo e Máximo* determinam o tamanho de uma parte do GameObject que sempre deve estar em exibição.

As propriedades *Distância Mínima e Máxima* determinam a distância na qual o GameObject deve ser mantido do usuário. Por exemplo, andar na direção do GameObject com uma *Distância Mínima* de 1m fará com que o GameObject nunca esteja a menos de 1m do usuário.

Geralmente, o [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) é usado em conjunto com o *Tipo de Destino Controlado* definido como [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) para que o componente siga o olhar do usuário. No entanto, esse componente pode funcionar para ser mantido em *"exibição"* de qualquer *Tipo de Destino Controlado*.

![Exemplo de RadialView](../../images/solver/RadialViewExample.png)  
*Exemplo de RadialView*

### <a name="follow"></a>Seguir

A classe [`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow) posiciona um elemento na frente do destino controlado em relação ao eixo dianteiro local. O elemento pode ser restrito de forma flexível (também conhecido como marcação) para que ele não siga até que o destino controlado se mova além dos limites definidos pelo usuário.

Ele funciona da mesma forma que o solucionador RadialView, com controles adicionais para gerenciar *Grau de Exibição Máximo Horizontal e Vertical*, e mecanismos para alterar a *Orientação* do objeto.

![Siga as propriedades](../../images/solver/FollowExample.png)  
*Siga as propriedades*

![Siga a cena de exemplo](../../images/solver/FollowExampleScene.gif)  
*Siga a Cena de Exemplo (Assets/MRTK/Examples/Demos/Solvers/Scenes/FollowSolverExample.unity)*

### <a name="inbetween"></a>InBetween

A classe [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) manterá o GameObject anexado entre duas transformações. Esses dois pontos de extremidade de transformação são definidos pelo próprio [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)*Tipo de Destino Controlado* do GameObject e pela propriedade do [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween)*Segundo Tipo de Destino Controlado* do componente. Em geral, ambos os tipos serão definidos como [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride) e os valores `SolverHandler.TransformOverride` e `InBetween.SecondTransformOverride` resultantes definidos como os dois pontos de extremidade controlados.

No tempo de execução, o componente [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) criará outro componente [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) com base nas propriedades do *Segundo Tipo de Destino Controlado* e *Segunda Substituição de Transformação*.

`PartwayOffset` define onde, na linha entre duas transformações, o objeto deve ser colocado com 0,5 como a metade, 1,0 na primeira transformação e 0,0 na segunda transformação.

![Exemplo de InBetween](../../images/solver/InBetweenExample.png)  
*Exemplo de uso do solucionador InBetween para manter o objeto entre duas transformações*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

[`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) funciona executando um raycast em um LayerMask definido de superfícies, e colocando o GameObject nesse ponto de contato.

O *Deslocamento Normal da Superfície* colocará o GameObject a uma distância definida em metros de distância da superfície na direção do normal no ponto de clique na superfície.

Por outro lado, o *Deslocamento do Raio de Superfície* colocará o GameObject a uma distância definida em metros de distância da superfície, mas na direção contrária do raycast executado. Portanto, se o raycast for o olhar do usuário, o GameObject se aproximará ao longo da linha do ponto de clique na superfície para a câmera.

O *Modo de Orientação* determina o tipo de rotação a ser aplicada em relação ao normal na superfície.

* *None* – nenhuma rotação aplicada
* *TrackedTarget* – o objeto ficará voltado para a transformação controlada executando o raycast
* *SurfaceNormal* – o objeto será alinhado com base no normal no ponto de clique na superfície
* *Blended* – o objeto será alinhado com base no normal no ponto de clique na superfície E com base na transformação controlada.

Para forçar o GameObject associado a permanecer na vertical em qualquer modo diferente de *None*, habilite *Manter Orientação Vertical*.

> [!NOTE]
> Use a propriedade *Combinação de Orientação* para controlar o equilíbrio entre os fatores de rotação quando o *Modo de Orientação* for definido como *Blended*. A orientação do valor de 0,0 será totalmente determinada pelo modo *TrackedTarget*, e a orientação do valor de 1,0 será totalmente determinada por *SurfaceNormal*.

![Exemplo de SurfaceMagtism](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>Determinando quais superfícies podem ser atingidas

Ao adicionar um componente [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) a um GameObject, é importante considerar a camada do GameObject e seus filhos, se algum tiver colisores. O componente funciona executando vários tipos de raycasts para determinar em qual superfície deverá se "atrair". Se o solucionador GameObject tiver um colisor em uma das camadas listadas na propriedade `MagneticSurfaces` de `SurfaceMagnetism`, o raycast provavelmente se atingirá, resultando na anexação do GameObject ao seu próprio ponto de colisor. Esse comportamento inesperado pode ser evitado definindo o GameObject principal e todos os filhos para a camada *Ignorar Raycast* ou modificando a matriz LayerMask `MagneticSurfaces` adequadamente.

Por outro lado, um GameObject [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) não colidirá com superfícies em uma camada não listada na propriedade `MagneticSurfaces`. Geralmente, é recomendável colocar todas as superfícies desejadas em uma camada dedicada (ou seja, *Superfícies*) e definir a propriedade `MagneticSurfaces` como apenas esta camada.  Usar o *padrão* ou *tudo* pode resultar em componentes de interface do usuário ou cursores que contribuem para o solucionador.

Por fim, superfícies mais distantes que a configuração da propriedade `MaxRaycastDistance` serão ignoradas pelos raycasts `SurfaceMagnetism`.

### <a name="directionalindicator"></a>DirectionalIndicator

A classe [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) é um componente de marcação voltado para a direção de um ponto desejado no espaço.

Mais comumente usado quando o *Tipo de Destino Controlado* do [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) é definido como [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head). Dessa forma, um componente de UX com o solucionador [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) direcionará um usuário a olhar  para o ponto desejado.

O ponto desejado é determinado por meio da propriedade *Destino Direcional*.

Se o destino direcional puder ser visualizado pelo usuário ou qualquer quadro de referência for definido no [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler), esse solucionador desabilitará todos os componentes [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) abaixo dele. Se não for visualizável, tudo será habilitado no indicador.

O tamanho do indicador reduzirá quanto mais próximo o usuário estiver de capturar o *Destino Direcional* em seu FOV.

* *Escala Mínima de Indicadores* – a escala mínima do objeto indicador
* *Escala Máxima de Indicadores* – a escala máxima do objeto indicador

* *Fator de Escala de Visibilidade* – multiplicador para aumentar ou diminuir o FOV que determina se o ponto do *Destino Direcional* é visualizável ou não
* *Deslocamento de Exibição* – do ponto de vista do quadro de referência (ou seja, possivelmente a câmera), essa propriedade define a qual distância, na direção do indicador, o objeto deve estar do centro do viewport.

![Propriedades do Indicador Direcional](../../images/solver/DirectionalIndicatorExample.png)  
*Propriedades do Indicador Direcional*

![Cena de exemplo do Indicador Direcional](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*Cena de Exemplo do Indicador Direcional (Assets/MRTK/Examples/Demos/Solvers/Scenes/DirectionalIndicatorSolverExample.unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>Menu lateral com HandConstraint e HandConstraintPalmUp

![Exemplo de UX do Menu Lateral](../../images/solver/MRTK_UX_HandMenu.png)

O comportamento [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) fornece um solucionador que restringe o objeto controlado a uma região segura para conteúdo restrito à mão (como interface do usuário da mão, menus etc.). Regiões seguras são consideradas áreas que não se cruzam com a mão. Uma classe derivada de [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) chamada [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) também é incluída para demonstrar um comportamento comum de ativar o objeto controlado pelo solucionador quando a palma da mão estiver voltada para o usuário.

[Consulte a página Menu Lateral](../hand-menu.md) para ver os exemplos de como usar o solucionador de Restrição de Mão para criar menus laterais.

## <a name="see-also"></a>Confira também

* [Acompanhamento da Mão](../../input/hand-tracking.md)
* [Foco](../../input/gaze.md)
