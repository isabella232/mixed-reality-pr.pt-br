---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717422"
---
# <a name="426"></a>[4.26](#tab/426)

Para obter os dados para os raios de mão, você deve usar a função obter dados do controlador de movimento da seção anterior. A estrutura retornada contém dois parâmetros que você pode usar para criar uma **posição** de raio e a **rotação** do AIM. Esses parâmetros formam um raio direcionado pelo cotovelo. Você deve levá-los e encontrar um holograma sendo apontado.

Abaixo está um exemplo de como determinar se um raio de lado atinge um widget e como definir um resultado de ocorrência personalizada:

![Plano gráfico da função obter dados do controlador de movimento](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

Para usar raios de mão em plantas, pesquise qualquer uma das ações em **HMD de realidade mista do Windows**:

![Raios-mão BP](../images/unreal/hand-rays-bp.png)

Para acessá-los em C++, inclua na `WindowsMixedRealityFunctionLibrary.h` parte superior do seu arquivo de código de chamada.

### <a name="enum"></a>Enumeração

Você também tem acesso a casos de entrada em **EHMDInputControllerButtons**, que podem ser usados em plantas:

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

Abaixo está uma análise dos dois casos de enumeração aplicáveis:

* **Select** -o evento de seleção disparado pelo usuário.
    * Disparado no HoloLens 2 por Air-TAP, olhar e Commit ou dizendo "Select" com [entrada de voz](../unreal-voice-input.md) habilitada.
* **Segure** -evento de Segure disparado pelo usuário.
    * Disparado no HoloLens 2 fechando os dedos do usuário em um holograma.

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

Você pode acessar a estrutura PointerPoseInfo por meio de plantas, conforme mostrado abaixo:

![Ponteiro de pose de informações BP](../images/unreal/pointer-pose-info-bp.png)

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

![Obter informações de pose de ponteiro](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **É Segure** retorna true se a mão estiver segurando no quadro atual.

Gráfico

![BP é compreendida](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Is Select pressionado** retorna true se o usuário disparasse SELECT no quadro atual.

Gráfico

![É selecione BP pressionado](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. O **botão é clicado** retorna true se o evento ou botão for disparado no quadro atual.

Gráfico

![É um botão clicado em BP](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Obter status de controle do controlador** retorna o status de acompanhamento no quadro atual.

Gráfico

![Obter o status de controle do controlador BP](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```