---
title: Janela de build
description: Documentação sobre como usar a janela de build no MRTK para Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, build, janela de build, ferramentas
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176155"
---
# <a name="build-window"></a>Janela de build
![Criar & fluxo de implantação](images/MRTK_BuildWindow0.png)

A janela de build do MRTK facilita a com build & implantar seus MRTK-Unity projetos. Com um único clique de botão, você pode criar um projeto do Unity e gerar Visual Studio solução(. SLN), pacote do aplicativo UWP(. APPX) e instale o pacote do aplicativo no dispositivo. 


## <a name="unity-build-options"></a>Opções de build do Unity
![Janela de build – Opções de build do Unity 1](images/MRTK_BuildWindow1.png)

Essas cenas são do build do Unity Configurações. Você pode alterar o tipo de dispositivo de destino usando o menu suspenso.

## <a name="appx-build-options"></a>Opções de build do Appx
![Janela de build – Opções de build do Appx 2](images/MRTK_BuildWindow2.png)

Essa guia mostra a configuração da solução Visual Studio configuração. Para habilitar HoloLens funcionalidade de entrada de acompanhamento ocular do 2, marque a **opção Funcionalidade de Entrada de** Olhar. 

Você pode atribuir o arquivo .glb no campo Modelo do Launcher de Aplicativo **3D** para o ícone personalizado do launcher de aplicativo 3D. Confira [Diretrizes de design do launcher de aplicativo 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para obter mais informações.

Por padrão, **o Incremento Automático** é verificado nas Opções de Versão. As versões do AppX serão incrementadas automaticamente.


## <a name="deploy-options"></a>Opções de implantação
![Janela build – Opções de implantação 3](images/MRTK_BuildWindow3.png)

Nessa guia, você pode se conectar ao dispositivo inserindo nome de usuário e senha para o Portal de Dispositivos. 

Na parte inferior da página, você pode encontrar a lista dos pacotes de aplicativos que foram criados. 

