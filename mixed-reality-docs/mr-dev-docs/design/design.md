---
title: Comece a projetar e a criar protótipos
description: Se estiver pronto para criar algo, aprenda os conceitos básicos de que você precisa para começar a projetar e a criar protótipos.
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, descobrir, distribuir, indexar, página de aterrissagem, design, desenvolvimento, tutoriais, aplicativos de exemplo, conceitos básicos, estudos de caso, recursos, instruções sobre o HoloLens, projetos de Software livre, principais conceitos, interação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: c4d9f9b4c4be1c5012ac8dc84fb55e6c5fa9eaee
ms.sourcegitcommit: 85ba3af69ec2a9056f759bab7b66f79f09a016b2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2021
ms.locfileid: "111454758"
---
# <a name="start-designing-and-prototyping"></a>Comece a projetar e a criar protótipos

![resumo do design de realidade misturada](images/design-hero-image.png)

Os aplicativos de Realidade Misturada são diferentes de qualquer outra coisa no mundo hoje, e projetá-los é um trabalho complicado. Você precisa levar em conta não apenas as combinações dos mundos real e virtual que está criando, mas também as novas experiências de usuário que elas proporcionam. Já que a Realidade Misturada é um tema substancial, selecionamos pontos importantes relativos ao seu espectro de design e os colocamos abaixo como uma série de pontos de verificação. Eles estão em ordem sequencial, porém, se você já estiver familiarizado com algum deles, fique à vontade para pular para qualquer uma das seções a seguir. 

Dê uma olhada no nosso vídeo de visão geral de design para começar:

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a>Pontos de verificação de design

Use os pontos de verificação a seguir para levar seus conceitos e ideias de aplicativos para o mundo da realidade misturada.

### <a name="1-getting-started"></a>1. Introdução

Assim como em todos os percursos, sua aventura de criação de aplicativos de Realidade Misturada começa com as noções básicas. Recomendamos que se familiarize com os artigos [O que é Realidade Misturada?](../discover/mixed-reality.md) e [O que é um holograma?](../discover/hologram.md) a fim de se preparar para o design de imersão. Depois de concluir a leitura, você estará pronto para iniciar seu percurso do design de Realidade Misturada!

![Gif de introdução do aplicativo Designing Holograms](images/HandTracking2.gif)

