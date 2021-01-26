---
title: Recomendações de desempenho para o Unreal
description: Saiba como obter o melhor desempenho dos seus aplicativos de realidade misturada com as configurações recomendadas do projeto do Unreal.
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583063"
---
# <a name="performance-recommendations-for-unreal"></a>Recomendações de desempenho para o Unreal

O Unreal Engine traz vários recursos que podem aumentar o desempenho de um aplicativo, tudo isso com base na discussão descrita em [Recomendações de desempenho para realidade misturada](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). Você é incentivado a detectar os gargalos do aplicativo, analisar e criar o perfil de aplicativos de realidade misturada e correções de desempenho gerais antes de continuar.

## <a name="recommended-unreal-project-settings"></a>Configurações recomendadas de projetos do Unreal

Você pode encontrar cada uma das configurações a seguir em **Editar > Configurações do Projeto**.

1. Como usar o renderizador de VR para dispositivos móveis:
    * Role até a seção **Projeto**, selecione **Hardware de Destino** e defina a plataforma de destino como **Celular/Tablet**

![Configuração de destino para dispositivos móveis](images/unreal/performance-recommendations-img-01.png)

2. Como usar o Renderizador de Encaminhamento: 
    * O Renderizador de Encaminhamento é muito melhor para a Realidade Misturada do que o pipeline de renderização Adiado padrão devido ao número de recursos que podem ser desabilitados individualmente. 
    * Você pode encontrar mais informações na [documentação do Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).

![Renderização de encaminhamento](images/unreal/performance-recommendations-img-04.png)

3. Uso da exibição múltipla em dispositivos móveis:
    * Role a página até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **VR** e habilite **Estéreo Instanciado** e **Exibição Múltipla em Dispositivos Móveis**. O HDR móvel deve estar desmarcado.

![Configurações de renderização de VR](images/unreal/performance-recommendations-img-03.png)

4. **[Somente em OpenXR]** Verifique se **Padrão** ou **D3D12** é o **RHI Padrão** selecionado:
    * A seleção de **D3D11** terá um impacto negativo no desempenho devido à plataforma que executa uma passagem de renderização adicional. O **D3D12** deve oferecer aprimoramentos de desempenho de renderização além de evitar a passagem de renderização adicional.

![RHI Padrão](images/unreal/performance-recommendations-img-09.png)

5. Como desabilitar a aplicação de neblina de vértice: 
    * a aplicação de neblina de vértice se aplica a cálculos de neblina em cada vértice em um polígono e interpola os resultados na face do polígono. Se o jogo não usar a neblina, recomendamos desabilitar a Neblina de Vértice para aumentar o desempenho do sombreamento.

![Opções de aplicação de neblina do vértice](images/unreal/performance-recommendations-img-05.png)

6. Desabilitando a remoção por oclusão:
    * Role até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **Remoção** e desmarque **Remoção por Oclusão**.
        + Se você precisa usar a remoção por oclusão em uma cena detalhada que está sendo renderizada, recomendamos habilitar o **Suporte a Remoção por Oclusão de Software** em **Mecanismo > Renderização**. O Unreal fará o trabalho na CPU e evitará consultas de oclusão de GPU, que têm um desempenho insatisfatório no HoloLens 2.
    * A remoção da oclusão na GPU em dispositivos móveis é lenta. Em geral, convém que a GPU se preocupe principalmente com a renderização. Se você achar que a oclusão ajudará o desempenho, tente habilitar a oclusão do software. 

> [!NOTE]
> A habilitação da oclusão do software pode piorar o desempenho se você já está vinculado à CPU por um grande número de chamadas de desenho.

![Desabilitar a remoção de oclusão](images/unreal/performance-recommendations-img-02.png)

7. Desabilitando a passagem personalizada do estêncil de profundidade:
    * A desabilitação do Estêncil de Profundidade Personalizada exige uma passagem extra, o que significa que ele é lento. A translucência também é lenta no Unreal. Você pode encontrar mais informações na [documentação do Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).

![Estêncil de profundidade](images/unreal/performance-recommendations-img-06.png)

8. Como reduzir os mapas de sombra em cascata: 
    * a redução do número de mapas de sombra vai aprimorar o desempenho. Em geral, você deve definir a propriedade como 1, a menos que haja uma perda de qualidade visível. 

![Mapas de sombra em cascata](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>Configurações opcionais

> [!NOTE]
> As configurações a seguir podem aprimorar o desempenho, mas à custa de desabilitar determinados recursos. Use essas configurações somente se tiver certeza de que não precisa dos recursos em questão.

1. Redução da Permuta do Sombreador Móvel
    * Se as luzes não forem movidas independentemente da câmera, você poderá definir o valor da propriedade com segurança como 0. O principal benefício é que ele permitirá que o Unreal remova várias permutações de sombreador, acelerando a compilação do sombreador.

![Redução da permuta do sombreador móvel](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>Confira também

* [Diretrizes de desempenho de dispositivos móveis do mecanismo do Unreal]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)