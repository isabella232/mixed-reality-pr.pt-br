---
title: ScreenshotUtility
description: Documentação sobre como usar a ferramenta de captura de tela no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: a1f5e6503244852d79abaf143f8e922ceb1b489c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101761975"
---
# <a name="screenshot-utility"></a><span data-ttu-id="2a16f-104">Utilitário de captura de tela</span><span class="sxs-lookup"><span data-stu-id="2a16f-104">Screenshot utility</span></span>

<span data-ttu-id="2a16f-105">Muitas vezes, fazer capturas de tela no Unity para documentação e imagens promocionais pode ser cansativo, e o resultado geralmente não é o que se espera.</span><span class="sxs-lookup"><span data-stu-id="2a16f-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="2a16f-106">Nesse momento, a classe `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) entra em cena.</span><span class="sxs-lookup"><span data-stu-id="2a16f-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="2a16f-107">A classe ScreenshotUtility ajuda a fazer capturas de tela por meio de itens de menu e APIs públicas no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="2a16f-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="2a16f-108">Capturas de tela podem ser capturadas em várias resoluções e com cores claras transparentes para uso em uma composição de imagens com facilidade.</span><span class="sxs-lookup"><span data-stu-id="2a16f-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="2a16f-109">Não há suporte para a criação de capturas de tela de uma compilação autônoma nesta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="2a16f-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="2a16f-110">Como tirar capturas de tela</span><span class="sxs-lookup"><span data-stu-id="2a16f-110">Taking screenshots</span></span>

<span data-ttu-id="2a16f-111">Capturas de tela podem ser obtidas facilmente enquanto estiverem no editor. Para isso, selecione *Kit de Ferramentas de Realidade Misturada->Utilitários->Tirar Captura de Tela* e a opção desejada.</span><span class="sxs-lookup"><span data-stu-id="2a16f-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="2a16f-112">Se estiver fazendo capturas enquanto não estiver jogando, verifique se a guia da janela do jogo está visível. Caso contrário, a captura de tela pode não ser salva.</span><span class="sxs-lookup"><span data-stu-id="2a16f-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="2a16f-113">Por padrão, todas as capturas de tela são salvas no seu [caminho de cache temporário](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html). O caminho para a captura de tela será exibido no console do Unity.</span><span class="sxs-lookup"><span data-stu-id="2a16f-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![Item de menu do utilitário de captura de tela](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="2a16f-115">Captura de tela de exemplo</span><span class="sxs-lookup"><span data-stu-id="2a16f-115">Example screenshot capture</span></span>

<span data-ttu-id="2a16f-116">A captura de tela abaixo foi capturada com a opção *"Resolução 4x (tela de fundo transparente)"* .</span><span class="sxs-lookup"><span data-stu-id="2a16f-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="2a16f-117">Isso gera uma imagem de alta resolução com qualquer pixel normalmente representado pela cor clara salva como pixels transparentes.</span><span class="sxs-lookup"><span data-stu-id="2a16f-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="2a16f-118">Essa técnica ajuda os desenvolvedores a demonstrar o aplicativo deles para a loja ou lojas de mídia, sobrepondo essa imagem sobre outras imagens.</span><span class="sxs-lookup"><span data-stu-id="2a16f-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![Exemplo de captura do utilitário de captura de tela](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
