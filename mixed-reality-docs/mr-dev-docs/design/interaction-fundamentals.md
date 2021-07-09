---
title: Interações instintivas
description: Conheça a filosofia de simples interações instintivas, presentes em toda a plataforma da realidade misturada.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento de foco, interação, design, hololens, MMR, multimodal, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, HoloLens
ms.openlocfilehash: 55e23ac2fb802af599fb9cc7d771d89d6ba36c47
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196411"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="979bf-104">Apresentação de interações instintivas</span><span class="sxs-lookup"><span data-stu-id="979bf-104">Introducing instinctual interactions</span></span>

![Manipulação distante com as mãos](images/04_InteractionFundamentals.png)

<span data-ttu-id="979bf-106">A filosofia de interações simples e instintivas está presente em toda a plataforma de MR (realidade misturada).</span><span class="sxs-lookup"><span data-stu-id="979bf-106">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="979bf-107">Temos três etapas para os desenvolvedores e designers de aplicativos fornecerem interações fáceis e intuitivas para os clientes deles.</span><span class="sxs-lookup"><span data-stu-id="979bf-107">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="979bf-108">Primeiro, confirmamos que os nossos sensores e as tecnologias de entrada se combinam em modelos de interação multimodal.</span><span class="sxs-lookup"><span data-stu-id="979bf-108">First, we've made sure our sensors and input technologies combine into multimodal interaction models.</span></span> <span data-ttu-id="979bf-109">Esses modelos de interação incluem o acompanhamento ocular e de mão, juntamente com a entrada de idioma natural.</span><span class="sxs-lookup"><span data-stu-id="979bf-109">These interaction models include hand and eye tracking along with natural language input.</span></span> <span data-ttu-id="979bf-110">Com base em nossa pesquisa, projetar e desenvolver em uma estrutura multimodal (em vez de com base em entradas individuais) é o segredo para criar experiências instintivas.</span><span class="sxs-lookup"><span data-stu-id="979bf-110">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="979bf-111">Em segundo lugar, reconhecemos que muitos desenvolvedores destinam suas criações a vários dispositivos HoloLens, por exemplo, HoloLens 2 e HoloLens (1ª geração) ou então HoloLens e VR.</span><span class="sxs-lookup"><span data-stu-id="979bf-111">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span> <span data-ttu-id="979bf-112">Sendo assim, criamos nossos modelos de interação para que funcionem em vários dispositivos (mesmo que a tecnologia de entrada varie em cada dispositivo).</span><span class="sxs-lookup"><span data-stu-id="979bf-112">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span> <span data-ttu-id="979bf-113">Por exemplo, a interação à distância em um headset imersivo do Windows com um controlador 6DoF e o HoloLens 2 usam funcionalidades e padrões idênticos.</span><span class="sxs-lookup"><span data-stu-id="979bf-113">For example, far interaction on a Windows Immersive headset with a 6DoF controller and HoloLens 2 both use identical affordances and patterns.</span></span> <span data-ttu-id="979bf-114">Isso facilita o desenvolvimento de aplicativos entre dispositivos e proporciona uma sensação natural às interações do usuário.</span><span class="sxs-lookup"><span data-stu-id="979bf-114">This makes it easy for cross-device application development and provides a natural feel to user interactions.</span></span> 

<span data-ttu-id="979bf-115">Ainda que reconheçamos que há milhares de interações eficazes, envolventes e mágicas possíveis na MR, descobrimos que empregar intencionalmente um só modelo de interação em um aplicativo é a melhor maneira de garantir que os usuários sejam bem-sucedidos e tenham uma ótima experiência.</span><span class="sxs-lookup"><span data-stu-id="979bf-115">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="979bf-116">Para isso, incluímos três coisas neste guia de interação:</span><span class="sxs-lookup"><span data-stu-id="979bf-116">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="979bf-117">Diretrizes específicas sobre os três principais modelos de interação e os componentes e os padrões necessários para cada um.</span><span class="sxs-lookup"><span data-stu-id="979bf-117">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="979bf-118">Diretrizes complementares sobre os outros benefícios fornecidos por nossa plataforma.</span><span class="sxs-lookup"><span data-stu-id="979bf-118">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="979bf-119">Diretrizes gerais para ajudar a selecionar o modelo de interação apropriado para seu cenário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="979bf-119">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a><span data-ttu-id="979bf-120">Demonstração do rastreamento básico de mãos e interações instintivas</span><span class="sxs-lookup"><span data-stu-id="979bf-120">Basic hand tracking and instinctual interactions demo</span></span>

