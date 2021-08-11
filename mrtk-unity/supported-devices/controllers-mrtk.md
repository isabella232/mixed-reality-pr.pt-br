---
title: Detectar controladores no MRTK
description: Documentação sobre como usar vários controladores com o MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity,HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Controladores, HP Reverb, Oculus, HTC Vive, Hands
ms.openlocfilehash: 04afcf75fc11c1c3b4c6fb9f244172c0960e8943bd469bc6424465b376ceaf53
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226398"
---
# <a name="detecting-controllers-in-mrtk"></a>Detectar controladores no MRTK

O MRTK tem suporte para muitos controladores diferentes. Muitos controladores, como HTC Vive Ltds e HTC Vive Bares, funcionarão na nativo depois que um aplicativo criado com o MRTK for lançado no dispositivo compatível. Outros controladores, como mãos articuladas na Oculus Quest e nos controladores HP Reverb G2, exigem pacotes adicionais antes que sejam reconhecidos pelo MRTK.

Este documento descreverá os cenários comuns em que pacotes extras precisam ser instalados. Para obter instruções sobre como implantar em seu dispositivo, consulte as páginas de implantação [**hololens/WMR**](./wmr-mrtk.md) [**ou Oculus Deployment.**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) Para obter informações adicionais sobre controladores, visite a [**página de recursos**](../features/input/controllers.md). Para depurar problemas com controladores, consulte a [ **ferramenta de mapeamento do controlador**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>Controladores HP Reverb G2

Para detectar e mostrar os controladores HP Reverb G2 ao usar o MRTK, siga estas etapas para instalar o pacote [**Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) Depois que esse pacote for instalado, nenhuma outra alteração nos perfis padrão precisará ser feita para que os controladores sejam lançados no HP Reverb. 

Para exibir os controladores no editor, você precisa garantir que está usando o usando o Plug-in [**OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).

## <a name="oculus-controllers"></a>Controladores Oculus 

Para visualizar modelos de controlador Oculus, siga as instruções de implantação do Oculus Deployment. Se você quiser mostrar as mãos virtuais ao usar os controladores, certifique-se de que Renderizar mãos do Avatar em vez de **controladores** está marcado no SDK XR Oculus Gerenciador de Dispositivos. Caso contrário, desmarque essa opção.

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
