---
title: MRTK e remoção de código gerenciado
description: S strip de código no MRTK e no Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 4348adf1d9cb2e7fc74cf5258e3272baaac96a5fc34565873cf35ae93225bdbe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221866"
---
# <a name="mrtk-and-managed-code-stripping"></a>MRTK e remoção de código gerenciado

Ao usar o back-end de script IL2CPP do Unity (opcional no Unity 2018.4, necessário em 2019 e mais [recentes),](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) ocorre a remoção de código gerenciado.
O linker do Unity executa esse processo para reduzir o tamanho binário, bem como diminuir os tempos de build.

A Toolkit realidade misturada usa um arquivo, , para influenciar como o vinculador do `link.xml` Unity processa assemblies do MRTK. Esse arquivo, descrito na documentação completa do [Unity,](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)fornece ao associador instruções sobre como preservar o código quando seu uso não pode ser inferido (por exemplo, usado por meio de reflexão).

Como uma plataforma flexível e personalizável, o MRTK cria o arquivo em na importação, se for `link.xml` considerado que ele não `Assets/MixedRealityToolkit.Generated` existe. Arquivos de link.xml existentes não são substituídos. É recomendável que `link.xml` e `link.xml.meta` sejam adicionados ao controle de versão. Os desenvolvedores devem se sentir à `Assets/MixedRealityToolkit.Generated/link.xml` vontade para personalizar para atender às necessidades do projeto.

Por padrão, link.xml arquivo criado pelo MRTK preserva a totalidade dos assemblies mostrados nos dados a seguir.

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

Para obter mais informações sobre o link.xml arquivo, consulte a documentação do Unity.

## <a name="see-also"></a>Confira também

- [Unity: s strip de código gerenciado](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: vincular arquivo XML](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
