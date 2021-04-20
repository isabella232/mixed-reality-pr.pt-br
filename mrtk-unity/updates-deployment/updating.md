---
title: Atualizar
description: Documentação para migrar de uma versão inferior do MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742232"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="da93e-104">Atualizando o Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="da93e-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="da93e-105">Atualizando para uma nova versão do MRTK</span><span class="sxs-lookup"><span data-stu-id="da93e-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="da93e-106">2.3.0 2.4.0</span><span class="sxs-lookup"><span data-stu-id="da93e-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="da93e-107">2.2.0 2.3.0</span><span class="sxs-lookup"><span data-stu-id="da93e-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="da93e-108">2.1.0 2.2.0</span><span class="sxs-lookup"><span data-stu-id="da93e-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="da93e-109">2.0.0 2.1.0</span><span class="sxs-lookup"><span data-stu-id="da93e-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="da93e-110">RC2 para 2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="da93e-111">Localizando a versão atual</span><span class="sxs-lookup"><span data-stu-id="da93e-111">Finding the current version</span></span> 

<span data-ttu-id="da93e-112">Siga estas instruções para descobrir qual versão do MRTK você está usando no momento:</span><span class="sxs-lookup"><span data-stu-id="da93e-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="da93e-113">Abra seu projeto do MRTK no Unity</span><span class="sxs-lookup"><span data-stu-id="da93e-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="da93e-114">Navegue até a pasta "MixedRealityToolkit" na janela do projeto</span><span class="sxs-lookup"><span data-stu-id="da93e-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="da93e-115">Abra o arquivo chamado "Version"</span><span class="sxs-lookup"><span data-stu-id="da93e-115">Open the file called "Version"</span></span>

<span data-ttu-id="da93e-116">Se o arquivo e a pasta acima não existirem, você estará em uma versão mais recente do MRTK.</span><span class="sxs-lookup"><span data-stu-id="da93e-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="da93e-117">Nesse caso, tente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="da93e-117">In that case, try the following:</span></span>

