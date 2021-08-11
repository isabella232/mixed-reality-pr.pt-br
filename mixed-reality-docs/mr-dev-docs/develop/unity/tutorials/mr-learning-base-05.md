---
title: Criar conteúdo dinâmico usando Solucionadores
description: Este curso mostra como usar os solucionadores do MRTK (Kit de Ferramentas de Realidade Misturada) para criar um conteúdo dinâmico.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, solucionadores
ms.localizationpriority: high
ms.openlocfilehash: 3060e6f6b1e04f356f2b9d7466c0f8f3481c53ba090f6d8a62405a4da3dc21a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221182"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5. Criar conteúdo dinâmico usando Solucionadores

Neste tutorial, você vai explorar maneiras de posicionar hologramas dinamicamente usando as ferramentas de posicionamento disponíveis do MRTK, conhecidas como Solucionadores, para resolver cenários de posicionamento espacial complexos. No MRTK, os Solucionadores são um sistema de scripts e comportamentos usados para permitir que os objetos sigam você, o usuário ou outros objetos do jogo na cena. Eles também podem ser usados para se ajustar a determinadas posições, tornando seu aplicativo mais intuitivo.

## <a name="objectives"></a>Objetivos

* Apresentar os Solucionadores do MRTK
* Saiba como usar os solucionadores para direcionar o usuário para objetos
* Saiba como usar os solucionadores para reposicionar objetos

## <a name="location-of-solvers-in-the-mrtk"></a>Localização dos Solucionadores no MRTK

 Os Solucionadores do MRTK estão localizados na pasta MRTK SDK. Para ver os Solucionadores disponíveis no seu projeto, na janela Projeto, navegue até **Pacotes** > **Mixed Reality Toolkit Foundation** > **SDK** > **Recursos** > **Utilitários** > **Solucionadores**:

![Janela Projeto do Unity com a pasta Solucionadores selecionada](images/mr-learning-base/base-05-section1-step1-1.png)

Neste tutorial, examinaremos a implementação do Solucionador de Indicador Direcional e o Solucionador Toque para Posicionar. Para saber mais sobre a gama completa de Solucionadores disponíveis no MRTK, você pode consultar o guia [Solucionadores](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) no [Portal de Documentação do MRTK](/windows/mixed-reality/mrtk-unity).

> [!NOTE]
> O Solucionador de Indicador Direcional não está localizado nas pastas de Solucionadores supramencionadas, mas nas pastas Pacotes > Mixed Reality Toolkit Foundation > SDK > Experimental > Recursos > Utilitários, pois é um recurso experimental.

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>Como usar o Solucionador de Indicador Direcional para direcionar o usuário a objetos

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-Fabricados**, clique e arraste o pré-fabricado **Divisa** para a janela Hierarquia e defina sua **Posição** de Transformação como X = 0, Y = 0, Z = 2 para posicioná-lo perto do objeto RoverExplorer:

