---
title: Contribuição
description: Como contribuir com o Kit de Ferramentas de Realidade Misturada
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Relatório de bugs,
ms.openlocfilehash: 525e704ae2f09580c8c19ca7e8a25dad4aed2647
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489256"
---
# <a name="contributing"></a>Participante

O MRTK (Kit de Ferramentas de Realidade Misturada) recebe contribuições da comunidade. Todas as alterações são pequenas ou grandes, precisam aderir aos padrões de codificação do [MRTK,](coding-guidelines.md)portanto, verifique se você está familiarizado com elas durante o desenvolvimento para evitar atrasos quando a alteração estiver sendo revisada.

Se você tiver dúvidas, entre em contato com o canal [mixed-reality-toolkit no Slack.](https://holodevelopers.slack.com/messages/C2H4HT858)
Você pode ingressar na comunidade do Slack por meio do [remetente de convite automático](https://holodevelopersslack.azurewebsites.net/).

## <a name="submission-process"></a>Processo de envio

Fornecemos vários caminhos para permitir que os desenvolvedores contribuam com o Kit de Ferramentas de Realidade Misturada, tudo começando com [a criação de um novo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

Aqui, você arquiva:

- **Relatório de bugs** – problema de funcionalidade com um dos componentes do Kit de Ferramentas de Realidade Misturada
- **Problema de documentação** – Problema com a documentação do Kit de Ferramentas de Realidade [Misturada](https://microsoft.github.io/MixedRealityToolkit-Unity)
- **Solicitação de recurso** – Proposta para um novo recurso do Kit de Ferramentas de Realidade Misturada

## <a name="proposing-feature-requests"></a>Solicitações de recurso de proposta

Ao solicitar um novo recurso do Kit de Ferramentas de Realidade Misturada, é importante documentar o problema/benefício do cliente a ser resolvido. Depois de enviada, uma solicitação de recurso será revisada e discutida no GitHub. Incentivamos uma discussão aberta e construtiva sobre cada proposta de recurso para garantir que o trabalho seja benéfico para um grande segmento de clientes.

Para evitar a necessidade de retrabalho do recurso, geralmente é recomendável que o desenvolvimento do recurso não comece durante a fase de revisão. Muitas vezes, o processo de revisão da comunidade descobre um ou mais problemas que podem exigir alterações significativas na implementação proposta.

> [!NOTE]
> Se você quiser trabalhar em algo que já existe em nossa lista de pendências, poderá usar esse item de trabalho como sua proposta. Certifique-se também de comentar sobre a tarefa notificando os mantenedores de que você está trabalhando para concluí-la.

## <a name="contribution-process"></a>Processo de contribuição

Para começar, basta seguir estas etapas:

1. Bifurcar o repositório. Clique no botão "bifurcação" no canto superior direito da página e siga o fluxo.
1. Crie uma ramificação em sua bifurcação (fora da ramificação [principal](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) ) para facilitar a aprovação de qualquer alteração até que esteja pronta para envio. Para correções de bugs durante um período de estabilização de liberação, procure a `prerelease/*` ramificação mais recente. Os novos recursos sempre devem entrar `main` .

Se você for novo no fluxo de trabalho do git, [Confira esta introdução do GitHub](https://guides.github.com/activities/hello-world/).

Ao adicionar um recurso ou correção de bug, siga estas etapas:

1. Implemente a correção de bugs ou o recurso. As instruções para criar e implantar MRTK estão em [BuildAndDeploy](../updates-deployment/build-and-deploy.md). Lembre-se de seguir as [diretrizes de codificação](../contributing/coding-guidelines.md).
1. Se adicionar um recurso, adicione também uma cena de exemplo que demonstra o recurso.
1. Se estiver adicionando um recurso experimental, não será necessário escrever testes e documentação. Em vez disso, siga as [diretrizes de recurso experimental](../contributing/experimental-features.md).
1. Adicione testes para verificar a correção de bug/recurso. As instruções para escrever e executar testes estão em [UnitTests](../contributing/unit-tests.md).
1. Verifique se o código e os recursos estão documentados conforme descrito nas [diretrizes de documentação](../contributing/documentation-guide.md).
1. Verifique se o código funciona conforme o esperado em todas as plataformas. Consulte as [notas de versão](../release-notes/mrtk-26-release-notes.md) para obter a lista de plataformas com suporte. Para projetos UWP do Windows, o código deve ser [compatível com wack](https://developer.microsoft.com/windows/develop/app-certification-kit). Para fazer isso, gere uma solução do Visual Studio, clique com o botão direito do mouse no projeto; **Armazenar**  >  **Criar pacotes de aplicativos**. Siga os prompts e execute testes DOLS. Certifique-se de que todos eles são bem-sucedidos.
1. Siga as instruções em [Solicitações pull ao](../contributing/pull-requests.md) fazer uma solicitação de pull.
