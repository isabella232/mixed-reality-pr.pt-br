---
title: Perfis
description: Perfis de documentação no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, perfis,
ms.openlocfilehash: b3ba5aa9ac08dcfe0eecdb479db075b39b43a0e376239822432df872b0775d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225648"
---
# <a name="profiles"></a>Perfis

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

Uma das principais formas de configuração do MRTK é por meio dos perfis disponíveis no pacote Foundation. O objeto [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) principal em uma cena terá o perfil ativo, que é um ScriptableObject. O perfil de configuração MRTK de nível superior contém dados de subperfil para cada núcleo dos principais sistemas de núcleo, cada um deles projetado para configurar o comportamento dos subsistemas correspondentes. Além disso, esses subperfis também são ScriptableObjects e podem conter referências a outros objetos de perfil um nível abaixo deles. Há essencialmente uma árvore inteira de perfis conectados que compõem as informações de configuração de inicialização dos subsistemas e recursos do MRTK.

Por exemplo, o comportamento do sistema de entrada é regido por um perfil de sistema de entrada, como o `DefaultMixedRealityInputSystemProfile` (ativos/MRTK/SDK/perfis).

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>Inspetor de perfil</sup>

## <a name="background"></a>Tela de fundo

Os perfis se destinam principalmente a dar suporte a cenários específicos em vários dispositivos, que são manipulados por meio dos provedores de dados. Dessa forma, um aplicativo pode ser projetado da maneira mais independente possível do dispositivo e permitir que o MRTK e os provedores de dados do perfil manipulem o suporte de multiplataforma.

Também há perfis criados com base nos recursos de entrada de dispositivos específicos, como o perfil do HoloLens 1 que usa como padrão as interações de estilo GGV.

## <a name="xr-sdk"></a>SDK do XR

::: moniker range=">= mrtkunity-2021-05"
Use qualquer um dos perfis de MRTK padrão, que são todos configurados nos pipelines XR do Unity. Os "DefaultOpenXRConfigurationProfile" e "DefaultXRSDKConfigurationProfile" anteriores agora estão rotulados como obsoletos.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Atualmente, há dois perfis fornecidos para o SDK do XR, `DefaultXRSDKConfigurationProfile` e `DefaultHoloLens2XRSDKConfigurationProfile`. Como resultado, nem todas as cenas de exemplo têm suporte total devido a configurações específicas de cenário e cena. Os exemplos que usam `DefaultMixedRealityToolkitConfigurationProfile` e `DefaultHoloLens2ConfigurationProfile` _podem_ ser trocados pelos seus perfis do SDK do XR correspondentes. Se você estiver usando o OpenXR com o SDK do XR, use o `DefaultOpenXRConfigurationProfile`.

O trabalho adicional está sendo retirado para facilitar a configuração e dar suporte a todas as cenas de exemplo, permitindo que o XR herdado e o SDK do XR sejam configurados lado a lado. Confira o problema [nº 9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) para acompanhamento.
::: moniker-end

Confira [Configuração do MRTK para o pipeline do SDK do XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) para obter mais informações sobre como converter perfis entre o XR herdado e o SDK do XR.

## <a name="default-profile"></a>Perfil padrão

O MRTK fornece um conjunto de perfis padrão, que abrangem a maioria das plataformas e cenários para os quais o MRTK dá suporte. Por exemplo, quando você seleciona o `DefaultMixedRealityToolkitConfigurationProfile` (ativos/MRTK/SDK/perfis), poderá experimentar cenários em VR (OpenVR, WMR) e HoloLens (1 e 2).

Observe que, como esse é um perfil de uso geral, ele não é otimizado para nenhum caso de uso específico. Se você quiser ter mais configurações de alto desempenho/específicas que são melhores em outras plataformas, confira os outros perfis abaixo, que são ligeiramente ajustados para serem melhores nas respectivas plataformas.

## <a name="hololens-2-profile"></a>Perfil do HoloLens 2

O MRTK também fornece um perfil padrão que é otimizado para implantação e teste no HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (ativos/MRTK/SDK/perfis/HoloLens2).

Quando vir a solicitação para escolher um perfil para o objeto MixedRealityToolkit, use esse perfil em vez do perfil selecionado padrão.

As principais diferenças entre o perfil HoloLens2 e o perfil padrão são:

Recursos **desabilitados**:

- [Sistema de limite](../boundary/boundary-system-getting-started.md)
- [Sistema de teletransporte](../teleport-system/teleport-system.md)
- [Sistema de conscientização espacial](../spatial-awareness/spatial-awareness-getting-started.md)
- [Visualização de malha à mão](../input/hand-tracking.md) (devido à sobrecarga de desempenho)

Sistemas **habilitados**:

- O [provedor de acompanhamento ocular](../input/eye-tracking/eye-tracking-main.md)
- Simulação de entrada a olho

As configurações de perfil da câmera são definidas para corresponder, de maneira que a qualidade do editor e do player sejam as mesmas. Isso é diferente do perfil de câmera padrão em que os monitores opacos são definidos com uma qualidade mais alta. Essa alteração significa que a qualidade no editor será menor, o que corresponde mais de acordo com o que será renderizado no dispositivo.

> [!NOTE]
> O sistema de Conscientização Espacial é desativado por padrão com base nos comentários do cliente. É uma visualização interessante para ver inicialmente, mas normalmente é desativada para evitar a distração visual e o impacto adicional de desempenho ao deixá-lo ativado. O sistema pode ser habilitado novamente seguindo as [instruções aqui](../spatial-awareness/spatial-awareness-getting-started.md).
