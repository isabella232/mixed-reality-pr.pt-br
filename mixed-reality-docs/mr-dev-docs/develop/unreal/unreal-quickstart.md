---
title: Como criar seu primeiro aplicativo Unreal do HoloLens
description: Saiba como configurar corretamente um projeto do Unreal com objetos de cena e interações de entrada para o desenvolvimento da realidade misturada do HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, editor do Unreal, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, documentação, guias, recursos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, portabilidade, atualização
ms.openlocfilehash: 07ec2760d691938015619d097d214d205cdbab78f250ff9dd8a793dd27f10c4a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209546"
---
# <a name="creating-your-first-hololens-unreal-application"></a>Como criar seu primeiro aplicativo Unreal do HoloLens

Este guia descreverá como executar seu primeiro aplicativo de Realidade Misturada no HoloLens no Unreal Engine. Na tradição do "Olá, Mundo", você criará um aplicativo simples que exibe um cubo na tela. Para torná-lo mais útil, você também criará seu primeiro gesto para girar o cubo e encerrar o aplicativo. 

## <a name="objectives"></a>Objetivos

* Iniciar um projeto do HoloLens
* Habilitar os plug-ins corretos
* Criar um ativo de dados ARSessionConfig
* Configurar entradas de gesto
* Criar um nível básico
* Implementar um gesto de pinçagem

## <a name="creating-a-new-project"></a>Crie um novo projeto

A primeira coisa que você precisa é de um projeto com o qual trabalhar. Se você é um desenvolvedor novo do Unreal, [baixe os arquivos de suporte](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) do Epic Launcher.

1. Iniciar Unreal Engine
2. Em **Novas Categorias de Projeto**, selecione **Jogos** e clique em **Avançar**:

![Janela Projetos recentes aberta com os Jogos realçados](images/unreal-quickstart-img-01.png)

3. Selecione o modelo **Em branco** e clique em **Avançar**:

![A janela do navegador de projetos do Unreal com o modelo Em branco realçado](images/unreal-quickstart-img-02.png)

4. Em **Configurações do Projeto**, defina **C++, 3D ou 2D Escalonável, Celular/Tablet** e **Nenhum Conteúdo Inicial**, escolha uma localização de salvamento e clique em **Criar Projeto**

> [!NOTE] 
> Você está usando um projeto C++ em vez de um projeto Blueprint para estar pronto para usar o plug-in OpenXR mais tarde. Este Guia de Início Rápido usa o plug-in OpenXR padrão fornecido com o Unreal Engine. No entanto, é recomendável baixar e usar o plug-in oficial do Microsoft OpenXR. Isso requer que o projeto seja um projeto C++.

![Janela de configurações do projeto com as opções de projeto, de desempenho, de plataforma de destino e de conteúdo inicial realçadas](images/unreal-quickstart-img-03.png)

O seu novo projeto deve ser aberto automaticamente no editor do Unreal, o que significa que você está pronto para a próxima seção.

## <a name="enabling-required-plugins"></a>Como habilitar os plugins necessários

Habilite dois plug-ins para começar a adicionar objetos à cena.

1. Abra **Editar > Plug-ins** e selecione **Realidade Aumentada** na lista de opções internas.
* Role para baixo até **HoloLens** e marque **Habilitado**

![A janela Plug-ins com a seção de realidade aumentada está aberta e o HoloLens está realçado](images/unreal-quickstart-img-04.png)

2. Digite **OpenXR** na caixa de pesquisa no canto superior direito e habilite os plug-ins **OpenXR** e **OpenXRMsftHandInteraction**:

![Janela Plug-ins com o OpenXR habilitado](images/unreal-quickstart-img-05.jpg)

![Janela Plug-ins com a Interação das Mãos do Open XR Msft habilitada](images/unreal-quickstart-img-06.jpg)

3. Reiniciar o editor

> [!NOTE]
> Este tutorial usa o OpenXR, mas os dois plug-ins que você instalou acima não fornecem atualmente o conjunto de recursos completo para o desenvolvimento do HoloLens. O plug-in HandInteraction será suficiente para o gesto de "pinçar" que você usará mais tarde, mas se quiser ir além dos conceitos básicos, você precisará [baixar o plug-in do OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).

Com os plug-ins habilitados, você pode se concentrar em preenchê-lo com conteúdo.

## <a name="creating-a-level"></a>Criar um nível

Sua próxima tarefa será criar uma configuração de jogador com um ponto de partida e um cubo para referência e escala.

1. Selecione **Arquivo > Novo Nível** e escolha **Nível Vazio**. A cena padrão no visor agora deve estar vazia
2. Na guia **Modos**, selecione **Básico** e arraste **PlayerStart** para a cena
* Na guia **Detalhes**, defina a **Localização** como o **X = 0, Y = 0** e **Z = 0** para colocar o usuário no centro da cena quando o aplicativo for iniciado

![A cena do editor do Unreal com a localização e o início do player adicionados](images/unreal-quickstart-img-07.png)

3. Na guia **Básico**, arraste um **Cubo** para a cena
* Defina a **Localização** do cubo como **X = 50, Y = 0** e **Z = 0** para posicionar o cubo a 50 cm de distância do player no início
* Altere a **Escala** do cubo para **X = 0,2, Y = 0,2** e **Z = 0,2** 

Você não poderá ver o cubo, a menos que adicione uma luz à cena, que será a sua última tarefa antes de testar a cena em questão.

