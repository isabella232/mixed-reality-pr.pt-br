---
title: Janela de migração
description: Documentação sobre como migrar para uma atualização no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 9e657e0b90f8087670b72c993ab1dcf78ae9e6680873139c6867d7c551a41895
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220028"
---
# <a name="migration-window"></a>Janela de migração

À medida que o MRTK passa por alterações, alguns componentes podem ser preteridos e substituições serão introduzidas.
A janela de migração é uma ferramenta que ajuda os usuários a migrar automaticamente um subconjunto desses componentes preteridos para as novas substituições.

![Janela de migração](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>Uso

para abrir a janela, selecione a janela de migração da **realidade mista**  >  **Toolkit**  >  **Utilities**  >  . Quando a janela de migração estiver aberta, as guias de navegação do modo de seleção poderão ser habilitadas escolhendo a implementação específica do componente do manipulador de migração.  

![Modos de seleção de migração](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>Modo de objeto

A seleção da guia objetos habilita o campo objeto para onde o usuário pode arrastar e soltar qualquer objeto de jogo da cena aberta no momento ou pré-fabricados da pasta do projeto a ser migrada.
Pressionar o botão Remover *(-)* exibido no lado direito do objeto listado remove o objeto da lista de seleção.

Depois que todos os objetos desejados estiverem na lista, pressionar o botão *migrar* aplicará as alterações exigidas pela implementação do manipulador de migração escolhido para todos os componentes na seleção que correspondam à implementação.

![Migração de seleção](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>Modo de cena

Permite que o usuário arraste e solte ativos de cena contendo objetos a serem migrados.

![Selecionando cenas para migração](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>modo de Project

Pressionar o botão *migrar* atualizará o componente direcionado pela implementação do manipulador de migração para todos os pré-fabricados e cenas no projeto.

![Migrando um projeto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>Confira também

- [Atualizando de versões anteriores](../../updates-deployment/updating.md)
- [Microsoft Mixed reality Toolkit versões](../../release-notes/mrtk-26-release-notes.md)
- [Roteiro do MRTK](../../roadmap.md)
