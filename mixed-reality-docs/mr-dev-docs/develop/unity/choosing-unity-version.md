---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in do Unity e XR mais recentes para o desenvolvimento de aplicativos holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: da171db41e508fe556d8645b23f12f6f437446a1
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908228"
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

* Aplicativos de comunicação de comunicação Plataforma Universal do Windows aplicativo holográfico usando Plataforma Universal do Windows de build não estão funcionando.
* O sistema de trabalhos gráficos do Unity é padrão, embora não seja compatível com projetos do HoloLens.

Se você optar por iniciar um novo projeto no Unity 2020 hoje, certifique-se de acompanhar nos próximos meses para builds atualizados do Unity e builds de plug-in do Windows XR antes de enviar seu aplicativo.  Isso garantirá que os usuários experimentem a estabilidade adequada do holograma.

> [!div class="nextstepaction"]
> [Como usar o plug-in de XR do Windows](windows-xr-plugin.md)

### <a name="using-openxr"></a>Usando OpenXR

O Unity 2020.3 LTS também dá suporte a uma visualização pública do plug-in **OpenXR de Realidade Misturada.**

O plug-in OpenXR de Realidade Misturada dá suporte total ao AR Foundation 4.0, fornecendo implementações ARPlaneManager e ARRaycastManager. Isso permite que você escreva um código de teste de clique uma vez que abrange os telefones e tablets holoLens 2 e ARCore/ARKit. 

Posteriormente neste ano, **o Unity 2020.3 LTS** com o plug-in OpenXR se tornará a configuração recomendada do Unity e os futuros recursos do HoloLens 2 no Unity serão expostos somente por meio desse plug-in.

> [!div class="nextstepaction"]
> [Usando o plug-in OpenXR](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021.1

Se você estiver tentando criar builds do **Unity 2021.1** no início, vá para o **plug-in OpenXR,** pois o plug-in do Windows XR foi preterido lá.  A partir do Unity 2021.2, o plug-in OpenXR será o único caminho para o desenvolvimento de Realidade Misturada, pois o plug-in do Windows XR não terá mais suporte.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Se você já tiver um projeto usando o Unity 2018.4 LTS, o mecanismo do Unity continuará com suporte por dois anos após seu lançamento.  O Unity 2018 LTS atingirá o fim do serviço na fonte de 2021.