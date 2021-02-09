---
title: Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure
description: Neste curso, você aprenderá a adicionar a tradução de fala dos Serviços Cognitivos do Azure em aplicativos de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, reconhecimento de fala, Windows 10, tradução de fala
ms.localizationpriority: high
ms.openlocfilehash: bcc966b63f4c3e5bb9e6d6a38dc7f0312b288402
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590138"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="a0fb9-104">3. Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure</span><span class="sxs-lookup"><span data-stu-id="a0fb9-104">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="a0fb9-105">Neste tutorial, você adicionará a tradução de fala ao seu projeto, o que permitirá que você traduza e transcreva sua fala em três idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="a0fb9-105">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="a0fb9-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a0fb9-106">Objectives</span></span>

* <span data-ttu-id="a0fb9-107">Saiba como integrar a Tradução de Fala do Azure</span><span class="sxs-lookup"><span data-stu-id="a0fb9-107">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="a0fb9-108">Instruções</span><span class="sxs-lookup"><span data-stu-id="a0fb9-108">Instructions</span></span>

<span data-ttu-id="a0fb9-109">Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Tradução do Lunarcom (Script)** ao objeto Lunarcom e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a0fb9-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="a0fb9-110">Altere o **Idioma de Destino** para um idioma de sua escolha, por exemplo, _Alemão_</span><span class="sxs-lookup"><span data-stu-id="a0fb9-110">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a0fb9-112">O componente Reconhecedor de Tradução do Lunarcom (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a0fb9-112">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a0fb9-113">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="a0fb9-113">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="a0fb9-114">Se agora você entrar no modo de Jogo, poderá testar a tradução de fala primeiro pressionando o botão de satélite.</span><span class="sxs-lookup"><span data-stu-id="a0fb9-114">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="a0fb9-115">Em seguida, supondo que o computador tenha um microfone, quando você disser algo, sua fala será traduzida para o idioma escolhido e transcrita no painel do terminal:</span><span class="sxs-lookup"><span data-stu-id="a0fb9-115">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="a0fb9-117">O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="a0fb9-117">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a0fb9-118">Parabéns</span><span class="sxs-lookup"><span data-stu-id="a0fb9-118">Congratulations</span></span>

<span data-ttu-id="a0fb9-119">Agora, seu projeto pode traduzir com êxito as palavras que você fala em vários idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="a0fb9-119">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="a0fb9-120">Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="a0fb9-120">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0fb9-121">Próximo tutorial: 4. Configurar a intenção e o reconhecimento vocal natural</span><span class="sxs-lookup"><span data-stu-id="a0fb9-121">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
