---
title: Acompanhamento de perguntas frequentes
description: Acompanhamento da solução de problemas de realidade mista do Windows que vai além da nossa documentação de suporte de consumidor padrão.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, solução de problemas, erros, ajuda, suporte, rastreamento
ms.openlocfilehash: 2634b95cf876a5b540710f80d3dd7f9d48b3bad9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725827"
---
# <a name="tracking-faqs"></a><span data-ttu-id="2286c-104">Acompanhamento de perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="2286c-104">Tracking FAQs</span></span>

## <a name="my-headset-has-stopped-tracking"></a><span data-ttu-id="2286c-105">Meu Headset parou o acompanhamento</span><span class="sxs-lookup"><span data-stu-id="2286c-105">My headset has stopped tracking</span></span>

<span data-ttu-id="2286c-106">Verifique se as luzes estão acesas e se não há nada obstruindo as câmeras de rastreamento internas na frente do headset.</span><span class="sxs-lookup"><span data-stu-id="2286c-106">Make sure the lights are on, and that there isn't anything obstructing the inside-out tracking cameras on the front of your headset.</span></span> <span data-ttu-id="2286c-107">Se o rastreamento for perdido, pode levar alguns segundos para retomar.</span><span class="sxs-lookup"><span data-stu-id="2286c-107">If tracking is lost, it can take a few seconds to resume.</span></span> <span data-ttu-id="2286c-108">Reiniciar o portal de realidade mista do Windows está o acompanhamento não é reiniciado.</span><span class="sxs-lookup"><span data-stu-id="2286c-108">Restart the Windows Mixed Reality Portal is tracking doesn't restart.</span></span>

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a><span data-ttu-id="2286c-109">Posso examinar, mas não posso traduzir (estou preso por 3DOF)</span><span class="sxs-lookup"><span data-stu-id="2286c-109">I can look around but I can't translate (I'm stuck in 3DOF)</span></span>

<span data-ttu-id="2286c-110">Isso significa que o sistema de controle não pode gerar pose ou o aplicativo foi interrompido usando novos dados de pose a serem renderizados.</span><span class="sxs-lookup"><span data-stu-id="2286c-110">This means that the tracking system can't generate pose, or the application has stopped using new pose data to render.</span></span> <span data-ttu-id="2286c-111">Para corrigir o problema:</span><span class="sxs-lookup"><span data-stu-id="2286c-111">To fix the issue:</span></span>

