---
title: Ferramenta de mapeamento de controlador
description: Documentação sobre a ferramenta de mapeamento do controlador no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176176"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="d8abf-104">Ferramenta de mapeamento de controlador</span><span class="sxs-lookup"><span data-stu-id="d8abf-104">Controller mapping tool</span></span>

<span data-ttu-id="d8abf-105">A ferramenta de mapeamento de controlador é uma ferramenta de tempo de execução (no dispositivo ou na editor) que permite aos desenvolvedores determinar rapidamente o eixo de entrada do Unity e os mapeamentos de botão para um controlador de hardware (por exemplo: controlador de movimento).</span><span class="sxs-lookup"><span data-stu-id="d8abf-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="d8abf-106">Essa ferramenta é muito útil ao desenvolver suporte para um novo controlador de hardware.</span><span class="sxs-lookup"><span data-stu-id="d8abf-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="d8abf-107">Ele também pode ajudar a confirmar um problema de mapeamento de controle suspeito na classe de suporte para um controlador existente.</span><span class="sxs-lookup"><span data-stu-id="d8abf-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Ferramenta de mapeamento de controlador](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="d8abf-109">Usando a ferramenta de mapeamento de controlador</span><span class="sxs-lookup"><span data-stu-id="d8abf-109">Using the controller mapping tool</span></span>

<span data-ttu-id="d8abf-110">Para começar a usar a ferramenta de mapeamento de controlador, navegue até **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** e abra a cena **ControllerMappingTool** .</span><span class="sxs-lookup"><span data-stu-id="d8abf-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="d8abf-111">Depois que a cena for carregada, o projeto poderá ser executado no editor, usando o modo de reprodução ou compilado e executado em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d8abf-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="d8abf-112">Para examinar os mapeamentos do Unity para um controlador:</span><span class="sxs-lookup"><span data-stu-id="d8abf-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="d8abf-113">Conexão controlador</span><span class="sxs-lookup"><span data-stu-id="d8abf-113">Connect the controller</span></span>
- <span data-ttu-id="d8abf-114">Pressione cada botão e mova cada eixo</span><span class="sxs-lookup"><span data-stu-id="d8abf-114">Press each button and move each axis</span></span>
- <span data-ttu-id="d8abf-115">Observe os mapeamentos na exibição</span><span class="sxs-lookup"><span data-stu-id="d8abf-115">Note the mappings in the display</span></span>
- <span data-ttu-id="d8abf-116">Atualizar os mapeamentos de controle no provedor de dados do sistema de entrada para o controlador</span><span class="sxs-lookup"><span data-stu-id="d8abf-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="d8abf-117">a ferramenta de mapeamento de controlador não faz uso do Microsoft Mixed reality Toolkit components.</span><span class="sxs-lookup"><span data-stu-id="d8abf-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="d8abf-118">Ele se comunica diretamente com o Unity para determinar e exibir os mapeamentos de controle.</span><span class="sxs-lookup"><span data-stu-id="d8abf-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="d8abf-119">Todos os controles são exibidos</span><span class="sxs-lookup"><span data-stu-id="d8abf-119">All controls display</span></span>

<span data-ttu-id="d8abf-120">O painel de exibição grande relata o estado de todos os eixos de entrada e botões de Unity definidos (por exemplo: eixo 10, botão 3).</span><span class="sxs-lookup"><span data-stu-id="d8abf-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="d8abf-121">Esse painel fornece uma exibição completa do estado do controlador.</span><span class="sxs-lookup"><span data-stu-id="d8abf-121">This panel provides a complete view of the state of the controller.</span></span>

![Todos os controles são exibidos](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="d8abf-123">Exibição de controles ativos</span><span class="sxs-lookup"><span data-stu-id="d8abf-123">Active controls display</span></span>

<span data-ttu-id="d8abf-124">O painel de exibição menor e estreito mostra o axed de entrada do Unity e os botões que estão em um estado ativo (por exemplo: um botão é pressionado).</span><span class="sxs-lookup"><span data-stu-id="d8abf-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="d8abf-125">A exibição de controles ativos fornece uma exibição resumida fácil de ler do estado do controlador.</span><span class="sxs-lookup"><span data-stu-id="d8abf-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![Exibição de controles ativos](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="d8abf-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="d8abf-127">See also</span></span>

- [<span data-ttu-id="d8abf-128">Criando um provedor de dados do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="d8abf-128">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="d8abf-129">Ferramenta InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="d8abf-129">InputFeatureUsage tool</span></span>](input-feature-usage-tool.md)
