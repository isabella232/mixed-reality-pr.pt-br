---
title: Controladores de reverbo do HP G2 em um não real
description: Instruções sobre como usar os controladores de reverberação HP reverbo G2 em OpenXR e SteamVR
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Inreal, mecanismo 4, UE4, reverberação, reverbal G2, HP reverbs G2, realidade misturada, desenvolvimento, controladores de movimento, entrada do usuário, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos
ms.openlocfilehash: c9d3ea3a8dd52ed0712f9df5c1a789121a68fd35
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638605"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="69dcb-104">Controladores de reverbo do HP G2 em um não real</span><span class="sxs-lookup"><span data-stu-id="69dcb-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="69dcb-105">Introdução</span><span class="sxs-lookup"><span data-stu-id="69dcb-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69dcb-106">O mecanismo inreal 4,26 e o OpenXR ou o SteamVR são necessários para acessar o plug-in do controlador HP Motion, você precisará trabalhar com os controladores de reverberação da HP.</span><span class="sxs-lookup"><span data-stu-id="69dcb-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="69dcb-107">Portando um aplicativo OpenXR existente</span><span class="sxs-lookup"><span data-stu-id="69dcb-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="69dcb-108">Se nenhuma associação de controlador existir no jogo para o controlador HP Mixed Reality, o tempo de execução do OpenXR tentará remapear as ligações existentes para o controlador ativo.</span><span class="sxs-lookup"><span data-stu-id="69dcb-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will attempt to remap the existing bindings to the active controller.</span></span>  <span data-ttu-id="69dcb-109">Nesse caso, o jogo tem ligações Oculus Touch e nenhuma associação de controlador HP Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="69dcb-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![Remapeando associações existentes quando não existe nenhuma associação de controlador](images/reverb-g2-img-04.png)

<span data-ttu-id="69dcb-111">Os eventos ainda serão disparados, mas se o jogo precisar usar associações específicas de controlador, como o botão de menu à direita, o perfil de interação de realidade mista da HP deverá ser usado.</span><span class="sxs-lookup"><span data-stu-id="69dcb-111">The events will still fire, but if the game needs to make use of controller specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="69dcb-112">Várias associações de controlador podem ser especificadas por ação para dar melhor suporte a dispositivos diferentes.</span><span class="sxs-lookup"><span data-stu-id="69dcb-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![Usando associações de vários controladores](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="69dcb-114">Adicionando mapeamentos de ação de entrada</span><span class="sxs-lookup"><span data-stu-id="69dcb-114">Adding input action mappings</span></span> 

<span data-ttu-id="69dcb-115">Defina uma nova ação e mapeie para um dos pressionamentos de tecla na seção controlador HP Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="69dcb-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![Definindo novas ações e mapeamentos](images/reverb-g2-img-02.png)

<span data-ttu-id="69dcb-117">O controlador do HP reverberar G2 também tem uma alça analógica, que pode ser usada nos mapeamentos de eixo com a associação "eixo de squeeze".</span><span class="sxs-lookup"><span data-stu-id="69dcb-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="69dcb-118">Há uma associação squeeze separada, que deve ser usada para mapeamentos de ação quando o botão de fixação é totalmente pressionado.</span><span class="sxs-lookup"><span data-stu-id="69dcb-118">There is a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![Usando as associações de eixo de squeeze](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="69dcb-120">Adicionando eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="69dcb-120">Adding input events</span></span>

<span data-ttu-id="69dcb-121">Clique com o botão direito do mouse em um plano gráfico e pesquise os novos nomes de ação do sistema de entrada para adicionar eventos para essas ações.</span><span class="sxs-lookup"><span data-stu-id="69dcb-121">Right click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="69dcb-122">Aqui, o plano gráfico está respondendo aos eventos com uma cadeia de caracteres de impressão gerando o botão atual e o estado do eixo.</span><span class="sxs-lookup"><span data-stu-id="69dcb-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![Plano gráfico respondendo a eventos e gerando o estado atual do botão e do eixo](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="69dcb-124">Usando entrada</span><span class="sxs-lookup"><span data-stu-id="69dcb-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="69dcb-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="69dcb-125">See also</span></span>
* [<span data-ttu-id="69dcb-126">Entrada SteamVR</span><span class="sxs-lookup"><span data-stu-id="69dcb-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="69dcb-127">Usando o SteamVR com o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="69dcb-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="69dcb-128">Câmera do Player não real</span><span class="sxs-lookup"><span data-stu-id="69dcb-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)