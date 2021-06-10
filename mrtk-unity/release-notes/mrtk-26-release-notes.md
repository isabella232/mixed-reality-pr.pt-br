---
title: Notas de versão do MRTK 2,6
description: Notas de versão do MRTK versão 2,6
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 4ac82f7e07135e840886fef810844ff00ef1ac1e
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647189"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Notas de versão do Microsoft Mixed Reality Toolkit 2,6

> [!IMPORTANT]
> Há um problema de compilador conhecido que afeta os aplicativos criados para o Microsoft HoloLens 2 usando o ARM64. Esse problema é corrigido com a atualização do Visual Studio 2019 para a versão 16,8 ou posterior. Se não for possível atualizar o Visual Studio, importe o `com.microsoft.mixedreality.toolkit.tools` pacote para aplicar uma solução alternativa.

## <a name="whats-new-in-262"></a>O que há de novo no 2.6.2

### <a name="corrects-parenting-of-the-spatial-mesh"></a>Corrige o pai da malha espacial

Corrige o [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) em que as malhas espaciais não estavam sendo corretamente localizadas depois que o objeto Playspace da realidade misturada foi movido (ex: por meio de um teleport).

## <a name="whats-new-in-261"></a>O que há de novo no 2.6.1

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>Corrige OpenXR não em execução no HoloLens 2/UWP

Corrige uma regressão que impediu o suporte de OpenXR da MRTK de ser executado no UWP.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>Corrige o objectmanipulador de movimento LEAP não girando

Corrige uma regressão em que a rotação de uma mão de movimento LEAP não foi levada em conta pelo script objectmanipuletor.

### <a name="sample-scene-updates"></a>Atualizações de cena de exemplo

Atualiza a cena de exemplo de compreensão da cena para refletir corretamente o estado de envio do plug-in do Unity. Também atualiza o exemplo para que não tenha mais uma dependência da cena de amostra de conscientização espacial que está sendo importada. Antes de atualizar para o 2.6.1, você deve excluir as amostras de reconhecimento espacial e compreensão de cena importadas se elas estiverem presentes no seu projeto para evitar possíveis conflitos. Se você não tiver removido esses exemplos e vir conflitos relacionados a eles no console do, remova os dois exemplos (ou a `Assets/Samples/Mixed Reality Toolkit Examples` pasta) e tente importar novamente.

Atualiza a cena de exemplo de caixa de diálogo para descrever corretamente os cenários de caixa de diálogo atuais.

## <a name="whats-new-in-260"></a>O que há de novo no 2.6.0
<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>Adicionar suporte para OpenXR

Foi adicionado o suporte inicial para o pacote de visualização do OpenXR da Unity e o pacote OpenXR da realidade misturada da Microsoft. Consulte [a página Introdução ao MRTK/XRSDK, a](../configuration/getting-started-with-mrtk-and-xrsdk.md) [postagem do fórum do Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)ou a [documentação da Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) para obter mais informações.

> [!IMPORTANT]
> O OpenXR no Unity só tem suporte no Unity 2020,2 e superior.
>
> Atualmente, ele também dá suporte apenas a compilações de x64 e ARM64.

### <a name="asset-swap-utility"></a>Utilitário de permuta de ativos

Troque vários ativos em uma cena do Unity com o novo [Utilitário de permuta de ativos](../features/tools/asset-swap-utility.md).

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>Os controladores HP Motion agora têm suporte com o MRTK

Controladores para o HP reverb G2 agora funcionam nativamente com MRTK.

### <a name="experimental-interactive-element--state-visualizer"></a>Elemento interativo experimental + Visualizador de estado

O elemento interativo é um ponto de entrada centralizado simplificado para o sistema de entrada MRTK. Ele contém métodos de gerenciamento de estado, gerenciamento de eventos e a lógica de configuração de estado para os Estados de interação principal. Para obter mais informações, consulte [documentação de elemento interativo](../features/experimental/interactive-element.md).

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

