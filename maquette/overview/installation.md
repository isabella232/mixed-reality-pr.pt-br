---
title: Instalando o maquette
description: Saiba como instalar e configurar o maquette no VSCode.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realidade mista do Windows, maquette, protótipoing, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935288"
---
# <a name="installing-maquette"></a>Instalando o maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![Instalação do MaquetteScript de logotipo ](../images/MaquetteIcon.png)

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
O desenvolvimento de MaquetteScript é feito principalmente dentro do VSCode. O MaquetteScript pode ser executado a partir de um script contido em `.mqjs` arquivos e também por meio de uma interface de extensão VSCode especial. A integração entre VSCode e maquette para habilitar a interface de extensão é realizada com uma extensão MaquetteScript VSCode.

## <a name="installing-the-vscode-extension"></a>Instalando a extensão VSCode

* Baixe e instale o [VSCode](https://code.visualstudio.com). 

A extensão maquette JavaScript está na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).

* Execute o [procedimento de instalação para a extensão](vscode:extension/ms-maquette.vscode-maquette-javascript).

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Habilitando scripts

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

Para tornar o script acessível durante o pré-lançamento:

* Coloque um arquivo com o nome `scripting.enabled` no diretório de documentos dos usuários para maquette em: `~/Documents/Maquette/Settings` .

Após a instalação, o script será desabilitado por padrão por motivos de segurança.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Para habilitar a execução do script, ative-o na guia principal da janela complementar ou no arquivo de configurações do JSON.

![Habilitando scripts no VS Code](images/IntroductionEnableScripting.png)


