---
title: Som espacial no Unity
description: Reproduzir o som espacial de um ponto 3D específico dentro de sua cena do Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, som espacial, HRTF, tamanho da sala
ms.openlocfilehash: 9c5f71b2d9d13fa40f0d1674237d2da6c769e584
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675222"
---
# <a name="spatial-sound-in-unity"></a>Som espacial no Unity

Esta página contém links para recursos de som espacial no Unity.

## <a name="spatializer-options"></a>Opções de Spatializer
As opções de Spatializer para aplicativos de realidade misturada incluem:
* *SPATIALIZER HRTF MS* . O Unity fornece isso como parte do pacote opcional do *Windows Mixed Reality* .
  * Isso é executado na CPU em uma arquitetura de ' fonte única ' de maior custo.
  * Isso é fornecido para compatibilidade com versões anteriores com aplicativos de HoloLens originais.
* O *Microsoft Spatializer* . Isso está disponível no [repositório GitHub do Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Isso usa uma arquitetura de "várias fontes" de menor custo.
  * No HoloLens 2, isso é descarregado para um acelerador de hardware.

Para novos aplicativos, recomendamos o *Microsoft Spatializer* .

## <a name="enable-spatialization"></a>Habilitar a espacialização

Use o [NuGet para o Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft. SpatialAudio. Spatializer. Unity_ e escolha **Microsoft Spatializer** nas configurações de áudio do seu projeto. Em seguida:
* Anexar uma **fonte de áudio** a um objeto na hierarquia
* Marque a caixa de seleção **habilitar a espacial**
* Mover o controle deslizante de **mistura espacial** para ' 1 '
* Verifique se o áudio espacial está habilitado na estação de trabalho do desenvolvedor. Habilite-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas e verificando se o som espacial está definido como algo diferente de "desativado". Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **Windows Sonic para fones de ouvido** .

>[!NOTE]
>Se você receber um erro no Unity sobre não poder carregar o plugin Microsoft. SpatialAudio. Spatializer. Unity porque uma de suas dependências está ausente, verifique se você tem a versão mais recente do [Microsoft Visual C++ redistribuível](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) instalado no seu computador.

Para obter mais informações, consulte:
* [Repositório GitHub do Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Tutorial do spatializer da Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentação da fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentação do spatializer do Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Atenuação de distância
O decaimento baseado em distância padrão da Unity tem uma distância mínima de 1 medidor e uma distância máxima de 500 metros, com um rolloff logarítmica. Essas configurações podem funcionar para seu cenário, ou você pode achar que as fontes são atenuadas muito rapidamente ou lentas. Para obter mais informações, consulte:
* [Design de som em realidade misturada](../../design/spatial-sound-design.md) para as configurações recomendadas.
* [Documentação de fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obter instruções sobre como definir essas curvas.

## <a name="reverb"></a>Reverberação
Por padrão, o _Microsoft Spatializer_ desabilita os efeitos de Spatializer. Para habilitar o reverberar e outros efeitos para fontes espaciais:
* Anexar o componente de **nível de envio de efeito Room** a cada fonte
* Ajuste a curva de nível de envio para cada fonte, para controlar o lucro do áudio enviado de volta ao grafo para o processamento de efeitos

Consulte [o capítulo 5 do tutorial do spatializer](tutorials/unity-spatial-audio-ch5.md) para obter detalhes.

## <a name="unity-spatial-sound-examples"></a>Exemplos de som espacial do Unity
Para obter exemplos de som espacial no Unity, consulte:
* [Demonstrações do MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* O [projeto de exemplo Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos principais blocos de construção da realidade misturada. A partir daqui, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

Ou vá para recursos e APIs da plataforma de realidade misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Consulte também
* [Design de som em realidade misturada](../../design/spatial-sound-design.md)
* [Tutorial do spatializer da Microsoft](tutorials/unity-spatial-audio-ch1.md)
