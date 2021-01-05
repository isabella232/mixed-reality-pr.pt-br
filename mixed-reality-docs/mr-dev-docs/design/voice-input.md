---
title: Entrada de voz
description: A entrada de voz é uma entrada principal para o HoloLens e os headsets de imersão de realidade mista do Windows. A voz pode ser usada para comandos, ditado, Cortana e muito mais.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, voz, Cortana, fala, entrada, headset de realidade misturada, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas da realidade mista, olhar
ms.openlocfilehash: 09f99083d769be80d8c15016b3de8713eae76515
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848133"
---
# <a name="voice-input"></a><span data-ttu-id="fa503-105">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="fa503-105">Voice input</span></span>

![Entrada de voz](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="fa503-107">A voz é uma das principais formas de entrada no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fa503-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="fa503-108">Ele permite que você comando diretamente um holograma sem precisar usar [gestos de mão](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="fa503-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="fa503-109">A entrada de voz pode ser uma maneira natural de comunicar sua intenção.</span><span class="sxs-lookup"><span data-stu-id="fa503-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="fa503-110">A voz é especialmente boa na passagem de interfaces complexas, pois permite que os usuários recortem os menus aninhados com um único comando.</span><span class="sxs-lookup"><span data-stu-id="fa503-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="fa503-111">A entrada de voz é alimentada pelo [mesmo mecanismo](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que dá suporte à fala em todos os _aplicativos universais do Windows_.</span><span class="sxs-lookup"><span data-stu-id="fa503-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all _Universal Windows Apps_.</span></span> <span data-ttu-id="fa503-112">No HoloLens, o reconhecimento de fala sempre funcionará no idioma de exibição do Windows configurado nas configurações do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fa503-112">On HoloLens, speech recognition will always function in the Windows display language configured in your device Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="fa503-113">Voz e olhar</span><span class="sxs-lookup"><span data-stu-id="fa503-113">Voice and gaze</span></span>

<span data-ttu-id="fa503-114">Quando você estiver usando comandos de voz, o olhar de cabeça ou de olho é o mecanismo de direcionamento típico, seja com um cursor para "selecionar" ou para canalizar o comando para um aplicativo que você está vendo.</span><span class="sxs-lookup"><span data-stu-id="fa503-114">When you're using voice commands, head or eye gaze is the typical targeting mechanism, whether with a cursor to "select" or to channel your command to an application you're looking at.</span></span> <span data-ttu-id="fa503-115">Talvez nem seja necessário mostrar qualquer cursor olhar _("vê-lo, digamos")_.</span><span class="sxs-lookup"><span data-stu-id="fa503-115">It may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="fa503-116">Alguns comandos de voz não exigem um destino, como "ir para iniciar" ou "Ei Cortana".</span><span class="sxs-lookup"><span data-stu-id="fa503-116">Some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="fa503-117">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="fa503-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fa503-118"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="fa503-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="fa503-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="fa503-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="fa503-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="fa503-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="fa503-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="fa503-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fa503-122">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="fa503-122">Voice input</span></span></td>
        <td><span data-ttu-id="fa503-123">✔️</span><span class="sxs-lookup"><span data-stu-id="fa503-123">✔️</span></span></td>
        <td><span data-ttu-id="fa503-124">✔️</span><span class="sxs-lookup"><span data-stu-id="fa503-124">✔️</span></span></td>
        <td><span data-ttu-id="fa503-125">✔️ (com microfone)</span><span class="sxs-lookup"><span data-stu-id="fa503-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="fa503-126">O comando "Select"</span><span class="sxs-lookup"><span data-stu-id="fa503-126">The "select" command</span></span>

<span data-ttu-id="fa503-127">**HoloLens (1ª geração)**</span><span class="sxs-lookup"><span data-stu-id="fa503-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="fa503-128">Mesmo sem adicionar especificamente suporte de voz ao seu aplicativo, os usuários podem ativar os hologramas simplesmente dizendo o comando de voz do sistema "Select".</span><span class="sxs-lookup"><span data-stu-id="fa503-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="fa503-129">Isso se comporta da mesma forma que um [toque de ar](gaze-and-commit.md#composite-gestures) no HoloLens, pressionando o botão Selecionar no [clicador de HoloLens](https://docs.microsoft.com/hololens/hololens1-clicker)ou pressionando o gatilho em um [controlador de movimento de realidade mista do Windows](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="fa503-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](https://docs.microsoft.com/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="fa503-130">Você ouvirá um som e verá uma dica de ferramenta com "Select" aparecer como confirmação.</span><span class="sxs-lookup"><span data-stu-id="fa503-130">You'll hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="fa503-131">"Select" é habilitado por um algoritmo de detecção de palavra-chave de baixa energia, o que significa que você pode dizer a ele a qualquer momento com impacto mínimo na vida útil da bateria.</span><span class="sxs-lookup"><span data-stu-id="fa503-131">"Select" is enabled by a low-power keyword detection algorithm, which means you can say it anytime with minimal battery life impact.</span></span> <span data-ttu-id="fa503-132">Você pode até mesmo dizer "selecionar" com suas mãos no seu lado.</span><span class="sxs-lookup"><span data-stu-id="fa503-132">You can even say "select" with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="fa503-133">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="fa503-133">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="fa503-134">Para usar o comando de voz "Select" no HoloLens 2, primeiro você precisa abrir o cursor olhar para usar como um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="fa503-134">To use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="fa503-135">O comando para trazê-lo é fácil de lembrar, apenas digamos, "Select".</span><span class="sxs-lookup"><span data-stu-id="fa503-135">The command to bring it up is easy to remember--just say, "select".</span></span><br><br>
        <span data-ttu-id="fa503-136">Para sair do modo, use suas mãos novamente por Air tocando, abordando um botão com seus dedos ou usando o gesto do sistema.</span><span class="sxs-lookup"><span data-stu-id="fa503-136">To exit the mode, use your hands again by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br> 
        <span data-ttu-id="fa503-137">*Imagem: Diga "selecionar" para usar o comando de voz para seleção*</span><span class="sxs-lookup"><span data-stu-id="fa503-137">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Um usuário pode dizer "selecionar" para usar o comando de voz para uma seleção.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a><span data-ttu-id="fa503-139">Ei Cortana</span><span class="sxs-lookup"><span data-stu-id="fa503-139">Hey Cortana</span></span>

<span data-ttu-id="fa503-140">Você pode dizer "Ei Cortana" para abrir a Cortana a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="fa503-140">You can say "Hey Cortana" to bring up Cortana at any time.</span></span> <span data-ttu-id="fa503-141">Você não precisa esperar que ela pareça continuar perguntando sua pergunta ou dando a ela uma instrução.</span><span class="sxs-lookup"><span data-stu-id="fa503-141">You don't have to wait for her to appear to continue asking her your question or giving her an instruction.</span></span> <span data-ttu-id="fa503-142">Por exemplo, tente dizer "Ei Cortana, qual é o clima?"</span><span class="sxs-lookup"><span data-stu-id="fa503-142">For example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="fa503-143">como uma única frase.</span><span class="sxs-lookup"><span data-stu-id="fa503-143">as a single sentence.</span></span> <span data-ttu-id="fa503-144">Para obter mais informações sobre a Cortana e o que você pode fazer, pergunte a ela!</span><span class="sxs-lookup"><span data-stu-id="fa503-144">For more information about Cortana and what you can do, ask her!</span></span> <span data-ttu-id="fa503-145">Diga "Ei Cortana, o que eu posso dizer?"</span><span class="sxs-lookup"><span data-stu-id="fa503-145">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="fa503-146">e ela receberá uma lista de comandos de trabalho e sugeridos.</span><span class="sxs-lookup"><span data-stu-id="fa503-146">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="fa503-147">Se você já estiver no aplicativo Cortana, selecione o **?**</span><span class="sxs-lookup"><span data-stu-id="fa503-147">If you're already in the Cortana app, select the **?**</span></span> <span data-ttu-id="fa503-148">na barra lateral para extrair esse mesmo menu.</span><span class="sxs-lookup"><span data-stu-id="fa503-148">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="fa503-149">**Comandos específicos do HoloLens**</span><span class="sxs-lookup"><span data-stu-id="fa503-149">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="fa503-150">"O que posso falar?"</span><span class="sxs-lookup"><span data-stu-id="fa503-150">"What can I say?"</span></span>
* <span data-ttu-id="fa503-151">"Ir para o início"-em vez de [cair](system-gesture.md#bloom) para chegar ao [menu iniciar](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="fa503-151">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="fa503-152">"Iniciar <app> "</span><span class="sxs-lookup"><span data-stu-id="fa503-152">"Launch <app>"</span></span>
* <span data-ttu-id="fa503-153">"Mover <app> aqui"</span><span class="sxs-lookup"><span data-stu-id="fa503-153">"Move <app> here"</span></span>
* <span data-ttu-id="fa503-154">"Tirar uma foto"</span><span class="sxs-lookup"><span data-stu-id="fa503-154">"Take a picture"</span></span>
* <span data-ttu-id="fa503-155">"Iniciar gravação"</span><span class="sxs-lookup"><span data-stu-id="fa503-155">"Start recording"</span></span>
* <span data-ttu-id="fa503-156">"Parar gravação"</span><span class="sxs-lookup"><span data-stu-id="fa503-156">"Stop recording"</span></span>
* <span data-ttu-id="fa503-157">"Mostrar lado raio"</span><span class="sxs-lookup"><span data-stu-id="fa503-157">"Show hand ray"</span></span>
* <span data-ttu-id="fa503-158">"Ocultar mão raio"</span><span class="sxs-lookup"><span data-stu-id="fa503-158">"Hide hand ray"</span></span>
* <span data-ttu-id="fa503-159">"Aumentar o brilho"</span><span class="sxs-lookup"><span data-stu-id="fa503-159">"Increase the brightness"</span></span>
* <span data-ttu-id="fa503-160">"Diminuir o brilho"</span><span class="sxs-lookup"><span data-stu-id="fa503-160">"Decrease the brightness"</span></span>
* <span data-ttu-id="fa503-161">"Aumentar o volume"</span><span class="sxs-lookup"><span data-stu-id="fa503-161">"Increase the volume"</span></span>
* <span data-ttu-id="fa503-162">"Diminuir o volume"</span><span class="sxs-lookup"><span data-stu-id="fa503-162">"Decrease the volume"</span></span>
* <span data-ttu-id="fa503-163">"Mudo" ou "desativar mudo"</span><span class="sxs-lookup"><span data-stu-id="fa503-163">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="fa503-164">"Desligar o dispositivo"</span><span class="sxs-lookup"><span data-stu-id="fa503-164">"Shut down the device"</span></span>
* <span data-ttu-id="fa503-165">"Reiniciar o dispositivo"</span><span class="sxs-lookup"><span data-stu-id="fa503-165">"Restart the device"</span></span>
* <span data-ttu-id="fa503-166">"Ir para o estado de suspensão"</span><span class="sxs-lookup"><span data-stu-id="fa503-166">"Go to sleep"</span></span>
* <span data-ttu-id="fa503-167">"Qual é o tempo?"</span><span class="sxs-lookup"><span data-stu-id="fa503-167">"What time is it?"</span></span>
* <span data-ttu-id="fa503-168">"A quantidade de bateria que resta?"</span><span class="sxs-lookup"><span data-stu-id="fa503-168">"How much battery do I have left?"</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="fa503-169">"Vê-lo, digamos"</span><span class="sxs-lookup"><span data-stu-id="fa503-169">"See It, Say It"</span></span><br>
        <span data-ttu-id="fa503-170">O HoloLens tem um modelo "vê-lo, digamos" para entrada de voz, em que os rótulos nos botões informam aos usuários quais comandos de voz eles podem dizer também.</span><span class="sxs-lookup"><span data-stu-id="fa503-170">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="fa503-171">Por exemplo, ao examinar uma janela de aplicativo no HoloLens (1º gen), um usuário pode dizer o comando "ajustar" para ajustar a posição do aplicativo no mundo.</span><span class="sxs-lookup"><span data-stu-id="fa503-171">For example, when looking at an app window in HoloLens (1st gen), a user can say "Adjust" command to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="fa503-172">*Imagem: um usuário pode dizer o comando "ajustar", que vê na barra de aplicativos para ajustar a posição do aplicativo*</span><span class="sxs-lookup"><span data-stu-id="fa503-172">*Image: A user can say the "Adjust" command, which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="fa503-173">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="fa503-173">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="fa503-174">![Ao examinar uma janela de aplicativo ou um holograma, um usuário pode dizer o comando "ajustar" que vê na barra de aplicativos para ajustar a posição do aplicativo no mundo](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="fa503-174">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="fa503-175">Quando os aplicativos seguem essa regra, os usuários podem entender facilmente o que dizer para controlar o sistema.</span><span class="sxs-lookup"><span data-stu-id="fa503-175">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="fa503-176">Enquanto nuvens em um botão no HoloLens (1º gen), você verá uma dica de ferramenta de "pesquisa de voz" que aparecerá após um segundo se o botão estiver habilitado para voz e exibirá o comando para falar para "pressionar".</span><span class="sxs-lookup"><span data-stu-id="fa503-176">While gazing at a button in HoloLens (1st gen), you'll see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="fa503-177">Para revelar as dicas de ferramenta de voz no HoloLens 2, mostre o cursor de voz dizendo "Select" ou "o que eu posso dizer" (consulte a imagem).</span><span class="sxs-lookup"><span data-stu-id="fa503-177">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="fa503-178">*Imagem: "vê-lo, digamos", os comandos aparecem abaixo dos botões*</span><span class="sxs-lookup"><span data-stu-id="fa503-178">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Vê-lo, digamos que os comandos de ti apareçam abaixo dos botões](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="fa503-180">Comandos de voz para manipulação rápida de holograma</span><span class="sxs-lookup"><span data-stu-id="fa503-180">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="fa503-181">Há muitos comandos de voz que você pode dizer ao nuvensr em um holograma para realizar tarefas de manipulação rapidamente.</span><span class="sxs-lookup"><span data-stu-id="fa503-181">There are many voice commands you can say while gazing at a hologram to quickly do manipulation tasks.</span></span> <span data-ttu-id="fa503-182">Esses comandos de voz funcionam em janelas de aplicativos e em objetos 3D que você colocou no mundo.</span><span class="sxs-lookup"><span data-stu-id="fa503-182">These voice commands work on app windows and 3D objects you've placed in the world.</span></span>

<span data-ttu-id="fa503-183">**Comandos de manipulação de holograma**</span><span class="sxs-lookup"><span data-stu-id="fa503-183">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="fa503-184">Entre em frente</span><span class="sxs-lookup"><span data-stu-id="fa503-184">Face me</span></span>
* <span data-ttu-id="fa503-185">Maior | Aprimorou</span><span class="sxs-lookup"><span data-stu-id="fa503-185">Bigger | Enhance</span></span>
* <span data-ttu-id="fa503-186">Menor</span><span class="sxs-lookup"><span data-stu-id="fa503-186">Smaller</span></span>

<span data-ttu-id="fa503-187">No HoloLens 2, você também pode criar interações mais naturais em combinação com olhar, o que fornece implicitamente informações contextuais sobre o que você está referindo.</span><span class="sxs-lookup"><span data-stu-id="fa503-187">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze, which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="fa503-188">Por exemplo, você pode examinar um holograma e dizer "colocar _isso_" e, em seguida, examinar onde deseja colocá-lo e dizer " _aqui_".</span><span class="sxs-lookup"><span data-stu-id="fa503-188">For example, you could look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="fa503-189">Ou você pode examinar uma parte Holographic em um computador complexo e dizer: "Dê-me mais informações sobre _isso_".</span><span class="sxs-lookup"><span data-stu-id="fa503-189">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>

## <a name="discovering-voice-commands"></a><span data-ttu-id="fa503-190">Descobrindo comandos de voz</span><span class="sxs-lookup"><span data-stu-id="fa503-190">Discovering voice commands</span></span>

<span data-ttu-id="fa503-191">Alguns comandos, como os comandos para manipulação rápida acima, podem ser ocultados.</span><span class="sxs-lookup"><span data-stu-id="fa503-191">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="fa503-192">Para saber mais sobre os comandos que você pode usar, olhar em um objeto e, por exemplo, "o que eu posso dizer?".</span><span class="sxs-lookup"><span data-stu-id="fa503-192">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="fa503-193">Uma lista de comandos possíveis é exibida.</span><span class="sxs-lookup"><span data-stu-id="fa503-193">A list of possible commands pops up.</span></span> <span data-ttu-id="fa503-194">Você também pode usar o cursor olhar de cabeçalho para examinar e revelar as dicas de ferramenta de voz para cada botão na frente de você.</span><span class="sxs-lookup"><span data-stu-id="fa503-194">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="fa503-195">Se você quiser uma lista completa, basta dizer "Mostrar todos os comandos" a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="fa503-195">If you want a complete list, just say, "Show all commands" anytime.</span></span> 

## <a name="dictation"></a><span data-ttu-id="fa503-196">Ditado</span><span class="sxs-lookup"><span data-stu-id="fa503-196">Dictation</span></span>

<span data-ttu-id="fa503-197">Em vez de digitar com [toques de ar](gaze-and-commit.md#composite-gestures), o ditado de voz pode ser mais eficiente para inserir texto em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa503-197">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="fa503-198">Isso pode acelerar muito a entrada com menos esforço para o usuário.</span><span class="sxs-lookup"><span data-stu-id="fa503-198">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="fa503-199">![O ditado de voz começa selecionando o botão de microfone](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="fa503-199">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="fa503-200">*O ditado de voz começa selecionando o botão de microfone no teclado*</span><span class="sxs-lookup"><span data-stu-id="fa503-200">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="fa503-201">Sempre que o teclado Holographic estiver ativo, você poderá alternar para o modo de ditado em vez de digitar.</span><span class="sxs-lookup"><span data-stu-id="fa503-201">Anytime the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="fa503-202">Selecione o microfone no lado da caixa de entrada de texto para começar.</span><span class="sxs-lookup"><span data-stu-id="fa503-202">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="fa503-203">Adicionando comandos de voz ao seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="fa503-203">Adding voice commands to your app</span></span>

<span data-ttu-id="fa503-204">Considere a adição de comandos de voz em qualquer experiência que você criar.</span><span class="sxs-lookup"><span data-stu-id="fa503-204">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="fa503-205">A voz é uma maneira poderosa de controlar o sistema e os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fa503-205">Voice is a powerful way control the system and apps.</span></span> <span data-ttu-id="fa503-206">Como os usuários falam com diferentes tipos de dialetos e acentos, a escolha correta das palavras-chave de fala garantirá que os comandos dos usuários sejam interpretados de forma não ambígua.</span><span class="sxs-lookup"><span data-stu-id="fa503-206">Because users speak with different kinds of dialects and accents, proper choice of speech keywords will make sure your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="fa503-207">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="fa503-207">Best practices</span></span>

<span data-ttu-id="fa503-208">A seguir, algumas práticas que auxiliarão em um reconhecimento de fala perfeito.</span><span class="sxs-lookup"><span data-stu-id="fa503-208">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="fa503-209">**Use comandos concisos** - quando possível, escolha palavras com duas ou mais sílabas.</span><span class="sxs-lookup"><span data-stu-id="fa503-209">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="fa503-210">Palavras com uma sílaba tendem a empregar sons de vogais diferentes quando faladas por pessoas com sotaques diferentes.</span><span class="sxs-lookup"><span data-stu-id="fa503-210">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="fa503-211">Exemplo: "reproduzir vídeo" é melhor do que "reproduzir o vídeo selecionado no momento"</span><span class="sxs-lookup"><span data-stu-id="fa503-211">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="fa503-212">**Usar vocabulário simples** -exemplo: "mostrar nota" é melhor do que "mostrar letreiro"</span><span class="sxs-lookup"><span data-stu-id="fa503-212">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="fa503-213">Certifique-se de que os **comandos não sejam destrutivos** -Verifique se as ações de comando de fala não são destrutivas e podem ser facilmente desfeitas caso outra pessoa falando perto do usuário dispare acidentalmente um comando.</span><span class="sxs-lookup"><span data-stu-id="fa503-213">**Make sure commands are non-destructive** - Make sure any speech command actions are non-destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="fa503-214">**Evite comandos de som semelhantes** -Evite registrar vários comandos de fala que parecem semelhantes.</span><span class="sxs-lookup"><span data-stu-id="fa503-214">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound similar.</span></span> <span data-ttu-id="fa503-215">Exemplo: "mostrar mais" e "mostrar armazenamento" pode ser um som semelhante.</span><span class="sxs-lookup"><span data-stu-id="fa503-215">Example: "Show more" and "Show store" can be similar sounding.</span></span>
* <span data-ttu-id="fa503-216">**Cancelar o registro de seu aplicativo quando ele não for usado** -quando seu aplicativo não estiver em um estado no qual um determinado comando de fala é válido, considere cancelar o registro para que outros comandos não sejam confusos para aquele.</span><span class="sxs-lookup"><span data-stu-id="fa503-216">**Unregister your app when not it uses** - When your app isn't in a state in which a particular speech command is valid, consider unregistering it so that other commands aren't confused for that one.</span></span>
* <span data-ttu-id="fa503-217">**Teste com sotaques diferentes** - teste seu aplicativo com usuários que tenham sotaques diferentes.</span><span class="sxs-lookup"><span data-stu-id="fa503-217">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="fa503-218">**Mantenha a consistência nos comandos de voz** - se "Voltar" vai para a página anterior, mantenha esse comportamento em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fa503-218">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="fa503-219">**Evite usar comandos do sistema** – os comandos de voz a seguir são reservados para o sistema, portanto, evite usá-los em seus aplicativos:</span><span class="sxs-lookup"><span data-stu-id="fa503-219">**Avoid using system commands** - The following voice commands are reserved for the system, so avoid using them in your applications:</span></span>
   * <span data-ttu-id="fa503-220">"Ei, Cortana!"</span><span class="sxs-lookup"><span data-stu-id="fa503-220">"Hey Cortana"</span></span>
   * <span data-ttu-id="fa503-221">"Selecionar"</span><span class="sxs-lookup"><span data-stu-id="fa503-221">"Select"</span></span>
   * <span data-ttu-id="fa503-222">"Ir para o início"</span><span class="sxs-lookup"><span data-stu-id="fa503-222">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="fa503-223">Vantagens da entrada de voz</span><span class="sxs-lookup"><span data-stu-id="fa503-223">Advantages of voice input</span></span>

<span data-ttu-id="fa503-224">A entrada de voz é uma maneira natural de comunicarmos nossas intenções.</span><span class="sxs-lookup"><span data-stu-id="fa503-224">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="fa503-225">A voz é especialmente boa em **atravessamentos** de interface porque pode ajudar os usuários a cortar várias etapas de uma interface.</span><span class="sxs-lookup"><span data-stu-id="fa503-225">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface.</span></span> <span data-ttu-id="fa503-226">Um usuário pode dizer "voltar" ao olhar para uma página da Web, em vez de ter que ir para cima e pressionar o botão voltar no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa503-226">A user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app.</span></span> <span data-ttu-id="fa503-227">Esse pequeno tempo de salvamento tem um **efeito emocional** poderoso sobre a percepção do usuário da experiência e dá uma pequena quantia superpotência.</span><span class="sxs-lookup"><span data-stu-id="fa503-227">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="fa503-228">O uso da voz também é um método de entrada conveniente quando nossos braços estão ocupados ou quando estamos **executando várias tarefas ao mesmo tempo**.</span><span class="sxs-lookup"><span data-stu-id="fa503-228">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="fa503-229">Em dispositivos em que é difícil digitar um teclado, o **ditado de voz** pode ser uma maneira alternativa eficiente de inserir texto.</span><span class="sxs-lookup"><span data-stu-id="fa503-229">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="fa503-230">Por fim, em alguns casos, quando o **intervalo de precisão** para olhar e gesto é limitado, a voz pode ajudar a desambiguar a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="fa503-230">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="fa503-231">**Como o uso da voz pode beneficiar o usuário?**</span><span class="sxs-lookup"><span data-stu-id="fa503-231">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="fa503-232">Reduz o tempo - deve tornar o objetivo final mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="fa503-232">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="fa503-233">Minimiza o esforço - deve tornar as tarefas mais fluídas e simples.</span><span class="sxs-lookup"><span data-stu-id="fa503-233">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="fa503-234">Reduz a carga cognitiva - é intuitivo e fácil de lembrar e aprender.</span><span class="sxs-lookup"><span data-stu-id="fa503-234">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="fa503-235">É aceitável: ele deve se ajustar com as normas sociedades de comportamento.</span><span class="sxs-lookup"><span data-stu-id="fa503-235">It's socially acceptable - it should fit in with societal norms of behavior.</span></span>
* <span data-ttu-id="fa503-236">É rotineiro - a voz pode facilmente se tornar um comportamento habitual.</span><span class="sxs-lookup"><span data-stu-id="fa503-236">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="fa503-237">Desafios para entrada de voz</span><span class="sxs-lookup"><span data-stu-id="fa503-237">Challenges for voice input</span></span>

<span data-ttu-id="fa503-238">Embora a entrada de voz seja ótima para muitos aplicativos diferentes, ela também enfrenta vários desafios.</span><span class="sxs-lookup"><span data-stu-id="fa503-238">While voice input is great for many different applications, it also faces several challenges.</span></span> <span data-ttu-id="fa503-239">Entender as vantagens e os desafios da entrada de voz permite que os desenvolvedores de aplicativos tomem decisões mais inteligentes sobre como e quando usar a entrada de voz e para criar uma ótima experiência para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="fa503-239">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="fa503-240">**Entrada de voz para controle de entrada contínuo** O controle refinado é um deles.</span><span class="sxs-lookup"><span data-stu-id="fa503-240">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="fa503-241">Por exemplo, um usuário pode querer alterar seu volume em seu aplicativo de música.</span><span class="sxs-lookup"><span data-stu-id="fa503-241">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="fa503-242">Ela pode dizer "mais alta", mas não fica claro quanto mais alto o sistema deve fazer o volume.</span><span class="sxs-lookup"><span data-stu-id="fa503-242">She can say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="fa503-243">O usuário poderia dizer: "torná-lo um pouco mais alto", mas "um pouco" é difícil quantificar.</span><span class="sxs-lookup"><span data-stu-id="fa503-243">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="fa503-244">A movimentação ou o dimensionamento de hologramas com voz é difícil.</span><span class="sxs-lookup"><span data-stu-id="fa503-244">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="fa503-245">**Confiabilidade da detecção de entrada de voz** Embora os sistemas de entrada de voz se tornem melhores e melhores, às vezes eles podem ouvir e interpretar um comando de voz incorretamente.</span><span class="sxs-lookup"><span data-stu-id="fa503-245">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="fa503-246">A chave é resolver o desafio em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa503-246">The key is to address the challenge in your application.</span></span> <span data-ttu-id="fa503-247">Forneça comentários para seus usuários quando o sistema estiver escutando e o que o sistema entendeu esclarece os possíveis problemas ao entender a fala dos usuários.</span><span class="sxs-lookup"><span data-stu-id="fa503-247">Provide feedback to your users when the system is listening and what the system understood clarifies potential issues understanding the users' speech.</span></span>  

<span data-ttu-id="fa503-248">**Entrada de voz em espaços compartilhados** A voz pode não ser socialmente aceitável em espaços que você compartilha com outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="fa503-248">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="fa503-249">Veja alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="fa503-249">Here are a few examples:</span></span>
* <span data-ttu-id="fa503-250">Talvez o usuário não queira incomodar outros (por exemplo, em uma biblioteca silenciosa ou em um escritório compartilhado)</span><span class="sxs-lookup"><span data-stu-id="fa503-250">The user may not want to disturb others (for example, in a quiet library or shared office)</span></span>
* <span data-ttu-id="fa503-251">Os usuários podem se sentir inconvenientes sendo vistos por si mesmos em público,</span><span class="sxs-lookup"><span data-stu-id="fa503-251">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="fa503-252">Um usuário pode sentir-se desconfortável ditando uma mensagem pessoal ou confidencial (incluindo senhas) enquanto outras estão ouvindo</span><span class="sxs-lookup"><span data-stu-id="fa503-252">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="fa503-253">**Entrada de voz de palavras exclusivas ou desconhecidas** As dificuldades de entrada de voz também são fornecidas quando os usuários estão ditando palavras que podem ser desconhecidas do sistema, como apelidos, determinadas palavras gírias ou abreviações.</span><span class="sxs-lookup"><span data-stu-id="fa503-253">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words, or abbreviations.</span></span> 

<span data-ttu-id="fa503-254">**Comandos de voz de aprendizagem** Embora o objetivo final seja conversar naturalmente com seu sistema, muitas vezes os aplicativos ainda dependem de comandos de voz predefinidos específicos.</span><span class="sxs-lookup"><span data-stu-id="fa503-254">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="fa503-255">Um desafio associado a um conjunto significativo de comandos de voz é como ensiná-los sem sobrecarregar o usuário e como ajudar o usuário a mantê-los.</span><span class="sxs-lookup"><span data-stu-id="fa503-255">A challenge associated with a significant set of voice commands is how to teach them without overloading the user and how to help the user to keep them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="fa503-256">Estados de retorno de voz</span><span class="sxs-lookup"><span data-stu-id="fa503-256">Voice feedback states</span></span>

<span data-ttu-id="fa503-257">Quando a voz é aplicada corretamente, o usuário sabe **o que pode dizer e obtém um retorno claro**, e o sistema **o ouve corretamente**.</span><span class="sxs-lookup"><span data-stu-id="fa503-257">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="fa503-258">Esses dois sinais fazem o usuário se sentir seguro para usar a Voz como uma entrada primária.</span><span class="sxs-lookup"><span data-stu-id="fa503-258">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="fa503-259">A seguir, um diagrama mostrando o que acontece com o cursor quando a entrada de voz é reconhecida e como ele comunica isso ao usuário.</span><span class="sxs-lookup"><span data-stu-id="fa503-259">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="fa503-260">![1. Estado regular do cursor](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="fa503-260">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="fa503-261">**1. Estado regular do cursor**</span><span class="sxs-lookup"><span data-stu-id="fa503-261">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="fa503-262">![2. comunica os comentários de voz e, em seguida, desaparece](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="fa503-262">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="fa503-263">**2. comunica os comentários de voz e, em seguida, desaparece**</span><span class="sxs-lookup"><span data-stu-id="fa503-263">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="fa503-264">![Beta.</span><span class="sxs-lookup"><span data-stu-id="fa503-264">![\*3.</span></span> <span data-ttu-id="fa503-265">Estado de cursor regular](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="fa503-265">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="fa503-266">**3. retorna ao Estado regular do cursor**</span><span class="sxs-lookup"><span data-stu-id="fa503-266">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="fa503-267">As principais coisas que os usuários devem saber sobre "fala" na realidade misturada</span><span class="sxs-lookup"><span data-stu-id="fa503-267">Top things users should know about "speech" in mixed reality</span></span>

* <span data-ttu-id="fa503-268">Diga **"Select" (selecionar** ) ao direcionar um botão (você pode usá-lo em qualquer lugar para selecionar um botão).</span><span class="sxs-lookup"><span data-stu-id="fa503-268">Say **"Select"** while targeting a button (you can use this anywhere to select a button).</span></span>
* <span data-ttu-id="fa503-269">Você pode dizer o **nome do rótulo de um botão da barra de aplicativos** em alguns aplicativos para realizar uma ação.</span><span class="sxs-lookup"><span data-stu-id="fa503-269">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="fa503-270">Por exemplo, ao examinar um aplicativo, um usuário pode dizer ao comando "remover" para remover o aplicativo do mundo (isso poupa tempo de ter que selecioná-lo com sua mão).</span><span class="sxs-lookup"><span data-stu-id="fa503-270">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to select it with your hand).</span></span>
* <span data-ttu-id="fa503-271">Você pode iniciar a escuta da Cortana dizendo **"Ei Cortana".**</span><span class="sxs-lookup"><span data-stu-id="fa503-271">You can start Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="fa503-272">Você pode fazer perguntas ("Ei, Cortana! Qual é a altura da Torre Eiffel?"), pedir para ela abrir um aplicativo ("Ei, Cortana! Abra o Netflix") ou pedir para ela abrir o Menu Iniciar ("Ei, Cortana! Abra o menu Iniciar") e muito mais.</span><span class="sxs-lookup"><span data-stu-id="fa503-272">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="fa503-273">Perguntas e preocupações comuns dos usuários em relação à voz</span><span class="sxs-lookup"><span data-stu-id="fa503-273">Common questions and concerns users have about voice</span></span>

* <span data-ttu-id="fa503-274">O que posso dizer?</span><span class="sxs-lookup"><span data-stu-id="fa503-274">What can I say?</span></span>
* <span data-ttu-id="fa503-275">Como saberei que o sistema me ouviu corretamente?</span><span class="sxs-lookup"><span data-stu-id="fa503-275">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="fa503-276">O sistema não entende corretamente meus comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="fa503-276">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="fa503-277">Ele não reage quando dou um comando de voz.</span><span class="sxs-lookup"><span data-stu-id="fa503-277">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="fa503-278">Ele reage de maneira errada quando dou um comando de voz.</span><span class="sxs-lookup"><span data-stu-id="fa503-278">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="fa503-279">Como direcionar minha voz a um aplicativo específico ou a um comando de aplicativo?</span><span class="sxs-lookup"><span data-stu-id="fa503-279">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="fa503-280">Posso usar a voz para comandar as coisas no quadro holográfico do HoloLens?</span><span class="sxs-lookup"><span data-stu-id="fa503-280">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="fa503-281">Comunicação</span><span class="sxs-lookup"><span data-stu-id="fa503-281">Communication</span></span>

<span data-ttu-id="fa503-282">Para aplicativos que desejam aproveitar as opções de processamento de entrada de áudio personalizadas fornecidas pelo HoloLens, é importante entender as várias [categorias de fluxo de áudio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que seu aplicativo pode consumir.</span><span class="sxs-lookup"><span data-stu-id="fa503-282">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it's important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="fa503-283">O Windows 10 dá suporte a várias categorias de fluxo diferentes e o HoloLens usa três delas para habilitar o processamento personalizado para otimizar a qualidade de áudio do microfone adaptada para fala, comunicação e outros, que podem ser usados para cenários de captura de áudio do ambiente de ambientes (ou seja, "camcorder").</span><span class="sxs-lookup"><span data-stu-id="fa503-283">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication, and other, which can be used for ambient environment audio capture (that is, "camcorder") scenarios.</span></span>
* <span data-ttu-id="fa503-284">A categoria de fluxo de AudioCategory_Communications é personalizada para cenários de qualidade de chamada e narração e fornece ao cliente um fluxo de áudio mono de 24 bits de 16-kHz da voz do usuário</span><span class="sxs-lookup"><span data-stu-id="fa503-284">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16-kHz 24-bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="fa503-285">A categoria AudioCategory_Speech Stream é personalizada para o mecanismo de fala do HoloLens (Windows) e a fornece com um fluxo mono de 16-kHz de 24 bits da voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="fa503-285">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16-kHz 24-bit mono stream of the user's voice.</span></span> <span data-ttu-id="fa503-286">Essa categoria pode ser usada por mecanismos de fala de terceiros, se necessário.</span><span class="sxs-lookup"><span data-stu-id="fa503-286">This category can be used by third-party speech engines if needed.</span></span>
* <span data-ttu-id="fa503-287">A categoria de AudioCategory_Other Stream é personalizada para a gravação de áudio do ambiente ambiental e fornece ao cliente um fluxo de áudio estéreo de 24 bits de 48-kHz.</span><span class="sxs-lookup"><span data-stu-id="fa503-287">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48-kHz 24-bit stereo audio stream.</span></span>

<span data-ttu-id="fa503-288">Todo esse processamento de áudio é acelerado por hardware, o que significa que os recursos esgotam muito menos energia do que se o mesmo processamento foi feito na CPU do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fa503-288">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="fa503-289">Evite executar outro processamento de entrada de áudio na CPU para maximizar a vida útil da bateria do sistema e aproveitar o processamento interno de entrada de áudio descarregado.</span><span class="sxs-lookup"><span data-stu-id="fa503-289">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built-in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="fa503-290">Idiomas</span><span class="sxs-lookup"><span data-stu-id="fa503-290">Languages</span></span>

<span data-ttu-id="fa503-291">O HoloLens 2 [dá suporte a vários idiomas](https://docs.microsoft.com/hololens/hololens2-language-support).</span><span class="sxs-lookup"><span data-stu-id="fa503-291">HoloLens 2 [supports multiple languages](https://docs.microsoft.com/hololens/hololens2-language-support).</span></span> <span data-ttu-id="fa503-292">Tenha em mente que os comandos de fala sempre serão executados no idioma de exibição do sistema, mesmo se vários teclados estiverem instalados ou se os aplicativos tentarem criar um reconhecedor de fala em um idioma diferente.</span><span class="sxs-lookup"><span data-stu-id="fa503-292">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="fa503-293">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="fa503-293">Troubleshooting</span></span>

<span data-ttu-id="fa503-294">Se você tiver problemas ao usar "Select" e "Ei Cortana", tente mudar para um espaço mais silencioso, desativando a fonte de ruído ou falando mais alto.</span><span class="sxs-lookup"><span data-stu-id="fa503-294">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="fa503-295">Neste momento, todo o reconhecimento de fala no HoloLens é ajustado e otimizado especificamente para os palestrantes nativos do Estados Unidos Inglês.</span><span class="sxs-lookup"><span data-stu-id="fa503-295">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="fa503-296">Para o Windows Mixed Reality Developer Edition versão 2017, a lógica de gerenciamento de ponto de extremidade de áudio funcionará bem (para sempre) depois de fazer logoff e voltar para a área de trabalho do PC após a conexão inicial do HMD.</span><span class="sxs-lookup"><span data-stu-id="fa503-296">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="fa503-297">Antes desse primeiro evento de logout/entrada depois de passar pelo WMR OOBE, o usuário pode experimentar vários problemas de funcionalidade de áudio, desde que não haja áudio para nenhuma alternância de áudio, dependendo de como o sistema foi configurado antes de conectar o HMD pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="fa503-297">Before that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up before connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="fa503-298">Entrada de voz em MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="fa503-298">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="fa503-299">Com o **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, você pode atribuir facilmente o comando de voz em qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="fa503-299">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="fa503-300">Use o **perfil de entrada de fala** do MRTK para definir suas palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="fa503-300">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="fa503-301">Ao atribuir o script **SpeechInputHandler** , você pode fazer com que qualquer objeto responda às palavras-chave definidas no perfil de entrada de fala.</span><span class="sxs-lookup"><span data-stu-id="fa503-301">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="fa503-302">O SpeechInputHandler também fornece um rótulo de confirmação de fala para melhorar a confiança do usuário.</span><span class="sxs-lookup"><span data-stu-id="fa503-302">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="fa503-303">MRTK-comando de voz</span><span class="sxs-lookup"><span data-stu-id="fa503-303">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)

---

## <a name="see-also"></a><span data-ttu-id="fa503-304">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa503-304">See also</span></span>

* [<span data-ttu-id="fa503-305">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="fa503-305">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="fa503-306">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="fa503-306">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="fa503-307">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="fa503-307">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="fa503-308">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="fa503-308">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)
