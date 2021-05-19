---
title: Configurações de câmera ar do Unity
description: Documentação para usar a câmera AR no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Câmera AR,
ms.openlocfilehash: baa54f4a7c6238b136a108cf5adcbddd29c3ee1b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143462"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="852a3-104">Provedor de configurações de câmera AR do Unity</span><span class="sxs-lookup"><span data-stu-id="852a3-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="852a3-105">O provedor de configurações de câmera AR do Unity é um componente experimental do MRTK que permite que aplicativos de realidade misturada executem em dispositivos Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="852a3-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="852a3-106">Opções do provedor de configurações de câmera ar do Unity</span><span class="sxs-lookup"><span data-stu-id="852a3-106">Unity AR camera settings provider options</span></span>

![Configuração de configurações da câmera AR do Unity](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="852a3-108">Para ver um guia sobre como adicionar o provedor à sua cena: [Como configurar o MRTK para iOS e Android](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="852a3-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="852a3-109">Configurações de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="852a3-109">Tracking settings</span></span>

<span data-ttu-id="852a3-110">O provedor de configurações de câmera AR do Unity permite opções de configuração para como o acompanhamento é executado.</span><span class="sxs-lookup"><span data-stu-id="852a3-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="852a3-111">Essas configurações são específicas para a implementação do provedor de configurações de câmera ar do Unity.</span><span class="sxs-lookup"><span data-stu-id="852a3-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="852a3-112">**Origem de pose**</span><span class="sxs-lookup"><span data-stu-id="852a3-112">**Pose Source**</span></span>

<span data-ttu-id="852a3-113">A origem de pose define os tipos disponíveis de poses de acompanhamento de realidade aumentada.</span><span class="sxs-lookup"><span data-stu-id="852a3-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="852a3-114">Em geral, esses valores são mapeados para um componente do dispositivo no qual o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="852a3-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="852a3-115">As opções disponíveis são descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="852a3-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="852a3-116">Opção</span><span class="sxs-lookup"><span data-stu-id="852a3-116">Option</span></span> | <span data-ttu-id="852a3-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="852a3-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="852a3-118">Centro</span><span class="sxs-lookup"><span data-stu-id="852a3-118">Center</span></span> | <span data-ttu-id="852a3-119">O olho central de um dispositivo montado na cabeça.</span><span class="sxs-lookup"><span data-stu-id="852a3-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="852a3-120">Câmera de cores</span><span class="sxs-lookup"><span data-stu-id="852a3-120">Color Camera</span></span> | <span data-ttu-id="852a3-121">A câmera de cores de um dispositivo móvel.</span><span class="sxs-lookup"><span data-stu-id="852a3-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="852a3-122">Head</span><span class="sxs-lookup"><span data-stu-id="852a3-122">Head</span></span> | <span data-ttu-id="852a3-123">O olho da cabeça de um dispositivo montado na cabeça, geralmente um pouco acima do olho central.</span><span class="sxs-lookup"><span data-stu-id="852a3-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="852a3-124">Olho esquerdo</span><span class="sxs-lookup"><span data-stu-id="852a3-124">Left Eye</span></span> | <span data-ttu-id="852a3-125">O olho à esquerda de um dispositivo montado no cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="852a3-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="852a3-126">Pose esquerda</span><span class="sxs-lookup"><span data-stu-id="852a3-126">Left Pose</span></span> | <span data-ttu-id="852a3-127">O controlador esquerdo é composto.</span><span class="sxs-lookup"><span data-stu-id="852a3-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="852a3-128">Olho à direita</span><span class="sxs-lookup"><span data-stu-id="852a3-128">Right Eye</span></span> | <span data-ttu-id="852a3-129">O olho certo de um dispositivo montado na cabeça.</span><span class="sxs-lookup"><span data-stu-id="852a3-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="852a3-130">Pose direita</span><span class="sxs-lookup"><span data-stu-id="852a3-130">Right Pose</span></span> | <span data-ttu-id="852a3-131">A pose do controlador à direita.</span><span class="sxs-lookup"><span data-stu-id="852a3-131">The right hand controller pose.</span></span> |

<span data-ttu-id="852a3-132">O valor padrão da origem da pose é a **câmera colorida**, para habilitar uma exibição transparente em dispositivos móveis, como um telefone ou Tablet.</span><span class="sxs-lookup"><span data-stu-id="852a3-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="852a3-133">**Tipo de rastreamento**</span><span class="sxs-lookup"><span data-stu-id="852a3-133">**Tracking Type**</span></span>

<span data-ttu-id="852a3-134">O tipo de rastreamento define as partes da pose que serão usadas para acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="852a3-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="852a3-135">As opções disponíveis são descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="852a3-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="852a3-136">Opção</span><span class="sxs-lookup"><span data-stu-id="852a3-136">Option</span></span> | <span data-ttu-id="852a3-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="852a3-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="852a3-138">Posição</span><span class="sxs-lookup"><span data-stu-id="852a3-138">Position</span></span> | <span data-ttu-id="852a3-139">A posição do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="852a3-139">The position of the device.</span></span> |
| <span data-ttu-id="852a3-140">Rotação</span><span class="sxs-lookup"><span data-stu-id="852a3-140">Rotation</span></span> | <span data-ttu-id="852a3-141">A rotação do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="852a3-141">The rotation of the device.</span></span> |
| <span data-ttu-id="852a3-142">Rotação e posição</span><span class="sxs-lookup"><span data-stu-id="852a3-142">Rotation And Position</span></span> | <span data-ttu-id="852a3-143">A posição e a rotação do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="852a3-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="852a3-144">O valor padrão para o tipo de rastreamento é **rotação e posição**, para habilitar a experiência de controle mais rica.</span><span class="sxs-lookup"><span data-stu-id="852a3-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="852a3-145">**Tipo de atualização**</span><span class="sxs-lookup"><span data-stu-id="852a3-145">**Update Type**</span></span>

<span data-ttu-id="852a3-146">O tipo de atualização define em quais pontos, durante o processamento de quadros, os dados de pose serão amostrados.</span><span class="sxs-lookup"><span data-stu-id="852a3-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="852a3-147">As opções disponíveis são descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="852a3-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="852a3-148">Opção</span><span class="sxs-lookup"><span data-stu-id="852a3-148">Option</span></span> | <span data-ttu-id="852a3-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="852a3-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="852a3-150">Antes da renderização</span><span class="sxs-lookup"><span data-stu-id="852a3-150">Before Render</span></span> | <span data-ttu-id="852a3-151">Logo antes da renderização.</span><span class="sxs-lookup"><span data-stu-id="852a3-151">Just before rendering.</span></span> |
| <span data-ttu-id="852a3-152">Atualizar</span><span class="sxs-lookup"><span data-stu-id="852a3-152">Update</span></span> | <span data-ttu-id="852a3-153">Durante a fase de atualização do quadro.</span><span class="sxs-lookup"><span data-stu-id="852a3-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="852a3-154">Atualizar e antes de renderizar</span><span class="sxs-lookup"><span data-stu-id="852a3-154">Update And Before Render</span></span> | <span data-ttu-id="852a3-155">Durante a fase de atualização e logo antes da renderização.</span><span class="sxs-lookup"><span data-stu-id="852a3-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="852a3-156">O valor padrão para o tipo de rastreamento **é Update And Before Render**, para habilitar a menor latência de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="852a3-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="852a3-157">Confira também</span><span class="sxs-lookup"><span data-stu-id="852a3-157">See also</span></span>

- [<span data-ttu-id="852a3-158">Visão geral do sistema de câmera</span><span class="sxs-lookup"><span data-stu-id="852a3-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="852a3-159">Criando um provedor de configurações de câmera</span><span class="sxs-lookup"><span data-stu-id="852a3-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
