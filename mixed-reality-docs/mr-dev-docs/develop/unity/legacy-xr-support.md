---
title: Como usar o suporte para XR interno do Legacy
description: Saiba como configurar seus projetos do Unity com e sem MRTK usando o suporte interno a XR herdado.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto, Windows Mixed Reality, UWP, XR, desempenho, herdado, mrtk
ms.openlocfilehash: 534df0b9c4efbe62b00af6cccb74f4203c1557e9479b2101320bab3bbdb5e565
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192040"
---
# <a name="using-legacy-built-in-xr-support"></a>Usando o suporte interno a XR herdado

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

> [!div class="nextstepaction"]
> [Experimente os nossos tutoriais do MRTK](./tutorials/mr-learning-base-02.md?tabs=wsa)

Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:

![captura de tela da janela criar Configurações abrir no editor do unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

se você estiver direcionando HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1.  selecione **arquivo > Build Configurações...**
2.  selecione **Plataforma Universal do Windows** na lista plataforma e selecione **alternar plataforma**
3.  Defina a **Arquitetura** como **ARM 64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina o **Tipo de Build** como **D3D**
6.  Defina o **SDK do UWP** como **Último instalado**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![captura de tela da janela criar Configurações abrir no editor do unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada.

> [!CAUTION]
> O XR herdado é preterido no Unity 2019 e removido no Unity 2020.

1. abrir **Player Configurações...** do **Configurações de compilação... janela** e expandir o grupo de **Configurações XR**
2. na seção **Configurações do XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual
3. Definir o **formato de profundidade** como profundidade de **16 bits** e habilitar o **compartilhamento de buffer de profundidade**
4. Definir **modo de renderização estéreo** para **instância de passagem única**
5. Selecione **WSA Holographic Remoting com suporte** se você quiser usar o Holographic de comunicação remota 

![captura de tela da janela configurações do Project abrir no editor do unity com a seção configurações do Player realçada](images/wmr-config-img-9.png)