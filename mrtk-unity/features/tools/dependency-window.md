---
title: Janela de dependência
description: Documentação sobre o uso da janela de dependência no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 09425fa46cb9888c2e81e0771419d4bce3dd2334f31b5b922049af12479876c8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214312"
---
# <a name="dependency-window"></a>Janela de dependência

No Unity, geralmente é difícil gleam quais ativos estão sendo usados e o que está fazendo referência a eles. A opção "localizar referências na cena" funciona muito bem quando você está preocupado apenas com a cena atual, mas e quanto a todo o seu projeto de Unity? É aí que a **janela de dependência** (assets/MRTK/Tools/DependencyWindow) pode ser útil.

A janela dependência exibe como a referência de ativos depende uns dos outros. As dependências são calculadas pela análise de GUIDs nos arquivos do Project YAML (Observe que as dependências de script para script não são consideradas).

## <a name="usage"></a>Uso

para abrir a janela, selecione Toolkit janela de dependência de utilitários de **realidade misturada**  >    >    >   que abrirá a janela e começará automaticamente a criar o grafo de dependência do projeto. Depois que o grafo de dependência for criado, você poderá selecionar ativos na guia projeto para inspecionar suas dependências.

![Janela de dependência](../images/dependency-window/MRTK_Dependency_Window.png)

A janela exibe uma lista de ativos dos quais o ativo atualmente selecionado depende e uma lista hierárquica de ativos que dependem dele. Se nada depender do ativo selecionado no momento, você poderá considerar excluí-lo do seu projeto (Observe que alguns ativos são carregados programaticamente por meio de APIs como shader. Find () e não podem ser capturados pelo rastreador de dependências).

A janela também pode exibir apenas uma lista de todos os ativos que não são referenciados por outros ativos e podem ser considerados para exclusão:

![Janela de dependência mostrando ativos não referenciados](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> Se os ativos forem modificados, adicionados ou removidos enquanto a janela de dependência estiver em uso, é aconselhável atualizar o grafo de dependência para os resultados mais "atualizados".
