---
title: Usando o plug-in OpenXR de realidade misturada para o Unity
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: cae588acbcddeefae45a555f335f1c74389f1824
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496164"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Usando o plug-in OpenXR de realidade misturada para o Unity

A partir da versão 2020,2 do Unity, o pacote de plugin OpenXR de realidade misturada da Microsoft está disponível usando o UPM (Gerenciador de pacotes do Unity).

## <a name="prerequisites"></a>Pré-requisitos

* Unity 2020,2 ou posterior
* Plug-in do Unity OpenXR 0.1.3 ou posterior
* Visual Studio 2019 ou posterior
* Instalar o suporte da plataforma **UWP** no Unity para aplicativos do HoloLens 2

> [!NOTE]
> Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário. No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a>Instalando o OpenXR com a ferramenta de funcionalidade de realidade misturada

Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada. Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](images/feature-tool-openxr.png)

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

![Captura de tela do Gerenciador de pacotes do Unity abrir no editor do Unity com realidade misturada OpenXR plugin selecionado e exemplos de importação do botão realçado](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Quando um pacote é atualizado, o Unity fornece a opção de atualizar amostras importadas.  A atualização de um exemplo importado substituirá as alterações feitas no exemplo e nos ativos associados.

## <a name="using-mrtk-with-openxr-support"></a>Usando o MRTK com suporte a OpenXR

O MRTK Unity dá suporte ao plug-in OpenXR da realidade mista começando pela versão 2.5.3.  

1. Abra a [ferramenta de funcionalidade Mixed Reality](welcome-to-mr-feature-tool.md) novamente e selecione o pacote de **plug-in OpenXR da realidade misturada** na categoria suporte à plataforma
2. Vá para o script de componente do MixedReality Toolkit no Inspetor e alterne para o perfil **DefaultOpenXRConfigurationProfile** :

![Captura de tela de alternância da configuração MRTK no componente Mixed Reality Toolkit no Inspetor](images/openxr-img-11.png)

### <a name="known-issues"></a>Problemas conhecidos 

Ao usar o recurso de acompanhamento de mão, adicione a seguinte linha no arquivo **assets/MixedRealityToolkit. Generated/link.xml** :

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a>Próximas etapas

Agora que você tem o projeto configurado para OpenXR e tem acesso a exemplos, confira quais [recursos](openxr-supported-features.md) têm suporte no momento em nosso plug-in OpenXR.

## <a name="have-feedback"></a>Tem comentários?

O OpenXR ainda é experimental, portanto, agradecemos os comentários que você pode nos dar para ajudá-lo a melhorá-lo. Você nos verá nos fóruns do [Unity](https://aka.ms/unityforums) marcando sua postagem no fórum com o **Microsoft**  +  **OpenXR** e o **HoloLens 2** ou a **realidade mista do Windows**.

## <a name="see-also"></a>Consulte também

* [Como configurar seu projeto sem o MRTK](configure-unity-project.md)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