<span data-ttu-id="979bf-121">Confira abaixo nosso vídeo de demonstração do **Projetando hologramas - rastreamento da cabeça e rastreamento dos olhos** e prossiga para saber mais sobre os tópicos específicos:</span><span class="sxs-lookup"><span data-stu-id="979bf-121">Check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below, then move on to more specific topics:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="979bf-122">*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*</span><span class="sxs-lookup"><span data-stu-id="979bf-122">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="979bf-123">Modelos de interação multimodal</span><span class="sxs-lookup"><span data-stu-id="979bf-123">Multimodal interaction models</span></span>

<span data-ttu-id="979bf-124">Com base nas pesquisas e nos comentários dos clientes, descobrimos que três modelos de interação principais atendem à maioria das experiências de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="979bf-124">Based on our research and feedback from customers, we've discovered that three primary interaction models suit most mixed reality experiences.</span></span> <span data-ttu-id="979bf-125">Em muitos aspectos, o modelo de interação é o modelo mental do usuário para a maneira como concluir um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="979bf-125">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="979bf-126">Cada um desses modelos de interação é otimizado para um conjunto de necessidades do cliente e é conveniente, avançado e utilizável quando usado corretamente.</span><span class="sxs-lookup"><span data-stu-id="979bf-126">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="979bf-127">O gráfico abaixo é uma visão geral simplificada.</span><span class="sxs-lookup"><span data-stu-id="979bf-127">The chart below is a simplified overview.</span></span> <span data-ttu-id="979bf-128">Há links para informações detalhadas de uso de cada modelo de interação nas páginas abaixo com imagens e exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="979bf-128">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="979bf-129"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="979bf-129"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="979bf-130"><strong>Cenários de exemplo</strong></span><span class="sxs-lookup"><span data-stu-id="979bf-130"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="979bf-131"><strong>Ajustar</strong></span><span class="sxs-lookup"><span data-stu-id="979bf-131"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="979bf-132"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="979bf-132"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="979bf-133"><a href="hands-and-tools.md">Controladores de movimentos e mãos</a></span><span class="sxs-lookup"><span data-stu-id="979bf-133"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="979bf-134">Experiências 3D espaciais, por exemplo, design e layout espacial, manipulação de conteúdo ou simulação.</span><span class="sxs-lookup"><span data-stu-id="979bf-134">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="979bf-135">Excelente para novos usuários, juntamente com voz, acompanhamento ocular ou foco com a cabeça.</span><span class="sxs-lookup"><span data-stu-id="979bf-135">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="979bf-136">Baixa curva de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="979bf-136">Low learning curve.</span></span> <span data-ttu-id="979bf-137">Experiência do usuário consistente com acompanhamento da mão e controladores 6DoF.</span><span class="sxs-lookup"><span data-stu-id="979bf-137">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="979bf-138">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="979bf-138">HoloLens 2</span></span><br><span data-ttu-id="979bf-139">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="979bf-139">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="979bf-140"><a href="hands-free.md">Mãos livres</a></span><span class="sxs-lookup"><span data-stu-id="979bf-140"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="979bf-141">Experiências contextuais, nas quais as mãos de um usuário estão ocupadas, por exemplo, no aprendizado no trabalho e na manutenção.</span><span class="sxs-lookup"><span data-stu-id="979bf-141">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="979bf-142">Algum aprendizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="979bf-142">Some learning required.</span></span> <span data-ttu-id="979bf-143">Caso as mãos não estejam disponíveis, o dispositivo emparelha bem com voz e linguagem natural.</span><span class="sxs-lookup"><span data-stu-id="979bf-143">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="979bf-144">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="979bf-144">HoloLens 2</span></span><br><span data-ttu-id="979bf-145">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="979bf-145">HoloLens (1st gen)</span></span><br><span data-ttu-id="979bf-146">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="979bf-146">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="979bf-147"><a href="gaze-and-commit.md">Focar e confirmar</a></span><span class="sxs-lookup"><span data-stu-id="979bf-147"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="979bf-148">Experiências de clique, por exemplo, apresentações 3D, demonstrações.</span><span class="sxs-lookup"><span data-stu-id="979bf-148">Click-through experiences, for example, 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="979bf-149">Requer treinamento em HMDs, mas não em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="979bf-149">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="979bf-150">Melhor para controladores acessíveis.</span><span class="sxs-lookup"><span data-stu-id="979bf-150">Best for accessible controllers.</span></span> <span data-ttu-id="979bf-151">Melhor para HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="979bf-151">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="979bf-152">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="979bf-152">HoloLens 2</span></span><br><span data-ttu-id="979bf-153">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="979bf-153">HoloLens (1st gen)</span></span><br><span data-ttu-id="979bf-154">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="979bf-154">Immersive headsets</span></span><br><span data-ttu-id="979bf-155">AR móvel</span><span class="sxs-lookup"><span data-stu-id="979bf-155">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="979bf-156">Para evitar lacunas na experiência de interação do usuário, é melhor seguir as diretrizes para um só modelo, do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="979bf-156">To avoid gaps in the user interaction experience, it's best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="979bf-157">As seções a seguir seguem as etapas de seleção e implementação de um desses modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="979bf-157">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-youll-understand-our-guidance-on"></a><span data-ttu-id="979bf-158">No final desta página, você entenderá nossas diretrizes sobre como:</span><span class="sxs-lookup"><span data-stu-id="979bf-158">By the end of this page, you'll understand our guidance on:</span></span>
 
