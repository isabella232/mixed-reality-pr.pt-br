---
title: Visão geral do desenvolvimento de JavaScript
description: Visão geral do desenvolvimento de realidade mista usando JavaScript para fones de ouvido de imersão Web, móvel e Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 conteúdo, imersão Web, imersão-Web, IW, immersiveweb
ms.openlocfilehash: 051c6079da939224c88d6414978b2b4b0e67f87c
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104908993"
---
# <a name="javascript-development-overview"></a>Visão geral do desenvolvimento em JavaScript

O JavaScript é uma das linguagens de programação mais populares do mundo! É simples, leve e amplamente usado na Web. Aproveite o poder de seu JavaScript e suas habilidades na Web para criar experiências de realidade misturadas mais atraentes.

## <a name="mixed-reality-applications-on-the-web"></a>Aplicativos de realidade misturada na Web

Os recursos misturados da realidade estão disponíveis na Web pelo uso de [WebXR](webxr-overview.md). Você pode ver o VR (realidade virtual) e o conteúdo da Reality (AR) em um navegador compatível com WebXR habilitado, sem instalar nenhum software ou plug-ins adicionais. Você pode usar esse mesmo navegador com um dispositivo físico como o HoloLens 2. Confira nossa documentação do [WebXR](webxr-overview.md) para obter mais detalhes.

> [!NOTE]
> O **WebVR** foi preterido e não está disponível nos navegadores atuais, portanto, ele não deve ser usado para nenhum novo desenvolvimento. Você precisará migrar todas as implementações de **WebVR** existentes para o **WebXR**.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>O que posso usar para desenvolver experiências de imersão na Web?

A lista a seguir mostra as estruturas e APIs do JavaScript para a criação de experiências de imersão que atualmente dominam o mercado e são amplamente aceitas e adotadas por desenvolvedores JavaScript de realidade misturada:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> O Babylon é um mecanismo 3D de JavaScript que facilita o desenvolvimento de conteúdo 3D e de aplicativos de imersão. Antes de começar a usar aplicativos de imersão, é recomendável aprender os conceitos básicos do desenvolvimento de Babylon.js.<br/><br/>-Saiba como criar aplicativos 3D com babylon.js [introdução](https://doc.babylonjs.com/start).<br/>-Brincar com exemplos 3D e seu código-fonte usando babylon.js [playground](https://doc.babylonjs.com/examples/)<br/>-Aprofunde-se no [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-Saiba como começar com nossos tutoriais [criar seu primeiro aplicativo "Olá, mundo!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Logotipo do BabylonJS](images/babylon.js.example.png) |
|[**Um quadro**](https://aframe.io/) <br/><br/>Um quadro é uma estrutura de JavaScript declarativa para começar com a realidade virtual na Web. Confira a [documentação de um quadro](https://aframe.io/docs/1.2.0/introduction/) para saber mais. |![Um quadro](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js é uma biblioteca 3D popular para a criação de experiências de imersão. Saiba mais sobre [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) na página de documentação e explorando [exemplos](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Você pode acessar as APIs do dispositivo WebXR diretamente usando APIs do WebGL. WebGL (Web Graphics Library) é uma API de JavaScript para renderizar gráficos interativos 3D e 2D de alto desempenho em qualquer navegador da Web compatível sem o uso de plug-ins. |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>Próximas etapas

Saiba como começar a usar nossos tutoriais.

> [!div class="nextstepaction"]
> [Criar seu primeiro aplicativo "Olá, Mundo!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>Consulte Também

* [Visão geral do WebXR](webxr-overview.md)
* [Especificação de API do dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentação da API do dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Exemplos de WebXR](https://immersive-web.github.io/webxr-samples/)
* [Usando Babylon.js para criar experiências de WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Realidade mista do Windows e o novo Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [GitHub W3C da Web de imersão](https://github.com/immersive-web)
* [API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)
