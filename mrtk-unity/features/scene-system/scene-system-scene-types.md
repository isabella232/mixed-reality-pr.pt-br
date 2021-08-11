---
title: Tipos de cena do sistema de cena
description: Documentação sobre diferentes tipos de cena no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: be34110c693c749535f6bfcd0411ecbd0bafc3bb48ab2392b3635c2e86a4dfb1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203300"
---
# <a name="scene-types"></a>Tipos de cena

As cenas foram divididas em três tipos e cada tipo tem uma função diferente.

![Sistema de cena na hierarquia](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>Cenas de conteúdo

Essas são as cenas com as que você está acostumado a lidar. Qualquer tipo de conteúdo pode ser armazenado neles e pode ser carregado ou descarregado em qualquer combinação.

As cenas de conteúdo são habilitadas por padrão. Todas as cenas incluídas na matriz do `Content Scenes` seu perfil podem ser carregadas/descarregadas pelo serviço.

___

## <a name="manager-scenes"></a>Cenas do gerente

Uma única cena com uma instância mixedRealityToolkit necessária. Essa cena será carregada primeiro no lançamento e permanecerá carregada durante o tempo de vida do aplicativo. A cena do gerente também pode hospedar outros objetos que nunca devem ser destruídos. Essa é a alternativa preferencial para DontDestroyOnLoad.

Para habilitar esse recurso, verifique `Use Manager Scene` seu perfil e arraste um objeto de cena para o campo `Manager Scene` .

___

## <a name="lighting-scenes"></a>Cenas de iluminação

Um conjunto de cenas que armazenam informações de iluminação e objetos de iluminação. Somente uma pode ser carregada por vez e suas configurações podem ser mescladas durante as cargas para transições de iluminação suave.

As configurações de iluminação do Unity – luz ambiente, skyboxes etc. – podem ser complicadas de gerenciar ao usar o carregamento aditivo porque estão vinculadas a cenas individuais e o comportamento de substituição não é simples. Na prática, isso pode causar confusão quando os ativos são autores em condições de iluminação que não são obtidas em runtime.

![Configurações de iluminação do sistema de cena](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

O Sistema de Cena usa cenas de iluminação para garantir que essas configurações permaneçam consistentes, independentemente de quais cenas estão carregadas ou ativas, tanto no modo de edição quanto no modo de reprodução.

Para habilitar esse recurso, `Use Lighting Scene` verifique seu perfil e preencha a `Lighting Scenes` matriz.

### <a name="cached-lighting-settings"></a>Configurações de iluminação armazenadas em cache

Seu perfil armazena cópias armazenadas em cache das configurações de iluminação mantidas em suas cenas de iluminação. Se essas configurações mudarem em suas cenas de iluminação, você precisará atualizar o cache para garantir que a iluminação apareça conforme o esperado no modo de reprodução. Seu perfil exibirá um aviso quando ele suspeita que suas configurações armazenadas em cache estão desa datadas. Clicar `Update Cached Lighting Settings` carregará cada uma das cenas de iluminação, extrairá suas configurações e as armazenará em seu perfil.

![Configurações de iluminação armazenadas em cache do sistema de cena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Comportamento do editor

Um benefício do uso de cenas de iluminação é saber que seu conteúdo é acessado corretamente durante a edição. Para esse fim, o Serviço de Cena manterá uma cena de iluminação carregada o tempo todo e copiará as configurações de iluminação dessa cena para a cena ativa atual.\*

Você pode alterar qual cena de iluminação é carregada abrindo o inspetor de serviço do Sistema [de Cena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) No modo de edição, você pode fazer a transição instantânea entre cenas de iluminação. No modo de reprodução, você pode visualizar transições.

![Inspetor do sistema de cena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Observação: normalmente, a cena ativa determina suas configurações de iluminação no editor. No entanto, optemos por não usar esse recurso para impor configurações de iluminação, pois a cena ativa também é onde objetos recém-criados são colocados por padrão e as cenas de iluminação só têm permissão para conter componentes de iluminação. Em vez disso, as configurações da cena de iluminação atual são copiadas automaticamente para as configurações da cena ativa. Lembre-se de que isso fará com que as configurações de iluminação da cena de conteúdo se sobressumente escritas.*
