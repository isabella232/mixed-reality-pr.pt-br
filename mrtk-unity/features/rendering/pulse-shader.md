---
title: Sombreador de pulso
description: descrição em Sombreadores de pulso no MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: e03c021689b6701b86ae25ba9fa253ece1368428
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144939"
---
# <a name="pulse-shader"></a><span data-ttu-id="60fe2-104">Sombreador de pulso</span><span class="sxs-lookup"><span data-stu-id="60fe2-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="60fe2-106">Use o sombreador de pulso para animar um efeito de pulso visual sobre a reconstrução da superfície, malha de mão articulada ou qualquer outra malha.</span><span class="sxs-lookup"><span data-stu-id="60fe2-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="60fe2-107">Sombreador e material</span><span class="sxs-lookup"><span data-stu-id="60fe2-107">Shader and material</span></span>

<span data-ttu-id="60fe2-108">Os materiais a **seguir SR_Triangles** sombreador.</span><span class="sxs-lookup"><span data-stu-id="60fe2-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="60fe2-109">Você pode configurar várias opções, como cor de preenchimento, cor da linha e cor do pulso.</span><span class="sxs-lookup"><span data-stu-id="60fe2-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="60fe2-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="60fe2-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="60fe2-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="60fe2-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="60fe2-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="60fe2-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="60fe2-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="60fe2-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="60fe2-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="60fe2-114">Prerequisites</span></span>

<span data-ttu-id="60fe2-115">Para o exemplo de malha espacial, verifique se MRTK_Pulse_ArticulatedHandMeshBlue.mat ou MRTK_Pulse_ArticulatedHandMeshPurple.mat está atribuído em Configurações do MRTK -> Reconhecimento Espacial -configurações de exibição > -> Material Visível.</span><span class="sxs-lookup"><span data-stu-id="60fe2-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="60fe2-116">Para o exemplo de malha manual, verifique se MRTK_Pulse_SpatialMeshBlue.mat ou MRTK_Pulse_SpatialMeshPurple.mat está atribuído em ArticulatedHandMesh.prefab, que deve ser atribuído em Configurações do MRTK -> Entrada -> Hand Tracking -> Hand Mesh Prefab.</span><span class="sxs-lookup"><span data-stu-id="60fe2-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="60fe2-117">Como ele funciona</span><span class="sxs-lookup"><span data-stu-id="60fe2-117">How it works</span></span>

<span data-ttu-id="60fe2-118">O sombreador de malha de mão usa UVs para mapear o pulso ao longo da malha da mão e esmaecer o pulso.</span><span class="sxs-lookup"><span data-stu-id="60fe2-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="60fe2-119">O sombreador de reconstrução da superfície usa as posições de vértice para mapear o pulso.</span><span class="sxs-lookup"><span data-stu-id="60fe2-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="60fe2-120">Exemplo de malha espacial – PulseShaderSpatialMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="60fe2-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="60fe2-121">Semelhante à experiência de shell do HoloLens 2, você pode apontar e tocar no ar com o raio de mão para gerar um efeito pulsante na malha espacial.</span><span class="sxs-lookup"><span data-stu-id="60fe2-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="60fe2-122">A cena de exemplo contém o objeto ExampleSpatialMesh, que é um teste de dados de malha espacial para o modo de jogo do Unity.</span><span class="sxs-lookup"><span data-stu-id="60fe2-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="60fe2-123">Esse objeto será desabilitado e oculto no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60fe2-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="60fe2-124">O script **PulseShaderSpatialMeshHandler.cs** gerará o efeito de pulso na malha espacial na posição do ponto de acerto, se `PulseOnSelect` for true.</span><span class="sxs-lookup"><span data-stu-id="60fe2-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="60fe2-125">A  `Auto Pulse` propriedade também pode ser definida como true no material em si para uma animação repetida.</span><span class="sxs-lookup"><span data-stu-id="60fe2-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="60fe2-126">Na cena de exemplo, esse script é anexado ao PulseShaderSpatialMeshParent pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="60fe2-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="60fe2-127">Esse pré-fabricado é referenciado no perfil de conscientização espacial por meio da propriedade pré-fabricado de malha espacial de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="60fe2-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="60fe2-128">Durante o tempo de execução, o PulseShaderSpatialMeshParent pré-fabricado e é instanciado e adicionado à hierarquia de malha espacial (somente no dispositivo, esse comportamento não pode ser observado no editor).</span><span class="sxs-lookup"><span data-stu-id="60fe2-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="60fe2-129">Exemplo de malha à mão – PulseShaderHandMeshExample. Unity</span><span class="sxs-lookup"><span data-stu-id="60fe2-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="60fe2-130">Esta cena de exemplo demonstra a visualização de malha à mão usando o sombreador de pulso.</span><span class="sxs-lookup"><span data-stu-id="60fe2-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="60fe2-131">Quando uma mão é detectada pelo dispositivo HoloLens, a animação Pulse será disparada uma vez.</span><span class="sxs-lookup"><span data-stu-id="60fe2-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="60fe2-132">Esse comentário visual pode aumentar a confiança da interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="60fe2-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="60fe2-133">O script **PulseShaderHandMeshHandler. cs** gera um efeito de pulso no material atribuído.</span><span class="sxs-lookup"><span data-stu-id="60fe2-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="60fe2-134">Por padrão, "pulso na mão detectada" está marcado.</span><span class="sxs-lookup"><span data-stu-id="60fe2-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
