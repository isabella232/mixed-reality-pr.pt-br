---
title: Tutoriais de introdução – 3. Como configurar os perfis do MRTK
description: Este curso mostra como configurar os perfis do MRTK (Kit de Ferramentas de Realidade Misturada).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, reconhecimento espacial
ms.localizationpriority: high
ms.openlocfilehash: 3b44ba6c4eac3cf7b42d15c8fb19d42676b10a4a
ms.sourcegitcommit: 5017f309827c1d20df4ce656d105a1a49ba7942c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106011135"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Como configurar os perfis do MRTK

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a personalizar e configurar os perfis do MRTK.

Os <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles.md" target="_blank">perfis do MRTK</a> são uma árvore de perfis aninhados que compõem as informações de configuração sobre como os sistemas e os recursos do MRTK devem ser inicializados. O perfil de nível superior, o Perfil de Configuração, contém perfis aninhados para cada um dos principais sistemas básicos. Cada perfil aninhado foi projetado para configurar o comportamento do respectivo sistema correspondente.

Este exemplo específico mostrará como ocultar a malha de reconhecimento espacial alterando as configurações do Observador de Malha Espacial. No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis do MRTK.

Como você experimentou quando implantou seu projeto no HoloLens 2 durante o [tutorial anterior](mr-learning-base-02.md#congratulations), a malha de <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Reconhecimento Espacial</a> é uma coleção de malhas que representa a geometria do ambiente. É uma visualização útil de ser vista inicialmente, mas em geral, é desativada para evitar a distração visual e o impacto adicional de desempenho da presença dela.

## <a name="objectives"></a>Objetivos

* Saiba como personalizar e configurar perfis do MRTK
* Ocultar a malha de reconhecimento espacial

## <a name="changing-the-spatial-awareness-display-option"></a>Como alterar a opção de exibição de reconhecimento espacial

As principais etapas que você seguirá para ocultar a malha de reconhecimento espacial são:

1. Clonar o perfil de configuração padrão
2. Habilitar o Sistema de Reconhecimento Espacial
3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão
4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão
5. Altere a visibilidade da malha de reconhecimento espacial

> [!NOTE]
> Por padrão, os perfis do MRTK não são editáveis. Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados. Há várias camadas aninhadas de perfis. Portanto, é comum clonar e editar vários perfis ao definir uma ou mais configurações.

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a clonar, personalizar e definir uma configurações e perfis do MRTK.

> [!div class="nextstepaction"]
> [Próximo tutorial: 4. Como posicionar objetos na cena](mr-learning-base-04.md)