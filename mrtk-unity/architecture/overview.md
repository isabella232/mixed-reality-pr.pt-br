---
title: Visão geral da arquitetura
description: Visão geral da arquitetura do MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, arquitetura MRTK,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281914"
---
# <a name="architecture-overview"></a>Visão geral da arquitetura

Para obter uma introdução geral ao conteúdo de MRTK, as informações de arquitetura contidas neste documento ajudarão você a entender o seguinte:

- Grandes pedaços de MRTK e como eles se conectam
- Conceitos que o MRTK introduz, que pode não existir no Unity da baunilha
- Como alguns dos sistemas maiores (como entrada) funcionam

Esta seção não se destina a ensinar como realizar tarefas, mas como essas tarefas são estruturadas e por quê.

## <a name="many-audiences-one-toolkit"></a>Muitos públicos, um kit de ferramentas

O MRTK não tem um público único e uniforme. Ele foi escrito para dar suporte a casos de uso que vão desde o primeiro hackathons, até indivíduos que criam experiências complexas e compartilhadas para empresas. Alguns códigos e APIs podem ter sido escritos e otimizados para um mais do que o outro (ou seja, algumas partes do MRTK parecem mais otimizadas para "configurar um clique"), mas é importante observar que alguns deles são mais para motivos históricos e de terceirização. À medida que o MRTK evolui, os recursos que são criados devem ser projetados para serem dimensionados para dar suporte ao intervalo de casos de uso.

O MRTK também tem requisitos para dimensionar normalmente em experiências de VR e AR. deve ser fácil criar aplicativos que são normalmente fallback no comportamento quando implantados em um HoloLens 2 ou em um HoloLens 1, e deve ser simples criar aplicativos direcionados a OpenVR e WMR (e outras plataformas). Embora às vezes a equipe possa focar uma iteração específica em um sistema ou plataforma específica, a meta a longo prazo é criar uma ampla gama de suporte para sempre que as pessoas criarem experiências de realidade misturada.

## <a name="high-level-breakdown"></a>Divisão de alto nível

O MRTK é uma coleção de ferramentas para obter experiências de realidade misturada (MR) com a base rapidamente, e também uma estrutura de aplicativo com opiniões sobre seu próprio tempo de execução, como ela deve ser estendida e como deve ser configurada.

Em um alto nível, o MRTK pode ser dividido das seguintes maneiras:

![Diagrama de visão geral da arquitetura](../features/images/architecture/MRTK_Architecture.png)

O MRTK também contém outro conjunto de utilitários de captura que têm pouca ou nenhuma dependência no restante do MRTK (para listar alguns: ferramentas de compilação, resolvedores, influenciadores de áudio, utilitários de suavização e renderizadores de linha)

O restante da documentação da arquitetura será criado de forma inferior, começando com a estrutura e o tempo de execução, progredindo para sistemas mais interessantes e complexos, como entrada. Consulte o Sumário para continuar com a visão geral da arquitetura.
