---
title: Ponto de foco no Unity
description: Ajuste manual da estabilidade do holograma no Unity definindo o ponto de foco
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, ponto de foco, plano de foco, plano de estabilização, ponto de estabilização, Reprojeção, LSR, buffer de profundidade, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: d2708dcf39f1d2c67ab1abf69f8330f9dd536ab0
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010267"
---
# <a name="focus-point-in-unity"></a>Ponto de foco no Unity

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo**: *HolographicSettings*

Use o [ponto de foco](../platform-capabilities-and-apis/hologram-stability.md#reprojection) para fornecer um HoloLens com uma dica sobre como estabilizar melhor os hologramas que estão sendo exibidos no momento.

Se você quiser definir o ponto de foco no Unity, ele precisará ser definido a cada quadro usando *HolographicSettings. SetFocusPointForFrame ()*. Quando o ponto de foco não está definido para um quadro, o plano de estabilização padrão é usado.

> [!NOTE]
> Por padrão, novos projetos do Unity têm a opção "Habilitar compartilhamento de buffer de profundidade" definida.  Com essa opção, um aplicativo de Unity em execução em um headset de área de trabalho imersiva ou um HoloLens executando a atualização de abril de 2018 do Windows (RS4) ou posterior enviará seu buffer de profundidade para o Windows para otimizar a estabilidade do holograma automaticamente, sem que seu aplicativo especifique um ponto de foco:
> * Em um headset de área de trabalho imersiva, isso habilitará a Reprojeção baseada em profundidade por pixel.
> * Em um HoloLens executando a atualização de abril de 2018 do Windows 10 ou posterior, isso analisará o buffer de profundidade para escolher um plano de estabilização ideal automaticamente.
>
> Qualquer uma das abordagens deve fornecer uma qualidade de imagem ainda melhor sem trabalho explícito por seu aplicativo para selecionar um ponto de foco para cada quadro.  Observe que, se você fornecer um ponto de foco manualmente, isso substituirá o comportamento automático descrito acima e geralmente reduzirá a estabilidade do holograma.  Em geral, você deve especificar apenas um ponto de foco manual quando seu aplicativo estiver em execução em um HoloLens que ainda não foi atualizado para a atualização do Windows 10 de abril de 2018.

### <a name="example"></a>Exemplo

Há várias maneiras de definir o ponto de foco, conforme sugerido pelas sobrecargas disponíveis na função estática *SetFocusPointForFrame* . Veja abaixo um exemplo simples para definir o plano de foco para o objeto fornecido para cada quadro:

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

> [!NOTE]
> O código simples acima pode reduzir a estabilidade do holograma se o objeto focalizado terminar por trás do usuário. Geralmente, recomendamos a configuração **[habilitar o compartilhamento de buffer de profundidade](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** em vez de especificar manualmente um ponto de foco.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada. A partir daqui, você pode continuar para o próximo tópico:

> [!div class="nextstepaction"]
> [Controle de perda](tracking-loss-in-unity.md)

Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:

> [!div class="nextstepaction"]
> [Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows](../platform-capabilities-and-apis/using-visual-studio.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-platform-capabilities-and-apis) a qualquer momento.

### <a name="see-also"></a>Confira também
* [Plano de estabilização](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
