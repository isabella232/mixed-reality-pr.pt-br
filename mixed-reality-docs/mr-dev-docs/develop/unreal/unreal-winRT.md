---
title: WinRT no Unreal
description: Saiba como escrever e gerenciar recursos personalizados do WinRT em aplicativos de realidade misturados reais para dispositivos HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Inreal, não real Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicação remota, realidade mista, desenvolvimento, introdução, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, WinRT, DLL
ms.openlocfilehash: ac28ce08443de40d9f7eb32eb1b2e8e071a618b3
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007026"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="bd76b-104">WinRT no Unreal</span><span class="sxs-lookup"><span data-stu-id="bd76b-104">WinRT in Unreal</span></span>

<span data-ttu-id="bd76b-105">Ao longo do desenvolvimento do seu HoloLens, talvez seja necessário escrever um recurso usando o WinRT.</span><span class="sxs-lookup"><span data-stu-id="bd76b-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="bd76b-106">Por exemplo, abrir uma caixa de diálogo de arquivo em um aplicativo HoloLens precisaria do FileSavePicker no arquivo de cabeçalho winrt/Windows. Storage....</span><span class="sxs-lookup"><span data-stu-id="bd76b-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="bd76b-107">O WinRT tem suporte no sistema de compilação inreal da versão 4,26 em diante.</span><span class="sxs-lookup"><span data-stu-id="bd76b-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="bd76b-108">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="bd76b-108">Next Development Checkpoint</span></span>

<span data-ttu-id="bd76b-109">Se está seguindo o percurso de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="bd76b-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="bd76b-110">A partir daqui, você pode continuar com qualquer [tópico](unreal-development-overview.md#3-platform-capabilities-and-apis) ou ir diretamente para a implantação de seu aplicativo em um dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="bd76b-110">From here, you can continue to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd76b-111">Como fazer a implantação no dispositivo</span><span class="sxs-lookup"><span data-stu-id="bd76b-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="bd76b-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="bd76b-112">See also</span></span>

* [<span data-ttu-id="bd76b-113">APIs do C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="bd76b-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="bd76b-114">Classe FileSavePicker</span><span class="sxs-lookup"><span data-stu-id="bd76b-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="bd76b-115">Bibliotecas de terceiros inreais</span><span class="sxs-lookup"><span data-stu-id="bd76b-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
