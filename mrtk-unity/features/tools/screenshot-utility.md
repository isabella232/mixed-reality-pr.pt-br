---
title: Utilitário de captura de tela
description: Documentação sobre como usar a ferramenta de captura de tela no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 59bf0df2a32030281c8bf0a1a8574b4dd9bf4607
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143797"
---
# <a name="screenshot-utility"></a>Utilitário de captura de tela

Muitas vezes, fazer capturas de tela no Unity para documentação e imagens promocionais pode ser cansativo, e o resultado geralmente não é o que se espera. Nesse momento, a classe `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) entra em cena.

A classe ScreenshotUtility ajuda a fazer capturas de tela por meio de itens de menu e APIs públicas no editor do Unity. Capturas de tela podem ser capturadas em várias resoluções e com cores claras transparentes para uso em uma composição de imagens com facilidade. Não há suporte para a criação de capturas de tela de uma compilação autônoma nesta ferramenta.

## <a name="taking-screenshots"></a>Como tirar capturas de tela

Capturas de tela podem ser obtidas facilmente enquanto estiverem no editor. Para isso, selecione *Kit de Ferramentas de Realidade Misturada->Utilitários->Tirar Captura de Tela* e a opção desejada. Se estiver fazendo capturas enquanto não estiver jogando, verifique se a guia da janela do jogo está visível. Caso contrário, a captura de tela pode não ser salva.

Por padrão, todas as capturas de tela são salvas no seu [caminho de cache temporário](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html). O caminho para a captura de tela será exibido no console do Unity.

![Item de menu do utilitário de captura de tela](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Captura de tela de exemplo

A captura de tela abaixo foi capturada com a opção *"Resolução 4x (tela de fundo transparente)"* . Isso gera uma imagem de alta resolução com qualquer pixel normalmente representado pela cor clara salva como pixels transparentes. Essa técnica ajuda os desenvolvedores a demonstrar o aplicativo deles para a loja ou lojas de mídia, sobrepondo essa imagem sobre outras imagens.

![Exemplo de captura do utilitário de captura de tela](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
