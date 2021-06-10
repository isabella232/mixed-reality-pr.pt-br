---
title: Como usar o plug-in OpenXR de Realidade Misturada
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547069"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a>Como usar o plug-in OpenXR de Realidade Misturada

Para os desenvolvedores que visam o Unity 2020 criarem aplicativos de realidade 2 ou misturados, o plug-in OpenXR pode ser usado em vez do plug-in WindowsXR para melhorar as compatibilidades entre plataformas.  O plug-in OpenXR de realidade misturada também funciona bem com o mais recente [Kit de ferramentas de realidade mista 2,7](/windows/mixed-reality/mrtk-unity).

## <a name="prerequisites"></a>Pré-requisitos

* LTS do Unity 2020,3 mais recente, (recomendamos o 2020.3.8 F1 ou superior)
* Plug-in mais recente do Unity OpenXR (Recomendamos 1,2 ou posterior)
* Ferramentas mais recentes [para o desenvolvimento do HoloLens 2](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* MRTK mais recente (opcional), (recomendamos a versão 2,7 ou posterior)
* Plugin OpenXR de realidade mista mais recente, (recomendamos a versão 1.0.0-Preview. 1 ou posterior)

![Captura de tela da amostra do Open XR Unity básico em execução em um HoloLens](images/openxr-example.png)

> [!NOTE]
> Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário. No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

> [!div class="nextstepaction"]
> [Configurar seu projeto usando o MRTK](./tutorials/mr-learning-base-02.md?tabs=openxr)

Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada. Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Configurando seu destino de compilação

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1. Selecione **arquivo > configurações de Build...**
2. Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**
3. Defina a **Arquitetura** como **ARM 64**
4. Defina o **Dispositivo de destino** como **HoloLens**
5. Defina o **Tipo de Build** como **D3D**
6. Defina o **SDK do UWP** como **Último instalado**

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

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

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Projetos de exemplo do Unity para OpenXR e HoloLens 2

Confira o [repositório de exemplos de realidade misturada OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo de Unity mostrando como criar aplicativos de Unity para o HoloLens 2 ou headsets de realidade misturada usando o plug-in OpenXR de realidade misturada.

## <a name="using-mrtk-with-openxr-support"></a>Usando o MRTK com suporte a OpenXR

O MRTK para a versão 2,7 do Unity agora dá suporte oficialmente ao plug-in OpenXR da realidade mista.

Abra a [ferramenta de funcionalidade Mixed Reality](welcome-to-mr-feature-tool.md) novamente para instalar o kit de ferramentas do reality misto, se ainda não tiver feito isso. O suporte do OpenXR está no pacote **base** .

![Ferramenta de recursos da realidade misturada descobrir janela de características com ativos padrão realçados](images/mrft-install-openxr.png)

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
