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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="40b27-104">Solução de problemas do OpenXR</span><span class="sxs-lookup"><span data-stu-id="40b27-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="40b27-105">Aqui estão algumas dicas de solução de problemas ao desenvolver um aplicativo OpenXR usando o tempo de execução do Windows Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="40b27-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="40b27-106">Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.</span><span class="sxs-lookup"><span data-stu-id="40b27-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="40b27-107">Há problemas conhecidos no tempo de execução OpenXR misto do Windows Mixed real com aplicativos x86.</span><span class="sxs-lookup"><span data-stu-id="40b27-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="40b27-108">Você deve criar aplicativos de desktop OpenXR para x64 no momento.</span><span class="sxs-lookup"><span data-stu-id="40b27-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="40b27-109">O aplicativo OpenXR não está iniciando a realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="40b27-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="40b27-110">Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, o tempo de execução do Windows Mixed Reality OpenXR não poderá ser definido como o tempo de execução ativo.</span><span class="sxs-lookup"><span data-stu-id="40b27-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="40b27-111">Siga as instruções para [introdução ao OpenXR for Windows Mixed realness headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="40b27-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="40b27-112">Você também pode executar o [OpenXR ferramentas para desenvolvedores para o Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obter ajuda para a solução de problemas no estado de seus sistemas Windows Mixed Reality OpenXR Runtime.</span><span class="sxs-lookup"><span data-stu-id="40b27-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>