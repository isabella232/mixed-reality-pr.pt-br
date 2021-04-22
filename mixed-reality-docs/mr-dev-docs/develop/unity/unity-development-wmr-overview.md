---
title: Desenvolvimento do Unity para VR
description: Introdução à criação de aplicativos de realidade misturada no Unity para headsets imersivos de VR e do Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realidade misturada, desenvolvimento, introdução, novo projeto, portabilidade, funcionalidade, câmera, simulação, emulação, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, o que é realidade virtual, o que é realidade aumentada, MRTK, kit de ferramentas de realidade misturada, entrada de voz, câmera localizável, emulador, Azure, tutoriais
ms.openlocfilehash: 50300ff08dd06c5fc250bc93979d537e10b38044
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528713"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>Desenvolvimento do Unity para VR e Windows Mixed Reality

![Logotipo do banner do Unity](../images/unity_logo_banner.png)

Se você não tem familiaridade com o Unity, recomendamos explorar os [tutoriais](https://unity3d.com/learn/tutorials) de nível iniciante na plataforma Unity Learn antes de continuar. Também é uma boa ideia acessar [fóruns de Realidade Misturada do Unity](https://forum.unity3d.com/forums/hololens.102/) para interagir com a comunidade online que cria aplicativos de realidade misturada. Você nunca sabe quais recursos ou soluções interessantes pode encontrar por aí. Quando você estiver pronto para começar a usar o MRTK, vá para os pontos de verificação de desenvolvimento abaixo!

> [!IMPORTANT]
> Se você já tem um projeto Unity que deseja mover para o headset imersivo do Windows Mixed Reality, confira nossos **[guias de portabilidade](../porting-apps/porting-overview.md)** . 

## <a name="development-checkpoints"></a>Pontos de verificação de desenvolvimento

Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unity para o mundo da realidade misturada. 

### <a name="1-getting-started"></a>1. Introdução

Há um pequeno conjunto de configurações do Unity que você precisará alterar manualmente para o desenvolvimento do Windows Mixed Reality e da VR. Elas são divididas em duas categorias: por projeto e por cena. No final desta seção, você terá as ferramentas e as configurações do projeto para começar a criar os próprios aplicativos!

|  Ponto de verificação  |  Resultado  |
| --- | --- |
| [Instale as ferramentas mais recentes](../install-the-tools.md) | Baixe e instale o pacote mais recente do Unity e configure seu projeto para realidade misturada |
| [Como configurar seu projeto para o WMR](windows-xr-plugin.md) | Saiba como criar aplicativos que renderizam conteúdo digital em dispositivos de vídeo holográficos e VR |

> [!IMPORTANT]
> Confira o [guia de configuração](choosing-unity-version.md) do projeto do Unity para obter mais informações sobre como configurar seus projetos.

### <a name="2-core-building-blocks"></a>2. Blocos principais de construção

Depois de iniciar um novo projeto de imersão, você precisará de alguns blocos de construção básicos para desenvolver aplicativos de imersão. Todos os principais blocos de construção para aplicativos de realidade misturada são expostos de maneira consistente com outras APIs do Unity. Talvez você não precise de todos eles de uma vez, mas recomendamos explorá-los logo no início. Depois de aprofundar-se nos principais blocos de construção listados abaixo, você terá uma caixa de ferramentas cheia de recursos que pode integrar ao seu projeto de VR.

|  Recurso  |  Funcionalidades  |
| --- | --- |
| [Câmera](../unity/camera-in-unity.md) | Otimize completamente a estabilidade do holograma e a qualidade visual nos seus aplicativos de Realidade Misturada |
| [Âncoras espaciais e bloqueio de mundo](spatial-anchors-in-unity.md) | Solucione problemas de estabilização e ajuste de câmera e integrar uma solução de sistema de coordenadas estável || [Controladores de movimentos](../unity/motion-controllers-in-unity.md) | Adicionar ações espaciais aos seus aplicativos de Realidade Misturada |
| [Gestos](../unity/gestures-in-unity.md) | Use gestos de mão como entrada em suas experiências de Realidade Misturada |
| [Som espacial](../unity/spatial-sound-in-unity.md) | Aprimore seus aplicativos com um áudio 3D imersivo |
| [Text](../unity/text-in-unity.md) | Obtenha texto nítido e de alta qualidade com tamanho gerenciável e renderização de qualidade |
| [Entrada de voz](../unity/voice-input-in-unity.md) | Capturar palavras-chave e frases faladas e ditado dos seus usuários|

### <a name="3-advanced-features"></a>3. Recursos avançados

Outros recursos importantes que desempenham uma função em aplicativos de imersão estão disponíveis por meio das APIs do Unity sem nenhum pacote ou configuração extra. Depois de se aprofundar nas funcionalidades mais avançadas que o Unity oferece, você conseguirá criar aplicativos de VR complexos e mais avançados.

|  Recurso  |  Funcionalidades  |
| --- | --- |
| [Controle de perda](tracking-loss-in-unity.md) | Lide com cenários em que seu dispositivo não consegue se localizar no espaço mundial dos aplicativos |
| [Entrada por teclado](keyboard-input-in-unity.md) | Obtenha informações de teclados do mundo real e de Realidade Misturada em seus aplicativos |

### <a name="4-deploying-to-a-device-or-emulator"></a>4. Como implantar em um dispositivo ou emulador

Depois que o projeto holográfico do Unity estiver pronto para teste, a próxima etapa será exportar e criar uma solução do Unity para Visual Studio. Com essa solução do VS em mãos, você pode executar seu aplicativo em dispositivos reais ou simulados. Ao final desta seção, você conseguirá implantar seu aplicativo em um dispositivo ou emulador que atenda às suas necessidades de desenvolvimento.

* [Headset imersivo do Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Simulador de headset imersivo do Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>E agora?

O trabalho dos desenvolvedores nunca termina, especialmente ao aprender uma nova ferramenta ou um SDK. As seções a seguir podem levar você para áreas que vão além do material de nível iniciante já concluído, juntamente com recursos úteis caso você não consiga avançar. Estes tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para explorá-los!

### <a name="porting"></a>Portabilidade

Se você tem aplicativos que gostaria de transferir, os artigos listados abaixo são sua próxima parada:

* [Portabilidade dos aplicativos de VR para o Windows Mixed Reality](../porting-apps/porting-guides.md?tabs=project)
* [Como atualizar aplicativos SteamVR para o Windows Mixed Reality](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a>Recursos adicionais

Antes de entrar no mundo da realidade misturada por conta própria, recomendamos dar uma olhada na documentação extra abaixo. 

* [Guia do entusiasta de VR](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Repositório de Ativos do Unity](https://assetstore.unity.com)

## <a name="see-also"></a>Confira também 

* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Melhores práticas para trabalhar com o Unity e o Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)