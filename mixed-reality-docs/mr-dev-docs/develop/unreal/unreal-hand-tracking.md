---
title: Acompanhamento da mão no Unreal
description: Explica como usar o rastreamento manual em não real
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, acompanhamento manual, inreal, Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91674855"
---
# <a name="hand-tracking-in-unreal"></a>Acompanhamento da mão no Unreal

## <a name="overview"></a>Visão geral

O sistema de acompanhamento manual usa Palms e dedos de uma pessoa como entrada. Você pode obter a posição e a rotação de cada dedo, todo o Palm e gestos de mão para usar em seu código. 

## <a name="hand-pose"></a>Pose de mão

A pose de mão permite que você acompanhe as mãos e os dedos do usuário ativo e use-os como entrada, que pode ser acessado por meio de plantas e do C++. Você pode encontrar mais detalhes técnicos na API inreal do [Windows. percepção. People. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) . A API inreal envia os dados como um sistema de coordenadas, com tiques sincronizados com o mecanismo inreal.

### <a name="understanding-the-bone-hierarchy"></a>Compreendendo a hierarquia do Bone

A `EWMRHandKeypoint` Enumeração descreve a hierarquia do Bone da mão. Você pode encontrar cada ponto de extremidade à mão listado em seus planos gráficos:

![Mão keypoint BP](images/hand-keypoint-bp.png)

A enumeração C++ completa está listada abaixo:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

Você pode encontrar os valores numéricos para cada caso de enum na tabela [Windows. percepção. People. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) . Todo o layout de pose de mão com casos de enumeração correspondentes é mostrado na imagem abaixo:

