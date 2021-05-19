---
title: Configuração do observador de malha de conscientização espacial
description: Como configurar o Observador de Malha Espacial in-box no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144961"
---
# <a name="configuring-mesh-observers-for-device"></a>Configurando observadores de malha para o dispositivo

Este guia orientará a configuração do Observador de Malha Espacial in-box no MRTK, que dá suporte à plataforma Windows Mixed Reality (ou seja, HoloLens). A implementação padrão fornecida pelo Kit de Ferramentas de Realidade Misturada é a [classe WindowsMixedRealitySpatialMeshObserver.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Muitas das propriedades neste artigo se aplicam a outras [implementações personalizadas do Observador](create-data-provider.md).

## <a name="profile-settings"></a>Configurações de perfil

Os dois itens a seguir devem ser definidos primeiro ao configurar um perfil de Observador de Malha Espacial para o [sistema de Reconhecimento Espacial](spatial-awareness-getting-started.md).

1. A implementação de tipo de observador concreto
1. lista de plataformas com suporte para executar este observador

> [!NOTE]
> Todos os observadores devem estender a interface [IMixedRealitySpatialAwarenessObserver.](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)

![Tipos de Plataforma de Configurações Gerais do Observador de Malha](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Configurações gerais

![Configurações gerais do Observador de Malha Configurações Genral](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Comportamento de inicialização**

O comportamento de inicialização especifica se o observador começará a ser executado quando for instautado pela primeira vez. As duas opções são:

* *Início Automático* – o valor padrão pelo qual o observador iniciará a operação após a inicialização
* *Início Manual* – o Observador aguardará para ser direcionado para iniciar

Se estiver usando *o Início Manual*, será necessário [retomá-los e suspendê-los em runtime por meio do código](usage-guide.md#starting-and-stopping-mesh-observation).

**Intervalo de atualização**

O tempo, em segundos, entre solicitações para a plataforma para atualizar dados de malha espacial. Os valores típicos se enquadram no intervalo de 0,1 e 5,0 segundos.

**É observador estacionário**

Indica se o observador deve ou não ser estacionário ou movido e atualizado com o usuário. Se for true, a *forma de observador* com volume definido por *extensões de observação* permanecerá na origem na inicialização. Se for false, o espaço do observador seguirá o cabeçalho do usuário como a origem da forma.

Não haverá dados de malha calculados para qualquer área física fora do espaço do observador, conforme definido por essas propriedades: *é observador estacionário*, * forma do observador * * e *extensões de observação*.

**Forma do observador**

A forma do observador define o tipo de volume que o observador de malha usará ao observar as malhas. As opções com suporte são:

* *Cubo alinhado ao eixo* – forma retangular que permanece alinhada com os eixos do sistema mundial de coordenadas, conforme determinado na inicialização do aplicativo.
* *Cubo alinhado ao usuário* – forma retangular que gira para alinhar com o sistema de coordenadas local dos usuários.
* *Esfera* -um volume esférico com um centro na origem do espaço mundial. O valor X da propriedade de *extensões de observação* será usado como o raio da esfera.

**Extensões de observação**

As extensões de observação definem a distância do ponto de observação que as malhas serão observadas.

### <a name="physics-settings"></a>Configurações de física

![Configurações de física do observador de malha](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Camada física**

A camada física na qual os objetos de malha espacial serão colocados para interagir com os sistemas física e RayCast do Unity.

> [!NOTE]
> O kit de ferramentas de realidade misturada reserva a *camada 31* por padrão para uso por observadores de conscientização espacial.

**Recalcular Normals**

Especifica se o observador de malha recalculará ou não os normais da malha após a observação. Essa configuração está disponível para garantir que os aplicativos recebam malhas que contêm dados normais válidos em plataformas que não as retornam com malhas.

### <a name="level-of-detail-settings"></a>Nível de configurações de detalhes

![Nível de Detalhes do Observador da Malha](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Nível de detalhes**

Especifica o nível de detalhes (LOD) dos dados da malha espacial. Os valores atualmente definidos são Coarse, Fine e Custom.

* *Alta* - coloca um impacto menor no desempenho do aplicativo e é uma excelente opção para a navegação/a descoberta de plano.

* *Média* – a configuração equilibrada geralmente é útil para experiências que digitalizaram continuamente o ambiente em busca de recursos grandes, pisos e paredes, bem como detalhes de oclusão.

* *Fine* – geralmente causa um impacto mais alto no desempenho do aplicativo e é uma ótima opção para malhas de oclusão.

* *Personalizado* – exige que o aplicativo especifique a propriedade *Triângulos/Medidor* Cúbica e permita que os aplicativos ajustem a precisão versus o impacto no desempenho do observador de malha espacial.

> [!NOTE]
> Não há garantia de que todos os *valores de Triângulos/Medidor Cúbica* sejam considerados por todas as plataformas. A experimentação e a criação de perfil são altamente recomendadas ao usar um LOD personalizado.

**Triângulos por medidor cúbica**

Válido ao usar a *configuração* Personalizada para a propriedade **Nível** de Detalhe e especifica a densidade do triângulo para a malha espacial.

### <a name="display-settings"></a>Configurações de vídeo

![Configurações de exibição do Observador de Malha](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Opção De exibição**

Especifica como malhas espaciais devem ser exibidas pelo observador. Os valores com suporte são:

* *Nenhum* – o Observador não renderizará a malha
* *Visível* – os dados da malha estarão visíveis usando *o Material Visível*
* *Oclusão* -os dados de malha serão occlude itens em cena usando o *material de oclusão*

![Selecione a implementação do sistema de conscientização espacial](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Os observadores espaciais podem ser [retomados/suspensos em tempo de execução por meio de código.](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> A configuração da *opção de exibição* para *nenhum* **não interrompe a** execução do observador. Se você quiser interromper todos os observadores, os aplicativos precisarão suspender todos os observadores por meio de [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Material visível**

Indica o material a ser usado ao visualizar a malha espacial.

**Material de oclusão**

Indica o material a ser usado para fazer com que a malha espacial occlude hologramas.

## <a name="see-also"></a>Confira também

* [Sistema de conscientização espacial](spatial-awareness-getting-started.md)
* [Configurando o sistema de reconhecimento espacial por meio de código](usage-guide.md)
* [Documentação da API do IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [Documentação da API do IMixedRealitySpatialAwarenessMeshObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [Documentação da API do BaseSpatialObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
