---
title: Configurando sua configuração de XR
description: Mantenha-se atualizado sobre as recomendações mais recentes de configuração de XR do Unity para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394560"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="98128-104">Configurando sua configuração de XR</span><span class="sxs-lookup"><span data-stu-id="98128-104">Setting up your XR configuration</span></span>

<span data-ttu-id="98128-105">Ao iniciar um novo projeto do Unity, você tem três opções diferentes para lidar com suas necessidades de XR:</span><span class="sxs-lookup"><span data-stu-id="98128-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="98128-106">Plug-in openXR</span><span class="sxs-lookup"><span data-stu-id="98128-106">OpenXR plugin</span></span>
* <span data-ttu-id="98128-107">Plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="98128-107">Windows XR plugin</span></span>
* <span data-ttu-id="98128-108">Plug-in XR herddo</span><span class="sxs-lookup"><span data-stu-id="98128-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="98128-109">Configurando seu projeto com o MRTK</span><span class="sxs-lookup"><span data-stu-id="98128-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="98128-110">O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="98128-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="98128-111">A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="98128-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="98128-112">O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="98128-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="98128-113">Experimente os nossos tutoriais do MRTK</span><span class="sxs-lookup"><span data-stu-id="98128-113">Try out our MRTK tutorials</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

<span data-ttu-id="98128-114">Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.</span><span class="sxs-lookup"><span data-stu-id="98128-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="98128-115">Usando o MRTK com suporte a OpenXR</span><span class="sxs-lookup"><span data-stu-id="98128-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="98128-116">MRTK-Unity versão 2.7 oferece melhor suporte para o plug-in OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="98128-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="98128-117">Abra a [Ferramenta de Recursos de Realidade](welcome-to-mr-feature-tool.md) Misturada novamente para instalar o Kit de Ferramentas de Realidade Misturada, caso ainda não tenha feito isso.</span><span class="sxs-lookup"><span data-stu-id="98128-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="98128-118">O suporte a OpenXR está no **pacote Foundation.**</span><span class="sxs-lookup"><span data-stu-id="98128-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="98128-119">Consulte a documentação do MRTK [para obter informações mais detalhadas sobre como migrar para o OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="98128-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="98128-120">Ao atualizar de uma versão anterior do MRTK anterior à **2.5.3,** verifique se a seguinte linha está no arquivo **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="98128-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="98128-121">Essa linha será adicionada por padrão se você tiver iniciado com o MRTK 2.5.4 ou mais novo.</span><span class="sxs-lookup"><span data-stu-id="98128-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="98128-122">Configuração manual sem MRTK</span><span class="sxs-lookup"><span data-stu-id="98128-122">Manual setup without MRTK</span></span>

<span data-ttu-id="98128-123">Embora a Microsoft e a comunidade tenham criado ferramentas do opensource, como o [MRTK (Kit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) de Ferramentas de Realidade Misturada) que configurará automaticamente o ambiente wmr, muitos desenvolvedores desejam criar suas experiências desde o zero.</span><span class="sxs-lookup"><span data-stu-id="98128-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]
