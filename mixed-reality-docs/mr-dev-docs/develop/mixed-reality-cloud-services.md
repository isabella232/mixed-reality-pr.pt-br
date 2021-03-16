---
layout: LandingPage
title: Visão geral dos serviços de nuvem da realidade misturada do Azure
description: Conheça todos os serviços de nuvem de realidade misturada do Azure que você pode integrar aos seus aplicativos Unity ou Unreal.
author: hferrone
ms.author: v-haferr
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Realidade Misturada, desenvolver, desenvolvimento, HoloLens, serviços de nuvem, Azure, remote rendering, âncoras espaciais, serviços cognitivos, cognição, unity, machine learning, tradução de fala, pesquisa visual computacional, Microsoft Graph
ms.openlocfilehash: 0c123c2bca412589086799c41b183eb6f9364d0c
ms.sourcegitcommit: ece91dbba40981720fe7e1a7c3b93e8b75ff71ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102547225"
---
# <a name="azure-mixed-reality-cloud-services-overview"></a>Visão geral dos serviços de nuvem da realidade misturada do Azure

![ Imagem das Âncoras Espaciais do Azure](../design/images/AzureSpatialAnchors.jpg)

Revele aquilo em que cada humano é especialista – o mundo físico tridimensional ao nosso redor – com os serviços de realidade misturada do Azure. Ajude as pessoas a criar, aprender e colaborar com mais eficiência capturando e identificando informações digitais dentro do contexto do trabalho e do mundo delas. Traga 3D para dispositivos móveis, headsets e outros dispositivos que não estão conectados. Usando o Azure, ajude a garantir que suas informações mais confidenciais fiquem protegidas.

## <a name="mixed-reality-services"></a>Serviços de realidade misturada

Serviços de nuvem de Realidade Misturada como **Azure Remote Rendering** e **Âncoras Espaciais do Azure** ajudam os desenvolvedores a criar experiências de imersão atraentes em uma variedade de plataformas. Esses serviços permitem que você integre o reconhecimento espacial aos seus projetos quando você cria aplicativos para treinamento 3D, manutenção preditiva do equipamento e revisão de design, tudo no contexto dos ambientes dos seus usuários.

### <a name="azure-remote-rendering"></a>Azure Remote Rendering

