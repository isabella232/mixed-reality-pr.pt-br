---
title: Introdução aos Tutoriais das Âncoras Espaciais do Azure
description: Conclua este curso para aprender a implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, ios, android, Windows 10, ARCore, macOS, Suporte de Build do Android, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6ef488dec38a918e0a3707b06644002a51c7d5e5
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590688"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="15735-104">1. Introdução aos Tutoriais das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="15735-104">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

<span data-ttu-id="15735-105">Bem-vindo(a) aos tutoriais de Âncoras Espaciais do Azure!</span><span class="sxs-lookup"><span data-stu-id="15735-105">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="15735-106">Nesta série de tutoriais, você aprenderá os conceitos básicos de <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">ASA</a> (Âncoras Espaciais do Azure) e como ancorar uma experiência de realidade misturada completa no mundo real.</span><span class="sxs-lookup"><span data-stu-id="15735-106">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="15735-107">Você também aprenderá a implantar o projeto no Android e no iOS.</span><span class="sxs-lookup"><span data-stu-id="15735-107">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="15735-108">Tutoriais desta série:</span><span class="sxs-lookup"><span data-stu-id="15735-108">Tutorials in this series:</span></span>

1. <span data-ttu-id="15735-109">[Introdução](mr-learning-asa-01.md) (Você já está aqui)</span><span class="sxs-lookup"><span data-stu-id="15735-109">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="15735-110">Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="15735-110">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="15735-111">Salvar, recuperar e compartilhar Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="15735-111">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="15735-112">Exibir os comentários da Âncora Espacial do Azure</span><span class="sxs-lookup"><span data-stu-id="15735-112">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="15735-113">Âncoras Espaciais do Azure para Android e o iOS</span><span class="sxs-lookup"><span data-stu-id="15735-113">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="15735-114">Objetivos</span><span class="sxs-lookup"><span data-stu-id="15735-114">Objectives</span></span>

* <span data-ttu-id="15735-115">Saber como criar âncoras espaciais e buscá-las no Azure</span><span class="sxs-lookup"><span data-stu-id="15735-115">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="15735-116">Saber como obter o alinhamento espacial entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="15735-116">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="15735-117">Saber como obter alinhamento espacial entre vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="15735-117">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="15735-118">Saber como preparar, compilar e implantar seu projeto no Android e iOS</span><span class="sxs-lookup"><span data-stu-id="15735-118">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="15735-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="15735-119">Prerequisites</span></span>

* <span data-ttu-id="15735-120">Um computador com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="15735-120">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="15735-121">SDK do Windows 10 10.0.18362.0 ou versão posterior</span><span class="sxs-lookup"><span data-stu-id="15735-121">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="15735-122">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="15735-122">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="15735-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019 LTS instalado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="15735-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="15735-124">Conclua a seção [Criar um recurso de Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Início Rápido: Criar um aplicativo HoloLens do Unity que usa as Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="15735-124">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="15735-125">Ter concluído a série de [Tutoriais de introdução](mr-learning-base-01.md) ou ter alguma experiência anterior básica com o Unity e o MRTK</span><span class="sxs-lookup"><span data-stu-id="15735-125">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="15735-126">Se você pretende implantar no Android, bem como no HoloLens</span><span class="sxs-lookup"><span data-stu-id="15735-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="15735-127">Um <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">desenvolvedor habilitado</a> e um dispositivo Android <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">com capacidade para ARCore</a> com conexão USB para o seu computador com Windows ou macOS</span><span class="sxs-lookup"><span data-stu-id="15735-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="15735-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019 LTS instalado e o módulo de Suporte de Build do Android adicionado</span><span class="sxs-lookup"><span data-stu-id="15735-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="15735-129">Se você pretende implantar no iOS, bem como no HoloLens</span><span class="sxs-lookup"><span data-stu-id="15735-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="15735-130">Um computador macOS com a versão mais recente do <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e do <a href="https://cocoapods.org" target="_blank">CocoaPods</a> instaladas</span><span class="sxs-lookup"><span data-stu-id="15735-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="15735-131">Um dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatível com ARKit</a> com conexão USB para seu computador macOS</span><span class="sxs-lookup"><span data-stu-id="15735-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="15735-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019 LTS instalado e o módulo de Suporte de Build do iOS adicionado</span><span class="sxs-lookup"><span data-stu-id="15735-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="15735-133">A versão recomendada do Kit de Ferramentas de Realidade Misturada para esta série de tutoriais é o MRTK 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="15735-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.5.3.</span></span>

> [!CAUTION]
> <span data-ttu-id="15735-134">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019 LTS. Isso substitui os requisitos de versão do Unity indicados nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="15735-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="15735-135">Próximo tutorial: 2. Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="15735-135">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
