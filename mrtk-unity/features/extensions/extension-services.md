---
title: Serviços de extensão
description: documentação para funcionalidade estendida no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f8f7b8dbac0355c226e4bbfae39246e5c1c58f69
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176270"
---
# <a name="extension-services"></a><span data-ttu-id="97d83-104">Serviços de extensão</span><span class="sxs-lookup"><span data-stu-id="97d83-104">Extension services</span></span>

<span data-ttu-id="97d83-105">Os serviços de extensão são componentes que estendem a funcionalidade do Toolkit.</span><span class="sxs-lookup"><span data-stu-id="97d83-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="97d83-106">Esses serviços podem ser fornecidos pelo MRTK ou por outras partes.</span><span class="sxs-lookup"><span data-stu-id="97d83-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="97d83-107">Criando um serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="97d83-107">Creating an extension service</span></span>

<span data-ttu-id="97d83-108">A maneira mais eficiente de criar um serviço de extensão é usar o assistente [de criação do serviço de extensão](../tools/extension-service-creation-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="97d83-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="97d83-109">Para iniciar o assistente de criação do serviço de extensão, selecione **Realidade Misturada Toolkit > Utilitários > Criar Serviço de Extensão**.</span><span class="sxs-lookup"><span data-stu-id="97d83-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Assistente de criação do serviço de extensão](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="97d83-111">O assistente automatiza a criação dos componentes de serviço e garante a herança de interface adequada.</span><span class="sxs-lookup"><span data-stu-id="97d83-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Componentes criados pelo assistente de criação do serviço de extensão](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="97d83-113">No MRTK versão 2.0.0, há um problema no assistente de serviço de extensão em que o inspetor de serviço e o perfil de serviço precisam ser gerados.</span><span class="sxs-lookup"><span data-stu-id="97d83-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="97d83-114">Consulte o problema [5654 para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="97d83-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="97d83-115">Quando o assistente for concluído, a funcionalidade do serviço poderá ser implementada.</span><span class="sxs-lookup"><span data-stu-id="97d83-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="97d83-116">Registrando um serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="97d83-116">Registering an extension service</span></span>

<span data-ttu-id="97d83-117">Para ser acessível por um aplicativo, o novo serviço de extensão precisa ser registrado com o Toolkit.</span><span class="sxs-lookup"><span data-stu-id="97d83-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="97d83-118">O assistente de criação do serviço de extensão pode ser usado para registrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="97d83-118">The extension service creation wizard can be used to register the service.</span></span>

![Registro do assistente de criação do serviço de extensão](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="97d83-120">O serviço também pode ser registrado manualmente usando o inspetor de configuração Toolkit Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="97d83-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Registro manual do serviço de extensão](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="97d83-122">Se o serviço de extensão usar um perfil, verifique se ele está especificado no inspetor.</span><span class="sxs-lookup"><span data-stu-id="97d83-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Serviço de extensão configurado](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="97d83-124">O nome e a prioridade do componente também podem ser ajustados.</span><span class="sxs-lookup"><span data-stu-id="97d83-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="97d83-125">Acessando um serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="97d83-125">Accessing an extension service</span></span>

<span data-ttu-id="97d83-126">Os serviços de extensão são acessados, no código, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) usando o conforme mostrado no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="97d83-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="97d83-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="97d83-127">See also</span></span>

- [<span data-ttu-id="97d83-128">Sistemas, serviços de extensão e provedores de dados</span><span class="sxs-lookup"><span data-stu-id="97d83-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="97d83-129">Assistente de criação do serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="97d83-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="97d83-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="97d83-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="97d83-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="97d83-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
