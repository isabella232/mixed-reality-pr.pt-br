---
title: Tutoriais de Âncoras Espaciais do Azure – 1. Introdução aos Tutoriais das Âncoras Espaciais do Azure
description: Conclua este curso para aprender a implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, ios, android, Windows 10, ARCore, macOS, Suporte de Build do Android, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 005bbf3f9ecb7ed7f15f78d4042b4090f00edca7
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679395"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="f56c4-105">1. Introdução aos Tutoriais das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="f56c4-105">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

## <a name="overview"></a><span data-ttu-id="f56c4-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f56c4-106">Overview</span></span>

<span data-ttu-id="f56c4-107">Bem-vindo(a) aos tutoriais de Âncoras Espaciais do Azure!</span><span class="sxs-lookup"><span data-stu-id="f56c4-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="f56c4-108">Nesta série de tutoriais, você aprenderá os conceitos básicos de <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">ASA</a> (Âncoras Espaciais do Azure) e como ancorar uma experiência de realidade misturada completa no mundo real.</span><span class="sxs-lookup"><span data-stu-id="f56c4-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="f56c4-109">Você também aprenderá a implantar o projeto no Android e no iOS.</span><span class="sxs-lookup"><span data-stu-id="f56c4-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="f56c4-110">Tutoriais desta série:</span><span class="sxs-lookup"><span data-stu-id="f56c4-110">Tutorials in this series:</span></span>

1. <span data-ttu-id="f56c4-111">[Introdução](mr-learning-asa-01.md) (Você já está aqui)</span><span class="sxs-lookup"><span data-stu-id="f56c4-111">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="f56c4-112">Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="f56c4-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="f56c4-113">Salvar, recuperar e compartilhar Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="f56c4-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="f56c4-114">Exibir os comentários da Âncora Espacial do Azure</span><span class="sxs-lookup"><span data-stu-id="f56c4-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="f56c4-115">Âncoras Espaciais do Azure para Android e o iOS</span><span class="sxs-lookup"><span data-stu-id="f56c4-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="f56c4-116">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f56c4-116">Objectives</span></span>

* <span data-ttu-id="f56c4-117">Saber como criar âncoras espaciais e buscá-las no Azure</span><span class="sxs-lookup"><span data-stu-id="f56c4-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="f56c4-118">Saber como obter o alinhamento espacial entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f56c4-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="f56c4-119">Saber como obter alinhamento espacial entre vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="f56c4-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="f56c4-120">Saber como preparar, compilar e implantar seu projeto no Android e iOS</span><span class="sxs-lookup"><span data-stu-id="f56c4-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f56c4-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f56c4-121">Prerequisites</span></span>

* <span data-ttu-id="f56c4-122">Um computador com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="f56c4-122">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="f56c4-123">SDK do Windows 10 10.0.18362.0 ou versão posterior</span><span class="sxs-lookup"><span data-stu-id="f56c4-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="f56c4-124">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="f56c4-124">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="f56c4-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="f56c4-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="f56c4-126">Conclua a seção [Criar um recurso de Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Início Rápido: Criar um aplicativo HoloLens do Unity que usa as Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="f56c4-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="f56c4-127">Ter concluído a série de [Tutoriais de introdução](mr-learning-base-01.md) ou ter alguma experiência anterior básica com o Unity e o MRTK</span><span class="sxs-lookup"><span data-stu-id="f56c4-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="f56c4-128">Se você pretende implantar no Android, bem como no HoloLens</span><span class="sxs-lookup"><span data-stu-id="f56c4-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="f56c4-129">Um <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">desenvolvedor habilitado</a> e um dispositivo Android <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">com capacidade para ARCore</a> com conexão USB para o seu computador com Windows ou macOS</span><span class="sxs-lookup"><span data-stu-id="f56c4-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="f56c4-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build do Android adicionado</span><span class="sxs-lookup"><span data-stu-id="f56c4-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="f56c4-131">Se você pretende implantar no iOS, bem como no HoloLens</span><span class="sxs-lookup"><span data-stu-id="f56c4-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="f56c4-132">Um computador macOS com a versão mais recente do <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e do <a href="https://cocoapods.org" target="_blank">CocoaPods</a> instaladas</span><span class="sxs-lookup"><span data-stu-id="f56c4-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="f56c4-133">Um dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatível com ARKit</a> com conexão USB para seu computador macOS</span><span class="sxs-lookup"><span data-stu-id="f56c4-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="f56c4-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build do iOS adicionado</span><span class="sxs-lookup"><span data-stu-id="f56c4-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="f56c4-135">A versão recomendada do Kit de Ferramentas de Realidade Misturada para esta série de tutoriais é o MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="f56c4-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="f56c4-136">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="f56c4-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="f56c4-137">Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="f56c4-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f56c4-138">Próximo tutorial: 2. Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="f56c4-138">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
