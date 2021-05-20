---
title: Visualização de varredura do ambiente
description: Aplicativos que exigem mapeamento espacial usam o dispositivo para coletar dados ao longo do tempo e entre sessões.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, padrões de aplicativo, design, HoloLens, verificação de sala, mapeamento espacial, malha, headset de realidade misturada, headset de realidade misturada do Windows, headset da realidade virtual, HoloLens
ms.openlocfilehash: 87312a5d5361ac0e8c24a622cf69fe3e9b147ff5
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196401"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="60e30-104">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="60e30-104">Room scan visualization</span></span>

<span data-ttu-id="60e30-105">Os aplicativos que exigem mapeamento espacial dependem do dispositivo para coletar dados ao longo do tempo e entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="60e30-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="60e30-106">A integridade e a qualidade dos dados de mapeamento dependem de muitos fatores, incluindo a quantidade de explorações que o usuário fez, quanto tempo passou desde a exploração e se objetos como mobília e portas foram movidos desde que o dispositivo examinou a área.</span><span class="sxs-lookup"><span data-stu-id="60e30-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="60e30-107">Para garantir dados de mapeamento espacial úteis, os desenvolvedores de aplicativos têm várias opções:</span><span class="sxs-lookup"><span data-stu-id="60e30-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="60e30-108">Conte com o que já pode ter sido coletado.</span><span class="sxs-lookup"><span data-stu-id="60e30-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="60e30-109">Esses dados podem estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="60e30-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="60e30-110">Peça ao usuário para usar o gesto de cair para chegar à página inicial do Windows Mixed Reality e, em seguida, explorar a área que desejam usar para a experiência.</span><span class="sxs-lookup"><span data-stu-id="60e30-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="60e30-111">Eles podem usar o Air-TAP para confirmar se toda a área necessária é conhecida pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60e30-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="60e30-112">Crie uma experiência de exploração personalizada em seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60e30-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="60e30-113">Em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso.</span><span class="sxs-lookup"><span data-stu-id="60e30-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="60e30-114">Se você quiser ver a visualização da verificação de sala em ação, Confira nossa demonstração de vídeo **de conscientização espacial a** seguir:</span><span class="sxs-lookup"><span data-stu-id="60e30-114">If you'd like to see room scan visualization in action, check out our **Designing Holograms - Spatial Awareness** video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="60e30-115">*Este vídeo foi tirado do aplicativo "criando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*</span><span class="sxs-lookup"><span data-stu-id="60e30-115">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="device-support"></a><span data-ttu-id="60e30-116">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="60e30-116">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="60e30-117"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="60e30-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="60e30-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="60e30-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="60e30-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="60e30-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="60e30-120">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="60e30-120">Room scan visualization</span></span></td>
        <td><span data-ttu-id="60e30-121">✔️</span><span class="sxs-lookup"><span data-stu-id="60e30-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="60e30-122">Criando uma experiência de verificação personalizada</span><span class="sxs-lookup"><span data-stu-id="60e30-122">Building a custom scanning experience</span></span>

<span data-ttu-id="60e30-123">Os aplicativos podem analisar os dados de mapeamento espacial no início da experiência para avaliar se querem que o usuário execute etapas adicionais para melhorar sua integridade e qualidade.</span><span class="sxs-lookup"><span data-stu-id="60e30-123">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="60e30-124">Se a análise indicar que a qualidade deve ser melhorada, os desenvolvedores devem fornecer uma visualização para sobreposição no mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="60e30-124">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="60e30-125">Quanto do volume total nos arredores dos usuários precisa fazer parte da experiência</span><span class="sxs-lookup"><span data-stu-id="60e30-125">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="60e30-126">Onde o usuário deve ir para melhorar os dados</span><span class="sxs-lookup"><span data-stu-id="60e30-126">Where the user should go to improve data</span></span>

