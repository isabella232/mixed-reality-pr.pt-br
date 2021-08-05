---
title: Usar som espacial em aplicativos de realidade misturada
description: O som espacial é uma ferramenta poderosa para imersão, acessibilidade e design de UX em aplicativos de realidade misturada.
author: kegodin
ms.author: v-hferrone
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, som espacial, design, estilo, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, gestos, interações, atenuação
ms.openlocfilehash: 687811f23e11cadf6e75129098c9feb0393009f819eb961cf2f55a3208cc5f96
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208956"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>Como usar o som em aplicativos de realidade mista

Você pode usar o som para informar e reforçar o modelo mental do usuário do estado do aplicativo. Use a espacial, quando apropriado, para inserir sons no mundo de realidade misturada. Ao conectar a auditoria e o Visual dessa forma, você aprofunda a natureza intuitiva das interações e aumenta a confiança do usuário.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>Quando adicionar sons

Aplicativos de realidade misturada geralmente têm uma necessidade maior de som do que aplicativos 2D, devido à falta de uma interface tactile. Adicione sons quando informar ao usuário ou reforçar as interações.

### <a name="inform-and-reinforce"></a>Informar e reforçar

* Para eventos que não são iniciados pelo usuário, como notificações, use o som para informar ao usuário que ocorreu uma alteração.
* As interações podem ter vários estágios. Use o som para reforçar as transições de estágio.

Consulte os exemplos de interações, eventos e características de som sugeridos a seguir.

### <a name="exercise-restraint"></a>Retentor exercício

Os usuários não têm uma capacidade ilimitada para informações de áudio.
* Cada som deve comunicar informações valiosas e específicas.
* Quando seu aplicativo toca um som para informar o usuário, reduza temporariamente o volume de outros sons.
* Para sons de botão de mouse (consulte as informações a seguir), adicione um atraso de tempo para evitar o disparo excessivo de som.

### <a name="dont-rely-solely-on-sounds"></a>Não confie exclusivamente em sons

Os sons que são usados bem são valiosos para os usuários. Mas certifique-se de que seu aplicativo é utilizável mesmo com o som desativado.
* Os usuários podem estar com deficiência auditiva.
* Seu aplicativo pode ser usado em um ambiente alto.
* Os usuários podem ter preocupações de privacidade ou outros motivos para desabilitar o áudio do dispositivo.

## <a name="how-to-sonify-interactions"></a>Como sonify interações

Os tipos de interação na realidade misturada incluem gesto, manipulação direta e voz. Use as características sugeridas a seguir para selecionar ou criar sons para essas interações.

### <a name="gesture-interactions"></a>Interações de gesto

Em realidade misturada, os usuários podem interagir com botões usando um mouse. As ações de botão geralmente ocorrem quando o usuário libera, em vez de pressionar o botão para dar ao usuário a oportunidade de cancelar a interação. Use sons para reforçar esses estágios. Para ajudar os usuários a se destinarem a botões distantes, considere também o uso de um som focalizado em ponteiro.
* Botão-pressionar sons deve ser curto, tactile "clique".<br/>Exemplo: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Botão-"Inpress" sons deve ter uma aparência tactile semelhante. Uma densidade mais alta do que a prensa tipográfica reforça a sensação de conclusão.<br/>Exemplo: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* Para sons de foco, considere usar um som sutil e não ameaçante, como um Thud ou um choque de baixa frequência.

### <a name="direct-manipulation"></a>Manipulação direta

no HoloLens 2, o controle de mão articulado dá suporte à manipulação direta de elementos de interface do usuário. Os sons são importantes quando não há outros comentários físicos.

Um som de *pressionamento de botão* é importante porque o usuário não recebe nenhuma outra indicação quando chega à parte inferior do traço de chave. Indicadores de som de viagem de chave podem ser pequenos, sutis e obstruído. Assim como ocorre com interações de gesto, os pressionamentos de botão devem ter um som curto, tactile, como um clique. As reimpressões devem ter um som de clique semelhante, mas com densidade elevada.
* Exemplo: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Exemplo: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

