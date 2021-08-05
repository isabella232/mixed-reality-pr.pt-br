---
title: Contribuindo para o MRTK
description: Como contribuir para a realidade misturada Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, relatório de bugs,
ms.openlocfilehash: e24ef1c568f9d6fa84fdd49dac17581f71dfc466018929e045de43d58549c09b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210742"
---
# <a name="contributing-to-mrtk"></a>Contribuindo para o MRTK

a realidade mista Toolkit (MRTK) agradece as contribuições da comunidade. Todas as alterações são pequenas ou grandes, precisam aderir aos [padrões de codificação MRTK](coding-guidelines.md), portanto, verifique se você está familiarizado com isso ao desenvolver para evitar atrasos quando a alteração está sendo revisada.

Se você tiver alguma dúvida, entre em contato com o [canal Mixed-Realm-Toolkit na margem de atraso](https://holodevelopers.slack.com/messages/C2H4HT858).
Você pode ingressar na comunidade do Slack por meio do [remetente de convite automático](https://holodevelopersslack.azurewebsites.net/).

## <a name="submission-process"></a>Processo de envio

fornecemos vários caminhos para permitir que os desenvolvedores contribuam para a realidade misturada Toolkit, tudo isso começando com a [criação de um novo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

A partir daqui, você arquivo:

- **relatório de bugs** -problema de funcionalidade com um dos componentes da realidade misturada Toolkit
- **problema de documentação** -problema com a realidade misturada Toolkit [documentação](https://microsoft.github.io/MixedRealityToolkit-Unity)
- **solicitação de recurso** -proposta para um novo recurso Toolkit de realidade misturada

## <a name="proposing-feature-requests"></a>Proposta de solicitações de recursos

ao solicitar uma nova realidade misturada Toolkit recurso, é importante documentar o benefício do cliente/problema a ser resolvido. Depois de enviado, uma solicitação de recurso será examinada e discutida em GitHub. Incentivamos a discussão aberta e construtivas de cada proposta de recurso para garantir que o trabalho seja benéfico para um grande segmento de clientes.

Para evitar a necessidade de retrabalhar o recurso, geralmente é recomendável que o desenvolvimento do recurso não comece durante a fase de revisão. Muitas vezes, o processo de revisão da Comunidade descobre um ou mais problemas que podem exigir alterações significativas na implementação proposta.

> [!NOTE]
> Se você deseja trabalhar em algo que já existe em nossa pendência, você pode usar esse item de trabalho como sua proposta. Lembre-se também de comentar a tarefa notificando os mantenedores de que você está trabalhando para concluí-la.

## <a name="contribution-process"></a>Processo de contribuição

Para começar, basta seguir estas etapas:

1. Crie fork do repositório. Clique no botão "bifurcação" no canto superior direito da página e siga o fluxo.
1. Crie uma ramificação em sua bifurcação (fora da ramificação [principal](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) ) para facilitar a aprovação de qualquer alteração até que esteja pronta para envio. Para correções de bugs durante um período de estabilização de liberação, procure a `prerelease/*` ramificação mais recente. Os novos recursos sempre devem entrar `main` .

Se você for novo no fluxo de trabalho do git, [Confira esta introdução do GitHub](https://guides.github.com/activities/hello-world/).

Ao adicionar um recurso ou correção de bug, siga estas etapas:

1. Implemente a correção de bugs ou o recurso. As instruções para criação e implantação de MRTK estão em [implantação em dispositivos Hololens e WMR](../supported-devices/wmr-mrtk.md). Lembre-se de seguir as [diretrizes de codificação](../contributing/coding-guidelines.md).
1. Se adicionar um recurso, adicione também uma cena de exemplo que demonstra o recurso.
1. Se estiver adicionando um recurso experimental, não será necessário escrever testes e documentação. Em vez disso, siga as [diretrizes de recurso experimental](../contributing/experimental-features.md).
1. Adicione testes para verificar a correção de bug/recurso. As instruções para escrever e executar testes estão em [UnitTests](../contributing/unit-tests.md).
1. Verifique se o código e os recursos estão documentados conforme descrito nas [diretrizes de documentação](../contributing/documentation-guide.md).
1. Verifique se o código funciona conforme o esperado em todas as plataformas. Consulte as [notas de versão](../release-notes/mrtk-26-release-notes.md) para obter a lista de plataformas com suporte. para Windows projetos UWP, o código deve ser [compatível com WACK](https://developer.microsoft.com/windows/develop/app-certification-kit). para fazer isso, gere uma solução de Visual Studio, clique com o botão direito do mouse no projeto; **Armazenar**  >  **Criar pacotes de aplicativos**. Siga os prompts e execute os testes do WACK. Certifique-se de que todos tenham sucesso.
1. Siga as instruções em [solicitações pull](../contributing/pull-requests.md) ao fazer uma solicitação de pull.