* <span data-ttu-id="979bf-159">Escolhendo um modelo de interação para seu cliente</span><span class="sxs-lookup"><span data-stu-id="979bf-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="979bf-160">Implementar o modelo de interação</span><span class="sxs-lookup"><span data-stu-id="979bf-160">Implementing the interaction model</span></span>
* <span data-ttu-id="979bf-161">Transição entre os modelos de interação</span><span class="sxs-lookup"><span data-stu-id="979bf-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="979bf-162">Próximas etapas de design</span><span class="sxs-lookup"><span data-stu-id="979bf-162">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="979bf-163">Escolha um modelo de interação para seu cliente</span><span class="sxs-lookup"><span data-stu-id="979bf-163">Choose an interaction model for your customer</span></span>

<span data-ttu-id="979bf-164">Na maioria dos casos, os desenvolvedores e criadores pensaram nos tipos de interações que seus clientes podem ter.</span><span class="sxs-lookup"><span data-stu-id="979bf-164">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="979bf-165">Para incentivar uma abordagem do design voltada para o cliente, é recomendável seguir as orientações abaixo para selecionar o modelo de interação que é otimizado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="979bf-165">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="979bf-166">Por que seguir esta orientação?</span><span class="sxs-lookup"><span data-stu-id="979bf-166">Why follow this guidance?</span></span>

