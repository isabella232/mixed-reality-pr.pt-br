---
title: Modularidade do MRTK
description: Descreve a componentização no MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144423"
---
# <a name="mixed-reality-toolkit-componentization"></a>Componentização do Kit de Ferramentas de Realidade Misturada

Um dos novos recursos excelentes do Kit de Ferramentas de Realidade Misturada v2 é a melhoria da componentização. Sempre que possível, os componentes individuais são isolados de todos, menos da camada principal da base.

## <a name="minimized-dependencies"></a>Dependências minimizadas

O MRTK v2 foi desenvolvido intencionalmente para ser modular e minimizar as dependências entre os serviços do sistema (por ex. reconhecimento espacial).

Devido à natureza de alguns serviços do sistema (por ex. entrada e teletransportação), há um pequeno número de dependências.

Embora seja esperado que os serviços precisem de um ou mais componentes do provedor de dados, não há links diretos entre eles. O mesmo vale para recursos do SDK (por exemplo, Interface do Usuário componentes).

## <a name="component-communication"></a>Comunicação de componente

Para garantir que não haja links diretos entre componentes, o MRTK v2 utiliza interfaces para se comunicar entre serviços, provedores de dados e código do aplicativo. Essas interfaces são definidas em e toda a comunicação é roteada por meio do componente principal do Kit de Ferramentas de Realidade Misturada.

![Usando o sistema de reconhecimento espacial por meio de interfaces](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>Minimizando o espaço de importação do MRTK

Neste momento, o MRTK é importado como um único pacote de base (ignorando por um momento a existência do pacote de exemplos, que é um pacote completamente opcional). É possível tornar esse volume menor reduzindo manualmente os arquivos importados, embora esse seja um processo altamente manual que não tem um guia bem definido.

É possível desmarcar itens arbitrários durante a importação do pacote Foundation. No entanto, não é recomendável fazer isso em um estágio inicial no desenvolvimento, pois ele pode quebrar a funcionalidade. Depois de descobrir o conjunto de recursos final de um aplicativo, a remoção de provedores e serviços não previstos pode ser feita nas seguintes pastas:

- MRTK/Serviços
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

Um serviço de autogerenciamento pode ser implementado como um objeto singleton na hierarquia de cena. Esse objeto forneceria e a propriedade de instância que o código do aplicativo poderia usar para acessar diretamente a funcionalidade do serviço.

#### <a name="custom-service-locator"></a>Localizador de serviço personalizado

Alguns desenvolvedores solicitaram a capacidade de criar um componente de localizador de serviço personalizado. Os localizadores de serviço personalizados implementariam a interface e gerenciariam o ciclo de vida e [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) os comportamentos principais dos serviços ativos.

#### <a name="hybrid-architecture"></a>Arquitetura híbrida

O MRTK dará suporte a uma arquitetura híbrida na qual os desenvolvedores podem combinar as abordagens anteriores conforme necessário ou desejado. Por exemplo, um desenvolvedor pode começar com o [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizador de serviço e adicionar um serviço de auto-registro.

> [!NOTE]
> Ao optar por uma arquitetura híbrida, é importante estar atento a qualquer duplicação de trabalho (por exemplo: adquirir dados do controlador de vários componentes).
