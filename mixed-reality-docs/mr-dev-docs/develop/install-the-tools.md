---
title: Instalar as ferramentas
description: Comece aqui com as versões mais atuais do Unity, do Visual Studio e de ferramentas recomendadas para o desenvolvimento do HoloLens e de VR.
author: thetuvix
ms.author: alexturn
ms.date: 01/13/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 0b952922c7723bf0e2c87ddb7fed9a896d65e833
ms.sourcegitcommit: 8c3af63fb49494f75c8ab46236fc3dd8533c1e9d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99606121"
---
# <a name="install-the-tools"></a>Instalar as ferramentas

Obtenha as ferramentas necessárias para criar aplicativos para os headsets imersivos (VR) do Microsoft HoloLens e do Windows Mixed Reality. Não há nenhum SDK separado para o desenvolvimento no Windows Mixed Reality; você usará o Visual Studio com o SDK do Windows 10.

Não tem um dispositivo de realidade misturada? Você pode instalar o [emulador do HoloLens](platform-capabilities-and-apis/using-the-hololens-emulator.md) para testar algumas funcionalidades de aplicativos de realidade misturada sem um HoloLens. Você também pode usar o [simulador do Windows Mixed Reality](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) para testar seus aplicativos de realidade misturada para headsets imersivos. 

É recomendável instalar o mecanismo de jogos Unity ou Unreal como a maneira mais fácil de começar a criar aplicativos de realidade misturada. No entanto, você também poderá criar com base no DirectX se quiser usar um mecanismo personalizado.

Se você estiver usando o Unity, poderá usar a simulação de entrada do [Kit de Ferramentas de Realidade Misturada do Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) para testar vários tipos de interações de entrada, como entrada por acompanhamento da mão e acompanhamento ocular. Para projetos do Unreal, use o [plug-in das Ferramentas de UX](https://github.com/microsoft/MixedReality-UXTools-Unreal) para testar interações comuns de entrada e recursos de experiência do usuário.

>[!TIP]
>Adicione esta página aos favoritos e acesse-a regularmente para se manter atualizado sobre a versão mais recente de cada ferramenta recomendada para o desenvolvimento de realidade misturada.

<br>

## <a name="installation-checklist"></a>Lista de verificação da instalação


| Ferramenta | Observações |
|---------|---------|
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (link de instalação manual)</a><br><br>Instale a versão mais recente do Windows 10, para que o sistema operacional do seu computador corresponda à plataforma para a qual você está compilando aplicativos de realidade misturada.  | **Instalação do Windows 10** <br> Você pode instalar a versão mais recente do Windows 10 via Windows Update nas Configurações ou criando uma mídia de instalação, usando o link na coluna à esquerda. <br><br>Veja as [notas de versão atuais](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md) para obter informações sobre os recursos mais recentes de realidade misturada disponíveis em cada versão do Windows 10. **Ative o modo de desenvolvedor no seu computador** em Configurações > Atualização e Segurança > Para Desenvolvedores. <br><br> **Observação para computadores empresariais e corporativos**<br>Se o computador for gerenciado pelo departamento de TI da sua organização, talvez seja necessário contatá-los para atualizar. <br><br> **"N" versões do Windows**<br> Headsets imersivos (VR) do Windows Mixed Reality não são compatíveis com as versões "N" do Windows. |
| ![Imagem do logotipo do Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 ou superior)** (link de instalação)</a> <br><br>Ambiente de desenvolvimento integrado (IDE) completo para Windows e muito mais. Você usará o Visual Studio para escrever o código, depurar, testar e implantar. | **Instalação do Visual Studio 2019** <br> Certifique-se de instalar as seguintes cargas de trabalho: <br><br>*● Desenvolvimento para desktop com C++*<br>*● Desenvolvimento da UWP (Plataforma Universal do Windows)*<br><br>Na carga de trabalho da UWP, certifique-se de verificar o seguinte componente opcional caso você esteja desenvolvendo para o HoloLens:<br><br>*● Conectividade do dispositivo USB*<br><br>**Observação sobre o Unity**<br>A menos que você esteja tentando instalar intencionalmente uma versão (não LTS) mais recente do Unity para uma finalidade específica, recomendamos *não* instalar a carga de trabalho do Unity como parte da instalação do Visual Studio. Em vez disso, instale o fluxo **2019 LTS do Unity**, conforme indicado abaixo.<br><br>**Problemas conhecidos**<br>há alguns problemas conhecidos com a depuração de aplicativos de realidade misturada no Visual Studio 2019 versão 16.0.  Verifique se você atualizou o **Visual Studio 2019 para a versão 16.8 ou superior**. |
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**SDK do Windows 10 (10.0.18362.0)** (link de instalação manual)</a> <br><br>Fornece os cabeçalhos, bibliotecas, metadados e ferramentas mais recentes para a compilação de aplicativos do Windows 10 no HoloLens 2. | **Para criar aplicativos do HoloLens 2, você precisará instalar o SDK do Windows, build 18362 ou posterior.**<br> <br> Se você estiver desenvolvendo aplicativos somente para headsets do Windows Mixed Reality de área de trabalho ou HoloLens (1ª geração), poderá usar o SDK do Windows instalado pelo Visual Studio 2017. |
| ![Logotipo do Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2152389" target="_blank">**Emulador do HoloLens 2 (Windows Holographic, versão 20H2, atualização de janeiro de 2021)** (Link de instalação: 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador do HoloLens (1ª geração)** (link de instalação: 10.0.17763.134)</a> <br><br>O emulador permite executar aplicativos em uma imagem de máquina virtual do HoloLens sem um HoloLens físico.<br> <br> | Veja [Usando o emulador do HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) para obter mais informações sobre como começar a usar o emulador.<br> <br> **O sistema deve ser compatível com Hyper-V** para a instalação do emulador ser bem-sucedida. Consulte a seção de Requisitos de sistema abaixo para obter detalhes. <br> <br> **Observação sobre o Emulador do HoloLens (1ª geração)** <br>  O Visual Studio 2017 é necessário para concluir a instalação com êxito. Se você estiver instalando o emulador do HoloLens (1ª geração) com o Visual Studio 2019, desmarque os modelos do VS e [instale-os por meio do Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="choose-your-engine"></a>Escolha seu mecanismo

Agora que você tem o Windows 10, o Visual Studio e o SDK do Windows 10 prontos para uso, vamos escolher um mecanismo para a criação.

[!INCLUDE[](includes/tools-overview.md)]

