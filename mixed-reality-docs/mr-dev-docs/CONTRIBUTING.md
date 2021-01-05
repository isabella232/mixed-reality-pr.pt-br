---
title: Instruções de contribuição
description: Saiba como contribuir para os documentos de desenvolvedor da realidade misturada na plataforma docs.microsoft.com usando a redução do GitHub.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: 47689a53557e6ce9b97d0e9d834a70fb0a7786d0
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865411"
---
# <a name="contributing-to-mixed-reality-developer-documentation"></a><span data-ttu-id="76a4c-103">Contribuindo para a documentação do desenvolvedor de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="76a4c-103">Contributing to Mixed Reality developer documentation</span></span>

<span data-ttu-id="76a4c-104">Bem-vindo ao [repositório público para documentação do desenvolvedor de realidade misturada](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="76a4c-104">Welcome to the [public repo for Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="76a4c-105">Todos os artigos que você criar ou editar neste repositório **estarão visíveis para o público.**</span><span class="sxs-lookup"><span data-stu-id="76a4c-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="76a4c-106">Os documentos de realidade misturada agora estão na plataforma docs.microsoft.com, que usa a redução de tipo de GitHub com recursos de Markdig.</span><span class="sxs-lookup"><span data-stu-id="76a4c-106">The Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown with Markdig features.</span></span> <span data-ttu-id="76a4c-107">O conteúdo editado neste repositório é formatado em páginas estilizadas que aparecem em https://docs.microsoft.com/windows/mixed-reality .</span><span class="sxs-lookup"><span data-stu-id="76a4c-107">The content you edit in this repo gets formatted into stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="76a4c-108">Esta página aborda as etapas e diretrizes básicas de contribuição e links para noções básicas de redução.</span><span class="sxs-lookup"><span data-stu-id="76a4c-108">This page covers the basic steps and guidelines for contributing and links to Markdown basics.</span></span> <span data-ttu-id="76a4c-109">Agradecemos a sua contribuição.</span><span class="sxs-lookup"><span data-stu-id="76a4c-109">Thank you for your contribution!</span></span>

## <a name="available-repos"></a><span data-ttu-id="76a4c-110">Repositórios disponíveis</span><span class="sxs-lookup"><span data-stu-id="76a4c-110">Available repos</span></span>

| <span data-ttu-id="76a4c-111">Nome do repositório</span><span class="sxs-lookup"><span data-stu-id="76a4c-111">Repository name</span></span> | <span data-ttu-id="76a4c-112">URL</span><span class="sxs-lookup"><span data-stu-id="76a4c-112">URL</span></span> |
| --- | --- |
| <span data-ttu-id="76a4c-113">Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="76a4c-113">Mixed Reality</span></span> | [<span data-ttu-id="76a4c-114">MicrosoftDocs/misto – realidade</span><span class="sxs-lookup"><span data-stu-id="76a4c-114">MicrosoftDocs/mixed-reality</span></span>](https://docs.microsoft.com/windows/mixed-reality) |
| <span data-ttu-id="76a4c-115">Guia dos entusiastas do VR</span><span class="sxs-lookup"><span data-stu-id="76a4c-115">VR Enthusiasts Guide</span></span> | [<span data-ttu-id="76a4c-116">MicrosoftDocs/misto-realidade/entusiasta-guia</span><span class="sxs-lookup"><span data-stu-id="76a4c-116">MicrosoftDocs/mixed-reality/enthusiast-guide</span></span>](https://github.com/MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide) |
| <span data-ttu-id="76a4c-117">HoloLens</span><span class="sxs-lookup"><span data-stu-id="76a4c-117">HoloLens</span></span> | [<span data-ttu-id="76a4c-118">MicrosoftDocs/HoloLens</span><span class="sxs-lookup"><span data-stu-id="76a4c-118">MicrosoftDocs/HoloLens</span></span>](https://github.com/MicrosoftDocs/Hololens) |

## <a name="before-you-start"></a><span data-ttu-id="76a4c-119">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="76a4c-119">Before you start</span></span>

<span data-ttu-id="76a4c-120">Se você ainda não tiver uma, precisará [criar uma conta do GitHub](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="76a4c-120">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="76a4c-121">Se você for um funcionário da Microsoft, vincule sua conta do GitHub ao seu alias da Microsoft no [portal do Microsoft Open Source](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="76a4c-121">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="76a4c-122">Junte-se às organizações **"Microsoft"** e **"MicrosoftDocs"** .</span><span class="sxs-lookup"><span data-stu-id="76a4c-122">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations.</span></span>

<span data-ttu-id="76a4c-123">Ao configurar sua conta do GitHub, também recomendamos estas precauções de segurança:</span><span class="sxs-lookup"><span data-stu-id="76a4c-123">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="76a4c-124">Crie uma [senha forte para sua conta do GitHub](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="76a4c-124">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="76a4c-125">Habilite [a autenticação de dois fatores](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="76a4c-125">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="76a4c-126">Salve seus [códigos de recuperação](https://github.com/settings/auth/recovery-codes) em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="76a4c-126">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="76a4c-127">Atualize suas [configurações de perfil público](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="76a4c-127">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="76a4c-128">Defina seu nome e considere definir seu *email público* para *não mostrar meu endereço de email*.</span><span class="sxs-lookup"><span data-stu-id="76a4c-128">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="76a4c-129">Recomendamos que você carregue uma imagem de perfil porque uma miniatura é mostrada nas páginas de docs para as quais você contribui.</span><span class="sxs-lookup"><span data-stu-id="76a4c-129">We recommend you upload a profile picture because a thumbnail is shown on docs pages you contribute to.</span></span>
- <span data-ttu-id="76a4c-130">Se você planeja usar a linha de comando, considere configurar o [git Credential Manager para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="76a4c-130">If you plan to use the command line, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span></span> <span data-ttu-id="76a4c-131">Dessa forma, você não precisará inserir sua senha toda vez que fizer uma contribuição.</span><span class="sxs-lookup"><span data-stu-id="76a4c-131">That way, you won't have to enter your password every time you make a contribution.</span></span>

<span data-ttu-id="76a4c-132">O sistema de publicação está vinculado ao GitHub, portanto, essas etapas são importantes.</span><span class="sxs-lookup"><span data-stu-id="76a4c-132">The publishing system is tied to GitHub, so these steps are important.</span></span> <span data-ttu-id="76a4c-133">Você será listado como autor ou colaborador para cada artigo usando seu alias do GitHub.</span><span class="sxs-lookup"><span data-stu-id="76a4c-133">You'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="76a4c-134">Editando um artigo existente</span><span class="sxs-lookup"><span data-stu-id="76a4c-134">Editing an existing article</span></span>

<span data-ttu-id="76a4c-135">Use o seguinte fluxo de trabalho para fazer atualizações em *um artigo existente* por meio do GitHub em um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="76a4c-135">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="76a4c-136">Navegue até o artigo que você deseja editar na pasta "Mixed-realde docs".</span><span class="sxs-lookup"><span data-stu-id="76a4c-136">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="76a4c-137">Selecione o botão Editar (ícone de lápis) no canto superior direito, que irá bifurcar automaticamente uma ramificação descartável para fora do Branch ' mestre '.</span><span class="sxs-lookup"><span data-stu-id="76a4c-137">Select the edit button (pencil icon) in the top right, which will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Edite um artigo.](images/editpage.png)
3. <span data-ttu-id="76a4c-139">Edite o conteúdo do artigo de acordo com as ["Noções básicas sobre redução"](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="76a4c-139">Edit the content of the article according to the ["Markdown basics"](#markdown-basics).</span></span>
4. <span data-ttu-id="76a4c-140">Atualize os metadados na parte superior de cada artigo:</span><span class="sxs-lookup"><span data-stu-id="76a4c-140">Update metadata at the top of each article:</span></span>
   * <span data-ttu-id="76a4c-141">**título**: título da página que aparece na guia do navegador quando o artigo está sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="76a4c-141">**title**: Page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="76a4c-142">Os títulos de página são usados para SEO e indexação, portanto, não altere o título, a menos que seja necessário (embora isso seja menos crítico antes que a documentação fique pública).</span><span class="sxs-lookup"><span data-stu-id="76a4c-142">Page titles are used for SEO and indexing, so don't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="76a4c-143">**Descrição**: escreva uma breve descrição do conteúdo do artigo, que aumenta a SEO e a descoberta.</span><span class="sxs-lookup"><span data-stu-id="76a4c-143">**description**: Write a brief description of the article's content, which boosts SEO and discovery.</span></span>
   * <span data-ttu-id="76a4c-144">**autor**: se você for o proprietário principal da página, adicione seu alias do GitHub aqui.</span><span class="sxs-lookup"><span data-stu-id="76a4c-144">**author**: If you're the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="76a4c-145">**MS. Author**: se você for o proprietário principal da página, adicione seu alias da Microsoft aqui (você não precisa @microsoft.com , apenas o alias).</span><span class="sxs-lookup"><span data-stu-id="76a4c-145">**ms.author**: If you're the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="76a4c-146">**MS. Date**: Atualize a data se você estiver adicionando conteúdo principal à página, mas não para correções como esclarecimento, formatação, gramática ou ortografia.</span><span class="sxs-lookup"><span data-stu-id="76a4c-146">**ms.date**: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="76a4c-147">**palavras-** chave: o Word ajuda na SEO (otimização do mecanismo de pesquisa).</span><span class="sxs-lookup"><span data-stu-id="76a4c-147">**keywords**: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="76a4c-148">Adicione palavras-chave, separadas por uma vírgula e um espaço, que são específicos do seu artigo, mas sem pontuação após a última palavra-chave em sua lista.</span><span class="sxs-lookup"><span data-stu-id="76a4c-148">Add keywords, separated by a comma and a space, that are specific to your article, but no punctuation after the last keyword in your list.</span></span> <span data-ttu-id="76a4c-149">Você não precisa adicionar palavras-chave globais que se aplicam a todos os artigos, pois elas são gerenciadas em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="76a4c-149">You don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="76a4c-150">Depois de concluir as edições do artigo, role para baixo e selecione **propor alteração de arquivo**.</span><span class="sxs-lookup"><span data-stu-id="76a4c-150">When you've completed your article edits, scroll down and select **Propose file change**.</span></span>
6. <span data-ttu-id="76a4c-151">Na página seguinte, selecione **criar solicitação de pull** para mesclar seu Branch criado automaticamente em ' mestre '.</span><span class="sxs-lookup"><span data-stu-id="76a4c-151">On the next page, select **Create pull request** to merge your automatically created branch into 'master.'</span></span>
7. <span data-ttu-id="76a4c-152">Repita as etapas acima para o próximo artigo que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="76a4c-152">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="76a4c-153">Renomeando ou excluindo um artigo existente</span><span class="sxs-lookup"><span data-stu-id="76a4c-153">Renaming or deleting an existing article</span></span>

<span data-ttu-id="76a4c-154">Se sua alteração for renomear ou excluir um artigo existente, certifique-se de adicionar um redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="76a4c-154">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="76a4c-155">Dessa forma, qualquer pessoa com um link para o artigo existente ainda será encerrada no lugar certo.</span><span class="sxs-lookup"><span data-stu-id="76a4c-155">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="76a4c-156">Os redirecionamentos são gerenciados pelo .openpublishing.redirection.jsno arquivo na raiz do repositório.</span><span class="sxs-lookup"><span data-stu-id="76a4c-156">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="76a4c-157">Para adicionar um redirecionamento para .openpublishing.redirection.jsem, adicione uma entrada à `redirections` matriz:</span><span class="sxs-lookup"><span data-stu-id="76a4c-157">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="76a4c-158">O `source_path` é o caminho relativo do repositório para o artigo antigo que você está removendo.</span><span class="sxs-lookup"><span data-stu-id="76a4c-158">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="76a4c-159">Verifique se o caminho começa com `mixed-reality-docs` e termina com `.md` .</span><span class="sxs-lookup"><span data-stu-id="76a4c-159">Be sure the path starts with `mixed-reality-docs` and ends with `.md`.</span></span>
- <span data-ttu-id="76a4c-160">O `redirect_url` é a URL pública relativa do artigo antigo para o novo artigo.</span><span class="sxs-lookup"><span data-stu-id="76a4c-160">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="76a4c-161">Certifique-se de que essa URL **não** contenha `mixed-reality-docs` ou `.md` , como se refere à URL pública e não ao caminho do repositório.</span><span class="sxs-lookup"><span data-stu-id="76a4c-161">Be sure that this URL **doesn't** contain `mixed-reality-docs` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="76a4c-162">É permitido vincular a uma seção dentro do novo artigo usando `#section` .</span><span class="sxs-lookup"><span data-stu-id="76a4c-162">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="76a4c-163">Você também pode usar um caminho absoluto para outro site aqui, se necessário.</span><span class="sxs-lookup"><span data-stu-id="76a4c-163">You can also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="76a4c-164">`redirect_document_id` indica se você deseja manter a ID do documento do arquivo anterior.</span><span class="sxs-lookup"><span data-stu-id="76a4c-164">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="76a4c-165">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="76a4c-165">The default is `false`.</span></span> <span data-ttu-id="76a4c-166">Use `true` se você quiser preservar o `ms.documentid` valor do atributo do artigo Redirecionado.</span><span class="sxs-lookup"><span data-stu-id="76a4c-166">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="76a4c-167">Se você preservar a ID do documento, os dados, como exibições de página e classificações, serão transferidos para o artigo de destino.</span><span class="sxs-lookup"><span data-stu-id="76a4c-167">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="76a4c-168">Faça isso se o redirecionamento for basicamente uma renomeação, e não um ponteiro para um artigo diferente que cobre apenas alguns dos mesmos conteúdos.</span><span class="sxs-lookup"><span data-stu-id="76a4c-168">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="76a4c-169">Se você adicionar um redirecionamento, certifique-se de excluir o arquivo antigo também.</span><span class="sxs-lookup"><span data-stu-id="76a4c-169">If you add a redirect, be sure to delete the old file as well.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="76a4c-170">Criando um novo artigo</span><span class="sxs-lookup"><span data-stu-id="76a4c-170">Creating a new article</span></span>

<span data-ttu-id="76a4c-171">Use o fluxo de trabalho a seguir para *criar novos artigos* no repositório de documentação por meio do GitHub em um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="76a4c-171">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="76a4c-172">Crie uma bifurcação da ramificação "mestre" do MicrosoftDocs/Mixed-Realm (usando o botão **bifurcar** no canto superior direito).</span><span class="sxs-lookup"><span data-stu-id="76a4c-172">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Bifurcar a ramificação mestre.](images/forkbranch.png)
2. <span data-ttu-id="76a4c-174">Na pasta "Mixed-Reality-docs", selecione **criar novo arquivo** no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="76a4c-174">In the "mixed-reality-docs" folder, select **Create new file** in the top right.</span></span>
3. <span data-ttu-id="76a4c-175">Crie um nome de página para o artigo (use hifens em vez de espaços e não use pontuação ou apóstrofos) e acrescente ". MD"</span><span class="sxs-lookup"><span data-stu-id="76a4c-175">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Nomeie sua nova página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="76a4c-177">Certifique-se de criar o novo artigo de dentro da pasta "Mixed-Realm docs".</span><span class="sxs-lookup"><span data-stu-id="76a4c-177">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="76a4c-178">Você pode confirmar isso verificando "/Mixed-Reality-docs/" na nova linha de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="76a4c-178">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="76a4c-179">Na parte superior da sua nova página, adicione o seguinte bloco de metadados:</span><span class="sxs-lookup"><span data-stu-id="76a4c-179">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="76a4c-180">Preencha os campos de metadados relevantes de acordo com as instruções na [seção acima](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="76a4c-180">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="76a4c-181">Escreva o conteúdo do artigo usando [noções básicas de redução](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="76a4c-181">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="76a4c-182">Adicione uma `## See also` seção na parte inferior do artigo com links para outros artigos relevantes.</span><span class="sxs-lookup"><span data-stu-id="76a4c-182">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="76a4c-183">Quando terminar, selecione **confirmar novo arquivo**.</span><span class="sxs-lookup"><span data-stu-id="76a4c-183">When finished, select **Commit new file**.</span></span>
9. <span data-ttu-id="76a4c-184">Selecione **nova solicitação de pull** e mescle a ramificação ' mestre ' de sua bifurcação em MicrosoftDocs/Mixed-Realm ' Master ' (verifique se a seta está apontando da maneira correta).</span><span class="sxs-lookup"><span data-stu-id="76a4c-184">Select **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Criar solicitação de pull de sua bifurcação em MicrosoftDocs/Mixed-Realm](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="76a4c-186">Noções básicas de markdown</span><span class="sxs-lookup"><span data-stu-id="76a4c-186">Markdown basics</span></span>

<span data-ttu-id="76a4c-187">Os recursos a seguir ajudarão você a aprender a editar a documentação usando a linguagem de redução:</span><span class="sxs-lookup"><span data-stu-id="76a4c-187">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="76a4c-188">Noções básicas de Markdown</span><span class="sxs-lookup"><span data-stu-id="76a4c-188">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="76a4c-189">Cartaz de referência de visão geral</span><span class="sxs-lookup"><span data-stu-id="76a4c-189">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="76a4c-190">Recursos adicionais para a redução do texto para docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="76a4c-190">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="76a4c-191">Adicionando tabelas</span><span class="sxs-lookup"><span data-stu-id="76a4c-191">Adding tables</span></span>

<span data-ttu-id="76a4c-192">Por causa da maneira como as tabelas de estilos docs.microsoft.com, elas não terão bordas ou estilos personalizados, mesmo que você experimente o CSS embutido.</span><span class="sxs-lookup"><span data-stu-id="76a4c-192">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="76a4c-193">Parecerá funcionar por um curto período de tempo, mas eventualmente a plataforma removerá o estilo da tabela.</span><span class="sxs-lookup"><span data-stu-id="76a4c-193">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="76a4c-194">Então, planeje com antecedência e mantenha suas tabelas simples.</span><span class="sxs-lookup"><span data-stu-id="76a4c-194">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="76a4c-195">[Aqui está um site que facilita a redução das tabelas](https://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="76a4c-195">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="76a4c-196">A [extensão de redução de documentos para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) também facilitará a geração de tabelas se você estiver usando [Visual Studio Code (veja abaixo)](#using-visual-studio-code) para editar a documentação.</span><span class="sxs-lookup"><span data-stu-id="76a4c-196">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="76a4c-197">Adicionando imagens</span><span class="sxs-lookup"><span data-stu-id="76a4c-197">Adding images</span></span>

<span data-ttu-id="76a4c-198">Você precisará carregar suas imagens na pasta "Mixed-Reality docs/images" no repositório e, em seguida, referenciá-las adequadamente no artigo.</span><span class="sxs-lookup"><span data-stu-id="76a4c-198">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="76a4c-199">As imagens aparecerão automaticamente em tamanho normal, o que significa que imagens grandes preencherão toda a largura do artigo.</span><span class="sxs-lookup"><span data-stu-id="76a4c-199">Images will automatically show up at full-size, which means large images will fill the entire width of the article.</span></span> <span data-ttu-id="76a4c-200">Recomendamos o dimensionamento prévio de suas imagens antes de carregá-las.</span><span class="sxs-lookup"><span data-stu-id="76a4c-200">We recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="76a4c-201">A largura recomendada é entre 600 e 700 pixels, embora você deva dimensionar ou reduzir se for uma captura de tela densa ou uma fração de uma captura de tela, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="76a4c-201">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="76a4c-202">Você só pode carregar imagens para seu repositório bifurcado antes de Mesclar.</span><span class="sxs-lookup"><span data-stu-id="76a4c-202">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="76a4c-203">Portanto, se você planeja adicionar imagens a um artigo, precisará [usar Visual Studio Code](#using-visual-studio-code) para adicionar as imagens à pasta "images" de sua bifurcação primeiro ou certifique-se de ter feito o seguinte em um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="76a4c-203">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="76a4c-204">Bifurcado o repositório MicrosoftDocs/Mixed-Reality.</span><span class="sxs-lookup"><span data-stu-id="76a4c-204">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="76a4c-205">Editou o artigo em sua bifurcação.</span><span class="sxs-lookup"><span data-stu-id="76a4c-205">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="76a4c-206">Foram carregadas as imagens que você está referenciando em seu artigo para a pasta "Mixed-Realm-docs/images" em sua bifurcação.</span><span class="sxs-lookup"><span data-stu-id="76a4c-206">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="76a4c-207">Criou uma **solicitação de pull** para mesclar sua bifurcação no Branch ' mestre ' da reality MicrosoftDocs/Mixed.</span><span class="sxs-lookup"><span data-stu-id="76a4c-207">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="76a4c-208">Para saber como configurar seu próprio repositório bifurcado, siga as instruções para [criar um novo artigo](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="76a4c-208">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="76a4c-209">Visualizando seu trabalho</span><span class="sxs-lookup"><span data-stu-id="76a4c-209">Previewing your work</span></span>

<span data-ttu-id="76a4c-210">Ao editar no GitHub por meio de um navegador da Web, você pode selecionar a guia **Visualizar** próximo à parte superior da página para visualizar seu trabalho antes de confirmar.</span><span class="sxs-lookup"><span data-stu-id="76a4c-210">While editing in GitHub via a web browser, you can select the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="76a4c-211">A visualização de suas alterações no review.docs.microsoft.com só está disponível para funcionários da Microsoft</span><span class="sxs-lookup"><span data-stu-id="76a4c-211">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="76a4c-212">Funcionários da Microsoft: depois que suas contribuições tiverem sido mescladas no Branch ' mestre ', você poderá examinar o conteúdo antes que ele seja público em https://review.docs.microsoft.com/windows/mixed-reality?branch=master .</span><span class="sxs-lookup"><span data-stu-id="76a4c-212">Microsoft employees: once your contributions have been merged into the 'master' branch, you can review the content before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master.</span></span> <span data-ttu-id="76a4c-213">Localize seu artigo usando o Sumário na coluna esquerda.</span><span class="sxs-lookup"><span data-stu-id="76a4c-213">Find your article using the table of contents in the left column.</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="76a4c-214">Editando no navegador versus editando com um cliente de desktop</span><span class="sxs-lookup"><span data-stu-id="76a4c-214">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="76a4c-215">A edição no navegador é a maneira mais fácil de fazer alterações rápidas, no entanto, há algumas desvantagens:</span><span class="sxs-lookup"><span data-stu-id="76a4c-215">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="76a4c-216">Você não tem verificação ortográfica.</span><span class="sxs-lookup"><span data-stu-id="76a4c-216">You don't get spell-check.</span></span>
- <span data-ttu-id="76a4c-217">Você não obtém nenhuma vinculação inteligente com outros artigos (você precisa digitar manualmente o nome do arquivo).</span><span class="sxs-lookup"><span data-stu-id="76a4c-217">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="76a4c-218">Pode ser um trabalho difícil de carregar e fazer referência a imagens.</span><span class="sxs-lookup"><span data-stu-id="76a4c-218">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="76a4c-219">Se você preferir não lidar com esses problemas, use um cliente de desktop como [Visual Studio Code](https://code.visualstudio.com/) com algumas [extensões úteis](#useful-extensions) ao contribuir.</span><span class="sxs-lookup"><span data-stu-id="76a4c-219">If you'd rather not deal with these issues, use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) when contributing.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="76a4c-220">Usar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="76a4c-220">Using Visual Studio Code</span></span>

<span data-ttu-id="76a4c-221">Pelos motivos listados [acima](#editing-in-the-browser-vs-editing-with-a-desktop-client), você pode preferir usar um cliente de desktop para editar a documentação em vez de um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="76a4c-221">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="76a4c-222">É recomendável usar [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="76a4c-222">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="76a4c-223">Instalação</span><span class="sxs-lookup"><span data-stu-id="76a4c-223">Setup</span></span>

<span data-ttu-id="76a4c-224">Siga estas etapas para configurar Visual Studio Code para trabalhar com este repositório:</span><span class="sxs-lookup"><span data-stu-id="76a4c-224">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="76a4c-225">Em um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="76a4c-225">In a web browser:</span></span>
    1. <span data-ttu-id="76a4c-226">Instale [o Git para seu computador](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="76a4c-226">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="76a4c-227">Instale o [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="76a4c-227">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="76a4c-228">[Bifurcação MicrosoftDocs/Mixed-Realm,](#creating-a-new-article) se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="76a4c-228">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="76a4c-229">Em sua bifurcação, selecione **clonar ou baixar** e copie a URL.</span><span class="sxs-lookup"><span data-stu-id="76a4c-229">In your fork, select **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="76a4c-230">Crie um clone local de sua bifurcação no Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="76a4c-230">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="76a4c-231">No menu **Exibir** , selecione **paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="76a4c-231">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="76a4c-232">Digite "Git: clone".</span><span class="sxs-lookup"><span data-stu-id="76a4c-232">Type "Git: Clone."</span></span>
    3. <span data-ttu-id="76a4c-233">Cole a URL que você copiou.</span><span class="sxs-lookup"><span data-stu-id="76a4c-233">Paste the URL you copied.</span></span>
    4. <span data-ttu-id="76a4c-234">Escolha onde salvar o clone em seu PC.</span><span class="sxs-lookup"><span data-stu-id="76a4c-234">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="76a4c-235">Selecione **abrir repositório** no pop-up.</span><span class="sxs-lookup"><span data-stu-id="76a4c-235">Select **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="76a4c-236">Editando a documentação</span><span class="sxs-lookup"><span data-stu-id="76a4c-236">Editing documentation</span></span>

<span data-ttu-id="76a4c-237">Use o seguinte fluxo de trabalho para fazer alterações na documentação com Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="76a4c-237">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="76a4c-238">Todas as diretrizes para [edição](#editing-an-existing-article) e [criação](#creating-a-new-article) de artigos, e os [fundamentos de redução de edição](#markdown-basics), a partir de acima aplicam-se também ao usar o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="76a4c-238">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="76a4c-239">Certifique-se de que sua bifurcação clonada esteja atualizada com o repositório oficial.</span><span class="sxs-lookup"><span data-stu-id="76a4c-239">Make sure your cloned fork is up to date with the official repo.</span></span>
   1. <span data-ttu-id="76a4c-240">Em um navegador da Web, crie uma solicitação de pull para sincronizar alterações recentes de outros colaboradores em MicrosoftDocs/Mixed-Realm ' Master ' para sua bifurcação (verifique se a seta está apontando da maneira correta).</span><span class="sxs-lookup"><span data-stu-id="76a4c-240">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Sincronizar alterações de MicrosoftDocs/Mixed-realm para sua bifurcação](images/sync_repos.PNG)
   2. <span data-ttu-id="76a4c-242">Em Visual Studio Code, selecione o botão Sincronizar para sincronizar sua bifurcação atualizada atualizada para o clone local.</span><span class="sxs-lookup"><span data-stu-id="76a4c-242">In Visual Studio Code, select the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Clique na imagem do botão Sincronizar](images/sync_clone.png)
2. <span data-ttu-id="76a4c-244">Crie ou edite artigos em seu repositório clonado usando Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="76a4c-244">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="76a4c-245">Edite um ou mais artigos (adicione imagens à pasta "imagens", se necessário).</span><span class="sxs-lookup"><span data-stu-id="76a4c-245">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="76a4c-246">**Salve** as alterações no **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="76a4c-246">**Save** changes in **Explorer**.</span></span>
      
      ![Escolha "salvar tudo" no Gerenciador](images/explorer_save.png)
   3. <span data-ttu-id="76a4c-248">**Confirmar todas** as alterações no **controle do código-fonte** (gravar mensagem de confirmação quando solicitado).</span><span class="sxs-lookup"><span data-stu-id="76a4c-248">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Escolha "confirmar tudo" no controle do código-fonte](images/source_control_commit.png)
   4. <span data-ttu-id="76a4c-250">Selecione o botão **sincronizar** para sincronizar suas alterações de volta à origem (sua bifurcação no GitHub).</span><span class="sxs-lookup"><span data-stu-id="76a4c-250">Select the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Clique no botão Sincronizar](images/sync_back.png)
3. <span data-ttu-id="76a4c-252">Em um navegador da Web, crie uma solicitação de pull para sincronizar novas alterações na bifurcação de volta para MicrosoftDocs/Mixed-Realm ' Master ' (verifique se a seta está apontando da maneira correta).</span><span class="sxs-lookup"><span data-stu-id="76a4c-252">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Criar solicitação de pull de sua bifurcação em MicrosoftDocs/Mixed-Realm](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="76a4c-254">Extensões úteis</span><span class="sxs-lookup"><span data-stu-id="76a4c-254">Useful extensions</span></span>

<span data-ttu-id="76a4c-255">As seguintes extensões de Visual Studio Code são úteis ao editar a documentação:</span><span class="sxs-lookup"><span data-stu-id="76a4c-255">The following Visual Studio Code extensions are useful when editing documentation:</span></span>

- <span data-ttu-id="76a4c-256">[Extensão de redução de documentos para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -use **ALT + M** para abrir um menu de opções de criação de docs como:</span><span class="sxs-lookup"><span data-stu-id="76a4c-256">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="76a4c-257">Pesquisar e fazer referência a imagens que você carregou.</span><span class="sxs-lookup"><span data-stu-id="76a4c-257">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="76a4c-258">Adicione formatação como listas, tabelas e chamadas de documentos específicas de docs como `>[!NOTE]` .</span><span class="sxs-lookup"><span data-stu-id="76a4c-258">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="76a4c-259">Pesquisar e referenciar links internos e indicadores (links para seções específicas em uma página).</span><span class="sxs-lookup"><span data-stu-id="76a4c-259">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="76a4c-260">Erros de formatação são realçados (passe o mouse sobre o erro para saber mais).</span><span class="sxs-lookup"><span data-stu-id="76a4c-260">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="76a4c-261">[Verificador ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -palavras incorretas serão sublinhadas; Clique com o botão direito do mouse em uma palavra incorreta para alterá-la ou salvá-la no dicionário.</span><span class="sxs-lookup"><span data-stu-id="76a4c-261">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
