---
title: Modularidade do MRTK
description: Descreve a componentização no MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 1c32486c83eda9b99540d1719753977b6cdb2d18735e799dcd6c2ca3fcf200ce
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203600"
---
# <a name="mrtk-modularization"></a>Modularidade do MRTK

um dos ótimos novos recursos da realidade misturada Toolkit v2 é a componentização aprimorada. Sempre que possível, os componentes individuais são isolados de todas, exceto a camada principal da base.

## <a name="minimized-dependencies"></a>Dependências minimizadas

O MRTK v2 foi desenvolvido intencionalmente para ser modular e minimizar dependências entre serviços do sistema (por exemplo, conscientização espacial).

Devido à natureza de alguns serviços do sistema (por exemplo: entrada e teleportação), há um pequeno número de dependências.

Embora seja esperado que os serviços precisem de um ou mais componentes de provedor de dados, não há links diretos entre eles. O mesmo é verdadeiro para recursos do SDK (por exemplo, componentes de interface do usuário).

## <a name="component-communication"></a>Comunicação de componente

Para garantir que não haja links diretos entre os componentes, o MRTK v2 utiliza interfaces para se comunicar entre serviços, provedores de dados e código do aplicativo. essas interfaces são definidas no e toda a comunicação é roteada por meio da realidade misturada Toolkit componente principal.

![Usando o sistema de reconhecimento espacial por meio de interfaces](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>Minimizando a superfície de importação do MRTK

Neste momento, o MRTK é importado como um único pacote de base (ignorando por um momento a existência do pacote de exemplos, que é um pacote completamente opcional). É possível tornar essa superfície menor reduzindo manualmente os arquivos importados, embora esse seja um processo altamente manual que não tenha um guia bem definido.

É possível desmarcar itens arbitrários durante a importação do pacote do Foundation. No entanto, não é recomendável fazer isso em um estágio inicial do desenvolvimento, pois ela pode interromper a funcionalidade. Depois de ter descoberto o conjunto de recursos final de um aplicativo, a remoção de provedores e serviços desnecessários pode ser feita nas seguintes pastas:

- MRTK/serviços
- MRTK/provedores
- MRTK/SDK/recursos

> [!NOTE]
> O MRTK v2. x **_requer_** o conteúdo da pasta assets/MRTK/Core.

## <a name="upcoming-features"></a>Recursos futuros

### <a name="application-architecture"></a>Arquitetura do aplicativo

O MRTK terá suporte para permitir que os aplicativos sejam criados com uma variedade de arquiteturas, incluindo:

- [Localizador de serviço MixedRealityToolkit](#mixedrealitytoolkit-service-locator)
- [Serviços individuais](#individual-service-components)
- [Localizador de serviço personalizado](#custom-service-locator)
- [Arquitetura híbrida](#hybrid-architecture)

Ao selecionar uma arquitetura de aplicativo, é importante considerar a flexibilidade de design e o desempenho do aplicativo. As arquiteturas descritas aqui não devem ser adequadas para todos os aplicativos.

#### <a name="mixedrealitytoolkit-service-locator"></a>Localizador de serviço MixedRealityToolkit

O MRTK habilita (e configura automaticamente) cenas de aplicativos para usar o componente de [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizador de serviço padrão. Este componente inclui suporte para configurar sistemas e provedores de dados MRTK por meio de inspetores de configuração e gerencia a vida útil do componente e os comportamentos principais (por exemplo: quando atualizar).

Todos os sistemas são representados no Inspetor de configuração principal, independentemente de estarem ou não presentes ou habilitados no projeto. Consulte o [Guia de configuração da realidade misturada](../configuration/mixed-reality-configuration-guide.md) para obter mais informações.

#### <a name="individual-service-components"></a>Componentes de serviço individuais

Alguns desenvolvedores expressou um desejo de incluir componentes de serviço individuais na hierarquia de cena do aplicativo. Para habilitar esse uso, os serviços precisarão ser encapsulados em um registrador personalizado ou em Autoregistro/autogerenciamento.

Um serviço de registro automático implementaria o [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) e se registrará para que o código do aplicativo pudesse descobrir a instância do serviço por meio de um registro.

Um serviço de autogerenciamento pode ser implementado como um objeto singleton na hierarquia de cena. Esse objeto forneceria a propriedade de instância e o código do aplicativo que poderia usar para acessar diretamente a funcionalidade do serviço.

#### <a name="custom-service-locator"></a>Localizador de serviço personalizado

Alguns desenvolvedores solicitaram a capacidade de criar um componente de localizador de serviço personalizado. Os localizadores de serviço personalizados implementariam a [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface e gerenciariam o ciclo de vida e os principais comportamentos dos serviços ativos.

#### <a name="hybrid-architecture"></a>Arquitetura híbrida

O MRTK dará suporte a uma arquitetura híbrida na qual os desenvolvedores podem combinar as abordagens anteriores, conforme necessário ou desejado. Por exemplo, um desenvolvedor pode começar com o [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizador de serviço e adicionar um serviço de registro automático.

> [!NOTE]
> Ao optar por uma arquitetura híbrida, é importante estar atento a qualquer duplicação de trabalho (por exemplo: adquirir dados de controlador de vários componentes).
