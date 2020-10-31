---
title: Usando o WebVR com o Windows Mixed Reality
description: Descreve o WebVR e como usá-lo com o Microsoft Edge em headsets de realidade mista do Windows.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, WebVR, Edge, Microsoft Edge, navegação na Web
ms.openlocfilehash: 8e8d7b5feefe5b1eccad0684808b40b63e9bbbca
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131850"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Usando o WebVR com o Windows Mixed Reality

>[!IMPORTANT]
>A maioria dos navegadores da Web modernos preteriu o suporte de WebVR em favor do WebXR, o novo padrão para a criação de experiências de imersão da Web para headsets de VR. Instale [o novo Microsoft Edge](using-microsoft-edge.md) para obter suporte ao WebXR.

## <a name="what-is-webvr"></a>O que é o WebVR?

[WebVR](https://webvr.info) é uma especificação aberta que possibilita a experiência de VR em seu navegador. Se um site implementar o suporte a WebVR e fornecer conteúdo 3D, ele poderá exibir conteúdo de imersão no headset, com consentimento do usuário.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Qual é a diferença entre WebVR e navegação na Web em VR

WebVR é uma tecnologia que permite que um autor de site adicione a funcionalidade VR a uma página. A API WebVR é usada por uma página para exibir conteúdo 3D (como vídeo 360 graus, ou um modelo 3D ou um jogo 3D) para todo o headset. **Exemplo:** Exibindo um vídeo 360 em [CNN.com/VR](http://cnn.com/vr). Se uma página der suporte a WebVR, ela adicionará um botão ou outro elemento de interface do usuário que você pode clicar para inserir VR.

Navegar na Web em VR significa usar o navegador Edge enquanto você está aproveitando o headset, como um Tablet de aplicativo 2D dentro do Cliffhouse.

## <a name="do-all-websites-support-webvr"></a>Todos os sites dão suporte a WebVR

Não. Os autores de sites devem optar por usar o WebVR e, além disso, podem criar sites que são otimizados para navegadores, headsets e controladores específicos. Por exemplo, um conteúdo de WebVR é otimizado somente para dispositivos móveis de VR. Além disso, tenha em mente que os sites precisam criar e fornecer conteúdo de WebVR explicitamente. O número de sites que têm algum conteúdo compatível com WebVR está crescendo todos os dias.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Posso usar meu Naopak/oculus, etc. para exibir o conteúdo do WebVR no Microsoft Edge

Não. Você deve usar um headset de realidade mista do Windows para usar o WebVR no Edge. No entanto, você pode acessar o conteúdo do WebVR em outro navegador; consulte a lista completa de dispositivos e navegadores compatíveis em: [WebVR. Rocks](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>Onde posso encontrar a documentação do desenvolvedor do WebVR

A documentação do desenvolvedor está localizada aqui: [documentação do desenvolvedor do WebVR](https://docs.microsoft.com/microsoft-edge/webvr/).

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>Encontrei um site com WebVR que não funciona na realidade mista do Windows. O que faço

Você pode relatar sites desfeitos diretamente à equipe do navegador Microsoft Edge no [Issue Tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)ou por meio do twitter usando [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

Você também pode registrar bugs usando o aplicativo Hub de comentários do Windows em Categoria:

Microsoft Edge-problemas de > do site

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>O que é uma boa página para testar se o WebVR está funcionando

Consulte [exemplos de webvr.info](http://webvr.info/samples/XX-vr-controllers.html).

## <a name="how-do-i-set-up-webvr"></a>Como fazer configurar o WebVR

Para experimentar o conteúdo do WebVR em um headset de realidade mista do Windows (usando hardware ou simulação), você deve:

1. Verifique se o headset está conectado.
2. Inicie o Microsoft Edge, seja na área de trabalho ou na realidade misturada.
3. Navegue até uma página habilitada para WebVR.
4. Clique no botão Inserir VR dentro da página (o local e a representação visual desse botão podem variar por site). Pode ser semelhante a: \
   ![Imagem Goggles VR](images/75px-enter-vr.png)
5. Na primeira vez que você tentar inserir VR em um domínio específico, o navegador pedirá consentimento para usar a exibição de imersão, clique em Sim: ![IU de consentimento que é exibida na primeira tentativa de inserir VR em um domínio específico](images/1053px-Webvr-consent-ui.png)
6. O headset deve começar a exibir o conteúdo do WebVR.

## <a name="see-also"></a>Veja também

* [Solução de problemas > WebVR](webvr-questions.md)
* [Como entrar em sua primeira experiência de WebVR](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Usando jogos e aplicativos no Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Sua base de realidade misturada](your-mixed-reality-home.md)
* [Sistema de controle](tracking-system.md)
* [Controladores de movimento](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Comentários de arquivamento](filing-feedback.md)
