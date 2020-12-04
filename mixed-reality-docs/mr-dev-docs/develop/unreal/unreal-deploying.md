---
title: Implantar no dispositivo no Unreal
description: Um guia para a implantação no dispositivo de não real para o HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, implantar em dispositivo, PC, documentação, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: ef33e037d6ab6a69059c1452b71a428fe51836b9
ms.sourcegitcommit: d56e7dd6c917ddc4ead0792ebff21891921174b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564016"
---
# <a name="deploy-to-device-in-unreal"></a>Implantar no dispositivo no Unreal

## <a name="overview"></a>Visão geral
Há duas maneiras de implantar um aplicativo inreal no HoloLens 2:
* Diretamente do editor inreal
* Como um pacote carregado por meio do portal do dispositivo

As duas opções exigem que você configure seu HoloLens para usar o [portal do dispositivo](../platform-capabilities-and-apis/using-the-windows-device-portal.md) para desenvolvimento.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Implantando no dispositivo do editor inreal

1. Clique na seta suspensa ao lado do botão **Iniciar** . Inicialmente, a opção do dispositivo HoloLens ficará esmaecida.

![Opções de menu suspenso de inicialização](images/unreal/launch-dropdown.png)

2. Abra o **Device Manager**. Observe que seu HoloLens não aparecerá automaticamente na lista de dispositivos.

3. Expanda a seção **Adicionar um dispositivo não listado** .

4. Selecione **HoloLens** como sua **plataforma**.

5. Insira o endereço IP e as informações de porta dos dispositivos separados por dois-pontos como o identificador do dispositivo. Por exemplo, "127.0.0.1:10080" (quando conectado via USB). Use as credenciais de nome de usuário e senha do portal do dispositivo.

6. Clique em **Adicionar** e feche o Gerenciador de dispositivos.
    * No caso de um erro (como endereço incorreto, nome de usuário ou senha), uma mensagem será impressa no log de saída.

![Adicionando um dispositivo não listado](images/unreal/add-unlisted-device.png)

7. Clique na seta suspensa ao lado do botão **Iniciar** novamente. desta vez, você verá o dispositivo HoloLens que você acabou de adicionar. Selecione o dispositivo HoloLens para compilar e implantar em seu HoloLens.

>[!NOTE]
>A criação para o dispositivo pode envolver a recompilação de sombreadores (especialmente na primeira execução) – isso pode levar algum tempo. Não deixe que o dispositivo vá para o estado de suspensão até que o aplicativo esteja em execução (talvez você precise fazê-lo). Caso contrário, haverá falha na compilação do sombreador!

## <a name="deploying-to-device-via-device-portal"></a>Implantando no dispositivo por meio do portal do dispositivo

Você pode encontrar instruções detalhadas sobre como [empacotar e implantar um aplicativo](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) na última seção do introdução com séries de tutoriais não reais.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento inreal, você estará no meio do estágio de implantação. A partir daqui, você pode continuar a adicionar serviços avançados:

> [!div class="nextstepaction"]
> [Serviços avançados](unreal-development-overview.md#5-adding-services)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) a qualquer momento.
