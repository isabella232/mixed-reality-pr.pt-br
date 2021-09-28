---
title: Usando o WebXR com Windows Mixed Reality
description: Conheça as noções básicas de como usar e desenvolver aplicativos WebXR em execução Windows Mixed Reality headsets imersivos.
author: yonet
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 vídeo, 360 vídeos, 360 fotos, 360 fotos, 360 conteúdo, web imersiva, immersiveweb, IW
ms.openlocfilehash: b0ab1eab5f1c3e546dde367c2cdb992fba7b452d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148691"
---
# <a name="javascript-development-with-webxr"></a>Desenvolvimento em JavaScript com WebXR

O JavaScript é uma das linguagens de programação mais populares do mundo! Ele é simples, leve e amplamente usado na Web. Aproveite o poder de suas habilidades do JavaScript e da Web para criar experiências de Realidade Misturada mais envolvente.

## <a name="mixed-reality-applications-on-the-web"></a>Aplicativos de Realidade Misturada na Web

Os recursos de Realidade Misturada estão disponíveis na Web por meio [do WebXR.](webxr-overview.md) Você pode ver o conteúdo de VR (realidade virtual) e AR (realidade aumentada) em um navegador compatível habilitado para WebXR sem instalar nenhum software ou plug-in adicional. Você pode usar esse mesmo navegador com um dispositivo físico como o HoloLens 2.

A [**API de Dispositivo WebXR**](https://www.w3.org/TR/webxr/) é para acessar dispositivos de VR (realidade virtual) e ar (realidade aumentada), incluindo sensores e telas montadas com a cabeça, na Web. A API de Dispositivo WebXR está disponível no Microsoft Edge e Chrome versão 79 e versões posteriores são compatíveis com o WebXR como padrão. Você pode verificar o status de suporte mais recente do navegador para WebXR [em caniuse.com](https://caniuse.com/#search=webxr).

> [!NOTE]
> **O WebVR** foi preterido e não está disponível em navegadores atuais, portanto, ele não deve ser usado para nenhum novo desenvolvimento. Você precisará migrar todas as implementações **webVR** existentes para o **WebXR.**

| Recurso WebXR | Disponibilidade |
|---------|---------|
|[API de Dispositivo WebXR (w3.org)](https://www.w3.org/TR/webxr/) | Edge 81 no Windows Desktop <br>Edge 91 no Hololens 2|
|[Módulo de Realidade Aumentada do WebXR – Nível 1 (w3.org)](https://www.w3.org/TR/webxr-ar-module-1/)|Edge 91. Somente Hololens 2|
|[Módulo de entrada manual do WebXR – Nível 1 (w3.org)](https://www.w3.org/TR/webxr-hand-input-1/)|Edge 93. Somente Hololens 2|
|[Módulo âncoras WebXR (immersive-web.github.io)](https://immersive-web.github.io/anchors/)|Edge 93. Somente Hololens 2|
|[Módulo de teste de acerto do WebXR (immersive-web.github.io)](https://immersive-web.github.io/hit-test/)|Edge 93. Somente Hololens 2 |

### <a name="viewing-webxr"></a>Exibindo o WebXR

Você pode exibir experiências do WebXR Windows Mixed Reality com os novos navegadores [Microsoft Edge](../../whats-new/new-microsoft-edge.md) [e Firefox Reality.](https://mixedreality.mozilla.org/firefox-reality/)
Para testar se o navegador dá suporte ao WebXR, você pode navegar até [Exemplos do WebXR](https://immersive-web.github.io/webxr-samples/) em seu navegador.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>O que posso usar para desenvolver experiências imersivas na Web?

A lista a seguir mostra as apIs e estruturas JavaScript para criar experiências imersivas que atualmente dominam o mercado e são amplamente aceitas e adotadas por desenvolvedores javaScript de realidade misturada:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> O Apple é um mecanismo 3D javaScript que facilita o desenvolvimento de conteúdo 3D e aplicativos imersivos. Antes de começar a usar aplicativos imersivos, recomendamos que você aprenda os conceitos básicos Babylon.js desenvolvimento.<br/><br/>– Saiba como criar aplicativos 3D com o babylon.js: [Guia de Início](https://doc.babylonjs.com/start)<br/>- Reproduzir com exemplos 3D e seu código-fonte usando babylon.js: [Playground](https://doc.babylonjs.com/examples/)<br/>- Aprofunde-se [no WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>– Saiba como começar a usar nossos tutoriais: Criar seu primeiro aplicativo ["Olá, Mundo!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Logotipo do AppleJS](images/babylon.js.example.png) |
|[**Quadro A**](https://aframe.io/) <br/><br/>Um quadro é uma estrutura declarativa do JavaScript que você pode usar para começar a usar a Realidade Virtual na Web. Para saber mais, confira a [documentação do A-Frame](https://aframe.io/docs/1.2.0/introduction/) |![Quadro A](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js é uma biblioteca 3D popular para criar experiências imersivas. Saiba mais sobre [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) [exemplos de exploração.](https://threejs.org/examples/#webgl_animation_cloth) |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Você pode acessar as APIs de dispositivo WebXR diretamente usando APIs WebGL. WebGL (Web Graphics Library) é uma API JavaScript para renderizar gráficos 3D e 2D interativos de alto desempenho em qualquer navegador da Web compatível sem o uso de plug-ins. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>Consulte Também

* [Especificação da API de Dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentação da API de Dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Exemplos do WebXR](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Usando Babylon.js para criar experiências webXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [Api do Gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [Extensões do Gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality e o novo Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [Manipulando contexto perdido no WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Ponteiro de ponteiro](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Grupo de comunidade da Web imersivo](https://www.w3.org/community/immersive-web/)
* [Github web imersivo W3C](https://github.com/immersive-web)

## <a name="next-steps--tutorials"></a>Próximas etapas – Tutoriais

> [!div class="nextstepaction"]
> [Crie seu primeiro aplicativo WebXR usando Babylon.js](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

> [!div class="nextstepaction"]
> [Criar um novo no WebXR usando Babylon.js](tutorials/babylonjs-webxr-piano/introduction-01.md)
