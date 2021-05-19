---
title: Visualização de varredura do ambiente
description: Aplicativos que exigem mapeamento espacial usam o dispositivo para coletar dados ao longo do tempo e entre sessões.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Padrões de aplicativo, design, HoloLens, verificação de sala, mapeamento espacial, malha, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143616"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="61601-104">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="61601-104">Room scan visualization</span></span>

<span data-ttu-id="61601-105">Os aplicativos que exigem mapeamento espacial dependem do dispositivo para coletar dados ao longo do tempo e entre sessões.</span><span class="sxs-lookup"><span data-stu-id="61601-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="61601-106">A conclusão e a qualidade dos dados de mapeamento dependem de muitos fatores, incluindo a quantidade de exploração que o usuário fez, quanto tempo passou desde a exploração e se objetos como móveis e portas foram movidos desde que o dispositivo examinou a área.</span><span class="sxs-lookup"><span data-stu-id="61601-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="61601-107">Para garantir dados úteis de mapeamento espacial, os desenvolvedores de aplicativos têm várias opções:</span><span class="sxs-lookup"><span data-stu-id="61601-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="61601-108">Confie no que pode já ter sido coletado.</span><span class="sxs-lookup"><span data-stu-id="61601-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="61601-109">Esses dados podem estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="61601-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="61601-110">Peça ao usuário para usar o gesto de bloom para chegar à Windows Mixed Reality e, em seguida, explorar a área que deseja usar para a experiência.</span><span class="sxs-lookup"><span data-stu-id="61601-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="61601-111">Eles podem usar o toque de ar para confirmar se toda a área necessária é conhecida pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="61601-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="61601-112">Crie uma experiência de exploração personalizada em seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61601-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="61601-113">Em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso.</span><span class="sxs-lookup"><span data-stu-id="61601-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="61601-114">Se você quiser ver a visualização de verificação de sala em ação, confira nossa demonstração de vídeo [Designing Holograms – Spatial Awareness]() abaixo:</span><span class="sxs-lookup"><span data-stu-id="61601-114">If you'd like to see room scan visualization in action, check out our [Designing Holograms - Spatial Awareness]() video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="device-support"></a><span data-ttu-id="61601-115">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="61601-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="61601-116"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="61601-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="61601-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="61601-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="61601-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="61601-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="61601-119">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="61601-119">Room scan visualization</span></span></td>
        <td><span data-ttu-id="61601-120">✔️</span><span class="sxs-lookup"><span data-stu-id="61601-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="61601-121">Criando uma experiência de verificação personalizada</span><span class="sxs-lookup"><span data-stu-id="61601-121">Building a custom scanning experience</span></span>

<span data-ttu-id="61601-122">Os aplicativos podem analisar os dados de mapeamento espacial no início da experiência para avaliar se eles querem que o usuário faça etapas adicionais para melhorar sua conclusão e sua qualidade.</span><span class="sxs-lookup"><span data-stu-id="61601-122">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="61601-123">Se a análise indicar que a qualidade deve ser aprimorada, os desenvolvedores deverão fornecer uma visualização para sobreposição no mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="61601-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="61601-124">Quanto do volume total na proximidade dos usuários precisa fazer parte da experiência</span><span class="sxs-lookup"><span data-stu-id="61601-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="61601-125">Onde o usuário deve ir para melhorar os dados</span><span class="sxs-lookup"><span data-stu-id="61601-125">Where the user should go to improve data</span></span>

<span data-ttu-id="61601-126">Os usuários não sabem o que torna uma verificação "boa".</span><span class="sxs-lookup"><span data-stu-id="61601-126">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="61601-127">Eles precisam ser mostrados ou disseram o que procurar se forem solicitados a avaliar uma verificação – Flatness, distância de paredes reais e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="61601-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="61601-128">O desenvolvedor deve implementar um loop de comentários que inclua a atualização dos dados de mapeamento espacial durante a fase de verificação ou exploração.</span><span class="sxs-lookup"><span data-stu-id="61601-128">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="61601-129">Em muitos casos, é melhor informar ao usuário o que eles precisam fazer para obter a qualidade de verificação necessária.</span><span class="sxs-lookup"><span data-stu-id="61601-129">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="61601-130">Por exemplo, examine o teto, procure atrás de mobília e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="61601-130">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="61601-131">Mapeamento espacial em cache versus contínua</span><span class="sxs-lookup"><span data-stu-id="61601-131">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="61601-132">Os dados de mapeamento espacial são os aplicativos de fonte de dados de peso mais intenso que podem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="61601-132">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="61601-133">Para evitar problemas de desempenho como quadros descartados ou excedentes, o consumo desses dados deve ser feito com cuidado.</span><span class="sxs-lookup"><span data-stu-id="61601-133">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="61601-134">A verificação ativa durante uma experiência pode ser benéfica e prejudicial, portanto, você precisará decidir qual método usar com base na experiência.</span><span class="sxs-lookup"><span data-stu-id="61601-134">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="61601-135">Mapeamento espacial armazenado em cache</span><span class="sxs-lookup"><span data-stu-id="61601-135">Cached spatial mapping</span></span>

