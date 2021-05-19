---
title: Ferramenta de atualização do sombreador
description: Documentação sobre como atualizar os sombreadores padrão do MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: ed9f9fa5e6337850f31ecce9d07bc82a8ea12060
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145135"
---
# <a name="updating-shaders"></a>Atualizando sombreadores

A partir da versão 2.6.0, os sombreadores MRTK estão sendo versionado por meio do MRTK. Arquivo shaders. Sentinel. Ao atualizar para uma nova versão do MRTK, a seguinte mensagem pode ser exibida.

![Aviso de atualização de sombreadores](../images/tools/UpdateShaderPrompt.png)

Selecionar **Sim** instrui o MRTK a substituir o conteúdo dos **ativos**  >  **MRTK**  >  **sombreadores** pela versão mais recente. Selecionar **não** preservará os arquivos atuais. **Ignorar** criará um arquivo ( `IgnoreUpdateCheck.sentinel` ) em **ativos**  >  **MRTK**  >  **sombreadores**, o que irá suprimir verificações de atualização de sombreador futuras.

> [!IMPORTANT]
> Ao substituir os arquivos do sombreador, todas as modificações personalizadas serão perdidas. Certifique-se de fazer backup de todos os arquivos de sombreador modificados antes de atualizar.
>
> Se o projeto tiver sido configurado para usar o pipeline de processamento universal (Urp), anteriormente conhecido como LWRP (pipeline de renderização leve), execute novamente o **Mixed Reality Toolkit** > **Utilities** >
>  **upgrade MRTK Standard Shader para Lightweight render pipeline**.

Em também é possível verificar se há atualizações de sombreador a qualquer momento usando utilitários de **Kit de ferramentas de realidade misturada**  >    >  **verificar atualizações de sombreador** na barra de menus do editor de Unity.

![Verificar se há atualizações de sombreador](../images/tools/ShaderUpdateMenu.png)

A **verificação de atualizações de sombreador** ignora o `IgnoreUpdateCheck.sentinel` arquivo e permite a atualização de sombreador sob demanda.

> [!NOTE]
> A verificação de atualizações de sombreador não é necessária ao importar os arquivos MRTK. unitypackage.
