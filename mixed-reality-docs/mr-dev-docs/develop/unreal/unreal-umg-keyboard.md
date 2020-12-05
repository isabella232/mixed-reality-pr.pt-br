---
title: UMG e teclado no Unreal
description: Saiba como usar gráficos de movimento inrealistas para criar um sistema de interface do usuário fora dos widgets.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens 2, controle de olho, entrada de olhar, tela de montagem de cabeça, mecanismo inreal, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, widgets, interface do usuário, UMG, gráficos de movimento inreal, mecanismo inreal, UE, UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609757"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="78b31-104">UMG e teclado no Unreal</span><span class="sxs-lookup"><span data-stu-id="78b31-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="78b31-105">O UMG (elementos gráficos de movimento inreal) é um sistema de interface do usuário interno do mecanismo não real, usado para criar interfaces como menus e caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="78b31-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="78b31-106">Interfaces de usuário criadas com UMG consistem em widgets.</span><span class="sxs-lookup"><span data-stu-id="78b31-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="78b31-107">Nós o orientaremos na criação de um novo widget, no acréscimo ao espaço mundial e na habilitação da interação usando o teclado do sistema como um exemplo.</span><span class="sxs-lookup"><span data-stu-id="78b31-107">We'll guide you through creating a new widget, adding it to world space, and enabling interaction using the system keyboard as an example.</span></span> <span data-ttu-id="78b31-108">Você pode aprender mais sobre o UMG na [documentação](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)oficial do mecanismo inreal.</span><span class="sxs-lookup"><span data-stu-id="78b31-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="78b31-109">Criar um novo widget</span><span class="sxs-lookup"><span data-stu-id="78b31-109">Create a new widget</span></span>

- <span data-ttu-id="78b31-110">Crie um gráfico de widget para definir o layout da interface do usuário do jogo:</span><span class="sxs-lookup"><span data-stu-id="78b31-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Captura de tela da adição de um plano gráfico do widget no menu não real](images/unreal-umg-img-01.png)

- <span data-ttu-id="78b31-112">Abra o novo Blueprint e adicione componentes da paleta à tela.</span><span class="sxs-lookup"><span data-stu-id="78b31-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="78b31-113">Nesse caso, adicionamos dois componentes de caixa de texto da seção "entrada":</span><span class="sxs-lookup"><span data-stu-id="78b31-113">In this case, we've added two Text Box components from the “Input” section:</span></span>

![Captura de tela da janela de hierarquia com componente de widget de texto realçado e expandido](images/unreal-umg-img-02.png)

- <span data-ttu-id="78b31-115">Selecione um widget na janela hierarquia ou designer e modifique os parâmetros no painel de detalhes.</span><span class="sxs-lookup"><span data-stu-id="78b31-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="78b31-116">Nesse caso, adicionamos um "texto de dica" padrão e uma cor de tonalidade que aparece quando você passa o mouse sobre a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="78b31-116">In this case, we’ve added some default “Hint Text” and a tint color that appears when you hover over the text box.</span></span>  <span data-ttu-id="78b31-117">Uma caixa de texto exibirá um teclado virtual no HoloLens quando ele estiver interagindo com:</span><span class="sxs-lookup"><span data-stu-id="78b31-117">A text box will pop up a virtual keyboard on HoloLens when it's interacted with:</span></span>

![Captura de tela de parâmetros modificados na janela hierarquia](images/unreal-umg-img-03.png)

- <span data-ttu-id="78b31-119">Os eventos também podem ser assinados no painel de detalhes:</span><span class="sxs-lookup"><span data-stu-id="78b31-119">Events can also be subscribed to in the details panel:</span></span>

![Captura de tela dos eventos no painel de detalhes](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="78b31-121">Adicionar um widget ao espaço de mundo</span><span class="sxs-lookup"><span data-stu-id="78b31-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="78b31-122">Crie um novo ator, adicione um componente de widget e adicione o ator à cena:</span><span class="sxs-lookup"><span data-stu-id="78b31-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Captura de tela de um ator com um widget anexado](images/unreal-umg-img-05.png)

- <span data-ttu-id="78b31-124">No painel de detalhes do widget, defina a **classe Widget** como o plano gráfico do widget criado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="78b31-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Captura de tela do painel detalhes do plano gráfico com o conjunto de classes widget](images/unreal-umg-img-06.png)

- <span data-ttu-id="78b31-126">Para um widget de texto, verifique se a **entrada do hardware de recebimento** está desmarcada, portanto, atualizamos apenas o texto do teclado virtual:</span><span class="sxs-lookup"><span data-stu-id="78b31-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Captura de tela da seção de interação com entrada de hardware de recebimento está desmarcada](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="78b31-128">Interação do widget</span><span class="sxs-lookup"><span data-stu-id="78b31-128">Widget Interaction</span></span>