<span data-ttu-id="61601-136">Se houver dados de mapeamento espacial em cache, o aplicativo normalmente capturará um instantâneo dos dados de mapeamento espacial e usará esse instantâneo durante a experiência.</span><span class="sxs-lookup"><span data-stu-id="61601-136">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="61601-137">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="61601-137">**Benefits**</span></span>
* <span data-ttu-id="61601-138">Redução da sobrecarga no sistema, enquanto a experiência está em execução levando a um aumento considerável de energia, térmico e ganhos de desempenho de CPU.</span><span class="sxs-lookup"><span data-stu-id="61601-138">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="61601-139">Uma implementação mais simples da experiência principal, uma vez que ela não é interrompida por alterações nos dados espaciais.</span><span class="sxs-lookup"><span data-stu-id="61601-139">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="61601-140">Um único custo individual em qualquer processamento posterior de dados espaciais para física, gráficos e outras finalidades.</span><span class="sxs-lookup"><span data-stu-id="61601-140">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="61601-141">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="61601-141">**Drawbacks**</span></span>
* <span data-ttu-id="61601-142">A movimentação de objetos do mundo real ou de pessoas não é refletida pelos dados armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="61601-142">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="61601-143">por exemplo, o aplicativo pode considerar uma porta aberta quando é fechado agora.</span><span class="sxs-lookup"><span data-stu-id="61601-143">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="61601-144">Possivelmente mais memória de aplicativo para manter a versão em cache dos dados.</span><span class="sxs-lookup"><span data-stu-id="61601-144">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="61601-145">Um bom caso para esse método é um ambiente controlado ou um jogo de topo de tabela.</span><span class="sxs-lookup"><span data-stu-id="61601-145">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="61601-146">Mapeamento espacial contínuo</span><span class="sxs-lookup"><span data-stu-id="61601-146">Continuous spatial mapping</span></span>

<span data-ttu-id="61601-147">Determinados aplicativos podem depender da varredura para atualizar dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="61601-147">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="61601-148">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="61601-148">**Benefits**</span></span>
* <span data-ttu-id="61601-149">Você não precisa criar uma experiência de verificação ou exploração separada antecipadamente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61601-149">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="61601-150">O movimento de objetos do mundo real pode ser refletido pelo jogo, embora com algum atraso.</span><span class="sxs-lookup"><span data-stu-id="61601-150">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="61601-151">**Inconvenientes**</span><span class="sxs-lookup"><span data-stu-id="61601-151">**Drawbacks**</span></span>
* <span data-ttu-id="61601-152">Maior complexidade na implementação da experiência principal.</span><span class="sxs-lookup"><span data-stu-id="61601-152">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="61601-153">Possível sobrecarga do processamento gráfico e físico extra, pois as alterações precisam ser ingeridos incrementalmente por esses sistemas.</span><span class="sxs-lookup"><span data-stu-id="61601-153">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="61601-154">Maior impacto de energia, calor e CPU.</span><span class="sxs-lookup"><span data-stu-id="61601-154">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="61601-155">Um bom caso para esse método é aquele em que os hologramas devem interagir com objetos de movimentação, por exemplo, um carro holográfico que conduz no chão pode querer colidir em uma porta, dependendo se ele está aberto ou fechado.</span><span class="sxs-lookup"><span data-stu-id="61601-155">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="61601-156">Veja também</span><span class="sxs-lookup"><span data-stu-id="61601-156">See also</span></span>

* [<span data-ttu-id="61601-157">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="61601-157">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="61601-158">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="61601-158">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="61601-159">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="61601-159">Spatial sound design</span></span>](spatial-sound-design.md)