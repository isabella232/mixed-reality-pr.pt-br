---
title: Notas de versão do MRTK 2,5
description: Notas de versão do MRTK versão 2,5
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 7d3e158bc7e4b0125f264aa9abc8f369a6e825562266891b0528066d8b8b9b71
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198103"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a>notas de versão do Microsoft Mixed reality Toolkit 2,5

> [!IMPORTANT]
> há um problema de compilador conhecido que afeta os aplicativos criados para Microsoft HoloLens 2 usando ARM64. esse problema é corrigido atualizando Visual Studio 2019 para a versão 16,8 ou posterior. se não for possível atualizar Visual Studio, importe o `com.microsoft.mixedreality.toolkit.tools` pacote para aplicar uma solução alternativa.

## <a name="whats-new-in-254"></a>O que há de novo no 2.5.4

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>Corrige um bug com a integração do Oculus ao usar o UPM

Ao usar UPM, o OculusXRSDKDeviceManagerProfile sempre teria seu [pré-fabricados definido como None na inicialização](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160). Esta versão configura o Gerenciador de Dispositivos para apontar para um conjunto de trabalho de pré-fabricados na inicialização.

### <a name="fixes-an-issue-with-openxr-via-upm"></a>Corrige um problema com o OpenXR via UPM

corrige um problema em que os provedores de OpenXR não foram adicionados ao link.xml por padrão, fazendo com que novos projetos falhem na execução no dispositivo ao usar OpenXR e MRTK por meio do Gerenciador de Pacotes do Unity. Os projetos existentes que são atualizados ainda precisarão ser adicionados manualmente.

## <a name="whats-new-in-253"></a>O que há de novo no 2.5.3

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>Corrige uma regressão com o Oculus introduzido no 2.5.2

o 2.5.2 introduziu [um problema de compilação ao integrar o SDK do Oculus](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083). Essa versão reverte esse problema.

## <a name="whats-new-in-252"></a>O que há de novo no 2.5.2

### <a name="add-support-for-openxr"></a>Adicionar suporte para OpenXR

Foi adicionado o suporte inicial para o pacote de visualização do OpenXR da Unity e o pacote OpenXR da realidade misturada da Microsoft. Consulte [a página Introdução ao MRTK/XRSDK, a](../configuration/getting-started-with-mrtk-and-xrsdk.md) [postagem do fórum do Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)ou a [documentação da Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) para obter mais informações.

> [!IMPORTANT]
> O OpenXR no Unity só tem suporte no Unity 2020,3 e superior.
> Ele também dá suporte apenas a compilações de x64, ARM e ARM64.

### <a name="boundary-visualization-errors-fixed"></a>Erros de visualização de limite corrigidos

As visualizações de limite, como o piso ou as paredes, agora serão configuradas e visíveis corretamente em tempo de execução de acordo com o perfil de limite.

### <a name="msbuild-for-unity-support"></a>MSBuild para suporte do Unity

o suporte para MSBuild para Unity foi removido da versão 2.5.2, para se alinhar com a [nova orientação de pacote do Unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).

## <a name="whats-new-in-251"></a>O que há de novo na 2.5.1

### <a name="package-dependency-errors-fixed"></a>Erros de dependência de pacote corrigidos

Esta versão corrige dependências de arquivo entre pacotes incorretas (por exemplo: arquivos em ativos padrão não referenciam mais arquivos na base). A versão 2.5.1 também adiciona uma dependência explícita na Pro de malha de texto.

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>Sombreadores de pacote de ativos padrão copiados para ativos/MRTK/sombreadores

Quando o pacote de ativos padrão for instalado por meio do UPM, os sombreadores serão copiados para a pasta assets/MRTK/shaders para que eles não sejam mais imutáveis. Isso resolve o problema de sombreadores atualizados para o pipeline de processamento universal (URP) para reverter o comportamento herdado na próxima vez que o projeto for carregado.

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>Correção do cursor teleport com mãos

