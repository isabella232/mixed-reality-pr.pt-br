---
title: Acompanhamento da mão no Unreal
description: Saiba como usar entradas de acompanhamento de mão, pose, malhas de mão e animações de link ao vivo em aplicativos de realidade misturada do Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, acompanhamento de mão, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 4c3b86c842fc875ebedbdf2527bf962fd8afd4d19cef90d168293cc85b664f70
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187124"
---
# <a name="hand-tracking-in-unreal"></a>Acompanhamento da mão no Unreal

O sistema de acompanhamento de mão usa as mãos e as mãos de uma pessoa como entrada. Dados sobre a posição e a rotação de cada dedo, a mão inteira e gestos de mão estão disponíveis. A partir do Unreal 4.26, o acompanhamento de mão é baseado no plug-in HeadMountedDisplay do Unreal e usa uma API comum em todas as plataformas e dispositivos XR. A funcionalidade é a mesma para sistemas Windows Mixed Reality e OpenXR.

## <a name="hand-pose"></a>Pose da mão

A pose da mão permite que você acompanhe e use as mãos e os dedos de seus usuários como entrada, que podem ser acessadas em Blueprints e C++. A API do Unreal envia os dados como um sistema de coordenadas, com tiques sincronizados com o Unreal Engine.

![Imagem de esqueleto da mão com o esqueleto da mão sobreposição ](images/hand-tracking-img-02.png)
 ![ de junções](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Animação de link ao vivo da mão

As poses de mão são expostas à Animação usando o [plug-in link ao vivo](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Se os plug-ins Windows Mixed Reality e Live Link estão habilitados:
1. Selecione **Janela > Link ao Vivo** para abrir a janela do editor do Link Ao Vivo.
2. Selecione **Origem** e habilita **Windows Mixed Reality De origem de Acompanhamento de Mão**

![Origem do Link Ao Vivo](images/unreal/live-link-source.png)

Depois de habilitar a origem  e abrir  um ativo de animação, expanda a seção Animação na guia Cena de Visualização também veja opções adicionais.

![Animação de link ao vivo](images/unreal/live-link-animation.png)

A hierarquia de animação de mão é a mesma que em `EWMRHandKeypoint` . A animação pode ser retargetada **usando WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:

![Animação de link ao vivo 2](images/unreal/live-link-animation2.png)

Ele também pode ser subclasse no editor:

![Remapa de Link Ao Vivo](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Malha manual

### <a name="hand-mesh-as-a-tracked-geometry"></a>Malha de mão como uma geometria rastreada

> [!IMPORTANT]
> Obter malhas de mão como uma geometria rastreada no OpenXR exige que você chame Set **Use Hand Mesh** with **Enabled Tracking Geometry**.

Para habilitar esse modo, você deve chamar **Definir Usar Malha de Mão** com Geometria de Acompanhamento **Habilitado**:

![Blueprint do evento begin play connected to set use hand mesh function with enabled tracking geometry mode](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> Não é possível que ambos os modos sejam habilitados ao mesmo tempo. Se você habilitar um, o outro será desabilitado automaticamente.

### <a name="accessing-hand-mesh-data"></a>Acessando dados de malha manual

![Malha manual](images/unreal/hand-mesh.png)

Antes de acessar dados de malha manual, você precisará:
- Selecione o ativo **ARSessionConfig,** expanda as configurações de Mapeamento Do Mundo Configurações **->** AR e marque Gerar Dados de Malha da **Geometria Rastreada.**

Abaixo estão os parâmetros de malha padrão:

1.  Usar dados de malha para oclusão
2.  Gerar colisão para dados de malha
3.  Gerar malha de nav para dados de malha
4.  Renderizar dados de malha no Wireframe – parâmetro de depuração que mostra a malha gerada

Esses valores de parâmetro são usados como os padrões de malha de mapeamento espacial e malha manual. Você pode alterá-los a qualquer momento em Blueprints ou código para qualquer malha.

### <a name="c-api-reference"></a>Referência da API do C++
Use `EEARObjectClassification` para localizar valores de malha manual em todos os objetos rastreáveis.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

Os delegados a seguir são chamados quando o sistema detecta qualquer objeto rastreável, incluindo uma malha manual.

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

Certifique-se de que os manipuladores delegados sigam a assinatura da função abaixo:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Você pode acessar dados de malha por meio do  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>Referência da API de Blueprint

Para trabalhar com malhas de mão em blueprints:
1. Adicionar um **componente ARTrackableNotify** a um ator de blueprint

![Notificação ARTrackable](images/unreal/ar-trackable-notify.png)

2. Vá para o **painel Detalhes** e expanda a **seção** Eventos.

![ArTrackable Notify 2](images/unreal/ar-trackable-notify2.png)

3. Substituir Em Adicionar/Atualizar/Remover Geometria Rastreada com os seguintes nós no seu evento Graph:

![No ARTrackable Notify](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>Visualização de malha manual no OpenXR

A maneira recomendada de visualizar a malha manual é usar o plug-in XRVisualization da Epic junto com o plug-in [microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal). 

Em seguida, no editor de blueprint, você deve usar a função **Set Use Hand Mesh** do [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) com **XRVisualization** habilitado como um parâmetro:

![Blueprint do evento begin play connected to set use hand mesh function with enabled xrvisualization mode](images/unreal-hand-tracking-img-05.png)

Para gerenciar o processo de renderização, você deve usar **Renderizar o Controlador de Movimento** do XRVisualization:

![Blueprint da função obter dados do controlador de movimento conectado para renderizar a função do controlador de movimento](images/unreal-hand-tracking-img-06.png)

O resultado :

![Imagem da mão digital sobrepassada em uma mão humana real](images/unreal-hand-tracking-img-07.png) 

Se precisar de algo mais complicado, como desenhar uma malha manual com um sombreador personalizado, você precisará obter as malhas como uma geometria rastreada. 

## <a name="hand-rays"></a>Raios de mão

A pose da mão funciona para interações próximas, como segurar objetos ou pressionar botões. No entanto, às vezes você precisa trabalhar com hologramas que estão longe de seus usuários. Isso pode ser feito com raios de mão, que podem ser usados como dispositivos que apontam para C++ e Blueprints. Você pode desenhar um raio de sua mão para um ponto distante e, com alguma ajuda do rastreamento de raio do Unreal, selecionar um holograma que, de outra forma, estaria fora de alcance. 

> [!IMPORTANT]
> Como todos os resultados da função mudam a cada quadro, todos eles são chamado. Para obter mais informações sobre funções puras e impure ou que podem ser chamada, consulte o Guid do usuário do Blueprint [nas funções](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Gestos

O HoloLens 2 rastreia gestos espaciais, o que significa que você pode capturar esses gestos como entrada. O acompanhamento de gestos é baseado em um modelo de assinatura. Você deve usar a função "Configurar Gestos" para dizer ao dispositivo quais gestos você deseja acompanhar.  Você pode encontrar mais detalhes sobre gestos no documento [HoloLens 2 Uso](/hololens/hololens2-basic-usage) Básico.

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se está seguindo o percurso de desenvolvimento do Unreal que estabelecemos, você está no meio da exploração dos principais blocos de construção do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Âncoras Espaciais locais](unreal-spatial-anchors.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Câmera do HoloLens](unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.