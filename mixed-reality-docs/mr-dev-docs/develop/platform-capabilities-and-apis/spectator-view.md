---
title: Modo de exibição Espectador
description: Visualize hologramas em um dispositivo externo para mostrar ou gravar uma experiência de realidade misturada em uma tela externa.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Modo de exibição Espectador, iPhone, iOS, iPad, OpenCV, câmera, ARKit, HoloLens, realidade misturada, MixedRealityToolkit, demonstração, gravar
ms.openlocfilehash: c344edea9b499bdff15d1d93e400b8be626a63b6
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530106"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="37cdd-104">Modo de exibição Espectador para o HoloLens e o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="37cdd-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="37cdd-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="37cdd-106">Overview</span></span>

<span data-ttu-id="37cdd-107">Quando você estiver usando um HoloLens, é fácil esquecer que uma pessoa que não o está usando possa ver as mesmas maravilhas que você.</span><span class="sxs-lookup"><span data-stu-id="37cdd-107">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="37cdd-108">O modo de exibição Espectador permite que outras pessoas vejam o que um usuário do HoloLens vê em uma tela 2D.</span><span class="sxs-lookup"><span data-stu-id="37cdd-108">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="37cdd-109">Também é uma abordagem rápida e acessível para a gravação de hologramas em HD com dispositivos móveis e a obtenção de gravações de ótima qualidade de hologramas com câmeras de vídeo.</span><span class="sxs-lookup"><span data-stu-id="37cdd-109">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="37cdd-110">Principais recursos</span><span class="sxs-lookup"><span data-stu-id="37cdd-110">Key Resources</span></span>

