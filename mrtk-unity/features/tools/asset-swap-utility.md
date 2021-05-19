---
title: Utilitário de permuta de ativos
description: Documentação sobre o uso do utilitário de permuta de ativos no MRTK para Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK
ms.openlocfilehash: c277cadffb356b93ffc359233b0b8307f43e8d57
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144131"
---
# <a name="asset-swap-utility"></a>Utilitário de permuta de ativos

Localizar e substituir é onipresente ao trabalhar em ferramentas de criação de conteúdo e texto. Quando você precisa trocar muitos ativos em uma cena de Unity, é aí que o [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) e o editor podem dar uma mão. O utilitário está incluído no `Microsoft.MixedReality.Toolkit.Unity.Tools` pacote.

O `AssetSwapUtility` salva todas as ações localizar e substituir como um ScriptableObject para que ela seja trivalda para alternar ou salvar "temas" de troca para uso futuro.

## <a name="swapping-assets"></a>Troca de ativos

A troca de ativos é fácil depois de você ter criado um `AssetSwapCollection` . Vamos demonstrar o uso alternando dois cubos vermelhos com dois antiazuls em uma cena. Primeiro, adicione dois cubos vermelhos à sua cena que usam o cubo do Unity padrão e o `MRTK_Standard_Red` material.

Para criar um `AssetSwapCollection` , navegue até **Mixed Reality Toolkit > Utilities > criar coleção de permuta de ativos**. Com o `AssetSwapCollection` preenchimento selecionado, as propriedades são mostradas na imagem abaixo:

![Coleção de permuta de ativos no editor do Unity](images/asset-swap-img-01.png)

Em seguida, selecione "azul" aqui na lista suspensa "tema selecionado" e pressione "aplicar". Todos os cubos vermelhos em sua cena devem ser substituídos por meio azul aqui.

![Coleção de permuta de ativos no editor do Unity com o tema selecionado realçado](images/asset-swap-img-02.png)

Neste exemplo, realizamos uma substituição de cena completa, mas você pode substituir partes da sua cena alterando o "modo de seleção". Você também pode alternar de volta para cubos vermelhos selecionando "cubos vermelhos" na lista suspensa "tema selecionado" e pressionando "aplicar" novamente.

> [!NOTE]
> É possível trocar qualquer tipo de ativo, como arquivos de áudio, fontes, pré-fabs, etc. O `AssetSwapUtility` executará algumas verificações de sanidade para garantir que você está trocando para tipos semelhantes.