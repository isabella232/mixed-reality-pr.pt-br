---
title: Depuração gerenciada com o Unity IL2CPP
description: Este artigo aborda como executar um depurador gerenciado em seu projeto do IL2CPP UWP do Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, depuração, il2cpp, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010237"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="e09b8-104">Depuração gerenciada com o Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="e09b8-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="e09b8-105">Siga estas etapas para anexar um depurador gerenciado à sua compilação do IL2CPP UWP do Unity para o HoloLens e o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e09b8-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="e09b8-106">Você precisará estar em uma rede que dá suporte a [multicast](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="e09b8-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="e09b8-107">Vá para **configurações de publicação de UWP recursos** e verifique **InternetClientServer** e **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="e09b8-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funcionalidades de configurações de publicação do UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="e09b8-109">Defina as configurações de Build do Unity UWP:</span><span class="sxs-lookup"><span data-stu-id="e09b8-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="e09b8-110">Build de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="e09b8-110">Development Build</span></span>
    - <span data-ttu-id="e09b8-111">Depuração de scripts</span><span class="sxs-lookup"><span data-stu-id="e09b8-111">Script Debugging</span></span>
    - <span data-ttu-id="e09b8-112">Aguardar o depurador gerenciado (opcional)</span><span class="sxs-lookup"><span data-stu-id="e09b8-112">Wait for Managed Debugger (optional)</span></span>

    ![Configurações de Build do UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="e09b8-114">Compilar no Unity.</span><span class="sxs-lookup"><span data-stu-id="e09b8-114">Build in Unity.</span></span>
5. <span data-ttu-id="e09b8-115">Crie e implante a partir da solução do Visual Studio para seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e09b8-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="e09b8-116">Você deve criar com as configurações de **depuração** ou de **versão** .</span><span class="sxs-lookup"><span data-stu-id="e09b8-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="e09b8-117">A configuração **mestra** desabilita o Unity Profiler e pode impedir a depuração ideal.</span><span class="sxs-lookup"><span data-stu-id="e09b8-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="e09b8-118">Opcionalmente, verifique a **Internet (cliente & Server)** e as **redes privadas (cliente & Server)** na lista de recursos em Package. appxmanifest na solução.</span><span class="sxs-lookup"><span data-stu-id="e09b8-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="e09b8-119">Verifique se o dispositivo está conectado à mesma rede que o seu PC e inicie o aplicativo em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e09b8-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="e09b8-120">Verifique se o dispositivo **não está** conectado ao seu PC via USB.</span><span class="sxs-lookup"><span data-stu-id="e09b8-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="e09b8-121">Clique duas vezes em um dos seus scripts no Unity e vá para a solução do Visual Studio que é aberta para exibir e editar.</span><span class="sxs-lookup"><span data-stu-id="e09b8-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="e09b8-122">Debug-> anexar o depurador Unity.</span><span class="sxs-lookup"><span data-stu-id="e09b8-122">Debug -> Attach Unity Debugger.</span></span>

    ![Anexar depurador do Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="e09b8-124">Selecione seu dispositivo na lista e clique em "OK" para anexar.</span><span class="sxs-lookup"><span data-stu-id="e09b8-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
