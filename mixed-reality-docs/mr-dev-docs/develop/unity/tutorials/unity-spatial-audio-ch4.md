---
title: Tutoriais de áudio espacial-4. Habilitar e desabilitar o áudio espacial em tempo de execução
description: Use um botão para habilitar e desabilitar a espacialização de áudio em tempo de execução.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer
ms.openlocfilehash: 26143975707b2cd6141803a6335cec89db5bbd26
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590728"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="e4634-105">4. habilitar e desabilitar a espacialização em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e4634-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="e4634-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e4634-106">Overview</span></span>

<span data-ttu-id="e4634-107">Neste tutorial, você aprenderá a habilitar e a desabilitar a espacial em tempo de execução e a testar isso no editor de Unity e no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e4634-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="e4634-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e4634-108">Objectives</span></span>

* <span data-ttu-id="e4634-109">Adicionar um novo script para controlar a espacialização em um objeto de jogo</span><span class="sxs-lookup"><span data-stu-id="e4634-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="e4634-110">Direcionar o script de controle de espacial de ações de botão</span><span class="sxs-lookup"><span data-stu-id="e4634-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="e4634-111">Adicionar script de controle de espacial</span><span class="sxs-lookup"><span data-stu-id="e4634-111">Add spatialization control script</span></span>

 <span data-ttu-id="e4634-112">Clique com o botão direito do mouse na janela do projeto e escolha **criar**  >  **script c#** para criar um novo script c#, insira um nome adequado para o script, por exemplo, _SpatializeOnOff_:</span><span class="sxs-lookup"><span data-stu-id="e4634-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![Criar script](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

<span data-ttu-id="e4634-114">Clique duas vezes no script na janela do projeto para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4634-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="e4634-115">Substitua o conteúdo do script padrão pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="e4634-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="e4634-116">Várias linhas do script são comentadas. Estas linhas não serão comentadas no [próximo capítulo: usando o reverberar para adicionar distância ao áudio espacial](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="e4634-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="e4634-117">Para habilitar ou desabilitar a espacialização, o script ajusta apenas a propriedade **spatialBlend** , deixando a propriedade de **espacial** habilitada.</span><span class="sxs-lookup"><span data-stu-id="e4634-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="e4634-118">Nesse modo, o Unity ainda aplica a curva de **volume** .</span><span class="sxs-lookup"><span data-stu-id="e4634-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="e4634-119">Caso contrário, se o usuário tivesse de desabilitar a espacial quando estiver longe da origem, ele ouviria o volume aumentar abruptamente.</span><span class="sxs-lookup"><span data-stu-id="e4634-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="e4634-120">Se você preferir desabilitar totalmente a espacialização, modifique o script para ajustar também a **Propriedade booliana** booleana da variável **SourceObject** .</span><span class="sxs-lookup"><span data-stu-id="e4634-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="e4634-121">Anexe o script e o conduza do botão</span><span class="sxs-lookup"><span data-stu-id="e4634-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="e4634-122">Selecione **Quad** na hierarquia e, na janela Inspetor, use o botão Adicionar componente para adicionar **SpatializeOnOff (script)**</span><span class="sxs-lookup"><span data-stu-id="e4634-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![Adicionar script ao Quad](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

<span data-ttu-id="e4634-124">Na hierarquia, localize **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="e4634-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="e4634-125">Com o **Quad** Object ainda selecionado na hierarquia, na janela do Inspetor, localize o componente **Spatial (script) espacial** e arraste e solte o componente **TextMeshPro** do PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="e4634-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![Localizar o objeto PressableButtonHoloLens2 na hierarquia](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

<span data-ttu-id="e4634-127">Para definir o botão para chamar o script **SpatializeOnOff** quando o botão for liberado, você precisará configurar o script de interação.</span><span class="sxs-lookup"><span data-stu-id="e4634-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="e4634-128">Na janela hierarquia, selecione o **PressableButtonHoloLens2**.</span><span class="sxs-lookup"><span data-stu-id="e4634-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="e4634-129">Na janela Inspetor, localize o componente de **interação (script)** e clique no ícone + no evento onclique ().</span><span class="sxs-lookup"><span data-stu-id="e4634-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="e4634-130">Com o objeto **PressableButtonHoloLens2** ainda selecionado na janela hierarquia, clique e arraste o objeto **Quad** da janela hierarquia para o campo **nenhum (objeto)** vazio do evento que você acabou de adicionar para fazer com que o objeto ButtonParent Ouça o evento de clique do botão do botão:</span><span class="sxs-lookup"><span data-stu-id="e4634-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="e4634-131">Clique no menu suspenso **Nenhuma Função** do mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="e4634-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="e4634-132">Em seguida, selecione **SpatializeOnOff**  >  **SwapSpatialization ()** para ativar e desativar o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="e4634-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![Configurações de ação do botão](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="e4634-134">Parabéns</span><span class="sxs-lookup"><span data-stu-id="e4634-134">Congratulations</span></span>

<span data-ttu-id="e4634-135">Neste tutorial, você aprendeu a habilitar e desabilitar a spatialização em tempo de execução, testar o aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="e4634-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="e4634-136">No aplicativo, agora você pode clicar no botão para ativar e desativar a spatialização do áudio.</span><span class="sxs-lookup"><span data-stu-id="e4634-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="e4634-137">No próximo tutorial, você adicionará um efeito de reverberação para dar aos sons uma sensação de distância.</span><span class="sxs-lookup"><span data-stu-id="e4634-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="e4634-138">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="e4634-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e4634-139">Próximo tutorial: 5. usando o reverberar para adicionar distância ao áudio espacial</span><span class="sxs-lookup"><span data-stu-id="e4634-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
