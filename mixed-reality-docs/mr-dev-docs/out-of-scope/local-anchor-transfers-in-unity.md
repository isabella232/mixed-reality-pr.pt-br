---
title: Transferências de âncora local no Unity
description: Saiba como transferir âncoras entre vários dispositivos do HoloLens em um aplicativo do Unity Mixed Reality.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Compartilhamento, ancoragem, WorldAnchor, Sr Sharing 250, WorldAnchorTransferBatch, SpatialPerception, transferência, transferência de âncora local, exportação de ancoragem, importação de âncora
ms.openlocfilehash: 1048e6a3cfc41a04cd49e201e5d1841e805a4193
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009636"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="0eb5c-104">Transferências de âncora local no Unity</span><span class="sxs-lookup"><span data-stu-id="0eb5c-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="0eb5c-105">Em situações em que você não pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espaciais do Azure</a>, as transferências de âncora local permitem que um dispositivo de hololens exporte uma âncora a ser importada por um segundo dispositivo hololens.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="0eb5c-106">As transferências de âncora local fornecem uma recall de ancoragem menos robusta do que as <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espaciais do Azure</a>, e os dispositivos IOS e Android não são compatíveis com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="0eb5c-107">Configurando o recurso SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="0eb5c-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="0eb5c-108">Para que um aplicativo transfira âncoras espaciais, o recurso *SpatialPerception* deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="0eb5c-109">Como habilitar o recurso *SpatialPerception* :</span><span class="sxs-lookup"><span data-stu-id="0eb5c-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="0eb5c-110">No editor do Unity, abra o painel **"configurações do Player"** (editar > configurações do projeto > Player)</span><span class="sxs-lookup"><span data-stu-id="0eb5c-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="0eb5c-111">Clique na guia **"Windows Store"**</span><span class="sxs-lookup"><span data-stu-id="0eb5c-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="0eb5c-112">Expanda **"configurações de publicação"** e verifique o recurso **"SpatialPerception"** na lista **"recursos"**</span><span class="sxs-lookup"><span data-stu-id="0eb5c-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="0eb5c-113">Se você já tiver exportado seu projeto do Unity para uma solução do Visual Studio, será necessário exportar para uma nova pasta ou [definir manualmente esse recurso no AppxManifest no Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="0eb5c-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="0eb5c-114">Transferência de âncora</span><span class="sxs-lookup"><span data-stu-id="0eb5c-114">Anchor Transfer</span></span>

<span data-ttu-id="0eb5c-115">**Namespace:** *UnityEngine. XR. WSA. Sharing*</span><span class="sxs-lookup"><span data-stu-id="0eb5c-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="0eb5c-116">**Tipo**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="0eb5c-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="0eb5c-117">Para transferir um [WorldAnchor](../develop/unity/coordinate-systems-in-unity.md), um deve estabelecer a âncora a ser transferida.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-117">To transfer a [WorldAnchor](../develop/unity/coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="0eb5c-118">O usuário de um HoloLens examina seu ambiente e, manual ou programaticamente, escolhe um ponto no espaço para ser a âncora para a experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="0eb5c-119">Os dados que representam esse ponto podem ser serializados e transmitidos para os outros dispositivos que estão compartilhando na experiência.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="0eb5c-120">Em seguida, cada dispositivo desserializa os dados de âncora e tenta localizar esse ponto no espaço.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="0eb5c-121">Para que a transferência de âncora funcione, cada dispositivo deve ser examinado em suficiente no ambiente, de modo que o ponto representado pela âncora possa ser identificado.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="0eb5c-122">Instalação</span><span class="sxs-lookup"><span data-stu-id="0eb5c-122">Setup</span></span>

<span data-ttu-id="0eb5c-123">O código de exemplo nesta página tem alguns campos que deverão ser inicializados:</span><span class="sxs-lookup"><span data-stu-id="0eb5c-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="0eb5c-124">*Gameobject rootGameObject* é um *gameobject* no Unity que tem um componente *WorldAnchor* .</span><span class="sxs-lookup"><span data-stu-id="0eb5c-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="0eb5c-125">Um usuário na experiência compartilhada coloca esse *gameobject* e exporta os dados para os outros usuários.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="0eb5c-126">*WorldAnchor gameRootAnchor* é *UnityEngine. XR. WSA. WorldAnchor* que está em *rootGameObject*.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="0eb5c-127">*byte [] importedData* é uma matriz de bytes para a âncora serializada que cada cliente está recebendo pela rede.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="0eb5c-128">Exportar</span><span class="sxs-lookup"><span data-stu-id="0eb5c-128">Exporting</span></span>

<span data-ttu-id="0eb5c-129">Para exportar, precisamos apenas de um *WorldAnchor* e saber o que iremos chamá-lo de modo que faça sentido para o aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="0eb5c-130">Um cliente na experiência compartilhada executará estas etapas para exportar a âncora compartilhada:</span><span class="sxs-lookup"><span data-stu-id="0eb5c-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="0eb5c-131">Criar um *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="0eb5c-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="0eb5c-132">Adicionar o *WorldAnchors* para transferência</span><span class="sxs-lookup"><span data-stu-id="0eb5c-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="0eb5c-133">Iniciar a exportação</span><span class="sxs-lookup"><span data-stu-id="0eb5c-133">Begin the export</span></span>
4. <span data-ttu-id="0eb5c-134">Manipular o evento *OnExportDataAvailable* à medida que os dados ficam disponíveis</span><span class="sxs-lookup"><span data-stu-id="0eb5c-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="0eb5c-135">Manipular o evento *OnExportComplete*</span><span class="sxs-lookup"><span data-stu-id="0eb5c-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="0eb5c-136">Criamos um *WorldAnchorTransferBatch* para encapsular o que iremos transferir e, em seguida, exportá-lo em bytes:</span><span class="sxs-lookup"><span data-stu-id="0eb5c-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="0eb5c-137">À medida que os dados ficam disponíveis, envie os bytes para o cliente ou buffer, pois os segmentos de dados estão disponíveis e envie por qualquer meio desejado:</span><span class="sxs-lookup"><span data-stu-id="0eb5c-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="0eb5c-138">Quando a exportação for concluída, se a transferência de dados e a serialização falharem, diga ao cliente para descartar os dados.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="0eb5c-139">Se a serialização tiver sido bem-sucedida, informe ao cliente que todos os dados foram transferidos e a importação pode começar:</span><span class="sxs-lookup"><span data-stu-id="0eb5c-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="0eb5c-140">Importação</span><span class="sxs-lookup"><span data-stu-id="0eb5c-140">Importing</span></span>

<span data-ttu-id="0eb5c-141">Depois de receber todos os bytes do remetente, podemos importar os dados de volta para um *WorldAnchorTransferBatch* e bloquear nosso objeto de jogo raiz para o mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="0eb5c-142">Observação: a importação, às vezes, falha transitória e precisa ser repetida:</span><span class="sxs-lookup"><span data-stu-id="0eb5c-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="0eb5c-143">Depois que um *gameobject* é bloqueado por meio da chamada *lockobject* , ele terá um *WorldAnchor* que o manterá na mesma posição física do mundo, mas pode estar em um local diferente no espaço de coordenadas do Unity do que outros usuários.</span><span class="sxs-lookup"><span data-stu-id="0eb5c-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

