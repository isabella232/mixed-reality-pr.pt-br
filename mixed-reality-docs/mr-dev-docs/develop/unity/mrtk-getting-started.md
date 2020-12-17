---
title: Introdução ao MRTK versão 2
description: Para novos desenvolvedores interessados em usar o MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, teste, Kit de Ferramentas de Realidade Misturada, MRTK versão 2, MRTK, ferramentas, SDK, HoloLens, HoloLens 2, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, multiplataforma
ms.openlocfilehash: a8e85e27617d5c7d616d6db75941c5cf5808f3ce
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010117"
---
# <a name="getting-started-with-mrtk-for-unity"></a>Introdução ao MRTK para Unity
![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>O que é o MRTK (Kit de Ferramentas de Realidade Misturada)?
O MRTK é um kit de ferramentas de software livre que existe desde que o HoloLens foi lançado pela primeira vez. Ele não seria o que é hoje sem o trabalho árduo da nossa comunidade de desenvolvedores. Nos últimos três anos, ouvimos os comentários da comunidade de desenvolvedores e criamos o MRTK v2 para abordas as principais preocupações.  

O MRTK para Unity é um kit de desenvolvimento de software livre multiplataforma para aplicativos de realidade misturada. O kit de ferramentas conta com um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

Confira a [documentação do MRTK no GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) e comece a usar com o [guia de instalação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).


## <a name="new-with-mrtk-v2"></a>Novidades com o MRTK v2
Queremos enfatizar nosso compromisso com estas ferramentas de plataforma.  Na verdade, aproveitamos o MRTK versão 2 para desenvolver nossas experiências de caixa de entrada, como a OOBE (configuração inicial pelo usuário) e nosso aplicativo Dicas sobre Realidade Misturada. Você também pode esperar ver as novas funcionalidades do HoloLens 2 apresentadas pela primeira vez por meio do MRTK, pois acreditamos que é a melhor maneira de realizar o desenvolvimento em nossa plataforma. 

### <a name="modular"></a>Modular
O MRTK foi criado de maneira modular, de modo que não seja necessário inserir todas as partes do kit de ferramentas no projeto.  Na verdade, há alguns benefícios nessa abordagem.  Ela reduz o tamanho do projeto e facilita o gerenciamento dele.  Além disso, como o kit foi criado com objetos programáveis e é orientado por interface, também é possível substituir os componentes incluídos pelos seus próprios, a fim de dar suporte a outros serviços, sistemas e plataformas.

### <a name="cross-platform"></a>Plataforma cruzada
Falando em outras plataformas, ele tem suporte multiplataforma.  Embora isso não signifique que todas as plataformas são compatíveis, garantimos que nenhum código do kit de ferramentas será desfeito quando você mudar o destino de build para outras plataformas.  A robustez e a extensibilidade do design modular compatibilizam seus aplicativos com diversas plataformas, como ARCore, ARKit e OpenVR.

### <a name="performant"></a>Alto desempenho
Trabalhando com plataformas móveis, nós o construímos com o desempenho em mente.  Isso é muito importante, e queremos garantir que as ferramentas não trabalharão contra você.

## <a name="see-also"></a>Veja também
* [Instalar as ferramentas](../install-the-tools.md)
* [MRTK – Guia de instalação (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK – Página inicial da documentação (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Portabilidade do HoloToolkit/MRTK para o MRTK versão 2 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
