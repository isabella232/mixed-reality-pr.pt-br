---
title: Solução de problemas do OpenXR
description: Solucionar problemas em seus aplicativos OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, solução de problemas
ms.openlocfilehash: ddfe548d689d84576ad0ac06bda46d7c2757859c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612930"
---
# <a name="openxr-troubleshooting"></a>Solução de problemas do OpenXR

Aqui estão algumas dicas de solução de problemas ao desenvolver um aplicativo OpenXR usando o tempo de execução do Windows Mixed Reality OpenXR.  Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.

>[!NOTE]
>Há problemas conhecidos no tempo de execução OpenXR misto do Windows Mixed real com aplicativos x86.  Você deve criar aplicativos de desktop OpenXR para x64 no momento.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>O aplicativo OpenXR não está iniciando a realidade mista do Windows

Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, o tempo de execução do Windows Mixed Reality OpenXR não poderá ser definido como o tempo de execução ativo. Siga as instruções para [introdução ao OpenXR for Windows Mixed realness headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para corrigir o problema.

Você também pode executar o [OpenXR ferramentas para desenvolvedores para o Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obter ajuda para a solução de problemas no estado de seus sistemas Windows Mixed Reality OpenXR Runtime.