---
title: Serviço de extensão de física manual
description: Descrição os serviços de extensão de física.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143430"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="b251b-104">Distribuir serviços de extensão de física</span><span class="sxs-lookup"><span data-stu-id="b251b-104">Hand physics extension services</span></span>

<span data-ttu-id="b251b-105">O serviço de física manual permite eventos de colisão de corpo rígidos e interações com mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="b251b-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="b251b-106">Introdução ao serviço de extensão de física manual</span><span class="sxs-lookup"><span data-stu-id="b251b-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="b251b-107">Adicione o serviço de física à mão à lista de serviços de extensão e use o perfil padrão.</span><span class="sxs-lookup"><span data-stu-id="b251b-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="b251b-108">Uma vez habilitado, use a propriedade istrigger de qualquer colisor para receber eventos de colisão de todos os 10 dígitos (e Palms, se estiverem habilitados).</span><span class="sxs-lookup"><span data-stu-id="b251b-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b251b-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b251b-109">Prerequisites</span></span>

- <span data-ttu-id="b251b-110">Habilitou o serviço de extensão</span><span class="sxs-lookup"><span data-stu-id="b251b-110">Enabled the extension service</span></span>
- <span data-ttu-id="b251b-111">Atribua um pré-fabricado apropriado ao conjunto de dedos/Palm.</span><span class="sxs-lookup"><span data-stu-id="b251b-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="b251b-112">Recomendações</span><span class="sxs-lookup"><span data-stu-id="b251b-112">Recommendations</span></span>

<span data-ttu-id="b251b-113">Embora o serviço seja padronizado para a camada "padrão", é recomendável usar uma camada separada para objetos HandPhysics.</span><span class="sxs-lookup"><span data-stu-id="b251b-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="b251b-114">Caso contrário, pode haver colisões indesejadas e/ou raycasts imprecisas.</span><span class="sxs-lookup"><span data-stu-id="b251b-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
