---
title: Configurando sua configuração XR
description: Mantenha-se atualizado sobre as recomendações de configuração do Unity XR mais recentes para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, Unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906932"
---
# <a name="setting-up-your-xr-configuration"></a>Configurando sua configuração XR

Ao iniciar um novo projeto do Unity, você tem três opções diferentes para lidar com suas necessidades de XR: 
* Plug-in OpenXR
* Plug-in do Windows XR
* Plug-in de XR herdado

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configurando seu projeto com o MRTK

O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

> [!div class="nextstepaction"]
> [Experimente os nossos tutoriais do MRTK](./tutorials/mr-learning-base-02.md?tabs=winxr)

Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.

### <a name="using-mrtk-with-openxr-support"></a>Usando o MRTK com suporte a OpenXR

MRTK-Unity versão 2,7 fornece suporte melhor para o plug-in OpenXR da realidade misturada.

Abra a [ferramenta de funcionalidade Mixed Reality](welcome-to-mr-feature-tool.md) novamente para instalar o kit de ferramentas do reality misto, se ainda não tiver feito isso. O suporte do OpenXR está no pacote **base** .

Consulte a documentação do MRTK para obter [informações mais detalhadas sobre como migrar para o OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).

> [!NOTE]
> Ao atualizar de uma versão anterior do MRTK com mais de **2.5.3**, verifique se a linha a seguir está no arquivo **assets/MixedRealityToolkit. Generated/link.xml** :
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Essa linha será adicionada por padrão se você tiver iniciado com MRTK 2.5.4 ou mais recente.

## <a name="manual-setup-without-mrtk"></a>Configuração manual sem MRTK

Embora a Microsoft e a Comunidade tenham criado ferramentas abertas como o [MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) que configurará automaticamente o ambiente WMR, muitos desenvolvedores desejam criar suas experiências desde o início.

[!INCLUDE[](includes/xr/manual-setup.md)]