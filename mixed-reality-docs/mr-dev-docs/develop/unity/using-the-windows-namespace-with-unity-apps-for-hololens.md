---
title: APIs do WinRT com Unity para HoloLens
description: Saiba mais sobre como usar as APIs do WinRT e o namespace Windows em seus projetos de realidade misturada do Unity para HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, passo a passo, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, APIs de Realidade Misturada
ms.openlocfilehash: 158c28d9186269108442226bbfcfc90a3c235a71336fdab9dbf9eadc21a309a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215602"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>APIs do WinRT com Unity para HoloLens

Esta página descreve como usar as APIs do WinRT em seu projeto do Unity para HoloLens.

## <a name="mixed-reality-apis"></a>APIs de Realidade Misturada

Um subconjunto voltado para Realidade Misturada do SDK do Windows foi disponibilizado em uma projeção compatível com o .NET Standard 2.0, que você pode usar em seu projeto sem diretivas de pré-processador. A maioria das APIs no Windows. Percepção e Windows. Ui. Os namespaces Input.Spatial são incluídos e podem ser expandidos para incluir APIs adicionais no futuro. As APIs projetadas podem ser usadas durante a execução no Editor, o que permite o uso do Modo [de Reprodução.](/windows/mixed-reality/unity-play-mode) Para usar essa projeção, faça as seguintes modificações em seu projeto:

1) Adicione uma referência ao [Microsoft.Windows. Pacote de NuGet MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) [usando NuGet para Unity.](https://github.com/GlitchEnzo/NuGetForUnity)
2) Referências de prefixo ao `Windows` namespace com `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Substitua as casts de ponteiro nativo por `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Incluir condicionalmente chamadas à API do WinRT

Você também pode usar as APIs do WinRT em projetos do Unity desenvolvidos para a plataforma Windows Universal e Xbox One usando diretivas de pré-processador. Qualquer código que você escreve em scripts do Unity destinados a APIs do WinRT deve ser incluído condicionalmente apenas para esses builds. 

Isso pode ser feito por meio de duas etapas no Unity:
1) O nível de compatibilidade da API deve ser definido como **.NET 4.6** **ou .NET Standard 2.0** nas configurações do player
    - **Editar**  >  **Project Configurações**  >  **Player**  >  **Configuração**  >  **Nível de compatibilidade da API** **para .NET 4.6** **ou .NET Standard 2.0**
2) A diretiva de **pré-processador ENABLE_WINMD_SUPPORT** deve ser envolvida em qualquer código aproveitado pelo WinRT

O snippet de código a seguir é da página manual do Unity para [a Plataforma universal Windows: API do WinRT em scripts C#.](https://docs.unity3d.com/Manual/windowsstore-scripts.html) Neste exemplo, uma ID de publicidade é retornada, mas somente na UWP e Xbox One builds:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Editar seus scripts em um projeto C# do Unity

Quando você clicar duas vezes em um script no editor do Unity, ele iniciará por padrão o script em um projeto de editor. As APIs do WinRT parecerão desconhecidas porque o Visual Studio projeto não faz referência ao Windows Runtime. A **ENABLE_WINMD_SUPPORT** é indefinida e qualquer código  #if é ignorado até que você crie seu projeto em uma solução de Visual Studio UWP.

## <a name="see-also"></a>Confira também
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Unity de suporte de runtime](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)