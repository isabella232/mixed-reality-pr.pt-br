---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097874"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in do Windows XR](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Como garantir a capacidade do microfone e adicionar o provedor de dados de entrada de fala

No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade do Microfone** está esmaecida:

![Habilitar a funcionalidade de microfone](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> A funcionalidade do Microfone deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#configuring-the-unity-project) quando você configurou o projeto do Unity no início desta série de tutoriais. No entanto, se não estiver habilitada, faça isso agora.

Na janela Hierarquia, selecione o objeto MixedRealityToolkit e na janela Inspetor, navegue até a guia Entrada:

* Expanda o item **Provedores de Dados de Entrada** e clique no botão **+ Adicionar Provedor de Dados** para adicionar um novo provedor de dados

![Provedor de dados para adicionar novos comandos de fala](../images/mr-learning-base/base-09-section1-step1-2.png)

Atribua a opção **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** ao campo **Tipo** do novo provedor de dados.

![Como adicionar configurações de novos comandos de fala](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Como garantir a capacidade do microfone e adicionar o provedor de dados de entrada de fala

No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade do Microfone** está esmaecida:

![Habilitar a capacidade do microfone para OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> A funcionalidade do Microfone deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#configuring-the-unity-project) quando você configurou o projeto do Unity no início desta série de tutoriais. No entanto, se não estiver habilitada, faça isso agora.

Na janela Hierarquia, selecione o objeto MixedRealityToolkit e na janela Inspetor, navegue até a guia Entrada:

* Expanda o item **Provedores de Dados de Entrada** e clique no botão **+ Adicionar Provedor de Dados** para adicionar um novo provedor de dados

![Como adicionar novos comandos de fala ao OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

Atribua a opção **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** ao campo **Tipo** do novo provedor de dados.

![Como adicionar novos comandos de fala para configurações do OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Garantir que a funcionalidade do Microfone esteja habilitada

No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade do Microfone** está esmaecida:

![Habilitar a funcionalidade de microfone](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> A funcionalidade do Microfone deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) quando você configurou o projeto do Unity no início desta série de tutoriais. No entanto, se não estiver habilitada, faça isso agora.
