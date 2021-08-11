---
title: Som espacial no Unity
description: Saiba como reproduzir e atenuar sons espaciais de um ponto 3D específico em sua cena do Unity com exemplos.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, som espacial, HRTF, tamanho da sala, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, MRTK, Toolkit Realidade Misturada, espacializador, reverb
ms.openlocfilehash: e6e56732a888fd096335a114fceba557519b01bf8df84a7670b9265f46c75a34
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228222"
---
# <a name="spatial-sound-in-unity"></a>Som espacial no Unity

Esta página vincula-se aos recursos para som espacial no Unity.

## <a name="spatializer-options"></a>Opções do spatializer

As opções do Spatializer para aplicativos de realidade misturada incluem:
* O Unity fornece *o Espacializador MS HRTF* como parte do *Windows Mixed Reality* pacote opcional.
  * É executado na CPU em uma arquitetura de "fonte única" de custo mais alto.
  * Fornecido para compatibilidade com compatibilidade com compatibilidade com HoloLens aplicativos originais.
* O *Microsoft Spatializer* está disponível no repositório [microsoft spatializer GitHub](https://github.com/microsoft/spatialaudio-unity).
  * Usa uma arquitetura de "várias fontes" de baixo custo.
  * Descarregado para um acelerador de hardware no HoloLens 2. 

Para novos aplicativos, recomendamos *o Microsoft Spatializer.*

## <a name="enable-spatialization"></a>Habilitar espacialização

Use [NuGet unity para](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) instalar _Microsoft.SpatialAudio.Spatializer.Unity_ e escolha **Microsoft Spatializer** nas configurações de áudio do projeto. Em seguida:
* Anexar **uma Fonte de** Áudio a um objeto na hierarquia
* Marque a **caixa de seleção Habilitar espacialização**
* Mover o **controle deslizante do Spatial Blend** para '1'
* Verifique se o áudio espacial está habilitado na estação de trabalho do desenvolvedor. 
    * Clique com o botão direito do mouse no ícone de volume na barra de tarefas e certifique-se de que o Som Espacial está definido como algo diferente de "off". 
    * Escolha **Windows Sonic para Fones de Ouvido** para obter a melhor representação do que você ouvirá HoloLens 2.

>[!NOTE]
>Se você receber um erro no Unity sobre não conseguir carregar o plug-in Microsoft.SpatialAudio.Spatializer.Unity porque uma de suas dependências está ausente, verifique se você tem a versão mais recente do [Microsoft Visual C++ Redistribuível](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) instalada em seu computador.

Para obter mais informações, consulte:
* [Repositório de GitHub microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Tutorial do espacializador da Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentação da fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentação do espacializador do Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Atenuação de distância

O decaimento padrão baseado em distância do Unity tem uma distância mínima de 1 medidor e uma distância máxima de 500 metros, com uma reação logarítmica. Essas configurações podem funcionar para seu cenário ou você pode achar que as fontes atenuam muito rápido ou muito lentamente. Para obter mais informações, consulte:
* [Design de som em realidade misturada](../../design/spatial-sound-design.md) para configurações recomendadas.
* [Documentação da fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obter instruções sobre como definir essas curvas.

## <a name="reverb"></a>Reverb

O _Microsoft Spatializer_ desabilita os efeitos pós-espacializador por padrão. Para habilitar o reverb e outros efeitos para fontes espacializadas:
* Anexar o **componente Nível de Envio de Efeito** De Sala a cada origem
* Ajuste a curva de nível de envio para cada fonte, para controlar o ganho no áudio enviado de volta para o grafo para processamento de efeitos

Confira [o Capítulo 5 do tutorial do espacializador](tutorials/unity-spatial-audio-ch5.md) para obter detalhes.

## <a name="unity-spatial-sound-examples"></a>Exemplos de som espacial do Unity

Para ver exemplos de som espacial no Unity, confira:
* [Demonstrações do MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* O [projeto de exemplo do Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que lançamos, você está no meio da exploração dos blocos de construção principais da Realidade Misturada. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Confira também

* [Design de som na realidade misturada](../../design/spatial-sound-design.md)
* [Tutorial do espacializador da Microsoft](tutorials/unity-spatial-audio-ch1.md)
