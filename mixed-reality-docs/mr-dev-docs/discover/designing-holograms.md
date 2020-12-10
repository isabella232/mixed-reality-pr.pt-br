---
title: Como criar hologramas
description: Saiba mais sobre a realidade misturada por meio do novo aplicativo de hologramas de design da Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, kit de ferramentas de realidade misturada, hologramas, criação de hologramas, aprendizado, aplicativo de exemplo, headset de realidade misturada, headset de realidade virtual, o que é realidade virtual
ms.openlocfilehash: bf904b319ed5b452f254b659315d9b531832a4d5
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002527"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="df68d-104">A criação de hologramas de design</span><span class="sxs-lookup"><span data-stu-id="df68d-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="df68d-105">Aguarde uma pequena janela de carregamento para considerar todos os GIFs e vídeos incorporados nesta página.</span><span class="sxs-lookup"><span data-stu-id="df68d-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="df68d-106">Aprender a criar uma realidade misturada pode ser difícil, especialmente com o quanto o Visual é o meio, que nem sempre se traduz bem em processos de design 2D.</span><span class="sxs-lookup"><span data-stu-id="df68d-106">Learning how to design for mixed reality can be hard, especially with how visual the medium is, which doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="df68d-107">Aqui na Microsoft, criamos um aplicativo gratuito que você pode baixar para o HoloLens 2, que ajuda você a aprender os conceitos básicos do design de UX da realidade misturada experimentando em primeira mão.</span><span class="sxs-lookup"><span data-stu-id="df68d-107">Here at Microsoft, we've created a free app you can download for the HoloLens 2, which helps you learn the fundamentals of mixed reality UX Design by experiencing it firsthand.</span></span> <span data-ttu-id="df68d-108">A abordagem exclusiva do aplicativo de criação de hologramas se aprofunda em comportamentos, dicas e recomendações de realidade misturada para ajudá-lo a criar aplicativos de HoloLens atraentes e incríveis.</span><span class="sxs-lookup"><span data-stu-id="df68d-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="df68d-109">Baixe o aplicativo gratuitamente na Microsoft Store e aprenda com a equipe de design da realidade misturada da Microsoft!</span><span class="sxs-lookup"><span data-stu-id="df68d-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df68d-110">Baixar o aplicativo de criação de hologramas</span><span class="sxs-lookup"><span data-stu-id="df68d-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animado da cena de acompanhamento de cabeçalho na sala de demonstração de criação de holograma](images/designing-holograms/demo-room.gif)

<span data-ttu-id="df68d-112">*Projetando a sala de demonstração do holograma (também conhecida como a casa Doll)*</span><span class="sxs-lookup"><span data-stu-id="df68d-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="df68d-113">Projetando para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="df68d-113">Designing for mixed reality</span></span>

<span data-ttu-id="df68d-114">Como muitos de vocês, usei para criar aplicativos móveis.</span><span class="sxs-lookup"><span data-stu-id="df68d-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="df68d-115">Vindo de um mundo de design 2D, que entra em total na computação espacial, onde tudo está agora no mundo, foi uma mudança significativa.</span><span class="sxs-lookup"><span data-stu-id="df68d-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="df68d-116">Em realidade misturada, os aplicativos não são mais confinados para uma tela 2D; na verdade, eles são quase gratuitos, colocados no mundo real e interagindo com objetos reais.</span><span class="sxs-lookup"><span data-stu-id="df68d-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="df68d-117">Para mim, conectar experiências 3D a processos de design de 2D convencionais é o aspecto mais desafiador do desenvolvimento de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="df68d-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="df68d-118">Em conversas com clientes, eu ouviria coisas como "sei quais recursos incluir e como colocá-los em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="df68d-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="df68d-119">É código, posso seguir os documentos e tutoriais, mas a experiência do usuário?</span><span class="sxs-lookup"><span data-stu-id="df68d-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="df68d-120">Tantos recursos, diferentes opções de entrada, diferentes cenários e ambientes físicos, é muito difícil ".</span><span class="sxs-lookup"><span data-stu-id="df68d-120">So many features, different input options, different scenarios and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="df68d-121">![Imagem do workshop de design do HoloLens 2 na ](images/designing-holograms/workshop.jpeg)
 *imagem de São Francisco do workshop de design do hololens 2 em San Francisco*</span><span class="sxs-lookup"><span data-stu-id="df68d-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="df68d-122">Uma oportunidade de ensinar</span><span class="sxs-lookup"><span data-stu-id="df68d-122">An opportunity to teach</span></span>

