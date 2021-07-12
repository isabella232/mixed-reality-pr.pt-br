---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603698"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Para começar a usar um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:

> [!div class="nextstepaction"]
> [Configurar um novo projeto OpenXR com o MRTK](../../tutorials/mr-learning-base-02.md?tabs=openxr)

Se você estiver atualizando um projeto do MRTK existente para **o OpenXR,** primeiro será melhor atualizar o MRTK-Unity para a versão mais recente (versão 2.7.2 ou posterior) para obter correções de chave para compatibilidade com o plug-in openXR de Realidade Misturada.  Use a [Ferramenta de Recursos de Realidade](../../welcome-to-mr-feature-tool.md) Misturada para atualizar para a versão mais recente do MRTK e siga as etapas manuais de instalação do [OpenXR abaixo.](#manual-setup-without-mrtk) Consulte a documentação do MRTK para obter informações mais detalhadas sobre como migrar um projeto [do MRTK existente para o OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)

> [!NOTE]
> Ao atualizar de uma versão anterior do MRTK anterior à **2.5.3,** verifique se a seguinte linha está no arquivo **Assets/MixedRealityToolkit.Generated/link.xml:**
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Essa linha será adicionada por padrão se você tiver iniciado com o MRTK 2.5.4 ou mais novo.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Para começar a usar um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:

> [!div class="nextstepaction"]
> [Configurar um novo projeto Windows XR com o MRTK](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

Para começar a usar um **novo projeto do Unity** usando o MRTK, comece da etapa 2 no tutorial do MRTK:

> [!div class="nextstepaction"]
> [Configurar um novo projeto XR herdado com o MRTK](../../tutorials/mr-learning-base-02.md?tabs=wsa)