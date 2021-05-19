---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in do Unity e XR mais recentes para o desenvolvimento de aplicativos holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: 3bdaa35f495d7a647a7cbf37ddcd4f85e96d74d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143669"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Como escolher uma versão do Unity e um plug-in de XR

Embora seja recomendável instalar o **Unity 2019.4 LTS** e usar o XR integrado herdado para desenvolvimento de Realidade Misturada, você também pode criar aplicativos com outras configurações do Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (recomendado)

A configuração atual recomendada do Unity da Microsoft para o desenvolvimento do HoloLens 2 e Windows Mixed Reality é **o Unity 2019.4 LTS** usando o suporte herdado a XR.

A melhor maneira de instalar e gerenciar o Unity é por meio <a href="https://unity3d.com/get-unity/download" target="_blank">do [Hub do Unity].</a> Quando ele estiver instalado, abra o Hub do Unity:

1. Selecione a **guia Instalar e** escolha **ADICIONAR**
2. Selecione Unity 2019.4 LTS e clique em **Próximo**

![Nova versão instal do hub do Unity](images/unity-hub-img-01.png)

3. Verifique os componentes a seguir **em 'Plataformas'**
    * **Suporte de build da Plataforma Universal do Windows** 
    * **Suporte de build do Windows (IL2CPP)**

![Opção do Unity de suporte de build da Plataforma Universal do Windows](../images/Unity_Install_Option_UWP.png)

4. Se você instalou o Unity sem essas opções, poderá adicioná-las por meio do menu **'Adicionar Módulos'** no Hub do Unity:

![Opção do Unity de suporte de build do Windows](../images/Unity_Install_Option_UWP2.png)

Para começar a trabalhar com o XR integrado herdados no Unity 2019.4 LTS, clique aqui:

> [!div class="nextstepaction"]
> [Configurar o XR integrado herddo](legacy-xr-support.md)

> [!NOTE]
> O Unity preterido seu suporte de XR integrado herdado a partir do Unity 2019.  Embora o Unity 2019 ofereça uma nova estrutura de plug-in XR, a Microsoft não está recomendando esse caminho no Unity 2019 devido a incompatibilidades das Âncoras Espaciais do Azure com o AR Foundation 2.  No Unity 2020, as Âncoras Espaciais do Azure são suportadas na estrutura de plug-in XR.

Se você estiver desenvolvendo aplicativos para HoloLens (1ª geração), esses headsets permanecerão com suporte no Unity 2019 LTS com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

Se você estiver usando **o Unity 2020.3 LTS,** poderá usar o **plug-in do Windows XR** para desenvolver o HoloLens 2 e Windows Mixed Reality aplicativos.

No entanto, há problemas conhecidos que afetam a estabilidade do holograma e outros recursos no HoloLens 2: 

* Os aplicativos de comunicação remota do aplicativo Holographic usando o destino de compilação Plataforma Universal do Windows não estão funcionando.
* O sistema de trabalhos gráficos do Unity é padronizado, embora não seja compatível com projetos do HoloLens.

Se você optar por iniciar um novo projeto no Unity 2020 hoje, certifique-se de acompanhar os próximos meses para obter as compilações do Unity atualizadas e as compilações do plug-in do Windows XR antes de enviar seu aplicativo.  Isso garantirá que seus usuários tenham a estabilidade correta do holograma.

> [!div class="nextstepaction"]
> [Como usar o plug-in de XR do Windows](windows-xr-plugin.md)

### <a name="using-openxr"></a>Usando OpenXR

O Unity 2020,3 LTS também dá suporte a uma visualização pública do plug-in **OpenXR da realidade mista** .

O plug-in Mixed Reality OpenXR dá suporte total ao AR Foundation 4,0, fornecendo implementações ARPlaneManager e ARRaycastManager. Isso permite que você escreva um código de teste de clique uma vez que se estenda a telefones 2 e ARCore/ARKit celulares e tablets. 

Posteriormente neste ano, o **unity 2020,3 LTS com o plug-in OpenXR** se tornará a configuração de Unity recomendada e futuros recursos do HoloLens 2 no Unity serão expostos somente por meio desse plug-in.

> [!div class="nextstepaction"]
> [Usando o plug-in OpenXR](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021,1

Se você estiver experimentando compilações iniciais do **Unity 2021,1** , deverá avançar para o **plug-in do OpenXR**, pois o plug-in do Windows XR foi preterido lá.  A partir do Unity 2021,2, o plug-in OpenXR será o único caminho para o desenvolvimento de realidade misturada, pois o plug-in do Windows XR não terá mais suporte.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Se você já tiver um projeto usando o Unity 2018,4 LTS, o seu mecanismo do Unity continuará a ter suporte por dois anos após seu lançamento.  O Unity 2018 LTS atingirá o fim do serviço no Spring de 2021.
