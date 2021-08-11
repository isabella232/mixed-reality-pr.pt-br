---
title: 5. Como adicionar um botão e redefinir locais de peças
description: Parte 5 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 5f37599e43147a79c8bdd9f0c28e0b23f163c39fa833d3835650c28deb4f0898
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226700"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Como adicionar um botão e redefinir locais de peças

No tutorial anterior, você adicionou Atores de Interação à Mão aos componentes Peão e Manipulador para o tabuleiro de xadrez, a fim de torná-los interativos. Nesta seção, você continuará usando o plug-in de Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada para desenvolver seu aplicativo de xadrez com novas funções e referências de Ator em Blueprints. Ao final desta seção, você estará pronto para empacotar e implantar o aplicativo de realidade misturada em um dispositivo ou emulador.

## <a name="objectives"></a>Objetivos

* Adicionar um botão interativo
* Criar uma função para redefinir a localização de uma peça
* Vincular o botão para disparar a função quando pressionado

## <a name="creating-a-reset-function"></a>Criar uma função de redefinição

Sua primeira tarefa é criar um blueprint de função que redefina uma peça de xadrez para a posição original dela na cena.

1.  Abra **WhiteKing**, selecione o ícone **+** ao lado da seção **Funções** no **Meu Blueprint** e nomeie-o **Redefinir Localização**.

2.  Arraste e solte a execução de **Redefinir Localização** na grade do Blueprint para criar um nó **SetActorRelativeTransform**.
    * Essa função define a transformação (localização, rotação e escala) de um ator em relação ao seu pai. Você usará essa função para redefinir a posição do rei no tabuleiro, mesmo que o tabuleiro tenha sido movido de sua posição original.

3. Clique com o botão direito do mouse no Grafo de Eventos, selecione **Transformar** e altere a **Localização** dele para **X = -26**, **Y = 4** e **Z = 0**.
    * Conecte o **Valor Retornado** dele ao marcador **Nova Transformação Relativa** em **SetActorRelativeTransform**.

![Função Reset Location](images/unreal-uxt/5-function.PNG)

Escolha **Compilar** e **Salvar** o projeto antes de voltar à Janela principal.


## <a name="adding-a-button"></a>Adicionar um botão

Agora que a função está configurada corretamente, a próxima tarefa é criar um botão que a dispare quando tocado.

1.  Clique em **Adicionar Novo > Classe de Blueprint**, expanda a seção **Todas as Classes** e pesquise **UxtPressableButtonActor**.
    * Nomeie-o como **ResetButton** e clique duas vezes para abrir o Blueprint

![Subclasse do novo Blueprint do botão de estilo do HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. No painel **Componentes**, selecione **ResetButton(self)** . No painel **Detalhes**, navegue até a seção **Botão**. Altere o **Rótulo do Botão** padrão para "Redefinir", expanda a seção **Pincel do Ícone do Botão** e clique no botão **Abrir o Icon Brush Editor**.

![Definir o rótulo e o ícone no botão](images/unreal-uxt/5-buttonconfig.PNG)

O Icon Brush Editor será aberto, que você poderá usar para selecionar um novo ícone para o botão.

![Selecionar um ícone para o botão](images/unreal-uxt/5-iconbrusheditor.PNG)

Há várias outras configurações que você pode ajustar para configurar seu botão. Para saber mais sobre o componente UXT Pressable Button, confira a [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).

3. Clique em **ButtonComponent (Herdado)** no painel **Componentes** e role o painel **Detalhes** para baixo até a seção **Eventos**.
    * Clique no botão **+** verde próximo de **On Button Pressed** para adicionar um evento Grafo de Eventos, que será chamado quando o botão for pressionado.

Deste ponto em diante, será conveniente que você chame a função **Redefinir Localização** do **WhiteKing**, que precisa de uma referência para o Ator **WhiteKing** no Nível.

4.  No painel **Meu Blueprint**, navegue até a seção **Variáveis**, clique no botão **+** e nomeie a variável **WhiteKing**.
    * No painel **Detalhes**, selecione a lista suspensa ao lado de **Tipo de Variável**, pesquise **WhiteKing** e selecione **Referência de Objeto**.
    * Marque a caixa ao lado de **Instância Editável**, que permite que a variável seja definida por meio do Nível Principal.

![Criar uma variável](images/unreal-uxt/5-var.PNG)

5.  Arraste a variável WhiteKing de **Meu Blueprint > Variáveis** até o Grafo de Eventos do Botão Redefinir e escolha **Obter WhiteKing**.

## <a name="firing-the-function"></a>Como disparar a função

Tudo o que resta fazer é disparar oficialmente a função de redefinição quando o botão for pressionado.

1.  Arraste o pino da saída WhiteKing e solte para posicionar um novo nó. Selecione a função **Reset Location**. Por fim, arraste o pino de execução de saída de **On Button Pressed** até o pino de execução de entrada em **Reset Location**. **Compile** e **Salve** o Blueprint ResetButton e, em seguida, retorne à Janela principal.

![Chamar função Reset Location de On Button Pressed](images/unreal-uxt/5-callresetloc.PNG)

2.  Arraste **ResetButton** até o visor e defina a localização dele como **X = 50**, **Y = -25** e **Z = 10**. Defina a rotação como **Z = 180**. Em **Padrão**, defina o valor da variável **WhiteKing** como **WhiteKing**.

![Definir a variável](images/unreal-uxt/5-buttonlevel.PNG)

Execute o aplicativo, mova a peça de xadrez para um novo local e pressione o botão de estilo do HoloLens 2 para ver a lógica de redefinição em ação!

Agora você tem um aplicativo de realidade misturada com uma peça e um tabuleiro de xadrez com os quais você pode interagir e um botão totalmente funcional que redefine a localização da peça. Você pode encontrar o aplicativo concluído até esse ponto no respectivo repositório do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp). Você pode ir além deste tutorial e configurar o restante das peças de xadrez, para que todo o tabuleiro seja redefinido quando você clicar no botão Redefinir.

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

Você está pronto para prosseguir para a seção final deste tutorial, em que aprenderá a empacotar e implantar o aplicativo em um dispositivo ou um emulador.

> [!IMPORTANT]
> Neste ponto, atualize seu projeto com as **[Configurações de desempenho do Unreal](../performance-recommendations-for-unreal.md)** recomendadas antes de implantar o aplicativo em um dispositivo ou emulador.

[Próxima seção: 6. Como empacotar e implantar no dispositivo ou emulador](unreal-uxt-ch6.md)
