---
ms.openlocfilehash: fb8b5b509ef83e2a4f9d978dbf0faebbf3e0be1d10d6697f16cfb9366d7a2edb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187183"
---
# <a name="426"></a>[4.26](#tab/426)

Para obter os dados dos raios de mão, você deve usar a função Obter Dados do Controlador de Movimento da seção anterior. A estrutura retornada contém dois parâmetros que você pode usar para criar um raio de mão – Posição **do alvo** e **Rotação de objetivo.** Esses parâmetros formam um raio direcionado pelo seu rosto. Você deve pegar e encontrar um holograma que está sendo apontado.

Veja abaixo um exemplo de como determinar se um raio de mão atinge um Widget e definir um resultado de acerto personalizado:

![Blueprint da função obter dados do controlador de movimento](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

Para usar raios de mão em blueprints, pesquise qualquer uma das ações **em Windows Mixed Reality HMD**:

![Raios de mão BP](../images/unreal/hand-rays-bp.png)

Para acessá-los no C++, `WindowsMixedRealityFunctionLibrary.h` inclua na parte superior do arquivo de código de chamada.

### <a name="enum"></a>Enumeração

Você também tem acesso a casos de entrada **em EHMDInputControllerButtons**, que podem ser usados em Blueprints:

![Botões do controlador de entrada](../images/unreal/input-controller-buttons.png)

Para acesso em C++, use a `EHMDInputControllerButtons` classe enum:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

Veja abaixo um detalhamento dos dois casos de enum aplicáveis:

* **Selecione** – O usuário disparou Selecionar evento.
    * Disparado no HoloLens 2 por toque de ar, olhar e confirmação ou dizendo "Selecionar" com a entrada [de voz](../unreal-voice-input.md) habilitada.
* **Entender** – evento De compreensão disparado pelo usuário.
    * Disparado no HoloLens 2 fechando os dedos do usuário em um holograma.

Você pode acessar o status de acompanhamento da malha manual em C++ por meio `EHMDTrackingStatus` da enum mostrada abaixo:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Veja abaixo um detalhamento dos dois casos de enum aplicáveis:

* **NotTracked** – a mão não está visível
* **Rastreado** – a mão está totalmente controlada

### <a name="struct"></a>Estrutura

O struct PointerPoseInfo pode lhe dar informações sobre os seguintes dados de mão:

* **Origem** – origem da mão
* **Direção** – direção da mão
* **Up** – vetor up da mão
* **Orientação** – quatternion de orientação
* **Status de acompanhamento** – status de acompanhamento atual

Você pode acessar o struct PointerPoseInfo por meio de Blueprints, conforme mostrado abaixo:

![Bp de informações de pose de ponteiro](../images/unreal/pointer-pose-info-bp.png)

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

1. **Obter Informações de Pose do** Ponteiro retorna informações completas sobre a direção do raio de mão no quadro atual.

Modelo:

![Obter informações de pose do ponteiro](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **É Compreendido retornará** true se a mão for a mão no quadro atual.

Modelo:

![Está segurando BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Se Selecionar Pressionado retornará** true se o usuário tiver disparado Selecionar no quadro atual.

Modelo:

![É selecionar BP pressionado](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **O botão Clicado retornará** true se o evento ou o botão for disparado no quadro atual.

Modelo:

![Botão é BP clicado](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Obter Status de Acompanhamento do Controlador** retorna o status de acompanhamento no quadro atual.

Modelo:

![Obter BP do status de acompanhamento do controlador](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```