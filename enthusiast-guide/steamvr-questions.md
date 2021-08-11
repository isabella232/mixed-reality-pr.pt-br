---
title: Perguntas frequentes do SteamVR
description: SteamVR Windows Mixed Reality solução de problemas que vai além da nossa documentação de suporte de consumidor padrão.
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, solução de problemas, erros, ajuda, suporte, SteamVR
ms.openlocfilehash: 0fb9c07dda8fe354966403bc9c6a21acb600e61cb943c270eb9c87f5ec2fb89a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199492"
---
# <a name="steamvr-faqs"></a>Perguntas frequentes do SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>como posso jogar SteamVR games em meu fone de ouvido Windows Mixed Reality

1. [Baixe e instale o SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe). O tutorial do SteamVR deve ser iniciado automaticamente quando você inicia o SteamVR.
2. Conexão o headset ao seu PC e ligar seus controladores de movimento.
3. depois que Windows Mixed Reality página inicial tiver carregado e seus controladores estiverem visíveis, abra o aplicativo de fluxo em sua área de trabalho.
4. Use o aplicativo de fluxo para iniciar um jogo SteamVR da sua biblioteca de fluxo. para iniciar jogos do SteamVR sem retirar seu headset, encontre-os e inicie-os em Windows Mixed Reality **iniciar > todos os aplicativos**.

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>uma mensagem diz "para usar o SteamVR com Windows Mixed Reality, você precisa instalar o último Windows Update" ou "Windows o modo de desenvolvedor necessário"

1. Verifique se o computador está executando a versão mais recente do Windows 10. acesse **Configurações > System > sobre** e, em "especificações de Windows", verifique se "Build do sistema operacional" é 16299,64 ou superior.
2. Verifique se você não tem nenhuma atualização aguardando para baixar ou instalar. vá para **Configurações > atualizar & > de segurança Windows Update** e selecione "verificar atualizações". Talvez você precise marcar várias vezes até que nenhuma atualização adicional esteja disponível e, em seguida, reiniciar o computador.

## <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR está falhando após a atualização Windows

algumas versões mais antigas do Windows Mixed Reality para SteamVR não são mais compatíveis com Windows. para garantir que sua versão do Windows Mixed Reality para SteamVR seja atual:

1. em sua biblioteca de fluxo, acesse **Software > Windows Mixed Reality para SteamVR**.
2. Clique com o botão direito do mouse e vá para "Propriedades".
3. Selecione a guia "atualizar" e "sempre manter este aplicativo atualizado".
4. Force a atualização acessando a guia "arquivos locais" e selecionando "verificar a integridade dos arquivos de aplicativo".
5. Reinicie o fluxo e o SteamVR.

se o SteamVR ainda estiver falhando após a atualização, você poderá ter duas instalações do Windows Mixed Reality para SteamVR em seu computador. Para confirmar:

1. localize ```%localappdata%\openvr\openvrpaths.vrpath``` e abra-o no Bloco de notas.
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
2. volte para Windows Mixed Reality página inicial e confirme se os controladores estão funcionando.
3. Inicie a experiência do SteamVR novamente e os controladores devem voltar ao normal.
4. se os problemas persistirem, envie comentários por arquivo usando o [Hub do Windows Feedback](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) na categoria de realidade misturada e inclua SteamVR no resumo.

Você usará seus controladores de movimento de forma diferente em jogos diferentes. Aqui estão alguns conceitos básicos para ajudá-lo a começar:
* Para abrir o painel de fluxo, pressione direto para baixo no Thumbstick esquerdo.
* para sair de um jogo do SteamVR e retornar para a página inicial do Windows Mixed Reality, pressione o botão Windows. Em seguida, selecione o botão Home da realidade misturada que aparece na tela.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Meus controladores à esquerda e à direita são revertidos no SteamVR

Inicie o jogo com seus controladores e, em seguida, ligue o controlador à esquerda, seguido do lado direito.

## <a name="my-games-are-running-slowly"></a>Meus jogos estão em execução lenta

1. verifique se seu PC atende às especificações de SteamVR no Windows Mixed Reality e no jogo que você está jogando.
2. No portal da realidade misturada na área de trabalho, selecione "Pausar" para parar a visualização da área de trabalho.
3. vá para **Configurações > System > sobre** e, em "especificações de Windows", verifique se "Build do sistema operacional" é 16299,64 ou posterior.
4. verifique se seu PC tem os drivers gráficos mais recentes ("verificar se há atualizações" em Windows Update).
5. Marque "Gerenciador de tarefas" para ver quais outros processos podem estar consumindo recursos em seu computador.
6. Verifique se o vapor está baixando um jogo em segundo plano, que consome recursos e faz com que os jogos sejam executados de forma ruim.
7. Uma pequena classe de aplicativos que não têm uma janela visível (por exemplo, SteamVR Home), tem um problema de desempenho conhecido. A maioria dos aplicativos não se enquadra nessa categoria, e uma correção estará disponível em uma atualização futura.

se você ainda estiver executando problemas de desempenho inesperados, envie-nos comentários usando o [Hub do Windows Feedback](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Certifique-se de seguir as instruções para [incluir um rastreamento de desempenho SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr).

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR está mostrando um erro de compositor (por exemplo, "Shared IPC compositor Conexão falhou (400)").

Isso pode acontecer se o headset e o monitor primário estiverem em dois adaptadores de vídeo diferentes. anexe o monitor ao mesmo adaptador de seu headset e configure-o como o monitor primário em **Configurações aplicativo > sistema > exibir**.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>O conteúdo do SteamVR aparece no lugar errado, como abaixo do piso ou acima da minha cabeça

Redefina sua posição:

1. Selecione o Thumbstick do controlador à esquerda para abrir o "painel do SteamVR".
2. selecione o botão "Configurações".
3. Selecione "redefinir posição encaixada".

## <a name="my-steam-app-closed-unexpectedly"></a>Meu aplicativo de fluxo fechou inesperadamente

O aplicativo de fluxo será fechado se:

* A tela do seu PC é bloqueada
* Remover o headset
* Trocar usuários
* Seu computador vai para o estado de suspensão
