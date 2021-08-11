---
title: Configuração dos observadores de malha para o dispositivo
description: Como configurar o Observador de Malha Espacial in-box no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 00a3b9afe1970239f52b1ead4f87f930c5826ba75522b99a52cf368249c9fd83
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228436"
---
# <a name="configuring-mesh-observers-for-device"></a>Configuração dos observadores de malha para o dispositivo

Este guia orientará a configuração do Observador de Malha Espacial in-box no MRTK, que dá suporte à plataforma Windows Mixed Reality (ou seja, HoloLens). A implementação padrão fornecida pela Toolkit Mixed Reality é a [classe WindowsMixedRealitySpatialMeshObserver.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Muitas das propriedades neste artigo se aplicam a outras [implementações personalizadas do Observador](create-data-provider.md).

## <a name="profile-settings"></a>Configurações de perfil

Os dois itens a seguir devem ser definidos primeiro ao configurar um perfil de Observador de Malha Espacial para o [sistema de Reconhecimento Espacial](spatial-awareness-getting-started.md).

1. A implementação de tipo de observador concreto
1. lista de plataformas com suporte para executar este observador

> [!NOTE]
> Todos os observadores devem estender a interface [IMixedRealitySpatialAwarenessObserver.](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)

![Tipos de plataforma de Configurações Observador de Malha](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Configurações gerais

![Configurações gerais do Configurações Genral do Observador de Malha](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Comportamento de inicialização**

O comportamento de inicialização especifica se o observador começará a ser executado quando for instautado pela primeira vez. As duas opções são:

* *Início Automático* – o valor padrão pelo qual o observador iniciará a operação após a inicialização
* *Início Manual* – o Observador aguardará para ser direcionado para iniciar

Se estiver usando *o Início Manual*, será necessário [retomá-los e suspendê-los em runtime por meio do código](usage-guide.md#starting-and-stopping-mesh-observation).

**Intervalo de atualização**

O tempo, em segundos, entre solicitações para a plataforma para atualizar dados de malha espacial. Os valores típicos se enquadram no intervalo de 0,1 e 5,0 segundos.

**É Observador Estacionário**

Indica se o observador deve ou não permanecer estacionário ou mover e atualizar com o usuário. Se true, a *Forma do Observador com* o volume definido por Extensão de *Observação* permanecerá na origem na inicialização. Se false, o espaço Observador seguirá a cabeça do usuário como a origem da forma.

Não haverá dados de malha calculados para qualquer área física fora do espaço Observador, conforme definido por estas propriedades: *Observador* Estacionário , *Forma do Observador** e Extensão *de Observação*.

**Forma do Observador**

A forma do observador define o tipo de volume que o observador de malha usará ao observar malhas. As opções com suporte são:

* *Cubo alinhado ao eixo* – forma retangular que permanece alinhada com os eixos do sistema de coordenadas mundial, conforme determinado na inicialização do aplicativo.
* *Cubo Alinhado pelo Usuário* – forma retangular que gira para alinhar com o sistema de coordenadas local dos usuários.
* *Sphere* – um volume esférico com um centro na origem do espaço do mundo. O valor X da propriedade *Deções de* Observação será usado como o raio da esfera.

**Extensão de observação**

As extensão de observação definem a distância do ponto de observação que as malhas serão observadas.

### <a name="physics-settings"></a>Configurações de física

![Mesh Observer Physics Configurações](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Camada física**

A camada física na qual os objetos de malha espacial serão colocados para interagir com os sistemas de Física do Unity e RayCast.

> [!NOTE]
> O banco de Toolkit reserva *a camada 31* por padrão para uso por observadores de Reconhecimento Espacial.

**Recalcular normais**

Especifica se o observador de malha recalculará ou não os normais da malha após a observação. Essa configuração está disponível para garantir que os aplicativos recebam malhas que contêm dados normais válidos em plataformas que não as retornam com malhas.

### <a name="level-of-detail-settings"></a>Nível de configurações de detalhes

![Nível de detalhes do observador de malha Configurações](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

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

![Exibição do Observador de Malha Configurações](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Opção De exibição**

Especifica como malhas espaciais devem ser exibidas pelo observador. Os valores com suporte são:

* *Nenhum* – o Observador não renderizará a malha
* *Visível* – os dados da malha estarão visíveis usando *o Material Visível*
* *Oclusão –* os dados da malha serão itens de occluir na cena usando *o Material de Oclusão*

![Selecione a implementação do sistema de reconhecimento espacial](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Observadores Espaciais podem [ser retomados/suspensos em runtime por meio de código.](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> Definir *Opção de Exibição* *como Nenhum* **NÃO impede** que o observador seja executado. Se você quiser interromper todos os observadores, os aplicativos precisarão suspender todos os observadores por meio de [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Material visível**

Indica o material a ser usado ao visualizar a malha espacial.

**Material de oclusão**

Indica o material a ser usado para fazer com que a malha espacial oclua hologramas.

## <a name="see-also"></a>Confira também

* [Sistema de Reconhecimento Espacial](spatial-awareness-getting-started.md)
* [Configurando o sistema de reconhecimento espacial por meio de código](usage-guide.md)
* [Documentação da API IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [Documentação da API IMixedRealitySpatialAwarenessMeshObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [Documentação da API BaseSpatialObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
