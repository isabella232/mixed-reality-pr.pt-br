---
title: Atualização de versões anteriores
description: Documentação para migrar da versão inferior do MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 5a914d6408d346dac0bf6c683f401564e875f4d8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175103"
---
# <a name="updating-from-earlier-versions"></a><span data-ttu-id="955bb-104">Atualização de versões anteriores</span><span class="sxs-lookup"><span data-stu-id="955bb-104">Updating from earlier versions</span></span>

- [<span data-ttu-id="955bb-105">Atualizando para uma nova versão do MRTK</span><span class="sxs-lookup"><span data-stu-id="955bb-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="955bb-106">2.3.0 a 2.4.0</span><span class="sxs-lookup"><span data-stu-id="955bb-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="955bb-107">2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="955bb-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="955bb-108">2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="955bb-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="955bb-109">2.0.0 a 2.1.0</span><span class="sxs-lookup"><span data-stu-id="955bb-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="955bb-110">RC2 a 2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="955bb-111">Localizar a versão atual</span><span class="sxs-lookup"><span data-stu-id="955bb-111">Finding the current version</span></span> 

<span data-ttu-id="955bb-112">Siga estas instruções para descobrir qual versão do MRTK você está usando no momento:</span><span class="sxs-lookup"><span data-stu-id="955bb-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="955bb-113">Abra seu projeto do MRTK no Unity</span><span class="sxs-lookup"><span data-stu-id="955bb-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="955bb-114">Navegue até a pasta "MixedRealityToolkit" na janela Project aplicativo</span><span class="sxs-lookup"><span data-stu-id="955bb-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="955bb-115">Abra o arquivo chamado "Versão"</span><span class="sxs-lookup"><span data-stu-id="955bb-115">Open the file called "Version"</span></span>

<span data-ttu-id="955bb-116">Se o arquivo e a pasta acima não existirem, você está em uma versão mais recente do MRTK.</span><span class="sxs-lookup"><span data-stu-id="955bb-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="955bb-117">Nesse caso, tente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="955bb-117">In that case, try the following:</span></span>

1. <span data-ttu-id="955bb-118">Navegue até a pasta "Mixed Reality Toolkit Foundation"</span><span class="sxs-lookup"><span data-stu-id="955bb-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="955bb-119">Clique no botão "package.jsem" para ver uma versão prévia no Unity ou abra-a com um editor de texto</span><span class="sxs-lookup"><span data-stu-id="955bb-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="955bb-120">Procure a linha com a palavra "version:"</span><span class="sxs-lookup"><span data-stu-id="955bb-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="955bb-121">Atualizando para uma nova versão do MRTK</span><span class="sxs-lookup"><span data-stu-id="955bb-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="955bb-122">*É altamente recomendável executar [](../features/tools/migration-window.md)* a ferramenta de migração depois de obter a atualização do MRTK para corrigir automaticamente e atualizar de componentes preterido e ajustar-se às alterações interrupntes.</span><span class="sxs-lookup"><span data-stu-id="955bb-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="955bb-123">A ferramenta de migração faz parte do **pacote Ferramentas.**</span><span class="sxs-lookup"><span data-stu-id="955bb-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="955bb-124">As instruções a seguir descrevem o caminho de atualização 2.4.0 para 2.5.0.</span><span class="sxs-lookup"><span data-stu-id="955bb-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="955bb-125">Se o projeto estiver na versão 2.3.0 [](#updating-230-to-240) ou anterior, leia as alterações entre [](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) as versões para entender o caminho de atualização ou leia as instruções da versão anterior para fazer uma atualização de versão por versão.</span><span class="sxs-lookup"><span data-stu-id="955bb-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="955bb-126">Ferramenta Recurso de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="955bb-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="955bb-127">A maneira mais fácil de atualizar o MRTK para [](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) uma versão mais recente do MRTK é usando a Ferramenta de Recursos de Realidade Misturada para baixar os pacotes mais recentes e carregá-los diretamente no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="955bb-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="955bb-128">Se o projeto usou anteriormente arquivos de ativos do Unity (.unitypackage), confira [estas instruções.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="955bb-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="955bb-129">Arquivos de ativos do Unity (.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="955bb-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="955bb-130">Outro caminho de atualização é baixar manualmente os pacotes do Unity do MRTK e aplicá-los ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="955bb-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="955bb-131">Consulte as etapas abaixo,</span><span class="sxs-lookup"><span data-stu-id="955bb-131">See the steps below,</span></span>

1. <span data-ttu-id="955bb-132">Salve uma cópia do seu projeto atual, caso você tenha problemas a qualquer momento nas etapas de atualização.</span><span class="sxs-lookup"><span data-stu-id="955bb-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="955bb-133">Fechar Unity</span><span class="sxs-lookup"><span data-stu-id="955bb-133">Close Unity</span></span>
1. <span data-ttu-id="955bb-134">Dentro da *pasta Ativos,* exclua as seguintes pastas **do MRTK,** juntamente com seus arquivos .meta (o projeto pode não ter todas as pastas listadas)</span><span class="sxs-lookup"><span data-stu-id="955bb-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="955bb-135">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="955bb-135">MRTK/Core</span></span>
    - <span data-ttu-id="955bb-136">MRTK/Exemplos</span><span class="sxs-lookup"><span data-stu-id="955bb-136">MRTK/Examples</span></span>
    - <span data-ttu-id="955bb-137">MRTK/Extensões</span><span class="sxs-lookup"><span data-stu-id="955bb-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="955bb-138">MRTK/Provedores</span><span class="sxs-lookup"><span data-stu-id="955bb-138">MRTK/Providers</span></span>
    - <span data-ttu-id="955bb-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="955bb-139">MRTK/SDK</span></span>
    - <span data-ttu-id="955bb-140">MRTK/Serviços</span><span class="sxs-lookup"><span data-stu-id="955bb-140">MRTK/Services</span></span>
    - <span data-ttu-id="955bb-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="955bb-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="955bb-142">Se foram feitas modificações nos sombreadores do MRTK, crie um backup local antes de excluir a pasta MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="955bb-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="955bb-143">MRTK/Ferramentas</span><span class="sxs-lookup"><span data-stu-id="955bb-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="955bb-144">NÃO exclua **a pasta MixedRealityToolkit.Generated** ou seu arquivo .meta.</span><span class="sxs-lookup"><span data-stu-id="955bb-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="955bb-145">Excluir a **pasta Biblioteca**</span><span class="sxs-lookup"><span data-stu-id="955bb-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="955bb-146">Algumas ferramentas do Unity, como o Unity Collab, salvam informações de configuração na pasta Biblioteca.</span><span class="sxs-lookup"><span data-stu-id="955bb-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="955bb-147">Se estiver usando uma ferramenta que faça isso, primeiro copie a pasta de dados da ferramenta da Biblioteca antes de excluir e restaure-a depois que a Biblioteca for regenerada.</span><span class="sxs-lookup"><span data-stu-id="955bb-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="955bb-148">Reaberto o projeto no Unity</span><span class="sxs-lookup"><span data-stu-id="955bb-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="955bb-149">Importar os novos pacotes do Unity</span><span class="sxs-lookup"><span data-stu-id="955bb-149">Import the new unity packages</span></span>
    - <span data-ttu-id="955bb-150">Foundation – _Importar este pacote primeiro_</span><span class="sxs-lookup"><span data-stu-id="955bb-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="955bb-151">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="955bb-151">Tools</span></span>
    - <span data-ttu-id="955bb-152">(Opcional) Extensões</span><span class="sxs-lookup"><span data-stu-id="955bb-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="955bb-153">Se extensões adicionais foram instaladas, talvez precisem ser importadas de novo.</span><span class="sxs-lookup"><span data-stu-id="955bb-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="955bb-154">(Opcional) Exemplos</span><span class="sxs-lookup"><span data-stu-id="955bb-154">(Optional) Examples</span></span>
1. <span data-ttu-id="955bb-155">Feche o Unity e exclua **a pasta** Biblioteca (leia a observação abaixo primeiro!).</span><span class="sxs-lookup"><span data-stu-id="955bb-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="955bb-156">Essa etapa é necessária para forçar o Unity a atualizar seu banco de dados de ativos e reconciliar perfis personalizados existentes.</span><span class="sxs-lookup"><span data-stu-id="955bb-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="955bb-157">Iniciar o Unity e para cada cena no projeto</span><span class="sxs-lookup"><span data-stu-id="955bb-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="955bb-158">**Exclua MixedRealityToolkit** **e MixedRealityPlayspace,** se presente, da hierarquia.</span><span class="sxs-lookup"><span data-stu-id="955bb-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="955bb-159">Isso excluirá a câmera principal, mas ela será criada na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="955bb-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="955bb-160">Se alguma propriedade da câmera principal tiver sido alterada manualmente, elas deverão ser aplicadas novamente manualmente depois que a nova câmera for criada.</span><span class="sxs-lookup"><span data-stu-id="955bb-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="955bb-161">Selecione **MixedRealityToolkit -> Adicionar à Cena e Configurar**</span><span class="sxs-lookup"><span data-stu-id="955bb-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="955bb-162">Selecione **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (precisa ser feito apenas uma vez) – isso atualizará todos os perfis de mapeamento de controlador personalizado com eixos e dados atualizados, deixando suas ações de entrada atribuídas personalizadas intactas</span><span class="sxs-lookup"><span data-stu-id="955bb-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="955bb-163">Execute a [ferramenta de migração](../features/tools/migration-window.md) e execute a ferramenta no Project *completo* para garantir que todo o seu código seja atualizado para o mais recente.</span><span class="sxs-lookup"><span data-stu-id="955bb-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="955bb-164">A janela de migração contém vários manipuladores de migração diferentes, que devem ser executados por conta própria.</span><span class="sxs-lookup"><span data-stu-id="955bb-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="955bb-165">Esta etapa envolve:</span><span class="sxs-lookup"><span data-stu-id="955bb-165">This step involves:</span></span>
   - <span data-ttu-id="955bb-166">Selecione o primeiro manipulador de migração na lista **suspenso Seleção do Manipulador de** Migração.</span><span class="sxs-lookup"><span data-stu-id="955bb-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="955bb-167">Clique no botão "Project completo".</span><span class="sxs-lookup"><span data-stu-id="955bb-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="955bb-168">Clique no botão "Adicionar projeto completo para migração" (isso verificará todo o projeto em busca de objetos para migrar).</span><span class="sxs-lookup"><span data-stu-id="955bb-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="955bb-169">Clique no botão "Migrar", que deverá ser habilitado se algum objeto migrado for encontrado.</span><span class="sxs-lookup"><span data-stu-id="955bb-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="955bb-170">Repita as três etapas anteriores para cada um dos manipuladores de migração na lista suspenso.</span><span class="sxs-lookup"><span data-stu-id="955bb-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="955bb-171">(Veja [esse problema que](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) aborda o trabalho que pode ser feito para simplificar esse processo de migração em uma versão futura)</span><span class="sxs-lookup"><span data-stu-id="955bb-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="955bb-172">Alternando de arquivos de ativos do Unity para a Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="955bb-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="955bb-173">Alternar de arquivos de ativos do Unity para pacotes da Ferramenta de Recursos de Realidade Misturada traz vários benefícios:</span><span class="sxs-lookup"><span data-stu-id="955bb-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="955bb-174">Atualização mais fácil</span><span class="sxs-lookup"><span data-stu-id="955bb-174">Easier updating</span></span>
- <span data-ttu-id="955bb-175">Tempos de compilação mais rápidos</span><span class="sxs-lookup"><span data-stu-id="955bb-175">Faster compile times</span></span>
- <span data-ttu-id="955bb-176">Menos projetos na solução Visual Studio dados</span><span class="sxs-lookup"><span data-stu-id="955bb-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="955bb-177">Alterar para usar a Ferramenta de Recursos de Realidade Misturada requer um conjunto único de etapas manuais.</span><span class="sxs-lookup"><span data-stu-id="955bb-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="955bb-178">Salve uma cópia do projeto atual.</span><span class="sxs-lookup"><span data-stu-id="955bb-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="955bb-179">Fechar Unity</span><span class="sxs-lookup"><span data-stu-id="955bb-179">Close Unity</span></span>
1. <span data-ttu-id="955bb-180">Dentro da *pasta Ativos,* exclua as seguintes pastas **do MRTK,** juntamente com seus arquivos .meta (o projeto pode não ter todas as pastas listadas)</span><span class="sxs-lookup"><span data-stu-id="955bb-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="955bb-181">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="955bb-181">MRTK/Core</span></span>
    - <span data-ttu-id="955bb-182">MRTK/Exemplos</span><span class="sxs-lookup"><span data-stu-id="955bb-182">MRTK/Examples</span></span>
    - <span data-ttu-id="955bb-183">MRTK/Extensões</span><span class="sxs-lookup"><span data-stu-id="955bb-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="955bb-184">MRTK/Provedores</span><span class="sxs-lookup"><span data-stu-id="955bb-184">MRTK/Providers</span></span>
    - <span data-ttu-id="955bb-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="955bb-185">MRTK/SDK</span></span>
    - <span data-ttu-id="955bb-186">MRTK/Serviços</span><span class="sxs-lookup"><span data-stu-id="955bb-186">MRTK/Services</span></span>
    - <span data-ttu-id="955bb-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="955bb-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="955bb-188">Se foram feitas modificações nos sombreadores do MRTK, crie um backup local antes de excluir a pasta MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="955bb-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="955bb-189">MRTK/Ferramentas</span><span class="sxs-lookup"><span data-stu-id="955bb-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="955bb-190">NÃO exclua **a pasta MixedRealityToolkit.Generated** ou seu arquivo .meta.</span><span class="sxs-lookup"><span data-stu-id="955bb-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="955bb-191">Excluir a **pasta Biblioteca**</span><span class="sxs-lookup"><span data-stu-id="955bb-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="955bb-192">Algumas ferramentas do Unity, como o Unity Collab, salvam informações de configuração na pasta Biblioteca.</span><span class="sxs-lookup"><span data-stu-id="955bb-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="955bb-193">Se estiver usando uma ferramenta que faça isso, primeiro copie a pasta de dados da ferramenta da Biblioteca antes de excluir e restaure-a depois que a Biblioteca for regenerada.</span><span class="sxs-lookup"><span data-stu-id="955bb-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="955bb-194">Reaberto o projeto no Unity</span><span class="sxs-lookup"><span data-stu-id="955bb-194">Re-open the project in Unity</span></span>

<span data-ttu-id="955bb-195">Depois que as etapas anteriores foram executadas, execute [a](#mixed-reality-feature-tool) Ferramenta de Recursos de Realidade Misturada e importe a versão desejada do Toolkit.</span><span class="sxs-lookup"><span data-stu-id="955bb-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="955bb-196">Atualizando 2.3.0 para 2.4.0</span><span class="sxs-lookup"><span data-stu-id="955bb-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="955bb-197">[Renomeações de pasta](#folder-renames-in-240) 
 [Alterações na API](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="955bb-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="955bb-198">Renomeações de pasta na 2.4.0</span><span class="sxs-lookup"><span data-stu-id="955bb-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="955bb-199">As pastas MixedRealityToolkit foram renomeadas e movidas para uma hierarquia comum na versão 2.4.</span><span class="sxs-lookup"><span data-stu-id="955bb-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="955bb-200">Se um aplicativo usar caminhos codificados para recursos do MRTK, ele precisará ser atualizado de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="955bb-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="955bb-201">Pasta anterior</span><span class="sxs-lookup"><span data-stu-id="955bb-201">Previous Folder</span></span> | <span data-ttu-id="955bb-202">Nova Pasta</span><span class="sxs-lookup"><span data-stu-id="955bb-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="955bb-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="955bb-203">MixedRealityToolkit</span></span> | <span data-ttu-id="955bb-204">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="955bb-204">MRTK/Core</span></span> |
| <span data-ttu-id="955bb-205">MixedRealityToolkit.Examples</span><span class="sxs-lookup"><span data-stu-id="955bb-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="955bb-206">MRTK/Exemplos</span><span class="sxs-lookup"><span data-stu-id="955bb-206">MRTK/Examples</span></span> |
| <span data-ttu-id="955bb-207">MixedRealityToolkit.Extensions</span><span class="sxs-lookup"><span data-stu-id="955bb-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="955bb-208">MRTK/Extensões</span><span class="sxs-lookup"><span data-stu-id="955bb-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="955bb-209">MixedRealityToolkit.Providers</span><span class="sxs-lookup"><span data-stu-id="955bb-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="955bb-210">MRTK/Provedores</span><span class="sxs-lookup"><span data-stu-id="955bb-210">MRTK/Providers</span></span> |
| <span data-ttu-id="955bb-211">MixedRealityToolkit.SDK</span><span class="sxs-lookup"><span data-stu-id="955bb-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="955bb-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="955bb-212">MRTK/SDK</span></span> |
| <span data-ttu-id="955bb-213">MixedRealityToolkit.Services</span><span class="sxs-lookup"><span data-stu-id="955bb-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="955bb-214">MRTK/Serviços</span><span class="sxs-lookup"><span data-stu-id="955bb-214">MRTK/Services</span></span> |
| <span data-ttu-id="955bb-215">MixedRealityToolkit.Tests</span><span class="sxs-lookup"><span data-stu-id="955bb-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="955bb-216">MRTK/testes</span><span class="sxs-lookup"><span data-stu-id="955bb-216">MRTK/Tests</span></span> |
| <span data-ttu-id="955bb-217">MixedRealityToolkit.Tools</span><span class="sxs-lookup"><span data-stu-id="955bb-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="955bb-218">MRTK/Ferramentas</span><span class="sxs-lookup"><span data-stu-id="955bb-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="955bb-219">O `MixedRealityToolkit.Generated` contém arquivos gerados pelo cliente e permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="955bb-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="955bb-220">Configuração do olhar na 2.4.0</span><span class="sxs-lookup"><span data-stu-id="955bb-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="955bb-221">Esta versão do MRTK modifica as etapas necessárias para a configuração do olhar.</span><span class="sxs-lookup"><span data-stu-id="955bb-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="955bb-222">A _caixa de seleção 'IsEyeTrackingEnabled'_ pode ser encontrada nas configurações de olhar do perfil de ponteiro de entrada.</span><span class="sxs-lookup"><span data-stu-id="955bb-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="955bb-223">A verificação dessa caixa habilita o olhar com base no olhar e, em vez disso, o olhar com base na cabeça padrão.</span><span class="sxs-lookup"><span data-stu-id="955bb-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="955bb-224">Para obter mais informações sobre essas alterações e instruções completas sobre a configuração do acompanhamento ocular, confira o artigo [acompanhamento ocular.](../features/input/eye-tracking/eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="955bb-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="955bb-225">Comportamento do ponteiro de olhar em 2.4.0</span><span class="sxs-lookup"><span data-stu-id="955bb-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="955bb-226">O comportamento padrão do ponteiro do olhar com o olhar foi modificado para corresponder ao comportamento padrão do ponteiro de olhar para a cabeça.</span><span class="sxs-lookup"><span data-stu-id="955bb-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="955bb-227">Um ponteiro de olhar para o olhar será suprimido automaticamente depois que uma mão for detectada.</span><span class="sxs-lookup"><span data-stu-id="955bb-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="955bb-228">O ponteiro do olhar ficará visível novamente depois de dizer "Selecionar".</span><span class="sxs-lookup"><span data-stu-id="955bb-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="955bb-229">Detalhes sobre o olhar e as configurações de mão podem ser encontrados no artigo [olhos e](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) mãos.</span><span class="sxs-lookup"><span data-stu-id="955bb-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="955bb-230">Alterações de API na 2.4.0</span><span class="sxs-lookup"><span data-stu-id="955bb-230">API changes in 2.4.0</span></span>

<span data-ttu-id="955bb-231">**Classes de controlador personalizadas**</span><span class="sxs-lookup"><span data-stu-id="955bb-231">**Custom controller classes**</span></span>

<span data-ttu-id="955bb-232">Classes de controlador personalizadas anteriormente tinham que definir `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="955bb-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="955bb-233">Esse método tornou-se obsoleto na 2.4, pois o parâmetro de entrega era redundante com a própria mão da classe do controlador.</span><span class="sxs-lookup"><span data-stu-id="955bb-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="955bb-234">O novo método não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="955bb-234">The new method has no parameters.</span></span> <span data-ttu-id="955bb-235">Além disso, muitas classes de controlador definiram isso da mesma maneira ( ), portanto, a chamada completa foi refactorada para e fez uma substituição opcional em vez `AssignControllerMappings(DefaultInteractions);` `BaseController` de necessária.</span><span class="sxs-lookup"><span data-stu-id="955bb-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="955bb-236">**Propriedades do Olhar**</span><span class="sxs-lookup"><span data-stu-id="955bb-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="955bb-237">A `UseEyeTracking` propriedade da implementação de foi `GazeProvider` `IMixedRealityEyeGazeProvider` renomeada para `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="955bb-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="955bb-238">Se você fez isso anteriormente...</span><span class="sxs-lookup"><span data-stu-id="955bb-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="955bb-239">Faça isso agora...</span><span class="sxs-lookup"><span data-stu-id="955bb-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="955bb-240">**Propriedades do WindowsApiChecker**</span><span class="sxs-lookup"><span data-stu-id="955bb-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="955bb-241">As propriedades do WindowsApiChecker a seguir foram marcadas como obsoletas.</span><span class="sxs-lookup"><span data-stu-id="955bb-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="955bb-242">Use `IsMethodAvailable` ou `IsPropertyAvailable` `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="955bb-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="955bb-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="955bb-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="955bb-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="955bb-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="955bb-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="955bb-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="955bb-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="955bb-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="955bb-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="955bb-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="955bb-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="955bb-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="955bb-249">Não há planos para adicionar propriedades ao WindowsApiChecker para versões futuras de contrato de API.</span><span class="sxs-lookup"><span data-stu-id="955bb-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="955bb-250">**GltfMeshPrimitiveAttributes somente leitura**</span><span class="sxs-lookup"><span data-stu-id="955bb-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="955bb-251">Os atributos primitivos da malha gltf costumavam ser settable, agora são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="955bb-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="955bb-252">Seus valores serão definidos uma vez quando desterlizados.</span><span class="sxs-lookup"><span data-stu-id="955bb-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="955bb-253">Migração de ícone de botão personalizado</span><span class="sxs-lookup"><span data-stu-id="955bb-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="955bb-254">Anteriormente, os ícones de botão personalizados exigiam a atribuição de um novo material ao renderador quad do botão.</span><span class="sxs-lookup"><span data-stu-id="955bb-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="955bb-255">Isso não é mais necessário e é recomendável mover texturas de ícone personalizadas para um IconSet.</span><span class="sxs-lookup"><span data-stu-id="955bb-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="955bb-256">Os ícones e materiais personalizados existentes são preservados.</span><span class="sxs-lookup"><span data-stu-id="955bb-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="955bb-257">No entanto, eles serão menos ideais até que sejam atualizados.</span><span class="sxs-lookup"><span data-stu-id="955bb-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="955bb-258">Para atualizar os ativos em todos os botões do projeto para o novo formato recomendado, use ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="955bb-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="955bb-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality. Toolkit. Utilities.ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="955bb-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Diálogo da janela de atualização](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="955bb-261">Se um ícone não for encontrado no ícone padrão definido durante a migração, um conjunto de ícones personalizado será criado em MixedRealityToolkit.Generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="955bb-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="955bb-262">Uma caixa de diálogo indicará que isso ocorreu.</span><span class="sxs-lookup"><span data-stu-id="955bb-262">A dialog will indicate that this has taken place.</span></span>

![Notificação de ícone personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="955bb-264">Atualizando 2.2.0 para 2.3.0</span><span class="sxs-lookup"><span data-stu-id="955bb-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="955bb-265">Alterações de API</span><span class="sxs-lookup"><span data-stu-id="955bb-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="955bb-266">Alterações de API na 2.3.0</span><span class="sxs-lookup"><span data-stu-id="955bb-266">API changes in 2.3.0</span></span>

<span data-ttu-id="955bb-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="955bb-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="955bb-268">O campo ControllerPoseSynchronizer.handedness privado foi marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="955bb-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="955bb-269">Isso deve ter impacto mínimo nos aplicativos, pois o campo não é visível fora de sua classe.</span><span class="sxs-lookup"><span data-stu-id="955bb-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="955bb-270">O setter da propriedade ControllerPoseSynchronizer.Handedness público foi removido ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="955bb-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="955bb-271">**MSBuild para Unity**</span><span class="sxs-lookup"><span data-stu-id="955bb-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="955bb-272">Esta versão do MRTK usa uma versão mais recente do MSBuild para Unity do que as versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="955bb-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="955bb-273">Durante o carregamento do projeto, se a versão mais antiga estiver listada no manifesto do Package Manger do Unity, a caixa de diálogo de configuração será exibida, com a opção Habilitar MSBuild para Unity marcada.</span><span class="sxs-lookup"><span data-stu-id="955bb-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="955bb-274">A aplicação executará uma atualização.</span><span class="sxs-lookup"><span data-stu-id="955bb-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="955bb-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="955bb-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="955bb-276">A classe ScriptingUtilities foi marcada como obsoleta e foi substituída por ScriptUtilities, no Microsoft.MixedReality. Toolkit. Assembly Editor.Utilities.</span><span class="sxs-lookup"><span data-stu-id="955bb-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="955bb-277">A nova classe refina o comportamento anterior e adiciona suporte para remover definições de script.</span><span class="sxs-lookup"><span data-stu-id="955bb-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="955bb-278">Embora o código existente continue a funcionar na versão 2.3.0, é recomendável atualizar para a nova classe.</span><span class="sxs-lookup"><span data-stu-id="955bb-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="955bb-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="955bb-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="955bb-280">Os membros lineRendererSelected e lineRendererNoTarget da classe ShellHandRayPointer foram substituídos por lineMaterialSelected e lineMaterialNoTarget, respectivamente ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="955bb-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="955bb-281">Substitua lineRendererSelected por lineMaterialSelected e/ou lineRendererNoTarget por lineMaterialNoTarget para resolver erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="955bb-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="955bb-282">**Inicialização do observador espacialBehavior**</span><span class="sxs-lookup"><span data-stu-id="955bb-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="955bb-283">Observadores espaciais construídos com base na classe agora adem `BaseSpatialObserver` o valor de StartupBehavior quando reabilitar ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="955bb-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="955bb-284">Nenhuma alteração é necessária para aproveitar essa correção.</span><span class="sxs-lookup"><span data-stu-id="955bb-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="955bb-285">**Pré-requisitos de controle de UX atualizados para usar PressableButton**</span><span class="sxs-lookup"><span data-stu-id="955bb-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="955bb-286">Os pré-requisitos a seguir agora estão usando o componente PressableButton em vez de TouchHandler para interação próxima ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span><span class="sxs-lookup"><span data-stu-id="955bb-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="955bb-287">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="955bb-287">AnimationButton</span></span>
- <span data-ttu-id="955bb-288">Botão</span><span class="sxs-lookup"><span data-stu-id="955bb-288">Button</span></span>
- <span data-ttu-id="955bb-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="955bb-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="955bb-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="955bb-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="955bb-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="955bb-291">CheckBox</span></span>
- <span data-ttu-id="955bb-292">RadialSet</span><span class="sxs-lookup"><span data-stu-id="955bb-292">RadialSet</span></span>
- <span data-ttu-id="955bb-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="955bb-293">ToggleButton</span></span>
- <span data-ttu-id="955bb-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="955bb-294">ToggleSwitch</span></span>
- <span data-ttu-id="955bb-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="955bb-295">UnityUIButton</span></span>
- <span data-ttu-id="955bb-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="955bb-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="955bb-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="955bb-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="955bb-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="955bb-298">UnityUIToggleButton</span></span>

<span data-ttu-id="955bb-299">O código do aplicativo pode exigir atualização devido a essa alteração.</span><span class="sxs-lookup"><span data-stu-id="955bb-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="955bb-300">**Namespace WindowsMixedRealityUtilities**</span><span class="sxs-lookup"><span data-stu-id="955bb-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="955bb-301">O namespace de WindowsMixedRealityUtilities foi alterado de Microsoft.MixedReality. Toolkit. WindowsMixedReality.Input para Microsoft.MixedReality. Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="955bb-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="955bb-302">Atualize #using instruções para resolver erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="955bb-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="955bb-303">Atualizando 2.1.0 para 2.2.0</span><span class="sxs-lookup"><span data-stu-id="955bb-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="955bb-304">Alterações de API</span><span class="sxs-lookup"><span data-stu-id="955bb-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="955bb-305">Alterações de API na 2.2.0</span><span class="sxs-lookup"><span data-stu-id="955bb-305">API changes in 2.2.0</span></span>

<span data-ttu-id="955bb-306">**IMixedRealityBoundarySystem.Contains**</span><span class="sxs-lookup"><span data-stu-id="955bb-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="955bb-307">Esse método anteriormente tinha uma enum experimental específica definida pelo Unity.</span><span class="sxs-lookup"><span data-stu-id="955bb-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="955bb-308">Agora, ele recebe uma enum definida pelo MRTK que é idêntica à enum do Unity.</span><span class="sxs-lookup"><span data-stu-id="955bb-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="955bb-309">Essa alteração ajuda a preparar o MRTK para as APIs de limite futuras do Unity.</span><span class="sxs-lookup"><span data-stu-id="955bb-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="955bb-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="955bb-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="955bb-311">Para descrever melhor os requisitos para dar suporte a um perfil, o MixedRealityServiceProfileAttribute foi atualizado para adicionar uma coleção opcional de tipos excluídos.</span><span class="sxs-lookup"><span data-stu-id="955bb-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="955bb-312">Como parte dessa alteração, a propriedade ServiceType foi alterada de Type para Type[] e renomeada para RequiredTypes.</span><span class="sxs-lookup"><span data-stu-id="955bb-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="955bb-313">Uma segunda propriedade, ExcludedTypes, também foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="955bb-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="955bb-314">Atualizando 2.0.0 para 2.1.0</span><span class="sxs-lookup"><span data-stu-id="955bb-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="955bb-315">Alterações de API</span><span class="sxs-lookup"><span data-stu-id="955bb-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="955bb-316">Alterações de perfil</span><span class="sxs-lookup"><span data-stu-id="955bb-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="955bb-317">Alterações de API na 2.1.0</span><span class="sxs-lookup"><span data-stu-id="955bb-317">API changes in 2.1.0</span></span>

<span data-ttu-id="955bb-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="955bb-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="955bb-319">O `BaseNearInteractionTouchable` foi modificado para marcar o método como `OnValidate` virtual.</span><span class="sxs-lookup"><span data-stu-id="955bb-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="955bb-320">As classes que se `BaseNearInteractionTouchable` estendem (por ex: `NearInteractionTouchableUnityUI` ) foram atualizadas para refletir essa alteração.</span><span class="sxs-lookup"><span data-stu-id="955bb-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="955bb-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="955bb-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="955bb-322">A classe `ColliderNearInteractionTouchable` foi substituída.</span><span class="sxs-lookup"><span data-stu-id="955bb-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="955bb-323">Atualize as referências de código para usar `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="955bb-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="955bb-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="955bb-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="955bb-325">**_Adicionado_**</span><span class="sxs-lookup"><span data-stu-id="955bb-325">**_Added_**</span></span>

<span data-ttu-id="955bb-326">`IMixedRealityMouseDeviceManager` foram adicionadas `CursorSpeed` propriedades `WheelSpeed` e .</span><span class="sxs-lookup"><span data-stu-id="955bb-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="955bb-327">Essas propriedades permitem que os aplicativos especifiquem um valor multiplicador pelo qual a velocidade do cursor e da roda, respectivamente, será dimensionada.</span><span class="sxs-lookup"><span data-stu-id="955bb-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="955bb-328">Essa é uma alteração da última vez e requer que as implementações existentes do gerenciador de dispositivo do mouse sejam modificadas.</span><span class="sxs-lookup"><span data-stu-id="955bb-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="955bb-329">Essa alteração não é compatível com versões anteriores com a versão 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="955bb-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="955bb-330">**_Preterido_**</span><span class="sxs-lookup"><span data-stu-id="955bb-330">**_Deprecated_**</span></span>

<span data-ttu-id="955bb-331">A `MouseInputProfile` propriedade foi marcada como obsoleta e será removida de uma versão futura do Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="955bb-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="955bb-332">É recomendável que o código do aplicativo não use mais essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="955bb-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="955bb-333">**Interativo**</span><span class="sxs-lookup"><span data-stu-id="955bb-333">**Interactable**</span></span>

<span data-ttu-id="955bb-334">Os métodos e propriedades a seguir foram preterido e serão removidos de uma versão futura do Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="955bb-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="955bb-335">A recomendação é atualizar o código do aplicativo de acordo com as diretrizes contidas no atributo Obsoleto e exibidas no console.</span><span class="sxs-lookup"><span data-stu-id="955bb-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="955bb-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="955bb-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="955bb-337">A `NearInteractionTouchableSurface` classe foi adicionada e agora serve como a classe base para e `NearInteractionTouchable` `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="955bb-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="955bb-338">Alterações de perfil na 2.1.0</span><span class="sxs-lookup"><span data-stu-id="955bb-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="955bb-339">**Perfil de acompanhamento de mão**</span><span class="sxs-lookup"><span data-stu-id="955bb-339">**Hand tracking profile**</span></span>

<span data-ttu-id="955bb-340">A malha manual e as visualizações conjuntas agora têm configurações separadas do editor e do player.</span><span class="sxs-lookup"><span data-stu-id="955bb-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="955bb-341">O perfil de acompanhamento de mão foi atualizado para permitir a configuração dessas visualizações como; Nothing, Everything, Editor ou Player.</span><span class="sxs-lookup"><span data-stu-id="955bb-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Modos de visualização de mão](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="955bb-343">Os perfis de acompanhamento de mão personalizados podem precisar ser atualizados para funcionar corretamente com a versão 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="955bb-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="955bb-344">Essa alteração não é compatível com versões anteriores com a versão 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="955bb-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="955bb-345">**Perfil de simulação de entrada**</span><span class="sxs-lookup"><span data-stu-id="955bb-345">**Input simulation profile**</span></span>

<span data-ttu-id="955bb-346">O sistema de simulação de entrada foi atualizado, o que altera algumas configurações no perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="955bb-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="955bb-347">Algumas alterações não podem ser migradas automaticamente e os usuários podem descobrir que os perfis estão usando valores padrão.</span><span class="sxs-lookup"><span data-stu-id="955bb-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="955bb-348">Todas as vinculações de botão keyCode e mouse no perfil foram substituídas por um struct genérico, que armazena o tipo de associação (chave ou mouse), bem como o código de associação real (KeyCode ou número do botão do `KeyBinding` mouse, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="955bb-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="955bb-349">O struct tem seu próprio inspetor, que permite a exibição unificada e oferece uma ferramenta de "associação automática" para definir rapidamente as vinculações de chave pressionando a respectiva chave em vez de selecionar em uma lista suspenso enorme.</span><span class="sxs-lookup"><span data-stu-id="955bb-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="955bb-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="955bb-350">FastControlKey</span></span>
    - <span data-ttu-id="955bb-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="955bb-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="955bb-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="955bb-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="955bb-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="955bb-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="955bb-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="955bb-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="955bb-355">`MouseLookToggle` foi incluído anteriormente `MouseLookButton` na enum como `InputSimulationMouseButton.Focused` , agora é uma opção separada.</span><span class="sxs-lookup"><span data-stu-id="955bb-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="955bb-356">Quando habilitada, a câmera continua girando com o mouse depois de soltar o botão, até que a tecla de escape seja pressionada.</span><span class="sxs-lookup"><span data-stu-id="955bb-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="955bb-357">`HandDepthMultiplier` O valor padrão foi baixado de 0,1 para 0,03 para acomodar algumas alterações na simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="955bb-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="955bb-358">Se a câmera se mover muito rápido ao rolar, tente reduzir esse valor.</span><span class="sxs-lookup"><span data-stu-id="955bb-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="955bb-359">As chaves para girar as mãos foram removidas, a rotação da mão agora também é controlada pelo mouse.</span><span class="sxs-lookup"><span data-stu-id="955bb-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="955bb-360">Manter `HandRotateButton` (Ctrl) junto com a tecla de manipulação esquerda/direita (LShift/Espaço) habilita a rotação da mão.</span><span class="sxs-lookup"><span data-stu-id="955bb-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="955bb-361">Um novo eixo "UpDown" foi introduzido na lista de eixos de entrada.</span><span class="sxs-lookup"><span data-stu-id="955bb-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="955bb-362">Isso controla a movimentação da câmera na vertical e assume como padrão as chaves Q/E, bem como os botões de gatilho do controlador.</span><span class="sxs-lookup"><span data-stu-id="955bb-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="955bb-363">Para obter mais informações sobre essas alterações, consulte o artigo [serviço de simulação de](../features/input-simulation/input-simulation-service.md) entrada.</span><span class="sxs-lookup"><span data-stu-id="955bb-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="955bb-364">**Perfil do provedor de dados do mouse**</span><span class="sxs-lookup"><span data-stu-id="955bb-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="955bb-365">O perfil do provedor de dados do mouse foi atualizado para expor as novas `CursorSpeed` propriedades `WheelSpeed` e .</span><span class="sxs-lookup"><span data-stu-id="955bb-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="955bb-366">Os perfis personalizados existentes terão valores padrão fornecidos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="955bb-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="955bb-367">Quando o perfil for salvo, esses novos valores serão persistentes.</span><span class="sxs-lookup"><span data-stu-id="955bb-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="955bb-368">**Perfil de mapeamento do controlador**</span><span class="sxs-lookup"><span data-stu-id="955bb-368">**Controller mapping profile**</span></span>

<span data-ttu-id="955bb-369">Alguns eixos e tipos de entrada foram atualizados na versão 2.1.0, especialmente em torno da plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="955bb-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="955bb-370">Selecione **MixedRealityToolkit -> Utilities -> Atualizar -> de** Mapeamento do Controlador ao atualizar.</span><span class="sxs-lookup"><span data-stu-id="955bb-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="955bb-371">Isso atualizará todos os Perfis de Mapeamento de Controlador personalizados com os eixos e dados atualizados, deixando suas ações de entrada atribuídas personalizadas intactas.</span><span class="sxs-lookup"><span data-stu-id="955bb-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="955bb-372">Atualizando RC2 para 2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="955bb-373">Entre as versões RC2 e 2.0.0 do Microsoft Mixed Reality Toolkit, foram feitas alterações que podem afetar os projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="955bb-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="955bb-374">Este documento descreve essas alterações e como atualizar projetos para a versão 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="955bb-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="955bb-375">Alterações de API</span><span class="sxs-lookup"><span data-stu-id="955bb-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="955bb-376">Alterações de nome do assembly</span><span class="sxs-lookup"><span data-stu-id="955bb-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="955bb-377">Alterações de API na 2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-377">API changes in 2.0.0</span></span>

<span data-ttu-id="955bb-378">Desde o lançamento do RC2, houve várias alterações na API, incluindo algumas que podem quebrar projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="955bb-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="955bb-379">As seções a seguir descrevem as alterações que ocorreram entre as versões RC2 e 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="955bb-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="955bb-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="955bb-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="955bb-381">As propriedades públicas a seguir no objeto MixedRealityToolkit foram preterida.</span><span class="sxs-lookup"><span data-stu-id="955bb-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="955bb-382">`RegisteredMixedRealityServices` não contém mais a coleção de serviços de extensões registradas e provedores de dados.</span><span class="sxs-lookup"><span data-stu-id="955bb-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="955bb-383">Para acessar os serviços de extensão, use `MixedRealityServiceRegistry.TryGetService<T>` .</span><span class="sxs-lookup"><span data-stu-id="955bb-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="955bb-384">Para acessar provedores de dados, caste a instância de serviço para [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) e use `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="955bb-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="955bb-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) ou, em vez disso, para as propriedades preteridas a seguir</span><span class="sxs-lookup"><span data-stu-id="955bb-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="955bb-386">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="955bb-386">**CoreServices**</span></span>

<span data-ttu-id="955bb-387">A classe é a substituição para os acessadores do sistema [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) estático (por exemplo: BoundarySystem) encontrados no `MixedRealityToolkit` objeto .</span><span class="sxs-lookup"><span data-stu-id="955bb-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="955bb-388">Os acessadores do sistema foram preterido na versão 2.0.0 e serão removidos em uma versão `MixedRealityToolkit` futura do MRTK.</span><span class="sxs-lookup"><span data-stu-id="955bb-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="955bb-389">O exemplo de código a seguir ilustra o padrão antigo e o novo.</span><span class="sxs-lookup"><span data-stu-id="955bb-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="955bb-390">O uso da nova classe CoreSystem garantirá que o código do aplicativo não precisará ser atualizado se você alterar o aplicativo para usar um registrador de serviços diferente (por ex. um dos gerenciadores de serviços experimentais).</span><span class="sxs-lookup"><span data-stu-id="955bb-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="955bb-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="955bb-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="955bb-392">Com a adição do IMixedRealityRaycastProvider, o perfil de configuração do sistema de entrada foi alterado.</span><span class="sxs-lookup"><span data-stu-id="955bb-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="955bb-393">Se você tiver um perfil personalizado, poderá receber os erros na imagem a seguir ao executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="955bb-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Selecionando o provedor Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="955bb-395">Para corrigi-los, adicione uma instância IMixedRealityRaycastProvider ao perfil do sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="955bb-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Selecionando o provedor Raycast 2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="955bb-397">**Sistema de Eventos**</span><span class="sxs-lookup"><span data-stu-id="955bb-397">**Event System**</span></span>

- <span data-ttu-id="955bb-398">Os `IMixedRealityEventSystem` métodos de API antigos e foram `Register` `Unregister` marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="955bb-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="955bb-399">Eles são preservados para compatibilidade com compatibilidade com vertida.</span><span class="sxs-lookup"><span data-stu-id="955bb-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="955bb-400">`InputSystemGlobalListener` foi marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="955bb-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="955bb-401">Sua funcionalidade não foi alterada.</span><span class="sxs-lookup"><span data-stu-id="955bb-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="955bb-402">`BaseInputHandler` a classe base foi alterada de `InputSystemGlobalListener` para `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="955bb-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="955bb-403">Essa é uma alteração significativa para os descendentes de `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="955bb-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="955bb-404">**_Motivação por trás da alteração_**</span><span class="sxs-lookup"><span data-stu-id="955bb-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="955bb-405">A antiga API do sistema de eventos `Register` e `Unregister` poderia causar vários problemas em tempo de execução, a principal é:</span><span class="sxs-lookup"><span data-stu-id="955bb-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="955bb-406">Se um componente for registrado para eventos globais, ele receberá eventos de entrada globais de *todos os* tipos.</span><span class="sxs-lookup"><span data-stu-id="955bb-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="955bb-407">Se um dos componentes em um objeto for registrado para eventos de entrada globais, todos os componentes nesse objeto receberão eventos de entrada globais de *todos os* tipos.</span><span class="sxs-lookup"><span data-stu-id="955bb-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="955bb-408">Se dois componentes no mesmo objeto forem registrados em eventos globais e um for desabilitado em tempo de execução, o segundo interromperá o recebimento de eventos globais.</span><span class="sxs-lookup"><span data-stu-id="955bb-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="955bb-409">Nova API `RegisterHandler` e `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="955bb-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="955bb-410">Fornece um controle explícito e granular sobre o qual os eventos de entrada devem ser ouvidos globalmente e que devem ser baseados em foco.</span><span class="sxs-lookup"><span data-stu-id="955bb-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="955bb-411">Permite que vários componentes no mesmo objeto escutem eventos globais independentemente um do outro.</span><span class="sxs-lookup"><span data-stu-id="955bb-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="955bb-412">**_Como migrar_**</span><span class="sxs-lookup"><span data-stu-id="955bb-412">**_How to migrate_**</span></span>

- <span data-ttu-id="955bb-413">Se você estiver chamando a `Register` / `Unregister` API diretamente antes, substitua essas chamadas por chamadas para `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="955bb-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="955bb-414">Use interfaces de manipulador que você implementar como parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="955bb-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="955bb-415">Se você implementar várias interfaces e várias delas ouvirem os eventos de entrada globais, chame `RegisterHandler` várias vezes.</span><span class="sxs-lookup"><span data-stu-id="955bb-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="955bb-416">Se você estiver herdando de `InputSystemGlobalListener` , altere a herança para `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="955bb-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="955bb-417">Implementar `RegisterHandlers` e `UnregisterHandlers` abstrair métodos.</span><span class="sxs-lookup"><span data-stu-id="955bb-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="955bb-418">Na chamada de implementação `inputSystem.RegisterHandler` ( `inputSystem.UnregisterHandler` ) para registrar em todas as interfaces de manipulador para as quais você deseja escutar eventos globais.</span><span class="sxs-lookup"><span data-stu-id="955bb-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="955bb-419">Se você estiver herdando de `BaseInputHandler` `RegisterHandlers` métodos Implement e `UnregisterHandlers` Abstract (o mesmo que for `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="955bb-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="955bb-420">**_Exemplos de migração_**</span><span class="sxs-lookup"><span data-stu-id="955bb-420">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="955bb-421">**Conscientização espacial**</span><span class="sxs-lookup"><span data-stu-id="955bb-421">**Spatial Awareness**</span></span>

<span data-ttu-id="955bb-422">As interfaces IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver fizeram várias alterações significativas, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="955bb-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="955bb-423">**_Alterações_**</span><span class="sxs-lookup"><span data-stu-id="955bb-423">**_Changes_**</span></span>

<span data-ttu-id="955bb-424">Os seguintes métodos foram renomeados para descrever melhor seu uso.</span><span class="sxs-lookup"><span data-stu-id="955bb-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="955bb-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` foi renomeado para `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` para esclarecer seu uso.</span><span class="sxs-lookup"><span data-stu-id="955bb-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="955bb-426">**_Adições_**</span><span class="sxs-lookup"><span data-stu-id="955bb-426">**_Additions_**</span></span>

<span data-ttu-id="955bb-427">Com base nos comentários dos clientes, o suporte à remoção fácil de dados de reconhecimento espacial observados anteriormente foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="955bb-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="955bb-428">**Solucionadores**</span><span class="sxs-lookup"><span data-stu-id="955bb-428">**Solvers**</span></span>

<span data-ttu-id="955bb-429">Alguns componentes do Solver e a classe SolverHandler Manager foram alterados para corrigir vários bugs e para um uso mais intuitivo.</span><span class="sxs-lookup"><span data-stu-id="955bb-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="955bb-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="955bb-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="955bb-431">A classe não se estende mais de `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="955bb-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="955bb-432">`TrackedObjectToReference` Propriedade pública preterida e renomeada como `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="955bb-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="955bb-433">`TrackedObjectType` substitui os valores da & do controlador à esquerda.</span><span class="sxs-lookup"><span data-stu-id="955bb-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="955bb-434">Em vez disso, use `MotionController` `HandJoint` valores ou e atualize `TrackedHandedness` a nova propriedade para limitar o controle para o controlador esquerdo ou direito</span><span class="sxs-lookup"><span data-stu-id="955bb-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="955bb-435">**_Entre_**</span><span class="sxs-lookup"><span data-stu-id="955bb-435">**_InBetween_**</span></span>

- <span data-ttu-id="955bb-436">`TrackedObjectForSecondTransform` Propriedade pública preterida e renomeada como `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="955bb-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="955bb-437">`AttachSecondTransformToNewTrackedObject()` foi removido.</span><span class="sxs-lookup"><span data-stu-id="955bb-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="955bb-438">Para atualizar o resolvedor, modifique as propriedades públicas (ou seja,</span><span class="sxs-lookup"><span data-stu-id="955bb-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="955bb-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="955bb-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="955bb-440">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="955bb-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="955bb-441">`MaxDistance` Propriedade pública preterida e renomeada como `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="955bb-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="955bb-442">`CloseDistance` Propriedade pública preterida e renomeada como `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="955bb-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="955bb-443">O valor padrão de `RaycastDirectionMode` é agora `TrackedTargetForward` qual raycasts na direção da transformação de destino rastreada em frente</span><span class="sxs-lookup"><span data-stu-id="955bb-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="955bb-444">`OrientationMode` os valores de enumeração `Vertical` e `Full` , foram renomeados para `TrackedTarget` e `SurfaceNormal` respectivamente</span><span class="sxs-lookup"><span data-stu-id="955bb-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="955bb-445">`KeepOrientationVertical` a propriedade pública foi adicionada para controlar se a orientação do gameobject associado permanece vertical</span><span class="sxs-lookup"><span data-stu-id="955bb-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="955bb-446">**Botões**</span><span class="sxs-lookup"><span data-stu-id="955bb-446">**Buttons**</span></span>

- <span data-ttu-id="955bb-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) Agora tem `DistanceSpaceMode` a propriedade definida `Local` como padrão.</span><span class="sxs-lookup"><span data-stu-id="955bb-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="955bb-448">Isso permite que os botões sejam dimensionados enquanto ainda podem ser prensados</span><span class="sxs-lookup"><span data-stu-id="955bb-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="955bb-449">**Esfera de recorte**</span><span class="sxs-lookup"><span data-stu-id="955bb-449">**Clipping Sphere**</span></span>

<span data-ttu-id="955bb-450">A interface ClippingSphere foi alterada para espelhar as APIs encontradas em ClippingBox e ClippingPlane.</span><span class="sxs-lookup"><span data-stu-id="955bb-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="955bb-451">A propriedade RADIUS do ClippingSphere agora é implicitamente calculada com base na escala de transformação.</span><span class="sxs-lookup"><span data-stu-id="955bb-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="955bb-452">Antes que os desenvolvedores precisem especificar o raio do ClippingSphere no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="955bb-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="955bb-453">Se você quiser alterar o raio, basta atualizar a escala de transformação da transformação como faria normalmente.</span><span class="sxs-lookup"><span data-stu-id="955bb-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="955bb-454">**NearInteractionTouchable e PokePointer**</span><span class="sxs-lookup"><span data-stu-id="955bb-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="955bb-455">NearInteractionTouchable não lida com o toque da tela da interface do usuário do Unity mais.</span><span class="sxs-lookup"><span data-stu-id="955bb-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="955bb-456">A classe NearInteractionTouchableUnityUI deve ser usada para a interface do usuário do Unity touchables agora.</span><span class="sxs-lookup"><span data-stu-id="955bb-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="955bb-457">ColliderNearInteractionTouchable é a nova classe base para touchables com base em colisors, ou seja, cada tocável, exceto NearInteractionTouchableUnityUI.</span><span class="sxs-lookup"><span data-stu-id="955bb-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="955bb-458">BaseNearInteractionTouchable. DistFront foi movido e renomeado para PokePointer. TouchableDistance essa é a distância e a qual o PokePointer pode interagir com touchables.</span><span class="sxs-lookup"><span data-stu-id="955bb-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="955bb-459">Anteriormente, cada tocável tinha sua própria distância máxima de interação, mas agora isso é definido no PokePointer, o que permite uma melhor otimização.</span><span class="sxs-lookup"><span data-stu-id="955bb-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="955bb-460">BaseNearInteractionTouchable. DistBack foi renomeado para PokeThreshold isso torna claro que PokeThreshold é o equivalente a DebounceThreshold.</span><span class="sxs-lookup"><span data-stu-id="955bb-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="955bb-461">Um toque é ativado quando o PokeThreshold é cruzado e liberado quando DebounceThreshold é cruzado.</span><span class="sxs-lookup"><span data-stu-id="955bb-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="955bb-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="955bb-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="955bb-463">O `Microsoft.MixedReality.Toolkit` namespace foi adicionado a `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` , e `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="955bb-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="955bb-464">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="955bb-464">**PointerClickHandler**</span></span>

<span data-ttu-id="955bb-465">A classe `PointerClickHandler` foi substituída.</span><span class="sxs-lookup"><span data-stu-id="955bb-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="955bb-466">O `PointerHandler` deve ser usado em vez disso, ele fornece a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="955bb-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="955bb-467">**suporte ao clique HoloLens**</span><span class="sxs-lookup"><span data-stu-id="955bb-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="955bb-468">os mapeamentos do controlador do HoloLens do clique foram alterados para serem desnecessários [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) .</span><span class="sxs-lookup"><span data-stu-id="955bb-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="955bb-469">Para considerar isso, um atualizador automático será executado na primeira vez que você abrir o perfil do ControllerMapping.</span><span class="sxs-lookup"><span data-stu-id="955bb-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="955bb-470">Abra qualquer perfil personalizado pelo menos uma vez após a atualização para o 2.0.0 para disparar essa etapa de migração única.</span><span class="sxs-lookup"><span data-stu-id="955bb-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="955bb-471">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="955bb-471">**InteractableHighlight**</span></span>

<span data-ttu-id="955bb-472">A classe `InteractableHighlight` foi substituída.</span><span class="sxs-lookup"><span data-stu-id="955bb-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="955bb-473">A `InteractableOnFocus` classe e o `FocusInteractableStates` ativo devem ser usados em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="955bb-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="955bb-474">para criar um novo `Theme` ativo para o `InteractableOnFocus` , clique com o botão direito do mouse na janela do projeto e selecione *criar*  >  *realidade misturada Toolkit*  >    >  *tema* interagir.</span><span class="sxs-lookup"><span data-stu-id="955bb-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="955bb-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="955bb-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="955bb-476">`HandInteractionPanZoom` foi movido para o namespace da interface do usuário porque não era um componente de entrada.</span><span class="sxs-lookup"><span data-stu-id="955bb-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="955bb-477">`HandPanEventData` também foi movido para esse namespace e simplificado para corresponder a outros dados de eventos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="955bb-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="955bb-478">Alterações de nome de assembly em 2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="955bb-479">na versão 2.0.0, toda a realidade misturada oficial Toolkit nomes de assembly e seus arquivos de definição de assembly (. asmdef) associados foram atualizados para se ajustarem ao padrão a seguir.</span><span class="sxs-lookup"><span data-stu-id="955bb-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="955bb-480">Em alguns casos, vários assemblies foram mesclados para criar um Unity melhor de seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="955bb-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="955bb-481">Se o seu projeto usa arquivos. asmdef personalizados, eles podem exigir atualização.</span><span class="sxs-lookup"><span data-stu-id="955bb-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="955bb-482">As tabelas a seguir descrevem como os nomes de arquivo RC2. asmdef são mapeados para a versão 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="955bb-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="955bb-483">Todos os nomes de assembly correspondem ao nome do arquivo. asmdef.</span><span class="sxs-lookup"><span data-stu-id="955bb-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="955bb-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="955bb-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="955bb-485">RC2</span><span class="sxs-lookup"><span data-stu-id="955bb-485">RC2</span></span> | <span data-ttu-id="955bb-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="955bb-487">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="955bb-488">Microsoft. MixedReality. Toolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="955bb-489">MixedRealityToolkit. Core. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="955bb-490">Microsoft. MixedReality. Toolkit. Editor. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="955bb-491">MixedRealityToolkit. Core. Definitions. Utilities. editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="955bb-492">Removido, use Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="955bb-493">MixedRealityToolkit. Core. Extensions. EditorClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="955bb-494">Microsoft. MixedReality. Toolkit. Editor. ClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="955bb-495">MixedRealityToolkit. Core. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="955bb-496">Microsoft. MixedReality. Toolkit. Editor. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="955bb-497">MixedRealityToolkit. Core. Inspectors. testinspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="955bb-498">Microsoft. MixedReality. Toolkit. Editor. userinspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="955bb-499">MixedRealityToolkit. Core. UtilitiesAsync. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="955bb-500">Microsoft. MixedReality. Toolkit. Async. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="955bb-501">MixedRealityToolkit. Core. Utilities. editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="955bb-502">Microsoft.MixedReality. Toolkit. Editor.Utilities.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="955bb-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="955bb-504">Microsoft.MixedReality. Toolkit. Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="955bb-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="955bb-506">Microsoft.MixedReality. Toolkit. Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="955bb-507">**MixedRealityToolkit.Providers**</span><span class="sxs-lookup"><span data-stu-id="955bb-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="955bb-508">RC2</span><span class="sxs-lookup"><span data-stu-id="955bb-508">RC2</span></span> | <span data-ttu-id="955bb-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="955bb-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="955bb-511">Microsoft.MixedReality. Toolkit. Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="955bb-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="955bb-513">Microsoft.MixedReality. Toolkit. Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="955bb-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="955bb-515">Microsoft.MixedReality. Toolkit. Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="955bb-516">**MixedRealityToolkit.Services**</span><span class="sxs-lookup"><span data-stu-id="955bb-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="955bb-517">RC2</span><span class="sxs-lookup"><span data-stu-id="955bb-517">RC2</span></span> | <span data-ttu-id="955bb-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="955bb-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="955bb-520">Microsoft.MixedReality. Toolkit. Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="955bb-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="955bb-522">Microsoft.MixedReality. Toolkit. Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="955bb-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="955bb-524">Microsoft.MixedReality. Toolkit. Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="955bb-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="955bb-526">Microsoft.MixedReality. Toolkit. Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="955bb-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="955bb-528">Microsoft.MixedReality. Toolkit. Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="955bb-529">MixedRealityToolkit.Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="955bb-530">Microsoft.MixedReality. Toolkit. Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="955bb-531">MixedRealityToolkit.Services.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="955bb-532">Microsoft.MixedReality. Toolkit. Services.InputSystem.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="955bb-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="955bb-534">Microsoft.MixedReality. Toolkit. Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="955bb-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="955bb-536">Microsoft.MixedReality. Toolkit. Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="955bb-537">MixedRealityToolkit.Services.System.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="955bb-538">Microsoft.MixedReality. Toolkit. Services.LtdSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="955bb-539">**MixedRealityToolkit.SDK**</span><span class="sxs-lookup"><span data-stu-id="955bb-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="955bb-540">RC2</span><span class="sxs-lookup"><span data-stu-id="955bb-540">RC2</span></span> | <span data-ttu-id="955bb-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="955bb-542">MixedRealityToolkit.SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="955bb-543">Microsoft.MixedReality. Toolkit. SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="955bb-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="955bb-545">Microsoft.MixedReality. Toolkit. Sdk. Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="955bb-546">**MixedRealityToolkit.Examples**</span><span class="sxs-lookup"><span data-stu-id="955bb-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="955bb-547">RC2</span><span class="sxs-lookup"><span data-stu-id="955bb-547">RC2</span></span> | <span data-ttu-id="955bb-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="955bb-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="955bb-549">MixedRealityToolkit.Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="955bb-550">Microsoft.MixedReality. Toolkit. Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="955bb-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="955bb-552">Microsoft.MixedReality. Toolkit. Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="955bb-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="955bb-554">Microsoft.MixedReality. Toolkit. Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="955bb-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="955bb-556">Microsoft.MixedReality. Toolkit. Demos.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="955bb-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="955bb-558">Microsoft.MixedReality. Toolkit. Demos.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="955bb-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="955bb-560">Microsoft.MixedReality. Toolkit. Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="955bb-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |
