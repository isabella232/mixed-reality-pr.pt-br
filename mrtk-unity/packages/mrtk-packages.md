---
title: Pacotes MRTK
description: Pacotes no MRTK com suporte a plataformas e hardware de realidade misturada.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Unity Gerenciador de Pacotes,
ms.openlocfilehash: 3c92448d99cd67efa0a06feff9b0c7561a6aea79
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143807"
---
# <a name="mixed-reality-toolkit-packages"></a>Pacotes do Kit de Ferramentas de Realidade Misturada

O MRTK (Kit de Ferramentas de Realidade Misturada) é uma coleção de pacotes que permitem o desenvolvimento de aplicativos de Realidade Misturada entre plataformas, fornecendo suporte para plataformas e hardware de Realidade Misturada.

O MRTK está disponível como [pacotes de ativos](#asset-packages) (.unitypackage) e por meio [do unity Gerenciador de Pacotes](#unity-package-manager).

## <a name="asset-packages"></a>Pacotes de ativos

O ativo do MRTK (.unitypackage) pode ser baixado do [GitHub.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)

Alguns dos benefícios de usar pacotes de ativos incluem:

- Disponível para Unity 2018.4 e mais novo
- Fácil de fazer alterações no MRTK
  - O MRTK está na pasta Ativos

Alguns dos desafios são:

- O MRTK faz parte da pasta Ativos do projeto, levando a
  - Projetos maiores
  - Tempos de compilação mais lentos
- Sem gerenciamento de dependências
  - Os clientes são necessários para resolver as dependências de pacote manualmente
- Processo de atualização manual
  - Várias etapas
  - Atualizações de controle do código-fonte grandes (mais de 3000 arquivos)
  - Risco de perda de alterações feitas no MRTK
- Importar o pacote de exemplos normalmente significa incluir todos os exemplos

Os pacotes disponíveis são:

- [Fundamental](#foundation-package)
- [Extensões](#extensions-package)
- [Ferramentas](#tools-package)
- [Utilitários de teste](#test-utilities-package)
- [Exemplos](#examples-package)

Esses pacotes são liberados e têm suporte da Microsoft do código-fonte no Branch [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) no github.

### <a name="foundation-package"></a>Pacote do Foundation

O Mixed Reality Toolkit Foundation é o conjunto de códigos que permite que seu aplicativo aproveite a funcionalidade comum entre plataformas de realidade misturada.

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<sup>Pacote do MRTK Foundation</sup>

O pacote do MRTK Foundation contém o seguinte.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/núcleo | | Definições de interface e tipo, classes base, sombreador padrão. |
| MRTK/núcleo/provedores | | Provedores de dados independentes de plataforma |
| | Participação | Suporte de classe base e serviços para acompanhamento à mão. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Suporte para registro de movimentação de cabeçalho e dados de rastreamento de mão. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Suporte para simulação de entrada e de olho no editor. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | O observador de conscientização espacial usando um modelo 3D como os dados. |
| | UnityInput | Dispositivos de entrada comuns (pixel, mouse etc.) implementados por meio da API de entrada do Unity. |
| MRTK/Provedores | | Provedores de dados específicos da plataforma |
| | LeapMotion | Suporte para o controlador UltraLeap Leap Motion. |
| | OpenVR | Suporte para dispositivos OpenVR. |
| | Oculus | Suporte para dispositivos Oculus, como o Busca. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | (Experimental) Provedor de configurações de câmera que habilita o uso do MRTK com dispositivos de AR móveis. |
| | WindowsMixedReality | Suporte para Windows Mixed Reality, incluindo Microsoft HoloLens e headsets imersivos. |
| | Windows | Suporte para APIs específicas do Microsoft Windows, por exemplo, fala e ditado. |
| | SDK do XR | (Experimental) Suporte para [a nova estrutura XR do Unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) no Unity 2019.3 e mais novo. |
| MRTK/SDK | | |
| | Habilitação | Recursos experimentais, incluindo sombreadores, controles de interface do usuário e gerenciadores de sistema individuais. |
| | Recursos | Funcionalidade que se baseia no pacote Foundation. |
| | Perfis | Perfis padrão para os serviços e sistemas do Microsoft Mixed Reality Toolkit. |
| | StandardAssets | Ativos comuns; modelos, texturas, materiais, etc. |
| MRTK/SceneSystemResources | | Ativos e recursos usados pelo sistema de cena |
| MRTK/serviços | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | Sistema implementando suporte de limite VR. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | Sistema implementando a configuração e o gerenciamento da câmera. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | Sistema implementando no Application Diagnostics, por exemplo, um criador de perfil Visual. |
| | [InputSystem](../features/input/overview.md) | Sistema que fornece suporte para acessar e manipular a entrada do usuário. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | Sistema que fornece suporte a aplicativos de várias cenas. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | Sistema que fornece suporte para a conscientização do ambiente do usuário. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Sistema que fornece suporte para teleportabilidade (mudando sobre a experiência em saltos). |
| MRTK/StandardAssets | | Sombreador padrão MRTK, materiais básicos e outros ativos padrão para experiências de realidade misturada |

### <a name="extensions-package"></a>Pacote de extensões

O pacote opcional Microsoft. MixedRealityToolkit. Unity. Extensions inclui serviços adicionais que estendem a funcionalidade do Microsoft Mixed Reality Toolkit.

> [!NOTE]
> O pacote de extensões requer Microsoft. MixedRealityToolkit. Unity. Foundation.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/extensões | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Serviço que adiciona suporte de física a mãos articuladas. |
| | LostTrackingService | Serviço que simplifica a manipulação da perda de rastreamento em dispositivos Microsoft HoloLens. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Serviço que simplifica a adição de transições de cena suaves. |

### <a name="tools-package"></a>Pacote de ferramentas

O pacote opcional Microsoft. MixedRealityToolkit. Unity. Tools inclui ferramentas úteis que aprimoram a experiência de desenvolvimento da realidade mista usando o Microsoft Mixed Reality Toolkit.
Essas ferramentas estão localizadas no menu **Mixed Reality Toolkit > Utilities** no editor do Unity.

> [!NOTE]
> O pacote de ferramentas requer Microsoft. MixedRealityToolkit. Unity. Foundation.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/ferramentas | |
| | BuildWindow | Ferramenta que ajuda a simplificar o processo de criação e implantação de aplicativos UWP. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Ferramenta que cria um grafo de dependência de ativos em um projeto. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Assistente para ajudar na criação de serviços de extensão. |
| | [MigrationWindow](../features/tools/migration-window.md) | Ferramenta que ajuda na atualização de código que usa componentes do MRTK preterido.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Utilitário para ajudar a automatizar a configuração de um projeto de realidade misturada para o melhor desempenho no Unity. |
| | ReserializeAssetsUtility | Fornece suporte para reserializar arquivos específicos do Unity. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Utilitário que permite aos desenvolvedores determinar rapidamente os mapeamentos do Unity para controladores de hardware. |
| | ScreenshotUtility | Habilita a captura de imagens de aplicativo no editor do Unity. |
| | TextureCombinerWindow | Utilitário para combinar texturas gráficas. |
| | [Caixa de Ferramentas](../features/ux-building-blocks/toolbox.md) | Interface do usuário que facilita a descoberta e o uso de componentes de UX do MRTK. |

### <a name="test-utilities-package"></a>Testar pacote de utilitários

O pacote opcional Microsoft.MixedRealityToolkit.TestUtilities é uma coleção de scripts auxiliares que permitem aos desenvolvedores criar facilmente testes de modo [de reprodução.](../contributing/unit-tests.md#play-mode-tests) Esses utilitários são especialmente úteis para desenvolvedores que criam componentes do MRTK.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/testes | |
| | TestUtilities | Métodos para simplificar a criação de testes de modo de reprodução, incluindo utilitários de simulação de mão. |

### <a name="examples-package"></a>Pacote de exemplos

O pacote de exemplos contém demonstrações, scripts de exemplo e exemplos de cenas que exercem a funcionalidade no pacote do Foundation. Este pacote contém a [cena HandInteractionExample](../features/example-scenes/hand-interaction-examples.md) (figurada abaixo) que contém objetos de exemplo que respondem a vários tipos de entrada mão (articulados e não articulados).

![Cena HandInteractionExample](../features/images/MRTK_Examples.png)

Este pacote também contém demonstrações de acompanhamento ocular, que estão [documentadas aqui](../features/example-scenes/eye-tracking-examples-overview.md)

Em geral, qualquer novo recurso no MRTK deve conter um exemplo correspondente no pacote de exemplos, aproximadamente seguindo a mesma estrutura de pastas e local.

> [!NOTE]
> O pacote de exemplos requer Microsoft. MixedRealityToolkit. Unity. Foundation.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/exemplos | | |
| | Demonstrações | Cenas simples que ilustram um ou dois recursos relacionados. |
| | Habilitação | Cenas de demonstração que ilustram recursos experimentais. |
| | StandardAssets | Ativos comuns compartilhados por várias cenas de demonstração. |

## <a name="unity-package-manager"></a>Gerenciador de pacotes do Unity

Para as experiências que estão sendo criadas usando o Unity 2019,4 e mais recente, o MRTK está disponível por meio do [Gerenciador de pacotes do Unity](https://docs.unity3d.com/Manual/Packages.html).

Alguns dos benefícios de usar pacotes de ativos incluem:

- Projetos menores
  - Soluções de limpeza do Visual Studio
  - Menos arquivos para fazer check-in (MRTK é uma referência simples no `Packages/manifest.json` arquivo)
- Compilação mais rápida
  - O Unity não precisa recompilar o MRTK durante a compilação
- Resolução de dependência
  - Os pacotes MRTK necessários são instalados automaticamente ao especificar pacotes com dependências
- Atualização fácil para novas versões do MRTK
  - Alterar a versão no `Packages/manifest.json` arquivo

Alguns dos desafios são:

- O MRTK é imutável
  - Não é possível fazer alterações sem que elas são removidas durante a resolução do pacote
- O MRTK não dá suporte a pacotes UPM com o Unity 2018.4

### <a name="foundation-package"></a>Pacote foundation

O pacote de base ( `com.microsoft.mixedreality.toolkit.foundation` ) forma a base do Kit de Ferramentas de Realidade Misturada.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/Core | | Definições de interface e tipo, classes base, sombreador padrão. |
| MRTK/Core/Providers | | Provedores de dados agnósticos de plataforma |
| | Mãos | Suporte de classe base e serviços para acompanhamento de mão. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Suporte para gravação de movimentação de cabeça e dados de acompanhamento de mão. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Suporte para simulação no editor de entrada de mão e olho. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Observador de reconhecimento espacial usando um modelo 3D como os dados. |
| | UnityInput | Dispositivos de entrada comuns (joystick, mouse, etc.) implementados por meio da API de entrada do Unity. |
| MRTK/provedores | | Provedores de dados específicos da plataforma |
| | LeapMotion | Suporte para o controlador de movimento UltraLeap Leap. |
| | OpenVR | Suporte para dispositivos OpenVR. |
| | Oculus | Suporte para dispositivos oculus, como o Quest. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | Experimental Provedor de configurações de câmera que habilita o uso de MRTK com dispositivos móveis. |
| | WindowsMixedReality | Suporte para dispositivos Windows Mixed Reality, incluindo o Microsoft HoloLens e o headsets de imersão. |
| | Windows | Suporte para APIs específicas do Microsoft Windows, por exemplo, fala e ditado. |
| | SDK do XR | Experimental Suporte para o [novo XR Framework do Unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) no Unity 2019,3 e mais recente. |
| MRTK/SDK | | |
| | Habilitação | Recursos experimentais, incluindo sombreadores, controles de interface do usuário e gerentes de sistema individuais. |
| | Recursos | Funcionalidade que se baseia no pacote base. |
| | Perfis | Perfis padrão para os sistemas e serviços do Microsoft Mixed Reality Toolkit. |
| | StandardAssets | Ativos comuns; modelos, texturas, materiais, etc. |
| MRTK/Serviços | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | Sistema que implementa o suporte de limite de VR. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | Sistema que implementa a configuração e o gerenciamento da câmera. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | Sistema que implementa no diagnóstico de aplicativo, por exemplo, um profiler visual. |
| | [InputSystem](../features/input/overview.md) | Sistema que fornece suporte para acessar e manipular a entrada do usuário. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | Sistema que fornece suporte a aplicativos de várias cenas. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | Sistema que fornece suporte para reconhecimento do ambiente do usuário. |
| | [System](../features/teleport-system/teleport-system.md) | Sistema que fornece suporte para teletransporte (movendo sobre a experiência em saltos). |

Dependências:

- Ativos Padrão ( `com.microsoft.mixedreality.toolkit.standardassets` )

### <a name="standard-assets"></a>Ativos Padrão

O pacote de ativos padrão ( `com.microsoft.mixedreality.toolkit.standardassets)` é uma coleção de componentes que são recomendados para todas as experiências de realidade misturada, incluindo:

- Sombreador Padrão do MRTK
- Materiais básicos usando o sombreador Padrão do MRTK
- Arquivos de áudio
- Fontes
- Texturas
- Ícones

> [!Note]
> Para evitar alterações significativas com base nas definições de assembly, os scripts usados para controlar alguns recursos do sombreador Standard MRTK não estão incluídos no pacote de ativos padrão. Esses scripts podem ser encontrados no pacote base da `MRTK/Core/Utilities/StandardShader` pasta.

Dependências: nenhuma

### <a name="extension-packages"></a>Pacotes de extensão

O pacote de extensões opcionais ( `com.microsoft.mixedreality.toolkit.extensions)` contém componentes adicionais que expandem a funcionalidade do MRTK.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/extensões | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Serviço que adiciona suporte de física a mãos articuladas. |
| | LostTrackingService | Serviço que simplifica a perda de rastreamento em dispositivos Microsoft HoloLens. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Serviço que simplifica a adição de transições de cena suaves. |
| | Amostras ~ | Uma pasta oculta (na editora do Unity) que contém os bastidores de exemplo e os ativos. |

Mais detalhes sobre o processo de uso de pacotes que contêm projetos de exemplo podem ser encontrados no artigo sobre o [Kit de ferramentas da realidade misturada e o Gerenciador de pacotes do Unity](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) .

Dependências:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="tools-package"></a>Pacote de ferramentas

O pacote de ferramentas opcionais ( `com.microsoft.mixedreality.toolkit.tools)` contém ferramentas úteis para a criação de experiências de realidade misturada. Em geral, essas ferramentas são componentes do editor e seu código não é fornecido como parte de um aplicativo.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/ferramentas | |
| | BuildWindow | Ferramenta que ajuda a simplificar o processo de criação e implantação de aplicativos UWP. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Ferramenta que cria um grafo de dependência de ativos em um projeto. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Assistente para ajudar na criação de serviços de extensão. |
| | [MigrationWindow](../features/tools/migration-window.md) | Ferramenta que ajuda na atualização de código que usa componentes do MRTK preterido.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Utilitário para ajudar a automatizar a configuração de um projeto de realidade misturada para o melhor desempenho no Unity. |
| | ReserializeAssetsUtility | Fornece suporte para reserializar arquivos específicos do Unity. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Utilitário que permite aos desenvolvedores determinar rapidamente os mapeamentos do Unity para controladores de hardware. |
| | ScreenshotUtility | Habilita a captura de imagens de aplicativo no editor do Unity. |
| | TextureCombinerWindow | Utilitário para combinar texturas gráficas. |
| | [Caixa de Ferramentas](../features/ux-building-blocks/toolbox.md) | Interface do usuário que facilita a descoberta e o uso de componentes de UX do MRTK. |

Dependências:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="test-utilities-package"></a>Testar pacote de utilitários

O pacote de utilitários de teste opcional ( ) contém uma coleção de scripts auxiliares que permitem aos desenvolvedores criar facilmente `com.microsoft.mixedreality.toolkit.testutilities` testes de modo de reprodução. Esses utilitários são especialmente úteis para desenvolvedores que criam componentes MRTK.

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/testes | |
| | TestUtilities | Métodos para simplificar a criação de testes de modo de reprodução, incluindo utilitários de simulação de mão. |

Dependências:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="examples-package"></a>Pacote de exemplos

O pacote de exemplos ( `com.microsoft.mixedreality.toolkit.examples` ), é estruturado para permitir que os desenvolvedores importem apenas os exemplos de interesse.

Mais detalhes sobre o processo de uso de pacotes que contêm projetos de exemplo podem ser encontrados no artigo sobre o [Kit de ferramentas da realidade misturada e o Gerenciador de pacotes do Unity](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) .

| Pasta | Componente | Descrição |
| --- | --- | --- |
| MRTK/exemplos | | |
| | Amostras ~ | Uma pasta oculta (na editora do Unity) que contém os bastidores de exemplo e os ativos. |
| | StandardAssets | Ativos comuns compartilhados por várias cenas de demonstração. |

Dependências:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )
- Extensões (`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>Confira também

- [Visão geral da arquitetura](../architecture/overview.md)
- [Sistemas, serviços de extensão e provedores de dados](../architecture/systems-extensions-providers.md)
- [Kit de ferramentas de realidade misturada e Gerenciador de pacotes do Unity](../configuration/usingupm.md)
