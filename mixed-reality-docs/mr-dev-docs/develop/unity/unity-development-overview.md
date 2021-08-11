---
title: Desenvolvimento do Unity para HoloLens
description: Comece a criar aplicativos de realidade misturada no Unity e HoloLens com nosso percurso de ponto de verificação selecionado.
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realidade misturada, desenvolvimento, introdução, novo projeto, portabilidade, funcionalidade, câmera, simulação, emulação, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, o que é realidade virtual, o que é a realidade aumentada, MRTK, kit de ferramentas de realidade misturada, mapeamento espacial, entrada de voz, câmera localizável, emulador, Azure, tutoriais
ms.openlocfilehash: f47e37f56f203590a16ec804c4a36a6ac601ec61cb2f3b7dfb69987d411eef15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202828"
---
# <a name="unity-development-for-hololens"></a>Desenvolvimento do Unity para HoloLens

![Logotipo do banner do Unity](../images/unity_logo_banner.png)

O Unity é uma das principais plataformas de desenvolvimento em tempo real no mercado, com código de runtime subjacente escrito em C++, e todo o script de desenvolvimento é feito em C#. Se você está buscando criar jogos, filmes e cinemática de animação ou, até mesmo, renderizar conceitos de arquitetura ou engenharia em um mundo virtual, o Unity tem a infraestrutura certa para ajudar você. Quando estiver pronto para começar, vá para os pontos de verificação de desenvolvimento abaixo.

> [!IMPORTANT]
> Se você já tem um projeto Unity que deseja mover para o HoloLens 2, confira nossos **[guias de portabilidade](../porting-apps/porting-overview.md)** . Temos guias para projetos que estão usando HTK, MRTK v1 ou SteamVR.

## <a name="development-checkpoints"></a>Pontos de verificação de desenvolvimento

Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unity para o mundo da realidade misturada. Se você ainda não explorou o [aplicativo de exemplo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), é recomendável baixá-lo e usá-lo para se familiarizar com os conceitos básicos da UX de Realidade Misturada.

## <a name="1-getting-started"></a>1. Introdução

A maneira mais fácil de desenvolver projetos no Unity é com o Kit de Ferramentas de Realidade Misturada. O MRTK ajudará você a configurar automaticamente um projeto para Realidade Misturada e fornecerá um conjunto de recursos para acelerar seu processo de desenvolvimento. Ao final desta seção, você terá uma compreensão básica do Kit de Ferramentas de Realidade Misturada, um ambiente de desenvolvimento configurado adequadamente para aplicativos de Realidade Misturada e um projeto do MRTK no Unity criado por você.

|  Ponto de verificação  |  Resultado  |
| --- | --- |
| [Apresentação do Kit de Ferramentas de Realidade Misturada](mrtk-getting-started.md) | Para iniciar seu percurso, familiarize-se com o Kit de Ferramentas de Realidade Misturada e o que ele tem a oferecer |
| [Baixe a Ferramenta de Recursos de Realidade Misturada](welcome-to-mr-feature-tool.md) | Uma nova ferramenta de desenvolvedor para descobrir, atualizar e adicionar pacotes de recursos de Realidade Misturada aos seus projetos do Unity |
| [Configurará seu ambiente de desenvolvedor](../install-the-tools.md) | Baixe e instale o pacote mais recente do Unity e configure seu projeto para realidade misturada |
| [Conclua a série de tutoriais do HoloLens 2](tutorials/mr-learning-base-01.md) | Aprofunde-se nos tutoriais do MRTK de nível principiante para hardware do HoloLens 2 |

> [!IMPORTANT]
> Caso você deseje criar um projeto do Unity sem importar o Kit de Ferramentas de Realidade Misturada, haverá um pequeno conjunto de configurações do Unity que precisará ser alterado manualmente para o Windows Mixed Reality. Dê uma olhada no [guia de configuração](choosing-unity-version.md) para obter mais informações.

> [!NOTE]
> Depois que você configurar o MRTK no seu projeto, objetos de jogo padrão do Unity, como a câmera, serão acesos imediatamente para uma experiência com escala de posição sentada. Você pode encontrar instruções sobre como alterar a escala de experiência de seu aplicativo na página de [sistemas de coordenadas](coordinate-systems-in-unity.md).

## <a name="2-core-building-blocks"></a>2. Blocos principais de construção

