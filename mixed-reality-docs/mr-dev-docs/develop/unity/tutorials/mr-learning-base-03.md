---
title: Tutoriais de introdução – 3. Como configurar os perfis do MRTK
description: Este curso mostra como configurar os perfis do MRTK (Kit de Ferramentas de Realidade Misturada).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, reconhecimento espacial
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300451"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="f836d-105">3. Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="f836d-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="f836d-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f836d-106">Overview</span></span>

<span data-ttu-id="f836d-107">Neste tutorial, você aprenderá a personalizar e configurar os perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="f836d-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="f836d-108">Os <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">perfis do MRTK</a> são uma árvore de perfis aninhados que compõem as informações de configuração sobre como os sistemas e os recursos do MRTK devem ser inicializados.</span><span class="sxs-lookup"><span data-stu-id="f836d-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="f836d-109">O perfil de nível superior, o Perfil de Configuração, contém perfis aninhados para cada um dos principais sistemas básicos.</span><span class="sxs-lookup"><span data-stu-id="f836d-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="f836d-110">Cada perfil aninhado foi projetado para configurar o comportamento do respectivo sistema correspondente.</span><span class="sxs-lookup"><span data-stu-id="f836d-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="f836d-111">Este exemplo específico mostrará como ocultar a malha de reconhecimento espacial alterando as configurações do Observador de Malha Espacial.</span><span class="sxs-lookup"><span data-stu-id="f836d-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="f836d-112">No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="f836d-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="f836d-113">Como você experimentou quando implantou seu projeto no HoloLens 2 durante o [tutorial anterior](mr-learning-base-02.md#congratulations), a malha de <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Reconhecimento Espacial</a> é uma coleção de malhas que representa a geometria do ambiente.</span><span class="sxs-lookup"><span data-stu-id="f836d-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="f836d-114">É uma visualização útil de ser vista inicialmente, mas em geral, é desativada para evitar a distração visual e o impacto adicional de desempenho da presença dela.</span><span class="sxs-lookup"><span data-stu-id="f836d-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="f836d-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f836d-115">Objectives</span></span>

* <span data-ttu-id="f836d-116">Saiba como personalizar e configurar perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="f836d-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="f836d-117">Ocultar a malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="f836d-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="f836d-118">Como alterar a opção de exibição de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="f836d-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="f836d-119">As principais etapas que você seguirá para ocultar a malha de reconhecimento espacial são:</span><span class="sxs-lookup"><span data-stu-id="f836d-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="f836d-120">Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="f836d-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="f836d-121">Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="f836d-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="f836d-122">Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="f836d-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="f836d-123">Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="f836d-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="f836d-124">Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="f836d-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="f836d-125">Por padrão, os perfis do MRTK não são editáveis.</span><span class="sxs-lookup"><span data-stu-id="f836d-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="f836d-126">Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados.</span><span class="sxs-lookup"><span data-stu-id="f836d-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="f836d-127">Há várias camadas aninhadas de perfis.</span><span class="sxs-lookup"><span data-stu-id="f836d-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="f836d-128">Portanto, é comum clonar e editar vários perfis ao definir uma ou mais configurações.</span><span class="sxs-lookup"><span data-stu-id="f836d-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="f836d-129">Parabéns</span><span class="sxs-lookup"><span data-stu-id="f836d-129">Congratulations</span></span>

<span data-ttu-id="f836d-130">Neste tutorial, você aprendeu a clonar, personalizar e definir uma configurações e perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="f836d-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f836d-131">Próximo tutorial: 4. Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="f836d-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)