---
title: Como criar hologramas
description: Saiba mais sobre a realidade misturada por meio do novo aplicativo de hologramas de design da Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, kit de ferramentas de realidade misturada, hologramas, criação de hologramas, aprendizado, aplicativo de exemplo, headset de realidade misturada, headset de realidade virtual, o que é realidade virtual
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757754"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="8fb80-104">A criação de hologramas de design</span><span class="sxs-lookup"><span data-stu-id="8fb80-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="8fb80-105">Aguarde uma pequena janela de carregamento para considerar todos os GIFs e vídeos incorporados nesta página.</span><span class="sxs-lookup"><span data-stu-id="8fb80-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="8fb80-106">Aprender a criar uma realidade misturada pode ser difícil porque a média nem sempre se traduz bem em processos de design 2D.</span><span class="sxs-lookup"><span data-stu-id="8fb80-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="8fb80-107">Aqui na Microsoft, criamos um aplicativo gratuito para o HoloLens 2 para ajudá-lo a aprender os conceitos básicos do design de UX da realidade misturada em primeira mão.</span><span class="sxs-lookup"><span data-stu-id="8fb80-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="8fb80-108">A abordagem exclusiva do aplicativo de criação de hologramas se aprofunda em comportamentos, dicas e recomendações de realidade misturada para ajudá-lo a criar aplicativos de HoloLens atraentes e incríveis.</span><span class="sxs-lookup"><span data-stu-id="8fb80-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="8fb80-109">Baixe o aplicativo gratuitamente na Microsoft Store e aprenda com a equipe de design da realidade misturada da Microsoft!</span><span class="sxs-lookup"><span data-stu-id="8fb80-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8fb80-110">Baixar o aplicativo de criação de hologramas</span><span class="sxs-lookup"><span data-stu-id="8fb80-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animado da cena de acompanhamento de cabeçalho na sala de demonstração de criação de holograma](images/designing-holograms/demo-room.gif)

<span data-ttu-id="8fb80-112">*Projetando a sala de demonstração do holograma (também conhecida como a casa Doll)*</span><span class="sxs-lookup"><span data-stu-id="8fb80-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="8fb80-113">Projetando para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="8fb80-113">Designing for mixed reality</span></span>

<span data-ttu-id="8fb80-114">Como muitos de vocês, usei para criar aplicativos móveis.</span><span class="sxs-lookup"><span data-stu-id="8fb80-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="8fb80-115">Vindo de um mundo de design 2D, que entra em total na computação espacial, onde tudo está agora no mundo, foi uma mudança significativa.</span><span class="sxs-lookup"><span data-stu-id="8fb80-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="8fb80-116">Em realidade misturada, os aplicativos não são mais confinados para uma tela 2D; na verdade, eles são quase gratuitos, colocados no mundo real e interagindo com objetos reais.</span><span class="sxs-lookup"><span data-stu-id="8fb80-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="8fb80-117">Para mim, conectar experiências 3D a processos de design de 2D convencionais é o aspecto mais desafiador do desenvolvimento de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8fb80-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="8fb80-118">Em conversas com clientes, eu ouviria coisas como "sei quais recursos incluir e como colocá-los em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="8fb80-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="8fb80-119">É código, posso seguir os documentos e tutoriais, mas a experiência do usuário?</span><span class="sxs-lookup"><span data-stu-id="8fb80-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="8fb80-120">Tantos recursos, diferentes opções de entrada, cenários diferentes e ambientes físicos, é muito difícil ".</span><span class="sxs-lookup"><span data-stu-id="8fb80-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="8fb80-121">![Imagem do workshop de design do HoloLens 2 na ](images/designing-holograms/workshop.jpeg)
 *imagem de São Francisco do workshop de design do hololens 2 em San Francisco*</span><span class="sxs-lookup"><span data-stu-id="8fb80-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="8fb80-122">Uma oportunidade de ensinar</span><span class="sxs-lookup"><span data-stu-id="8fb80-122">An opportunity to teach</span></span>

