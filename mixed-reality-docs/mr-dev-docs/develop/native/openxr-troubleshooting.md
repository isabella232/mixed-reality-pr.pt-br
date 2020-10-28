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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="2bfef-104">Solução de problemas do OpenXR</span><span class="sxs-lookup"><span data-stu-id="2bfef-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="2bfef-105">Aqui estão algumas dicas de solução de problemas ao desenvolver um aplicativo OpenXR usando o tempo de execução do Windows Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="2bfef-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="2bfef-106">Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.</span><span class="sxs-lookup"><span data-stu-id="2bfef-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="2bfef-107">Há problemas conhecidos no tempo de execução OpenXR misto do Windows Mixed real com aplicativos x86.</span><span class="sxs-lookup"><span data-stu-id="2bfef-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="2bfef-108">Você deve criar aplicativos de desktop OpenXR para x64 no momento.</span><span class="sxs-lookup"><span data-stu-id="2bfef-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="2bfef-109">O aplicativo OpenXR não está iniciando a realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="2bfef-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="2bfef-110">Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, o tempo de execução do Windows Mixed Reality OpenXR não poderá ser definido como o tempo de execução ativo.</span><span class="sxs-lookup"><span data-stu-id="2bfef-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="2bfef-111">Certifique-se de seguir as instruções para [introdução ao OpenXR for Windows Mixed realness headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para tornar o tempo de execução ativo.</span><span class="sxs-lookup"><span data-stu-id="2bfef-111">Be sure to follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="2bfef-112">Você também pode executar o [OpenXR ferramentas para desenvolvedores for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obter ajuda adicional sobre o estado do tempo de execução do Windows Mixed Reality OpenXR em seu sistema.</span><span class="sxs-lookup"><span data-stu-id="2bfef-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>