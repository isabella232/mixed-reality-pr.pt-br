---
title: UMG e Keyboard não reais
description: Saiba como usar gráficos de movimento inrealistas para criar um sistema de interface do usuário fora dos widgets.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens 2, controle de olho, entrada de olhar, tela de montagem de cabeça, mecanismo inreal, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, widgets, interface do usuário, UMG, gráficos de movimento inreal, mecanismo inreal, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355251"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="07bb5-104">UMG e Keyboard não reais</span><span class="sxs-lookup"><span data-stu-id="07bb5-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="07bb5-105">O UMG (elementos gráficos de movimento inreal) é um sistema de interface do usuário interno do mecanismo não real, usado para criar interfaces como menus e caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="07bb5-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="07bb5-106">Interfaces de usuário criadas com UMG consistem em widgets.</span><span class="sxs-lookup"><span data-stu-id="07bb5-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="07bb5-107">Este guia mostrará como criar um novo widget, adicioná-lo ao espaço mundial e habilitar a interação com esse widget em realidade misturada, usando o teclado do sistema como um exemplo.</span><span class="sxs-lookup"><span data-stu-id="07bb5-107">This guide will show you how to create a new widget, add it to world space, and enable interaction with that widget in mixed reality, using the system keyboard as an example.</span></span> <span data-ttu-id="07bb5-108">Você pode aprender mais sobre o UMG na [documentação](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)oficial do mecanismo inreal.</span><span class="sxs-lookup"><span data-stu-id="07bb5-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="07bb5-109">Criar um novo widget</span><span class="sxs-lookup"><span data-stu-id="07bb5-109">Create a new widget</span></span>

- <span data-ttu-id="07bb5-110">Crie um gráfico de widget para definir o layout da interface do usuário do jogo:</span><span class="sxs-lookup"><span data-stu-id="07bb5-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Captura de tela da adição de um plano gráfico do widget no menu não real](images/unreal-umg-img-01.png)

- <span data-ttu-id="07bb5-112">Abra o novo Blueprint e adicione componentes da paleta à tela.</span><span class="sxs-lookup"><span data-stu-id="07bb5-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="07bb5-113">Nesse caso, adicionamos dois componentes de caixa de texto da seção "entrada":</span><span class="sxs-lookup"><span data-stu-id="07bb5-113">In this case we have added two Text Box components from the “Input” section:</span></span>

![Captura de tela da janela de hierarquia com componente de widget de texto realçado e expandido](images/unreal-umg-img-02.png)

- <span data-ttu-id="07bb5-115">Selecione um widget na janela hierarquia ou designer e modifique os parâmetros no painel de detalhes.</span><span class="sxs-lookup"><span data-stu-id="07bb5-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="07bb5-116">Nesse caso, adicionamos um "texto de dica" padrão e uma cor de tonalidade quando o cursor está focalizando a caixa de texto para fornecer comentários com os quais o widget está pronto para ser interagindo.</span><span class="sxs-lookup"><span data-stu-id="07bb5-116">In this case, we’ve added some default “Hint Text” and a tint color when the cursor is hovering over the text box to give feedback that the widget is ready to be interacted with.</span></span>  <span data-ttu-id="07bb5-117">Uma caixa de texto exibirá um teclado virtual no HoloLens quando ele estiver interagindo com:</span><span class="sxs-lookup"><span data-stu-id="07bb5-117">A text box will pop up a virtual keyboard on HoloLens when it is interacted with:</span></span>

![Captura de tela de parâmetros modificados na janela hierarquia](images/unreal-umg-img-03.png)

- <span data-ttu-id="07bb5-119">Os eventos também podem ser assinados no painel de detalhes:</span><span class="sxs-lookup"><span data-stu-id="07bb5-119">Events can also be subscribed to in the details panel:</span></span>

![Captura de tela dos eventos no painel de detalhes](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="07bb5-121">Adicionar um widget ao espaço de mundo</span><span class="sxs-lookup"><span data-stu-id="07bb5-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="07bb5-122">Crie um novo ator, adicione um componente de widget e adicione o ator à cena:</span><span class="sxs-lookup"><span data-stu-id="07bb5-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Captura de tela de um ator com um widget anexado](images/unreal-umg-img-05.png)

- <span data-ttu-id="07bb5-124">No painel de detalhes do widget, defina a **classe Widget** como o plano gráfico do widget criado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="07bb5-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Captura de tela do painel detalhes do plano gráfico com o conjunto de classes widget](images/unreal-umg-img-06.png)

