---
title: Ponto de foco no Unity
description: Ajuste manual da estabilidade do holograma no Unity definindo o ponto de foco
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, ponto de foco, plano de foco, plano de estabilização, ponto de estabilização, Reprojeção, LSR, buffer de profundidade, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 48c0d26e89124b9dbfc1d108354fb6e751e51783
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678685"
---
# <a name="focus-point-in-unity"></a>Ponto de foco no Unity

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo**: *HolographicSettings*

O [ponto de foco](../platform-capabilities-and-apis/hologram-stability.md#reprojection) pode ser definido para fornecer uma dica sobre como executar melhor a estabilização nos hologramas que estão sendo exibidos no momento.

Se você quiser definir o ponto de foco no Unity, ele precisará ser definido a cada quadro usando *HolographicSettings. SetFocusPointForFrame ()*. Se o ponto de foco não estiver definido para um quadro, o plano de estabilização padrão será usado.

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

Observe que o código simples acima pode acabar reduzindo a estabilidade do holograma se o objeto focalizado terminar por trás do usuário.  É por isso que você geralmente deve definir "habilitar o compartilhamento de buffer de profundidade" em vez de especificar manualmente um ponto de foco.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada. Daí, você pode prosseguir para o próximo tópico:

> [!div class="nextstepaction"]
> [Controle de perda](tracking-loss-in-unity.md)

Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:

> [!div class="nextstepaction"]
> [Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows](../platform-capabilities-and-apis/using-visual-studio.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-platform-capabilities-and-apis) a qualquer momento.

### <a name="see-also"></a>Veja também
* [Plano de estabilização](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
