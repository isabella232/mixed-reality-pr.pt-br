---
title: Hub de exemplos do MRTK
description: Visão geral sobre cenas de exemplo no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 6f86a7b6469a8dc7f6253d81f8cf647fbcfe35830fa8cf044066ba8ae9c5a286
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209238"
---
# <a name="mrtk-examples-hub"></a>Hub de exemplos do MRTK

![Hub de exemplos do MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

O Hub de Exemplos do MRTK é uma cena do Unity que facilita a experiência de várias cenas. Ele usa o Sistema de Cena do MRTK para carregar & descarregar as cenas.

**MRTKExamplesHub.unity é** a cena de contêiner que tem componentes compartilhados, incluindo ``MixedRealityToolkit`` e ``MixedRealityPlayspace`` . **A cena MRTKExamplesHubMainMenu.unity** tem os botões de cubo.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Baixar o aplicativo Microsoft Store no HoloLens 2
Se você tiver HoloLens 2, poderá baixar e instalar diretamente o aplicativo em seu dispositivo.

<a href='//www.microsoft.com/store/apps/9mv8c39l2sj4?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="prerequisite"></a>Pré-requisito

O Hub de Exemplos do MRTK usa [o Serviço de Transição de Cena](../extensions/scene-transition-service.md) e scripts relacionados. Se você estiver usando o MRTK por meio de pacotes do Unity, importe **Microsoft.MixedReality.Toolkit. Unity.Extensions.x.x.x.unitypackage** que faz parte dos pacotes [de lançamento.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Se você estiver usando o MRTK por meio do clone do repositório, já deverá ter a pasta **MRTK/Extensões** em seu projeto.

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamples Cena doHub e o sistema de cena

Abra **MRTKExamplesHub.unity,** que está localizado em É uma cena vazia com `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace e LoadHubOnStartup. Esta cena está configurada para usar o Sistema de Cena do MRTK. Clique `MixedRealitySceneSystem` em MixedRealityToolkit. Ele exibirá as informações do Sistema de Cena no painel Inspetor.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

Na parte inferior do Inspetor, ele exibe a lista das cenas definidas no Perfil do Sistema de Cena. Você pode clicar nos nomes de cena para carregá-los/descarregá-los.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Exemplo de carregamento _da cena MRTKExamplesHub_ clicando no nome da cena na lista.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Exemplo de carregamento _da cena HandInteractionExamples._
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Exemplo de carregamento de várias cenas.

## <a name="running-the-scene"></a>Executando a cena

A cena funciona no modo de jogo do Unity e no dispositivo. Execute a **cena MRTKExamplesHub** no editor do Unity e use a simulação de entrada do MRTK para interagir com o conteúdo da cena. Para criar e implantar, basta criar a cena **MRTKExamplesHub** com outras cenas incluídas na lista do Sistema de Cena. O inspetor também facilita adicionar cenas ao build Configurações. Na cena Configurações, certifique-se de que **MRTKExamplesHub** está na parte superior da lista no índice 0.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>Como MRTKExamplesHub carrega uma cena

Na cena **MRTKExamplesHub,** você pode encontrar o ``ExamplesHubButton`` pré-fab.
Há um **objeto FrontPlate** no pré-fab que contém ``Interactable`` .
Usando o e o evento Interactable, ele dispara a função ``OnClick()`` ``OnTouch()`` **LoadContentScene** do script **LoadContent().**
No Inspetor do script **LoadContentScene,** você pode definir o nome da cena a ser carregada.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

O script usa a função LoadContent() do Sistema de Cena para carregar a cena.
Consulte a página Sistema [de Cena](../scene-system/scene-system-getting-started.md) para obter mais detalhes.

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Retornando à cena do menu principal

Para retornar à cena do menu principal (cena MRTKExamplesHubMainMenu), você pode usar o mesmo método sistema de `LoadContent()` cena. O **ToggleFeaturesPanelExamplesHub.prefab** fornece o botão "Página Inicial", que contém o script **LoadContentScene.** Use esse pré-fab ou forneça um botão home personalizado em cada cena para permitir que o usuário retorne à cena principal. É possível colocar **ToggleFeaturesPanelExamplesHub.prefab** na cena **MRTKExamplesHub** para torná-la sempre visível, pois **MRTKExamplesHub** é uma cena de contêiner compartilhado. Certifique-se de ocultar/desativar **ToggleFeaturesPanel.prefab** em cada cena de exemplo.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Adicionando botões adicionais

No objeto **CubeCollection,** duplique (ou adicione) os pré-fabs _ExampleHubButton_ e clique em Atualizar **Coleção** no `GridObjectCollection` .
Isso atualizará o layout do cilindro com base no novo número total de botões.
Consulte a página [Coleção de Objetos](../ux-building-blocks/object-collection.md) para obter mais detalhes.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Depois de adicionar os botões, atualize o nome da cena no script **LoadContentScene** (explicado acima).
Adicione cenas adicionais ao perfil do Sistema de Cena.
