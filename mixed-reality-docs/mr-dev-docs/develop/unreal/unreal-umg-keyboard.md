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
# <a name="umg-and-keyboard-in-unreal"></a>UMG e teclado no Unreal

O UMG (elementos gráficos de movimento inreal) é um sistema de interface do usuário interno do mecanismo não real, usado para criar interfaces como menus e caixas de texto. Interfaces de usuário criadas com UMG consistem em widgets. Nós o orientaremos na criação de um novo widget, no acréscimo ao espaço mundial e na habilitação da interação usando o teclado do sistema como um exemplo. Você pode aprender mais sobre o UMG na [documentação](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)oficial do mecanismo inreal. 

## <a name="create-a-new-widget"></a>Criar um novo widget

- Crie um gráfico de widget para definir o layout da interface do usuário do jogo:

![Captura de tela da adição de um plano gráfico do widget no menu não real](images/unreal-umg-img-01.png)

- Abra o novo Blueprint e adicione componentes da paleta à tela.  Nesse caso, adicionamos dois componentes de caixa de texto da seção "entrada":

![Captura de tela da janela de hierarquia com componente de widget de texto realçado e expandido](images/unreal-umg-img-02.png)

- Selecione um widget na janela hierarquia ou designer e modifique os parâmetros no painel de detalhes.  Nesse caso, adicionamos um "texto de dica" padrão e uma cor de tonalidade que aparece quando você passa o mouse sobre a caixa de texto.  Uma caixa de texto exibirá um teclado virtual no HoloLens quando ele estiver interagindo com:

![Captura de tela de parâmetros modificados na janela hierarquia](images/unreal-umg-img-03.png)

- Os eventos também podem ser assinados no painel de detalhes:

![Captura de tela dos eventos no painel de detalhes](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>Adicionar um widget ao espaço de mundo

- Crie um novo ator, adicione um componente de widget e adicione o ator à cena:

![Captura de tela de um ator com um widget anexado](images/unreal-umg-img-05.png)

- No painel de detalhes do widget, defina a **classe Widget** como o plano gráfico do widget criado anteriormente:

![Captura de tela do painel detalhes do plano gráfico com o conjunto de classes widget](images/unreal-umg-img-06.png)

- Para um widget de texto, verifique se a **entrada do hardware de recebimento** está desmarcada, portanto, atualizamos apenas o texto do teclado virtual:

![Captura de tela da seção de interação com entrada de hardware de recebimento está desmarcada](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Interação do widget

Os widgets do UMG normalmente recebem a entrada de um mouse.  No HoloLens ou VR, precisamos simular um mouse com um componente de interação do widget para obter os mesmos eventos.

- Crie um novo ator, adicione um componente de **interação do widget** e adicione o ator à sua cena:

![Captura de tela de um novo ator com um componente de interação do widget realçado](images/unreal-umg-img-08.png)

- No painel de detalhes do componente de interação do widget:
    - Defina a distância de interação com o valor de distância desejado
    - Definir a **origem da interação** como **personalizada**
    - Para desenvolvimento, defina **Mostrar depuração** como **true**:

![Captura de tela da interação do widget e das propriedades do componente de depuração](images/unreal-umg-img-09.png)

O padrão para a origem da interação é "mundo", que deve enviar raycasts com base na posição mundial do componente de interação do widget. No AR e VR, esse não é o caso.  Habilitar a "mostrar depuração" e adicionar um tom de foco aos widgets é importante para verificar se o componente de interação do widget está fazendo o que você espera.  A solução alternativa é usar uma fonte personalizada e definir o Raycast no grafo de eventos a partir do raio da mão.  

Aqui, estamos chamando isso a partir do tique do evento:

![Plano gráfico de tiques de eventos](images/unreal-umg-img-10.png)

Em seguida, adicione eventos de ponteiro do mouse virtual ao componente de interação do widget reagindo à entrada do HoloLens.  Nesse caso, envie um evento de pressionamento do mouse à esquerda quando a mão estiver segurando e um evento de liberação do mouse esquerdo quando não for compreendido:

![Plano gráfico com eventos de ponteiro de mouse virtual adicionados](images/unreal-umg-img-13.png)

Agora, ao implantar o aplicativo no HoloLens 2, você verá uma extensão de raio à direita do seu lado direito. Se você o direcionar a uma das caixas de texto editáveis e ao toque do ar, o teclado do sistema aparecerá na frente de você e permitirá que você insira o texto. 
 
> [!NOTE]
> O teclado do sistema do HoloLens requer um mecanismo inreal 4,26 ou posterior. Além disso, o teclado não será exibido quando seu aplicativo estiver sendo transmitido do editor inreal para o headset, somente quando o aplicativo estiver em execução no dispositivo.

## <a name="see-also"></a>Consulte Também:
* [Documentação de UMG inreal](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Tutoriais de UMG inreais](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
