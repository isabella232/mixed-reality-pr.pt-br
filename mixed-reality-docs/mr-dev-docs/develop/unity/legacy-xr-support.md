---
title: Como usar o suporte para XR interno do Legacy
description: Saiba como configurar seus projetos do Unity com e sem o MRTK usando o suporte a XR herdado.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidade misturada, desenvolvimento, começar, novo projeto, Windows Mixed Reality, UWP, XR, desempenho, herdado, mrtk
ms.openlocfilehash: b5faa48ec913c5095b12361318729b6f14276f30
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743506"
---
# <a name="using-legacy-built-in-xr-support"></a>Usando o suporte de XR herddo

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

> [!div class="nextstepaction"]
> [Experimente os nossos tutoriais do MRTK](./tutorials/mr-learning-base-02.md?tabs=wsa)

Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:

![Captura de tela da janela Configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

Se você estiver direcionando o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:

1.  Selecione **Arquivo > Configurações de Build...**
2.  Selecione **Plataforma Universal do Windows** na lista Plataforma e selecione **Alternar Plataforma**
3.  Defina a **Arquitetura** como **ARM 64**
4.  Defina o **Dispositivo de destino** como **HoloLens**
5.  Defina o **Tipo de Build** como **D3D**
6.  Defina o **SDK do UWP** como **Último instalado**
7.  Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar

![Captura de tela da janela Configurações de Build aberta no editor do Unity Plataforma Universal do Windows realçada](images/wmr-config-img-4.png)

Depois de configurar sua plataforma, você precisa permitir que o Unity saiba para criar uma [exibição](../../design/app-views.md) imersiva em vez de uma exibição 2D quando exportada.

> [!CAUTION]
> O XR herdado foi preterido no Unity 2019 e removido no Unity 2020.

1. Abra **Configurações do Player...** nas **Configurações de Build... janela** e expanda o **grupo Configurações XR**
2. Na seção **Configurações do XR,** selecione **Realidade Virtual Com** Suporte para adicionar a lista Dispositivos de Realidade Virtual
3. Definir **Formato de Profundidade** como Profundidade de **16 bits e** habilitar o **Compartilhamento de Buffer de Profundidade**
4. Definir **o modo de renderização estéreo** como instância de passagem **única**
5. Selecione **WSA Holographic Remoting Supported** se você quiser usar a remoting holográfica 

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com a seção Configurações do player realçada](images/wmr-config-img-9.png)