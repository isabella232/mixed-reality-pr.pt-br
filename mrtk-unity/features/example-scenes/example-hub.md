---
title: Hub de exemplos do MRTK
description: Visão geral das cenas de exemplo em MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 2b7e1234ed79a99e826184e42c319f84582ff23a
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757044"
---
# <a name="mrtk-examples-hub"></a>Hub de exemplos do MRTK

![Hub de exemplos do MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

O MRTK examples Hub é uma cena do Unity que facilita a experiência em várias cenas. Ele usa o sistema de cena do MRTK para carregar & descarregar os bastidores.

**MRTKExamplesHub. Unity** é a cena de contêiner que tem componentes compartilhados ``MixedRealityToolkit`` , incluindo e ``MixedRealityPlayspace`` . A cena **MRTKExamplesHubMainMenu. Unity** tem os botões de cubo.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>baixar o aplicativo de Microsoft Store no HoloLens 2
se você tiver HoloLens 2 dispositivo, poderá baixar e instalar diretamente o aplicativo em seu dispositivo.

<a href='//www.microsoft.com/store/apps/9mv8c39l2sj4?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="prerequisite"></a>Pré-requisito

O Hub de exemplos do MRTK usa o [serviço de transição de cena](../extensions/scene-transition-service.md) e os scripts relacionados. Se você estiver usando o MRTK por meio de pacotes do Unity, importe **Microsoft. MixedReality. Toolkit. Unity. Extensions. x. x. x. unitypackage** que faz parte dos [pacotes de versão](https://github.com/microsoft/MixedRealityToolkit-Unity/releases). Se você estiver usando o MRTK por meio do clone do repositório, você já deve ter a pasta **MRTK/Extensions** em seu projeto.

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>Cena MRTKExamplesHub e o sistema de cena

Abra **MRTKExamplesHub. Unity** que está localizado em `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` uma cena vazia com MixedRealityToolkit, MixedRealityPlayspace e LoadHubOnStartup. Esta cena está configurada para usar o sistema de cena do MRTK. Clique `MixedRealitySceneSystem` em em MixedRealityToolkit. Ele exibirá as informações do sistema de cena no painel inspetor.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

Na parte inferior do Inspetor, ele exibe a lista das cenas definidas no perfil do sistema de cena. Você pode clicar nos nomes de cena para carregá-los/descarregá-los.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Exemplo de carregamento de cena _MRTKExamplesHub_ clicando no nome da cena na lista.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Exemplo de carregamento de cena _HandInteractionExamples_ .
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Exemplo de carregamento de várias cenas.

## <a name="running-the-scene"></a>Executando a cena

A cena funciona no modo de jogo do Unity e no dispositivo. Execute a cena **MRTKExamplesHub** no editor do Unity e use a simulação de entrada do MRTK para interagir com o conteúdo da cena. Para compilar e implantar, basta criar uma cena **MRTKExamplesHub** com outras cenas incluídas na lista do sistema de cena. o inspetor também facilita a adição de cenas ao Configurações de compilação. no Configurações de construção, verifique se a cena **MRTKExamplesHub** está na parte superior da lista no índice 0.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>Como o MRTKExamplesHub carrega uma cena

Na cena **MRTKExamplesHub** , você pode encontrar o ``ExamplesHubButton`` pré-fabricado.
Há um objeto **FrontPlate** no pré-fabricado que contém ``Interactable`` .
Usando o ``OnClick()`` evento e interagir ``OnTouch()`` , ele dispara a função **LoadContent ()** do script **LoadContentScene** .
No Inspetor do script **LoadContentScene** , você pode definir o nome da cena a ser carregada.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

O script usa a função LoadContent () do sistema de cena para carregar a cena.
Consulte a página do [sistema de cena](../scene-system/scene-system-getting-started.md) para obter mais detalhes.

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Retornando à cena do menu principal

Para retornar à cena do menu principal (cena MRTKExamplesHubMainMenu), você pode usar o mesmo método de sistema de cena `LoadContent()` . O **ToggleFeaturesPanelExamplesHub. pré-fabricado** fornece o botão ' Home ' que contém o script **LoadContentScene** . Use este pré-fabricado ou forneça um botão Início personalizado em cada cena para permitir que o usuário retorne à cena principal. É possível colocar o **ToggleFeaturesPanelExamplesHub. pré-fabricado** na cena **MRTKExamplesHub** para torná-lo sempre visível, já que **MRTKExamplesHub** é uma cena de contêiner compartilhada. Certifique-se de ocultar/desativar **ToggleFeaturesPanel. pré-fabricado** em cada cena de exemplo.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Adicionando botões adicionais

No objeto **CubeCollection** , duplique (ou adicione) _ExampleHubButton_ pré-fabricados e clique em **Atualizar coleção** no `GridObjectCollection` .
Isso atualizará o layout do cilindro com base no novo número total de botões.
Veja a página [coleção de objetos](../ux-building-blocks/object-collection.md) para obter mais detalhes.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Depois de adicionar os botões, atualize o nome da cena no script **LoadContentScene** (explicado acima).
Adicione cenas adicionais ao perfil do sistema de cena.
