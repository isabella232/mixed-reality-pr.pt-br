---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097874"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="711bb-101">Unity 2019/2020 + Plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="711bb-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="711bb-102">Como garantir a capacidade do microfone e adicionar o provedor de dados de entrada de fala</span><span class="sxs-lookup"><span data-stu-id="711bb-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="711bb-103">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade do Microfone** está esmaecida:</span><span class="sxs-lookup"><span data-stu-id="711bb-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Habilitar a funcionalidade de microfone](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="711bb-105">A funcionalidade do Microfone deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#configuring-the-unity-project) quando você configurou o projeto do Unity no início desta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="711bb-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="711bb-106">No entanto, se não estiver habilitada, faça isso agora.</span><span class="sxs-lookup"><span data-stu-id="711bb-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="711bb-107">Na janela Hierarquia, selecione o objeto MixedRealityToolkit e na janela Inspetor, navegue até a guia Entrada:</span><span class="sxs-lookup"><span data-stu-id="711bb-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="711bb-108">Expanda o item **Provedores de Dados de Entrada** e clique no botão **+ Adicionar Provedor de Dados** para adicionar um novo provedor de dados</span><span class="sxs-lookup"><span data-stu-id="711bb-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Provedor de dados para adicionar novos comandos de fala](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="711bb-110">Atribua a opção **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** ao campo **Tipo** do novo provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="711bb-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Como adicionar configurações de novos comandos de fala](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="711bb-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="711bb-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="711bb-113">Como garantir a capacidade do microfone e adicionar o provedor de dados de entrada de fala</span><span class="sxs-lookup"><span data-stu-id="711bb-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="711bb-114">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade do Microfone** está esmaecida:</span><span class="sxs-lookup"><span data-stu-id="711bb-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Habilitar a capacidade do microfone para OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="711bb-116">A funcionalidade do Microfone deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#configuring-the-unity-project) quando você configurou o projeto do Unity no início desta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="711bb-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="711bb-117">No entanto, se não estiver habilitada, faça isso agora.</span><span class="sxs-lookup"><span data-stu-id="711bb-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="711bb-118">Na janela Hierarquia, selecione o objeto MixedRealityToolkit e na janela Inspetor, navegue até a guia Entrada:</span><span class="sxs-lookup"><span data-stu-id="711bb-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="711bb-119">Expanda o item **Provedores de Dados de Entrada** e clique no botão **+ Adicionar Provedor de Dados** para adicionar um novo provedor de dados</span><span class="sxs-lookup"><span data-stu-id="711bb-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Como adicionar novos comandos de fala ao OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="711bb-121">Atribua a opção **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** ao campo **Tipo** do novo provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="711bb-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Como adicionar novos comandos de fala para configurações do OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="711bb-123">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="711bb-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="711bb-124">Garantir que a funcionalidade do Microfone esteja habilitada</span><span class="sxs-lookup"><span data-stu-id="711bb-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="711bb-125">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade do Microfone** está esmaecida:</span><span class="sxs-lookup"><span data-stu-id="711bb-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Habilitar a funcionalidade de microfone](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="711bb-127">A funcionalidade do Microfone deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) quando você configurou o projeto do Unity no início desta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="711bb-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="711bb-128">No entanto, se não estiver habilitada, faça isso agora.</span><span class="sxs-lookup"><span data-stu-id="711bb-128">However, if it is not enabled, make sure you enable it now.</span></span>
