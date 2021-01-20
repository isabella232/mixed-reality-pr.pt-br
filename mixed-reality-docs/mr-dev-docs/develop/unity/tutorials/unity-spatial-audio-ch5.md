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
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Usar o reverb para adicionar distância ao áudio espacial

## <a name="overview"></a>Visão geral

No tutorial anterior, você adicionou a espacialização dos sons para dar a eles uma ideia de direção neste tutorial. você adicionará um efeito de reverberação para dar aos sons uma sensação de distância.

## <a name="objectives"></a>Objetivos

* Melhore a distância percebida de fontes de som adicionando o reverberar.
* Controle a distância percebida do som usando a distância do ouvinte para o holograma.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Adicionar um grupo de mixers e um efeito de reverberação

No [tutorial de sons de interação do botão espacial](unity-spatial-audio-ch2.md), adicionamos um mixer. O mixer inclui um **grupo** por padrão chamado **Master**. Como só desejamos aplicar um efeito de reverberação a alguns sons, vamos adicionar um segundo grupo para esses sons. Para adicionar um grupo, clique com o botão direito do mouse no grupo mestre no **mixer de áudio** escolha **Adicionar grupo filho** e forneça um nome adequado para o exemplo de _efeito de sala_:

![Adicionar grupo filho](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

Cada **grupo** tem seu próprio conjunto de efeitos. Adicione um efeito de reverberação ao novo grupo clicando em **Adicionar...** no novo grupo e escolhendo o **reverberar de SFX**:

![Adicionar reverbo SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

Na terminologia de áudio, o áudio unreverberated original é chamado de _caminho seco_, e o áudio após a filtragem com o filtro de reverberação é chamado de _caminho úmida_. Ambos os caminhos são enviados para a saída de áudio, e seus pontos fortes relativos nessa mistura são chamados de _mistura úmida/seca_. A mistura úmida/seca afeta fortemente a sensação de distância.

O **inverbo SFX** inclui controles para ajustar a mistura úmida/seca dentro do efeito. Como o plug-in **Spatializer da Microsoft** trata o caminho seco, usaremos o único **verbo SFX** somente para o caminho úmida. No painel Inspetor de seu **reverbo SFX**:

* Definir a propriedade de **nível seco** para a configuração mais baixa (-10000 MB)
* Definir a **Propriedade Room** como a configuração mais alta (0 MB)

![Propriedades de reverberação SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

As outras configurações controlam a sensação da sala simulada. Em particular, o **tempo de decaimento** está relacionado ao tamanho de sala percebido.

## <a name="enable-reverb-on-the-video-playback"></a>Habilitar reverberação na reprodução de vídeo

Há duas etapas para habilitar o reverberador em uma fonte de áudio:

* Rotear a **fonte de áudio** para o **grupo** apropriado
* Defina o plug-in **Microsoft Spatializer** para passar áudio para o **grupo** para processamento

Nas etapas a seguir, você ajustará o script para controlar o roteamento de áudio e anexará um script de controle fornecido com o plug-in do **Microsoft Spatializer** para alimentar dados no reverbo.

Com o **Quad** selecionado na hierarquia, clique em **Adicionar componente** na janela Inspetor e adicione o **nível de envio de efeito Room (script)**:

![Adicionar script de nível de envio](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> A menos que você habilite o recurso de **nível de envio de efeito Room** do plug-in do **Microsoft Spatializer** , ele não envia nenhum áudio de volta para o mecanismo de áudio do Unity para processamento de efeito.

O componente de **nível de envio de efeito Room** inclui um controle de gráfico que define o nível do áudio enviado ao mecanismo de áudio do Unity para o processamento de reverberação. Para abrir o controle de gráfico, clique no **nível de envio de efeito de sala**.  Clique e arraste a curva verde para baixo para definir o nível como About-30dB:

![Ajustar curva de reverberação](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

Em seguida, remova os comentários das 4 linhas comentadas no script **SpatializeOnOff** . O script agora terá esta aparência:

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

Depois que essas linhas são desmarcadas, elas adicionam duas propriedades ao inspetor do **script SpatializeOnOff**. atribua-os na janela Inspetor do componente **SpatializeOnOff** do **Quad**.

Com o quad Object ainda selecionado na hierarquia, na janela do Inspetor, localize o componente de **script SpatializeOnOff** e:

* Defina a propriedade **grupo de efeitos da sala** como o novo grupo do mixer de efeito Room
* Definir a propriedade do **grupo mestre** como o grupo do mixer mestre

![Espacial eslongada estendida](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a>Parabéns

Você concluiu os tutoriais de áudio espacial 2 do HoloLens para o Unity. Experimente o aplicativo em um HoloLens 2 ou Unity. Quando você clica no botão no aplicativo para ativar a espacialização, o script roteará o áudio do vídeo para o grupo de efeitos da sala para adicionar o reverberador. Ao alternar para o estéreo, ele encaminhará o áudio para o grupo mestre e evitará adicionar o reverberador.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
