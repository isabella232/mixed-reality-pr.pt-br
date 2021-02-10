---
title: Tutoriais do MRTK – 4. Como posicionar objetos na cena
description: Este curso mostra como posicionar objetos na cena e como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para organizar objetos em uma grade.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, solucionadores, coleção de objetos de grade
ms.localizationpriority: high
ms.openlocfilehash: 9087800eca3536704ed4ef01a5d8178720b6a875
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590488"
---
# <a name="4-positioning-objects-in-the-scene"></a>4. Como posicionar objetos na cena

## <a name="overview"></a>Visão geral

Neste tutorial, você importará os ativos do tutorial e posicionará os objetos fornecidos na cena.

## <a name="objectives"></a>Objetivos

* Saiba como posicionar objetos na cena
* Saiba como usar o recurso Coleção de Objetos de Grade do MRTK

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe o seguinte pacote personalizado do Unity:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

Para importar um pacote personalizado do Unity, no menu do Unity selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](images/mr-learning-base/base-04-section1-step1-1.png)

Na janela Importar pacote..., selecione o **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage** que você baixou e clique no botão Abrir:

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](images/mr-learning-base/base-04-section1-step1-2.png)

Na janela Importar Pacote do Unity, clique no botão Todos para garantir que todos os ativos sejam selecionados e clique no botão Importar para importar os ativos:

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](images/mr-learning-base/base-04-section1-step1-3.png)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](images/mr-learning-base/base-04-section1-step1-4.png)

## <a name="creating-the-parent-object"></a>Como criar um objeto pai

Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Criar Vazio** para adicionar um objeto vazio à sua cena:

![Menu pop-up contextual Criar Vazio do Unity](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> Para exibir a janela Cena e Jogo lado a lado como mostra a imagem acima, arraste a janela Jogo para o lado direito da janela Cena. Para saber mais sobre como personalizar o seu workspace, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Como personalizar o seu workspace</a> do Unity.

Clique com o botão direito do mouse no objeto recém-criado, selecione **Renomear** e altere o nome para **RoverExplorer**:

![Menu pop-up contextual Renomear do Unity](images/mr-learning-base/base-04-section2-step1-2.png)

Com o objeto RoverExplorer ainda selecionado, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:

* **Posição**: X = 0, Y = -0,6, Z = 2
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Unity com o objeto RoverExplorer selecionado e posicionado](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> A câmera representa a cabeça do usuário e é posicionada na origem, X = 0, Y = 0, Z = 0. Em geral, uma unidade no Unity corresponde a aproximadamente um metro no mundo físico. Porém, há exceções, por exemplo, quando objetos são filhos de objetos dimensionados. No cenário acima, o RoverExplorer é posicionado 2 metros na frente e 0,6 metros abaixo da cabeça do usuário.

## <a name="adding-the-tutorial-prefabs"></a>Como adicionar os pré-fabricados do tutorial

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados**:

![Janela Projeto do Unity com a pasta Pré-fabricados selecionada](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um GameObject pré-configurado armazenado como um Ativo Unitário e pode ser reutilizado em todo o seu projeto.

Na janela Projeto, clique e arraste o pré-fabricado **Tabela** no objeto **RoverExplorer** para torná-la um filho do objeto RoverExplorer e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:

* **Posição**: X = 0, Y = -0,005, Z = 0
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1,2, Y = 0,01, Z = 1,2

![Unity com o pré-fabricado Tabela recém-adicionado selecionado e posicionado](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> Para exibir a cena conforme mostrado na imagem acima use o <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Utensílio de Cena</a>, localizado no canto superior direito da janela Cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço, clique duas vezes no objeto MixedRealityPlayspace para colocá-lo em foco na câmera e amplie se necessário.

Na janela Projeto, clique e arraste o pré-fabricado **RoverAssembly** para o objeto **RoverExplorer** para torná-lo um filho do objeto RoverExplorer e, em seguida, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:

* **Posição**: X = -0,1, Y = 0, Z = 0
* **Rotação**: X = 0, Y = -135, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Unity com o pré-fabricado RoverAssembly recém-adicionado selecionado e posicionado](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>Como organizar objetos em uma coleção

Na janela Hierarquia, clique com o botão direito do mouse no objeto **RoverExplorer** e selecione **Criar Vazio** para adicionar um objeto vazio como um filho do RoverExplorer, nomeie o objeto **RoverParts** e configure o componente **Transformar** da seguinte maneira:

* **Posição**: X = 0, Y = 0,06, Z = 0
* **Rotação**: X = 0, Y = 90, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Unity com o objeto RoverParts recém-criado selecionado e posicionado](images/mr-learning-base/base-04-section4-step1-1.png)

Na janela Hierarquia, selecione todos os objetos filhos em RoverExplorer > RoverAssembly > RoverModel > **Parts** clique com o botão direito do mouse neles e selecione **Duplicar** para criar uma cópia de cada uma das peças:

![Unity com todas as Peças selecionadas e o menu pop-up contextual Duplicar](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> Para selecionar vários objetos adjacentes, pressione e segure a tecla SHIFT enquanto usa o mouse para selecionar o primeiro e o último objeto.

Com os objetos filho de Peças recentemente duplicados ainda selecionados, clique e arraste-os para o objeto **RoverParts** para torná-los objetos filho do objeto RoverParts:

![Unity com as peças recém-duplicadas como filhos do objeto RoverParts](images/mr-learning-base/base-04-section4-step1-3.png)

Para facilitar o trabalho com a sua cena, na janela Hierarquia, clique no ícone de **olho** à esquerda do objeto para desativar a **visibilidade da cena** para o objeto **RoverAssembly**. Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo:

![Unity com a visibilidade de cena do RoverAssembly desativada](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> Para saber mais sobre os controles de Visibilidade da Cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> do Unity.

Na janela Hierarquia, limpe os nomes dos objetos filho RoverParts substituindo o **(1)** acrescentado por **_Part**:

![Unity com o nome de peças duplicadas limpo](images/mr-learning-base/base-04-section4-step1-5.png)

Na janela Hierarquia, selecione o objeto **RoverParts** e, em seguida, na janela Inspetor, clique no botão **Adicionar Componente** e pesquise e selecione **GridObjectCollection** para adicionar o componente GridObjectCollection ao objeto RoverParts:

![Objeto RoverParts do Unity com a Adição de Coleção de Objetos de Grade de Componentes em andamento](images/mr-learning-base/base-04-section4-step1-6.png)

Configure os valores de componente **GridObjectCollection** da seguinte maneira:

* **Tipo de Classificação**: Alfabético
* **Layout**: Horizontal
* **Largura da Célula**: 0,25
* **Distância do pai**: 0,38

![Unity com o componente GridObjectCollection configurado](images/mr-learning-base/base-04-section4-step1-7.png)

Em seguida, clique no botão **Atualizar Coleção** para atualizar a posição dos objetos filho RoverParts:

![Unity com o componente GridObjectCollection aplicado](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a posicionar objetos na cena em relação ao usuário e a usar o recurso Coleção de Objetos de Grade do MRTK para organizar objetos em uma coleção.

> [!div class="nextstepaction"]
>[Próximo tutorial: 5. Criar conteúdo dinâmico usando Solucionadores](mr-learning-base-05.md)
