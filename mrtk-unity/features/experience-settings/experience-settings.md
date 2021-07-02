---
title: Configurações de experiência
description: Documentação sobre as diferentes configurações de experiência do MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177350"
---
# <a name="experience-settings"></a><span data-ttu-id="c1469-104">Configurações de experiência</span><span class="sxs-lookup"><span data-stu-id="c1469-104">Experience settings</span></span>

<span data-ttu-id="c1469-105">Um dos desafios da criação da interface do usuário para Realidade Misturada é o alinhamento entre diferentes experiências.</span><span class="sxs-lookup"><span data-stu-id="c1469-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="c1469-106">Com o MRTK, você pode definir o e o para sua cena, configurará o seguinte para se comportar adequadamente `Target Experience Scale` para a escala de `Content Offset` destino.</span><span class="sxs-lookup"><span data-stu-id="c1469-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="c1469-107">Conteúdo da cena de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c1469-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="c1469-108">Sistema de limite</span><span class="sxs-lookup"><span data-stu-id="c1469-108">Boundary System</span></span>

  ![Experiência Configurações perfil de configuração do MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="c1469-110">Escala de experiência de destino</span><span class="sxs-lookup"><span data-stu-id="c1469-110">Target Experience Scale</span></span>

<span data-ttu-id="c1469-111">A **Escala de Experiência de** Destino especifica o ambiente para o qual a experiência foi projetada.</span><span class="sxs-lookup"><span data-stu-id="c1469-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="c1469-112">Ele pode assumir os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="c1469-112">It can take on the following values.</span></span>

* <span data-ttu-id="c1469-113">*OrientationOnly* – uma experiência que utiliza apenas a orientação do headset e está alinhada à gravidade.</span><span class="sxs-lookup"><span data-stu-id="c1469-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="c1469-114">A origem do sistema de coordenadas está no nível da cabeça.</span><span class="sxs-lookup"><span data-stu-id="c1469-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="c1469-115">*Seated* – uma experiência projetada para uso de sedados.</span><span class="sxs-lookup"><span data-stu-id="c1469-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="c1469-116">A origem do sistema de coordenadas está no nível do chão.</span><span class="sxs-lookup"><span data-stu-id="c1469-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="c1469-117">*Permanente* – uma experiência projetada para uso estacionário.</span><span class="sxs-lookup"><span data-stu-id="c1469-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="c1469-118">A origem do sistema de coordenadas está no nível do chão.</span><span class="sxs-lookup"><span data-stu-id="c1469-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="c1469-119">*Sala* – uma experiência projetada para dar suporte à movimentação em uma sala.</span><span class="sxs-lookup"><span data-stu-id="c1469-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="c1469-120">A origem do sistema de coordenadas está no nível do chão.</span><span class="sxs-lookup"><span data-stu-id="c1469-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="c1469-121">*Mundo* – uma experiência projetada para utilizar e mover-se pelo mundo físico.</span><span class="sxs-lookup"><span data-stu-id="c1469-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="c1469-122">A origem do sistema de coordenadas está no nível da cabeça.</span><span class="sxs-lookup"><span data-stu-id="c1469-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="c1469-123">Deslocamento de conteúdo</span><span class="sxs-lookup"><span data-stu-id="c1469-123">Content Offset</span></span>

<span data-ttu-id="c1469-124">Esse parâmetro especifica a altura acima do chão para deslocamento do conteúdo da cena de [realidade](scene-content.md) misturada quando o tipo **de** alinhamento é definido como Alinhar com a escala **de experiência**</span><span class="sxs-lookup"><span data-stu-id="c1469-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>
