---
title: Janela de build do MRTK
description: Documentação sobre como usar a janela de build no MRTK para Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, build, janela de build, ferramentas
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196838"
---
# <a name="build-window"></a><span data-ttu-id="58060-104">Janela de build</span><span class="sxs-lookup"><span data-stu-id="58060-104">Build window</span></span>
![Criar & fluxo de implantação](images/MRTK_BuildWindow0.png)

<span data-ttu-id="58060-106">A janela de build do MRTK facilita a com build & implantar seus MRTK-Unity projetos.</span><span class="sxs-lookup"><span data-stu-id="58060-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="58060-107">Com um único clique de botão, você pode criar um projeto do Unity e gerar Visual Studio solução(. SLN), pacote do aplicativo UWP(. APPX) e instale o pacote do aplicativo no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="58060-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="58060-108">Opções de build do Unity</span><span class="sxs-lookup"><span data-stu-id="58060-108">Unity Build Options</span></span>
![Janela de build – Opções de build do Unity 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="58060-110">Essas cenas são das Configurações de Build do Unity.</span><span class="sxs-lookup"><span data-stu-id="58060-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="58060-111">Você pode alterar o tipo de dispositivo de destino usando o menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="58060-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="58060-112">Opções de build do Appx</span><span class="sxs-lookup"><span data-stu-id="58060-112">Appx Build Options</span></span>
![Janela de build – Opções de build do Appx 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="58060-114">Essa guia mostra a configuração da solução Visual Studio configuração.</span><span class="sxs-lookup"><span data-stu-id="58060-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="58060-115">Para habilitar a funcionalidade de entrada de acompanhamento ocular do HoloLens 2, marque a opção Funcionalidade de **Entrada de** Olhar.</span><span class="sxs-lookup"><span data-stu-id="58060-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="58060-116">Você pode atribuir o arquivo .glb no campo Modelo do Launcher de Aplicativo **3D** para o ícone personalizado do launcher de aplicativo 3D.</span><span class="sxs-lookup"><span data-stu-id="58060-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="58060-117">Confira [Diretrizes de design do launcher de aplicativo 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="58060-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="58060-118">Por padrão, **o Incremento Automático** é verificado nas Opções de Versão.</span><span class="sxs-lookup"><span data-stu-id="58060-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="58060-119">As versões do AppX serão incrementadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="58060-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="58060-120">Opções de implantação</span><span class="sxs-lookup"><span data-stu-id="58060-120">Deploy Options</span></span>
![Janela build – Opções de implantação 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="58060-122">Nessa guia, você pode se conectar ao dispositivo digitando o nome de usuário e a senha para o portal do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="58060-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="58060-123">Na parte inferior da página, você pode encontrar a lista de pacotes de aplicativos que foram criados.</span><span class="sxs-lookup"><span data-stu-id="58060-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

