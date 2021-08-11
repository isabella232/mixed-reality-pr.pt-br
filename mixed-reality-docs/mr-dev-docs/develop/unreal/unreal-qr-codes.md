---
title: Códigos QR no Unreal
description: Saiba como configurar, usar e controlar códigos QR em aplicativos de realidade misturada no Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, códigos qr, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 689ebe9b904b269c00078245b137bc21f2e56df2b441150c7c6b18c179ac51f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205102"
---
# <a name="qr-codes-in-unreal"></a>Códigos QR no Unreal

O HoloLens 2 pode ver códigos QR no espaço de mundo usando a webcam, que os renderiza como hologramas na posição de cada código no mundo real. O HoloLens 2 também pode renderizar os hologramas em vários dispositivos na mesma localização para criar uma experiência compartilhada. Verifique se você está seguindo as melhores práticas para adicionar códigos QR aos aplicativos:

- Zonas silenciosas
- Iluminação e pano de fundo
- Tamanho, distância e posição angular

Preste atenção especial às [considerações sobre o ambiente](/hololens/hololens-environment-considerations) quando os códigos QR estiverem sendo posicionados em seu aplicativo. Você pode encontrar mais informações sobre cada um desses tópicos e instruções sobre como baixar o pacote NuGet necessário no documento principal [rastreamento de código QR](../platform-capabilities-and-apis/qr-code-tracking.md).

> [!CAUTION]
> Os códigos QR são os únicos tipos de imagens que podem ser controlados pelo HoloLens para uso imediato. Não há suporte ao módulo **UARTrackedImage** do Unreal no HoloLens. Se precisar controlar imagens personalizadas, acesse a [webcam](unreal-hololens-camera.md) do dispositivo e processe imagens usando uma biblioteca de reconhecimento de imagem de terceiros. 

## <a name="enabling-qr-detection"></a>Como habilitar a detecção de QR

Como o HoloLens 2 precisa usar a webcam para ver os códigos QR, você precisará habilitá-la nas configurações do projeto:
- Abra **Editar > Configurações de Projeto**, role o painel até a seção **Plataformas** e selecione **HoloLens**.
    + Expanda a seção **Funcionalidades** e marque **Webcam**.  
- Você também precisará aceitar o controle de código QR [adicionando um ativo ARSessionConfig](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>Como configurar um código QR controlado

Os códigos QR são exibidos por meio do sistema de geometria controlado pelo RA do Unreal como uma imagem rastreada. Para fazer isso funcionar, você precisará:
1. Criar um Blueprint Actor e adicionar um componente **ARTrackableNotify**:

![AR Trackable Notify de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Selecionar **ARTrackableNotify** e expandir a seção **Eventos** no painel **Detalhes**:

![Eventos de QR](images/unreal-spatialmapping-events.PNG)

3. Clique em **+** ao lado de **Ao Adicionar Geometria Rastreada** para adicionar o nó ao Grafo de Eventos.
    - Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).

![Adicionar nó a Ao Adicionar Geometria Rastreada](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>Como usar um código QR controlado

O Grafo de Eventos na imagem a seguir mostra o evento **OnUpdateTrackedImage** que está sendo usado para processar um ponto no centro de um código QR e imprimir os dados desse código.

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

Isto é o que está acontecendo:
1. Primeiro, a imagem rastreada é convertida em um **ARTrackedQRCode** para verificar se a imagem atualizada atual é um código QR.  
2. Os dados codificados são recuperados da variável **QRCode**. Com o local de **GetLocalToWorldTransform**, é possível obter as coordenadas do canto superior esquerdo do código QR; já com **GetEstimateSize**, é possível obter as dimensões desse código.

Você também pode [obter o sistema de coordenadas de um código QR](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) no código.

## <a name="finding-the-unique-id"></a>Como localizar a ID exclusiva

Todo código QR tem uma ID GUID exclusiva, que pode ser encontrada:
- Arrastando e soltando o marcador **Como QRCode ARTracked** e pesquisando por **Obter ID Exclusiva**.

![GUID de QR](images/unreal-qr-guid.PNG)

Há muita coisa acontecendo nos bastidores envolvendo os códigos QR. Portanto, esse não é o final da estrada. Não deixe de conferir os links a seguir para obter mais detalhes sobre o que está acontecendo nos bastidores.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada. Daí, você pode prosseguir para o próximo tópico:

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:

> [!div class="nextstepaction"]
> [Como fazer a implantação no dispositivo](unreal-deploying.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#3-advanced-features) a qualquer momento.

## <a name="see-also"></a>Veja também
* [Mapeamento espacial](../../design/spatial-mapping.md)
* [Hologramas](../../discover/hologram.md)
* [Sistemas de coordenadas](../../design/coordinate-systems.md)