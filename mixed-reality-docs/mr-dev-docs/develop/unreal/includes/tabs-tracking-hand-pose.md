---
ms.openlocfilehash: c5a13798ca6a73f1a6410abe310c2166b67f4626
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717871"
---
# <a name="426"></a>[4.26](#tab/426)

A hierarquia é descrita por `EHandKeypoint` enum:

![Imagem de opções do Bluprint keypoint](../images/hand-keypoint-bp.png)

Você pode obter todos esses dados de uma mão do usuário usando a função **obter dados do controlador de movimento** . Essa função retorna uma estrutura **XRMotionControllerData** . Veja abaixo um exemplo de script de Blueprint que analisa a estrutura XRMotionControllerData para obter locais conjuntos em conjunto e desenha um sistema de coordenadas de depuração em cada local de cada conjunto.

![Plano gráfico da função obter dados olhar conectados ao rastreamento de linha por função de canal](../images/unreal-hand-tracking-img-03.png)

É importante verificar se a estrutura é válida e se ela é uma mão. Caso contrário, você pode obter um comportamento indefinido no acesso a posições, rotações e matrizes de raios.

# <a name="425"></a>[4.25](#tab/425)

A `EWMRHandKeypoint` Enumeração descreve a hierarquia do Bone da mão. Você pode encontrar cada ponto de extremidade à mão listado em seus planos gráficos:

![Mão keypoint BP](../images/hand-keypoint-bp.png)

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

Você pode encontrar os valores numéricos para cada caso de enum na tabela [Windows. percepção. People. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .

### <a name="supporting-hand-tracking"></a>Acompanhamento de suporte à mão

Você pode usar o rastreamento manual em plantas adicionando **suporte ao rastreamento** à mão **> realidade mista do Windows**:

![Controle à mão BP](../images/unreal/hand-tracking-bp.png)

Essa função retornará `true` se o controle à mão tiver suporte no dispositivo e `false` se o rastreamento à mão não estiver disponível.

![Dá suporte ao controle à mão BP](../images/unreal/supports-hand-tracking-bp.png)

C++:

Inclua `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Obtendo controle à mão

Você pode usar **GetHandJointTransform** para retornar dados espaciais da mão. Os dados são atualizados a cada quadro, mas se você estiver dentro de um quadro, os valores retornados serão armazenados em cache. Não é recomendável ter muita lógica nessa função por motivos de desempenho.

![Obter transformação conjunta de entrega](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Aqui está uma análise dos parâmetros de função do GetHandJointTransform:

* A **mão** – pode ser os usuários à esquerda ou à direita.
* **Ponto de extremidade** – o Bone da mão.
* **Transformação** – coordenadas e orientação da base do Bone. Você pode solicitar a base do próximo Bone para obter os dados de transformação para o final de um Bone. Um Bone de dica especial dá ao fim do distal.
* * * RADIUS — raio da base do Bone.
* * * Valor de retorno — true se o Bone for rastreado neste quadro, false se o Bone não for acompanhado.

