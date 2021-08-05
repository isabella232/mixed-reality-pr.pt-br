---
title: Serviços de extensão
description: documentação para funcionalidade estendida no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0f9f30bb7d2d44cef828b79bc916d933a6355dbb1068b09e73317d1c977ef45a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186976"
---
# <a name="extension-services"></a>Serviços de extensão

Os serviços de extensão são componentes que estendem a funcionalidade da realidade misturada Toolkit. Esses serviços podem ser fornecidos pelo MRTK ou por outras partes.

## <a name="creating-an-extension-service"></a>Criando um serviço de extensão

A maneira mais eficiente de criar um serviço de extensão é usar o [Assistente de criação de serviço de extensão](../tools/extension-service-creation-wizard.md).
para iniciar o assistente para criação de serviço de extensão, selecione **realidade misturada Toolkit > utilitários > criar serviço de extensão**.

![Assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceCreationWizard.png)

O assistente automatiza a criação dos componentes de serviço e garante a herança de interface adequada.

![Componentes criados pelo Assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> No MRTK versão 2.0.0, há um problema no assistente de serviço de extensão em que o Inspetor de serviço e o perfil de serviço devem ser gerados. Consulte o problema [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) para obter mais informações.

Quando o assistente for concluído, a funcionalidade do serviço poderá ser implementada.

## <a name="registering-an-extension-service"></a>Registrando um serviço de extensão

Para ser acessível por um aplicativo, o novo serviço de extensão precisa ser registrado com a realidade misturada Toolkit.

O assistente para criação de serviço de extensão pode ser usado para registrar o serviço.

![Registro do assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceWizardRegister.png)

o serviço também pode ser registrado manualmente usando a realidade misturada Toolkit inspetor de configuração.

![Registro de serviço de extensão manual](../images/profiles/RegisterExtensionService.png)

Se o serviço de extensão usar um perfil, verifique se ele está especificado no Inspetor.

![Serviço de extensão configurado](../images/profiles/ConfiguredExtensionService.png)

O nome do componente e a prioridade também podem ser ajustados.

## <a name="accessing-an-extension-service"></a>Acessando um serviço de extensão

Os serviços de extensão são acessados, no código, usando o, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) conforme mostrado no exemplo abaixo.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>Consulte também

- [Sistemas, serviços de extensão e provedores de dados](../../architecture/systems-extensions-providers.md)
- [Assistente para criação de serviço de extensão](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
