---
ms.openlocfilehash: d8d46da1a1a095074f059b53ebd997e1b6f89961
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984316"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in do Windows XR](#tab/winxr)

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

![Caminho do menu Configurações de Projeto... do Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-ins do XR** > **Instalar o Gerenciamento de Plug-ins do XR**, para instalar o Gerenciamento de Plug-ins do XR:

![Configurações de XR do Unity](../images/mr-learning-base/base-02-section5-step2-2.png)

Depois que o Unity terminar de instalar o Gerenciamento de Plug-ins do XR. Verifique se você está nas configurações da Plataforma Universal do Windows e marque as opções **Inicializar o XR ao Iniciar** e **Windows Mixed Reality**.

![Configurações de XR do Unity com a adição do SDK do Windows Mixed Reality](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente. Se ela não aparecer, use o menu do Unity para abri-la.

Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:

![Configurações de XR do Unity com o SDK do Windows Mixed Reality selecionado](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto. Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada. Para saber mais sobre este tópico, veja os <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.

Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-ins do XR** > **Windows Mixed Reality** > **Configurações de Runtime** e use a lista suspensa **Formato de Buffer de Profundidade** para selecionar a **profundidade de 16 bits**:

![Configurações de publicação do Unity com o nome do pacote realçado](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto. Para saber mais sobre este tópico, veja a seção <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">Desempenho</a> do MRTK.

Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:

![Configurações de publicação do Unity com o nome do pacote](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> O 'Nome do pacote' é o identificador exclusivo do aplicativo. Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.

> [!TIP]
> O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens. Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

![Caminho do menu Configurações de Projeto... do Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-ins do XR** > **Instalar o Gerenciamento de Plug-ins do XR**, para instalar o Gerenciamento de Plug-ins do XR:

![Configurações de XR do Unity com o gerenciamento de plug-ins de instalação do XR selecionado](../images/mr-learning-base/base-02-section5-step2-2.png)

Depois que o Unity terminar de instalar o Gerenciamento de Plug-ins do XR. Verifique se você está nas configurações da Plataforma Universal do Windows e marque as opções **Inicializar o XR ao iniciar**, **OpenXR** e **Conjunto de recursos do Microsoft HoloLens**.

![Configurações de XR do Unity com a adição do OpenXR e dos recursos do Microsoft HoloLens selecionados](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

>[!Important]
>Se você vir um ícone de aviso vermelho ao lado de Plug-in do OpenXR (Versão Prévia), clique no ícone e selecione Corrigir Tudo antes de continuar. O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.
>![Menu de validação de projeto do OpenXR com todos os problemas a serem corrigidos selecionados.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)

Na barra de menus na parte superior da tela, navegue até **Realidade Misturada > OpenXR > Aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.

![Menu da Realidade Misturada com as opções OpenXR e Aplicar as configurações de projeto recomendadas para o HoloLens 2 selecionadas](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

Depois que o Unity terminar de importar os arquivos necessários, a janela do Configurador de Projeto do MRTK será exibida novamente. Se ela não aparecer, use o menu do Unity para abri-la.

Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:

![Janela de configuração do MRTK com as opções padrão selecionadas](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto. Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada. Para saber mais sobre este tópico, veja os <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.


Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:

![Configurações de Publicação do Unity](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> O 'Nome do pacote' é o identificador exclusivo do aplicativo. Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.

> [!TIP]
> O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens. Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e marque a caixa de seleção **Realidade Virtual com Suporte**, clique no ícone **+** e selecione Windows Mixed Reality para adicionar o SDK do Windows Mixed Reality:

![Configurações de XR do Unity, adição do SDK do Windows Mixed Reality selecionada](../images/mr-learning-base/base-02-section5-step2-4.png)

Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente. Caso contrário, você pode abri-la manualmente no menu do Unity acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**

Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:

![Janela de configuração do MRTK](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto. Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada. Para saber mais sobre este tópico, veja os <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.

Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e, em seguida, use a lista suspensa **Formato de Profundidade** para selecionar a **Profundidade de 16 bits**:

![Habilitação da profundidade de 16 bits do Unity](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto. Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação Desempenho do MRTK.

Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:

![Configurações de Publicação do Unity. Nome do pacote configurado](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> O 'Nome do pacote' é o identificador exclusivo do aplicativo. Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.

> [!TIP]
> O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens. Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.
