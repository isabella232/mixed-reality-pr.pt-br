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
# <a name="persistence-in-unity"></a><span data-ttu-id="d0232-104">Persistência no Unity</span><span class="sxs-lookup"><span data-stu-id="d0232-104">Persistence in Unity</span></span>

<span data-ttu-id="d0232-105">**Namespace:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="d0232-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="d0232-106">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="d0232-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="d0232-107">O WorldAnchorStore é a chave para criar experiências de Holographic em que os hologramas permanecem em posições reais específicas entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0232-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="d0232-108">Isso permite que os usuários fixem hologramas individuais ou um espaço de trabalho onde quer que eles desejam e, em seguida, os consideram mais tarde, quando esperam mais de muitos usos de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0232-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="d0232-109">Como manter os hologramas entre as sessões</span><span class="sxs-lookup"><span data-stu-id="d0232-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="d0232-110">O WorldAnchorStore permitirá que você persista o local de WorldAnchor entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="d0232-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="d0232-111">Para realmente manter os hologramas entre as sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica.</span><span class="sxs-lookup"><span data-stu-id="d0232-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="d0232-112">Geralmente faz sentido criar uma raiz gameobject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.</span><span class="sxs-lookup"><span data-stu-id="d0232-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="d0232-113">Para carregar os hologramas de sessões anteriores:</span><span class="sxs-lookup"><span data-stu-id="d0232-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="d0232-114">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="d0232-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="d0232-115">Carregar dados de aplicativo relacionados à âncora mundial, que fornece a ID da âncora mundial</span><span class="sxs-lookup"><span data-stu-id="d0232-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="d0232-116">Carregar uma âncora mundial de sua ID</span><span class="sxs-lookup"><span data-stu-id="d0232-116">Load a world anchor from its id</span></span>

<span data-ttu-id="d0232-117">Para salvar os hologramas para sessões futuras:</span><span class="sxs-lookup"><span data-stu-id="d0232-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="d0232-118">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="d0232-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="d0232-119">Salvar uma âncora mundial especificando uma ID</span><span class="sxs-lookup"><span data-stu-id="d0232-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="d0232-120">Salvar dados de aplicativo relacionados à âncora mundial, juntamente com uma ID</span><span class="sxs-lookup"><span data-stu-id="d0232-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="d0232-121">Obtendo o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="d0232-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="d0232-122">Gostaríamos de manter uma referência para o WorldAnchorStore, portanto, sabemos que estamos prontos para começar quando quisermos realizar uma operação.</span><span class="sxs-lookup"><span data-stu-id="d0232-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="d0232-123">Como essa é uma chamada assíncrona, possivelmente assim que for iniciada, queremos chamar</span><span class="sxs-lookup"><span data-stu-id="d0232-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="d0232-124">O StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:</span><span class="sxs-lookup"><span data-stu-id="d0232-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="d0232-125">Agora temos uma referência ao WorldAnchorStore que usaremos para salvar e carregar âncoras mundiais específicas.</span><span class="sxs-lookup"><span data-stu-id="d0232-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="d0232-126">Salvando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="d0232-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="d0232-127">Para economizar, precisamos simplesmente nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes de se desejarmos salvar.</span><span class="sxs-lookup"><span data-stu-id="d0232-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="d0232-128">Observação: tentar salvar duas âncoras na mesma cadeia de caracteres falhará (Store. Save retornará false).</span><span class="sxs-lookup"><span data-stu-id="d0232-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="d0232-129">Você precisa excluir o salvamento anterior antes de salvar o novo:</span><span class="sxs-lookup"><span data-stu-id="d0232-129">You need to Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="d0232-130">Carregando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="d0232-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="d0232-131">E para carregar:</span><span class="sxs-lookup"><span data-stu-id="d0232-131">And to load:</span></span>

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

<span data-ttu-id="d0232-132">Além disso, podemos usar Store. Delete () para remover uma âncora que salvamos e armazenamos anteriormente. Clear () para remover todos os dados salvos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d0232-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="d0232-133">Enumerando âncoras existentes</span><span class="sxs-lookup"><span data-stu-id="d0232-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="d0232-134">Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="d0232-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="d0232-135">Persistendo hologramas para vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="d0232-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="d0232-136">Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos de HoloLens, Ios e Android, mesmo se esses dispositivos não estiverem presentes juntos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="d0232-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="d0232-137">Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="d0232-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="d0232-138">Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="d0232-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="d0232-139">Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="d0232-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d0232-140">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="d0232-140">Next Development Checkpoint</span></span>

<span data-ttu-id="d0232-141">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos principais blocos de construção da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="d0232-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="d0232-142">De lá, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="d0232-142">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d0232-143">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="d0232-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="d0232-144">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="d0232-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d0232-145">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="d0232-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="d0232-146">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="d0232-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0232-147">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d0232-147">See Also</span></span>
* [<span data-ttu-id="d0232-148">Persistência de ancoragem espacial</span><span class="sxs-lookup"><span data-stu-id="d0232-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="d0232-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="d0232-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="d0232-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="d0232-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
