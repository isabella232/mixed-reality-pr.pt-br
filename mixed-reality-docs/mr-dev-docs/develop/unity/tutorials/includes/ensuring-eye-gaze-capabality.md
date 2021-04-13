---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097850"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="76e12-101">Unity 2019/2020 + Plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="76e12-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="76e12-102">Como garantir a capacidade de entrada com o olhar e como adicionar o provedor de dados do olhar</span><span class="sxs-lookup"><span data-stu-id="76e12-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="76e12-103">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade de Entrada de Foco de Olho** está esmaecida:</span><span class="sxs-lookup"><span data-stu-id="76e12-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Janela Configurador de Projeto do MRTK no Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="76e12-105">A funcionalidade de Entrada de Foco deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#configuring-the-unity-project) quando você configurou o projeto do Unity no início desta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="76e12-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="76e12-106">No entanto, se não estiver habilitada, faça isso agora.</span><span class="sxs-lookup"><span data-stu-id="76e12-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="76e12-107">Na janela Hierarquia, selecione o objeto MixedRealityToolkit e na janela Inspetor, navegue até a guia Entrada:</span><span class="sxs-lookup"><span data-stu-id="76e12-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="76e12-108">Expanda o item **Provedores de Dados de Entrada** e clique no botão **+ Adicionar Provedor de Dados** para adicionar um novo provedor de dados</span><span class="sxs-lookup"><span data-stu-id="76e12-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Como adicionar o provedor de dados de olhar 1](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="76e12-110">Atribua a opção **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** ao campo **Tipo** do novo provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="76e12-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Como adicionar o provedor de dados de olhar 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="76e12-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="76e12-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="76e12-113">Como garantir a capacidade de entrada com o olhar e como adicionar o provedor de dados do olhar</span><span class="sxs-lookup"><span data-stu-id="76e12-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="76e12-114">Na janela Hierarquia, selecione o objeto MixedRealityToolkit e na janela Inspetor, navegue até a guia Entrada:</span><span class="sxs-lookup"><span data-stu-id="76e12-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="76e12-115">Expanda o item **Provedores de Dados de Entrada** e clique no botão **+ Adicionar Provedor de Dados** para adicionar um novo provedor de dados</span><span class="sxs-lookup"><span data-stu-id="76e12-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Como adicionar o provedor de dados de olhar 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="76e12-117">Atribua a opção **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** ao campo **Tipo** do novo provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="76e12-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Como adicionar o provedor de dados de olhar 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="76e12-119">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="76e12-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="76e12-120">Como garantir que a funcionalidade de Entrada de Foco de Olho esteja habilitada</span><span class="sxs-lookup"><span data-stu-id="76e12-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="76e12-121">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade de Entrada de Foco de Olho** está esmaecida:</span><span class="sxs-lookup"><span data-stu-id="76e12-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Janela Configurador de Projeto do MRTK no Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="76e12-123">A funcionalidade de Entrada de Foco deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) quando você configurou o projeto do Unity no início desta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="76e12-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="76e12-124">No entanto, se não estiver habilitada, faça isso agora.</span><span class="sxs-lookup"><span data-stu-id="76e12-124">However, if it is not enabled, make sure you enable it now.</span></span>
