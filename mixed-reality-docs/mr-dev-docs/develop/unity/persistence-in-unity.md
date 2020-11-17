---
title: Persistência no Unity
description: A persistência permite que os usuários fixem hologramas individuais ou um espaço de trabalho onde quer que eles o desejam e, em seguida, os encontrem mais tarde, quando esperam muitos usos de seu aplicativo.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistência, Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: cff7f05a5a5695ae8e379ed681c3b7320622968c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678525"
---
# <a name="persistence-in-unity"></a>Persistência no Unity

**Namespace:** *UnityEngine. XR. WSA. Persistence*<br>
**Classe:** *WorldAnchorStore*

O WorldAnchorStore é a chave para criar experiências de Holographic em que os hologramas permanecem em posições reais específicas entre instâncias do aplicativo. Isso permite que os usuários fixem hologramas individuais ou um espaço de trabalho onde quer que eles desejam e, em seguida, os consideram mais tarde, quando esperam mais de muitos usos de seu aplicativo.

## <a name="how-to-persist-holograms-across-sessions"></a>Como manter os hologramas entre as sessões

O WorldAnchorStore permitirá que você persista o local de WorldAnchor entre as sessões. Para realmente manter os hologramas entre as sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica. Geralmente faz sentido criar uma raiz gameobject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.

Para carregar os hologramas de sessões anteriores:
1. Obter o WorldAnchorStore
2. Carregar dados de aplicativo relacionados à âncora mundial, que fornece a ID da âncora mundial
3. Carregar uma âncora mundial de sua ID

Para salvar os hologramas para sessões futuras:
1. Obter o WorldAnchorStore
2. Salvar uma âncora mundial especificando uma ID
3. Salvar dados de aplicativo relacionados à âncora mundial, juntamente com uma ID

### <a name="getting-the-worldanchorstore"></a>Obtendo o WorldAnchorStore

Gostaríamos de manter uma referência para o WorldAnchorStore, portanto, sabemos que estamos prontos para começar quando quisermos realizar uma operação. Como essa é uma chamada assíncrona, possivelmente assim que for iniciada, queremos chamar

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

O StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Agora temos uma referência ao WorldAnchorStore que usaremos para salvar e carregar âncoras mundiais específicas.

### <a name="saving-a-worldanchor"></a>Salvando um WorldAnchor

Para economizar, precisamos simplesmente nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes de se desejarmos salvar. Observação: tentar salvar duas âncoras na mesma cadeia de caracteres falhará (Store. Save retornará false). Você precisa excluir o salvamento anterior antes de salvar o novo:

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>Carregando um WorldAnchor

E para carregar:

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

Além disso, podemos usar Store. Delete () para remover uma âncora que salvamos e armazenamos anteriormente. Clear () para remover todos os dados salvos anteriormente.

### <a name="enumerating-existing-anchors"></a>Enumerando âncoras existentes

Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistendo hologramas para vários dispositivos

Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos de HoloLens, Ios e Android, mesmo se esses dispositivos não estiverem presentes juntos ao mesmo tempo.  Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.

Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.

Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos principais blocos de construção da realidade misturada. De lá, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Mapeamento espacial](spatial-mapping-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Consulte Também
* [Persistência de ancoragem espacial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a>
