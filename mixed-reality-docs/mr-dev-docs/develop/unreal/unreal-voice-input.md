---
title: Entrada de voz
description: Tutorial sobre como configurar e usar a entrada de voz no HoloLens 2 e no mecanismo inreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, inreal, Engine 4, UE4, HoloLens 2, voz, entrada de voz, reconhecimento de fala, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 504a2d978e3c9bc698e8edd11ea8a4d6be13795a
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609747"
---
# <a name="voice-input-in-unreal"></a>Entrada de voz em não real

A entrada de voz em forma inreal permite que você interaja com um holograma sem precisar usar gestos de mão e só tem suporte para o HoloLens 2. A entrada de voz no HoloLens 2 é alimentada pelo mesmo mecanismo que dá suporte à fala em todos os outros aplicativos universais do Windows, mas o uso não real usa um mecanismo mais limitado para processar a entrada de voz. Isso limita os recursos de entrada de voz em mapeamentos de fala inreais para predefinidos, que são abordados nas seções a seguir. 

## <a name="enabling-speech-recognition"></a>Habilitando o reconhecimento de fala

Para habilitar o reconhecimento de fala no HoloLens:
1. Selecione **configurações do projeto > plataforma > recursos de > do HoloLens** e habilite o **microfone**. 
2. Habilitado o reconhecimento de fala em **configurações > privacidade > fala** e selecione **Inglês**.

> [!NOTE]
> O reconhecimento de fala sempre funciona no idioma de exibição do Windows configurado no aplicativo **configurações** . É recomendável que você também habilite o **reconhecimento de fala online** para a melhor qualidade de serviço.

![Configurações de reconhecimento de fala do Windows](images/unreal/speech-recognition-settings.png)

3. Uma caixa de diálogo será exibida quando o aplicativo começar a perguntar se você deseja habilitar o microfone. Selecionar **Sim** inicia a entrada de voz no aplicativo.

A entrada de voz não requer nenhuma API especial do Windows Mixed Reality; Ele foi criado na API de mapeamento de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) do mecanismo 4 inreal existente. 

## <a name="adding-speech-mappings"></a>Adicionando mapeamentos de fala

Conectar a fala a ação é uma etapa importante ao usar a entrada de voz. Esses mapeamentos monitoram o aplicativo para palavras-chave de fala que um usuário pode dizer e, em seguida, dispara uma ação vinculada. Você pode encontrar mapeamentos de fala de:
1. Selecione **editar > configurações do projeto**, role até a seção **mecanismo** e clique em **entrada**.

Para adicionar um novo mapeamento de fala para um comando de salto:
1. Selecione o **+** ícone ao lado de **elementos da matriz** e preencha os seguintes valores:
    * **jumpWord** para o **nome da ação**
    * **ir** para **palavra-chave de fala**

> [!NOTE]
> Qualquer palavra (s) em inglês ou sentenças curtas podem ser usadas como uma palavra-chave. 

![Configurações de entrada do mecanismo UE4](images/unreal/engine-input.png)

Os mapeamentos de fala podem ser usados como componentes de entrada como mapeamentos de ação ou de eixo ou como nós de plano gráfico no grafo de eventos. Por exemplo, você pode vincular o comando de salto para imprimir dois logs diferentes dependendo de quando a palavra for falada:

1. Clique duas vezes em um plano gráfico para abri-lo no **grafo de eventos**.
2. **Clique com o botão direito do mouse** e pesquise pelo **nome da ação** do seu mapeamento de fala (neste caso, **jumpWord**) e, em seguida, pressione **Enter** para adicionar um nó de **ação de entrada** ao grafo.
3. Arraste e solte o pino **pressionado** para **Imprimir** o nó da cadeia de caracteres, conforme mostrado na imagem abaixo. Você pode deixar o PIN **liberado** vazio, ele não executará nada para mapeamentos de fala.
 
![Ação simples para voz](images/unreal/voice-input-img-03.png)

4. Reproduza o aplicativo, digamos que o **salto** de palavras e assista ao console para imprimir os logs!

Essa é toda a configuração que você precisará para começar a adicionar entrada de voz aos seus aplicativos de HoloLens em um não real. Você pode encontrar mais informações sobre a fala e a interatividade nos links abaixo e certifique-se de pensar sobre a experiência que está criando para seus usuários.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento inreal que apresentamos, a próxima tarefa está explorando os recursos e as APIs da plataforma de realidade misturada: 

> [!div class="nextstepaction"]
> [Câmera do HoloLens](unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Veja também
* [Entrada de voz](../../design/voice-input.md)
* [Focar e confirmar](../../design/gaze-and-commit.md)
* [Interações instinctuais](../../design/interaction-fundamentals.md)

