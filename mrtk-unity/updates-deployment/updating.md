---
title: Atualização de versões anteriores
description: Documentação para migrar da versão inferior do MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 5a914d6408d346dac0bf6c683f401564e875f4d8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175103"
---
# <a name="updating-from-earlier-versions"></a>Atualização de versões anteriores

- [Atualizando para uma nova versão do MRTK](#upgrading-to-a-new-version-of-mrtk)
- [2.3.0 a 2.4.0](#updating-230-to-240)
- [2.2.0 a 2.3.0](#updating-220-to-230)
- [2.1.0 a 2.2.0](#updating-210-to-220)
- [2.0.0 a 2.1.0](#updating-200-to-210)
- [RC2 a 2.0.0](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>Localizar a versão atual 

Siga estas instruções para descobrir qual versão do MRTK você está usando no momento:

1. Abra seu projeto do MRTK no Unity
2. Navegue até a pasta "MixedRealityToolkit" na janela Project aplicativo
3. Abra o arquivo chamado "Versão"

Se o arquivo e a pasta acima não existirem, você está em uma versão mais recente do MRTK. Nesse caso, tente o seguinte:

1. Navegue até a pasta "Mixed Reality Toolkit Foundation"
2. Clique no botão "package.jsem" para ver uma versão prévia no Unity ou abra-a com um editor de texto
3. Procure a linha com a palavra "version:" 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>Atualizando para uma nova versão do MRTK

*É altamente recomendável executar [](../features/tools/migration-window.md)* a ferramenta de migração depois de obter a atualização do MRTK para corrigir automaticamente e atualizar de componentes preterido e ajustar-se às alterações interrupntes. A ferramenta de migração faz parte do **pacote Ferramentas.**

As instruções a seguir descrevem o caminho de atualização 2.4.0 para 2.5.0. Se o projeto estiver na versão 2.3.0 [](#updating-230-to-240) ou anterior, leia as alterações entre [](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) as versões para entender o caminho de atualização ou leia as instruções da versão anterior para fazer uma atualização de versão por versão.

### <a name="mixed-reality-feature-tool"></a>Ferramenta Recurso de Realidade Misturada
A maneira mais fácil de atualizar o MRTK para [](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) uma versão mais recente do MRTK é usando a Ferramenta de Recursos de Realidade Misturada para baixar os pacotes mais recentes e carregá-los diretamente no projeto do Unity.

Se o projeto usou anteriormente arquivos de ativos do Unity (.unitypackage), confira [estas instruções.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool) 

### <a name="unity-asset-unitypackage-files"></a>Arquivos de ativos do Unity (.unitypackage)

Outro caminho de atualização é baixar manualmente os pacotes do Unity do MRTK e aplicá-los ao seu projeto. Consulte as etapas abaixo,

1. Salve uma cópia do seu projeto atual, caso você tenha problemas a qualquer momento nas etapas de atualização.
1. Fechar Unity
1. Dentro da *pasta Ativos,* exclua as seguintes pastas **do MRTK,** juntamente com seus arquivos .meta (o projeto pode não ter todas as pastas listadas)
    - MRTK/Core
    - MRTK/Exemplos
    - MRTK/Extensões
    - MRTK/Provedores
    - MRTK/SDK
    - MRTK/Serviços
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Se foram feitas modificações nos sombreadores do MRTK, crie um backup local antes de excluir a pasta MRTK/StandardAssets
    - MRTK/Ferramentas
    > [!IMPORTANT]
    > NÃO exclua **a pasta MixedRealityToolkit.Generated** ou seu arquivo .meta.
1. Excluir a **pasta Biblioteca**
    > [!IMPORTANT]
    > Algumas ferramentas do Unity, como o Unity Collab, salvam informações de configuração na pasta Biblioteca. Se estiver usando uma ferramenta que faça isso, primeiro copie a pasta de dados da ferramenta da Biblioteca antes de excluir e restaure-a depois que a Biblioteca for regenerada.
1. Reaberto o projeto no Unity
1. Importar os novos pacotes do Unity
    - Foundation – _Importar este pacote primeiro_
    - Ferramentas
    - (Opcional) Extensões
    > [!NOTE]
    > Se extensões adicionais foram instaladas, talvez precisem ser importadas de novo.
    - (Opcional) Exemplos
1. Feche o Unity e exclua **a pasta** Biblioteca (leia a observação abaixo primeiro!). Essa etapa é necessária para forçar o Unity a atualizar seu banco de dados de ativos e reconciliar perfis personalizados existentes.
1. Iniciar o Unity e para cada cena no projeto
    - **Exclua MixedRealityToolkit** **e MixedRealityPlayspace,** se presente, da hierarquia. Isso excluirá a câmera principal, mas ela será criada na próxima etapa. Se alguma propriedade da câmera principal tiver sido alterada manualmente, elas deverão ser aplicadas novamente manualmente depois que a nova câmera for criada.
    - Selecione **MixedRealityToolkit -> Adicionar à Cena e Configurar**
    - Selecione **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (precisa ser feito apenas uma vez) – isso atualizará todos os perfis de mapeamento de controlador personalizado com eixos e dados atualizados, deixando suas ações de entrada atribuídas personalizadas intactas
1. Execute a [ferramenta de migração](../features/tools/migration-window.md) e execute a ferramenta no Project *completo* para garantir que todo o seu código seja atualizado para o mais recente.
   A janela de migração contém vários manipuladores de migração diferentes, que devem ser executados por conta própria. Esta etapa envolve:
   - Selecione o primeiro manipulador de migração na lista **suspenso Seleção do Manipulador de** Migração.
   - Clique no botão "Project completo".
   - Clique no botão "Adicionar projeto completo para migração" (isso verificará todo o projeto em busca de objetos para migrar).
   - Clique no botão "Migrar", que deverá ser habilitado se algum objeto migrado for encontrado.
   - Repita as três etapas anteriores para cada um dos manipuladores de migração na lista suspenso.
     (Veja [esse problema que](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) aborda o trabalho que pode ser feito para simplificar esse processo de migração em uma versão futura)

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>Alternando de arquivos de ativos do Unity para a Ferramenta de Recursos de Realidade Misturada

Alternar de arquivos de ativos do Unity para pacotes da Ferramenta de Recursos de Realidade Misturada traz vários benefícios:

- Atualização mais fácil
- Tempos de compilação mais rápidos
- Menos projetos na solução Visual Studio dados

Alterar para usar a Ferramenta de Recursos de Realidade Misturada requer um conjunto único de etapas manuais.

1. Salve uma cópia do projeto atual.
1. Fechar Unity
1. Dentro da *pasta Ativos,* exclua as seguintes pastas **do MRTK,** juntamente com seus arquivos .meta (o projeto pode não ter todas as pastas listadas)
    - MRTK/Core
    - MRTK/Exemplos
    - MRTK/Extensões
    - MRTK/Provedores
    - MRTK/SDK
    - MRTK/Serviços
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Se foram feitas modificações nos sombreadores do MRTK, crie um backup local antes de excluir a pasta MRTK/StandardAssets
    - MRTK/Ferramentas
    > [!IMPORTANT]
    > NÃO exclua **a pasta MixedRealityToolkit.Generated** ou seu arquivo .meta.
1. Excluir a **pasta Biblioteca**
    > [!IMPORTANT]
    > Algumas ferramentas do Unity, como o Unity Collab, salvam informações de configuração na pasta Biblioteca. Se estiver usando uma ferramenta que faça isso, primeiro copie a pasta de dados da ferramenta da Biblioteca antes de excluir e restaure-a depois que a Biblioteca for regenerada.
1. Reaberto o projeto no Unity

Depois que as etapas anteriores foram executadas, execute [a](#mixed-reality-feature-tool) Ferramenta de Recursos de Realidade Misturada e importe a versão desejada do Toolkit.

## <a name="updating-230-to-240"></a>Atualizando 2.3.0 para 2.4.0

[Renomeações de pasta](#folder-renames-in-240) 
 [Alterações na API](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>Renomeações de pasta na 2.4.0

As pastas MixedRealityToolkit foram renomeadas e movidas para uma hierarquia comum na versão 2.4. Se um aplicativo usar caminhos codificados para recursos do MRTK, ele precisará ser atualizado de acordo com a tabela a seguir.

| Pasta anterior | Nova Pasta |
| --- | --- |
| MixedRealityToolkit | MRTK/Core |
| MixedRealityToolkit.Examples | MRTK/Exemplos |
| MixedRealityToolkit.Extensions | MRTK/Extensões |
| MixedRealityToolkit.Providers | MRTK/Provedores |
| MixedRealityToolkit.SDK | MRTK/SDK |
| MixedRealityToolkit.Services | MRTK/Serviços |
| MixedRealityToolkit.Tests | MRTK/testes |
| MixedRealityToolkit.Tools | MRTK/Ferramentas |

> [!IMPORTANT]
> O `MixedRealityToolkit.Generated` contém arquivos gerados pelo cliente e permanece inalterado.

### <a name="eye-gaze-setup-in-240"></a>Configuração do olhar na 2.4.0

Esta versão do MRTK modifica as etapas necessárias para a configuração do olhar. A _caixa de seleção 'IsEyeTrackingEnabled'_ pode ser encontrada nas configurações de olhar do perfil de ponteiro de entrada. A verificação dessa caixa habilita o olhar com base no olhar e, em vez disso, o olhar com base na cabeça padrão.

Para obter mais informações sobre essas alterações e instruções completas sobre a configuração do acompanhamento ocular, confira o artigo [acompanhamento ocular.](../features/input/eye-tracking/eye-tracking-basic-setup.md)

### <a name="eye-gaze-pointer-behavior-in-240"></a>Comportamento do ponteiro de olhar em 2.4.0

O comportamento padrão do ponteiro do olhar com o olhar foi modificado para corresponder ao comportamento padrão do ponteiro de olhar para a cabeça. Um ponteiro de olhar para o olhar será suprimido automaticamente depois que uma mão for detectada. O ponteiro do olhar ficará visível novamente depois de dizer "Selecionar".

Detalhes sobre o olhar e as configurações de mão podem ser encontrados no artigo [olhos e](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) mãos.

### <a name="api-changes-in-240"></a>Alterações de API na 2.4.0

**Classes de controlador personalizadas**

Classes de controlador personalizadas anteriormente tinham que definir `SetupDefaultInteractions(Handedness)` . Esse método tornou-se obsoleto na 2.4, pois o parâmetro de entrega era redundante com a própria mão da classe do controlador. O novo método não tem parâmetros. Além disso, muitas classes de controlador definiram isso da mesma maneira ( ), portanto, a chamada completa foi refactorada para e fez uma substituição opcional em vez `AssignControllerMappings(DefaultInteractions);` `BaseController` de necessária.

**Propriedades do Olhar**

A `UseEyeTracking` propriedade da implementação de foi `GazeProvider` `IMixedRealityEyeGazeProvider` renomeada para `IsEyeTrackingEnabled` .

Se você fez isso anteriormente...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

Faça isso agora...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**Propriedades do WindowsApiChecker**

As propriedades do WindowsApiChecker a seguir foram marcadas como obsoletas. Use `IsMethodAvailable` ou `IsPropertyAvailable` `IsTypeAvailable` .

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

Não há planos para adicionar propriedades ao WindowsApiChecker para versões futuras de contrato de API.

**GltfMeshPrimitiveAttributes somente leitura**

Os atributos primitivos da malha gltf costumavam ser settable, agora são somente leitura. Seus valores serão definidos uma vez quando desterlizados.

### <a name="custom-button-icon-migration"></a>Migração de ícone de botão personalizado

Anteriormente, os ícones de botão personalizados exigiam a atribuição de um novo material ao renderador quad do botão. Isso não é mais necessário e é recomendável mover texturas de ícone personalizadas para um IconSet. Os ícones e materiais personalizados existentes são preservados. No entanto, eles serão menos ideais até que sejam atualizados.
Para atualizar os ativos em todos os botões do projeto para o novo formato recomendado, use ButtonConfigHelperMigrationHandler.
(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality. Toolkit. Utilities.ButtonConfigHelperMigrationHandler)

![Diálogo da janela de atualização](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Se um ícone não for encontrado no ícone padrão definido durante a migração, um conjunto de ícones personalizado será criado em MixedRealityToolkit.Generated/CustomIconSets. Uma caixa de diálogo indicará que isso ocorreu.

![Notificação de ícone personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>Atualizando 2.2.0 para 2.3.0

- [Alterações de API](#api-changes-in-230)

### <a name="api-changes-in-230"></a>Alterações de API na 2.3.0

**ControllerPoseSynchronizer**

O campo ControllerPoseSynchronizer.handedness privado foi marcado como obsoleto. Isso deve ter impacto mínimo nos aplicativos, pois o campo não é visível fora de sua classe.

O setter da propriedade ControllerPoseSynchronizer.Handedness público foi removido ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**MSBuild para Unity**

Esta versão do MRTK usa uma versão mais recente do MSBuild para Unity do que as versões anteriores. Durante o carregamento do projeto, se a versão mais antiga estiver listada no manifesto do Package Manger do Unity, a caixa de diálogo de configuração será exibida, com a opção Habilitar MSBuild para Unity marcada. A aplicação executará uma atualização.

**ScriptingUtilities**

A classe ScriptingUtilities foi marcada como obsoleta e foi substituída por ScriptUtilities, no Microsoft.MixedReality. Toolkit. Assembly Editor.Utilities. A nova classe refina o comportamento anterior e adiciona suporte para remover definições de script.

Embora o código existente continue a funcionar na versão 2.3.0, é recomendável atualizar para a nova classe.

**ShellHandRayPointer**

Os membros lineRendererSelected e lineRendererNoTarget da classe ShellHandRayPointer foram substituídos por lineMaterialSelected e lineMaterialNoTarget, respectivamente ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).

Substitua lineRendererSelected por lineMaterialSelected e/ou lineRendererNoTarget por lineMaterialNoTarget para resolver erros de compilação.

**Inicialização do observador espacialBehavior**

Observadores espaciais construídos com base na classe agora adem `BaseSpatialObserver` o valor de StartupBehavior quando reabilitar ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).

Nenhuma alteração é necessária para aproveitar essa correção.

**Pré-requisitos de controle de UX atualizados para usar PressableButton**

Os pré-requisitos a seguir agora estão usando o componente PressableButton em vez de TouchHandler para interação próxima ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))

- AnimationButton
- Botão
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- CheckBox
- RadialSet
- ToggleButton
- ToggleSwitch
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

O código do aplicativo pode exigir atualização devido a essa alteração.

**Namespace WindowsMixedRealityUtilities**

O namespace de WindowsMixedRealityUtilities foi alterado de Microsoft.MixedReality. Toolkit. WindowsMixedReality.Input para Microsoft.MixedReality. Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).

Atualize #using instruções para resolver erros de compilação.

## <a name="updating-210-to-220"></a>Atualizando 2.1.0 para 2.2.0

- [Alterações de API](#api-changes-in-220)

### <a name="api-changes-in-220"></a>Alterações de API na 2.2.0

**IMixedRealityBoundarySystem.Contains**

Esse método anteriormente tinha uma enum experimental específica definida pelo Unity. Agora, ele recebe uma enum definida pelo MRTK que é idêntica à enum do Unity. Essa alteração ajuda a preparar o MRTK para as APIs de limite futuras do Unity.

**MixedRealityServiceProfileAttribute**

Para descrever melhor os requisitos para dar suporte a um perfil, o MixedRealityServiceProfileAttribute foi atualizado para adicionar uma coleção opcional de tipos excluídos. Como parte dessa alteração, a propriedade ServiceType foi alterada de Type para Type[] e renomeada para RequiredTypes.

Uma segunda propriedade, ExcludedTypes, também foi adicionada.

## <a name="updating-200-to-210"></a>Atualizando 2.0.0 para 2.1.0

- [Alterações de API](#api-changes-in-210)
- [Alterações de perfil](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>Alterações de API na 2.1.0

**BaseNearInteractionTouchable**

O `BaseNearInteractionTouchable` foi modificado para marcar o método como `OnValidate` virtual. As classes que se `BaseNearInteractionTouchable` estendem (por ex: `NearInteractionTouchableUnityUI` ) foram atualizadas para refletir essa alteração.

**ColliderNearInteractionTouchable**

A classe `ColliderNearInteractionTouchable` foi substituída. Atualize as referências de código para usar `BaseNearInteractionTouchable` .

**IMixedRealityMouseDeviceManager**

**_Adicionado_**

`IMixedRealityMouseDeviceManager` foram adicionadas `CursorSpeed` propriedades `WheelSpeed` e . Essas propriedades permitem que os aplicativos especifiquem um valor multiplicador pelo qual a velocidade do cursor e da roda, respectivamente, será dimensionada.

Essa é uma alteração da última vez e requer que as implementações existentes do gerenciador de dispositivo do mouse sejam modificadas.

>[!NOTE]
>Essa alteração não é compatível com versões anteriores com a versão 2.0.0.

**_Preterido_**

A `MouseInputProfile` propriedade foi marcada como obsoleta e será removida de uma versão futura do Microsoft Mixed Reality Toolkit. É recomendável que o código do aplicativo não use mais essa propriedade.

**Interativo**

Os métodos e propriedades a seguir foram preterido e serão removidos de uma versão futura do Microsoft Mixed Reality Toolkit. A recomendação é atualizar o código do aplicativo de acordo com as diretrizes contidas no atributo Obsoleto e exibidas no console.

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

**NearInteractionTouchableSurface**

A `NearInteractionTouchableSurface` classe foi adicionada e agora serve como a classe base para e `NearInteractionTouchable` `NearInteractionTouchableUnityUI` .

### <a name="profile-changes-in-210"></a>Alterações de perfil na 2.1.0

**Perfil de acompanhamento de mão**

A malha manual e as visualizações conjuntas agora têm configurações separadas do editor e do player. O perfil de acompanhamento de mão foi atualizado para permitir a configuração dessas visualizações como; Nothing, Everything, Editor ou Player.

![Modos de visualização de mão](../release-notes/images/HandTrackingVisualizationModes.png)

Os perfis de acompanhamento de mão personalizados podem precisar ser atualizados para funcionar corretamente com a versão 2.1.0.

>[!NOTE]
>Essa alteração não é compatível com versões anteriores com a versão 2.0.0.

**Perfil de simulação de entrada**

O sistema de simulação de entrada foi atualizado, o que altera algumas configurações no perfil de simulação de entrada. Algumas alterações não podem ser migradas automaticamente e os usuários podem descobrir que os perfis estão usando valores padrão.

1. Todas as vinculações de botão keyCode e mouse no perfil foram substituídas por um struct genérico, que armazena o tipo de associação (chave ou mouse), bem como o código de associação real (KeyCode ou número do botão do `KeyBinding` mouse, respectivamente). O struct tem seu próprio inspetor, que permite a exibição unificada e oferece uma ferramenta de "associação automática" para definir rapidamente as vinculações de chave pressionando a respectiva chave em vez de selecionar em uma lista suspenso enorme.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` foi incluído anteriormente `MouseLookButton` na enum como `InputSimulationMouseButton.Focused` , agora é uma opção separada. Quando habilitada, a câmera continua girando com o mouse depois de soltar o botão, até que a tecla de escape seja pressionada.
1. `HandDepthMultiplier` O valor padrão foi baixado de 0,1 para 0,03 para acomodar algumas alterações na simulação de entrada. Se a câmera se mover muito rápido ao rolar, tente reduzir esse valor.
1. As chaves para girar as mãos foram removidas, a rotação da mão agora também é controlada pelo mouse. Manter `HandRotateButton` (Ctrl) junto com a tecla de manipulação esquerda/direita (LShift/Espaço) habilita a rotação da mão.
1. Um novo eixo "UpDown" foi introduzido na lista de eixos de entrada. Isso controla a movimentação da câmera na vertical e assume como padrão as chaves Q/E, bem como os botões de gatilho do controlador.

Para obter mais informações sobre essas alterações, consulte o artigo [serviço de simulação de](../features/input-simulation/input-simulation-service.md) entrada.

**Perfil do provedor de dados do mouse**

O perfil do provedor de dados do mouse foi atualizado para expor as novas `CursorSpeed` propriedades `WheelSpeed` e . Os perfis personalizados existentes terão valores padrão fornecidos automaticamente. Quando o perfil for salvo, esses novos valores serão persistentes.

**Perfil de mapeamento do controlador**

Alguns eixos e tipos de entrada foram atualizados na versão 2.1.0, especialmente em torno da plataforma OpenVR. Selecione **MixedRealityToolkit -> Utilities -> Atualizar -> de** Mapeamento do Controlador ao atualizar. Isso atualizará todos os Perfis de Mapeamento de Controlador personalizados com os eixos e dados atualizados, deixando suas ações de entrada atribuídas personalizadas intactas.

## <a name="updating-rc2-to-200"></a>Atualizando RC2 para 2.0.0

Entre as versões RC2 e 2.0.0 do Microsoft Mixed Reality Toolkit, foram feitas alterações que podem afetar os projetos existentes. Este documento descreve essas alterações e como atualizar projetos para a versão 2.0.0.

- [Alterações de API](#api-changes-in-200)
- [Alterações de nome do assembly](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>Alterações de API na 2.0.0

Desde o lançamento do RC2, houve várias alterações na API, incluindo algumas que podem quebrar projetos existentes. As seções a seguir descrevem as alterações que ocorreram entre as versões RC2 e 2.0.0.

**MixedRealityToolkit**

As propriedades públicas a seguir no objeto MixedRealityToolkit foram preterida.

- `RegisteredMixedRealityServices` não contém mais a coleção de serviços de extensões registradas e provedores de dados.

Para acessar os serviços de extensão, use `MixedRealityServiceRegistry.TryGetService<T>` . Para acessar provedores de dados, caste a instância de serviço para [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) e use `GetDataProvider<T>` .

Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) ou, em vez disso, para as propriedades preteridas a seguir

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

A classe é a substituição para os acessadores do sistema [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) estático (por exemplo: BoundarySystem) encontrados no `MixedRealityToolkit` objeto .

>[!IMPORTANT]
>Os acessadores do sistema foram preterido na versão 2.0.0 e serão removidos em uma versão `MixedRealityToolkit` futura do MRTK.

O exemplo de código a seguir ilustra o padrão antigo e o novo.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

O uso da nova classe CoreSystem garantirá que o código do aplicativo não precisará ser atualizado se você alterar o aplicativo para usar um registrador de serviços diferente (por ex. um dos gerenciadores de serviços experimentais).

**IMixedRealityRaycastProvider**

Com a adição do IMixedRealityRaycastProvider, o perfil de configuração do sistema de entrada foi alterado. Se você tiver um perfil personalizado, poderá receber os erros na imagem a seguir ao executar seu aplicativo.

![Selecionando o provedor Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

Para corrigi-los, adicione uma instância IMixedRealityRaycastProvider ao perfil do sistema de entrada.

![Selecionando o provedor Raycast 2](../release-notes/images/SelectRaycastProvider.png)

**Sistema de Eventos**

- Os `IMixedRealityEventSystem` métodos de API antigos e foram `Register` `Unregister` marcados como obsoletos. Eles são preservados para compatibilidade com compatibilidade com vertida.
- `InputSystemGlobalListener` foi marcado como obsoleto. Sua funcionalidade não foi alterada.
- `BaseInputHandler` a classe base foi alterada de `InputSystemGlobalListener` para `InputSystemGlobalHandlerListener` . Essa é uma alteração significativa para os descendentes de `BaseInputHandler` .

**_Motivação por trás da alteração_**

A antiga API do sistema de eventos `Register` e `Unregister` poderia causar vários problemas em tempo de execução, a principal é:

- Se um componente for registrado para eventos globais, ele receberá eventos de entrada globais de *todos os* tipos.
- Se um dos componentes em um objeto for registrado para eventos de entrada globais, todos os componentes nesse objeto receberão eventos de entrada globais de *todos os* tipos.
- Se dois componentes no mesmo objeto forem registrados em eventos globais e um for desabilitado em tempo de execução, o segundo interromperá o recebimento de eventos globais.

Nova API `RegisterHandler` e `UnregisterHandler` :

- Fornece um controle explícito e granular sobre o qual os eventos de entrada devem ser ouvidos globalmente e que devem ser baseados em foco.
- Permite que vários componentes no mesmo objeto escutem eventos globais independentemente um do outro.

**_Como migrar_**

- Se você estiver chamando a `Register` / `Unregister` API diretamente antes, substitua essas chamadas por chamadas para `RegisterHandler` / `UnregisterHandler` . Use interfaces de manipulador que você implementar como parâmetros genéricos. Se você implementar várias interfaces e várias delas ouvirem os eventos de entrada globais, chame `RegisterHandler` várias vezes.
- Se você estiver herdando de `InputSystemGlobalListener` , altere a herança para `InputSystemGlobalHandlerListener` . Implementar `RegisterHandlers` e `UnregisterHandlers` abstrair métodos. Na chamada de implementação `inputSystem.RegisterHandler` ( `inputSystem.UnregisterHandler` ) para registrar em todas as interfaces de manipulador para as quais você deseja escutar eventos globais.
- Se você estiver herdando de `BaseInputHandler` `RegisterHandlers` métodos Implement e `UnregisterHandlers` Abstract (o mesmo que for `InputSystemGlobalListener` ).

**_Exemplos de migração_**

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

**Conscientização espacial**

As interfaces IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver fizeram várias alterações significativas, conforme descrito abaixo.

**_Alterações_**

Os seguintes métodos foram renomeados para descrever melhor seu uso.

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` foi renomeado para `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` para esclarecer seu uso.

**_Adições_**

Com base nos comentários dos clientes, o suporte à remoção fácil de dados de reconhecimento espacial observados anteriormente foi adicionado.

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**Solucionadores**

Alguns componentes do Solver e a classe SolverHandler Manager foram alterados para corrigir vários bugs e para um uso mais intuitivo.

**_SolverHandler_**

- A classe não se estende mais de `ControllerFinder`
- `TrackedObjectToReference` Propriedade pública preterida e renomeada como `TrackedTargetType`
- `TrackedObjectType` substitui os valores da & do controlador à esquerda. Em vez disso, use `MotionController` `HandJoint` valores ou e atualize `TrackedHandedness` a nova propriedade para limitar o controle para o controlador esquerdo ou direito

**_Entre_**

- `TrackedObjectForSecondTransform` Propriedade pública preterida e renomeada como `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` foi removido. Para atualizar o resolvedor, modifique as propriedades públicas (ou seja, `SecondTrackedObjectType`)

**_SurfaceMagnetism_**

- `MaxDistance` Propriedade pública preterida e renomeada como `MaxRaycastDistance`
- `CloseDistance` Propriedade pública preterida e renomeada como `ClosestDistance`
- O valor padrão de `RaycastDirectionMode` é agora `TrackedTargetForward` qual raycasts na direção da transformação de destino rastreada em frente
- `OrientationMode` os valores de enumeração `Vertical` e `Full` , foram renomeados para `TrackedTarget` e `SurfaceNormal` respectivamente
- `KeepOrientationVertical` a propriedade pública foi adicionada para controlar se a orientação do gameobject associado permanece vertical

**Botões**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) Agora tem `DistanceSpaceMode` a propriedade definida `Local` como padrão. Isso permite que os botões sejam dimensionados enquanto ainda podem ser prensados

**Esfera de recorte**

A interface ClippingSphere foi alterada para espelhar as APIs encontradas em ClippingBox e ClippingPlane.

A propriedade RADIUS do ClippingSphere agora é implicitamente calculada com base na escala de transformação. Antes que os desenvolvedores precisem especificar o raio do ClippingSphere no Inspetor. Se você quiser alterar o raio, basta atualizar a escala de transformação da transformação como faria normalmente.

**NearInteractionTouchable e PokePointer**

- NearInteractionTouchable não lida com o toque da tela da interface do usuário do Unity mais. A classe NearInteractionTouchableUnityUI deve ser usada para a interface do usuário do Unity touchables agora.
- ColliderNearInteractionTouchable é a nova classe base para touchables com base em colisors, ou seja, cada tocável, exceto NearInteractionTouchableUnityUI.
- BaseNearInteractionTouchable. DistFront foi movido e renomeado para PokePointer. TouchableDistance essa é a distância e a qual o PokePointer pode interagir com touchables. Anteriormente, cada tocável tinha sua própria distância máxima de interação, mas agora isso é definido no PokePointer, o que permite uma melhor otimização.
- BaseNearInteractionTouchable. DistBack foi renomeado para PokeThreshold isso torna claro que PokeThreshold é o equivalente a DebounceThreshold. Um toque é ativado quando o PokeThreshold é cruzado e liberado quando DebounceThreshold é cruzado.

**ReadOnlyAttribute**

O `Microsoft.MixedReality.Toolkit` namespace foi adicionado a `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` , e `EndReadOnlyGroupAttribute` .

**PointerClickHandler**

A classe `PointerClickHandler` foi substituída. O `PointerHandler` deve ser usado em vez disso, ele fornece a mesma funcionalidade.

**suporte ao clique HoloLens**

os mapeamentos do controlador do HoloLens do clique foram alterados para serem desnecessários [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) . Para considerar isso, um atualizador automático será executado na primeira vez que você abrir o perfil do ControllerMapping. Abra qualquer perfil personalizado pelo menos uma vez após a atualização para o 2.0.0 para disparar essa etapa de migração única.

**InteractableHighlight**

A classe `InteractableHighlight` foi substituída. A `InteractableOnFocus` classe e o `FocusInteractableStates` ativo devem ser usados em seu lugar. para criar um novo `Theme` ativo para o `InteractableOnFocus` , clique com o botão direito do mouse na janela do projeto e selecione *criar*  >  *realidade misturada Toolkit*  >    >  *tema* interagir.

**HandInteractionPanZoom**

`HandInteractionPanZoom` foi movido para o namespace da interface do usuário porque não era um componente de entrada. `HandPanEventData` também foi movido para esse namespace e simplificado para corresponder a outros dados de eventos de interface do usuário.

### <a name="assembly-name-changes-in-200"></a>Alterações de nome de assembly em 2.0.0

na versão 2.0.0, toda a realidade misturada oficial Toolkit nomes de assembly e seus arquivos de definição de assembly (. asmdef) associados foram atualizados para se ajustarem ao padrão a seguir.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

Em alguns casos, vários assemblies foram mesclados para criar um Unity melhor de seu conteúdo. Se o seu projeto usa arquivos. asmdef personalizados, eles podem exigir atualização.

As tabelas a seguir descrevem como os nomes de arquivo RC2. asmdef são mapeados para a versão 2.0.0. Todos os nomes de assembly correspondem ao nome do arquivo. asmdef.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | Microsoft. MixedReality. Toolkit. asmdef |
| MixedRealityToolkit. Core. BuildAndDeploy. asmdef | Microsoft. MixedReality. Toolkit. Editor. BuildAndDeploy. asmdef |
| MixedRealityToolkit. Core. Definitions. Utilities. editor. asmdef | Removido, use Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef |
| MixedRealityToolkit. Core. Extensions. EditorClassExtensions. asmdef | Microsoft. MixedReality. Toolkit. Editor. ClassExtensions. asmdef
| MixedRealityToolkit. Core. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. Editor. Inspectors. asmdef |
| MixedRealityToolkit. Core. Inspectors. testinspectors. asmdef | Microsoft. MixedReality. Toolkit. Editor. userinspectors. asmdef |
| MixedRealityToolkit. Core. UtilitiesAsync. asmdef | Microsoft. MixedReality. Toolkit. Async. asmdef |
| MixedRealityToolkit. Core. Utilities. editor. asmdef | Microsoft.MixedReality. Toolkit. Editor.Utilities.asmdef |
| MixedRealityToolkit.Utilities.Gltf.asmdef | Microsoft.MixedReality. Toolkit. Gltf.asmdef |
| MixedRealityToolkit.Utilities.Gltf.Importers.asmdef | Microsoft.MixedReality. Toolkit. Gltf.Importers.asmdef |

**MixedRealityToolkit.Providers**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Providers.OpenVR.asmdef | Microsoft.MixedReality. Toolkit. Providers.OpenVR.asmdef |
| MixedRealityToolkit.Providers.WindowsMixedReality.asmdef | Microsoft.MixedReality. Toolkit. Providers.WindowsMixedReality.asmdef |
| MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef | Microsoft.MixedReality. Toolkit. Providers.WindowsVoiceInput.asmdef |

**MixedRealityToolkit.Services**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Services.BoundarySystem.asmdef | Microsoft.MixedReality. Toolkit. Services.BoundarySystem.asmdef |
| MixedRealityToolkit.Services.CameraSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.CameraSystem.asmdef |
| MixedRealityToolkit.Services.DiagnosticsSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.DiagnosticsSystem.asmdef |
| MixedRealityToolkit.Services.InputSimulation.asmdef | Microsoft.MixedReality. Toolkit. Services.InputSimulation.asmdef |
| MixedRealityToolkit.Services.InputSimulation.Editor.asmdef | Microsoft.MixedReality. Toolkit. Services.InputSimulation.Editor.asmdef |
| MixedRealityToolkit.Services.InputSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.InputSystem.asmdef |
| MixedRealityToolkit.Services.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Services.InputSystem.Editor.asmdef |
| MixedRealityToolkit.Services.SceneSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.SceneSystem.asmdef |
| MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.SpatialAwarenessSystem.asmdef |
| MixedRealityToolkit.Services.System.asmdef | Microsoft.MixedReality. Toolkit. Services.LtdSystem.asmdef |

**MixedRealityToolkit.SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.SDK.asmdef | Microsoft.MixedReality. Toolkit. SDK.asmdef |
| MixedRealityToolkit.SDK.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Sdk. Inspectors.asmdef |

**MixedRealityToolkit.Examples**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Examples.asmdef | Microsoft.MixedReality. Toolkit. Examples.asmdef |
| MixedRealityToolkit.Examples.Demos.Gltf.asmdef | Microsoft.MixedReality. Toolkit. Demos.Gltf.asmdef |
| MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Demos.StandardShader.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef | Microsoft.MixedReality. Toolkit. Demos.InspectorFields.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Demos.InspectorFields.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef | Microsoft.MixedReality. Toolkit. Demos.UX.Interactables.asmdef |