1. <span data-ttu-id="da93e-118">Navegue até a pasta "Mixed Reality Toolkit Foundation"</span><span class="sxs-lookup"><span data-stu-id="da93e-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="da93e-119">Clique em "package.jsem" para ver uma visualização no Unity ou abri-la com um editor de texto</span><span class="sxs-lookup"><span data-stu-id="da93e-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="da93e-120">Procure a linha com a palavra "Version:"</span><span class="sxs-lookup"><span data-stu-id="da93e-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="da93e-121">Atualizando para uma nova versão do MRTK</span><span class="sxs-lookup"><span data-stu-id="da93e-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="da93e-122">*É altamente recomendável executar a [ferramenta de migração](../features/tools/migration-window.md) depois de obter a atualização do MRTK* para corrigir automaticamente e atualizar de componentes preteridos e ajustar para alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="da93e-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="da93e-123">A ferramenta de migração faz parte do pacote de **ferramentas** .</span><span class="sxs-lookup"><span data-stu-id="da93e-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="da93e-124">As instruções a seguir descrevem o caminho de atualização do 2.4.0 para 2.5.0.</span><span class="sxs-lookup"><span data-stu-id="da93e-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="da93e-125">Se seu projeto estiver no 2.3.0 ou anterior, leia sobre as alterações [entre as versões](#updating-230-to-240) para entender o caminho de atualização ou leia as [instruções da versão](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) anterior para fazer uma atualização de versão por versão.</span><span class="sxs-lookup"><span data-stu-id="da93e-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="da93e-126">Ferramenta Recurso de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="da93e-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="da93e-127">A maneira mais fácil de atualizar o MRTK para uma versão mais recente do MRTK é usando a [ferramenta de recursos de realidade misturada](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) para baixar os pacotes mais recentes e carregá-los diretamente em seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="da93e-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="da93e-128">Se o projeto usava anteriormente arquivos de ativo de Unity (. unitypackage), consulte [estas instruções](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="da93e-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="da93e-129">Arquivos de ativo de Unity (. unitypackage)</span><span class="sxs-lookup"><span data-stu-id="da93e-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="da93e-130">Outro caminho de atualização é baixar manualmente os pacotes do MRTK Unity e aplicá-los ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="da93e-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="da93e-131">Consulte as etapas abaixo,</span><span class="sxs-lookup"><span data-stu-id="da93e-131">See the steps below,</span></span>

1. <span data-ttu-id="da93e-132">Salve uma cópia do seu projeto atual, caso você tenha atingido quaisquer empecilhos em qualquer ponto nas etapas de atualização.</span><span class="sxs-lookup"><span data-stu-id="da93e-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="da93e-133">Fechar o Unity</span><span class="sxs-lookup"><span data-stu-id="da93e-133">Close Unity</span></span>
1. <span data-ttu-id="da93e-134">Dentro da pasta *ativos* , exclua as seguintes pastas **MRTK** , juntamente com seus arquivos. meta (o projeto pode não ter todas as pastas listadas)</span><span class="sxs-lookup"><span data-stu-id="da93e-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="da93e-135">MRTK/núcleo</span><span class="sxs-lookup"><span data-stu-id="da93e-135">MRTK/Core</span></span>
    - <span data-ttu-id="da93e-136">MRTK/exemplos</span><span class="sxs-lookup"><span data-stu-id="da93e-136">MRTK/Examples</span></span>
    - <span data-ttu-id="da93e-137">MRTK/extensões</span><span class="sxs-lookup"><span data-stu-id="da93e-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="da93e-138">MRTK/provedores</span><span class="sxs-lookup"><span data-stu-id="da93e-138">MRTK/Providers</span></span>
    - <span data-ttu-id="da93e-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="da93e-139">MRTK/SDK</span></span>
    - <span data-ttu-id="da93e-140">MRTK/serviços</span><span class="sxs-lookup"><span data-stu-id="da93e-140">MRTK/Services</span></span>
    - <span data-ttu-id="da93e-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="da93e-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="da93e-142">Se foram feitas modificações nos sombreadores MRTK, crie um backup local antes de excluir a pasta MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="da93e-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="da93e-143">MRTK/ferramentas</span><span class="sxs-lookup"><span data-stu-id="da93e-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="da93e-144">Não exclua a pasta **MixedRealityToolkit. Generated** ou seu arquivo. meta.</span><span class="sxs-lookup"><span data-stu-id="da93e-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="da93e-145">Excluir a pasta de **biblioteca**</span><span class="sxs-lookup"><span data-stu-id="da93e-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="da93e-146">Algumas ferramentas do Unity, como o Unity collab, salvam informações de configuração na pasta de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="da93e-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="da93e-147">Se estiver usando uma ferramenta que faz isso, primeiro copie a pasta de dados da ferramenta da biblioteca antes de excluí-la e, em seguida, restaure-a após a regeneração da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="da93e-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="da93e-148">Abra novamente o projeto no Unity</span><span class="sxs-lookup"><span data-stu-id="da93e-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="da93e-149">Importar os novos pacotes do Unity</span><span class="sxs-lookup"><span data-stu-id="da93e-149">Import the new unity packages</span></span>
    - <span data-ttu-id="da93e-150">Foundation – _importar primeiro este pacote_</span><span class="sxs-lookup"><span data-stu-id="da93e-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="da93e-151">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="da93e-151">Tools</span></span>
    - <span data-ttu-id="da93e-152">Adicional WMZ</span><span class="sxs-lookup"><span data-stu-id="da93e-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="da93e-153">Se extensões adicionais tiverem sido instaladas, talvez elas precisem ser importadas novamente.</span><span class="sxs-lookup"><span data-stu-id="da93e-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="da93e-154">Adicional Disso</span><span class="sxs-lookup"><span data-stu-id="da93e-154">(Optional) Examples</span></span>
1. <span data-ttu-id="da93e-155">Feche o Unity e exclua a pasta de **biblioteca** (leia a observação abaixo primeiro!).</span><span class="sxs-lookup"><span data-stu-id="da93e-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="da93e-156">Esta etapa é necessária para forçar o Unity a atualizar seu banco de dados de ativos e reconciliar perfis personalizados existentes.</span><span class="sxs-lookup"><span data-stu-id="da93e-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="da93e-157">Inicie o Unity e, para cada cena no projeto</span><span class="sxs-lookup"><span data-stu-id="da93e-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="da93e-158">Exclua **MixedRealityToolkit** e **MixedRealityPlayspace**, se presente, da hierarquia.</span><span class="sxs-lookup"><span data-stu-id="da93e-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="da93e-159">Isso excluirá a câmera principal, mas ela será recriada na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="da93e-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="da93e-160">Se qualquer propriedade da câmera principal tiver sido alterada manualmente, elas precisarão ser reaplicadas manualmente depois que a nova câmera for criada.</span><span class="sxs-lookup"><span data-stu-id="da93e-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="da93e-161">Selecione **MixedRealityToolkit-> adicionar à cena e configurar**</span><span class="sxs-lookup"><span data-stu-id="da93e-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="da93e-162">Selecione **utilitários de >-> atualização-> perfis de mapeamento do controlador** (só precisa ser feito uma vez)-isso atualizará todos os perfis de mapeamento do controlador personalizado com os dados e eixos atualizados, deixando as ações de entrada atribuídas personalizadas intactas</span><span class="sxs-lookup"><span data-stu-id="da93e-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="da93e-163">Execute a [ferramenta de migração](../features/tools/migration-window.md) e execute a ferramenta no *projeto completo* para garantir que todo o seu código seja atualizado para a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="da93e-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="da93e-164">A janela de migração contém vários manipuladores de migração diferentes, que devem ser executados por conta própria.</span><span class="sxs-lookup"><span data-stu-id="da93e-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="da93e-165">Esta etapa envolve:</span><span class="sxs-lookup"><span data-stu-id="da93e-165">This step involves:</span></span>
   - <span data-ttu-id="da93e-166">Selecione o primeiro manipulador de migração na lista suspensa **seleção do manipulador de migração** .</span><span class="sxs-lookup"><span data-stu-id="da93e-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="da93e-167">Clique no botão "projeto completo".</span><span class="sxs-lookup"><span data-stu-id="da93e-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="da93e-168">Clique no botão "Adicionar projeto completo para migração" (isso examinará todo o projeto para que os objetos sejam migrados).</span><span class="sxs-lookup"><span data-stu-id="da93e-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="da93e-169">Clique no botão "migrar", que deverá ser habilitado se qualquer objeto migrável for encontrado.</span><span class="sxs-lookup"><span data-stu-id="da93e-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="da93e-170">Repita as três etapas anteriores para cada um dos manipuladores de migração no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="da93e-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="da93e-171">(Consulte [esse problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) que aborda o trabalho que pode ser feito para simplificar esse processo de migração em uma versão futura)</span><span class="sxs-lookup"><span data-stu-id="da93e-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="da93e-172">Alternando de arquivos de ativos de Unity para a ferramenta de recursos misturados de realidade</span><span class="sxs-lookup"><span data-stu-id="da93e-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="da93e-173">A alternância de arquivos de ativos de Unity para a realidade mistura de recursos da ferramenta traz vários benefícios:</span><span class="sxs-lookup"><span data-stu-id="da93e-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="da93e-174">Atualização mais fácil</span><span class="sxs-lookup"><span data-stu-id="da93e-174">Easier updating</span></span>
- <span data-ttu-id="da93e-175">Tempos de compilação mais rápidos</span><span class="sxs-lookup"><span data-stu-id="da93e-175">Faster compile times</span></span>
- <span data-ttu-id="da93e-176">Menos projetos na solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da93e-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="da93e-177">Mudar para o uso da ferramenta de funcionalidade Mixed Reality requer um conjunto único de etapas manuais.</span><span class="sxs-lookup"><span data-stu-id="da93e-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="da93e-178">Salve uma cópia do seu projeto atual.</span><span class="sxs-lookup"><span data-stu-id="da93e-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="da93e-179">Fechar o Unity</span><span class="sxs-lookup"><span data-stu-id="da93e-179">Close Unity</span></span>
1. <span data-ttu-id="da93e-180">Dentro da pasta *ativos* , exclua as seguintes pastas **MRTK** , juntamente com seus arquivos. meta (o projeto pode não ter todas as pastas listadas)</span><span class="sxs-lookup"><span data-stu-id="da93e-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="da93e-181">MRTK/núcleo</span><span class="sxs-lookup"><span data-stu-id="da93e-181">MRTK/Core</span></span>
    - <span data-ttu-id="da93e-182">MRTK/exemplos</span><span class="sxs-lookup"><span data-stu-id="da93e-182">MRTK/Examples</span></span>
    - <span data-ttu-id="da93e-183">MRTK/extensões</span><span class="sxs-lookup"><span data-stu-id="da93e-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="da93e-184">MRTK/provedores</span><span class="sxs-lookup"><span data-stu-id="da93e-184">MRTK/Providers</span></span>
    - <span data-ttu-id="da93e-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="da93e-185">MRTK/SDK</span></span>
    - <span data-ttu-id="da93e-186">MRTK/serviços</span><span class="sxs-lookup"><span data-stu-id="da93e-186">MRTK/Services</span></span>
    - <span data-ttu-id="da93e-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="da93e-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="da93e-188">Se foram feitas modificações nos sombreadores MRTK, crie um backup local antes de excluir a pasta MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="da93e-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="da93e-189">MRTK/ferramentas</span><span class="sxs-lookup"><span data-stu-id="da93e-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="da93e-190">Não exclua a pasta **MixedRealityToolkit. Generated** ou seu arquivo. meta.</span><span class="sxs-lookup"><span data-stu-id="da93e-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="da93e-191">Excluir a pasta de **biblioteca**</span><span class="sxs-lookup"><span data-stu-id="da93e-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="da93e-192">Algumas ferramentas do Unity, como o Unity collab, salvam informações de configuração na pasta de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="da93e-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="da93e-193">Se estiver usando uma ferramenta que faz isso, primeiro copie a pasta de dados da ferramenta da biblioteca antes de excluí-la e, em seguida, restaure-a após a regeneração da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="da93e-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="da93e-194">Abra novamente o projeto no Unity</span><span class="sxs-lookup"><span data-stu-id="da93e-194">Re-open the project in Unity</span></span>

<span data-ttu-id="da93e-195">Depois que as etapas anteriores forem executadas, execute a [ferramenta de funcionalidade Mixed Reality](#mixed-reality-feature-tool) e importe a versão desejada do kit de ferramentas da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="da93e-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="da93e-196">Atualizando 2.3.0 para 2.4.0</span><span class="sxs-lookup"><span data-stu-id="da93e-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="da93e-197">[Renomeações](#folder-renames-in-240) 
 de pasta [Alterações de API](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="da93e-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="da93e-198">Renomeações de pasta no 2.4.0</span><span class="sxs-lookup"><span data-stu-id="da93e-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="da93e-199">As pastas MixedRealityToolkit foram renomeadas e movidas para uma hierarquia comum na versão 2,4.</span><span class="sxs-lookup"><span data-stu-id="da93e-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="da93e-200">Se um aplicativo usar caminhos embutidos em código para MRTK recursos, eles precisarão ser atualizados de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="da93e-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="da93e-201">Pasta anterior</span><span class="sxs-lookup"><span data-stu-id="da93e-201">Previous Folder</span></span> | <span data-ttu-id="da93e-202">Nova Pasta</span><span class="sxs-lookup"><span data-stu-id="da93e-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="da93e-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="da93e-203">MixedRealityToolkit</span></span> | <span data-ttu-id="da93e-204">MRTK/núcleo</span><span class="sxs-lookup"><span data-stu-id="da93e-204">MRTK/Core</span></span> |
| <span data-ttu-id="da93e-205">MixedRealityToolkit. exemplos</span><span class="sxs-lookup"><span data-stu-id="da93e-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="da93e-206">MRTK/exemplos</span><span class="sxs-lookup"><span data-stu-id="da93e-206">MRTK/Examples</span></span> |
| <span data-ttu-id="da93e-207">MixedRealityToolkit. Extensions</span><span class="sxs-lookup"><span data-stu-id="da93e-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="da93e-208">MRTK/extensões</span><span class="sxs-lookup"><span data-stu-id="da93e-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="da93e-209">MixedRealityToolkit. Providers</span><span class="sxs-lookup"><span data-stu-id="da93e-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="da93e-210">MRTK/provedores</span><span class="sxs-lookup"><span data-stu-id="da93e-210">MRTK/Providers</span></span> |
| <span data-ttu-id="da93e-211">MixedRealityToolkit. SDK</span><span class="sxs-lookup"><span data-stu-id="da93e-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="da93e-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="da93e-212">MRTK/SDK</span></span> |
| <span data-ttu-id="da93e-213">MixedRealityToolkit. Services</span><span class="sxs-lookup"><span data-stu-id="da93e-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="da93e-214">MRTK/serviços</span><span class="sxs-lookup"><span data-stu-id="da93e-214">MRTK/Services</span></span> |
| <span data-ttu-id="da93e-215">MixedRealityToolkit. Tests</span><span class="sxs-lookup"><span data-stu-id="da93e-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="da93e-216">MRTK/testes</span><span class="sxs-lookup"><span data-stu-id="da93e-216">MRTK/Tests</span></span> |
| <span data-ttu-id="da93e-217">MixedRealityToolkit. Tools</span><span class="sxs-lookup"><span data-stu-id="da93e-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="da93e-218">MRTK/ferramentas</span><span class="sxs-lookup"><span data-stu-id="da93e-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="da93e-219">O `MixedRealityToolkit.Generated` contém arquivos gerados pelo cliente e permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="da93e-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="da93e-220">Olhare a configuração de olho no 2.4.0</span><span class="sxs-lookup"><span data-stu-id="da93e-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="da93e-221">Esta versão do MRTK modifica as etapas necessárias para a instalação de olho do olhar.</span><span class="sxs-lookup"><span data-stu-id="da93e-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="da93e-222">A caixa de seleção _' IsEyeTrackingEnabled '_ pode ser encontrada nas configurações de olhar do perfil de ponteiro de entrada.</span><span class="sxs-lookup"><span data-stu-id="da93e-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="da93e-223">Marcar essa caixa permitirá olhar com base nos olhos, em vez de olhar padrão com base em cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="da93e-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="da93e-224">Para obter mais informações sobre essas alterações e instruções completas para a configuração de acompanhamento de olho, consulte o artigo [acompanhamento de olho](../features/input/eye-tracking/eye-tracking-basic-setup.md) .</span><span class="sxs-lookup"><span data-stu-id="da93e-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="da93e-225">Comportamento do ponteiro olhar ocular no 2.4.0</span><span class="sxs-lookup"><span data-stu-id="da93e-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="da93e-226">O comportamento de ponteiro padrão olhar de olho foi modificado para corresponder ao comportamento de ponteiro padrão olhar de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="da93e-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="da93e-227">Um ponteiro olhar ocular será suprimido automaticamente quando uma mão for detectada.</span><span class="sxs-lookup"><span data-stu-id="da93e-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="da93e-228">O ponteiro olhar ocular ficará visível novamente depois de dizer "Select".</span><span class="sxs-lookup"><span data-stu-id="da93e-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="da93e-229">Os detalhes sobre as configurações de olhar e mão podem ser encontrados no artigo [olhos e mãos](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) .</span><span class="sxs-lookup"><span data-stu-id="da93e-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="da93e-230">Alterações de API em 2.4.0</span><span class="sxs-lookup"><span data-stu-id="da93e-230">API changes in 2.4.0</span></span>

<span data-ttu-id="da93e-231">**Classes de controlador personalizadas**</span><span class="sxs-lookup"><span data-stu-id="da93e-231">**Custom controller classes**</span></span>

<span data-ttu-id="da93e-232">As classes de controlador personalizadas tinham que ser definidas anteriormente `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="da93e-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="da93e-233">Esse método tornou-se obsoleto em 2,4, pois o parâmetro de destro-canhoto era redundante com a classe de controlador ' própria destromente.</span><span class="sxs-lookup"><span data-stu-id="da93e-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="da93e-234">O novo método não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="da93e-234">The new method has no parameters.</span></span> <span data-ttu-id="da93e-235">Além disso, muitas classes de controlador definidas da mesma forma ( `AssignControllerMappings(DefaultInteractions);` ), portanto, a chamada completa foi Refatorada para baixo `BaseController` e fez uma substituição opcional em vez de obrigatória.</span><span class="sxs-lookup"><span data-stu-id="da93e-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="da93e-236">**Propriedades de olhar de olho**</span><span class="sxs-lookup"><span data-stu-id="da93e-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="da93e-237">A `UseEyeTracking` propriedade da `GazeProvider` implementação de `IMixedRealityEyeGazeProvider` foi renomeada para `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="da93e-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="da93e-238">Se você fez isso anteriormente...</span><span class="sxs-lookup"><span data-stu-id="da93e-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="da93e-239">Faça isso agora...</span><span class="sxs-lookup"><span data-stu-id="da93e-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="da93e-240">**Propriedades de WindowsApiChecker**</span><span class="sxs-lookup"><span data-stu-id="da93e-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="da93e-241">As propriedades WindowsApiChecker a seguir foram marcadas como obsoletas.</span><span class="sxs-lookup"><span data-stu-id="da93e-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="da93e-242">Use `IsMethodAvailable` , `IsPropertyAvailable` ou `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="da93e-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="da93e-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="da93e-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="da93e-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="da93e-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="da93e-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="da93e-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="da93e-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="da93e-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="da93e-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="da93e-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="da93e-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="da93e-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="da93e-249">Não há planos para adicionar propriedades a WindowsApiChecker para versões futuras de contrato de API.</span><span class="sxs-lookup"><span data-stu-id="da93e-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="da93e-250">**GltfMeshPrimitiveAttributes somente leitura**</span><span class="sxs-lookup"><span data-stu-id="da93e-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="da93e-251">Os atributos primitivos de malha gltf usados para ser configurável, agora são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="da93e-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="da93e-252">Seus valores serão definidos uma vez quando desserializados.</span><span class="sxs-lookup"><span data-stu-id="da93e-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="da93e-253">Migração de ícone de botão personalizado</span><span class="sxs-lookup"><span data-stu-id="da93e-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="da93e-254">Os ícones de botão personalizados anteriormente exigiam a atribuição de um novo material ao processador quádruplo do botão.</span><span class="sxs-lookup"><span data-stu-id="da93e-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="da93e-255">Isso não é mais necessário e é recomendável mover as texturas do ícone personalizado para um ícone do.</span><span class="sxs-lookup"><span data-stu-id="da93e-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="da93e-256">Os materiais e os ícones personalizados existentes são preservados.</span><span class="sxs-lookup"><span data-stu-id="da93e-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="da93e-257">No entanto, elas serão menos ideais até que sejam atualizadas.</span><span class="sxs-lookup"><span data-stu-id="da93e-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="da93e-258">Para atualizar os ativos em todos os botões do projeto para o novo formato recomendado, use o ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="da93e-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="da93e-259">(O kit de ferramentas da realidade mista – utilitários de >-> janela de migração-> seleção do manipulador de migração-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="da93e-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Caixa de diálogo atualizar janela](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="da93e-261">Se um ícone não for encontrado no conjunto de ícones padrão durante a migração, um conjunto de ícones personalizado será criado em MixedRealityToolkit. Generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="da93e-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="da93e-262">Uma caixa de diálogo indicará que isso foi realizado.</span><span class="sxs-lookup"><span data-stu-id="da93e-262">A dialog will indicate that this has taken place.</span></span>

![Notificação de ícone personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="da93e-264">Atualizando 2.2.0 para 2.3.0</span><span class="sxs-lookup"><span data-stu-id="da93e-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="da93e-265">Alterações de API</span><span class="sxs-lookup"><span data-stu-id="da93e-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="da93e-266">Alterações de API em 2.3.0</span><span class="sxs-lookup"><span data-stu-id="da93e-266">API changes in 2.3.0</span></span>

<span data-ttu-id="da93e-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="da93e-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="da93e-268">O campo particular ControllerPoseSynchronizer. destros foi marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="da93e-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="da93e-269">Isso deve ter um impacto mínimo sobre os aplicativos, pois o campo não é visível fora de sua classe.</span><span class="sxs-lookup"><span data-stu-id="da93e-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="da93e-270">O setter da propriedade pública ControllerPoseSynchronizer. Destroy foi removido ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="da93e-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="da93e-271">**MSBuild para Unity**</span><span class="sxs-lookup"><span data-stu-id="da93e-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="da93e-272">Esta versão do MRTK usa uma versão mais recente do MSBuild para o Unity do que as versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="da93e-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="da93e-273">Durante o carregamento do projeto, se a versão mais antiga estiver listada no manifesto do Gerenciador de pacotes do Unity, a caixa de diálogo de configuração será exibida com a opção Habilitar MSBuild para Unity marcada.</span><span class="sxs-lookup"><span data-stu-id="da93e-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="da93e-274">A aplicação executará uma atualização.</span><span class="sxs-lookup"><span data-stu-id="da93e-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="da93e-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="da93e-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="da93e-276">A classe ScriptingUtilities foi marcada como obsoleta e foi substituída por ScriptUtilities, no assembly Microsoft. MixedReality. Toolkit. editor. Utilities.</span><span class="sxs-lookup"><span data-stu-id="da93e-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="da93e-277">A nova classe refina o comportamento anterior e adiciona suporte para a remoção de definições de script.</span><span class="sxs-lookup"><span data-stu-id="da93e-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="da93e-278">Enquanto o código existente continuará a funcionar na versão 2.3.0, é recomendável atualizar para a nova classe.</span><span class="sxs-lookup"><span data-stu-id="da93e-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="da93e-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="da93e-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="da93e-280">Os membros lineRendererSelected e lineRendererNoTarget da classe ShellHandRayPointer foram substituídos por lineMaterialSelected e lineMaterialNoTarget, respectivamente ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="da93e-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="da93e-281">Substitua lineRendererSelected por lineMaterialSelected e/ou lineRendererNoTarget por lineMaterialNoTarget para resolver erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="da93e-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="da93e-282">**Observador espacial Startupbehavior fazendo**</span><span class="sxs-lookup"><span data-stu-id="da93e-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="da93e-283">Os observadores espaciais criados na `BaseSpatialObserver` classe agora respeitam o valor de startupbehavior fazendo quando reabilitados ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="da93e-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="da93e-284">Nenhuma alteração é necessária para aproveitar essa correção.</span><span class="sxs-lookup"><span data-stu-id="da93e-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="da93e-285">**Pré-fabricados de controle UX atualizado para usar o PressableButton**</span><span class="sxs-lookup"><span data-stu-id="da93e-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="da93e-286">Os pré-fabricados a seguir agora estão usando o componente PressableButton em vez de TouchHandler para interação próxima ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span><span class="sxs-lookup"><span data-stu-id="da93e-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="da93e-287">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="da93e-287">AnimationButton</span></span>
- <span data-ttu-id="da93e-288">Botão</span><span class="sxs-lookup"><span data-stu-id="da93e-288">Button</span></span>
- <span data-ttu-id="da93e-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="da93e-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="da93e-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="da93e-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="da93e-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="da93e-291">CheckBox</span></span>
- <span data-ttu-id="da93e-292">Radialset</span><span class="sxs-lookup"><span data-stu-id="da93e-292">RadialSet</span></span>
- <span data-ttu-id="da93e-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="da93e-293">ToggleButton</span></span>
- <span data-ttu-id="da93e-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="da93e-294">ToggleSwitch</span></span>
- <span data-ttu-id="da93e-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="da93e-295">UnityUIButton</span></span>
- <span data-ttu-id="da93e-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="da93e-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="da93e-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="da93e-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="da93e-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="da93e-298">UnityUIToggleButton</span></span>

<span data-ttu-id="da93e-299">O código do aplicativo pode exigir atualização devido a essa alteração.</span><span class="sxs-lookup"><span data-stu-id="da93e-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="da93e-300">**Namespace WindowsMixedRealityUtilities**</span><span class="sxs-lookup"><span data-stu-id="da93e-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="da93e-301">O namespace de WindowsMixedRealityUtilities mudou de Microsoft. MixedReality. Toolkit. WindowsMixedReality. Input para Microsoft. MixedReality. Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="da93e-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="da93e-302">Atualize #using instruções para resolver erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="da93e-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="da93e-303">Atualizando 2.1.0 para 2.2.0</span><span class="sxs-lookup"><span data-stu-id="da93e-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="da93e-304">Alterações de API</span><span class="sxs-lookup"><span data-stu-id="da93e-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="da93e-305">Alterações de API em 2.2.0</span><span class="sxs-lookup"><span data-stu-id="da93e-305">API changes in 2.2.0</span></span>

<span data-ttu-id="da93e-306">**IMixedRealityBoundarySystem. Contains**</span><span class="sxs-lookup"><span data-stu-id="da93e-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="da93e-307">Esse método levou anteriormente em uma enumeração experimental específica definida pelo Unity.</span><span class="sxs-lookup"><span data-stu-id="da93e-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="da93e-308">Agora, ele usa um enum definido pelo MRTK que é idêntico ao enum do Unity.</span><span class="sxs-lookup"><span data-stu-id="da93e-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="da93e-309">Essa alteração ajuda a preparar o MRTK para as APIs de limite futuras do Unity.</span><span class="sxs-lookup"><span data-stu-id="da93e-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="da93e-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="da93e-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="da93e-311">Para descrever melhor os requisitos de suporte a um perfil, o MixedRealityServiceProfileAttribute foi atualizado para adicionar uma coleção opcional de tipos excluídos.</span><span class="sxs-lookup"><span data-stu-id="da93e-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="da93e-312">Como parte dessa alteração, a Propriedade ServiceType foi alterada de Type para Type [] e foi renomeada para RequiredTypes.</span><span class="sxs-lookup"><span data-stu-id="da93e-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="da93e-313">Uma segunda propriedade, ExcludedTypes também foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="da93e-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="da93e-314">Atualizando 2.0.0 para 2.1.0</span><span class="sxs-lookup"><span data-stu-id="da93e-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="da93e-315">Alterações de API</span><span class="sxs-lookup"><span data-stu-id="da93e-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="da93e-316">Alterações de perfil</span><span class="sxs-lookup"><span data-stu-id="da93e-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="da93e-317">Alterações de API em 2.1.0</span><span class="sxs-lookup"><span data-stu-id="da93e-317">API changes in 2.1.0</span></span>

<span data-ttu-id="da93e-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="da93e-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="da93e-319">O `BaseNearInteractionTouchable` foi modificado para marcar o `OnValidate` método como virtual.</span><span class="sxs-lookup"><span data-stu-id="da93e-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="da93e-320">As classes que estendem `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI` ) foram atualizadas para refletir essa alteração.</span><span class="sxs-lookup"><span data-stu-id="da93e-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="da93e-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="da93e-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="da93e-322">A classe `ColliderNearInteractionTouchable` foi substituída.</span><span class="sxs-lookup"><span data-stu-id="da93e-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="da93e-323">Atualize as referências de código a serem usadas `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="da93e-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="da93e-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="da93e-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="da93e-325">**_Mais_**</span><span class="sxs-lookup"><span data-stu-id="da93e-325">**_Added_**</span></span>

<span data-ttu-id="da93e-326">`IMixedRealityMouseDeviceManager` foram adicionadas `CursorSpeed` e `WheelSpeed` Propriedades.</span><span class="sxs-lookup"><span data-stu-id="da93e-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="da93e-327">Essas propriedades permitem que os aplicativos especifiquem um valor multiplicador pelo qual a velocidade do cursor e da roda, respectivamente, será dimensionada.</span><span class="sxs-lookup"><span data-stu-id="da93e-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="da93e-328">Essa é uma alteração significativa e requer que as implementações existentes do Gerenciador de dispositivos do mouse sejam modificadas.</span><span class="sxs-lookup"><span data-stu-id="da93e-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="da93e-329">Essa alteração não é compatível com versões anteriores com a versão 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="da93e-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="da93e-330">**_Preterido_**</span><span class="sxs-lookup"><span data-stu-id="da93e-330">**_Deprecated_**</span></span>

<span data-ttu-id="da93e-331">A `MouseInputProfile` propriedade foi marcada como obsoleta e será removida de uma versão futura do kit de ferramentas do Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="da93e-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="da93e-332">É recomendável que o código do aplicativo não use mais essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="da93e-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="da93e-333">**Interativo**</span><span class="sxs-lookup"><span data-stu-id="da93e-333">**Interactable**</span></span>

<span data-ttu-id="da93e-334">Os métodos e as propriedades a seguir foram preteridos e serão removidos de uma versão futura do kit de ferramentas do Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="da93e-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="da93e-335">A recomendação é atualizar o código do aplicativo de acordo com as diretrizes contidas no atributo obsoleto e exibi-lo no console do.</span><span class="sxs-lookup"><span data-stu-id="da93e-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

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

<span data-ttu-id="da93e-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="da93e-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="da93e-337">A `NearInteractionTouchableSurface` classe foi adicionada e agora serve como a classe base para `NearInteractionTouchable` e `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="da93e-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="da93e-338">Alterações de perfil em 2.1.0</span><span class="sxs-lookup"><span data-stu-id="da93e-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="da93e-339">**Perfil de acompanhamento à mão**</span><span class="sxs-lookup"><span data-stu-id="da93e-339">**Hand tracking profile**</span></span>

<span data-ttu-id="da93e-340">A malha de mão e as visualizações conjuntas agora têm um editor separado e configurações de Player.</span><span class="sxs-lookup"><span data-stu-id="da93e-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="da93e-341">O perfil de acompanhamento de mão foi atualizado para permitir a definição dessas visualizações como; Nada, tudo, editor ou Player.</span><span class="sxs-lookup"><span data-stu-id="da93e-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Modos de visualização de mão](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="da93e-343">Os perfis de controle de mão personalizada talvez precisem ser atualizados para funcionar corretamente com a versão 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="da93e-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="da93e-344">Essa alteração não é compatível com versões anteriores com a versão 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="da93e-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="da93e-345">**Perfil de simulação de entrada**</span><span class="sxs-lookup"><span data-stu-id="da93e-345">**Input simulation profile**</span></span>

<span data-ttu-id="da93e-346">O sistema de simulação de entrada foi atualizado, o que altera algumas configurações no perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="da93e-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="da93e-347">Algumas alterações não podem ser migradas automaticamente e os usuários podem descobrir que os perfis estão usando valores padrão.</span><span class="sxs-lookup"><span data-stu-id="da93e-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="da93e-348">Todas as associações de botão do mouse e do código-chave no perfil foram substituídas por uma `KeyBinding` estrutura genérica, que armazena o tipo de associação (chave ou mouse), bem como o código de associação real (código de tecla ou número do botão do mouse, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="da93e-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="da93e-349">O struct tem seu próprio Inspetor, que permite a exibição unificada e oferece uma ferramenta de "ligação automática" para definir rapidamente as associações de chave pressionando a respectiva chave em vez de selecionar em uma grande lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="da93e-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="da93e-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="da93e-350">FastControlKey</span></span>
    - <span data-ttu-id="da93e-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="da93e-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="da93e-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="da93e-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="da93e-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="da93e-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="da93e-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="da93e-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="da93e-355">`MouseLookToggle` foi anteriormente incluído no `MouseLookButton` enum como `InputSimulationMouseButton.Focused` , agora é uma opção separada.</span><span class="sxs-lookup"><span data-stu-id="da93e-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="da93e-356">Quando habilitado, a câmera continuará girando com o mouse depois de soltar o botão, até que a tecla escape seja pressionada.</span><span class="sxs-lookup"><span data-stu-id="da93e-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="da93e-357">`HandDepthMultiplier` o valor padrão foi reduzido de 0,1 para 0, 3 para acomodar algumas alterações na simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="da93e-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="da93e-358">Se a câmera se mover muito rapidamente durante a rolagem, tente reduzir esse valor.</span><span class="sxs-lookup"><span data-stu-id="da93e-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="da93e-359">As chaves para as mãos de rotação foram removidas, a rotação de mãos agora é controlada pelo mouse também.</span><span class="sxs-lookup"><span data-stu-id="da93e-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="da93e-360">Manter `HandRotateButton` (Ctrl) junto com a chave de manipulação esquerda/direita (LShift/Space) habilitará a rotação da mão.</span><span class="sxs-lookup"><span data-stu-id="da93e-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="da93e-361">Um novo eixo "upDown" foi introduzido na lista eixo de entrada.</span><span class="sxs-lookup"><span data-stu-id="da93e-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="da93e-362">Isso controla a movimentação da câmera na vertical e usa como padrão as chaves p/E, bem como os botões de gatilho do controlador.</span><span class="sxs-lookup"><span data-stu-id="da93e-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="da93e-363">Para obter mais informações sobre essas alterações, consulte o artigo [serviço de simulação de entrada](../features/input-simulation/input-simulation-service.md) .</span><span class="sxs-lookup"><span data-stu-id="da93e-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="da93e-364">**Perfil do provedor de dados do mouse**</span><span class="sxs-lookup"><span data-stu-id="da93e-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="da93e-365">O perfil do provedor de dados do mouse foi atualizado para expor as novas `CursorSpeed` `WheelSpeed` Propriedades e.</span><span class="sxs-lookup"><span data-stu-id="da93e-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="da93e-366">Os perfis personalizados existentes terão automaticamente os valores padrão fornecidos.</span><span class="sxs-lookup"><span data-stu-id="da93e-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="da93e-367">Quando o perfil for salvo, esses novos valores serão persistidos.</span><span class="sxs-lookup"><span data-stu-id="da93e-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="da93e-368">**Perfil de mapeamento do controlador**</span><span class="sxs-lookup"><span data-stu-id="da93e-368">**Controller mapping profile**</span></span>

<span data-ttu-id="da93e-369">Alguns eixos e tipos de entrada foram atualizados no 2.1.0, especialmente em relação à plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="da93e-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="da93e-370">Certifique-se de selecionar os **utilitários > MixedRealityToolkit-> atualização-> perfis de mapeamento do controlador** ao atualizar.</span><span class="sxs-lookup"><span data-stu-id="da93e-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="da93e-371">Isso atualizará todos os perfis de mapeamento do controlador personalizado com os dados e eixos atualizados, deixando as ações de entrada atribuídas personalizadas intactas.</span><span class="sxs-lookup"><span data-stu-id="da93e-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="da93e-372">Atualizando o RC2 para o 2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="da93e-373">Entre as versões RC2 e 2.0.0 do kit de ferramentas de realidade misturada da Microsoft, foram feitas alterações que podem afetar os projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="da93e-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="da93e-374">Este documento descreve essas alterações e como atualizar projetos para a versão 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="da93e-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="da93e-375">Alterações de API</span><span class="sxs-lookup"><span data-stu-id="da93e-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="da93e-376">Alterações de nome de assembly</span><span class="sxs-lookup"><span data-stu-id="da93e-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="da93e-377">Alterações de API em 2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-377">API changes in 2.0.0</span></span>

<span data-ttu-id="da93e-378">Desde o lançamento do RC2, houve várias alterações de API, incluindo algumas que podem interromper projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="da93e-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="da93e-379">As seções a seguir descrevem as alterações que ocorreram entre as versões RC2 e 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="da93e-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="da93e-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="da93e-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="da93e-381">As propriedades públicas a seguir no objeto MixedRealityToolkit foram preteridas.</span><span class="sxs-lookup"><span data-stu-id="da93e-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="da93e-382">`RegisteredMixedRealityServices` Não contém mais a coleção de serviços de extensões registradas e provedores de dados.</span><span class="sxs-lookup"><span data-stu-id="da93e-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="da93e-383">Para acessar os serviços de extensão, use `MixedRealityServiceRegistry.TryGetService<T>` .</span><span class="sxs-lookup"><span data-stu-id="da93e-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="da93e-384">Para acessar os provedores de dados, converta a instância de serviço [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) e use `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="da93e-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="da93e-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) ou [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) em vez das seguintes propriedades preteridas</span><span class="sxs-lookup"><span data-stu-id="da93e-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="da93e-386">**Principaisservices**</span><span class="sxs-lookup"><span data-stu-id="da93e-386">**CoreServices**</span></span>

<span data-ttu-id="da93e-387">A [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) classe é a substituição para os acessadores de sistema estáticos (ex: BoundarySystem) encontrados no `MixedRealityToolkit` objeto.</span><span class="sxs-lookup"><span data-stu-id="da93e-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="da93e-388">Os `MixedRealityToolkit` acessadores do sistema foram preteridos na versão 2.0.0 e serão removidos em uma versão futura do MRTK.</span><span class="sxs-lookup"><span data-stu-id="da93e-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="da93e-389">O exemplo de código a seguir ilustra o padrão antigo e o novo.</span><span class="sxs-lookup"><span data-stu-id="da93e-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="da93e-390">Usar a nova classe CoreSystem garantirá que o código do aplicativo não precisará ser atualizado se você alterar o aplicativo para usar um registrador de serviço diferente (por exemplo, um dos gerenciadores de serviços experimentais).</span><span class="sxs-lookup"><span data-stu-id="da93e-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="da93e-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="da93e-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="da93e-392">Com a adição do IMixedRealityRaycastProvider, o perfil de configuração do sistema de entrada foi alterado.</span><span class="sxs-lookup"><span data-stu-id="da93e-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="da93e-393">Se você tiver um perfil personalizado, poderá receber os erros na imagem a seguir ao executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da93e-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Selecionando o provedor Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="da93e-395">Para corrigi-los, adicione uma instância do IMixedRealityRaycastProvider ao seu perfil do sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="da93e-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Selecionando o provedor Raycast 2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="da93e-397">**Sistema de eventos**</span><span class="sxs-lookup"><span data-stu-id="da93e-397">**Event System**</span></span>

- <span data-ttu-id="da93e-398">Os `IMixedRealityEventSystem` métodos antigos da API `Register` e foram `Unregister` marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="da93e-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="da93e-399">Eles são preservados para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="da93e-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="da93e-400">`InputSystemGlobalListener` foi marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="da93e-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="da93e-401">Sua funcionalidade não foi alterada.</span><span class="sxs-lookup"><span data-stu-id="da93e-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="da93e-402">`BaseInputHandler` a classe base foi alterada de `InputSystemGlobalListener` para `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="da93e-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="da93e-403">Essa é uma alteração significativa para os descendentes de `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="da93e-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="da93e-404">**_Motivação por trás da alteração_**</span><span class="sxs-lookup"><span data-stu-id="da93e-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="da93e-405">A antiga API do sistema de eventos `Register` e `Unregister` poderia causar vários problemas em tempo de execução, a principal é:</span><span class="sxs-lookup"><span data-stu-id="da93e-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="da93e-406">Se um componente for registrado para eventos globais, ele receberá eventos de entrada globais de *todos os* tipos.</span><span class="sxs-lookup"><span data-stu-id="da93e-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="da93e-407">Se um dos componentes em um objeto for registrado para eventos de entrada globais, todos os componentes nesse objeto receberão eventos de entrada globais de *todos os* tipos.</span><span class="sxs-lookup"><span data-stu-id="da93e-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="da93e-408">Se dois componentes no mesmo objeto forem registrados em eventos globais e um for desabilitado em tempo de execução, o segundo interromperá o recebimento de eventos globais.</span><span class="sxs-lookup"><span data-stu-id="da93e-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="da93e-409">Nova API `RegisterHandler` e `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="da93e-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="da93e-410">Fornece um controle explícito e granular sobre o qual os eventos de entrada devem ser ouvidos globalmente e que devem ser baseados em foco.</span><span class="sxs-lookup"><span data-stu-id="da93e-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="da93e-411">Permite que vários componentes no mesmo objeto escutem eventos globais independentemente um do outro.</span><span class="sxs-lookup"><span data-stu-id="da93e-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="da93e-412">**_Como migrar_**</span><span class="sxs-lookup"><span data-stu-id="da93e-412">**_How to migrate_**</span></span>

- <span data-ttu-id="da93e-413">Se você estiver chamando a `Register` / `Unregister` API diretamente antes, substitua essas chamadas por chamadas para `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="da93e-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="da93e-414">Use interfaces de manipulador que você implementar como parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="da93e-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="da93e-415">Se você implementar várias interfaces e várias delas ouvirem os eventos de entrada globais, chame `RegisterHandler` várias vezes.</span><span class="sxs-lookup"><span data-stu-id="da93e-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="da93e-416">Se você estiver herdando de `InputSystemGlobalListener` , altere a herança para `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="da93e-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="da93e-417">Implementar `RegisterHandlers` e `UnregisterHandlers` abstrair métodos.</span><span class="sxs-lookup"><span data-stu-id="da93e-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="da93e-418">Na chamada de implementação `inputSystem.RegisterHandler` ( `inputSystem.UnregisterHandler` ) para registrar em todas as interfaces de manipulador para as quais você deseja escutar eventos globais.</span><span class="sxs-lookup"><span data-stu-id="da93e-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="da93e-419">Se você estiver herdando de `BaseInputHandler` `RegisterHandlers` métodos Implement e `UnregisterHandlers` Abstract (o mesmo que for `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="da93e-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="da93e-420">**_Exemplos de migração_**</span><span class="sxs-lookup"><span data-stu-id="da93e-420">**_Examples of migration_**</span></span>

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

<span data-ttu-id="da93e-421">**Conscientização espacial**</span><span class="sxs-lookup"><span data-stu-id="da93e-421">**Spatial Awareness**</span></span>

<span data-ttu-id="da93e-422">As interfaces IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver fizeram várias alterações significativas, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="da93e-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="da93e-423">**_For_**</span><span class="sxs-lookup"><span data-stu-id="da93e-423">**_Changes_**</span></span>

<span data-ttu-id="da93e-424">Os seguintes métodos foram renomeados para descrever melhor seu uso.</span><span class="sxs-lookup"><span data-stu-id="da93e-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="da93e-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` foi renomeado para `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` para esclarecer seu uso.</span><span class="sxs-lookup"><span data-stu-id="da93e-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="da93e-426">**_Adições_**</span><span class="sxs-lookup"><span data-stu-id="da93e-426">**_Additions_**</span></span>

<span data-ttu-id="da93e-427">Com base nos comentários dos clientes, o suporte à remoção fácil de dados de reconhecimento espacial observados anteriormente foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="da93e-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="da93e-428">**Solucionadores**</span><span class="sxs-lookup"><span data-stu-id="da93e-428">**Solvers**</span></span>

<span data-ttu-id="da93e-429">Alguns componentes do Solver e a classe SolverHandler Manager foram alterados para corrigir vários bugs e para um uso mais intuitivo.</span><span class="sxs-lookup"><span data-stu-id="da93e-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="da93e-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="da93e-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="da93e-431">A classe não se estende mais de `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="da93e-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="da93e-432">`TrackedObjectToReference` Propriedade pública preterida e renomeada como `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="da93e-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="da93e-433">`TrackedObjectType` substitui os valores da & do controlador à esquerda.</span><span class="sxs-lookup"><span data-stu-id="da93e-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="da93e-434">Em vez disso, use `MotionController` `HandJoint` valores ou e atualize `TrackedHandedness` a nova propriedade para limitar o controle para o controlador esquerdo ou direito</span><span class="sxs-lookup"><span data-stu-id="da93e-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="da93e-435">**_Entre_**</span><span class="sxs-lookup"><span data-stu-id="da93e-435">**_InBetween_**</span></span>

- <span data-ttu-id="da93e-436">`TrackedObjectForSecondTransform` Propriedade pública preterida e renomeada como `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="da93e-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="da93e-437">`AttachSecondTransformToNewTrackedObject()` foi removido.</span><span class="sxs-lookup"><span data-stu-id="da93e-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="da93e-438">Para atualizar o resolvedor, modifique as propriedades públicas (ou seja,</span><span class="sxs-lookup"><span data-stu-id="da93e-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="da93e-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="da93e-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="da93e-440">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="da93e-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="da93e-441">`MaxDistance` Propriedade pública preterida e renomeada como `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="da93e-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="da93e-442">`CloseDistance` Propriedade pública preterida e renomeada como `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="da93e-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="da93e-443">O valor padrão de `RaycastDirectionMode` é agora `TrackedTargetForward` qual raycasts na direção da transformação de destino rastreada em frente</span><span class="sxs-lookup"><span data-stu-id="da93e-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="da93e-444">`OrientationMode` os valores de enumeração `Vertical` e `Full` , foram renomeados para `TrackedTarget` e `SurfaceNormal` respectivamente</span><span class="sxs-lookup"><span data-stu-id="da93e-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="da93e-445">`KeepOrientationVertical` a propriedade pública foi adicionada para controlar se a orientação do gameobject associado permanece vertical</span><span class="sxs-lookup"><span data-stu-id="da93e-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="da93e-446">**Botões**</span><span class="sxs-lookup"><span data-stu-id="da93e-446">**Buttons**</span></span>

- <span data-ttu-id="da93e-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) Agora tem `DistanceSpaceMode` a propriedade definida `Local` como padrão.</span><span class="sxs-lookup"><span data-stu-id="da93e-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="da93e-448">Isso permite que os botões sejam dimensionados enquanto ainda podem ser prensados</span><span class="sxs-lookup"><span data-stu-id="da93e-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="da93e-449">**Esfera de recorte**</span><span class="sxs-lookup"><span data-stu-id="da93e-449">**Clipping Sphere**</span></span>

<span data-ttu-id="da93e-450">A interface ClippingSphere foi alterada para espelhar as APIs encontradas em ClippingBox e ClippingPlane.</span><span class="sxs-lookup"><span data-stu-id="da93e-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="da93e-451">A propriedade RADIUS do ClippingSphere agora é implicitamente calculada com base na escala de transformação.</span><span class="sxs-lookup"><span data-stu-id="da93e-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="da93e-452">Antes que os desenvolvedores precisem especificar o raio do ClippingSphere no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="da93e-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="da93e-453">Se você quiser alterar o raio, basta atualizar a escala de transformação da transformação como faria normalmente.</span><span class="sxs-lookup"><span data-stu-id="da93e-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="da93e-454">**NearInteractionTouchable e PokePointer**</span><span class="sxs-lookup"><span data-stu-id="da93e-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="da93e-455">NearInteractionTouchable não lida com o toque da tela da interface do usuário do Unity mais.</span><span class="sxs-lookup"><span data-stu-id="da93e-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="da93e-456">A classe NearInteractionTouchableUnityUI deve ser usada para a interface do usuário do Unity touchables agora.</span><span class="sxs-lookup"><span data-stu-id="da93e-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="da93e-457">ColliderNearInteractionTouchable é a nova classe base para touchables com base em colisors, ou seja, cada tocável, exceto NearInteractionTouchableUnityUI.</span><span class="sxs-lookup"><span data-stu-id="da93e-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="da93e-458">BaseNearInteractionTouchable. DistFront foi movido e renomeado para PokePointer. TouchableDistance essa é a distância e a qual o PokePointer pode interagir com touchables.</span><span class="sxs-lookup"><span data-stu-id="da93e-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="da93e-459">Anteriormente, cada tocável tinha sua própria distância máxima de interação, mas agora isso é definido no PokePointer, o que permite uma melhor otimização.</span><span class="sxs-lookup"><span data-stu-id="da93e-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="da93e-460">BaseNearInteractionTouchable. DistBack foi renomeado para PokeThreshold isso torna claro que PokeThreshold é o equivalente a DebounceThreshold.</span><span class="sxs-lookup"><span data-stu-id="da93e-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="da93e-461">Um toque é ativado quando o PokeThreshold é cruzado e liberado quando DebounceThreshold é cruzado.</span><span class="sxs-lookup"><span data-stu-id="da93e-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="da93e-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="da93e-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="da93e-463">O `Microsoft.MixedReality.Toolkit` namespace foi adicionado a `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` , e `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="da93e-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="da93e-464">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="da93e-464">**PointerClickHandler**</span></span>

<span data-ttu-id="da93e-465">A classe `PointerClickHandler` foi substituída.</span><span class="sxs-lookup"><span data-stu-id="da93e-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="da93e-466">O `PointerHandler` deve ser usado em vez disso, ele fornece a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="da93e-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="da93e-467">**Suporte ao clicador de HoloLens**</span><span class="sxs-lookup"><span data-stu-id="da93e-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="da93e-468">Os mapeamentos do controlador do clico do HoloLens foram alterados de um não lado [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) a lado [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) .</span><span class="sxs-lookup"><span data-stu-id="da93e-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="da93e-469">Para considerar isso, um atualizador automático será executado na primeira vez que você abrir o perfil do ControllerMapping.</span><span class="sxs-lookup"><span data-stu-id="da93e-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="da93e-470">Abra qualquer perfil personalizado pelo menos uma vez após a atualização para o 2.0.0 para disparar essa etapa de migração única.</span><span class="sxs-lookup"><span data-stu-id="da93e-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="da93e-471">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="da93e-471">**InteractableHighlight**</span></span>

<span data-ttu-id="da93e-472">A classe `InteractableHighlight` foi substituída.</span><span class="sxs-lookup"><span data-stu-id="da93e-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="da93e-473">A `InteractableOnFocus` classe e o `FocusInteractableStates` ativo devem ser usados em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="da93e-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="da93e-474">Para criar um novo `Theme` ativo para o `InteractableOnFocus` , clique com o botão direito do mouse na janela do projeto e selecione *criar*  >  tema do *Kit de ferramentas de realidade mista*  >    >  .</span><span class="sxs-lookup"><span data-stu-id="da93e-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="da93e-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="da93e-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="da93e-476">`HandInteractionPanZoom` foi movido para o namespace da interface do usuário porque não era um componente de entrada.</span><span class="sxs-lookup"><span data-stu-id="da93e-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="da93e-477">`HandPanEventData` também foi movido para esse namespace e simplificado para corresponder a outros dados de eventos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="da93e-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="da93e-478">Alterações de nome de assembly em 2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="da93e-479">Na versão 2.0.0, todos os nomes de assembly oficiais do kit de ferramentas de realidade misto e seus arquivos de definição de assembly (. asmdef) associados foram atualizados para se ajustarem ao padrão a seguir.</span><span class="sxs-lookup"><span data-stu-id="da93e-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="da93e-480">Em alguns casos, vários assemblies foram mesclados para criar um Unity melhor de seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="da93e-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="da93e-481">Se o seu projeto usa arquivos. asmdef personalizados, eles podem exigir atualização.</span><span class="sxs-lookup"><span data-stu-id="da93e-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="da93e-482">As tabelas a seguir descrevem como os nomes de arquivo RC2. asmdef são mapeados para a versão 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="da93e-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="da93e-483">Todos os nomes de assembly correspondem ao nome do arquivo. asmdef.</span><span class="sxs-lookup"><span data-stu-id="da93e-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="da93e-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="da93e-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="da93e-485">RC2</span><span class="sxs-lookup"><span data-stu-id="da93e-485">RC2</span></span> | <span data-ttu-id="da93e-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="da93e-487">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="da93e-488">Microsoft. MixedReality. Toolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="da93e-489">MixedRealityToolkit. Core. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="da93e-490">Microsoft. MixedReality. Toolkit. editor. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="da93e-491">MixedRealityToolkit. Core. Definitions. Utilities. editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="da93e-492">Removido, use Microsoft. MixedReality. Toolkit. editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="da93e-493">MixedRealityToolkit. Core. Extensions. EditorClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="da93e-494">Microsoft. MixedReality. Toolkit. editor. ClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="da93e-495">MixedRealityToolkit. Core. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="da93e-496">Microsoft. MixedReality. Toolkit. editor. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="da93e-497">MixedRealityToolkit. Core. Inspectors. testinspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="da93e-498">Microsoft. MixedReality. Toolkit. editor. userinspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="da93e-499">MixedRealityToolkit. Core. UtilitiesAsync. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="da93e-500">Microsoft. MixedReality. Toolkit. Async. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="da93e-501">MixedRealityToolkit. Core. Utilities. editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="da93e-502">Microsoft. MixedReality. Toolkit. editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="da93e-503">MixedRealityToolkit. Utilities. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="da93e-504">Microsoft. MixedReality. Toolkit. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="da93e-505">MixedRealityToolkit. Utilities. Gltf. conporters. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="da93e-506">Microsoft. MixedReality. Toolkit. Gltf. Importers. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="da93e-507">**MixedRealityToolkit. Providers**</span><span class="sxs-lookup"><span data-stu-id="da93e-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="da93e-508">RC2</span><span class="sxs-lookup"><span data-stu-id="da93e-508">RC2</span></span> | <span data-ttu-id="da93e-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="da93e-510">MixedRealityToolkit. Providers. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="da93e-511">Microsoft. MixedReality. Toolkit. Providers. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="da93e-512">MixedRealityToolkit. Providers. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="da93e-513">Microsoft. MixedReality. Toolkit. Providers. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="da93e-514">MixedRealityToolkit. Providers. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="da93e-515">Microsoft. MixedReality. Toolkit. Providers. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="da93e-516">**MixedRealityToolkit. Services**</span><span class="sxs-lookup"><span data-stu-id="da93e-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="da93e-517">RC2</span><span class="sxs-lookup"><span data-stu-id="da93e-517">RC2</span></span> | <span data-ttu-id="da93e-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="da93e-519">MixedRealityToolkit. Services. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="da93e-520">Microsoft. MixedReality. Toolkit. Services. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="da93e-521">MixedRealityToolkit. Services. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="da93e-522">Microsoft. MixedReality. Toolkit. Services. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="da93e-523">MixedRealityToolkit. Services. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="da93e-524">Microsoft. MixedReality. Toolkit. Services. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="da93e-525">MixedRealityToolkit. Services. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="da93e-526">Microsoft. MixedReality. Toolkit. Services. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="da93e-527">MixedRealityToolkit. Services. InputSimulation. editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="da93e-528">Microsoft. MixedReality. Toolkit. Services. InputSimulation. editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="da93e-529">MixedRealityToolkit. Services. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="da93e-530">Microsoft. MixedReality. Toolkit. Services. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="da93e-531">MixedRealityToolkit. Services. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="da93e-532">Microsoft. MixedReality. Toolkit. Services. InputSystem. editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="da93e-533">MixedRealityToolkit. Services. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="da93e-534">Microsoft. MixedReality. Toolkit. Services. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="da93e-535">MixedRealityToolkit. Services. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="da93e-536">Microsoft. MixedReality. Toolkit. Services. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="da93e-537">MixedRealityToolkit. Services. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="da93e-538">Microsoft. MixedReality. Toolkit. Services. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="da93e-539">**MixedRealityToolkit. SDK**</span><span class="sxs-lookup"><span data-stu-id="da93e-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="da93e-540">RC2</span><span class="sxs-lookup"><span data-stu-id="da93e-540">RC2</span></span> | <span data-ttu-id="da93e-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="da93e-542">MixedRealityToolkit. SDK. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="da93e-543">Microsoft. MixedReality. Toolkit. SDK. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="da93e-544">MixedRealityToolkit. SDK. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="da93e-545">Microsoft. MixedReality. Toolkit. SDK. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="da93e-546">**MixedRealityToolkit. exemplos**</span><span class="sxs-lookup"><span data-stu-id="da93e-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="da93e-547">RC2</span><span class="sxs-lookup"><span data-stu-id="da93e-547">RC2</span></span> | <span data-ttu-id="da93e-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="da93e-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="da93e-549">MixedRealityToolkit. examples. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="da93e-550">Microsoft. MixedReality. Toolkit. examples. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="da93e-551">MixedRealityToolkit. examples. demos. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="da93e-552">Microsoft. MixedReality. Toolkit. demos. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="da93e-553">MixedRealityToolkit. examples. demos. StandardShader. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="da93e-554">Microsoft. MixedReality. Toolkit. demos. StandardShader. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="da93e-555">MixedRealityToolkit. examples. demos. Utilities. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="da93e-556">Microsoft. MixedReality. Toolkit. demos. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="da93e-557">MixedRealityToolkit. examples. demos. Utilities. InspectorFields. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="da93e-558">Microsoft. MixedReality. Toolkit. demos. InspectorFields. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="da93e-559">MixedRealityToolkit. examples. demos. UX. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="da93e-560">Microsoft. MixedReality. Toolkit. demos. UX. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="da93e-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |