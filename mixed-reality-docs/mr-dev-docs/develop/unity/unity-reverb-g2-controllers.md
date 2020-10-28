---
title: Controladores de reverbo do HP G2 no Unity
description: Instruções sobre como usar os controladores de reverberação HP reverbo G2 no SteamVR e no Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, reverberação, reverbo G2, HP reverbs G2, realidade mista, desenvolvimento, controladores de movimento, entrada do usuário, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638383"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="e90a0-104">Controladores de reverbo do HP G2 no Unity</span><span class="sxs-lookup"><span data-stu-id="e90a0-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="e90a0-105">Introdução</span><span class="sxs-lookup"><span data-stu-id="e90a0-105">Getting started</span></span>

<span data-ttu-id="e90a0-106">Não há nenhuma configuração adicional necessária para usar o controlador do HP reverberar G2 se você estiver desenvolvendo para SteamVR ou usando a API de entrada do Windows Mixed Reality (XR. WSA. Entrada).</span><span class="sxs-lookup"><span data-stu-id="e90a0-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="e90a0-107">No entanto, os botões A, B, X, Y e o gatilho squeeze não estão acessíveis no momento por meio do Gerenciador de entrada, a menos que você esteja usando SteamVR.</span><span class="sxs-lookup"><span data-stu-id="e90a0-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="e90a0-108">O suporte para as entradas adicionais de reverberação G2 estará disponível em um futuro próximo, portanto, lembre-se de verificar novamente!</span><span class="sxs-lookup"><span data-stu-id="e90a0-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="e90a0-109">Portando aplicativos existentes</span><span class="sxs-lookup"><span data-stu-id="e90a0-109">Porting existing applications</span></span>

<span data-ttu-id="e90a0-110">Se você já tiver um aplicativo existente que está desenvolvendo para headsets de imersão de realidade mista do Windows, confira nosso [Guia de portador](../porting-apps/porting-guides.md) e as seções de [configurações de projeto](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) para obter sugestões gerais.</span><span class="sxs-lookup"><span data-stu-id="e90a0-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="e90a0-111">Entrada de mapeamento</span><span class="sxs-lookup"><span data-stu-id="e90a0-111">Mapping input</span></span>

<span data-ttu-id="e90a0-112">Quando estiver pronto para colocar seu mapeamento de entrada em funcionamento para seus novos controladores, comece na seção [mapeamento de entrada](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) do guia de porta de imersão.</span><span class="sxs-lookup"><span data-stu-id="e90a0-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="e90a0-113">Instruções sobre como configurar entradas no Unity são detalhadas em [gestos e controladores de movimento](gestures-and-motion-controllers-in-unity.md), juntamente com um [botão completo e uma tabela de mapeamento de eixo](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) para referência.</span><span class="sxs-lookup"><span data-stu-id="e90a0-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="e90a0-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="e90a0-114">See also</span></span>
* [<span data-ttu-id="e90a0-115">Atualizar para o SteamVR</span><span class="sxs-lookup"><span data-stu-id="e90a0-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)