---
title: Movimento Leap do MRTK
description: Documentação a ser configurada para o Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Leap Motion,
ms.openlocfilehash: 44593713f08a00fa53325eebfae2cf9042d386be
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207468"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="a8e27-104">Como configurar o acompanhamento de mão do Leap Motion (por Ultraleap) no MRTK</span><span class="sxs-lookup"><span data-stu-id="a8e27-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="a8e27-105">Um [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) é necessário para usar esse provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="a8e27-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="a8e27-106">O leap Motion Provedor de Dados permite o acompanhamento de mão articulado para VR e pode ser útil para criação rápida de protótipos no editor.</span><span class="sxs-lookup"><span data-stu-id="a8e27-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="a8e27-107">O provedor de dados pode ser configurado para usar o Leap Motion Controller montado em um headset ou colocado em uma face de suporte.</span><span class="sxs-lookup"><span data-stu-id="a8e27-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="a8e27-109">Esse provedor pode ser usado no editor e no dispositivo enquanto estiver na plataforma autônoma.</span><span class="sxs-lookup"><span data-stu-id="a8e27-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="a8e27-110">Ele também pode ser usado no editor enquanto estiver na plataforma UWP, mas NÃO em um build UWP.</span><span class="sxs-lookup"><span data-stu-id="a8e27-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="a8e27-111">Versão do MRTK</span><span class="sxs-lookup"><span data-stu-id="a8e27-111">MRTK Version</span></span> | <span data-ttu-id="a8e27-112">Versões de módulos do Unity do Leap Motion com suporte</span><span class="sxs-lookup"><span data-stu-id="a8e27-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="a8e27-113">2.6.x</span><span class="sxs-lookup"><span data-stu-id="a8e27-113">2.6.x</span></span> | <span data-ttu-id="a8e27-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="a8e27-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="a8e27-115">2.7.x</span><span class="sxs-lookup"><span data-stu-id="a8e27-115">2.7.x</span></span>| <span data-ttu-id="a8e27-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1</span><span class="sxs-lookup"><span data-stu-id="a8e27-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="a8e27-117">Usando o acompanhamento de mão do Leap Motion (por Ultraleap) no MRTK</span><span class="sxs-lookup"><span data-stu-id="a8e27-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="a8e27-118">Importando o MRTK e os módulos do Unity do Leap Motion</span><span class="sxs-lookup"><span data-stu-id="a8e27-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="a8e27-119">Instale o [SDK do Leap Motion](https://developer.leapmotion.com/releases/?category=orion) mais recente se ele ainda não estiver instalado</span><span class="sxs-lookup"><span data-stu-id="a8e27-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="a8e27-120">Importe o **pacote Microsoft.MixedReality.Toolkit.Foundation** para o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="a8e27-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="a8e27-121">Baixar e importar a versão mais recente dos [Módulos do Unity do Leap Motion](https://developer.leapmotion.com/unity) para o projeto</span><span class="sxs-lookup"><span data-stu-id="a8e27-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="a8e27-122">Importar somente o pacote **principal** dentro dos módulos do Unity</span><span class="sxs-lookup"><span data-stu-id="a8e27-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="a8e27-123">Integre os módulos de movimento Leap do Unity com MRTK</span><span class="sxs-lookup"><span data-stu-id="a8e27-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="a8e27-124">Depois que os módulos do Unity estiverem no projeto, navegue até **Mixed Reality Toolkit**  >  **Leap Motion**  >  **integrar o LEAP Motion Unity modules**</span><span class="sxs-lookup"><span data-stu-id="a8e27-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="a8e27-125">A integração dos módulos do Unity ao MRTK adiciona 10 definições de assembly ao projeto e adiciona referências à definição do assembly **Microsoft. MixedReality. Toolkit. Providers. LeapMotion** .</span><span class="sxs-lookup"><span data-stu-id="a8e27-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="a8e27-126">Verifique se o Visual Studio está fechado.</span><span class="sxs-lookup"><span data-stu-id="a8e27-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="a8e27-128">Adicionando a Provedor de Dados de movimento Leap</span><span class="sxs-lookup"><span data-stu-id="a8e27-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="a8e27-129">Criar uma nova cena do Unity</span><span class="sxs-lookup"><span data-stu-id="a8e27-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="a8e27-130">Adicione MRTK à cena navegando até **Mixed Reality Toolkit**  >  **Adicionar à cena e configurar**</span><span class="sxs-lookup"><span data-stu-id="a8e27-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="a8e27-131">Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.</span><span class="sxs-lookup"><span data-stu-id="a8e27-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="a8e27-133">Selecionar o perfil de configuração de **entrada**</span><span class="sxs-lookup"><span data-stu-id="a8e27-133">Select the **Input** Configuration Profile</span></span>

    ![Perfil de configuração de entrada 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="a8e27-135">Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.</span><span class="sxs-lookup"><span data-stu-id="a8e27-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="a8e27-137">Abra a seção **provedores de dados de entrada** , selecione **Adicionar provedor de dados** na parte superior, um novo provedor de dados será adicionado no final da lista.</span><span class="sxs-lookup"><span data-stu-id="a8e27-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="a8e27-138">Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. LeapMotion. Input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="a8e27-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Adicionar Provedor de Dados](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="a8e27-140">Selecione **clonar** para alterar as configurações padrão de movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="a8e27-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="a8e27-142">A Provedor de Dados de movimento Leap contém a `LeapControllerOrientation` propriedade que é o local do controlador de movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="a8e27-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="a8e27-143">`LeapControllerOrientation.Headset` indica que o controlador está montado em um headset.</span><span class="sxs-lookup"><span data-stu-id="a8e27-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="a8e27-144">`LeapControllerOrientation.Desk` indica que o controlador é colocado simples no desk.</span><span class="sxs-lookup"><span data-stu-id="a8e27-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="a8e27-145">O valor padrão é definido como `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="a8e27-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="a8e27-146">Cada orientação do controlador contém propriedades de deslocamento:</span><span class="sxs-lookup"><span data-stu-id="a8e27-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="a8e27-147">As **propriedades de deslocamento** de orientação do headset espelham as propriedades de deslocamento no componente LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="a8e27-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="a8e27-148">O `LeapVRDeviceOffsetMode` tem três opções: Padrão, Deslocamento de Cabeça Manual e Transformação.</span><span class="sxs-lookup"><span data-stu-id="a8e27-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="a8e27-149">Se o modo de deslocamento for Padrão, um deslocamento não será aplicado ao Controlador de Movimento Bissexo.</span><span class="sxs-lookup"><span data-stu-id="a8e27-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="a8e27-150">O modo deslocamento de cabeça manual permite a modificação de três propriedades: `LeapVRDeviceOffsetY` e `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="a8e27-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="a8e27-151">Os valores de propriedade de deslocamento do eixo são aplicados ao posicionamento padrão do controlador.</span><span class="sxs-lookup"><span data-stu-id="a8e27-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="a8e27-152">O modo de deslocamento transformar contém `LeapVRDeviceOrigin` a propriedade Transformar que especifica uma nova origem para o Controlador de Movimento Bissextos.</span><span class="sxs-lookup"><span data-stu-id="a8e27-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="a8e27-153">A **orientação** De mesa contém `LeapControllerOffset` a propriedade que define a posição de âncora das mãos bissextivas da mesa.</span><span class="sxs-lookup"><span data-stu-id="a8e27-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="a8e27-154">O deslocamento é calculado em relação à posição da câmera principal e o valor padrão é (0,-0,2, 0,35) para garantir que as mãos apareçam na frente e na exibição da câmera.</span><span class="sxs-lookup"><span data-stu-id="a8e27-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="a8e27-155">As propriedades de deslocamento no perfil são aplicadas uma vez quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="a8e27-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="a8e27-156">Para modificar os valores durante o runtime, obter o Provedor de Serviços de Movimento Bissexdo da Gerenciador de Dispositivos:</span><span class="sxs-lookup"><span data-stu-id="a8e27-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="a8e27-157">`EnterPinchDistance` e `ExitPinchDistance` são os limites de distância para detecção de gestos de pinçar/tocar no ar.</span><span class="sxs-lookup"><span data-stu-id="a8e27-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="a8e27-158">O gesto de pinçamento é calculado medindo a distância entre a ponta do dedo indicador e a ponta do dedo indicador.</span><span class="sxs-lookup"><span data-stu-id="a8e27-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="a8e27-159">Para auportar um evento na entrada para baixo, o `EnterPinchDistance` padrão é definido como 0,02.</span><span class="sxs-lookup"><span data-stu-id="a8e27-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="a8e27-160">Para auportar um evento na entrada (saindo da pinçação), a distância padrão entre a ponta do dedo indicador e a dica de miniatura é 0,05.</span><span class="sxs-lookup"><span data-stu-id="a8e27-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="a8e27-161">`LeapControllerOrientation`: headset (padrão)</span><span class="sxs-lookup"><span data-stu-id="a8e27-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="a8e27-162">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="a8e27-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="a8e27-167">Testando o movimento Leap Provedor de Dados</span><span class="sxs-lookup"><span data-stu-id="a8e27-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="a8e27-168">Depois que o movimento Leap Provedor de Dados tiver sido adicionado ao perfil do sistema de entrada, pressione reproduzir, mova-o para frente do controlador de movimento Leap e você deverá ver a representação conjunta do lado.</span><span class="sxs-lookup"><span data-stu-id="a8e27-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="a8e27-169">Criando seu projeto</span><span class="sxs-lookup"><span data-stu-id="a8e27-169">Building your project</span></span>
    - <span data-ttu-id="a8e27-170">Navegue até o **arquivo > configurações de Build**</span><span class="sxs-lookup"><span data-stu-id="a8e27-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="a8e27-171">Somente compilações autônomas têm suporte se você estiver usando o Provedor de Dados de movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="a8e27-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="a8e27-172">Para obter instruções sobre como usar um headset de realidade mista do Windows para compilações autônomas, consulte [compilando e implantando MRTK (autônomo)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span><span class="sxs-lookup"><span data-stu-id="a8e27-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="a8e27-173">Obtendo as junções de mão</span><span class="sxs-lookup"><span data-stu-id="a8e27-173">Getting the hand joints</span></span>

<span data-ttu-id="a8e27-174">A obtenção de junções usando o movimento Leap Provedor de Dados é idêntica à recuperação conjunta da MRTK para uma mão articulada.</span><span class="sxs-lookup"><span data-stu-id="a8e27-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="a8e27-175">Para obter mais informações, consulte [controle à mão](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="a8e27-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="a8e27-176">Com MRTK em uma cena do Unity e o movimento Leap Provedor de Dados adicionado como uma entrada Provedor de Dados no perfil do sistema de entrada, crie um objeto de jogo vazio e anexe o script de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a8e27-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="a8e27-177">Esse script é um exemplo simples de como recuperar a pose do conjunto de Palm em uma mão de movimento bissexto.</span><span class="sxs-lookup"><span data-stu-id="a8e27-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="a8e27-178">Uma esfera segue a mão à esquerda enquanto um cubo segue a mão à direita.</span><span class="sxs-lookup"><span data-stu-id="a8e27-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="a8e27-179">Dica de fluxo de trabalho do editor do Unity</span><span class="sxs-lookup"><span data-stu-id="a8e27-179">Unity editor workflow tip</span></span>

<span data-ttu-id="a8e27-180">Usar o Provedor de Dados de movimento LEAP não exige um headset VR.</span><span class="sxs-lookup"><span data-stu-id="a8e27-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="a8e27-181">As alterações em um aplicativo MRTK podem ser testadas no editor com as mãos Leap sem um headset.</span><span class="sxs-lookup"><span data-stu-id="a8e27-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="a8e27-182">As mãos de movimento Leap aparecerão no editor, sem um headset VR conectado.</span><span class="sxs-lookup"><span data-stu-id="a8e27-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="a8e27-183">Se o estiver definido como Headset, o controlador leap Motion precisará ser mantido em uma mão com a `LeapControllerOrientation` câmera voltada para frente. </span><span class="sxs-lookup"><span data-stu-id="a8e27-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="a8e27-184">Se a câmera for movida usando chaves WASD no editor e o for `LeapControllerOrientation` **Headset**, as mãos não seguirão a câmera.</span><span class="sxs-lookup"><span data-stu-id="a8e27-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="a8e27-185">As mãos só seguirão o movimento da câmera se um headset vr estiver conectado enquanto o `LeapControllerOrientation` estiver definido como **Headset**.</span><span class="sxs-lookup"><span data-stu-id="a8e27-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="a8e27-186">As mãos do Leap seguirão o movimento da câmera no editor se `LeapControllerOrientation` o estiver definido como **Desk.**</span><span class="sxs-lookup"><span data-stu-id="a8e27-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="a8e27-187">Removendo o Leap Motion do projeto</span><span class="sxs-lookup"><span data-stu-id="a8e27-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="a8e27-188">Navegue até os **módulos** do Unity do  >  **Leap Motion Separados** do Leap Motion do Kit de Ferramentas de Realidade  >  **Misturada**</span><span class="sxs-lookup"><span data-stu-id="a8e27-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="a8e27-189">Permitir que o Unity atualize como referências **no arquivo Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** são modificadas nesta etapa</span><span class="sxs-lookup"><span data-stu-id="a8e27-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="a8e27-190">Fechar Unity</span><span class="sxs-lookup"><span data-stu-id="a8e27-190">Close Unity</span></span>
1. <span data-ttu-id="a8e27-191">Feche Visual Studio, se estiver aberto</span><span class="sxs-lookup"><span data-stu-id="a8e27-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="a8e27-192">Abra Explorador de Arquivos e navegue até a raiz do projeto unity do MRTK</span><span class="sxs-lookup"><span data-stu-id="a8e27-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="a8e27-193">Excluir o **diretório UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="a8e27-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="a8e27-194">Excluir o **diretório UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="a8e27-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="a8e27-195">Excluir o **arquivo UnityProjectName/Assets/Plugins/LeapMotion.meta**</span><span class="sxs-lookup"><span data-stu-id="a8e27-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="a8e27-196">Reabrir o Unity</span><span class="sxs-lookup"><span data-stu-id="a8e27-196">Reopen Unity</span></span>

<span data-ttu-id="a8e27-197">No Unity 2018.4, você pode observar que os erros ainda permanecem no console depois de excluir a Biblioteca e os Ativos do Leap Motion Core.</span><span class="sxs-lookup"><span data-stu-id="a8e27-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="a8e27-198">Se os erros são registrados após a reabertura, reinicie o Unity novamente.</span><span class="sxs-lookup"><span data-stu-id="a8e27-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="a8e27-199">Erros Comuns</span><span class="sxs-lookup"><span data-stu-id="a8e27-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="a8e27-200">O Leap Motion não foi integrado ao MRTK</span><span class="sxs-lookup"><span data-stu-id="a8e27-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="a8e27-201">Para testar se os Módulos do Unity do Leap Motion foram integrados ao MRTK:</span><span class="sxs-lookup"><span data-stu-id="a8e27-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="a8e27-202">Navegue até **Kit de Ferramentas de Realidade Misturada > utilitários > Leap Motion > verificar o status de integração**</span><span class="sxs-lookup"><span data-stu-id="a8e27-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="a8e27-203">Isso exibirá uma janela pop-up com uma mensagem sobre se os Módulos do Unity do Leap Motion foram integrados ou não ao MRTK.</span><span class="sxs-lookup"><span data-stu-id="a8e27-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="a8e27-204">Se a mensagem informar que os ativos não foram integrados:</span><span class="sxs-lookup"><span data-stu-id="a8e27-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="a8e27-205">Certifique-se de que os módulos do Unity de movimento Leap estejam no projeto</span><span class="sxs-lookup"><span data-stu-id="a8e27-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="a8e27-206">Verifique se a versão adicionada tem suporte, consulte a tabela na parte superior da página para obter as versões com suporte.</span><span class="sxs-lookup"><span data-stu-id="a8e27-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="a8e27-207">Experimente a **Mixed Reality Toolkit > Utilities > movimento leap > integrar módulos de movimento Leap**</span><span class="sxs-lookup"><span data-stu-id="a8e27-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="a8e27-208">Falha ao copiar HLAPI de vários participantes do assembly</span><span class="sxs-lookup"><span data-stu-id="a8e27-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="a8e27-209">Na importação dos ativos do Unity Core de movimento Leap, esse erro pode ser registrado:</span><span class="sxs-lookup"><span data-stu-id="a8e27-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="a8e27-210">**Solução**</span><span class="sxs-lookup"><span data-stu-id="a8e27-210">**Solution**</span></span>

- <span data-ttu-id="a8e27-211">Uma solução de curto prazo é reiniciar o Unity.</span><span class="sxs-lookup"><span data-stu-id="a8e27-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="a8e27-212">Consulte o [problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="a8e27-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="a8e27-213">Cena de exemplo de movimento Leap</span><span class="sxs-lookup"><span data-stu-id="a8e27-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="a8e27-214">A cena de exemplo usa o perfil DefaultLeapMotionConfiguration e determina se o projeto do Unity foi configurado corretamente para usar o Provedor de Dados de movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="a8e27-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="a8e27-215">A cena de exemplo está contida no pacote **Microsoft. MixedReality. Toolkit. examples** no diretório **MRTK/examples/demos/HandTracking/** .</span><span class="sxs-lookup"><span data-stu-id="a8e27-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="a8e27-216">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8e27-216">See also</span></span>

- [<span data-ttu-id="a8e27-217">Provedores de entrada</span><span class="sxs-lookup"><span data-stu-id="a8e27-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="a8e27-218">Acompanhamento à mão</span><span class="sxs-lookup"><span data-stu-id="a8e27-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
