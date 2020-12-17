---
title: Visão geral do desenvolvimento nativo
description: Crie um mecanismo de realidade mista com base em DirectX usando as APIs de realidade mista do Windows diretamente.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, renderização Holographic, nativo, aplicativo nativo, WinRT, aplicativo WinRT, APIs de plataforma, mecanismo personalizado, middleware, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 493715660ff8df79df25e09c82fe48b863053ed3
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613070"
---
# <a name="native-development-overview"></a>Visão geral do desenvolvimento nativo

![Logotipo de faixa nativa](../images/native_logo_banner.png)

mecanismos 3D como [Unity](../unity/unity-development-overview.md) ou [inreal](../unreal/unreal-development-overview.md) não são os únicos caminhos de desenvolvimento de realidade misturados abertos para você. Você também pode criar aplicativos de realidade misturada usando as APIs de realidade mista do Windows com DirectX 11 ou DirectX 12. Acessando a origem da plataforma, você está basicamente criando seu próprio middleware ou estrutura. 

> [!IMPORTANT]
> Se você tiver um projeto WinRT existente que gostaria de manter, vá para nossa documentação principal do [winrt](creating-a-holographic-directx-project.md). 

## <a name="development-checkpoints"></a>Pontos de verificação de desenvolvimento

Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unity para o mundo da realidade misturada.

### <a name="1-getting-started"></a>1. Introdução

O Windows Mixed Reality dá suporte a [dois tipos de aplicativos](../../design/app-views.md):
* Aplicativos UWP ou Win32 **mistos de realidade** que usam a [API HOLOGRAPHICSPACE](getting-a-holographicspace.md) ou a [API OpenXR](openxr.md) para processar uma [exibição imersiva](../../design/app-views.md) que preenche a tela do headset
* **aplicativos 2D** (UWP) que usam DirectX, XAML ou outra estrutura para renderizar [exibições 2D](../../design/app-views.md#2d-views) em slates na página inicial do Windows Mixed Reality

As diferenças entre o desenvolvimento DirectX para [exibições 2D e exibições de imersão](../../design/app-views.md) envolvem principalmente a renderização Holographic e a entrada espacial. O [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) do seu aplicativo UWP ou o HWND do seu aplicativo Win32 são necessários e permanecem basicamente os mesmos. O mesmo é verdadeiro para as APIs do WinRT que estão disponíveis para seu aplicativo. Mas você deve usar um subconjunto diferente dessas APIs para aproveitar os recursos do Holographic. Por exemplo, o sistema para aplicativos Holographic gerencia o SwapChain e o quadro presente para habilitar um loop de quadro previsto para pose.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Blocos principais de construção

Os aplicativos do Windows Mixed Reality usam as seguintes APIs para criar experiências de [realidade mista](../../discover/mixed-reality.md) para o HoloLens e outros headsets de imersão:

|  Recurso  |  Funcionalidade  |
| --- | --- |
| [Foco](../../design/gaze-and-commit.md) | Permitir que os usuários direcionem hologramas olhando para eles |
| [Gesto](../../design/gaze-and-commit.md#composite-gestures) | Adicionar ações espaciais aos seus aplicativos |
| [Renderização holográfica](../platform-capabilities-and-apis/rendering.md) | Desenhe um holograma em um local preciso no mundo em seus usuários |
| [Controlador de movimento](../../design/motion-controllers.md) | Permitir que os usuários executem ações em seus ambientes de realidade misturada |
| [Mapeamento espacial](../../design/spatial-mapping.md) | Mapear seu espaço físico com uma sobreposição de malha virtual para marcar os limites do seu ambiente |
| [Voz](../../design/voice-input.md) | Capturar palavras-chave e frases faladas e ditado dos seus usuários |
 
> [!NOTE]
> Você pode encontrar recursos centrais futuros e no desenvolvimento na documentação do [mapa](openxr.md#roadmap) do OpenXR.

### <a name="3-deploying-and-testing"></a>3. implantação e teste

Você pode desenvolver em um desktop usando OpenXR em um fone de ouvido de imersão 2 ou Windows Mixed realm.  Se você não tiver acesso a um headset, poderá usar o [emulador do HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou o [simulador de realidade mista do Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .

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
