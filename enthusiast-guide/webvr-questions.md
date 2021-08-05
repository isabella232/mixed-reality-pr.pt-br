---
title: Perguntas frequentes sobre WebVR
description: Mantenha-se atualizado com a solução de problemas de Realidade Misturada para aplicativos Web que vão além da nossa documentação de suporte ao consumidor padrão.
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Solução de Problemas, Erros, Ajuda, Suporte, WebVR
ms.openlocfilehash: d0f91af9cf14d8019707e504a9f8bc076bbe39db566895f17e1e56d6b906336d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211088"
---
# <a name="webvr-faqs"></a>Perguntas frequentes sobre WebVR

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Por que não consigo ver meus controladores ao exibir o conteúdo de VR do Edge

Nem todo o conteúdo do WebVR é autor para dar suporte a controladores de movimento. O WebVR permite que os desenvolvedores de conteúdo deem suporte a diferentes tipos de entrada, como controladores de jogo ou controladores de movimento. Se você não vir seus controladores em um site, ele provavelmente não terá suporte para o controlador de movimento.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Por que não posso usar o mouse em uma exibição de WebVR imersiva

Usar um mouse é um recurso opcional da especificação WebVR. Nem todos os navegadores suportam esse recurso e nem todo o conteúdo do WebVR é autor para dar suporte à entrada do mouse. O WebVR permite que os desenvolvedores de conteúdo deem suporte a diferentes tipos de entrada, como mouse, teclado, controladores de jogo ou controladores de movimento. O comportamento de entrada do mouse varia de acordo com o navegador. Dentro Microsoft Edge, os autores do site devem garantir que eles levam 'pointerlock' ao apresentar ao headset para que a entrada do mouse funcione.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Por que não consigo exibir vídeos de 360 graus do Youtube/Facebook/Vimeo/The Guardian, etc. do Edge em VR

Há uma especificação webVR que permite aos sites iniciar experiências de VR diretamente do navegador. Os autores desses sites não implementaram essa especificação no momento. Pode haver aplicativos para download em algumas plataformas que permitem a exibição de conteúdo de VR desses fornecedores.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Por que não consigo inserir VR do Firefox ou Chrome

O WebVR só tem suporte Windows Mixed Reality dispositivos no Edge no momento.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Ao inserir a VR de um site, por que vejo uma tela em branco no meu headset

O site pode não ter implementado o suporte para vários computadores GPU (incluindo laptops de GPU híbrida). Tente:

* Recarregue a página.
* Em computadores desktop, conecte o headset ao mesmo adaptador gráfico que o monitor que está exibindo Microsoft Edge. Conecte ambos à placa gráfica de alta potência, não ao adaptador gráfico integrado.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Quando eu sair da VR ao assistir a um vídeo do Edge, o som continuará sendo gravado, mas a janela do Edge fica es cinza

Esse é um problema conhecido ao executar o WebVR do Edge no Casa no Penhasco. Para resolvê-lo, pressione escape no teclado em vez do botão janelas para sair da experiência WebVR ou ative a janela de borda esgoçada selecionando-a e, em seguida, pare o vídeo.

## <a name="can-i-use-webvr-on-the-hololens"></a>Posso usar o WebVR no HoloLens

A Microsoft não anunciou nada sobre o WebVR no HoloLens neste momento.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Por que minha exibição está no nível do chão ao exibir o conteúdo webVR do Edge

O site não dá suporte corretamente Windows Mixed Reality headsets. Para solucionar esse problema:

1. Coloque o headset no chão do seu espaço.
2. Navegue até a página WebVR usando Microsoft Edge na área de trabalho (não dentro da realidade misturada).
3. Selecione "Inserir VR".
4. Aguarde de cinco a 10 segundos para que a experiência entre totalmente no modo imersivo.
5. Coloque o headset.

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a>A exibição é de baixa resolução em algumas experiências de WebVR

Esses sites não são compatíveis corretamente com headsets de alta resolução. Para solucionar esse problema:

* Se estiver iniciando o WebVR da área de trabalho (em vez da realidade misturada Casa no Penhasco), verifique se a janela está maximizada antes de selecionar "Inserir VR".
* Evite reizing da janela Microsoft Edge depois de entrar em VR.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Por que a exibição imersiva do WebVR sai quando eu altero as guias do navegador

Esse comportamento é esperado. Por motivos de segurança, somente a guia do navegador ativo pode acessar headsets conectados.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Por que não consigo ouvir áudio em uma experiência WebVR específica

O site pode estar usando o formato de arquivo de áudio OGG, que Microsoft Edge não dá suporte no momento.

Você pode relatar sites desfeitos diretamente à Microsoft Edge do navegador no [rastreador](https://developer.microsoft.com/microsoft-edge/platform/issues/)de problemas ou por meio do Twitter [usando #EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Por que os comentários não funcionam no WebVR com controladores de movimento

Microsoft Edge atualmente não dá suporte a tics nas extensões da API do gamepad WebVR.