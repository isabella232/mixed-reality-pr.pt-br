---
title: ScreenshotUtility
description: Documentação sobre como usar a ferramenta de captura de tela no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 4fbd5457dd0af502ddedf30a10482690cd8e1a1d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682079"
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
