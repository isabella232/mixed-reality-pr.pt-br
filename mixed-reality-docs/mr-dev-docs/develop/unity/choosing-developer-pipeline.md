---
title: Escolhendo seu pipeline de desenvolvedor
description: Mantenha-se atualizado sobre as recomendações de pipeline de desenvolvimento do Unity mais recentes para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, Unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394550"
---
# <a name="choosing-your-developer-pipeline"></a>Escolhendo seu pipeline de desenvolvedor

![Faixa do logotipo do Unity](../images/unity_logo_banner.png)<br>

Embora, no momento, **recomendamos a instalação do Unity 2019,4 LTS e o uso da XR interna herdada** para o desenvolvimento de realidade misturada, você também pode criar aplicativos com outras configurações do Unity.

## <a name="mixed-reality-toolkit-recommended"></a>Kit de ferramentas de realidade mista (recomendado)

A configuração atual do Unity recomendada pela Microsoft para o HoloLens 2 é o kit de ferramentas de realidade misturada...

### <a name="install-the-mixed-reality-feature-tool"></a>Instalar a ferramenta de funcionalidade de realidade misturada

A [Ferramenta de Recursos de Realidade Misturada](welcome-to-mr-feature-tool.md) é uma nova maneira para os desenvolvedores descobrirem e adicionarem pacotes de recursos de Realidade Misturada em projetos do Unity. 

Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação. Depois de validar os pacotes desejados, a ferramenta Recurso de Realidade Misturada os baixará no projeto de sua escolha.

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a>Importando o kit de ferramentas de realidade misturada para o Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

O [MRTK](mrtk-getting-started.md) (Kit de Ferramentas de Realidade Misturada) é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada. 

* Instale o pacote do Kit de Ferramentas de Realidade Misturada seguindo as [instruções de instalação e uso](welcome-to-mr-feature-tool.md#system-requirements) e selecionando o pacote do **Mixed Reality Toolkit Foundation**.

Recomendamos a conclusão da seção de introdução dos nossos percursos de desenvolvimento do [HoloLens](unity-development-overview.md#1-getting-started) ou de [VR](unity-development-wmr-overview.md#1-getting-started). Se você já estiver seguindo o percurso de desenvolvimento do Unity para HoloLens, conclua o restante das etapas de instalação listadas abaixo e avance para os [tutoriais de Introdução do HoloLens 2](tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Observe que as instruções de instalação são destinadas à combinação estável mais recente das versões do MRTK e do Unity, que são as versões **MRTK 2.6.1** e **Unity 2019.4 LTS**.

> [!NOTE]
> Se você não quiser usar o MRTK para o Unity, precisará [criar o script de todas as interações e todos os comportamentos por conta própria](configure-unity-project.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Faixa do Unity](../images/MRTK-Unity-Banner.png)<br>**Kit de Ferramentas de Realidade Misturada – Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a>Manual 

TBD...