---
title: Usando o WebVR com o Windows Mixed Reality
description: Aprenda as noções básicas do WebVR, como usá-lo com o Microsoft Edge em headsets de realidade mista do Windows e problemas comuns de solução de problemas.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, WebVR, Edge, Microsoft Edge, navegação na Web
ms.openlocfilehash: 89d9e51bf4adb63e7836968a0112849f7ac403d0
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581750"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="c4dd6-104">Usando o WebVR com o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c4dd6-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT]
><span data-ttu-id="c4dd6-105">A maioria dos navegadores da Web modernos preteriu o suporte de WebVR em favor do WebXR, o novo padrão para a criação de experiências de imersão da Web para headsets de VR.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="c4dd6-106">Instale [o novo Microsoft Edge](using-microsoft-edge.md) para obter suporte ao WebXR.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="c4dd6-107">O que é o WebVR?</span><span class="sxs-lookup"><span data-stu-id="c4dd6-107">What is WebVR</span></span>

<span data-ttu-id="c4dd6-108">[WebVR](https://webvr.info) é uma especificação aberta que permite que você experimente o VR diretamente de um navegador.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-108">[WebVR](https://webvr.info) is an open specification that lets you experience VR right from a browser.</span></span> <span data-ttu-id="c4dd6-109">Se um site implementar o suporte a WebVR e fornecer conteúdo 3D, ele poderá exibir conteúdo de imersão no headset, com consentimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="c4dd6-110">Qual é a diferença entre WebVR e navegação na Web em VR</span><span class="sxs-lookup"><span data-stu-id="c4dd6-110">What is the difference between WebVR and browsing the web in VR</span></span>

<span data-ttu-id="c4dd6-111">WebVR é uma tecnologia que permite que um autor de site adicione a funcionalidade VR a uma página.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="c4dd6-112">A API WebVR é usada por uma página para exibir conteúdo 3D (como vídeo de 360 graus, ou um modelo 3D ou um jogo 3D) para todo o headset.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-112">The WebVR API is used by a page to display 3D content (such as 360-degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="c4dd6-113">**Exemplo:** Exibindo um vídeo 360 em [CNN.com/VR](http://cnn.com/vr).</span><span class="sxs-lookup"><span data-stu-id="c4dd6-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="c4dd6-114">Se uma página der suporte a WebVR, ela adicionará um botão ou outro elemento de interface do usuário que você pode selecionar para inserir VR.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-114">If a page supports WebVR, it will add a button or other UI element that you can select to enter VR.</span></span>

<span data-ttu-id="c4dd6-115">Navegar na Web em VR significa usar o navegador Edge enquanto você está aproveitando o headset, como um Tablet de aplicativo 2D dentro do Cliffhouse.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-115">Browsing the web in VR means using the Edge browser while you're wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="c4dd6-116">Todos os sites dão suporte a WebVR</span><span class="sxs-lookup"><span data-stu-id="c4dd6-116">Do all websites support WebVR</span></span>

<span data-ttu-id="c4dd6-117">Não.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-117">No.</span></span> <span data-ttu-id="c4dd6-118">Os autores de sites devem optar por usar o WebVR e podem criar sites otimizados para navegadores, headsets e controladores específicos.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-118">Website authors must opt in to use WebVR and they may create optimized sites for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="c4dd6-119">Alguns conteúdos de WebVR são otimizados somente para dispositivos móveis VR.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-119">Some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="c4dd6-120">Além disso, tenha em mente que os sites precisam criar e fornecer conteúdo de WebVR explicitamente.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="c4dd6-121">O número de sites que têm algum conteúdo compatível com WebVR está crescendo todos os dias.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="c4dd6-122">Posso usar meu Naopak/oculus, etc. para exibir o conteúdo do WebVR no Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="c4dd6-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge</span></span>

<span data-ttu-id="c4dd6-123">Não.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-123">No.</span></span> <span data-ttu-id="c4dd6-124">Um headset de realidade mista do Windows é necessário para usar o WebVR no Edge.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-124">A Windows Mixed Reality headset is required to use WebVR in Edge.</span></span> <span data-ttu-id="c4dd6-125">No entanto, você pode acessar o conteúdo do WebVR em outro navegador; consulte a lista completa de dispositivos e navegadores compatíveis em: [WebVR. Rocks](http://webvr.rocks/).</span><span class="sxs-lookup"><span data-stu-id="c4dd6-125">However, you can access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="c4dd6-126">Onde posso encontrar a documentação do desenvolvedor do WebVR</span><span class="sxs-lookup"><span data-stu-id="c4dd6-126">Where can I find the WebVR developer documentation</span></span>

<span data-ttu-id="c4dd6-127">A documentação do desenvolvedor está localizada aqui: [documentação do desenvolvedor do WebVR](/microsoft-edge/webvr/).</span><span class="sxs-lookup"><span data-stu-id="c4dd6-127">The developer documentation is located here: [WebVR Developer Documentation](/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="c4dd6-128">Encontrei um site com WebVR que não funciona na realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="c4dd6-129">O que faço</span><span class="sxs-lookup"><span data-stu-id="c4dd6-129">What do I do</span></span>

<span data-ttu-id="c4dd6-130">Você pode relatar sites desfeitos diretamente à equipe do navegador Microsoft Edge no [Issue Tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)ou por meio do twitter usando [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span><span class="sxs-lookup"><span data-stu-id="c4dd6-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="c4dd6-131">Você também pode registrar bugs usando o aplicativo Hub de comentários do Windows em Categoria:</span><span class="sxs-lookup"><span data-stu-id="c4dd6-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="c4dd6-132">Microsoft Edge-problemas de > do site</span><span class="sxs-lookup"><span data-stu-id="c4dd6-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="c4dd6-133">O que é uma boa página para testar se o WebVR está funcionando</span><span class="sxs-lookup"><span data-stu-id="c4dd6-133">What is a good page to test if WebVR is working</span></span>

<span data-ttu-id="c4dd6-134">Consulte [exemplos de webvr.info](http://webvr.info/samples/XX-vr-controllers.html).</span><span class="sxs-lookup"><span data-stu-id="c4dd6-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="c4dd6-135">Como fazer configurar o WebVR</span><span class="sxs-lookup"><span data-stu-id="c4dd6-135">How do I set up WebVR</span></span>

<span data-ttu-id="c4dd6-136">Para experimentar o conteúdo do WebVR em um headset de realidade mista do Windows (usando hardware ou simulação), você deve:</span><span class="sxs-lookup"><span data-stu-id="c4dd6-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation), you must:</span></span>

1. <span data-ttu-id="c4dd6-137">Verifique se o headset está conectado.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="c4dd6-138">Inicie o Microsoft Edge, seja na área de trabalho ou na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="c4dd6-139">Navegue até uma página habilitada para WebVR.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="c4dd6-140">Selecione o botão Inserir VR dentro da página (o local e a representação visual desse botão podem variar por site).</span><span class="sxs-lookup"><span data-stu-id="c4dd6-140">Select the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="c4dd6-141">Pode ser semelhante a: </span><span class="sxs-lookup"><span data-stu-id="c4dd6-141">It may look similar to:</span></span>\
   ![Imagem Goggles VR](images/75px-enter-vr.png)
5. <span data-ttu-id="c4dd6-143">Na primeira vez que você tentar inserir VR em um domínio específico, o navegador pedirá consentimento para usar a exibição de imersão, selecione Sim:</span><span class="sxs-lookup"><span data-stu-id="c4dd6-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, select yes:</span></span> ![IU de consentimento que é exibida na primeira tentativa de inserir VR em um domínio específico](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="c4dd6-145">O headset deve começar a exibir o conteúdo do WebVR.</span><span class="sxs-lookup"><span data-stu-id="c4dd6-145">Your headset should begin displaying the WebVR content.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4dd6-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4dd6-146">See also</span></span>

* [<span data-ttu-id="c4dd6-147">Solução de problemas > WebVR</span><span class="sxs-lookup"><span data-stu-id="c4dd6-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="c4dd6-148">Como entrar em sua primeira experiência de WebVR</span><span class="sxs-lookup"><span data-stu-id="c4dd6-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="c4dd6-149">Usando jogos e aplicativos no Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c4dd6-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="c4dd6-150">Sua base de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c4dd6-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="c4dd6-151">Sistema de controle</span><span class="sxs-lookup"><span data-stu-id="c4dd6-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="c4dd6-152">Controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="c4dd6-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="c4dd6-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="c4dd6-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="c4dd6-154">Comentários de arquivamento</span><span class="sxs-lookup"><span data-stu-id="c4dd6-154">Filing feedback</span></span>](filing-feedback.md)