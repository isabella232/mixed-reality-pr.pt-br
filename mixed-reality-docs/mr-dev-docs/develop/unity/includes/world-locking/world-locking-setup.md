---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528772"
---
# <a name="world-locking-tools-recommended"></a>[Ferramentas de bloqueio Mundial (recomendado)](#tab/wlt)

Recomendamos instalar as ferramentas de bloqueio mundial usando a nova ferramenta de funcionalidade de realidade misturada. Depois de baixar a ferramenta de recurso de realidade misturada do link abaixo, selecione a versão mais recente do **WLT Core** na seção de **ferramentas de bloqueio mundial** :

![Janela de seleção de recursos da ferramenta de recurso de realidade misturada com ferramentas de bloqueio mundial selecionadas](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [Instalar ferramentas de bloqueio mundial com a ferramenta de recurso MR](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>Configuração automatizada

Quando seu projeto estiver pronto para começar, execute o utilitário configurar cena do **Kit de ferramentas de realidade misturada > utilitários > ferramentas de bloqueio mundial**:

![Editor Unity com o menu do kit de ferramentas da realidade misturada selecionado](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> O utilitário configurar cena pode ser executado novamente a qualquer momento. Por exemplo, ele deve ser executado novamente se o destino AR tiver sido alterado de herdado para o SDK do XR. Se a cena já estiver configurada corretamente, a execução do utilitário não terá nenhum efeito.

### <a name="visualizers"></a>Visualizadores

Durante o desenvolvimento antecipado, adicionar visualizadores pode ser útil para garantir que o WLT esteja configurado e funcionando corretamente. Eles podem ser removidos para o desempenho de produção ou se por qualquer motivo não forem mais necessários, usando o utilitário remover visualizadores. Mais detalhes sobre os visualizadores podem ser encontrados na [documentação de ferramentas](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

O plug-in Mixed Reality OpenXR fornece a funcionalidade de ancoragem básica por meio de uma implementação de ARFoundation **ARAnchorManager** do Unity. Para aprender as noções básicas sobre o ARAnchors no ARFoundation, visite o [manual do ARFoundation para o gerente de ancoragem ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>Criando uma experiência de escala mundial

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

Para experiências reais em grande **escala** sobre o HoloLens que permitem aos usuários percorrer mais de 5 metros, você precisará de novas técnicas além das usadas para experiências em escala de sala. Uma técnica importante que você usará é criar uma [âncora espacial](../../../../design/coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente no mundo físico, não importa o quanto o usuário está em roaming e, em seguida, [encontrar esses hologramas novamente em sessões posteriores](../../../../design/coordinate-systems.md#spatial-anchor-persistence).

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