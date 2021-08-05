---
title: Guia de portabilidade de entrada para Unity
description: Saiba como lidar com a entrada para Windows Mixed Reality no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: entrada, unity, portação
ms.openlocfilehash: b2c328152d681a4c8753e29babf0f3ece6bdc0d3f21f9df6dd8de150c3fb47f0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212074"
---
# <a name="input-porting-guide-for-unity"></a>Guia de portabilidade de entrada para Unity

Você pode por a portabilidade da lógica de entrada para Windows Mixed Reality usando uma das duas abordagens. A primeira é usar as APIs Input.GetButton/GetAxis gerais do Unity que abrangem várias plataformas. O segundo é o XR Windows específico do Windows. Wsa. APIs de entrada, que oferecem dados mais rico especificamente para controladores de movimento e HoloLens mãos.

## <a name="general-inputgetbuttongetaxis-apis"></a>APIs Input.GetButton/GetAxis gerais

Atualmente, o Unity usa suas APIs Input.GetButton/Input.GetAxis gerais para expor a entrada para o [SDK do Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e o [SDK do OpenVR.](https://docs.unity3d.com/Manual/OpenVRControllers.html) Se seus aplicativos já estão usando essas APIs para entrada, as APIs Input.GetButton/Input.GetAxis são os caminhos mais fáceis para dar suporte a controladores de movimento Windows Mixed Reality. Você só precisará remapear botões e eixos no Gerenciador de Entrada.

Para obter mais informações, consulte a tabela de mapeamento de [eixo/botão](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) do Unity e a [visão geral das APIs comuns do Unity.](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows XR específico. Wsa. APIs de entrada

Se seu aplicativo já criar uma lógica de entrada personalizada para cada plataforma, você poderá usar as APIs de entrada espaciais específicas Windows no namespace **UnityEngine.XR.WSA.Input.** A partir daí, você acessa informações adicionais, como a precisão da posição ou o tipo de origem, o que permite separar as mãos e os controladores HoloLens.

Para obter mais informações, consulte a [visão geral das APIs UnityEngine.XR.WSA.Input.](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)

## <a name="grip-pose-vs-pointing-pose"></a>Pose da mão versus pose apontando

Windows Mixed Reality dá suporte a controladores de movimento em diferentes fatores forma. O design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural de "avançar" que os aplicativos devem usar para apontar ao renderizar o controlador.

Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada fonte de interação:

* A **mão representa**, que representa o local da mão de uma mão detectada por um HoloLens ou da mão que mantém um controlador de movimento.
    * Em headsets imersivos, essa pose é mais bem usada para **renderizar** a mão do usuário ou um objeto mantido na mão do **usuário,** como um capacete ou umaada.
    * A **posição da mão:** o centroide da mão ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralar a posição dentro da mão.
    * Eixo direito da orientação da **mão:** quando você abre completamente a mão para formar uma pose de 5 dedos simples, o raio que é normal para sua mão (para frente da mão esquerda, para trás da mão direita)
    * Eixo **de** avanço da orientação da mão: quando você fecha a mão parcialmente, como se estivesse segurando o controlador, o raio que aponta para "para frente" pelo sinal formado pelos dedos não polegares.
    * Eixo **para cima da orientação da** mão: o eixo Para cima implícito nas definições Direita e Avanço.
    * Você pode acessar a pose de controle por meio da API de entrada entre fornecedores do Unity **[(XR). InputTracking.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html) GetLocalPosition/Rotation**) ou por meio da API específica do Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** solicitando a pose de mão).
* O **ponteiro representa**, representando a dica do controlador apontando para frente.
    * Essa pose é melhor usada para raycast **ao apontar para** a interface do usuário quando você estiver renderizar o próprio modelo de controlador.
    * Atualmente, a pose do ponteiro está disponível somente por meio da API específica Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** solicitando a pose De ponteiro).

Todas essas coordenadas de pose são expressas em coordenadas do mundo do Unity.

## <a name="see-also"></a>Confira também
* [Controladores de movimento]().. /.. /design/motion-controllers.md)
* [Controladores de movimento no Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guias de portabilidade](porting-guides.md)