<span data-ttu-id="78b31-129">Os widgets do UMG normalmente recebem a entrada de um mouse.</span><span class="sxs-lookup"><span data-stu-id="78b31-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="78b31-130">No HoloLens ou VR, precisamos simular um mouse com um componente de interação do widget para obter os mesmos eventos.</span><span class="sxs-lookup"><span data-stu-id="78b31-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="78b31-131">Crie um novo ator, adicione um componente de **interação do widget** e adicione o ator à sua cena:</span><span class="sxs-lookup"><span data-stu-id="78b31-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Captura de tela de um novo ator com um componente de interação do widget realçado](images/unreal-umg-img-08.png)

- <span data-ttu-id="78b31-133">No painel de detalhes do componente de interação do widget:</span><span class="sxs-lookup"><span data-stu-id="78b31-133">In the details panel for the Widget Interaction component:</span></span>
    - <span data-ttu-id="78b31-134">Defina a distância de interação com o valor de distância desejado</span><span class="sxs-lookup"><span data-stu-id="78b31-134">Set the interaction distance to the distance value you want</span></span>
    - <span data-ttu-id="78b31-135">Definir a **origem da interação** como **personalizada**</span><span class="sxs-lookup"><span data-stu-id="78b31-135">Set the **Interaction Source** to **custom**</span></span>
    - <span data-ttu-id="78b31-136">Para desenvolvimento, defina **Mostrar depuração** como **true**:</span><span class="sxs-lookup"><span data-stu-id="78b31-136">For development, set **Show Debug** to **true**:</span></span>

![Captura de tela da interação do widget e das propriedades do componente de depuração](images/unreal-umg-img-09.png)

<span data-ttu-id="78b31-138">O padrão para a origem da interação é "mundo", que deve enviar raycasts com base na posição mundial do componente de interação do widget.</span><span class="sxs-lookup"><span data-stu-id="78b31-138">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component.</span></span> <span data-ttu-id="78b31-139">No AR e VR, esse não é o caso.</span><span class="sxs-lookup"><span data-stu-id="78b31-139">In AR and VR, that's not the case.</span></span>  <span data-ttu-id="78b31-140">Habilitar a "mostrar depuração" e adicionar um tom de foco aos widgets é importante para verificar se o componente de interação do widget está fazendo o que você espera.</span><span class="sxs-lookup"><span data-stu-id="78b31-140">Enabling “Show Debug” and adding a hover tint to widgets is important to check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="78b31-141">A solução alternativa é usar uma fonte personalizada e definir o Raycast no grafo de eventos a partir do raio da mão.</span><span class="sxs-lookup"><span data-stu-id="78b31-141">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="78b31-142">Aqui, estamos chamando isso a partir do tique do evento:</span><span class="sxs-lookup"><span data-stu-id="78b31-142">Here we're calling this from Event Tick:</span></span>

![Plano gráfico de tiques de eventos](images/unreal-umg-img-10.png)

<span data-ttu-id="78b31-144">Em seguida, adicione eventos de ponteiro do mouse virtual ao componente de interação do widget reagindo à entrada do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="78b31-144">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="78b31-145">Nesse caso, envie um evento de pressionamento do mouse à esquerda quando a mão estiver segurando e um evento de liberação do mouse esquerdo quando não for compreendido:</span><span class="sxs-lookup"><span data-stu-id="78b31-145">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Plano gráfico com eventos de ponteiro de mouse virtual adicionados](images/unreal-umg-img-13.png)

<span data-ttu-id="78b31-147">Agora, ao implantar o aplicativo no HoloLens 2, você verá uma extensão de raio à direita do seu lado direito.</span><span class="sxs-lookup"><span data-stu-id="78b31-147">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="78b31-148">Se você o direcionar a uma das caixas de texto editáveis e ao toque do ar, o teclado do sistema aparecerá na frente de você e permitirá que você insira o texto.</span><span class="sxs-lookup"><span data-stu-id="78b31-148">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="78b31-149">O teclado do sistema do HoloLens requer um mecanismo inreal 4,26 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="78b31-149">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="78b31-150">Além disso, o teclado não será exibido quando seu aplicativo estiver sendo transmitido do editor inreal para o headset, somente quando o aplicativo estiver em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="78b31-150">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="78b31-151">Consulte Também:</span><span class="sxs-lookup"><span data-stu-id="78b31-151">See Also:</span></span>
* [<span data-ttu-id="78b31-152">Documentação de UMG inreal</span><span class="sxs-lookup"><span data-stu-id="78b31-152">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="78b31-153">Tutoriais de UMG inreais</span><span class="sxs-lookup"><span data-stu-id="78b31-153">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
