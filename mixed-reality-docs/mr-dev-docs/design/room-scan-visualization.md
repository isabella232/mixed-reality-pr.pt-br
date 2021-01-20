---
title: Visualização de varredura do ambiente
description: Aplicativos que exigem mapeamento espacial usam o dispositivo para coletar dados ao longo do tempo e entre sessões.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, padrões de aplicativo, design, HoloLens, verificação de sala, mapeamento espacial, malha, headset de realidade misturada, headset de realidade misturada do Windows, headset da realidade virtual, HoloLens
ms.openlocfilehash: 0bef09d7f023127f1f5eedf28065758b4a438f3e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583607"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="aa0d6-104">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="aa0d6-104">Room scan visualization</span></span>

<span data-ttu-id="aa0d6-105">Os aplicativos que exigem mapeamento espacial dependem do dispositivo para coletar dados ao longo do tempo e entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="aa0d6-106">A integridade e a qualidade dos dados de mapeamento dependem de muitos fatores, incluindo a quantidade de explorações que o usuário fez, quanto tempo passou desde a exploração e se objetos como mobília e portas foram movidos desde que o dispositivo examinou a área.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="aa0d6-107">Para garantir dados de mapeamento espacial úteis, os desenvolvedores de aplicativos têm várias opções:</span><span class="sxs-lookup"><span data-stu-id="aa0d6-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="aa0d6-108">Conte com o que já pode ter sido coletado.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="aa0d6-109">Esses dados podem estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="aa0d6-110">Peça ao usuário para usar o gesto de cair para chegar à página inicial do Windows Mixed Reality e, em seguida, explorar a área que desejam usar para a experiência.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="aa0d6-111">Eles podem usar o Air-TAP para confirmar se toda a área necessária é conhecida pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="aa0d6-112">Crie uma experiência de exploração personalizada em seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="aa0d6-113">Em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="aa0d6-114">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="aa0d6-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="aa0d6-115"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="aa0d6-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="aa0d6-116"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="aa0d6-116"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="aa0d6-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="aa0d6-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="aa0d6-118">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="aa0d6-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="aa0d6-119">✔️</span><span class="sxs-lookup"><span data-stu-id="aa0d6-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="aa0d6-120">Criando uma experiência de verificação personalizada</span><span class="sxs-lookup"><span data-stu-id="aa0d6-120">Building a custom scanning experience</span></span>

<span data-ttu-id="aa0d6-121">Os aplicativos podem analisar os dados de mapeamento espacial no início da experiência para avaliar se querem que o usuário execute etapas adicionais para melhorar sua integridade e qualidade.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-121">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="aa0d6-122">Se a análise indicar que a qualidade deve ser melhorada, os desenvolvedores devem fornecer uma visualização para sobreposição no mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="aa0d6-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="aa0d6-123">Quanto do volume total nos arredores dos usuários precisa fazer parte da experiência</span><span class="sxs-lookup"><span data-stu-id="aa0d6-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="aa0d6-124">Onde o usuário deve ir para melhorar os dados</span><span class="sxs-lookup"><span data-stu-id="aa0d6-124">Where the user should go to improve data</span></span>

