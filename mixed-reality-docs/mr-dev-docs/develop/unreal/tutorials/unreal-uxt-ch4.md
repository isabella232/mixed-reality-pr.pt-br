---
title: 4. Como tornar sua cena interativa
description: Parte 4 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 771dd4028adfacb27544e632aa0f355d3bc91c66
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712585"
---
# <a name="4-making-your-scene-interactive"></a>4. Como tornar sua cena interativa

No tutorial anterior, você adicionou um ARSession, um Peão e um Modo de Jogo para concluir a configuração de realidade misturada para o aplicativo de xadrez. Esta seção concentra-se no plug-in de software livre [Ferramentas de UX do Kit de Ferramentas de Realidade Misturada](https://github.com/microsoft/MixedReality-UXTools-Unreal), que oferece ferramentas para tornar sua cena interativa. Ao final desta seção, as peças de xadrez serão movidas pela entrada do usuário.

## <a name="objectives"></a>Objetivos

* Instalação do plug-in das Ferramentas de UX de Realidade Misturada
* Como adicionar Atores de Interação à Mão às pontas dos seus dedos
* Como criar e adicionar manipuladores a objetos na cena
* Como usar simulação de entrada para validar o projeto

## <a name="downloading-the-mixed-reality-ux-tools-plugin"></a>Baixar o plug-in das Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
Antes de começar a trabalhar com a entrada do usuário, você precisa adicionar o plug-in das Ferramentas de UX de Realidade Misturada ao projeto. Para saber mais sobre as Ferramentas de UX, confira o projeto no [GitHub](https://aka.ms/uxt-unreal).

1. Abra o Epic Games Launcher. Navegue até o Marketplace do Unreal Engine e pesquise "[Ferramentas de UX de Realidade Misturada](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)". Instale o plug-in em seu mecanismo.

![Marketplace do Unreal](images/unreal-uxt/2-uxt-plugin.PNG)

2. Retorne ao editor do Unreal, acesse as **Configurações de projeto** > **Plug-ins** e pesquise "Ferramentas de UX de Realidade Misturada". Verifique se o plug-in está ativado e reinicie o editor, se solicitado.

![Ativação do plug-in de Ferramentas de UX de Realidade Misturada](images/unreal-uxt/2-enable-uxt.PNG)

3.  O plug-in UXTools fornece uma pasta Conteúdo com subpastas para componentes, incluindo **Botões**, **Simulação de XR** e **Ponteiros**, bem como uma pasta Classes C++ com um código adicional.  

> [!NOTE]
> Se a seção **Conteúdo do UXTools** não aparecer em **Navegador de conteúdo**, clique em **Visualizar opções > Mostrar conteúdo do mecanismo**.

![Mostrar conteúdo do mecanismo](images/unreal-uxt/4-showenginecontent.PNG)

Encontre a documentação adicional do plug-in no [repositório](https://aka.ms/uxt-unreal) GitHub das Ferramentas de Experiência de Usuário de Realidade Misturada.

Com o plug-in instalado, você está pronto para começar a usar as ferramentas que ele tem a oferecer, começando com os atores de interação à mão.

## <a name="spawning-hand-interaction-actors"></a>Como gerar Atores de Interação à Mão

A interação da mão com elementos de Experiência de Usuário é feita com Atores de Interação da Mão, que criam e orientam os ponteiros e os visuais para interações próximas e distantes.
- *Interações próximas*: pinçar os elementos entre o dedo indicador e o polegar ou cutucá-los com a ponta do dedo.
- *Interações distantes*: apontar um raio da mão virtual para um elemento e pressionar o indicador e o polegar juntos.

Em nosso caso, adicionar um Ator de Interação Manual a **MRPawn** vai:
- Adicionar um cursor às pontas dos dedos indicadores do peão.
- Fornecer eventos de entrada com a mão articulada, que podem ser manipulados por meio do peão.
- Permita eventos de entrada de interação distante por meio de raios de mão, que se estendem das palmas das mãos virtuais.

Recomendamos ler a [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) sobre interações das mãos antes de prosseguir.

Quando você estiver pronto, abra o Blueprint **MRPawn** e navegue até o **Grafo de Eventos**.

1. Arraste o marcador de execução do **Evento BeginPlay** e solte-o para criar um nó no local desejado.
    * Selecione **Gerar Ator Com Base em Classe**, clique na lista suspensa próxima ao marcador **Classe** e pesquise por **Ator de Interação à Mão Uxt**.  

2. Gere um segundo **Ator de Interação à Mão Uxt**, desta vez definindo a **Mão** como **Direita**. Quando o evento for iniciado, um Ator de Interação à Mão Uxt será gerado em cada mão.

Seu **Grafo do Eventos** deve corresponder à seguinte captura de tela:

![Gerar Atores de Interação à Mão UXT](images/unreal-uxt/4-spawnactor.PNG)

Ambos os Atores de Interação à Mão Uxt precisam de proprietários e locais de transformação inicial. A transformação inicial não importa nesse caso, pois as Ferramentas de Experiência de Usuário farão com que os Atores de Interação da Mão passem para as mãos virtuais assim que elas estiverem visíveis. No entanto, a função `SpawnActor` requer uma entrada de Transformação para evitar um erro de compilador, então você usará os valores padrão.

1. Arraste o marcador de um dos marcadores **Gerar Transformação** e solte-o para criar um nó no local desejado.
    * Procure o nó **Efetuar Transformação** e, em seguida, arraste o **Valor Retornado** para o pino **Gerar Transformação** da outra mão para que ambos os nós **SpawnActor** sejam conectados.

2.  Selecione a **seta para baixo** na parte inferior de ambos os nós **SpawnActor** para revelar o marcador **Proprietário**.    
    * Arraste o pino de um dos pinos **Proprietário** e solte-o para posicionar um novo nó.
    * Pesquise **self** e selecione a variável **Obter uma referência a self**.
    * Crie um vínculo entre o nó de referência do objeto **Self** e o outro marcador **Proprietário** do Ator de Interação da Mão.
3. Por fim, marque a caixa **Mostrar o Cursor Próximo aos Destinos de Captura** para os Atores de Interação da Mão. Um cursor será exibido no destino de captura, à medida que o seu dedo indicador se aproximar, de modo que você possa ver em que local o dedo é relativo ao destino.
    * **Compile**, **salve** e retorne para a Janela principal.

Verifique se as conexões correspondem à captura de tela a seguir, mas fique à vontade para arrastar os nós a fim de tornar o Blueprint mais legível.

![Configuração de Ator de Interação à Mão UXT completa](images/unreal-uxt/4-fingerptrs.PNG)

Encontre mais informações sobre os Atores de Interação da Mão na [documentação das Ferramentas de Experiência de Usuário](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html).

Agora, as mãos virtuais no projeto têm uma forma de selecionar objetos, mas ainda não podem manipulá-los. Sua última tarefa antes de testar o aplicativo é adicionar componentes de Manipulador aos atores na cena.

## <a name="attaching-manipulators"></a>Como anexar manipuladores

Um manipulador é um componente que responde à entrada de mão articulada e pode ser pego, girado e traduzido. Aplicar a transformação do Manipulador a uma transformação de Atores permite a manipulação direta do Ator.

1. Abra o blueprint **Tabuleiro**, clique em **Adicionar Componente** e pesquise por **Manipulador Genérico Uxt** no painel **Componentes**.

![Adicionar manipulador genérico](images/unreal-uxt/4-addmanip.PNG)

2. Expanda a seção **Manipulador Genérico** no painel **Detalhes**. Nela, você pode definir a manipulação de uma ou duas mãos, o modo de rotação e a suavização. Selecione os modos que quiser e, em seguida, **Compile** e **Salve** o Board.

![Definir o modo](images/unreal-uxt/4-setrotmode.PNG)

3. Repita as etapas acima para o Ator **WhiteKing**.

Encontre mais informações sobre os Componentes do Manipulador fornecidos no plug-in das Ferramentas de Experiência de Usuário de Realidade Misturada na [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html).

## <a name="testing-the-scene"></a>Como testar a cena

Boa notícia para todos! Você está pronto para testar o aplicativo com as novas mãos virtuais e entrada do usuário dele. Clique em **Jogar** na Janela principal e você verá duas mãos de malha com raios se estendendo da palma de cada mão. Você pode controlar as mãos e as respectivas interações da seguinte maneira:
- Mantenha pressionada a tecla **Alt esquerda** para controlar a **mão esquerda** e a tecla **Shift esquerda** para controlar a **mão direita**.
- Mova o cursor do mouse para mover a mão e use o **botão de rolagem do mouse** para mover a mão **para frente** ou **para trás**.
- Use o botão esquerdo do mouse para **pinçar** e o botão do meio do mouse para **cutucar**.

> [!NOTE]
> A simulação de entrada poderá não funcionar se você tiver vários headsets conectados a seu PC. Se você estiver com problemas, experimente desconectar os outros headsets.

![Mãos simuladas no visor](images/unreal-uxt/4-handsim.PNG)

Tente usar as mãos simuladas para pegar, mover e posicionar o rei branco do xadrez e manipular o tabuleiro! Faça experimentos com a interação próxima e distante. Observe que, quando as mãos ficam próximas o suficiente para pegar o tabuleiro e o rei diretamente, um cursor na ponta do dedo indicador substitui o raio de mão.

Você pode obter mais informações sobre o recurso de mãos simuladas fornecido pelo plug-in Ferramentas de UX do MRTK na [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html).

Agora que suas mãos virtuais podem interagir com objetos, você está pronto para passar para o próximo tutorial e adicionar interfaces do usuário e eventos.

[Próxima seção: 5. Como adicionar um botão e redefinir locais de peças](unreal-uxt-ch5.md)
