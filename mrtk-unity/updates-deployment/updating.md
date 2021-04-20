---
title: Atualizar
description: Documentação para migrar de uma versão inferior do MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742232"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a>Atualizando o Microsoft Mixed Reality Toolkit

- [Atualizando para uma nova versão do MRTK](#upgrading-to-a-new-version-of-mrtk)
- [2.3.0 2.4.0](#updating-230-to-240)
- [2.2.0 2.3.0](#updating-220-to-230)
- [2.1.0 2.2.0](#updating-210-to-220)
- [2.0.0 2.1.0](#updating-200-to-210)
- [RC2 para 2.0.0](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>Localizando a versão atual 

Siga estas instruções para descobrir qual versão do MRTK você está usando no momento:

1. Abra seu projeto do MRTK no Unity
2. Navegue até a pasta "MixedRealityToolkit" na janela do projeto
3. Abra o arquivo chamado "Version"

Se o arquivo e a pasta acima não existirem, você estará em uma versão mais recente do MRTK. Nesse caso, tente o seguinte:

1. Navegue até a pasta "Mixed Reality Toolkit Foundation"
2. Clique em "package.jsem" para ver uma visualização no Unity ou abri-la com um editor de texto
3. Procure a linha com a palavra "Version:" 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>Atualizando para uma nova versão do MRTK

*É altamente recomendável executar a [ferramenta de migração](../features/tools/migration-window.md) depois de obter a atualização do MRTK* para corrigir automaticamente e atualizar de componentes preteridos e ajustar para alterações significativas. A ferramenta de migração faz parte do pacote de **ferramentas** .

As instruções a seguir descrevem o caminho de atualização do 2.4.0 para 2.5.0. Se seu projeto estiver no 2.3.0 ou anterior, leia sobre as alterações [entre as versões](#updating-230-to-240) para entender o caminho de atualização ou leia as [instruções da versão](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) anterior para fazer uma atualização de versão por versão.

### <a name="mixed-reality-feature-tool"></a>Ferramenta Recurso de Realidade Misturada
A maneira mais fácil de atualizar o MRTK para uma versão mais recente do MRTK é usando a [ferramenta de recursos de realidade misturada](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) para baixar os pacotes mais recentes e carregá-los diretamente em seu projeto do Unity.

Se o projeto usava anteriormente arquivos de ativo de Unity (. unitypackage), consulte [estas instruções](#switching-from-unity-asset-files-to-mixed-reality-feature-tool). 

### <a name="unity-asset-unitypackage-files"></a>Arquivos de ativo de Unity (. unitypackage)

Outro caminho de atualização é baixar manualmente os pacotes do MRTK Unity e aplicá-los ao seu projeto. Consulte as etapas abaixo,

1. Salve uma cópia do seu projeto atual, caso você tenha atingido quaisquer empecilhos em qualquer ponto nas etapas de atualização.
1. Fechar o Unity
1. Dentro da pasta *ativos* , exclua as seguintes pastas **MRTK** , juntamente com seus arquivos. meta (o projeto pode não ter todas as pastas listadas)
    - MRTK/núcleo
    - MRTK/exemplos
    - MRTK/extensões
    - MRTK/provedores
    - MRTK/SDK
    - MRTK/serviços
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Se foram feitas modificações nos sombreadores MRTK, crie um backup local antes de excluir a pasta MRTK/StandardAssets
    - MRTK/ferramentas
    > [!IMPORTANT]
    > Não exclua a pasta **MixedRealityToolkit. Generated** ou seu arquivo. meta.
1. Excluir a pasta de **biblioteca**
    > [!IMPORTANT]
    > Algumas ferramentas do Unity, como o Unity collab, salvam informações de configuração na pasta de biblioteca. Se estiver usando uma ferramenta que faz isso, primeiro copie a pasta de dados da ferramenta da biblioteca antes de excluí-la e, em seguida, restaure-a após a regeneração da biblioteca.
1. Abra novamente o projeto no Unity
1. Importar os novos pacotes do Unity
    - Foundation – _importar primeiro este pacote_
    - Ferramentas
    - Adicional WMZ
    > [!NOTE]
    > Se extensões adicionais tiverem sido instaladas, talvez elas precisem ser importadas novamente.
    - Adicional Disso
1. Feche o Unity e exclua a pasta de **biblioteca** (leia a observação abaixo primeiro!). Esta etapa é necessária para forçar o Unity a atualizar seu banco de dados de ativos e reconciliar perfis personalizados existentes.
1. Inicie o Unity e, para cada cena no projeto
    - Exclua **MixedRealityToolkit** e **MixedRealityPlayspace**, se presente, da hierarquia. Isso excluirá a câmera principal, mas ela será recriada na próxima etapa. Se qualquer propriedade da câmera principal tiver sido alterada manualmente, elas precisarão ser reaplicadas manualmente depois que a nova câmera for criada.
    - Selecione **MixedRealityToolkit-> adicionar à cena e configurar**
    - Selecione **utilitários de >-> atualização-> perfis de mapeamento do controlador** (só precisa ser feito uma vez)-isso atualizará todos os perfis de mapeamento do controlador personalizado com os dados e eixos atualizados, deixando as ações de entrada atribuídas personalizadas intactas
1. Execute a [ferramenta de migração](../features/tools/migration-window.md) e execute a ferramenta no *projeto completo* para garantir que todo o seu código seja atualizado para a versão mais recente.
   A janela de migração contém vários manipuladores de migração diferentes, que devem ser executados por conta própria. Esta etapa envolve:
   - Selecione o primeiro manipulador de migração na lista suspensa **seleção do manipulador de migração** .
   - Clique no botão "projeto completo".
   - Clique no botão "Adicionar projeto completo para migração" (isso examinará todo o projeto para que os objetos sejam migrados).
   - Clique no botão "migrar", que deverá ser habilitado se qualquer objeto migrável for encontrado.
   - Repita as três etapas anteriores para cada um dos manipuladores de migração no menu suspenso.
     (Consulte [esse problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) que aborda o trabalho que pode ser feito para simplificar esse processo de migração em uma versão futura)

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>Alternando de arquivos de ativos de Unity para a ferramenta de recursos misturados de realidade

A alternância de arquivos de ativos de Unity para a realidade mistura de recursos da ferramenta traz vários benefícios:

- Atualização mais fácil
- Tempos de compilação mais rápidos
- Menos projetos na solução do Visual Studio

Mudar para o uso da ferramenta de funcionalidade Mixed Reality requer um conjunto único de etapas manuais.

1. Salve uma cópia do seu projeto atual.
1. Fechar o Unity
1. Dentro da pasta *ativos* , exclua as seguintes pastas **MRTK** , juntamente com seus arquivos. meta (o projeto pode não ter todas as pastas listadas)
    - MRTK/núcleo
    - MRTK/exemplos
    - MRTK/extensões
    - MRTK/provedores
    - MRTK/SDK
    - MRTK/serviços
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Se foram feitas modificações nos sombreadores MRTK, crie um backup local antes de excluir a pasta MRTK/StandardAssets
    - MRTK/ferramentas
    > [!IMPORTANT]
    > Não exclua a pasta **MixedRealityToolkit. Generated** ou seu arquivo. meta.
1. Excluir a pasta de **biblioteca**
    > [!IMPORTANT]
    > Algumas ferramentas do Unity, como o Unity collab, salvam informações de configuração na pasta de biblioteca. Se estiver usando uma ferramenta que faz isso, primeiro copie a pasta de dados da ferramenta da biblioteca antes de excluí-la e, em seguida, restaure-a após a regeneração da biblioteca.
1. Abra novamente o projeto no Unity

Depois que as etapas anteriores forem executadas, execute a [ferramenta de funcionalidade Mixed Reality](#mixed-reality-feature-tool) e importe a versão desejada do kit de ferramentas da realidade misturada.

## <a name="updating-230-to-240"></a>Atualizando 2.3.0 para 2.4.0

[Renomeações](#folder-renames-in-240) 
 de pasta [Alterações de API](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>Renomeações de pasta no 2.4.0

As pastas MixedRealityToolkit foram renomeadas e movidas para uma hierarquia comum na versão 2,4. Se um aplicativo usar caminhos embutidos em código para MRTK recursos, eles precisarão ser atualizados de acordo com a tabela a seguir.

| Pasta anterior | Nova Pasta |
| --- | --- |
| MixedRealityToolkit | MRTK/núcleo |
| MixedRealityToolkit. exemplos | MRTK/exemplos |
| MixedRealityToolkit. Extensions | MRTK/extensões |
| MixedRealityToolkit. Providers | MRTK/provedores |
| MixedRealityToolkit. SDK | MRTK/SDK |
| MixedRealityToolkit. Services | MRTK/serviços |
| MixedRealityToolkit. Tests | MRTK/testes |
| MixedRealityToolkit. Tools | MRTK/ferramentas |

> [!IMPORTANT]
> O `MixedRealityToolkit.Generated` contém arquivos gerados pelo cliente e permanece inalterado.

### <a name="eye-gaze-setup-in-240"></a>Olhare a configuração de olho no 2.4.0

Esta versão do MRTK modifica as etapas necessárias para a instalação de olho do olhar. A caixa de seleção _' IsEyeTrackingEnabled '_ pode ser encontrada nas configurações de olhar do perfil de ponteiro de entrada. Marcar essa caixa permitirá olhar com base nos olhos, em vez de olhar padrão com base em cabeçalho.

Para obter mais informações sobre essas alterações e instruções completas para a configuração de acompanhamento de olho, consulte o artigo [acompanhamento de olho](../features/input/eye-tracking/eye-tracking-basic-setup.md) .

### <a name="eye-gaze-pointer-behavior-in-240"></a>Comportamento do ponteiro olhar ocular no 2.4.0

O comportamento de ponteiro padrão olhar de olho foi modificado para corresponder ao comportamento de ponteiro padrão olhar de cabeçalho. Um ponteiro olhar ocular será suprimido automaticamente quando uma mão for detectada. O ponteiro olhar ocular ficará visível novamente depois de dizer "Select".

Os detalhes sobre as configurações de olhar e mão podem ser encontrados no artigo [olhos e mãos](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) .

### <a name="api-changes-in-240"></a>Alterações de API em 2.4.0

**Classes de controlador personalizadas**

As classes de controlador personalizadas tinham que ser definidas anteriormente `SetupDefaultInteractions(Handedness)` . Esse método tornou-se obsoleto em 2,4, pois o parâmetro de destro-canhoto era redundante com a classe de controlador ' própria destromente. O novo método não tem parâmetros. Além disso, muitas classes de controlador definidas da mesma forma ( `AssignControllerMappings(DefaultInteractions);` ), portanto, a chamada completa foi Refatorada para baixo `BaseController` e fez uma substituição opcional em vez de obrigatória.

**Propriedades de olhar de olho**

A `UseEyeTracking` propriedade da `GazeProvider` implementação de `IMixedRealityEyeGazeProvider` foi renomeada para `IsEyeTrackingEnabled` .

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

**Propriedades de WindowsApiChecker**

As propriedades WindowsApiChecker a seguir foram marcadas como obsoletas. Use `IsMethodAvailable` , `IsPropertyAvailable` ou `IsTypeAvailable` .

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

Não há planos para adicionar propriedades a WindowsApiChecker para versões futuras de contrato de API.

**GltfMeshPrimitiveAttributes somente leitura**

Os atributos primitivos de malha gltf usados para ser configurável, agora são somente leitura. Seus valores serão definidos uma vez quando desserializados.

### <a name="custom-button-icon-migration"></a>Migração de ícone de botão personalizado

Os ícones de botão personalizados anteriormente exigiam a atribuição de um novo material ao processador quádruplo do botão. Isso não é mais necessário e é recomendável mover as texturas do ícone personalizado para um ícone do. Os materiais e os ícones personalizados existentes são preservados. No entanto, elas serão menos ideais até que sejam atualizadas.
Para atualizar os ativos em todos os botões do projeto para o novo formato recomendado, use o ButtonConfigHelperMigrationHandler.
(O kit de ferramentas da realidade mista – utilitários de >-> janela de migração-> seleção do manipulador de migração-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)

![Caixa de diálogo atualizar janela](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Se um ícone não for encontrado no conjunto de ícones padrão durante a migração, um conjunto de ícones personalizado será criado em MixedRealityToolkit. Generated/CustomIconSets. Uma caixa de diálogo indicará que isso foi realizado.

![Notificação de ícone personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>Atualizando 2.2.0 para 2.3.0

- [Alterações de API](#api-changes-in-230)

### <a name="api-changes-in-230"></a>Alterações de API em 2.3.0

**ControllerPoseSynchronizer**

O campo particular ControllerPoseSynchronizer. destros foi marcado como obsoleto. Isso deve ter um impacto mínimo sobre os aplicativos, pois o campo não é visível fora de sua classe.

O setter da propriedade pública ControllerPoseSynchronizer. Destroy foi removido ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**MSBuild para Unity**

Esta versão do MRTK usa uma versão mais recente do MSBuild para o Unity do que as versões anteriores. Durante o carregamento do projeto, se a versão mais antiga estiver listada no manifesto do Gerenciador de pacotes do Unity, a caixa de diálogo de configuração será exibida com a opção Habilitar MSBuild para Unity marcada. A aplicação executará uma atualização.

**ScriptingUtilities**

A classe ScriptingUtilities foi marcada como obsoleta e foi substituída por ScriptUtilities, no assembly Microsoft. MixedReality. Toolkit. editor. Utilities. A nova classe refina o comportamento anterior e adiciona suporte para a remoção de definições de script.

Enquanto o código existente continuará a funcionar na versão 2.3.0, é recomendável atualizar para a nova classe.

**ShellHandRayPointer**

Os membros lineRendererSelected e lineRendererNoTarget da classe ShellHandRayPointer foram substituídos por lineMaterialSelected e lineMaterialNoTarget, respectivamente ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).

Substitua lineRendererSelected por lineMaterialSelected e/ou lineRendererNoTarget por lineMaterialNoTarget para resolver erros de compilação.

**Observador espacial Startupbehavior fazendo**

Os observadores espaciais criados na `BaseSpatialObserver` classe agora respeitam o valor de startupbehavior fazendo quando reabilitados ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).

Nenhuma alteração é necessária para aproveitar essa correção.

**Pré-fabricados de controle UX atualizado para usar o PressableButton**

Os pré-fabricados a seguir agora estão usando o componente PressableButton em vez de TouchHandler para interação próxima ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))

- AnimationButton
- Botão
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- CheckBox
- Radialset
- ToggleButton
- ToggleSwitch
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

O código do aplicativo pode exigir atualização devido a essa alteração.

**Namespace WindowsMixedRealityUtilities**

O namespace de WindowsMixedRealityUtilities mudou de Microsoft. MixedReality. Toolkit. WindowsMixedReality. Input para Microsoft. MixedReality. Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).

Atualize #using instruções para resolver erros de compilação.

## <a name="updating-210-to-220"></a>Atualizando 2.1.0 para 2.2.0

- [Alterações de API](#api-changes-in-220)

### <a name="api-changes-in-220"></a>Alterações de API em 2.2.0

**IMixedRealityBoundarySystem. Contains**

Esse método levou anteriormente em uma enumeração experimental específica definida pelo Unity. Agora, ele usa um enum definido pelo MRTK que é idêntico ao enum do Unity. Essa alteração ajuda a preparar o MRTK para as APIs de limite futuras do Unity.

**MixedRealityServiceProfileAttribute**

Para descrever melhor os requisitos de suporte a um perfil, o MixedRealityServiceProfileAttribute foi atualizado para adicionar uma coleção opcional de tipos excluídos. Como parte dessa alteração, a Propriedade ServiceType foi alterada de Type para Type [] e foi renomeada para RequiredTypes.

Uma segunda propriedade, ExcludedTypes também foi adicionada.

## <a name="updating-200-to-210"></a>Atualizando 2.0.0 para 2.1.0

- [Alterações de API](#api-changes-in-210)
- [Alterações de perfil](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>Alterações de API em 2.1.0

**BaseNearInteractionTouchable**

O `BaseNearInteractionTouchable` foi modificado para marcar o `OnValidate` método como virtual. As classes que estendem `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI` ) foram atualizadas para refletir essa alteração.

**ColliderNearInteractionTouchable**

A classe `ColliderNearInteractionTouchable` foi substituída. Atualize as referências de código a serem usadas `BaseNearInteractionTouchable` .

**IMixedRealityMouseDeviceManager**

**_Mais_**

`IMixedRealityMouseDeviceManager` foram adicionadas `CursorSpeed` e `WheelSpeed` Propriedades. Essas propriedades permitem que os aplicativos especifiquem um valor multiplicador pelo qual a velocidade do cursor e da roda, respectivamente, será dimensionada.

Essa é uma alteração significativa e requer que as implementações existentes do Gerenciador de dispositivos do mouse sejam modificadas.

>[!NOTE]
>Essa alteração não é compatível com versões anteriores com a versão 2.0.0.

**_Preterido_**

A `MouseInputProfile` propriedade foi marcada como obsoleta e será removida de uma versão futura do kit de ferramentas do Microsoft Mixed Reality. É recomendável que o código do aplicativo não use mais essa propriedade.

**Interativo**

Os métodos e as propriedades a seguir foram preteridos e serão removidos de uma versão futura do kit de ferramentas do Microsoft Mixed Reality. A recomendação é atualizar o código do aplicativo de acordo com as diretrizes contidas no atributo obsoleto e exibi-lo no console do.

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

A `NearInteractionTouchableSurface` classe foi adicionada e agora serve como a classe base para `NearInteractionTouchable` e `NearInteractionTouchableUnityUI` .

### <a name="profile-changes-in-210"></a>Alterações de perfil em 2.1.0

**Perfil de acompanhamento à mão**

A malha de mão e as visualizações conjuntas agora têm um editor separado e configurações de Player. O perfil de acompanhamento de mão foi atualizado para permitir a definição dessas visualizações como; Nada, tudo, editor ou Player.

![Modos de visualização de mão](../release-notes/images/HandTrackingVisualizationModes.png)

Os perfis de controle de mão personalizada talvez precisem ser atualizados para funcionar corretamente com a versão 2.1.0.

>[!NOTE]
>Essa alteração não é compatível com versões anteriores com a versão 2.0.0.

**Perfil de simulação de entrada**

O sistema de simulação de entrada foi atualizado, o que altera algumas configurações no perfil de simulação de entrada. Algumas alterações não podem ser migradas automaticamente e os usuários podem descobrir que os perfis estão usando valores padrão.

1. Todas as associações de botão do mouse e do código-chave no perfil foram substituídas por uma `KeyBinding` estrutura genérica, que armazena o tipo de associação (chave ou mouse), bem como o código de associação real (código de tecla ou número do botão do mouse, respectivamente). O struct tem seu próprio Inspetor, que permite a exibição unificada e oferece uma ferramenta de "ligação automática" para definir rapidamente as associações de chave pressionando a respectiva chave em vez de selecionar em uma grande lista suspensa.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` foi anteriormente incluído no `MouseLookButton` enum como `InputSimulationMouseButton.Focused` , agora é uma opção separada. Quando habilitado, a câmera continuará girando com o mouse depois de soltar o botão, até que a tecla escape seja pressionada.
1. `HandDepthMultiplier` o valor padrão foi reduzido de 0,1 para 0, 3 para acomodar algumas alterações na simulação de entrada. Se a câmera se mover muito rapidamente durante a rolagem, tente reduzir esse valor.
1. As chaves para as mãos de rotação foram removidas, a rotação de mãos agora é controlada pelo mouse também. Manter `HandRotateButton` (Ctrl) junto com a chave de manipulação esquerda/direita (LShift/Space) habilitará a rotação da mão.
1. Um novo eixo "upDown" foi introduzido na lista eixo de entrada. Isso controla a movimentação da câmera na vertical e usa como padrão as chaves p/E, bem como os botões de gatilho do controlador.

Para obter mais informações sobre essas alterações, consulte o artigo [serviço de simulação de entrada](../features/input-simulation/input-simulation-service.md) .

**Perfil do provedor de dados do mouse**

O perfil do provedor de dados do mouse foi atualizado para expor as novas `CursorSpeed` `WheelSpeed` Propriedades e. Os perfis personalizados existentes terão automaticamente os valores padrão fornecidos. Quando o perfil for salvo, esses novos valores serão persistidos.

**Perfil de mapeamento do controlador**

Alguns eixos e tipos de entrada foram atualizados no 2.1.0, especialmente em relação à plataforma OpenVR. Certifique-se de selecionar os **utilitários > MixedRealityToolkit-> atualização-> perfis de mapeamento do controlador** ao atualizar. Isso atualizará todos os perfis de mapeamento do controlador personalizado com os dados e eixos atualizados, deixando as ações de entrada atribuídas personalizadas intactas.

## <a name="updating-rc2-to-200"></a>Atualizando o RC2 para o 2.0.0

Entre as versões RC2 e 2.0.0 do kit de ferramentas de realidade misturada da Microsoft, foram feitas alterações que podem afetar os projetos existentes. Este documento descreve essas alterações e como atualizar projetos para a versão 2.0.0.

- [Alterações de API](#api-changes-in-200)
- [Alterações de nome de assembly](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>Alterações de API em 2.0.0

Desde o lançamento do RC2, houve várias alterações de API, incluindo algumas que podem interromper projetos existentes. As seções a seguir descrevem as alterações que ocorreram entre as versões RC2 e 2.0.0.

**MixedRealityToolkit**

As propriedades públicas a seguir no objeto MixedRealityToolkit foram preteridas.

- `RegisteredMixedRealityServices` Não contém mais a coleção de serviços de extensões registradas e provedores de dados.

Para acessar os serviços de extensão, use `MixedRealityServiceRegistry.TryGetService<T>` . Para acessar os provedores de dados, converta a instância de serviço [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) e use `GetDataProvider<T>` .

Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) ou [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) em vez das seguintes propriedades preteridas

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**Principaisservices**

A [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) classe é a substituição para os acessadores de sistema estáticos (ex: BoundarySystem) encontrados no `MixedRealityToolkit` objeto.

>[!IMPORTANT]
>Os `MixedRealityToolkit` acessadores do sistema foram preteridos na versão 2.0.0 e serão removidos em uma versão futura do MRTK.

O exemplo de código a seguir ilustra o padrão antigo e o novo.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

Usar a nova classe CoreSystem garantirá que o código do aplicativo não precisará ser atualizado se você alterar o aplicativo para usar um registrador de serviço diferente (por exemplo, um dos gerenciadores de serviços experimentais).

**IMixedRealityRaycastProvider**

Com a adição do IMixedRealityRaycastProvider, o perfil de configuração do sistema de entrada foi alterado. Se você tiver um perfil personalizado, poderá receber os erros na imagem a seguir ao executar o aplicativo.

![Selecionando o provedor Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

Para corrigi-los, adicione uma instância do IMixedRealityRaycastProvider ao seu perfil do sistema de entrada.

![Selecionando o provedor Raycast 2](../release-notes/images/SelectRaycastProvider.png)

**Sistema de eventos**

- Os `IMixedRealityEventSystem` métodos antigos da API `Register` e foram `Unregister` marcados como obsoletos. Eles são preservados para compatibilidade com versões anteriores.
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

**_For_**

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

**Suporte ao clicador de HoloLens**

Os mapeamentos do controlador do clico do HoloLens foram alterados de um não lado [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) a lado [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) . Para considerar isso, um atualizador automático será executado na primeira vez que você abrir o perfil do ControllerMapping. Abra qualquer perfil personalizado pelo menos uma vez após a atualização para o 2.0.0 para disparar essa etapa de migração única.

**InteractableHighlight**

A classe `InteractableHighlight` foi substituída. A `InteractableOnFocus` classe e o `FocusInteractableStates` ativo devem ser usados em seu lugar. Para criar um novo `Theme` ativo para o `InteractableOnFocus` , clique com o botão direito do mouse na janela do projeto e selecione *criar*  >  tema do *Kit de ferramentas de realidade mista*  >    >  .

**HandInteractionPanZoom**

`HandInteractionPanZoom` foi movido para o namespace da interface do usuário porque não era um componente de entrada. `HandPanEventData` também foi movido para esse namespace e simplificado para corresponder a outros dados de eventos de interface do usuário.

### <a name="assembly-name-changes-in-200"></a>Alterações de nome de assembly em 2.0.0

Na versão 2.0.0, todos os nomes de assembly oficiais do kit de ferramentas de realidade misto e seus arquivos de definição de assembly (. asmdef) associados foram atualizados para se ajustarem ao padrão a seguir.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

Em alguns casos, vários assemblies foram mesclados para criar um Unity melhor de seu conteúdo. Se o seu projeto usa arquivos. asmdef personalizados, eles podem exigir atualização.

As tabelas a seguir descrevem como os nomes de arquivo RC2. asmdef são mapeados para a versão 2.0.0. Todos os nomes de assembly correspondem ao nome do arquivo. asmdef.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | Microsoft. MixedReality. Toolkit. asmdef |
| MixedRealityToolkit. Core. BuildAndDeploy. asmdef | Microsoft. MixedReality. Toolkit. editor. BuildAndDeploy. asmdef |
| MixedRealityToolkit. Core. Definitions. Utilities. editor. asmdef | Removido, use Microsoft. MixedReality. Toolkit. editor. Utilities. asmdef |
| MixedRealityToolkit. Core. Extensions. EditorClassExtensions. asmdef | Microsoft. MixedReality. Toolkit. editor. ClassExtensions. asmdef
| MixedRealityToolkit. Core. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. editor. Inspectors. asmdef |
| MixedRealityToolkit. Core. Inspectors. testinspectors. asmdef | Microsoft. MixedReality. Toolkit. editor. userinspectors. asmdef |
| MixedRealityToolkit. Core. UtilitiesAsync. asmdef | Microsoft. MixedReality. Toolkit. Async. asmdef |
| MixedRealityToolkit. Core. Utilities. editor. asmdef | Microsoft. MixedReality. Toolkit. editor. Utilities. asmdef |
| MixedRealityToolkit. Utilities. Gltf. asmdef | Microsoft. MixedReality. Toolkit. Gltf. asmdef |
| MixedRealityToolkit. Utilities. Gltf. conporters. asmdef | Microsoft. MixedReality. Toolkit. Gltf. Importers. asmdef |

**MixedRealityToolkit. Providers**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. Providers. OpenVR. asmdef | Microsoft. MixedReality. Toolkit. Providers. OpenVR. asmdef |
| MixedRealityToolkit. Providers. WindowsMixedReality. asmdef | Microsoft. MixedReality. Toolkit. Providers. WindowsMixedReality. asmdef |
| MixedRealityToolkit. Providers. WindowsVoiceInput. asmdef | Microsoft. MixedReality. Toolkit. Providers. WindowsVoiceInput. asmdef |

**MixedRealityToolkit. Services**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. Services. BoundarySystem. asmdef | Microsoft. MixedReality. Toolkit. Services. BoundarySystem. asmdef |
| MixedRealityToolkit. Services. CameraSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. CameraSystem. asmdef |
| MixedRealityToolkit. Services. DiagnosticsSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. DiagnosticsSystem. asmdef |
| MixedRealityToolkit. Services. InputSimulation. asmdef | Microsoft. MixedReality. Toolkit. Services. InputSimulation. asmdef |
| MixedRealityToolkit. Services. InputSimulation. editor. asmdef | Microsoft. MixedReality. Toolkit. Services. InputSimulation. editor. asmdef |
| MixedRealityToolkit. Services. InputSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. InputSystem. asmdef |
| MixedRealityToolkit. Services. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. Services. InputSystem. editor. asmdef |
| MixedRealityToolkit. Services. SceneSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. SceneSystem. asmdef |
| MixedRealityToolkit. Services. SpatialAwarenessSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. SpatialAwarenessSystem. asmdef |
| MixedRealityToolkit. Services. TeleportSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. TeleportSystem. asmdef |

**MixedRealityToolkit. SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. SDK. asmdef | Microsoft. MixedReality. Toolkit. SDK. asmdef |
| MixedRealityToolkit. SDK. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. SDK. Inspectors. asmdef |

**MixedRealityToolkit. exemplos**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. examples. asmdef | Microsoft. MixedReality. Toolkit. examples. asmdef |
| MixedRealityToolkit. examples. demos. Gltf. asmdef | Microsoft. MixedReality. Toolkit. demos. Gltf. asmdef |
| MixedRealityToolkit. examples. demos. StandardShader. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. demos. StandardShader. Inspectors. asmdef |
| MixedRealityToolkit. examples. demos. Utilities. InspectorFields. asmdef | Microsoft. MixedReality. Toolkit. demos. InspectorFields. asmdef |
| MixedRealityToolkit. examples. demos. Utilities. InspectorFields. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. demos. InspectorFields. Inspectors. asmdef |
| MixedRealityToolkit. examples. demos. UX. Interactables. asmdef | Microsoft. MixedReality. Toolkit. demos. UX. Interactables. asmdef |