|  Ponto de verificação  |  Resultado  |
| --- | --- |
| [Expanda seu processo de design](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | Dê uma olhada em primeira mão no processo de design da Realidade Misturada, coletado de designers dentro e fora da Microsoft |
| [Tipos de aplicativos de Realidade Misturada](types-of-mixed-reality-apps.md) | Decida onde sua experiência de aplicativo residirá no espectro da Realidade Misturada |
| [Aplicativo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | Aprenda os conceitos básicos do Design de UX de Realidade Misturada fazendo experimentos com dicas, comportamentos e recomendações para criar aplicativos HoloLens incríveis (disponíveis para download na Microsoft Store no HoloLens 2) |
| [Hub de exemplos do MRTK](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | Experimente interações espaciais comuns e blocos de construção de UX para Realidade Misturada (disponível para download na Microsoft Store no HoloLens 2) |
| **Opcional** [Download do Kit de ferramentas do Figma](figma-toolkit.md) | O Kit de ferramentas do Figma fornece ativos para você usar para esboço e layout da interface do usuário com base nos componentes disponíveis no MRTK |

### <a name="2-core-concepts"></a>2. Conceitos fundamentais

Independentemente de você fazer o desenvolvimento para VR ou RA, existem vários conceitos básicos que se aplicam ao design de experiências de imersão fluidas. Compreender o ponto de vista dos usuários, posicionar objetos e garantir que todos estejam confortáveis e seguros são suas principais prioridades nesta fase do percurso. Ao final desta seção, você terá uma base sólida para realizar o design de interação.

![Imagem de exemplo de conceitos básicos](images/fragments-750px.jpg)

|  Conceito  |  Resultado  |
| --- | --- |
| [Quadro holográfico](holographic-frame.md) | Entenda como os usuários veem seu conteúdo sobreposto ao mundo real quando usam headsets |
| [Sistemas de coordenadas](coordinate-systems.md) | Saiba como posicionar hologramas em lugares do mundo que tenham relevância, podendo ser a sala física do usuário ou um realm virtual criado por você |
| [Mapeamento espacial](spatial-mapping.md) | Ancore objetos no mundo do usuário e aproveite as superfícies físicas do mundo real |
| [Considerações sobre conforto](comfort.md) | Garanta o conforto e a segurança do usuário criando e apresentando o conteúdo de imersão de uma forma que imite o mundo natural |

### <a name="3-interaction-design"></a>3. Design de interação

Não importa o quanto uma experiência virtual seja bela e imersiva, ela será inútil sem interação. Esta seção descreverá modelos básicos de interação, controladores de movimentos e mãos, entrada de voz e coleta de dados por acompanhamento ocular dos seus usuários. Ao final desta seção, você estará pronto para lidar com o último grande tópico em seu percurso de design: a experiência do usuário.

![Fatores de design de interação](images/UX_Hero_Manipulation.jpg)

|  Conceito  |  Resultado  |
| --- | --- |
| [Modelos de interação](interaction-fundamentals.md) | Forneça a seus usuários interações instintivas por meio das mãos, dos olhos e da voz |
| [Controladores de movimentos e mãos](hands-and-tools.md) | Saiba como interagir com os hologramas de perto com as mãos de um usuário ou de longe com interações precisas |
| [Entrada de voz](voice-input.md) | Use comandos de voz como entrada em seus aplicativos de imersão para controlar ambientes e hologramas ao redor  |
| [Acompanhamento ocular](eye-tracking.md) | Adicione um novo nível de contexto e compreensão humana a uma experiência holográfica usando informações sobre o que os usuários estão olhando |

### <a name="4-user-experience-elements"></a>4. Elementos de experiência do usuário

Agora que você já domina as interações básicas, pode se concentrar nos pontos mais refinados dos elementos de experiência do usuário e em como adaptá-los para ambientes exclusivos da Realidade Misturada. Você abordará comportamentos comuns, design de ativos, dimensionamento de objetos e tipografia, além de tornar a experiência intuitiva para os usuários. Esta seção marca o fim do percurso oficial de design de Realidade Misturada, mas há outros recursos na seção [O que vem a seguir?](#whats-next) para você continuar trabalhando.

![Elementos de UX](images/UX_Hero_BoundingBox.jpg)

|  Conceito  |  Resultado  |
| --- | --- |
| [Controles e comportamentos comuns](app-patterns-landingpage.md) | Aprenda sobre interações espaciais e blocos de construção de interface do usuário usados ​​com frequência |
| [Cor, luz e materiais](color-light-and-materials.md) | Projete ativos de qualidade para Realidade Misturada que levem em conta a cor, a iluminação e os materiais |
| [Escala de objetos](scale.md) | Incorpore o máximo possível de dicas visuais do mundo real para ajudar os usuários a entender onde estão os objetos, qual o tamanho deles e do que são feitos |
| [Tipografia](typography.md) | Use um texto nítido e legível em um espaço tridimensional para fornecer aos usuários as informações importantes de que eles precisam |

## <a name="whats-next"></a>E agora?

O trabalho de um designer nunca termina, especialmente quando se aprende a criar experiências imersivas em um novo paradigma. As seções a seguir vão além do material de design de nível iniciante que você já concluiu e abordam o mundo do desenvolvimento da Realidade Misturada. Estes tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para explorá-los!

### <a name="choose-a-prototyping-option"></a>Escolha uma opção de protótipo  

:::row:::   
    :::column:::    
        [![Kit de ferramentas do MRTK Figma](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Kit de ferramentas do Figma](figma-toolkit.md)**<br>   
        O Kit de ferramentas do Figma fornece os ativos que podem ser usados para esboçar e definir a interface do usuário. Todos os controles da interface do usuário são baseados nos componentes disponíveis no MRTK.
    :::column-end:::        
    :::column:::    
       [![Conheça o Unity](../images/Final_unity_logo.png)](https://learn.unity.com/)<br>
        **[Conheça o Unity](https://learn.unity.com/)**<br>
        Saiba como criar experiências interativas com o Unity. Aprenda fazendo, do começo ao fim.
    :::column-end:::    
    :::column:::    
        [![MRTK (Kit de ferramentas de realidade misturada)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[MRTK (Kit de ferramentas de realidade misturada)](/windows/mixed-reality/mrtk-unity/)**<br>  
        Com os blocos de construção de interface do usuário e a interação espacial, você pode iniciar o desenvolvimento e o design de realidade misturada com o Unity.   
    :::column-end:::
    :::column:::    
        [![Maquete da Microsoft](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Maquete da Microsoft](https://www.maquette.ms/)**<br>  
        Design para VR. A Maquete da Microsoft torna a criação de protótipos especiais fácil, rápida e imersiva. 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a>Outros recursos

:::row:::
    :::column:::
       [![Noções básicas](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[Noções básicas](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        Entenda melhor o que define a realidade misturada e como ela está sendo usada.
    :::column-end:::
    :::column:::
        [![Participe de um evento](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[Participe de um evento](../whats-new/sf-academy-events.md)**<br>
        Consulte o hardware e obtenha um tutorial prático para criar seu primeiro aplicativo HoloLens 2.
    :::column-end:::
    :::column:::
        [![Instalar as ferramentas](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[Instalar as ferramentas](../develop/install-the-tools.md)**<br>
        Use a lista de verificação de instalação para obter as ferramentas necessárias para criar aplicativos para HoloLens e realidade misturada.
    :::column-end:::
    :::column:::
        [![Comece a desenvolver](images/74-18.png)](../develop/development.md)<br>
        **[Comece a desenvolver](../develop/development.md)**<br>
        Escolha um caminho de desenvolvimento com base no seu nível de habilidade, estilo de trabalho ou interesse na plataforma.
    :::column-end:::
:::row-end:::

<br>

<br>
