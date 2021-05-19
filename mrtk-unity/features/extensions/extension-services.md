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
# <a name="extension-services"></a>Serviços de extensão

Os serviços de extensão são componentes que estendem a funcionalidade do kit de ferramentas de realidade misturada. Esses serviços podem ser fornecidos pelo MRTK ou por outras partes.

## <a name="creating-an-extension-service"></a>Criando um serviço de extensão

A maneira mais eficiente de criar um serviço de extensão é usar o [Assistente de criação de serviço de extensão](../tools/extension-service-creation-wizard.md).
Para iniciar o assistente para criação de serviço de extensão, selecione o **Kit de ferramentas do reality Toolkit > utilitários > criar serviço de extensão**.

![Assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceCreationWizard.png)

O assistente automatiza a criação dos componentes de serviço e garante a herança de interface adequada.

![Componentes criados pelo Assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> No MRTK versão 2.0.0, há um problema no assistente de serviço de extensão em que o Inspetor de serviço e o perfil de serviço devem ser gerados. Consulte o problema [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) para obter mais informações.

Quando o assistente for concluído, a funcionalidade do serviço poderá ser implementada.

## <a name="registering-an-extension-service"></a>Registrando um serviço de extensão

Para ser acessível por um aplicativo, o novo serviço de extensão precisa ser registrado com o kit de ferramentas de realidade misturada.

O assistente para criação de serviço de extensão pode ser usado para registrar o serviço.

![Registro do assistente para criação de serviço de extensão](../images/extension-wizard/ExtensionServiceWizardRegister.png)

O serviço também pode ser registrado manualmente usando o Inspetor de configuração do kit de ferramentas de realidade misturada.

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

## <a name="see-also"></a>Confira também

- [Sistemas, serviços de extensão e provedores de dados](../../architecture/systems-extensions-providers.md)
- [Assistente para criação de serviço de extensão](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
