---
title: Escolhendo uma versão do Unity e um plug-in XR
description: Mantenha-se atualizado sobre as recomendações de plug-in mais recentes do Unity e do XR para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938095"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Escolhendo uma versão do Unity e um plug-in XR

Embora, no momento, **recomendamos a instalação do Unity 2019,4 LTS e o uso da XR interna herdada** para o desenvolvimento de realidade misturada, você também pode criar aplicativos com outras configurações do Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019,4 LTS (recomendado)

A configuração atual do Unity recomendada pela Microsoft para o HoloLens 2 e o desenvolvimento de realidade mista do Windows é o **Unity 2019,4 LTS usando o suporte interno a XR herdado** .

A melhor maneira de instalar e gerenciar o Unity é por meio do <a href="https://unity3d.com/get-unity/download" target="_blank">[Hub do Unity]</a>. Quando ele estiver instalado, abra o Hub do Unity:

1. Selecione a guia **instalações** e escolha **Adicionar**
2. Selecione Unity 2019,4 LTS e clique em **Avançar**

![Instalar nova versão do Hub do Unity](images/unity-hub-img-01.png)

3. Verifique os seguintes componentes em **' plataformas '**
    * **Suporte à compilação de Plataforma Universal do Windows** 
    * **Suporte à compilação do Windows (IL2CPP)**

![Opção de suporte de Build Plataforma Universal do Windows do Unity](../images/Unity_Install_Option_UWP.png)

4. Se você instalou o Unity sem essas opções, poderá adicioná-los por meio do menu **' Adicionar módulos '** no Hub do Unity:

![Opção de suporte de compilação do Windows Unity](../images/Unity_Install_Option_UWP2.png)

Para começar a usar a XR interna herdada no Unity 2019,4 LTS, clique aqui:

> [!div class="nextstepaction"]
> [Configurar a XR interna herdada](legacy-xr-support.md)

> [!NOTE]
> O Unity preteriu seu suporte interno de XR herdado a partir do Unity 2019.  Embora o Unity 2019 ofereça uma nova estrutura de plug-ins XR, a Microsoft não recomenda esse caminho no Unity 2019 devido a incompatibilidades de âncoras espaciais do Azure com o AR Foundation 2.  No Unity 2020, há suporte para âncoras espaciais do Azure na estrutura de plug-ins do XR.

Se você estiver desenvolvendo aplicativos para o HoloLens (1º gen), esses headsets permanecerão com suporte no Unity 2019 LTS com a XR interna herdada para o ciclo de vida completo do Unity 2019 LTS até o Mid-2022.

## <a name="unity-20203-lts"></a>Unity 2020,3 LTS 

Se você estiver usando o **Unity 2020,3 LTS**, poderá usar o **plug-in do Windows XR** para desenvolver aplicativos do HoloLens 2 e do Windows Mixed Reality.

No entanto, há problemas conhecidos que afetam a estabilidade do holograma e outros recursos no HoloLens 2: 

* O envio do buffer de profundidade foi regressivo nas compilações recentes do Unity 2020, o que resulta em instabilidade de holograma grave.
* Os aplicativos de comunicação remota do aplicativo Holographic usando o destino de compilação Plataforma Universal do Windows não estão funcionando.
* O sistema de trabalhos gráficos do Unity é padronizado, embora não seja compatível com projetos do HoloLens.

Se você optar por iniciar um novo projeto no Unity 2020 hoje, certifique-se de acompanhar os próximos meses para obter as compilações do Unity atualizadas e as compilações do plug-in do Windows XR antes de enviar seu aplicativo.  Isso garantirá que seus usuários tenham a estabilidade correta do holograma.

> [!div class="nextstepaction"]
> [Usando o plug-in do Windows XR](windows-xr-plugin.md)

### <a name="using-openxr"></a>Usando OpenXR

O Unity 2020,3 LTS também dá suporte a uma visualização pública do plug-in **OpenXR da realidade mista** .

O plug-in Mixed Reality OpenXR dá suporte total ao AR Foundation 4,0, fornecendo implementações ARPlaneManager e ARRaycastManager. Isso permite que você escreva um código de teste de clique uma vez que se estenda a telefones 2 e ARCore/ARKit celulares e tablets. 

Posteriormente neste ano, o **unity 2020,3 LTS com o plug-in OpenXR** se tornará a configuração de Unity recomendada e futuros recursos do HoloLens 2 no Unity serão expostos somente por meio desse plug-in.  Você pode iniciar seu projeto aqui por enquanto, se seu projeto tiver como alvo o HoloLens 2, você encontrará atualmente a estabilidade do holograma do Unity 2020 e outros problemas listados acima.  Certifique-se de voltar nos próximos meses para obter as compilações do Unity atualizadas e as compilações do plug-in OpenXR antes de enviar seu aplicativo.  Isso garantirá que seus usuários tenham a estabilidade correta do holograma. 

> [!div class="nextstepaction"]
> [Usando o plug-in OpenXR](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021,1

Se você estiver experimentando compilações iniciais do **Unity 2021,1** , deverá avançar para o **plug-in do OpenXR**, pois o plug-in do Windows XR foi preterido lá.  A partir do Unity 2021,2, o plug-in OpenXR será o único caminho para o desenvolvimento de realidade misturada, pois o plug-in do Windows XR não terá mais suporte.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Se você já tiver um projeto usando o Unity 2018,4 LTS, o seu mecanismo do Unity continuará a ter suporte por dois anos após seu lançamento.  O Unity 2018 LTS atingirá o fim do serviço no Spring de 2021.
