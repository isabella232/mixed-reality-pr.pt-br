---
title: Ponto de foco no Unity
description: Saiba como ajustar manualmente a estabilidade do holograma no Unity definindo o ponto de foco para HoloLens e Windows Mixed Reality headsets imersivos.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, ponto de foco, plano de foco, plano de estabilização, ponto de estabilização, reprojeto, LSR, buffer de profundidade, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 91fba310cf86f145174512c4c1e23d69907d2f57f48f3fe1992b417eb283235f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203588"
---
# <a name="focus-point-in-unity"></a>Ponto de foco no Unity

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *HolographicSettings*

Use o [ponto de foco](../platform-capabilities-and-apis/hologram-stability.md#reprojection) para fornecer HoloLens uma dica sobre como estabilizar melhor os hologramas que estão sendo exibidos no momento.

Se você quiser definir o Ponto de Foco no Unity, ele precisará ser definido em cada quadro usando *HolographicSettings.SetFocusPointForFrame().* Quando o Ponto de Foco não está definido para um quadro, o plano de estabilização padrão é usado.

> [!NOTE]
> Por padrão, os novos projetos do Unity têm a opção "Habilitar Compartilhamento de Buffer de Profundidade" definida.  Com essa opção, um aplicativo unity em execução em um headset da área de trabalho imersiva ou um HoloLens executando a RS4 (Atualização de abril de 2018) do Windows 10 ou posterior enviará seu buffer de profundidade para o Windows para otimizar a estabilidade do holograma automaticamente, sem que seu aplicativo especifique um ponto de foco:
> * Em um headset de área de trabalho imersivo, isso habilita a reprodução baseada em profundidade por pixel.
> * Em um HoloLens executando a atualização de Windows 10 de abril de 2018 ou posterior, isso analisará o buffer de profundidade para escolher um plano de estabilização ideal automaticamente.
>
> Qualquer abordagem deve fornecer uma qualidade de imagem ainda melhor sem o trabalho explícito do seu aplicativo para selecionar um ponto de foco para cada quadro.  Observe que, se você fornecer um ponto de foco manualmente, isso substituirá o comportamento automático descrito acima e geralmente reduzirá a estabilidade do holograma.  Em geral, você só deve especificar um ponto de foco manual quando seu aplicativo estiver em execução em um HoloLens que ainda não tenha sido atualizado para a atualização de Windows 10 de abril de 2018.

### <a name="example"></a>Exemplo

Há muitas maneiras de definir o Ponto de Foco, conforme sugerido pelas sobrecargas disponíveis na função estática *SetFocusPointForFrame.* Apresentado abaixo está um exemplo simples para definir o plano de foco para o objeto fornecido para cada quadro:

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
> O código simples acima poderá reduzir a estabilidade do holograma se o objeto focalizado acabar atrás do usuário. Geralmente, recomendamos definir **[Habilitar Compartilhamento](camera-in-unity.md#sharing-depth-buffers)** de Buffer de Profundidade em vez de especificar manualmente um ponto de foco.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que lançamos, você está no meio da exploração das APIs e funcionalidades da plataforma de Realidade Misturada. Deste ponto, você pode prosseguir para o próximo tópico:

> [!div class="nextstepaction"]
> [Controle de perda](tracking-loss-in-unity.md)

Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:

> [!div class="nextstepaction"]
> [Implantar em HoloLens ou Windows Mixed Reality headsets imersivos](../platform-capabilities-and-apis/using-visual-studio.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-advanced-features) a qualquer momento.

### <a name="see-also"></a>Confira também

* [Plano de estabilização](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
