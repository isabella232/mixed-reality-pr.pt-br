---
title: 5. Como adicionar um botão e redefinir locais de peças
description: Parte 5 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 08/14/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: f903848b8d5c9c1dccfc00cd7bd6d16d2e491a5e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679835"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="0bbc5-104">5. Como adicionar um botão e redefinir locais de peças</span><span class="sxs-lookup"><span data-stu-id="0bbc5-104">5. Adding a button & resetting piece locations</span></span>


## <a name="overview"></a><span data-ttu-id="0bbc5-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="0bbc5-105">Overview</span></span>

<span data-ttu-id="0bbc5-106">No tutorial anterior, você adicionou Atores de Interação à Mão aos componentes Peão e Manipulador para o tabuleiro de xadrez, a fim de torná-los interativos.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-106">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="0bbc5-107">Nesta seção, você continuará trabalhando com as Ferramentas de UX do Kit de Ferramentas de Realidade Misturada ao criar os recursos do seu aplicativo de xadrez.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-107">In this section, you'll continue working with the Mixed Reality Toolkit UX Tools plugin by building out the features of your chess app.</span></span> <span data-ttu-id="0bbc5-108">Isso inclui a criação de uma função e o aprendizado de como obter referências a Atores em um Blueprint.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-108">This includes creating a new function and learning how to get references to Actors in a Blueprint.</span></span> <span data-ttu-id="0bbc5-109">Ao final desta seção, você estará pronto para empacotar e implantar o aplicativo de realidade misturada em um dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-109">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="0bbc5-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0bbc5-110">Objectives</span></span>

* <span data-ttu-id="0bbc5-111">Adicionar um botão interativo</span><span class="sxs-lookup"><span data-stu-id="0bbc5-111">Adding an interactive button</span></span>
* <span data-ttu-id="0bbc5-112">Criar uma função para redefinir a localização de uma peça</span><span class="sxs-lookup"><span data-stu-id="0bbc5-112">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="0bbc5-113">Vincular o botão para disparar a função quando pressionado</span><span class="sxs-lookup"><span data-stu-id="0bbc5-113">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="0bbc5-114">Criar uma função de redefinição</span><span class="sxs-lookup"><span data-stu-id="0bbc5-114">Creating a reset function</span></span>
<span data-ttu-id="0bbc5-115">Sua primeira tarefa é criar um blueprint de função que redefina uma peça de xadrez para a posição original dela na cena.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-115">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span> 

1.  <span data-ttu-id="0bbc5-116">Abra **WhiteKing**, clique no ícone **+** ao lado da seção **Funções** no **Meu Blueprint** e nomeie-o como **Redefinir Localização**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-116">Open **WhiteKing**, click the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span> 

2.  <span data-ttu-id="0bbc5-117">Arraste e solte a execução de **Redefinir Localização** na grade do Blueprint para criar um nó **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-117">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span> 
    * <span data-ttu-id="0bbc5-118">Essa função define a transformação (localização, rotação e escala) de um ator em relação ao seu pai.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-118">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="0bbc5-119">Você usará essa função para redefinir a posição do rei no tabuleiro, mesmo que o tabuleiro tenha sido movido de sua posição original.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-119">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> 
    
3. <span data-ttu-id="0bbc5-120">Clique com o botão direito do mouse no Grafo de Eventos, selecione **Transformar** e altere a **Localização** dele para **X = -26**, **Y = 4** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-120">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="0bbc5-121">Conecte o **Valor Retornado** dele ao marcador **Nova Transformação Relativa** em **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-121">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span> 