- <span data-ttu-id="07bb5-126">Para um widget de texto, verifique se a **entrada do hardware de recebimento** está desmarcada, portanto, atualizamos apenas o texto do teclado virtual:</span><span class="sxs-lookup"><span data-stu-id="07bb5-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Captura de tela da seção de interação com entrada de hardware de recebimento está desmarcada](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="07bb5-128">Interação do widget</span><span class="sxs-lookup"><span data-stu-id="07bb5-128">Widget Interaction</span></span>

<span data-ttu-id="07bb5-129">Os widgets do UMG normalmente recebem a entrada de um mouse.</span><span class="sxs-lookup"><span data-stu-id="07bb5-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="07bb5-130">No HoloLens ou VR, precisamos simular um mouse com um componente de interação do widget para obter os mesmos eventos.</span><span class="sxs-lookup"><span data-stu-id="07bb5-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="07bb5-131">Crie um novo ator, adicione um componente de **interação do widget** e adicione o ator à sua cena:</span><span class="sxs-lookup"><span data-stu-id="07bb5-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Captura de tela de um novo ator com um componente de interação do widget realçado](images/unreal-umg-img-08.png)

- <span data-ttu-id="07bb5-133">No painel de detalhes do componente de interação do widget, defina a distância de interação com a distância desejada, defina a **origem da interação** como **personalizada** e para desenvolvimento, defina **Mostrar depuração** como **verdadeiro**:</span><span class="sxs-lookup"><span data-stu-id="07bb5-133">In the details panel for the Widget Interaction component, set the interaction distance to the desired distance, set the **Interaction Source** to **custom**, and for development, set **Show Debug** to **true**:</span></span>

![Captura de tela da interação do widget e das propriedades do componente de depuração](images/unreal-umg-img-09.png)

<span data-ttu-id="07bb5-135">O padrão para a origem da interação é "mundo", que deve enviar raycasts com base na posição mundial do componente de interação do widget, mas no AR e na VR isso não parece ser o caso.</span><span class="sxs-lookup"><span data-stu-id="07bb5-135">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component, but in AR and VR this does not appear to be the case.</span></span>  <span data-ttu-id="07bb5-136">Habilitar a "mostrar depuração" e adicionar um tom de foco aos widgets enquanto o desenvolvimento é importante para a sanidade verifica se o componente de interação do widget está fazendo o que você espera.</span><span class="sxs-lookup"><span data-stu-id="07bb5-136">Enabling “Show Debug” and adding a hover tint to widgets while developing is important to sanity check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="07bb5-137">A solução alternativa é usar uma fonte personalizada e definir o Raycast no grafo de eventos a partir do raio da mão.</span><span class="sxs-lookup"><span data-stu-id="07bb5-137">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="07bb5-138">Aqui, estamos chamando isso a partir do tique do evento:</span><span class="sxs-lookup"><span data-stu-id="07bb5-138">Here we are calling this from Event Tick:</span></span>

![Plano gráfico de tiques de eventos](images/unreal-umg-img-10.png)

<span data-ttu-id="07bb5-140">Em seguida, adicione eventos de ponteiro do mouse virtual ao componente de interação do widget reagindo à entrada do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="07bb5-140">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="07bb5-141">Nesse caso, envie um evento de pressionamento do mouse à esquerda quando a mão estiver segurando e um evento de liberação do mouse esquerdo quando não for compreendido:</span><span class="sxs-lookup"><span data-stu-id="07bb5-141">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Plano gráfico com eventos de ponteiro de mouse virtual adicionados](images/unreal-umg-img-13.png)

<span data-ttu-id="07bb5-143">Agora, ao implantar o aplicativo no HoloLens 2, você verá uma extensão de raio à direita do seu lado direito.</span><span class="sxs-lookup"><span data-stu-id="07bb5-143">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="07bb5-144">Se você o direcionar a uma das caixas de texto editáveis e ao toque do ar, o teclado do sistema aparecerá na frente de você e permitirá que você insira o texto.</span><span class="sxs-lookup"><span data-stu-id="07bb5-144">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="07bb5-145">O teclado do sistema do HoloLens requer um mecanismo inreal 4,26 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="07bb5-145">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="07bb5-146">Além disso, o teclado não será exibido quando seu aplicativo estiver sendo transmitido do editor inreal para o headset, somente quando o aplicativo estiver em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="07bb5-146">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="07bb5-147">Consulte Também:</span><span class="sxs-lookup"><span data-stu-id="07bb5-147">See Also:</span></span>
* [<span data-ttu-id="07bb5-148">Documentação de UMG inreal</span><span class="sxs-lookup"><span data-stu-id="07bb5-148">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="07bb5-149">Tutoriais de UMG inreais</span><span class="sxs-lookup"><span data-stu-id="07bb5-149">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
