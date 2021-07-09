---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175765"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Quando o **MixedRealityFeatureTool** for aberto, clique em **Iniciar** para começar a usar a Ferramenta de Recursos da Realidade Misturada.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

A primeira etapa é apontar a Ferramenta Recurso de Realidade Misturada para o **caminho de Projeto** usando o botão de **reticências**, clicar no botão de reticências de três pontos ao lado do caminho de Projeto e navegar até a pasta do projeto no explorador, por exemplo _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Quando você tiver localizado a pasta do projeto, clique no botão Abrir para retornar à Ferramenta Recurso de Realidade Misturada. Em seguida, clique em **Descobrir Recursos**.

> [!NOTE]
> A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo. É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.

> [!Important]
> A Ferramenta de Recursos da Realidade Misturada executa a validação para garantir que ela tenha sido direcionada para uma pasta de projeto do Unity. A pasta deve conter pastas de Ativos, Pacotes e Configurações do Projeto.

Os recursos são agrupados por categoria para que seja mais fácil encontrar o que você quer. Clique na lista suspensa **Kit de Ferramentas de Realidade Misturada** para encontrar pacotes relacionados ao Kit de Ferramentas de Realidade Misturada e clique na lista suspensa **Suporte de Plataforma** para encontrar pacotes relacionados a diversas plataformas de suporte.

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

Verifique a **Mixed Reality Toolkit Foundation** e clique na lista suspensa ao lado para selecionar **MRTK 2.7.2**. Selecione também o **Plug-In OpenXR de Realidade Misturada 1.0.0** e clique na lista suspensa ao lado para selecionar a versão mais recente disponível e, em seguida, clique no botão **Obter recursos** para baixar os pacotes selecionados.

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

Em seguida, clique no botão **Validar** para validar o pacote selecionado. Você receberá um pop-up com a mensagem **Não foi detectado nenhum problema de validação**, clique em **OK** para fechar o pop-up e clique no botão **Importar**.

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


Clique no botão **Aprovar** para adicionar o **Kit de Ferramentas de Realidade Misturada** ao projeto.

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>Como configurar o projeto do Unity

Depois que o Unity terminar de importar o pacote da seção anterior, uma mensagem de aviso será exibida para reiniciar o editor do Unity para habilitar os back-ends para o novo sistema de plug-ins, clique em **Sim**

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Após a reinicialização do Unity, o Configurador de Projeto do MRTK deve aparecer. Caso contrário, você pode abri-lo manualmente acessando **Kit de Ferramentas** > **de Realidade Misturada** > **Utilitários**  > **Configurar Projeto para MRTK**:

