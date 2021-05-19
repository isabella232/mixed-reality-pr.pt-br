---
title: Ferramenta de uso de recursos de entrada
description: Entrada da documentaçãoA ferramenta InputFeatureUsage no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145013"
---
# <a name="inputfeatureusage-tool"></a><span data-ttu-id="bef86-104">Ferramenta InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="bef86-104">InputFeatureUsage tool</span></span>

<span data-ttu-id="bef86-105">A ferramenta InputFeatureUsage é uma ferramenta de runtime (no dispositivo ou no editor) que permite aos desenvolvedores determinar rapidamente a InputFeatureUsages do Unity disponível para uma fonte de entrada detectada (por exemplo: controlador de movimento ou mão articulada).</span><span class="sxs-lookup"><span data-stu-id="bef86-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="bef86-106">Essa cena só funciona no Unity 2019.3 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="bef86-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="bef86-107">Essa ferramenta é muito útil ao desenvolver suporte para um novo controlador de hardware.</span><span class="sxs-lookup"><span data-stu-id="bef86-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="bef86-108">Ele também pode ajudar a confirmar um problema de mapeamento de controle suspeito na classe de suporte para um controlador existente.</span><span class="sxs-lookup"><span data-stu-id="bef86-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Ferramenta InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="bef86-110">Usando a ferramenta InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="bef86-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="bef86-111">Para começar com a ferramenta InputFeatureUsage, navegue até **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** e abra a cena **InputFeatureUsageTool.**</span><span class="sxs-lookup"><span data-stu-id="bef86-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="bef86-112">Depois que a cena tiver sido carregada, o projeto poderá ser executado no editor, usando o modo de reprodução ou criado e executado em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bef86-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="bef86-113">Para examinar os mapeamentos do Unity para um controlador:</span><span class="sxs-lookup"><span data-stu-id="bef86-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="bef86-114">Conectar o controlador</span><span class="sxs-lookup"><span data-stu-id="bef86-114">Connect the controller</span></span>
- <span data-ttu-id="bef86-115">Pressione cada botão e mova cada eixo</span><span class="sxs-lookup"><span data-stu-id="bef86-115">Press each button and move each axis</span></span>
- <span data-ttu-id="bef86-116">Observe os usos de recursos na exibição</span><span class="sxs-lookup"><span data-stu-id="bef86-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="bef86-117">Atualizar os mapeamentos de controle no provedor de dados do sistema de entrada para o controlador</span><span class="sxs-lookup"><span data-stu-id="bef86-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="bef86-118">A ferramenta InputFeatureUsage não usa componentes do Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="bef86-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="bef86-119">Ele se comunica diretamente com o Unity para determinar e exibir os usos de recursos.</span><span class="sxs-lookup"><span data-stu-id="bef86-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="bef86-120">Painéis</span><span class="sxs-lookup"><span data-stu-id="bef86-120">Panels</span></span>

<span data-ttu-id="bef86-121">Os painéis exibem o estado atual de todas as InputFeatureUsages relatadas em todas as fontes de entrada do Unity detectadas.</span><span class="sxs-lookup"><span data-stu-id="bef86-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="bef86-122">O painel menor na parte superior lista os nomes de todas as fontes detectadas.</span><span class="sxs-lookup"><span data-stu-id="bef86-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="bef86-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="bef86-123">See also</span></span>

- [<span data-ttu-id="bef86-124">Criando um provedor de dados do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="bef86-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="bef86-125">Ferramenta de mapeamento de controlador</span><span class="sxs-lookup"><span data-stu-id="bef86-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
