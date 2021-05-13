---
title: Contribuição
description: Como contribuir com o kit de ferramentas de realidade misturada
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, relatório de bugs,
ms.openlocfilehash: 11a62708b4cb1a5acc3d230f933be2e88e0ac87b
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850362"
---
# <a name="contributing"></a>Participante

O MRTK (Mixed Reality Toolkit) agradece as contribuições da Comunidade. Todas as alterações são pequenas ou grandes, precisam aderir aos [padrões de codificação MRTK](coding-guidelines.md), portanto, verifique se você está familiarizado com isso ao desenvolver para evitar atrasos quando a alteração está sendo revisada.

Se você tiver alguma dúvida, entre em contato com o [canal Mixed-Realm-Toolkit na margem de atraso](https://holodevelopers.slack.com/messages/C2H4HT858).
Você pode ingressar na comunidade do Slack por meio do [remetente de convite automático](https://holodevelopersslack.azurewebsites.net/).

## <a name="submission-process"></a>Processo de envio

Fornecemos vários caminhos para permitir que os desenvolvedores contribuam para o kit de ferramentas da realidade misturada, tudo isso começando com [a criação de um novo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

A partir daqui, você arquivo:

- **Relatório de bugs** -problema de funcionalidade com um dos componentes mistos do kit de ferramentas da realidade
- **Problema de documentação** -problema com a [documentação](https://microsoft.github.io/MixedRealityToolkit-Unity) do kit de ferramentas de realidade misturada
- **Solicitação de recurso** -proposta para um novo recurso do kit de ferramentas de realidade misturada

## <a name="proposing-feature-requests"></a>Proposta de solicitações de recursos

Ao solicitar um novo recurso do kit de ferramentas de realidade misturada, é importante documentar o benefício do cliente/problema a ser resolvido. Depois de enviado, uma solicitação de recurso será revisada e discutida no GitHub. Incentivamos a discussão aberta e construtivas de cada proposta de recurso para garantir que o trabalho seja benéfico para um grande segmento de clientes.

Para evitar a necessidade de retrabalhar o recurso, geralmente é recomendável que o desenvolvimento do recurso não comece durante a fase de revisão. Muitas vezes, o processo de revisão da Comunidade descobre um ou mais problemas que podem exigir alterações significativas na implementação proposta.

> [!NOTE]
> Se você deseja trabalhar em algo que já existe em nossa pendência, você pode usar esse item de trabalho como sua proposta. Lembre-se também de comentar a tarefa notificando os mantenedores de que você está trabalhando para concluí-la.

## <a name="contribution-process"></a>Processo de contribuição

Para começar, basta seguir estas etapas:

1. Crie fork do repositório. Clique no botão "Bifurcar" no canto superior direito da página e siga o fluxo.
1. Crie um branch em sua bifurcação (fora do [branch principal)](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) para facilitar a isolação das alterações até que esteja pronto para envio. Para correções de bugs durante um período de estabilização de versão, procure o branch `prerelease/*` mais recente. Novos recursos sempre devem entrar no `main` .

Se você for novo no fluxo de trabalho do Git, [confira esta introdução do Github.](https://guides.github.com/activities/hello-world/)

Ao adicionar uma correção de bug ou recurso, siga estas etapas:

1. Implemente a correção de bug ou o recurso. As instruções para criar e implantar o MRTK estão em [Implantando em dispositivos Hololens e WMR.](../supported-devices/wmr-mrtk.md) Lembre-se de seguir [as Diretrizes de Codificação](../contributing/coding-guidelines.md).
1. Se adicionar um recurso, adicione também uma cena de exemplo que demonstra o recurso.
1. Se você adicionar um recurso experimental, não será necessário escrever testes e documentação. Em vez disso, siga [as diretrizes de recurso experimental](../contributing/experimental-features.md).
1. Adicione testes para verificar a correção de bug/recurso. As instruções para escrever e executar testes estão em [UnitTests.](../contributing/unit-tests.md)
1. Verifique se o código e os recursos estão documentados conforme descrito nas Diretrizes [de documentação.](../contributing/documentation-guide.md)
1. Verifique se o código funciona conforme o esperado em todas as plataformas. Confira [Notas sobre a](../release-notes/mrtk-26-release-notes.md) versão para ver a lista de plataformas com suporte. Para projetos UWP do Windows, o código deve estar [em conformidade com o CASO.](https://developer.microsoft.com/windows/develop/app-certification-kit) Para fazer isso, gere uma solução Visual Studio, clique com o botão direito do mouse no projeto; **Store**  >  **Criar pacotes de aplicativos**. Siga os prompts e execute testes DOLS. Certifique-se de que todos tenham sucesso.
1. Siga as instruções em [solicitações pull](../contributing/pull-requests.md) ao fazer uma solicitação de pull.
