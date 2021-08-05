---
title: Persistência no Unity
description: A persistência permite que o usuário fixe hologramas individuais onde quer que ele queira e, em seguida, encontre-os posteriormente em vários usos do seu aplicativo.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistência, Unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 9283191c024cbe33ecda3946a4e9bcbd5f3708c21a3578484b547207ee70a49b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208966"
---
# <a name="persistence-in-unity"></a>Persistência no Unity

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Classe:** *WorldAnchorStore*

O WorldAnchorStore é a chave para criar experiências holográficas em que os hologramas permanecem em posições específicas do mundo real entre instâncias do aplicativo. Os usuários podem fixar hologramas individuais sempre que quiserem e encontrá-los posteriormente no mesmo local em vários usos de seu aplicativo.

## <a name="how-to-persist-holograms-across-sessions"></a>Como persistir hologramas entre sessões

O WorldAnchorStore permitirá que você persista o local do WorldAnchor entre as sessões. Para realmente persistir hologramas entre sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica. Geralmente, faz sentido criar uma raiz GameObject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.

Para carregar hologramas de sessões anteriores:
1. Obter o WorldAnchorStore
2. Carregar dados do aplicativo relacionados à âncora mundial, que fornece a ID da âncora do mundo
3. Carregar uma âncora mundial de sua ID

Para salvar hologramas para sessões futuras:
1. Obter o WorldAnchorStore
2. Salvar uma âncora mundial especificando uma ID
3. Salvar dados do aplicativo relacionados à âncora do mundo juntamente com uma ID

### <a name="getting-the-worldanchorstore"></a>Obter o WorldAnchorStore

Você deve manter uma referência ao WorldAnchorStore para saber quando ele está pronto para executar uma operação. Como essa é uma chamada assíncrona, potencialmente assim que iniciar, você deseja chamar:

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Agora temos uma referência ao WorldAnchorStore, que vamos usar para salvar e carregar Âncoras Do Mundo específicas.

### <a name="saving-a-worldanchor"></a>Salvando um WorldAnchor

Para salvar, basta nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes quando queremos salvar. Observação: a tentativa de salvar duas âncoras na mesma cadeia de caracteres falhará (armazenar. Salvar retornará false). Exclua o salvar anteriormente antes de salvar o novo:

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

Além disso, podemos usar o store. Delete() para remover uma âncora que salvamos anteriormente e armazenamos. Clear() para remover todos os dados salvos anteriormente.

### <a name="enumerating-existing-anchors"></a>Enumerando âncoras existentes

Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistir hologramas para vários dispositivos

Você pode usar âncoras espaciais do <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> para criar uma âncora de nuvem durável de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos HoloLens, iOS e Android, mesmo que esses dispositivos não estão presentes juntos ao mesmo tempo.  Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.

Para começar a criar experiências compartilhadas no Unity, experimente os <a href="/azure/spatial-anchors/unity-overview" target="_blank">inícios rápidos</a>do Unity das Âncoras Espaciais do Azure de 5 minutos.

Quando estiver em execução com as Âncoras Espaciais do Azure, você poderá criar e <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">localizar âncoras no Unity.</a>

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso do ponto de verificação de desenvolvimento do Unity que lançamos, você está no meio da exploração dos blocos de construção principais da Realidade Misturada. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Mapeamento espacial](spatial-mapping-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Consulte Também
* [Persistência de âncora espacial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de Âncoras Espaciais do Azure para Unity</a>