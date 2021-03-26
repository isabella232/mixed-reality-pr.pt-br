---
title: Orientador de mão
description: Saiba como as mãos 3D são disparadas usando o direito de aprendizado quando o sistema não detecta as mãos do usuário para ajudar a ajudá-las.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Realidade mista do Windows, design, direito à mão, headset de imersão, MRTK, mãos, ajuda, mãos, headsets de realidade misturada, headset de realidade mista do Windows, Headset virtual realismo, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 56a56893a7c5bc772268ab9980f25327eae83af5
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550066"
---
# <a name="hand-coach"></a><span data-ttu-id="10158-104">Orientador de mão</span><span class="sxs-lookup"><span data-stu-id="10158-104">Hand coach</span></span>

![Exemplo: à mão](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="10158-106">A mão do direito aciona as mãos modeladas 3D quando o sistema não detecta as mãos do usuário.</span><span class="sxs-lookup"><span data-stu-id="10158-106">Hand coach triggers 3D modeled hands when the system doesn't detect the user’s hands.</span></span> <span data-ttu-id="10158-107">Esse recurso é um componente "ensinando" que ajuda a orientar o usuário quando o gesto não foi ensinado.</span><span class="sxs-lookup"><span data-stu-id="10158-107">This feature is a “teaching” component that helps guide the user when the gesture hasn't been taught.</span></span> <span data-ttu-id="10158-108">Se os usuários não tiverem feito o gesto especificado por um período, as mãos entrarão em loop com um atraso.</span><span class="sxs-lookup"><span data-stu-id="10158-108">If users haven't done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="10158-109">A mão da direita poderia ser usada para representar o pressionamento de um botão ou a seleção de um holograma.</span><span class="sxs-lookup"><span data-stu-id="10158-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="10158-110">Mão da direita fornecida</span><span class="sxs-lookup"><span data-stu-id="10158-110">Hand coach provided</span></span>

<span data-ttu-id="10158-111">O modelo de interação atual representa uma ampla variedade de controles de gesto, como rolagem, seleção extrema e quase toque.</span><span class="sxs-lookup"><span data-stu-id="10158-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="10158-112">Abaixo está uma lista completa dos gestos de mão existentes fornecidos no<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span><span class="sxs-lookup"><span data-stu-id="10158-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="10158-113">![Exemplo de próximo Select](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="10158-114">**Exemplo de próximo Select-used mostrar como selecionar botões ou fechar objetos que interagem**</span><span class="sxs-lookup"><span data-stu-id="10158-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="10158-115">![Exemplo de toque de ar](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="10158-116">**Exemplo de toque de ar – usado para mostrar como selecionar objetos que estão distantes**</span><span class="sxs-lookup"><span data-stu-id="10158-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="10158-117">![Exemplo de movimentação](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="10158-118">**Exemplo de movimentação de um objeto em espaço-usado para mostrar como mover um holograma no espaço**</span><span class="sxs-lookup"><span data-stu-id="10158-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="10158-119">![Exemplo de rotação](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="10158-120">**Exemplo de Rotate-Used para mostrar como girar hologramas ou objetos**</span><span class="sxs-lookup"><span data-stu-id="10158-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="10158-121">![Exemplo de escala](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="10158-122">**Exemplo de escala-usado para mostrar como manipular hologramas para serem maiores ou menores**</span><span class="sxs-lookup"><span data-stu-id="10158-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="10158-123">![Exemplo de Palm up](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="10158-124">**Exemplo de Palm up – sugestão de uso, para exibir menus à mão**</span><span class="sxs-lookup"><span data-stu-id="10158-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="10158-125">![Exemplo de HandFlip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="10158-126">**Exbordo de mão invertida – outra maneira de exibir menus à mão**</span><span class="sxs-lookup"><span data-stu-id="10158-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="10158-127">![Exemplo de rolagem](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="10158-128">**Exemplo de Scroll – usado para rolar uma lista ou um documento longo**</span><span class="sxs-lookup"><span data-stu-id="10158-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="10158-129">Conceitos de design</span><span class="sxs-lookup"><span data-stu-id="10158-129">Design concepts</span></span>

<span data-ttu-id="10158-130">Para Hololens2, criamos interações de mão com base em gestos de instinctual e de mão natural.</span><span class="sxs-lookup"><span data-stu-id="10158-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="10158-131">Acreditamos que eles sejam intuitivos para a maioria dos usuários, portanto, não criamos momentos de aprendizado de gestos dedicados.</span><span class="sxs-lookup"><span data-stu-id="10158-131">We believe these to be intuitive to most users, so we didn't create dedicated gesture learning moments.</span></span> <span data-ttu-id="10158-132">Em vez disso, criamos o direito de acesso para ajudar os usuários a aprender sobre esses gestos se eles estiverem presos ou não estiverem familiarizados com as interações com o holograma.</span><span class="sxs-lookup"><span data-stu-id="10158-132">Instead, we created the hand coach to help users learn about these gestures if they get stuck or are unfamiliar with hologram interactions.</span></span> <span data-ttu-id="10158-133">Sem um momento de aprendizado, sentimos que mostrar aos usuários como executar uma ação demonstrando que seria a melhor opção.</span><span class="sxs-lookup"><span data-stu-id="10158-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="10158-134">Descobrimos que os usuários conseguiram descobrir o gesto, mas precisavam de uma pequena orientação.</span><span class="sxs-lookup"><span data-stu-id="10158-134">We found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="10158-135">Se detectarmos que um usuário não interage com um objeto por um período, uma mão orientada seria disparada demonstrando o posicionamento correto e o local do dedo.</span><span class="sxs-lookup"><span data-stu-id="10158-135">If we detect a user doesn't interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="10158-136">Simples</span><span class="sxs-lookup"><span data-stu-id="10158-136">Intuitive</span></span>

<span data-ttu-id="10158-137">Ao animar as mãos, deve ser óbvio e não deve causar qualquer confusão.</span><span class="sxs-lookup"><span data-stu-id="10158-137">When animating hands, it should be obvious and shouldn't cause any confusion.</span></span> <span data-ttu-id="10158-138">A animação de mão é uma representação do gesto que você está tentando solicitar que o usuário entenda.</span><span class="sxs-lookup"><span data-stu-id="10158-138">The hand animation is a representation of the gesture you're trying to prompt the user to understand.</span></span> 

<span data-ttu-id="10158-139">Por exemplo, se você quiser que um usuário pressione um botão, um botão à mão será disparado.</span><span class="sxs-lookup"><span data-stu-id="10158-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="10158-140">![Exemplo: mão com o direito ao lado de toque](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="10158-141">*Mão da direita demonstrando perto de tocar em uma gem*</span><span class="sxs-lookup"><span data-stu-id="10158-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="10158-142">Escala manual</span><span class="sxs-lookup"><span data-stu-id="10158-142">Hand scale</span></span>

<span data-ttu-id="10158-143">Testamos vários tamanhos de mão com os menus da interface do usuário e achamos que, se as mãos fossem verdadeiras para o tamanho, ela deu uma sensação menacing.</span><span class="sxs-lookup"><span data-stu-id="10158-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling.</span></span> <span data-ttu-id="10158-144">Se eles fossem muito pequenos, era difícil ver e entender o gesto.</span><span class="sxs-lookup"><span data-stu-id="10158-144">If they were too small, it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="10158-145">**Voz e mãos**</span><span class="sxs-lookup"><span data-stu-id="10158-145">**Voice over and hands**</span></span>

<span data-ttu-id="10158-146">Não espere que os usuários possam ouvir um conjunto de instruções por meio de voz e assistir a instruções diferentes por meio da mão.</span><span class="sxs-lookup"><span data-stu-id="10158-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="10158-147">Sequenciar suas instruções para ajudar os usuários a se concentrarem em relação à sua atenção para reduzir a sobrecarga do sensor.</span><span class="sxs-lookup"><span data-stu-id="10158-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="10158-148">Posso criar o meu próprio?</span><span class="sxs-lookup"><span data-stu-id="10158-148">Can I create my own?</span></span>

<span data-ttu-id="10158-149">Sim!</span><span class="sxs-lookup"><span data-stu-id="10158-149">Yes!</span></span> <span data-ttu-id="10158-150">Incentivamos você a criar seu próprio gesto exclusivo para seu jogo e contribuir de volta para a Comunidade!</span><span class="sxs-lookup"><span data-stu-id="10158-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="10158-151">Fornecemos um arquivo Maya de um rigged Hand que pode ser usado para seu aplicativo, que pode ser baixado aqui: <a href="files/HandCoach_MRTK.zip"> baixar HandCoach_MRTK.zip </a></span><span class="sxs-lookup"><span data-stu-id="10158-151">We've provided a Maya file of a Rigged hand that can be used for your app, which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip </a></span></span>

<span data-ttu-id="10158-152">![Exemplo de mãos animadas no Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="10158-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="10158-153">*Exemplo de mão animada ao investigar uma caixa no Maya*</span><span class="sxs-lookup"><span data-stu-id="10158-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="10158-154">**Ferramenta de criação recomendada**</span><span class="sxs-lookup"><span data-stu-id="10158-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="10158-155">Entre artistas 3D, muitos optam por usar o [Maya do Autodesk, que pode usar o HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar a maneira como os ativos são criados.</span><span class="sxs-lookup"><span data-stu-id="10158-155">Among 3D artists, many choose to use [Autodesk’s Maya, which can use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="10158-156">O arquivo hands fornecido é um arquivo binário Maya, portanto, é recomendável usar Maya para animar e exportar as mãos.</span><span class="sxs-lookup"><span data-stu-id="10158-156">The hands file provided is a Maya Binary File, so it's recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="10158-157">Se você preferir usar outro programa 3D, aqui está um <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Baixe HandCoachMRTK_FBX.zip </a> para criar sua própria configuração de controlador.</span><span class="sxs-lookup"><span data-stu-id="10158-157">If you prefer to use another 3D program, here's a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Download HandCoachMRTK_FBX.zip </a> to create your own controller setup.</span></span> 

<span data-ttu-id="10158-158">Se estiver usando o arquivo do Maya Hand disponível para download fornecido, é recomendável reduzir verticalmente as mãos no Unity para 0,6.</span><span class="sxs-lookup"><span data-stu-id="10158-158">If using the downloadable maya Hand File provided, it's suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="10158-159">![Exemplo: mão de Rig do dispositivo em Maya](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="10158-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="10158-160">*Rigged hands*</span><span class="sxs-lookup"><span data-stu-id="10158-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="10158-161">Especificações técnicas</span><span class="sxs-lookup"><span data-stu-id="10158-161">Technical Specs</span></span>

*   <span data-ttu-id="10158-162">O arquivo de dois mãos está disponível no formato ASCII Maya</span><span class="sxs-lookup"><span data-stu-id="10158-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="10158-163">A mão direita e esquerda está disponível no formato binário Maya</span><span class="sxs-lookup"><span data-stu-id="10158-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="10158-164">Definir o arquivo Maya para 24 FPS</span><span class="sxs-lookup"><span data-stu-id="10158-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="10158-165">Dentro do arquivo, há uma mão esquerda e direita, que pode ser usada para dois gestos de mão ou de entrega única.</span><span class="sxs-lookup"><span data-stu-id="10158-165">Within the file, there's a left and right hand, which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="10158-166">A mão direita só estará visível por padrão.</span><span class="sxs-lookup"><span data-stu-id="10158-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="10158-167">É recomendável deixar um buffer de cerca de 10 quadros no início e no final para esmaecer</span><span class="sxs-lookup"><span data-stu-id="10158-167">It's suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="10158-168">Se animar um objeto com um destino especificado, sua prática recomendada será animar para uma caixa padrão ou NULL.</span><span class="sxs-lookup"><span data-stu-id="10158-168">If animating an object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="10158-169">Se a mão estiver animando um objeto físico, como uma caixa, sua melhor prática para não animar a tradução em Maya, mas esperar para animá-la no Unity ou no código.</span><span class="sxs-lookup"><span data-stu-id="10158-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="10158-170">A animação visível deve ser 1,5 segundos para que todas as informações significativas sejam transmitidas</span><span class="sxs-lookup"><span data-stu-id="10158-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="10158-171">Quando você sentir satisfeito com sua animação:</span><span class="sxs-lookup"><span data-stu-id="10158-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="10158-172">Selecionar todas as junções e distortar quadros-chave</span><span class="sxs-lookup"><span data-stu-id="10158-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="10158-173">Exclua os controladores, selecione as junções e a malha e exporte como um FBX</span><span class="sxs-lookup"><span data-stu-id="10158-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="10158-174">Se houver várias animações, você poderá usar o exportador de jogos interno do Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="10158-174">If there are Multiple Animations, you can use Maya’s built-in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="10158-175">Exportando do Maya</span><span class="sxs-lookup"><span data-stu-id="10158-175">Exporting from Maya</span></span>

<span data-ttu-id="10158-176">Depois de estar satisfeito com sua animação</span><span class="sxs-lookup"><span data-stu-id="10158-176">After you're satisfied with your animation</span></span>
* <span data-ttu-id="10158-177">Selecionar todas as junções: selecionar hierarquia de ></span><span class="sxs-lookup"><span data-stu-id="10158-177">Select all joints: Select > Hierarchy</span></span>

     ![Exemplo: hierarquia no menu](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="10158-179">Distortar sua animação: alternar para animação > chave > animação de torta</span><span class="sxs-lookup"><span data-stu-id="10158-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Exemplo: distortar local do menu de animação](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="10158-181">Excluir o dispositivo de controlador: contorno > MainR_Grp ou MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="10158-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Exemplo: local do menu de equipamentos do controlador](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="10158-183">Exportar como FBX: selecione JNT + malha: arquivo > exportar seleção (caixa de opção) > exportar seleção</span><span class="sxs-lookup"><span data-stu-id="10158-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Exemplo: exportar local do menu de seleção](images/HandCoach/OptionBox.png)<br>

     ![Exemplo: local do menu](images/HandCoach/SelectionExport.png)<br>

     ![Exemplo: local do menu de opções de exportação](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="10158-187">Ao exportar como um FBX e trazido para o Unity, dimensione as mãos para 0,6.</span><span class="sxs-lookup"><span data-stu-id="10158-187">When exporting as an FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="10158-188">Descobrimos que esse foi um equilíbrio perfeito para a exibição das mãos.</span><span class="sxs-lookup"><span data-stu-id="10158-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="10158-189">![Exemplo: configurações de Unity](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="10158-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="10158-190">*Configurações de Unity para HandCoach_R pré-fabricado encontradas em MRTK*</span><span class="sxs-lookup"><span data-stu-id="10158-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="10158-191">Implementando mãos em seu projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="10158-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="10158-192">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="10158-192">Best practices</span></span>

* <span data-ttu-id="10158-193">Sugerimos reduzir verticalmente as mãos no Unity para 0,6</span><span class="sxs-lookup"><span data-stu-id="10158-193">It's suggested to scale down the hands in unity to 0.6</span></span>
* <span data-ttu-id="10158-194">As mãos devem ser executadas duas vezes e, se não forem concluídas, passarão continuamente em loop até que o gesto seja concluído.</span><span class="sxs-lookup"><span data-stu-id="10158-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="10158-195">As mãos devem ser repetidas duas vezes para garantir que o usuário tenha tempo para se registrar e ver o gesto.</span><span class="sxs-lookup"><span data-stu-id="10158-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="10158-196">As mãos devem aparecer e desaparecer entre os loops.</span><span class="sxs-lookup"><span data-stu-id="10158-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="10158-197">Se as mãos do usuário estiverem visíveis por câmeras HL2, mas os usuários não estiverem fazendo a interação necessária, as mãos serão exibidas após 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="10158-197">If user’s hands are visible by HL2 cameras but users aren't doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="10158-198">Se as mãos do usuário não estiverem visíveis por câmeras HL2, as mãos aparecerão após 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="10158-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="10158-199">Se as mãos do usuário forem visivelmente rastreadas por câmeras HL2s no meio da animação, a animação será concluída e desaparecer.</span><span class="sxs-lookup"><span data-stu-id="10158-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="10158-200">Se você estiver incluindo a voz, sugerimos que ela corresponda ao gesto da mão.</span><span class="sxs-lookup"><span data-stu-id="10158-200">If you're including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="10158-201">Se você tiver ensinado as mãos pelo menos uma vez, repita o gesto se detectar que o usuário está preso.</span><span class="sxs-lookup"><span data-stu-id="10158-201">If you've taught the hands at least once, only repeat the gesture if it's detected that the user is stuck.</span></span>
*   <span data-ttu-id="10158-202">Se as posições de dedos/mãos específicas forem críticas, verifique se os usuários podem ver claramente essas nuances na animação.</span><span class="sxs-lookup"><span data-stu-id="10158-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="10158-203">Experimente Angling as mãos para que as partes mais importantes fiquem claramente visíveis.</span><span class="sxs-lookup"><span data-stu-id="10158-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="10158-204">Se você perceber distorção nas mãos, precisará ir para as configurações de qualidade do Unity aumentar o número de Bones.</span><span class="sxs-lookup"><span data-stu-id="10158-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the number of bones.</span></span> 
 <span data-ttu-id="10158-205">Acesse as configurações de projeto de > de edição do Unity > qualidade > outros pesos do Blend >.</span><span class="sxs-lookup"><span data-stu-id="10158-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="10158-206">Verifique se "4 Bones" estão selecionados para ver as junções suaves.</span><span class="sxs-lookup"><span data-stu-id="10158-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![Exemplo: janela de configurações do projeto](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a><span data-ttu-id="10158-208">O que evitar</span><span class="sxs-lookup"><span data-stu-id="10158-208">What to avoid</span></span>

* <span data-ttu-id="10158-209">Dimensionar as mãos muito grandes</span><span class="sxs-lookup"><span data-stu-id="10158-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="10158-210">colocar as mãos muito próximas ao usuário</span><span class="sxs-lookup"><span data-stu-id="10158-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="10158-211">As mãos só devem ser ensinadas uma vez.</span><span class="sxs-lookup"><span data-stu-id="10158-211">Hands should only be taught once.</span></span> <span data-ttu-id="10158-212">O excesso de ensino pode causar confusão e bagunças</span><span class="sxs-lookup"><span data-stu-id="10158-212">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="10158-213">Colocando-o no Unity, baixe o MRTK mais recente aqui: https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="10158-213">Bringing it into Unity, download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="10158-214">Material: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="10158-214">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="10158-215">Scripts: consulte as diretrizes do MRTK para o <a href= "/windows/mixed-reality/mrtk-docs/features/experimental/hand-coach.md"> MRTK Hand </a></span><span class="sxs-lookup"><span data-stu-id="10158-215">Scripts: Refer to MRTK guidelines for <a href= "/windows/mixed-reality/mrtk-docs/features/experimental/hand-coach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="10158-216">Configuração por projeto</span><span class="sxs-lookup"><span data-stu-id="10158-216">Per- project setting</span></span>
        *   <span data-ttu-id="10158-217">Cena definida como UWP: a instrução pode ser encontrada no [projeto do Unity de configuração](../develop/unity/Configure-Unity-Project.md) para o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="10158-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](../develop/unity/Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="10158-218">Veja também</span><span class="sxs-lookup"><span data-stu-id="10158-218">See also</span></span>

* [<span data-ttu-id="10158-219">Interação-conceitos básicos</span><span class="sxs-lookup"><span data-stu-id="10158-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="10158-220">Processo de criação de ativos</span><span class="sxs-lookup"><span data-stu-id="10158-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="10158-221">Gestos</span><span class="sxs-lookup"><span data-stu-id="10158-221">Gestures</span></span>](./interaction-fundamentals.md)
* [<span data-ttu-id="10158-222">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="10158-222">Install the Tools</span></span>](../develop/install-the-tools.md)
* [<span data-ttu-id="10158-223">Configurar projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="10158-223">Configure Unity Project</span></span>](../develop/unity/Configure-Unity-Project.md)
* [<span data-ttu-id="10158-224">Visão geral do desenvolvimento do Unity</span><span class="sxs-lookup"><span data-stu-id="10158-224">Unity development overview</span></span>](../develop/unity/unity-development-overview.md)
* [<span data-ttu-id="10158-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="10158-225">MRTK 101</span></span>](../out-of-scope/mrtk-101.md)