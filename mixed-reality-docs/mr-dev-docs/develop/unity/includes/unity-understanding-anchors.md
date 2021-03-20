---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719782"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

O plug-in Mixed Reality OpenXR fornece a funcionalidade de ancoragem básica por meio de uma implementação de ARFoundation **ARAnchorManager** do Unity. Para aprender as noções básicas sobre o ARAnchors no ARFoundation, visite o [manual do ARFoundation para o gerente de ancoragem ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). 

# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in do Unity 2019/2020 + Windows XR](#tab/winxr)

O plug-in Mixed Reality OpenXR fornece a funcionalidade de ancoragem básica por meio de uma implementação de ARFoundation **ARAnchorManager** do Unity. Para aprender as noções básicas sobre o ARAnchors no ARFoundation, visite o [manual do ARFoundation para o gerente de ancoragem ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

## <a name="building-a-world-scale-experience"></a>Criando uma experiência de escala mundial

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

Para experiências reais em grande **escala** sobre o HoloLens que permitem aos usuários percorrer mais de 5 metros, você precisará de novas técnicas além das usadas para experiências em escala de sala. Uma técnica importante que você usará é criar uma [âncora espacial](../../../design/coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente no mundo físico, não importa o quanto o usuário está em roaming e, em seguida, [encontrar esses hologramas novamente em sessões posteriores](../../../design/coordinate-systems.md#spatial-anchor-persistence).

No Unity, você cria uma âncora espacial adicionando o componente **WorldAnchor** Unity a um gameobject.

### <a name="adding-a-world-anchor"></a>Adicionando uma âncora mundial

Para adicionar uma âncora mundial, ligue para `AddComponent<WorldAnchor>()` o objeto Game com a transformação que você deseja ancorar no mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

É isso! Este objeto de jogo agora será ancorado ao seu local atual no mundo físico – você pode ver que suas coordenadas do Unity World se ajustam um pouco ao longo do tempo para garantir que o alinhamento físico. Consulte [carregando uma âncora mundial](#loading-a-worldanchor) para localizar esse local ancorado novamente em uma sessão de aplicativo futura.

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