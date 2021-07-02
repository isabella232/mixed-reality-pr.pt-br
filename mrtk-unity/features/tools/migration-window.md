---
title: Janela de migração
description: Documentação sobre como migrar para uma atualização no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 9d960d01e738736edd452a124db5c306b5d752ce
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176132"
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