<span data-ttu-id="df68d-123">Não era óbvio a princípio, mas foi apresentada uma excelente oportunidade de usar realidade misturada como uma mídia para ensiná-la.</span><span class="sxs-lookup"><span data-stu-id="df68d-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="df68d-124">A criação de hologramas é uma experiência visual que explica conceitos e recomendações de design de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="df68d-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="df68d-125">É apenas você e um professor virtual que demonstra conceitos de design de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="df68d-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="df68d-126">Tudo é da perspectiva de uma terceira pessoa com a experiência firmemente em seu próprio espaço.</span><span class="sxs-lookup"><span data-stu-id="df68d-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="df68d-127">*Vídeo do trailer de design de hologramas*</span><span class="sxs-lookup"><span data-stu-id="df68d-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="df68d-128">Explorando a casa Doll</span><span class="sxs-lookup"><span data-stu-id="df68d-128">Exploring the doll house</span></span>

<span data-ttu-id="df68d-129">A Doll House é o ambiente virtual que usamos em todo o aplicativo, uma sala em miniatura de 80 x 60 x 40-cm que contém os elementos básicos que a maioria das salas tem em comum, como paredes, lâmpadas, mobília, uma tabela e uma TV.</span><span class="sxs-lookup"><span data-stu-id="df68d-129">The doll house is the virtual environment we use throughout the app, an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="df68d-130">A Doll House é a principal protagonist da experiência do aplicativo, portanto, precisávamos garantir que ela funcionasse muito bem em qualquer ambiente.</span><span class="sxs-lookup"><span data-stu-id="df68d-130">The doll house is the main protagonist of the app experience, so we needed to make sure that it would work great in any environment.</span></span> <span data-ttu-id="df68d-131">Imagine-o como um pequeno espaço de demonstração para Visualizar todos os tipos de conceitos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="df68d-131">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="df68d-132">*Vídeo do comportamento de ajuste de Dollhouse*</span><span class="sxs-lookup"><span data-stu-id="df68d-132">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="df68d-133">protótipos de 1:1 x 1:10</span><span class="sxs-lookup"><span data-stu-id="df68d-133">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="df68d-134">Nossa suposição inicial era que 1:1 demonstrações seriam incríveis, quase como examinar um professor de vida real.</span><span class="sxs-lookup"><span data-stu-id="df68d-134">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="df68d-135">O usuário veria tudo o que o professor vê em uma escala de vida real.</span><span class="sxs-lookup"><span data-stu-id="df68d-135">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="df68d-136">No entanto, percebemos imediatamente que haveria alguns problemas:</span><span class="sxs-lookup"><span data-stu-id="df68d-136">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="df68d-137">A maioria dos desenvolvedores executará seus aplicativos em escritórios ou salas menores do que a sala de demonstração e, portanto, não se ajustaria.</span><span class="sxs-lookup"><span data-stu-id="df68d-137">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="df68d-138">As exibições são aditivas, o que significa que todo o ambiente virtual será sobreposto ao espaço de um usuário.</span><span class="sxs-lookup"><span data-stu-id="df68d-138">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="df68d-139">Isso pode ficar confuso com duas tabelas, talvez duas vezes em sofás e paredes que não se alinhem.</span><span class="sxs-lookup"><span data-stu-id="df68d-139">That can get confusing with two tables, maybe double couches and walls that don’t align.</span></span>
- <span data-ttu-id="df68d-140">E o pior de todo um ambiente virtual altamente restrito por um campo de exibição.</span><span class="sxs-lookup"><span data-stu-id="df68d-140">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="df68d-141">Quando tentamos ter uma escala de 1:10, o resultado era uma exibição de visão de pássaros fantástica de um espaço realista em que você poderia ver tudo o que estava acontecendo de qualquer ângulo e todos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="df68d-141">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room where you could see everything that was going on from any angle and all at the same time.</span></span> <span data-ttu-id="df68d-142">O que era mais surpreendente é que a maioria dos testadores o achava muito mais imersiva para ver uma versão pequena, então eles nunca mudaram de volta para a escala 1:1.</span><span class="sxs-lookup"><span data-stu-id="df68d-142">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="df68d-143">Então, decidimos realmente refazer a versão 1:1 e evitar o trabalho extra necessário para adaptar a interface do usuário e outros aspectos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df68d-143">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="df68d-144">![Campo de exibição com 1:1 escala ](images/designing-holograms/1-1-scale.png)
 *do campo de exibição com escala de 1:1*</span><span class="sxs-lookup"><span data-stu-id="df68d-144">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="df68d-145">![Campo de exibição com 1:10 escala ](images/designing-holograms/1-10-scale.png)
 *do campo de exibição com escala de 1:10*</span><span class="sxs-lookup"><span data-stu-id="df68d-145">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="df68d-146">Usando a captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="df68d-146">Using Mixed Reality Capture</span></span>

