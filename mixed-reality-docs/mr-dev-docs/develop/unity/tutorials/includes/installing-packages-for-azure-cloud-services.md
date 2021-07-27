---
ms.openlocfilehash: 7cd9400ddb83b95f145a9b962be51aaed30df47b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224357"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

No menu do Unity, selecione **Janela** > **Gerenciador de pacotes** para abrir a janela do Gerenciador de pacotes, e verifique se a versão do **AR Foundation** > **4.1.7** está instalada.

![Janela Gerenciador de Pacotes do Unity com o AR Foundation selecionado](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

> [!NOTE]
> Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure e será importado na próxima seção.

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Adicione o SDK V2.10 do AzurespatialAnchors ao seu projeto. Para adicionar os pacotes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](../images/mr-learning-azure/tutorial1-section4-step1-1-OpenXR.png)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, consulte as instruções em  [Como importar o Kit de Ferramentas de Realidade Misturada](../mr-learning-base-04.md#importing-the-tutorial-assets) .

# <a name="unity-2020--windows-xr-plugin"></a>[Unity 2020 + Plug-in do Windows XR](#tab/winxr)

No menu do Unity, selecione **Janela** > **Gerenciador de pacotes** para abrir a janela do Gerenciador de pacotes e selecione **AR Foundation > 4.0.12** e clique em **Instalar** para instalar o pacote:

![Janela Gerenciador de Pacotes do Unity com o AR Foundation selecionado](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

> [!NOTE]
> Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure e será importado na próxima seção.

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Adicione o SDK V2.10 do AzurespatialAnchors ao seu projeto. Para adicionar os pacotes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](../images/mr-learning-azure/tutorial1-section4-step1-1-XRSDK.png)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, consulte as instruções em  [Como importar o Kit de Ferramentas de Realidade Misturada](../mr-learning-base-04.md#importing-the-tutorial-assets) .

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

No menu do Unity, selecione **Janela** > **Gerenciador de pacotes** para abrir a janela do Gerenciador de pacotes e selecione **AR Foundation > 3.1.3** e clique em **Instalar** para instalar o pacote:

![Janela Gerenciador de Pacotes do Unity com o AR Foundation selecionado](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

> [!NOTE]
> Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure e será importado na próxima seção.

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Adicione o SDK V2.7.2 do AzurespatialAnchors ao seu projeto. Para adicionar os pacotes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](../images/mr-learning-azure/tutorial1-section4-step1-1-Legacy.png)

> [!NOTE]
> Se você vir avisos CS0618 sobre 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' e 'WorldAnchor.GetNativeSpatialAnchorPtr()' estarem obsoletos, poderá ignorá-los.

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, consulte as instruções em  [Como importar o Kit de Ferramentas de Realidade Misturada](../mr-learning-base-04.md#importing-the-tutorial-assets) .
