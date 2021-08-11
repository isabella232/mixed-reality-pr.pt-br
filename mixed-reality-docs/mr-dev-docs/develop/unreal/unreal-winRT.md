---
title: WinRT no Unreal
description: saiba como escrever e gerenciar recursos personalizados do WinRT em aplicativos inreais de realidade misturada para dispositivos HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicação remota, realidade misturada, desenvolvimento, introdução, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, WinRT, DLL
ms.openlocfilehash: b00886908f51804650220b6dbb7b3bfe4184cf33b505e3bd278327d1669c5067
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198358"
---
# <a name="winrt-in-unreal"></a>WinRT no Unreal

no decorrer do desenvolvimento de HoloLens, talvez seja necessário escrever um recurso usando o WinRT. por exemplo, abrir uma caixa de diálogo de arquivo em um aplicativo HoloLens precisaria do FileSavePicker no winrt/Windows. Armazenamento. Arquivo de cabeçalho de seletores. h. O WinRT tem suporte no sistema de compilação inreal da versão 4,26 em diante.

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se está seguindo o percurso de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada. A partir daqui, você pode continuar com qualquer [tópico](unreal-development-overview.md#3-advanced-features) ou ir diretamente para a implantação de seu aplicativo em um dispositivo ou emulador.

> [!div class="nextstepaction"]
> [Como fazer a implantação no dispositivo](unreal-deploying.md)

## <a name="see-also"></a>Confira também

* [APIs do C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)
* [Classe FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Bibliotecas de terceiros inreais](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)