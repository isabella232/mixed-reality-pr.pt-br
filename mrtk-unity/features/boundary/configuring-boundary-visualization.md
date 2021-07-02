---
title: Configurando a visualização de limite
description: Detalhes para configurar o sistema de limites no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Sistema de Limites,
ms.openlocfilehash: 77bdaedb60700bac27643ae718c795c02e5ee7e7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177090"
---
# <a name="configuring-boundary-visualization"></a>Configurando a visualização de limite

O *Perfil de Visualização de* Limite fornece opções para configurar a linguagem visual e outros parâmetros relacionados para o sistema de limites. As visualizações de limite são anexadas ao objeto do Playspace de Realidade Misturada na cena e são conectadas ao usuário.

## <a name="general-settings"></a>Configurações gerais

![Visualização de limite geral Configurações](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>Altura do limite

A altura do limite indica a distância acima do plano de piso no qual o limite deve ser renderizado. O valor padrão é 3 metros.

## <a name="floor-settings"></a>Configurações de piso

![Área de visualização de limite Configurações](../images/boundary/BoundaryVisualizationFloorSettings.png)

**Mostrar**

Indica se um plano de piso deve ou não ser criado e adicionado à cena. O valor padrão é true.

**Material**

Indica o material que deve ser usado ao criar o plano de piso.

**Escala**

Indica o tamanho, em metros, do plano de piso a ser criado. A escala padrão é um quadrado de 3 metros x 3 metros.

**Camada física**

A camada na qual o plano de piso deve ser definido. O valor padrão é a *camada* Padrão.

## <a name="play-area-settings"></a>Configurações da área de reprodução

![Área de reprodução de visualização de limite Configurações](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**Mostrar**

Indica se um retângulo de área de reprodução é criado e adicionado à cena. O valor padrão é true.

**Material**

Indica o material que deve ser usado ao criar o objeto de área de reprodução.

**Camada física**

A camada na qual a área de reprodução deve ser definida. O valor padrão é a *camada Ignorar Raycast.*

## <a name="tracked-area-settings"></a>Configurações de área rastreada

![Área rastreada de visualização de limite Configurações](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**Mostrar**

Indica se o contorno da área rastreada é criado ou não e adicionado à cena. O valor padrão é true.

**Material**

Indica o material que deve ser usado ao criar o contorno da área rastreada.

**Camada física**

A camada na qual a área rastreada deve ser configurada. O valor padrão é a *camada Ignorar Raycast.*

## <a name="boundary-wall-settings"></a>Configurações de parede de limite

![Mural de limite de visualização de limite Configurações](../images/boundary/BoundaryVisualizationWallSettings.png)

**Mostrar**

Indica se planos de parede de limite devem ou não ser criados e adicionados à cena. O valor padrão é false.

**Material**

Indica o material que deve ser usado ao criar os planos de parede de limite.

**Camada física**

A camada na qual as paredes de limite devem ser definidas. O valor padrão é a *camada Ignorar Raycast.*

> [!NOTE]
> Definir o componente de parede de limite como uma camada física diferente de *Ignorar Raycast* pode impedir que os usuários interajam com objetos dentro da cena.

## <a name="boundary-ceiling-settings"></a>Configurações de limite de limite

![Limite limite limite de visualização Configurações](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**Mostrar**

Indica se um plano de limite deve ou não ser criado e adicionado à cena. O valor padrão é false.

**Material**

Indica o material que deve ser usado ao criar o plano de limite de limite.

**Camada física**

A camada na qual as paredes de limite devem ser definidas. O valor padrão é a *camada Ignorar Raycast.*

> [!NOTE]
> Definir o componente de limite de limite para uma camada física diferente de *Ignorar Raycast* pode impedir que os usuários interajam com objetos dentro da cena.

## <a name="see-also"></a>Confira também

- [Documentação da API de limite](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Sistema de limite](boundary-system-getting-started.md)
