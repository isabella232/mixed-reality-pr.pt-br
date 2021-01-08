---
title: Como controlar a perda no Unity
description: Saiba como lidar com a perda de rastreamento manual e padrão em um aplicativo do Unity Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perda de controle, imagem de perda de rastreamento, sondagem, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009846"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="64fc6-104">Como controlar a perda no Unity</span><span class="sxs-lookup"><span data-stu-id="64fc6-104">Tracking loss in Unity</span></span>

<span data-ttu-id="64fc6-105">Quando o dispositivo não consegue se localizar no mundo, o aplicativo tem "perda de rastreamento".</span><span class="sxs-lookup"><span data-stu-id="64fc6-105">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="64fc6-106">Por padrão, o Unity pausará o loop de atualização e exibirá uma imagem de abertura para o usuário em qualquer momento que o controle for perdido.</span><span class="sxs-lookup"><span data-stu-id="64fc6-106">By default, Unity will pause the update loop and display a splash image to the user anytime tracking is lost.</span></span> <span data-ttu-id="64fc6-107">Depois que o controle é retomado, a imagem de abertura desaparece e o loop de atualização continua.</span><span class="sxs-lookup"><span data-stu-id="64fc6-107">Once tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="64fc6-108">Como alternativa, o usuário pode lidar com essa transição manualmente, recusando a configuração.</span><span class="sxs-lookup"><span data-stu-id="64fc6-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="64fc6-109">Todo o conteúdo parecerá ficar bloqueado durante a perda de rastreamento se nada for feito para tratá-lo.</span><span class="sxs-lookup"><span data-stu-id="64fc6-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="64fc6-110">Manipulação padrão</span><span class="sxs-lookup"><span data-stu-id="64fc6-110">Default Handling</span></span>

<span data-ttu-id="64fc6-111">O loop Update e todas as mensagens e eventos serão interrompidos pela duração da perda de rastreamento por padrão.</span><span class="sxs-lookup"><span data-stu-id="64fc6-111">The update loop and all messages and events will stop for the duration of tracking loss by default.</span></span> <span data-ttu-id="64fc6-112">Ao mesmo tempo, uma imagem será exibida para o usuário.</span><span class="sxs-lookup"><span data-stu-id="64fc6-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="64fc6-113">Você pode personalizar essa imagem acessando configurações de >de edição – >Player, clicando em imagem de abertura e definindo a imagem de perda de rastreamento de Holographic.</span><span class="sxs-lookup"><span data-stu-id="64fc6-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="64fc6-114">Manipulação manual</span><span class="sxs-lookup"><span data-stu-id="64fc6-114">Manual Handling</span></span>

<span data-ttu-id="64fc6-115">Para tratar manualmente a perda de rastreamento, você precisa ir para **Editar**  >  **configurações de projeto**  >    >  **plataforma universal do Windows guia Configurações**  >  **imagem de splash**  >  **Windows Holographic** e desmarcar "durante a perda de controle Pause e show image".</span><span class="sxs-lookup"><span data-stu-id="64fc6-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="64fc6-116">Depois, você precisa lidar com as alterações de controle com as APIs especificadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="64fc6-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="64fc6-117">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="64fc6-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="64fc6-118">**Tipo:** *worldmanager*</span><span class="sxs-lookup"><span data-stu-id="64fc6-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="64fc6-119">O World Manager expõe um evento para detectar o controle perdido/obtido (*worldmanager. OnPositionalLocatorStateChanged*) e uma propriedade para consultar o estado atual (*worldmanager. State*)</span><span class="sxs-lookup"><span data-stu-id="64fc6-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="64fc6-120">Quando o estado de controle não está ativo, a câmera parece não ser traduzida no mundo virtual mesmo que o usuário se traduz.</span><span class="sxs-lookup"><span data-stu-id="64fc6-120">When the tracking state isn't active, the camera won't appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="64fc6-121">Os objetos não corresponderão mais a qualquer local físico e todos serão exibidos no corpo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="64fc6-121">Objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="64fc6-122">Ao manipular alterações de controle por conta própria, você precisa sondar a propriedade de estado em cada quadro ou manipular o evento *OnPositionalLocatorStateChanged* .</span><span class="sxs-lookup"><span data-stu-id="64fc6-122">When handling tracking changes on your own, you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="64fc6-123">Sondagem</span><span class="sxs-lookup"><span data-stu-id="64fc6-123">Polling</span></span>

<span data-ttu-id="64fc6-124">O estado mais importante é *PositionalLocatorState. Active*, o que significa que o controle é totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="64fc6-124">The most important state is *PositionalLocatorState.Active*, which means tracking is fully functional.</span></span> <span data-ttu-id="64fc6-125">Qualquer outro Estado resultará em apenas deltas rotacionais para a câmera principal.</span><span class="sxs-lookup"><span data-stu-id="64fc6-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="64fc6-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="64fc6-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="64fc6-127">Manipulando o evento OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="64fc6-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="64fc6-128">Mais convenientemente, você também pode assinar o *OnPositionalLocatorStateChanged* para lidar com as transições:</span><span class="sxs-lookup"><span data-stu-id="64fc6-128">More conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="64fc6-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="64fc6-129">See also</span></span>

* [<span data-ttu-id="64fc6-130">Lidando com a perda de controle no DirectX</span><span class="sxs-lookup"><span data-stu-id="64fc6-130">Handling tracking loss in DirectX</span></span>](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
