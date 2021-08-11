---
title: Como usar o Leap Motion
description: Documentação a ser configurada para o Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Leap Motion,
ms.openlocfilehash: e675521a3a688bc0f9f8afdf1bdc01e583d0b47808d0aaff8b2eff263fce35bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222884"
---
# <a name="using-leap-motion"></a>Como usar o Leap Motion

Um [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) é necessário para usar esse provedor de dados.

O leap Motion Provedor de Dados permite o acompanhamento de mão articulado para VR e pode ser útil para criação rápida de protótipos no editor.  O provedor de dados pode ser configurado para usar o Leap Motion Controller montado em um headset ou colocado em uma face de suporte.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Esse provedor pode ser usado no editor e no dispositivo enquanto estiver na plataforma autônoma.  Ele também pode ser usado no editor enquanto estiver na plataforma UWP, mas NÃO em um build UWP.

| Versão do MRTK | Versões de módulos do Unity do Leap Motion com suporte |
| --- | --- |
|2.6.x | 4.5.0, 4.5.1|
|2.7.x| 4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Usando o acompanhamento de mão do Leap Motion (por Ultraleap) no MRTK

1. Importando o MRTK e os módulos do Unity do Leap Motion
    - Instale o [SDK do Leap Motion](https://developer.leapmotion.com/releases/?category=orion) mais recente se ele ainda não estiver instalado
    - Importe o **Microsoft.MixedReality.Toolkit. Pacote** base no projeto do Unity.
    - Baixar e importar a versão mais recente dos [Módulos do Unity do Leap Motion](https://developer.leapmotion.com/unity) para o projeto
        - Importar apenas o **pacote Core** dentro dos Módulos do Unity

1. Integrar os módulos do Leap Motion Unity ao MRTK
    - Depois que os Módulos do Unity estão no projeto, navegue até Realidade **Misturada Toolkit**  >  **Módulos** do Leap Motion Integrar o Leap Motion  >  **Unity**
    > [!NOTE]
    > A integração dos Módulos do Unity ao MRTK adiciona 10 definições de assembly ao projeto e adiciona referências ao **Microsoft.MixedReality.Toolkit. Definição de assembly Providers.LeapMotion.** Verifique se o Visual Studio está fechado.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Adicionando o Provedor de Dados
    - Criar uma nova cena do Unity
    - Adicione o MRTK à cena navegando até Realidade **Misturada Toolkit**  >  **Adicionar à Cena e Configurar**
    - Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione Copiar e **Personalizar** para clonar o perfil de realidade misturada padrão.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - Selecione o Perfil **de Configuração** de Entrada

    ![Perfil de Configuração de Entrada 1](../images/cross-platform/InputConfigurationProfile.png)

    - Selecione **Clonar** no perfil do sistema de entrada para habilitar a modificação.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - Abra a **seção Provedores de** Dados de **Entrada, selecione Adicionar Provedor de Dados** na parte superior, um novo provedor de dados será adicionado ao final da lista.  Abra o novo provedor de dados e de definir **o Tipo** **como Microsoft.MixedReality.Toolkit. LeapMotion.Input > LeapMotionDeviceManager**

    ![Leap Add Provedor de Dados](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Selecione **Clonar** para alterar as configurações padrão do Leap Motion.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - A propriedade Leap Motion Provedor de Dados `LeapControllerOrientation` contém a propriedade que é o local do Controlador de Movimento Bissexo. `LeapControllerOrientation.Headset` indica que o controlador está montado em um headset. `LeapControllerOrientation.Desk` indica que o controlador é colocado simples no desk. O valor padrão é definido como `LeapControllerOrientation.Headset` .
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

1. Testando o Provedor de Dados
    - Depois que o Leap Motion Provedor de Dados tiver sido adicionado ao perfil do sistema de entrada, pressione Reproduzir, mova a mão para frente do Leap Motion Controller e você deverá ver a representação conjunta da mão.

1. Criando seu projeto
    - Navegue **até Arquivo > Build Configurações**
    - Somente builds autônomos são suportados se você estiver usando o Provedor de Dados.
    - Para obter instruções sobre como usar um headset Windows Mixed Reality para builds autônomos, consulte Criando e implantando o [MRTK em headsets WMR (autônomos).](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)

## <a name="getting-the-hand-joints"></a>Obter as junções de mão

Obter junções usando o leap motion Provedor de Dados é idêntico à recuperação conjunta manual para uma mão articulada do MRTK.  Para obter mais informações, consulte [Acompanhamento de mão.](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)

Com o MRTK em uma cena do Unity e o Provedor de Dados Leap Motion adicionado como um Provedor de Dados entrada no perfil sistema de entrada, crie um objeto de jogo vazio e anexe o script de exemplo a seguir.

Esse script é um exemplo simples de como recuperar a pose da junção de mão em uma Mão de Movimento Bissexo.  Uma esfera segue a mão esquerda do Leap enquanto um cubo segue a mão direita do Leap.

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

O uso da Provedor de Dados Leap Motion não requer um headset vr.  As alterações em um aplicativo MRTK podem ser testadas no editor com as mãos bissexto sem um headset.

As Mãos do Leap Motion aparecerão no editor, sem um headset vr conectado.  Se o estiver definido como Headset, o controlador leap Motion precisará ser mantido em uma mão com a `LeapControllerOrientation` câmera voltada para frente. 

> [!NOTE]
> Se a câmera for movida usando chaves WASD no editor e o for `LeapControllerOrientation` **Headset**, as mãos não seguirão a câmera. As mãos só seguirão o movimento da câmera se um headset vr estiver conectado enquanto o `LeapControllerOrientation` estiver definido como **Headset**.  As mãos do Leap seguirão o movimento da câmera no editor se `LeapControllerOrientation` o estiver definido como **Desk.**

## <a name="removing-leap-motion-from-the-project"></a>Removendo o Leap Motion do Project

1. Navegue até os **módulos do** Unity de Toolkit de Movimento Bissexo  >    >  **Separados do Leap Motion**
    - Deixe o Unity atualizar como referências no **Microsoft.MixedReality.Toolkit. O arquivo Providers.LeapMotion.asmdef** é modificado nesta etapa
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

- Navegue até **Realidade Misturada Toolkit > Utilitários > Leap Motion > Verificar Status de Integração**
  - Isso exibirá uma janela pop-up com uma mensagem sobre se os Módulos do Unity do Leap Motion foram integrados ou não ao MRTK.
- Se a mensagem diz que os ativos não foram integrados:
  - Certifique-se de que os Módulos do Unity do Leap Motion estão no projeto
  - Certifique-se de que a versão adicionada tenha suporte, consulte a tabela na parte superior da página para ver as versões com suporte.
  - Experimente **os utilitários Toolkit > de realidade misturada > Leap Motion > integrar módulos do Leap Motion Unity**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Falha ao copiar o assembly multijogador HLAPI

Na importação dos Ativos Principais do Unity do Leap Motion, esse erro pode ser registrado:

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Solução**

- Uma solução de curto prazo é reiniciar o Unity. Consulte [Problema 7761 para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) obter mais informações.

## <a name="leap-motion-example-scene"></a>Cena de exemplo de movimento bissexo

A cena de exemplo usa o perfil DefaultLeapMotionConfiguration e determina se o projeto do Unity foi configurado corretamente para usar o leap motion Provedor de Dados.

A cena de exemplo está contida no **Microsoft.MixedReality.Toolkit. Pacote de** exemplos **no diretório MRTK/Examples/Demos/HandTracking/.**  

## <a name="see-also"></a>Confira também

- [Provedores de entrada](../features/input/input-providers.md)
- [Acompanhamento da Mão](../features/input/hand-tracking.md)
