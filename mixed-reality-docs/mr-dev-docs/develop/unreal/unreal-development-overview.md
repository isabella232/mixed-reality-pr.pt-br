---
title: Visão geral do desenvolvimento com o Unreal
description: Introdução ao desenvolvimento de realidade misturada para HoloLens e VR usando o Unreal Engine 4 com nosso percurso de ponto de verificação selecionado.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicação remota, realidade misturada, desenvolvimento, introdução, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, OpenXR
ms.openlocfilehash: 90dfb113008e6f8b1162c068ebfc967ed74fd6b4
ms.sourcegitcommit: 71c2a4884bd83599e35dd894771a5e43e951b574
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2021
ms.locfileid: "128184662"
---
# <a name="unreal-development-overview"></a>Visão geral do desenvolvimento com o Unreal

![Logotipo da faixa do Unreal](../images/unreal_logo_banner.png)

A introdução aos <a href="/windows/mixed-reality" target="_blank" title="Documentos do Mixed Reality"> aplicativos de realidade misturada</a> é uma grande tarefa. Novos conceitos, plataformas e hardware de ponta podem ser vistos como barreiras. No entanto, se você é um desenvolvedor do Unreal, você está com sorte. Há suporte completo para o Unreal Engine 4 em dispositivos <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Documentação do Windows Mixed Reality">Windows Mixed Reality</a> (VR) e <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="Documentação do HoloLens 2">HoloLens 2</a> (RA).

[!INCLUDE[](includes/tabs-unreal-features.md)]

Se você estiver começando agora o desenvolvimento no Unreal, não prossiga às cegas. Explore a <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">série de tutoriais do Unreal</a> e procure ativos no <a href="https://www.unrealengine.com/marketplace/store" target="_blank">marketplace</a> do Unreal. Encontre também suporte nos <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">fóruns</a> de realidade misturada. Esses recursos são os seus links para a comunidade de criadores e solucionadores de problemas no mercado atual de realidade misturada.

> [!IMPORTANT]
> Dê uma olhada no nosso **[guia de portabilidade](unreal-reverb-g2-controllers.md)** se você tiver um projeto existente do Unreal que deseja trazer para os headsets imersivos, como o Reverb G2.

## <a name="development-checkpoints"></a>Pontos de verificação de desenvolvimento

Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unreal para o mundo da realidade misturada. Se você ainda não explorou o [aplicativo de exemplo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), recomendamos baixá-lo para se familiarizar com os conceitos básicos da Experiência de Usuário da Realidade Misturada.

### <a name="1-getting-started"></a>1. Introdução

Primeiro, você precisará instalar as ferramentas para o desenvolvimento do HoloLens 2. Depois, acompanhe nossa série de tutoriais para ter uma compreensão básica do Kit de Ferramentas de Realidade Misturada, um ambiente de desenvolvimento configurado adequadamente para aplicativos de realidade misturada e um projeto funcional do MRTK no Unreal. A partir do Unreal 4.26, você também tem a opção de desenvolver um aplicativo OpenXR para o HoloLens 2.

