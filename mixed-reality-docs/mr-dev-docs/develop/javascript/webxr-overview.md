---
title: Usando o WebXR com o Windows Mixed Reality
description: Aprenda as noções básicas de como usar e desenvolver para aplicativos WebXR executados em headsets de imersão de realidade mista do Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 Content, imersão Web, immersiveweb, IW
ms.openlocfilehash: f29be9af3a2dd1d13b301988845d0cc322e9d4de
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394370"
---
# <a name="webxr-overview"></a>Visão geral do WebXR

## <a name="javascript-development"></a>Desenvolvimento de JavaScript

O JavaScript é uma das linguagens de programação mais populares do mundo! É simples, leve e amplamente usado na Web. Aproveite o poder de seu JavaScript e suas habilidades na Web para criar experiências de realidade misturadas mais atraentes.

## <a name="mixed-reality-applications-on-the-web"></a>Aplicativos de realidade misturada na Web

Os recursos misturados da realidade estão disponíveis na Web pelo uso de [WebXR](webxr-overview.md). Você pode ver o VR (realidade virtual) e o conteúdo da Reality (AR) em um navegador compatível com WebXR habilitado, sem instalar nenhum software ou plug-ins adicionais. Você pode usar esse mesmo navegador com um dispositivo físico como o HoloLens 2.

A [**API do dispositivo WebXR**](https://www.w3.org/TR/webxr/) é para acessar os dispositivos **VR (realidade virtual)** e **ar (realidade aumentada)** , incluindo **sensores** e **exibições montadas no cabeçalho** na **Web**. A API do dispositivo WebXR está disponível atualmente no Microsoft Edge, e o Chrome versão 79 e versões posteriores dão suporte a WebXR como padrão. Você pode verificar o status de suporte do navegador mais recente para WebXR em [caniuse.com](https://caniuse.com/#search=webxr).

> [!NOTE]
> O **WebVR** foi preterido e não está disponível nos navegadores atuais, portanto, ele não deve ser usado para nenhum novo desenvolvimento. Você precisará migrar todas as implementações de **WebVR** existentes para o **WebXR**.

### <a name="viewing-webxr"></a>Exibindo WebXR

Você pode exibir WebXR experinces no [Windows Mixed Reality e a nova realidade do Microsoft Edge e do](../../whats-new/new-microsoft-edge.md) [Firefox](https://mixedreality.mozilla.org/firefox-reality/).
Para testar se o navegador dá suporte a WebXR, você pode navegar até [exemplos de WebXR](https://immersive-web.github.io/webxr-samples/) no navegador

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>O que posso usar para desenvolver experiências de imersão na Web?

A lista a seguir mostra as estruturas e APIs do JavaScript para a criação de experiências de imersão que atualmente dominam o mercado e são amplamente aceitas e adotadas por desenvolvedores JavaScript de realidade misturada:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> O Babylon é um mecanismo 3D de JavaScript que facilita o desenvolvimento de conteúdo 3D e de aplicativos de imersão. Antes de começar a usar aplicativos de imersão, é recomendável aprender os conceitos básicos do desenvolvimento de Babylon.js.<br/><br/>-Saiba como criar aplicativos 3D com babylon.js [introdução](https://doc.babylonjs.com/start).<br/>-Brincar com exemplos 3D e seu código-fonte usando babylon.js [playground](https://doc.babylonjs.com/examples/)<br/>-Aprofunde-se no [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-Saiba como começar com nossos tutoriais [criar seu primeiro aplicativo "Olá, mundo!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Logotipo do BabylonJS](images/babylon.js.example.png) |
|[**Um quadro**](https://aframe.io/) <br/><br/>Um quadro é uma estrutura de JavaScript declarativa para começar com a realidade virtual na Web. Confira a [documentação de um quadro](https://aframe.io/docs/1.2.0/introduction/) para saber mais. |![Um quadro](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js é uma biblioteca 3D popular para a criação de experiências de imersão. Saiba mais sobre [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) na página de documentação e explorando [exemplos](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Você pode acessar as APIs do dispositivo WebXR diretamente usando APIs do WebGL. WebGL (Web Graphics Library) é uma API de JavaScript para renderizar gráficos interativos 3D e 2D de alto desempenho em qualquer navegador da Web compatível sem o uso de plug-ins. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>Consulte Também

* [Visão geral do WebXR](webxr-overview.md)
* [Especificação de API do dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentação da API do dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Exemplos de WebXR](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Usando Babylon.js para criar experiências de WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Realidade mista do Windows e o novo Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [Manipulando o contexto perdido no WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Grupo de comunidades da Web de imersão](https://www.w3.org/community/immersive-web/)
* [GitHub W3C da Web de imersão](https://github.com/immersive-web)