Todos os principais blocos de construção para aplicativos de realidade misturada são expostos de maneira consistente com outras APIs do Unity. Esses blocos de construção estão disponíveis como recursos autônomos e por meio do Kit de Ferramentas de Realidade Misturada. Talvez você não precise de todos eles de uma vez, mas recomendamos explorá-los logo no início. Depois de se aprofundar nos principais blocos de construção listados abaixo, você terá uma caixa de ferramentas cheia de recursos que pode integrar aos seus projetos de Realidade Misturada por conta própria ou por meio do MRTK.

|  Recurso  |  Funcionalidades  |
| --- | --- |
| [Câmera](../unity/camera-in-unity.md) | Otimize completamente a estabilidade do holograma e a qualidade visual nos seus aplicativos de Realidade Misturada |
| [Âncoras espaciais e bloqueio de mundo](spatial-anchors-in-unity.md) | Solucione problemas de estabilização e ajuste de câmera e integrar uma solução de sistema de coordenadas estável |
| [Experiências compartilhadas](shared-experiences-in-unity.md) | Exiba e interaja coletivamente com o mesmo holograma em um ponto fixo no espaço usando o compartilhamento de âncora espacial |
| [Foco](../unity/gaze-in-unity.md) | Permitir que os usuários direcionem hologramas olhando para eles |
| [Controladores de movimentos](../unity/motion-controllers-in-unity.md) | Adicionar ações espaciais aos seus aplicativos de Realidade Misturada |
| [Gestos](../unity/gestures-in-unity.md) | Use gestos de mão como entrada em suas experiências de Realidade Misturada |
| [Acompanhamento de mãos e olhos](../unity/hand-eye-in-unity.md) | Integre a entrada articulada de acompanhamento de mãos e olhos em sua experiência do usuário |
| [Mapeamento espacial](../unity/spatial-mapping-in-unity.md) | Mapeie seu espaço físico com uma sobreposição de malha virtual para marcar os limites do seu ambiente |
| [Som espacial](../unity/spatial-sound-in-unity.md) | Aprimore seus aplicativos com um áudio 3D imersivo |
| [Text](../unity/text-in-unity.md) | Obtenha texto nítido e de alta qualidade com tamanho gerenciável e renderização de qualidade |
| [Entrada de voz](../unity/voice-input-in-unity.md) | Capturar palavras-chave e frases faladas e ditado dos seus usuários|

## <a name="3-advanced-features"></a>3. Recursos avançados

Outros recursos importantes que desempenham uma função em aplicativos de realidade misturada estão disponíveis por meio das APIs do Unity sem nenhum pacote ou configuração extra. Esses recursos podem ser adicionados a projetos do Unity com ou sem o MRTK instalado. Depois de se aprofundar nos recursos mais avançados que o Unity oferece, você conseguirá criar aplicativos de realidade misturada complexos e mais avançados.

|  Recurso  |  Funcionalidades  |
| --- | --- |
| [Câmera de foto e vídeo](locatable-camera-in-unity.md) | Capture fotos e conteúdo de vídeo em seu aplicativo de realidade misturada |
| [Ponto de foco](focus-point-in-unity.md) | Dê ao HoloLens uma dica sobre a melhor forma de realizar a estabilização nos hologramas que estão sendo exibidos |
| [Controle de perda](tracking-loss-in-unity.md) | Lide com cenários em que seu dispositivo não consegue se localizar no espaço mundial dos aplicativos |
| [Entrada por teclado](keyboard-input-in-unity.md) | Obtenha informações de teclados do mundo real e de Realidade Misturada em seus aplicativos |

## <a name="4-deploying-to-a-device-or-emulator"></a>4. Como implantar em um dispositivo ou emulador

Depois que o projeto holográfico do Unity estiver pronto para teste, a próxima etapa será exportar e criar uma solução do Unity para Visual Studio. Com a solução do VS em mãos, você pode executar seu aplicativo em um dispositivo real ou simulado de três maneiras. Ao final desta seção, você conseguirá implantar seu aplicativo em qualquer dispositivo ou emulador que atenda às suas necessidades de desenvolvimento.