<span data-ttu-id="df68d-147">Um dos recursos mais característicos desse aplicativo é o uso da captura de realidade misturada para ensinar e demonstrar conceitos de design de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="df68d-147">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="df68d-148">A Microsoft tem um estúdio de captura de realidade misturada em San Francisco.</span><span class="sxs-lookup"><span data-stu-id="df68d-148">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="df68d-149">A Microsoft também licencia essa tecnologia para outros estúdios, que incluem a dimensão de avatar em Washington D.C., metastage em Los Angeles, Dimension estúdios em Londres, SK Telecom in Seul e Volucap em Berlim.</span><span class="sxs-lookup"><span data-stu-id="df68d-149">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="df68d-150">Você pode encontrar mais informações sobre nossa [estúdios de captura de realidade misturada aqui](https://www.microsoft.com/mixed-reality/capture-studios).</span><span class="sxs-lookup"><span data-stu-id="df68d-150">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="df68d-151">*A seqüência bruta de Daniel Escudero de uma das câmeras 106 no estúdio de captura de realidade misturada em San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="df68d-151">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="df68d-152">O processo de captura gera uma malha, Normals e texturas em quadros-chave, que podem ser entregues como arquivos OBJ/PNG para posterior produção ou pronto para reprodução como um arquivo MP4 compactado H. 264.</span><span class="sxs-lookup"><span data-stu-id="df68d-152">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="df68d-153">Esses arquivos podem ser importados para o Unity, não real, nativo e WebXR e executados no Windows, iOS, Mac, Android, Magic Leap e PlayStation VR.</span><span class="sxs-lookup"><span data-stu-id="df68d-153">These files can be imported into Unity, Unreal, native, and WebXR and run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="df68d-154">*O player de captura fornecido para analisar MP4s que contêm vídeo com malhas de áudio e incorporadas.*</span><span class="sxs-lookup"><span data-stu-id="df68d-154">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="df68d-155">Manipulando capturas e objetos virtuais</span><span class="sxs-lookup"><span data-stu-id="df68d-155">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="df68d-156">As capturas de realidade misturadas produzem representações virtuais de pessoas ou animais, mas às vezes você pode precisar desses caracteres para interagir com outros objetos virtuais.</span><span class="sxs-lookup"><span data-stu-id="df68d-156">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="df68d-157">Os dois exemplos a seguir mostram diferentes maneiras de manipularmos as cenas para alcançar esse efeito.</span><span class="sxs-lookup"><span data-stu-id="df68d-157">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="df68d-158">Ajuste de olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="df68d-158">Head Gaze Adjustment</span></span>

<span data-ttu-id="df68d-159">O ajuste Headgaze permite que você mova a cabeça de uma pessoa capturada em tempo de execução, o que significa que você pode ter uma face de captura em direção a um usuário.</span><span class="sxs-lookup"><span data-stu-id="df68d-159">Headgaze adjustment lets you to move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="df68d-160">Em nosso caso, nós o usamos para mostrar o campo de exibição e campo de interesse.</span><span class="sxs-lookup"><span data-stu-id="df68d-160">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="df68d-161">O que você vê abaixo é um gameobject em movimento agindo como um destino para o olhar de cabeçalho examinar.</span><span class="sxs-lookup"><span data-stu-id="df68d-161">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="df68d-162">À medida que movemos o destino do lado a lado, o início da captura é mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="df68d-162">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="df68d-163">Usamos esse truque para garantir que a captura ociosa sempre se deparasse com os hologramas colocados em diferentes partes da casa Doll.</span><span class="sxs-lookup"><span data-stu-id="df68d-163">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![A cabeça da captura está sendo movida no tempo de execução após um gameobject de destino no Unity](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="df68d-165">*A cabeça da captura está sendo movida no tempo de execução após um gameobject de destino no Unity.*</span><span class="sxs-lookup"><span data-stu-id="df68d-165">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="df68d-166">Sincronizando objetos animados</span><span class="sxs-lookup"><span data-stu-id="df68d-166">Syncing Animated Objects</span></span>

<span data-ttu-id="df68d-167">A segunda, estava animando objetos para sincronizar com o movimento de uma captura.</span><span class="sxs-lookup"><span data-stu-id="df68d-167">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="df68d-168">Em diferentes partes do aplicativo, importamos objs tivessem sequenciais de uma captura específica a cada cinco quadros.</span><span class="sxs-lookup"><span data-stu-id="df68d-168">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="df68d-169">Os objs tivessem foram então animados na cena para garantir que correspondam ao quadro correspondente da captura.</span><span class="sxs-lookup"><span data-stu-id="df68d-169">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="df68d-170">É um processo entediante de animação e enquadramento, mas o resultado é ótimo. agora você pode ver uma captura de realidade misturada interagindo com objetos não capturados.</span><span class="sxs-lookup"><span data-stu-id="df68d-170">It’s a tedious process of animating and keyframing, but the result is great, you can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Animação sincronizada entre uma captura de realidade misturada e o painel da interface do usuário](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="df68d-172">*Animação sincronizada entre uma captura de realidade misturada e o painel da interface do usuário*</span><span class="sxs-lookup"><span data-stu-id="df68d-172">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="df68d-173">Processo criativo da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="df68d-173">UI creative process</span></span>

<span data-ttu-id="df68d-174">Quando começamos a ideating o design da interface do usuário, além de transportar informações, também queríamos mostrar algumas das mágicas e as possibilidades que os hologramas têm a oferecer.</span><span class="sxs-lookup"><span data-stu-id="df68d-174">When we started ideating the UI design, besides from transporting information we also wanted to show some of the magic and the possibilities that holograms have to offer.</span></span> <span data-ttu-id="df68d-175">Simplesmente Mostrar janelas 2D estáticas e caixas de texto não se sente bem no mundo 3D e não mostra muitas das possibilidades em mãos, logo desde o início, decidimos afastar-se e fazer uso completo do espaço 3D Holographic.</span><span class="sxs-lookup"><span data-stu-id="df68d-175">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world and doesn’t show many of the possibilities at hand, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="df68d-176">Inicialmente, começamos com a adição de uma espessura aos painéis e ícones, além das informações de texto.</span><span class="sxs-lookup"><span data-stu-id="df68d-176">At first, we started with adding some thickness to the panels and icons in addition to text information.</span></span> <span data-ttu-id="df68d-177">Ainda assim, como um usuário, o que vejo é uma caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="df68d-177">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="df68d-178">Caixas de texto com imagens, mas não estamos lá.</span><span class="sxs-lookup"><span data-stu-id="df68d-178">Text boxes with images, but we are not there.</span></span> <span data-ttu-id="df68d-179">Além disso, usamos os sombreadores do MRTK (Kit de ferramentas de realidade misturada).</span><span class="sxs-lookup"><span data-stu-id="df68d-179">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="df68d-180">Os sombreadores MRTK se tornaram uma ferramenta poderosa e usamos seus recursos de estêncil, alguns podem conhecê-lo como o efeito do portal, para adicionar profundidade negativa aos painéis.</span><span class="sxs-lookup"><span data-stu-id="df68d-180">The MRTK shaders became a powerful tool, and we made use of its stencil features, some may know it as the portal effect, to add negative depth to the panels.</span></span> <span data-ttu-id="df68d-181">Isso significa que, em vez de adicionar elementos na frente de uma caixa de texto, os ícones agora aparecem atrás de um painel transparente.</span><span class="sxs-lookup"><span data-stu-id="df68d-181">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="df68d-182">O que vejo agora como um usuário é algo que simplesmente não posso replicar no mundo real, e é aí que começou a Holographic mágica.</span><span class="sxs-lookup"><span data-stu-id="df68d-182">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="df68d-183">Além disso, como um usuário que eu não gosto muito de ler, faço isso já muito no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="df68d-183">Also as a user I don’t really like to read, I do that a lot already in the physical world.</span></span>

<span data-ttu-id="df68d-184">Obviamente, os ícones funcionam muito melhor do que o texto simples, portanto, para fornecer uma orientação ainda mais poderosa, comecei a criar um conjunto de objetos animados e avatars, cada um deles dizendo uma pequena história sobre o que está sendo feito no respectivo cenário e como ele está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="df68d-184">Obviously icons work a lot better than simple text does, so in order to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![GIF animado de um sistema de menus Holographic interativo](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="df68d-186">Conceitos fundamentais</span><span class="sxs-lookup"><span data-stu-id="df68d-186">Core concepts</span></span>

<span data-ttu-id="df68d-187">**Quadro holográfico**</span><span class="sxs-lookup"><span data-stu-id="df68d-187">**Holographic frame**</span></span>

![GIF animado de um usuário olhando o Dollhouse com o quadro Holographic realçado](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="df68d-189">**Sistemas de coordenadas**</span><span class="sxs-lookup"><span data-stu-id="df68d-189">**Coordinate systems**</span></span>

![GIF animado de um usuário que procura o Dollhouse com os sistemas de coordenadas realçados](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="df68d-191">**Acompanhamento ocular**</span><span class="sxs-lookup"><span data-stu-id="df68d-191">**Eye tracking**</span></span>

![GIF animado de um usuário olhando para hologramas fixos com o olho olhar Ray realçado](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="df68d-193">**Visualização da verificação de sala e mapeamento espacial**</span><span class="sxs-lookup"><span data-stu-id="df68d-193">**Room scan visualization and spatial mapping**</span></span>

![GIF animado de todas as superfícies dentro do Dollhouse que está sendo mapeado](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="df68d-195">**Reconhecimento de cena**</span><span class="sxs-lookup"><span data-stu-id="df68d-195">**Scene understanding**</span></span>

![GIF animado de objetos no Dollhouse que está sendo reconhecido](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="df68d-197">**Apontar e confirmar com raios de mão**</span><span class="sxs-lookup"><span data-stu-id="df68d-197">**Point and commit with hand rays**</span></span>

![GIF animado de um usuário levantando sua mão com um raio de mão realçado](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="df68d-199">Tempo "Experimente"</span><span class="sxs-lookup"><span data-stu-id="df68d-199">"Try it out" moments</span></span>

<span data-ttu-id="df68d-200">A criação de hologramas ensina conceitos de realidade misturada, mas também permite testá-los em sua sala.</span><span class="sxs-lookup"><span data-stu-id="df68d-200">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="df68d-201">Depois de algumas dessas explicações, vamos pausar e levá-lo da casa Doll e em um momento interativo.</span><span class="sxs-lookup"><span data-stu-id="df68d-201">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="df68d-202">Aqui estão alguns exemplos desses momentos interativos:</span><span class="sxs-lookup"><span data-stu-id="df68d-202">Here are some examples of those interactive moments:</span></span>

![GIF animado do quadro de acompanhamento à mão mostrando quando as mãos são detectadas e quando elas inserem o campo de exibição](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="df68d-204">*O quadro de acompanhamento à mão mostrando quando as mãos são detectadas e quando elas inserem o campo de exibição.*</span><span class="sxs-lookup"><span data-stu-id="df68d-204">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![GIF animado de interagir com a colisão de Crystals por meio de interação distante](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="df68d-206">*Interagindo com a colisão de Crystals por meio de interação distante*</span><span class="sxs-lookup"><span data-stu-id="df68d-206">*Interacting with colliding crystals through far interaction*</span></span>

![GIF animado de explorar o capacidades de interação próxima](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="df68d-208">*Explorando capacidades de interação próxima*</span><span class="sxs-lookup"><span data-stu-id="df68d-208">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="df68d-209">Sobre a equipe</span><span class="sxs-lookup"><span data-stu-id="df68d-209">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="df68d-210"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="df68d-210"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="df68d-211"><i>Designer técnico líder</i></span><span class="sxs-lookup"><span data-stu-id="df68d-211"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="df68d-212">Dan é o diretor criativo da criação de hologramas e atualmente funciona como líder de design para a Academia de realidade misturada da Microsoft em São Francisco, e era um designer de uma das estúdios de realidade misturada da Microsoft em Londres.</span><span class="sxs-lookup"><span data-stu-id="df68d-212">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="df68d-213"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="df68d-213"><b>Martin Wettig</b></span></span><br><span data-ttu-id="df68d-214"><i>Artista 3D sênior</i></span><span class="sxs-lookup"><span data-stu-id="df68d-214"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="df68d-215">Martin lidera a arte 3D e o design da interface do usuário na criação de hologramas e era anteriormente um artista 3D sênior em uma das estúdios de realidade misturada da Microsoft em Berlim.</span><span class="sxs-lookup"><span data-stu-id="df68d-215">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist in one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="df68d-216">Um enorme agradecimento à equipe de design da realidade misturada por compartilhar tanto conhecimento e, claro, para o incrível pessoal da [teoria do objeto](https://objecttheory.com/) que se tornou pessoas essenciais em cada etapa deste projeto.</span><span class="sxs-lookup"><span data-stu-id="df68d-216">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge and of course to the amazing folks at [Object Theory](https://objecttheory.com/) that became essential teammates in every single step of this project.</span></span> <span data-ttu-id="df68d-217">Obrigado por todos os talentos incríveis, pelo entusiasmo e pelo olho excepcional para o design.</span><span class="sxs-lookup"><span data-stu-id="df68d-217">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df68d-218">Baixar o aplicativo de criação de hologramas</span><span class="sxs-lookup"><span data-stu-id="df68d-218">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)