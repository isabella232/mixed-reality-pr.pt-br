---
ms.openlocfilehash: 695db2d7e6765d3584c9e9a6459071ab537c1f003d13461ce5736481b98b7495
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202704"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Para começar com um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:

> [!div class="nextstepaction"]
> [Configurar um novo projeto OpenXR com MRTK](../../tutorials/mr-learning-base-02.md?tabs=openxr)

Se você estiver atualizando um **projeto MRTK existente para OpenXR**, primeiro você vai querer atualizar MRTK-Unity para a versão mais recente (versão 2.7.2 ou posterior) para obter as principais correções de compatibilidade com o plug-in Mixed Reality OpenXR.  Use a [ferramenta de funcionalidade mistura de realidade](../../welcome-to-mr-feature-tool.md) para atualizar para a versão mais recente do MRTK e siga as [etapas manuais de configuração do OpenXR abaixo](#manual-setup-without-mrtk). Consulte a documentação do MRTK para obter [informações mais detalhadas sobre como migrar um projeto MRTK existente para o OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).

> [!NOTE]
> Ao atualizar de uma versão anterior do MRTK com mais de **2.5.3**, verifique se a linha a seguir está no arquivo **assets/MixedRealityToolkit. Generated/link.xml** :
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Essa linha será adicionada por padrão se você tiver iniciado com MRTK 2.5.4 ou mais recente.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Para começar com um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:

> [!div class="nextstepaction"]
> [configurar um novo projeto do Windows XR com MRTK](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

Para começar com um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:

> [!div class="nextstepaction"]
> [Configurar um novo projeto de XR herdado com MRTK](../../tutorials/mr-learning-base-02.md?tabs=wsa)