* [Headset imersivo do Windows Mixed Reality ou HoloLens](../platform-capabilities-and-apis/using-visual-studio.md)
* [Emulador do HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Simulador de headset imersivo do Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="5-adding-services"></a>5. Como adicionar serviços

Neste ponto em seu percurso de desenvolvimento, você pode buscar a adição de serviços ou uma ajuda com a implantação comercial. A integração dos [Serviços de Nuvem do Azure](../mixed-reality-cloud-services.md) pode melhorar muito o nível dos seus projetos. Compilamos alguns pontos de partida para você explorar e expandir seu conhecimento sobre Realidade Misturada.

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

Também temos uma [lista abrangente de documentação de suporte para serviços adicionais do Azure](../mixed-reality-cloud-services.md#standalone-unity-services) que você pode adicionar aos seus projetos do Unity por conta própria.

## <a name="6-low-code-alternatives"></a>6. Alternativas de código de baixo nível

[!INCLUDE[](../includes/unity-low-code.md)]

## <a name="whats-next"></a>E agora?

O trabalho dos desenvolvedores nunca termina, especialmente ao aprender uma nova ferramenta ou um SDK. As seções a seguir podem levar você para áreas que vão além do material de nível iniciante já concluído, juntamente com recursos úteis caso você não consiga avançar. Estes tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para explorá-los!

### <a name="porting"></a>Portabilidade

Se você tem aplicativos que gostaria de transferir, os artigos listados abaixo são sua próxima parada:

* [HoloToolkit/MRTK para MRTK v2](../porting-apps/porting-hl1-hl2.md)
* [Guia de portabilidade para aplicativos imersivos](../porting-apps/porting-guides.md)
* [Guia de portabilidade de entrada](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>Tutoriais

Para adicionar recursos específicos de realidade misturada aos seus aplicativos, acesse nossos vários tutoriais selecionados, que podem orientar você por todo o processo de ponta a ponta. Nosso conteúdo mais popular do HoloLens 2 e do HoloLens (1ª Geração) está listado abaixo, mas você pode encontrar a coleção inteira visitando a visão geral dos tutoriais.

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>Recursos adicionais

Antes de entrar no mundo da realidade misturada por conta própria, recomendamos dar uma olhada na documentação relacionada ao MRTK listada abaixo. Estes artigos são ótimos pontos de partida para entender como o MRTK funciona em mais detalhes e oferecem informações sobre como melhorar o desempenho de seu aplicativo.

|  Tópico  |  Descrição  |
| --- | --- |
| [Visão geral da arquitetura do MRTK](/windows/mixed-reality/mrtk-unity/architecture/overview) | Obtenha uma compreensão mais profunda de como o SDK do MRTK funciona em seus projetos |
| [Configurações e desempenho](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started) | Crie o perfil de seu aplicativo, atualize as configurações do Unity e obtenha o melhor desempenho de estabilização de holograma disponível |
| [Introdução ao MRTK + XR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk) | Faça a portabilidade para o pipeline XR alternativo fornecido pelo Unity |

### <a name="unity-resources"></a>Recursos do Unity

Além desta documentação disponível em docs.microsoft.com, o Unity instala a documentação da funcionalidade do Windows Mixed Reality junto com o Editor do Unity. A documentação fornecida pelo Unity inclui duas seções separadas.

|  Recurso  |  Descrição  |
| --- | --- |
| [Referência de script](https://docs.unity3d.com/ScriptReference/) | Esta seção da documentação contém detalhes da API de script que o Unity fornece e pode ser acessada online no Editor do Unity clicando em **Ajuda > Referência de Script** |
| [Manual](https://docs.unity3d.com/Manual/index.html) | Este manual foi desenvolvido para ajudar você a aprender como usar o Unity, de técnicas básicas a avançadas, e pode ser acessado online ou no Editor do Unity clicando em **Ajuda > Manual** |

> [!div class="nextstepaction"]
> [Explorar o MRTK](mrtk-getting-started.md)

## <a name="have-feedback"></a>Tem comentários?

Você pode nos encontrar nos [Fóruns do Unity](https://aka.ms/unityforums) marcando a **Microsoft** e uma combinação das seguintes marcas para nos ajudar a entender para qual plug-in você está enviando comentários:

* HoloLens 2 
* Windows Mixed Reality
* OpenXR
* XRSDK
* Legacy XR

## <a name="see-also"></a>Veja também

* [Kit de Ferramentas de Realidade Misturada v2](mrtk-getting-started.md)
* [Noções básicas do MR 100: introdução ao Unity](tutorials/holograms-100.md)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Como usar o namespace do Windows com aplicativos Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Melhores práticas para trabalhar com o Unity e o Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de reprodução do Unity](unity-play-mode.md)
* [Guias de portabilidade](../porting-apps/porting-guides.md)
