---
title: Início da conscientização espacial
description: descreve o Reconhecimento espacial no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176709"
---
# <a name="spatial-awareness-getting-started"></a>Início da conscientização espacial

![Conscientização espacial](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

O sistema de Reconhecimento Espacial fornece reconhecimento ambiental do mundo real em aplicativos de realidade misturada. Quando introduzido no Microsoft HoloLens, o Reconhecimento Espacial forneceu uma coleção de malhas, representando a geometria do ambiente, o que permitia interações atraentes entre hologramas e o mundo real.

> [!NOTE]
> Neste momento, a Toolkit realidade misturada não é fornecidas com algoritmos de Compreensão Espacial como originalmente empacotados no HoloToolkit. A Compreensão Espacial geralmente envolve transformar dados de Malha Espacial para criar dados de Malha simplificados e/ou agrupados, como planos, paredes, pisos, limites etc.

## <a name="getting-started"></a>Introdução

A adição de suporte para o Reconhecimento Espacial requer dois componentes principais do Toolkit Realidade Misturada: o sistema de Reconhecimento Espacial e um provedor de plataforma com suporte.

1. [Habilitar](#enable-the-spatial-awareness-system) o sistema de Reconhecimento Espacial
2. [Registrar](#register-observers) e [configurar](configuring-spatial-awareness-mesh-observer.md) um ou mais observadores espaciais para fornecer dados de malha
3. [Criar e implantar em](#build-and-deploy) uma plataforma que dá suporte ao Reconhecimento Espacial

### <a name="enable-the-spatial-awareness-system"></a>Habilitar o sistema de reconhecimento espacial

O sistema de Reconhecimento Espacial é gerenciado pelo objeto MixedRealityToolkit (ou outro componente [do registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) serviços). Siga as etapas abaixo para habilitar ou desabilitar o sistema *de Reconhecimento Espacial* no perfil *MixedRealityToolkit.*

O Toolkit realidade misturada é lançado com alguns perfis pré-configurados padrão. Alguns deles têm o sistema de Reconhecimento Espacial habilitado ou desabilitado por padrão. A intenção dessa pré-configuração, especialmente para quando desabilitada, é evitar a sobrecarga visual de calcular e renderizar as malhas.

| Perfil | Sistema habilitado por padrão |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Ativos/MRTK/SDK/Perfis/HoloLens1) | Falso |
| `DefaultHoloLens2ConfigurationProfile` (Ativos/MRTK/SDK/Perfis/HoloLens2) | Falso |
| `DefaultMixedRealityToolkitConfigurationProfile` (Ativos/MRTK/SDK/Perfis) | True |

1. Selecione o objeto MixedRealityToolkit na hierarquia de cena para abrir no Painel inspetor.

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Navegue até a *seção Sistema de Reconhecimento Espacial* e marque *Habilitar Sistema de Reconhecimento Espacial*

    ![Habilitar o Reconhecimento Espacial](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Selecione o tipo de implementação do sistema de Reconhecimento Espacial desejado. O [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) é o padrão fornecido.

    ![Selecione a implementação do sistema de reconhecimento espacial](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Registrar observadores

Os serviços na plataforma de Toolkit podem ter Provedor de Dados [serviços](../../architecture/systems-extensions-providers.md) que complementam o serviço principal com controles de implementação e dados específicos da plataforma. Um exemplo disso é o Sistema de Entrada de Realidade Misturada que tem vários provedores de dados para obter o controlador e outras informações de entrada relacionadas de várias APIs [específicas](../input/input-providers.md) da plataforma.

O sistema de Reconhecimento Espacial é semelhante, já que os provedores de dados fornecem ao sistema dados de malha sobre o mundo real. O perfil de Reconhecimento Espacial deve ter pelo menos um Observador Espacial registrado. Observadores Espaciais geralmente são componentes específicos da plataforma que atuam como o provedor para a busca de vários tipos de dados de malha de um ponto de extremidade específico da plataforma (ou seja, HoloLens).

1. Abrir ou expandir o perfil *do Sistema de Reconhecimento Espacial*

    ![Perfil do Sistema de Reconhecimento Espacial](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Clique no *botão "Adicionar Observador Espacial"*
1. Selecione o tipo de *implementação do Observador Espacial desejado*

    ![Selecione a Implementação do Observador Espacial](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Modificar as propriedades de configuração no observador](configuring-spatial-awareness-mesh-observer.md) conforme necessário

> [!NOTE]
> Os usuários do `DefaultMixedRealityToolkitConfigurationProfile` (Ativos/MRTK/SDK/Perfis) terão o sistema de Reconhecimento Espacial pré-configurado para a plataforma Windows Mixed Reality que usa a [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe .

### <a name="build-and-deploy"></a>Criar e implantar

Depois que o sistema de Reconhecimento Espacial estiver configurado com os observadores desejados, o projeto poderá ser criado e implantado na plataforma de destino.

> [!IMPORTANT]
> Se estiver direcionando a plataforma Windows Mixed Reality (por ex. HoloLens), é [](/windows/mixed-reality/spatial-mapping-in-unity) importante garantir que a funcionalidade de Percepção Espacial seja habilitada para usar o sistema de Reconhecimento Espacial no dispositivo.

> [!WARNING]
> Algumas plataformas, incluindo Microsoft HoloLens, fornecem suporte para execução remota de dentro do Unity. Esse recurso permite o desenvolvimento e o teste rápidos sem exigir a etapa de build e implantação. Certifique-se de fazer o teste de aceitação final usando uma versão criada e implantada do aplicativo, em execução no hardware e na plataforma de destino.

## <a name="next-steps"></a>Próximas etapas

Depois de seguir os procedimentos acima para habilitar o sistema de Reconhecimento Espacial, o sistema pode ser configurado e controlado com mais detalhes.

Informações para configurar observadores no inspetor:

- [Configurando observadores para no uso do dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configurando observadores para uso no editor](spatial-object-mesh-observer.md)

Informações para controlar e estender observadores por meio de código:

- [Configurando observadores por meio de código](usage-guide.md)
- [Criando um Observador personalizado](create-data-provider.md)

## <a name="see-also"></a>Confira também

- [Documentação da API de Reconhecimento Espacial](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Visão geral do WMR do mapeamento espacial](/windows/mixed-reality/spatial-mapping)
- [Mapeamento espacial no WmR do Unity](/windows/mixed-reality/spatial-mapping-in-unity)
