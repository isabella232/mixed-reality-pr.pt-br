---
title: Solução de problemas do OpenXR
description: Encontre recursos e respostas para solucionar problemas comuns em seus aplicativos OpenXR de realidade mista do Windows.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, solução de problemas
ms.openlocfilehash: 6e1696bca4f31f70af10c32087400ed56efa3c11
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006725"
---
# <a name="openxr-troubleshooting"></a>Solução de problemas do OpenXR

Aqui estão algumas dicas de solução de problemas ao desenvolver um aplicativo OpenXR usando o tempo de execução do Windows Mixed Reality OpenXR.  Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.

>[!NOTE]
>Há problemas conhecidos no tempo de execução OpenXR misto do Windows Mixed real com aplicativos x86.  Você deve criar aplicativos de desktop OpenXR para x64 no momento.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>O aplicativo OpenXR não está iniciando a realidade mista do Windows

Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, o tempo de execução do Windows Mixed Reality OpenXR não poderá ser definido como o tempo de execução ativo. Siga as instruções para [introdução ao OpenXR for Windows Mixed realness headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para corrigir o problema.

Você também pode executar o [OpenXR ferramentas para desenvolvedores para o Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obter ajuda para a solução de problemas no estado de seus sistemas Windows Mixed Reality OpenXR Runtime.