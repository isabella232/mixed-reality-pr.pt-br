---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098066"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in do Windows XR](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar o perfil de configuração padrão

> [!NOTE]
> O perfil de configuração é o perfil de nível superior. Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, verifique se o Perfil de Configuração do **MixedRealityToolkit** está configurado como **DefaultXRSDKConfigurationProfile**:

![Componente MixedRealityToolkit do Unity com DefaultHoloLens2ConfigurationProfile selecionado](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:

![Botão Copiar e Personalizar do componente MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_XRSDKConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultXRSDKConfigurationProfile**:

![Janela pop-up Perfil de Configuração do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:

![Componente MixedRealityToolkit do Unity com o HoloLens2ConfigurationProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.

> [!TIP]
> Lembre-se de salvar seu trabalho ao longo dos tutoriais.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar o Sistema de Reconhecimento Espacial

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:

![Componente MixedRealityToolkit do Unity com o Sistema de Reconhecimento Espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> Para projetos futuros, se o seu aplicativo não precisa responder ao ambiente nem interagir com ele, recomendamos manter o reconhecimento espacial desativado para reduzir o custo de desempenho.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão

Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:

![Componente MixedRealityToolkit do Unity com a guia Reconhecimento Espacial selecionada](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, e clique no botão **Clonar** para criar uma cópia editável do **DefaultXRSDKSpatialAwarenessSystemProfile**:

![Janela pop-up Perfil do Sistema de Reconhecimento Espacial do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessSystemProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão

Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality do SDK do XR** e clique no botão **Clonar** para abrir a janela Clonar Perfil:

![Componente MixedRealityToolkit do Unity com a seção Observador de Malha Espacial do Windows Mixed Reality expandida](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Janela pop-up Perfil de Observador da Malha Espacial do clone MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessMeshObserverProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Altere a visibilidade da malha de reconhecimento espacial

Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:

![Componente MixedRealityToolkit do Unity com a Opção de Exibição de Observador de Malha Espacial definida como Oclusão](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional. Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.

Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão. Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão. Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar o perfil de configuração padrão

> [!NOTE]
> O perfil de configuração é o perfil de nível superior. Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, verifique se o Perfil de Configuração do **MixedRealityToolkit** está configurado como **DefaultOpenXRConfigurationProfile**:

![Componente MixedRealityToolkit do Unity com perfil padrão do OpenXR selecionado](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:

![Componente MixedRealityToolkit do Unity, botão Copiar e Personalizar para o perfil do OpenXR](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_OpenXRConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultOpenXRConfigurationProfile**:

![Janela pop-up Perfil de Configuração do clone de MixedRealityToolkit do Unity para o perfil do OpenXR](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:

![Componente MixedRealityToolkit do Unity com o OpenXR recém-criado e personalizado aplicado](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.

> [!TIP]
> Lembre-se de salvar seu trabalho ao longo dos tutoriais.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar o Sistema de Reconhecimento Espacial

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:

![Componente MixedRealityToolkit do Unity com o Sistema de Reconhecimento Espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> Para projetos futuros, se o seu aplicativo não precisa responder ao ambiente nem interagir com ele, recomendamos manter o reconhecimento espacial desativado para reduzir o custo de desempenho.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão

Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:

![Componente MixedRealityToolkit do Unity com a guia Reconhecimento Espacial selecionada](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, GettingStarted_OpenXRSpatialAwarenessSystemProfile e clique no botão **Clonar** para criar uma cópia editável do **DefaultXRSDKSpatialAwarenessSystemProfile**:

![Janela pop-up Perfil do Sistema de Reconhecimento Espacial do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessSystemProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão

Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality do SDK do XR** e clique no botão **Clonar** para abrir a janela Clonar Perfil:

![Componente MixedRealityToolkit do Unity com a seção Observador de Malha Espacial do Windows Mixed Reality expandida](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Janela pop-up Perfil de Observador da Malha Espacial do clone MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessMeshObserverProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Altere a visibilidade da malha de reconhecimento espacial

Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:

![Componente MixedRealityToolkit do Unity com a Opção de Exibição de Observador de Malha Espacial definida como Oclusão](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional. Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.

Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão. Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão. Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).


# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar o perfil de configuração padrão

> [!NOTE]
> O perfil de configuração é o perfil de nível superior. Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, altere o Perfil de Configuração do **MixedRealityToolkit** para o **DefaultHoloLens2ConfigurationProfile**:

![Componente MixedRealityToolkit do Unity com DefaultHoloLens2ConfigurationProfile selecionado](../images/mr-learning-base/base-03-section1-step1-1.png)

Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:

![Botão Copiar e Personalizar do componente MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step1-2.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_HoloLens2ConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:

![Janela pop-up Perfil de Configuração do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step1-3.png)

Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:

![Componente MixedRealityToolkit do Unity com o HoloLens2ConfigurationProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step1-4.png)

No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.

> [!TIP]
> Lembre-se de salvar seu trabalho ao longo dos tutoriais.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar o Sistema de Reconhecimento Espacial

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:

![Componente MixedRealityToolkit do Unity com o Sistema de Reconhecimento Espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Para projetos futuros, se o seu aplicativo não precisa responder ao ambiente nem interagir com ele, recomendamos manter o reconhecimento espacial desativado para reduzir o custo de desempenho.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão

Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:

![Componente MixedRealityToolkit do Unity com a guia Reconhecimento Espacial selecionada](../images/mr-learning-base/base-03-section1-step3-1.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![Janela pop-up Perfil do Sistema de Reconhecimento Espacial do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step3-2.png)

O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessSystemProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão

Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality** e clique no botão **Clonar** para abrir a janela Clonar Perfil:

![Componente MixedRealityToolkit do Unity com a seção Observador de Malha Espacial do Windows Mixed Reality expandida](../images/mr-learning-base/base-03-section1-step4-1.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Janela pop-up Perfil de Observador da Malha Espacial do clone MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step4-2.png)

O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessMeshObserverProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Altere a visibilidade da malha de reconhecimento espacial

Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:

![Componente MixedRealityToolkit do Unity com a Opção de Exibição de Observador de Malha Espacial definida como Oclusão](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional. Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.

Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão. Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão. Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).
