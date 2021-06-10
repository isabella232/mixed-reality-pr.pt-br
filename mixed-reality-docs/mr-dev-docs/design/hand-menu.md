---
title: Menu lateral
description: Os menus de mão permitem que os usuários aumentem rapidamente a interface do usuário anexada à mão para funções usadas com frequência.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: hand, menu, button, quick access, layout, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600325"
---
# <a name="hand-menu"></a><span data-ttu-id="8d090-104">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="8d090-104">Hand menu</span></span>

![Local do lado do Ulnar](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="8d090-106">O menu de mão é um dos padrões de experiência do usuário mais exclusivos no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8d090-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="8d090-107">Ele permite que você aumente rapidamente a interface do usuário anexada à mão.</span><span class="sxs-lookup"><span data-stu-id="8d090-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="8d090-108">Como ele pode ser acessado a qualquer momento e pode ser mostrado e ocultado facilmente, é ótimo para ações rápidas.</span><span class="sxs-lookup"><span data-stu-id="8d090-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="8d090-109">Você encontrará nossas práticas recomendadas para trabalhar com menus de mão na lista abaixo.</span><span class="sxs-lookup"><span data-stu-id="8d090-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="8d090-110">Você também pode encontrar uma cena de exemplo que demonstra o menu de mão no [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span><span class="sxs-lookup"><span data-stu-id="8d090-110">You can also find an example scene demonstrating the hand menu in [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="8d090-111">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="8d090-111">Best practices</span></span>

<span data-ttu-id="8d090-112">**Manter o número de botões pequenos**</span><span class="sxs-lookup"><span data-stu-id="8d090-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="8d090-113">Devido à distância próxima entre um menu bloqueado à mão e os olhos e a tendência de os usuários se concentrarem em uma área visual relativamente pequena a qualquer momento (o cone atenuário da visão é de aproximadamente 10 graus), recomendamos manter o número de botões pequenos.</span><span class="sxs-lookup"><span data-stu-id="8d090-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="8d090-114">Com base em nossa exploração, uma coluna com três botões funciona bem mantendo todo o conteúdo dentro do FOV (campo de exibição), mesmo quando um usuário move as mãos para o centro do FOV.</span><span class="sxs-lookup"><span data-stu-id="8d090-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="8d090-115">**Usar o menu de mão para ação rápida**</span><span class="sxs-lookup"><span data-stu-id="8d090-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="8d090-116">A acionamento de um arm e a manutenção da posição podem causar facilmente a queda de braço.</span><span class="sxs-lookup"><span data-stu-id="8d090-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="8d090-117">Use um método bloqueado manualmente para o menu que exige uma interação curta.</span><span class="sxs-lookup"><span data-stu-id="8d090-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="8d090-118">Se o menu for complexo e exigir tempos de interação estendidos, considere usar world-locked ou body-locked.</span><span class="sxs-lookup"><span data-stu-id="8d090-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="8d090-119">**Botão/Ângulo do painel**</span><span class="sxs-lookup"><span data-stu-id="8d090-119">**Button / Panel angle**</span></span>

<span data-ttu-id="8d090-120">Os menus devem ser posicionados no meio da cabeça e no lado oposto da cabeça: isso permite que uma movimentação natural da mão interaja com o menu com a mão oposta e evita posições de mão inconvenientes ou inconvenientes ao tocar em botões.</span><span class="sxs-lookup"><span data-stu-id="8d090-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="8d090-121">**Considere dar suporte a uma operação de mãos ou mãos livres**</span><span class="sxs-lookup"><span data-stu-id="8d090-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="8d090-122">Não suponha que ambas as mãos do usuário estão sempre disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8d090-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="8d090-123">Considere uma ampla variedade de contextos quando uma ou ambas as mãos não estão disponíveis e certifique-se de que suas contas de design para essas situações.</span><span class="sxs-lookup"><span data-stu-id="8d090-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="8d090-124">Para dar suporte a um menu com uma mão, você pode tentar fazer a transição do posicionamento do menu de bloqueado manualmente para o world-locked quando a mão se inverter (ficar inocável).</span><span class="sxs-lookup"><span data-stu-id="8d090-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="8d090-125">Para cenários de mãos livres, considere usar um comando de voz para invocar o menu de mão.</span><span class="sxs-lookup"><span data-stu-id="8d090-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="8d090-126">**Evite adicionar botões próximos ao pulso (botão página início do sistema)**</span><span class="sxs-lookup"><span data-stu-id="8d090-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="8d090-127">Se os botões do menu de mão são colocados muito próximos ao botão página início, ele pode disparar acidentalmente ao interagir com o menu de mão.</span><span class="sxs-lookup"><span data-stu-id="8d090-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="8d090-128">Menu manual com controles de interface do usuário grandes e complexos</span><span class="sxs-lookup"><span data-stu-id="8d090-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="8d090-129">É recomendável limitar o número de botões ou controles de interface do usuário em menus anexados manualmente.</span><span class="sxs-lookup"><span data-stu-id="8d090-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="8d090-130">Isso porque a interação estendida com um grande número de elementos da interface do usuário pode causar a queda do braço.</span><span class="sxs-lookup"><span data-stu-id="8d090-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="8d090-131">Se sua experiência exigir um menu grande, forneça uma maneira fácil para o usuário bloquear o menu.</span><span class="sxs-lookup"><span data-stu-id="8d090-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="8d090-132">Uma técnica que recomendamos é bloquear o mundo e, em seguida, usar o menu quando a mão cair ou se inverter do usuário.</span><span class="sxs-lookup"><span data-stu-id="8d090-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="8d090-133">Uma segunda técnica é permitir que o usuário pegue diretamente o menu com a outra mão.</span><span class="sxs-lookup"><span data-stu-id="8d090-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="8d090-134">Quando o usuário libera o menu, o menu deve bloquear o mundo.</span><span class="sxs-lookup"><span data-stu-id="8d090-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="8d090-135">Dessa forma, um usuário pode interagir com vários elementos da interface do usuário de maneira confortável e confiante durante um longo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="8d090-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="8d090-136">Quando o menu estiver bloqueado pelo mundo, forneça uma maneira de mover o menu e feche o menu quando ele não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="8d090-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="8d090-137">Tornar o menu móvel fornecendo alças nos lados ou na parte superior do menu.</span><span class="sxs-lookup"><span data-stu-id="8d090-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="8d090-138">Adicione um botão Fechar para permitir que o menu seja fechado.</span><span class="sxs-lookup"><span data-stu-id="8d090-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="8d090-139">Permita que o menu seja reattado à mão quando a mão do usuário estiver de frente para o usuário.</span><span class="sxs-lookup"><span data-stu-id="8d090-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="8d090-140">Também recomendamos exigir que os usuários se alocarem para evitar ativações falsas (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="8d090-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="8d090-141">**Menu grande que mostra um problema de usabilidade**</span><span class="sxs-lookup"><span data-stu-id="8d090-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="8d090-142">**Menu bloqueado pelo mundo no menu suspenso**</span><span class="sxs-lookup"><span data-stu-id="8d090-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="8d090-143">**Captura manual & pull para bloquear o menu**</span><span class="sxs-lookup"><span data-stu-id="8d090-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="8d090-144">Como evitar a ativação falsa</span><span class="sxs-lookup"><span data-stu-id="8d090-144">How to prevent false activation</span></span>

<span data-ttu-id="8d090-145">Se você usar apenas a mão como um evento para disparar o menu de mão, ele poderá aparecer acidentalmente quando você não precisar dele (falso positivo), porque as pessoas movem as mãos intencionalmente (para comunicação e manipulação de objetos) e não intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="8d090-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="8d090-146">Para reduzir as ativações falsas, adicione uma etapa extra além do evento de ativação para invocar o menu da mão (como dedos totalmente abertos ou o usuário olhando intencionalmente à mão).</span><span class="sxs-lookup"><span data-stu-id="8d090-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="8d090-147">**Exigir uma mão simples**</span><span class="sxs-lookup"><span data-stu-id="8d090-147">**Require Flat Palm**</span></span>

<span data-ttu-id="8d090-148">Ao exigir uma mão aberta simples, você pode impedir a ativação falsa que pode ocorrer à medida que o usuário manipula objetos ou gestos ao se comunicar em um ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d090-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="8d090-149">**Exigir o olhar**</span><span class="sxs-lookup"><span data-stu-id="8d090-149">**Require Gaze**</span></span>

<span data-ttu-id="8d090-150">Ao exigir que o usuário se atenule à mão (com o olhar com o olhar ou o olhar com a cabeça), ele impede as ativações falsas porque o usuário precisa direcionar sua atenção para a mão como uma etapa de ativação secundária (com um limite de distância fixo usado para permitir o conforto do usuário).</span><span class="sxs-lookup"><span data-stu-id="8d090-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="8d090-151">Práticas recomendadas de posicionamento do menu de mão</span><span class="sxs-lookup"><span data-stu-id="8d090-151">Hand menu placement best practices</span></span>

<span data-ttu-id="8d090-152">Na anatomia humana, o cérebro ulnar é um cérebro que é executado próximo à ulna.</span><span class="sxs-lookup"><span data-stu-id="8d090-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="8d090-153">A ulna é um longo dedo encontrado no forearm que se alonga do rosto até o menor dedo.</span><span class="sxs-lookup"><span data-stu-id="8d090-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="8d090-154">Abaixo estão dois posicionamentos recomendados com base em nossas explorações:</span><span class="sxs-lookup"><span data-stu-id="8d090-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8d090-155">![Localização da mão lateral ulnar dentro da mão](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="8d090-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="8d090-156">**A. Ulnar dentro da mão**</span><span class="sxs-lookup"><span data-stu-id="8d090-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="8d090-157">Essa posição é confiável porque as mãos não se sobrepõem umas às outras.</span><span class="sxs-lookup"><span data-stu-id="8d090-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="8d090-158">Isso é essencial para detecção e acompanhamento precisos da mão.</span><span class="sxs-lookup"><span data-stu-id="8d090-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d090-159">![Local do lado do Ulnar acima](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="8d090-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="8d090-160">**B. Ulnar acima**</span><span class="sxs-lookup"><span data-stu-id="8d090-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="8d090-161">Esse local é confortável para os usuários porque eles não precisam auximo muito o braço para interagir com o menu de mão.</span><span class="sxs-lookup"><span data-stu-id="8d090-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="8d090-162">É recomendável colocar os menus **13 cm** acima da mão e alinhar os botões dentro da mão ulnar.</span><span class="sxs-lookup"><span data-stu-id="8d090-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="8d090-163">Leia mais sobre o tamanho ideal do botão</span><span class="sxs-lookup"><span data-stu-id="8d090-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="8d090-164">Por motivos técnicos, recomendamos esse local com uma implementação necessária: o desenvolvedor precisará congelar o menu quando a mão oposta do usuário ficar próxima de interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="8d090-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="8d090-165">Isso evitará a tremtividade da sobreposição de mãos e também permitirá um direcionamento mais rápido dos botões.</span><span class="sxs-lookup"><span data-stu-id="8d090-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="8d090-166">As câmeras do HoloLens 2 identificam as mãos com precisão quando estão separadas umas das outras.</span><span class="sxs-lookup"><span data-stu-id="8d090-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="8d090-167">As mãos sobrepostas podem fazer com que os menus de mão se movam para fora do local de âncora.</span><span class="sxs-lookup"><span data-stu-id="8d090-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="8d090-168">Posições de menu que não são recomendadas</span><span class="sxs-lookup"><span data-stu-id="8d090-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="8d090-169">Fizemos uma pesquisa de usuário com diferentes layouts e locais de menus, os seguintes locais de menu **NÃO** são recomendados, encontre os contras de cada estudo abaixo:</span><span class="sxs-lookup"><span data-stu-id="8d090-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8d090-170">![Acima do arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="8d090-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="8d090-171">**Acima do arm**</span><span class="sxs-lookup"><span data-stu-id="8d090-171">**Above the arm**</span></span><br>
        <span data-ttu-id="8d090-172">1 – Difícil manter um bom acompanhamento de mão</span><span class="sxs-lookup"><span data-stu-id="8d090-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="8d090-173">2 – Causa a fatiga do usuário devido à posição anormal</span><span class="sxs-lookup"><span data-stu-id="8d090-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d090-174">![Acima dos dedos](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="8d090-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="8d090-175">**Acima dos dedos**</span><span class="sxs-lookup"><span data-stu-id="8d090-175">**Above fingers**</span></span><br>
        <span data-ttu-id="8d090-176">1 - Estouro da mão devido à segurando a mão por um longo tempo</span><span class="sxs-lookup"><span data-stu-id="8d090-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="8d090-177">2 – Problemas de acompanhamento da mão no índice e nos dedos médios</span><span class="sxs-lookup"><span data-stu-id="8d090-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="8d090-178">![Acima da mão central](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="8d090-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="8d090-179">**Acima da mão central**</span><span class="sxs-lookup"><span data-stu-id="8d090-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="8d090-180">1 - Problemas de acompanhamento de mão devido à sobreposição de mãos</span><span class="sxs-lookup"><span data-stu-id="8d090-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="8d090-181">2 - Estouro da mão devido à mão segurando as mãos por muito tempo para interagir com menus</span><span class="sxs-lookup"><span data-stu-id="8d090-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d090-182">![Ponta do dedo ](images/TopFingerTip.gif) **superior do dedo superior**</span><span class="sxs-lookup"><span data-stu-id="8d090-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="8d090-183">1 - Problemas de acompanhamento de mão</span><span class="sxs-lookup"><span data-stu-id="8d090-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="8d090-184">2 - Ressatirção da mão ao segurar a mão acima da postura normal</span><span class="sxs-lookup"><span data-stu-id="8d090-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="8d090-185">3 – Problemas ao pressionar botões com outros dedos por acidente devido ao espaço limitado entre os dedos</span><span class="sxs-lookup"><span data-stu-id="8d090-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="8d090-186">![Parte traseira do Arm](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="8d090-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="8d090-187">**Parte traseira do arm**</span><span class="sxs-lookup"><span data-stu-id="8d090-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="8d090-188">1 – Pode disparar o botão Página Principal por acidente</span><span class="sxs-lookup"><span data-stu-id="8d090-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="8d090-189">2 - Não é uma posição natural ou confortável</span><span class="sxs-lookup"><span data-stu-id="8d090-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8d090-190">Menu de mão no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="8d090-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="8d090-191">**[O MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e cenas de exemplo para o menu de mão.</span><span class="sxs-lookup"><span data-stu-id="8d090-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="8d090-192">O script do solucionador HandConstraintPalmUp permite anexar quaisquer objetos às mãos com várias opções configuráveis.</span><span class="sxs-lookup"><span data-stu-id="8d090-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="8d090-193">Os exemplos de menu de mão do MRTK incluem opções úteis, como a mão simples e o requisito de olhar para evitar a ativação falsa.</span><span class="sxs-lookup"><span data-stu-id="8d090-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="8d090-194">Documentações do menu Mão</span><span class="sxs-lookup"><span data-stu-id="8d090-194">Hand Menu Documentations</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [<span data-ttu-id="8d090-195">Cena de exemplo do menu mão</span><span class="sxs-lookup"><span data-stu-id="8d090-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="8d090-196">Você pode experimentar exemplos de menu manual no HoloLens 2 com o aplicativo Hub de Exemplos do MRTK.</span><span class="sxs-lookup"><span data-stu-id="8d090-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span>

* [<span data-ttu-id="8d090-197">Cena do menu Mão no Hub de Exemplos do MRTK</span><span class="sxs-lookup"><span data-stu-id="8d090-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="8d090-198">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d090-198">See also</span></span>

* [<span data-ttu-id="8d090-199">Cursores</span><span class="sxs-lookup"><span data-stu-id="8d090-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8d090-200">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="8d090-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8d090-201">Botão</span><span class="sxs-lookup"><span data-stu-id="8d090-201">Button</span></span>](button.md)
* [<span data-ttu-id="8d090-202">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="8d090-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8d090-203">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="8d090-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8d090-204">Manipulação</span><span class="sxs-lookup"><span data-stu-id="8d090-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8d090-205">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="8d090-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8d090-206">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="8d090-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8d090-207">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="8d090-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8d090-208">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="8d090-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8d090-209">Teclado</span><span class="sxs-lookup"><span data-stu-id="8d090-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8d090-210">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="8d090-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8d090-211">Slate</span><span class="sxs-lookup"><span data-stu-id="8d090-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="8d090-212">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="8d090-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="8d090-213">Sombreador</span><span class="sxs-lookup"><span data-stu-id="8d090-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="8d090-214">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="8d090-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8d090-215">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="8d090-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8d090-216">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="8d090-216">Surface magnetism</span></span>](surface-magnetism.md)