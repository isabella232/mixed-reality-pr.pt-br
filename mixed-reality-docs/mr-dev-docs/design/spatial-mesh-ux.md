---
title: Visualização de malha espacial
description: Saiba mais sobre as diretrizes de design e a compreensão do ambiente físico com a visualização de malha espacial no MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: realidade misturada, HoloLens, controles de interface do usuário, interação, interface do usuário, ux, Design de ux, interface do usuário espacial, interação espacial, interface do usuário 3d, ux 3d, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, HoloLens, MRTK, realidade misturada Toolkit
ms.openlocfilehash: 7fcba586f55e6131235d031327da131aa8ba6c97958e4ac282a8f8d048d37992
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216272"
---
# <a name="spatial-mesh"></a>Malha espacial

![Malha espacial](images/MRTK_PulseShader_SpatialMesh.gif)

Os usuários aprendem como um dispositivo percebe e compreende o ambiente físico por meio da visualização de malha espacial. A visualização de malha espacial adequada pode criar uma experiência de interessantes e mágico enquanto fornece o contexto espacial.  

## <a name="design-guideline"></a>Diretriz de design

É importante permitir que o usuário se concentre e interaja com o conteúdo. A visualização contínua da malha espacial em segundo plano pode ser uma distração. É recomendável Visualizar o ambiente com moderação, seja apenas uma vez na inicialização inicial ou quando o usuário mostrar claramente que deseja ver a malha ambiental por direcionamento e espaço de toque. Você pode observar esse comportamento no portal de realidade misturada.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>visualização de malha espacial em MRTK (realidade misturada Toolkit) para o Unity

O MRTK fornece vários materiais para a visualização de malha espacial.

- **MRTK_Wireframe. esteira, MRTK_Wireframe. passe-partout**: material de malha espacial estática padrão, que mostra os contornos de malha sem animação. Esse material é útil para fins de depuração, pois mostra as geometrias de malha espacial inteiras. No entanto, não é recomendável para produção.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. passe-partout**: esse material oferece um efeito de pulso animado na malha espacial. Você pode usar esse material para visualizar o ambiente em um momento específico ou na entrada aérea do usuário. Consulte a cena **PulseShaderExamples. Unity** para ver os exemplos.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* Para obter mais informações, consulte [reconhecimento espacial do MRTK](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) e [sombreador MRTK-Pulse](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).

<br>

---

## <a name="see-also"></a>Confira também

* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)