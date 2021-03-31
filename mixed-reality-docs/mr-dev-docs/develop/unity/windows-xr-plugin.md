---
title: Usando o plug-in do Windows XR
description: Saiba como configurar seus projetos do Unity com e sem MRTK usando o suporte do Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto, realidade do Windows Mixed, UWP, XR, desempenho, herdado, mrtk, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938091"
---
# <a name="using-windows-xr-plugin"></a>Usando o plug-in do Windows XR

Para desenvolvedores direcionados para o Unity 2020, o plug-in do Windows XR permite o acesso a recursos mistos de realidade em headsets do HoloLens 2 e do Windows Mixed Reality.  Esse plug-in também tem suporte no Unity 2019, embora haja algumas incompatibilidades conhecidas com âncoras espaciais do Azure ao usar esse plug-in nessa versão.

Embora a Microsoft e a Comunidade tenham criado ferramentas abertas como o [MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) que configurará automaticamente o ambiente WMR, muitos desenvolvedores desejam criar suas experiências desde o início.  A documentação a seguir demonstrará como configurar corretamente um projeto para o desenvolvimento de realidade misturada se você estiver usando MRTK ou não.  As configurações que você precisa alterar são divididas em duas categorias: configurações por projeto e configurações por cena.

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

> [!div class="nextstepaction"]
> [Experimente os nossos tutoriais do MRTK](tutorials/mr-learning-base-01.md)

Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

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

Depois de definir sua plataforma, você precisa permitir que o Unity saiba como criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada:

1. No editor do Unity, navegue até **editar > configurações do projeto** e selecione **Gerenciamento de plugin XR**

2. Selecione **instalar o gerenciamento de plugin XR**

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-5.png)

3. Selecione **inicializar XR na inicialização** e **Windows Mixed Reality**

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-7.png)

4. Expanda a seção **Gerenciamento de plug-ins do XR** e selecione **Universal guia Configurações da plataforma Windows**
5. Se você estiver usando o Unity 2020 ou posterior, verá as opções para verificar a realidade do **OpenXR** ou do **Windows Mixed**. 
    * Você pode escolher qualquer tempo de execução.  Se você estiver desenvolvendo especificamente para o HoloLens 2 ou para a HP reverbs G2 e decidir experimentar o **OpenXR**, selecione a caixa OpenXR e examine nosso guia para [usar o plug-in de realidade misturada do OpenXR para](openxr-getting-started.md) que o Unity se prepare corretamente para esses dispositivos antes de retornar a este tutorial

> [!NOTE]
> A partir do Unity 2020 LTS, a Microsoft está adotando o desenvolvimento com o OpenXR.  À medida que migramos para esse caminho, no Unity 2021,1, o plug-in do Windows XR será preterido e removido em 2021,2, tornando OpenXR o único caminho com suporte. Você pode encontrar mais informações sobre como [usar o plug-in OpenXR de realidade misturada](openxr-getting-started.md).

6. Se você decidir escolher o plug-in de **realidade mista do Windows** , marque todas as caixas e defina o **modo de envio de profundidade** como profundidade de **16 bits**

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção realidade mista do Windows realçada](images/wmr-config-img-8.png)
