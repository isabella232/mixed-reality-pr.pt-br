---
title: Sistemas de coordenadas no Unity
description: Saiba como criar experiências de realidade misturada, em posição de sala e em escala mundial no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciais, somente orientação, escala assentada, escala em posição, espaço em escala, escala mundial, 360 graus, encaixada, posicionada, sala, mundo, escala, posição, orientação, Unity, âncora, âncora espacial, ancoragem mundial, trancada mundial, bloqueio mundial, fone de ouvido, bloqueio de corpo, perda de controle, locatability, limites, recentralizar, realidade misturada, headset do Windows, headset de realidade virtual
ms.openlocfilehash: aa68ae44e09dfe579f8ab8924d1b300506a1f00e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581065"
---
# <a name="coordinate-systems-in-unity"></a>Sistemas de coordenadas no Unity

O Windows Mixed Reality dá suporte a aplicativos em uma ampla variedade de [escalas de experiência](../../design/coordinate-systems.md), desde aplicativos de dimensionamento e de orientação e escalados até aplicativos em escala de sala. No HoloLens, você pode ir além e criar aplicativos de escala mundial que permitem que os usuários passem além de 5 metros, explorando um andar inteiro de um edifício e além disso.

Sua primeira etapa na criação de uma experiência de realidade mista no Unity é determinar qual [escala de experiência](../../design/coordinate-systems.md) seu aplicativo será direcionada.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Criando uma experiência somente de orientação ou de escala assentada

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Para criar uma experiência **somente de orientação** ou **de escala assentada**, você precisa definir o Unity para o tipo de espaço de rastreamento estacionário. O espaço de acompanhamento fixo define o sistema de coordenadas mundiais do Unity para acompanhar o [quadro de referência](../../design/coordinate-systems.md#spatial-coordinate-systems). No modo de rastreamento estacionário, o conteúdo colocado no editor apenas na frente do local padrão da câmera (Forward is-Z) aparecerá na frente do usuário quando o aplicativo for iniciado.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *InputTracking*

Para uma **experiência pura somente de orientação** , como um visualizador de vídeo de 360 graus (em que as atualizações de cabeça posicional poderiam arruinar a ilusão), você pode então definir a [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) para true:

```cs
InputTracking.disablePositionalTracking = true;
```

Para uma **experiência em escala**, para permitir que o usuário recentralize a origem encaixada novamente, você pode chamar a [XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Criando uma experiência em escala ou em escala de sala

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Para uma experiência **de escala de** colocação ou de escala de **espaço**, você precisará colocar o conteúdo em relação ao andar. Você se deparar com o andar do usuário usando o **[estágio espacial](../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa a origem definida do nível de chão do usuário e o limite de sala opcional, configurado durante a primeira execução.

Para garantir que o Unity esteja operando com seu sistema de coordenadas mundiais no nível de piso, você pode definir e testar se o Unity está usando o tipo de espaço de rastreamento RoomScale:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Se SetTrackingSpaceType retornar true, o Unity alternará com êxito seu sistema de coordenadas mundiaI para acompanhar o [quadro de referência de estágio](../../design/coordinate-systems.md#spatial-coordinate-systems).
* Se SetTrackingSpaceType retornar false, o Unity não poderá alternar para o quadro de referência de estágio, provavelmente porque o usuário não configurou um andar em seu ambiente. Embora um valor falso de retorno não seja comum, isso pode acontecer se o estágio estiver configurado em uma sala diferente e o dispositivo for movido para o espaço atual sem que o usuário configure um novo estágio.

Depois que o aplicativo definir o tipo de espaço de acompanhamento RoomScale com êxito, o conteúdo colocado no plano y = 0 aparecerá no chão. A origem em 0, 0, será o local específico no andar em que o usuário se deparava durante a configuração da sala, com-Z representando a direção de encaminhamento que ele estava enfrentando durante a instalação.

**Namespace:** *UnityEngine. experimental. XR*<br>
**Tipo:** *limite*

No código de script, você pode chamar o método TryGetGeometry no tipo UnityEngine. experimental. XR. limite para obter um polígono de limite, especificando um tipo de limite de TrackedArea. Se o usuário definiu um limite (você obtém uma lista de vértices), é seguro fornecer uma **experiência de escala de sala** ao usuário, na qual eles podem percorrer a cena que você criar.

> [!NOTE]
> O sistema irá renderizar automaticamente o limite quando o usuário o aproximar. Seu aplicativo não precisa usar este polígono para renderizar o limite em si. No entanto, você pode optar por definir o layout de seus objetos de cena usando esse polígono de limite, para garantir que o usuário possa alcançar fisicamente esses objetos sem teleportação:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Criando uma experiência de escala mundial

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

Para experiências reais em grande **escala** sobre o HoloLens que permitem aos usuários percorrer mais de 5 metros, você precisará de novas técnicas além das usadas para experiências em escala de sala. Uma técnica importante que você usará é criar uma [âncora espacial](../../design/coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente no mundo físico, não importa o quanto o usuário está em roaming e, em seguida, [encontrar esses hologramas novamente em sessões posteriores](../../design/coordinate-systems.md#spatial-anchor-persistence).

No Unity, você cria uma âncora espacial adicionando o componente **WorldAnchor** Unity a um gameobject.

### <a name="adding-a-world-anchor"></a>Adicionando uma âncora mundial

Para adicionar uma âncora mundial, chame addComponent <WorldAnchor> () no objeto Game com a transformação que você deseja ancorar no mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Pronto! Este objeto de jogo agora será ancorado ao seu local atual no mundo físico – você pode ver que suas coordenadas do Unity World se ajustam um pouco ao longo do tempo para garantir que o alinhamento físico. Use a [persistência](persistence-in-unity.md) para localizar esse local ancorado novamente em uma sessão de aplicativo futura.

### <a name="removing-a-world-anchor"></a>Removendo uma âncora mundial

Se você não quiser mais que o gameobject seja bloqueado em um local físico do mundo e não pretenda movê-lo para esse quadro, você pode simplesmente chamar Destroy no componente de âncora mundial.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Se você quiser mover o gameobject para este quadro, precisará chamar DestroyImmediate em vez disso.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Movendo um jogo de jogos ancorado

O gameobject não pode ser movido enquanto uma âncora mundial está nele. Se você precisar mover o gameobject para este quadro, precisará:
1. DestroyImmediate o componente de âncora mundial
2. Mover o gameobject
3. Adicione um novo componente de âncora mundial ao gameobject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Manipulando alterações de Locatability

Um WorldAnchor pode não ser localizável no mundo físico em um ponto no tempo. Se isso ocorrer, o Unity não atualizará a transformação do objeto ancorado. Isso também pode ser alterado enquanto um aplicativo está em execução. A falha ao manipular a alteração em locatability fará com que o objeto não apareça no local físico correto do mundo.

Para ser notificado sobre as alterações de locatability:
1. Assinar o evento onrastreiechanged
2. Manipular o evento

O evento **Oncontrolchanged** será chamado sempre que a âncora espacial subjacente for alterada entre o estado de ser localizável versus não ser localizável.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Em seguida, manipule o evento:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Às vezes, as âncoras estão localizadas imediatamente. Nesse caso, essa propriedade islocalizada da âncora será definida como true quando addComponent <WorldAnchor> () retornar. Como resultado, o evento onrastreiochanged não será disparado. Um padrão limpo seria chamar o manipulador oncontrolchanged com o estado inicial IsDeleted depois de anexar uma âncora.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Compartilhando âncoras entre dispositivos

Use <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável a partir de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos HoloLens, Ios e Android.  Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.

Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos principais blocos de construção da realidade misturada. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Foco](gaze-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Consulte Também
* [Escalas de experiência](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Estágio espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Como controlar a perda no Unity](tracking-loss-in-unity.md)
* [Âncoras espaciais](../../design/spatial-anchors.md)
* [Persistência no Unity](persistence-in-unity.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)
* <a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a>