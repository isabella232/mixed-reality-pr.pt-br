---
title: Visão geral do desenvolvimento com o Unreal
description: Visão geral do desenvolvimento de realidade misturada usando o Unreal Engine 4
author: hferrone
ms.author: v-hferrone
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicação remota, realidade misturada, desenvolvimento, introdução, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: b810ad7500f8bb2a70ef18ad29fb32df8801a2de
ms.sourcegitcommit: 2759aba06e643d70004023b105ed26b33ce3dbfa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810442"
---
# <a name="unreal-development-overview"></a>Visão geral do desenvolvimento com o Unreal

![Logotipo da faixa do Unreal](../images/unreal_logo_banner.png)

A introdução aos <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Documentos do Mixed Reality"> aplicativos de realidade misturada</a> é uma grande tarefa. Novos conceitos, plataformas e hardware de ponta podem ser vistos como barreiras. No entanto, se você é um desenvolvedor do Unreal, você está com sorte. O suporte aos <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Documentos do Windows Mixed Reality">Windows Mixed Reality</a> (VR) e aos <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="Documentos do HoloLens 2">HoloLens 2</a> (RA) agora está incluído em <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Notas sobre a versão do Unreal Engine 4.25">versão</a> mais recente. Essa atualização inclui:
* Compatibilidade com o plug-in de Ferramentas de UX de Realidade Misturada
* Compatibilidade com OpenXR
* Comunicação remota com o aplicativo por meio de um aplicativo da área de trabalho
* Melhor desempenho
* Captura de realidade mista
* Suporte inicial para Âncoras Espaciais do Azure

Se você não estiver familiarizado com o desenvolvimento no Unreal, não prossiga às cegas. Explore a <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">série de tutoriais</a> do Unreal para se familiarizar e procure ativos e suporte no <a href="https://www.unrealengine.com/marketplace/store" target="_blank">marketplace</a> do Unreal e nos <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">fóruns</a> sobre realidade misturada. Esses recursos são seus links para a comunidade de criadores e solucionadores de problemas no mercado atual de realidade misturada.

> [!IMPORTANT]
> Dê uma olhada no nosso **[guia de portabilidade](unreal-reverb-g2-controllers.md)** se você tiver um projeto existente do Unreal que deseja trazer para os headsets imersivos, como o Reverb G2.

## <a name="development-checkpoints"></a>Pontos de verificação de desenvolvimento

Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unreal para o mundo da realidade misturada. Se você ainda não explorou o [aplicativo de exemplo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), é recomendável baixá-lo e usá-lo para se familiarizar com os conceitos básicos da UX de Realidade Misturada.

### <a name="1-getting-started"></a>1. Introdução

O [Kit de Ferramentas de Realidade Misturada para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) é um conjunto de componentes projetados para acelerar seu desenvolvimento no Unreal. Cada componente inclui plug-ins, exemplos e documentação para configurar experiências imersivas.

* As [Ferramentas de UX para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) são o primeiro componente a ser lançado e atualmente só são compatíveis com o HoloLens 2. O plug-in do componente inclui código, blueprints e ativos de exemplo de recursos de UX comuns para simulação de entrada, atores de interação à mão, componentes de botões que podem ser pressionados, componentes de manipulador e componentes de comportamento de acompanhamento.

Ao final desta seção, você terá uma compreensão básica do Kit de Ferramentas de Realidade Misturada, um ambiente de desenvolvimento configurado corretamente para aplicativos de Realidade Misturada e um projeto do MRTK em funcionamento no Unreal.

|  Ponto de verificação  |  Resultado  |
| --- | --- |
| [Instale as ferramentas mais recentes](../install-the-tools.md) | Baixe e instale a última versão do Unreal Engine e configure seu projeto para realidade misturada |
| [Série de tutoriais do HoloLens 2](tutorials/unreal-uxt-ch1.md) | Aprofunde-se nos tutoriais do MRTK de nível principiante para hardware do HoloLens 2 |

### <a name="2-core-building-blocks"></a>2. Blocos principais de construção

Há vários recursos importantes de desenvolvimento de realidade misturada que nossa série de tutoriais não abrange. Esses blocos de construção estão disponíveis como recursos autônomos e por meio do Kit de Ferramentas de Realidade Misturada. Talvez você não precise de todos eles de uma vez, mas recomendamos explorar logo no início. Depois de aprofundar-se nos principais blocos de construção listados abaixo, você terá uma caixa de ferramentas cheia de recursos que pode integrar aos seus projetos de Realidade Misturada.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> Você pode se aprofundar nas **[Ferramentas de UX para o repositório do GitHub no Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)** para obter mais detalhes.

