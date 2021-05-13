---
title: LeapMotionMRTK
description: Documentação a ser configurada para o Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Leap Motion,
ms.openlocfilehash: ea9e257815116c364fe2f1e37ca3477ec56262cb
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852316"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="7e101-104">Como configurar o acompanhamento de mão do Leap Motion (por Ultraleap) no MRTK</span><span class="sxs-lookup"><span data-stu-id="7e101-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="7e101-105">Um [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) é necessário para usar esse provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="7e101-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="7e101-106">O leap Motion Provedor de Dados permite o acompanhamento de mão articulado para VR e pode ser útil para criação rápida de protótipos no editor.</span><span class="sxs-lookup"><span data-stu-id="7e101-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="7e101-107">O provedor de dados pode ser configurado para usar o Leap Motion Controller montado em um headset ou colocado em uma face de suporte.</span><span class="sxs-lookup"><span data-stu-id="7e101-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="7e101-109">Esse provedor pode ser usado no editor e no dispositivo enquanto estiver na plataforma autônoma.</span><span class="sxs-lookup"><span data-stu-id="7e101-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="7e101-110">Ele também pode ser usado no editor enquanto estiver na plataforma UWP, mas NÃO em um build UWP.</span><span class="sxs-lookup"><span data-stu-id="7e101-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

