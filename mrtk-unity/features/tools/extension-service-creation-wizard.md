---
title: Assistente para criação de serviço de extensão
description: Documentação sobre o assistente para fazer a transição de singletons para serviços MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 83797a9d6d465a150406b27162a5e84c157567f1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143547"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="ba101-104">Assistente para criação de serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="ba101-104">Extension service creation wizard</span></span>

<span data-ttu-id="ba101-105">Fazer a transição de singletons para serviços pode ser difícil.</span><span class="sxs-lookup"><span data-stu-id="ba101-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="ba101-106">Este assistente pode complementar nossa outra documentação e código de exemplo, permitindo que o desenvolvedores crie novos serviços com (aproximadamente) a mesma facilidade que criar um novo script de monocomportamento.</span><span class="sxs-lookup"><span data-stu-id="ba101-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="ba101-107">Para saber mais sobre como criar serviços do zero, consulte nosso [guia para criar serviços registrados](../../configuration/mixed-reality-configuration-guide.md) (em breve).</span><span class="sxs-lookup"><span data-stu-id="ba101-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="ba101-108">Iniciando o assistente</span><span class="sxs-lookup"><span data-stu-id="ba101-108">Launching the wizard</span></span>

<span data-ttu-id="ba101-109">Inicie o assistente no menu principal: **MixedRealityToolkit/Utilities/criar serviço de extensão** -o assistente guiará você pelo processo de geração do script de serviço, interface e classe de perfil.</span><span class="sxs-lookup"><span data-stu-id="ba101-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="ba101-110">Editando o script de serviço</span><span class="sxs-lookup"><span data-stu-id="ba101-110">Editing your service script</span></span>

<span data-ttu-id="ba101-111">Por padrão, os novos ativos de script serão gerados na `MixedRealityToolkit.Generated/Extensions` pasta.</span><span class="sxs-lookup"><span data-stu-id="ba101-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="ba101-112">Depois de concluir o assistente, navegue aqui e abra o novo script de serviço.</span><span class="sxs-lookup"><span data-stu-id="ba101-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="ba101-113">Os scripts de serviço gerados incluem alguns prompts semelhantes aos novos scripts de monocomportamento.</span><span class="sxs-lookup"><span data-stu-id="ba101-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="ba101-114">Eles permitirão que você saiba onde inicializar e atualizar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ba101-114">They will let you know where to initialize and update your service.</span></span>

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

<span data-ttu-id="ba101-115">Se você optar por registrar seu serviço no assistente, tudo o que precisará fazer é editar esse script e seu serviço será atualizado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ba101-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="ba101-116">Caso contrário, você pode ler sobre como [registrar seu novo serviço aqui](../../configuration/mixed-reality-configuration-guide.md).</span><span class="sxs-lookup"><span data-stu-id="ba101-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
