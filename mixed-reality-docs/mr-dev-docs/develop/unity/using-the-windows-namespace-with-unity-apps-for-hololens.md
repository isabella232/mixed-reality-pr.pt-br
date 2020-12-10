---
title: APIs do WinRT com Unity para HoloLens
description: Explica como fazer uso de APIs do WinRT (o namespace do Windows) em seu projeto do Unity para o HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, realidade mista do Windows, API, passo a passos, headset de realidade misturada, headset da realidade mista do Windows, headset da realidade virtual, APIs de realidade misturada
ms.openlocfilehash: ff12df7eb41350fe1f842b3450f3532e4ab8ffa1
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010577"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="55203-104">APIs do WinRT com Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="55203-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="55203-105">Esta página descreve como fazer uso de APIs do WinRT em seu projeto do Unity para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="55203-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="55203-106">APIs de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="55203-106">Mixed Reality APIs</span></span>

<span data-ttu-id="55203-107">Um subconjunto focado na realidade misturada do SDK do Windows foi disponibilizado em uma projeção compatível com .NET Standard 2,0, que pode ser usada em seu projeto sem diretivas de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="55203-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="55203-108">A maioria das APIs no Windows.</span><span class="sxs-lookup"><span data-stu-id="55203-108">Most APIs in the Windows.</span></span> <span data-ttu-id="55203-109">Os namespaces de percepção e Windows. UI. Input. Spatial estão incluídos e podem expandir para incluir APIs adicionais no futuro.</span><span class="sxs-lookup"><span data-stu-id="55203-109">Perception and Windows.UI.Input.Spatial namespaces are included and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="55203-110">As APIs projetadas podem ser usadas durante a execução no editor, o que permite o uso do [modo de reprodução](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span><span class="sxs-lookup"><span data-stu-id="55203-110">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="55203-111">Para usar essa projeção, faça as seguintes modificações em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="55203-111">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="55203-112">Adicione uma referência ao pacote NuGet [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) usando o [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="55203-112">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="55203-113">Referências de prefixo ao `Windows` namespace com `Microsoft.` :</span><span class="sxs-lookup"><span data-stu-id="55203-113">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="55203-114">Substituir conversões de ponteiro nativo por `FromNativePtr` :</span><span class="sxs-lookup"><span data-stu-id="55203-114">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="55203-115">Incluir condicionalmente chamadas à API do WinRT</span><span class="sxs-lookup"><span data-stu-id="55203-115">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="55203-116">Você também pode usar as APIs do WinRT em projetos do Unity criados para o Plataforma Universal do Windows e o Xbox One Platform usando diretivas de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="55203-116">You can also use the WinRT APIs in Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives.</span></span> <span data-ttu-id="55203-117">Qualquer código que você escreve em scripts do Unity que visam APIs do WinRT deve ser incluído condicionalmente somente para as compilações.</span><span class="sxs-lookup"><span data-stu-id="55203-117">Any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="55203-118">Isso pode ser feito por meio de duas etapas no Unity:</span><span class="sxs-lookup"><span data-stu-id="55203-118">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="55203-119">O nível de compatibilidade da API deve ser definido como **.net 4,6** ou **.net Standard 2,0** nas configurações do Player</span><span class="sxs-lookup"><span data-stu-id="55203-119">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="55203-120">**Editar**  >  **Configurações**  >  do projeto **Player**  >  do **Configuração**  >  do **Nível de compatibilidade de API** para **.net 4,6** ou **.net Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="55203-120">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="55203-121">A diretiva de pré-processador **ENABLE_WINMD_SUPPORT** deve ser encapsulada em torno de qualquer código aproveitado por WinRT</span><span class="sxs-lookup"><span data-stu-id="55203-121">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="55203-122">O trecho de código a seguir é da página manual do Unity para [plataforma universal do Windows: API do WinRT em scripts C#](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="55203-122">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="55203-123">Neste exemplo, uma ID de anúncio é retornada, mas somente no UWP e no Xbox, uma compila:</span><span class="sxs-lookup"><span data-stu-id="55203-123">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="55203-124">Editar seus scripts em um projeto do Unity C#</span><span class="sxs-lookup"><span data-stu-id="55203-124">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="55203-125">Quando você clica duas vezes em um script no editor do Unity, ele inicia o script por padrão em um projeto do editor.</span><span class="sxs-lookup"><span data-stu-id="55203-125">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="55203-126">As APIs do WinRT parecerão desconhecidas, pois o projeto do Visual Studio não faz referência à Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="55203-126">The WinRT APIs will appear to be unknown because the Visual Studio project doesn't reference the Windows Runtime.</span></span> <span data-ttu-id="55203-127">A diretiva **ENABLE_WINMD_SUPPORT** é indefinida e qualquer *#if* código encapsulado é ignorado até que você compile seu projeto em uma solução UWP do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55203-127">The **ENABLE_WINMD_SUPPORT** directive is undefined and any *#if* wrapped code is ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="55203-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="55203-128">See also</span></span>
* [<span data-ttu-id="55203-129">Como exportar e criar uma solução do Visual Studio do Unity</span><span class="sxs-lookup"><span data-stu-id="55203-129">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="55203-130">Windows Runtime Unity de suporte</span><span class="sxs-lookup"><span data-stu-id="55203-130">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
