---
title: Usar o reverb para adicionar distância ao áudio espacial
description: Saiba como adicionar um efeito de reverberação para aprimorar o sentido de variação de distância para áudio espacial em um aplicativo de realidade misturada.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, mixer de áudio, reverbo SFX
ms.openlocfilehash: 6c04ac1e4b52c7eb6104d54c184c789bec413852
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006356"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="cb546-104">Usar o reverb para adicionar distância ao áudio espacial</span><span class="sxs-lookup"><span data-stu-id="cb546-104">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="cb546-105">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cb546-105">Objectives</span></span>

<span data-ttu-id="cb546-106">Nos capítulos anteriores, adicionamos a espacialização a sons para dar a eles uma ideia de direção.</span><span class="sxs-lookup"><span data-stu-id="cb546-106">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="cb546-107">Neste quinto capítulo, vamos adicionar um efeito de reverberação para dar aos sons uma sensação de distância.</span><span class="sxs-lookup"><span data-stu-id="cb546-107">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="cb546-108">Nossos objetivos são:</span><span class="sxs-lookup"><span data-stu-id="cb546-108">Our objectives are to:</span></span>
* <span data-ttu-id="cb546-109">Melhorar a distância percebida de fontes de som adicionando o reverberador</span><span class="sxs-lookup"><span data-stu-id="cb546-109">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="cb546-110">Controle a distância percebida do som usando a distância do ouvinte para o holograma</span><span class="sxs-lookup"><span data-stu-id="cb546-110">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="cb546-111">Adicionar um grupo de mixers e um efeito de reverberação</span><span class="sxs-lookup"><span data-stu-id="cb546-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="cb546-112">No [capítulo 2](unity-spatial-audio-ch2.md), adicionamos um mixer.</span><span class="sxs-lookup"><span data-stu-id="cb546-112">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="cb546-113">O mixer inclui um **grupo** por padrão chamado **Master**.</span><span class="sxs-lookup"><span data-stu-id="cb546-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="cb546-114">Como só desejamos aplicar um efeito de reverberação a alguns sons, vamos adicionar um segundo **grupo** para esses sons.</span><span class="sxs-lookup"><span data-stu-id="cb546-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="cb546-115">Para adicionar um **grupo**, clique com o botão direito do mouse no grupo **mestre** no **mixer de áudio** e escolha **Adicionar grupo filho**:</span><span class="sxs-lookup"><span data-stu-id="cb546-115">To add a **Group**, right click on the **Master** group in the **Audio Mixer** and choose **Add child group**:</span></span>

![Adicionar grupo filho](images/spatial-audio/add-child-group.png)