![Função Reset Location](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="0bbc5-123">Escolha **Compilar** e **Salvar** o projeto antes de voltar à Janela principal.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-123">**Compile** and **Save** the project before returning to the Main window.</span></span> 


## <a name="adding-a-button"></a><span data-ttu-id="0bbc5-124">Adicionar um botão</span><span class="sxs-lookup"><span data-stu-id="0bbc5-124">Adding a button</span></span>
<span data-ttu-id="0bbc5-125">Agora que a função está configurada corretamente, a próxima tarefa é criar um botão que a dispare quando tocado.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-125">Now that the function is setup correctly, your next task is to create a button that fires it off when touched.</span></span> 


1.  <span data-ttu-id="0bbc5-126">Clique em **Adicionar Novo > Classe de Blueprint**, expanda a seção **Todas as Classes** e pesquise por **BP_ButtonHoloLens2**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-126">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **BP_ButtonHoloLens2**.</span></span> 
    * <span data-ttu-id="0bbc5-127">Nomeie-o como **ResetButton** e clique duas vezes para abrir o Blueprint</span><span class="sxs-lookup"><span data-stu-id="0bbc5-127">Name it **ResetButton** and double click to open the Blueprint</span></span>

> [!NOTE]
> <span data-ttu-id="0bbc5-128">O **BP_ButtonHoloLens2** é um Ator do Blueprint de botão 3D que faz parte do plug-in Ferramentas de UX.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-128">**BP_ButtonHoloLens2** is a 3D button Blueprint Actor that's part of the UX Tools plugin.</span></span>

![Subclasse do novo Blueprint do botão de estilo do HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="0bbc5-130">No painel **Componentes**, selecione **ResetButton(self)** .</span><span class="sxs-lookup"><span data-stu-id="0bbc5-130">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="0bbc5-131">No painel **Detalhes**, navegue até a seção **Botão**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-131">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="0bbc5-132">Altere o padrão **Botão de Rótulo** para "Redefinir".</span><span class="sxs-lookup"><span data-stu-id="0bbc5-132">Change the default **Button Label** to "Reset".</span></span> <span data-ttu-id="0bbc5-133">Expanda a seção **Pincel do Ícone do Botão** e pressione o botão **Abrir o Icon Brush Editor**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-133">Expand the **Button Icon Brush** section and press the **Open Icon Brush Editor** button.</span></span> 

![Definir o rótulo e o ícone no botão](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="0bbc5-135">Isso abrirá o Icon Brush Editor, um utilitário fornecido pelo plug-in de Ferramentas de UX que pode ser usado para selecionar um novo ícone para o botão.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-135">This will open up the Icon Brush Editor, which is a utility provided by the UX Tools plugin which you can use to select a new icon for your button.</span></span> 

![Selecionar um ícone para o botão](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="0bbc5-137">Há várias outras configurações que você pode ajustar para configurar seu botão.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-137">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="0bbc5-138">Para saber mais sobre o componente UXT Pressable Button, confira a [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html).</span><span class="sxs-lookup"><span data-stu-id="0bbc5-138">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="0bbc5-139">Clique em **UxtPressableButton (Herdado)** no painel **Componentes** e role o painel **Detalhes** para baixo até a seção **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-139">Click **UxtPressableButton (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span> 
    * <span data-ttu-id="0bbc5-140">Clique no botão **+** verde próximo de **On Button Pressed** para adicionar um evento Grafo de Eventos, que será chamado quando o botão for pressionado.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-140">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span> 
    
<span data-ttu-id="0bbc5-141">Deste ponto em diante, será conveniente que você chame a função **Redefinir Localização** do **WhiteKing**, que precisa de uma referência para o Ator **WhiteKing** no Nível.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-141">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span> 

4.  <span data-ttu-id="0bbc5-142">No painel **Meu Blueprint**, navegue até a seção **Variáveis**, clique no botão **+** e nomeie a variável **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-142">In the **My Blueprint** panel, navigate to the **Variables** section , click the **+** button and name the variable **WhiteKing**.</span></span> 
    * <span data-ttu-id="0bbc5-143">No painel **Detalhes**, selecione a lista suspensa ao lado de **Tipo de Variável**, pesquise **WhiteKing** e selecione **Referência de Objeto**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-143">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span> 
    * <span data-ttu-id="0bbc5-144">Marque a caixa ao lado de **Instância Editável**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-144">Check the box next to **Instance Editable**.</span></span> <span data-ttu-id="0bbc5-145">Isso permitirá que a variável seja definida no Nível Principal.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-145">This will allow the variable to be set from the Main Level.</span></span> 

![Criar uma variável](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="0bbc5-147">Arraste a variável WhiteKing de **Meu Blueprint > Variáveis** até o Grafo de Eventos do Botão Redefinir e escolha **Obter WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-147">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span> 

## <a name="firing-the-function"></a><span data-ttu-id="0bbc5-148">Como disparar a função</span><span class="sxs-lookup"><span data-stu-id="0bbc5-148">Firing the function</span></span>
<span data-ttu-id="0bbc5-149">Tudo o que resta fazer é disparar oficialmente a função de redefinição quando o botão for pressionado.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-149">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="0bbc5-150">Arraste o pino da saída WhiteKing e solte para posicionar um novo nó.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-150">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="0bbc5-151">Selecione a função **Reset Location**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-151">Select the **Reset Location** function.</span></span> <span data-ttu-id="0bbc5-152">Por fim, arraste o pino de execução de saída de **On Button Pressed** até o pino de execução de entrada em **Reset Location**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-152">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="0bbc5-153">**Compile** e **Salve** o Blueprint ResetButton e, em seguida, retorne à Janela principal.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-153">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![Chamar função Reset Location de On Button Pressed](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="0bbc5-155">Arraste **ResetButton** até o visor e defina a localização dele como **X = 50**, **Y = -25** e **Z = 10**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-155">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="0bbc5-156">Defina a rotação como **Z = 180**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-156">Set its rotation to **Z = 180**.</span></span> <span data-ttu-id="0bbc5-157">Em **Padrão**, defina o valor da variável **WhiteKing** como **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-157">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![Definir a variável](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="0bbc5-159">Execute o aplicativo, mova a peça de xadrez para um novo local e pressione o botão de estilo do HoloLens 2 para ver a lógica de redefinição em ação!</span><span class="sxs-lookup"><span data-stu-id="0bbc5-159">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="0bbc5-160">Agora você tem um aplicativo de realidade misturada com uma peça e um tabuleiro de xadrez com os quais você pode interagir, bem como um botão totalmente funcional que redefinirá a localização da peça.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-160">You now have a mixed reality app with a chess piece and board that you can interact with, as well as a fully functioning button that will reset the piece’s location.</span></span> <span data-ttu-id="0bbc5-161">Você pode encontrar o aplicativo concluído até esse ponto no respectivo repositório do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span><span class="sxs-lookup"><span data-stu-id="0bbc5-161">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="0bbc5-162">Você pode ir além deste tutorial e configurar o restante das peças de xadrez, para que todo o tabuleiro seja redefinido quando o botão for pressionado.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-162">Feel free to go beyond this tutorial and set up the remainder of the chess pieces so that the entire board is reset when the button is pressed.</span></span>

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="0bbc5-164">Você está pronto para prosseguir para a seção final deste tutorial, em que você aprenderá a empacotar e implantar corretamente o aplicativo em um dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-164">You're ready to move on to the final section of this tutorial where you'll learn how to correctly package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0bbc5-165">Neste ponto, atualize seu projeto com as **[Configurações de desempenho do Unreal](../performance-recommendations-for-unreal.md)** recomendadas antes de implantar o aplicativo em um dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-165">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="0bbc5-166">Próxima seção: 6. Como empacotar e implantar no dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="0bbc5-166">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
