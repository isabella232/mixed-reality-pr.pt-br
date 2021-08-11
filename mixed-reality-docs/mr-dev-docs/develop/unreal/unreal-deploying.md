---
title: Implantar no dispositivo no Unreal
description: Saiba tudo o que você precisa saber sobre como implantar seus aplicativos unreal de realidade misturada HoloLens 2 usando o editor ou o portal do dispositivo.
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, implantação no dispositivo, PC, documentação, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: d6df3f9af21a0759c98306c28696d21eac7687b92d3cb74a9cd9948122cbcbcc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226628"
---
# <a name="deploy-to-device-in-unreal"></a>Implantar no dispositivo no Unreal

Há duas maneiras de implantar um aplicativo Unreal no HoloLens 2:
* Diretamente do editor do Unreal
* Como um pacote carregado por meio do portal do dispositivo

Ambas as opções exigem que você configurar seu HoloLens para usar o [portal do dispositivo](../platform-capabilities-and-apis/using-the-windows-device-portal.md) para desenvolvimento.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Implantando no dispositivo do editor do Unreal

1. Selecione a seta para baixo ao lado do **botão** Iniciar. Inicialmente, a opção HoloLens dispositivo único ficará es cinza.

![Iniciar opções de lista suspenso](images/unreal/launch-dropdown.png)

2. Abra o **Gerenciador de Dispositivos** e observe que o HoloLens não aparecerá automaticamente na lista de dispositivos.

3. Expanda **a seção Adicionar um dispositivo não listado.**

4. Selecione **HoloLens** como sua **Plataforma.**

5. Insira o endereço IP e as informações de porta dos dispositivos separados por dois-pontos como o identificador do dispositivo. Por exemplo, "127.0.0.1:10080" (quando conectado via USB). Use suas credenciais Portal de Dispositivos nome de usuário e senha.

6. Em **Adicionar e** feche o gerenciador de dispositivos.
    * Se houver um erro, como endereço errado ou credenciais de usuário, uma mensagem será impressa no Log de Saída.

![Adicionando um dispositivo não na lista](images/unreal/add-unlisted-device.png)

7. Selecione a seta para baixo ao lado do **botão** Iniciar novamente – desta vez, você deverá ver HoloLens dispositivo que acabou de adicionar. Selecione o HoloLens para criar e implantar em seu HoloLens.

>[!NOTE]
>A criação do dispositivo pode envolver sombreadores de recomilação (especialmente na primeira vez) – isso pode levar algum tempo. Não deixe o dispositivo ficar em sleep até que o aplicativo seja executado (talvez seja preciso usá-lo). Caso contrário, a compilação do sombreador falhará!

## <a name="deploying-to-device-via-device-portal"></a>Implantando no dispositivo por meio do portal do dispositivo

Você pode encontrar instruções detalhadas sobre como empacotar e implantar um aplicativo na série [de tutoriais do Unreal](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unreal que lançamos, você está no meio do estágio de implantação. A partir daqui, você pode continuar adicionando serviços avançados:

> [!div class="nextstepaction"]
> [Serviços avançados](unreal-development-overview.md#5-adding-services)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) a qualquer momento.
