---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in do Unity e XR mais recentes para o desenvolvimento de aplicativos holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080693"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Como escolher uma versão do Unity e um plug-in de XR

Embora seja recomendável instalar o **Unity 2020.3 LTS** com o plug-in OpenXR de Realidade Misturada mais recente para desenvolvimento de Realidade Misturada, você também pode criar aplicativos com outras configurações do Unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (recomendado)

A configuração atual recomendada do Unity da Microsoft para o holoLens 2 e Windows Mixed Reality desenvolvimento é **o Unity 2020.3 LTS** com o plug-in OpenXR de Realidade Misturada mais recente. Você DEVE usar o patch do Unity versão 2020.3.8f1 ou posterior para evitar problemas de desempenho conhecidos com builds anteriores de 2020.3.

> [!IMPORTANT]
> O Unity 2020 não dá suporte ao direcionamento do HoloLens (1ª geração). Esses headsets permanecem com suporte no **[Unity 2019 LTS](#unity-20194-lts)** com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.
>
> [!NOTE]
> Azure Remote Rendering ainda não enviou uma versão atualizada com suporte ao Unity 2020.
>
> Se o projeto do Unity usar Azure Remote Rendering, recomendamos manter a atualização do projeto para o Unity 2020 até que um pacote atualizado seja disponibilizado.

A melhor maneira de instalar e gerenciar o Unity é por meio do <a href="https://unity3d.com/get-unity/download" target="_blank">Hub do Unity</a>. Quando ele estiver instalado, abra o Hub do Unity:

1. Selecione a **guia Instalar e** escolha **ADICIONAR**
2. Selecione Unity 2020.3 LTS e clique em **Próximo**

![Nova versão instal do hub do Unity](images/unity-hub-img-01.png)

3. Verifique os componentes a seguir **em 'Plataformas'**
    * **Suporte de build da Plataforma Universal do Windows**
    * **Suporte de build do Windows (IL2CPP)**

![Opção do Unity de suporte de build da Plataforma Universal do Windows](../images/Unity_Install_Option_UWP.png)

4. Se você instalou o Unity sem essas opções, poderá adicioná-las por meio do menu **'Adicionar Módulos'** no Hub do Unity:

![Opção do Unity de suporte de build do Windows](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [Usando o plug-in OpenXR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> Embora seja recomendável usar o OpenXR para todos os novos projetos, o Unity 2020.3 LTS também dá suporte ao [plug-in do Windows XR.](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr) Esse plug-in tem suporte total, embora não receba novos recursos, como o suporte do AR Foundation 4.0.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Se você precisar usar o Unity 2019, poderá usar **o Unity 2019 LTS com xR integrado herdado.** Para começar a trabalhar com o XR integrado herdados no Unity 2019.4 LTS, clique aqui:

> [!div class="nextstepaction"]
> [Configurar o XR integrado herddo](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> O Unity preterido seu suporte de XR integrado herdado a partir do Unity 2019.  Embora o Unity 2019 ofereça uma nova estrutura de plug-in XR, a Microsoft não está recomendando esse caminho no Unity 2019 devido a incompatibilidades das Âncoras Espaciais do Azure com o AR Foundation 2.  No Unity 2020, as Âncoras Espaciais do Azure são suportadas na estrutura de plug-in XR.

Se você estiver desenvolvendo aplicativos para HoloLens (1ª geração), esses headsets permanecerão com suporte no Unity 2019 LTS com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.

## <a name="unity-20211"></a>Unity 2021.1

Se você estiver tentando criar builds do **Unity 2021.1** no início, vá para o **plug-in OpenXR,** pois o plug-in do Windows XR foi preterido lá.  A partir do Unity 2021.2, o plug-in OpenXR será o único caminho para o desenvolvimento de Realidade Misturada, pois o plug-in do Windows XR não terá mais suporte.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Se você já tiver um projeto usando o Unity 2018.4 LTS, o mecanismo do Unity continuará com suporte por dois anos após seu lançamento.  O Unity 2018 LTS atingirá o fim do serviço na fonte de 2021.
