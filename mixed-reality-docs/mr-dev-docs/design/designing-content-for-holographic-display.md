---
title: Criar conteúdo para exibição holográfica
description: Saiba mais sobre as diretrizes de design e as práticas recomendadas para a exibição do Holographic em dispositivos HoloLens.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Design de interface do usuário, exibição de Holographic, design de conteúdo, tema escuro, tema claro, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, design, pixels
ms.openlocfilehash: 6bf65b9e40e42f1609b1108b366ac65637fcf106
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759271"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="dee8f-104">Criar conteúdo para exibição holográfica</span><span class="sxs-lookup"><span data-stu-id="dee8f-104">Designing content for holographic display</span></span>

![Local do ulnar](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="dee8f-106">Ao criar conteúdo para exibições do Holographic, há vários elementos que você precisa considerar para obter a melhor experiência.</span><span class="sxs-lookup"><span data-stu-id="dee8f-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="dee8f-107">Listamos algumas das nossas recomendações abaixo e você pode aprender mais sobre as características de exibições do Holographic na página [cor, luz e materiais](color-light-and-materials.md) .</span><span class="sxs-lookup"><span data-stu-id="dee8f-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="dee8f-108">Desafios com uma cor brilhante em uma grande superfície</span><span class="sxs-lookup"><span data-stu-id="dee8f-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="dee8f-109">Com base em nossa pesquisa e teste de experiência de HoloLens, descobrimos que o uso de cores brilhantes em uma grande área da exibição pode causar vários problemas:</span><span class="sxs-lookup"><span data-stu-id="dee8f-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="dee8f-110">**Fadiga de olho**</span><span class="sxs-lookup"><span data-stu-id="dee8f-110">**Eye fatigue**</span></span> 

<span data-ttu-id="dee8f-111">Como a exibição de Holographic é aditiva, os hologramas com cores brilhantes usam mais luz.</span><span class="sxs-lookup"><span data-stu-id="dee8f-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="dee8f-112">Uma cor sólida e brilhante em uma grande área da exibição pode facilmente causar fadigas de olho para o usuário.</span><span class="sxs-lookup"><span data-stu-id="dee8f-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="dee8f-113">**Oclusão mão**</span><span class="sxs-lookup"><span data-stu-id="dee8f-113">**Hand occlusion**</span></span> 

<span data-ttu-id="dee8f-114">A cor brilhante torna difícil para o usuário ver suas mãos ao interagir diretamente com objetos.</span><span class="sxs-lookup"><span data-stu-id="dee8f-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="dee8f-115">Como o usuário não consegue ver suas mãos, fica difícil perceber a profundidade/distância entre a mão/dedo para a superfície de destino.</span><span class="sxs-lookup"><span data-stu-id="dee8f-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="dee8f-116">O cursor Finger ajuda a compensar esse problema, mas ainda pode ser desafiador em uma superfície branca brilhante.</span><span class="sxs-lookup"><span data-stu-id="dee8f-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="dee8f-117">![Cor e mão oclusão ](images/color_handocclusion.jpg)
 *dificuldade para ver a mão na placa traseira de conteúdo colorido brilhante*</span><span class="sxs-lookup"><span data-stu-id="dee8f-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="dee8f-118">**Uniformidade de cores**</span><span class="sxs-lookup"><span data-stu-id="dee8f-118">**Color uniformity**</span></span>

<span data-ttu-id="dee8f-119">Devido às características das exibições do Holographic, uma grande área brilhante na exibição pode se tornar blotchy.</span><span class="sxs-lookup"><span data-stu-id="dee8f-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="dee8f-120">Usando esquemas de cores escuros, você pode minimizar esse problema.</span><span class="sxs-lookup"><span data-stu-id="dee8f-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="dee8f-121">Diretrizes de design para opções de cores</span><span class="sxs-lookup"><span data-stu-id="dee8f-121">Design guidelines for color choices</span></span>

<span data-ttu-id="dee8f-122">**Usar cor escura para o plano de fundo da interface do usuário**</span><span class="sxs-lookup"><span data-stu-id="dee8f-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="dee8f-123">Usando o esquema de cores escuro, você pode minimizar os olhos fadiga e melhorar a confiança em interações diretas.</span><span class="sxs-lookup"><span data-stu-id="dee8f-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="dee8f-124">![Exemplos de cores escuras usadas para os exemplos de conteúdo em segundo plano ](images/color_dark_examples.jpg)
 *da cor escura usada para o plano de fundo do conteúdo*</span><span class="sxs-lookup"><span data-stu-id="dee8f-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="dee8f-125">**Usar seminegrito ou espessura de fonte em negrito**</span><span class="sxs-lookup"><span data-stu-id="dee8f-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="dee8f-126">O HoloLens permite que sua experiência mostre um lindo texto de alta resolução.</span><span class="sxs-lookup"><span data-stu-id="dee8f-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="dee8f-127">No entanto, é recomendável que você evite pesos de fontes finas, como luz ou semileve, porque os traços verticais podem se tremular em tamanho de fonte pequeno.</span><span class="sxs-lookup"><span data-stu-id="dee8f-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="dee8f-128">![A espessura da fonte em negrito ou seminegrito (painel superior) melhora a ](images/color_font_examples.jpg)
 *espessura da fonte de negrito ou seminegrito (painel superior) melhora a legibilidade*</span><span class="sxs-lookup"><span data-stu-id="dee8f-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="dee8f-129">**Usar o material de HolographicBackplate do MRTK**</span><span class="sxs-lookup"><span data-stu-id="dee8f-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="dee8f-130">O material HolographicBackplate é aplicado a vários painéis de interface do usuário no Shell do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dee8f-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="dee8f-131">Um de seus recursos é um efeito iridescence que é visível para os usuários à medida que eles alternam sua posição com base no painel.</span><span class="sxs-lookup"><span data-stu-id="dee8f-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="dee8f-132">A cor da chapa traseira muda sutilmente em um espectro predefinido, criando um efeito visual envolvente e dinâmico sem interferir na legibilidade do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="dee8f-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="dee8f-133">Essa mudança sutil na cor também serve para compensar as irregularidades de cores secundárias.</span><span class="sxs-lookup"><span data-stu-id="dee8f-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="dee8f-134">Desafios com a placa traseira da interface do usuário Transparent ou translúcida</span><span class="sxs-lookup"><span data-stu-id="dee8f-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="dee8f-135">![Exemplos de interface do usuário transparente exemplos ](images/color_transparent_examples.jpg)
 *de placa traseira da interface do usuário transparente*</span><span class="sxs-lookup"><span data-stu-id="dee8f-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="dee8f-136">**Complexidade e acessibilidade Visual**</span><span class="sxs-lookup"><span data-stu-id="dee8f-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="dee8f-137">Como o Holographic Objects Blend com o ambiente físico, o conteúdo ou a interface do usuário legível em janelas transparentes ou translúcidas pode ser degradado.</span><span class="sxs-lookup"><span data-stu-id="dee8f-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="dee8f-138">Além disso, quando os objetos Holographic transparentes são sobrepostos uns dos outros, pode dificultar o usuário de interagir devido à profundidade confusa.</span><span class="sxs-lookup"><span data-stu-id="dee8f-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="dee8f-139">**Desempenho**</span><span class="sxs-lookup"><span data-stu-id="dee8f-139">**Performance**</span></span>

<span data-ttu-id="dee8f-140">Para que objetos transparentes ou translúcidas sejam renderizados corretamente, eles devem ser classificados e mesclados com todos os objetos, que existem em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="dee8f-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="dee8f-141">A classificação de objetos transparentes tem um custo modesto de CPU, a mesclagem tem um custo de GPU considerável porque não permite que a GPU Faça a remoção da superfície oculta por meio de seleção de z (ou seja,</span><span class="sxs-lookup"><span data-stu-id="dee8f-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="dee8f-142">teste de profundidade).</span><span class="sxs-lookup"><span data-stu-id="dee8f-142">depth testing).</span></span> <span data-ttu-id="dee8f-143">Não permitir remoção de superfície oculta aumenta o número de operações necessárias para o pixel renderizado final.</span><span class="sxs-lookup"><span data-stu-id="dee8f-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="dee8f-144">Isso coloca mais restrições de taxa de preenchimento de pressão.</span><span class="sxs-lookup"><span data-stu-id="dee8f-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="dee8f-145">**Problema de estabilidade de holograma com profundidade LSR tecnologia**</span><span class="sxs-lookup"><span data-stu-id="dee8f-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="dee8f-146">Para melhorar a Reprojeção do Holographic ou a estabilidade do holograma, um aplicativo pode enviar um buffer de profundidade ao sistema para cada quadro renderizado.</span><span class="sxs-lookup"><span data-stu-id="dee8f-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="dee8f-147">Ao usar o buffer de profundidade para a Reprojeção, você precisa escrever um buffer de profundidade para cada cor renderizada em pixel como uma profundidade correspondente.</span><span class="sxs-lookup"><span data-stu-id="dee8f-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="dee8f-148">Qualquer pixel com um valor de profundidade também deve ter um valor de cor.</span><span class="sxs-lookup"><span data-stu-id="dee8f-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="dee8f-149">Se as diretrizes acima não forem seguidas, as áreas da imagem renderizada que não possuam informações de profundidade válidas poderão ser reprojetadas de uma forma que produza artefatos, que geralmente são visíveis como uma distorção do tipo Wave.</span><span class="sxs-lookup"><span data-stu-id="dee8f-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="dee8f-150">Diretrizes de design para elementos transparentes</span><span class="sxs-lookup"><span data-stu-id="dee8f-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="dee8f-151">**Usar plano de fundo opaco da interface do usuário**</span><span class="sxs-lookup"><span data-stu-id="dee8f-151">**Use opaque UI background**</span></span>

