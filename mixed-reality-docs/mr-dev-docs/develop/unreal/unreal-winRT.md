---
title: WinRT no Unreal
description: Visão geral do plug-in de áudio espacial do Unreal Engine.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Inreal, não real Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicação remota, realidade mista, desenvolvimento, introdução, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, WinRT, DLL
ms.openlocfilehash: f86939ee53b51fad1e31d18f810d92c3d20611f8
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926071"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="56b69-104">WinRT no Unreal</span><span class="sxs-lookup"><span data-stu-id="56b69-104">WinRT in Unreal</span></span>

<span data-ttu-id="56b69-105">Ao longo do desenvolvimento do seu HoloLens, talvez seja necessário escrever um recurso usando o WinRT.</span><span class="sxs-lookup"><span data-stu-id="56b69-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="56b69-106">Por exemplo, abrir uma caixa de diálogo de arquivo em um aplicativo HoloLens precisaria do FileSavePicker no arquivo de cabeçalho winrt/Windows. Storage....</span><span class="sxs-lookup"><span data-stu-id="56b69-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="56b69-107">O WinRT tem suporte no sistema de compilação inreal da versão 4,26 em diante.</span><span class="sxs-lookup"><span data-stu-id="56b69-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="56b69-108">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="56b69-108">Next Development Checkpoint</span></span>

<span data-ttu-id="56b69-109">Se você estiver seguindo a jornada de desenvolvimento inreal que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="56b69-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="56b69-110">A partir daqui, você pode continuar com qualquer [tópico](unreal-development-overview.md#3-platform-capabilities-and-apis) ou ir diretamente para a implantação de seu aplicativo em um dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="56b69-110">From here, you can continue to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56b69-111">Como fazer a implantação no dispositivo</span><span class="sxs-lookup"><span data-stu-id="56b69-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="56b69-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="56b69-112">See also</span></span>
* [<span data-ttu-id="56b69-113">APIs do C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="56b69-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="56b69-114">Classe FileSavePicker</span><span class="sxs-lookup"><span data-stu-id="56b69-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="56b69-115">Bibliotecas de terceiros inreais</span><span class="sxs-lookup"><span data-stu-id="56b69-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
