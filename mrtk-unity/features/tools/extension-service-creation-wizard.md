---
title: Assistente para criação de serviço de extensão
description: Documentação sobre o assistente para fazer a transição de singletons para serviços MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 6b4efa39a99755f3c031757c7298465886d0c39512c93750f4653200edce9e17
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214292"
---
# <a name="extension-service-creation-wizard"></a>Assistente para criação de serviço de extensão

Fazer a transição de singletons para serviços pode ser difícil. Este assistente pode complementar nossa outra documentação e código de exemplo, permitindo que o desenvolvedores crie novos serviços com (aproximadamente) a mesma facilidade que criar um novo script de monocomportamento. Para saber mais sobre como criar serviços do zero, consulte nosso [guia para criar serviços registrados](../../configuration/mixed-reality-configuration-guide.md) (em breve).

## <a name="launching-the-wizard"></a>Iniciando o assistente

Inicie o assistente no menu principal: **MixedRealityToolkit/Utilities/criar serviço de extensão** -o assistente guiará você pelo processo de geração do script de serviço, interface e classe de perfil.

## <a name="editing-your-service-script"></a>Editando o script de serviço

Por padrão, os novos ativos de script serão gerados na `MixedRealityToolkit.Generated/Extensions` pasta. Depois de concluir o assistente, navegue aqui e abra o novo script de serviço.

Os scripts de serviço gerados incluem alguns prompts semelhantes aos novos scripts de monocomportamento. Eles permitirão que você saiba onde inicializar e atualizar seu serviço.

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

Se você optar por registrar seu serviço no assistente, tudo o que precisará fazer é editar esse script e seu serviço será atualizado automaticamente. Caso contrário, você pode ler sobre como [registrar seu novo serviço aqui](../../configuration/mixed-reality-configuration-guide.md).
