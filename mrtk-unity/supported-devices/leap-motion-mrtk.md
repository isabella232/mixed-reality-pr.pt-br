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
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Como configurar o acompanhamento de mão do Leap Motion (por Ultraleap) no MRTK

Um [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) é necessário para usar esse provedor de dados.

O leap Motion Provedor de Dados permite o acompanhamento de mão articulado para VR e pode ser útil para criação rápida de protótipos no editor.  O provedor de dados pode ser configurado para usar o Leap Motion Controller montado em um headset ou colocado em uma face de suporte.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Esse provedor pode ser usado no editor e no dispositivo enquanto estiver na plataforma autônoma.  Ele também pode ser usado no editor enquanto estiver na plataforma UWP, mas NÃO em um build UWP.

| Versão do MRTK | Versões de módulos do Unity do Leap Motion com suporte |
| --- | --- |
|2.6.x | 4.5.0, 4.5.1|
|2.7.x| 4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Usando o acompanhamento de mão do Leap Motion (por Ultraleap) no MRTK

1. Importando o MRTK e os módulos do Unity do Leap Motion
    - Instale o [SDK do Leap Motion](https://developer.leapmotion.com/releases/?category=orion) mais recente se ele ainda não estiver instalado
    - Importe o **pacote Microsoft.MixedReality.Toolkit.Foundation** para o projeto do Unity.
    - Baixar e importar a versão mais recente dos [Módulos do Unity do Leap Motion](https://developer.leapmotion.com/unity) para o projeto
        - Importar somente o pacote **principal** dentro dos módulos do Unity

1. Integre os módulos de movimento Leap do Unity com MRTK
    - Depois que os módulos do Unity estiverem no projeto, navegue até **Mixed Reality Toolkit**  >  **Leap Motion**  >  **integrar o LEAP Motion Unity modules**
    > [!NOTE]
    > A integração dos módulos do Unity ao MRTK adiciona 10 definições de assembly ao projeto e adiciona referências à definição do assembly **Microsoft. MixedReality. Toolkit. Providers. LeapMotion** . Verifique se o Visual Studio está fechado.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Adicionando a Provedor de Dados de movimento Leap
    - Criar uma nova cena do Unity
    - Adicione MRTK à cena navegando até **Mixed Reality Toolkit**  >  **Adicionar à cena e configurar**
    - Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - Selecionar o perfil de configuração de **entrada**

    ![Perfil de configuração de entrada 1](../images/cross-platform/InputConfigurationProfile.png)

    - Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - Abra a seção **provedores de dados de entrada** , selecione **Adicionar provedor de dados** na parte superior, um novo provedor de dados será adicionado no final da lista.  Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. LeapMotion. Input > LeapMotionDeviceManager**

    ![Leap Adicionar Provedor de Dados](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Selecione **clonar** para alterar as configurações padrão de movimento Leap.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - A Provedor de Dados de movimento Leap contém a `LeapControllerOrientation` propriedade que é o local do controlador de movimento Leap. `LeapControllerOrientation.Headset` indica que o controlador está montado em um headset. `LeapControllerOrientation.Desk` indica que o controlador é colocado simples no desk. O valor padrão é definido como `LeapControllerOrientation.Headset` .
    - Cada orientação do controlador contém propriedades de deslocamento:
      - As **propriedades de deslocamento** de orientação do headset espelham as propriedades de deslocamento no componente LeapXRServiceProvider.  O `LeapVRDeviceOffsetMode` tem três opções: Padrão, Deslocamento de Cabeça Manual e Transformação.  Se o modo de deslocamento for Padrão, um deslocamento não será aplicado ao Controlador de Movimento Bissexo.  O modo deslocamento de cabeça manual permite a modificação de três propriedades: `LeapVRDeviceOffsetY` e `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` .  Os valores de propriedade de deslocamento do eixo são aplicados ao posicionamento padrão do controlador.  O modo de deslocamento transformar contém `LeapVRDeviceOrigin` a propriedade Transformar que especifica uma nova origem para o Controlador de Movimento Bissextos.
      - A **orientação** De mesa contém `LeapControllerOffset` a propriedade que define a posição de âncora das mãos bissextivas da mesa.  O deslocamento é calculado em relação à posição da câmera principal e o valor padrão é (0,-0,2, 0,35) para garantir que as mãos apareçam na frente e na exibição da câmera.

        > [!NOTE]
        > As propriedades de deslocamento no perfil são aplicadas uma vez quando o aplicativo é iniciado.  Para modificar os valores durante o runtime, obter o Provedor de Serviços de Movimento Bissexdo da Gerenciador de Dispositivos:
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` e `ExitPinchDistance` são os limites de distância para detecção de gestos de pinçar/tocar no ar.  O gesto de pinçamento é calculado medindo a distância entre a ponta do dedo indicador e a ponta do dedo indicador.  Para auportar um evento na entrada para baixo, o `EnterPinchDistance` padrão é definido como 0,02.  Para auportar um evento na entrada (saindo da pinçação), a distância padrão entre a ponta do dedo indicador e a dica de miniatura é 0,05.

    `LeapControllerOrientation`: headset (padrão) |  `LeapControllerOrientation`: Desk
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. Testando o movimento Leap Provedor de Dados
    - Depois que o movimento Leap Provedor de Dados tiver sido adicionado ao perfil do sistema de entrada, pressione reproduzir, mova-o para frente do controlador de movimento Leap e você deverá ver a representação conjunta do lado.

1. Criando seu projeto
    - Navegue até o **arquivo > configurações de Build**
    - Somente compilações autônomas têm suporte se você estiver usando o Provedor de Dados de movimento Leap.
    - Para obter instruções sobre como usar um headset de realidade mista do Windows para compilações autônomas, consulte [compilando e implantando MRTK (autônomo)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).

## <a name="getting-the-hand-joints"></a>Obtendo as junções de mão

A obtenção de junções usando o movimento Leap Provedor de Dados é idêntica à recuperação conjunta da MRTK para uma mão articulada.  Para obter mais informações, consulte [controle à mão](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).

Com MRTK em uma cena do Unity e o movimento Leap Provedor de Dados adicionado como uma entrada Provedor de Dados no perfil do sistema de entrada, crie um objeto de jogo vazio e anexe o script de exemplo a seguir.

Esse script é um exemplo simples de como recuperar a pose do conjunto de Palm em uma mão de movimento bissexto.  Uma esfera segue a mão à esquerda enquanto um cubo segue a mão à direita.

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

## <a name="unity-editor-workflow-tip"></a>Dica de fluxo de trabalho do editor do Unity

Usar o Provedor de Dados de movimento LEAP não exige um headset VR.  As alterações em um aplicativo MRTK podem ser testadas no editor com as mãos Leap sem um headset.

As mãos de movimento Leap aparecerão no editor, sem um headset VR conectado.  Se o estiver definido como Headset, o controlador leap Motion precisará ser mantido em uma mão com a `LeapControllerOrientation` câmera voltada para frente. 

> [!NOTE]
> Se a câmera for movida usando chaves WASD no editor e o for `LeapControllerOrientation` **Headset**, as mãos não seguirão a câmera. As mãos só seguirão o movimento da câmera se um headset vr estiver conectado enquanto o `LeapControllerOrientation` estiver definido como **Headset**.  As mãos do Leap seguirão o movimento da câmera no editor se `LeapControllerOrientation` o estiver definido como **Desk.**

## <a name="removing-leap-motion-from-the-project"></a>Removendo o Leap Motion do projeto

1. Navegue até os **módulos** do Unity do  >  **Leap Motion Separados** do Leap Motion do Kit de Ferramentas de Realidade  >  **Misturada**
    - Permitir que o Unity atualize como referências **no arquivo Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** são modificadas nesta etapa
1. Fechar Unity
1. Feche Visual Studio, se estiver aberto
1. Abra Explorador de Arquivos e navegue até a raiz do projeto unity do MRTK
    - Excluir o **diretório UnityProjectName/Library**
    - Excluir o **diretório UnityProjectName/Assets/Plugins/LeapMotion**
    - Excluir o **arquivo UnityProjectName/Assets/Plugins/LeapMotion.meta**
1. Reabrir o Unity

No Unity 2018.4, você pode observar que os erros ainda permanecem no console depois de excluir a Biblioteca e os Ativos do Leap Motion Core.
Se os erros são registrados após a reabertura, reinicie o Unity novamente.

## <a name="common-errors"></a>Erros Comuns

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>O Leap Motion não foi integrado ao MRTK

Para testar se os Módulos do Unity do Leap Motion foram integrados ao MRTK:

- Navegue até **Kit de Ferramentas de Realidade Misturada > utilitários > Leap Motion > verificar o status de integração**
  - Isso exibirá uma janela pop-up com uma mensagem sobre se os Módulos do Unity do Leap Motion foram integrados ou não ao MRTK.
- Se a mensagem informar que os ativos não foram integrados:
  - Certifique-se de que os módulos do Unity de movimento Leap estejam no projeto
  - Verifique se a versão adicionada tem suporte, consulte a tabela na parte superior da página para obter as versões com suporte.
  - Experimente a **Mixed Reality Toolkit > Utilities > movimento leap > integrar módulos de movimento Leap**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Falha ao copiar HLAPI de vários participantes do assembly

Na importação dos ativos do Unity Core de movimento Leap, esse erro pode ser registrado:

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Solução**

- Uma solução de curto prazo é reiniciar o Unity. Consulte o [problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) para obter mais informações.

## <a name="leap-motion-example-scene"></a>Cena de exemplo de movimento Leap

A cena de exemplo usa o perfil DefaultLeapMotionConfiguration e determina se o projeto do Unity foi configurado corretamente para usar o Provedor de Dados de movimento Leap.

A cena de exemplo está contida no pacote **Microsoft. MixedReality. Toolkit. examples** no diretório **MRTK/examples/demos/HandTracking/** .  

## <a name="see-also"></a>Confira também

- [Provedores de entrada](../features/input/input-providers.md)
- [Acompanhamento à mão](../features/input/hand-tracking.md)
