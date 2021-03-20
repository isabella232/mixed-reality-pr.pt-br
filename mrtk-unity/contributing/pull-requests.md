---
title: PullRequests
description: Detalhes relacionados a solicitações de pull.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, PR,
ms.openlocfilehash: c49934139ae23b714addcb9c015e95377f47900e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693283"
---
# <a name="pull-requests"></a>Solicitações de pull

## <a name="prerequisites"></a>Pré-requisitos

Se você não contribuiu para um projeto da Microsoft antes, talvez precise assinar um [contrato de licença de contribuição](https://cla.microsoft.com/).
Um comentário na PR informará se você precisa assiná-lo.

> [!IMPORTANT]
> Se você é funcionário da Microsoft e não é membro da [organização Microsoft no GitHub](https://github.com/Microsoft), vincule suas contas Microsoft e do GitHub na rede corporativa acessando [Software livre na Microsoft](https://opensource.microsoft.com/) antes de iniciar sua solicitação de pull. Há alguns processos que você precisará realizar antecipadamente.

## <a name="creating-a-pull-request"></a>Como criar uma solicitação de pull

Quando estiver pronto para enviar uma solicitação de pull, [crie uma solicitação de pull](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1) direcionando o branch [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development).

Leia as diretrizes e verifique se a sua solicitação de pull atende às diretrizes.

* Referencie qualquer solicitação de recurso/problema ou tarefa à qual a PR está relacionada.
* Verifique se a solicitação de pull contém somente arquivos/alterações relacionados à PR.
* Verifique se a documentação está atualizada e incluída. Verifique se todos os campos públicos têm comentários.
* Se estiver adicionando um novo recurso, verifique se os testes estão incluídos para validar o recurso (confira [UnitTests](../contributing/unit-tests.md)).
* Se estiver corrigindo um bug, escreva um teste para verificar a correção de bug.

Os mantenedores do projeto examinarão suas alterações. Nosso objetivo é examinar todas as alterações em até três dias úteis. Examine os comentários de revisão, envie-os por push para o branch do tópico e poste um comentário informando-nos que há um novo conteúdo a ser examinado.

> [!NOTE]
> Todas as PRs enviadas ao projeto também serão verificadas de acordo com o [Guia de padrões de codificação do MRTK](../contributing/coding-guidelines.md). Portanto, examine-o antes de enviar a PR para garantir um processo contínuo.

## <a name="pull-request-guidelines"></a>Diretrizes de solicitação de pull

Essas diretrizes se baseiam nas [práticas de engenharia da Google](https://google.github.io/eng-practices/review/developer/small-cls.html).

### <a name="keep-pull-requests-small"></a>Mantenha as solicitações de pull pequenas

As PRs menores são examinadas mais detalhadamente e com mais rapidez e têm menos probabilidade de apresentar bugs, além de serem mais fáceis de serem revertidas e mescladas.

As solicitações de pull devem ser pequenas o suficiente para que um engenheiro possa examiná-la em menos de 30 minutos. Tente fazer uma alteração mínima que aborde apenas uma coisa. Se precisar criar uma PR grande, divida-a em várias PRs que entrem no branch local ou em um branch de recurso do MRTK. Evite adicionar novos ativos (por exemplo, FBX, arquivos OBJ) e, em vez disso, tenha como objetivo reutilizar os ativos existentes.

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>Os testes devem ser adicionados na mesma PR da correção/do recurso, exceto em caso de emergências

Eles são a melhor maneira de garantir que as alterações não retenham o código existente, mas também é fácil esquecer os testes ao enviar solicitações de pull. Exigir que eles entrem com a PR são uma excelente maneira de garantir que os testes sejam escritos.

Cada recurso e correção de bug devem ter testes associados a eles. Se você não tiver a experiência nem o tempo para escrever um teste, crie um problema para escrever os testes e marque-os com o rótulo **Considerar para Iteração Atual**.

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>A documentação deve ser adicionada à mesma solicitação de pull de uma correção/um recurso

A maioria dos desenvolvedores examina primeiro a documentação, não o código, ao entender como usar um recurso. Garantir que a documentação esteja atualizada facilita muito para as pessoas consumir os MRTKs e confiar neles.  A documentação sempre deve ser agrupada com o pull relacionado para garantir que os itens permaneçam atualizados e consistentes.

Verifique se que cada campo público, método e propriedade tem [comentários de resumo de barra tripla](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) para que nosso site docfx possa gerar descrições para campos/métodos. Se necessário, atualize os arquivos de markdown na pasta Documentação.

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>As descrições das solicitações de pull devem explicar as alterações com clareza e integridade

Descrições claras e completas das solicitações de pull garantem que os revisores entendam o que estão examinando.

Se estiver adicionando recursos que contenham UX, adicione uma imagem/um GIF do recurso que está sendo alterado. [Veja a seguir um bom exemplo](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532). Outra sugestão é ter um GIF de Antes e Depois, [por exemplo, nesta solicitação de pull](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896). Uma ferramenta que recomendamos para gerar GIFs com base em capturas de tela é o [ScreenToGif](https://www.screentogif.com/).
