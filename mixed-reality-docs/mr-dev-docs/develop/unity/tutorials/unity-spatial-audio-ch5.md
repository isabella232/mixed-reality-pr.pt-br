---
title: Tutoriais de áudio espacial-5. Usar o reverb para adicionar distância ao áudio espacial
description: Adicione um efeito de reverberação para melhorar o sentido de variação de distância para áudio espacial.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, mixer de áudio, reverbo SFX
ms.openlocfilehash: 3d19bb0b22c507eb692a752aa318ecb82a1cf2f7
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578355"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="a8895-105">5. Usar o reverb para adicionar distância ao áudio espacial</span><span class="sxs-lookup"><span data-stu-id="a8895-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="a8895-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="a8895-106">Overview</span></span>

<span data-ttu-id="a8895-107">No tutorial anterior, você adicionou a espacialização dos sons para dar a eles uma ideia de direção neste tutorial. você adicionará um efeito de reverberação para dar aos sons uma sensação de distância.</span><span class="sxs-lookup"><span data-stu-id="a8895-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="a8895-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a8895-108">Objectives</span></span>

* <span data-ttu-id="a8895-109">Melhore a distância percebida de fontes de som adicionando o reverberar.</span><span class="sxs-lookup"><span data-stu-id="a8895-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="a8895-110">Controle a distância percebida do som usando a distância do ouvinte para o holograma.</span><span class="sxs-lookup"><span data-stu-id="a8895-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="a8895-111">Adicionar um grupo de mixers e um efeito de reverberação</span><span class="sxs-lookup"><span data-stu-id="a8895-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="a8895-112">No [tutorial de sons de interação do botão espacial](unity-spatial-audio-ch2.md), adicionamos um mixer.</span><span class="sxs-lookup"><span data-stu-id="a8895-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="a8895-113">O mixer inclui um **grupo** por padrão chamado **Master**.</span><span class="sxs-lookup"><span data-stu-id="a8895-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="a8895-114">Como só desejamos aplicar um efeito de reverberação a alguns sons, vamos adicionar um segundo grupo para esses sons.</span><span class="sxs-lookup"><span data-stu-id="a8895-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="a8895-115">Para adicionar um grupo, clique com o botão direito do mouse no grupo mestre no **mixer de áudio** escolha **Adicionar grupo filho** e forneça um nome adequado para o exemplo de _efeito de sala_:</span><span class="sxs-lookup"><span data-stu-id="a8895-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![Adicionar grupo filho](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

<span data-ttu-id="a8895-117">Cada **grupo** tem seu próprio conjunto de efeitos.</span><span class="sxs-lookup"><span data-stu-id="a8895-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="a8895-118">Adicione um efeito de reverberação ao novo grupo clicando em **Adicionar...** no novo grupo e escolhendo o **reverberar de SFX**:</span><span class="sxs-lookup"><span data-stu-id="a8895-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Adicionar reverbo SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

