---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603698"
---
# <a name="openxr"></a>[<span data-ttu-id="ae215-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ae215-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ae215-102">Para começar a usar um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:</span><span class="sxs-lookup"><span data-stu-id="ae215-102">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae215-103">Configurar um novo projeto OpenXR com o MRTK</span><span class="sxs-lookup"><span data-stu-id="ae215-103">Set up a new OpenXR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="ae215-104">Se você estiver atualizando um projeto do MRTK existente para **o OpenXR,** primeiro será melhor atualizar o MRTK-Unity para a versão mais recente (versão 2.7.2 ou posterior) para obter correções de chave para compatibilidade com o plug-in openXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="ae215-104">If you're upgrading an **existing MRTK project to OpenXR**, you'll first want to upgrade MRTK-Unity to the latest version (version 2.7.2 or later) to get key fixes for compatibility with the Mixed Reality OpenXR plugin.</span></span>  <span data-ttu-id="ae215-105">Use a [Ferramenta de Recursos de Realidade](../../welcome-to-mr-feature-tool.md) Misturada para atualizar para a versão mais recente do MRTK e siga as etapas manuais de instalação do [OpenXR abaixo.](#manual-setup-without-mrtk)</span><span class="sxs-lookup"><span data-stu-id="ae215-105">Use the [Mixed Reality Feature Tool](../../welcome-to-mr-feature-tool.md) to upgrade to the latest version of MRTK and then follow the [manual OpenXR setup steps below](#manual-setup-without-mrtk).</span></span> <span data-ttu-id="ae215-106">Consulte a documentação do MRTK para obter informações mais detalhadas sobre como migrar um projeto [do MRTK existente para o OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="ae215-106">See the MRTK documentation for [more in-depth information on migrating an existing MRTK project to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="ae215-107">Ao atualizar de uma versão anterior do MRTK anterior à **2.5.3,** verifique se a seguinte linha está no arquivo **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="ae215-107">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="ae215-108">Essa linha será adicionada por padrão se você tiver iniciado com o MRTK 2.5.4 ou mais novo.</span><span class="sxs-lookup"><span data-stu-id="ae215-108">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="ae215-109">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="ae215-109">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="ae215-110">Para começar a usar um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:</span><span class="sxs-lookup"><span data-stu-id="ae215-110">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae215-111">Configurar um novo projeto Windows XR com o MRTK</span><span class="sxs-lookup"><span data-stu-id="ae215-111">Set up a new Windows XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[<span data-ttu-id="ae215-112">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="ae215-112">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="ae215-113">Para começar a usar um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:</span><span class="sxs-lookup"><span data-stu-id="ae215-113">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae215-114">Configurar um novo projeto XR herdado com o MRTK</span><span class="sxs-lookup"><span data-stu-id="ae215-114">Set up a new Legacy XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=wsa)