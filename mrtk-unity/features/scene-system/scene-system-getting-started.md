---
title: Introdução ao sistema de cena
description: Página de aterrissagem do sistema de cena com MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 5b4f1c3b0f069d320feca8ccecacc6c66576b50339ea7b7733f34525005dd842
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191540"
---
# <a name="scene-system-getting-started"></a>Introdução ao sistema de cena

## <a name="when-to-use-the-scene-system"></a>Quando usar o sistema de cena

Se o projeto consistir em uma única cena, o sistema de cena provavelmente não é necessário. É mais útil quando um ou mais dos seguintes itens são verdadeiros:

- Seu projeto tem várias cenas.
- Você está acostumado a carregar uma única cena, mas não gosta da maneira como ela destrói a instância MixedRealityToolkit.
- Você quer uma maneira simples de carregar de forma aditiva várias cenas para construir sua experiência.
- Você quer uma maneira simples de controlar as operações de carregamento em andamento ou uma maneira simples de controlar a ativação de cena para várias cenas sendo carregadas ao mesmo tempo.
- Você deseja manter a iluminação consistente e previsível em todos os seus bastidores.

## <a name="scene-system-resources"></a>Recursos do sistema de cena

Por padrão, o sistema de cena utiliza um par de objetos de cena (DefaultManagerScene e cena de defaultlighting). Se nenhuma dessas cenas não puder ser localizada, uma mensagem será exibida no Inspetor de perfil do sistema de cena.

![Mensagem de recursos padrão](../images/scene-system/DefaultResourcesMessage.png)

>! Anotações Se o projeto estiver usando cenas de iluminação e gerente personalizado, essa mensagem poderá ser ignorada com segurança.

As seções a seguir descrevem agora para resolver essa mensagem, com base em qual método foi usado para importar a realidade misturada Toolkit.

### <a name="unity-package-manager-upm"></a>Gerenciador de Pacotes do Unity (UPM)

na realidade misturada Toolkit pacotes UPM, os recursos do sistema de cena são empacotados como um exemplo. Devido aos pacotes UPM serem imutáveis, o Unity não pode abrir o arquivo de cena necessário, a menos que eles sejam explicitamente importados para o projeto.

Para importar, use as seguintes etapas:

- selecionar   >  **Gerenciador de Pacotes** de janela
- selecionar **realidade misturada Toolkit Foundation**
- Localizar **recursos do sistema de cena** na seção de **exemplos**

  ![Importar recursos do sistema de cena](../images/scene-system/UpmImportSceneSystemResources.png)

- Selecionar **importação**

### <a name="asset-unitypackage-files"></a>Arquivos de ativo (. unitypackage)

Se a pasta SceneSystemResources tiver sido excluída ou tiver sido desmarcada durante a importação, ela poderá ser recuperada usando as seguintes etapas:

- Selecione os **ativos** pacote de  >  **importação** pacote  >  **personalizado**
- Abra o **Microsoft. MixedReality. Toolkit.** Pacote do Foundation
- Verifique se os **Serviços/SceneSystem/SceneSystemResources** e todas as opções filho estão selecionadas

  ![Reimportar recursos do sistema de cena](../images/scene-system/ReimportSceneSystemResources.png)

- Selecionar **importação**

## <a name="how-to-use-the-scene-system"></a>Como usar o sistema de cena

- [Tipos de cena](scene-system-scene-types.md)
- [Carregamento de cena de conteúdo](scene-system-content-loading.md)
- [Monitorando o carregamento de conteúdo](scene-system-load-progress.md)
- [Carregamento da cena de iluminação](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>Configurações do editor

Por padrão, o sistema de cena impõe vários comportamentos no editor do Unity. se você encontrar qualquer um desses comportamentos de alta gramatura, eles poderão ser desabilitados no **Editor Configurações** seção do seu perfil de sistema de cena.

- `Editor Manage Build Settings:` Se for true, o serviço atualizará as configurações de Build automaticamente, garantindo que todas as cenas de gerente, iluminação e conteúdo sejam adicionadas. Desabilite-o se desejar ter controle total sobre as configurações de compilação.

- `Editor Enforce Scene Order:` Se for true, o serviço garantirá que a cena do gerente seja exibida primeiro na hierarquia de cena, seguida da iluminação e do conteúdo. Desabilite-o se desejar ter controle total sobre a hierarquia de cena.

- `Editor Manage Loaded Scenes:` Se for verdadeiro, o serviço garantirá que os bastidores gerente, conteúdo e iluminação sempre sejam carregados. Desabilite se você quiser o controle total sobre quais cenas são carregadas no editor.

- `Editor Enforce Lighting Scene Types:` Se for true, o serviço garantirá que apenas os componentes relacionados à iluminação definidos no `PermittedLightingSceneComponentTypes` sejam permitidos em cenas de iluminação. Desabilite se você quiser controle total sobre o conteúdo de cenas de iluminação.

![Configurações do editor do sistema de cena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
