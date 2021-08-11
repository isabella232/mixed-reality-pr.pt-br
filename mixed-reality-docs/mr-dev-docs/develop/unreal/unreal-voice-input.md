---
title: Entrada de voz em não real
description: saiba como configurar e usar entrada de voz, mapeamentos de fala e reconhecimento em aplicativos inreais de realidade misturada para dispositivos HoloLens 2.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, inreal, inreal Engine 4, UE4, HoloLens 2, voz, entrada de voz, reconhecimento de fala, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 12d0c595b5319da50e119f4a2463e2ca3e07ce449f11d6fd266c5f988d180465
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220992"
---
# <a name="voice-input-in-unreal"></a>Entrada de voz em não real

a entrada de voz em forma inreal permite que você interaja com um holograma sem precisar usar gestos de mão e só tem suporte HoloLens 2. a entrada de voz no HoloLens 2 é alimentada pelo mesmo mecanismo que dá suporte à fala em todos os outros aplicativos de Windows Universal, mas o uso não real usa um mecanismo mais limitado para processar a entrada de voz. Isso limita os recursos de entrada de voz em mapeamentos de fala inreais para predefinidos, que são abordados nas seções a seguir. 

## <a name="enabling-speech-recognition"></a>Habilitando o reconhecimento de fala

se você usar Windows Mixed Reality plug-in, a entrada de voz não exigirá nenhuma api especial de Windows Mixed Reality; Ele foi criado na API de mapeamento de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) do mecanismo 4 inreal existente. Se você usar o OpenXR, também deverá instalar [o plug-in do Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal). 

Para habilitar o reconhecimento de fala no HoloLens:
1. selecione **Project Configurações plataforma de > > HoloLens recursos >** e habilite o **microfone**. 
2. habilitado o reconhecimento de fala no **Configurações > privacidade > fala** e selecione **inglês**.

> [!NOTE]
> o reconhecimento de fala sempre funciona no Windows idioma de exibição configurado no aplicativo **Configurações** . É recomendável que você também habilite o **reconhecimento de fala online** para a melhor qualidade de serviço.

![Windows Configurações de reconhecimento de fala](images/unreal/speech-recognition-settings.png)

3. Uma caixa de diálogo será exibida quando o aplicativo começar a perguntar se você deseja habilitar o microfone. Selecionar **Sim** inicia a entrada de voz no aplicativo.

## <a name="adding-speech-mappings"></a>Adicionando mapeamentos de fala

Conectar a fala a ação é uma etapa importante ao usar a entrada de voz. Esses mapeamentos monitoram o aplicativo para palavras-chave de fala que um usuário pode dizer e, em seguida, dispara uma ação vinculada. Você pode encontrar mapeamentos de fala de:
1. selecione **editar > Project Configurações**, role até a seção **mecanismo** e clique em **entrada**.

Para adicionar um novo mapeamento de fala para um comando de salto:
1. Selecione o **+** ícone ao lado de **elementos da matriz** e preencha os seguintes valores:
    * **jumpWord** para o **nome da ação**
    * **ir** para **palavra-chave de fala**

> [!NOTE]
> Qualquer palavra (s) em inglês ou sentenças curtas podem ser usadas como uma palavra-chave. 

![Configurações de entrada do mecanismo UE4](images/unreal/engine-input.png)

Os mapeamentos de fala podem ser usados como componentes de entrada como mapeamentos de ação ou de eixo ou como nós de plano gráfico no Graph de eventos. Por exemplo, você pode vincular o comando de salto para imprimir dois logs diferentes dependendo de quando a palavra for falada:

1. Clique duas vezes em um plano gráfico para abri-lo no **Graph de eventos**.
2. **Clique com o botão direito do mouse** e pesquise pelo **nome da ação** do seu mapeamento de fala (neste caso, **jumpWord**) e, em seguida, pressione **Enter** para adicionar um nó de **ação de entrada** ao grafo.
3. Arraste e solte o pino **pressionado** para **Imprimir** o nó da cadeia de caracteres, conforme mostrado na imagem abaixo. Você pode deixar o PIN **liberado** vazio, ele não executará nada para mapeamentos de fala.
 
![Ação simples para voz](images/unreal/voice-input-img-03.png)

4. Reproduza o aplicativo, digamos que o **salto** de palavras e assista ao console para imprimir os logs!

essa é toda a configuração que você precisará para começar a adicionar entrada de voz aos seus aplicativos HoloLens em um não real. Você pode encontrar mais informações sobre a fala e a interatividade nos links abaixo e certifique-se de pensar sobre a experiência que está criando para seus usuários.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento inreal que apresentamos, a próxima tarefa está explorando os recursos e as APIs da plataforma de realidade misturada: 

> [!div class="nextstepaction"]
> [Câmera do HoloLens](unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Veja também
* [Entrada de voz](../../design/voice-input.md)
* [Focar e confirmar](../../design/gaze-and-commit.md)
* [Interações instinctuais](../../design/interaction-fundamentals.md)

