---
title: Perguntas frequentes sobre o SteamVR
description: O SteamVR Windows Mixed Reality solução de problemas que vai além da nossa documentação de suporte ao consumidor padrão.
author: qianwen
ms.author: v-qianwen
ms.date: 09/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Solução de Problemas, Erros, Ajuda, Suporte, SteamVR
ms.openlocfilehash: 17ab1709e8a2fc7e3eee70082aef64f0dc23d318
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436793"
---
# <a name="steamvr-faqs"></a>Perguntas frequentes sobre o SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Como posso jogar jogos do SteamVR no meu headset Windows Mixed Reality trabalho

1. [Baixe e instale o SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe) O tutorial do SteamVR deve começar automaticamente quando você iniciar o SteamVR.
2. Conexão headset no computador e ativar os controladores de movimento.
3. Depois Windows Mixed Reality página base tiver sido carregada e seus controladores ficam visíveis, abra o aplicativo Steam na área de trabalho.
4. Use o aplicativo Steam para iniciar um jogo do SteamVR de sua biblioteca do Steam. Para iniciar jogos do SteamVR sem tirar o headset, encontre e inicie-os em Iniciar > Todos **os Aplicativos do** Windows Mixed Reality .

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Uma mensagem diz "Para usar o SteamVR com Windows Mixed Reality, você precisa instalar a atualização Windows mais recente" ou "Windows modo de desenvolvedor obrigatório"

1. Certifique-se de que o computador está executando a versão mais recente do Windows 10 ou Windows 11. Vá para **Configurações > System > Sobre** e, em "especificações Windows", certifique-se de que "Build do sistema operacional" seja 16299,64 ou superior.
2. Certifique-se de que você não tem nenhuma atualização aguardando para baixar ou instalar. Vá para **Configurações > Atualizar & Segurança > Windows Atualizar** e selecione "Verificar se há atualizações". Talvez seja preciso verificar várias vezes até que nenhuma outra atualização seja disponibilizada e, em seguida, reinicie o computador.

## <a name="steamvr-is-crashing-after-updating-windows"></a>O SteamVR está falhando após a atualização Windows

Algumas versões mais antigas do Windows Mixed Reality para o SteamVR não são mais compatíveis com Windows. Para garantir que sua versão do Windows Mixed Reality para o SteamVR seja atual:

1. Na biblioteca do Steam, acesse **Software > Windows Mixed Reality para SteamVR.**
2. Clique com o botão direito do mouse e vá para "Propriedades".
3. Selecione a guia "Atualizar" e "Sempre mantenha este aplicativo atualizado".
4. Force a atualização indo para a guia "Arquivos Locais" e selecionando "Verificar a integridade dos arquivos de aplicativo".
5. Reinicie o Steam e o SteamVR.

Se o SteamVR ainda estiver falhando após a atualização, você poderá ter duas instalações do Windows Mixed Reality para o SteamVR em seu computador. Para confirmar:

1. Localize ```%localappdata%\openvr\openvrpaths.vrpath``` e abra-o Bloco de notas.
2. As seções "drivers externos" procurarão várias entradas para "MixedRealityVRDriver"
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Se você vir várias entradas, remova a mais antiga das duas entradas. Depois que você tiver apenas uma entrada, não deverá mais haver uma vírgula no final da linha. Por exemplo:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Salve o arquivo e feche-o.
5. Reinicie o Steam e o SteamVR.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Meus controladores não estão funcionando conforme o esperado no SteamVR

1. Feche o SteamVR.
2. Volte para Windows Mixed Reality página e confirme se os controladores estão funcionando.
3. Iniciar a experiência do SteamVR novamente e os controladores deverão voltar ao normal.
4. Se os problemas persistirem, [arquiva](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) comentários usando Hub do Windows Feedback na categoria Realidade Misturada e inclua o SteamVR no resumo.

Você usará seus controladores de movimento de maneira diferente em jogos diferentes. Aqui estão algumas noções básicas para ajudá-lo a começar:
* Para abrir o painel do Steam, pressione diretamente no thumbstick esquerdo.
* Para sair de um jogo do SteamVR e retornar ao Windows Mixed Reality, pressione o botão Windows entrada. Em seguida, selecione o botão Página Inicial da Realidade Misturada que aparece na tela.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Meus controladores esquerdo e direito são invertidos no SteamVR

Inicie o jogo com seus controladores desligados e, em seguida, a ligue o controlador esquerdo, seguido pelo à direita.

## <a name="my-games-are-running-slowly"></a>Meus jogos estão sendo executados lentamente

1. Certifique-se de que seu computador atenda às especificações do SteamVR Windows Mixed Reality e o jogo que você está fazendo.
2. Na Portal de Realidade Misturada desktop, selecione "Pausar" para interromper a visualização da área de trabalho.
3. Vá **para Configurações > System > Sobre** e, em "especificações Windows", certifique-se de que "Build do sistema operacional" seja 16299.64 ou posterior.
4. Verifique se o computador tem os drivers gráficos mais recentes ("Verificar se há atualizações" no Windows Atualização).
5. Verifique "Gerenciador de Tarefas" para ver quais outros processos podem estar consumindo recursos em seu computador.
6. Verifique se o Steam está baixando um jogo em segundo plano, o que consome recursos e faz os jogos funcionarem incorretamente.
7. Uma pequena classe de aplicativos que não têm uma janela visível (por exemplo, Casa do SteamVR), tem um problema de desempenho conhecido. A maioria dos aplicativos não se enquadra nessa categoria e uma correção estará disponível em uma atualização futura.

Se você ainda estiver com problemas de desempenho inesperados, envie-nos comentários usando o [Hub do Windows Feedback](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Siga as instruções para incluir [um Rastreamento de Desempenho do SteamVR.](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>O SteamVR está mostrando um erro de compositor (por exemplo, "Falha Conexão IPC Compartilhado (400)").

Isso pode acontecer se o headset e o monitor primário estão em dois adaptadores de vídeo diferentes. Anexe o monitor ao mesmo adaptador que o headset e configure-o como o monitor primário no Configurações aplicativo > **Sistema > Exibir**.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>O conteúdo do SteamVR aparece no lugar errado, como abaixo do chão ou acima da minha cabeça

Redefinir sua posição:

1. Selecione o thumbstick do controlador esquerdo para abrir o "Painel do SteamVR".
2. Selecione o botão "Configurações".
3. Selecione "Redefinir Posição Setada".

## <a name="my-steam-app-closed-unexpectedly"></a>Meu aplicativo do Steam foi fechado inesperadamente

O aplicativo Steam será fechado se:

* Você bloqueará a tela do computador
* Remover o headset
* Alternar usuários
* Seu computador vai para sleep
