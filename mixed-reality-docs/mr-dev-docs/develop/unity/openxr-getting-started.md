---
title: Usando o plug-in OpenXR de realidade misturada para o Unity
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: ebe7d32b236e28259b2ed9a7915bd337f84f8762
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088495"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Usando o plug-in OpenXR de realidade misturada para o Unity

A partir da versão 2020,2 do Unity, o pacote de plugin OpenXR de realidade misturada da Microsoft está disponível usando o UPM (Gerenciador de pacotes do Unity).

## <a name="prerequisites"></a>Pré-requisitos

* Unity 2020,3 LTS ou posterior
* Plug-in do Unity OpenXR 1.0.3 ou posterior
* Visual Studio 2019 ou posterior
* Instalar o suporte da plataforma **UWP** no Unity para aplicativos do HoloLens 2

> [!NOTE]
> Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário. No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

> [!div class="nextstepaction"]
> [Configurar seu projeto usando o MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada. Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Configurando seu destino de compilação

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1.  Selecione **arquivo > configurações de Build...**
2.  Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**
3.  Definir a **arquitetura** para o **ARM 64**
4.  Definir o **dispositivo de destino** para o **HoloLens**
5.  Definir **tipo de compilação** como **D3D**
6.  Definir o **SDK do UWP** para o **mais recente instalado**
7.  Definir a **configuração de Build** como **Release** porque há problemas de desempenho conhecidos com a depuração

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada.

## <a name="configuring-xr-plugin-management-for-openxr"></a>Configurando o gerenciamento de plugin XR para OpenXR

Para definir OpenXR como o tempo de execução no Unity:

1. No editor do Unity, navegue até **editar > configurações do projeto**
2. Na lista de configurações, selecione **Gerenciamento de plugin XR**
3. Verifique as caixas **inicializar XR nas Startup** e **OpenXR**
4. Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione **conjunto de recursos do Microsoft HoloLens**

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-img-05.png)

## <a name="optimization"></a>Optimization

Se você estiver desenvolvendo para o HoloLens 2, navegue até a **realidade misturada> OpenXR > aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](images/openxr-img-08.png)

> [!IMPORTANT]
> Se você vir um ícone de aviso vermelho ao lado de **plug-in OpenXR**, clique no ícone e selecione **corrigir tudo** antes de continuar. O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.

![Captura de tela da janela de validação do projeto OpenXR](images/openxr-img-06.png)

Agora você está pronto para começar a desenvolver com o OpenXR no Unity!  Continue na próxima seção para aprender a usar os exemplos de OpenXR.

## <a name="try-out-the-unity-sample-scenes"></a>Experimente os bastidores de exemplo do Unity

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

MRTK-Unity dá suporte ao plug-in OpenXR de realidade misturada começando pela versão 2.5.3.

1. Abra a [ferramenta de funcionalidade Mixed Reality](welcome-to-mr-feature-tool.md) novamente para instalar o kit de ferramentas do reality misto, se ainda não tiver feito isso. O suporte do OpenXR está no pacote **base** .
2. Vá para o script de componente do MixedReality Toolkit no Inspetor e alterne para o perfil **DefaultOpenXRConfigurationProfile** :

    ![Captura de tela de alternância da configuração MRTK no componente Mixed Reality Toolkit no Inspetor](images/openxr-img-11.png)

    1. Consulte a documentação do MRTK para obter [informações mais detalhadas sobre como migrar para o OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).

> [!NOTE]
> Ao atualizar de uma versão anterior do MRTK, verifique se a linha a seguir está no arquivo **assets/MixedRealityToolkit. Generated/link.xml** :
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Essa linha será adicionada por padrão se você tiver iniciado com MRTK 2.5.4 ou mais recente.

## <a name="next-steps"></a>Próximas etapas

Agora que você tem o projeto configurado para OpenXR e tem acesso a exemplos, confira quais [recursos](openxr-supported-features.md) têm suporte no momento em nosso plug-in OpenXR.

## <a name="have-feedback"></a>Tem comentários?

O OpenXR ainda é experimental, portanto, agradecemos os comentários que você pode nos dar para ajudá-lo a melhorá-lo. Você nos verá nos fóruns do [Unity](https://aka.ms/unityforums) marcando sua postagem no fórum com o **Microsoft**  +  **OpenXR** e o **HoloLens 2** ou a **realidade mista do Windows**.

## <a name="see-also"></a>Confira também

* [Como configurar seu projeto sem o MRTK](configure-unity-project.md)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
