---
title: MRTK e remoção de código gerenciado
description: Remoção de código no MRTK e no Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 09e5140fd9585c19eacac5ba937eaf4ea8f2a8ea
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143732"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="9c444-104">Remoção de código gerenciado por MRTK e Unity</span><span class="sxs-lookup"><span data-stu-id="9c444-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="9c444-105">Ao usar o back-end de script IL2CPP do Unity (opcional no Unity 2018,4, necessário no 2019 e mais recente), ocorre a [remoção de código gerenciado](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) .</span><span class="sxs-lookup"><span data-stu-id="9c444-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="9c444-106">O vinculador da Unity executa esse processo para reduzir o tamanho binário, bem como para diminuir os tempos de compilação.</span><span class="sxs-lookup"><span data-stu-id="9c444-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="9c444-107">O kit de ferramentas da realidade mista usa um arquivo, `link.xml` , para influenciar como o vinculador do Unity processa ASSEMBLIES MRTK.</span><span class="sxs-lookup"><span data-stu-id="9c444-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="9c444-108">Esse arquivo, descrito em Full na [documentação do Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), fornece ao vinculador instruções sobre como preservar o código quando seu uso não pode ser inferido (por exemplo: usado por meio de reflexão).</span><span class="sxs-lookup"><span data-stu-id="9c444-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="9c444-109">Como uma plataforma flexível e personalizável, o MRTK cria o `link.xml` arquivo na `Assets/MixedRealityToolkit.Generated` importação, caso ele não exista.</span><span class="sxs-lookup"><span data-stu-id="9c444-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="9c444-110">Arquivos de link.xml preexistentes não são substituídos.</span><span class="sxs-lookup"><span data-stu-id="9c444-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="9c444-111">É recomendável que `link.xml` e `link.xml.meta` seja adicionado ao controle de versão.</span><span class="sxs-lookup"><span data-stu-id="9c444-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="9c444-112">Os desenvolvedores devem se sentir livres para personalizar `Assets/MixedRealityToolkit.Generated/link.xml` o para atender às necessidades do projeto.</span><span class="sxs-lookup"><span data-stu-id="9c444-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="9c444-113">Por padrão, o arquivo de link.xml criado pelo MRTK preserva todo o conjunto de módulos (assemblies) mostrados nos dados a seguir.</span><span class="sxs-lookup"><span data-stu-id="9c444-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

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

<span data-ttu-id="9c444-114">Para obter mais informações sobre o formato de arquivo link.xml, consulte a documentação do Unity.</span><span class="sxs-lookup"><span data-stu-id="9c444-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c444-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="9c444-115">See also</span></span>

- [<span data-ttu-id="9c444-116">Unity: remoção de código gerenciado</span><span class="sxs-lookup"><span data-stu-id="9c444-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="9c444-117">Unity: vincular arquivo XML</span><span class="sxs-lookup"><span data-stu-id="9c444-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
