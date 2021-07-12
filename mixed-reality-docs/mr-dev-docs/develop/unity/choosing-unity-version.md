---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in do Unity e XR mais recentes para HoloLens aplicativo.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603677"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Como escolher uma versão do Unity e um plug-in de XR

Embora seja recomendável instalar o **Unity 2020.3 LTS** com o plug-in OpenXR de Realidade Misturada mais recente para desenvolvimento de Realidade Misturada, você também pode criar aplicativos com outras configurações do Unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (recomendado)

A configuração atual recomendada do Unity da Microsoft para HoloLens 2 e Windows Mixed Reality é **o Unity 2020.3 LTS** com o plug-in OpenXR de Realidade Misturada mais recente. Você **deve usar** o patch do Unity versão 2020.3.8f1 ou posterior para evitar problemas de desempenho conhecidos com builds anteriores de 2020.3.

> [!IMPORTANT]
> O Unity 2020 não dá suporte ao direcionamento HoloLens (1ª geração). Esses headsets permanecem com suporte no **[Unity 2019 LTS](#unity-20194-lts)** com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.

A melhor maneira de instalar e gerenciar o Unity é por meio do **Hub do Unity:**

1. Instale <a href="https://unity3d.com/get-unity/download" target="_blank">**o Hub do Unity.**</a>
2. Selecione a **guia Instalar** e escolha **Adicionar**.
3. Selecione **Unity 2020.3 LTS** e clique em **Próximo.**

![Instalar nova versão do Hub do Unity](images/unity-hub-img-01.png)

4. Verifique os seguintes componentes em **'Plataformas':**
    * **Suporte de build da Plataforma Universal do Windows**
    * **Suporte de build do Windows (IL2CPP)**

![Opção do Unity de suporte de build da Plataforma Universal do Windows](../images/Unity_Install_Option_UWP.png)

5. Se você instalou o Unity anteriormente sem essas opções, poderá adicioná-las por meio do menu **'Adicionar Módulos'** no Hub do Unity:

![Opção do Unity de suporte de build do Windows](../images/Unity_Install_Option_UWP2.png)

Depois que o Unity 2020.3 estiver instalado, começar a criar um projeto ou atualizar um projeto existente usando o plug-in OpenXR de Realidade Misturada:

> [!div class="nextstepaction"]
> [Configurar seu projeto com o plug-in OpenXR](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> Embora seja recomendável usar o OpenXR para todos os novos projetos, o Unity 2020.3 LTS também dá suporte ao [plug-in Windows XR.](xr-project-setup.md?tabs=windowsxr) Esse plug-in tem suporte total, embora não receba novos recursos, como o suporte do AR Foundation 4.0.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Se você precisar usar o Unity 2019, poderá usar **o Unity 2019 LTS com xR integrado herdado.** Para começar a trabalhar com o XR integrado herdados no Unity 2019.4 LTS, clique aqui:

> [!div class="nextstepaction"]
> [Configurar seu projeto com o XR integrado herddo](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> O Unity preterido seu suporte de XR integrado herdado a partir do Unity 2019.  Embora o Unity 2019 ofereça uma nova estrutura de plug-in XR, a Microsoft não está recomendando esse caminho no Unity 2019 devido a incompatibilidades das Âncoras Espaciais do Azure com o AR Foundation 2.  No Unity 2020, as Âncoras Espaciais do Azure são suportadas na estrutura de plug-in XR.

Se você estiver desenvolvendo aplicativos para HoloLens (1ª geração), esses headsets permanecerão com suporte no Unity 2019 LTS com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.

## <a name="unity-20212"></a>Unity 2021.2

Se você estiver tentando os primeiros builds do **Unity 2021.2,** vá para o [**plug-in OpenXR**](xr-project-setup.md?tabs=openxr)do Mixed Reality . O plug-in OpenXR é o único caminho para o desenvolvimento de realidade misturada no Unity 2021.2 e posterior, pois a versão final do Unity para dar suporte ao plug-in Windows XR era o Unity 2021.1.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

O Unity 2018.4 LTS atingiu o final da janela de suporte do Long-Term de dois anos do Unity e não está mais recebendo atualizações do Unity, embora seus projetos continuem sendo executados.

Se você tiver um projeto do Unity 2018, considere planejar uma migração para o Unity 2020.3 LTS e o plug-in OpenXR de Realidade Misturada.