4. No painel **Modos**, alterne para a guia **Luzes** e arraste uma **Luz Direcional** até a cena
* Posicione a luz acima de **PlayerStart** para que você possa vê-lo

![Cena do editor do Unreal com o cubo e a luz direcional adicionados](images/unreal-quickstart-img-08.png)

5. Acesse **Arquivo > Salvar Atual**, nomeie o nível **Principal** e selecione **Salvar**

Com a cena preparada, pressione **Jogar** na barra de ferramentas para ver o cubo em ação! Quando tiver terminado de admirar seu trabalho, pressione Esc para interromper o aplicativo.

![Cena no modo de jogo com o cubo no meio da tela](images/unreal-quickstart-img-09.png)

Agora que a cena está configurada, vamos prepará-la para algumas interações básicas no RA. Primeiro, você precisa criar uma Sessão de RA e pode adicionar blueprints para habilitar a interação das mãos.

## <a name="adding-a-session-asset"></a>Como adicionar um ativo de sessão

As sessões de RA no Unreal não acontecem espontaneamente. Para usar uma sessão, você precisará de um ativo de dados ARSessionConfig com o qual trabalhará, que será a sua próxima tarefa:

1. No **Navegador de Conteúdo**, selecione **Adicionar Novo > Diversos > Ativos de Dados** e verifique se você está no nível da pasta de Conteúdo raiz
2. Selecione **ARSessionConfig**, clique em **Selecionar** e nomeie o ativo **ARSessionConfig**:

![Janela Selecionar classe de ativo de dados aberta com o ativo de configuração de sessão de RA realçado](images/unreal-quickstart-img-10.png)

2. Clique duas vezes em **ARSessionConfig** para abri-lo, selecione **Salvar** com todas as configurações padrão e retorne para a Janela principal:

![Janela Detalhes do ativo de configuração de sessão de RA](images/unreal-quickstart-img-11.png)

Com isso feito, a próxima etapa será verificar se a sessão de RA começa e é interrompida quando o nível é carregado e encerrado. A boa notícia é que o Unreal tem um blueprint especial chamado **Blueprint de Nível** que funciona como um grafo de eventos global em todo esse nível. Conectar o ativo ARSessionConfig no Blueprint de Nível garante que a sessão de RA será disparada exatamente quando o jogo começar.

3. Na barra de ferramentas do editor, selecione **Blueprints > Abrir Blueprint de Nível**:

![Menu do Blueprint aberto com a opção Abrir blueprint de nível realçada](images/unreal-quickstart-img-12.png)

4. Arraste o nó de execução (ícone de seta à esquerda) para o **Evento BeginPlay** e solte-o
* Pesquise pelo nó **Iniciar Sessão de RA** e clique em Enter
* Clique na lista suspensa **Selecionar Ativo** em **Configuração de Sessão** e escolha o ativo **ARSessionConfig**

![Grafo de blueprint com o evento Iniciar jogo conectado à função Iniciar sessão de RA](images/unreal-quickstart-img-13.png)

5. Clique com o botão direito do mouse em qualquer lugar do EventGraph e crie um nó **EndPlay de Evento**. 
* Arraste o marcador de execução e solte-o e, em seguida, pesquise um nó **Interromper Sessão de RA** e clique em Enter 
* Clique em **Compilar**, **Salvar** e retorne para a Janela principal

> [!IMPORTANT]
> Se a sessão de RA ainda estiver em execução quando o nível for encerrado, alguns recursos poderão parar de funcionar se você reiniciar o aplicativo durante o streaming para um headset.

![Nó Encerrar jogo do evento anexado à função Parar sessão de RA](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>Como configurar entradas

1. Selecione **Editar > Configurações de Projeto** e acesse **Mecanismo > Entrada**
2. Selecione o ícone **+** ao lado de **Mapeamentos de Ação** e crie as ações **RightPinch** e **LeftPinch**:

![Associando as configurações de entrada com os mapeamentos de ação de pinçagem à direita e à esquerda realçados](images/unreal-quickstart-img-15.jpg)

3. Mapeie as ações **RightPinch** e **LeftPinch** para as respectivas ações **Interação das mãos do OpenXR MSFT**:

![Mapeamentos de ação com as opções de Interação das mãos do OpenXR MSFT realçadas](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a>Como configurar gestos

Agora que configuramos as entradas, podemos chegar à parte interessante: Adicionar gestos! Vamos girar o cubo com uma pinçagem à direita e encerrar o aplicativo com uma pinçagem à esquerda.

1. Abra o **Blueprint de Nível** e adicione **InputAction RightPinch** e **InputAction LeftPinch**
* Conecte o evento de pinçagem à direita a um **AddActorLocalRotation** com o seu **Cubo** como o destino e a **Rotação Delta** definida como **X = 0, Y = 0** e **Z = 20**. O cubo agora será girado em 20 graus sempre que você pinçar
* Conecte o evento de pinçagem à esquerda para **Encerrar o Jogo**

![Blueprint de nível aberto com as ações de entrada para eventos de pinçagem à direita e à esquerda](images/unreal-quickstart-img-17.jpg)

2. Nas configurações de **Transformação** do cubo, defina a **Mobilidade** como **Móvel** para que ele possa ser movido dinamicamente:

![Configurações de transformação com a propriedade de mobilidade realçada](images/unreal-quickstart-img-18.jpg)

Neste ponto, você está pronto para implantar e testar o aplicativo.