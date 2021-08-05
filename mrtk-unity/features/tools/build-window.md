---
title: Janela de build
description: Documentação sobre o uso da janela de compilação no MRTK para Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, compilação, janela de compilação, ferramentas
ms.openlocfilehash: d01fefd09337e2639388a43d94bd8beb93716e3ef7f12a9c924b5755fb594447
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211368"
---
# <a name="build-window"></a>Janela de build
![Criar & fluxo de implantação](images/MRTK_BuildWindow0.png)

A janela de Build do MRTK facilita a criação de & implantar seus projetos de MRTK-Unity. com um único clique de botão, você pode criar um projeto do Unity e gerar Visual Studio solução (. SLN), pacote de aplicativo UWP (. APPX) e instale o pacote do aplicativo no dispositivo. 


## <a name="unity-build-options"></a>Opções de Build do Unity
![Compilar janela-Opções de Build do Unity 1](images/MRTK_BuildWindow1.png)

esses bastidores são da Configurações de Build do Unity. Você pode alterar o tipo de dispositivo de destino usando o menu suspenso.

## <a name="appx-build-options"></a>Opções de Build do Appx
![Janela de compilação-opções de Build do AppX 2](images/MRTK_BuildWindow2.png)

essa guia mostra a configuração para a solução de Visual Studio. para habilitar a funcionalidade de entrada de controle de olho do HoloLens 2, marque a opção de **recurso de entrada olhar** . 

Você pode atribuir o arquivo. glb no campo **modelo do iniciador de aplicativo 3D** para o ícone de inicializador de aplicativo 3D personalizado. Consulte a [diretriz de design do iniciador de aplicativo 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para obter mais informações.

Por padrão, o **incremento automático** é verificado nas opções de controle de versão. As versões do AppX serão incrementadas automaticamente.


## <a name="deploy-options"></a>Opções de implantação
![Janela de compilação – opções de implantação 3](images/MRTK_BuildWindow3.png)

Nessa guia, você pode se conectar ao dispositivo digitando o nome de usuário e a senha para o portal do dispositivo. 

Na parte inferior da página, você pode encontrar a lista de pacotes de aplicativos que foram criados. 

