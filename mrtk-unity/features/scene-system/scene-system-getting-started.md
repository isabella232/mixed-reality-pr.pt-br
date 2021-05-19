---
title: Introdução ao sistema de cena
description: Página de aterrissagem do sistema de cena com o MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144306"
---
# <a name="scene-system-overview"></a>Visão geral do sistema de cena

## <a name="when-to-use-the-scene-system"></a>Quando usar o sistema de cena

Se o projeto consistir em uma única cena, o Sistema de Cena provavelmente não será necessário. É mais útil quando um ou mais dos seguintes são verdadeiros:

- Seu projeto tem várias cenas.
- Você está acostumado com o carregamento de cena única, mas não gosta da maneira como ela destrói a instância do MixedRealityToolkit.
- Você deseja uma maneira simples de carregar aditivamente várias cenas para construir sua experiência.
- Você deseja uma maneira simples de acompanhar as operações de carga em andamento ou uma maneira simples de controlar a ativação de cena para várias cenas sendo carregadas ao mesmo tempo.
- Você deseja manter a iluminação consistente e previsível em todas as suas cenas.

## <a name="scene-system-resources"></a>Recursos do sistema de cena

Por padrão, o Sistema de Cena utiliza um par de objetos de cena (cena DefaultManagerScene e DefaultLighting). Se qualquer uma dessas cenas não puder ser localizada, uma mensagem será exibida no inspetor de perfil do Sistema de Cena.

![Mensagem de recursos padrão](../images/scene-system/DefaultResourcesMessage.png)

>! [Observação] Se o projeto estiver usando o gerenciador personalizado e as cenas de iluminação, essa mensagem poderá ser ignorada com segurança.

As seções a seguir descrevem agora para resolver essa mensagem, com base em qual método foi usado para importar o Kit de Ferramentas de Realidade Misturada.

### <a name="unity-package-manager-upm"></a>Unity Gerenciador de Pacotes (UPM)

Nos pacotes UPM do Kit de Ferramentas de Realidade Misturada, os recursos do sistema de cena são empacotados como um exemplo. Devido a pacotes UPM serem imutáveis, o Unity não poderá abrir o arquivo de cena necessário, a menos que eles sejam explicitamente importados para o projeto.

Para importar, use as seguintes etapas:

- Selecionar   >  **Gerenciador de pacotes** do Windows
- Selecione **Mixed Reality Toolkit Foundation**
- Localizar **recursos do sistema de cena** na seção de **exemplos**

  ![Importar recursos do sistema de cena](../images/scene-system/UpmImportSceneSystemResources.png)

- Selecionar **importação**

### <a name="asset-unitypackage-files"></a>Arquivos de ativo (. unitypackage)

Se a pasta SceneSystemResources tiver sido excluída ou tiver sido desmarcada durante a importação, ela poderá ser recuperada usando as seguintes etapas:

- Selecione os **ativos** pacote de  >  **importação** pacote  >  **personalizado**
- Abra o pacote **Microsoft. MixedReality. Toolkit. Foundation**
- Verifique se os **Serviços/SceneSystem/SceneSystemResources** e todas as opções filho estão selecionadas

  ![Reimportar recursos do sistema de cena](../images/scene-system/ReimportSceneSystemResources.png)

- Selecionar **importação**

## <a name="how-to-use-the-scene-system"></a>Como usar o sistema de cena

- [Tipos de cena](scene-system-scene-types.md)
- [Carregamento de cena de conteúdo](scene-system-content-loading.md)
- [Monitorando o carregamento de conteúdo](scene-system-load-progress.md)
- [Carregamento da cena de iluminação](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>Configurações do editor

Por padrão, o sistema de cena impõe vários comportamentos no editor do Unity. Se você encontrar qualquer um desses comportamentos de alta mão, eles poderão ser desabilitados na seção **configurações do editor** do seu perfil de sistema de cena.

- `Editor Manage Build Settings:` Se for true, o serviço atualizará as configurações de Build automaticamente, garantindo que todas as cenas de gerente, iluminação e conteúdo sejam adicionadas. Desabilite-o se desejar ter controle total sobre as configurações de compilação.

- `Editor Enforce Scene Order:` Se for true, o serviço garantirá que a cena do gerente seja exibida primeiro na hierarquia de cena, seguida da iluminação e do conteúdo. Desabilite-o se desejar ter controle total sobre a hierarquia de cena.

- `Editor Manage Loaded Scenes:` Se for verdadeiro, o serviço garantirá que os bastidores gerente, conteúdo e iluminação sempre sejam carregados. Desabilite se você quiser o controle total sobre quais cenas são carregadas no editor.

- `Editor Enforce Lighting Scene Types:` Se for true, o serviço garantirá que apenas os componentes relacionados à iluminação definidos no `PermittedLightingSceneComponentTypes` sejam permitidos em cenas de iluminação. Desabilite se você quiser controle total sobre o conteúdo de cenas de iluminação.

![Configurações do editor do sistema de cena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
