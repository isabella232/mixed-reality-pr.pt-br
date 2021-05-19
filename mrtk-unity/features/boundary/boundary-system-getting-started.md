---
title: Introdução ao sistema de marco de delimitação
description: Página de aterrissagem do sistema de limites no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Sistema de Limites,
ms.openlocfilehash: 2858b770fb49a44d1e2d704e8d3a81affe74d272
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144733"
---
# <a name="boundary-system"></a>Sistema de limites

O sistema de limites fornece suporte para visualizar componentes de limite da Realidade Virtual em aplicativos de realidade misturada. Os limites definem a área na qual os usuários podem se mover com segurança enquanto usam um headset de VR. Os limites são um componente importante de uma experiência de realidade misturada para ajudar os usuários a evitar obstáculos não vistos ao usar um headset de VR.

Muitas plataformas de Realidade Virtual fornecem uma exibição automática, por exemplo, um contorno em branco sobreposto no mundo virtual à medida que o usuário ou seu controlador se aproxima do limite. O Sistema de Limites do Kit de Ferramentas de Realidade Misturada estende esse recurso para habilitar a exibição de um contorno da área rastreada, um plano de chão e outros recursos que podem ser usados para fornecer informações adicionais aos usuários.

## <a name="getting-started"></a>Introdução

A adição de suporte para limites requer dois componentes principais do Kit de Ferramentas de Realidade Misturada: o Sistema de Limites e uma plataforma de Realidade Virtual configurada com um limite.

1. [Habilitar](#enable-boundary-system) o sistema de limites
2. [Configurar](#configure-boundary-visualization) a visualização de limite
3. [Criar e implantar](#build-and-deploy) em uma plataforma de VR com um limite configurado

## <a name="enable-boundary-system"></a>Habilitar o sistema de limites

O Sistema de Limites é gerenciado pelo objeto MixedRealityToolkit (ou outro componente [do registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) serviços).

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Navegue pelo painel Inspetor até a seção Sistema de Limites e marque Habilitar

    ![Habilitar o sistema de limites](../images/boundary/MRTKConfig_Boundary.png)

1. Selecione a implementação do sistema de limite. A implementação de classe padrão fornecida pelo MRTK é o [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![Selecione a implementação do sistema de limite](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> Toda a implementação do sistema de limite deve estender o [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>Configurar a visualização de limite

O [sistema de limite usa um perfil de configuração](configuring-boundary-visualization.md) para especificar quais componentes de limite devem ser exibidos e para configurar sua aparência.

![Opções de visualização de limite](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> Os usuários do perfil padrão, `DefaultMixedRealityBoundaryVisualizationProfile` (assets/MRTK/SDK/Profiles) terão o sistema de limite pré-configurado para exibir um plano de chão, a área de reprodução e a área rastreada.

## <a name="build-and-deploy"></a>Criar e implantar

Depois que o sistema de limite é configurado com as opções de visualização desejadas, o projeto pode ser compilado implantado na plataforma de destino.

> [!NOTE]
> O modo de reprodução do Unity permite a visualização no editor do limite configurado. Esse recurso permite desenvolvimento e testes rápidos sem a necessidade de criar e implantar a etapa. Certifique-se de fazer o teste de aceitação final usando uma versão compilada e implantada do aplicativo, em execução no hardware e na plataforma de destino.

## <a name="accessing-boundary-system-via-code"></a>Acessando o sistema de limite por meio de código

Se habilitado e configurado, o sistema de limite pode ser acessado por meio da classe auxiliar estático CoreServices. A referência pode ser usada para alterar dinamicamente os parâmetros de limite e acessar o GameObjects relacionado gerenciado pelo sistema.

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>Confira também

- [Documentação da API de limite](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Configurando a visualização de limite](configuring-boundary-visualization.md)
