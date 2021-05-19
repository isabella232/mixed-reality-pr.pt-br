---
title: Conscientização espacial
description: descreve o Reconhecimento espacial no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 776033dbb4736ccaa44cdb683c4fce284758a51c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144459"
---
# <a name="spatial-awareness"></a>Conscientização espacial

![Conscientização espacial](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

O sistema de Reconhecimento Espacial fornece reconhecimento ambiental do mundo real em aplicativos de realidade misturada. Quando introduzido no Microsoft HoloLens, o Reconhecimento Espacial forneceu uma coleção de malhas, representando a geometria do ambiente, o que permitia interações atraentes entre hologramas e o mundo real.

> [!NOTE]
> Neste momento, o Kit de Ferramentas de Realidade Misturada não é lançado com algoritmos de Compreensão Espacial, conforme originalmente empacotado no HoloToolkit. A Compreensão Espacial geralmente envolve transformar dados de Malha Espacial para criar dados de Malha simplificados e/ou agrupados, como planos, paredes, pisos, limites etc.

## <a name="getting-started"></a>Introdução

A adição de suporte para o Reconhecimento Espacial requer dois componentes principais do Kit de Ferramentas de Realidade Misturada: o sistema de Reconhecimento Espacial e um provedor de plataforma com suporte.

1. [Habilitar](#enable-the-spatial-awareness-system) o sistema de Reconhecimento Espacial
2. [Registrar](#register-observers) e [configurar](configuring-spatial-awareness-mesh-observer.md) um ou mais observadores espaciais para fornecer dados de malha
3. [Criar e implantar em](#build-and-deploy) uma plataforma que dá suporte ao Reconhecimento Espacial

### <a name="enable-the-spatial-awareness-system"></a>Habilitar o sistema de reconhecimento espacial

O sistema de Reconhecimento Espacial é gerenciado pelo objeto MixedRealityToolkit (ou outro componente [do registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) serviços). Siga as etapas abaixo para habilitar ou desabilitar o sistema *de Reconhecimento Espacial* no perfil *MixedRealityToolkit.*

O Kit de Ferramentas de Realidade Misturada é lançado com alguns perfis pré-configurados padrão. Alguns deles têm o sistema de Reconhecimento Espacial habilitado ou desabilitado por padrão. A intenção dessa pré-configuração, especialmente para quando desabilitada, é evitar a sobrecarga visual de calcular e renderizar as malhas.

| Perfil | Sistema habilitado por padrão |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Ativos/MRTK/SDK/Perfis/HoloLens1) | Falso |
| `DefaultHoloLens2ConfigurationProfile` (Ativos/MRTK/SDK/Perfis/HoloLens2) | Falso |
| `DefaultMixedRealityToolkitConfigurationProfile` (Ativos/MRTK/SDK/Perfis) | True |

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena para abrir no Painel inspetor.

    ![MRTK hierarquia de cena configurada](../images/MRTK_ConfiguredHierarchy.png)

1. Navegue até a seção *sistema de conscientização espacial* e marque *habilitar sistema de conscientização espacial*

    ![Habilitar reconhecimento espacial](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Selecione o tipo de implementação do sistema de conscientização espacial desejado. O [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) é o padrão fornecido.

    ![Selecione a implementação do sistema de conscientização espacial](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Registrar observadores

Os serviços no kit de ferramentas de realidade misturada podem ter [provedor de dados serviços](../../architecture/systems-extensions-providers.md) que complementam o serviço principal com dados específicos da plataforma e controles de implementação. Um exemplo disso é o sistema de entrada de realidade misturada que tem [vários provedores de dados](../input/input-providers.md) para obter o controlador e outras informações de entrada relacionadas de várias APIs específicas da plataforma.

O sistema de conscientização espacial é semelhante nos provedores de dados que fornecem o sistema com dados de malha sobre o mundo real. O perfil de conscientização espacial deve ter pelo menos um observador espacial registrado. Os observadores espaciais geralmente são componentes específicos da plataforma que atuam como o provedor para identificando vários tipos de dados de malha de um ponto de extremidade específico da plataforma (ou seja, HoloLens).

1. Abrir ou expandir o *perfil do sistema de conscientização espacial*

    ![Perfil do sistema de conscientização espacial](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Clique no botão *"Adicionar observador espacial"*
1. Selecione o *tipo de implementação de observador espacial* desejado

    ![Selecionar a implementação do observador espacial](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Modifique as propriedades de configuração no observador](configuring-spatial-awareness-mesh-observer.md) conforme necessário

> [!NOTE]
> Os usuários do `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles) terão o sistema de conscientização espacial pré-configurado para a plataforma de realidade mista do Windows que usa a [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe.

### <a name="build-and-deploy"></a>Criar e implantar

Depois que o sistema de conscientização espacial é configurado com os observadores desejados, o projeto pode ser compilado e implantado na plataforma de destino.

> [!IMPORTANT]
> Se estiver direcionando para a plataforma de realidade mista do Windows (ex: HoloLens), é importante garantir que o [recurso de percepção espacial](/windows/mixed-reality/spatial-mapping-in-unity) esteja habilitado para usar o sistema de conscientização espacial no dispositivo.

> [!WARNING]
> Algumas plataformas, incluindo o Microsoft HoloLens, oferecem suporte para a execução remota de dentro do Unity. Esse recurso permite desenvolvimento e testes rápidos sem a necessidade de criar e implantar a etapa. Certifique-se de fazer o teste de aceitação final usando uma versão compilada e implantada do aplicativo, em execução no hardware e na plataforma de destino.

## <a name="next-steps"></a>Próximas etapas

Depois de seguir os procedimentos acima para habilitar o sistema de conscientização espacial, o sistema pode ser configurado e controlado mais detalhadamente.

Informações para configurar os observadores no Inspetor:

- [Configurando observadores para o uso do dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configurando observadores para uso no editor](spatial-object-mesh-observer.md)

Informações para controlar e estender os observadores por meio de código:

- [Configurando observadores por meio de código](usage-guide.md)
- [Criando um observador personalizado](create-data-provider.md)

## <a name="see-also"></a>Confira também

- [Documentação da API de conscientização espacial](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Visão geral do mapeamento espacial WMR](/windows/mixed-reality/spatial-mapping)
- [Mapeamento espacial no Unity WMR](/windows/mixed-reality/spatial-mapping-in-unity)