* [<span data-ttu-id="37cdd-111">**Modo de exibição Espectador no GitHub**</span><span class="sxs-lookup"><span data-stu-id="37cdd-111">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="37cdd-112">**Documentação do Modo de exibição Espectador**</span><span class="sxs-lookup"><span data-stu-id="37cdd-112">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="37cdd-113">**Amostras do Modo de exibição Espectador**</span><span class="sxs-lookup"><span data-stu-id="37cdd-113">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="37cdd-114">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="37cdd-114">Use Cases</span></span>

* <span data-ttu-id="37cdd-115">Você pode gravar uma experiência de realidade misturada usando um dispositivo iPhone ou Android.</span><span class="sxs-lookup"><span data-stu-id="37cdd-115">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="37cdd-116">Grave em full HD e aplique suavização a hologramas e sombra para ter uma forma econômica e rápida de capturar vídeo de hologramas.</span><span class="sxs-lookup"><span data-stu-id="37cdd-116">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="37cdd-117">Transmita experiências de realidade misturada ao vivo para uma Apple TV diretamente no iPhone ou no iPad, sem retardos.</span><span class="sxs-lookup"><span data-stu-id="37cdd-117">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="37cdd-118">Compartilhe a experiência com seus convidados: Permita que os usuários que não sejam do HoloLens experimentem os hologramas diretamente em seus respectivos telefones ou tablets.</span><span class="sxs-lookup"><span data-stu-id="37cdd-118">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="37cdd-119">Recursos atuais</span><span class="sxs-lookup"><span data-stu-id="37cdd-119">Current Features</span></span>

* <span data-ttu-id="37cdd-120">Sincronização espacial de hologramas, de modo que todos vejam os hologramas exatamente no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="37cdd-120">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="37cdd-121">Suporte para iOS (dispositivos habilitados para ARKit) e Android (dispositivos habilitados para ARCore).</span><span class="sxs-lookup"><span data-stu-id="37cdd-121">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="37cdd-122">Vários convidados do iOS.</span><span class="sxs-lookup"><span data-stu-id="37cdd-122">Multiple iOS guests.</span></span>
<span data-ttu-id="37cdd-123">Gravação de vídeo + hologramas + som ambiente + som de holograma.</span><span class="sxs-lookup"><span data-stu-id="37cdd-123">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="37cdd-124">Compartilhe a planilha para salvar um vídeo, enviá-lo por email ou compartilhá-lo com outros aplicativos de suporte.</span><span class="sxs-lookup"><span data-stu-id="37cdd-124">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="37cdd-125">![Marcador](images/SpecViewPhoneDemo.jpg)
![Marcador](images/hololensspectatorview-500px.jpg) ![Marcador](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="37cdd-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="37cdd-126">A tabela a seguir mostra diferentes funcionalidades do Modo de exibição Espectador e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="37cdd-126">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="37cdd-127">Escolha a opção que melhor se adapte às suas necessidades de gravação de vídeo:</span><span class="sxs-lookup"><span data-stu-id="37cdd-127">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="37cdd-128">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="37cdd-128">Functionality</span></span>                                | <span data-ttu-id="37cdd-129">Móvel</span><span class="sxs-lookup"><span data-stu-id="37cdd-129">Mobile</span></span>                  |                    <span data-ttu-id="37cdd-130">Câmera de vídeo</span><span class="sxs-lookup"><span data-stu-id="37cdd-130">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="37cdd-131">Qualidade de HD</span><span class="sxs-lookup"><span data-stu-id="37cdd-131">HD quality</span></span>                           |         <span data-ttu-id="37cdd-132">Full HD</span><span class="sxs-lookup"><span data-stu-id="37cdd-132">Full HD</span></span>         |        <span data-ttu-id="37cdd-133">Filmagem de qualidade profissional (conforme determinado pela câmera de vídeo)</span><span class="sxs-lookup"><span data-stu-id="37cdd-133">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="37cdd-134">Fácil movimento da câmera</span><span class="sxs-lookup"><span data-stu-id="37cdd-134">Easy camera movement</span></span>                 |            <span data-ttu-id="37cdd-135">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-135">✔</span></span>            |                      <span data-ttu-id="37cdd-136">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-136">✔</span></span>                      |
| <span data-ttu-id="37cdd-137">Exibição de terceira pessoa</span><span class="sxs-lookup"><span data-stu-id="37cdd-137">Third-person view</span></span>                    |            <span data-ttu-id="37cdd-138">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-138">✔</span></span>            |                      <span data-ttu-id="37cdd-139">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-139">✔</span></span>                      |
| <span data-ttu-id="37cdd-140">Pode ser transmitido para telas</span><span class="sxs-lookup"><span data-stu-id="37cdd-140">Can be streamed to screens</span></span>           |            <span data-ttu-id="37cdd-141">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-141">✔</span></span>            |                      <span data-ttu-id="37cdd-142">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-142">✔</span></span>                      |
| <span data-ttu-id="37cdd-143">Portáteis</span><span class="sxs-lookup"><span data-stu-id="37cdd-143">Portable</span></span>                             |            <span data-ttu-id="37cdd-144">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-144">✔</span></span>            |                                             |
| <span data-ttu-id="37cdd-145">Sem fio</span><span class="sxs-lookup"><span data-stu-id="37cdd-145">Wireless</span></span>                             |            <span data-ttu-id="37cdd-146">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-146">✔</span></span>            |                                             |
| <span data-ttu-id="37cdd-147">Hardware adicional necessário</span><span class="sxs-lookup"><span data-stu-id="37cdd-147">Additional required hardware</span></span>         |     <span data-ttu-id="37cdd-148">Telefone Android, iPhone</span><span class="sxs-lookup"><span data-stu-id="37cdd-148">Android phone, iPhone</span></span>    | <span data-ttu-id="37cdd-149">HoloLens + simulador + tripé + câmera de vídeo + computador + Unity</span><span class="sxs-lookup"><span data-stu-id="37cdd-149">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="37cdd-150">Investimento de hardware</span><span class="sxs-lookup"><span data-stu-id="37cdd-150">Hardware investment</span></span>                  |           <span data-ttu-id="37cdd-151">Baixo</span><span class="sxs-lookup"><span data-stu-id="37cdd-151">Low</span></span>            |                     <span data-ttu-id="37cdd-152">Alto</span><span class="sxs-lookup"><span data-stu-id="37cdd-152">High</span></span>                    |
| <span data-ttu-id="37cdd-153">Plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="37cdd-153">Cross-platform</span></span>                       |           <span data-ttu-id="37cdd-154">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="37cdd-154">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="37cdd-155">Conteúdo sincronizado</span><span class="sxs-lookup"><span data-stu-id="37cdd-155">Synchronized content</span></span>                 |            <span data-ttu-id="37cdd-156">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-156">✔</span></span>            |                      <span data-ttu-id="37cdd-157">✔</span><span class="sxs-lookup"><span data-stu-id="37cdd-157">✔</span></span>                      |
| <span data-ttu-id="37cdd-158">Duração da instalação de runtime</span><span class="sxs-lookup"><span data-stu-id="37cdd-158">Runtime setup duration</span></span>               |         <span data-ttu-id="37cdd-159">Instantâneo</span><span class="sxs-lookup"><span data-stu-id="37cdd-159">Instant</span></span>          |                     <span data-ttu-id="37cdd-160">Lento</span><span class="sxs-lookup"><span data-stu-id="37cdd-160">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="37cdd-161">Confira também</span><span class="sxs-lookup"><span data-stu-id="37cdd-161">See also</span></span>

* [<span data-ttu-id="37cdd-162">Captura de realidade mista</span><span class="sxs-lookup"><span data-stu-id="37cdd-162">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="37cdd-163">Captura de realidade misturada para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="37cdd-163">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="37cdd-164">Experiências compartilhadas em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="37cdd-164">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
