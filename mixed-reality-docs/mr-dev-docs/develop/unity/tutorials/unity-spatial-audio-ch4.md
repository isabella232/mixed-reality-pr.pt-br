---
title: Tutoriais de áudio espacial – 4. Habilitar e desabilitar o áudio espacial em tempo de execução
description: Use um botão para habilitar e desabilitar a espacialização de áudio em tempo de executar.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade misturada, UWP, Windows 10, HRTF, função de transferência relacionada à cabeça, reverb, Microsoft Spatializer
ms.openlocfilehash: 9d0fa432f2e653cdd6820cb6c779cc1acc5c4b15
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712735"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="3aa5d-105">4. Habilitando e desabilitando a espacialização em tempo de executar</span><span class="sxs-lookup"><span data-stu-id="3aa5d-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="3aa5d-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3aa5d-106">Overview</span></span>

<span data-ttu-id="3aa5d-107">Neste tutorial, você aprenderá a Habilitar e desabilitar a espacialização em tempo de executar e testá-la no editor do Unity e no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="3aa5d-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3aa5d-108">Objectives</span></span>

* <span data-ttu-id="3aa5d-109">Adicionar um novo script para controlar a espacialização em um objeto de jogo</span><span class="sxs-lookup"><span data-stu-id="3aa5d-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="3aa5d-110">Conduzir o script de controle de espacialização de ações de botão</span><span class="sxs-lookup"><span data-stu-id="3aa5d-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="3aa5d-111">Adicionar script de controle de espacialização</span><span class="sxs-lookup"><span data-stu-id="3aa5d-111">Add spatialization control script</span></span>

 <span data-ttu-id="3aa5d-112">Clique com o botão direito do mouse na janela Projeto e escolha Criar Script C# para criar um novo script C#, insira um nome adequado para o script, por  >   exemplo, _SpatializeOnOff:_</span><span class="sxs-lookup"><span data-stu-id="3aa5d-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![Criar script](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

<span data-ttu-id="3aa5d-114">Clique duas vezes no script na janela Projeto para abri-lo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="3aa5d-115">Substitua o conteúdo do script padrão pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="3aa5d-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="3aa5d-116">Várias linhas do script são comentadas. Essas linhas não serão comentados no [Próximo Capítulo: Usando o reverb para adicionar distância ao áudio espacial.](unity-spatial-audio-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="3aa5d-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="3aa5d-117">Para habilitar ou desabilitar a espacialização, o script ajusta apenas a **propriedade spatialBlend,** deixando a **propriedade spatialization** habilitada.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="3aa5d-118">Nesse modo, o Unity ainda aplica a **curva volume.**</span><span class="sxs-lookup"><span data-stu-id="3aa5d-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="3aa5d-119">Caso contrário, se o usuário desabilitar a espacialização quando estiver longe da origem, ele ouvirá o volume aumentar de forma tão repentina.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="3aa5d-120">Se você preferir desabilitar totalmente a espacialização,  modifique o script para também ajustar a propriedade booliana de espacialização da **variável SourceObject.**</span><span class="sxs-lookup"><span data-stu-id="3aa5d-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="3aa5d-121">Anexe o script e o conduza do botão</span><span class="sxs-lookup"><span data-stu-id="3aa5d-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="3aa5d-122">Selecione **Quad** na Hierarquia e, na janela Inspetor, use o botão Adicionar Componente para adicionar **SpatializeOnOff(Script)**</span><span class="sxs-lookup"><span data-stu-id="3aa5d-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![Adicionar script ao quad](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

<span data-ttu-id="3aa5d-124">Na hierarquia, **localize PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="3aa5d-125">Com o **objeto Quad** ainda selecionado na Hierarquia, na janela Inspetor, localize o componente **Spatialize On Off (Script)** e Arraste e solte o Componente **TextMeshPro** do PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![Encontrar o objeto PressableButtonHoloLens2 na hierarquia](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

<span data-ttu-id="3aa5d-127">Para definir o botão para chamar o script **SpatializeOnOff** quando o botão for liberado, você precisará configurar o script interacionável.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="3aa5d-128">Na janela Hierarquia, selecione **PressableButtonHoloLens2**.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="3aa5d-129">Na janela Inspetor, localize **o componente Interactable (Script)** e clique no ícone + em Evento OnClick ().</span><span class="sxs-lookup"><span data-stu-id="3aa5d-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="3aa5d-130">Com o objeto **PressableButtonHoloLens2** ainda selecionado na janela Hierarquia, clique e arraste o objeto **Quad** da janela Hierarquia para o campo **Vazio Nenhum (Objeto)** do evento que você acabou de adicionar para fazer com que o objeto ButtonParent escute o evento de clique de botão deste botão:</span><span class="sxs-lookup"><span data-stu-id="3aa5d-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="3aa5d-131">Clique no menu suspenso **Nenhuma Função** do mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="3aa5d-132">Em seguida, **selecione SpatializeOnOff**  >  **SwapSpatialization ()** para ativar e desativar o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="3aa5d-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![Configurações de ação de botão](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="3aa5d-134">Parabéns</span><span class="sxs-lookup"><span data-stu-id="3aa5d-134">Congratulations</span></span>

<span data-ttu-id="3aa5d-135">Neste tutorial, você aprendeu a habilitar e desabilitar a espacialização em tempo de executar, testar o aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="3aa5d-136">No aplicativo, agora você pode clicar no botão para ativar e desativar a espacialização do áudio.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="3aa5d-137">No próximo tutorial, você adicionará um efeito reverb para dar uma noção de distância aos sons.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="3aa5d-138">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="3aa5d-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3aa5d-139">Próximo Tutorial: 5. Usar o reverb para adicionar distância ao áudio espacial</span><span class="sxs-lookup"><span data-stu-id="3aa5d-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
