---
title: Tutoriais de áudio espacial – 4. Habilitar e desabilitar o áudio espacial em tempo de execução
description: Use um botão para habilitar e desabilitar a espacialização de áudio em tempo de executar.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade misturada, UWP, Windows 10, HRTF, função de transferência relacionada à cabeça, reverb, Microsoft Spatializer
ms.openlocfilehash: 2599e2f360afa4518102ab9535608e9d378264ae87f84a36823d460f934d6a05
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213204"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. Habilitando e desabilitando a espacialização em tempo de executar

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a Habilitar e desabilitar a espacialização em tempo de executar e testá-la no editor do Unity e HoloLens 2.

## <a name="objectives"></a>Objetivos

* Adicionar um novo script para controlar a espacialização em um objeto de jogo
* Conduzir o script de controle de espacialização de ações de botão

## <a name="add-spatialization-control-script"></a>Adicionar script de controle de espacialização

 Clique com o botão direito do mouse na janela Project e escolha Criar Script C# para criar um script C#, insira um nome adequado para o script, por  >   exemplo, _SpatializeOnOff:_

![Criar script](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

Clique duas vezes no script na janela Project para abri-lo Visual Studio. Substitua o conteúdo do script padrão pelo seguinte:

> [!NOTE]
> Várias linhas do script são comentadas. Essas linhas não serão comentados no [Próximo Capítulo: Usando o reverb para adicionar distância ao áudio espacial.](unity-spatial-audio-ch5.md)

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
> Para habilitar ou desabilitar a espacialização, o script ajusta apenas a **propriedade spatialBlend,** deixando a **propriedade spatialization** habilitada. Nesse modo, o Unity ainda aplica a **curva volume.** Caso contrário, se o usuário desabilitar a espacialização quando estiver longe da origem, ele ouvirá o volume aumentar de forma tão repentina.
> Se você preferir desabilitar totalmente a espacialização,  modifique o script para também ajustar a propriedade booliana de espacialização da **variável SourceObject.**

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Anexe o script e o conduza do botão

Selecione **Quad** na Hierarquia e, na janela Inspetor, use o botão Adicionar Componente para adicionar **SpatializeOnOff(Script)**

![Adicionar script ao quad](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

Na hierarquia, **localize PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.

Com o **objeto Quad** ainda selecionado na Hierarquia, na janela Inspetor, localize o componente **Spatialize On Off (Script)** e Arraste e solte o Componente **TextMeshPro** do PressableButtonHoloLens2.

![Encontrar o objeto PressableButtonHoloLens2 na hierarquia](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

Para definir o botão para chamar o script **SpatializeOnOff** quando o botão for liberado, você precisará configurar o script interacionável.

Na janela Hierarquia, selecione **PressableButtonHoloLens2**. Na janela Inspetor, localize **o componente Interactable (Script)** e clique no ícone + em Evento OnClick ().

* Com o objeto **PressableButtonHoloLens2** ainda selecionado na janela Hierarquia, clique e arraste o objeto **Quad** da janela Hierarquia para o campo **Vazio Nenhum (Objeto)** do evento que você acabou de adicionar para fazer com que o objeto ButtonParent escute o evento de clique de botão deste botão:

* Clique no menu suspenso **Nenhuma Função** do mesmo evento. Em seguida, **selecione SpatializeOnOff**  >  **SwapSpatialization ()** para ativar e desativar o áudio espacial

![Configurações de ação de botão](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a habilitar e desabilitar a espacialização em tempo de executar, testar o aplicativo em um HoloLens 2 ou no editor do Unity. No aplicativo, agora você pode clicar no botão para ativar e desativar a espacialização do áudio.

No próximo tutorial, você adicionará um efeito reverb para dar uma noção de distância aos sons.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Próximo Tutorial: 5. Usar o reverb para adicionar distância ao áudio espacial](unity-spatial-audio-ch5.md)
