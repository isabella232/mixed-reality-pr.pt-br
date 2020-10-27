---
title: Controladores de reverbo do HP G2 no Unity
description: Instruções sobre como usar os controladores de reverberação HP reverbo G2 no SteamVR e no Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, reverberação, reverbo G2, HP reverbs G2, realidade mista, desenvolvimento, controladores de movimento, entrada do usuário, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638383"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Controladores de reverbo do HP G2 no Unity

## <a name="getting-started"></a>Introdução

Não há nenhuma configuração adicional necessária para usar o controlador do HP reverberar G2 se você estiver desenvolvendo para SteamVR ou usando a API de entrada do Windows Mixed Reality (XR. WSA. Entrada). No entanto, os botões A, B, X, Y e o gatilho squeeze não estão acessíveis no momento por meio do Gerenciador de entrada, a menos que você esteja usando SteamVR. O suporte para as entradas adicionais de reverberação G2 estará disponível em um futuro próximo, portanto, lembre-se de verificar novamente!

## <a name="porting-existing-applications"></a>Portando aplicativos existentes

Se você já tiver um aplicativo existente que está desenvolvendo para headsets de imersão de realidade mista do Windows, confira nosso [Guia de portador](../porting-apps/porting-guides.md) e as seções de [configurações de projeto](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) para obter sugestões gerais.

## <a name="mapping-input"></a>Entrada de mapeamento

Quando estiver pronto para colocar seu mapeamento de entrada em funcionamento para seus novos controladores, comece na seção [mapeamento de entrada](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) do guia de porta de imersão. Instruções sobre como configurar entradas no Unity são detalhadas em [gestos e controladores de movimento](gestures-and-motion-controllers-in-unity.md), juntamente com um [botão completo e uma tabela de mapeamento de eixo](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) para referência.

## <a name="see-also"></a>Veja também
* [Atualizar para o SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)