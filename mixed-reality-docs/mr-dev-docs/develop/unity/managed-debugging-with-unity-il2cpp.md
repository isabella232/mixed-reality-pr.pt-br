---
title: Depuração gerenciada com o Unity
description: Este artigo aborda como executar um depurador gerenciado em seu projeto UWP do Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, depuração, il2cpp, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547083"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="c18ee-104">Depuração gerenciada com o Unity</span><span class="sxs-lookup"><span data-stu-id="c18ee-104">Managed debugging with Unity</span></span>

<span data-ttu-id="c18ee-105">Siga estas etapas para anexar um depurador gerenciado ao build UWP do Unity IL2CPP para HoloLens e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c18ee-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="c18ee-106">Você precisará estar em uma rede que dá suporte a [multicast.](https://en.wikipedia.org/wiki/Multicast)</span><span class="sxs-lookup"><span data-stu-id="c18ee-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="c18ee-107">Acesse **Funcionalidades de Configurações de Publicação UWP** e verifique **InternetClientServer** e **PrivateNetworkClientServer:**</span><span class="sxs-lookup"><span data-stu-id="c18ee-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funcionalidades de configurações de publicação da UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="c18ee-109">De acordo com as configurações de build da UWP do Unity:</span><span class="sxs-lookup"><span data-stu-id="c18ee-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="c18ee-110">Build de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="c18ee-110">Development Build</span></span>
    - <span data-ttu-id="c18ee-111">Depuração de scripts</span><span class="sxs-lookup"><span data-stu-id="c18ee-111">Script Debugging</span></span>
    - <span data-ttu-id="c18ee-112">Aguardar o Depurador Gerenciado (opcional)</span><span class="sxs-lookup"><span data-stu-id="c18ee-112">Wait for Managed Debugger (optional)</span></span>

    ![Configurações de build da UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="c18ee-114">Criar no Unity.</span><span class="sxs-lookup"><span data-stu-id="c18ee-114">Build in Unity.</span></span>
5. <span data-ttu-id="c18ee-115">Crie e implante da solução Visual Studio para seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c18ee-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="c18ee-116">Você deve criar com as **configurações de Depuração** **ou** Versão.</span><span class="sxs-lookup"><span data-stu-id="c18ee-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="c18ee-117">A **configuração** Mestre desabilita o profiler do Unity e pode impedir a depuração ideal.</span><span class="sxs-lookup"><span data-stu-id="c18ee-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="c18ee-118">Opcionalmente, verifique **Internet (Servidor & Cliente)** e Redes Privadas **(Cliente & Server)** na lista de funcionalidades em Package.appxmanifest na solução.</span><span class="sxs-lookup"><span data-stu-id="c18ee-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="c18ee-119">Certifique-se de que seu dispositivo esteja conectado à mesma rede que o computador e inicie o aplicativo em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c18ee-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="c18ee-120">Certifique-se de que **o dispositivo não esteja** conectado ao computador via USB.</span><span class="sxs-lookup"><span data-stu-id="c18ee-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="c18ee-121">Clique duas vezes em um de seus scripts no Unity e vá para a Visual Studio que é aberta para exibir e editar.</span><span class="sxs-lookup"><span data-stu-id="c18ee-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="c18ee-122">Depurar -> Anexar Depurador do Unity.</span><span class="sxs-lookup"><span data-stu-id="c18ee-122">Debug -> Attach Unity Debugger.</span></span>

    ![Anexar o depurador do Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="c18ee-124">Selecione seu dispositivo na lista e clique em "OK" para anexar.</span><span class="sxs-lookup"><span data-stu-id="c18ee-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
