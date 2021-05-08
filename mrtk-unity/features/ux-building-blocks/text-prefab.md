---
title: TextPrefab
description: Visão geral do TextPrefab no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, TMP,
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489286"
---
# <a name="text-prefab"></a><span data-ttu-id="7fc21-104">Pré-fab de texto</span><span class="sxs-lookup"><span data-stu-id="7fc21-104">Text prefab</span></span>

<span data-ttu-id="7fc21-105">Esses pré-requisitos são otimizados para a qualidade de renderização Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="7fc21-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="7fc21-106">Para obter mais informações, leia a diretriz [Texto no Unity](/windows/mixed-reality/text-in-unity) no Microsoft Centro de Desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="7fc21-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="7fc21-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7fc21-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="7fc21-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="7fc21-108">3DTextPrefab</span></span>

<span data-ttu-id="7fc21-109">Pré-fab de Malha de Texto 3D (Ativos/MRTK/SDK/StandardAssets/Prefabs/Text) com fator de dimensionamento otimizado a uma distância de 2 metros.</span><span class="sxs-lookup"><span data-stu-id="7fc21-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="7fc21-110">(Leia as instruções abaixo)</span><span class="sxs-lookup"><span data-stu-id="7fc21-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="7fc21-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="7fc21-111">UITextPrefab</span></span>

<span data-ttu-id="7fc21-112">Pré-fab de Malha de Texto da Interface do Usuário (Ativos/MRTK/SDK/StandardAssets/Prefabs/Text) com fator de dimensionamento otimizado a uma distância de 2 metros.</span><span class="sxs-lookup"><span data-stu-id="7fc21-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="7fc21-113">(Leia as instruções abaixo)</span><span class="sxs-lookup"><span data-stu-id="7fc21-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="7fc21-114">Fontes</span><span class="sxs-lookup"><span data-stu-id="7fc21-114">Fonts</span></span>

