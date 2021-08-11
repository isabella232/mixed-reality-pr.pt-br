---
title: Ferramenta de Atualização do Sombreador
description: Documentação sobre como atualizar sombreadores padrão do MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 9ed8a1e439b2bf911d8144a90259d99bf38b12e0404d9ad3365152bed633042c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197056"
---
# <a name="updating-shaders"></a>Atualizando sombreadores

A partir da versão 2.6.0, os sombreadores do MRTK estão sendo versão por meio do MRTK. Arquivo Shaders.sentinel. Ao atualizar para uma nova versão do MRTK, a mensagem a seguir pode aparecer.

![Atualizar prompt de sombreadores](../images/tools/UpdateShaderPrompt.png)

Selecionar **Sim** instrui o MRTK a substituir o conteúdo dos **Sombreadores** do  >  **MRTK** de  >   Ativos pela versão mais recente. Selecionar **Não** preservará os arquivos atuais. **Ignorar** criará um arquivo ( `IgnoreUpdateCheck.sentinel` ) em Sombreadores   >  **do MRTK** de  >  Ativos, que suprimirá futuras verificações de atualização do sombreador.

> [!IMPORTANT]
> Ao sobrescrever os arquivos de sombreador, todas as modificações personalizadas serão perdidas. Certifique-se de fazer backup de todos os arquivos de sombreador modificados antes de atualizar.
>
> Se o projeto tiver sido configurado para usar o URP (Pipeline de Renderização Universal)  – anteriormente LWRP (Lightweight Render Pipeline Toolkit), execute o Sombreador Padrão do MRTK de Atualização de Realidade Misturada para Pipeline de >  >  >
>  **Renderização** Leve.

Em também é possível verificar se há atualizações do sombreador a qualquer momento usando a Opção Toolkit Utilitários de Realidade Misturada Verificar se há Atualizações do Sombreador na barra de  >    >    >  **menus** do Editor do Unity.

![Verificar se há atualizações do sombreador](../images/tools/ShaderUpdateMenu.png)

**A verificação de Atualizações do Sombreador** desconsidera o arquivo e permite a atualização `IgnoreUpdateCheck.sentinel` do sombreador sob demanda.

> [!NOTE]
> A verificação de atualizações do sombreador não é necessária ao importar os arquivos .unitypackage do MRTK.
