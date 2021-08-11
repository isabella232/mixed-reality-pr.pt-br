---
title: Solução de problemas do OpenXR
description: encontre recursos e respostas a problemas comuns de solução em seus aplicativos Windows Mixed Reality OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, solução de problemas
ms.openlocfilehash: 456dcf927c70aaaebc8dda1338d24acc910a1e801cf29e8880048d44f9432718
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219200"
---
# <a name="openxr-troubleshooting"></a>Solução de problemas do OpenXR

aqui estão algumas dicas de solução de problemas ao desenvolver um aplicativo OpenXR usando o tempo de execução do Windows Mixed Reality OpenXR.  Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.

>[!NOTE]
>há problemas conhecidos no tempo de execução atual do Windows Mixed Reality OpenXR com aplicativos x86.  Você deve criar aplicativos de desktop OpenXR para x64 no momento.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>O aplicativo OpenXR não está iniciando Windows Mixed Reality

se seu aplicativo OpenXR não estiver iniciando Windows Mixed Reality quando você executá-lo, o Windows Mixed Reality tempo de execução do OpenXR não poderá ser definido como o tempo de execução ativo. siga as instruções de [introdução ao OpenXR para obter Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para corrigir o problema.

você também pode executar o [Ferramentas para Desenvolvedores OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obter ajuda para a solução de problemas no estado de seus sistemas Windows Mixed Reality tempo de execução do OpenXR.