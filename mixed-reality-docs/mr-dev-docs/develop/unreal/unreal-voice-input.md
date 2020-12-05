---
title: Entrada de voz
description: Tutorial sobre como configurar e usar a entrada de voz no HoloLens 2 e no mecanismo inreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, inreal, Engine 4, UE4, HoloLens 2, voz, entrada de voz, reconhecimento de fala, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 504a2d978e3c9bc698e8edd11ea8a4d6be13795a
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609747"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="7c473-104">Entrada de voz em não real</span><span class="sxs-lookup"><span data-stu-id="7c473-104">Voice Input in Unreal</span></span>

<span data-ttu-id="7c473-105">A entrada de voz em forma inreal permite que você interaja com um holograma sem precisar usar gestos de mão e só tem suporte para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7c473-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="7c473-106">A entrada de voz no HoloLens 2 é alimentada pelo mesmo mecanismo que dá suporte à fala em todos os outros aplicativos universais do Windows, mas o uso não real usa um mecanismo mais limitado para processar a entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="7c473-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="7c473-107">Isso limita os recursos de entrada de voz em mapeamentos de fala inreais para predefinidos, que são abordados nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c473-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="7c473-108">Habilitando o reconhecimento de fala</span><span class="sxs-lookup"><span data-stu-id="7c473-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="7c473-109">Para habilitar o reconhecimento de fala no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="7c473-109">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="7c473-110">Selecione **configurações do projeto > plataforma > recursos de > do HoloLens** e habilite o **microfone**.</span><span class="sxs-lookup"><span data-stu-id="7c473-110">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="7c473-111">Habilitado o reconhecimento de fala em **configurações > privacidade > fala** e selecione **Inglês**.</span><span class="sxs-lookup"><span data-stu-id="7c473-111">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="7c473-112">O reconhecimento de fala sempre funciona no idioma de exibição do Windows configurado no aplicativo **configurações** .</span><span class="sxs-lookup"><span data-stu-id="7c473-112">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="7c473-113">É recomendável que você também habilite o **reconhecimento de fala online** para a melhor qualidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="7c473-113">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Configurações de reconhecimento de fala do Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="7c473-115">Uma caixa de diálogo será exibida quando o aplicativo começar a perguntar se você deseja habilitar o microfone.</span><span class="sxs-lookup"><span data-stu-id="7c473-115">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="7c473-116">Selecionar **Sim** inicia a entrada de voz no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c473-116">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="7c473-117">A entrada de voz não requer nenhuma API especial do Windows Mixed Reality; Ele foi criado na API de mapeamento de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) do mecanismo 4 inreal existente.</span><span class="sxs-lookup"><span data-stu-id="7c473-117">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="7c473-118">Adicionando mapeamentos de fala</span><span class="sxs-lookup"><span data-stu-id="7c473-118">Adding Speech Mappings</span></span>

<span data-ttu-id="7c473-119">Conectar a fala a ação é uma etapa importante ao usar a entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="7c473-119">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="7c473-120">Esses mapeamentos monitoram o aplicativo para palavras-chave de fala que um usuário pode dizer e, em seguida, dispara uma ação vinculada.</span><span class="sxs-lookup"><span data-stu-id="7c473-120">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="7c473-121">Você pode encontrar mapeamentos de fala de:</span><span class="sxs-lookup"><span data-stu-id="7c473-121">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="7c473-122">Selecione **editar > configurações do projeto**, role até a seção **mecanismo** e clique em **entrada**.</span><span class="sxs-lookup"><span data-stu-id="7c473-122">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="7c473-123">Para adicionar um novo mapeamento de fala para um comando de salto:</span><span class="sxs-lookup"><span data-stu-id="7c473-123">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="7c473-124">Selecione o **+** ícone ao lado de **elementos da matriz** e preencha os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7c473-124">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="7c473-125">**jumpWord** para o **nome da ação**</span><span class="sxs-lookup"><span data-stu-id="7c473-125">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="7c473-126">**ir** para **palavra-chave de fala**</span><span class="sxs-lookup"><span data-stu-id="7c473-126">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="7c473-127">Qualquer palavra (s) em inglês ou sentenças curtas podem ser usadas como uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="7c473-127">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Configurações de entrada do mecanismo UE4](images/unreal/engine-input.png)

<span data-ttu-id="7c473-129">Os mapeamentos de fala podem ser usados como componentes de entrada como mapeamentos de ação ou de eixo ou como nós de plano gráfico no grafo de eventos.</span><span class="sxs-lookup"><span data-stu-id="7c473-129">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="7c473-130">Por exemplo, você pode vincular o comando de salto para imprimir dois logs diferentes dependendo de quando a palavra for falada:</span><span class="sxs-lookup"><span data-stu-id="7c473-130">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="7c473-131">Clique duas vezes em um plano gráfico para abri-lo no **grafo de eventos**.</span><span class="sxs-lookup"><span data-stu-id="7c473-131">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="7c473-132">**Clique com o botão direito do mouse** e pesquise pelo **nome da ação** do seu mapeamento de fala (neste caso, **jumpWord**) e, em seguida, pressione **Enter** para adicionar um nó de **ação de entrada** ao grafo.</span><span class="sxs-lookup"><span data-stu-id="7c473-132">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="7c473-133">Arraste e solte o pino **pressionado** para **Imprimir** o nó da cadeia de caracteres, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="7c473-133">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="7c473-134">Você pode deixar o PIN **liberado** vazio, ele não executará nada para mapeamentos de fala.</span><span class="sxs-lookup"><span data-stu-id="7c473-134">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Ação simples para voz](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="7c473-136">Reproduza o aplicativo, digamos que o **salto** de palavras e assista ao console para imprimir os logs!</span><span class="sxs-lookup"><span data-stu-id="7c473-136">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="7c473-137">Essa é toda a configuração que você precisará para começar a adicionar entrada de voz aos seus aplicativos de HoloLens em um não real.</span><span class="sxs-lookup"><span data-stu-id="7c473-137">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="7c473-138">Você pode encontrar mais informações sobre a fala e a interatividade nos links abaixo e certifique-se de pensar sobre a experiência que está criando para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="7c473-138">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7c473-139">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="7c473-139">Next Development Checkpoint</span></span>

<span data-ttu-id="7c473-140">Se você estiver seguindo a jornada de desenvolvimento inreal que apresentamos, a próxima tarefa está explorando os recursos e as APIs da plataforma de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="7c473-140">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c473-141">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="7c473-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="7c473-142">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="7c473-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c473-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="7c473-143">See also</span></span>
* [<span data-ttu-id="7c473-144">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="7c473-144">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="7c473-145">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="7c473-145">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="7c473-146">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="7c473-146">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