<span data-ttu-id="cb546-117">Neste exemplo, nomeamos o novo grupo "efeito de sala".</span><span class="sxs-lookup"><span data-stu-id="cb546-117">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="cb546-118">Cada **grupo** tem seu próprio conjunto de efeitos.</span><span class="sxs-lookup"><span data-stu-id="cb546-118">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="cb546-119">Adicione um efeito de reverberação ao novo grupo clicando em **Adicionar...** no novo grupo e escolhendo o **reverberar de SFX**:</span><span class="sxs-lookup"><span data-stu-id="cb546-119">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Adicionar reverbo SFX](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="cb546-121">Na terminologia de áudio, o áudio unreverberated original é chamado de _caminho seco_, e o áudio após a filtragem com o filtro de reverberação é chamado de _caminho úmida_.</span><span class="sxs-lookup"><span data-stu-id="cb546-121">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="cb546-122">Ambos os caminhos são enviados para a saída de áudio, e seus pontos fortes relativos nessa mistura são chamados de _mistura úmida/seca_.</span><span class="sxs-lookup"><span data-stu-id="cb546-122">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="cb546-123">A mistura úmida/seca afeta fortemente a sensação de distância.</span><span class="sxs-lookup"><span data-stu-id="cb546-123">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="cb546-124">O **inverbo SFX** inclui controles para ajustar a mistura úmida/seca dentro do efeito.</span><span class="sxs-lookup"><span data-stu-id="cb546-124">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="cb546-125">Como o plug-in **Spatializer da Microsoft** trata o caminho seco, usaremos o único **verbo SFX** somente para o caminho úmida.</span><span class="sxs-lookup"><span data-stu-id="cb546-125">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="cb546-126">No painel **Inspetor** de seu **reverbo SFX**:</span><span class="sxs-lookup"><span data-stu-id="cb546-126">On the **Inspector** pane of your **SFX Reverb**:</span></span>
* <span data-ttu-id="cb546-127">Definir a propriedade de nível seco para a configuração mais baixa (-10000 mB)</span><span class="sxs-lookup"><span data-stu-id="cb546-127">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="cb546-128">Definir a propriedade Room como a configuração mais alta (0 mB)</span><span class="sxs-lookup"><span data-stu-id="cb546-128">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="cb546-129">Após essas alterações, o painel de **Inspetor** do **reverberador SFX** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="cb546-129">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![Propriedades de reverberação SFX](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="cb546-131">As outras configurações controlam a sensação da sala simulada.</span><span class="sxs-lookup"><span data-stu-id="cb546-131">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="cb546-132">Em particular, o **tempo de decaimento** está relacionado ao tamanho de sala percebido.</span><span class="sxs-lookup"><span data-stu-id="cb546-132">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="cb546-133">Habilitar reverberação na reprodução de vídeo</span><span class="sxs-lookup"><span data-stu-id="cb546-133">Enable reverb on the video playback</span></span>

<span data-ttu-id="cb546-134">Há duas etapas para habilitar o reverberador em uma fonte de áudio:</span><span class="sxs-lookup"><span data-stu-id="cb546-134">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="cb546-135">Rotear a **fonte de áudio** para o **grupo** apropriado</span><span class="sxs-lookup"><span data-stu-id="cb546-135">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="cb546-136">Defina o plug-in **Microsoft Spatializer** para passar áudio para o **grupo** para processamento</span><span class="sxs-lookup"><span data-stu-id="cb546-136">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="cb546-137">Nas etapas a seguir, vamos ajustar nosso script para controlar o roteamento de áudio e anexar um script de controle fornecido com o plug-in do **Microsoft Spatializer** para alimentar dados no reverberador.</span><span class="sxs-lookup"><span data-stu-id="cb546-137">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="cb546-138">No painel **Inspetor** para o **Quad**, clique em **Adicionar componente** e adicione o script de **nível de envio de efeito Room** :</span><span class="sxs-lookup"><span data-stu-id="cb546-138">On the **Inspector** pane for the **Quad**, click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![Adicionar script de nível de envio](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="cb546-140">A menos que você habilite o recurso de **nível de envio de efeito Room** do plug-in do **Microsoft Spatializer** , ele não envia nenhum áudio de volta para o mecanismo de áudio do Unity para processamento de efeito.</span><span class="sxs-lookup"><span data-stu-id="cb546-140">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="cb546-141">O componente de **nível de envio de efeito Room** inclui um controle de gráfico que define o nível do áudio enviado ao mecanismo de áudio do Unity para o processamento de reverberação.</span><span class="sxs-lookup"><span data-stu-id="cb546-141">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="cb546-142">Clique e arraste a curva para baixo para definir o nível como About-30dB:</span><span class="sxs-lookup"><span data-stu-id="cb546-142">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![Ajustar curva de reverberação](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="cb546-144">Em seguida, remova os comentários das 4 linhas comentadas no script **SpatializeOnOff** .</span><span class="sxs-lookup"><span data-stu-id="cb546-144">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="cb546-145">O script agora terá esta aparência:</span><span class="sxs-lookup"><span data-stu-id="cb546-145">The script will now look like this:</span></span>
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

<span data-ttu-id="cb546-146">Remover os comentários dessas linhas adiciona duas propriedades ao painel de **Inspetor** para o script.</span><span class="sxs-lookup"><span data-stu-id="cb546-146">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="cb546-147">Para defini-las, no painel **Inspetor** do componente **espacial on off** do **Quad**:</span><span class="sxs-lookup"><span data-stu-id="cb546-147">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad**:</span></span>
* <span data-ttu-id="cb546-148">Defina a propriedade **grupo de efeitos da sala** como o novo grupo do mixer de efeito Room</span><span class="sxs-lookup"><span data-stu-id="cb546-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="cb546-149">Definir a propriedade do **grupo mestre** como o grupo do mixer mestre</span><span class="sxs-lookup"><span data-stu-id="cb546-149">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="cb546-150">Após essas alterações, as propriedades **espaciais off** ficarão assim:</span><span class="sxs-lookup"><span data-stu-id="cb546-150">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Espacial eslongada estendida](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="cb546-152">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="cb546-152">Next steps</span></span>

<span data-ttu-id="cb546-153">Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="cb546-153">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="cb546-154">Agora, ao tocar o botão no aplicativo para ativar a espacialização, o script roteará o áudio do vídeo para o grupo de efeitos Room para adicionar o reverberador.</span><span class="sxs-lookup"><span data-stu-id="cb546-154">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="cb546-155">Ao alternar para o estéreo, ele encaminhará o áudio para o grupo mestre e evitará adicionar o reverberador.</span><span class="sxs-lookup"><span data-stu-id="cb546-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="cb546-156">Você concluiu os tutoriais de áudio espacial 2 do HoloLens para o Unity.</span><span class="sxs-lookup"><span data-stu-id="cb546-156">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="cb546-157">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="cb546-157">Congratulations!</span></span>


