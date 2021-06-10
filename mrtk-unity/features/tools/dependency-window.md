---
title: Janela de dependência
description: Documentação sobre o uso da janela de dependência no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: fd17db3f365d8bd97b8cd9c43a6111e2b82a61fe
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647032"
---
# <a name="dependency-window"></a>Janela dependência

No Unity, geralmente é difícil entender quais ativos estão sendo usados e o que está fazendo referência a eles. A opção "Encontrar Referências na Cena" funciona muito bem quando você está preocupado apenas com a cena atual, mas e quanto a todo o projeto do Unity? É aí que **a Janela de Dependência** (Ativos/MRTK/Ferramentas/DependencyWindow) pode ser útil.

A Janela de Dependência exibe como os ativos se referenciam e dependem uns dos outros. As dependências são calculadas pela análise de guids nos arquivos YAML do projeto (observação, as dependências de script para script não são consideradas).

## <a name="usage"></a>Uso

Para abrir a janela, **selecione** Janela de Dependência de Utilitários do Kit de Ferramentas de Realidade  >    >    >   Misturada, que abrirá a janela e começará automaticamente a criar o grafo de dependência do projeto. Depois que o grafo de dependência for criado, você poderá selecionar ativos na guia do projeto para inspecionar suas dependências.

![Janela dependência](../images/dependency-window/MRTK_Dependency_Window.png)

A janela exibe uma lista de ativos dos que o ativo selecionado no momento depende e uma lista hierárquica de ativos que dependem dele. Se nada depender do ativo selecionado no momento, considere excluí-lo do projeto (observe que alguns ativos são carregados programaticamente por meio de APIs como Shader.Find() e podem não ser capturados pelo rastreador de dependência).

A janela também pode exibir apenas uma lista de todos os ativos que não são referenciados por outros ativos e podem ser considerados para exclusão:

![Janela dependência mostrando ativos não marcados](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> Se os ativos são modificados, adicionados ou removidos enquanto a janela de dependência está em uso, é aconselhável atualizar o grafo de dependência para os resultados mais "atualizados".
