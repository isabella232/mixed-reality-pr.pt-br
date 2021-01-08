---
title: Exibindo o progresso
description: Saiba como os controles de progresso fornecem comentários ao usuário de que uma operação de longa execução está em andamento em seus aplicativos de realidade misturada.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, controles, interface do usuário, UX, indicador de progresso, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas da realidade misturada
ms.openlocfilehash: 489f4bd9fea31126f936673db7acafeab27d9cd9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009456"
---
# <a name="progress-indicator"></a><span data-ttu-id="b24c2-104">Indicador de progresso</span><span class="sxs-lookup"><span data-stu-id="b24c2-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="b24c2-105">Um controle de progresso fornece comentários de que uma operação de longa execução está em andamento.</span><span class="sxs-lookup"><span data-stu-id="b24c2-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="b24c2-106">Quando um indicador de progresso é visível, os usuários podem ver o tempo de espera e não podem interagir com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b24c2-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="b24c2-107">Tipo de progresso</span><span class="sxs-lookup"><span data-stu-id="b24c2-107">Types of progress</span></span>

<span data-ttu-id="b24c2-108">É importante fornecer as informações do usuário sobre o que está acontecendo.</span><span class="sxs-lookup"><span data-stu-id="b24c2-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="b24c2-109">Em realidade misturada, os usuários podem ser facilmente distraídos pelo ambiente físico ou pelos objetos se seu aplicativo não tiver bons comentários visuais.</span><span class="sxs-lookup"><span data-stu-id="b24c2-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="b24c2-110">Para situações que levam alguns segundos, como quando os dados estão sendo carregados ou uma cena está atualizando, é uma boa ideia mostrar um indicador visual.</span><span class="sxs-lookup"><span data-stu-id="b24c2-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="b24c2-111">Há duas opções para mostrar ao usuário que uma operação está em andamento – uma **barra de progresso** ou um **anel de progresso**.</span><span class="sxs-lookup"><span data-stu-id="b24c2-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="b24c2-112">Barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b24c2-112">Progress bar</span></span><br>
        <span data-ttu-id="b24c2-113">Uma barra de progresso mostra a porcentagem concluída de uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="b24c2-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="b24c2-114">Ele deve ser usado durante uma operação cuja duração é conhecida (desterminada), mas seu progresso não deve bloquear a interação do usuário com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b24c2-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="b24c2-115">*Imagem: exemplo de barra de progresso no HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b24c2-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b24c2-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b24c2-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b24c2-117">![Exemplo de barra de progresso no HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="b24c2-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="b24c2-118">Anel de progresso</span><span class="sxs-lookup"><span data-stu-id="b24c2-118">Progress ring</span></span><br>
        <span data-ttu-id="b24c2-119">Um anel de progresso tem apenas um estado indeterminado e deve ser usado quando a interação do usuário é bloqueada até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="b24c2-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="b24c2-120">*Imagem: exemplo de anel de andamento no HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b24c2-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b24c2-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b24c2-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b24c2-122">![Exemplo de anel de andamento no dispositivo HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="b24c2-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="b24c2-123">Progresso com um objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="b24c2-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="b24c2-124">Você pode adicionar à identidade da marca e personalidade do seu aplicativo Personalizando o controle de progresso com seus próprios objetos 2D/3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="b24c2-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="b24c2-125">*Imagem: progresso com o exemplo de malha personalizada no HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b24c2-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b24c2-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b24c2-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b24c2-127">![Progresso com o exemplo de malha personalizada no HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="b24c2-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="b24c2-128">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b24c2-128">Best practices</span></span>
* <span data-ttu-id="b24c2-129">Associe rigidamente a [mensagem ou a marca](billboarding-and-tag-along.md) à exibição do progresso, uma vez que o usuário pode mover facilmente o cabeçalho para o espaço vazio e perder o contexto.</span><span class="sxs-lookup"><span data-stu-id="b24c2-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="b24c2-130">Seu aplicativo pode parecer que ele falhou se o usuário não conseguir ver nada.</span><span class="sxs-lookup"><span data-stu-id="b24c2-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="b24c2-131">A cobrança e a marcação são criadas no pré-fabricado de progresso.</span><span class="sxs-lookup"><span data-stu-id="b24c2-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="b24c2-132">É sempre bom fornecer informações de status sobre o que está acontecendo com o usuário.</span><span class="sxs-lookup"><span data-stu-id="b24c2-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="b24c2-133">O progresso pré-fabricado fornece vários estilos visuais, incluindo o progresso padrão do Windows do tipo de toque para fornecer o status.</span><span class="sxs-lookup"><span data-stu-id="b24c2-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="b24c2-134">Você também pode usar uma malha personalizada com uma animação se quiser que o estilo do seu progresso se alinhe à marca do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b24c2-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="b24c2-135">Indicador de progresso em MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="b24c2-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="b24c2-136">MRTK pré-fabricados indicador de progresso</span><span class="sxs-lookup"><span data-stu-id="b24c2-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="b24c2-137">Serviço de transição MRTK-Scene</span><span class="sxs-lookup"><span data-stu-id="b24c2-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="b24c2-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="b24c2-138">See also</span></span>

* [<span data-ttu-id="b24c2-139">Cursores</span><span class="sxs-lookup"><span data-stu-id="b24c2-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b24c2-140">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="b24c2-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="b24c2-141">Botão</span><span class="sxs-lookup"><span data-stu-id="b24c2-141">Button</span></span>](button.md)
* [<span data-ttu-id="b24c2-142">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="b24c2-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b24c2-143">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="b24c2-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b24c2-144">Manipulação</span><span class="sxs-lookup"><span data-stu-id="b24c2-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b24c2-145">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="b24c2-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="b24c2-146">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="b24c2-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="b24c2-147">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="b24c2-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b24c2-148">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="b24c2-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="b24c2-149">Teclado</span><span class="sxs-lookup"><span data-stu-id="b24c2-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="b24c2-150">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="b24c2-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="b24c2-151">Slate</span><span class="sxs-lookup"><span data-stu-id="b24c2-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="b24c2-152">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="b24c2-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="b24c2-153">Sombreador</span><span class="sxs-lookup"><span data-stu-id="b24c2-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="b24c2-154">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="b24c2-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="b24c2-155">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="b24c2-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="b24c2-156">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="b24c2-156">Surface magnetism</span></span>](surface-magnetism.md)
