---
title: Notas de versão do MRTK 2.6
description: Notas sobre a versão do MRTK versão 2.6
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 452f0f352443620dea70b1680859bab4e2b3a0818de5f130accdb84c2798cfe0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206682"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Notas de versão do Microsoft Mixed Reality Toolkit 2.6

> [!IMPORTANT]
> Há um problema conhecido do compilador que afeta os aplicativos compilados para Microsoft HoloLens 2 usando ARM64. Esse problema é corrigido pela atualização do Visual Studio 2019 para a versão 16.8 ou posterior. Se você não conseguir atualizar Visual Studio, importe o `com.microsoft.mixedreality.toolkit.tools` pacote para aplicar uma solução alternativa.

## <a name="whats-new-in-262"></a>Novidades na versão 2.6.2

### <a name="corrects-parenting-of-the-spatial-mesh"></a>Corrige o pai da malha espacial

Corrige o [problema em](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) que malhas espaciais não estavam sendo localizadas corretamente depois que o objeto do Playspace de Realidade Misturada foi movido (por ex.: por meio de um teletransporte).

## <a name="whats-new-in-261"></a>Novidades na versão 2.6.1

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>Corrige a não execução do OpenXR no HoloLens 2/UWP

Corrige uma regressão que impedia a execução do suporte openXR do MRTK na UWP.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>Corrige o ObjectManipulator de Movimento Bissexo que não está girando

Corrige uma regressão em que a rotação de uma mão do Leap Motion não foi levada em conta pelo script ObjectManipulator.

### <a name="sample-scene-updates"></a>Atualizações de cena de exemplo

Atualiza a cena de exemplo de compreensão da cena para refletir corretamente o estado enviado do plug-in do Unity. Também atualiza o exemplo para não ter mais uma dependência da cena de exemplo de reconhecimento espacial que está sendo importada. Antes de atualizar para a 2.6.1, exclua os exemplos de reconhecimento espacial e compreensão de cena importados se eles estão presentes em seu projeto para evitar possíveis conflitos. Se você não removeu esses exemplos e vê conflitos relacionados a eles no console, remova os dois exemplos (ou a pasta) e tente importar `Assets/Samples/Mixed Reality Toolkit Examples` novamente.

Atualiza a cena de exemplo da caixa de diálogo para descrever corretamente os cenários de diálogo atuais.

## <a name="whats-new-in-260"></a>Novidades na versão 2.6.0

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>Adicionar suporte para OpenXR

O suporte inicial para o pacote de versão prévia do OpenXR do Unity e o pacote OpenXR de Realidade Misturada da Microsoft foi adicionado. Consulte a página de início do [MRTK/XRSDK,](../configuration/getting-started-with-mrtk-and-xrsdk.md)a postagem do fórum do [Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)ou a documentação [da Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) para obter mais informações.

> [!IMPORTANT]
> O OpenXR no Unity só tem suporte no Unity 2020.2 e superior.
>
> Atualmente, ele também dá suporte apenas a builds x64 e ARM64.

### <a name="asset-swap-utility"></a>Utilitário de troca de ativos

Altere vários ativos em uma cena do Unity com o novo utilitário [Asset Swap](../features/tools/asset-swap-utility.md).

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>Controladores de movimento HP agora são suportados com o MRTK

Os controladores para o HP Reverb G2 agora funcionam de forma nativa com o MRTK.

### <a name="experimental-interactive-element--state-visualizer"></a>Elemento interativo experimental + visualizador de estado

O Elemento Interativo é um ponto de entrada centralizado simplificado para o sistema de entrada do MRTK. Ele contém métodos de gerenciamento de estado, gerenciamento de eventos e a lógica de configuração de estado para estados de interação principais. Para obter mais informações, consulte [Documentação do elemento interativo](../features/experimental/interactive-element.md).

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

