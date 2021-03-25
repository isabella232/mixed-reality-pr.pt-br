---
title: Desenvolvimento do Unity para VR
description: Introdução à criação de aplicativos de realidade misturada no Unity para headsets imersivos de VR e do Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realidade misturada, desenvolvimento, introdução, novo projeto, portabilidade, funcionalidade, câmera, simulação, emulação, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, o que é realidade virtual, o que é realidade aumentada, MRTK, kit de ferramentas de realidade misturada, entrada de voz, câmera localizável, emulador, Azure, tutoriais
ms.openlocfilehash: e80c5411c7d180e0d78e031599455235dabaceb7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237137"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="b07f1-104">Desenvolvimento do Unity para VR e Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b07f1-104">Unity development for VR and Windows Mixed Reality</span></span>

![Logotipo do banner do Unity](../images/unity_logo_banner.png)

<span data-ttu-id="b07f1-106">Se você não tem familiaridade com o Unity, recomendamos explorar os [tutoriais](https://unity3d.com/learn/tutorials) de nível iniciante na plataforma Unity Learn antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b07f1-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="b07f1-107">Também é uma boa ideia acessar [fóruns de Realidade Misturada do Unity](https://forum.unity3d.com/forums/hololens.102/) para interagir com a comunidade online que cria aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b07f1-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="b07f1-108">Você nunca sabe quais recursos ou soluções interessantes pode encontrar por aí.</span><span class="sxs-lookup"><span data-stu-id="b07f1-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="b07f1-109">Quando você estiver pronto para começar a usar o MRTK, vá para os pontos de verificação de desenvolvimento abaixo!</span><span class="sxs-lookup"><span data-stu-id="b07f1-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b07f1-110">Se você já tem um projeto Unity que deseja mover para o headset imersivo do Windows Mixed Reality, confira nossos **[guias de portabilidade](../porting-apps/porting-overview.md)** .</span><span class="sxs-lookup"><span data-stu-id="b07f1-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="b07f1-111">Pontos de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="b07f1-111">Development checkpoints</span></span>

<span data-ttu-id="b07f1-112">Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unity para o mundo da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b07f1-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="b07f1-113">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="b07f1-113">1. Getting started</span></span>

<span data-ttu-id="b07f1-114">Há um pequeno conjunto de configurações do Unity que você precisará alterar manualmente para o desenvolvimento do Windows Mixed Reality e da VR.</span><span class="sxs-lookup"><span data-stu-id="b07f1-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR development.</span></span> <span data-ttu-id="b07f1-115">Elas são divididas em duas categorias: por projeto e por cena.</span><span class="sxs-lookup"><span data-stu-id="b07f1-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="b07f1-116">No final desta seção, você terá as ferramentas e as configurações do projeto para começar a criar os próprios aplicativos!</span><span class="sxs-lookup"><span data-stu-id="b07f1-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="b07f1-117">Ponto de verificação</span><span class="sxs-lookup"><span data-stu-id="b07f1-117">Checkpoint</span></span>  |  <span data-ttu-id="b07f1-118">Resultado</span><span class="sxs-lookup"><span data-stu-id="b07f1-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="b07f1-119">Instale as ferramentas mais recentes</span><span class="sxs-lookup"><span data-stu-id="b07f1-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="b07f1-120">Baixe e instale o pacote mais recente do Unity e configure seu projeto para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="b07f1-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="b07f1-121">Como configurar seu projeto para o WMR</span><span class="sxs-lookup"><span data-stu-id="b07f1-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="b07f1-122">Saiba como criar aplicativos que renderizam conteúdo digital em dispositivos de vídeo holográficos e VR</span><span class="sxs-lookup"><span data-stu-id="b07f1-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="b07f1-123">2. Blocos principais de construção</span><span class="sxs-lookup"><span data-stu-id="b07f1-123">2. Core building blocks</span></span>

<span data-ttu-id="b07f1-124">Depois de iniciar um novo projeto de imersão, você precisará de alguns blocos de construção básicos para desenvolver aplicativos de imersão.</span><span class="sxs-lookup"><span data-stu-id="b07f1-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="b07f1-125">Todos os principais blocos de construção para aplicativos de realidade misturada são expostos de maneira consistente com outras APIs do Unity.</span><span class="sxs-lookup"><span data-stu-id="b07f1-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="b07f1-126">Talvez você não precise de todos eles de uma vez, mas recomendamos explorá-los logo no início.</span><span class="sxs-lookup"><span data-stu-id="b07f1-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="b07f1-127">Depois de aprofundar-se nos principais blocos de construção listados abaixo, você terá uma caixa de ferramentas cheia de recursos que pode integrar ao seu projeto de VR.</span><span class="sxs-lookup"><span data-stu-id="b07f1-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="b07f1-128">3. Recursos avançados</span><span class="sxs-lookup"><span data-stu-id="b07f1-128">3. Advanced features</span></span>

<span data-ttu-id="b07f1-129">Outros recursos importantes que desempenham uma função em aplicativos de imersão estão disponíveis por meio das APIs do Unity sem nenhum pacote ou configuração extra.</span><span class="sxs-lookup"><span data-stu-id="b07f1-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="b07f1-130">Depois de se aprofundar nas funcionalidades mais avançadas que o Unity oferece, você conseguirá criar aplicativos de VR complexos e mais avançados.</span><span class="sxs-lookup"><span data-stu-id="b07f1-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="b07f1-131">Recurso</span><span class="sxs-lookup"><span data-stu-id="b07f1-131">Feature</span></span>  |  <span data-ttu-id="b07f1-132">Funcionalidades</span><span class="sxs-lookup"><span data-stu-id="b07f1-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="b07f1-133">Controle de perda</span><span class="sxs-lookup"><span data-stu-id="b07f1-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="b07f1-134">Lide com cenários em que seu dispositivo não consegue se localizar no espaço mundial dos aplicativos</span><span class="sxs-lookup"><span data-stu-id="b07f1-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="b07f1-135">Entrada por teclado</span><span class="sxs-lookup"><span data-stu-id="b07f1-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="b07f1-136">Obtenha informações de teclados do mundo real e de Realidade Misturada em seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="b07f1-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="b07f1-137">4. Como implantar em um dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="b07f1-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="b07f1-138">Depois que o projeto holográfico do Unity estiver pronto para teste, a próxima etapa será exportar e criar uma solução do Unity para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b07f1-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="b07f1-139">Com essa solução do VS em mãos, você pode executar seu aplicativo em dispositivos reais ou simulados.</span><span class="sxs-lookup"><span data-stu-id="b07f1-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="b07f1-140">Ao final desta seção, você conseguirá implantar seu aplicativo em um dispositivo ou emulador que atenda às suas necessidades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="b07f1-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="b07f1-141">Headset imersivo do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b07f1-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="b07f1-142">Simulador de headset imersivo do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b07f1-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="b07f1-143">E agora?</span><span class="sxs-lookup"><span data-stu-id="b07f1-143">What's next?</span></span>

<span data-ttu-id="b07f1-144">O trabalho dos desenvolvedores nunca termina, especialmente ao aprender uma nova ferramenta ou um SDK.</span><span class="sxs-lookup"><span data-stu-id="b07f1-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="b07f1-145">As seções a seguir podem levar você para áreas que vão além do material de nível iniciante já concluído, juntamente com recursos úteis caso você não consiga avançar.</span><span class="sxs-lookup"><span data-stu-id="b07f1-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="b07f1-146">Estes tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para explorá-los!</span><span class="sxs-lookup"><span data-stu-id="b07f1-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="b07f1-147">Portabilidade</span><span class="sxs-lookup"><span data-stu-id="b07f1-147">Porting</span></span>

<span data-ttu-id="b07f1-148">Se você tem aplicativos que gostaria de transferir, os artigos listados abaixo são sua próxima parada:</span><span class="sxs-lookup"><span data-stu-id="b07f1-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="b07f1-149">Portabilidade dos aplicativos de VR para o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b07f1-149">Porting VR apps to Windows Mixed Reality</span></span>](../porting-apps/porting-guides.md?tabs=project)
* [<span data-ttu-id="b07f1-150">Como atualizar aplicativos SteamVR para o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b07f1-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a><span data-ttu-id="b07f1-151">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b07f1-151">Additional resources</span></span>

<span data-ttu-id="b07f1-152">Antes de entrar no mundo da realidade misturada por conta própria, recomendamos dar uma olhada na documentação extra abaixo.</span><span class="sxs-lookup"><span data-stu-id="b07f1-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="b07f1-153">Guia do entusiasta de VR</span><span class="sxs-lookup"><span data-stu-id="b07f1-153">VR enthusiast guide</span></span>](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="b07f1-154">Repositório de Ativos do Unity</span><span class="sxs-lookup"><span data-stu-id="b07f1-154">Unity Asset Store</span></span>](https://assetstore.unity.com)

## <a name="see-also"></a><span data-ttu-id="b07f1-155">Confira também</span><span class="sxs-lookup"><span data-stu-id="b07f1-155">See also</span></span> 

* [<span data-ttu-id="b07f1-156">Configurações recomendadas do Unity</span><span class="sxs-lookup"><span data-stu-id="b07f1-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="b07f1-157">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="b07f1-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="b07f1-158">Como exportar e criar uma solução do Visual Studio do Unity</span><span class="sxs-lookup"><span data-stu-id="b07f1-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="b07f1-159">Melhores práticas para trabalhar com o Unity e o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b07f1-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)