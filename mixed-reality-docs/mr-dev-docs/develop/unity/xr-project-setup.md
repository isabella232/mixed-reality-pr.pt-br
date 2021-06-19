---
title: Configurando sua configuração de XR
description: Mantenha-se atualizado sobre as recomendações mais recentes de configuração de XR do Unity para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394560"
---
# <a name="setting-up-your-xr-configuration"></a>Configurando sua configuração de XR

Ao iniciar um novo projeto do Unity, você tem três opções diferentes para lidar com suas necessidades de XR: 
* Plug-in openXR
* Plug-in do Windows XR
* Plug-in XR herddo

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

> [!div class="nextstepaction"]
> [Experimente os nossos tutoriais do MRTK](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.

### <a name="using-mrtk-with-openxr-support"></a>Usando o MRTK com suporte a OpenXR

MRTK-Unity versão 2.7 oferece melhor suporte para o plug-in OpenXR de Realidade Misturada.

Abra a [Ferramenta de Recursos de Realidade](welcome-to-mr-feature-tool.md) Misturada novamente para instalar o Kit de Ferramentas de Realidade Misturada, caso ainda não tenha feito isso. O suporte a OpenXR está no **pacote Foundation.**

Consulte a documentação do MRTK [para obter informações mais detalhadas sobre como migrar para o OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)

> [!NOTE]
> Ao atualizar de uma versão anterior do MRTK anterior à **2.5.3,** verifique se a seguinte linha está no arquivo **Assets/MixedRealityToolkit.Generated/link.xml:**
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Essa linha será adicionada por padrão se você tiver iniciado com o MRTK 2.5.4 ou mais novo.

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

Embora a Microsoft e a comunidade tenham criado ferramentas do opensource, como o [MRTK (Kit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) de Ferramentas de Realidade Misturada) que configurará automaticamente o ambiente wmr, muitos desenvolvedores desejam criar suas experiências desde o zero.

[!INCLUDE[](includes/xr/manual-setup.md)]