Esta versão corrige um [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) em que o cursor de destino teleport pode ficar com os visuais à mão.

## <a name="whats-new-in-250"></a>O que há de novo no 2.5.0

### <a name="unity-package-manager-upm-support"></a>suporte a Gerenciador de Pacotes do Unity (UPM)

a realidade misturada Toolkit agora pode ser gerenciada usando o Gerenciador de Pacotes do Unity.

![Pacote UPM do MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Há algumas etapas manuais necessárias para importar os pacotes MRTK UPM. examine a [realidade misturada Toolkit e Gerenciador de Pacotes do Unity](../configuration/usingupm.md) para obter mais informações.

### <a name="oculus-quest-xr-sdk-support"></a>Suporte ao SDK do Oculus Quest XR

O MRTK agora dá suporte à execução de headsets e controladores do Oculus Quest usando o pipeline do SDK do XR nativo. O acompanhamento à mão também tem suporte com o [pacote de integração do Oculus da Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) graças ao trabalho [de Eric Provencher](https://twitter.com/prvncher) no MRTK-Quest!

Para obter instruções sobre como implantar seu dispositivo no Oculus Quest usando o novo pipeline, consulte o [Guia de instalação do Oculus Quest](../supported-devices/oculus-quest-mrtk.md)

### <a name="scrolling-object-collection"></a>Rolagem da coleção de objetos

O componente MRTK UX foi atualizado a partir de um recurso experimental e oferece mais liberdade para o layout de conteúdo 3D de tamanhos diferentes com suporte adicional para objetos que não têm colisor anexados. Uma nova opção para desabilitar a máscara de conteúdo também foi adicionada, facilitando a criação de protótipos.

Consulte [rolagem de coleção de objetos](../features/ux-building-blocks/scrolling-object-collection.md) para obter mais informações.

![Rolagem da coleção de objetos](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>Animação de ponteiro teleport, manipulação e melhorias de som

O ponteiro teleport agora tem animações e comentários de áudio aprimorados. Também melhoramos a manipulação do ponteiro teleport para que ele lide mais suave ao fazer a transição para o ponto em superfícies próximas até as superfícies distantes.

### <a name="input-simulation-cheat-sheet"></a>Roteiro de simulação de entrada

A cena HandInteractionExamples agora tem um atalho configurável para mostrar uma página de ajuda para a simulação de entrada

![Roteiro de simulação de entrada](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>Olhar de olho de simulação de entrada com o mouse

Agora, os usuários podem usar o mouse para simular o controle de olho. Consulte o `Eye Simulation Mode` campo no perfil de simulação de entrada e defina-o como mouse. Isso substitui o `Simulate Eye Position` campo anterior.

![Mouse de olho olhar](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>Controlador de movimento de simulação de entrada no modo de reprodução do editor

Agora, os usuários podem simular o controle de movimento como as mãos no modo de reprodução do editor. No momento, há suporte para os botões gatilho, captura e menu.

### <a name="conical-grab-pointer"></a>Ponteiro de captura cônica

Os ponteiros de captura agora podem ser configurados para consultar objetos próximos usando um cone do ponto de captura em vez de uma esfera. isso é mais parecido com o comportamento da interface padrão HoloLens 2, que consulta objetos próximos usando um cone. O DefaultHoloLens2InputSystemProfile também foi ajustado para usar o novo `ConicalGrabPointer` .

![Ponteiro de captura cônica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>Pacote TestUtilities

Agora há um pacote (Microsoft. MixedReality. Toolkit. Unity. TestUtilities. 2.5.0. unitypackage) que contém a infraestrutura de teste PlayMode e testmode que o MRTK usa para criar testes de ponta a ponta. Essa infraestrutura foi extremamente útil para a equipe de MRTK em si, e estamos empolgados em ter consumidores que o utilizam para adicionar cobertura de teste a seus próprios projetos.

O código a seguir mostra como criar uma mão de teste, mostrá-la em um determinado local, movê-la e, em seguida, pinçar e abrir.

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

Para obter instruções sobre como escrever um teste usando esses TestUtilities, consulte esta seção sobre como [escrever testes](../contributing/unit-tests.md#writing-tests).

Para obter exemplos de testes existentes que usam essa infraestrutura, consulte [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)da MRTK.

### <a name="support-for-the-leap-motion-451-unity-modules"></a>Suporte para os módulos do movimento Leap 4.5.1 Unity

O suporte para os módulos do Unity de movimento Leap versão 4.5.1 foi adicionado e o suporte para os ativos 4.4.0 foi removido. As versões atuais com suporte dos módulos do movimento bissexto do Unity são 4.5.0 e 4.5.1.

Também há uma etapa adicional para a integração inicial do movimento Leap, consulte [como configurar o acompanhamento da mão de movimento Leap no MRTK](../supported-devices/leap-motion-mrtk.md) para obter mais informações.

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>O observador de malha de conscientização espacial lida melhor com a personalização de materiais

Com esta versão, o `Windows Mixed Reality Spatial Mesh Observer` e os `Generic XR SDK Spatial Mesh Observer` componentes melhoraram o manuseio de material visual. Os materiais agora são preservados quando uma malha é atualizada pelo observador, onde, anteriormente, eram redefinidos para o VisibleMaterial padrão, conforme configurado no perfil.

Isso permite que os desenvolvedores alterem o material de malha e não tenham as alterações substituídas inesperadamente.

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>Link.xml criado na pasta MixedRealityToolkit. Generated

Com a introdução do Gerenciador de pacotes do Unity MRTK, o MRTK agora grava um `link.xml` arquivo na `Assets/MixedRealityToolkit.Generated` pasta, se nenhum estiver presente. É recomendável adicionar esse arquivo (e `link.xml.meta` ) ser adicionado ao controle do código-fonte. Link.xml é usado para influenciar a funcionalidade de [remoção de código gerenciado](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) do vinculador do Unity.

Mais informações sobre o arquivo de link.xml MRTK podem ser encontradas no artigo [MRTK e a remoção de código gerenciado](../updates-deployment/mrtk-and-managed-code-stripping.md) .

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3 +: a caixa de diálogo de configuração MRTK não tenta mais habilitar o suporte a XR herdado

Para evitar possíveis conflitos ao usar a plataforma XR da Unity, a opção para habilitar o suporte a XR herdado foi removida da caixa de diálogo de configuração do MRTK. se desejar, o suporte a XR herdado poderá ser habilitado, no Unity 2019, usando a realidade de **editar**  >  **Project Configurações**  >
 **Player**  >  **XR Configurações**  >  **com suporte**.

### <a name="reduction-in-initializeonload-overhead"></a>Redução na sobrecarga de InitializeOnLoad

Estamos trabalhando para reduzir a quantidade de trabalho que é executada em manipuladores InitializeOnLoad, o que deve levar a melhorias na velocidade de desenvolvimento do loop interno. Os manipuladores InitializeOnLoad são executados toda vez que um script é compilado, antes da inserção do modo de reprodução e também na inicialização do editor. Esses manipuladores agora são executados em muito menos casos, resultando em melhorias gerais de capacidade de resposta do Unity.

Em alguns casos, houve uma compensação que tinha que ser feita:

- Confira [configuração de acompanhamento da mão de movimento Leap](../supported-devices/leap-motion-mrtk.md) para obter a etapa de integração extra.
- Para aqueles que estão usando o ARFoundation, agora há uma etapa manual adicional em suas etapas de introdução.
  Consulte [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) para obter as novas etapas.
- para aqueles que usarão a [comunicação remota do Holographic com o pipeline do XR herdado](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) no HoloLens 2, agora há uma [etapa manual](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) a ser executada.

### <a name="bounds-control-graduated"></a>Controle de limites graduado

![Controle de limites](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

O [controle de limites](../features/ux-building-blocks/bounds-control.md) foi graduado de forma experimental e vem com vários novos recursos e toneladas de correções de bugs.
Aqui está uma lista dos destaques desta atualização:

- as propriedades são divididas em configurações, o que torna mais fácil configurar o controle de limites
- as configurações podem ser compartilhadas por meio de objetos programáveis
- cada propriedade de propriedade/script é configurável pelo tempo de execução
- o dispositivo de controle de limites não é mais recriado nas alterações de propriedade
- suporte a identificadores de tradução
- suporte completo a restrições por meio do Gerenciador de restrições
- integração do sistema elásticos (experimental)

A caixa delimitadora antiga foi preterida e os objetos de jogo existentes usando a caixa delimitadora podem ser [atualizados usando a ferramenta de migração](../features/tools/migration-window.md) ou o [inspetor da caixa delimitadora](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control).

### <a name="constraint-manager-component"></a>Componente do Gerenciador de restrição

As restrições agora podem ser usadas por ambos, controle de limites e objeto manipulador por meio do novo [componente Gerenciador de restrição](../features/ux-building-blocks/constraint-manager.md). Os dois componentes criarão um Gerenciador de restrição por padrão e processarão quaisquer restrições anexadas automaticamente.

Além disso, o Gerenciador de restrição de comportamento automático também vem com um modo manual que permite aos usuários decidir qual restrição deve ser processada.
Por esse motivo, a maneira como exibimos restrições no Inspetor de propriedades mudou um pouco.

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

As restrições que são aplicadas ao componente agora são mostradas como uma lista no componente Gerenciador de restrição, enquanto o componente usando o Gerenciador de restrição ( [controle de limites](../features/ux-building-blocks/bounds-control.md#constraint-system) ou manipulador de [objeto](../features/ux-building-blocks/object-manipulator.md#constraint-manager)) agora mostrará o Gerenciador e o modo de restrição selecionado (automático ou manual).
Para obter mais informações, leia a seção [Gerenciador de restrição](../features/ux-building-blocks/constraint-manager.md) em nossos documentos.

### <a name="hololens-2-button-material-update"></a>atualização de material de botão HoloLens 2

atualizado o material do compartimento frontal do botão HoloLens 2 para remover a cor preta na MRC.

![atualização de material de botão HoloLens 2](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>Atualização do painel de descrição, cena de exemplo móvel

Painel de descrição atualizado. (SceneDescriptionPanelRev. pré-fabricado) o novo design fornece uma barra superior de captura que permite ao usuário ajustar/mover toda a cena.

![Atualização do painel de descrição](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>Visualização de malha espacial-pulso no ar-toque

exemplo atualizado de sombreador de pulso para a malha espacial para corresponder ao comportamento do shell do HoloLens 2.

![Pulso no ar-toque](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a>Sistema elástico (experimental)

![System2 elástico](../features/images/elastics/Elastics_Main.gif)

O MRTK agora vem com um [sistema de simulação elástica](../features/experimental/elastic-system.md) que inclui uma ampla variedade de subclasses extensíveis e flexíveis, oferecendo associações para molas de quaternions bidimensionais, molas de volume tridimensionais e sistemas Spring lineares simples.

Atualmente, os seguintes componentes do MRTK que dão suporte ao [Gerenciador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) podem aproveitar a funcionalidade de elásticos:

- [Controle de limites](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [Manipulador de objetos](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a>Joystick (experimental)

Um exemplo de interface de joystick que pode controlar um objeto de destino grande.

![Botões](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a>Seletor de cores (experimental)

Um controle experimental que facilita a alteração de cores de material em qualquer objeto no tempo de execução.

![Três métodos diferentes de controle de seletor de cor](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![Quatro métodos diferentes de controle do seletor de cores](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a>Alterações de quebra

### <a name="assembly-definition-files-changes"></a>Alterações de arquivos de definição de assembly

Alguns arquivos asmdef são alterados e agora têm suporte apenas para o Unity 2018.4.13 F1 ou posterior. Erros de compilação serão exibidos ao atualizar para o MRTK 2,5 em versões anteriores do Unity. Isso pode ser corrigido acessando `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` na janela do projeto e removendo a referência ausente no Inspetor. Repita essas etapas com `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` e `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` . Observação Você deve reverter as alterações substituindo esses três arquivos asmdef por aqueles originais (ou seja, não modificados) ao atualizar para o Unity 2019.

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

Esta interface foi atualizada para ter uma nova função:

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

Se você tiver um ponteiro personalizado mediador que não seja subclasse DefaultPointerMediator, será necessário implementar essa nova função. Consulte [esse problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) para obter mais informações sobre por que isso foi adicionado. Isso foi adicionado para garantir que as preferências de ponteiro sejam passadas explicitamente para o mediador, em vez de terem sido feitas implicitamente com base na presença de um construtor que tirou um IPointerPreferences.

### <a name="rest--device-portal-api"></a>API do portal do dispositivo/REST

A `UseSSL` propriedade estática foi movida de `Rest` para `DevicePortal` .

Se você fez isso anteriormente...

```csharp
Rest.UseSSL = true
```

Faça isso agora...

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

se um aplicativo estava usando anteriormente a distribuição de NuGet do MRTK, o `link.xml` arquivo foi removido do pacote base. Para restaurar as regras de preservação de código, abrir o projeto no Unity uma vez criará um `link.xml` arquivo padrão no `Assets/MixedRealityToolkit.Generated` . É recomendável que esse arquivo (e `link.xml.meta` ) seja adicionado ao controle do código-fonte.

### <a name="transform-constraint-changes"></a>Transformar alterações de restrição

A propriedade TargetTransform foi marcada como obsoleta, pois não foi usada pelo sistema de restrição. A lógica de restrição se baseia na transformação passada para os métodos Initialize e Apply. As restrições de usuário derivadas que dependem dessa propriedade podem armazenar em cache o TargetTransform em sua implementação armazenando a transformação do componente de restrição para obter o mesmo comportamento.

O tipo de dados de pose do mundo inicial armazenado foi `worldPoseOnManipulationStart` alterado de MixedRealityPose para MixedRealityTransform, que inclui o valor de escala local do objeto manipulado. Com essa alteração, não é mais necessário armazenar em cache separadamente quaisquer valores iniciais de escala.

### <a name="new-property-in-imixedrealitydictationsystem"></a>Nova propriedade em IMixedRealityDictationSystem

Uma nova propriedade foi `AudioClip` adicionada à interface IMixedRealityDictationSystem. A `AudioClip` Propriedade habilita o acesso ao clipe de áudio associado à sessão de ditado atual. Os usuários devem implementar a propriedade em seus scripts que implementam a interface.

### <a name="service-facades-turn-down"></a>Desativação do serviço fachadas

Os serviços fachadas estão sendo desativados em 2,5. Esse recurso foi originalmente adicionado para tornar a configuração dos perfis MRTK mais fácil (criando GameObjects falsificados na cena que representavam cada um dos serviços de MRTK). A longo prazo, queremos evitar a criação de objetos falsos no jogo e tentar mantê-los em sincronia (como a sincronização de dados e os problemas de "origem de verdade" são notoriamente difíceis de dimensionar e chegar à direita).

Em 2,5, os manipuladores de fachada de serviço são mantidos para garantir que a atualização do projeto seja tranqüila. qualquer fachadas que exista no projeto será excluído pelo manipulador de fachada de serviço para garantir que as cenas abertas no 2,5 sejam corrigidas automaticamente.

O código restante associado ao recurso de fachada do serviço será removido em uma versão futura.

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>Adição de controlador de movimento ao serviço de simulação de entrada

A simulação do controlador de movimento agora é oferecida no modo de reprodução do editor ao longo da simulação de mão existente. Para habilitar essa alteração, muitas funções/campos/propriedades atuais agora estão marcados como obsoletos, com `InputSimulationService.cs` e `MixedRealityInputSimulationProfile.cs` obtendo as alterações mais significativas. A lógica e o comportamento do código relevante permanecem os mesmos amplamente, e a maioria das funções obsoletas, etc., estão relacionadas à substituição da referência a "mãos" para o termo mais genérico "Controller" (por exemplo, de `DefaultHandSimulationMode` para `DefaultControllerSimulationMode` ). Além de obter novos nomes, o tipo de retorno de determinadas funções novas é atualizado para corresponder à alteração de nome/comportamento (por exemplo, `GetControllerDevice` com base no original `GetHandDevice` retornado `BaseController` , em vez de `SimulatedHand` ).

`IInputSimulationService` Agora tem novas propriedades `MotionControllerDataLeft` e `MotionControllerDataRight` . `MixedRealityInputSimulationProfile` Agora inclui novos campos para o mapeamento de teclado de certos botões do controlador de movimento.

## <a name="known-issues"></a>Problemas conhecidos

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache pode criar uma nova câmera ao desligar

Em algumas situações (por exemplo, ao usar o provedor LeapMotion no editor do Unity), é possível que o CameraCache recrie o MainCamera no desligamento. Consulte [este problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) para obter mais informações.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando exemplos são importados por meio do Unity Gerenciador de Pacotes

dependendo do tamanho do caminho do projeto, a importação de exemplos por meio do Unity Gerenciador de Pacotes poderá gerar mensagens FileNotFoundException no Console do Unity. A causa disso é o caminho para o arquivo "Missing" ter mais de MAX_PATH (256 caracteres). Para resolver, reduza o tamanho do caminho do projeto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Nenhum spatializer foi especificado. O aplicativo não dará suporte a som espacial

Um aviso "nenhum spatializer foi especificado" será exibido se um spatializer de áudio não estiver configurado. Isso pode ocorrer se nenhum pacote do XR estiver instalado, pois o Unity inclui spatializers nesses pacotes.

Para resolver, verifique se:

- **Janela**  >  do **Gerenciador de Pacotes** tem um ou mais pacotes XR instalados
- **Realidade misturada Toolkit**  >  **Utilitários**  >  do **configurar Project do Unity** e fazer uma seleção para **Spatializer de áudio**

  ![Selecionar áudio Spatializer](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: referência de objeto não definida para uma instância de um objeto (SceneTransitionService.Initialize)

Em algumas situações, `EyeTrackingDemo-00-RootScene` a abertura pode causar uma NullReferenceException no método Initialize da classe SceneTransitionService.
Esse erro ocorre devido à desdefinição do perfil de configuração do serviço de transição de cena. Para resolver, use as seguintes etapas:

- Navegar até o `MixedRealityToolkit` objeto na hierarquia
- Na janela Inspetor, selecione `Extensions`
- Se não for expandido, expanda `Scene Transition Service`
- Defina o valor de `Configuration Profile` como **MRTKExamplesHubSceneTransitionServiceProfile**

![Corrigir transição de cena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Solicitação Oculus

Atualmente, há um problema conhecido para usar o [plug-in OCULUS XR com o direcionamento de plataformas autônomas](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/). Verifique o Oculus Bug Tracker/fóruns/notas de versão para obter atualizações.

O bug é representado com esse conjunto de três erros:

![Erro de plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Há um problema conhecido para as versões mais recentes do TextMeshPro (1.5.0 + ou 2.1.1 +), em que o tamanho da fonte padrão para os menus suspensos e o espaçamento de caracteres de fonte em negrito foi alterado.

![Imagem TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Isso pode ser solucionado por meio do downgrade para uma versão anterior do TextMeshPro. Consulte o [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) para obter mais detalhes.
