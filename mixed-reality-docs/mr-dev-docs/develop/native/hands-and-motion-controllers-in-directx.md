---
title: Controladores de mãos e emovimento no DirectX
description: Começar a usar o guia do desenvolvedor para usar controladores de movimento e acompanhamento de mão em aplicativos DirectX nativos.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: mãos, controladores de movimento, directx, entrada, hologramas, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 13988df80052ef85662dcf9834406baa91d48f7c0b70242d1c904548c2707105
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210948"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Controladores de mãos e emovimento no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herddas.  Para novos projetos de aplicativo nativo, é recomendável usar a **[API openXR](openxr-getting-started.md)**.

No Windows Mixed Reality, a entrada [](../../design/motion-controllers.md) do controlador de movimento e da mão é tratada por meio das APIs de entrada espacial, encontradas no [Windows. Ui. Namespace Input.Spatial.](/uwp/api/windows.ui.input.spatial) Isso permite que você controle facilmente as ações comuns, como **Selecionar** pressiona da mesma maneira entre as mãos e os controladores de movimento.

## <a name="getting-started"></a>Introdução

Para acessar a entrada espacial Windows Mixed Reality, comece com a interface SpatialInteractionManager.  Você pode acessar essa interface chamando  [SpatialInteractionManager::GetForCurrentView](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), normalmente durante a inicialização do aplicativo.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

O trabalho de SpatialInteractionManager é fornecer acesso a [SpatialInteractionSources](/uwp/api/windows.ui.input.spatial.spatialinteractionsource), que representam uma fonte de entrada.  Há três tipos de SpatialInteractionSources disponíveis no sistema.
* **A** mão representa a mão detectada de um usuário. As fontes de mão oferecem recursos diferentes com base no dispositivo, desde gestos básicos no HoloLens até o acompanhamento de mão totalmente articulado no HoloLens 2. 
* **O** controlador representa um controlador de movimento emparelhado. Os controladores de movimento podem oferecer diferentes recursos, por exemplo, Selecionar gatilhos, Botões de menu, Botões de compreensão, touchpads e thumbsticks.
* **A** voz representa as palavras-chave detectadas pelo sistema de fala de voz do usuário. Por exemplo, essa fonte injetará uma opção Selecionar pressione e solte sempre que o usuário diz "Selecionar".

