---
title: Utilitário de permuta de ativos
description: Documentação sobre como usar o utilitário de troca de ativos no MRTK para Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176165"
---
# <a name="asset-swap-utility"></a>Utilitário de permuta de ativos

Encontrar e substituir é onipresente ao trabalhar em ferramentas de criação de texto e conteúdo. Quando você precisa trocar muitos ativos em uma cena do Unity, é aí que o [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) e o editor podem ajudar. O utilitário está incluído no `Microsoft.MixedReality.Toolkit.Unity.Tools` pacote.

O salva todas as ações de encontrar e substituir como um ScriptableObject para que seja trival para alternar entre si ou salvar "temas" de permuta para `AssetSwapUtility` uso futuro.

## <a name="swapping-assets"></a>Troca de ativos

A troca de ativos é fácil depois que você cria um `AssetSwapCollection` . Vamos demonstrar o uso trocando dois cubos vermelhos por duas esferas azuis em uma cena. Primeiro, adicione dois cubos vermelhos à cena que usam o cubo padrão do Unity e o `MRTK_Standard_Red` material.

Para criar um `AssetSwapCollection` , navegue até Realidade **Misturada Toolkit > Utilitários > Criar Coleção de Troca de Ativos**. Com o `AssetSwapCollection` selecionado, preencha as propriedades conforme visto na imagem abaixo:

![Coleção de permuta de ativos no editor do Unity](images/asset-swap-img-01.png)

Em seguida, selecione "Blue Spheres" na lista suspenso "Tema Selecionado" e clique em "Aplicar". Todos os cubos vermelhos em sua cena devem ser substituídos por esferas azuis.

![Coleção de permuta de ativos no editor do Unity com o tema selecionado realçada](images/asset-swap-img-02.png)

Neste exemplo, realizamos uma substituição de cena completa, mas você pode substituir partes da cena alterando o "Modo de Seleção". Você também pode trocar de volta para cubos vermelhos selecionando "Cubos Vermelhos" na lista suspenso "Tema Selecionado" e clicando em "Aplicar" novamente.

> [!NOTE]
> É possível trocar qualquer tipo de ativo, como arquivos de áudio, fontes, pré-fabs, etc. O `AssetSwapUtility` executará algumas verificações de sanidade para garantir que você está trocando para tipos semelhantes.
