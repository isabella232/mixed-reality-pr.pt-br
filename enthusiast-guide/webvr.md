---
title: Usando o WebVR com Windows Mixed Reality
description: Conheça as noções básicas do WebVR, como usá-lo com Microsoft Edge headsets Windows Mixed Reality e problemas comuns de solução de problemas.
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, WebVR, Edge, Microsoft Edge, navegação na Web
ms.openlocfilehash: f61fff3c8d5083236c10d79d3824c489111f8d2be2138984f5613f295849bdf2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214120"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Usando o WebVR com Windows Mixed Reality

>[!IMPORTANT]
>A maioria dos navegadores da Web modernos tem o suporte preterido do WebVR em favor do WebXR, o novo padrão para criar experiências da Web imersivas para headsets de VR. Instale o [novo Microsoft Edge](using-microsoft-edge.md) para suporte a WebXR.

## <a name="what-is-webvr"></a>O que é WebVR

[O WebVR](https://webvr.info) é uma especificação aberta que permite que você experimente a VR em um navegador. Se um site implementa o suporte a WebVR e fornece conteúdo 3D, ele pode exibir conteúdo imersivo no headset, com consentimento do usuário.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Qual é a diferença entre o WebVR e a navegação na Web em VR

O WebVR é uma tecnologia que permite que um autor do site adicione funcionalidade de VR a uma página. A API WebVR é usada por uma página para exibir conteúdo 3D (como vídeo de 360 graus ou um modelo 3D ou um jogo 3D) para toda a parte do headset. **Exemplo:** Exibindo um vídeo 360 [no cnn.com/vr](http://cnn.com/vr). Se uma página for compatível com WebVR, ela adicionará um botão ou outro elemento de interface do usuário que você pode selecionar para inserir VR.

Navegar pela Web em VR significa usar o navegador Edge enquanto você estiver usando o headset, como um slate de aplicativo 2D dentro doHouse.

## <a name="do-all-websites-support-webvr"></a>Todos os sites são suportados por WebVR

Não. Os autores de site devem optar por usar o WebVR e podem criar sites otimizados para navegadores, headsets e controladores específicos. Algum conteúdo webVR é otimizado somente para dispositivos móveis de VR. Além disso, tenha em mente que os sites precisam criar e fornecer conteúdo de WebVR explicitamente. O número de sites que têm algum conteúdo compatível com WebVR está crescendo todos os dias.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Posso usar minha Oculus/Oculus etc para exibir o conteúdo do WebVR em Microsoft Edge

Não. Um Windows Mixed Reality headset é necessário para usar o WebVR no Edge. No entanto, você pode acessar o conteúdo do WebVR em outro navegador; consulte a lista completa de dispositivos e navegadores compatíveis em: [WebVR.rocks.](http://webvr.rocks/)

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>Onde posso encontrar a documentação do desenvolvedor do WebVR

A documentação do desenvolvedor está localizada aqui: [Documentação do desenvolvedor do WebVR.](/microsoft-edge/webvr/)

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>Encontrei um site com WebVR que não funciona no Windows Mixed Reality. O que fazer?

Você pode relatar sites desfeitos diretamente à Microsoft Edge do navegador no [rastreador](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)de problemas ou por meio do Twitter [usando #EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

Você também pode registrar bugs usando o aplicativo Hub do Windows Feedback na categoria:

Microsoft Edge -> site

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>O que é uma boa página para testar se o WebVR está funcionando

Consulte [webvr.info exemplos](http://webvr.info/samples/XX-vr-controllers.html).

## <a name="how-do-i-set-up-webvr"></a>Como fazer configurar o WebVR

Para experimentar o conteúdo do WebVR em um headset Windows Mixed Reality (usando hardware ou simulação), você deve:

1. Verifique se o headset está conectado.
2. Iniciar Microsoft Edge, seja na área de trabalho ou na Realidade Misturada.
3. Navegue até uma página habilitada para WebVR.
4. Selecione o botão Inserir VR na página (o local e a representação visual desse botão podem variar por site). Pode ser semelhante a:\
   ![Imagem de alternâncias de VR](images/75px-enter-vr.png)
5. Na primeira vez que você tentar inserir VR em um domínio específico, o navegador solicitará consentimento para usar a exibição imersiva, selecione sim: ![Interface do usuário de consentimento exibida na primeira tentativa de Inserir VR em um domínio específico](images/1053px-Webvr-consent-ui.png)
6. O headset deve começar a exibir o conteúdo do WebVR.

## <a name="see-also"></a>Confira também

* [Solução de > WebVR](webvr-questions.md)
* [Como entrar em sua primeira experiência webVR](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Usando jogos e aplicativos no Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Sua página de casa de realidade misturada](your-mixed-reality-home.md)
* [Sistema de acompanhamento](tracking-system.md)
* [Controladores de movimento](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Arquivar comentários](filing-feedback.md)