---
title: Integrar as Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar as Âncoras Espaciais do Azure em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens 2, âncoras espaciais do Azure, serviços de nuvem do azure, visão personalizada do azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 7f85efae0ee24e4785d862873b8b1723460791d2d6a00406a3fd81f465c6faa7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218546"
---
# <a name="4-integrating-azure-spatial-anchors"></a>4. Integrar as Âncoras Espaciais do Azure

Neste tutorial, você aprenderá a usar as **Âncoras Espaciais do Azure**. Você armazenará o local de um **Objeto Rastreado** como uma Âncora Espacial do Azure. Quando você consultar a âncora, uma seta será exibida para guiar você em direção ao local.

## <a name="objectives"></a>Objetivos

* Aprender os conceitos básicos das Âncoras Espaciais do Azure.
* Saber como configurar a cena para usar as Âncoras Espaciais do Azure neste projeto.
* Saber como integrar de locais de armazenamento e consulta.

## <a name="understanding-azure-spatial-anchors"></a>Noções básicas sobre Âncoras Espaciais do Azure

 As **Âncoras Espaciais do Azure** fazem parte da família de Serviços de Nuvem do Azure e são usadas para salvar locais de âncora. Os locais de âncora salvos podem ser recuperados com base na *ID da âncora* na nuvem. Esse local de âncora pode ser compartilhado e acessado por dispositivos de várias plataformas, como dispositivos HoloLens, iOS e Android.

Saiba mais sobre as [Âncoras Espaciais do Azure](/azure/spatial-anchors/overview).

## <a name="preparing-azure-spatial-anchors"></a>Preparar as Âncoras Espaciais do Azure

Para começar, crie um recurso de âncora espacial no portal do Azure.
Saiba como criar um [recurso de âncora espacial](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você aprenderá a configurar a cena e a fazer as alterações necessárias.

Selecione o objeto **MixedRealityToolkit** na janela Hierarquia e use o botão **Adicionar Componente** na janela Inspetor para adicionar o **AR Anchor Manager (script)**

![Objeto MixedRealityToolkit do Unity com os componentes do AR Anchor Manager adicionados ](images/mr-learning-azure/tutorial4-section1-step1-1.png)

> [!NOTE]
> Quando você adiciona o componente AR Anchor Manager (script), o componente AR Session Origin (script) é adicionado automaticamente, pois ele é exigido pelo componente AR Anchor Manager (script).

Na janela Projeto, navegue até **Ativos > MRTK.Tutorials.AzureCloudServices > Pré-fabricados > Gerenciador**

![Unity com o pré-fabricado AnchorManager selecionado](images/mr-learning-azure/tutorial4-section1-step1-2.png)

Na pasta **Gerenciador**, arraste e solte o pré-fabricadp **Gerenciador de Âncora** na Hierarquia de cena.

Selecione o GameObject **Gerenciador de Âncora** na Hierarquia e, na seção Inspetor, você encontrará o **Gerenciador de Âncora Espacial** (Script). Localize a ID da conta e o campo de chave e adicione as credenciais que você criou no pré-requisito no estágio anterior.

![Unity com o pré-fabricado AnchorManager recém-adicionado ainda selecionado](images/mr-learning-azure/tutorial4-section1-step2-1.png)

Agora, localize o objeto **Controlador de Cena** na Hierarquia de cena e selecione-o. Você verá o Inspetor do **Controlador de Cena**.

![Unity com o componente de script de SceneController configurado](images/mr-learning-azure/tutorial4-section1-step3-1.png)

Você observará que o campo do **Gerenciador de Âncora** no componente **Controlador de Cena** está vazio; arraste o **Gerenciador de Âncora** da Hierarquia e solte-o na cena desse campo e salve a cena.

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a>Compilar e Implantar o aplicativo no HoloLens 2

As Âncoras Espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade delas, você precisa implantar o projeto em seu dispositivo.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo no seu HoloLens 2](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>Execute o aplicativo no seu HoloLens 2 e siga as instruções no aplicativo

### <a name="create-an-anchor-to-store-a-location"></a>Criar uma âncora para armazenar um local

Nesta seção, você verá como salvar o local do objeto.

Execute o aplicativo e clique em **Definir Objeto** no menu principal da experiência.

Forneça o **nome** do objeto que você deseja salvar e clique em **Definir Objeto** para continuar. Para adicionar mais informações sobre o objeto, selecione a **imagem** e descreva o objeto.

Para salvar o local, clique em **Salvar Local**

Você verá um **ponteiro de âncora** que poderá mover e posicionar no local que deseja salvar. Depois disso, você verá um pop-up de confirmação. Se você quiser confirmar e salvar o local, clique em **Sim**; caso contrário, altere o local clicando em **Não** e selecionando o local novamente.

Depois de confirmar o local clicando em **Sim**, o local e a ID da Âncora serão salvos no armazenamento em nuvem do Azure. Depois de salvar, você verá a **Marca de objeto** na âncora com o nome do objeto.

Agora o local do objeto foi salvo com êxito.

### <a name="query-for-finding-an-anchor-location"></a>Consultar para localizar um local de âncora

Depois de salvar com êxito o local de âncora, agora você pode encontrar o local da âncora selecionando **Pesquisar Objeto** no menu principal.

Depois de clicar em **Pesquisar Objeto**, uma nova janela será exibida, na qual você deverá dar o nome do objeto que deseja pesquisar.

Insira o nome do objeto e clique em **Pesquisar Objeto**. Se o objeto foi salvo anteriormente e for encontrado no banco de dados, você obterá o cartão de objeto com todos os detalhes do objeto que você salvou anteriormente.

Agora você pode clicar em **Mostrar Local** para localizar o objeto. Ao clicar em **Mostrar Local**, o sistema consultará o endereço do objeto no armazenamento em nuvem.

Depois de recuperar o local com êxito, uma **seta** vai direcioná-lo para o local do objeto. Siga a marca de seta até encontrar o local do objeto.

Ao encontrar o objeto, o nome do objeto aparecerá na parte superior e a marca de seta desaparecerá e agora você poderá clicar na **marca de objeto** para ver os detalhes do objeto.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como as Âncoras Espaciais do Azure podem salvar e recuperar o local do objeto no Hololense 2.

No tutorial final, você aprenderá a usar o **Serviço de Bot do Azure** para adicionar linguagem natural como um novo método de interação para o aplicativo.

> [!div class="nextstepaction"]
> [Próximo tutorial: 5. Integrar o Serviço de Bot do Azure com o LUIS](mr-learning-azure-05.md)