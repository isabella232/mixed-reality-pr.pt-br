---
title: Solução de problemas do OpenXR
description: Solucionar problemas em seus aplicativos OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, solução de problemas
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903091"
---
# <a name="openxr-troubleshooting"></a>Solução de problemas do OpenXR

Aqui estão algumas dicas de solução de problemas ao desenvolver um aplicativo OpenXR usando o tempo de execução do Windows Mixed Reality OpenXR.  Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.

>[!NOTE]
>Há problemas conhecidos no tempo de execução OpenXR misto do Windows Mixed real com aplicativos x86.  Você deve criar aplicativos de desktop OpenXR para x64 no momento.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>O aplicativo OpenXR não está iniciando a realidade mista do Windows

Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, o tempo de execução do Windows Mixed Reality OpenXR não poderá ser definido como o tempo de execução ativo.  Certifique-se de seguir as instruções para [introdução ao OpenXR for Windows Mixed realness headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para tornar o tempo de execução ativo.

Você também pode executar o [OpenXR ferramentas para desenvolvedores for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obter ajuda adicional sobre o estado do tempo de execução do Windows Mixed Reality OpenXR em seu sistema.