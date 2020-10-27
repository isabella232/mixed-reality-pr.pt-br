---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638607"
---
# <a name="all-platforms"></a>[<span data-ttu-id="ab593-101">Todas as plataformas</span><span class="sxs-lookup"><span data-stu-id="ab593-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="ab593-102">Habilitando plug-in do controlador HP Motion</span><span class="sxs-lookup"><span data-stu-id="ab593-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="ab593-103">O perfil de interação e os mapeamentos do controlador estão no plug-in do controlador HP Motion, que deve ser habilitado para expor os mapeamentos do controlador para o sistema de entrada do inreal.</span><span class="sxs-lookup"><span data-stu-id="ab593-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![Habilitando o plug-in OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="ab593-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="ab593-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="ab593-106">Configurando inicialização e HMDPluginPriority</span><span class="sxs-lookup"><span data-stu-id="ab593-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="ab593-107">A entrada em inreal usando SteamVR tem algumas diferenças.</span><span class="sxs-lookup"><span data-stu-id="ab593-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="ab593-108">Ao configurar o projeto, primeiro verifique se ele está usando o novo sistema de entrada do SteamVR adicionando **VR. SteamVR. EnableVRInput = 1** para a seção de **inicialização** em **Engine/config/ConsoleVariables.ini** .</span><span class="sxs-lookup"><span data-stu-id="ab593-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="ab593-109">Esse ini é encontrado no diretório de instalação do mecanismo, não no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="ab593-109">This ini is found in the engine install directory, not the project directory.</span></span>

![Atualizando a configuração de inicialização](../images/reverb-g2-img-07.png)

<span data-ttu-id="ab593-111">O plug-in do controlador HP Motion habilitará o OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ab593-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="ab593-112">Se você não estiver usando o OpenXR, será necessário editar o HMDPluginPriority de SteamVR no BaseEngine.ini no mesmo diretório que ConsoleVariables.ini.</span><span class="sxs-lookup"><span data-stu-id="ab593-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="ab593-113">Altere o valor de SteamVR para que seja maior que o valor de OpenXRHMD.</span><span class="sxs-lookup"><span data-stu-id="ab593-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![Atualizando a configuração do HMDPluginPriority](../images/reverb-g2-img-08.png)