O Visualizador de Estado é um componente de animação que depende do Elemento Interativo. Esse componente cria Clipes de Animação, define os keyframes e gera um Computador de Estado animador. Para obter mais informações, consulte [Documentação do Visualizador de Estado](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>Agora há suporte para o gesto de teletransporte em todas as plataformas

Os usuários agora podem usar o gesto de teletransporte para mover seu espaço de reprodução em todas as plataformas. Para usar um controlador em dispositivos MR com configurações padrão, use o thumbstick. Para fazer um gesto com as mãos articuladas, faça um gesto com a mão voltada para cima com o índice e o polegar para fora, concluindo o anel ondulando o dedo indicador. Para fazer a simulação de entrada, confira nossa documentação atualizada [do Serviço de Simulação de Entrada](../features/input-simulation/input-simulation-service.md).

![Gesto de Teletransporte](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>O Reconhecimento de Cena agora está disponível no MRTK como um observador experimental de reconhecimento espacial

O suporte experimental do [Entendimento de Cena](/windows/mixed-reality/scene-understanding) é introduzido no MRTK 2.6. Os usuários podem incorporar as funcionalidades de reconhecimento de cena do HoloLens 2 como um observador de reconhecimento espacial em projetos baseados no MRTK. Leia a [documentação do Scene Understanding para](../features/spatial-awareness/scene-understanding.md) obter mais informações.

> [!IMPORTANT]
> O Entendimento de Cena só tem suporte HoloLens 2 e Unity 2019.4 e superior.
>
> Esse recurso requer o pacote De compreensão de cena, que agora está disponível por meio da Ferramenta [de Recursos de Realidade Misturada](https://aka.ms/MRFeatureTool).
> Ao usar a Ferramenta de Recursos de Realidade Misturada ou importar por meio de UPM, importe o exemplo Demonstrações – SpatialAwareness antes de importar o exemplo Experimental - SceneUnderstanding devido a um problema de dependência. Confira este [GitHub para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) obter mais informações.

![Noções básicas sobre a cena](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>Suporte à alternação de perfil de runtime

O MRTK agora permite a alternação de perfil antes da inicialização da instância do MRTK (ou seja, opção de perfil de inicialização pré-MRTK) e depois que um perfil está em uso ativo (ou seja, opção de perfil ativo). A opção anterior pode ser usada para habilitar a seleção de componentes com base nas funcionalidades do hardware, enquanto a última pode ser usada para modificar a experiência à medida que o usuário inser em uma subparte do aplicativo. Leia a [documentação sobre a alternação de perfil](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) para obter mais informações e exemplos de código.

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>Indicador direcional e solucionadores de acompanhamento com base em experimentais

Dois novos solucionadores estão prontos para uso com o MRTK de linha principal.

![Solucionador de Indicador Direcional](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>Hand Coach formado em experimentais

O recurso Hand Coach agora está pronto para uso com o MRTK de linha principal.

![Exemplo de técnico de mão](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>Controles de caixa de diálogo formados por experimentais

Os controles de caixa de diálogo agora estão prontos para uso com o MRTK de linha principal.

![Controles de caixa de diálogo](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>Sombreador de pulso com base em experimental

Os scripts do sombreador Pulse se desdoram de experimentais. Para obter mais informações, consulte: [Documentação do sombreador de pulso](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>Melhorias no Serviço de Gravação de Entrada

`InputRecordingService` e `InputPlaybackService` agora podem registrar e reproduzir a entrada de olhar para trás. A gravação foi otimizada para garantir uma taxa de quadros consistente durante o período de gravação, enquanto o tamanho do arquivo de gravação e o tempo de economia também são reduzidos em cerca de 50%. Salvar e carregar arquivos de gravação agora pode ser executado de forma assíncrona. Observe que o formato de arquivo da gravação foi [](../features/input-simulation/input-animation-file-format.md) alterado nesta versão do MRTK. Consulte aqui para obter mais informações sobre as novas especificações da versão 1.1.

### <a name="reading-mode"></a>Modo de leitura

Adicionado suporte para [o modo de](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) leitura HoloLens 2. O modo de leitura reduz o campo de exibição do sistema, mas elimina um dimensionamento da saída do Unity. Um pixel renderizado pelo Unity corresponderá a um pixel projetado HoloLens 2. Os autores de aplicativos devem fazer testes com vários indivíduos para ter certeza de que essa é uma recompensa que eles querem em seu aplicativo.

![Windows Mixed Reality modo de leitura](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>Suporte para iniciadores de aplicativo 3D na UWP

Adiciona a capacidade de definir um [launcher de aplicativo 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para UWP. Essa configuração é exposta na Janela de Build do MRTK e no Project Configurações MRTK, em Build Configurações. Ele é gravado automaticamente no projeto durante o build no Unity.

![Configurações de build](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>Alterações de quebra

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>Determinados campos de objetos GLTF importados agora estão em maiúsculas

Devido a problemas relacionados à desseerlização, alguns campos de objetos GLTF importados agora estão começando com letras maiúsculas. Os campos afetados são (em seus novos nomes): `ComponentType` , , , , , , , , , `Path` , `Interpolation` , `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` .

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>O arquivo binário de animação de entrada tem um formato atualizado da versão 1.1

O arquivo binário de animação de entrada, usado por e , agora tem um formato de arquivo atualizado para habilitar as `InputRecordingService` `InputPlaybackService` otimizações feitas nesses dois serviços. Consulte aqui [para](../features/input-simulation/input-animation-file-format.md) obter mais informações sobre as novas especificações da versão 1.1.

### <a name="msbuild-for-unity-support"></a>MSBuild suporte ao Unity

O suporte para MSBuild para Unity foi removido a partir da versão 2.5.2, para alinhar-se com as novas diretrizes de [pacote do Unity.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="known-issues"></a>Problemas conhecidos

### <a name="openxr"></a>OpenXR

Atualmente, há um problema conhecido com o Holographic Remoting e o OpenXR, em que as junções de mão não estão consistentemente disponíveis.
Além disso, as cenas de exemplo de acompanhamento ocular não são compatíveis no momento, embora o acompanhamento ocular _funcione._

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Alguns recursos do Sombreador Padrão Toolkit Realidade Misturada exigem o pacote Foundation

Quando importados por meio do Gerenciador de Pacotes Unity, os scripts de utilitários do Sombreador Padrão do MRTK (por ex. HoverLight.cs) não são co-localizados com o sombreador no pacote Ativos Padrão. Para acessar essa funcionalidade, os aplicativos exigirão que o pacote Foundation seja importado.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache pode criar uma nova câmera no desligamento

Em algumas situações (por exemplo, ao usar o provedor LeapMotion no Editor do Unity), é possível que o CameraCache crie a MainCamera no desligamento. Consulte esse [problema para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) obter mais informações.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando exemplos são importados por meio do Unity Gerenciador de Pacotes

Dependendo do comprimento do caminho do projeto, importar exemplos por meio do Unity Gerenciador de Pacotes pode gerar mensagens FileNotFoundException no Console do Unity. A causa disso é o caminho para o arquivo "ausente" ser maior que MAX_PATH (256 caracteres). Para resolver, reduza o comprimento do caminho do projeto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Nenhum espacializador foi especificado. O aplicativo não dará suporte ao Som Espacial

Um aviso "Nenhum espacializador foi especificado" será exibido se um espacializador de áudio não estiver configurado. Isso poderá ocorrer se nenhum pacote XR estiver instalado, pois o Unity inclui espacializadores nesses pacotes.

Para resolver, verifique se:

- **Janela**  >  **Gerenciador de Pacotes** tem um ou mais pacotes XR instalados
- **Realidade Misturada Toolkit**  >  **Utilitários**  >  **Configurar o Unity Project** e fazer uma seleção para o **Espacializador de Áudio**

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

Atualmente, há um problema conhecido para usar o [plug-in do Oculus XR com ao direcionar plataformas autônomas.](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/) Verifique o rastreador de bugs do Oculus/fóruns/notas sobre a versão para ver se há atualizações.

O bug é significado com este conjunto de três erros:

![Erro de plug-in do Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Há um problema conhecido para versões mais recentes do TextMeshPro (1.5.0+ ou 2.1.1+), em que o tamanho da fonte padrão para menus suspensos e espaçamento de caracteres de fonte em negrito foi alterado.

![Imagem TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Isso pode ser feito com o downgrade para uma versão anterior do TextMeshPro. Consulte [o problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) para obter mais detalhes.