![Abrir a janela do configurador de projeto do MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

Clique em **Plug-in OpenXR do Unity** para Habilitar o Gerenciamento de Plug-In XR e adicione seus pacotes necessários ao seu projeto.

![Adicionar Plug-in OpenXR do Unity ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

Isso resultará na importação dos pacotes do Unity necessários para o Gerenciamento de Plug-in XR. Após concluir, clique em **Mostrar Configurações de Gerenciamento de Plug-In XR** no Configurador do projeto do MRTK.

![Mostrar as Configurações de Gerenciamento do Plug-In XR ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

Isso abrirá a **janela de Configurações do Projeto**. Na janela Configurações do Projeto em **Gerenciamento de Plug-in XR**, verifique se você está nas configurações da Plataforma Universal do Windows (guia do logotipo do Windows). Verifique também se **Inicializar XR na Inicialização** está marcado e, em seguida, clique nas caixas de seleção **OpenXR** e **Conjunto de recursos do Microsoft HoloLens** para habilita-los.

![Habilitar Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

Após selecionar a caixa de seleção OpenXR, a janela Configurador de Projeto do MRTK exibirá a mensagem atualizada com o botão **Aplicar Configurações**. Clique no botão **Aplicar Configurações**. 

![Janela 1 das Configurações do Projeto](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

Ao clicar em Aplicar Configurações, você poderá ver essa mensagem de erro no Console. Você pode prosseguir se esse for o único erro ou se não houver nenhum erro.

![Mensagem de Erro de Comunicação Remota do OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

Para validar a configuração do OpenXR, clique em **OpenXR** em **Gerenciamento de Plug-in XR**, e marque estes itens:
* Modo de Envio de Intensidade: **Intensidade de 16 Bits**
* Perfis de Interação: **Perfil de Interação à Mão da Microsoft**

![Janela 2 das Configurações do Projeto](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> A redução do formato de profundidade para 16 bits é opcional, mas pode ajudar a aprimorar o desempenho gráfico no projeto. Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação Desempenho do MRTK.


Na janela **Configurador do Projeto do MRTK** clique em **Próximo** e, em seguida, clique no botão **Aplicar** para aplicar as configurações. (Se você tiver fechado, você pode abri-lo manualmente acessando **Kit de Ferramentas** > **de Realidade Misturada** > **Utilitários**  > **Configurar Projeto para MRTK**)

![Janela 3 das Configurações do Projeto](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Janela 4 das Configurações do Projeto](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

Após clicar em Aplicar, o Unity tentará reiniciar para que o sistema de entrada entre em vigor. Clique em **Aplicar** para reiniciar o editor do Unity

### <a name="configure-additional-project-settings"></a>Definir configurações adicionais do projeto

No menu do Unity, selecione **Editar** > **Configurações do projeto...** para abrir a janela Configurações do Projeto.

Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:

![Configurações de Publicação do Unity. Nome do pacote configurado](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> O 'Nome do pacote' é o identificador exclusivo do aplicativo. Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.

> [!TIP]
> O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens. Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in do Windows XR](#tab/winxr)

Quando o **MixedRealityFeatureTool** for aberto, clique em **Iniciar** para começar a usar a Ferramenta de Recursos da Realidade Misturada.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

A primeira etapa é apontar a Ferramenta Recurso de Realidade Misturada para o **caminho de Projeto** usando o botão de **reticências**, clicar no botão de reticências de três pontos ao lado do caminho de Projeto e navegar até a pasta do projeto no explorador, por exemplo _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


Quando você tiver localizado a pasta do projeto, clique no botão Abrir para retornar à Ferramenta Recurso de Realidade Misturada. Em seguida, clique em **Descobrir Recursos**.

> [!NOTE]
> A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo. É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.

> [!Important]
> A Ferramenta de Recursos da Realidade Misturada executa a validação para garantir que ela tenha sido direcionada para uma pasta de projeto do Unity. A pasta deve conter pastas de Ativos, Pacotes e Configurações do Projeto.

Os recursos são agrupados por categoria para que seja mais fácil encontrar o que você quer. Clique na lista suspensa **Kit de Ferramentas de Realidade Misturada** para encontrar pacotes relacionados ao Kit de Ferramentas de Realidade Misturada.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Selecione a caixa **Mixed Reality Toolkit Foundation**, clique na lista suspensa ao lado para selecionar **MRTK 2.7.0**, e clique no botão **Obter recursos** para baixar os pacotes selecionados.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Em seguida, clique no botão **Validar** para validar o pacote selecionado. Você receberá um pop-up com a mensagem **Não foi detectado nenhum problema de validação**, clique em **OK** para fechar o pop-up e clique no botão **Importar**.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


Clique no botão **Aprovar** para adicionar o **Kit de Ferramentas de Realidade Misturada** ao projeto.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Como configurar o projeto do Unity

Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer. Caso contrário, você pode abri-lo manualmente acessando **Kit de Ferramentas** > **de Realidade Misturada** > **Utilitários**  > **Configurar Projeto para MRTK**:

![abrindo a ferramenta de configurador do MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

Clique em **Plug-in Interno do Unity (não OpenXR)** para Habilitar o Gerenciamento de Plug-In XR e adicione seus pacotes necessários ao seu projeto.

![ Ferramenta de configurador do MRTK](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> A captura de tela acima é do Unity 2020. Se você estiver usando o Unity 2019, selecione **Gerenciamento de XR SDK/XR**

Isso resultará na importação dos pacotes do Unity necessários para o Gerenciamento de Plug-in XR. Após concluir, clique em **Mostrar Configurações** no Configurador do projeto do MRTK.

![Janela configurações do player](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

Isso abre a **janela Configurações do Projeto** na janela Configurações do Projeto em **Gerenciamento do Plug-in XR** Verifique se você está nas configurações da Plataforma Universal do Windows e Verifique se **Inicializar XR na Inicialização** está selecionado, e selecione a caixa de seleção **Windows Mixed Reality**.

![Janela configurações do player Habilitar Realidade Misturada-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente. Se ela não aparecer, use o menu do Unity para abri-la.

Na janela Configurador de Projeto do MRTK, clique em **próximo**, e, em seguida, use a lista suspensa Espacializador de áudio para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:

![Configurador de projeto do MRTK-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:

> * Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho. Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) da documentação [Desempenho](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) do MRTK.
> * Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial. Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.

> [!TIP]
> A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto. Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada. Para saber mais sobre este tópico, veja os <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.

Clique em **Próximo** e clique em **Concluído** na janela Configurador de Projeto do MRTK para concluir a configuração de projeto do Unity para XRSDK.

### <a name="configure-additional-project-settings"></a>Definir configurações adicionais do projeto

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-in do XR** > **Windows Mixed Reality** > **Configurações de Tempo de Execução** e use a lista suspensa **Formato de Buffer de Profundidade** para selecionar a **intensidade de 16 bits**:

![Habilitação da profundidade de 16 bits do Unity](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto. Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação Desempenho do MRTK.

Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:

![Configurações de Publicação do Unity. Nome do pacote configurado](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> O 'Nome do pacote' é o identificador exclusivo do aplicativo. Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.

> [!TIP]
> O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens. Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

Quando o **MixedRealityFeatureTool** for aberto, clique em **Iniciar** para começar a usar a Ferramenta de Recursos da Realidade Misturada.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

A primeira etapa é apontar a Ferramenta Recurso de Realidade Misturada para o **caminho de Projeto** usando o botão de **reticências**, clicar no botão de reticências de três pontos ao lado do caminho de Projeto e navegar até a pasta do projeto no explorador, por exemplo _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Quando você tiver localizado a pasta do projeto, clique no botão Abrir para retornar à Ferramenta Recurso de Realidade Misturada. Em seguida, clique em **Descobrir Recursos**.

> [!NOTE]
> A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo. É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.

> [!Important]
> A Ferramenta de Recursos da Realidade Misturada executa a validação para garantir que ela tenha sido direcionada para uma pasta de projeto do Unity. A pasta deve conter pastas de Ativos, Pacotes e Configurações do Projeto.

Os recursos são agrupados por categoria para que seja mais fácil encontrar o que você quer. Clique na lista suspensa **Kit de Ferramentas de Realidade Misturada** para encontrar pacotes relacionados ao Kit de Ferramentas de Realidade Misturada.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

selecione **Mixed Reality Toolkit Foundation**, clique na lista suspensa ao lado para selecionar **MRTK 2.7.0**, e clique no botão **Obter recursos** para baixar os pacotes selecionados.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Em seguida, clique no botão **Validar** para validar o pacote selecionado. Você receberá um pop-up com a mensagem **Não foi detectado nenhum problema de validação**, clique em **OK** para fechar o pop-up e clique no botão **Importar**.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

Clique no botão **Aprovar** para adicionar o **Kit de Ferramentas de Realidade Misturada** ao projeto.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Como configurar o projeto do Unity

Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer. Caso contrário, você pode abri-lo manualmente acessando **Kit de Ferramentas** > **de Realidade Misturada** > **Utilitários**  > **Configurar Projeto para MRTK**:

![Caminho do menu Configurar Projeto do Unity no Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

Clique em **XR Herdado** para habilitar o XR Herdado e adicionar seus pacotes necessários ao seu projeto.

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

Clique no botão próximo para habilitar as configurações de pipeline XR para XR Herdado.

![Janela de Configuração do MRTK do Unity](../images/mr-learning-base/base-02-section5-step1-3.PNG)

Na janela Configurador de Projeto do MRTK, verifique se todas as opções estão marcadas e use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:

![Janela de configuração do MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:

> * Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho. Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) da documentação [Desempenho](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) do MRTK.
> * Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial. Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.

> [!TIP]
> A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto. Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada. Para saber mais sobre este tópico, veja os <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.

Clique em **Próximo** e clique no botão **Concluído** na janela Configurador de Projeto do MRTK para concluir a configuração de projeto do Unity para XR Herdado.

### <a name="configure-additional-project-settings"></a>Definir configurações adicionais do projeto

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e, em seguida, use a lista suspensa **Formato de Profundidade** para selecionar a **Profundidade de 16 bits**:

![Habilitação da profundidade de 16 bits do Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto. Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação Desempenho do MRTK.

Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:

![Configurações de Publicação do Unity. Nome do pacote configurado](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> O 'Nome do pacote' é o identificador exclusivo do aplicativo. Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.

> [!TIP]
> O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens. Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.
