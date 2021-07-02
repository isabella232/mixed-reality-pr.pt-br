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
# <a name="extension-services"></a>Serviços de extensão

Os serviços de extensão são componentes que estendem a funcionalidade do Toolkit. Esses serviços podem ser fornecidos pelo MRTK ou por outras partes.

## <a name="creating-an-extension-service"></a>Criando um serviço de extensão

A maneira mais eficiente de criar um serviço de extensão é usar o assistente [de criação do serviço de extensão](../tools/extension-service-creation-wizard.md).
Para iniciar o assistente de criação do serviço de extensão, selecione **Realidade Misturada Toolkit > Utilitários > Criar Serviço de Extensão**.

![Assistente de criação do serviço de extensão](../images/extension-wizard/ExtensionServiceCreationWizard.png)

O assistente automatiza a criação dos componentes de serviço e garante a herança de interface adequada.

![Componentes criados pelo assistente de criação do serviço de extensão](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> No MRTK versão 2.0.0, há um problema no assistente de serviço de extensão em que o inspetor de serviço e o perfil de serviço precisam ser gerados. Consulte o problema [5654 para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) obter mais informações.

Quando o assistente for concluído, a funcionalidade do serviço poderá ser implementada.

## <a name="registering-an-extension-service"></a>Registrando um serviço de extensão

Para ser acessível por um aplicativo, o novo serviço de extensão precisa ser registrado com o Toolkit.

O assistente de criação do serviço de extensão pode ser usado para registrar o serviço.

![Registro do assistente de criação do serviço de extensão](../images/extension-wizard/ExtensionServiceWizardRegister.png)

O serviço também pode ser registrado manualmente usando o inspetor de configuração Toolkit Realidade Misturada.

![Registro manual do serviço de extensão](../images/profiles/RegisterExtensionService.png)

Se o serviço de extensão usar um perfil, verifique se ele está especificado no inspetor.

![Serviço de extensão configurado](../images/profiles/ConfiguredExtensionService.png)

O nome e a prioridade do componente também podem ser ajustados.

## <a name="accessing-an-extension-service"></a>Acessando um serviço de extensão

Os serviços de extensão são acessados, no código, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) usando o conforme mostrado no exemplo abaixo.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>Confira também

- [Sistemas, serviços de extensão e provedores de dados](../../architecture/systems-extensions-providers.md)
- [Assistente de criação do serviço de extensão](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
