---
title: Áudio em realidade misturada
description: O áudio na realidade misturada pode aumentar a confiança do usuário nas interações da interface do usuário e aprofundar os usuários na experiência.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: som espacial, som surround, áudio 3d, som 3d, áudio espacial, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, estudos de caso, acústica
ms.openlocfilehash: 75b87098f90611140d2c43bb596e7c5d50dab9c47fc49426d5bcbbe0095c3847
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188816"
---
# <a name="audio-in-mixed-reality"></a>Áudio em realidade misturada

O áudio é uma parte essencial do design e da produtividade na realidade misturada. O som pode:
* Aumente a confiança do usuário em interações de gesto e voz.
* Orientar os usuários para as próximas etapas.
* Combine efetivamente objetos virtuais com o mundo real.

O acompanhamento de cabeça de baixa latência de headsets de realidade misturada, incluindo HoloLens, dá suporte à espacialização baseada em HRTF de alta qualidade. Você pode espacializar o áudio em seu aplicativo para:
* Chame a atenção para elementos visuais.
* Ajudar os usuários a manter o reconhecimento de seus ambientes do mundo real.

A acústica conecta mais profundamente hologramas ao mundo da realidade misturada. Ele fornece dicas sobre o ambiente e o estado do objeto.

Confira [exemplos detalhados de design que usam áudio.](spatial-sound-design.md)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (primeira geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Espacialização</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Aceleração de hardware de espacialização</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>Uso de sons na realidade misturada

[O uso de sons na realidade misturada](spatial-sound-design.md) requer uma abordagem diferente de em aplicativos de toque e teclado e mouse. As principais decisões de design de som incluem quais sons espacializar e quais interações serão ressignificados. Essas decisões efetivam a confiança, a produtividade e a curva de aprendizado do usuário.

### <a name="case-studies"></a>Estudos de caso

O HoloTour virtualmente leva os usuários para sites históricos e históricos em todo o mundo. Confira o estudo de caso Design de [som para HoloTour.](case-study-spatial-sound-design-for-holotour.md) Um microfone especial e uma configuração de renderização foram usados para capturar os espaços de assunto.

O RoboRaid é um robô de alta energia para HoloLens. O estudo de caso Design de som [para RoboRaid](case-study-using-spatial-sound-in-roboraid.md) descreve as opções de design que foram feitas para garantir que o áudio espacial foi usado para o efeito mais profundo.

## <a name="spatialization"></a>Espacialização

Espacialização é o componente direcional do áudio espacial. Para uma configuração de home-home do 7.1, a espacialização é tão simples quanto o panorâmico entre alto-falantes. Mas para fones de ouvido na realidade misturada, é essencial usar uma tecnologia baseada em HRTF para precisão e conforto. Windows oferece espacialização baseada em HRTF e esse suporte é acelerado por hardware HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Devo espacializar?

A espacialização pode melhorar muitos sons em aplicativos de realidade misturada. A espacialização tira um som da cabeça do ouvinte e coloca-o no mundo. Para sugestões sobre o uso efetivo da espacialização em seu aplicativo, consulte [Design de som espacial.](spatial-sound-design.md)

### <a name="spatializer-personalization"></a>Personalização do spatializer

AS HRTFs manipulam as diferenças de nível e fase entre os olhos em todo o espectro de frequência. Eles se baseiam em modelos físicos e medidas de formas de cabeça, de cabeça e de ouvido (pinnae) humanas. Nossos cérebros respondem a essas diferenças para fornecer a direção percebida no som.

Cada indivíduo tem uma forma de ouvido exclusiva, tamanho da cabeça e posição de ouvido. Portanto, os melhores HRTFs estão em conformidade com você. Para aumentar a precisão da espacialização, HoloLens usa sua IPD (distância interescalar) do headset para ajustar as HRTFs para o tamanho da cabeça.

### <a name="spatializer-platform-support"></a>Suporte à plataforma spatializer

Windows oferece espacialização, incluindo HRTFs, por meio da [API ISpatialAudioClient](/windows/win32/coreaudio/spatial-sound). Essa API expõe a aceleração de hardware HoloLens 2 HRTF para aplicativos.

### <a name="spatializer-middleware-support"></a>Suporte a middleware do Spatializer

O suporte Windows HRTFs está disponível para os seguintes mecanismos de áudio de terceiros.
* Um [plug-in do mecanismo de áudio do Unity](../develop/unity/spatial-sound-in-unity.md)
* Um [plug-in do mecanismo de áudio Wwise](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>Acústica

O áudio espacial é mais do que a direção. Outras dimensões incluem oclusão, obstrução, reverb, portaling e modelagem de origem. Coletivamente, essas dimensões são conhecidas como *acústica.* Sem acústica, os sons espacializados não têm distância percebida.

Os tratamentos acústicos variam de simples a complexo. Você pode usar um reverb com suporte de qualquer mecanismo de áudio para efetuar push de sons espacializados no ambiente do ouvinte. Sistemas acústicos, [como Project Acústica,](/gaming/acoustics/what-is-acoustics) fornecem um tratamento acústico mais rico e atraente. Project A acústica pode modelar o efeito de paredes, portas e outras geometrias de cena em um som. É uma opção efetiva para casos em que a geometria de cena relevante é conhecida no momento do desenvolvimento.

## <a name="next-steps"></a>Próximas etapas

- [Som espacial no Unity](../develop/unity/spatial-sound-in-unity.md)
- [Como usar o som em aplicativos de realidade misturada](spatial-sound-design.md)