---
title: Entrada olhar em não real
description: Tutorial sobre como configurar a entrada de olhar para o HoloLens e o mecanismo inreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens 2, controle de olho, entrada de olhar, exibição montada de cabeçalho, mecanismo inreal, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679045"
---
# <a name="gaze-input"></a>Entrada olhar

## <a name="overview"></a>Visão geral

O [plug-in do Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) não fornece funções internas para entrada olhar, mas o HoloLens 2 dá suporte ao acompanhamento de olho. Os recursos de acompanhamento reais são fornecidos por APIs de exibição e acompanhamento de cabeça e de **controle de olhos** **desmontadas** e incluem:

- Informações do dispositivo
- Sensores de acompanhamento
- Orientação e posição
- Painéis de recorte
- Informações de rastreamento e dados do olhar

Você pode encontrar a lista completa de recursos na documentação de exibição e [controle de olho](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) do [rumo](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) .

Além das APIs inreais, confira a documentação sobre a [interação baseada em olhar](../../design/eye-gaze-interaction.md) para o hololens 2 e leia como o [controle de olhos no hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) funciona.

> [!IMPORTANT]
> Só há suporte para acompanhamento de olho no HoloLens 2.

## <a name="enabling-eye-tracking"></a>Habilitando o acompanhamento de olho
A entrada olhar precisa ser habilitada nas configurações do projeto do HoloLens antes que você possa usar qualquer uma das APIs inreais. Quando o aplicativo for iniciado, você verá um prompt de consentimento mostrado na captura de tela abaixo.

- Selecione **Sim** para definir a permissão e obter acesso à entrada olhar. Se você precisar alterar essa configuração a qualquer momento, ela poderá ser encontrada no aplicativo **configurações** .

![Permissões de entrada de olho](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> O controle de olhos do HoloLens em tempo inreal tem apenas um único olhar Ray para ambos os olhos, em vez dos dois raios necessários para o acompanhamento do estereoscópico, o que não é suportado.

Essa é a configuração que você precisará para começar a adicionar a entrada olhar aos seus aplicativos do HoloLens 2 em um não real. Mais informações sobre a entrada do olhar e como isso afeta os usuários em realidade misturada podem ser encontradas nos links abaixo. Lembre-se de pensar nisso ao criar suas experiências interativas.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal, você está no meio da exploração dos principais blocos de construção do MRTK. De lá, você pode prosseguir para o próximo bloco de construção: 

> [!div class="nextstepaction"]
> [Acompanhamento da mão](unreal-hand-tracking.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Câmera do HoloLens](unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Veja também
* [Calibragem](../../calibration.md)
* [Conforto](../../design/comfort.md)
* [Focar e confirmar](../../design/gaze-and-commit.md)
* [Entrada de voz](../../out-of-scope/voice-design.md)