![Esqueleto da mão](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>Acompanhamento de suporte à mão

Você pode usar o rastreamento manual em plantas adicionando **suporte ao rastreamento** à mão **> realidade mista do Windows** :

![Controle à mão BP](images/unreal/hand-tracking-bp.png)

Essa função retornará `true` se o controle à mão tiver suporte no dispositivo e `false` se o rastreamento à mão não estiver disponível.

![Dá suporte ao controle à mão BP](images/unreal/supports-hand-tracking-bp.png)

C++: 

Inclua `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Obtendo controle à mão
Você pode usar **GetHandJointTransform** para retornar dados espaciais da mão. Os dados são atualizados a cada quadro, mas se você estiver dentro de um quadro, os valores retornados serão armazenados em cache. Não é recomendável ter muita lógica nessa função por motivos de desempenho. 

![Obter transformação conjunta de entrega](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Divisão de parâmetro de função:

* **Mão** – um é o lado esquerdo ou direito do usuário
* **Ponto de extremidade** – o Bone da mão. 
* **Transformação** – coordenadas e orientação da base do Bone. Você pode solicitar a base do próximo Bone para obter os dados de transformação para o final de um Bone. Um Bone de dica especial dá ao fim do distal. 
* **RADIUS** — raio da base do Bone.
* **Valor de retorno** — true se o Bone for rastreado neste quadro, false se o Bone não for acompanhado.

## <a name="hand-live-link-animation"></a>Animação do link ao vivo à mão
As poses de mão são expostas à animação usando o [plug-in de vínculo dinâmico](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Se a realidade mista do Windows e os plug-ins do Live link estiverem habilitados: 
1. Selecione **janela > link ao vivo** para abrir a janela do editor de link dinâmico. 
2. Clique em **origem** e habilite a **fonte de acompanhamento do Windows Mixed Reality**

![Origem do link dinâmico](images/unreal/live-link-source.png)
 
Depois de habilitar a origem e abrir um ativo de animação, expanda a seção **animação** na guia **cena de visualização** também para ver as opções adicionais (os detalhes estão na documentação de link dinâmico do inreal-como o plug-in está em beta, o processo pode ser alterado posteriormente).

![Animação de link ao vivo](images/unreal/live-link-animation.png)
 
A hierarquia de animação da mão é a mesma do `EWMRHandKeypoint` . A animação pode ser redirecionada usando **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :

![Animação de link ao vivo 2](images/unreal/live-link-animation2.png)
 
Ele também pode ser subclasse no editor:

![Remapeamento de link dinâmico](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>Acessando dados de malha de mão

![Malha à mão](images/unreal/hand-mesh.png)

Antes de poder acessar os dados da malha, você precisará:
- Selecione o ativo do **ARSessionConfig** , expanda as configurações do **ar->** configurações de mapeamento do mundo e marque **gerar dados de malha da geometria rastreada** . 

Abaixo estão os parâmetros de malha padrão:

1.  Usar dados de malha para oclusão
2.  Gerar colisão para dados de malha
3.  Gerar malha NAV para dados de malha
4.  Renderizar dados de malha em wireframe – parâmetro de depuração que mostra a malha gerada

Esses valores de parâmetro são usados como os padrões de malha de mapeamento espacial e malha de mão. Você pode alterá-los a qualquer momento em plantas ou código para qualquer malha.

### <a name="c-api-reference"></a>Referência da API do C++ 
Use `EEARObjectClassification` para localizar valores de malha do lado em todos os objetos rastreáveis.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

Os delegados a seguir são chamados quando o sistema detecta qualquer objeto rastreável, incluindo uma malha à mão. 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Verifique se os manipuladores delegados seguem a assinatura de função abaixo:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Você pode acessar os dados de malha por meio do  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>Referência de API de Blueprint

Para trabalhar com malhas à mão em plantas:
1. Adicionar um componente **ARTrackableNotify** a um ator do Blueprint

![ARTrackable notificar](images/unreal/ar-trackable-notify.png)
 
2. Vá para o painel de **detalhes** e expanda a seção **eventos** . 

![Notificação ARTrackable 2](images/unreal/ar-trackable-notify2.png)
 
3. Substituir em Adicionar/atualizar/remover geometria rastreada com os seguintes nós em seu grafo de eventos:

![Na notificação do ARTrackable](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Raios de mão

Você pode usar um raio de mão como um dispositivo apontador em C++ e plantas, que expõem a API [Windows. UI. Input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .

É importante mencionar que, como os resultados de todas as funções alteram todos os quadros, todos eles se tornaram chamáveis. Para obter mais informações sobre funções puras e impuras ou que podem ser chamadas, consulte o GUID do usuário do Blueprint em [funções](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

Para usar raios de mão em plantas, pesquise qualquer uma das ações em **HMD de realidade mista do Windows** :

![Raios-mão BP](images/unreal/hand-rays-bp.png)
 
Para acessá-los em C++, inclua na `WindowsMixedRealityFunctionLibrary.h` parte superior do seu arquivo de código de chamada.

### <a name="enum"></a>Enumeração
Você também tem acesso a casos de entrada em **EHMDInputControllerButtons** , que podem ser usados em plantas:

![Botões do controlador de entrada](images/unreal/input-controller-buttons.png)

Para acesso em C++, use a `EHMDInputControllerButtons` classe enum:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

Abaixo está uma análise dos dois casos de enumeração aplicáveis:
* **Select** -o evento de seleção disparado pelo usuário. 
    * O evento pode ser disparado no HoloLens 2 por Air-TAP, olhar e Commit ou dizendo "Select" com a [entrada de voz](unreal-voice-input.md) habilitada. 
* **Segure** -evento de Segure disparado pelo usuário. 
    * Esse evento pode ser disparado no HoloLens 2 fechando os dedos do usuário em um holograma. 

Você pode acessar o status de acompanhamento da malha do seu lado em C++ por meio da `EHMDTrackingStatus` Enumeração mostrada abaixo:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Abaixo está uma análise dos dois casos de enumeração aplicáveis:
* Não **rastreado** – a mão não está visível
* **Acompanhado** – a mão é totalmente controlada

### <a name="struct"></a>Estrutura
A estrutura PointerPoseInfo pode fornecer informações sobre os seguintes dados de mão:
* **Origem** – origem da mão
* **Direção** – direção da mão
* **Up** – vetor de cima à mão
* **Orientação** – o quaternion de orientação 
* **Status de rastreamento** – status de acompanhamento atual

Você pode acessá-lo por meio de plantas, conforme mostrado abaixo:

![Ponteiro de pose de informações BP](images/unreal/pointer-pose-info-bp.png)

Ou com C++:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Funções

Todas as funções listadas abaixo podem ser chamadas em cada quadro, o que permite o monitoramento contínuo. 

1. **Obter** informações de pose de ponteiro retorna informações completas sobre a direção de raio da mão no quadro atual. 

Gráfico

![Obter informações de pose de ponteiro](images/unreal/get-pointer-pose-info.png)

C++: 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **É Segure** retorna true se a mão estiver segurando no quadro atual.

Gráfico

![BP é compreendida](images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. **Is Select pressionado** retorna true se o usuário disparasse SELECT no quadro atual.

Gráfico

![É selecione BP pressionado](images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. O **botão é clicado** retorna true se o evento ou botão for disparado no quadro atual.

Gráfico

![É um botão clicado em BP](images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Obter status de controle do controlador** retorna o status de acompanhamento no quadro atual.

Gráfico

![Obter o status de controle do controlador BP](images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>Gestos

O Hololens 2 pode rastrear gestos espaciais, o que significa que você pode capturar esses gestos como entrada. Você pode encontrar mais detalhes sobre gestos são o documento de [uso básico do HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

Você pode encontrar a função Blueprint na **entrada espacial de realidade mista do Windows** e a função C++ adicionando o `WindowsMixedRealitySpatialInputFunctionLibrary.h` arquivo de código de chamada.

![Gestos de captura](images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumeração
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Gráfico 

![Tipo de gesto](images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Função
Você pode habilitar e desabilitar a captura de gestos com a `CaptureGestures` função. Quando um gesto habilitado aciona eventos de entrada, a função retorna `true` se a captura do gesto foi bem-sucedida e, `false` se houver um erro.

Gráfico

![Gestos de captura BP](images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

Veja a seguir os principais eventos, que você pode encontrar em plantas e C++: ![ principais eventos](images/unreal/key-events.png)

![Principais eventos 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento inreal que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core. A partir daqui, você pode prosseguir para o próximo bloco de construção: 

> [!div class="nextstepaction"]
> [Âncoras Espaciais locais](unreal-spatial-anchors.md)

Ou vá para recursos e APIs da plataforma de realidade misturada:

> [!div class="nextstepaction"]
> [Câmera do HoloLens](unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento inreais](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.