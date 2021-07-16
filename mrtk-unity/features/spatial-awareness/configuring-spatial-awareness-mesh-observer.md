---
title: Configurando os observadores de malha para o dispositivo
description: Como configurar o observador de malha espacial pronta no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281931"
---
# <a name="configuring-mesh-observers-for-device"></a>Configurando os observadores de malha para o dispositivo

este guia explicará como configurar o observador de malha espacial pronta no MRTK, que dá suporte à plataforma de Windows Mixed Reality (ou seja, HoloLens). a implementação padrão fornecida pela realidade misturada Toolkit é a classe [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) . Muitas das propriedades neste artigo se aplicam a outras [implementações personalizadas do observador](create-data-provider.md).

## <a name="profile-settings"></a>Configurações de perfil

Os dois itens a seguir devem ser definidos primeiro ao configurar um perfil de observador de malha espacial para o [sistema de conscientização espacial](spatial-awareness-getting-started.md).

1. A implementação do tipo de observador concreto
1. lista de plataforma (s) com suporte para executar este observador

> [!NOTE]
> Todos os observadores devem estender a interface [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) .

![observador de malha geral Configurações tipos de plataforma](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Configurações gerais

![observador de malha geral Configurações configurações de Genral](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Comportamento de inicialização**

O comportamento de inicialização especifica se o observador começará a ser executado quando a primeira instância for criada. As duas opções são:

* *Início automático* -o valor padrão no qual o observador iniciará a operação após a inicialização
* *Início manual* -o observador aguardará para ser direcionado para o início

Se estiver usando o *início manual, será* necessário [retomá-los e suspendê-los em tempo de execução por meio de código](usage-guide.md#starting-and-stopping-mesh-observation).

**Intervalo de atualização**

O tempo, em segundos, entre as solicitações para a plataforma para atualizar dados de malha espacial. Os valores típicos se enquadram no intervalo de 0,1 a 5,0 segundos.

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

![Configurações física do observador de malha](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Camada física**

A camada física na qual os objetos de malha espacial serão colocados para interagir com os sistemas física e RayCast do Unity.

> [!NOTE]
> a realidade misturada Toolkit reserva a *camada 31* por padrão para uso por observadores de conscientização espacial.

**Recalcular Normals**

Especifica se o observador de malha recalculará os Normals da malha após a observação. Essa configuração está disponível para garantir que os aplicativos recebam malhas que contêm dados normais válidos em plataformas que não as retornam com malhas.

### <a name="level-of-detail-settings"></a>Nível de configurações de detalhes

![nível de detalhe do observador de malha Configurações](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Nível de detalhe**

Especifica o nível de detalhe (LOD) dos dados de malha espacial. Os valores definidos no momento são grande, bem e personalizados.

* Em *grande* lugar, um impacto menor no desempenho do aplicativo e é uma excelente opção para a localização de navegação/plano.

* A configuração com balanceamento *médio* geralmente é útil para experiências que verificam continuamente o ambiente em busca de recursos grandes, andares e paredes, bem como detalhes de oclusão.

* *Normalmente,* isso é exatamente um impacto maior no desempenho do aplicativo e é uma ótima opção para as malhas de oclusão.

* *Personalizado* – exige que o aplicativo especifique a propriedade de *medidor de triângulos/cúbico* e permite que os aplicativos ajustem a precisão versus o impacto no desempenho do observador de malha espacial.

> [!NOTE]
> Não há garantia de que todos os valores de *medidor de triângulos/cúbicos* sejam respeitados por todas as plataformas. A experimentação e a criação de perfil são altamente recomendadas ao usar um LOD personalizado.

**Triângulos por medidor cúbico**

Válido ao usar a configuração *personalizada* para o **nível de propriedade de detalhe** e especifica a densidade de triângulo para a malha espacial.

### <a name="display-settings"></a>Configurações de vídeo

![Configurações de exibição de observador de malha](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Opção de exibição**

Especifica como as malhas espaciais devem ser exibidas pelo observador. Os valores com suporte são:

* *Nenhum* -o observador não renderizará a malha
* *Visível* -os dados de malha ficarão visíveis usando o *material visível*
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
