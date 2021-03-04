---
title: Acompanhamento da mão no Unreal
description: Saiba como usar a entrada de rastreamento manual, a pose, as malhas à mão e as animações de link ao vivo em aplicativos inreais de realidade misturada.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, acompanhamento manual, inreal, Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade do Windows misturada, headset de realidade virtual
ms.openlocfilehash: ea4ba3ad5905e899eae474e4d571585fef77c0c2
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117650"
---
# <a name="hand-tracking-in-unreal"></a>Acompanhamento da mão no Unreal

O sistema de acompanhamento manual usa Palms e dedos de uma pessoa como entrada. Dados na posição e na rotação de cada dedo, todo o Palm e gestos de mão estão disponíveis. A partir do inreal 4,26, o rastreamento manual é baseado no plug-in HeadMountedDisplay inreal e usa uma API comum em todas as plataformas e dispositivos XR. A funcionalidade é a mesma para sistemas OpenXR e realidade mista do Windows.

## <a name="hand-pose"></a>Pose de mão

A pose de mão permite que você controle e use as mãos e os dedos de seus usuários como entrada, que podem ser acessados em planos gráficos e em C++. A API inreal envia os dados como um sistema de coordenadas, com tiques sincronizados com o mecanismo inreal.

![Esqueleto da mão](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Animação do link ao vivo à mão

As poses de mão são expostas à animação usando o [plug-in de vínculo dinâmico](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Se a realidade mista do Windows e os plug-ins do Live link estiverem habilitados:
1. Selecione **janela > link ao vivo** para abrir a janela do editor de link dinâmico.
2. Selecionar **origem** e habilitar a **fonte de acompanhamento do Windows Mixed Reality**

![Origem do link dinâmico](images/unreal/live-link-source.png)

Depois de habilitar a origem e abrir um ativo de animação, expanda a seção **animação** na guia **Visualizar cena** também para ver as opções adicionais.

![Animação de link ao vivo](images/unreal/live-link-animation.png)

A hierarquia de animação da mão é a mesma do `EWMRHandKeypoint` . A animação pode ser redirecionada usando **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:

![Animação de link ao vivo 2](images/unreal/live-link-animation2.png)

Ele também pode ser subclasse no editor:

![Remapeamento de link dinâmico](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Malha à mão

### <a name="hand-mesh-as-a-tracked-geometry"></a>Malha à mão como uma geometria rastreada

> [!IMPORTANT]
> A obtenção de malhas à mão como uma geometria rastreada no OpenXR exige que você chame **definir a malha de uso** com a geometria de **acompanhamento habilitada**.

Para habilitar esse modo, você deve chamar **set use mesh** com a **geometria de acompanhamento habilitada**:

![Plano gráfico de início de evento de execução conectado para definir a função de malha manual de uso com o modo de geometria de rastreamento habilitado](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> Não é possível habilitar ambos os modos ao mesmo tempo. Se você habilitar um, o outro será desabilitado automaticamente.

### <a name="accessing-hand-mesh-data"></a>Acessando dados de malha de mão

![Malha à mão](images/unreal/hand-mesh.png)

Antes de poder acessar os dados da malha, você precisará:
- Selecione o ativo do **ARSessionConfig** , expanda as configurações do **ar->** configurações de mapeamento do mundo e marque **gerar dados de malha da geometria rastreada**.

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

### <a name="hand-mesh-visualization-in-openxr"></a>Visualização de malha à mão em OpenXR

A maneira recomendada de visualizar a malha à mão é usar o plug-in XRVisualization do Epic junto com o [plug-in OpenXR da Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal). 

Em seguida, no editor do Blueprint, você deve usar a função de **malha de uso manual** do [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) com o **XRVisualization habilitado** como um parâmetro:

![Plano gráfico do evento de início de execução conectado para definir a função de malha manual de uso com o modo xrvisualization habilitado](images/unreal-hand-tracking-img-05.png)

Para gerenciar o processo de renderização, você deve usar o **controlador de movimento de renderização** de XRVisualization:

![Plano gráfico da função obter dados do controlador de movimento conectado à função renderizar o controlador de movimento](images/unreal-hand-tracking-img-06.png)

O resultado :

![Imagem da mão digital sobreposta em uma mão humana real](images/unreal-hand-tracking-img-07.png) 

Se precisar de algo mais complicado, como desenhar uma malha à mão com um sombreador personalizado, você precisará obter as malhas como uma geometria rastreada. 

## <a name="hand-rays"></a>Raios de mão

A obtenção de entrega manual funciona para as interações próximas, como a captura de objetos ou o pressionamento de botões. No entanto, às vezes você precisa trabalhar com hologramas que estão longe de seus usuários. Isso pode ser feito com raios de mão, que podem ser usados como dispositivos apontadores em C++ e em planos gráficos. Você pode desenhar um raio a partir de sua mão até um ponto distante e, com alguma ajuda de rastreamento de Ray não real, selecionar um holograma que, de outra forma, estaria fora do alcance. 

> [!IMPORTANT]
> Como todos os resultados da função alteram todos os quadros, todos eles se tornaram chamáveis. Para obter mais informações sobre funções puras e impuras ou que podem ser chamadas, consulte o GUID do usuário do Blueprint em [funções](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Gestos

O HoloLens 2 rastreia gestos espaciais, o que significa que você pode capturar esses gestos como entrada. O rastreamento de gestos é baseado em um modelo de assinatura. Você deve usar a função "configurar gestos" para informar ao dispositivo quais gestos você deseja rastrear.  Você pode encontrar mais detalhes sobre gestos são o documento de [uso básico do HoloLens 2](/hololens/hololens2-basic-usage) .

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se está seguindo o percurso de desenvolvimento do Unreal que estabelecemos, você está no meio da exploração dos principais blocos de construção do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Âncoras Espaciais locais](unreal-spatial-anchors.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Câmera do HoloLens](unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.