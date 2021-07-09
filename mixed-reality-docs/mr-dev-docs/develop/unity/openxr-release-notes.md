---
title: Notas de versão do plug-in OpenXR de Realidade Misturada
description: Fique por dentro das últimas notas de versão e atualizações do plug-in OpenXR de Realidade Misturada.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394626"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="cdaf0-104">Notas de versão do plug-in OpenXR de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="cdaf0-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="cdaf0-105">1.0.0 - Versão atual</span><span class="sxs-lookup"><span data-stu-id="cdaf0-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="cdaf0-106">Correção de um bug em que um XRAnchorSubsystem sempre foi iniciado na inicialização do aplicativo, independentemente do ARAnchorManager presente.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="cdaf0-107">Um bug onde o modo de reprojeção não funcionou corretamente foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="cdaf0-108">1.0.0-preview.2 - 2021-06-14</span><span class="sxs-lookup"><span data-stu-id="cdaf0-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="cdaf0-109">Depende do plug-in OpenXR 1.2.2 do Unity.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="cdaf0-110">Os recursos de Comunicação Remota Holográfica foram alterados para grupos de recursos individuais.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="cdaf0-111">Um bug onde "Aplicar configurações de projeto do HoloLens 2" altera o espaço de cores do projeto foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="cdaf0-112">Isso não é mais necessário após o plug-in 1.2.0 OpenXR do Unity.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="cdaf0-113">Um bug onde um dispositivo de entrada é conectado sem desconectar após o aplicativo ser suspenso e retomado foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="cdaf0-114">Suporte adicionado para detectar plug-in e estados de acompanhamento atuais via ARSession.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="cdaf0-115">Um bug onde o "Plano Padrão AR" ARFoundation pré-fabricado não estaria visível foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="cdaf0-116">1.0.0-preview.1 - 2021-06-02</span><span class="sxs-lookup"><span data-stu-id="cdaf0-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="cdaf0-117">Dá suporte a extensões MSFT de reconhecimento de cena do OpenXR em vez de extensões de visualização.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="cdaf0-118">A detecção de plano no HoloLens 2 não requer mais versões prévias dos tempos de execução OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="cdaf0-119">0.9.5 - 2021-05-21</span><span class="sxs-lookup"><span data-stu-id="cdaf0-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="cdaf0-120">Depende do Plug-in OpenXR 1.2.0 do Unity</span><span class="sxs-lookup"><span data-stu-id="cdaf0-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="cdaf0-121">Adaptado para a nova interface do usuário do recurso (no Plug-in 1.2.0 do OpenXR) para configuração.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="cdaf0-122">Um bug onde o provedor da câmera localizável não estava cancelando o registro corretamente foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="cdaf0-123">Alguns usos extras de [Preserve] foram limpos.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="cdaf0-124">Atualize o nome "HP Reverb G2 Controller (OpenXR)" na interface do usuário do sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="cdaf0-125">0.9.4 - 2021-05-20</span><span class="sxs-lookup"><span data-stu-id="cdaf0-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="cdaf0-126">Depende do Plug-in OpenXR 1.2.0 do Unity.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="cdaf0-127">Uma API do C# nova foi adicionada para obter o modelo de glTF do controlador de movimentos.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="cdaf0-128">Uma API do C# nova foi adicionada para obter as configurações de exibição habilitadas e definir as configurações de reprojeção.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="cdaf0-129">Uma API do C# nova foi adicionada para definir configurações adicionais para malhas de computação com XRMeshSubsystem.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="cdaf0-130">Uma API do C# nova foi adicionada para configurar e assinar eventos de reconhecimento de gestos.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="cdaf0-131">Windows->XR->Diálogo das configurações de Comunicação Remota do Editor adicionado.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="cdaf0-132">Suporte adicionado à ARM para aplicativos HoloLens UWP.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="cdaf0-133">0.9.3 - 2021-04-29</span><span class="sxs-lookup"><span data-stu-id="cdaf0-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="cdaf0-134">Um bug onde a conexão remota Holographic não é confiável foi corrigido</span><span class="sxs-lookup"><span data-stu-id="cdaf0-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="cdaf0-135">Um bug onde o desempenho de renderização VR está abaixo do ideal após a atualização para o plug-in OpenXR 1.1.1 do Unity foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="cdaf0-136">0.9.2 - 2021-04-21</span><span class="sxs-lookup"><span data-stu-id="cdaf0-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="cdaf0-137">A detecção de plano no HoloLens 2 na versão 0.9.1 do plug-in funcionará com a versão 105 do tempo de execução da verão prévia do OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="cdaf0-138">A detecção de plano no HoloLens 2 na versão 0.9.2 do plug-in funcionará com a versão 106 do tempo de execução da verão prévia do OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="cdaf0-139">Foram removidos alguns retornos de chamada não utilizados do Inputprovider para evitar que chamadas como XRInputSubsystem.\* GetTrackingOriginMode (que não são gerenciadas pelo nosso sistema de entrada) retornem com êxito com valores enganosos.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="cdaf0-140">Divida a versão preterida do XRAnchorStore em seu próprio arquivo para impedir o aviso do console do Unity.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="cdaf0-141">0.9.1 - 2021-04-20</span><span class="sxs-lookup"><span data-stu-id="cdaf0-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="cdaf0-142">Depende do Plug-in OpenXR 1.1.1 do Unity.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="cdaf0-143">Suporte adicionado ao aplicativo de Comunicação Remota Holográfica para a plataforma UWP.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="cdaf0-144">Corrija a UnityException onde XRAnchorStore estava tentando obter uma instância de configurações fora da thread principal.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="cdaf0-145">0.9.0 - 2021-03-29</span><span class="sxs-lookup"><span data-stu-id="cdaf0-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="cdaf0-146">Suporte adicionado ao mapeamento espacial por meio do XRMeshSubsystem e ARMeshManager.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="cdaf0-147">Uma API do C# nova foi adicionada para obter identificadores de OpenXR para dar suporte a outros pacotes do Unity que consomem extensões OpenXR.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="cdaf0-148">Uma API do C# nova foi adicionada à interoperabilidade com Windows. APIs de Percepção para dar suporte a outros pacotes do Unity consumindo APIs WinRT de Percepção.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="cdaf0-149">Perfis de interação removidos dos recursos necessários no conjunto de recursos do Windows Mixed Reality, para que os desenvolvedores possam escolher os controladores de movimento com os quais eles testaram.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="cdaf0-150">Validador de recursos de comunicação remota do editor do Holographic adicionado para ajudar os usuários a configurar corretamente a comunicação remota do editor.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="cdaf0-151">Um bug onde o editor do Unity falha ao sair do modo de comunicação remota do editor de Holographic após a falha de conexão foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="cdaf0-152">Um bug onde texturas alfa não pré-multiplicadas levam a um desempenho abaixo do ideal no HoloLens 2 foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="cdaf0-153">Um bug onde o acompanhamento da mão não estava localizado corretamente quando a origem da cena estava no nível do chão foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="cdaf0-154">Um bug onde o acompanhamento de malha à mão desaparece após sair e carregar uma nova cena foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="cdaf0-155">Um bug onde o provedor de câmera localizável não foi limpo corretamente foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="cdaf0-156">Namespace da API XRAnchorStore revisado para Microsoft.MixedReality.OpenXR.</span><span class="sxs-lookup"><span data-stu-id="cdaf0-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>