### <a name="3-platform-capabilities-and-apis"></a>3. Funcionalidades de plataforma e APIs

Outros recursos importantes que desempenham uma função em aplicativos de realidade misturada estão disponíveis sem nenhum pacote ou configuração extra. Esses recursos podem ser adicionados a projetos do Unreal com ou sem o MRTK instalado. Após aprofundar-se nessas funcionalidades mais avançadas, você poderá criar aplicativos de Realidade Misturada mais complexos.

|  Recurso  |  Funcionalidades  |
| --- | --- |
| [Câmera do HoloLens](unreal-hololens-camera.md) | Capturar o conteúdo visual do mundo real e de Realidade Misturada do seu aplicativo em execução em um dispositivo HoloLens |
| [Códigos QR](unreal-qr-codes.md) | Renderizar códigos QR como hologramas usando um sistema de coordenadas na posição do mundo real de cada código |
| [WinRT](unreal-winrt.md) | Criar um binário separado com código WinRT que pode ser consumido pelo sistema de build do Unreal |

### <a name="4-deploying-to-a-device"></a>4. Como fazer a implantação em um dispositivo

Se esta é a primeira vez que você cria ou implanta um aplicativo do Unreal para o HoloLens, [baixe os arquivos de suporte](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) do Epic Launcher. Depois de instalar esses arquivos, você estará pronto para implantar o [editor do Unreal](unreal-deploying.md) ou o [Portal de Dispositivos](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

### <a name="5-adding-services"></a>5. Como adicionar serviços

Neste ponto em seu percurso de desenvolvimento, você pode buscar a adição de serviços ou uma ajuda com a implantação comercial. A integração dos [Serviços de Nuvem do Azure](../mixed-reality-cloud-services.md) e dos recursos do Dynamics 365 pode melhorar muito o nível dos seus projetos. Compilamos alguns pontos de partida para você explorar e expandir seu conhecimento de Realidade Misturada.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>E agora?

O trabalho dos desenvolvedores nunca termina, especialmente ao aprender uma nova ferramenta ou um SDK. As seções a seguir podem levar você para áreas que vão além do material de nível de iniciante que você já concluiu, juntamente com recursos úteis se você não conseguir avançar. Observe que esses tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para mergulhar neles e explorá-los!

### <a name="streaming--debugging"></a>Streaming e depuração

Se desejar testar seu aplicativo em um dispositivo HoloLens enquanto ainda estiver em desenvolvimento, você poderá [transmiti-lo diretamente do seu PC](unreal-streaming.md) usando o editor do Unreal ou um arquivo executável do Windows empacotado.

Se você pretende depurar o aplicativo com o Visual Studio, siga estas [instruções](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Desempenho

O desenvolvimento para realidade misturada vem com pontos de verificação de desempenho que dependem da plataforma. Um aplicativo do HoloLens 2 deve ser executado em 60 quadros por segundo para que os hologramas pareçam estáveis e dinâmicos. Uma vantagem é que temos [recomendações de desempenho](performance-recommendations-for-unreal.md) para alcançar isso nos aplicativos do Unreal.

## <a name="supported-features"></a>Recursos compatíveis

| Recurso do HoloLens 2 | Versão do Unreal Engine compatível mais antiga |
| ----------- | ----------- |
| Compatibilidade com ARM64 | 4.23 |
| Streaming de um PC | 4.23 |
| mapeamento espacial | 4.23 |
| Controle de mão e junta | 4.23 |
| Acompanhamento ocular | 4.23 |
| Entrada de voz | 4.23 |
| Âncoras espaciais | 4.23 |
| Acesso à câmera | 4.23 |
| Códigos QR | 4.23 |
| Áudio espacial | 4.23 |
| Compatibilidade com tela Espectador para streaming | 4.24 |
| LSR Planar por streaming | 4.24 |
| Aplicativos de exemplo ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) e [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Exibição múltipla em dispositivos móveis: Desempenho alcança 60 quadros/s | 4.25 |
| Renderização de 3ª câmera | 4.25 |
| Streaming de um aplicativo da área de trabalho empacotado | 4.25.1 |
| Âncoras Espaciais do Azure para o HoloLens 2 (beta) | 4.25 |
| Compatibilidade com OpenXR (beta) | 4.25 |
| Compatibilidade com Ferramentas de UX (0.8) | 4.25 |
| Documentos do desenvolvedor e tutoriais | 4.25 |

> [!div class="nextstepaction"]
> [Instalar as ferramentas](../install-the-tools.md)

## <a name="see-also"></a>Veja também
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Documentos do Unreal para streaming, implantação em emulador e em dispositivo</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Diretrizes de desempenho do Unreal para dispositivos móveis</a>