É difícil confirmar visualmente uma ação de captação ou liberação. A mão do usuário geralmente estará no caminho de qualquer efeito visual, e os objetos apto para não têm uma analogia visual do mundo real de "captação". Os sons podem comunicar efetivamente as interações de captura e liberação bem-sucedidas.
* As ações de captura devem ter um som de tactile curto e um pouco muffled que solicite a ideia de fechamento de um objeto. Às vezes, há também um som "whoosh" que leva até o som de captação para comunicar o movimento do lado.<br/>Exemplo: [MRTK_Move_Start. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* As ações de liberação devem ter um som tactile e curto. Isso geralmente é mais baixo do que o som de captura e na ordem inversa, com um impacto e, em seguida, um "whoosh" para se comunicar que o objeto está sendo liquidado no lugar.<br/>Exemplo: [MRTK_Move_End. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Uma interação de *desenho* deve obter um som persistente, em loop com o volume determinado pelo movimento da mão do usuário. Ele deve ser silencioso quando a mão do usuário ainda estiver e mais alta quando a mão estiver se movendo rapidamente.

### <a name="voice-interactions"></a>Interações de voz

As interações de voz geralmente têm elementos visuais sutis. Use sons para reforçar os estágios de interação. Talvez você queira usar sons com mais tons para diferenciá-los dos sons de gesto e de manipulação direta.

* Use um tom de som positivo para *confirmações* de comando de voz. Os tons crescentes e os principais intervalos musicais entram em vigor.
* Use um tom de som menor e menos positivo para *falhas* de comando de voz. Evite sons negativos. Em vez disso, use um som mais percussive, neutro para comunicar que o aplicativo está se movendo da interação.
* Se seu aplicativo tiver uma palavra de ativação, use um tom curto e AdaBoost quando o dispositivo *começar a escutar*. Use um som de loop sutil enquanto o aplicativo *estiver* ouvindo.

### <a name="notifications"></a>Notificações

As notificações sinalizam alterações no estado do aplicativo e outros eventos que o usuário não iniciou. As alterações de estado podem incluir conclusões de processo, mensagens e chamadas telefônicas.

Em realidade misturada, os objetos às vezes se movem para fora do campo de exibição do usuário. Emparelhe a movimentação de *objetos animados* com um som espacial que depende do tipo de objeto e da velocidade de movimento.
* Ele ajuda a reproduzir um som espacial no final de uma animação para informar o usuário sobre a nova posição do objeto.
* Para movimentos graduais, um som "whoosh" durante a movimentação ajuda o usuário a controlar o objeto.

Os sons de *notificação de mensagem* podem ser ouvidos repetidamente, às vezes em uma rápida sucessão. É importante que eles não se destaquem. Os sons de tons positivos do intervalo médio entram em vigor.

* Os sons de chamada de entrada devem ter qualidades semelhantes a um toque de telefone celular. Esses sons estão em loop de frases musicais que são executadas até que o usuário responda à chamada.
* A conexão de comunicação de voz e a desconexão devem ter um som tonal curto. O som de conexão deve ser um tom positivo para indicar uma conexão bem-sucedida. O som de desconexão deve ser um som neutro para indicar a conclusão da chamada.

## <a name="handle-spatialization"></a>A espacial da manipulação

A espacialização usa fones estéreo ou alto-falantes para inserir sons no mundo de realidade misturada.

### <a name="which-sounds-to-spatialize"></a>O que parece ter uma espacial

Um som deve ser espacial quando estiver associado a um evento que tenha um local espacial. Isso inclui a interface do usuário, as vozes de ia incorporadas e os indicadores visuais.

Espacialize os elementos da *interface do usuário* para ajudar a confundir o "espaço" do Sonic do usuário, limitando o número de sons estéreo que eles ouvem. As interações de manipulação, como toque, captura e liberação, se sentem mais naturais quando os comentários de áudio são espaciais. Considere as seguintes informações sobre a atenuação de distância para esses elementos.

Espaciale os *indicadores visuais* e as *vozes de ia incorporadas* para informar os usuários de forma intuitiva quando essas coisas estiverem fora do campo de exibição.
    
Por outro lado, evite a espacialização para *vozes de ia sem face* e outros elementos que não têm um local espacial bem definido. A espacialização sem um elemento visual relacionado pode distrair os usuários de pensar que há um elemento visual que ele não pode localizar.

A espacialização vem com algum custo de CPU. Muitos aplicativos têm no máximo dois sons reproduzidos simultaneamente. O custo da espacial nesse caso provavelmente é insignificante. Você pode usar o monitor de taxa de quadros MRTK para avaliar o impacto da adição de espacial.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>Quando e como aplicar atenuação baseada em distância

No mundo físico, os sons mais distantes são mais silenciosos. O mecanismo de áudio pode modelar essa atenuação com base na distância de origem. Use a atenuação baseada em distância ao comunicar informações relevantes.

As distâncias para *indicadores visuais*, *hologramas animados* e outros sons informativos são relevantes para o usuário. Use atenuação baseada em distância para fornecer indicações intuitivas.

Ajuste a curva de atenuação de cada fonte para se ajustar ao tamanho dos espaços do mundo de realidade misturada. A curva padrão do mecanismo de áudio geralmente é destinada a espaços grandes (até metade de Kilometer).

Sons que reforçam os *estágios progressivos de ações de botão* e outras interações não devem ter a atenuação aplicada. Os efeitos de reforçamento desses sons são mais importantes do que comunicar a distância com o botão. As variações podem ser discadas, especialmente com teclados, quando muitos cliques de botão podem ser ouvidos sucessivamente.

### <a name="which-spatialization-technology-to-use"></a>Qual tecnologia de espacial deve ser usada

com os fones de ouvido ou os alto-falantes de HoloLens, use tecnologias de espacial com base em HRTF (função de transferência relacionada à carga). Essas tecnologias modelam a propagação sonora em toda a cabeça do mundo físico. Mesmo quando uma fonte de som está no lado distante do cabeçalho de um, o som é propagado para o Ear distante com algumas atenuações e atrasos. O movimento panorâmico do orador depende apenas da atenuação e aplica a atenuação total no Ear esquerdo quando sons estão no lado direito e o contrário. Essa técnica pode ser desconfortável para ouvintes "audição normais" e inacessíveis para ouvintes que têm deficiência auditiva em um Ear.

## <a name="next-steps"></a>Próximas etapas

* [Usar som espacial no Unity](../develop/unity/spatial-sound-in-unity.md)
* [Estudo de caso do Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Estudo de caso do HoloTour](case-study-spatial-sound-design-for-holotour.md)
