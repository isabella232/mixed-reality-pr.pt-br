---
title: Documentação do desenvolvedor do MRTK-Unity
description: Saiba mais sobre o Kit de Ferramentas de Realidade Misturada para Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK
ms.openlocfilehash: cef4bcf671caaaf8d5cb7cdc639446c6c6e91fa0
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850432"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>O que é o Kit de Ferramentas de Realidade Misturada

![Kit de ferramentas de realidade misturada](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

MRTK-Unity é um projeto conduzido pela Microsoft que fornece um conjunto de componentes e recursos usados para acelerar o desenvolvimento de aplicativos MR de plataforma cruzada no Unity. Confira algumas funções dele abaixo:

* Fornece o **sistema de entrada multiplataforma e os blocos de construção para interações espaciais e interface do usuário**.
* Habilita a **prototipagem rápida** por meio de simulação no editor, que permite ver as alterações imediatamente.
* Opera como uma **estrutura extensível** que fornece aos desenvolvedores a capacidade de trocar componentes principais.
* **Dá suporte a diversas plataformas**:

| Plataforma | Dispositivos com suporte |
|---|---|
| OpenXR (Unity 2020.2 ou mais recente) | Microsoft HoloLens 2 <br> Headsets do Windows Mixed Reality |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Headsets do Windows Mixed Reality  |
| Oculus (Unity 2019.3 ou mais recente) | Solicitação Oculus |
| OpenVR |  Headsets do Windows Mixed Reality <br> HTC Vive <br> Oculus Rift |
| Acompanhamento de mãos Ultraleap | Leap Motion Controller da Ultraleap |
| Dispositivos móveis | iOS e Android |

## <a name="getting-started-with-mrtk"></a>Introdução ao MRTK

Se você for novo no desenvolvimento de MRTK ou de Realidade Misturada no Unity, recomendamos que você instale e explore o aplicativo de exemplo Hub de exemplos do MRTK em seu dispositivo ou emulador. 

> [!div class="nextstepaction"]
> [Baixar o aplicativo Hub de exemplos de MRTK](running-examples-hub.md)

Assim que você compreender o que a Realidade Misturada e o MRTK têm a oferecer, instale as ferramentas necessárias e siga nossa série de tutoriais de nível de principiante do HoloLens 2.

> [!div class="nextstepaction"]
> [Instalar as ferramentas](/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [Série de tutoriais do HoloLens 2](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

Quer ver o que está acontecendo nos bastidores?
> [!div class="nextstepaction"]
> [Explorar o MRTK no GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>Documentação

| [![Notas de Versão](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)<br/>[Notas sobre a versão](release-notes/mrtk-26-release-notes.md)| [![Visão geral do MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[Visão geral do MRTK](architecture/overview.md)|[![Referência de API](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[Referência da API](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>Status do Build

| Branch | Status de CI | Status dos documentos |
|---|---|---|
| `main` |[![Status de CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![Status dos documentos](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>Áreas de recursos

:::row:::
    :::column:::
       [![Sistema de entrada](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)<br>
        **[Sistema de entrada](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![Acompanhamento da Mão (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)<br>
        **[Acompanhamento da Mão <br> (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![Acompanhamento Ocular (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)<br>
        **[Acompanhamento Ocular <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![Perfis](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)<br>
        **[Perfis](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Acompanhamento da Mão (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)<br>
        **[Acompanhamento da Mão <br/> (Ultraleap)](supported-devices/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![Controles de interface do usuário](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)<br>
        **[Controles de interface do usuário](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![Solucionadores](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)<br>
        **[Solucionadores](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![Gerenciador de várias cenas](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Gerenciador<br/> de várias cenas](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Conscientização espacial](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)<br>
        **[Conscientização <br/> espacial](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Ferramenta de diagnóstico](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Ferramenta <br/> de diagnóstico](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Exibição do Sombreador Padrão do MRTK](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)<br>
        **[Exibição de exemplo do Sombreador Padrão do MRTK](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![Fala e Ditado](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Fala](features/input/speech.md)<br/> & [Ditado](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Sistema de limite](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)<br>
        **[Sistema <br/>de limite](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Simulação no Editor](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Simulação <br/> no Editor](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Recursos experimentais](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)<br>
        **[Recursos <br/> experimentais](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>Blocos de construção de experiência do usuário

:::row:::
    :::column:::
       [![Botão](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Botão](features/ux-building-blocks/button.md)**<br>
        Um controle de botão que dá suporte a vários métodos de entrada, incluindo a mão articulada do HoloLens 2
    :::column-end:::
    :::column:::
        [![Controle de limites](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Controle de limites](features/ux-building-blocks/bounds-control.md)**<br>
        Interface do usuário padrão para manipular objetos no espaço 3D
    :::column-end:::
    :::column:::
        [![Manipulador de objetos](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Manipulador de objetos](features/ux-building-blocks/object-manipulator.md)**<br>
        Script para manipular objetos com uma ou duas mãos
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Ardósia](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Ardósia](features/ux-building-blocks/slate.md)**<br>
        Plano de estilo 2D que dá suporte à rolagem com entrada de mão articulada
    :::column-end:::
    :::column:::
        [![Teclado do sistema](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Teclado do sistema](features/ux-building-blocks/system-keyboard.md)**<br>
        Exemplo de script de uso do teclado do sistema no Unity
    :::column-end:::
    :::column:::
        [![Interativo](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interativo](features/ux-building-blocks/interactable.md)**<br>
        Um script para tornar os objetos interativos com os estados visuais e o suporte a temas
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Solucionador](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solucionador](features/ux-building-blocks/solvers/solver.md)**<br>
        Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e magnetismo de superfície
    :::column-end:::
    :::column:::
        [![Coleção de objetos](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Coleção de objetos](features/ux-building-blocks/object-collection.md)**<br>
        Script para dispor uma matriz de objetos em uma forma tridimensional
    :::column-end:::
    :::column:::
        [![Dica de ferramenta](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Dica de ferramenta](features/ux-building-blocks/tooltip.md)**<br>
        A interface do usuário de anotações com um sistema de âncora/dinâmico flexível, que pode ser usado para rotular controladores de movimento e objetos
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Controle deslizante](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Controle deslizante](features/ux-building-blocks/sliders.md)**<br>
        Interface do usuário do controle deslizante para ajustar valores que dão suporte à interação direta de acompanhamento da mão
    :::column-end:::
    :::column:::
        [![Sombreador padrão do MRTK](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[Sombreador padrão do MRTK](features/rendering/mrtk-standard-shader.md)**<br>
        O sombreador padrão do MRTK dá suporte a vários elementos de Fluent Design com desempenho
    :::column-end:::
    :::column:::
        [![Menu lateral](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Menu lateral](features/ux-building-blocks/hand-menu.md)**<br>
        Interface do usuário protegida por mão para acesso rápido, usando o solucionador de restrição de mão
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Barra de aplicativos](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[Barra de aplicativos](features/ux-building-blocks/app-bar.md)**<br>
        Interface do usuário para ativação manual do controle de limites
    :::column-end:::
    :::column:::
        [![Ponteiros](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Ponteiros](features/input/pointers.md)**<br>
        Saiba mais sobre os vários tipos de ponteiros
    :::column-end:::
    :::column:::
        [![Visualização da ponta do dedo](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Visualização da ponta do dedo](features/ux-building-blocks/fingertip-visualization.md)**<br>
        A funcionalidade visual na ponta do dedo, que aprimora a confiança da interação direta
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Menu próximo](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Menu próximo](features/ux-building-blocks/near-menu.md)**<br>
        Interface do usuário do menu flutuante para as interações próximas
    :::column-end:::
    :::column:::
        [![Introdução à conscientização espacial](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Exibição da conscientização espacial](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        Fazer com que seus objetos holográficos interajam com os ambientes físicos
    :::column-end:::
    :::column:::
        [![Comando de voz](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Comando de voz](features/input/speech.md)**<br>
        Scripts e exemplos para integrar a entrada de fala
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Indicador de progresso](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Indicador de progresso](features/ux-building-blocks/progress-indicator.md)**<br>
        Indicador visual para comunicação do processo de dados ou operação
    :::column-end:::
    :::column:::
        [![Caixa de diálogo](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Caixa de diálogo](features/ux-building-blocks/dialog.md)**<br>
        Interface de usuário para solicitar confirmação ou reconhecimento do usuário
    :::column-end:::
    :::column:::
        [![Orientador de mão](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Orientador de mão](features/ux-building-blocks/hand-coach.md)**<br>
        Componente que ajuda a orientar o usuário quando o gesto não foi ensinado
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Serviço de física de mão](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Serviço de física de mão [Experimental]](features/experimental/hand-physics-service.md)**<br>
        O serviço de física de mão permite eventos de colisão de corpo rígido e interações com mãos articuladas
    :::column-end:::
    :::column:::
        [![Rolagem da coleção](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Rolagem da coleção](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        Uma coleção de objetos que rola nativamente objetos 3D
    :::column-end:::
    :::column:::
        [![Doca](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Doca [Experimental]](features/experimental/dock.md)**<br>
        A Doca permite que os objetos sejam movidos para dentro e para fora das posições predeterminadas
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Acompanhamento ocular: seleção de destino](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Acompanhamento ocular: seleção de destino](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena
    :::column-end:::
    :::column:::
        [![Acompanhamento ocular: navegação](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Acompanhamento ocular: navegação](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        Saiba como rolar automaticamente o texto ou ampliar de maneira fluente o conteúdo focado com base no que você está vendo
    :::column-end:::
    :::column:::
        [![Acompanhamento ocular: mapa de calor](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Acompanhamento ocular: mapa de calor](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo
    :::column-end:::
:::row-end:::

## <a name="tools"></a>Ferramentas

|  [![Otimizar janela](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Otimizar janela](features/tools/optimize-window.md) | [![Janela de dependência](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Janela de dependência](features/tools/dependency-window.md) | ![Janela de compilação](features/images/MRTK_Icon_BuildWindow.png) Janela de compilação | [![Gravação de entrada](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Gravação de entrada](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Automatizar a configuração de projetos de realidade misturada para otimizações de desempenho | Analisar dependências entre ativos e identificar ativos não utilizados |  Configurar e executar um processo de compilação de ponta a ponta para aplicativos de realidade misturada | Movimentação de cabeçotes de gravação e reprodução e dados de acompanhamento da mão no editor |

## <a name="example-scenes"></a>Cenas de exemplo

Explore os vários tipos de interações e controles de interface do usuário do MRTK nesta [cena de exemplo](features/example-scenes/hand-interaction-examples.md).

[![Cena de exemplo 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>Hub de exemplos do MRTK

Com o Hub de exemplos do MRTK, você pode experimentar várias cenas de exemplo no MRTK.
Você pode baixar pacotes de aplicativos pré-criados para o HoloLens (x86), o HoloLens 2(ARM) e os headsets imersivos do Windows Mixed Reality (x64) selecionando o pacote "Exemplos do Kit de Ferramentas de Realidade Misturada" na [ferramenta de recurso de MR](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool). [Use o Portal de Dispositivos do Windows para instalar aplicativos no HoloLens (1ª geração).](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens) No HoloLens 2, você pode baixar e instalar o [Hub de exemplos do MRTK por meio do aplicativo Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).

Confira a [página LEIAME do hub de exemplos](features/example-scenes/example-hub.md) para saber mais sobre os detalhes de como criar um hub de várias cenas com o sistema de cena do MRTK e o serviço de transição de cena.

[![Hub de cena de exemplo](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>Aplicativos de exemplo feitos com o MRTK

| [![Tabela periódica dos elementos](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Explorador da galáxia](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)| [![Aplicativo de exemplo Surfaces](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [A tabela periódica dos elementos](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) é um aplicativo de exemplo de software livre que demonstra como usar o sistema de entrada e os blocos de construção do MRTK a fim de criar uma experiência de aplicativo para o HoloLens e os headsets imersivos. Leia a história de portagem: [Como trazer o aplicativo Tabela periódica dos elementos para o HoloLens 2 com o MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |O [Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) é um aplicativo de exemplo de software livre originalmente desenvolvido em março de 2016 como parte da campanha 'Compartilhe sua ideia' do HoloLens. O Galaxy Explorer foi atualizado com novos recursos para o HoloLens 2, usando o MRTK v2. Leia a história: [A criação do Galaxy Explorer para o HoloLens 2](/windows/mixed-reality/galaxy-explorer-update) |O [Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) é um aplicativo de exemplo de software livre para o HoloLens 2, que explora como podemos criar uma sensação tátil com visual, áudio e acompanhamento da mão totalmente articulado. Confira a sessão do Microsoft MR Dev Days [Aprendizados com o aplicativo Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) para ver o design detalhado e a história de desenvolvimento. |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Vídeos de sessão do evento Mixed Reality Dev Days 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Tutorial sobre como criar um aplicativo MRTK simples do início ao fim. Saiba mais sobre os conceitos de interação e os recursos multiplataforma do MRTK. | Aprofunde-se nos blocos de construção de experiência do usuário do MRTK que ajudam você a criar belas experiências de realidade misturada. | Uma introdução a ferramentas de desempenho, no MRTK e externas, assim como uma visão geral do Sombreador Padrão do MRTK. |

Confira o evento [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) para explorar mais vídeos de sessão.

## <a name="engage-with-the-community"></a>Envolva-se com a comunidade

* Junte-se à conversa sobre MRTK no [Slack](https://holodevelopers.slack.com/). Você pode ingressar na comunidade do Slack por meio do [remetente de convite automático](https://holodevelopersslack.azurewebsites.net/).

* Faça perguntas sobre como usar o MRTK no [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) usando a marca **MRTK**.

* Procure [problemas conhecidos](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) ou registre [um novo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) se você encontrar algo errado no código MRTK.

* Para dúvidas sobre como contribuir com o MRTK, vá para o canal [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) no Slack.

Este projeto adotou o [Código de Conduta de Software Livre da Microsoft](https://opensource.microsoft.com/codeofconduct/).
Para saber mais, confira as [Perguntas frequentes sobre o Código de Conduta](https://opensource.microsoft.com/codeofconduct/faq/) ou contate o [opencode@microsoft.com](mailto:opencode@microsoft.com) caso tenha outras dúvidas ou comentários.

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Recursos úteis no Centro de Desenvolvimento de realidade misturada

| ![Descobrir](features/images/mrdevcenter/icon-discover.png) [Descobrir](/windows/mixed-reality/)| ![Projetar](features/images/mrdevcenter/icon-design.png) [Projetar](/windows/mixed-reality/design)| ![Desenvolver](features/images/mrdevcenter/icon-develop.png) [Desenvolver](/windows/mixed-reality/development)| ![Distribuir](features/images/mrdevcenter/icon-distribute.png) [Distribuir](/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Saiba como criar experiências de realidade misturada para o HoloLens e headsets imersivos (VR).          | Obtenha guias de design. Crie interface do usuário. Saiba mais sobre as interações e a entrada.     | Obtenha guias de desenvolvimento. Conheça a tecnologia. Entenda a ciência.       | Prepare seu aplicativo para outras pessoas e considere a criação de um iniciador 3D. |

## <a name="useful-resources-on-azure"></a>Recursos úteis no Azure

| ![Âncoras Espaciais](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Âncoras Espaciais](/azure/spatial-anchors/)| ![Serviços de Fala](features/images/mrdevcenter/icon-azurespeechservices.png) [Serviços de Fala](/azure/cognitive-services/speech-service/)| ![Serviços de visão](features/images/mrdevcenter/icon-azurevisionservices.png) [Serviços de visão](/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| As Âncoras Espaciais são um serviço multiplataforma que permite que você crie experiências de Realidade Misturada usando objetos que mantêm seu local em todos os dispositivos ao longo do tempo.| Descubra e integre as funcionalidades de fala habilitadas para Azure como conversão de fala em texto, reconhecimento de locutor ou tradução de fala em seu aplicativo.| Identifique e analise seu conteúdo de imagem ou de vídeo usando os Serviços de Visão como pesquisa visual computacional, detecção facial, reconhecimento de emoções ou video indexer. |

## <a name="how-to-contribute"></a>Como contribuir

Saiba como contribuir com o MRTK em [Como contribuir](contributing/contributing.md).

## <a name="getting-help"></a>Obtendo ajuda

Se você tiver problemas causados pelo MRTK ou tiver dúvidas sobre como fazer algo, há alguns recursos que podem ajudar:

* Para relatórios de bugs, [registre um problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) no repositório GitHub.
* Se tiver dúvidas, entre em contato com [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) ou com o [canal mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) no Slack. Você pode ingressar na comunidade do Slack por meio do [remetente de convite automático](https://holodevelopersslack.azurewebsites.net/).