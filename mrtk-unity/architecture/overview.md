---
title: Visão geral da arquitetura
description: Visão geral da arquitetura do MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, Arquitetura do MRTK,
ms.openlocfilehash: 7113ee68a3d8bae016236996725a879c95e31f410cb273184ddcc255ae7a0685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186592"
---
# <a name="architecture-overview"></a>Visão geral da arquitetura

Para obter uma introdução geral ao conteúdo do MRTK, as informações de arquitetura contidas neste documento ajudarão você a entender o seguinte:

- Grandes partes do MRTK e como eles se conectam
- Conceitos que o MRTK apresenta, que podem não existir no Unity do Vanilla
- Como alguns dos sistemas maiores (como Entrada) funcionam

Esta seção não se destina a ensinar como realizar tarefas, mas como essas tarefas são estruturadas e por quê.

## <a name="many-audiences-one-toolkit"></a>Muitos públicos, um kit de ferramentas

O MRTK não tem um único público uniforme. Ele foi escrito para dar suporte a casos de uso que vão desde a primeira vez em hackathons até indivíduos que estão criando experiências complexas e compartilhadas para a empresa. Alguns códigos e APIs podem ter sido escritos que são otimizados para um mais do que o outro (ou seja, algumas partes do MRTK parecem mais otimizadas para "configurar um clique"), mas é importante observar que algumas delas são mais por motivos históricos e de ressalto. À medida que o MRTK evolui, os recursos criados devem ser projetados para dimensionar para dar suporte à variedade de casos de uso.

O MRTK também tem requisitos para dimensionar normalmente entre experiências de VR e RA. Deve ser fácil criar aplicativos que normalmente se enquadram no comportamento quando implantados em um HoloLens 2 OU um HoloLens 1 e deve ser simples criar aplicativos destinados a OpenVR e WMR (e outras plataformas). Embora, às vezes, a equipe possa concentrar uma iteração específica em um sistema ou plataforma específico, a meta de longo prazo é criar uma ampla variedade de suporte para onde quer que as pessoas estejam criando experiências de realidade misturada.

## <a name="high-level-breakdown"></a>Divisão de alto nível

O MRTK é uma coleção de ferramentas para obter experiências de MR (realidade misturada) rapidamente e também uma estrutura de aplicativos com opiniões sobre seu próprio runtime, como ele deve ser estendido e como ele deve ser configurado.

Em um alto nível, o MRTK pode ser dividido das seguintes maneiras:

![Diagrama de visão geral da arquitetura](../features/images/architecture/MRTK_Architecture.png)

O MRTK também contém outro conjunto de utilitários de pegue-bag que têm pouca ou nenhuma dependência no restante do MRTK (para listar algumas: ferramentas de build, solucionadores, influenciadores de áudio, utilitários de suavização e renderadores de linha)

O restante da documentação de arquitetura será construído de baixo para cima, começando pela estrutura e pelo runtime, progredindo para sistemas mais interessantes e complexos, como entrada. Confira o tabela de conteúdo para continuar com a visão geral da arquitetura.
