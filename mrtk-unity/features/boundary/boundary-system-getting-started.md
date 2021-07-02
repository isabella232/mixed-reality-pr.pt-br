---
title: Visão geral do sistema de limite
description: Página de aterrissagem para o sistema de limite no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, sistema de limites,
ms.openlocfilehash: fd70479e5183e9a7557de5c5a532cc87161be017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177083"
---
# <a name="boundary-system-overview"></a>Visão geral do sistema de limite

O sistema de limite fornece suporte para visualização de componentes de limite da realidade virtual em aplicativos de realidade misturada. Os limites definem a área na qual os usuários podem se movimentar com segurança ao mesmo tempo em que se aproveitam um headset VR. Os limites são um componente importante de uma experiência de realidade misturada para ajudar os usuários a evitar obstáculos não vistos ao utilizar um headset de VR.

Muitas plataformas de realidade virtual fornecem uma exibição automática, por exemplo, uma estrutura de tópicos branco sobreposta no mundo virtual como o usuário ou seu controlador perto do limite. o sistema de limite da realidade mista Toolkit estende esse recurso para permitir a exibição de uma estrutura de tópicos da área controlada, um plano de chão e outros recursos que podem ser usados para fornecer informações adicionais aos usuários.

## <a name="getting-started"></a>Introdução

adicionar suporte para limites requer dois componentes principais da realidade misturada Toolkit: o sistema de limite e uma plataforma de realidade Virtual configurada com um limite.

1. [Habilitar](#enable-boundary-system) o sistema de limite
2. [Configurar](#configure-boundary-visualization) a visualização de limite
3. [Crie e implante](#build-and-deploy) em uma plataforma VR com um limite configurado

## <a name="enable-boundary-system"></a>Habilitar sistema de limite

O sistema de limite é gerenciado pelo objeto MixedRealityToolkit (ou outro componente [registrador de serviço](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).

As etapas a seguir presumem o uso do objeto MixedRealityToolkit. As etapas necessárias para outros registradores de serviço podem ser diferentes.

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena.

    ![MRTK hierarquia de cena configurada](../images/MRTK_ConfiguredHierarchy.png)

1. Navegue pelo painel Inspetor até a seção sistema de limite e marque Habilitar

    ![Habilitar o sistema de limite](../images/boundary/MRTKConfig_Boundary.png)

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
