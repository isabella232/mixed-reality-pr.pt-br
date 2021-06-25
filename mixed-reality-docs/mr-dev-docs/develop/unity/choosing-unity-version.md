---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in mais recentes do Unity e do XR para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, Unity
ms.openlocfilehash: f37dbdccf175a5cea9a647f0c14b90682b19dfb3
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906845"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Como escolher uma versão do Unity e um plug-in de XR

Embora, no momento, **recomendamos a instalação do Unity 2019,4 LTS e o uso da XR interna herdada** para o desenvolvimento de realidade misturada, você também pode criar aplicativos com outras configurações do Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019,4 LTS (recomendado)

A configuração atual do Unity recomendada pela Microsoft para o HoloLens 2 e o desenvolvimento de realidade mista do Windows é o **Unity 2019,4 LTS usando o suporte interno a XR herdado** .

A melhor maneira de instalar e gerenciar o Unity é por meio do <a href="https://unity3d.com/get-unity/download" target="_blank">[Hub do Unity]</a>. Quando ele estiver instalado, abra o Hub do Unity:

1. Selecione a guia **instalações** e escolha **Adicionar**
2. Selecione Unity 2019,4 LTS e clique em **Avançar**

![Instalar nova versão do Hub do Unity](images/unity-hub-img-2019.png)

3. Verifique os seguintes componentes em **' plataformas '**
    * **Suporte de build da Plataforma Universal do Windows** 
    * **Suporte de build do Windows (IL2CPP)**

![Opção do Unity de suporte de build da Plataforma Universal do Windows](images/Unity_Install_Option_UWP_2019.png)

4. Se você instalou o Unity sem essas opções, poderá adicioná-los por meio do menu **' Adicionar módulos '** no Hub do Unity:

![Opção do Unity de suporte de build do Windows](images/Unity_Install_Option_UWP2_2019.png)

Para começar a usar a XR interna herdada no Unity 2019,4 LTS, clique aqui:

> [!div class="nextstepaction"]
> [Configurar a XR interna herdada](./xr-project-setup.md?tabs=legacy)

> [!NOTE]
> O Unity preteriu seu suporte interno de XR herdado a partir do Unity 2019.  Embora o Unity 2019 ofereça uma nova estrutura de plug-ins XR, a Microsoft não recomenda esse caminho no Unity 2019 devido a incompatibilidades de âncoras espaciais do Azure com o AR Foundation 2.  No Unity 2020, há suporte para âncoras espaciais do Azure na estrutura de plug-ins do XR.

Se você estiver desenvolvendo aplicativos para o HoloLens (1º gen), esses headsets permanecerão com suporte no Unity 2019 LTS com a XR interna herdada para o ciclo de vida completo do Unity 2019 LTS até o Mid-2022.

## <a name="unity-20203-lts"></a>Unity 2020,3 LTS 

Se você estiver usando o **Unity 2020,3 LTS**, a recomendação atual da Microsoft será o **plug-in OpenXR de realidade misturada** mais recente. Você deve usar a versão de patch do Unity 2020.3.8 F1 ou posterior para evitar problemas de desempenho conhecidos com compilações anteriores a 2020,3.

O plug-in Mixed Reality OpenXR dá suporte total ao AR Foundation 4,0, fornecendo implementações ARPlaneManager e ARRaycastManager. Isso permite que você escreva um código de teste de clique uma vez que se estenda a telefones 2 e ARCore/ARKit celulares e tablets.

No entanto, há problemas conhecidos que afetam os projetos do Unity 2020 LTS:

* O pipeline de renderização universal (URP) 10.5.0 ou mais antigo tem penalidades de desempenho em dispositivos do HoloLens 2.

Se você optar por iniciar um novo projeto no Unity 2020 hoje, certifique-se de acompanhar as próximas semanas para as compilações atualizadas do Unity e os pacotes URP antes de enviar seu aplicativo.  Isso garantirá que seus usuários tenham a estabilidade correta do holograma.

> [!div class="nextstepaction"]
> [Usando o plug-in OpenXR](./xr-project-setup.md?tabs=openxr)

## <a name="unity-20211"></a>Unity 2021,1

Se você estiver experimentando compilações iniciais do **Unity 2021,1** , deverá avançar para o **plug-in do OpenXR**, pois o plug-in do Windows XR foi preterido lá.  A partir do Unity 2021,2, o plug-in OpenXR será o único caminho para o desenvolvimento de realidade misturada, pois o plug-in do Windows XR não terá mais suporte.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Se você já tiver um projeto usando o Unity 2018,4 LTS, o seu mecanismo do Unity continuará a ter suporte por dois anos após seu lançamento.  O Unity 2018 LTS atingirá o fim do serviço no Spring de 2021.