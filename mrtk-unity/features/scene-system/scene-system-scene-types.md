---
title: Tipos de cena do sistema de cena
description: Documentação sobre diferentes tipos de cena no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144578"
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

O sistema de cena usa cenas de iluminação para garantir que essas configurações permaneçam consistentes, independentemente de quais cenas são carregadas ou ativas, tanto no modo de edição quanto no modo de reprodução.

Para habilitar esse recurso, faça check- `Use Lighting Scene` in do seu perfil e preencha a `Lighting Scenes` matriz.

### <a name="cached-lighting-settings"></a>Configurações de iluminação em cache

Seu perfil armazena cópias em cache das configurações de iluminação mantidas em suas cenas de iluminação. Se essas configurações forem alteradas nos bastidores de iluminação, você precisará atualizar seu cache para garantir que a iluminação apareça como esperado no modo de reprodução. Seu perfil exibirá um aviso quando suspeitar de que as configurações armazenadas em cache estão desatualizadas. Clicar em `Update Cached Lighting Settings` carregará cada uma de suas cenas de iluminação, extrairá suas configurações e, em seguida, as armazenará em seu perfil.

![Configurações de iluminação em cache do sistema de cena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Comportamento do editor

Um benefício de usar cenas de iluminação é saber que o conteúdo está aceso corretamente durante a edição. Para esse fim, o serviço de cena manterá uma cena de iluminação carregada em todos os momentos e copiará as configurações de iluminação dessa cena para a cena ativa atual.\*

Você pode alterar qual cena de iluminação é carregada abrindo o [Inspetor de serviço](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) do sistema de cena. No modo de edição, você pode fazer a transição instantânea entre os bastidores de iluminação. No modo de reprodução, você pode visualizar as transições.

![Inspetor do sistema de cena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Observação: normalmente, a cena ativa determina as configurações de iluminação no editor. No entanto, optamos por não usar esse recurso para impor as configurações de iluminação, pois a cena ativa também é onde os objetos recém-criados são colocados por padrão, e cenas de iluminação só são permitidas para conter componentes de iluminação. Em vez disso, as configurações da cena de iluminação atual são automaticamente copiadas para as configurações da cena ativa. Tenha em mente que isso fará com que as configurações de iluminação de sua cena de conteúdo sejam sobrescritas.*
