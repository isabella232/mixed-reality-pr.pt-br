---
title: Como usar o Gerenciador de Pacotes do Unity
description: Usando o MRTK no Unity Gerenciador de Pacotes
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, Pacotes MRTK,
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177318"
---
# <a name="using-the-unity-package-manager"></a>Como usar o Gerenciador de Pacotes do Unity

A partir da versão 2.5.0, usando a Ferramenta de Recursos de Realidade Misturada [,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)o Microsoft Mixed Reality Toolkit se integra ao UNITY Gerenciador de Pacotes (UPM) ao usar o Unity 2019.4 e mais recente.

## <a name="using-the-mixed-reality-feature-tool"></a>Como usar a Ferramenta de Recursos de Realidade Misturada

Conforme descrito em [Bem-vindo à Ferramenta de Recursos de Realidade](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) Misturada, você pode baixar a ferramenta usando este [link](https://aka.ms/MRFeatureTool).

> [!IMPORTANT]
> Se o manifesto do projeto tiver uma `Microsoft Mixed Reality` entrada na seção , é `scopedRegistries` recomendável que ele seja removido.
>
> Para remover um registro com escopo configurado, acesse `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![Removendo o registro com escopo](../features/images/packaging/RemoveScopedRegistry.png)

Os pacotes do MRTK aparecem sob `Mixed Reality Toolkit` o título ao descobrir recursos.

![Descobrir recursos](../features/images/packaging/DiscoverFeatures.png)

Ao selecionar recursos, não é necessário se preocupar com as dependências necessárias, a ferramenta baixará e as integrará automaticamente ao projeto.

![Dependências necessárias](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Gerenciando recursos de Realidade Misturada com o Gerenciador de Pacotes

Depois que um pacote Toolkit de Realidade Misturada tiver sido adicionado ao manifesto do pacote, ele poderá ser gerenciado usando a interface do usuário Gerenciador de Pacotes Unity.

![Pacote UPM do MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Se um pacote de Toolkit realidade misturada for removido usando o Gerenciador de Pacotes Unity, ele terá que ser adicionado de novo usando as etapas [descritas anteriormente.](#using-the-mixed-reality-feature-tool)

### <a name="using-mixed-reality-toolkit-examples"></a>Usando exemplos de Toolkit realidade misturada

Ao contrário de usar arquivos de pacote de ativos (.unitypackage) e `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` não importar automaticamente as cenas de exemplo e os ativos.

Para utilizar um ou mais exemplos, use as seguintes etapas:

1. No Editor do Unity, navegue até `Window` > `Package Manager`
1. Na lista de pacotes, selecione `Mixed Reality Toolkit Examples`
1. Localizar os exemplos desejados na `Samples` lista
1. Clique em `Import into Project`

![Importando exemplos](../features/images/packaging/MRTK_ExamplesUpm.png)

Quando um pacote de exemplo é atualizado, o Unity fornece a opção de atualizar exemplos importados.

> [!NOTE]
> Atualizar um exemplo importado substituirá as alterações feitas nesse exemplo e nos ativos associados.

## <a name="see-also"></a>Consulte Também

- [Pacotes de Toolkit realidade misturada](../packages/mrtk-packages.md)