|<span data-ttu-id="7e101-111">Versões de módulos do Unity do Leap Motion com suporte</span><span class="sxs-lookup"><span data-stu-id="7e101-111">Leap Motion Unity Modules Versions Supported</span></span>|
|---|
|<span data-ttu-id="7e101-112">4.5.0</span><span class="sxs-lookup"><span data-stu-id="7e101-112">4.5.0</span></span>|
|<span data-ttu-id="7e101-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7e101-113">4.5.1</span></span>|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="7e101-114">Usando o acompanhamento de mão do Leap Motion (por Ultraleap) no MRTK</span><span class="sxs-lookup"><span data-stu-id="7e101-114">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="7e101-115">Importando o MRTK e os módulos do Unity do Leap Motion</span><span class="sxs-lookup"><span data-stu-id="7e101-115">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="7e101-116">Instale o [SDK do Leap Motion 4.0.0](https://developer.leapmotion.com/releases/?category=orion) se ele ainda não estiver instalado</span><span class="sxs-lookup"><span data-stu-id="7e101-116">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="7e101-117">Importe o **pacote Microsoft.MixedReality.Toolkit.Foundation** para o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="7e101-117">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="7e101-118">Baixar e importar a versão mais recente dos [Módulos do Unity do Leap Motion](https://developer.leapmotion.com/unity) para o projeto</span><span class="sxs-lookup"><span data-stu-id="7e101-118">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="7e101-119">Importar apenas o **pacote Core** dentro dos Módulos do Unity</span><span class="sxs-lookup"><span data-stu-id="7e101-119">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="7e101-120">Integrar os módulos do Leap Motion Unity ao MRTK</span><span class="sxs-lookup"><span data-stu-id="7e101-120">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="7e101-121">Depois que os Módulos do Unity estão no projeto, navegue até **Módulos** do Leap Motion do Leap Motion do Kit de Ferramentas de Realidade  >    >  **Misturada**</span><span class="sxs-lookup"><span data-stu-id="7e101-121">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="7e101-122">A integração dos Módulos do Unity ao MRTK adiciona 10 definições de assembly ao projeto e adiciona referências à definição de assembly **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.**</span><span class="sxs-lookup"><span data-stu-id="7e101-122">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="7e101-123">Verifique se o Visual Studio está fechado.</span><span class="sxs-lookup"><span data-stu-id="7e101-123">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="7e101-125">Adicionando a Provedor de Dados de movimento Leap</span><span class="sxs-lookup"><span data-stu-id="7e101-125">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="7e101-126">Criar uma nova cena do Unity</span><span class="sxs-lookup"><span data-stu-id="7e101-126">Create a new Unity scene</span></span>
    - <span data-ttu-id="7e101-127">Adicione MRTK à cena navegando até **Mixed Reality Toolkit**  >  **Adicionar à cena e configurar**</span><span class="sxs-lookup"><span data-stu-id="7e101-127">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="7e101-128">Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.</span><span class="sxs-lookup"><span data-stu-id="7e101-128">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="7e101-130">Selecionar o perfil de configuração de **entrada**</span><span class="sxs-lookup"><span data-stu-id="7e101-130">Select the **Input** Configuration Profile</span></span>

    ![Perfil de configuração de entrada 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="7e101-132">Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.</span><span class="sxs-lookup"><span data-stu-id="7e101-132">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="7e101-134">Abra a seção **provedores de dados de entrada** , selecione **Adicionar provedor de dados** na parte superior, um novo provedor de dados será adicionado no final da lista.</span><span class="sxs-lookup"><span data-stu-id="7e101-134">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="7e101-135">Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. LeapMotion. Input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="7e101-135">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Adicionar Provedor de Dados](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="7e101-137">Selecione **clonar** para alterar as configurações padrão de movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="7e101-137">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="7e101-139">A Provedor de Dados de movimento Leap contém a `LeapControllerOrientation` propriedade que é o local do controlador de movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="7e101-139">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="7e101-140">`LeapControllerOrientation.Headset` indica que o controlador está montado em um headset.</span><span class="sxs-lookup"><span data-stu-id="7e101-140">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="7e101-141">`LeapControllerOrientation.Desk` indica que o controlador é colocado plano na mesa.</span><span class="sxs-lookup"><span data-stu-id="7e101-141">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="7e101-142">O valor padrão é definido como `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="7e101-142">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="7e101-143">Cada orientação de controlador contém propriedades de deslocamento:</span><span class="sxs-lookup"><span data-stu-id="7e101-143">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="7e101-144">As **propriedades de deslocamento** de orientação do headset espelham as propriedades de deslocamento no componente LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="7e101-144">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="7e101-145">O `LeapVRDeviceOffsetMode` tem três opções: Padrão, Deslocamento de Cabeça Manual e Transformação.</span><span class="sxs-lookup"><span data-stu-id="7e101-145">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="7e101-146">Se o modo de deslocamento for Padrão, um deslocamento não será aplicado ao Controlador de Movimento Bissexo.</span><span class="sxs-lookup"><span data-stu-id="7e101-146">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="7e101-147">O modo deslocamento de cabeça manual permite a modificação de três propriedades: `LeapVRDeviceOffsetY` e `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="7e101-147">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="7e101-148">Os valores de propriedade de deslocamento do eixo são aplicados ao posicionamento padrão do controlador.</span><span class="sxs-lookup"><span data-stu-id="7e101-148">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="7e101-149">O modo de deslocamento transformar contém `LeapVRDeviceOrigin` a propriedade Transformar que especifica uma nova origem para o Controlador de Movimento Bissextos.</span><span class="sxs-lookup"><span data-stu-id="7e101-149">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="7e101-150">A **orientação** De mesa contém `LeapControllerOffset` a propriedade que define a posição de âncora das mãos bissextivas da mesa.</span><span class="sxs-lookup"><span data-stu-id="7e101-150">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="7e101-151">O deslocamento é calculado em relação à posição da câmera principal e o valor padrão é (0,-0,2, 0,35) para garantir que as mãos apareçam na frente e na exibição da câmera.</span><span class="sxs-lookup"><span data-stu-id="7e101-151">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="7e101-152">As propriedades de deslocamento no perfil são aplicadas uma vez quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="7e101-152">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="7e101-153">Para modificar os valores durante o runtime, obter o Provedor de Serviços de Movimento Bissexdo da Gerenciador de Dispositivos:</span><span class="sxs-lookup"><span data-stu-id="7e101-153">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="7e101-154">`EnterPinchDistance` e `ExitPinchDistance` são os limites de distância para detecção de gestos de pinçar/tocar no ar.</span><span class="sxs-lookup"><span data-stu-id="7e101-154">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="7e101-155">O gesto de pinçamento é calculado medindo a distância entre a ponta do dedo indicador e a ponta do dedo indicador.</span><span class="sxs-lookup"><span data-stu-id="7e101-155">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="7e101-156">Para auportar um evento na entrada para baixo, o `EnterPinchDistance` padrão é definido como 0,02.</span><span class="sxs-lookup"><span data-stu-id="7e101-156">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="7e101-157">Para auportar um evento na entrada (saindo da pinçação), a distância padrão entre a ponta do dedo indicador e a dica de miniatura é 0,05.</span><span class="sxs-lookup"><span data-stu-id="7e101-157">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="7e101-158">`LeapControllerOrientation`: headset (padrão)</span><span class="sxs-lookup"><span data-stu-id="7e101-158">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="7e101-159">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="7e101-159">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="7e101-164">Testando o movimento Leap Provedor de Dados</span><span class="sxs-lookup"><span data-stu-id="7e101-164">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="7e101-165">Depois que o movimento Leap Provedor de Dados tiver sido adicionado ao perfil do sistema de entrada, pressione reproduzir, mova-o para frente do controlador de movimento Leap e você deverá ver a representação conjunta do lado.</span><span class="sxs-lookup"><span data-stu-id="7e101-165">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="7e101-166">Criando seu projeto</span><span class="sxs-lookup"><span data-stu-id="7e101-166">Building your project</span></span>
    - <span data-ttu-id="7e101-167">Navegue até o **arquivo > configurações de Build**</span><span class="sxs-lookup"><span data-stu-id="7e101-167">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="7e101-168">Somente compilações autônomas têm suporte se você estiver usando o Provedor de Dados de movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="7e101-168">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="7e101-169">Para obter instruções sobre como usar um headset de realidade mista do Windows para compilações autônomas, consulte [compilando e implantando MRTK (autônomo)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span><span class="sxs-lookup"><span data-stu-id="7e101-169">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="7e101-170">Obtendo as junções de mão</span><span class="sxs-lookup"><span data-stu-id="7e101-170">Getting the hand joints</span></span>

<span data-ttu-id="7e101-171">A obtenção de junções usando o movimento Leap Provedor de Dados é idêntica à recuperação conjunta da MRTK para uma mão articulada.</span><span class="sxs-lookup"><span data-stu-id="7e101-171">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="7e101-172">Para obter mais informações, consulte [controle à mão](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="7e101-172">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="7e101-173">Com MRTK em uma cena do Unity e o movimento Leap Provedor de Dados adicionado como uma entrada Provedor de Dados no perfil do sistema de entrada, crie um objeto de jogo vazio e anexe o script de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7e101-173">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="7e101-174">Esse script é um exemplo simples de como recuperar a pose do conjunto de Palm em uma mão de movimento bissexto.</span><span class="sxs-lookup"><span data-stu-id="7e101-174">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="7e101-175">Uma esfera segue a mão à esquerda enquanto um cubo segue a mão à direita.</span><span class="sxs-lookup"><span data-stu-id="7e101-175">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="7e101-176">Dica de fluxo de trabalho do editor do Unity</span><span class="sxs-lookup"><span data-stu-id="7e101-176">Unity editor workflow tip</span></span>

<span data-ttu-id="7e101-177">Usar o Provedor de Dados de movimento LEAP não exige um headset VR.</span><span class="sxs-lookup"><span data-stu-id="7e101-177">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="7e101-178">As alterações em um aplicativo MRTK podem ser testadas no editor com as mãos Leap sem um headset.</span><span class="sxs-lookup"><span data-stu-id="7e101-178">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="7e101-179">As mãos de movimento Leap aparecerão no editor, sem um headset VR conectado.</span><span class="sxs-lookup"><span data-stu-id="7e101-179">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="7e101-180">Se o `LeapControllerOrientation` for definido como **Headset**, o controlador de movimento Leap precisará ser mantido com uma mão com a câmera voltada para frente.</span><span class="sxs-lookup"><span data-stu-id="7e101-180">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="7e101-181">Se a câmera for movida usando chaves WASD no editor e o `LeapControllerOrientation` fone de **ouvido**, as mãos não seguirão a câmera.</span><span class="sxs-lookup"><span data-stu-id="7e101-181">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="7e101-182">As mãos seguirão apenas a movimentação da câmera se um headset de VR estiver conectado enquanto o `LeapControllerOrientation` estiver definido como **Headset**.</span><span class="sxs-lookup"><span data-stu-id="7e101-182">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="7e101-183">As mãos de salto seguirão o movimento da câmera no editor se o `LeapControllerOrientation` estiver definido como **escrivaninha**.</span><span class="sxs-lookup"><span data-stu-id="7e101-183">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="7e101-184">Removendo o Leap Motion do projeto</span><span class="sxs-lookup"><span data-stu-id="7e101-184">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="7e101-185">Navegue até os **módulos** do Unity do  >  **Leap Motion Separados** do Leap Motion do Kit de Ferramentas de Realidade  >  **Misturada**</span><span class="sxs-lookup"><span data-stu-id="7e101-185">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="7e101-186">Permitir que o Unity atualize como referências **no arquivo Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** são modificadas nesta etapa</span><span class="sxs-lookup"><span data-stu-id="7e101-186">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="7e101-187">Fechar Unity</span><span class="sxs-lookup"><span data-stu-id="7e101-187">Close Unity</span></span>
1. <span data-ttu-id="7e101-188">Feche Visual Studio, se estiver aberto</span><span class="sxs-lookup"><span data-stu-id="7e101-188">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="7e101-189">Abra Explorador de Arquivos e navegue até a raiz do projeto unity do MRTK</span><span class="sxs-lookup"><span data-stu-id="7e101-189">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="7e101-190">Excluir o **diretório UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="7e101-190">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="7e101-191">Excluir o **diretório UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="7e101-191">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="7e101-192">Excluir o **arquivo UnityProjectName/Assets/Plugins/LeapMotion.meta**</span><span class="sxs-lookup"><span data-stu-id="7e101-192">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="7e101-193">Reabrir o Unity</span><span class="sxs-lookup"><span data-stu-id="7e101-193">Reopen Unity</span></span>

<span data-ttu-id="7e101-194">No Unity 2018.4, você pode observar que os erros ainda permanecem no console depois de excluir a Biblioteca e os Ativos do Leap Motion Core.</span><span class="sxs-lookup"><span data-stu-id="7e101-194">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="7e101-195">Se os erros são registrados após a reabertura, reinicie o Unity novamente.</span><span class="sxs-lookup"><span data-stu-id="7e101-195">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="7e101-196">Erros Comuns</span><span class="sxs-lookup"><span data-stu-id="7e101-196">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="7e101-197">O Leap Motion não foi integrado ao MRTK</span><span class="sxs-lookup"><span data-stu-id="7e101-197">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="7e101-198">Para testar se os Módulos do Unity do Leap Motion foram integrados ao MRTK:</span><span class="sxs-lookup"><span data-stu-id="7e101-198">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="7e101-199">Navegue até **Kit de Ferramentas de Realidade Misturada > utilitários > Leap Motion > verificar o status de integração**</span><span class="sxs-lookup"><span data-stu-id="7e101-199">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="7e101-200">Isso exibirá uma janela pop-up com uma mensagem sobre se os Módulos do Unity do Leap Motion foram integrados ou não ao MRTK.</span><span class="sxs-lookup"><span data-stu-id="7e101-200">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="7e101-201">Se a mensagem diz que os ativos não foram integrados:</span><span class="sxs-lookup"><span data-stu-id="7e101-201">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="7e101-202">Certifique-se de que os Módulos do Unity do Leap Motion estão no projeto</span><span class="sxs-lookup"><span data-stu-id="7e101-202">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="7e101-203">Certifique-se de que a versão adicionada tenha suporte, consulte a tabela na parte superior da página para ver as versões com suporte.</span><span class="sxs-lookup"><span data-stu-id="7e101-203">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="7e101-204">Experimente **o Kit de Ferramentas de Realidade Misturada > utilitários > Leap Motion > integrar módulos do Leap Motion Unity**</span><span class="sxs-lookup"><span data-stu-id="7e101-204">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="7e101-205">Falha ao copiar HLAPI de vários participantes do assembly</span><span class="sxs-lookup"><span data-stu-id="7e101-205">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="7e101-206">Na importação dos ativos do Unity Core de movimento Leap, esse erro pode ser registrado:</span><span class="sxs-lookup"><span data-stu-id="7e101-206">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="7e101-207">**Solução**</span><span class="sxs-lookup"><span data-stu-id="7e101-207">**Solution**</span></span>

- <span data-ttu-id="7e101-208">Uma solução de curto prazo é reiniciar o Unity.</span><span class="sxs-lookup"><span data-stu-id="7e101-208">A short term solution is to restart Unity.</span></span> <span data-ttu-id="7e101-209">Consulte o [problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="7e101-209">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="7e101-210">Cena de exemplo de movimento Leap</span><span class="sxs-lookup"><span data-stu-id="7e101-210">Leap Motion Example Scene</span></span>

<span data-ttu-id="7e101-211">A cena de exemplo usa o perfil DefaultLeapMotionConfiguration e determina se o projeto do Unity foi configurado corretamente para usar o Provedor de Dados de movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="7e101-211">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="7e101-212">A cena de exemplo está contida no pacote **Microsoft. MixedReality. Toolkit. examples** no diretório **MRTK/examples/demos/HandTracking/** .</span><span class="sxs-lookup"><span data-stu-id="7e101-212">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="7e101-213">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e101-213">See also</span></span>

<span data-ttu-id="7e101-214">-[Provedores](../features/input/input-providers.md) 
- de entrada [Acompanhamento à mão](../features/input/hand-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="7e101-214">-[Input Providers](../features/input/input-providers.md)
-[Hand Tracking](../features/input/hand-tracking.md)</span></span>