|  Ponto de verificação  |  Resultado  |
| --- | --- |
| [Instale as ferramentas mais recentes](../install-the-tools.md) | Baixe e instale a última versão do Unreal Engine e configure seu projeto para realidade misturada |
| [Configurar o seu projeto](unreal-project-setup.md) | Obtenha a versão mais recente do Unreal Engine e do MRTK |
| [Como criar seu primeiro aplicativo Unreal do HoloLens](unreal-quickstart.md) | Comece seu percurso de desenvolvimento no Unreal e no HoloLens criando um aplicativo básico de Realidade Misturada |
| [Série de tutoriais do HoloLens 2](tutorials/unreal-uxt-ch1.md) | Prepare-se para o desenvolvimento de realidade misturada no Unreal, crie seu primeiro aplicativo com o MRTK e implante-o no HoloLens 2 |
| Introdução ao [OpenXR](../native/openxr.md) no Unreal | Instale e habilite o seguinte plug-in do Marketplace do Unreal Engine:<ul><li> [Microsoft OpenXR](https://www.unrealengine.com/marketplace/en-US/product/ef8930ca860148c498b46887da196239)</li></ul>Confira se o plug-in do Windows Mixed Reality da Microsoft está desabilitado.<br><br>A lista completa de recursos atualmente compatíveis com o OpenXR é mostrada [abaixo](#supported-features).|

### <a name="2-core-building-blocks"></a>2. Blocos principais de construção

Há vários recursos importantes da realidade misturada que não são abordados em nossa série de tutoriais. Esses blocos de construção estão disponíveis como recursos autônomos e por meio do Kit de Ferramentas de Realidade Misturada. Talvez você não precise de todos eles de uma vez, mas recomendamos explorar logo no início. Depois de aprofundar-se nos principais blocos de construção listados abaixo, você terá uma caixa de ferramentas cheia de recursos que pode integrar aos seus projetos de Realidade Misturada.

O [Kit de Ferramentas de Realidade Misturada para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) é um conjunto de plug-ins projetados para acelerar seu desenvolvimento no Unreal. Cada plug-in inclui componentes, exemplos e documentação para configurar experiências imersivas.

* As [Ferramentas de Experiência de Usuário para Unreal](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools) são o primeiro plug-in a ser lançado e atualmente só são compatíveis com o HoloLens 2. O plug-in inclui código C++, blueprints e ativos de exemplo de recursos comuns da Experiência de Usuário para simulação de entrada, interações das mãos, magnetismo de superfície, entre outros.

* As [Ferramentas de Gráficos para Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/) são um plug-in de jogo do UE com um código, blueprints e ativos de exemplo criados para ajudar a melhorar a fidelidade visual de aplicativos de Realidade Misturada ao mesmo tempo que cumprem os orçamentos de desempenho.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> Você pode se aprofundar nas **[Ferramentas de UX para o repositório do GitHub no Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)** para obter mais detalhes.

### <a name="3-advanced-features"></a>3. Recursos avançados

Outros recursos importantes que desempenham uma função em aplicativos de realidade misturada estão disponíveis sem nenhum pacote ou configuração extra. Esses recursos podem ser adicionados a projetos do Unreal com ou sem o MRTK instalado. Após aprofundar-se nessas funcionalidades mais avançadas, você poderá criar aplicativos de Realidade Misturada mais complexos.

|  Recurso  |  Funcionalidades  |
| --- | --- |
| [Câmera do HoloLens](unreal-hololens-camera.md) | Capturar o conteúdo visual do mundo real e de Realidade Misturada do seu aplicativo em execução em um dispositivo HoloLens |
| [Códigos QR](unreal-qr-codes.md) | Renderizar códigos QR como hologramas usando um sistema de coordenadas na posição do mundo real de cada código |
| [WinRT](unreal-winrt.md) | Criar um binário separado com código WinRT que pode ser consumido pelo sistema de build do Unreal |

### <a name="4-streaming-and-deploying-to-a-device"></a>4. Streaming e implantação em um dispositivo

Caso deseje testar seu aplicativo em um dispositivo HoloLens enquanto ele ainda está em desenvolvimento, [transmita-o diretamente do seu PC](unreal-streaming.md) usando o editor do Unreal ou um executável empacotado do Windows.

Se esta é a primeira vez que você implanta um aplicativo do Unreal no HoloLens 2, [baixe os arquivos de suporte](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) do Epic Launcher. Depois de instalar esses arquivos, você estará pronto para implantar o [editor do Unreal](unreal-deploying.md) ou o [Portal de Dispositivos](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

### <a name="5-adding-services"></a>5. Como adicionar serviços

Neste ponto no seu percurso de desenvolvimento, você pode estar buscando adicionar serviços ou uma ajuda com a implantação comercial. A integração dos [Serviços de Nuvem do Azure](../mixed-reality-cloud-services.md) pode melhorar muito o nível dos seus projetos. Compilamos alguns pontos de partida para você explorar e expandir seu conhecimento sobre Realidade Misturada.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

### <a name="6-low-code-alternatives"></a>6. Alternativas de código de baixo nível

[!INCLUDE[](../includes/unreal-low-code.md)]

## <a name="whats-next"></a>E agora?

O trabalho de um desenvolvedor nunca termina, especialmente ao aprender uma nova ferramenta ou um SDK. As seções a seguir podem levar você para áreas que vão além do material de nível de iniciante que você já concluiu, juntamente com recursos úteis se você não conseguir avançar. Observe que esses tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para mergulhar neles e explorá-los!

### <a name="debugging"></a>Depuração

Se você pretende depurar o aplicativo enquanto ele está em execução no dispositivo com o Visual Studio, siga estas [instruções](/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Desempenho

O desenvolvimento para realidade misturada vem com pontos de verificação de desempenho que dependem da plataforma. Um aplicativo do HoloLens 2 deve ser executado em 60 quadros por segundo para que os hologramas pareçam estáveis e dinâmicos. A boa notícia é que temos [recomendações de desempenho](performance-recommendations-for-unreal.md) para atualizar o desempenho nos seus aplicativos do Unreal.

## <a name="supported-features"></a>Recursos compatíveis

| Recurso do HoloLens 2 | Versão do Unreal Engine compatível mais antiga | Compatível no OpenXR (4.26+) |
| ----------- | ----------- | ----------- |
| Compatibilidade com ARM64 | 4.23 | ✔️ |
| Streaming de um PC | 4.23 | ✔️ |
| mapeamento espacial | 4.23 | ✔️ |
| Controle de mão e junta | 4.23 | ✔️ |
| Acompanhamento ocular | 4.23 | ✔️ |
| Entrada de voz | 4.23 | ✔️ |
| Âncoras espaciais | 4.23 | ✔️ |
| Acesso à câmera | 4.23 | ✔️ |
| Códigos QR | 4.23 | ✔️ |
| Áudio espacial | 4.23 | ✔️ |
| LSR Planar por streaming | 4.24 |
| [Aplicativos de exemplo](../features-and-samples.md) | 4.24 | ✔️ |
| Exibição múltipla em dispositivos móveis: Desempenho alcança 60 quadros/s | 4.25 | ✔️ |
| Streaming de um aplicativo da área de trabalho empacotado | 4.25.1 | ✔️ |
| Âncoras Espaciais do Azure para HoloLens 2 | 4.25 | ✔️ |
| Suporte a Ferramentas de Experiência de Usuário de Realidade Misturada | 4.25 | ✔️ |
| Documentos do desenvolvedor e tutoriais | 4.25 | ✔️ |
| Teclado do sistema | 4.26 | ✔️ |
| Plug-in do HoloLens Media Player | 4.26 | ✔️ |
| Âncoras Espaciais do Azure para iOS e Android | 4.26 |
| Plug-in do Microsoft OpenXR com extensões do OpenXR específicas do fornecedor da Microsoft | 4.26 | ✔️ |
| Streaming do Azure para o HoloLens 2 | 4.26 | ✔️ |
| Conformidade do Kit de Certificação de Aplicativos Windows para aplicativos empacotados | 4.26 | ✔️ |
| Suporte ao controlador do HP Reverb G2 | 4.26 | ✔️ |

> [!div class="nextstepaction"]
> [Instalar as ferramentas](../install-the-tools.md)

## <a name="see-also"></a>Veja também
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Documentos do Unreal para streaming, implantação em emulador e em dispositivo</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Diretrizes de desempenho do Unreal para dispositivos móveis</a>