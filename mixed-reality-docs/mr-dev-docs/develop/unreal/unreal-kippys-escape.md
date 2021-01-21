---
title: A criação do escape do Kippy
description: Acompanhe conosco ao explorarmos a criação do aplicativo de realidade misturada de escape do Kippy para o HoloLens 2 em um mecanismo inreal.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, implantar em dispositivo, PC, documentação, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: eca0b12cd9ba4e3d5d4033790184ffd770b44280
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635394"
---
# <a name="the-making-of-kippys-escape"></a>A criação do escape do Kippy

Kippy o robô é ativado para se encontrar em uma ilha. Cabe a você colocar sua solução de problemas para ajudá-lo a encontrar um caminho de volta para seu Rocket Ship! A tira do seu HoloLens 2 e [Baixe o aplicativo](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) do Microsoft Store ou clone o [repositório](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) do GitHub e obtenha o Kippy Home Safe!  

> [!IMPORTANT]
> Verifique se você está usando o **mecanismo não real 4,25 ou posterior** se estiver compilando o escape do Kippy no repositório github.

O escape do Kippy é um aplicativo de exemplo do [HoloLens 2](/hololens/hololens2-hardware) de software livre criado com as ferramentas de UX inreal do mecanismo 4 e [da realidade misturada para o inreal](https://github.com/microsoft/MixedReality-UXTools-Unreal). Nesta postagem, vamos orientá-lo pelo processo dos primeiros princípios e Design Visual para implementar e otimizar a experiência. Você pode encontrar mais informações sobre como desenvolver aplicativos de realidade misturada com as ferramentas do MRTK UX na [visão geral do desenvolvimento inreal](unreal-development-overview.md).

## <a name="first-principles"></a>Primeiros princípios 

Na configuração para criar o escape do Kippy, nosso objetivo era criar uma experiência que realçasse o [suporte do hololens 2 do mecanismo inreal](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), os recursos do hololens 2 e o kit de ferramentas de realidade misturada. Queríamos inspirar os desenvolvedores a imaginar o que poderiam criar com o inreal e o HoloLens 2.  

Nós chegamos a três princípios de orientação para a experiência: que precisa ser divertido, interativo e ter uma barreira baixa para entrar. Queríamos que a experiência seja intuitiva o suficiente, até mesmo um usuário de realidade misturada pela primeira vez não precisará de um tutorial para passar por ele.  

## <a name="designing-the-game"></a>Projetando o jogo 

O HoloLens 2 tem acesso aos recursos de design encontrados em qualquer lugar no jogo hoje. Os objetos podem ser enviados por Push ou manipulados diretamente usando suas mãos ou direcionados com acompanhamento de olho. Esses recursos principais estão por trás de algum tempo divertido que criamos no escape do Kippy.  

Usando os recursos exclusivos do HoloLens 2 como orientação para nosso design de jogos, fizemos um escopo de alguns cenários de ambiente pequeno. As ilhas faziam sentido porque podem ser ajustadas para diferentes alturas do jogador e fornecer ideias de ponte divertidas. Nós descarregoumos o tema de Civilization antigo que cumprem a tecnologia Sci-Fi, com a ideia de que alguém tinha criado máquinas sobre ruins aproveitando uma energia estranha fornecida por cada ilha. As ilhas eram cada uma dada à aparência própria, um detalhe que ajudou a criar interesse visual. Um bom equilíbrio entre modelagem e texturing manteria as chamadas de desenho baixas para o desempenho de renderização, de modo que uma aparência estilizada foi projetada com isso em mente. 

![O design inicial de jogos esboça ](images/kippys-escape/kippys-escape-img-01.png)
 *alguns esboços iniciais sobre a aparência da experiência*

![Renderizações dos renderizadores da segunda ilha ](images/kippys-escape/kippys-escape-img-02.png)
 *da segunda ilha*

Para manter em nossa programação de produção curta, concordamos que um caractere flutuante poderia capturar intenções e emoções sem ciclos de animação rigorosos. Kippy nasceu! Ele emotes algumas expressões diferentes por meio de seus olhos e por meio de efeitos de som vocal mínimos para ajudar a orientar o Player durante toda a experiência. 

![Kippy mostrando expressões diferentes por seus olhos](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy mostrando expressões diferentes por seus olhos*

![Se o usuário levar muito tempo para resolver um quebra-cabeça, Kippy dará ao usuário uma dica](images/kippys-escape/kippys-escape-img-04.gif)

*Se o usuário levar muito tempo para resolver um quebra-cabeça, Kippy dará ao usuário uma dica*

Além do design de caractere e de ambiente, fizemos um esforço em conjunto para fazer com que o jogo fique divertido. O controle ocular nos permitiu disparar os atributos material e Sound, que realçaram as principais partes do jogo. O áudio espacial ajudou a fazer com que os níveis se sintam em casa no ambiente do jogador. Ser capaz de captar objetos, botões de ação e manipular controles deslizantes impulsiona contratos de jogador inovadores. Era importante ter certeza de que esses pontos de conexão pareciam naturais. 

![O fim do cabo da ponte é brilho quando a mão do usuário se aproxima dele](images/kippys-escape/kippys-escape-img-05.gif)

*O fim do cabo da ponte é brilho quando a mão do usuário se aproxima dele*

## <a name="building-the-game-mechanics"></a>Criando a mecânica do jogo 

O escape do Kippy depende muito de componentes de ferramentas de UX da realidade misturada para tornar o jogo interativo – ou seja, os atores, controles associados, manipuladores, controles deslizantes e botões.   

O [ator de interação manual](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) permite a manipulação direta e longe de hologramas. No início do escape do Kippy, o usuário terá a oportunidade de definir o local do jogo. As emissões de mão que se estendem da palma do usuário facilitam a manipulação de hologramas grandes que estão distantes, como visto no gif abaixo.  

![Gif do ator de interação manual](images/kippys-escape/kippys-escape-img-06.gif)

A própria cena de espaço reservado pode ser arrastada e girada usando componente de [controle de limites](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) de ferramentas de UX.  

Na segunda ilha, o usuário deve selecionar Gems e colocá-las em seus slots correspondentes. Os Gems têm os [manipuladores](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) anexados a eles que permitem que o usuário os pegue e os coloque. 

![Gif de exemplo de manipulador](images/kippys-escape/kippys-escape-img-07.gif)

Um [botão pressionável](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) é a chave para colocar o bombas para uso na terceira ilha.  

![Gif de exemplo de botão pressionável](images/kippys-escape/kippys-escape-img-08.gif)

Um componente [Slider](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) aparece na quarta ilha, disparando a ponte final a ser gerada.  

![Exemplo de componente de controle deslizante gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Otimizando para o HoloLens 2 

Com qualquer experiência criada para ser executada em um dispositivo móvel, manter-se atento ao desempenho é essencial. O inreal 4,25 inclui uma atualização importante para dar suporte a várias exibições móveis, o que reduz significativamente a sobrecarga de renderização e aumenta a taxa de quadros. É recomendável verificar nossas outras [configurações de desempenho recomendadas](performance-recommendations-for-unreal.md) para desenvolvimento de HoloLens 2 com inreal quando você está otimizando.  

Os objetos de física ainda permanecem caros para o desempenho, portanto, algumas soluções alternativas inteligentes foram usadas. Por exemplo, a terceira "ponte" requer a sopro de alguns resíduos que bloqueiam o Stairway. Em vez de ter um impacto forçado nas pedras como objetos de física, o bomba denotação dispara uma permuta, alternando as pedras estáticas para um efeito de partículas explodida. 

![Exemplo otimizado para GIF 2 do HoloLens](images/kippys-escape/kippys-escape-img-10.gif) 

Também reduzimos nossas chamadas de desenho de mais de 400 para ~ 260: 
* Reduzindo a complexidade da malha
* Combinando malhas
* Removendo alguns dos nossos elementos de iluminação dinâmica inicial

Embora seja muito provável que possamos ter feito, achamos que foi um bom equilíbrio entre desempenho e qualidade visual.  

## <a name="try-it-out"></a>Experimente! 

Inicialize o seu HoloLens 2 e [Baixe](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) o aplicativo do Microsoft Store, ou clone o [repositório](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) do GitHub e crie o aplicativo por conta própria!  

## <a name="about-the-team"></a>Sobre a equipe

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack-Caron</b><br><i>Designer de jogo líder</i><br>Atualmente, a Jack trabalha em experiências de realidade mista para a Microsoft, incluindo projetos do HoloLens 2 e AltspaceVR, e era um designer da equipe da plataforma do HoloLens.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Wu de verão</b><br><i>Produtor</i><br>O verão funciona na plataforma de desenvolvedor da realidade misturada e tem como mente os esforços relacionados ao mecanismo não real da equipe.</td>
</tr>
</table>

Obrigado especial aos nossos amigos em [Framestore](https://www.framestore.com/) para nos ajudar a dar vida ao Kippy de escape. Desde o desenvolvimento de caracteres até o design de ativos até a programação de jogos, a colaboração desse projeto era dinamizada.