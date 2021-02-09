---
title: Adicionar um modo offline para tradução de fala em texto local
description: Conclua este curso para saber como adicionar o modo offline para a conversão local de fala em texto em aplicativos de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, reconhecimento de fala, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 2e7a48dc4bb64eb177e6fa290f4918345c3d642f
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590148"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="4e2a0-104">2. Adicionar um modo offline para tradução de fala em texto local</span><span class="sxs-lookup"><span data-stu-id="4e2a0-104">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="4e2a0-105">Neste tutorial, você adicionará a capacidade de executar comandos usando o reconhecimento de fala do Azure, que permitirá que você faça algo com base na palavra ou na frase que você definir.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="4e2a0-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4e2a0-106">Objectives</span></span>

* <span data-ttu-id="4e2a0-107">Saiba como o reconhecimento de fala do Azure pode ser usado para executar comandos</span><span class="sxs-lookup"><span data-stu-id="4e2a0-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="4e2a0-108">Instruções</span><span class="sxs-lookup"><span data-stu-id="4e2a0-108">Instructions</span></span>

<span data-ttu-id="4e2a0-109">Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Palavra de Despertar do Lunarcom (Script)** ao objeto Lunarcom e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4e2a0-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="4e2a0-110">No campo **Palavra de Despertar**, insira uma frase adequada, por exemplo, _Ativar o terminal_.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="4e2a0-111">No campo **Palavra de Ignorar**, insira uma frase adequada, por exemplo, _Ignorar o terminal_.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Editor do Unity com o componente de script Reconhecedor de Palavra de Despertar do Lunarcom realçado](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4e2a0-113">O componente Reconhecedor de Palavra de Despertar do Lunarcom (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="4e2a0-114">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="4e2a0-115">Se agora você inserir o modo de jogo, como no tutorial anterior, o painel do terminal será habilitado por padrão, mas você poderá desabilitá-lo dizendo a Palavra de Ignorar, **Ignorar terminal**:</span><span class="sxs-lookup"><span data-stu-id="4e2a0-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![Editor do Unity no modo de reprodução com o recurso de reconhecimento de fala em uso](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="4e2a0-117">E habilitá-la novamente dizendo a Palavra de Despertar, **Ativar terminal**:</span><span class="sxs-lookup"><span data-stu-id="4e2a0-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![Editor do Unity no modo de reprodução com terminal ativo](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="4e2a0-119">O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="4e2a0-120">Se você prever que frequentemente não poderá se conectar ao Azure, também poderá implementar comandos de fala usando o MRTK de acordo com as instruções [Usar comandos de fala](mr-learning-base-09.md).</span><span class="sxs-lookup"><span data-stu-id="4e2a0-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4e2a0-121">Parabéns</span><span class="sxs-lookup"><span data-stu-id="4e2a0-121">Congratulations</span></span>

<span data-ttu-id="4e2a0-122">Você implementou comandos de fala da plataforma Azure.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="4e2a0-123">Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="4e2a0-124">No próximo tutorial, você aprenderá a traduzir a fala usando a Tradução de Fala do Azure.</span><span class="sxs-lookup"><span data-stu-id="4e2a0-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4e2a0-125">Próximo tutorial: 3. Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure</span><span class="sxs-lookup"><span data-stu-id="4e2a0-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
