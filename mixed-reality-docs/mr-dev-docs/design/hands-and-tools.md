---
title: Controladores de mãos e de movimento
description: Saiba mais sobre os modelos de interação dos controladores de movimentos e práticas, que podem remover o limite entre o virtual e o físico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realidade misturada, mãos, controladores de movimento, interação, design, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847319"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="ae681-104">Controladores de mãos e de movimento</span><span class="sxs-lookup"><span data-stu-id="ae681-104">Hands and motion controllers</span></span>

## <a name="scenarios"></a><span data-ttu-id="ae681-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="ae681-105">Scenarios</span></span>

<span data-ttu-id="ae681-106">Depois de ler a [visão geral da interação](interaction-fundamentals.md), você escolhe o modelo de interação do controlador de mão e de movimento.</span><span class="sxs-lookup"><span data-stu-id="ae681-106">After reading the [interaction overview](interaction-fundamentals.md), you choose the hand and motion controller interaction model.</span></span> <span data-ttu-id="ae681-107">Isso significa que você está desenvolvendo um aplicativo que exige que os usuários usem duas mãos para interagir com o mundo Holographic.</span><span class="sxs-lookup"><span data-stu-id="ae681-107">This means you're developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="ae681-108">Seu aplicativo vai atingir o objetivo de remover o limite entre virtual e físico.</span><span class="sxs-lookup"><span data-stu-id="ae681-108">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="ae681-109">Alguns cenários específicos podem ser:</span><span class="sxs-lookup"><span data-stu-id="ae681-109">Some specific scenarios might be:</span></span>
* <span data-ttu-id="ae681-110">Fornecimento de telas virtuais 2D a profissionais da informação, com funcionalidades de UI (interface do usuário) para exibir e controlar o conteúdo</span><span class="sxs-lookup"><span data-stu-id="ae681-110">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="ae681-111">Fornecendo tutoriais e guias de primeira linha aos funcionários para linhas de assembly de fábrica</span><span class="sxs-lookup"><span data-stu-id="ae681-111">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="ae681-112">Desenvolvimento de ferramentas profissionais para auxiliar e orientar profissionais médicos</span><span class="sxs-lookup"><span data-stu-id="ae681-112">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="ae681-113">Uso de objetos virtuais 3D para decorar o mundo real ou criar um segundo mundo</span><span class="sxs-lookup"><span data-stu-id="ae681-113">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="ae681-114">Criação de serviços e jogos baseados em localização usando o mundo real como tela de fundo</span><span class="sxs-lookup"><span data-stu-id="ae681-114">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="ae681-115">Modalidades de controladores de mãos e de movimento</span><span class="sxs-lookup"><span data-stu-id="ae681-115">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="ae681-116">[![Manipulação direta com as mãos](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="ae681-116">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="ae681-117">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="ae681-117">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="ae681-118">A modalidade aplica a potência das mãos que os usuários podem usar para tocar e manipular hologramas.</span><span class="sxs-lookup"><span data-stu-id="ae681-118">Modality applying the power of hands that users can use to touch and manipulate holograms.</span></span> <span data-ttu-id="ae681-119">Usando experiências diárias de vida e fornecendo capacidades visuais adequados, os usuários podem usar a mesma maneira de manipular objetos reais para interagir com os virtuais.</span><span class="sxs-lookup"><span data-stu-id="ae681-119">By using daily life experiences and providing proper visual affordances, users can use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ae681-120">[![Apontar e confirmar com as mãos](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="ae681-120">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="ae681-121">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="ae681-121">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="ae681-122">Essa modalidade permite que os usuários interajam com os hologramas em uma distância.</span><span class="sxs-lookup"><span data-stu-id="ae681-122">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="ae681-123">Ele permite que os usuários façam o melhor uso de arredores.</span><span class="sxs-lookup"><span data-stu-id="ae681-123">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="ae681-124">Os usuários podem posicionar os hologramas em qualquer lugar e ainda acessá-los de qualquer distância.</span><span class="sxs-lookup"><span data-stu-id="ae681-124">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="ae681-125">Os modelos mentales e gestos para controlar e manipular os hologramas 2D e 3D são altamente sincronizados com aqueles de manipulação direta.</span><span class="sxs-lookup"><span data-stu-id="ae681-125">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ae681-126">[![Controladores de movimento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="ae681-126">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="ae681-127">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="ae681-127">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="ae681-128">Os controladores de movimento estendem os recursos físicos do usuário com interações precisas em um intervalo de distâncias durante o uso de uma ou de ambas as mãos.</span><span class="sxs-lookup"><span data-stu-id="ae681-128">Motion controllers extend the user's physical capabilities with precise interactions across a range of distances while using one or both hands.</span></span> <span data-ttu-id="ae681-129">Esses acessórios de hardware fornecem atalhos para muitas interações usadas com frequência e fornecem comentários tactiles e com rodapé para várias ações.</span><span class="sxs-lookup"><span data-stu-id="ae681-129">These hardware accessories provide shortcuts to many commonly used interactions and provide sure-footed, tactile feedback for various actions.</span></span> <span data-ttu-id="ae681-130">Atualmente, os controladores de movimento só estão disponíveis para cenários de WMR (realidade mista do Windows).</span><span class="sxs-lookup"><span data-stu-id="ae681-130">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="ae681-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="ae681-131">See also</span></span>
* [<span data-ttu-id="ae681-132">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="ae681-132">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ae681-133">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="ae681-133">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="ae681-134">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="ae681-134">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ae681-135">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="ae681-135">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="ae681-136">Mãos livres</span><span class="sxs-lookup"><span data-stu-id="ae681-136">Hands-free</span></span>](hands-free.md)
