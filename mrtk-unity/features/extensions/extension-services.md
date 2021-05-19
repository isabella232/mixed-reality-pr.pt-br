---
title: Serviços de Extensão
description: documentação para funcionalidade estendida no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: a39616a091a3f6800c429dc797ec2f3130e96f40
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144545"
---
# <a name="extension-services"></a><span data-ttu-id="0bfaf-104">Serviços de extensão</span><span class="sxs-lookup"><span data-stu-id="0bfaf-104">Extension services</span></span>

<span data-ttu-id="0bfaf-105">Os serviços de extensão são componentes que estendem a funcionalidade do kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="0bfaf-106">Esses serviços podem ser fornecidos pelo MRTK ou por outras partes.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="0bfaf-107">Criando um serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="0bfaf-107">Creating an extension service</span></span>

<span data-ttu-id="0bfaf-108">A maneira mais eficiente de criar um serviço de extensão é usar o [Assistente de criação de serviço de extensão](../tools/extension-service-creation-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="0bfaf-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="0bfaf-109">Para iniciar o assistente para criação de serviço de extensão, selecione o **Kit de ferramentas do reality Toolkit > utilitários > criar serviço de extensão**.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="0bfaf-111">O assistente automatiza a criação dos componentes de serviço e garante a herança de interface adequada.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Componentes criados pelo Assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="0bfaf-113">No MRTK versão 2.0.0, há um problema no assistente de serviço de extensão em que o Inspetor de serviço e o perfil de serviço devem ser gerados.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="0bfaf-114">Consulte o problema [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="0bfaf-115">Quando o assistente for concluído, a funcionalidade do serviço poderá ser implementada.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="0bfaf-116">Registrando um serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="0bfaf-116">Registering an extension service</span></span>

<span data-ttu-id="0bfaf-117">Para ser acessível por um aplicativo, o novo serviço de extensão precisa ser registrado com o kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="0bfaf-118">O assistente para criação de serviço de extensão pode ser usado para registrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-118">The extension service creation wizard can be used to register the service.</span></span>

![Registro do assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="0bfaf-120">O serviço também pode ser registrado manualmente usando o Inspetor de configuração do kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Registro de serviço de extensão manual](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="0bfaf-122">Se o serviço de extensão usar um perfil, verifique se ele está especificado no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Serviço de extensão configurado](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="0bfaf-124">O nome do componente e a prioridade também podem ser ajustados.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="0bfaf-125">Acessando um serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="0bfaf-125">Accessing an extension service</span></span>

<span data-ttu-id="0bfaf-126">Os serviços de extensão são acessados, no código, usando o, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) conforme mostrado no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="0bfaf-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="0bfaf-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="0bfaf-127">See also</span></span>

- [<span data-ttu-id="0bfaf-128">Sistemas, serviços de extensão e provedores de dados</span><span class="sxs-lookup"><span data-stu-id="0bfaf-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="0bfaf-129">Assistente para criação de serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="0bfaf-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="0bfaf-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="0bfaf-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="0bfaf-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="0bfaf-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
