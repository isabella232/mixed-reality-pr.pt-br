---
title: Âncoras Espaciais locais no Unreal
description: Guia para uso de âncoras espaciais em Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: d223c451cbbf0fb4e2cc1392394d2fe771ec8069
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91696134"
---
# <a name="local-spatial-anchors-in-unreal"></a>Âncoras Espaciais locais no Unreal

## <a name="overview"></a>Visão geral

As âncoras espaciais são usadas para salvar os hologramas no espaço do mundo real entre as sessões do aplicativo. Elas são exibidas por meio do Unreal como **ARPin** s e são salvas no repositório de âncoras do HoloLens, que é carregado em sessões futuras. As âncoras locais são ideais como fallback quando não há nenhuma conectividade com a Internet.

> [!IMPORTANT]
> Elas são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem. Se você pretende usar os serviços de nuvem do Azure para armazenar suas âncoras, temos um documento que pode orientar você na integração das [Âncoras Espaciais do Azure](unreal-azure-spatial-anchors.md). Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.

## <a name="checking-the-anchor-store"></a>Como verificar o repositório de âncoras

Antes de salvar ou carregar âncoras, você precisa verificar se o repositório de âncoras está pronto.  A tentativa de chamar qualquer uma das funções de âncora do HoloLens antes que o repositório de âncora esteja pronto não terá sucesso.  

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>Como salvar âncoras

Quando o aplicativo tem um componente que precisa ser fixado no mundo, ele pode ser salvo no repositório de âncoras com a seguinte sequência: 

![Salvar âncoras espaciais](images/unreal-spatialanchors-save.PNG)

Passo a passo detalhado:
1. Gere um ator em um local conhecido.
2. Crie um **ARPin** com esse local e um nome com base na classe do ator. 
3. Adicione o ator ao **ARPin** e salve o marcador no repositório de âncoras do HoloLens.  
    * O nome da âncora que você escolhe, que neste exemplo é o carimbo de data/hora atual, precisa ser exclusivo. 

4. Se a âncora for salva com êxito no repositório de âncoras, você poderá inspecioná-la no portal do dispositivo do HoloLens em **Sistema > Gerenciador de mapas > Arquivos de Âncora Salvos no Dispositivo** . 

## <a name="loading-anchors"></a>Como carregar âncoras

Quando um aplicativo é iniciado, é possível usar o blueprint a seguir para restaurar os componentes aos respectivos locais de âncora:

![Carregar âncoras espaciais](images/unreal-spatialanchors-load.PNG)

Passo a passo detalhado:
1. Itere por todas as âncoras no repositório de âncoras. 
2. Gere um ator na identidade.
3. Fixe esse ator no **ARPin** do repositório de âncoras.  

    * É importante gerar o ator na identidade, uma vez que a âncora é responsável por reposicionar o holograma no mundo com base no local em que ele foi salvo. Transformações adicionadas aqui adicionarão um deslocamento à âncora. 

A ID da âncora também é consultada para que atores diferentes possam ser gerados dependendo do nome salvo da âncora. 

## <a name="removing-anchors"></a>Como remover âncoras 

Quando você terminar de usar uma âncora, poderá limpar âncoras individuais ou o repositório de âncoras inteiro com os componentes **Remover ARPin do Repositório WMRAnchor** e **Remover Todos os ARPins do Repositório WMRAnchor** .

![Remover âncoras espaciais](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> Tenha em mente que as Âncoras Espaciais ainda estão na versão beta, portanto, lembre-se de conferir este material novamente para obter informações e recursos atualizados.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso de pontos de verificação de desenvolvimento do Unreal, está no meio da exploração dos principais blocos de construção do MRTK. A partir daí, você pode prosseguir para o próximo bloco de construção: 

> [!div class="nextstepaction"]
> [Âncoras Espaciais do Azure](unreal-azure-spatial-anchors.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Câmera do HoloLens](unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Veja também
* [Âncoras Espaciais do Azure](unreal-azure-spatial-anchors.md)
* [Âncoras espaciais](../../design/spatial-anchors.md)
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