O [ARR](https://docs.microsoft.com/azure/remote-rendering/), ou Azure Remote Rendering, é um serviço que permite renderizar modelos 3D altamente complexos quase em tempo real e transmiti-los para um dispositivo. No momento, o ARR está em versão prévia pública e pode ser adicionado aos seus projetos C++ do Unity ou do Native direcionados ao HoloLens 2 ou ao computador desktop Windows.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-Azure-Mixed-Reality-Services-Azure-Remote-Rendering/player]

O ARR é um componente essencial de qualquer aplicativo de Realidade Misturada executado em um dispositivo não conectado, pois tem menos capacidade computacional de renderização. Use a seguinte comparação de modelo de mecanismo lado a lado como exemplo: o modelo de alta fidelidade à esquerda tem mais de 18 milhões triângulos, enquanto o modelo reduzido à direita tem apenas cerca de 200 mil. Em cenários em que todos os detalhes são importantes – gerenciamento de plantas industriais, análise de design para ativos como motores de caminhão, planejamento pré-operatório para cirurgia e muito mais –, a visualização 3D dá vida a esses detalhes. É isso que ajuda os designers, engenheiros, médicos e estudantes a entender melhor as informações complexas e fazer a chamada correta. Mas essa simplificação pode resultar em uma perda de detalhes importantes que é necessária nas principais decisões de negócios e de design.

![Exemplo do Azure Remote Rendering no aplicativo de demonstração do Unity](images/arr-engine.png)

O ARR soluciona esse problema movendo a carga de trabalho de renderização para GPUs de alta gama na nuvem. Um mecanismo de elementos gráficos hospedado na nuvem toma o controle e renderiza a imagem, codifica-a como um fluxo de vídeo e transmite o modelo diretamente para o dispositivo de destino. 

* Para modelos complexos que são muito grandes para uma GPU de alta gama manipular, o ARR distribui a carga de trabalho para várias GPUs e mescla o resultado em uma única imagem, tornando o processo totalmente transparente para o usuário. 

Como um bônus adicional, o ARR não restringe o tipo de interface do usuário que você pode usar em seu aplicativo. No final de um quadro, seu conteúdo renderizado localmente é automaticamente combinado com a imagem remota, como mostrado na imagem abaixo:

![Exemplo do Azure Remote Rendering no aplicativo de demonstração do Unity](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Âncoras Espaciais do Azure

As [Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/) são um serviço multiplataforma que permite criar aplicativos de realidade misturada com reconhecimento espacial. Com as Âncoras Espaciais do Azure, você pode mapear, persistir e compartilhar conteúdo holográfico entre vários dispositivos em escala do mundo real. 

As Âncoras Espaciais do Azure são uma solução exclusivamente personalizada para casos de uso comuns na Realidade Misturada, incluindo:
* **Orientação**: duas ou mais âncoras espaciais podem ser conectadas para criar uma lista de tarefas ou pontos de interesse com os quais um usuário precisa interagir.
* **Experiências de vários usuários**: os usuários podem passar movimentos para frente e para trás interagindo com objetos no mesmo espaço virtual.
* **Persistência de conteúdo virtual no mundo real**: os usuários podem inserir objetos virtuais no mundo real que são visíveis por outros dispositivos com suporte.

![Exemplo de Âncoras Espaciais do Azure](images/persistence.gif)

O serviço pode ser desenvolvido em um host de ambientes e implantado em um grande grupo de dispositivos e plataformas. Isso lhes dá isenção especial para a própria lista de plataformas disponíveis:
* Unity para HoloLens
* Unity para iOS
* Unity para Android
* iOS nativo
* Android nativo
* C++/WinRT e DirectX para HoloLens
* Xamarin para iOS
* Xamarin para Android

## <a name="cognitive-services"></a>Serviços Cognitivos

:::row:::
    :::column:::
       [![Speech](../whats-new/images/speech.jpg)](/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Fala](/azure/cognitive-services/speech-service/)
        Descubra como a Fala habilita a integração de funcionalidades de processamento de fala em qualquer aplicativo ou serviço. Converta o idioma falado em texto ou produza uma fala que soa natural com base em texto usando fontes de voz padrão (ou personalizáveis). Experimente qualquer serviço gratuitamente – e crie rapidamente aplicativos e serviços habilitados para fala com as funcionalidades a seguir.
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![Visão](../whats-new/images/vision.jpg)](/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Visão](/azure/cognitive-services/computer-vision/)
        Reconheça, identifique, legende, indexe e modere imagens, vídeos e conteúdo de tinta digital. Saiba como a Visão possibilita que aplicativos e serviços identifiquem e analisem com precisão o conteúdo em imagens, vídeos e tinta digital.
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>Serviços Unity autônomos

Os serviços autônomos listados abaixo não se aplicam à Realidade Misturada, mas podem ser úteis em uma ampla variedade de contextos de desenvolvimento. Se você estiver fazendo desenvolvimentos no Unity, cada um desses serviços poderá ser integrado a seus projetos novos ou existentes.

### <a name="device-support"></a>Suporte a dispositivos
<table>
    <tr>
        <td><strong>Serviço de Nuvem do Azure</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 1ª geração</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">Tradução de idioma</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">Pesquisa Visual Computacional</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">Visão Personalizada</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">Notificações entre dispositivos</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">Reconhecimento facial</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">Funções e armazenamento</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">Streaming de vídeo</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">Aprendizado de máquina</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">Funções e armazenamento</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">Application Insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">Detecção de objetos</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">Integração de bots</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>Confira também

* Tutoriais sobre as Âncoras Espaciais do Azure para HoloLens 2 – [1 de 3: Introdução às Âncoras Espaciais do Azure](./unity/tutorials/mr-learning-asa-02.md)
* Tutoriais sobre os Serviços de Fala do Azure para HoloLens 2 – [1 de 4 Como integrar e usar a transcrição e o reconhecimento de fala](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)