<span data-ttu-id="dee8f-152">Por padrão, os objetos Transparent ou translúcidas não gravam profundidade para permitir a mistura adequada.</span><span class="sxs-lookup"><span data-stu-id="dee8f-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="dee8f-153">Maneiras de atenuar esse problema incluem, usando objetos opacos, garantindo que objetos translúcidas pareçam próximos a objetos opacos (como um botão translúcida na frente de uma chapa traseira opaca), forçando os objetos translúcidas a gravar profundidade (não aplicável em todos os cenários) ou renderizando objetos proxy, que só contribuem com valores de profundidade no final do quadro.</span><span class="sxs-lookup"><span data-stu-id="dee8f-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="dee8f-154">Soluções dentro do MRTK-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="dee8f-154">Solutions within MRTK-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="dee8f-155">Usando uma chapa invertida sólida e opaca, podemos proteger a segurança da legibilidade e da interação.</span><span class="sxs-lookup"><span data-stu-id="dee8f-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="dee8f-156">**Minimizar o número de pixels afetados**</span><span class="sxs-lookup"><span data-stu-id="dee8f-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="dee8f-157">Se o seu projeto deve usar objetos transparentes, tente minimizar o número de pixels afetados.</span><span class="sxs-lookup"><span data-stu-id="dee8f-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="dee8f-158">Por exemplo, se um objeto só estiver visível em determinadas condições (como um efeito de brilho aditivo), desabilite o objeto quando ele estiver totalmente invisível (em vez de definir a cor aditiva como preto).</span><span class="sxs-lookup"><span data-stu-id="dee8f-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="dee8f-159">Para formas 2D simples criadas usando um quad com uma máscara alfa, considere a criação de uma representação de malha da forma com um sombreador opaco em vez disso.</span><span class="sxs-lookup"><span data-stu-id="dee8f-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="dee8f-160">Exemplos escuros da interface do usuário em MRTK (Mixed Reality Toolkit) para o Unity</span><span class="sxs-lookup"><span data-stu-id="dee8f-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="dee8f-161">O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece muitos exemplos de blocos de construção de interface do usuário com base nos esquemas de cores escuros.</span><span class="sxs-lookup"><span data-stu-id="dee8f-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="dee8f-162">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="dee8f-162">Near Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/near-menu.md)
* [<span data-ttu-id="dee8f-163">Diálogo</span><span class="sxs-lookup"><span data-stu-id="dee8f-163">Dialog</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/dialog.md)
* [<span data-ttu-id="dee8f-164">Menu do lado</span><span class="sxs-lookup"><span data-stu-id="dee8f-164">Hand Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="dee8f-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="dee8f-165">See also</span></span>

* [<span data-ttu-id="dee8f-166">Cor, luz e materiais</span><span class="sxs-lookup"><span data-stu-id="dee8f-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="dee8f-167">Cursores</span><span class="sxs-lookup"><span data-stu-id="dee8f-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="dee8f-168">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="dee8f-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="dee8f-169">Botão</span><span class="sxs-lookup"><span data-stu-id="dee8f-169">Button</span></span>](button.md)
* [<span data-ttu-id="dee8f-170">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="dee8f-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="dee8f-171">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="dee8f-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="dee8f-172">Manipulação</span><span class="sxs-lookup"><span data-stu-id="dee8f-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="dee8f-173">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="dee8f-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="dee8f-174">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="dee8f-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="dee8f-175">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="dee8f-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="dee8f-176">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="dee8f-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="dee8f-177">Teclado</span><span class="sxs-lookup"><span data-stu-id="dee8f-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="dee8f-178">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="dee8f-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="dee8f-179">Slate</span><span class="sxs-lookup"><span data-stu-id="dee8f-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="dee8f-180">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="dee8f-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="dee8f-181">Sombreador</span><span class="sxs-lookup"><span data-stu-id="dee8f-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="dee8f-182">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="dee8f-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="dee8f-183">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="dee8f-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="dee8f-184">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="dee8f-184">Surface magnetism</span></span>](surface-magnetism.md)
