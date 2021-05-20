---
title: Controladores no MRTK
description: Documentação sobre como usar vários controladores com o MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Controladores, HP Reverb, Oculus, HTC Vive, Hands
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145452"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="ad002-104">Controladores no MRTK</span><span class="sxs-lookup"><span data-stu-id="ad002-104">Controllers in MRTK</span></span>

<span data-ttu-id="ad002-105">O MRTK tem suporte para muitos controladores diferentes.</span><span class="sxs-lookup"><span data-stu-id="ad002-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="ad002-106">Muitos controladores, como HTC Vive Ltds e HTC Vive Bares, funcionarão na nativo depois que um aplicativo criado com o MRTK for lançado no dispositivo compatível.</span><span class="sxs-lookup"><span data-stu-id="ad002-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="ad002-107">Outros controladores, como mãos articuladas na Oculus Quest e nos controladores HP Reverb G2, exigem pacotes adicionais antes que sejam reconhecidos pelo MRTK.</span><span class="sxs-lookup"><span data-stu-id="ad002-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="ad002-108">Este documento descreverá os cenários comuns em que pacotes extras precisam ser instalados.</span><span class="sxs-lookup"><span data-stu-id="ad002-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="ad002-109">Para obter informações adicionais sobre controladores, visite a [**página de recursos**](../features/input/controllers.md).</span><span class="sxs-lookup"><span data-stu-id="ad002-109">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="ad002-110">Para depurar problemas com controladores, consulte a [ **ferramenta de mapeamento do controlador**](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="ad002-110">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="ad002-111">Controladores HP Reverb G2</span><span class="sxs-lookup"><span data-stu-id="ad002-111">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="ad002-112">Para detectar e mostrar os controladores HP Reverb G2 ao usar o MRTK, siga estas etapas para instalar o pacote [**Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="ad002-112">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="ad002-113">Depois que esse pacote for instalado, nenhuma outra alteração nos perfis padrão precisará ser feita para que os controladores sejam lançados no HP Reverb.</span><span class="sxs-lookup"><span data-stu-id="ad002-113">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="ad002-114">Para exibir os controladores no editor, você precisa garantir que está usando o usando o Plug-in [**OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span><span class="sxs-lookup"><span data-stu-id="ad002-114">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="ad002-115">Controladores Oculus</span><span class="sxs-lookup"><span data-stu-id="ad002-115">Oculus Controllers</span></span> 

<span data-ttu-id="ad002-116">Para visualizar modelos de controlador Oculus, siga as instruções de implantação do Oculus Deployment.</span><span class="sxs-lookup"><span data-stu-id="ad002-116">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="ad002-117">Se você quiser mostrar as mãos virtuais ao usar os controladores, certifique-se de que Renderizar mãos do Avatar em vez de **controladores** está marcado no SDK XR Oculus Gerenciador de Dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ad002-117">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="ad002-118">Caso contrário, desmarque essa opção.</span><span class="sxs-lookup"><span data-stu-id="ad002-118">Otherwise, uncheck this option.</span></span>

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
