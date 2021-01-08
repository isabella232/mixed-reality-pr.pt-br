---
title: Habilitar e desabilitar o áudio espacial em tempo de execução
description: Saiba como escrever um script C# que usa um botão para habilitar e desabilitar a espacial de áudio em tempo de execução.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer
ms.openlocfilehash: eaaf8a05088b5bab674ca11b15b0c63383faa479
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007336"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="171ed-104">Habilitando e desabilitando a espacial em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="171ed-104">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="171ed-105">Objetivos</span><span class="sxs-lookup"><span data-stu-id="171ed-105">Objectives</span></span>

<span data-ttu-id="171ed-106">Neste 4º Capítulo, você vai:</span><span class="sxs-lookup"><span data-stu-id="171ed-106">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="171ed-107">Adicionar um novo script para controlar a espacialização em um objeto de jogo</span><span class="sxs-lookup"><span data-stu-id="171ed-107">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="171ed-108">Direcionar o script de controle de espacial de ações de botão</span><span class="sxs-lookup"><span data-stu-id="171ed-108">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="171ed-109">Adicionar script de controle de espacial</span><span class="sxs-lookup"><span data-stu-id="171ed-109">Add spatialization control script</span></span>

<span data-ttu-id="171ed-110">Clique com o botão direito do mouse no painel **projeto** e crie um novo script C# escolhendo **criar-> script c#**.</span><span class="sxs-lookup"><span data-stu-id="171ed-110">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="171ed-111">Nomeie o seu script como "SpatializeOnOff".</span><span class="sxs-lookup"><span data-stu-id="171ed-111">Name your script "SpatializeOnOff".</span></span>

![Criar script](images/spatial-audio/create-script.png)

<span data-ttu-id="171ed-113">Clique duas vezes no script no painel de **projeto** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="171ed-113">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="171ed-114">Substitua o conteúdo do script padrão pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="171ed-114">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="171ed-115">Várias linhas do script são comentadas. Essas linhas não serão comentadas no [capítulo 5](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="171ed-115">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="171ed-116">Para habilitar ou desabilitar a espacialização, o script ajusta apenas a propriedade **spatialBlend** , deixando a propriedade de **espacial** habilitada.</span><span class="sxs-lookup"><span data-stu-id="171ed-116">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="171ed-117">Nesse modo, o Unity ainda aplica a curva de **volume** .</span><span class="sxs-lookup"><span data-stu-id="171ed-117">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="171ed-118">Caso contrário, se o usuário tivesse de desabilitar a espacial quando estiver longe da origem, ele ouviria o volume aumentar abruptamente.</span><span class="sxs-lookup"><span data-stu-id="171ed-118">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="171ed-119">Se você preferir desabilitar totalmente a espacialização, modifique o script para ajustar também a **Propriedade booliana** booleana da variável **SourceObject** .</span><span class="sxs-lookup"><span data-stu-id="171ed-119">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="171ed-120">Anexe o script e o conduza do botão</span><span class="sxs-lookup"><span data-stu-id="171ed-120">Attach your script and drive it from the button</span></span>

<span data-ttu-id="171ed-121">No painel **Inspetor** do **Quad**, clique em **Adicionar componente** e adicione o script **Spatial-off** :</span><span class="sxs-lookup"><span data-stu-id="171ed-121">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![Adicionar script ao Quad](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="171ed-123">No componente **espacial em diante** do **Quad**:</span><span class="sxs-lookup"><span data-stu-id="171ed-123">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="171ed-124">Localize o **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** Subject na **hierarquia**:</span><span class="sxs-lookup"><span data-stu-id="171ed-124">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subject in the **Hierarchy**:</span></span>

![Localizar o objeto PressableButtonHoloLens2 na hierarquia](images/spatial-audio/pressable-button-object.png)

2. <span data-ttu-id="171ed-126">Arraste a entidade **TextMeshPro** para o campo **ButtonTextObject** do componente **espacial-off**</span><span class="sxs-lookup"><span data-stu-id="171ed-126">Drag the **TextMeshPro** subject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="171ed-127">Após essas alterações, o componente **espacial ativado** do **Quad** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="171ed-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Espacial desabilitada básica](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="171ed-129">Para definir o botão para chamar o script **Spatial on off** quando o botão for liberado, abra o painel **Inspetor** do objeto **PressableButtonHoloLens2** , localize o componente **interagindo** e:</span><span class="sxs-lookup"><span data-stu-id="171ed-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="171ed-130">Localizar a região **OnClick ()** da subseção de **eventos**</span><span class="sxs-lookup"><span data-stu-id="171ed-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="171ed-131">Arraste o **Quad** da **hierarquia** para o slot do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="171ed-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="171ed-132">Selecione **SpatializeOnOff. SwapSpatialization** na caixa suspensa ação.</span><span class="sxs-lookup"><span data-stu-id="171ed-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="171ed-133">Após essas alterações, o componente **interagindo** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="171ed-133">After these changes, the **Interactable** component will look like this:</span></span>

![Configurações de ação do botão](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="171ed-135">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="171ed-135">Next steps</span></span>

<span data-ttu-id="171ed-136">Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="171ed-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="171ed-137">No aplicativo, agora você pode tocar no botão para ativar e desativar a espacial no vídeo.</span><span class="sxs-lookup"><span data-stu-id="171ed-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="171ed-138">Ao testar no editor do Unity, pressione a barra de espaço e role com a roda de rolagem para ativar a simulação de mão.</span><span class="sxs-lookup"><span data-stu-id="171ed-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="171ed-139">Capítulo 5</span><span class="sxs-lookup"><span data-stu-id="171ed-139">Chapter 5</span></span>](unity-spatial-audio-ch5.md) 

