---
title: Controladores de mãos e de movimento
description: Saiba mais sobre os modelos de interação dos controladores de movimentos e práticas, que podem remover o limite entre o virtual e o físico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realidade mista, mãos, controladores de movimento, interação, design
ms.openlocfilehash: 8b2ed6127708204d0c4a537c56b2225ff26e0d0f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675792"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="9612a-104">Controladores de mãos e de movimento</span><span class="sxs-lookup"><span data-stu-id="9612a-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="9612a-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="9612a-105">Scenarios</span></span>
<span data-ttu-id="9612a-106">Se você optar por adotar esse modelo de interação depois de ler a [visão geral da interação](interaction-fundamentals.md), significa que você está desenvolvendo um aplicativo que exige que os usuários usem duas mãos para interagir com o Holographic World.</span><span class="sxs-lookup"><span data-stu-id="9612a-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="9612a-107">Seu aplicativo vai atingir o objetivo de remover o limite entre virtual e físico.</span><span class="sxs-lookup"><span data-stu-id="9612a-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="9612a-108">Alguns cenários específicos podem ser:</span><span class="sxs-lookup"><span data-stu-id="9612a-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="9612a-109">Fornecimento de telas virtuais 2D a profissionais da informação, com funcionalidades de UI (interface do usuário) para exibir e controlar o conteúdo</span><span class="sxs-lookup"><span data-stu-id="9612a-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="9612a-110">Fornecendo tutoriais e guias de primeira linha aos funcionários para linhas de assembly de fábrica</span><span class="sxs-lookup"><span data-stu-id="9612a-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="9612a-111">Desenvolvimento de ferramentas profissionais para auxiliar e orientar profissionais médicos</span><span class="sxs-lookup"><span data-stu-id="9612a-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="9612a-112">Uso de objetos virtuais 3D para decorar o mundo real ou criar um segundo mundo</span><span class="sxs-lookup"><span data-stu-id="9612a-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="9612a-113">Criação de serviços e jogos baseados em localização usando o mundo real como tela de fundo</span><span class="sxs-lookup"><span data-stu-id="9612a-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="9612a-114">Modalidades de controladores de mãos e de movimento</span><span class="sxs-lookup"><span data-stu-id="9612a-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="9612a-115">[![Manipulação direta com as mãos](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="9612a-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="9612a-116">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="9612a-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="9612a-117">Essa é uma modalidade que aproveita o poder das mãos, com as quais os usuários são capazes de tocar e manipular os hologramas diretamente.</span><span class="sxs-lookup"><span data-stu-id="9612a-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="9612a-118">Aproveitando as experiências diárias de vida e fornecendo uma capacidades Visual adequada, os usuários podem usar a mesma maneira de manipular objetos reais para interagir com os virtuais.</span><span class="sxs-lookup"><span data-stu-id="9612a-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="9612a-119">[![Apontar e confirmar com as mãos](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="9612a-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="9612a-120">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="9612a-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="9612a-121">Essa modalidade permite que os usuários interajam com os hologramas em uma distância.</span><span class="sxs-lookup"><span data-stu-id="9612a-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="9612a-122">Ele permite que os usuários façam o melhor uso de arredores.</span><span class="sxs-lookup"><span data-stu-id="9612a-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="9612a-123">Os usuários podem posicionar os hologramas em qualquer lugar e ainda acessá-los de qualquer distância.</span><span class="sxs-lookup"><span data-stu-id="9612a-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="9612a-124">Os modelos mentales e gestos para controlar e manipular os hologramas 2D e 3D são altamente sincronizados com aqueles de manipulação direta.</span><span class="sxs-lookup"><span data-stu-id="9612a-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="9612a-125">[![Controladores de movimento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="9612a-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="9612a-126">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="9612a-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="9612a-127">Os controladores de movimento são ferramentas que estendem os recursos físicos do usuário, fornecendo interações precisas em uma grande variedade de distâncias ao usar uma ou ambas as mãos.</span><span class="sxs-lookup"><span data-stu-id="9612a-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="9612a-128">Esses acessórios de hardware fornecem atalhos para muitas interações usadas com frequência e fornecem comentários de Surefooted, tactile para uma variedade de ações.</span><span class="sxs-lookup"><span data-stu-id="9612a-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="9612a-129">Atualmente, os controladores de movimento só estão disponíveis para cenários de WMR (realidade mista do Windows).</span><span class="sxs-lookup"><span data-stu-id="9612a-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="9612a-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="9612a-130">See also</span></span>
* [<span data-ttu-id="9612a-131">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="9612a-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="9612a-132">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="9612a-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="9612a-133">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="9612a-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9612a-134">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="9612a-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="9612a-135">Mãos livres</span><span class="sxs-lookup"><span data-stu-id="9612a-135">Hands-free</span></span>](hands-free.md)
