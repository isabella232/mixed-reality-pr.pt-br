---
title: MRTK e remoção de código gerenciado
description: Remoção de código no MRTK e no Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 8b8e0f4488a6e955e599084c0b59d8c80f553a78
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176290"
---
# <a name="mrtk-and-managed-code-stripping"></a>MRTK e remoção de código gerenciado

Ao usar o back-end de script IL2CPP do Unity (opcional no Unity 2018,4, necessário no 2019 e mais recente), ocorre a [remoção de código gerenciado](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) .
O vinculador da Unity executa esse processo para reduzir o tamanho binário, bem como para diminuir os tempos de compilação.

a realidade misturada Toolkit usa um arquivo, `link.xml` , para influenciar como o vinculador do Unity processa os assemblies MRTK. Esse arquivo, descrito em Full na [documentação do Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), fornece ao vinculador instruções sobre como preservar o código quando seu uso não pode ser inferido (por exemplo: usado por meio de reflexão).

Como uma plataforma flexível e personalizável, o MRTK cria o `link.xml` arquivo na `Assets/MixedRealityToolkit.Generated` importação, caso ele não exista. Arquivos de link.xml preexistentes não são substituídos. É recomendável que `link.xml` e `link.xml.meta` seja adicionado ao controle de versão. Os desenvolvedores devem se sentir livres para personalizar `Assets/MixedRealityToolkit.Generated/link.xml` o para atender às necessidades do projeto.

Por padrão, o arquivo de link.xml criado pelo MRTK preserva todo o conjunto de módulos (assemblies) mostrados nos dados a seguir.

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

Para obter mais informações sobre o formato de arquivo link.xml, consulte a documentação do Unity.

## <a name="see-also"></a>Confira também

- [Unity: remoção de código gerenciado](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: vincular arquivo XML](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
