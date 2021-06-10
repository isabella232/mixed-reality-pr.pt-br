---
title: Controladores no MRTK
description: Documentação sobre como usar vários controladores com o MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, controladores, HP reverbera, oculus, HTC Naopak, mãos
ms.openlocfilehash: 111ebf2b1eb26bbef8cde16832f780acfa758595
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743588"
---
# <a name="controllers-in-mrtk"></a>Controladores no MRTK

O MRTK tem suporte para vários controladores diferentes. Muitos controladores, como o HTC Naopak Knuckles e as varinhas de Naopak do HTC, funcionarão de forma nativa quando um aplicativo criado com MRTK for iniciado no dispositivo compatível. Outros controladores, como as mãos articuladas na Quest Oculus e os controladores de reverberação HP reverbo G2, exigem pacotes adicionais antes de serem reconhecidos pelo MRTK.

Este documento descreverá os cenários comuns em que os pacotes extras precisam ser instalados. Para obter instruções sobre como implantar em seu dispositivo, consulte as páginas de implantação do [**Hololens/WMR**](./wmr-mrtk.md) ou [**Oculus Quest**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) . Para obter informações adicionais sobre os controladores, visite a [**página recursos**](../features/input/controllers.md). Para depurar problemas com controladores, consulte a [ **ferramenta de mapeamento de controlador**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>Controladores de reverbo do HP G2

Para detectar e mostrar os controladores de reverbo do HP G2 ao usar o MRTK, siga estas etapas para instalar o pacote [**Microsoft. MixedReality. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) . Depois que esse pacote for instalado, nenhuma outra alteração nos perfis padrão precisará ser feita para que os controladores sejam exibidos no HP reverbo. 

Para exibir os controladores no editor, você precisa garantir que esteja usando o [**plug-in OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).

## <a name="oculus-controllers"></a>Controladores Oculus 

Para visualizar os modelos do controlador oculus, siga as instruções de implantação do Oculus Quest. Se você quiser mostrar as mãos virtuais ao usar os controladores, certifique-se de que **renderizar mãos de avatar em vez de controladores** esteja marcado no Oculus SDK do XR Gerenciador de dispositivos. Caso contrário, desmarque essa opção.

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)