<span data-ttu-id="7fc21-115">Fontes de código aberto (Ativos/MRTK/Core/StandardAssets/Fontes) incluídas no Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="7fc21-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7fc21-116">O Pré-fab de Texto usa a fonte de código aberto 'Selawik'.</span><span class="sxs-lookup"><span data-stu-id="7fc21-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="7fc21-117">Para usar o Pré-fab de Texto com uma fonte diferente, importe o arquivo de fonte e siga as instruções abaixo.</span><span class="sxs-lookup"><span data-stu-id="7fc21-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="7fc21-118">O exemplo abaixo mostra como usar a fonte "Segoe UI" com o Pré-fab de Texto.</span><span class="sxs-lookup"><span data-stu-id="7fc21-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![Importando Segoe UI de fonte](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="7fc21-120">Atribua textura de fonte ao material 3DTextSânciaUI.mat.</span><span class="sxs-lookup"><span data-stu-id="7fc21-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![Atribuindo textura de fonte](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="7fc21-122">No material 3DTextSegoeUI. passe-partout, selecione o sombreador personalizado/3DTextShader. sombreador.</span><span class="sxs-lookup"><span data-stu-id="7fc21-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![Atribuindo sombreador](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="7fc21-124">Atribua Segoe UI fonte e material 3DTextSegoeUI aos componentes de texto no pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="7fc21-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![Atribuindo material e arquivo de fonte](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="7fc21-126">Trabalhando com fontes no Unity</span><span class="sxs-lookup"><span data-stu-id="7fc21-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="7fc21-127">Ao adicionar uma nova textmesh 3D a uma cena no Unity, há dois problemas que são visualmente aparentes.</span><span class="sxs-lookup"><span data-stu-id="7fc21-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="7fc21-128">Uma delas, a fonte aparece muito grande e duas, a fonte aparece muito borrada.</span><span class="sxs-lookup"><span data-stu-id="7fc21-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="7fc21-129">Também é interessante observar que o valor do tamanho da fonte padrão é definido como zero no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="7fc21-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="7fc21-130">Substituir esse valor zero por 13 não mostrará nenhuma diferença no tamanho, porque 13 é, na verdade, o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="7fc21-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="7fc21-131">O Unity pressupõe que todos os novos elementos adicionados a uma cena tenham uma unidade Unity de tamanho ou uma escala de transformação de 100%, o que traduz em cerca de 1 metro no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7fc21-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="7fc21-132">No caso de fontes, a caixa delimitadora de uma telemalha 3D entra, por padrão, em cerca de 1 metro de altura.</span><span class="sxs-lookup"><span data-stu-id="7fc21-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="7fc21-133">Escala de fonte e tamanhos de fonte</span><span class="sxs-lookup"><span data-stu-id="7fc21-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="7fc21-134">A maioria dos designers visuais usa pontos para definir tamanhos de fonte no mundo real, bem como seus programas de design.</span><span class="sxs-lookup"><span data-stu-id="7fc21-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="7fc21-135">Há cerca de 2835 pontos (2, 834.645666399962) em 1 metro.</span><span class="sxs-lookup"><span data-stu-id="7fc21-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="7fc21-136">Com base na conversão do sistema de ponto para 1 medidor e tamanho de fonte de textmesh padrão de Unity de 13, a matemática simples de 13 dividido por 2835 é igual a 0, 46 (0.004586111116 a ser exato) fornece uma boa escala padrão para começar, embora alguns possam desejar arredondar para 0, 5.</span><span class="sxs-lookup"><span data-stu-id="7fc21-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="7fc21-137">De qualquer forma, dimensionar o objeto de texto ou o contêiner para esses valores não só permitirá a conversão 1:1 de tamanhos de fonte de um programa de design, mas também fornecerá um padrão para manter a consistência em todo o aplicativo ou jogo.</span><span class="sxs-lookup"><span data-stu-id="7fc21-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="7fc21-138">Texto da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7fc21-138">UI Text</span></span>

<span data-ttu-id="7fc21-139">Ao adicionar um elemento de texto baseado na interface do usuário ou tela a uma cena, o tamanho da disparidade ainda é maior.</span><span class="sxs-lookup"><span data-stu-id="7fc21-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="7fc21-140">As diferenças nos dois tamanhos são cerca de 1000%, o que levaria o fator de escala para componentes de texto baseados na interface do usuário a 0, 46 (0.0004586111116 para ser exato) ou 0, 5 para o valor arredondado.</span><span class="sxs-lookup"><span data-stu-id="7fc21-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="7fc21-141">**Isenção de responsabilidade**: o valor padrão de qualquer fonte pode ser afetado pelo tamanho da textura dessa fonte ou como a fonte foi importada para o Unity.</span><span class="sxs-lookup"><span data-stu-id="7fc21-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="7fc21-142">Esses testes foram executados com base na fonte Arial padrão no Unity, bem como em outra fonte importada.</span><span class="sxs-lookup"><span data-stu-id="7fc21-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![Tamanho da fonte com fatores de dimensionamento](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="7fc21-144">Text3DSerikik.mat</span><span class="sxs-lookup"><span data-stu-id="7fc21-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="7fc21-145">Material para 3DTextPrefab com suporte para oclusão.</span><span class="sxs-lookup"><span data-stu-id="7fc21-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="7fc21-146">Requer 3DTextShader.shader</span><span class="sxs-lookup"><span data-stu-id="7fc21-146">Requires 3DTextShader.shader</span></span>

![Material de fonte padrão versus material 3DTextSngoeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="7fc21-148">Text3DShader.shader</span><span class="sxs-lookup"><span data-stu-id="7fc21-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="7fc21-149">Sombreador para 3DTextPrefab com suporte para oclusão.</span><span class="sxs-lookup"><span data-stu-id="7fc21-149">Shader for 3DTextPrefab with occlusion support.</span></span>