<span data-ttu-id="a8895-120">Na terminologia de áudio, o áudio unreverberated original é chamado de _caminho seco_, e o áudio após a filtragem com o filtro de reverberação é chamado de _caminho úmida_.</span><span class="sxs-lookup"><span data-stu-id="a8895-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="a8895-121">Ambos os caminhos são enviados para a saída de áudio, e seus pontos fortes relativos nessa mistura são chamados de _mistura úmida/seca_.</span><span class="sxs-lookup"><span data-stu-id="a8895-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="a8895-122">A mistura úmida/seca afeta fortemente a sensação de distância.</span><span class="sxs-lookup"><span data-stu-id="a8895-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="a8895-123">O **inverbo SFX** inclui controles para ajustar a mistura úmida/seca dentro do efeito.</span><span class="sxs-lookup"><span data-stu-id="a8895-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="a8895-124">Como o plug-in **Spatializer da Microsoft** trata o caminho seco, usaremos o único **verbo SFX** somente para o caminho úmida.</span><span class="sxs-lookup"><span data-stu-id="a8895-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="a8895-125">No painel Inspetor de seu **reverbo SFX**:</span><span class="sxs-lookup"><span data-stu-id="a8895-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="a8895-126">Definir a propriedade de **nível seco** para a configuração mais baixa (-10000 MB)</span><span class="sxs-lookup"><span data-stu-id="a8895-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="a8895-127">Definir a **Propriedade Room** como a configuração mais alta (0 MB)</span><span class="sxs-lookup"><span data-stu-id="a8895-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![Propriedades de reverberação SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

<span data-ttu-id="a8895-129">As outras configurações controlam a sensação da sala simulada.</span><span class="sxs-lookup"><span data-stu-id="a8895-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="a8895-130">Em particular, o **tempo de decaimento** está relacionado ao tamanho de sala percebido.</span><span class="sxs-lookup"><span data-stu-id="a8895-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="a8895-131">Habilitar reverberação na reprodução de vídeo</span><span class="sxs-lookup"><span data-stu-id="a8895-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="a8895-132">Há duas etapas para habilitar o reverberador em uma fonte de áudio:</span><span class="sxs-lookup"><span data-stu-id="a8895-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="a8895-133">Rotear a **fonte de áudio** para o **grupo** apropriado</span><span class="sxs-lookup"><span data-stu-id="a8895-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="a8895-134">Defina o plug-in **Microsoft Spatializer** para passar áudio para o **grupo** para processamento</span><span class="sxs-lookup"><span data-stu-id="a8895-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="a8895-135">Nas etapas a seguir, você ajustará o script para controlar o roteamento de áudio e anexará um script de controle fornecido com o plug-in do **Microsoft Spatializer** para alimentar dados no reverbo.</span><span class="sxs-lookup"><span data-stu-id="a8895-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="a8895-136">Com o **Quad** selecionado na hierarquia, clique em **Adicionar componente** na janela Inspetor e adicione o **nível de envio de efeito Room (script)**:</span><span class="sxs-lookup"><span data-stu-id="a8895-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![Adicionar script de nível de envio](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a8895-138">A menos que você habilite o recurso de **nível de envio de efeito Room** do plug-in do **Microsoft Spatializer** , ele não envia nenhum áudio de volta para o mecanismo de áudio do Unity para processamento de efeito.</span><span class="sxs-lookup"><span data-stu-id="a8895-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="a8895-139">O componente de **nível de envio de efeito Room** inclui um controle de gráfico que define o nível do áudio enviado ao mecanismo de áudio do Unity para o processamento de reverberação.</span><span class="sxs-lookup"><span data-stu-id="a8895-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="a8895-140">Para abrir o controle de gráfico, clique no **nível de envio de efeito de sala**.</span><span class="sxs-lookup"><span data-stu-id="a8895-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="a8895-141">Clique e arraste a curva verde para baixo para definir o nível como About-30dB:</span><span class="sxs-lookup"><span data-stu-id="a8895-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![Ajustar curva de reverberação](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

<span data-ttu-id="a8895-143">Em seguida, remova os comentários das 4 linhas comentadas no script **SpatializeOnOff** .</span><span class="sxs-lookup"><span data-stu-id="a8895-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="a8895-144">O script agora terá esta aparência:</span><span class="sxs-lookup"><span data-stu-id="a8895-144">The script will now look like this:</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

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
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="a8895-145">Depois que essas linhas são desmarcadas, elas adicionam duas propriedades ao inspetor do **script SpatializeOnOff**.</span><span class="sxs-lookup"><span data-stu-id="a8895-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="a8895-146">atribua-os na janela Inspetor do componente **SpatializeOnOff** do **Quad**.</span><span class="sxs-lookup"><span data-stu-id="a8895-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="a8895-147">Com o quad Object ainda selecionado na hierarquia, na janela do Inspetor, localize o componente de **script SpatializeOnOff** e:</span><span class="sxs-lookup"><span data-stu-id="a8895-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="a8895-148">Defina a propriedade **grupo de efeitos da sala** como o novo grupo do mixer de efeito Room</span><span class="sxs-lookup"><span data-stu-id="a8895-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="a8895-149">Definir a propriedade do **grupo mestre** como o grupo do mixer mestre</span><span class="sxs-lookup"><span data-stu-id="a8895-149">Set the **Master Group** property to the Master mixer group</span></span>

![Espacial eslongada estendida](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="a8895-151">Parabéns</span><span class="sxs-lookup"><span data-stu-id="a8895-151">Congratulations</span></span>

<span data-ttu-id="a8895-152">Você concluiu os tutoriais de áudio espacial 2 do HoloLens para o Unity.</span><span class="sxs-lookup"><span data-stu-id="a8895-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="a8895-153">Experimente o aplicativo em um HoloLens 2 ou Unity.</span><span class="sxs-lookup"><span data-stu-id="a8895-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="a8895-154">Quando você clica no botão no aplicativo para ativar a espacialização, o script roteará o áudio do vídeo para o grupo de efeitos da sala para adicionar o reverberador.</span><span class="sxs-lookup"><span data-stu-id="a8895-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="a8895-155">Ao alternar para o estéreo, ele encaminhará o áudio para o grupo mestre e evitará adicionar o reverberador.</span><span class="sxs-lookup"><span data-stu-id="a8895-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="a8895-156">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="a8895-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