O Visualizador de estado é um componente de animação que depende do elemento interativo.  Esse componente cria clipes de animação, define quadros-chave e gera um computador de estado Animator. Para obter mais informações, consulte [documentação do State Visualizer](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>A teleportação com o gesto teleport agora tem suporte em todas as plataformas

Agora, os usuários podem usar o gesto de teleport para se mover em todo o espaço de reprodução em todas as plataformas. Para teleport com um controlador em dispositivos MR com configurações padrão, use o Thumbstick. Para teleportr com as mãos articuladas, faça um gesto com seu Palm voltado para cima com o índice e o polegar para cima, concluindo o teleport ao enrolar o dedo do índice. Para teleport com a simulação de entrada, consulte nossa [documentação](../features/input-simulation/input-simulation-service.md)atualizada do serviço de simulação de entrada.

  ![Gesto de teleport](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>Compreensão da cena agora disponível no MRTK como um observador de reconhecimento espacial experimental

O suporte experimental do [entendimento da cena](/windows/mixed-reality/scene-understanding) foi introduzido no MRTK 2,6. Os usuários podem incorporar os recursos de compreensão da cena do HoloLens 2 como um observador de conscientização espacial em projetos baseados em MRTK. Leia a [documentação de compreensão da cena](../features/spatial-awareness/scene-understanding.md) para obter mais informações.

> [!IMPORTANT]
> Só há suporte para a compreensão da cena no HoloLens 2 e no Unity 2019,4 e superior.
>
> Este recurso requer o pacote de compreensão da cena, que agora está disponível por meio da [ferramenta de recursos de realidade misturada](https://aka.ms/MRFeatureTool).
> Ao usar a ferramenta de funcionalidade Mixed Reality ou importar de outra forma via UPM, importe o exemplo de demos-SpatialAwareness antes de importar o exemplo experimental-SceneUnderstanding devido a um problema de dependência. Consulte [este problema do GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obter mais informações.

  ![Compreensão da cena](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>Suporte à alternância de perfil de tempo de execução

O MRTK agora permite a troca de perfil antes da inicialização da instância MRTK (ou seja, a opção de perfil de inicialização MRTK) e, depois que um perfil está em uso ativo (ou seja, a opção de perfil ativo). A opção anterior pode ser usada para habilitar componentes selecionados com base nos recursos do hardware, enquanto o último pode ser usado para modificar a experiência, pois o usuário insere um subitem do aplicativo. Leia a [documentação sobre a alternância de perfil](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) para obter mais informações e exemplos de código.

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>Indicador direcional e siga os resolvedores graduados de experimental

Dois novos resolvedores estão prontos para uso com o MRTK principal.

  ![Resolvedor de indicador direcional](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>O direito de mão graduado de experimental

Agora, o recurso de a mão está pronto para uso com o MRTK principal.
  ![Exemplo de direito do](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>Controles de caixa de diálogo graduados de experimental

Os controles da caixa de diálogo agora estão prontos para uso com o MRTK principal.

  ![Controles de diálogo](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>Sombreador de pulso graduado de experimental

Os scripts do Pulse Shader graduaram de forma experimental. Para obter mais informações, consulte: [documentação do sombreador de pulso](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>Aprimoramentos do serviço de registro de entrada

`InputRecordingService` e `InputPlaybackService` agora pode gravar e reproduzir a entrada olhar de olho. A gravação foi otimizada para garantir uma taxa de quadros consistente durante o período de gravação, enquanto o tamanho do arquivo de gravação e o tempo de salvamento também são reduzidos em cerca de 50%. O salvamento e o carregamento de arquivos de gravação agora podem ser executados de forma assíncrona. Observe que o formato de arquivo da gravação foi alterado nesta versão do MRTK, consulte [aqui](../features/input-simulation/input-animation-file-format.md) para obter mais informações sobre as novas especificações da versão 1,1.

### <a name="reading-mode"></a>Modo de leitura

Adicionado suporte para o [modo de leitura](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) no HoloLens 2. O modo de leitura reduz o campo de exibição do sistema, mas elimina um dimensionamento da saída do Unity. Um pixel renderizado pelo Unity corresponderá a um pixel projetado no HoloLens 2. Os autores de aplicativos devem fazer testes com várias pessoas para ter certeza de que essa é uma desvantagem que desejam em seu aplicativo.

  ![Modo de leitura de realidade mista do Windows](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>Suporte para iniciadores de aplicativos 3D no UWP

Adiciona a capacidade de definir um [iniciador de aplicativo 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para UWP. Essa configuração é exposta tanto na janela de compilação do MRTK quanto nas configurações do projeto MRTK, em configurações de compilação. Ele é gravado automaticamente no projeto durante a compilação no Unity.

  ![Configurações de build](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>Alterações de quebra

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>Determinados campos dos objetos GLTF importados agora estão em letras maiúsculas

Devido a problemas relacionados à desserialização, alguns campos dos objetos GLTF importados agora começam com letras maiúsculas. Os campos afetados são (em seus novos nomes):,,,,,, `ComponentType` `Path` ,, `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` , `WrapT` .

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>O arquivo binário da animação de entrada tem um formato atualizado de versão 1,1

O arquivo binário de animação de entrada, usado por `InputRecordingService` e `InputPlaybackService` , agora tem um formato de arquivo atualizado para habilitar as otimizações feitas nesses dois serviços. Consulte [aqui](../features/input-simulation/input-animation-file-format.md) para obter mais informações sobre as novas especificações da versão 1,1.

### <a name="msbuild-for-unity-support"></a>Suporte do MSBuild para Unity

O suporte para MSBuild para Unity foi removido da versão 2.5.2, para se alinhar com a [nova orientação de pacote do Unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).

## <a name="known-issues"></a>Problemas conhecidos

### <a name="openxr"></a>OpenXR

Atualmente, há um problema conhecido com Holographic de comunicação remota e OpenXR, em que as junções de mão não estão disponíveis de forma consistente.
Além disso, as cenas de exemplo de acompanhamento ocular não são compatíveis no momento, embora o acompanhamento ocular *funcione.*

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Alguns recursos do Sombreador Standard do Kit de Ferramentas de Realidade Misturada exigem o pacote Foundation

Quando importados por meio do Gerenciador de Pacotes Unity, os scripts de utilitários do Sombreador Padrão do MRTK (por ex. HoverLight.cs) não são co-localizados com o sombreador no pacote Ativos Padrão. Para acessar essa funcionalidade, os aplicativos exigirão que o pacote Foundation seja importado.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache pode criar uma nova câmera no desligamento

Em algumas situações (por exemplo, ao usar o provedor LeapMotion no Editor do Unity), é possível que o CameraCache crie a MainCamera no desligamento. Consulte esse [problema para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) obter mais informações.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando exemplos são importados por meio do Unity Gerenciador de Pacotes

Dependendo do comprimento do caminho do projeto, importar exemplos por meio do Unity Gerenciador de Pacotes pode gerar mensagens FileNotFoundException no Console do Unity. A causa disso é o caminho para o arquivo "ausente" ser maior que MAX_PATH (256 caracteres). Para resolver, reduza o comprimento do caminho do projeto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Nenhum espacializador foi especificado. O aplicativo não dará suporte ao Som Espacial

Um aviso "Nenhum espacializador foi especificado" será exibido se um espacializador de áudio não estiver configurado. Isso poderá ocorrer se nenhum pacote XR estiver instalado, pois o Unity inclui espacializadores nesses pacotes.

Para resolver, verifique se:

- **Janela**  >  **Gerenciador de Pacotes** tem um ou mais pacotes XR instalados
- **Kit de Ferramentas de Realidade Misturada**  >  **Utilitários**  >  **Configurar o Projeto do Unity** e fazer uma seleção para o **Espacializador de Áudio**

  ![Selecione Espacializador de Áudio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: referência de objeto não definida como uma instância de um objeto (SceneTransitionService.Initialize)

Em algumas situações, a `EyeTrackingDemo-00-RootScene` abertura pode causar uma NullReferenceException no método Initialize da classe SceneTransitionService.
Esse erro ocorre porque o perfil de configuração do Serviço de Transição de Cena está sendo desatoado. Para resolver, use as seguintes etapas:

- Navegue até `MixedRealityToolkit` o objeto na Hierarquia
- Na janela Inspetor, selecione `Extensions`
- Se não estiver expandido, expanda `Scene Transition Service`
- Definir o valor de `Configuration Profile` como **MRTKExamplesHubSceneTransitionServiceProfile**

![Corrigir perfil de transição de cena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Solicitação Oculus

Atualmente, há um problema conhecido para usar o [plug-in do Oculus XR com ao direcionar plataformas autônomas.](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)  Verifique o rastreador de bugs do Oculus/fóruns/notas sobre a versão para ver se há atualizações.

O bug é significado com este conjunto de três erros:

![Erro de plug-in do Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Há um problema conhecido para versões mais recentes do TextMeshPro (1.5.0+ ou 2.1.1+), em que o tamanho da fonte padrão para menus suspensos e espaçamento de caracteres de fonte em negrito foi alterado.

![Imagem TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Isso pode ser feito com o downgrade para uma versão anterior do TextMeshPro. Consulte [o problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) para obter mais detalhes.