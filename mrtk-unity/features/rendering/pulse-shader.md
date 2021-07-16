---
title: Sombreador de pulso
description: Descrição em sombreadores de pulso em MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0b26242d71bbe080e440f9c52a009e29000ab00b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224204"
---
# <a name="pulse-shader"></a><span data-ttu-id="5b94f-104">Sombreador de pulso</span><span class="sxs-lookup"><span data-stu-id="5b94f-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="5b94f-106">Use o sombreador de pulso para animar um efeito de pulso visual sobre a reconstrução da superfície, a malha da mão articulada ou qualquer outra malha.</span><span class="sxs-lookup"><span data-stu-id="5b94f-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="5b94f-107">Sombreador e material</span><span class="sxs-lookup"><span data-stu-id="5b94f-107">Shader and material</span></span>

<span data-ttu-id="5b94f-108">Os materiais a seguir usam o sombreador **SR_Triangles** .</span><span class="sxs-lookup"><span data-stu-id="5b94f-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="5b94f-109">Você pode configurar várias opções, como cor de preenchimento, cor da linha e cor do pulso.</span><span class="sxs-lookup"><span data-stu-id="5b94f-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="5b94f-110">**MRTK_Pulse_SpatialMeshBlue. passe-partout**</span><span class="sxs-lookup"><span data-stu-id="5b94f-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="5b94f-111">**MRTK_Pulse_SpatialMeshPurple. passe-partout**</span><span class="sxs-lookup"><span data-stu-id="5b94f-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="5b94f-112">**MRTK_Pulse_ArticulatedHandMeshBlue. passe-partout**</span><span class="sxs-lookup"><span data-stu-id="5b94f-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="5b94f-113">**MRTK_Pulse_ArticulatedHandMeshPurple. passe-partout**</span><span class="sxs-lookup"><span data-stu-id="5b94f-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="5b94f-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5b94f-114">Prerequisites</span></span>

<span data-ttu-id="5b94f-115">para o exemplo de malha espacial, verifique se MRTK_Pulse_SpatialMeshBlue. esteira ou MRTK_Pulse_SpatialMeshPurple. passe-partout está atribuído em objeto MixedRealityToolkit-> perfil de conscientização espacial-> exibir Configurações Material visível.</span><span class="sxs-lookup"><span data-stu-id="5b94f-115">For the spatial mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned under MixedRealityToolkit object -> Spatial Awareness Profile -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="5b94f-116">para o exemplo de malha à mão, certifique-se de que MRTK_Pulse_ArticulatedHandMeshBlue. esteira ou MRTK_Pulse_ArticulatedHandMeshPurple. passe-partout seja atribuído em ArticulatedHandMesh. pré-fabricado, que deve ser atribuído em MRTK Configurações-> entrada-> mão > de malha.</span><span class="sxs-lookup"><span data-stu-id="5b94f-116">For the hand mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="5b94f-117">Como ele funciona</span><span class="sxs-lookup"><span data-stu-id="5b94f-117">How it works</span></span>

<span data-ttu-id="5b94f-118">O sombreador de malha à mão usa UVs para mapear o pulso ao longo da malha à mão e para esmaecer o pulso.</span><span class="sxs-lookup"><span data-stu-id="5b94f-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="5b94f-119">O sombreador de reconstrução de superfície usa as posições de vértice para mapear o pulso.</span><span class="sxs-lookup"><span data-stu-id="5b94f-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="5b94f-120">Exemplo de malha espacial – PulseShaderSpatialMeshExample. Unity</span><span class="sxs-lookup"><span data-stu-id="5b94f-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="5b94f-121">semelhante à experiência de shell de HoloLens 2, você pode apontar e tocar o ar com a mão ray para gerar um efeito de pulsing na malha espacial.</span><span class="sxs-lookup"><span data-stu-id="5b94f-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="5b94f-122">A cena de exemplo contém o objeto ExampleSpatialMesh, que é um teste de dados de malha espacial para o modo de jogo do Unity.</span><span class="sxs-lookup"><span data-stu-id="5b94f-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="5b94f-123">Este objeto será desabilitado e oculto no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5b94f-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="5b94f-124">O script **PulseShaderSpatialMeshHandler. cs** gera o efeito de pulso na malha espacial na posição do ponto de acesso se `PulseOnSelect` for verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="5b94f-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="5b94f-125">A  `Auto Pulse` propriedade também pode ser definida como true no material em si para uma animação repetida.</span><span class="sxs-lookup"><span data-stu-id="5b94f-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="5b94f-126">Na cena de exemplo, esse script é anexado ao PulseShaderSpatialMeshParent pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="5b94f-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="5b94f-127">Esse pré-fabricado é referenciado no perfil de conscientização espacial por meio da propriedade pré-fabricado de malha espacial de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5b94f-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="5b94f-128">Durante o tempo de execução, o PulseShaderSpatialMeshParent pré-fabricado e é instanciado e adicionado à hierarquia de malha espacial (somente no dispositivo, esse comportamento não pode ser observado no editor).</span><span class="sxs-lookup"><span data-stu-id="5b94f-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="5b94f-129">Exemplo de malha à mão – PulseShaderHandMeshExample. Unity</span><span class="sxs-lookup"><span data-stu-id="5b94f-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="5b94f-130">Esta cena de exemplo demonstra a visualização de malha à mão usando o sombreador de pulso.</span><span class="sxs-lookup"><span data-stu-id="5b94f-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="5b94f-131">quando uma mão for detectada pelo dispositivo HoloLens, a animação pulse será disparada uma vez.</span><span class="sxs-lookup"><span data-stu-id="5b94f-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="5b94f-132">Esse comentário visual pode aumentar a confiança da interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b94f-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="5b94f-133">O script **PulseShaderHandMeshHandler. cs** gera um efeito de pulso no material atribuído.</span><span class="sxs-lookup"><span data-stu-id="5b94f-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="5b94f-134">Por padrão, "pulso na mão detectada" está marcado.</span><span class="sxs-lookup"><span data-stu-id="5b94f-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
