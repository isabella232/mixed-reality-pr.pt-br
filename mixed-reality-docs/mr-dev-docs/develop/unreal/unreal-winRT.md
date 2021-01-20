---
title: WinRT no Unreal
description: Saiba como escrever e gerenciar recursos personalizados do WinRT em aplicativos de realidade misturados reais para dispositivos HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Inreal, não real Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicação remota, realidade mista, desenvolvimento, introdução, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, WinRT, DLL
ms.openlocfilehash: f32b5b3ddbee2e24e61d08b0a1b887b7b06e6da4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580416"
---
# <a name="winrt-in-unreal"></a>WinRT no Unreal

Ao longo do desenvolvimento do seu HoloLens, talvez seja necessário escrever um recurso usando o WinRT. Por exemplo, abrir uma caixa de diálogo de arquivo em um aplicativo HoloLens precisaria do FileSavePicker no arquivo de cabeçalho winrt/Windows. Storage.... O WinRT tem suporte no sistema de compilação inreal da versão 4,26 em diante.

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se está seguindo o percurso de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada. A partir daqui, você pode continuar com qualquer [tópico](unreal-development-overview.md#3-advanced-features) ou ir diretamente para a implantação de seu aplicativo em um dispositivo ou emulador.

> [!div class="nextstepaction"]
> [Como fazer a implantação no dispositivo](unreal-deploying.md)

## <a name="see-also"></a>Confira também

* [APIs do C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)
* [Classe FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Bibliotecas de terceiros inreais](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)