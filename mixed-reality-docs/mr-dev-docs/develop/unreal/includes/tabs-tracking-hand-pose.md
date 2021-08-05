---
ms.openlocfilehash: ec1246085989b4b157504e9b8551694d6116e6f08789fa669200e5425ef75cc6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187182"
---
# <a name="426"></a>[4.26](#tab/426)

A hierarquia é descrita `EHandKeypoint` por enum:

![Imagem das opções de impressão de ponto de tecla de mão](../images/hand-keypoint-bp.png)

Você pode obter todos esses dados das mãos de um usuário usando a **função Obter Dados do Controlador de** Movimento. Essa função retorna uma **estrutura XRMotionControllerData.** Abaixo está um script de blueprint de exemplo que analisado a estrutura XRMotionControllerData para obter localizações conjuntas de mão e desenha um sistema de coordenadas de depuração no local de cada junção.

![Blueprint da função get gaze data conectado à função de rastreamento de linha por canal](../images/unreal-hand-tracking-img-03.png)

É importante verificar se a estrutura é válida e se ela é uma mão. Caso contrário, você poderá obter um comportamento indefinido no acesso a posições, rotações e matrizes de rádio.

# <a name="425"></a>[4.25](#tab/425)

A `EWMRHandKeypoint` enum descreve a hierarquia de hierarquia da mão. Você pode encontrar cada ponto de chave de mão listado em seus Blueprints:

![Bp do ponto de chave de mão](../images/hand-keypoint-bp.png)

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

Você pode encontrar os valores numéricos para cada caso de enum no [Windows. Tabela Perception.People.HandJointKind.](/uwp/api/windows.perception.people.handjointkind)

### <a name="supporting-hand-tracking"></a>Suporte ao acompanhamento de mão

Você pode usar o acompanhamento de mão em Blueprints adicionando **Suporte ao acompanhamento de mão** do controle de mão **> Windows Mixed Reality**:

![BP de acompanhamento de mão](../images/unreal/hand-tracking-bp.png)

Essa função retornará se o controle de mão tiver suporte no dispositivo e se o controle de `true` `false` mão não estiver disponível.

![Dá suporte à BP de acompanhamento de mão](../images/unreal/supports-hand-tracking-bp.png)

C++:

Inclua `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Obter acompanhamento de mão

Você pode usar **GetHandJointTransform** para retornar dados espaciais da mão. Os dados atualiza cada quadro, mas se você estiver dentro de um quadro, os valores retornados serão armazenados em cache. Não é recomendável ter uma lógica pesada nessa função por motivos de desempenho.

![Obter transformação conjunta de mão](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Aqui está um detalhamento dos parâmetros de função de GetHandJointTransform:

* **Mão** – podem ser os usuários à esquerda ou à direita.
* **Ponto de** chave – o ponto da mão.
* **Transformação** – coordenadas e orientação da base do 11. Você pode solicitar a base do próximo agente para obter os dados de transformação para o final de um dia. Um tipo especial fornece o fim de sua vida.
* **Raio— raio da base do pau.
* **Valor de Retorno – true se o quadro for rastreado, false se o valor não for rastreado.