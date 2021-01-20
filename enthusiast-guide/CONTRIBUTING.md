---
title: Instruções de contribuição
description: Conheça as etapas e as diretrizes básicas para contribuir com o guia de entusiasta do Windows Mixed Reality. Agradecemos seus comentários, edições, adições e ajuda.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
appliesto:
- Windows 10
ms.openlocfilehash: 28ca1653019252c749fe5977a06bff4503800c10
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580187"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Contribuindo para o guia de entusiastas da realidade misturada

Agradecemos seu interesse no guia de entusiasta. Agradecemos seus comentários, edições, adições e ajuda no aprimoramento de nossos documentos. Esta página aborda as etapas e diretrizes básicas de contribuição.

> [!IMPORTANT]
> Todos os repositórios que publicam no docs.microsoft.com adotaram o [Código de Conduta de Software Livre da Microsoft](https://opensource.microsoft.com/codeofconduct/). Para saber mais, confira as [Perguntas frequentes sobre o Código de Conduta](https://opensource.microsoft.com/codeofconduct/faq/) ou entre em contato com [opencode@microsoft.com](mailto:opencode@microsoft.com) para enviar perguntas ou comentários.<br>
>
> Os [Termos de Uso de docs.microsoft.com](/legal/termsofuse) incluem correções secundárias ou esclarecimentos sobre a documentação, além de exemplos de código nos repositórios públicos. As alterações novas ou significativas gerarão um comentário na solicitação de pull pedindo o envio de um CLA (Contrato de Licença de Contribuição) online, caso você não seja um funcionário da Microsoft. Precisamos que você preencha o formulário online antes de aceitarmos sua solicitação pull.

## <a name="before-you-start"></a>Antes de começar

Se você ainda não tiver uma, precisará [criar uma conta do GitHub](https://github.com/join).

>[!NOTE]
>Se você for um funcionário da Microsoft, vincule sua conta do GitHub ao seu alias da Microsoft no [portal do Microsoft Open Source](https://repos.opensource.microsoft.com/). Junte-se às organizações **"Microsoft"** e **"MicrosoftDocs"** .

Ao configurar sua conta do GitHub, também recomendamos estas precauções de segurança:
- Crie uma [senha forte para sua conta do GitHub](https://github.com/settings/admin).
- Habilite [a autenticação de dois fatores](https://github.com/settings/two_factor_authentication/configure).
- Salve seus [códigos de recuperação](https://github.com/settings/auth/recovery-codes) em um local seguro.
- Atualize suas [configurações de perfil público](https://github.com/settings/profile).
   - Defina seu nome e considere definir seu *email público* para *não mostrar meu endereço de email*.
   - Recomendamos que você carregue uma imagem de perfil porque uma miniatura é mostrada nas páginas de docs para as quais você contribui.
- Se você planeja usar a linha de comando, considere configurar o [git Credential Manager para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). Dessa forma, você não precisará inserir sua senha toda vez que fizer uma contribuição.

O sistema de publicação está vinculado ao GitHub, portanto, essas etapas são importantes. Você será listado como autor ou colaborador para cada artigo usando seu alias do GitHub.

## <a name="how-to-make-a-change"></a>Como fazer uma alteração

| Para sugerir uma alteração aos documentos, siga estas etapas: | Capturas de tela |
| :------------------- | :--------: |
| 1. se você estiver exibindo uma página do Docs.microsoft.com, clique no botão **Editar** no canto superior direito da página.  Você será redirecionado para o arquivo de origem de Markdown correspondente no [repositório GitHub](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide). | ![Botão Editar](images/edit_button.jpg) |
| 2. se você ainda não tiver uma conta do GitHub, clique em **inscrever-** se no canto superior direito e crie uma nova conta. | ![Botão de inscrição](images/signup-for-github-button.png)|
| 3. na página correspondente do GitHub que é aberta, clique em Editar (o ícone de lápis). | ![Botão de lápis](images/pencil_button.jpg)|
| 4. no painel Editar arquivo, [atualize os metadados dos arquivos](#updating-metadata) e use o idioma de redução para alterar o conteúdo. ([Como escrever redução.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![Editar arquivo](images/edit-in-github.png)|
| 5. clique em Visualizar alterações para verificar se a formatação parece como esperado. | ![Visualizar alterações](images/edit-in-github.png)|
| 6. quando terminar, role até a parte inferior da página e clique em "propor alteração de arquivo", você verá uma página "comparando alterações", permitindo que você verifique suas alterações. Em seguida, clique no botão "criar solicitação de pull" para enviar suas alterações. Neste ponto, você terminou! | ![Propor uma alteração](images/propose.jpg)|

Depois de enviar as alterações (por meio de uma solicitação de pull), elas serão revisadas por um membro da equipe de documentação. Se sua solicitação for aceita, as atualizações serão publicadas no [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide) .

* Somente para revisão interna, você pode ver suas alterações em [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

### <a name="updating-metadata"></a>Atualizando metadados

Atualize os metadados na parte superior de cada artigo:
   * **título**: título da página que aparece na guia do navegador quando o artigo está sendo exibido. Os títulos de página são usados para SEO e indexação, portanto, não altere o título, a menos que seja necessário (embora isso seja menos crítico antes que a documentação fique pública).
   * **Descrição**: escreva uma breve descrição do conteúdo do artigo, que aumenta a SEO e a descoberta.
   * **autor**: se você for o proprietário principal da página, adicione seu alias do GitHub aqui.
   * **MS. Author**: se você for o proprietário principal da página, adicione seu alias da Microsoft aqui (você não precisa @microsoft.com , apenas o alias).
   * **MS. Date**: Atualize a data se você estiver adicionando conteúdo principal à página, mas não para correções como esclarecimento, formatação, gramática ou ortografia.
   * **palavras-** chave: o Word ajuda na SEO (otimização do mecanismo de pesquisa). Adicione palavras-chave, separadas por uma vírgula e um espaço, que são específicos do seu artigo, mas sem pontuação após a última palavra-chave em sua lista. Você não precisa adicionar palavras-chave globais que se aplicam a todos os artigos, pois elas são gerenciadas em outro lugar. 

### <a name="renaming-or-deleting-an-existing-article"></a>Renomeando ou excluindo um artigo existente

Se sua alteração for renomear ou excluir um artigo existente, certifique-se de adicionar um redirecionamento. Dessa forma, qualquer pessoa com um link para o artigo existente ainda será encerrada no lugar certo. Os redirecionamentos são gerenciados pelo .openpublishing.redirection.jsno arquivo na raiz do repositório.

Para adicionar um redirecionamento para .openpublishing.redirection.jsem, adicione uma entrada à `redirections` matriz:

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- O `source_path` é o caminho relativo do repositório para o artigo antigo que você está removendo. Verifique se o caminho começa com `mixed-reality-docs/enthusiast-guide` e termina com `.md` .
- O `redirect_url` é a URL pública relativa do artigo antigo para o novo artigo. Certifique-se de que essa URL **não** contenha `mixed-reality-docs/enthusiast-guide` ou `.md` , como se refere à URL pública e não ao caminho do repositório. É permitido vincular a uma seção dentro do novo artigo usando `#section` . Você também pode usar um caminho absoluto para outro site aqui, se necessário.
- `redirect_document_id` indica se você deseja manter a ID do documento do arquivo anterior. O padrão é `false`. Use `true` se você quiser preservar o `ms.documentid` valor do atributo do artigo Redirecionado. Se você preservar a ID do documento, os dados, como exibições de página e classificações, serão transferidos para o artigo de destino. Faça isso se o redirecionamento for basicamente uma renomeação, e não um ponteiro para um artigo diferente que cobre apenas alguns dos mesmos conteúdos.

Se você adicionar um redirecionamento, certifique-se de excluir o arquivo antigo também.

### <a name="creating-a-new-article"></a>Criando um novo artigo

Use o fluxo de trabalho a seguir para *criar novos artigos* no repositório de documentação por meio do GitHub em um navegador da Web:

1. Crie uma bifurcação do Branch de MicrosoftDocs/Mixed-Realm/Tree/docs/entusiasta-Guide ' mestre ' (usando o botão **Fork** no canto superior direito).

   ![Bifurcar a ramificação mestre.](images/forkbranch.png)
2. Na pasta "Mixed-Reality/entusiasta-Guide", selecione **criar novo arquivo** no canto superior direito.
3. Crie um nome de página para o artigo (use hifens em vez de espaços e não use pontuação ou apóstrofos) e acrescente ". MD"

   ![Nomeie sua nova página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Certifique-se de criar o novo artigo de dentro da pasta "Mixed-Realm-docs/entusiasta". Você pode confirmar isso verificando "/Mixed-Reality-docs/Enthusiast-Guide" na nova linha de nome de arquivo.

4. Na parte superior da sua nova página, adicione o seguinte bloco de metadados:

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

5. Preencha os campos de metadados relevantes de acordo com as instruções na [seção acima](#updating-metadata).
6. Escreva o conteúdo do artigo usando [noções básicas de redução](#markdown-basics).
7. Adicione uma `## See also` seção na parte inferior do artigo com links para outros artigos relevantes.
8. Quando terminar, selecione **confirmar novo arquivo**.
9. Selecione **nova solicitação de pull** e mescle a ramificação ' mestre ' de sua bifurcação em MicrosoftDocs/Mixed-Realm/entusiasta-Guide ' mestre ' (verifique se a seta está apontando da maneira correta).

   ![Criar solicitação de pull de sua bifurcação no MicrosoftDocs/Mixed-Realm/entusiasta-Guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Trabalhando com ramificações

O [repositório GitHub do guia de entusiasta da realidade misturada](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) utiliza dois branches pai principais: [mestre](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), esse conteúdo pode ser revisado no [site de preparo](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)e [ao vivo](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), para conteúdo exibido no [site ativo](/windows/mixed-reality/enthusiast-guide).

Ao fazer contribuições, envie sua solicitação de pull (PR) para o Branch **mestre** . Essa ramificação pode ser exibida no site de preparo e deve conter apenas as contribuições que estão prontas para serem publicadas online. Você também pode criar e enviar um Branch com seu próprio nome de Branch exclusivo que pode ser selecionado e exibido no site de preparo. (A ramificação **ao vivo** só é permitida para uso pelos administradores de conteúdo.)

## <a name="markdown-basics"></a>Noções básicas de markdown

Os recursos a seguir ajudarão você a aprender a editar a documentação usando a linguagem de redução:

- [Noções básicas de Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Cartaz de referência de visão geral](images/MarkdownPoster.pdf)
- [Recursos adicionais para a redução do texto para docs.microsoft.com](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Adicionando tabelas

Por causa da maneira como as tabelas de estilos docs.microsoft.com, elas não terão bordas ou estilos personalizados, mesmo que você experimente o CSS embutido. Parecerá funcionar por um curto período de tempo, mas eventualmente a plataforma removerá o estilo da tabela. Então, planeje com antecedência e mantenha suas tabelas simples. [Aqui está um site que facilita a redução das tabelas](https://www.tablesgenerator.com/markdown_tables).

A [extensão de redução de documentos para Visual Studio Code](/teamblog/docs-extension) também facilitará a geração de tabelas se você estiver usando [Visual Studio Code (veja abaixo)](#using-visual-studio-code) para editar a documentação.

### <a name="adding-images"></a>Adicionando imagens

Você precisará carregar suas imagens na pasta "Mixed-Reality docs/images" no repositório e, em seguida, referenciá-las adequadamente no artigo. As imagens aparecerão automaticamente em tamanho normal, o que significa que imagens grandes preencherão toda a largura do artigo. Recomendamos o dimensionamento prévio de suas imagens antes de carregá-las. A largura recomendada é entre 600 e 700 pixels, embora você deva dimensionar ou reduzir se for uma captura de tela densa ou uma fração de uma captura de tela, respectivamente.

>[!IMPORTANT]
>Você só pode carregar imagens para seu repositório bifurcado antes de Mesclar. Portanto, se você planeja adicionar imagens a um artigo, precisará [usar Visual Studio Code](#using-visual-studio-code) para adicionar as imagens à pasta "images" de sua bifurcação primeiro ou certifique-se de ter feito o seguinte em um navegador da Web:
>
>1. Bifurcado o repositório MicrosoftDocs/Mixed-Reality.
>2. Editou o artigo em sua bifurcação.
>3. Foram carregadas as imagens que você está referenciando em seu artigo para a pasta "Mixed-Realm-docs/images" em sua bifurcação.
>4. Criou uma **solicitação de pull** para mesclar sua bifurcação no Branch ' mestre ' da reality MicrosoftDocs/Mixed.
>
>Para saber como configurar seu próprio repositório bifurcado, siga as instruções para [criar um novo artigo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Visualizando seu trabalho

Ao editar no GitHub por meio de um navegador da Web, você pode selecionar a guia **Visualizar** próximo à parte superior da página para visualizar seu trabalho antes de confirmar. 

>[!NOTE]
>A visualização de suas alterações no review.docs.microsoft.com só está disponível para funcionários da Microsoft

Funcionários da Microsoft: depois que suas contribuições tiverem sido mescladas no Branch ' mestre ', você poderá examinar o conteúdo antes que ele seja público em https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master . Localize seu artigo usando o Sumário na coluna esquerda.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Editando no navegador versus editando com um cliente de desktop

A edição no navegador é a maneira mais fácil de fazer alterações rápidas, no entanto, há algumas desvantagens:

- Você não tem verificação ortográfica.
- Você não obtém nenhuma vinculação inteligente com outros artigos (você precisa digitar manualmente o nome do arquivo).
- Pode ser um trabalho difícil de carregar e fazer referência a imagens.

Se você preferir não lidar com esses problemas, use um cliente de desktop como [Visual Studio Code](https://code.visualstudio.com/) com algumas [extensões úteis](#useful-extensions) ao contribuir.

## <a name="using-visual-studio-code"></a>Usar o Visual Studio Code

Pelos motivos listados [acima](#editing-in-the-browser-vs-editing-with-a-desktop-client), você pode preferir usar um cliente de desktop para editar a documentação em vez de um navegador da Web. É recomendável usar [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Instalação

Siga estas etapas para configurar Visual Studio Code para trabalhar com este repositório:

1. Em um navegador da Web:
    1. Instale [o Git para seu computador](https://git-scm.com/downloads).
    2. Instale o [Visual Studio Code](https://code.visualstudio.com/).
    3. [Bifurcação MicrosoftDocs/Mixed-Realm,](#creating-a-new-article) se ainda não tiver feito isso.
    4. Em sua bifurcação, selecione **clonar ou baixar** e copie a URL.
2. Crie um clone local de sua bifurcação no Visual Studio Code:
    1. No menu **Exibir** , selecione **paleta de comandos**.
    2. Digite "Git: clone".
    3. Cole a URL que você copiou.
    4. Escolha onde salvar o clone em seu PC.
    5. Selecione **abrir repositório** no pop-up.

### <a name="editing-documentation"></a>Editando a documentação

Use o seguinte fluxo de trabalho para fazer alterações na documentação com Visual Studio Code:

>[!NOTE]
>Todas as diretrizes para [edição](#how-to-make-a-change) e [criação](#creating-a-new-article) de artigos, e os [fundamentos de redução de edição](#markdown-basics), a partir de acima aplicam-se também ao usar o Visual Studio Code.

1. Certifique-se de que sua bifurcação clonada esteja atualizada com o repositório oficial.
   1. Em um navegador da Web, crie uma solicitação de pull para sincronizar alterações recentes de outros colaboradores em MicrosoftDocs/Mixed-Realm ' Master ' para sua bifurcação (verifique se a seta está apontando da maneira correta).
      
      ![Sincronizar alterações de MicrosoftDocs/Mixed-realm para sua bifurcação](images/sync_repos.PNG)
   2. Em Visual Studio Code, selecione o botão Sincronizar para sincronizar sua bifurcação atualizada atualizada para o clone local.
      
      ![Clique na imagem do botão Sincronizar](images/sync_clone.png)
2. Crie ou edite artigos em seu repositório clonado usando Visual Studio Code.
   1. Edite um ou mais artigos (adicione imagens à pasta "imagens", se necessário).
   2. **Salve** as alterações no **Explorer**.
      
      ![Escolha "salvar tudo" no Gerenciador](images/explorer_save.png)
   3. **Confirmar todas** as alterações no **controle do código-fonte** (gravar mensagem de confirmação quando solicitado).
      
      ![Escolha "confirmar tudo" no controle do código-fonte](images/source_control_commit.png)
   4. Selecione o botão **sincronizar** para sincronizar suas alterações de volta à origem (sua bifurcação no GitHub).
      
      ![Clique no botão Sincronizar](images/sync_back.png)
3. Em um navegador da Web, crie uma solicitação de pull para sincronizar novas alterações na bifurcação de volta para MicrosoftDocs/Mixed-Realm ' Master ' (verifique se a seta está apontando da maneira correta).

   ![Criar solicitação de pull de sua bifurcação em MicrosoftDocs/Mixed-Realm](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensões úteis

As seguintes extensões de Visual Studio Code são úteis ao editar a documentação:

- [Extensão de redução de documentos para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -use **ALT + M** para abrir um menu de opções de criação de docs como:
   - Pesquisar e fazer referência a imagens que você carregou.
   - Adicione formatação como listas, tabelas e chamadas de documentos específicas de docs como `>[!NOTE]` .
   - Pesquisar e referenciar links internos e indicadores (links para seções específicas em uma página).
   - Erros de formatação são realçados (passe o mouse sobre o erro para saber mais).
- [Verificador ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -palavras incorretas serão sublinhadas; Clique com o botão direito do mouse em uma palavra incorreta para alterá-la ou salvá-la no dicionário.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Usando problemas para fornecer comentários sobre o guia de entusiastas do Windows Mixed Reality

Para fornecer comentários ou indicar um problema, em vez de modificar diretamente as páginas de documentação reais, [crie um problema](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) e os proprietários do conteúdo farão o melhor para resolver o problema em tempo hábil.

Certifique-se de incluir o título do tópico e a URL se você estiver criando um problema com relação a uma página específica.

Obrigado por dar suporte a esse conteúdo!