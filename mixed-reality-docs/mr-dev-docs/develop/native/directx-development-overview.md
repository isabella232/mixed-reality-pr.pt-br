---
title: Visão geral do desenvolvimento nativo
description: saiba como criar um mecanismo de realidade misturada baseado em DirectX usando as APIs de Windows Mixed Reality diretamente.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, renderização Holographic, nativo, aplicativo nativo, WinRT, aplicativo WinRT, APIs de plataforma, mecanismo personalizado, middleware, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 056cb0c07002cb319e8acadf66e7f59650f5e00413440d6ad0103aa8ee936400
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200136"
---
# <a name="native-development-overview"></a>Visão geral do desenvolvimento nativo

![Logotipo de faixa nativa](../images/native_logo_banner.png)

mecanismos 3D como [Unity](../unity/unity-development-overview.md) ou [inreal](../unreal/unreal-development-overview.md) não são os únicos caminhos de desenvolvimento de realidade misturados abertos para você. você também pode criar aplicativos de realidade misturada usando as APIs de Windows Mixed Reality com directx 11 ou directx 12. Acessando a origem da plataforma, você está basicamente criando seu próprio middleware ou estrutura. 

> [!IMPORTANT]
> Se você tiver um projeto WinRT existente que gostaria de manter, vá para nossa documentação principal do [winrt](creating-a-holographic-directx-project.md). 

## <a name="development-checkpoints"></a>Pontos de verificação de desenvolvimento

Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unity para o mundo da realidade misturada.

### <a name="1-getting-started"></a>1. Introdução

o Windows Mixed Reality dá suporte a [dois tipos de aplicativos](../../design/app-views.md):
* Aplicativos UWP ou Win32 **mistos de realidade** que usam a [API HOLOGRAPHICSPACE](getting-a-holographicspace.md) ou a [API OpenXR](openxr.md) para processar uma [exibição imersiva](../../design/app-views.md) que preenche a tela do headset
* **aplicativos 2d** (UWP) que usam DirectX, XAML ou outra estrutura para renderizar [exibições 2d](../../design/app-views.md#2d-views) em slates na Windows Mixed Reality página inicial

As diferenças entre o desenvolvimento DirectX para [exibições 2D e exibições de imersão](../../design/app-views.md) envolvem principalmente a renderização Holographic e a entrada espacial. O [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) do seu aplicativo UWP ou o HWND do seu aplicativo Win32 são necessários e permanecem basicamente os mesmos. O mesmo é verdadeiro para as APIs do WinRT que estão disponíveis para seu aplicativo. Mas você deve usar um subconjunto diferente dessas APIs para aproveitar os recursos do Holographic. Por exemplo, o sistema para aplicativos Holographic gerencia o SwapChain e o quadro presente para habilitar um loop de quadro previsto para pose.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Blocos principais de construção

Windows Mixed Reality aplicativos usam as seguintes APIs para criar experiências de [realidade mista](../../discover/mixed-reality.md) para HoloLens e outros headsets de imersão:

|  Recurso  |  Funcionalidade  |
| --- | --- |
| [Foco](../../design/gaze-and-commit.md) | Permitir que os usuários direcionem hologramas olhando para eles |
| [Gesto](../../design/gaze-and-commit.md#composite-gestures) | Adicionar ações espaciais aos seus aplicativos |
| [Renderização holográfica](../platform-capabilities-and-apis/rendering.md) | Desenhe um holograma em um local preciso no mundo em seus usuários |
| [Controlador de movimento](../../design/motion-controllers.md) | Permitir que os usuários executem ações em seus ambientes de realidade misturada |
| [Mapeamento espacial](../../design/spatial-mapping.md) | Mapeie seu espaço físico com uma sobreposição de malha virtual para marcar os limites do seu ambiente |
| [Voz](../../design/voice-input.md) | Capturar palavras-chave e frases faladas e ditado dos seus usuários |
 
> [!NOTE]
> Você pode encontrar recursos centrais futuros e no desenvolvimento na documentação do [mapa](openxr.md#roadmap) do OpenXR.

### <a name="3-deploying-and-testing"></a>3. implantação e teste

você pode desenvolver em uma área de trabalho usando OpenXR em um HoloLens 2 ou Windows Mixed Reality headset de imersão.  se você não tiver acesso a um headset, poderá usar o [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou o [simulador de Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) em vez disso.

## <a name="whats-next"></a>E agora?

O trabalho de um desenvolvedor nunca termina, especialmente ao aprender uma nova ferramenta ou um SDK. As seções a seguir podem levá-lo para áreas além do material de nível de iniciante que você já concluiu. Esses tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para pular e explorar!

### <a name="additional-resources"></a>Recursos adicionais

Se você pretende nivelar o jogo do OpenXR, confira os links abaixo:

* [Práticas recomendadas do OpenXR](openxr-best-practices.md)
* [Desempenho do OpenXR](openxr-performance.md)
* [Solução de problemas do OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>Confira também
* [Modelo de aplicativo](../../design/app-model.md)
* [Modos de exibição do aplicativo](../../design/app-views.md)