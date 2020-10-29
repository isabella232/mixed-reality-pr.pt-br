---
title: Perguntas frequentes do WebVR
description: Solução de problemas avançada do Windows Mixed realm que vai além da nossa documentação de suporte padrão do consumidor.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, solução de problemas, erros, ajuda, suporte, WebVR
ms.openlocfilehash: 8bc7ab010c1f6ebddf899262b09ba1d08f4ab3ae
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675475"
---
# <a name="webvr-faqs"></a>Perguntas frequentes do WebVR

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Por que não consigo ver meus controladores ao exibir o conteúdo VR do Edge?

Nem todo o conteúdo do WebVR é criado para dar suporte a controladores de movimento. O WebVR permite que os desenvolvedores de conteúdo ofereçam suporte a diferentes tipos de entrada, como controladores de jogos ou controladores de movimento. Se você não vir seus controladores em um site, ele provavelmente não terá suporte ao controlador de movimento.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Por que não posso usar o mouse em uma exibição WebVR de imersão?

Esse é um recurso opcional da especificação WebVR. Nem todos os navegadores oferecem suporte a esse recurso, e nem todo o conteúdo do WebVR é criado para dar suporte à entrada do mouse. O WebVR permite que os desenvolvedores de conteúdo ofereçam suporte a diferentes tipos de entrada, como mouse, teclado, controladores de jogos ou controladores de movimento. O comportamento de entrada do mouse varia de acordo com o navegador. No Microsoft Edge, os autores de sites devem garantir que eles tomam ' pointerlock ' ao apresentar o fone de ouvido para que a entrada do mouse funcione.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Por que não consigo exibir vídeos de 360 graus do YouTube/Facebook/Vimeo/The Guardian, etc. do Edge em VR?

Há uma especificação WebVR que permite que sites iniciem experiências VR diretamente do navegador e os autores desses sites não implementaram essa especificação no momento. Pode haver aplicativos para download em algumas plataformas que permitem a exibição de conteúdo VR desses fornecedores.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Por que não posso inserir o VR no Firefox ou no Chrome?

O WebVR só tem suporte dos dispositivos Windows Mixed Reality no Edge no momento.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Quando eu inseri o VR em um site, por que vejo uma tela em branco no meu Headset?

O site pode não ter implementado suporte para computadores com várias GPU (incluindo laptops GPU híbridos). Tente:
* Recarregue a página.
* Em computadores desktop, conecte o headset no mesmo adaptador gráfico que o monitor que está exibindo o Microsoft Edge. Conecte ambos à placa gráfica mais alta, não ao adaptador gráfico integrado.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Quando eu sair de VR ao assistir a um vídeo do Edge, o som continuará sendo reproduzido, mas a janela de borda ficará esmaecida.

Esse é um problema conhecido ao executar o WebVR do Edge na casa Cliff da realidade misturada. Para resolvê-lo, pressione escape no teclado em vez de pressionar o botão Windows para sair da experiência do WebVR ou ativar a janela de borda esmaecida selecionando-a e, em seguida, pare o vídeo.

## <a name="can-i-use-webvr-on-the-hololens"></a>Posso usar WebVR no HoloLens?

A Microsoft não anunciou nada sobre WebVR no HoloLens neste momento.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Por que a minha exibição no nível do piso ao exibir o conteúdo do WebVR da borda?

O site não dá suporte adequado a headsets do Windows Mixed Reality. Para solucionar esse problema:
1. Coloque o headset no chão do seu espaço.
2. Navegue até a página do WebVR usando o Microsoft Edge na área de trabalho (não dentro da realidade misturada).
3. Selecione "inserir VR".
4. Aguarde de cinco a 10 segundos para que a experiência entre totalmente no modo de imersão.
5. Colocado no headset.

## <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>A exibição tem uma resolução muito baixa em algumas experiências de WebVR.

Esses sites não dão suporte adequado a headsets de alta resolução. Para solucionar este problema:
* Se iniciar o WebVR da área de trabalho (em vez da realidade misturada Cliff House), verifique se a janela está maximizada antes de selecionar "inserir VR".
* Evite redimensionar a janela do Microsoft Edge depois de inserir o VR.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Por que a exibição de imersão de WebVR é encerrada quando eu altero as guias do navegador?

Este comportamento é esperado. Por motivos de segurança, somente a guia active browser pode acessar fones de ouvido conectados.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Por que não consigo ouvir áudio em uma experiência específica do WebVR?

O site pode estar usando o formato de arquivo de áudio OGG, ao qual o Microsoft Edge não oferece suporte no momento.

Você pode relatar sites desfeitos diretamente à equipe do navegador Microsoft Edge no [Issue Tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)ou por meio do twitter usando [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Por que os comentários do Haptic não funcionam no WebVR com os controladores de movimento?

No momento, o Microsoft Edge não dá suporte a haptics nas extensões da API do gamepad do WebVR.