<span data-ttu-id="8fb80-123">Não era óbvio a princípio, mas foi apresentada uma excelente oportunidade de usar realidade misturada como uma mídia para ensiná-la.</span><span class="sxs-lookup"><span data-stu-id="8fb80-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="8fb80-124">A criação de hologramas é uma experiência visual que explica conceitos e recomendações de design de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8fb80-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="8fb80-125">É apenas você e um professor virtual que demonstra conceitos de design de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8fb80-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="8fb80-126">Tudo é da perspectiva de uma terceira pessoa com a experiência firmemente em seu próprio espaço.</span><span class="sxs-lookup"><span data-stu-id="8fb80-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="8fb80-127">*Vídeo do trailer de design de hologramas*</span><span class="sxs-lookup"><span data-stu-id="8fb80-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="8fb80-128">Explorando a casa Doll</span><span class="sxs-lookup"><span data-stu-id="8fb80-128">Exploring the doll house</span></span>

<span data-ttu-id="8fb80-129">A Doll House é o ambiente virtual que usamos em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8fb80-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="8fb80-130">O ambiente é uma sala em miniatura de 80 x 60 x 40 cm que contém os elementos básicos que a maioria das salas tem em comum, como paredes, lâmpadas, mobília, uma tabela e uma TV.</span><span class="sxs-lookup"><span data-stu-id="8fb80-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="8fb80-131">A Doll House é a principal protagonist da experiência do aplicativo, portanto, precisávamos garantir que ela funcionasse muito bem em qualquer ambiente.</span><span class="sxs-lookup"><span data-stu-id="8fb80-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="8fb80-132">Imagine-o como um pequeno espaço de demonstração para Visualizar todos os tipos de conceitos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8fb80-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="8fb80-133">*Vídeo do comportamento de ajuste de Dollhouse*</span><span class="sxs-lookup"><span data-stu-id="8fb80-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="8fb80-134">protótipos de 1:1 x 1:10</span><span class="sxs-lookup"><span data-stu-id="8fb80-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="8fb80-135">Nossa suposição inicial era que 1:1 demonstrações seriam incríveis, quase como examinar um professor de vida real.</span><span class="sxs-lookup"><span data-stu-id="8fb80-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="8fb80-136">O usuário veria tudo o que o professor vê em uma escala de vida real.</span><span class="sxs-lookup"><span data-stu-id="8fb80-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="8fb80-137">No entanto, percebemos imediatamente que haveria alguns problemas:</span><span class="sxs-lookup"><span data-stu-id="8fb80-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="8fb80-138">A maioria dos desenvolvedores executará seus aplicativos em escritórios ou salas menores do que a sala de demonstração e, portanto, não se ajustaria.</span><span class="sxs-lookup"><span data-stu-id="8fb80-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="8fb80-139">As exibições são aditivas, o que significa que todo o ambiente virtual será sobreposto ao espaço de um usuário.</span><span class="sxs-lookup"><span data-stu-id="8fb80-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="8fb80-140">Isso pode ficar confuso com duas tabelas, talvez duas vezes em sofás e as paredes que não se alinham.</span><span class="sxs-lookup"><span data-stu-id="8fb80-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="8fb80-141">E o pior de todo um ambiente virtual altamente restrito por um campo de exibição.</span><span class="sxs-lookup"><span data-stu-id="8fb80-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="8fb80-142">Quando tentamos uma escala de 1:10, o resultado era uma visão fantástica de uma sala realista.</span><span class="sxs-lookup"><span data-stu-id="8fb80-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="8fb80-143">Você poderia ver tudo o que estava acontecendo de qualquer ângulo ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="8fb80-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="8fb80-144">O que era mais surpreendente é que a maioria dos testadores o achava muito mais imersiva para ver uma versão pequena, então eles nunca mudaram de volta para a escala 1:1.</span><span class="sxs-lookup"><span data-stu-id="8fb80-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="8fb80-145">Então, decidimos realmente refazer a versão 1:1 e evitar o trabalho extra necessário para adaptar a interface do usuário e outros aspectos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8fb80-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="8fb80-146">![Campo de exibição com 1:1 escala ](images/designing-holograms/1-1-scale.png)
 *do campo de exibição com escala de 1:1*</span><span class="sxs-lookup"><span data-stu-id="8fb80-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="8fb80-147">![Campo de exibição com 1:10 escala ](images/designing-holograms/1-10-scale.png)
 *do campo de exibição com escala de 1:10*</span><span class="sxs-lookup"><span data-stu-id="8fb80-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="8fb80-148">Usando a captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="8fb80-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="8fb80-149">Um dos recursos mais característicos desse aplicativo é o uso da captura de realidade misturada para ensinar e demonstrar conceitos de design de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8fb80-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="8fb80-150">A Microsoft tem um estúdio de captura de realidade misturada em San Francisco.</span><span class="sxs-lookup"><span data-stu-id="8fb80-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="8fb80-151">A Microsoft também licencia essa tecnologia para outros estúdios, que incluem a dimensão de avatar em Washington D.C., metastage em Los Angeles, Dimension estúdios em Londres, SK Telecom in Seul e Volucap em Berlim.</span><span class="sxs-lookup"><span data-stu-id="8fb80-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="8fb80-152">Você pode encontrar mais informações sobre nossa [estúdios de captura de realidade misturada aqui](https://www.microsoft.com/mixed-reality/capture-studios).</span><span class="sxs-lookup"><span data-stu-id="8fb80-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="8fb80-153">*A seqüência bruta de Daniel Escudero de uma das câmeras 106 no estúdio de captura de realidade misturada em San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="8fb80-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="8fb80-154">O processo de captura gera uma malha, Normals e texturas em quadros-chave, que podem ser entregues como arquivos OBJ/PNG para posterior produção ou pronto para reprodução como um arquivo MP4 compactado H. 264.</span><span class="sxs-lookup"><span data-stu-id="8fb80-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="8fb80-155">Esses arquivos podem ser importados para projetos do Unity, inreal, nativo e WebXR.</span><span class="sxs-lookup"><span data-stu-id="8fb80-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="8fb80-156">Os arquivos podem ser executados no Windows, iOS, Mac, Android, Magic Leap e PlayStation VR.</span><span class="sxs-lookup"><span data-stu-id="8fb80-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="8fb80-157">*O player de captura fornecido para analisar MP4s que contêm vídeo com malhas de áudio e incorporadas.*</span><span class="sxs-lookup"><span data-stu-id="8fb80-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="8fb80-158">Manipulando capturas e objetos virtuais</span><span class="sxs-lookup"><span data-stu-id="8fb80-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="8fb80-159">As capturas de realidade misturadas produzem representações virtuais de pessoas ou animais, mas às vezes você pode precisar desses caracteres para interagir com outros objetos virtuais.</span><span class="sxs-lookup"><span data-stu-id="8fb80-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="8fb80-160">Os dois exemplos a seguir mostram diferentes maneiras de manipularmos as cenas para alcançar esse efeito.</span><span class="sxs-lookup"><span data-stu-id="8fb80-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="8fb80-161">Ajuste de olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="8fb80-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="8fb80-162">O ajuste Headgaze permite mover o cabeçalho de uma pessoa capturada em tempo de execução, o que significa que você pode ter uma face de captura para um usuário.</span><span class="sxs-lookup"><span data-stu-id="8fb80-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="8fb80-163">Em nosso caso, nós o usamos para mostrar o campo de exibição e campo de interesse.</span><span class="sxs-lookup"><span data-stu-id="8fb80-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="8fb80-164">O que você vê abaixo é um gameobject em movimento agindo como um destino para o olhar de cabeçalho examinar.</span><span class="sxs-lookup"><span data-stu-id="8fb80-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="8fb80-165">À medida que movemos o destino do lado a lado, o início da captura é mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="8fb80-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="8fb80-166">Usamos esse truque para garantir que a captura ociosa sempre se deparasse com os hologramas colocados em diferentes partes da casa Doll.</span><span class="sxs-lookup"><span data-stu-id="8fb80-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![A cabeça da captura está sendo movida no tempo de execução após um gameobject de destino no Unity](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="8fb80-168">*A cabeça da captura está sendo movida no tempo de execução após um gameobject de destino no Unity.*</span><span class="sxs-lookup"><span data-stu-id="8fb80-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="8fb80-169">Sincronizando objetos animados</span><span class="sxs-lookup"><span data-stu-id="8fb80-169">Syncing Animated Objects</span></span>

<span data-ttu-id="8fb80-170">A segunda, estava animando objetos para sincronizar com o movimento de uma captura.</span><span class="sxs-lookup"><span data-stu-id="8fb80-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="8fb80-171">Em diferentes partes do aplicativo, importamos objs tivessem sequenciais de uma captura específica a cada cinco quadros.</span><span class="sxs-lookup"><span data-stu-id="8fb80-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="8fb80-172">Os objs tivessem foram então animados na cena para garantir que correspondam ao quadro correspondente da captura.</span><span class="sxs-lookup"><span data-stu-id="8fb80-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="8fb80-173">É um processo entediante de animação e enquadramento, mas o resultado é ótimo.</span><span class="sxs-lookup"><span data-stu-id="8fb80-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="8fb80-174">Agora você pode ver uma interação de captura de realidade misturada com objetos não capturados.</span><span class="sxs-lookup"><span data-stu-id="8fb80-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Animação sincronizada entre uma captura de realidade misturada e o painel da interface do usuário](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="8fb80-176">*Animação sincronizada entre uma captura de realidade misturada e o painel da interface do usuário*</span><span class="sxs-lookup"><span data-stu-id="8fb80-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="8fb80-177">Processo criativo da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="8fb80-177">UI creative process</span></span>

<span data-ttu-id="8fb80-178">Quando começamos o design da interface do usuário, queríamos mostrar algumas das mágicas e possibilidades que os hologramas têm a oferecer.</span><span class="sxs-lookup"><span data-stu-id="8fb80-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="8fb80-179">Simplesmente Mostrar janelas 2D estáticas e caixas de texto não se sente bem no mundo 3D.</span><span class="sxs-lookup"><span data-stu-id="8fb80-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="8fb80-180">Muitas das possibilidades à mão simplesmente não aparecem, logo desde o início, decidimos sair dessa parte e fazer uso completo do espaço 3D Holographic.</span><span class="sxs-lookup"><span data-stu-id="8fb80-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="8fb80-181">Inicialmente, começamos com a adição de uma espessura aos painéis, ícones e informações de texto.</span><span class="sxs-lookup"><span data-stu-id="8fb80-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="8fb80-182">Ainda assim, como um usuário, o que vejo é uma caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="8fb80-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="8fb80-183">Caixas de texto com imagens, mas não estamos lá.</span><span class="sxs-lookup"><span data-stu-id="8fb80-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="8fb80-184">Além disso, usamos os sombreadores do MRTK (Kit de ferramentas de realidade misturada).</span><span class="sxs-lookup"><span data-stu-id="8fb80-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="8fb80-185">Os sombreadores MRTK se tornaram uma ferramenta poderosa e usamos seus recursos de estêncil para adicionar profundidade negativa aos painéis.</span><span class="sxs-lookup"><span data-stu-id="8fb80-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="8fb80-186">Isso significa que, em vez de adicionar elementos na frente de uma caixa de texto, os ícones agora aparecem atrás de um painel transparente.</span><span class="sxs-lookup"><span data-stu-id="8fb80-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="8fb80-187">O que vejo agora como um usuário é algo que simplesmente não posso replicar no mundo real, e é aí que começou a Holographic mágica.</span><span class="sxs-lookup"><span data-stu-id="8fb80-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="8fb80-188">Também como um usuário que eu não gosto muito de ler, eu já tenho muito no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="8fb80-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="8fb80-189">Obviamente, os ícones funcionam muito melhor do que o texto simples, para fornecer uma orientação ainda mais poderosa, comecei a criar um conjunto de objetos animados e avatars, cada um deles dizendo uma pequena história sobre o que está sendo feito no respectivo cenário e como ele está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="8fb80-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![GIF animado de um sistema de menus Holographic interativo](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="8fb80-191">Conceitos fundamentais</span><span class="sxs-lookup"><span data-stu-id="8fb80-191">Core concepts</span></span>

<span data-ttu-id="8fb80-192">**Quadro holográfico**</span><span class="sxs-lookup"><span data-stu-id="8fb80-192">**Holographic frame**</span></span>

![GIF animado de um usuário olhando o Dollhouse com o quadro Holographic realçado](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="8fb80-194">**Sistemas de coordenadas**</span><span class="sxs-lookup"><span data-stu-id="8fb80-194">**Coordinate systems**</span></span>

![GIF animado de um usuário que procura o Dollhouse com os sistemas de coordenadas realçados](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="8fb80-196">**Acompanhamento ocular**</span><span class="sxs-lookup"><span data-stu-id="8fb80-196">**Eye tracking**</span></span>

![GIF animado de um usuário olhando para hologramas fixos com o olho olhar Ray realçado](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="8fb80-198">**Visualização da verificação de sala e mapeamento espacial**</span><span class="sxs-lookup"><span data-stu-id="8fb80-198">**Room scan visualization and spatial mapping**</span></span>

![GIF animado de todas as superfícies dentro do Dollhouse que está sendo mapeado](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="8fb80-200">**Reconhecimento de cena**</span><span class="sxs-lookup"><span data-stu-id="8fb80-200">**Scene understanding**</span></span>

![GIF animado de objetos no Dollhouse que está sendo reconhecido](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="8fb80-202">**Apontar e confirmar com raios de mão**</span><span class="sxs-lookup"><span data-stu-id="8fb80-202">**Point and commit with hand rays**</span></span>

![GIF animado de um usuário levantando sua mão com um raio de mão realçado](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="8fb80-204">Tempo "Experimente"</span><span class="sxs-lookup"><span data-stu-id="8fb80-204">"Try it out" moments</span></span>

<span data-ttu-id="8fb80-205">A criação de hologramas ensina conceitos de realidade misturada, mas também permite testá-los em sua sala.</span><span class="sxs-lookup"><span data-stu-id="8fb80-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="8fb80-206">Depois de algumas dessas explicações, vamos pausar e levá-lo da casa Doll e em um momento interativo.</span><span class="sxs-lookup"><span data-stu-id="8fb80-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="8fb80-207">Aqui estão alguns exemplos desses momentos interativos:</span><span class="sxs-lookup"><span data-stu-id="8fb80-207">Here are some examples of those interactive moments:</span></span>

![GIF animado do quadro de acompanhamento à mão mostrando quando as mãos são detectadas e quando elas inserem o campo de exibição](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="8fb80-209">*O quadro de acompanhamento à mão mostrando quando as mãos são detectadas e quando elas inserem o campo de exibição.*</span><span class="sxs-lookup"><span data-stu-id="8fb80-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![GIF animado de interagir com a colisão de Crystals por meio de interação distante](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="8fb80-211">*Interagindo com a colisão de Crystals por meio de interação distante*</span><span class="sxs-lookup"><span data-stu-id="8fb80-211">*Interacting with colliding crystals through far interaction*</span></span>

![GIF animado de explorar o capacidades de interação próxima](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="8fb80-213">*Explorando capacidades de interação próxima*</span><span class="sxs-lookup"><span data-stu-id="8fb80-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="8fb80-214">Sobre a equipe</span><span class="sxs-lookup"><span data-stu-id="8fb80-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="8fb80-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="8fb80-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="8fb80-216"><i>Designer técnico líder</i></span><span class="sxs-lookup"><span data-stu-id="8fb80-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="8fb80-217">Dan é o diretor criativo da criação de hologramas e atualmente funciona como líder de design para a Academia de realidade misturada da Microsoft em São Francisco, e era um designer de uma das estúdios de realidade misturada da Microsoft em Londres.</span><span class="sxs-lookup"><span data-stu-id="8fb80-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="8fb80-218"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="8fb80-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="8fb80-219"><i>Artista 3D sênior</i></span><span class="sxs-lookup"><span data-stu-id="8fb80-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="8fb80-220">Martin lidera a arte 3D e o design da interface do usuário na criação de hologramas e era anteriormente um artista 3D sênior em um dos estúdios de realidade misturada da Microsoft em Berlim.</span><span class="sxs-lookup"><span data-stu-id="8fb80-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="8fb80-221">Um enorme agradecimento à equipe de design da realidade misturada por compartilhar tanto conhecimento e para o pessoal incrível da [teoria do objeto](https://objecttheory.com/) para ser um colega de equipe essencial em cada etapa do projeto.</span><span class="sxs-lookup"><span data-stu-id="8fb80-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="8fb80-222">Obrigado por todos os talentos incríveis, pelo entusiasmo e pelo olho excepcional para o design.</span><span class="sxs-lookup"><span data-stu-id="8fb80-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8fb80-223">Baixar o aplicativo de criação de hologramas</span><span class="sxs-lookup"><span data-stu-id="8fb80-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)