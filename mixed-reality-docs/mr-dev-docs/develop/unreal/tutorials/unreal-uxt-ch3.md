---
title: 3. Como configurar seu projeto para a realidade misturada
description: Parte 3 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 491e17c5a85ed05f2e324a4f346cc82d207440469fae97fc88fee7065fae0495
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226781"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Como configurar seu projeto para a realidade misturada

No tutorial anterior, você passou tempo configurando o projeto de aplicativo de xadrez. Esta seção vai orientá-lo pela configuração do aplicativo para o desenvolvimento de realidade misturada, o que significa adicionar uma sessão de RA. Para essa tarefa, você usará um ativo de dados ARSessionConfig, que tem muitas configurações úteis de RA, como mapeamento espacial e oclusão. Encontre mais detalhes sobre o ativo [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) e a classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) na documentação do Unreal.

## <a name="objectives"></a>Objetivos

* Como trabalhar com configurações de RA do Unreal Engine
* Como usar um ativo de dados do ARSessionConfig
* Como configurar um peão e um modo de jogo

## <a name="adding-the-session-asset"></a>Como adicionar o ativo de sessão

As sessões de RA no Unreal não acontecem espontaneamente. Para usar uma sessão, você precisará de um ativo de dados ARSessionConfig com o qual trabalhará, que será a sua próxima tarefa:

1. Clique em **Adicionar Novo > Diversos > Ativo de Dados** no **Navegador de Conteúdo**. Verifique se você está no nível raiz da pasta **Conteúdo**.
    * Selecione **ARSessionConfig**, clique em **Selecionar** e nomeie o ativo **ARSessionConfig**.

![Criar um ativo de dados](images/unreal-uxt/3-createasset.PNG)

3. Clique duas vezes em **ARSessionConfig** para abri-lo, deixe todas as configurações padrão e clique em **Salvar**. Volte para a Janela principal.

![Configuração de sessão de RA](images/unreal-uxt/3-arsessionconfig.PNG)

Com isso feito, a próxima etapa será verificar se a sessão de RA começa e é interrompida quando o nível é carregado e encerrado. A boa notícia é que o Unreal tem um blueprint especial chamado **Blueprint de Nível** que funciona como um grafo de eventos global em todo esse nível. Conectar o ativo ARSessionConfig no **Blueprint de Nível** garante que a sessão de RA será disparada exatamente quando o jogo começar.

1. Clique em **Blueprints > Abrir Blueprint de Nível** na barra de ferramentas do editor:

![Abrir Blueprint de Nível](images/unreal-uxt/3-level-blueprint.PNG)

5. Arraste o nó de execução (ícone de seta para a esquerda) para fora do **Evento BeginPlay** e solte-o, procure o nó **Iniciar Sessão de RA** e clique em ENTER.  
    * Clique na lista suspensa **Selecionar Ativo** em **Configuração de Sessão** e escolha o ativo **ARSessionConfig**.

![Iniciar Sessão de RA](images/unreal-uxt/3-start-ar-session.PNG)

6. Clique com o botão direito do mouse em qualquer lugar do EventGraph e crie um nó **EndPlay de Evento**. Arraste o marcador de execução e solte-o, procure um nó **Interromper Sessão de RA** e clique em ENTER. Se a sessão de RA ainda estiver em execução quando o nível for encerrado, alguns recursos poderão parar de funcionar se você reiniciar o aplicativo durante o streaming para um headset.
    * Escolha **Compilar**, depois **Salvar** e retorne para a Janela principal.

![Interromper Sessão de RA](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>Criar um Peão

Neste ponto, o projeto ainda precisa de um objeto de jogador. No Unreal, um **Peão** representa o usuário no jogo, mas neste caso, será a experiência do HoloLens 2.

1. Clique em **Adicionar Novo > Classe de Blueprint** na pasta **Conteúdo** e expanda a seção **Todas as Classes** na parte inferior.
    * Pesquise **DefaultPawn**, clique em **Selecionar**, nomeie-o **MRPawn** e clique duas vezes no ativo para abri-lo.

![Criar um Peão herdando de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

2. Clique em **Adicionar Componente > Câmera** no painel **Componentes** e nomeie-o como **Câmera**. Verifique se o componente **Câmera** é um filho direto da raiz (**CollisionComponent**). Isso permite que a câmera do player se mova com o dispositivo HoloLens 2.

> [!NOTE]
> Por padrão, os Peões têm componentes de malha e colisão. Na maioria dos projetos do Unreal, os Peões são objetos sólidos que podem colidir com outros componentes. Já que o peão e o usuário são a mesma coisa em realidade misturada, você deseja ser capaz de passar pelos hologramas sem nenhuma colisão.

3. Selecione **CollisionComponent** no painel **Componentes** e role para baixo até a seção **Colisão** do painel **Detalhes**.
    * Clique na lista suspensa de **Predefinições de Colisão** e altere o valor para **NoCollision**.
    * Faça o mesmo para o **MeshComponent**

![Ajustar as Predefinições de Colisão do Peão](images/unreal-uxt/3-nocollision.PNG)

4. **Compile** e **salve** o blueprint.

Com seu trabalho aqui terminado, retorne para a Janela principal.

## <a name="create-a-game-mode"></a>Criar um Modo de Jogo

A última peça do quebra-cabeça da configuração da realidade misturada é o Modo de Jogo. O Modo de Jogo determina um diversas configurações para o jogo ou a experiência, incluindo o peão padrão a ser usado.

1.  Clique em **Adicionar Nova > Classe de Blueprint** na pasta **Conteúdo** e selecione **Base de Modo de Jogo** como a classe pai. Nomeie-a **MRGameMode** e clique duas vezes para abri-la.

![MRGameMode no Navegador de Conteúdo](images/unreal-uxt/3-gamemode.PNG)

2.  Vá para a seção **Classes** no painel **Detalhes** e altere a **Classe de Peão Padrão** para **MRPawn**.
    * Escolha **Compilar**, depois **Salvar** e retorne para a Janela principal.

![Definir a Classe Peão Padrão](images/unreal-uxt/3-setpawn.PNG)

3.  Selecione **Editar > Configurações de Projetos** e clique em **Mapas e Modos** na lista à esquerda.
    * Expanda **Modos Padrão** e altere **Modo de Jogo Padrão** para **MRGameMode**.
    * Expanda **Mapas Padrão** e altere **EditorStartupMap** e **GameDefaultMap** para **Principal**. Quando você fechar o editor e abri-lo novamente ou jogar o jogo, o mapa Principal já estará selecionado por padrão.

![Configurações do projeto – Mapas e Modos](images/unreal-uxt/3-mapsandmodes.PNG)

Com o projeto totalmente configurado para realidade misturada, você está pronto para passar para o próximo tutorial e começar a adicionar a entrada do usuário à cena.

[Próxima seção: 4. Como tornar sua cena interativa](unreal-uxt-ch4.md)
