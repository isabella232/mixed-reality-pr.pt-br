---
title: Instruções de contribuição
description: Conheça as etapas básicas e as diretrizes para contribuir com o Guia Windows Mixed Reality de Windows Mixed Reality Desast. Agradecemos seus comentários, edições, adições e ajuda.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Comentários, Hub de Comentários, bugs
appliesto:
- Windows 10
ms.openlocfilehash: fd47e806a1ac14d85f503d7d4f799b232cbd3e102c3d4494d5704082bf0e08ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188065"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Contribuição para o Guia deHusiast de Realidade Misturada

Agradecemos seu interesse no Guia de Enthusiast. Agradecemos seus comentários, edições, adições e ajuda para melhorar nossos documentos. Esta página aborda as etapas básicas e as diretrizes para contribuir.

> [!IMPORTANT]
> Todos os repositórios que publicam no docs.microsoft.com adotaram o [Código de Conduta de Software Livre da Microsoft](https://opensource.microsoft.com/codeofconduct/). Para saber mais, confira as [Perguntas frequentes sobre o Código de Conduta](https://opensource.microsoft.com/codeofconduct/faq/) ou entre em contato com [opencode@microsoft.com](mailto:opencode@microsoft.com) para enviar perguntas ou comentários.<br>
>
> Os [Termos de Uso de docs.microsoft.com](/legal/termsofuse) incluem correções secundárias ou esclarecimentos sobre a documentação, além de exemplos de código nos repositórios públicos. As alterações novas ou significativas gerarão um comentário na solicitação de pull pedindo o envio de um CLA (Contrato de Licença de Contribuição) online, caso você não seja um funcionário da Microsoft. Precisamos que você preencha o formulário online antes de aceitarmos sua solicitação pull.

## <a name="before-you-start"></a>Antes de começar

Se você ainda não tiver uma, precisará criar uma conta [GitHub .](https://github.com/join)

>[!NOTE]
>Se você for um funcionário da Microsoft, vincule sua GitHub ao alias da Microsoft no portal de Código Aberto [da Microsoft.](https://repos.opensource.microsoft.com/) Participe das **organizações "Microsoft"** **e "MicrosoftDocs".**

Ao configurar sua conta GitHub, também recomendamos estas precauções de segurança:
- Crie uma [senha forte para sua conta do Github.](https://github.com/settings/admin)
- [Habilita a autenticação de dois fatores.](https://github.com/settings/two_factor_authentication/configure)
- Salve seus [códigos de recuperação](https://github.com/settings/auth/recovery-codes) em um local seguro.
- Atualize [suas configurações de perfil público](https://github.com/settings/profile).
   - De definir seu nome e considere definir seu *email público* como Não mostrar meu endereço *de email*.
   - Recomendamos que você carregue uma imagem de perfil porque uma miniatura é mostrada nas páginas de documentos com as que você contribui.
- Se você planeja usar a linha de comando, considere configurar o [Git Gerenciador de Credenciais para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). Dessa forma, você não precisa inserir sua senha sempre que fizer uma contribuição.

O sistema de publicação está vinculado GitHub, portanto, essas etapas são importantes. Você será listado como autor ou colaborador de cada artigo usando seu alias GitHub dados.

## <a name="how-to-make-a-change"></a>Como fazer uma alteração

| Para sugerir uma alteração aos documentos, siga estas etapas: | Capturas de tela |
| :------------------- | :--------: |
| 1. Se você estiver exibindo uma Docs.microsoft.com, clique no **botão** Editar no canto superior direito da página.  Você será redirecionado para o arquivo de origem de Markdown correspondente no [repositório GitHub](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide). | ![Botão Editar](images/edit_button.jpg) |
| 2. Se você ainda não tiver uma conta  GitHub, clique em Inscrever-se no canto superior direito e crie uma nova conta. | ![Botão Inscrever-se](images/signup-for-github-button.png)|
| 3. Na página de GitHub correspondente que é aberta, clique em Editar (o ícone de lápis). | ![Botão de lápis](images/pencil_button.jpg)|
| 4. No painel Editar [arquivo,](#updating-metadata) atualize os metadados dos arquivos e use a linguagem Markdown para alterar o conteúdo. ([Como gravar markdown.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![Editar Arquivo](images/edit-in-github.png)|
| 5. Clique em Visualizar alterações para verificar se a formatação é a aparência esperada. | ![Visualizar alterações](images/edit-in-github.png)|
| 6. Quando terminar, role até a parte inferior da página e clique em "Propor alteração de arquivo", você receberá uma página "Comparando alterações", permitindo que você verifique as alterações. Em seguida, clique no botão "Criar solicitação de pull" para enviar suas alterações. Neste ponto, você terminou! | ![Propor uma alteração](images/propose.jpg)|

Depois que você enviar alterações (por meio de uma solicitação de pull), elas serão revisadas por um membro da equipe de documentação. Se sua solicitação for aceita, as atualizações serão publicadas no [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide) .

*Somente para revisão interna, você pode ver suas alterações em [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

### <a name="updating-metadata"></a>Atualizando metadados

Atualize os metadados na parte superior de cada artigo:
   * **título:** título da página que aparece na guia do navegador quando o artigo está sendo exibido. Os títulos de página são usados para SEO e indexação, portanto, não altere o título, a menos que necessário (embora isso seja menos crítico antes que a documentação seja pública).
   * **description**: escreva uma breve descrição do conteúdo do artigo, o que aumenta o SEO e a descoberta.
   * **author**: se você for o proprietário principal da página, adicione seu alias GitHub aqui.
   * **ms.author:** se você for o proprietário principal da página, adicione o alias da Microsoft aqui (você não precisa @microsoft.com apenas do alias).
   * **ms.date:** atualize a data se você estiver adicionando conteúdo principal à página, mas não para correções como esclarecimento, formatação, gramática ou ortografia.
   * **palavras-chave:** as palavras-chave auxiliam no SEO (otimização do mecanismo de pesquisa). Adicione palavras-chave, separadas por uma vírgula e um espaço, que são específicas para seu artigo, mas nenhuma pontuação após a última palavra-chave em sua lista. Você não precisa adicionar palavras-chave globais que se aplicam a todos os artigos, pois eles são gerenciados em outro lugar. 

### <a name="renaming-or-deleting-an-existing-article"></a>Renomeando ou excluindo um artigo existente

Se a alteração renomear ou excluir um artigo existente, adicione um redirecionamento. Dessa forma, qualquer pessoa com um link para o artigo existente ainda acabará no lugar certo. Os redirecionamentos são gerenciados pelo .openpublishing.redirection.jsno arquivo na raiz do repo.

Para adicionar um redirecionamento .openpublishing.redirection.js, adicione uma entrada à `redirections` matriz:

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- O `source_path` é o caminho do repositório relativo para o artigo antigo que você está removendo. Certifique-se de que o caminho comece `mixed-reality-docs/enthusiast-guide` com e termine com `.md` .
- O `redirect_url` é a URL pública relativa do artigo antigo para o novo artigo. Certifique-se de que essa URL **não contenha** ou , pois ela se refere à `mixed-reality-docs/enthusiast-guide` URL pública e não ao caminho do `.md` repositório. A vinculação a uma seção dentro do novo artigo usando `#section` é permitida. Você também pode usar um caminho absoluto para outro site aqui, se necessário.
- `redirect_document_id` indica se você gostaria de manter a ID do documento do arquivo anterior. O padrão é `false`. Use `true` se você quiser preservar o valor do atributo do artigo `ms.documentid` redirecionado. Se você preservar a ID do documento, os dados, como exibições de página e classificações, serão transferidos para o artigo de destino. Faça isso se o redirecionamento for principalmente renomeado e não um ponteiro para um artigo diferente que abrange apenas parte do mesmo conteúdo.

Se você adicionar um redirecionamento, exclua o arquivo antigo também.

### <a name="creating-a-new-article"></a>Criando um novo artigo

Use o fluxo de trabalho a *seguir para criar novos artigos* no GitHub documentação em um navegador da Web:

1. Crie um fork do branch 'mestre' do MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide (usando o botão Bifurcar no canto superior direito). 

   ![Bifurcar o branch mestre.](images/forkbranch.png)
2. Na pasta "mixed-reality/enthusiast-guide", selecione Criar **novo** arquivo no canto superior direito.
3. Crie um nome de página para o artigo (use hifens em vez de espaços e não use pontuação ou apóstrofos) e anexar ".md"

   ![Nomeia sua nova página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Crie o novo artigo de dentro da pasta "mixed-reality-docs/enthusiast". Você pode confirmar isso verificando "/mixed-reality-docs/enthusiast-guide" na nova linha de nome de arquivo.

4. Na parte superior da nova página, adicione o seguinte bloco de metadados:

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Preencha os campos de metadados relevantes de acordo com as instruções na [seção acima.](#updating-metadata)
6. Escreva o conteúdo do artigo [usando noções básicas de Markdown.](#markdown-basics)
7. Adicione uma `## See also` seção na parte inferior do artigo com links para outros artigos relevantes.
8. Quando terminar, selecione **Commit new file**.
9. Selecione **Nova solicitação de pull** e mesclar o branch 'mestre' do fork em MicrosoftDocs/mixed-reality/enthusiast-guide 'master' (certifique-se de que a seta está apontando para o caminho correto).

   ![Criar solicitação de pull de seu fork em MicrosoftDocs/mixed-reality/enthusiast-guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Trabalhando com ramificações

O [](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) repositório GitHub Guia de Usuários de Realidade Misturada utiliza duas ramificações pai principais: [Mestre](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), esse conteúdo pode ser revisado no [site](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)de preparação e ao vivo [para](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)o conteúdo que aparece no site [ao vivo.](/windows/mixed-reality/enthusiast-guide)

Ao fazer contribuições, envie sua PR (Solicitação de Pull) para o **branch** Mestre. Essa ramificação pode ser exibida no site de preparo e deve conter apenas as contribuições que estão prontas para serem publicadas online. Você também pode criar e enviar um branch com seu próprio nome de branch exclusivo que pode ser selecionado e exibido no site de preparação. (O **branch ao** vivo só é permitido para uso pelos administradores de conteúdo.)

## <a name="markdown-basics"></a>Noções básicas de markdown

Os recursos a seguir ajudarão você a aprender a editar a documentação usando a linguagem Markdown:

- [Noções básicas de Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Cartaz de referência de Markdown-at-a-glance](images/MarkdownPoster.pdf)
- [Recursos adicionais para escrever Markdown para docs.microsoft.com](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Adicionando tabelas

Devido à maneira como docs.microsoft.com tabelas de estilos, elas não terão bordas nem estilos personalizados, mesmo se você tentar CSS em linha. Ele parece funcionará por um curto período de tempo, mas, eventualmente, a plataforma retirará o estilo da tabela. Portanto, planeje com antecedência e mantenha as tabelas simples. [Aqui está um site que facilita as tabelas de Markdown.](https://www.tablesgenerator.com/markdown_tables)

A Extensão Markdown do [Docs para Visual Studio Code](/teamblog/docs-extension) também facilita a geração de tabelas se você estiver usando Visual Studio Code [(veja abaixo)](#using-visual-studio-code) para editar a documentação.

### <a name="adding-images"></a>Adição de imagens

Você precisará carregar suas imagens na pasta "mixed-reality-docs/images" no repo e, em seguida, fazer referência a elas adequadamente no artigo. As imagens aparecerão automaticamente em tamanho total, o que significa que imagens grandes preencherão toda a largura do artigo. É recomendável pré-fazer o pré-sizing das imagens antes de enviá-las. A largura recomendada está entre 600 e 700 pixels, embora você deva ter um tamanho para cima ou para baixo se for uma captura de tela densa ou uma fração de uma captura de tela, respectivamente.

>[!IMPORTANT]
>Você só pode carregar imagens no seu repo bifurcado antes de mesclar. Portanto, se você planeja adicionar imagens a um artigo, precisará usar o [Visual Studio Code](#using-visual-studio-code) para adicionar as imagens à pasta "imagens" do fork primeiro ou fazer o seguinte em um navegador da Web:
>
>1. Forked the MicrosoftDocs/mixed-reality repo( Forked the MicrosoftDocs/mixed-reality repo).
>2. Editou o artigo em sua bifurcação.
>3. Carregou as imagens que você está referenciando em seu artigo para a pasta "mixed-reality-docs/images" em sua bifurcação.
>4. Criou uma **solicitação de pull** para mesclar seu fork no branch 'mestre' MicrosoftDocs/mixed-reality.
>
>Para saber como configurar seu próprio repo bifurcado, siga as instruções para [criar um novo artigo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Visualizando seu trabalho

Durante a edição no GitHub por meio de um  navegador da Web, você pode selecionar a guia Visualização na parte superior da página para visualizar seu trabalho antes de se comprometer. 

>[!NOTE]
>Visualizar suas alterações no review.docs.microsoft.com está disponível apenas para funcionários da Microsoft

Funcionários da Microsoft: depois que suas contribuições foram mescladas no branch "mestre", você pode revisar o conteúdo antes que ele seja público em https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master . Encontre seu artigo usando o tabela de conteúdo na coluna à esquerda.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Edição no navegador versus edição com um cliente da área de trabalho

A edição no navegador é a maneira mais fácil de fazer alterações rápidas, no entanto, há algumas desvantagens:

- Você não obterá a verificação ort ort só.
- Você não tem nenhuma vinculação inteligente a outros artigos (você precisa digitar manualmente o nome do arquivo do artigo).
- Pode ser um problema carregar e referenciar imagens.

Se você preferir não lidar com esses problemas, use um cliente da área de trabalho [como Visual Studio Code](https://code.visualstudio.com/) com algumas extensões úteis [ao](#useful-extensions) contribuir.

## <a name="using-visual-studio-code"></a>Usar o Visual Studio Code

Pelos motivos listados [acima,](#editing-in-the-browser-vs-editing-with-a-desktop-client)você pode preferir usar um cliente da área de trabalho para editar a documentação em vez de um navegador da Web. O uso do [Visual Studio Code](https://code.visualstudio.com/) é recomendado.

### <a name="setup"></a>Instalação

Siga estas etapas para configurar Visual Studio Code para trabalhar com este repo:

1. Em um navegador da Web:
    1. Instale [o Git para seu computador.](https://git-scm.com/downloads)
    2. Instale o [Visual Studio Code](https://code.visualstudio.com/).
    3. [Bifurcar MicrosoftDocs/realidade misturada](#creating-a-new-article) se você ainda não fez isso.
    4. Na bifurcação, selecione **Clonar ou baixar** e copie a URL.
2. Crie um clone local da bifurcação Visual Studio Code:
    1. No menu **Exibir,** selecione **Paleta de Comandos**.
    2. Digite "Git: Clone".
    3. Colar a URL que você copiou.
    4. Escolha onde salvar o clone em seu computador.
    5. Selecione **Abrir o repo** no pop-up.

### <a name="editing-documentation"></a>Documentação de edição

Use o seguinte fluxo de trabalho para fazer alterações na documentação com Visual Studio Code:

>[!NOTE]
>Todas as diretrizes para [](#creating-a-new-article) [edição](#how-to-make-a-change) e criação de artigos e as noções básicas de edição de [Markdown,](#markdown-basics)acima, se aplica ao usar Visual Studio Code também.

1. Certifique-se de que o fork clonado esteja atualizado com o repo oficial.
   1. Em um navegador da Web, crie uma solicitação de pull para sincronizar alterações recentes de outros colaboradores no MicrosoftDocs/mixed-reality 'master' para sua bifurcação (certifique-se de que a seta está apontando para a direita).
      
      ![Sincronizar alterações do MicrosoftDocs/realidade misturada para sua bifurcação](images/sync_repos.PNG)
   2. No Visual Studio Code, selecione o botão de sincronização para sincronizar sua bifurcação atualizada recentemente com o clone local.
      
      ![Clique na imagem do botão de sincronização](images/sync_clone.png)
2. Crie ou edite artigos em seu repo clonado usando Visual Studio Code.
   1. Edite um ou mais artigos (adicione imagens à pasta "imagens", se necessário).
   2. **Salve** as alterações no **Explorer.**
      
      ![Escolha "Salvar tudo" no Explorer](images/explorer_save.png)
   3. **Faça commit de** todas as alterações **no Controle do Código-Fonte** (escreva a mensagem de commit quando solicitado).
      
      ![Escolha "Commit all" no controle do código-fonte](images/source_control_commit.png)
   4. Selecione o botão **de sincronização** para sincronizar suas alterações de volta à origem (seu fork GitHub).
      
      ![Clique no botão de sincronização](images/sync_back.png)
3. Em um navegador da Web, crie uma solicitação de pull para sincronizar novas alterações em seu fork de volta para MicrosoftDocs/mixed-reality 'master' (certifique-se de que a seta está apontando para o caminho correto).

   ![Criar solicitação de pull de seu fork para MicrosoftDocs/realidade misturada](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensões úteis

As seguintes Visual Studio Code extensões são úteis ao editar a documentação:

- [Extensão Markdown do Docs para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) – use **Alt+M** para abrir um menu de opções de autor de documentos, como:
   - Pesquisar e referenciar imagens que você carregou.
   - Adicione formatação como listas, tabelas e saídas específicas de documentos, como `>[!NOTE]` .
   - Pesquisar e referenciar links internos e indicadores (links para seções específicas em uma página).
   - Erros de formatação são realçadas (passe o mouse sobre o erro para saber mais).
- [Verificador Ortônico de](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) Código – palavras com ortagem inoclinada serão sublinhadas; Clique com o botão direito do mouse em uma palavra com o botão direito do mouse para alterá-la ou salvá-la no dicionário.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Usando problemas para fornecer comentários sobre Windows Mixed Reality guia de usuários

Para fornecer comentários ou apontar um problema, em vez de modificar diretamente as páginas de documentação [reais,](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) crie um problema e os proprietários de conteúdo fará o melhor para resolver o problema em tempo hábil.

Certifique-se de incluir o título do tópico e a URL se você estiver criando um problema em relação a uma página específica.

Obrigado por dar suporte a este conteúdo!