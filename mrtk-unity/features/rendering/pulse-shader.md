---
title: Sombreador de pulso
description: descrição em Sombreadores de pulso no MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 087806d48c7304d43f8383285cbaa2a12d8bf99a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176314"
---
# <a name="pulse-shader"></a><span data-ttu-id="b1f8a-104">Sombreador de pulso</span><span class="sxs-lookup"><span data-stu-id="b1f8a-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="b1f8a-106">Use o sombreador de pulso para animar um efeito de pulso visual sobre a reconstrução da superfície, malha de mão articulada ou qualquer outra malha.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="b1f8a-107">Sombreador e material</span><span class="sxs-lookup"><span data-stu-id="b1f8a-107">Shader and material</span></span>

<span data-ttu-id="b1f8a-108">Os materiais a **seguir SR_Triangles** sombreador.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="b1f8a-109">Você pode configurar várias opções, como cor de preenchimento, cor da linha e cor do pulso.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="b1f8a-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="b1f8a-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="b1f8a-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="b1f8a-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="b1f8a-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="b1f8a-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="b1f8a-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="b1f8a-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="b1f8a-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b1f8a-114">Prerequisites</span></span>

<span data-ttu-id="b1f8a-115">Para o exemplo de malha espacial, verifique se MRTK_Pulse_ArticulatedHandMeshBlue.mat ou MRTK_Pulse_ArticulatedHandMeshPurple.mat está atribuído em MrTK Configurações -> Spatial Awareness -> Display Configurações -> Visible Material.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="b1f8a-116">Para o exemplo de malha manual, verifique se MRTK_Pulse_SpatialMeshBlue.mat ou MRTK_Pulse_SpatialMeshPurple.mat está atribuído em ArticulatedHandMesh.prefab, que deve ser atribuído no MRTK Configurações -> Input -> Hand Tracking -> Hand Mesh Prefab.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="b1f8a-117">Como ele funciona</span><span class="sxs-lookup"><span data-stu-id="b1f8a-117">How it works</span></span>

<span data-ttu-id="b1f8a-118">O sombreador de malha de mão usa UVs para mapear o pulso ao longo da malha da mão e esmaecer o pulso.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="b1f8a-119">O sombreador de reconstrução da superfície usa as posições de vértice para mapear o pulso.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="b1f8a-120">Exemplo de malha espacial – PulseShaderSpatialMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="b1f8a-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="b1f8a-121">Semelhante à HoloLens shell do 2, você pode apontar e tocar no ar com o raio de mão para gerar um efeito pulsante na malha espacial.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="b1f8a-122">A cena de exemplo contém o objeto ExampleSpatialMesh, que é um teste de dados de malha espacial para o modo de jogo do Unity.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="b1f8a-123">Esse objeto será desabilitado e oculto no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="b1f8a-124">O script **PulseShaderSpatialMeshHandler.cs** gerará o efeito de pulso na malha espacial na posição do ponto de acerto, se `PulseOnSelect` for true.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="b1f8a-125">A  `Auto Pulse` propriedade também pode ser definida como true no próprio material para uma animação repetida.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="b1f8a-126">Na cena de exemplo, esse script é anexado ao pré-fab PulseShaderSpatialMeshParent.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="b1f8a-127">Esse pré-fab é referenciado no Perfil de Reconhecimento Espacial por meio da propriedade Pré-fab de Malha Espacial de Runtime.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="b1f8a-128">Durante o runtime, o pré-fab PulseShaderSpatialMeshParent é instanciado e adicionado à hierarquia de malha espacial (somente no dispositivo, esse comportamento não pode ser observado no editor).</span><span class="sxs-lookup"><span data-stu-id="b1f8a-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="b1f8a-129">Exemplo de malha manual – PulseShaderHandMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="b1f8a-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="b1f8a-130">Esta cena de exemplo demonstra a visualização de malha manual usando o sombreador de pulso.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="b1f8a-131">Quando uma mão é detectada pelo dispositivo HoloLens, a animação de pulso será disparada uma vez.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="b1f8a-132">Os comentários visuais podem aumentar a confiança de interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="b1f8a-133">O script **PulseShaderHandMeshHandler.cs** gera efeito de pulso no material atribuído.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="b1f8a-134">Por padrão, 'Pulse On Hand Detected' é verificado.</span><span class="sxs-lookup"><span data-stu-id="b1f8a-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