* <span data-ttu-id="2286c-112">Verifique se a sala tem luz suficiente.</span><span class="sxs-lookup"><span data-stu-id="2286c-112">Make sure the room has enough light.</span></span>
* <span data-ttu-id="2286c-113">Verifique se a sala tem detalhes suficientes para acompanhar.</span><span class="sxs-lookup"><span data-stu-id="2286c-113">Make sure the room has enough details to track.</span></span>
* <span data-ttu-id="2286c-114">Desconecte o dispositivo, feche a realidade mista do Windows e conecte o dispositivo novamente.</span><span class="sxs-lookup"><span data-stu-id="2286c-114">Unplug the device, close Windows Mixed Reality, and plug in the device again.</span></span>
* <span data-ttu-id="2286c-115">Se a mensagem persistir, contate o atendimento [ao cliente](https://support.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="2286c-115">If the message persists, contact [customer support](https://support.microsoft.com/)</span></span>

## <a name="the-view-in-the-hmd-is-frozen"></a><span data-ttu-id="2286c-116">A exibição no HMD é congelada</span><span class="sxs-lookup"><span data-stu-id="2286c-116">The view in the HMD is frozen</span></span>

<span data-ttu-id="2286c-117">Isso geralmente significa que o aplicativo ou um componente de nível de sistema falhou.</span><span class="sxs-lookup"><span data-stu-id="2286c-117">This usually means the application or a system level component has failed.</span></span> <span data-ttu-id="2286c-118">Tente:</span><span class="sxs-lookup"><span data-stu-id="2286c-118">Try to:</span></span>

1. <span data-ttu-id="2286c-119">Pressione o botão "página inicial" para sair do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2286c-119">Press the "home" button to leave the application.</span></span>
2. <span data-ttu-id="2286c-120">Desconecte o dispositivo, feche o MRP e conecte o dispositivo novamente.</span><span class="sxs-lookup"><span data-stu-id="2286c-120">Unplug the device, close MRP, and plug the device back in.</span></span>
3. <span data-ttu-id="2286c-121">Reinicie o computador.</span><span class="sxs-lookup"><span data-stu-id="2286c-121">Restart the PC.</span></span>

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a><span data-ttu-id="2286c-122">O mundo brevemente froze e se inverteu de cabeça para baixo antes de retornar ao normal</span><span class="sxs-lookup"><span data-stu-id="2286c-122">The world briefly froze and tilted or flipped upside down before returning to normal</span></span>

<span data-ttu-id="2286c-123">Isso pode ser causado por um aplicativo ou componente no nível do sistema que está atingindo um erro fatal ou uma falta temporária de memória ou recursos de CPU.</span><span class="sxs-lookup"><span data-stu-id="2286c-123">This could be caused by an application or system level component hitting a fatal error or a temporary lack of memory or CPU resources.</span></span> <span data-ttu-id="2286c-124">Para verificar:</span><span class="sxs-lookup"><span data-stu-id="2286c-124">To check:</span></span>

1. <span data-ttu-id="2286c-125">Abra o Gerenciador de tarefas e verifique se pelo menos 20% da CPU está livre, 400 MB de memória está disponível e a e/s de disco deve estar abaixo de 80%.</span><span class="sxs-lookup"><span data-stu-id="2286c-125">Open Task Manager and ensure that at least 20% of the CPU is free, 400 MB of memory is available and disk IO should be below 80%.</span></span>
2. <span data-ttu-id="2286c-126">Vá para **Visualizador de Eventos > logs do Windows > aplicativo** para procurar quaisquer erros em vez da hora do congelamento.</span><span class="sxs-lookup"><span data-stu-id="2286c-126">Go to **Event Viewer > Windows Logs > Application** to look for any errors from around the time of the freeze.</span></span> <span data-ttu-id="2286c-127">Procure qualquer coisa que se refira a sensores do HoloLens, realidade misturada ou o aplicativo que você estava executando em todo esse tempo.</span><span class="sxs-lookup"><span data-stu-id="2286c-127">Look for anything that refers to HoloLens sensors, Mixed Reality, or the application that you were running around that time.</span></span> <span data-ttu-id="2286c-128">Esses logs podem explicar o que causou a falha.</span><span class="sxs-lookup"><span data-stu-id="2286c-128">Those logs might explain what caused the failure.</span></span>
3. <span data-ttu-id="2286c-129">Reinicie o PC se o problema persistir.</span><span class="sxs-lookup"><span data-stu-id="2286c-129">Restart the PC if the problem persists.</span></span>

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a><span data-ttu-id="2286c-130">O mundo se inverteu de cabeça momentaneamente e retornou ao normal</span><span class="sxs-lookup"><span data-stu-id="2286c-130">The world flipped upside down momentarily and returned to normal</span></span>

<span data-ttu-id="2286c-131">Isso geralmente é causado por erros na obtenção de dados de sensor do headset para informar os algoritmos de controle.</span><span class="sxs-lookup"><span data-stu-id="2286c-131">This is typically caused by errors in obtaining sensor data from the headset to inform the tracking algorithms.</span></span> <span data-ttu-id="2286c-132">Se isso ocorrer com frequência:</span><span class="sxs-lookup"><span data-stu-id="2286c-132">If this happens frequently:</span></span>

1. <span data-ttu-id="2286c-133">Conecte o headset em uma porta USB 3,0 diferente.</span><span class="sxs-lookup"><span data-stu-id="2286c-133">Plug the headset into a different USB 3.0 port.</span></span>
2. <span data-ttu-id="2286c-134">Conecte o headset diretamente no PC, em vez de em um hub USB 3,0.</span><span class="sxs-lookup"><span data-stu-id="2286c-134">Plug the headset directly into the PC rather than into a USB 3.0 hub.</span></span>
3. <span data-ttu-id="2286c-135">Se o problema persistir, entre em contato com o atendimento [ao cliente](https://support.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="2286c-135">If the problem persists, contact [customer support](https://support.microsoft.com/).</span></span>

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a><span data-ttu-id="2286c-136">O mundo está inclinado, mas posso navegar e percorrer na realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="2286c-136">The world is tilted but I can navigate and walk around in Windows Mixed Reality</span></span>

<span data-ttu-id="2286c-137">Se os erros de dados do sensor forem registrados nos dados do ambiente em seu computador, isso poderá fazer com que a realidade mista do Windows pareça inclinada, às vezes permanentemente.</span><span class="sxs-lookup"><span data-stu-id="2286c-137">If sensor data errors are recorded into the environment data on your PC, it can cause Windows Mixed Reality to appear tilted, sometimes permanently.</span></span> <span data-ttu-id="2286c-138">Para corrigir isso:</span><span class="sxs-lookup"><span data-stu-id="2286c-138">To fix this:</span></span>

1. <span data-ttu-id="2286c-139">Desconecte o headset, feche a realidade mista do Windows e conecte o headset novamente.</span><span class="sxs-lookup"><span data-stu-id="2286c-139">Unplug the headset, close Windows Mixed Reality and plug the headset back in.</span></span>
2. <span data-ttu-id="2286c-140">Reinicie o computador.</span><span class="sxs-lookup"><span data-stu-id="2286c-140">Restart the PC.</span></span>
3. <span data-ttu-id="2286c-141">Apague os dados do seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="2286c-141">Clear your environment data.</span></span>