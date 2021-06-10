---
title: ExperienceSettings
description: Documentação sobre as diferentes configurações de experiência para MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647747"
---
# <a name="experience-settings"></a><span data-ttu-id="0f301-104">Configurações da experiência</span><span class="sxs-lookup"><span data-stu-id="0f301-104">Experience Settings</span></span>

<span data-ttu-id="0f301-105">Um dos desafios de criar a interface do usuário para realidade misturada está se alinhando em experiências diferentes.</span><span class="sxs-lookup"><span data-stu-id="0f301-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="0f301-106">Com o MRTK, você pode definir o `Target Experience Scale` e o `Content Offset` para sua cena, configurar o seguinte para se comportar adequadamente para a escala de destino.</span><span class="sxs-lookup"><span data-stu-id="0f301-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="0f301-107">Conteúdo da cena de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="0f301-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="0f301-108">Sistema de limite</span><span class="sxs-lookup"><span data-stu-id="0f301-108">Boundary System</span></span>

  ![Configurações de experiência no perfil de configuração do MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="0f301-110">Escala de experiência de destino</span><span class="sxs-lookup"><span data-stu-id="0f301-110">Target Experience Scale</span></span>

<span data-ttu-id="0f301-111">A **escala de experiência de destino** especifica o ambiente para o qual a experiência foi projetada.</span><span class="sxs-lookup"><span data-stu-id="0f301-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="0f301-112">Pode assumir os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="0f301-112">It can take on the following values.</span></span>

* <span data-ttu-id="0f301-113">*OrientationOnly* – uma experiência que utiliza apenas a orientação do headset e está alinhada à gravidade.</span><span class="sxs-lookup"><span data-stu-id="0f301-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="0f301-114">A origem do sistema de coordenadas está no nível do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="0f301-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="0f301-115">*Sentado* -uma experiência projetada para uso em estação.</span><span class="sxs-lookup"><span data-stu-id="0f301-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="0f301-116">A origem do sistema de coordenadas está no nível do piso.</span><span class="sxs-lookup"><span data-stu-id="0f301-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="0f301-117">Em *pé* – uma experiência projetada para uso estacionário.</span><span class="sxs-lookup"><span data-stu-id="0f301-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="0f301-118">A origem do sistema de coordenadas está no nível do piso.</span><span class="sxs-lookup"><span data-stu-id="0f301-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="0f301-119">*Sala* -uma experiência projetada para dar suporte à movimentação ao longo de uma sala.</span><span class="sxs-lookup"><span data-stu-id="0f301-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="0f301-120">A origem do sistema de coordenadas está no nível do piso.</span><span class="sxs-lookup"><span data-stu-id="0f301-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="0f301-121">*Mundo* – uma experiência projetada para utilizar e percorrer o mundo físico.</span><span class="sxs-lookup"><span data-stu-id="0f301-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="0f301-122">A origem do sistema de coordenadas está no nível do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="0f301-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="0f301-123">Deslocamento de conteúdo</span><span class="sxs-lookup"><span data-stu-id="0f301-123">Content Offset</span></span>

<span data-ttu-id="0f301-124">Esse parâmetro especifica a altura acima do andar para deslocar o [conteúdo da cena de realidade misturada](scene-content.md) quando o **tipo de alinhamento** está definido para **alinhar com a escala de experiência**</span><span class="sxs-lookup"><span data-stu-id="0f301-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>