* <span data-ttu-id="979bf-167">Testamos nossos modelos de interação com critérios objetivos e subjetivos, incluindo esforço físico e cognitivo, intuitividade e capacidade de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="979bf-167">We test our interaction models for objective and subjective criteria, including physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="979bf-168">Como as interações são diferentes, as funcionalidades de áudio/visuais e o comportamento de objeto podem ser diferentes entre os modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="979bf-168">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="979bf-169">Combinar partes de vários modelos de interação cria o risco de funcionalidades conflitantes, tais como raios de mão simultâneos e um cursor de foco com a cabeça.</span><span class="sxs-lookup"><span data-stu-id="979bf-169">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="979bf-170">Isso pode sobrecarregar e confundir os usuários.</span><span class="sxs-lookup"><span data-stu-id="979bf-170">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="979bf-171">Aqui estão alguns exemplos de como as capacidades e os comportamentos são otimizados para cada modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="979bf-171">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="979bf-172">Vemos com frequência que novos usuários têm perguntas semelhantes, como _"como faço para saber se o sistema está funcionando”_ , _“como saber o que posso fazer”_ e _“como saber se entendi o que acabei de fazer?"_</span><span class="sxs-lookup"><span data-stu-id="979bf-172">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="979bf-173"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="979bf-173"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="979bf-174"><strong>Como saber se está funcionando?</strong></span><span class="sxs-lookup"><span data-stu-id="979bf-174"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="979bf-175"><strong>Como saber o que posso fazer?</strong></span><span class="sxs-lookup"><span data-stu-id="979bf-175"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="979bf-176"><strong>Como saber o que eu acabei de fazer?</strong></span><span class="sxs-lookup"><span data-stu-id="979bf-176"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="979bf-177"><a href="hands-and-tools.md">Controladores de movimentos e mãos</a></span><span class="sxs-lookup"><span data-stu-id="979bf-177"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="979bf-178">Vejo uma malha de mão, uma funcionalidade de ponta do dedo ou raios de mão/controlador.</span><span class="sxs-lookup"><span data-stu-id="979bf-178">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="979bf-179">Vejo alças ou uma caixa delimitadora é exibida quando a minha mão está próxima de um objeto.</span><span class="sxs-lookup"><span data-stu-id="979bf-179">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="979bf-180">Posso ouvir sons e ver animações ao capturar e soltar.</span><span class="sxs-lookup"><span data-stu-id="979bf-180">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="979bf-181"><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></span><span class="sxs-lookup"><span data-stu-id="979bf-181"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="979bf-182">Eu vejo um cursor no centro do meu campo de visão.</span><span class="sxs-lookup"><span data-stu-id="979bf-182">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="979bf-183">O cursor muda de estado quando está sobre determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="979bf-183">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="979bf-184">Posso ver/ouvir confirmações visuais e audíveis quando executo uma ação.</span><span class="sxs-lookup"><span data-stu-id="979bf-184">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="979bf-185"><a href="hands-free.md">Mãos livres (foco com a cabeça e permanência)</a></span><span class="sxs-lookup"><span data-stu-id="979bf-185"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="979bf-186">Eu vejo um cursor no centro do meu campo de visão.</span><span class="sxs-lookup"><span data-stu-id="979bf-186">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="979bf-187">Vejo um indicador de progresso quando paro em um objeto com o qual posso interagir.</span><span class="sxs-lookup"><span data-stu-id="979bf-187">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="979bf-188">Posso ver/ouvir confirmações visuais e audíveis quando executo uma ação.</span><span class="sxs-lookup"><span data-stu-id="979bf-188">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="979bf-189"><a href="hands-free.md">Mãos livres (comandos de voz)</a></span><span class="sxs-lookup"><span data-stu-id="979bf-189"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="979bf-190">Vejo um indicador de escuta e legendas que mostram o que o sistema ouviu.</span><span class="sxs-lookup"><span data-stu-id="979bf-190">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="979bf-191">Obtenho prompts de voz e dicas.</span><span class="sxs-lookup"><span data-stu-id="979bf-191">I get voice prompts and hints.</span></span> <span data-ttu-id="979bf-192">Quando digo: "O que posso falar?"</span><span class="sxs-lookup"><span data-stu-id="979bf-192">When I say: "What can I say?"</span></span> <span data-ttu-id="979bf-193">Vejo feedback.</span><span class="sxs-lookup"><span data-stu-id="979bf-193">I see feedback.</span></span></td>
        <td><span data-ttu-id="979bf-194">Vejo/ouço confirmações visuais e auditivas quando emito um comando ou obtenho uma experiência de usuário de desambiguação quando necessário.</span><span class="sxs-lookup"><span data-stu-id="979bf-194">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="979bf-195">Veja as perguntas que descobrimos que ajudam as equipes e selecionar um modelo de interação:</span><span class="sxs-lookup"><span data-stu-id="979bf-195">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="979bf-196">P:  Meus usuários desejam tocar em hologramas e executar manipulações holográficas de precisão?</span><span class="sxs-lookup"><span data-stu-id="979bf-196">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="979bf-197">R:  Nesse caso, confira o modelo de interação de mãos e controladores de movimentos para direcionamento de precisão e manipulação.</span><span class="sxs-lookup"><span data-stu-id="979bf-197">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="979bf-198">P:  Meus usuários precisam manter as mãos livres para tarefas do mundo real?</span><span class="sxs-lookup"><span data-stu-id="979bf-198">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="979bf-199">R:  Nesse caso, examine o modelo de interação de mãos livres, que fornece uma ótima experiência de mãos livres por meio de interações de movimento e voz.</span><span class="sxs-lookup"><span data-stu-id="979bf-199">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="979bf-200">P:  Meus usuários têm tempo para aprender as interações de meu aplicativo de realidade misturada ou precisam das interações com a curva de aprendizado mais baixa possível?</span><span class="sxs-lookup"><span data-stu-id="979bf-200">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="979bf-201">R:  Para a mais baixa curva de aprendizado e as interações mais intuitivas, recomendamos o modelo de mãos e controladores de movimentos, desde que os usuários possam usar as mãos para interação.</span><span class="sxs-lookup"><span data-stu-id="979bf-201">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users can use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="979bf-202">P:  Meus usuários usam controladores de movimento para apontar e manipular?</span><span class="sxs-lookup"><span data-stu-id="979bf-202">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="979bf-203">R:  O modelo de mãos e de controladores de movimentos inclui todas as orientações para uma ótima experiência com os controladores de movimentos.</span><span class="sxs-lookup"><span data-stu-id="979bf-203">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="979bf-204">P:  Meus usuários usam um controlador de acessibilidade ou um controlador de Bluetooth comum, como um clicker?</span><span class="sxs-lookup"><span data-stu-id="979bf-204">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="979bf-205">R:  Recomendamos o modelo de foco com a cabeça e de confirmação para todos os controladores não acompanhados.</span><span class="sxs-lookup"><span data-stu-id="979bf-205">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="979bf-206">Ele foi projetado para permitir que um usuário passe por uma experiência completa com um mecanismo simples de "direcionar e confirmar".</span><span class="sxs-lookup"><span data-stu-id="979bf-206">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="979bf-207">P: Meus usuários progridem por uma experiência somente "clicando" (por exemplo em um ambiente de apresentação de slides 3D), em vez de navegar por layouts densos de controles de interface de usuário?</span><span class="sxs-lookup"><span data-stu-id="979bf-207">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="979bf-208">R:  Caso os usuários não precisem controlar muitos aspectos da interface do usuário, o foco com a cabeça e a confirmação oferecem uma opção que pode ser aprendida, na qual os usuários não precisam se preocupar com o direcionamento.</span><span class="sxs-lookup"><span data-stu-id="979bf-208">A:  If users don't need to control a lot of UI, Head-gaze and commit offers a learnable option where users don't have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="979bf-209">P:  Meus usuários usam o HoloLens (1ª geração) e HoloLens 2/headsets imersivos do Windows Mixed Reality (VR)?</span><span class="sxs-lookup"><span data-stu-id="979bf-209">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="979bf-210">R:  Como o foco com a cabeça e a confirmação é o modelo de interação do HoloLens (1ª geração), recomendamos que os criadores que dão suporte ao HoloLens (1ª geração) usem o foco com a cabeça e a confirmação para os recursos ou os modos que os usuários experimentarão em um headset do HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="979bf-210">A:  Since Head-gaze and commit are the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="979bf-211">Confira a próxima seção sobre *Transição de modelos de interação* para obter detalhes sobre como ter uma ótima experiência em várias gerações do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="979bf-211">See the next section on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="979bf-212">P: E quanto aos usuários que usam dispositivos móveis, que abrangem um espaço amplo ou a movimentação entre espaços, em relação aos usuários que tendem a trabalhar em um só espaço?</span><span class="sxs-lookup"><span data-stu-id="979bf-212">Q: What about users who are mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="979bf-213">R:  Qualquer um dos modelos de interação funcionará para esses usuários.</span><span class="sxs-lookup"><span data-stu-id="979bf-213">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="979bf-214">Mais diretrizes específicas ao design de aplicativo [em breve](../out-of-scope/news.md).</span><span class="sxs-lookup"><span data-stu-id="979bf-214">More guidance specific to app design [coming soon](../out-of-scope/news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="979bf-215">Modelos de interação de transição</span><span class="sxs-lookup"><span data-stu-id="979bf-215">Transitioning interaction models</span></span>
<span data-ttu-id="979bf-216">Também há casos de uso que podem exigir o uso de mais de um modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="979bf-216">There are also use cases that might require using more than one interaction model.</span></span> <span data-ttu-id="979bf-217">Por exemplo, o fluxo de criação do seu aplicativo usa o modelo de interação de _"mãos e controladores de movimentos"_ , mas o ideal é empregar um modo de mãos livres para técnicos de campo.</span><span class="sxs-lookup"><span data-stu-id="979bf-217">For example, your application's creation flow uses the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span> <span data-ttu-id="979bf-218">Se a sua experiência exigir vários modelos de interação, os usuários poderão ter dificuldade em fazer a transição de um modelo para outro, especialmente quando estiverem se familiarizando com a Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="979bf-218">If your experience does require multiple interaction models, users might have difficulty transitioning from one model to another, especially when they're new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="979bf-219">Estamos trabalhando constantemente em mais diretrizes que estarão disponíveis para desenvolvedores e designers, informando-os sobre como, quando e por que usar vários modelos de interação de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="979bf-219">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="979bf-220">Veja também</span><span class="sxs-lookup"><span data-stu-id="979bf-220">See also</span></span>
* [<span data-ttu-id="979bf-221">Conforto</span><span class="sxs-lookup"><span data-stu-id="979bf-221">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="979bf-222">Interação ocular</span><span class="sxs-lookup"><span data-stu-id="979bf-222">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="979bf-223">Acompanhamento ocular no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="979bf-223">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="979bf-224">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="979bf-224">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="979bf-225">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="979bf-225">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="979bf-226">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="979bf-226">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="979bf-227">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="979bf-227">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="979bf-228">Mãos – Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="979bf-228">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="979bf-229">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="979bf-229">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="979bf-230">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="979bf-230">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="979bf-231">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="979bf-231">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="979bf-232">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="979bf-232">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="979bf-233">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="979bf-233">Voice input</span></span>](voice-input.md)


