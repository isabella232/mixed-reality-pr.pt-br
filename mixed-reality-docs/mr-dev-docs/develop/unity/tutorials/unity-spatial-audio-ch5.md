---
title: Tutoriais de áudio espacial – 5. Usar o reverb para adicionar distância ao áudio espacial
description: Adicione um efeito reverb para aprimorar a noção de variação de distância ao áudio espacial.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade misturada, UWP, Windows 10, HRTF, função de transferência relacionada à cabeça, reverb, Microsoft Spatializer, mixer de áudio, reverb SFX
ms.openlocfilehash: 8adc92eb96cb8ebd2cc5fff14d522bcfe72733cc5748183dd6db59d753e12a3e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192952"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Usar o reverb para adicionar distância ao áudio espacial

## <a name="overview"></a>Visão geral

No tutorial anterior, você adicionou espacialização para os sons para dar a eles uma noção de direção neste tutorial, você adicionará um efeito reverb para dar aos sons uma noção de distância.

## <a name="objectives"></a>Objetivos

* Melhore a distância percebida das fontes de som adicionando o reverb.
* Controlar a distância percebida do som usando a distância do ouvinte para o holograma.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Adicionar um grupo de mixers e um efeito reverb

Em [Espacializar a interação do botão soa Tutorial](unity-spatial-audio-ch2.md), adicionamos um mixer. O mixer inclui um Grupo **por** padrão chamado **Mestre.** Como só queremos aplicar um efeito reverb a alguns sons, vamos adicionar um segundo Grupo para esses sons. Para adicionar um Grupo, clique com o botão  direito do mouse no grupo Mestre no Mixer de **Áudio,** escolha Adicionar grupo filho e dê um nome adequado, por _exemplo, Efeito de Sala_:

![Adicionar grupo filho](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

Cada **Grupo** tem seu próprio conjunto de efeitos. Adicione um efeito reverb ao novo grupo clicando em **Adicionar...** no novo grupo e escolhendo **Reverb SFX**:

![Adicionar reverb SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

Na terminologia de áudio, o áudio original nãoverberado é chamado de caminho de secagem e o áudio após a filtragem com o filtro reverb é chamado de _caminho quente._ Ambos os caminhos são enviados para a saída de áudio e seus pontos fortes relativos nessa mistura são chamados de _combinação de umidade/secagem._ A combinação de umidade/secagem afeta fortemente a sensação de distância.

O **Reverb SFX** inclui controles para ajustar a mistura de umidade/umidade dentro do efeito. Como o **plug-in do Microsoft Spatializer** lida com o caminho de secagem, vamos usar o **Reverb SFX** apenas para o caminho de umidade. No painel Inspetor do seu **Reverb SFX:**

* De acordo **com a propriedade Nível** de Secagem como a configuração mais baixa (-10000 mB)
* Definir a **propriedade Room** como a configuração mais alta (0 mB)

![Propriedades de Reverb do SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

As outras configurações controlam a sensação da sala simulada. Em particular, **Tempo de Decaimento** está relacionado ao tamanho do quarto percebido.

## <a name="enable-reverb-on-the-video-playback"></a>Habilitar o reverb na reprodução de vídeo

Há duas etapas para habilitar o reverb em uma fonte de áudio:

* Rotear **a fonte de** áudio para o grupo **apropriado**
* Definir o **plug-in Microsoft Spatializer** para passar áudio para o **Grupo** para processamento

Nas etapas a seguir, você ajustará o script para controlar o roteamento de áudio e anexará um script de controle fornecido com o plug-in **Microsoft Spatializer** para alimentar dados no reverb.

Com o **Quad** selecionado na Hierarquia, clique em **Adicionar** Componente na janela Inspetor e adicione o Nível de Envio de Efeito de Sala **(Script)**:

![Adicionar script de nível de envio](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> A menos que você **habilita** o recurso Nível de Envio de Efeito De Sala do plug-in **do Microsoft Spatializer,** ele não envia nenhum áudio de volta para o mecanismo de áudio do Unity para processamento de efeito.

O **componente Nível** de Envio de Efeito De Sala inclui um controle de grafo que define o nível do áudio enviado ao mecanismo de áudio do Unity para processamento reverb. Para abrir o controle de grafo, clique no Nível de Envio **de Efeito De Sala**.  Clique e arraste a curva verde para baixo para definir o nível como cerca de -30dB:

![Ajustar a curva de reverb](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

Em seguida, descomente as quatro linhas comentadas no script **SpatializeOnOff.** O script agora terá esta aparência:

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

Depois que essas linhas são não comentadas, ela adiciona duas propriedades ao Inspetor do **script SpatializeOnOff**. atribua-os na janela Inspetor **do componente SpatializeOnOff** do **Quad.**

Com o objeto Quad ainda selecionado na Hierarquia, na janela Inspetor, localize o componente **SpatializeOnOff Script** e :

* Definir a **propriedade Grupo de Efeitos de Sala** para o novo grupo de mixer efeito de sala
* Definir a **propriedade Grupo Mestre** como o grupo de mixers Mestre

![Spatialize On Off Estendido](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>Parabéns

Você concluiu os tutoriais de áudio espacial do HoloLens 2 para Unity. Experimente o aplicativo em um HoloLens 2 ou Unity. Quando você clica no botão no aplicativo para ativar a espacialização, o script roteia o áudio do vídeo para o Grupo de Efeitos da Sala para adicionar o reverb. Ao alternar para estéreo, ele roteia o áudio para o grupo Mestre e evita adicionar reverb.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
