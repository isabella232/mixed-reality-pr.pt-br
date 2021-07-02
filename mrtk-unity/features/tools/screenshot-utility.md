---
title: Utilitário de captura de tela
description: Documentação sobre como usar a ferramenta de captura de tela no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 936126214f9e6d93ccbb871b9c80a2c93acf5a86
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176427"
---
# <a name="screenshot-utility"></a>Utilitário de captura de tela

Muitas vezes, fazer capturas de tela no Unity para documentação e imagens promocionais pode ser cansativo, e o resultado geralmente não é o que se espera. Nesse momento, a classe `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) entra em cena.

A classe ScreenshotUtility ajuda a fazer capturas de tela por meio de itens de menu e APIs públicas no editor do Unity. Capturas de tela podem ser capturadas em várias resoluções e com cores claras transparentes para uso em uma composição de imagens com facilidade. Não há suporte para a criação de capturas de tela de uma compilação autônoma nesta ferramenta.

## <a name="taking-screenshots"></a>Como tirar capturas de tela

capturas de tela podem ser facilmente capturadas no editor, selecionando **realidade misturada**  >  **Toolkit** os  >  **utilitários**  >  **usam captura de tela** e selecionando a opção desejada. Se estiver fazendo capturas enquanto não estiver jogando, verifique se a guia da janela do jogo está visível. Caso contrário, a captura de tela pode não ser salva.

Por padrão, todas as capturas de tela são salvas no seu [caminho de cache temporário](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html). O caminho para a captura de tela será exibido no console do Unity.

![Item de menu do utilitário de captura de tela](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Captura de tela de exemplo

A captura de tela abaixo foi capturada com a opção *"Resolução 4x (tela de fundo transparente)"* . Isso gera uma imagem de alta resolução com qualquer pixel normalmente representado pela cor clara salva como pixels transparentes. Essa técnica ajuda os desenvolvedores a demonstrar o aplicativo deles para a loja ou lojas de mídia, sobrepondo essa imagem sobre outras imagens.

![Exemplo de captura do utilitário de captura de tela](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
