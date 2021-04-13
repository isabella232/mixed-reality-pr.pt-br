---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097850"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in do Windows XR](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Como garantir a capacidade de entrada com o olhar e como adicionar o provedor de dados do olhar

No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade de Entrada de Foco de Olho** está esmaecida:

![Janela Configurador de Projeto do MRTK no Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> A funcionalidade de Entrada de Foco deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#configuring-the-unity-project) quando você configurou o projeto do Unity no início desta série de tutoriais. No entanto, se não estiver habilitada, faça isso agora.

Na janela Hierarquia, selecione o objeto MixedRealityToolkit e na janela Inspetor, navegue até a guia Entrada:

* Expanda o item **Provedores de Dados de Entrada** e clique no botão **+ Adicionar Provedor de Dados** para adicionar um novo provedor de dados

![Como adicionar o provedor de dados de olhar 1](../images/mr-learning-base/base-08-section1-step1-2.png)

Atribua a opção **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** ao campo **Tipo** do novo provedor de dados.

![Como adicionar o provedor de dados de olhar 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Como garantir a capacidade de entrada com o olhar e como adicionar o provedor de dados do olhar

Na janela Hierarquia, selecione o objeto MixedRealityToolkit e na janela Inspetor, navegue até a guia Entrada:

* Expanda o item **Provedores de Dados de Entrada** e clique no botão **+ Adicionar Provedor de Dados** para adicionar um novo provedor de dados

![Como adicionar o provedor de dados de olhar 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

Atribua a opção **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** ao campo **Tipo** do novo provedor de dados.

![Como adicionar o provedor de dados de olhar 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Como garantir que a funcionalidade de Entrada de Foco de Olho esteja habilitada

No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade de Entrada de Foco de Olho** está esmaecida:

![Janela Configurador de Projeto do MRTK no Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> A funcionalidade de Entrada de Foco deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) quando você configurou o projeto do Unity no início desta série de tutoriais. No entanto, se não estiver habilitada, faça isso agora.