<span data-ttu-id="aa0d6-125">Os usuários não sabem o que faz uma verificação "boa".</span><span class="sxs-lookup"><span data-stu-id="aa0d6-125">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="aa0d6-126">Eles precisam ser mostrados ou disseram o que procurar se forem solicitados a avaliar uma verificação – Flatness, distância de paredes reais e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="aa0d6-127">O desenvolvedor deve implementar um loop de comentários que inclua a atualização dos dados de mapeamento espacial durante a fase de verificação ou exploração.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-127">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="aa0d6-128">Em muitos casos, é melhor informar ao usuário o que eles precisam fazer para obter a qualidade de verificação necessária.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-128">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="aa0d6-129">Por exemplo, examine o teto, procure atrás de mobília e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-129">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="aa0d6-130">Mapeamento espacial em cache versus contínua</span><span class="sxs-lookup"><span data-stu-id="aa0d6-130">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="aa0d6-131">Os dados de mapeamento espacial são os aplicativos de fonte de dados de peso mais intenso que podem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-131">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="aa0d6-132">Para evitar problemas de desempenho como quadros descartados ou excedentes, o consumo desses dados deve ser feito com cuidado.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-132">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="aa0d6-133">A verificação ativa durante uma experiência pode ser benéfica e prejudicial, portanto, você precisará decidir qual método usar com base na experiência.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-133">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="aa0d6-134">Mapeamento espacial armazenado em cache</span><span class="sxs-lookup"><span data-stu-id="aa0d6-134">Cached spatial mapping</span></span>

<span data-ttu-id="aa0d6-135">Se houver dados de mapeamento espacial em cache, o aplicativo normalmente capturará um instantâneo dos dados de mapeamento espacial e usará esse instantâneo durante a experiência.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-135">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="aa0d6-136">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="aa0d6-136">**Benefits**</span></span>
* <span data-ttu-id="aa0d6-137">Redução da sobrecarga no sistema, enquanto a experiência está em execução levando a um aumento considerável de energia, térmico e ganhos de desempenho de CPU.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-137">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="aa0d6-138">Uma implementação mais simples da experiência principal, uma vez que ela não é interrompida por alterações nos dados espaciais.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-138">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="aa0d6-139">Um único custo individual em qualquer processamento posterior de dados espaciais para física, gráficos e outras finalidades.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-139">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="aa0d6-140">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="aa0d6-140">**Drawbacks**</span></span>
* <span data-ttu-id="aa0d6-141">A movimentação de objetos do mundo real ou de pessoas não é refletida pelos dados armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-141">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="aa0d6-142">por exemplo, o aplicativo pode considerar uma porta aberta quando é fechado agora.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-142">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="aa0d6-143">Possivelmente mais memória de aplicativo para manter a versão em cache dos dados.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="aa0d6-144">Um bom caso para esse método é um ambiente controlado ou um jogo de topo de tabela.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="aa0d6-145">Mapeamento espacial contínuo</span><span class="sxs-lookup"><span data-stu-id="aa0d6-145">Continuous spatial mapping</span></span>

<span data-ttu-id="aa0d6-146">Determinados aplicativos podem depender da varredura para atualizar dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="aa0d6-147">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="aa0d6-147">**Benefits**</span></span>
* <span data-ttu-id="aa0d6-148">Você não precisa criar uma experiência separada de verificação ou exploração antecipada em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="aa0d6-149">A movimentação de objetos do mundo real pode ser refletida pelo jogo, embora com algum atraso.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="aa0d6-150">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="aa0d6-150">**Drawbacks**</span></span>
* <span data-ttu-id="aa0d6-151">Maior complexidade na implementação da experiência principal.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="aa0d6-152">Sobrecarga potencial do processamento de elementos gráficos e da física extra, pois as alterações precisam ser ingeridas incrementalmente por esses sistemas.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-152">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="aa0d6-153">Maior capacidade, térmico e impacto na CPU.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-153">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="aa0d6-154">Um bom caso para esse método é um em que os hologramas devem interagir com a movimentação de objetos, por exemplo, um carro Holographic que as unidades no chão podem desejar aumentar para uma porta dependendo se ela está aberta ou fechada.</span><span class="sxs-lookup"><span data-stu-id="aa0d6-154">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa0d6-155">Veja também</span><span class="sxs-lookup"><span data-stu-id="aa0d6-155">See also</span></span>

* [<span data-ttu-id="aa0d6-156">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="aa0d6-156">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="aa0d6-157">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="aa0d6-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="aa0d6-158">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="aa0d6-158">Spatial sound design</span></span>](spatial-sound-design.md)