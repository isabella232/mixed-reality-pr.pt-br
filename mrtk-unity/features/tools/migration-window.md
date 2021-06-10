---
title: Janela de migração
description: Documentação sobre como migrar para uma atualização no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647119"
---
# <a name="migration-window"></a>Janela de migração

À medida que o MRTK passa por alterações, alguns componentes podem ser preterido e as substituições serão introduzidas.
A janela de migração é uma ferramenta que ajuda os usuários a migrar automaticamente um subconjunto desses componentes preterido para as novas substituições.

![Janela de migração](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>Uso

Para abrir a janela, selecione Janela **de** Migração de Utilitários do Kit de Ferramentas de Realidade  >    >    >  **Misturada**. Depois que a janela de migração for aberta, as guias de navegação do modo de seleção poderão ser habilitadas escolhendo a implementação específica do componente do manipulador de migração.  

![Modos de seleção de migração](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>Modo de objeto

Selecionar a guia objetos permite que o objeto Campo para o qual o usuário possa arrastar e soltar qualquer objeto Game da cena aberta no momento ou pré-requisitos da pasta do projeto a ser migrado.
Pressionar o botão *remover (-)* exibido no lado direito do objeto listado remove o objeto da lista de seleção.

Depois que todos os objetos desejados estão na lista, pressionar o botão *Migrar* aplicará as alterações exigidas pela implementação do manipulador de migração escolhido a todos os componentes na seleção que corresponderem à implementação.

![Migração de seleção](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>Modo de cena

Permite que o usuário arraste e solte os ativos de cena que contêm objetos a serem migrados.

![Selecionando cenas para migração](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Modo de projeto

Pressionar o *botão Migrar* atualizará o componente direcionado pela implementação do manipulador de migração para todos os pré-requisitos e cenas no projeto.

![Migrando um projeto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>Confira também

- [Atualização de versões anteriores](../../updates-deployment/updating.md)
- [Versões do Microsoft Mixed Reality Toolkit](../../release-notes/mrtk-26-release-notes.md)
- [Roteiro do MRTK](../../roadmap.md)
