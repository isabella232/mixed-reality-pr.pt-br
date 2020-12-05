---
title: Controladores de reverbo do HP G2 em um não real
description: Instruções sobre como usar os controladores de reverberação HP reverbo G2 em OpenXR e SteamVR
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Inreal, mecanismo 4, UE4, reverberação, reverbo G2, HP reverbs G2, realidade misturada, desenvolvimento, controladores de movimento, entrada do usuário, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 419f5b803a6abb2b19080807ef9f403b96758683
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609587"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Controladores de reverbo do HP G2 em um não real 

## <a name="getting-started"></a>Introdução

> [!IMPORTANT]
> O mecanismo inreal 4,26 e o OpenXR ou o SteamVR são necessários para acessar o plug-in do controlador HP Motion, você precisará trabalhar com os controladores de reverberação da HP.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Portando um aplicativo OpenXR existente 

Se nenhuma associação de controlador existir no jogo para o controlador HP Mixed Reality, o tempo de execução do OpenXR tentará remapear as ligações existentes para o controlador ativo.  Nesse caso, o jogo tem ligações Oculus Touch e nenhuma associação de controlador HP Mixed Reality.

![Remapeando associações existentes quando não existe nenhuma associação de controlador](images/reverb-g2-img-04.png)

Os eventos ainda serão acionados, mas se o jogo precisar usar associações específicas do controlador, como o botão de menu à direita, o perfil de interação da realidade mista HP deverá ser usado.  Várias associações de controlador podem ser especificadas por ação para dar melhor suporte a dispositivos diferentes.
   
![Usando associações de vários controladores](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Adicionando mapeamentos de ação de entrada 

Defina uma nova ação e mapeie para um dos pressionamentos de tecla na seção controlador HP Mixed Reality.

![Definindo novas ações e mapeamentos](images/reverb-g2-img-02.png)

O controlador do HP reverberar G2 também tem uma alça analógica, que pode ser usada nos mapeamentos de eixo com a associação "eixo de squeeze".  Há uma associação squeeze separada, que deve ser usada para mapeamentos de ação quando o botão de fixação é totalmente pressionado. 

![Usando as associações de eixo de squeeze](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Adicionando eventos de entrada

Clique com o botão direito do mouse em um plano gráfico e procure os novos nomes de ação do sistema de entrada para adicionar eventos para essas ações.  Aqui, o plano gráfico está respondendo aos eventos com uma cadeia de caracteres de impressão gerando o botão atual e o estado do eixo.

![Plano gráfico respondendo a eventos e gerando o estado atual do botão e do eixo](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Usando entrada 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Confira também
* [Entrada SteamVR](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Usando o SteamVR com o Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Câmera do Player não real](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)