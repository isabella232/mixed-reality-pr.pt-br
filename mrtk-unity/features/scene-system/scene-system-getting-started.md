---
title: Começar a trabalhar com o sistema de cena
description: Página de aterrissagem do sistema de cena com o MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 16adf431498f8146ca2cc60565e59dc8ae03fd92
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177569"
---
# <a name="scene-system-getting-started"></a>Começar a trabalhar com o sistema de cena

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

As seções a seguir descrevem agora para resolver essa mensagem, com base em qual método foi usado para importar o Toolkit.

### <a name="unity-package-manager-upm"></a>Unity Gerenciador de Pacotes (UPM)

Nos pacotes upm Toolkit realidade misturada, os recursos do sistema de cena são empacotados como um exemplo. Devido a pacotes UPM serem imutáveis, o Unity não poderá abrir o arquivo de cena necessário, a menos que eles sejam explicitamente importados para o projeto.

Para importar, use as seguintes etapas:

- Selecione **Janela**  >  **Gerenciador de Pacotes**
- Selecione **Realidade Misturada Toolkit Foundation**
- Localizar **recursos do sistema de** cena na seção **Exemplos**

  ![Importar recursos do sistema de cena](../images/scene-system/UpmImportSceneSystemResources.png)

- Selecione **Importar**

### <a name="asset-unitypackage-files"></a>Arquivos de ativo (.unitypackage)

Se a pasta SceneSystemResources tiver sido excluída ou tiver sido deseleitada durante a importação, ela poderá ser recuperada usando as seguintes etapas:

- Selecionar **Pacote** Personalizado  >  **de Importação de**  >  **Ativos**
- Abra o **Microsoft.MixedReality.Toolkit. Pacote foundation**
- Verifique se **Services/SceneSystem/SceneSystemResources** e todas as opções filho estão selecionadas

  ![Reimporte recursos do sistema de cena](../images/scene-system/ReimportSceneSystemResources.png)

- Selecione **Importar**

## <a name="how-to-use-the-scene-system"></a>Como usar o sistema de cena

- [Tipos de cena](scene-system-scene-types.md)
- [Carregamento de cena de conteúdo](scene-system-content-loading.md)
- [Monitorando o carregamento de conteúdo](scene-system-load-progress.md)
- [Carregamento de cena de iluminação](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>Configurações do editor

Por padrão, o Sistema de Cena impõe vários comportamentos no editor do Unity. Se você encontrar qualquer um desses comportamentos com muita mão, eles poderão ser desabilitados na seção **Editor Configurações** do seu perfil do Sistema de Cena.

- `Editor Manage Build Settings:` Se true, o serviço atualizará suas configurações de build automaticamente, garantindo que todas as cenas de gerenciador, iluminação e conteúdo sejam adicionadas. Desabilite isso se você quiser ter controle total sobre as configurações de build.

- `Editor Enforce Scene Order:` Se true, o serviço garantirá que a cena do gerente seja exibida primeiro na hierarquia de cena, seguida pela iluminação e, em seguida, pelo conteúdo. Desabilite isso se você quiser ter controle total sobre a hierarquia de cena.

- `Editor Manage Loaded Scenes:` Se true, o serviço garantirá que o gerenciador, o conteúdo e as cenas de iluminação sejam sempre carregados. Desabilite se você quiser ter controle total sobre quais cenas são carregadas no editor.

- `Editor Enforce Lighting Scene Types:` Se true, o serviço garantirá que somente os componentes relacionados à iluminação definidos em `PermittedLightingSceneComponentTypes` sejam permitidos em cenas de iluminação. Desabilite se você quiser controle total sobre o conteúdo das cenas de iluminação.

![Configurações do editor do sistema de cena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