![Unity com o pré-fabricado Divisa recém-adicionado selecionado](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> Se você descobrir que a câmera ou quaisquer outros ícones em sua cena estão ocultando os objetos ou causando distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição Desligado, conforme mostra a imagem acima. Para saber mais sobre o menu Gizmos e como você pode usá-lo para otimizar a exibição de cena, consulte a documentação do <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu Gizmos</a> do Unity.

Renomeie o objeto Chevron recém-adicionado para **Indicador** e na janela Inspetor, use o botão **Adicionar componente** para adicionar **DirectionalIndicator**:

![Unity com o componente do solucionador DirectionalIndicator adicionado](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> Quando você adiciona um solucionador, nesse caso, o componente DirectionalIndicator, o componente SolverHandler é adicionado automaticamente porque os solucionadores exigem isso.

Configure os componentes DirectionalIndicator e SolverHandler da seguinte maneira:

* Verifique se o **Tipo de Destino Rastreado** do componente **SolverHandler** está definido como **Cabeça**
* Atribua o **RoverExplorer** ao **Destino Direcional** do componente **DirectionalIndicator** arrastando-o da janela hierarquia para o campo **Nenhum (Transformação)**
* Altere o **Deslocamento de Exibição** para 0,2

![Unity com o componente do solucionador DirectionalIndicator configurado](images/mr-learning-base/base-05-section2-step1-3.png)

Pressione o botão Reproduzir para entrar no modo Jogo, pressione e mantenha o botão direito do mouse pressionado enquanto move o mouse para a esquerda ou para a direita para girar a direção do foco e observe o seguinte:

* Quando você olhar para longe do objeto RoverExplorer, o objeto de Indicador será exibido e apontará para o objeto RoverExplorer

![Modo de exibição dividida do Modo de reprodução do Unity com o solucionador DirectionalIndicator em uso](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> Se você não vir o raio da câmera na janela Cena, verifique se o menu Gizmos está habilitado, como mostra a imagem acima.

> [!TIP]
> Para saber como usar a simulação de entrada no editor, você pode consultar o guia [Como usar a simulação de entrada de mão no editor para testar uma cena](/windows/mixed-reality/mrtk-unity/features/input-simulation/input-simulation-service) no [Portal de documentação do MRTK](/windows/mixed-reality/mrtk-unity).

> [!TIP]
> Se o computador tiver um microfone, você poderá alternar facilmente o estado ativo do painel Diagnóstico que aparece na janela Jogo usando o comando de fala "alternar diagnóstico". Como alternativa, você pode desabilitá-lo no Perfil de Configuração do MRTK > Diagnóstico > Habilitar o Sistema de Diagnóstico. No entanto, geralmente é recomendável manter o Sistema de Diagnóstico ativo durante o desenvolvimento.

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>Usando o Solucionador Tocar para Posicionar para reposicionar objetos

Na janela hierarquia, selecione o objeto RoverExplorer > **RoverAssembly** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Tocar para Posicionar (Script)** e configure-o da seguinte maneira:

* Verifique se o **Tipo de Destino Rastreado** do componente **SolverHandler** está definido como **Cabeça**
* Desmarque a opção **Usar Deslocamento Normal da Superfície Padrão** e verifique se o **Deslocamento Normal da Superfície** está definido como 0
* Marque a caixa de seleção **Manter Orientação Vertical**
* No menu suspenso **Superfícies Magnéticas** > **Elemento 0**, desmarque todas as opções que esperam **Reconhecimento Espacial**

![Unity com o componente do solucionador TapToPlace adicionado e configurado](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> A configuração de Superfícies Magnéticas determina quais objetos o componente Tocar para Posicionar (Script) pode detectar ao posicionar um objeto. Ao alterar a configuração para Somente Reconhecimento Espacial, o componente Tocar para Posicionar (Script) só poderá posicionar o Rover em objetos na camada do Unity denominada Reconhecimento Espacial, que, por padrão, é a Malha de Conscientização Espacial gerada pelo HoloLens.
>
> Para saber mais sobre Camadas, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Camadas</a> do Unity.

> [!TIP]
> Se você quiser ver a malha de conscientização espacial ao testar a funcionalidade Tocar para Posicionar em seu HoloLens, poderá definir temporariamente a Opção de Exibição do Observador de Malha Espacial como Visível. Para obter um lembrete sobre como alterar a Opção de Exibição, você pode consultar as instruções de [Como alterar a opção de exibição de conscientização espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).

Com o objeto RoverAssembly ainda selecionado na janela Hierarquia, na janela Inspetor, localize o evento **On Placing Started ()** e clique no ícone **+** para adicionar um evento:

![Unity com o evento TapToPlace OnPlacingStarted adicionado](images/mr-learning-base/base-05-section3-step1-2.png)

Configure o evento da seguinte maneira:

* Atribua o objeto **RoverAssembly** como um ouvinte para o evento On Placing Started () arrastando-o da janela Hierarquia para o campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **TapToPlace** > **float SurfaceNormalOffset** para atualizar o valor da propriedade SurfaceNormalOffset quando o evento é disparado
* Verifique se o argumento está definido como **0**

![Unity com o evento TapToPlace OnPlacingStarted configurado](images/mr-learning-base/base-05-section3-step1-3.png)

Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Objeto 3D** > **Cubo**, para criar um objeto temporário que representa o aterramento e configure o componente **Transformação** da seguinte maneira:

* **Posição**: X = 0, Y = -1,65, Z = 6
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala**: X = 10, Y = 0,2, Z = 10

![Unity com o objeto de cubo de chão temporário adicionado e posicionado](images/mr-learning-base/base-05-section3-step1-4.png)

Com o Cubo temporário ainda selecionado na janela Hierarquia, na janela Inspetor, use a lista suspensa **Camadas** para alterar a configuração de camada do cubo apenas para incluir a camada **Conscientização Espacial**:

![Unity com a Camada de objeto de cubo de chão temporário definida como Reconhecimento Espacial](images/mr-learning-base/base-05-section3-step1-5.png)

Pressione o botão Reproduzir para entrar no modo Jogo e pressione e segure o botão direito do mouse enquanto move o mouse para baixo até o foco atingir o objeto RoverAssembly:

![Modo de exibição dividida do Modo de reprodução do Unity com o foco sobre o objeto RoverAssembly](images/mr-learning-base/base-05-section3-step1-6.png)

Clique no botão esquerdo do mouse para iniciar o processo de tocar para posicionar:

![Modo de exibição dividida do Modo de reprodução do Unity com o posicionamento de TapToPlace iniciado](images/mr-learning-base/base-05-section3-step1-7.png)

Pressione e mantenha o botão direito do mouse pressionado enquanto move o mouse para a esquerda ou para a direita para girar sua direção de foco. Quando estiver satisfeito com o posicionamento, clique no botão esquerdo do mouse:

![Modo de exibição dividida do Modo de reprodução do Unity com o posicionamento de TapToPlace encerrado](images/mr-learning-base/base-05-section3-step1-8.png)

Quando terminar de testar o recurso no modo de jogo, clique com o botão direito do mouse no objeto Cubo e selecione **Excluir** para removê-lo da cena:

![Unity com o cubo de chão temporário selecionado e o menu pop-up contextual Excluir](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a usar o Solucionador Direcional do MRTK para ter um elemento de interface do usuário instruindo intuitivamente os usuários a objetos. Você também aprendeu a usar o Solucionador Toque para Posicionar para reposicionar os objetos facilmente.

Para saber mais sobre esses e outros solucionadores incluídos no MRTK, consulte o guia [Solucionadores](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) no [Portal de Documentação do MRTK](/windows/mixed-reality/mrtk-unity/).

> [!div class="nextstepaction"]
> [Próximo tutorial: 6. Como criar interfaces do usuário](mr-learning-base-06.md)
