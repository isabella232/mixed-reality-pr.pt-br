---
title: Âncoras Espaciais locais no Unreal
description: Saiba como usar, salvar e gerenciar âncoras espaciais em aplicativos de realidade misturada do Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, âncoras espaciais, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: d44610ea0632dbc93941096007e60e4ae7be53e1
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009976"
---
# <a name="local-spatial-anchors-in-unreal"></a>Âncoras Espaciais locais no Unreal

As âncoras espaciais salvam hologramas no espaço do mundo real entre as sessões do aplicativo como **ARPin** s. Depois de salvos no repositório de âncoras do HoloLens, os ARPins podem ser carregados em sessões futuras e são uma opção de fallback ideal quando não há conectividade com a Internet.

> [!NOTE]
> As funções de âncora do UE 4.25 estão obsoletas na versão 4.26 e devem ser substituídas por outras mais recentes. 

> [!IMPORTANT]
> Elas são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem. Se você pretende usar os serviços de nuvem do Azure para armazenar suas âncoras, temos um documento que pode orientar você na integração das [Âncoras Espaciais do Azure](unreal-azure-spatial-anchors.md). Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.

## <a name="checking-the-anchor-store"></a>Como verificar o repositório de âncoras

Antes de salvar ou carregar âncoras, você precisa verificar se o repositório de âncoras está pronto.  A chamada de uma das funções de âncora do HoloLens antes que o repositório de âncoras esteja pronto não terá êxito.  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a>Como salvar âncoras

Quando o aplicativo tem um componente que você precisa fixar no mundo, ele pode ser salvo no repositório de âncoras com a seguinte sequência: 

[!INCLUDE[](includes/tabs-sa-2.md)]

Passo a passo detalhado:
1. Gere um ator em um local conhecido.
2. Crie um **ARPin** com esse local e um nome com base na classe do ator. 
3. Adicione o ator ao **ARPin** e salve o marcador no repositório de âncoras do HoloLens.  
    * O nome da âncora que você escolhe, que neste exemplo é o carimbo de data/hora atual, precisa ser exclusivo. 

4. Se a âncora for salva com êxito no repositório de âncoras, você poderá vê-la no portal do dispositivo do HoloLens em **Sistema > Gerenciador de mapas > Arquivos de Âncora Salvos no Dispositivo**. 

## <a name="loading-anchors"></a>Como carregar âncoras

Quando um aplicativo é iniciado, é possível usar o blueprint a seguir para restaurar os componentes aos respectivos locais de âncora:

[!INCLUDE[](includes/tabs-sa-3.md)]

Passo a passo detalhado:
1. Itere por todas as âncoras no repositório de âncoras. 
2. Gere um ator na identidade.
3. Fixe esse ator no **ARPin** do repositório de âncoras.  

    * É importante gerar o ator na identidade, uma vez que a âncora é responsável por reposicionar o holograma no mundo com base no local em que ele foi salvo. Transformações adicionadas aqui adicionarão um deslocamento à âncora. 

A ID da âncora também é consultada para que atores diferentes possam ser gerados dependendo do nome salvo da âncora. 

## <a name="removing-anchors"></a>Como remover âncoras 

Quando terminar de usar uma âncora, limpe âncoras individuais ou o repositório de âncoras inteiro com os componentes **Remover ARPin do Repositório WMRAnchor** e **Remover Todos os ARPins do Repositório WMRAnchor**.

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> Tenha em mente que as Âncoras Espaciais ainda estão na versão beta, portanto, lembre-se de conferir este material novamente para obter informações e recursos atualizados.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se está seguindo o percurso de desenvolvimento do Unreal que estabelecemos, você está no meio da exploração dos principais blocos de construção do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção: 

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
