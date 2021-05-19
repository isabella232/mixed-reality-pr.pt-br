---
title: Ferramenta de atualização do sombreador
description: Documentação sobre como atualizar os sombreadores padrão do MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: ed9f9fa5e6337850f31ecce9d07bc82a8ea12060
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145135"
---
# <a name="updating-shaders"></a><span data-ttu-id="f7390-104">Atualizando sombreadores</span><span class="sxs-lookup"><span data-stu-id="f7390-104">Updating Shaders</span></span>

<span data-ttu-id="f7390-105">A partir da versão 2.6.0, os sombreadores MRTK estão sendo versionado por meio do MRTK. Arquivo shaders. Sentinel.</span><span class="sxs-lookup"><span data-stu-id="f7390-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="f7390-106">Ao atualizar para uma nova versão do MRTK, a seguinte mensagem pode ser exibida.</span><span class="sxs-lookup"><span data-stu-id="f7390-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![Aviso de atualização de sombreadores](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="f7390-108">Selecionar **Sim** instrui o MRTK a substituir o conteúdo dos **ativos**  >  **MRTK**  >  **sombreadores** pela versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="f7390-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="f7390-109">Selecionar **não** preservará os arquivos atuais.</span><span class="sxs-lookup"><span data-stu-id="f7390-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="f7390-110">**Ignorar** criará um arquivo ( `IgnoreUpdateCheck.sentinel` ) em **ativos**  >  **MRTK**  >  **sombreadores**, o que irá suprimir verificações de atualização de sombreador futuras.</span><span class="sxs-lookup"><span data-stu-id="f7390-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7390-111">Ao substituir os arquivos do sombreador, todas as modificações personalizadas serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="f7390-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="f7390-112">Certifique-se de fazer backup de todos os arquivos de sombreador modificados antes de atualizar.</span><span class="sxs-lookup"><span data-stu-id="f7390-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="f7390-113">Se o projeto tiver sido configurado para usar o pipeline de processamento universal (Urp), anteriormente conhecido como LWRP (pipeline de renderização leve), execute novamente o **Mixed Reality Toolkit** > **Utilities** >
>  **upgrade MRTK Standard Shader para Lightweight render pipeline**.</span><span class="sxs-lookup"><span data-stu-id="f7390-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="f7390-114">Em também é possível verificar se há atualizações de sombreador a qualquer momento usando utilitários de **Kit de ferramentas de realidade misturada**  >    >  **verificar atualizações de sombreador** na barra de menus do editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="f7390-114">At is also possible to check for shader updates at any time using **Mixed Reality Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![Verificar se há atualizações de sombreador](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="f7390-116">A **verificação de atualizações de sombreador** ignora o `IgnoreUpdateCheck.sentinel` arquivo e permite a atualização de sombreador sob demanda.</span><span class="sxs-lookup"><span data-stu-id="f7390-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="f7390-117">A verificação de atualizações de sombreador não é necessária ao importar os arquivos MRTK. unitypackage.</span><span class="sxs-lookup"><span data-stu-id="f7390-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
