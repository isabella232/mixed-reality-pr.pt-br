---
title: Como usar o plug-in OpenXR de Realidade Misturada
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 733bbbd75dd170241e8781e24989d23902781fb9
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333438"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a>Como usar o plug-in OpenXR de Realidade Misturada

Para os desenvolvedores que visam o Unity 2020 criarem aplicativos de realidade 2 ou misturados, o plug-in OpenXR pode ser usado em vez do plug-in WindowsXR para melhorar as compatibilidades entre plataformas.  O plug-in Mixed Reality OpenXR também funciona bem com a [ferramenta de recursos de realidade misturada](welcome-to-mr-feature-tool.md)mais recente.

## <a name="prerequisites"></a>Pré-requisitos

* Mais recente o Unity 2020,3 LTS, recomendado 2020.3.6 F1 ou superior.
* Plug-in mais recente do Unity OpenXR, recomendado 1,2 ou posterior
* Ferramentas mais recentes [para o desenvolvimento do HoloLens 2](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* MRTK mais recente (opcional), recomendar a versão 2,6 ou posterior
* Plugin OpenXR de realidade mista mais recente, recomendar a versão 0.9.5 ou posterior

> [!NOTE]
> Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário. No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

> [!div class="nextstepaction"]
> [Configurar seu projeto usando o MRTK](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada. Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Configurando seu destino de compilação

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

Se você estiver direcionando o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1. Selecione **Arquivo > Configurações de Build...**
2. Selecione **Plataforma Universal do Windows** na lista Plataforma e selecione **Alternar Plataforma**
3. Defina a **Arquitetura** como **ARM 64**
4. Defina o **Dispositivo de destino** como **HoloLens**
5. Defina o **Tipo de Build** como **D3D**
6. Defina o **SDK do UWP** como **Último instalado**

![Captura de tela da janela Configurações de Build aberta no editor do Unity Plataforma Universal do Windows realçada](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>Configurando o gerenciamento de plug-in XR para OpenXR

Para definir o OpenXR como o runtime no Unity:

1. No Editor do Unity, navegue até **Editar configurações > projeto**
2. Na lista de Configurações, selecione Gerenciamento **de Plug-in XR**
3. Marque as **caixas Inicializar XR na Inicialização** **e OpenXR**
4. Se estiver direcionando o HoloLens 2, certifique-se de que você está na plataforma UWP e selecione **Microsoft HoloLens conjunto de recursos**

![Captura de tela do painel de configurações do projeto aberto no editor do Unity com o gerenciamento de plug-in XR realçada](images/openxr-img-05.png)

## <a name="optimization"></a>Optimization

Se você estiver desenvolvendo para o HoloLens 2, navegue até Realidade **Misturada> OpenXR > Aplicar** as configurações de projeto recomendadas para o HoloLens 2 para obter um melhor desempenho do aplicativo.

![Captura de tela do item de menu de realidade misturada aberto com OpenXR selecionado](images/openxr-img-08.png)

> [!IMPORTANT]
> Se você vir um ícone de aviso vermelho ao lado do **Plug-in OpenXR,** clique no ícone e selecione **Corrigir tudo** antes de continuar. O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.

![Captura de tela da janela de validação do projeto OpenXR](images/openxr-img-06.png)

Agora você está pronto para começar a desenvolver com o OpenXR no Unity!  Continue na próxima seção para saber como usar os exemplos do OpenXR.

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Projetos de exemplo do Unity para OpenXR e HoloLens 2

Confira o repo de exemplos do [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo do Unity mostrando como criar aplicativos unity para headsets do HoloLens 2 ou realidade misturada usando o plug-in OpenXR de Realidade Misturada.

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
