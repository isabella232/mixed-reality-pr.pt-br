---
title: Executando as cenas de exemplo
description: Saiba como adquirir e usar as cenas de exemplo do MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: kit de ferramentas de realidade misturada, MRTK, exemplos, HoloLens, HoloLens 2, sombreadores, dicas de ferramenta, interação com a mão, recorte, caixas delimitadoras, botões, menus de mão, slate, controle deslizante
ms.openlocfilehash: 8ba4df237189f0de3bd869bc05bdf7e3c5451490
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111911854"
---
# <a name="example-scenes"></a><span data-ttu-id="126aa-104">Cenas de exemplo</span><span class="sxs-lookup"><span data-stu-id="126aa-104">Example scenes</span></span>

<span data-ttu-id="126aa-105">O MRTK fornece vários tipos de cenas de exemplo que demonstram os recursos e blocos de construção do MRTK para a experiência espacial do usuário.</span><span class="sxs-lookup"><span data-stu-id="126aa-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="126aa-106">Experimentar e dissecar cenas de exemplo pode ser útil para entender os recursos e aplicá-los aos seus projetos.</span><span class="sxs-lookup"><span data-stu-id="126aa-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="126aa-107">Como adquirir cenas de exemplo</span><span class="sxs-lookup"><span data-stu-id="126aa-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="126aa-108">Usando a Ferramenta de Recursos de Realidade Misturada e o Gerenciador de Pacotes do Unity</span><span class="sxs-lookup"><span data-stu-id="126aa-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="126aa-109">Você pode baixar e importar o pacote **de Exemplos** do Kit de Ferramentas de Realidade Misturada por meio da [Ferramenta de Recursos de Realidade Misturada](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="126aa-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="126aa-110">No Unity, use o menu **Janela > Gerenciador de Pacotes > No Projeto > Personalizado** e selecione Exemplos do Kit de Ferramentas de Realidade **Misturada**.</span><span class="sxs-lookup"><span data-stu-id="126aa-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="126aa-111">Na lista no lado direito do painel, clique no botão **Importar no** Projeto ao lado dos nomes de cena de exemplo.</span><span class="sxs-lookup"><span data-stu-id="126aa-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="126aa-112">Por exemplo, você pode clicar **no botão Importar** para Projeto ao lado de Demonstrações – **HandTracking.**</span><span class="sxs-lookup"><span data-stu-id="126aa-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="126aa-113">Depois de importado, você poderá encontrá-los na pasta **Ativos > Exemplos.**</span><span class="sxs-lookup"><span data-stu-id="126aa-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="126aa-114">**A cena HandInteractionExamples** é um ótimo lugar para começar a experimentar as interações espaciais do MRTK e os blocos de construção da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="126aa-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="126aa-115">Baixando e importando pacotes diretamente do GitHub</span><span class="sxs-lookup"><span data-stu-id="126aa-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="126aa-116">Se você não usar a Ferramenta de Recursos de Realidade Misturada, poderá baixar e importar diretamente **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** da página de lançamento do [GitHub do MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="126aa-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="126aa-117">Use **Ativos > importar pacote >** menu Pacote Personalizado para importar .unitypackage baixado.</span><span class="sxs-lookup"><span data-stu-id="126aa-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="126aa-118">Depois que ele for importado, você poderá encontrar cenas de exemplo em **Ativos > MRTK > Exemplos > Demonstrações**.</span><span class="sxs-lookup"><span data-stu-id="126aa-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>