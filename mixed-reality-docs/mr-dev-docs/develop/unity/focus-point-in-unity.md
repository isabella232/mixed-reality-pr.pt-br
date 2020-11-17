---
title: Ponto de foco no Unity
description: Ajuste manual da estabilidade do holograma no Unity definindo o ponto de foco
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, ponto de foco, plano de foco, plano de estabilização, ponto de estabilização, Reprojeção, LSR, buffer de profundidade, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 48c0d26e89124b9dbfc1d108354fb6e751e51783
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678685"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="2cd9a-104">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="2cd9a-104">Focus point in Unity</span></span>

<span data-ttu-id="2cd9a-105">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="2cd9a-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="2cd9a-106">**Tipo**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="2cd9a-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="2cd9a-107">O [ponto de foco](../platform-capabilities-and-apis/hologram-stability.md#reprojection) pode ser definido para fornecer uma dica sobre como executar melhor a estabilização nos hologramas que estão sendo exibidos no momento.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-107">The [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="2cd9a-108">Se você quiser definir o ponto de foco no Unity, ele precisará ser definido a cada quadro usando *HolographicSettings. SetFocusPointForFrame ()*.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="2cd9a-109">Se o ponto de foco não estiver definido para um quadro, o plano de estabilização padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="2cd9a-110">Por padrão, novos projetos do Unity têm a opção "Habilitar compartilhamento de buffer de profundidade" definida.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="2cd9a-111">Com essa opção, um aplicativo de Unity em execução em um headset de área de trabalho imersiva ou um HoloLens executando a atualização de abril de 2018 do Windows (RS4) ou posterior enviará seu buffer de profundidade para o Windows para otimizar a estabilidade do holograma automaticamente, sem que seu aplicativo especifique um ponto de foco:</span><span class="sxs-lookup"><span data-stu-id="2cd9a-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="2cd9a-112">Em um headset de área de trabalho imersiva, isso habilitará a Reprojeção baseada em profundidade por pixel.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="2cd9a-113">Em um HoloLens executando a atualização de abril de 2018 do Windows 10 ou posterior, isso analisará o buffer de profundidade para escolher um plano de estabilização ideal automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="2cd9a-114">Qualquer uma das abordagens deve fornecer uma qualidade de imagem ainda melhor sem trabalho explícito por seu aplicativo para selecionar um ponto de foco para cada quadro.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="2cd9a-115">Observe que, se você fornecer um ponto de foco manualmente, isso substituirá o comportamento automático descrito acima e geralmente reduzirá a estabilidade do holograma.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="2cd9a-116">Em geral, você deve especificar apenas um ponto de foco manual quando seu aplicativo estiver em execução em um HoloLens que ainda não foi atualizado para a atualização do Windows 10 de abril de 2018.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="2cd9a-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cd9a-117">Example</span></span>

<span data-ttu-id="2cd9a-118">Há várias maneiras de definir o ponto de foco, conforme sugerido pelas sobrecargas disponíveis na função estática *SetFocusPointForFrame* .</span><span class="sxs-lookup"><span data-stu-id="2cd9a-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="2cd9a-119">Veja abaixo um exemplo simples para definir o plano de foco para o objeto fornecido para cada quadro:</span><span class="sxs-lookup"><span data-stu-id="2cd9a-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="2cd9a-120">Observe que o código simples acima pode acabar reduzindo a estabilidade do holograma se o objeto focalizado terminar por trás do usuário.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="2cd9a-121">É por isso que você geralmente deve definir "habilitar o compartilhamento de buffer de profundidade" em vez de especificar manualmente um ponto de foco.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2cd9a-122">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="2cd9a-122">Next Development Checkpoint</span></span>

<span data-ttu-id="2cd9a-123">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-123">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="2cd9a-124">Daí, você pode prosseguir para o próximo tópico:</span><span class="sxs-lookup"><span data-stu-id="2cd9a-124">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2cd9a-125">Controle de perda</span><span class="sxs-lookup"><span data-stu-id="2cd9a-125">Tracking loss</span></span>](tracking-loss-in-unity.md)

<span data-ttu-id="2cd9a-126">Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:</span><span class="sxs-lookup"><span data-stu-id="2cd9a-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2cd9a-127">Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="2cd9a-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="2cd9a-128">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-platform-capabilities-and-apis) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="2cd9a-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="2cd9a-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="2cd9a-129">See also</span></span>
* [<span data-ttu-id="2cd9a-130">Plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="2cd9a-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
