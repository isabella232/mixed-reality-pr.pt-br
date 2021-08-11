---
title: Controladores do HP Reverb G2 no Unreal
description: Saiba como usar os novos controladores HP Reverb G2 no OpenXR e no SteamVR para aplicativos de realidade misturada do Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, Reverb, Reverb G2, HP Reverb G2, realidade misturada, desenvolvimento, controladores de movimento, entrada do usuário, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: b287a5c7de1ea086b76228d9109cc07a4e1569f5f926cb42dc3e37cc2a3bb916
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204148"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Controladores do HP Reverb G2 no Unreal 

## <a name="getting-started"></a>Introdução

> [!IMPORTANT]
> O Unreal Engine 4.26 e o OpenXR ou o SteamVR são necessários para acessar o plug-in do Controlador de Movimento HP. Você precisará trabalhar com os controladores HP Reverb G2.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Portando um aplicativo OpenXR existente 

Se não existir nenhuma associação de controlador no jogo para o Controlador de Realidade Misturada hp, o runtime do OpenXR tentará remapear as vinculações existentes para o controlador ativo.  Nesse caso, o jogo tem vinculações do Oculus Touch e nenhuma associação do HP Mixed Reality Controller.

![Remapeando as vinculações existentes quando não há nenhuma associação de controlador](images/reverb-g2-img-04.png)

Os eventos ainda serão ativas, mas se o jogo precisar usar as vinculações específicas do controlador, como o botão de menu à direita, o perfil de interação da HP Mixed Reality deverá ser usado.  Várias vinculações de controlador podem ser especificadas por ação para dar melhor suporte a dispositivos diferentes.
   
![Usando várias vinculações de controlador](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Adicionando mapeamentos de ação de entrada 

Defina uma nova ação e mapeie para uma das teclas pressionadas na seção Controlador de Realidade Misturada da HP.

![Definindo novas ações e mapeamentos](images/reverb-g2-img-02.png)

O controlador HP Reverb G2 também tem uma mão análoga, que pode ser usada nos mapeamentos de eixo com a associação "Eixo De Eixo Eixo".  Há uma associação Desaperte separada, que deve ser usada para mapeamentos de ação quando o botão de controle é totalmente pressionado. 

![Usando as vinculações do eixo Desapertamento](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Adicionando eventos de entrada

Clique com o botão direito do mouse em um Blueprint e pesquise os novos nomes de ação do sistema de entrada para adicionar eventos para essas ações.  Aqui, o Blueprint está respondendo aos eventos com uma cadeia de caracteres de impressão que saída do estado atual do botão e do eixo.

![Blueprint respondendo a eventos e saída do botão atual e do estado do eixo](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Usando entrada 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Confira também
* [Entrada do SteamVR](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Usando o SteamVR com Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Câmera do Unreal Player](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)