<span data-ttu-id="60e30-127">Os usuários não sabem o que torna uma verificação "boa".</span><span class="sxs-lookup"><span data-stu-id="60e30-127">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="60e30-128">Eles precisam ser mostrados ou informado sobre o que procurar se eles são solicitados a avaliar uma verificação – flatness, distance from actual walls e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="60e30-128">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="60e30-129">O desenvolvedor deve implementar um loop de comentários que inclui a atualização dos dados de mapeamento espacial durante a fase de verificação ou exploração.</span><span class="sxs-lookup"><span data-stu-id="60e30-129">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="60e30-130">Em muitos casos, é melhor dizer ao usuário o que ele precisa fazer para obter a qualidade de verificação necessária.</span><span class="sxs-lookup"><span data-stu-id="60e30-130">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="60e30-131">Por exemplo, veja o limite, procure por trás de móveis e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="60e30-131">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="60e30-132">Mapeamento espacial em cache versus contínuo</span><span class="sxs-lookup"><span data-stu-id="60e30-132">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="60e30-133">Os dados de mapeamento espacial são os aplicativos de fonte de dados de peso mais pesados que podem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="60e30-133">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="60e30-134">Para evitar problemas de desempenho, como quadros descartados ou gagueja, o consumo desses dados deve ser feito com cuidado.</span><span class="sxs-lookup"><span data-stu-id="60e30-134">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="60e30-135">A verificação ativa durante uma experiência pode ser benéfica e prejudicial, portanto, você precisará decidir qual método usar com base na experiência.</span><span class="sxs-lookup"><span data-stu-id="60e30-135">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="60e30-136">Mapeamento espacial armazenado em cache</span><span class="sxs-lookup"><span data-stu-id="60e30-136">Cached spatial mapping</span></span>

<span data-ttu-id="60e30-137">Se houver dados de mapeamento espacial armazenados em cache, o aplicativo normalmente tirará um instantâneo dos dados de mapeamento espacial e usará esse instantâneo durante a experiência.</span><span class="sxs-lookup"><span data-stu-id="60e30-137">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="60e30-138">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="60e30-138">**Benefits**</span></span>
* <span data-ttu-id="60e30-139">Redução da sobrecarga no sistema enquanto a experiência está em execução, levando a ganhos de desempenho de energia, calor e cpu drásticas.</span><span class="sxs-lookup"><span data-stu-id="60e30-139">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="60e30-140">Uma implementação mais simples da experiência principal, pois ela não é interrompida por alterações nos dados espaciais.</span><span class="sxs-lookup"><span data-stu-id="60e30-140">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="60e30-141">Um único custo único em qualquer pós-processamento dos dados espaciais para física, gráficos e outras finalidades.</span><span class="sxs-lookup"><span data-stu-id="60e30-141">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="60e30-142">**Inconvenientes**</span><span class="sxs-lookup"><span data-stu-id="60e30-142">**Drawbacks**</span></span>
* <span data-ttu-id="60e30-143">A movimentação de objetos ou pessoas do mundo real não é refletida pelos dados armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="60e30-143">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="60e30-144">por exemplo, o aplicativo pode considerar uma porta aberta quando ele está fechado agora.</span><span class="sxs-lookup"><span data-stu-id="60e30-144">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="60e30-145">Potencialmente mais memória do aplicativo para manter a versão armazenada em cache dos dados.</span><span class="sxs-lookup"><span data-stu-id="60e30-145">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="60e30-146">Um bom caso para esse método é um ambiente controlado ou um jogo de topo de tabela.</span><span class="sxs-lookup"><span data-stu-id="60e30-146">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="60e30-147">Mapeamento espacial contínuo</span><span class="sxs-lookup"><span data-stu-id="60e30-147">Continuous spatial mapping</span></span>

<span data-ttu-id="60e30-148">Determinados aplicativos podem depender da varredura para atualizar dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="60e30-148">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="60e30-149">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="60e30-149">**Benefits**</span></span>
* <span data-ttu-id="60e30-150">Você não precisa criar uma experiência separada de verificação ou exploração antecipada em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60e30-150">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="60e30-151">A movimentação de objetos do mundo real pode ser refletida pelo jogo, embora com algum atraso.</span><span class="sxs-lookup"><span data-stu-id="60e30-151">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="60e30-152">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="60e30-152">**Drawbacks**</span></span>
* <span data-ttu-id="60e30-153">Maior complexidade na implementação da experiência principal.</span><span class="sxs-lookup"><span data-stu-id="60e30-153">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="60e30-154">Sobrecarga potencial do processamento de elementos gráficos e da física extra, pois as alterações precisam ser ingeridas incrementalmente por esses sistemas.</span><span class="sxs-lookup"><span data-stu-id="60e30-154">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="60e30-155">Maior capacidade, térmico e impacto na CPU.</span><span class="sxs-lookup"><span data-stu-id="60e30-155">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="60e30-156">Um bom caso para esse método é um em que os hologramas devem interagir com a movimentação de objetos, por exemplo, um carro Holographic que as unidades no chão podem desejar aumentar para uma porta dependendo se ela está aberta ou fechada.</span><span class="sxs-lookup"><span data-stu-id="60e30-156">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="60e30-157">Veja também</span><span class="sxs-lookup"><span data-stu-id="60e30-157">See also</span></span>

* [<span data-ttu-id="60e30-158">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="60e30-158">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="60e30-159">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="60e30-159">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="60e30-160">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="60e30-160">Spatial sound design</span></span>](spatial-sound-design.md)