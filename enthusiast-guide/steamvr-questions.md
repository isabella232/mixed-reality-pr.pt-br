---
title: Perguntas frequentes do SteamVR
description: SteamVR a solução de problemas de realidade mista do Windows que vai além da nossa documentação de suporte de consumidor padrão.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, solução de problemas, erros, ajuda, suporte, SteamVR
ms.openlocfilehash: 275a334b2cbf402ea576948c4622f2098d8f3ec0
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725877"
---
# <a name="steamvr-faqs"></a>Perguntas frequentes do SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Como posso jogar SteamVR Games no meu Headset do Windows Mixed Reality

1. [Baixe e instale o SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe). O tutorial do SteamVR deve ser iniciado automaticamente quando você inicia o SteamVR.
2. Conecte seu headset ao seu PC e ligue seus controladores de movimento.
3. Depois que o Windows Mixed Reality Home tiver sido carregado e seus controladores estiverem visíveis, abra o aplicativo de fluxo na área de trabalho.
4. Use o aplicativo de fluxo para iniciar um jogo SteamVR da sua biblioteca de fluxo. Para iniciar jogos do SteamVR sem retirar seu headset, encontre-os e inicie-os no início da realidade misturada do Windows **> todos os aplicativos**.

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Uma mensagem diz "para usar o SteamVR com o Windows Mixed Reality, você precisa instalar o Windows Update mais recente" ou "o modo de desenvolvedor do Windows necessário"

1. Verifique se o PC está executando a versão mais recente do Windows 10. Vá para **configurações > > do sistema** e, em "especificações do Windows", verifique se "Build do sistema operacional" é 16299,64 ou superior.
2. Verifique se você não tem nenhuma atualização aguardando para baixar ou instalar. Vá para **configurações > atualização & segurança > Windows Update** e selecione "verificar atualizações". Talvez você precise marcar várias vezes até que nenhuma atualização adicional esteja disponível e, em seguida, reiniciar o computador.

## <a name="steamvr-is-crashing-after-updating-windows"></a>O SteamVR está falhando após a atualização do Windows

Algumas versões mais antigas do Windows Mixed Reality for SteamVR não são mais compatíveis com o Windows. Para garantir que sua versão do Windows Mixed Reality para SteamVR seja atual:

1. Em sua biblioteca de fluxo, acesse **Software > a realidade mista do Windows para SteamVR**.
2. Clique com o botão direito do mouse e vá para "Propriedades".
3. Selecione a guia "atualizar" e "sempre manter este aplicativo atualizado".
4. Force a atualização acessando a guia "arquivos locais" e selecionando "verificar a integridade dos arquivos de aplicativo".
5. Reinicie o fluxo e o SteamVR.

Se o SteamVR ainda estiver falhando após a atualização, você poderá ter duas instalações do Windows Mixed Reality para SteamVR em seu computador. Para confirmar:

1. Localize ```%localappdata%\openvr\openvrpaths.vrpath``` e abra-o no bloco de notas.
2. Procure as seções "drivers externos" para procurar várias entradas para "MixedRealityVRDriver"
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Se você vir várias entradas, remova as duas entradas mais antigas. Quando você tiver apenas uma entrada, não deverá haver mais uma vírgula no final da linha. Por exemplo:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Salve o arquivo e feche-o.
5. Reinicie o fluxo e o SteamVR.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Meus controladores não estão funcionando conforme o esperado no SteamVR

1. Feche o SteamVR.
2. Volte para a página inicial do Windows Mixed Reality e confirme se os controladores estão funcionando.
3. Inicie a experiência do SteamVR novamente e os controladores devem voltar ao normal.
4. Se os problemas persistirem, envie comentários por arquivo usando o [Hub de comentários do Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) na categoria realidade misturada e inclua SteamVR no resumo.

Você usará seus controladores de movimento de forma diferente em jogos diferentes. Aqui estão alguns conceitos básicos para ajudá-lo a começar:
* Para abrir o painel de fluxo, pressione direto para baixo no Thumbstick esquerdo.
* Para sair de um jogo SteamVR e retornar para a página inicial do Windows Mixed Reality, pressione o botão Windows. Em seguida, selecione o botão Home da realidade misturada que aparece na tela.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Meus controladores à esquerda e à direita são revertidos no SteamVR

Inicie o jogo com seus controladores e, em seguida, ligue o controlador à esquerda, seguido do lado direito.

## <a name="my-games-are-running-slowly"></a>Meus jogos estão em execução lenta

1. Verifique se seu PC atende às especificações de SteamVR no Windows Mixed Reality e o jogo que você está jogando.
2. No portal da realidade misturada na área de trabalho, selecione "Pausar" para parar a visualização da área de trabalho.
3. Vá para **configurações > > do sistema** e, em "especificações do Windows", verifique se "Build do sistema operacional" é 16299,64 ou posterior.
4. Verifique se seu PC tem os drivers gráficos mais recentes ("verificar se há atualizações" em Windows Update).
5. Marque "Gerenciador de tarefas" para ver quais outros processos podem estar consumindo recursos em seu computador.
6. Verifique se o vapor está baixando um jogo em segundo plano, que consome recursos e faz com que os jogos sejam executados de forma ruim.
7. Uma pequena classe de aplicativos que não têm uma janela visível (por exemplo, SteamVR Home), tem um problema de desempenho conhecido. A maioria dos aplicativos não se enquadra nessa categoria, e uma correção estará disponível em uma atualização futura.

Se você ainda estiver executando problemas de desempenho inesperados, envie-nos comentários usando o [Hub de comentários do Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Certifique-se de seguir as instruções para [incluir um rastreamento de desempenho SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr).

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR está mostrando um erro de compositor (por exemplo, "falha de conexão do compositor de IPC compartilhado (400)").

Isso pode acontecer se o headset e o monitor primário estiverem em dois adaptadores de vídeo diferentes. Anexe o monitor ao mesmo adaptador do headset e configure-o como o monitor principal no **aplicativo configurações > sistema > exibição**.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>O conteúdo do SteamVR aparece no lugar errado, como abaixo do piso ou acima da minha cabeça

Redefina sua posição:

1. Selecione o Thumbstick do controlador à esquerda para abrir o "painel do SteamVR".
2. Selecione o botão "configurações".
3. Selecione "redefinir posição encaixada".

## <a name="my-steam-app-closed-unexpectedly"></a>Meu aplicativo de fluxo fechou inesperadamente

O aplicativo de fluxo será fechado se:

* A tela do seu PC é bloqueada
* Remover o headset
* Trocar usuários
* Seu computador vai para o estado de suspensão
