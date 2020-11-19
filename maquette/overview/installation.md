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
# <a name="installing-maquette"></a><span data-ttu-id="2527e-104">Instalando o maquette</span><span class="sxs-lookup"><span data-stu-id="2527e-104">Installing Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text. -->
<span data-ttu-id="2527e-105">![Instalação do MaquetteScript de logotipo ](../images/MaquetteIcon.png)</span><span class="sxs-lookup"><span data-stu-id="2527e-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Installation</span></span>

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
<span data-ttu-id="2527e-106">O desenvolvimento de MaquetteScript é feito principalmente dentro do VSCode.</span><span class="sxs-lookup"><span data-stu-id="2527e-106">MaquetteScript development is primarily done within VSCode.</span></span> <span data-ttu-id="2527e-107">O MaquetteScript pode ser executado a partir de um script contido em `.mqjs` arquivos e também por meio de uma interface de extensão VSCode especial.</span><span class="sxs-lookup"><span data-stu-id="2527e-107">MaquetteScript can run from script contained in `.mqjs` files and also via a special VSCode extension interface.</span></span> <span data-ttu-id="2527e-108">A integração entre VSCode e maquette para habilitar a interface de extensão é realizada com uma extensão MaquetteScript VSCode.</span><span class="sxs-lookup"><span data-stu-id="2527e-108">Integration between VSCode and Maquette to enable the extension interface is accomplished with a MaquetteScript VSCode extension.</span></span>

## <a name="installing-the-vscode-extension"></a><span data-ttu-id="2527e-109">Instalando a extensão VSCode</span><span class="sxs-lookup"><span data-stu-id="2527e-109">Installing the VSCode Extension</span></span>

* <span data-ttu-id="2527e-110">Baixe e instale o [VSCode](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="2527e-110">Download and install [VSCode](https://code.visualstudio.com).</span></span> 

<span data-ttu-id="2527e-111">A extensão maquette JavaScript está na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="2527e-111">The Maquette javascript extension is in [the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span></span>

* <span data-ttu-id="2527e-112">Execute o [procedimento de instalação para a extensão](vscode:extension/ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="2527e-112">Run the [installation procedure for the extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span></span>

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a><span data-ttu-id="2527e-113">Habilitando scripts</span><span class="sxs-lookup"><span data-stu-id="2527e-113">Enabling Scripting</span></span>

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

<span data-ttu-id="2527e-114">Para tornar o script acessível durante o pré-lançamento:</span><span class="sxs-lookup"><span data-stu-id="2527e-114">To make scripting accessible during pre-release:</span></span>

* <span data-ttu-id="2527e-115">Coloque um arquivo com o nome `scripting.enabled` no diretório de documentos dos usuários para maquette em: `~/Documents/Maquette/Settings` .</span><span class="sxs-lookup"><span data-stu-id="2527e-115">Put a file with the name `scripting.enabled` in the Users Documents directory for Maquette in: `~/Documents/Maquette/Settings`.</span></span>

<span data-ttu-id="2527e-116">Após a instalação, o script será desabilitado por padrão por motivos de segurança.</span><span class="sxs-lookup"><span data-stu-id="2527e-116">After installation, scripting will be disabled by default for security reasons.</span></span>

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* <span data-ttu-id="2527e-117">Para habilitar a execução do script, ative-o na guia principal da janela complementar ou no arquivo de configurações do JSON.</span><span class="sxs-lookup"><span data-stu-id="2527e-117">To enable execution of script, turn it ON in the main tab of the companion window or in the json settings file.</span></span>

![Habilitando scripts no VS Code](images/IntroductionEnableScripting.png)


