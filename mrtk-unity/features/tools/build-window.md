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
# <a name="build-window"></a><span data-ttu-id="b68b4-104">Janela de build</span><span class="sxs-lookup"><span data-stu-id="b68b4-104">Build window</span></span>
![Criar & fluxo de implantação](images/MRTK_BuildWindow0.png)

<span data-ttu-id="b68b4-106">A janela de build do MRTK facilita a com build & implantar seus MRTK-Unity projetos.</span><span class="sxs-lookup"><span data-stu-id="b68b4-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="b68b4-107">Com um único clique de botão, você pode criar um projeto do Unity e gerar Visual Studio solução(. SLN), pacote do aplicativo UWP(. APPX) e instale o pacote do aplicativo no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b68b4-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="b68b4-108">Opções de build do Unity</span><span class="sxs-lookup"><span data-stu-id="b68b4-108">Unity Build Options</span></span>
![Janela de build – Opções de build do Unity 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="b68b4-110">Essas cenas são do build do Unity Configurações.</span><span class="sxs-lookup"><span data-stu-id="b68b4-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="b68b4-111">Você pode alterar o tipo de dispositivo de destino usando o menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="b68b4-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="b68b4-112">Opções de build do Appx</span><span class="sxs-lookup"><span data-stu-id="b68b4-112">Appx Build Options</span></span>
![Janela de build – Opções de build do Appx 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="b68b4-114">Essa guia mostra a configuração da solução Visual Studio configuração.</span><span class="sxs-lookup"><span data-stu-id="b68b4-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="b68b4-115">Para habilitar HoloLens funcionalidade de entrada de acompanhamento ocular do 2, marque a **opção Funcionalidade de Entrada de** Olhar.</span><span class="sxs-lookup"><span data-stu-id="b68b4-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="b68b4-116">Você pode atribuir o arquivo .glb no campo Modelo do Launcher de Aplicativo **3D** para o ícone personalizado do launcher de aplicativo 3D.</span><span class="sxs-lookup"><span data-stu-id="b68b4-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="b68b4-117">Confira [Diretrizes de design do launcher de aplicativo 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b68b4-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="b68b4-118">Por padrão, **o Incremento Automático** é verificado nas Opções de Versão.</span><span class="sxs-lookup"><span data-stu-id="b68b4-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="b68b4-119">As versões do AppX serão incrementadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b68b4-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="b68b4-120">Opções de implantação</span><span class="sxs-lookup"><span data-stu-id="b68b4-120">Deploy Options</span></span>
![Janela build – Opções de implantação 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="b68b4-122">Nessa guia, você pode se conectar ao dispositivo inserindo nome de usuário e senha para o Portal de Dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b68b4-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="b68b4-123">Na parte inferior da página, você pode encontrar a lista dos pacotes de aplicativos que foram criados.</span><span class="sxs-lookup"><span data-stu-id="b68b4-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

