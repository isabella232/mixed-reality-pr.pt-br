---
title: Usando o plug-in OpenXR de realidade misturada para o Unity
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 7d28dd50e111da4b010bcae699b7451d967e8f35
ms.sourcegitcommit: 653ddcae6d7a1617c89da1153fa8e7b482ef6818
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97905288"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Usando o plug-in OpenXR de realidade misturada para o Unity

A partir da versão 2020,2 do Unity, o pacote de plugin OpenXR de realidade misturada da Microsoft está disponível usando o UPM (Gerenciador de pacotes do Unity).

## <a name="prerequisites"></a>Pré-requisitos

* Unity 2020,2 ou posterior
* Plug-in do Unity OpenXR 0.1.1 ou posterior
* Visual Studio 2019 ou posterior
* Instalar o suporte da plataforma **UWP** no Unity para aplicativos do HoloLens 2

> [!NOTE]
> Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário. No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.

## <a name="installing-the-mixed-reality-openxr-plugin"></a>Instalando o plug-in OpenXR de realidade misturada

Seu projeto precisa instalar o plug-in **OpenXR** e pacotes de **Gerenciamento de plugin XR** antes de usar o plug-in OpenXR da realidade mista. Se você já os instalou, ótimo! Caso contrário, a instalação do plug-in OpenXR de realidade misturada os instalará automaticamente como dependências:

1. No editor do Unity, navegue até **Editar configurações do projeto > > Gerenciador de pacotes**
2. Expanda a seção **registros no escopo** , insira as informações a seguir e selecione **salvar**:
    * Definir o **nome** para a **realidade mista da Microsoft**
    * Definir **URL** como **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**
    * Definir **escopo (s)** como **com. Microsoft. mixedreality**

3. Em **Configurações avançadas**, selecione **habilitar pacotes de visualização**

![Captura de tela da janela do Gerenciador de pacotes do Unity aberta nas configurações do projeto](images/openxr-img-01.png)

O Gerenciador de pacotes do Unity usa um arquivo de manifesto chamado *manifest.jsno* para determinar quais pacotes instalar e os registros dos quais eles podem ser instalados.

> [!IMPORTANT]
> O OpenXR ainda é experimental no Unity e esse processo pode mudar ao longo do tempo enquanto trabalhamos para otimizar a experiência do desenvolvedor.

### <a name="registering-the-mixed-reality-dependency"></a>Registrando a dependência da realidade misturada

Depois que o registro com escopo do Microsoft Mixed Reality tiver sido adicionado ao manifesto, o pacote OpenXR poderá ser especificado.

Para adicionar o pacote OpenXR:

1. Abra **[projectRoot]/Packages/manifest.js** em um editor de texto como Visual Studio Code
    1. Para obter aqui, clique com o botão direito do mouse em **pacotes** no painel esquerdo da janela do projeto. Em seguida, clique em **Mostrar no Explorer**.
    ![Captura de tela da listagem de pacotes na janela do projeto](images/packages.png)
1. Modifique a seção dependências dos *pacotes/manifest.jsno* arquivo da seguinte maneira:

    > [!IMPORTANT]
    > Pode haver mais dependências no arquivo de manifesto do que mostrado aqui. Não exclua nenhum deles, basta adicionar a dependência OpenXR à lista.

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.1",
      }
    ```

1. Salve o arquivo, volte para o editor do Unity e abra o **Gerenciador de pacotes** para confirmar se o plug-in está instalado:

    ![Captura de tela do Gerenciador de pacotes do Unity aberta no editor do Unity com realidade misturada OpenXR plugin realçado](images/openxr-img-03.png)

    > [!Note]
    > Se o pacote OpenXR for removido usando o Gerenciador de pacotes do Unity, você precisará adicioná-lo novamente usando as etapas descritas anteriormente.

## <a name="configuring-xr-plugin-management-for-openxr"></a>Configurando o gerenciamento de plugin XR para OpenXR

Para definir OpenXR como o tempo de execução no Unity:

1. No editor do Unity, navegue até **editar > configurações do projeto**
2. Na lista de configurações, selecione **Gerenciamento de plugin XR**
3. Verifique as caixas **inicializar XR nas inicializações** e **OpenXR (visualização)**
4. Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione **conjunto de recursos do Microsoft HoloLens**

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-img-05.png)

> [!IMPORTANT]
> Se você vir um ícone de aviso vermelho ao lado do **plug-in OpenXR (versão prévia)**, clique no ícone e selecione **corrigir tudo** antes de continuar. O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.

![Captura de tela da janela de validação do projeto OpenXR](images/openxr-img-06.png)

Agora você está pronto para começar a desenvolver com o OpenXR no Unity!  Continue na próxima seção para aprender a usar os exemplos de OpenXR.

## <a name="optimization"></a>Optimization

Se você estiver desenvolvendo para o HoloLens 2, navegue até a **realidade misturada> OpenXR > aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>Experimente os bastidores de exemplo do Unity

Para utilizar um ou mais dos exemplos, instale o [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) do **Gerenciador de pacotes**:

![Captura de tela do Gerenciador de pacotes do Unity aberta no editor do Unity com o AR Foundation realçado](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>Exemplos de HoloLens 2

1. No editor do Unity, navegue até a **janela > Gerenciador de pacotes**
2. Na lista de pacotes, selecione **OpenXR de realidade misturada plug-in**
3. Localize o exemplo na lista de **exemplos** e selecione **importar**

![Captura de tela do Gerenciador de pacotes do Unity abrir no editor do Unity com realidade misturada OpenXR plugin selecionado e exemplos de importação do botão realçado](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Quando um pacote é atualizado, o Unity fornece a opção de atualizar amostras importadas.  A atualização de um exemplo importado substituirá as alterações feitas no exemplo e nos ativos associados.

## <a name="next-steps"></a>Próximas etapas

Agora que você tem o projeto configurado para OpenXR e tem acesso a exemplos, confira quais [recursos](openxr-supported-features.md) têm suporte no momento em nosso plug-in OpenXR.

## <a name="have-feedback"></a>Tem comentários?

O OpenXR ainda é experimental, portanto, agradecemos os comentários que você pode nos dar para ajudá-lo a melhorá-lo. Você nos verá nos fóruns do [Unity](https://aka.ms/unityforums) marcando sua postagem no fórum com o **Microsoft**  +  **OpenXR** e o **HoloLens 2** ou a **realidade mista do Windows**.

## <a name="see-also"></a>Veja também

* [Como configurar seu projeto sem o MRTK](configure-unity-project.md)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
