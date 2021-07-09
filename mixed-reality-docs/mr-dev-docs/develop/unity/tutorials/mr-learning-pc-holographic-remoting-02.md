---
title: Criar um aplicativo de Comunicação Remota Holográfica para PC
description: Conclua este curso para aprender a criar um aplicativo de PC para uma experiência de realidade misturada do seu PC para o HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, comunicação remota holográfica do PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392473"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="b3539-104">2. Como criar um aplicativo de Comunicação Remota Holográfica para PC</span><span class="sxs-lookup"><span data-stu-id="b3539-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="b3539-105">Neste tutorial, você aprenderá a criar um aplicativo para PC de Comunicação Remota Holográfica e a conectar-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo em 3D na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b3539-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="b3539-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b3539-106">Objectives</span></span>

* <span data-ttu-id="b3539-107">Configurar o Unity para Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="b3539-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="b3539-108">Saber como criar e implantar o aplicativo com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b3539-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="b3539-109">Desenvolver o aplicativo de Comunicação Remota Holográfica e conectar-se ao HoloLens</span><span class="sxs-lookup"><span data-stu-id="b3539-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="b3539-110">Como configurar as funcionalidades</span><span class="sxs-lookup"><span data-stu-id="b3539-110">Configuring the capabilities</span></span>

<span data-ttu-id="b3539-111">Na janela **Configurações do projeto**, expanda as **Configurações de publicação**, role para baixo até a seção Funcionalidades e selecione a caixa de seleção de funcionalidades mostrada abaixo, além das funcionalidades existentes.</span><span class="sxs-lookup"><span data-stu-id="b3539-111">In the **Project Settings** window, expand the **Publishing Settings**, scroll down to the Capabilities section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="b3539-112">Servidor Cliente da Internet</span><span class="sxs-lookup"><span data-stu-id="b3539-112">Internet Clint server</span></span>
* <span data-ttu-id="b3539-113">Servidor Cliente de Redes Privadas</span><span class="sxs-lookup"><span data-stu-id="b3539-113">Private Network Client Server</span></span>

![habilitando recursos](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a><span data-ttu-id="b3539-115">Criar o aplicativo para PC</span><span class="sxs-lookup"><span data-stu-id="b3539-115">Build your application to PC</span></span>

<span data-ttu-id="b3539-116">O seu aplicativo de Comunicação Remota Holográfica agora está pronto para ser criado no PC.</span><span class="sxs-lookup"><span data-stu-id="b3539-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="b3539-117">Siga as etapas abaixo e faça estas alterações para criar esse aplicativo no seu PC.</span><span class="sxs-lookup"><span data-stu-id="b3539-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="b3539-118">Como testar o aplicativo remoto de Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="b3539-118">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="b3539-119">Para conectar o seu aplicativo para PC ao seu HoloLens 2, siga o processo abaixo:</span><span class="sxs-lookup"><span data-stu-id="b3539-119">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="b3539-120">1. Instale o aplicativo de Player de Comunicação Remota no dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b3539-120">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="b3539-121">No seu HoloLens 2, visite a Loja de aplicativos e pesquise por "**Player de Comunicação Remota**".</span><span class="sxs-lookup"><span data-stu-id="b3539-121">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="b3539-122">Selecione o aplicativo **Player de Comunicação Remota**.</span><span class="sxs-lookup"><span data-stu-id="b3539-122">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="b3539-123">Toque em **Instalar** para baixar e instalar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3539-123">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="b3539-124">2. Conectar o aplicativo de Comunicação Remota Holográfica para PC ao Player de Comunicação Remota</span><span class="sxs-lookup"><span data-stu-id="b3539-124">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="b3539-125">Inicie o **Player de Comunicação Remota** no seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b3539-125">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="b3539-126">Anote o **endereço IP** do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b3539-126">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="b3539-127">Ele será exibido como um holograma pelo **Player de Comunicação Remota** assim que for iniciado.</span><span class="sxs-lookup"><span data-stu-id="b3539-127">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="b3539-128">Abra um aplicativo de Comunicação Remota Holográfica para PC no seu PC.</span><span class="sxs-lookup"><span data-stu-id="b3539-128">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="b3539-129">Depois que o aplicativo for iniciado, insira o **endereço IP** e clique no botão **Conectar** para se conectar.</span><span class="sxs-lookup"><span data-stu-id="b3539-129">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b3539-130">Parabéns</span><span class="sxs-lookup"><span data-stu-id="b3539-130">Congratulations</span></span>

<span data-ttu-id="b3539-131">Neste tutorial, você aprendeu como criar um aplicativo remoto para PC de Comunicação Remota Holográfica e a conectar-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo em 3D na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b3539-131">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="b3539-132">Depois que o HoloLens estiver conectado ao aplicativo de Comunicação Remota Holográfica para PC, você deverá ver a transmissão da experiência de realidade misturada no seu dispositivo de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b3539-132">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
