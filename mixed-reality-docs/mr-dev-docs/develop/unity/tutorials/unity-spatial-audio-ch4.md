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
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. habilitar e desabilitar a espacialização em tempo de execução

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a habilitar e a desabilitar a espacial em tempo de execução e a testar isso no editor de Unity e no HoloLens 2.

## <a name="objectives"></a>Objetivos

* Adicionar um novo script para controlar a espacialização em um objeto de jogo
* Direcionar o script de controle de espacial de ações de botão

## <a name="add-spatialization-control-script"></a>Adicionar script de controle de espacial

 Clique com o botão direito do mouse na janela do projeto e escolha **criar**  >  **script c#** para criar um novo script c#, insira um nome adequado para o script, por exemplo, _SpatializeOnOff_:

![Criar script](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

Clique duas vezes no script na janela do projeto para abri-lo no Visual Studio. Substitua o conteúdo do script padrão pelo seguinte:

> [!NOTE]
> Várias linhas do script são comentadas. Estas linhas não serão comentadas no [próximo capítulo: usando o reverberar para adicionar distância ao áudio espacial](unity-spatial-audio-ch5.md).

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
> Para habilitar ou desabilitar a espacialização, o script ajusta apenas a propriedade **spatialBlend** , deixando a propriedade de **espacial** habilitada. Nesse modo, o Unity ainda aplica a curva de **volume** . Caso contrário, se o usuário tivesse de desabilitar a espacial quando estiver longe da origem, ele ouviria o volume aumentar abruptamente.
> Se você preferir desabilitar totalmente a espacialização, modifique o script para ajustar também a **Propriedade booliana** booleana da variável **SourceObject** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Anexe o script e o conduza do botão

Selecione **Quad** na hierarquia e, na janela Inspetor, use o botão Adicionar componente para adicionar **SpatializeOnOff (script)**

![Adicionar script ao Quad](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

Na hierarquia, localize **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.

Com o **Quad** Object ainda selecionado na hierarquia, na janela do Inspetor, localize o componente **Spatial (script) espacial** e arraste e solte o componente **TextMeshPro** do PressableButtonHoloLens2.

![Localizar o objeto PressableButtonHoloLens2 na hierarquia](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

Para definir o botão para chamar o script **SpatializeOnOff** quando o botão for liberado, você precisará configurar o script de interação.

Na janela hierarquia, selecione o **PressableButtonHoloLens2**. Na janela Inspetor, localize o componente de **interação (script)** e clique no ícone + no evento onclique ().

* Com o objeto **PressableButtonHoloLens2** ainda selecionado na janela hierarquia, clique e arraste o objeto **Quad** da janela hierarquia para o campo **nenhum (objeto)** vazio do evento que você acabou de adicionar para fazer com que o objeto ButtonParent Ouça o evento de clique do botão do botão:

* Clique no menu suspenso **Nenhuma Função** do mesmo evento. Em seguida, selecione **SpatializeOnOff**  >  **SwapSpatialization ()** para ativar e desativar o áudio espacial

![Configurações de ação do botão](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a habilitar e desabilitar a spatialização em tempo de execução, testar o aplicativo em um HoloLens 2 ou no editor do Unity. No aplicativo, agora você pode clicar no botão para ativar e desativar a spatialização do áudio.

No próximo tutorial, você adicionará um efeito de reverberação para dar aos sons uma sensação de distância.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Próximo tutorial: 5. usando o reverberar para adicionar distância ao áudio espacial](unity-spatial-audio-ch5.md)