Os dados por quadro de uma fonte são representados pela interface [SpatialInteractionSourceState.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Há duas maneiras diferentes de acessar esses dados, dependendo se você deseja usar um modelo baseado em sondagem ou baseado em eventos em seu aplicativo.

### <a name="event-driven-input"></a>Entrada controlada por evento
O SpatialInteractionManager fornece vários eventos que seu aplicativo pode escutar.  Alguns exemplos incluem [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased e [SourceUpdated.](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)

Por exemplo, o código a seguir conectará um manipulador de eventos chamado MyApp::OnSourcePressed ao evento SourcePressed.  Isso permite que seu aplicativo detecte pressões em qualquer tipo de fonte de interação.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Esse evento pressionado é enviado para seu aplicativo de forma assíncrona, juntamente com o SpatialInteractionSourceState correspondente no momento em que a pressão ocorreu. Seu aplicativo ou mecanismo de jogos pode querer iniciar o processamento imediatamente ou enfileirar os dados do evento em sua rotina de processamento de entrada. Aqui está uma função de manipulador de eventos para o evento SourcePressed, que verifica se o botão selecionar foi pressionado.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

O código acima verifica apenas a pressionação "Selecionar", que corresponde à ação primária no dispositivo. Os exemplos incluem fazer um AirTap no HoloLens ou estorná-lo em um controlador de movimento.  Os pressionamentos 'Select' representam a intenção do usuário de ativar o holograma que ele está direcionando.  O evento SourcePressed será acionou para vários botões e gestos diferentes, e você pode inspecionar outras propriedades no SpatialInteractionSource para testar esses casos.

### <a name="polling-based-input"></a>Entrada baseada em sondagem
Você também pode usar SpatialInteractionManager para sondar o estado atual de entrada a cada quadro.  Para fazer isso, chame [GetDetectedSourcesAtTimestamp a](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) cada quadro.  Essa função retorna uma matriz que contém [um SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) para cada [SpatialInteractionSource ativo.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource) Isso significa que um para cada controlador de movimento ativo, um para cada mão rastreada e outro para fala se um comando 'select' tiver sido enunciado recentemente. Em seguida, você pode inspecionar as propriedades em cada SpatialInteractionSourceState para inserir a entrada em seu aplicativo. 

Aqui está um exemplo de como verificar a ação "selecionar" usando o método de sondagem. A *variável* de previsão representa [um objeto HolographicFramePrediction,](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) que pode ser obtido do [HolographicFrame.](/uwp/api/windows.graphics.holographic.holographicframe)

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Cada SpatialInteractionSource tem uma ID, que você pode usar para identificar novas fontes e correlacionar fontes existentes de quadro a quadro.  As mãos obterão uma nova ID sempre que sairem e inserirem o FOV, mas as IDs do controlador permanecerão estáticas durante a sessão.  Você pode usar os eventos em SpatialInteractionManager, como [SourceDetected](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) e [SourceLost,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)para reagir quando as mãos entram ou saem da exibição do dispositivo ou quando os controladores de movimento são ligado/desligados ou emparelhados/não emparelhados.

### <a name="predicted-vs-historical-poses"></a>Poses previstas versus históricas
GetDetectedSourcesAtTimestamp tem um parâmetro timestamp. Isso permite que você solicite o estado e represente dados que são previstos ou históricos, permitindo correlacionar interações espaciais com outras fontes de entrada. Por exemplo, ao renderizar a posição da mão no quadro atual, você pode passar o timestamp previsto fornecido pelo [HolographicFrame.](/uwp/api/windows.graphics.holographic.holographicframe) Isso permite que o sistema preveve a posição da mão para alinhar-se estreitamente com a saída de quadro renderizada, minimizando a latência percebida.

No entanto, essa pose prevista não produz um raio apontador ideal para direcionamento com uma fonte de interação. Por exemplo, quando um botão do controlador de movimento é pressionado, pode levar até 20 ms para que esse evento se esgoe por meio de Bluetooth para o sistema operacional. Da mesma forma, depois que um usuário faz um gesto de mão, algum tempo pode passar antes que o sistema detecte o gesto e seu aplicativo, em seguida, sonda-o. Quando seu aplicativo sonda uma alteração de estado, a cabeça e a mão são usadas para direcionar essa interação que realmente aconteceu no passado. Se você direcionar passando o timestamp atual do HolographicFrame para GetDetectedSourcesAtTimestamp, a pose será encaminhada prevista para o raio de direcionamento no momento em que o quadro será exibido, o que pode ter mais de 20 ms no futuro. Essa pose futura é boa *para* renderizar a  origem da interação, mas também é um problema de tempo para direcionar a interação, pois o direcionamento do usuário ocorreu no passado.

Felizmente, os [eventos SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased e [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) [SourceUpdated](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) fornecem o estado histórico associado a cada evento de entrada.  Isso inclui diretamente as poses de cabeça e mão históricas disponíveis por meio de [TryGetPointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), juntamente com um [timestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) histórico que você pode passar para outras APIs para correlacionar com esse evento.

Isso leva às seguintes práticas recomendadas ao renderizar e direcionar com mãos e controladores cada quadro:
* Para renderizar cada quadro à  **mão/controlador,** seu aplicativo deve sondar a pose prevista para frente de cada fonte de interação no momento do foton do quadro atual.   Você pode sondar todas as fontes de interação chamando [GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) em cada quadro, passando o timestamp previsto fornecido por [HolographicFrame::CurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Para o direcionamento de **mão/controlador** em uma press ou versão, seu aplicativo  deve manipular eventos pressionados/liberados, raycasting com base na pose de cabeça ou mão histórica para esse evento. Você obterá esse raio de direcionamento manipulando o evento [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) ou [SourceReleased,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) obter a propriedade [State](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) dos argumentos de evento e, em seguida, chamar seu [método TryGetPointerPose.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)

## <a name="cross-device-input-properties"></a>Propriedades de entrada entre dispositivos
A API SpatialInteractionSource dá suporte a controladores e sistemas de acompanhamento de mão com uma ampla variedade de recursos. Vários desses recursos são comuns entre tipos de dispositivo. Por exemplo, o controle de mão e os controladores de movimento fornecem uma ação 'select' e uma posição 3D. Sempre que possível, a API mapeia esses recursos comuns para as mesmas propriedades em SpatialInteractionSource.  Isso permite que os aplicativos deem mais suporte a uma ampla variedade de tipos de entrada. A tabela a seguir descreve as propriedades com suporte e como elas são comparadas entre tipos de entrada.

| Propriedade | Descrição | HoloLens(1ª geração) Gestos | Controladores de movimento | Mãos articuladas|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Entrega**](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Controle/à direita ou à esquerda. | Sem suporte | Com suporte | Suportado |
| [SpatialInteractionSourceState::**IsSelectPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Estado atual do botão primário. | Toque de Ar | Gatilho | Toque de Ar Descontraído (pinça vertical) |
| [SpatialInteractionSourceState::**IsGrasped**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Estado atual do botão de captura. | Sem suporte | Botão Segurar | Pinçar ou fechar a mão |
| [SpatialInteractionSourceState::**IsMenuPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Estado atual do botão de menu.    | Sem suporte | Botão Menu | Sem suporte |
| [SpatialInteractionSourceLocation::**Position**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Local XYZ da posição da mão ou da mão no controlador. | Localização da mão | Posição da pose da mão | Localização da mão |
| [SpatialInteractionSourceLocation::**Orientação**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Quaternion representando a orientação da posição de mão ou de alça no controlador. | Sem suporte | Segure a orientação da pose | Orientação de Palm |
| [SpatialPointerInteractionSourcePose::**Position**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origem do raio de apontar. | Sem suporte | Com suporte | Suportado |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Direção do raio de apontar. | Sem suporte | Com suporte | Suportado |

Algumas das propriedades acima não estão disponíveis em todos os dispositivos, e a API fornece um meio de testar isso. Por exemplo, você pode inspecionar a propriedade [SpatialInteractionSource:: IsGraspSupported](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) para determinar se a origem fornece uma ação de compreensão.

### <a name="grip-pose-vs-pointing-pose"></a>Segurar pose vs. ponto de apontar

o Windows Mixed Reality dá suporte a controladores de movimento em fatores forma diferentes.  Ele também dá suporte a sistemas de controle de mão articulados.  Todos esses sistemas têm diferentes relações entre a posição da mão e a direção natural "encaminhar" que os aplicativos devem usar para apontar ou renderizar objetos na mão do usuário.  Para dar suporte a tudo isso, há dois tipos de poses 3D fornecidos para os controladores de rastreamento e de movimento à mão.  A primeira é Segure pose, que representa a posição da mão do usuário.  A segunda é a pose de ponto, que representa um ponteiro de raio originário da mão do usuário ou do controlador. Portanto, se você quiser renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**, como uma gumes ou uma arma, use a pose de alça. Se você quiser Raycast a partir do controlador ou da mão, por exemplo, quando o usuário for * * apontando para a interface do usuário, use a pose de ponteiro.

Você pode acessar a **alça de pose** por meio de [SpatialInteractionSourceState::P Propriedades:: TryGetLocation (...)](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_). Ele é definido da seguinte maneira:
* A **posição de alça**: o Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça.
* O **eixo direito da orientação de alça**: quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)
* O **eixo de encaminhamento da orientação de alça**: quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.
* O **eixo superior da orientação de alça**: o eixo superior implícito pelas definições direita e avançar.

Você pode acessar o **ponteiro de pose** por meio de [SpatialInteractionSourceState::P Propriedades:: TryGetLocation (...):: SourcePointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) ou [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Propriedades de entrada específicas do controlador
Para controladores, o SpatialInteractionSource tem uma propriedade de controlador com recursos adicionais.
* **HasThumbstick:** Se for true, o controlador terá um Thumbstick. Inspecione a propriedade [controllerproperties](/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) do SpatialInteractionSourceState para adquirir os valores x e y de Thumbstick (ThumbstickX e ThumbstickY), bem como seu estado pressionado (IsThumbstickPressed).
* **HasTouchpad:** Se for true, o controlador terá um touchpad. Inspecione a propriedade Controllerproperties do SpatialInteractionSourceState para adquirir os valores x e y do Touchpad (TouchpadX e touchpad) e para saber se o usuário está tocando no Pad (IsTouchpadTouched) e se ele está pressionando o touchpad (IsTouchpadPressed).
* **SimpleHapticsController:** A API do SimpleHapticsController para o controlador permite inspecionar os recursos do haptics do controlador e também permite que você controle os comentários do Haptic.

O intervalo para Touchpad e Thumbstick é de-1 a 1 para ambos os eixos (de baixo para cima e da esquerda para a direita). O intervalo para o gatilho analógico, que é acessado usando a propriedade SpatialInteractionSourceState:: SelectPressedValue, tem um intervalo de 0 a 1. Um valor de 1 se correlaciona com IsSelectPressed sendo igual a true; qualquer outro valor se correlaciona com IsSelectPressed sendo igual a false.

## <a name="articulated-hand-tracking"></a>Acompanhamento de mão articulada
a API de Windows Mixed Reality fornece suporte completo para acompanhamento de mão articulada, por exemplo, no HoloLens 2. O controle de mão articulado pode ser usado para implementar a manipulação direta e modelos de entrada de ponto e confirmação em seus aplicativos. Ele também pode ser usado para criar interações totalmente personalizadas.

### <a name="hand-skeleton"></a>Esqueleto da mão
O controle de mão articulado fornece um esqueleto de 25 conjunta que permite muitos tipos diferentes de interações.  O esqueleto fornece cinco junções para o índice/meio/anel/pequenos dedos, quatro junções para o Thumb e uma junta de pulso.  A junta do pulso serve como a base da hierarquia. A figura a seguir ilustra o layout do esqueleto.

![Esqueleto da mão](images/hand-skeleton.png)

Na maioria dos casos, cada conjunto é nomeado com base no Bone que ele representa.  Como há dois Bones em cada conjunto, usamos uma Convenção de nomear cada conjunto com base no Bone filho nesse local.  O Bone filho é definido como o Bone além do pulso.  Por exemplo, a junção "index proximal" contém a posição inicial do proximal Bone do índice e a orientação desse Bone.  Ele não contém a posição final do Bone.  Se precisar disso, você o obteria do próximo conjunto na hierarquia, a junção de "índice intermediário".

Além das 25 junções hierárquicas, o sistema fornece um conjunto de Palm.  A Palm normalmente não é considerada parte da estrutura estrutural. Ele é fornecido apenas como uma maneira conveniente de obter a posição e a orientação gerais do manual.

As informações a seguir são fornecidas para cada conjunto:

| Name | Descrição |
|--- |--- |
|Posição | posição 3D da junção, disponível em qualquer sistema de coordenadas solicitado. |
|Orientation | orientação 3D do Bone, disponível em qualquer sistema de coordenadas solicitado. |
|Raio | Distância da superfície da capa na posição conjunta. Útil para ajustar interações diretas ou visualizações que dependem da largura do dedo. |
|Precisão | Fornece uma dica sobre a confiança do sistema sobre as informações deste conjunto. |

Você pode acessar os dados de esqueleto da mão por meio de uma função no [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  A função é chamada de [TryGetHandPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)e retorna um objeto chamado [HandPose](/uwp/api/windows.perception.people.handpose).  Se a origem não der suporte a mãos articuladas, essa função retornará NULL.  Depois de ter um HandPose, você pode obter os dados concorrentes atuais chamando [TryGetJoint](/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), com o nome da junção em que você está interessado.  Os dados são retornados como uma estrutura [JointPose](/uwp/api/windows.perception.people.jointpose) .  O código a seguir obtém a posição da dica de dedo do índice. A variável *CurrentState* representa uma instância de [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Malha à mão

A API de acompanhamento de mão articulada permite uma malha à mão do triângulo totalmente reformado.  Essa malha pode Deform em tempo real junto com o esqueleto da mão e é útil para visualização e técnicas de física avançadas.  Para acessar a malha à mão, primeiro você precisa criar um objeto [HandMeshObserver](/uwp/api/windows.perception.people.handmeshobserver) chamando [TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) no [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Isso só precisa ser feito uma vez por fonte, normalmente na primeira vez que você o vê.  Isso significa que você chamará essa função para criar um objeto HandMeshObserver sempre que uma mão inserir o FOV.  Essa é uma função assíncrona, portanto, você terá que lidar com um pouco de simultaneidade aqui.  Uma vez disponível, você pode solicitar ao objeto HandMeshObserver para o buffer de índice de triângulo chamando [GetTriangleIndices](/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Os índices não alteram o quadro no quadro, para que você possa obtê-los uma vez e armazená-los em cache durante o tempo de vida da origem.  Os índices são fornecidos na ordem de enrolamento no sentido horário.

O código a seguir gira um std:: thread desanexado para criar o observador de malha e extrai o buffer de índice quando o observador de malha está disponível.  Ele começa com uma variável chamada *CurrentState*, que é uma instância de [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) que representa uma mão controlada.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas.  Como alternativa, você pode usar a nova funcionalidade de [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) com suporte do C++/WinRT.

Depois de ter um objeto HandMeshObserver, você deve mantê-lo durante a duração em que seu SpatialInteractionSource correspondente está ativo.  Em seguida, cada quadro pode ser solicitado para o último buffer de vértice que representa a mão chamando [GetVertexStateForPose](/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) e passando uma instância [HandPose](/uwp/api/windows.perception.people.handpose) que represente a pose para a qual você deseja vértices.  Cada vértice no buffer tem uma posição e um normal.  Aqui está um exemplo de como obter o conjunto atual de vértices para uma malha à mão.  Como antes, a variável *CurrentState* representa uma instância de [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

Ao contrário das junções de esqueleto, a API de malha à mão não permite que você especifique um sistema de coordenadas para os vértices.  Em vez disso, o [HandMeshVertexState](/uwp/api/windows.perception.people.handmeshvertexstate) especifica o sistema de coordenadas no qual os vértices são fornecidos.  Em seguida, você pode obter uma transformação de malha chamando [TryGetTransformTo](/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) e especificando o sistema de coordenadas desejado.  Você precisará usar essa transformação de malha sempre que trabalhar com os vértices.  Essa abordagem reduz a sobrecarga da CPU, especialmente se você estiver usando apenas a malha para fins de processamento.

## <a name="gaze-and-commit-composite-gestures"></a>Gestos de composição olhar e Commit
para aplicativos que usam o modelo de entrada olhar-and-commit, especialmente em HoloLens (primeira gen), a API de entrada espacial fornece um [SpatialGestureRecognizer](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) opcional que pode ser usado para habilitar gestos compostos criados sobre o evento ' select '.  Ao rotear interações do SpatialInteractionManager para o SpatialGestureRecognizer de um holograma, os aplicativos podem detectar eventos de toque, retenção, manipulação e navegação uniformemente entre dispositivos de entrada de teclado, de voz e espaciais, sem a necessidade de lidar manualmente com os pressionamentos e as versões.

SpatialGestureRecognizer faz apenas a Desambigüidade mínima entre o conjunto de gestos que você solicita. Por exemplo, se você solicitar apenas o toque, o usuário poderá manter seu dedo no mesmo tempo que desejar e um toque ainda ocorrerá. Se você solicitar tocar e segurar, depois de cerca de um segundo de manter o dedo, o gesto será promovido para uma espera e um toque não ocorrerá mais.

Para usar o SpatialGestureRecognizer, manipule o evento [InteractionDetected](/uwp/api/Windows.UI.Input.Spatial.SpatialInteractionManager) do SpatialInteractionManager e pegue o SpatialPointerPose exposto lá. Use o cabeçalho do usuário olhar Ray desta pose para fazer a interseção com os hologramas e as malhas de superfície no ambiente do usuário para determinar o que o usuário está pretendendo a interagir. Em seguida, encaminhe o SpatialInteraction nos argumentos do evento para o SpatialGestureRecognizer do holograma de destino, usando seu método [CaptureInteraction](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) . Isso começa a interpretar essa interação de acordo com o [SpatialGestureSettings](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureSettings) definido no reconhecedor no momento da criação-ou por [TrySetGestureSettings](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer).

em HoloLens (primeira gen), as interações e gestos devem derivar seu direcionamento do olhar de cabeça do usuário, em vez de renderizar ou interagir no local da mão. Depois que uma interação for iniciada, movimentos relativos da mão poderão ser usados para controlar o gesto, assim como com o gesto de manipulação ou de navegação.

## <a name="see-also"></a>Confira também
* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Modelo de entrada de manipulação direta](../../design/direct-manipulation.md)
* [Modelo de entrada de ponto e confirmação](../../design/point-and-commit.md)
* [Olhar e confirmar modelo de entrada](../../design/gaze-and-commit.md)
* [Controladores de movimentos](../../design/motion-controllers.md)