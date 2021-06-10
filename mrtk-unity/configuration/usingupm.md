---
title: Como usar o Gerenciador de Pacotes do Unity
description: Usando o MRTK no Gerenciador de pacotes do Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, pacotes MRTK,
ms.openlocfilehash: e3e7a2d06cd38d7a9e8daf579f1a312904a86280
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345069"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>Kit de ferramentas de realidade misturada e Gerenciador de pacotes do Unity

A partir da versão 2.5.0, usando a [ferramenta de funcionalidade Mixed Reality](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), o Microsoft Mixed Reality Toolkit integra-se com o UPM (Gerenciador de pacotes do Unity) ao usar o Unity 2019,4 e mais recente.

## <a name="using-the-mixed-reality-feature-tool"></a>Como usar a Ferramenta de Recursos de Realidade Misturada

Conforme descrito em [Bem-vindo à ferramenta de funcionalidade de realidade misturada](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) , você pode baixar a ferramenta usando [esse link](https://aka.ms/MRFeatureTool).

> [!IMPORTANT]
> Se o manifesto do projeto tiver uma `Microsoft Mixed Reality` entrada na `scopedRegistries` seção, é recomendável que ele seja removido.
>
> Para remover um registro com escopo configurado, acesse para `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![Removendo registro com escopo](../features/images/packaging/RemoveScopedRegistry.png)

Os pacotes MRTK aparecem sob o `Mixed Reality Toolkit` título ao descobrir recursos.

![Descobrir recursos](../features/images/packaging/DiscoverFeatures.png)

Ao selecionar recursos, não há necessidade de se preocupar com as dependências necessárias, a ferramenta irá baixá-las e integrá-las automaticamente no projeto.

![Dependências necessárias](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Gerenciando recursos mistos de realidade com o Gerenciador de pacotes do Unity

Depois que um pacote do kit de ferramentas da realidade misturada tiver sido adicionado ao manifesto do pacote, ele poderá ser gerenciado usando a interface do usuário do Gerenciador de pacotes do Unity.

![Pacote UPM do MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Se um pacote do kit de ferramentas da realidade misturada for removido usando o Gerenciador de pacotes do Unity, ele precisará ser adicionado novamente usando as [etapas descritas anteriormente](#using-the-mixed-reality-feature-tool).

### <a name="using-mixed-reality-toolkit-examples"></a>Usando exemplos do kit de ferramentas de realidade misturada

Ao contrário do uso de arquivos de pacote de ativos (. unitypackage) `com.microsoft.mixedreality.toolkit.examples` e `com.microsoft.mixedreality.toolkit.handphysicsservice` não importam automaticamente as cenas de exemplo e os ativos.

Para utilizar um ou mais dos exemplos, use as seguintes etapas:

1. No editor do Unity, navegue até `Window` > `Package Manager`
1. Na lista de pacotes, selecione `Mixed Reality Toolkit Examples`
1. Localize os exemplos desejados na `Samples` lista
1. Clique em `Import into Project`

![Importando amostras](../features/images/packaging/MRTK_ExamplesUpm.png)

Quando um pacote de exemplo é atualizado, o Unity fornece a opção de atualizar amostras importadas.

> [!NOTE]
> A atualização de um exemplo importado substituirá as alterações feitas nesse exemplo e nos ativos associados.

## <a name="see-also"></a>Consulte Também

- [Pacotes do kit de ferramentas de realidade misturada](../packages/mrtk-packages.md)