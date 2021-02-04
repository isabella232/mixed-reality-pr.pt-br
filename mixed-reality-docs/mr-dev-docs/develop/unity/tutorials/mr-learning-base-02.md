---
title: Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como configurar seu projeto do Unity para o MRTK (Kit de Ferramentas de Realidade Misturada) e como implantá-lo no HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ff479df81316ab5ceeabf045ad1bbae007190ed4
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238145"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Como inicializar o seu projeto e implantar o primeiro aplicativo

Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> e importar o MRTK. Você também aprenderá mais sobre como configurar, compilar e implantar uma cena básica do Unity do Visual Studio para o HoloLens 2. Depois de implantá-la no HoloLens 2, você verá uma malha de mapeamento espacial que abrange as superfícies percebidas pelo HoloLens. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.

## <a name="objectives"></a>Objetivos

* Saiba como configurar o Unity para o desenvolvimento no HoloLens
* Saiba como criar e implantar o seu aplicativo no HoloLens
* Experimente a malha de mapeamento espacial, as malhas de mão e o contador da taxa de quadros no dispositivo HoloLens 2

## <a name="creating-the-unity-project"></a>Como criar o projeto do Unity

Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:

![Hub do Unity com o botão Novo realçado](images/mr-learning-base/base-02-section1-step1-1.png)

Na lista suspensa, selecione a **versão** do Unity especificada em [Pré-requisitos](mr-learning-base-01.md#prerequisites):

![Hub do Unity com a lista suspensa do seletor de NOVA versão](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Se a versão específica do Unity não estiver disponível no Hub do Unity, você poderá iniciar a instalação em <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Arquivos de Download</a> do Unity.

Na janela Criar um novo projeto:

* Verifique se **Modelos** está definido como **3D**
* Insira um **Nome de Projeto** adequado, por exemplo, _Tutoriais do MRTK_
* Escolha um **Local** adequado para armazenar seu projeto, por exemplo, _D:\MixedRealityLearning_
* Clique no botão **Criar** para criar e iniciar o novo projeto do Unity

![Hub do Unity com a janela Criar um projeto preenchida](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres. Consequentemente, você deve salvar o projeto do Unity próximo à raiz da unidade.

Aguarde até que o Unity crie o projeto:

![Criação de projeto do Unity em andamento](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Como alternar a plataforma de build

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build:

![Caminho do menu Configurações de Build... do Unity](images/mr-learning-base/base-02-section2-step1-1.png)

Na janela Configurações de Build, selecione **Plataforma Universal do Windows** e clique no botão **Mudar Plataforma**:

![Janela Configurações de Build do Unity com o UWP selecionado para alternar a plataforma da opção Autônomo](images/mr-learning-base/base-02-section2-step1-2.png)

Aguarde até que o Unity termine de mudar a plataforma:

![Alternância de plataforma do Unity em andamento](images/mr-learning-base/base-02-section2-step1-3.png)

Quando o Unity terminar de mudar a plataforma, clique no ícone vermelho **x** para fechar a janela Configurações de Build:

![Janela Build do Unity com ícone de Fechar realçado](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>Como importar os Recursos Essenciais do TextMeshPro

No menu do Unity, selecione **Janela** > **TextMeshPro** > **Importar Recursos Essenciais do TMP** para abrir a janela Importar Pacote do Unity:

![Caminho do menu Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-1.png)

Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:

![Janela Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Os Recursos Essenciais do TextMeshPro são exigidos pelos elementos da interface do usuário do MRTK. Você poderá ignorar esta etapa se não estiver planejando usar os elementos da interface do usuário do MRTK no seu projeto.

## <a name="importing-the-mixed-reality-toolkit"></a>Como importar o Kit de Ferramentas de Realidade Misturada

### <a name="using-the-mixed-reality-feature-tool"></a>Como usar a Ferramenta de Recursos de Realidade Misturada

Para instalar o MRTK com nosso novo aplicativo Ferramenta de Recursos de Realidade Misturada, siga nossas [instruções de instalação e uso](../welcome-to-mr-feature-tool.md) e selecione o pacote **Mixed Reality Toolkit Foundation** na categoria do Kit de Ferramentas da Realidade Misturada.

### <a name="using-unity-packages"></a>Como usar pacotes do Unity

Para instalar o MRTK com um pacote personalizado:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

No menu do Unity, selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:

![Caminho do menu Importar Pacote Personalizado... do Unity](images/mr-learning-base/base-02-section4-step1-1.png)

Na janela Importar pacote..., selecione o **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** que você baixou e clique no botão **Abrir**:

![Importar Pacote Personalizado do Unity com a janela de prompt Abrir](images/mr-learning-base/base-02-section4-step1-2.png)

Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:

![Janela de importação do MRTK Foundation no Unity](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>Como configurar o projeto do Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Aplicar as configurações do Configurador de Projeto do MRTK

Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer. Caso contrário, você pode abri-la manualmente acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**:

![Caminho do menu Configurar Projeto do Unity no Unity](images/mr-learning-base/base-02-section5-step1-1.png)

Na janela Configurador de Projeto do MRTK, expanda a seção **Modificar Configurações**, verifique se todas as opções estão marcadas e clique no botão **Aplicar** para aplicar as configurações:

![Janela Configurador de Projeto do MRTK no Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:

> * Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho. Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) da documentação [Desempenho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) do MRTK.
> * Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial. Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.

### <a name="2-configure-additional-project-settings"></a>2. Definir configurações adicionais do projeto

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

![Caminho do menu Configurações de Projeto... do Unity](images/mr-learning-base/base-02-section5-step2-1.png)

Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-ins do XR** > **Instalar o Gerenciamento de Plug-ins do XR**, para instalar o Gerenciamento de Plug-ins do XR:

![Configurações de projeto com o Gerenciamento de Plug-in do XR selecionado](images/mr-learning-base/base-02-section5-step2-2.png)

Depois que o Unity terminar de instalar o Gerenciamento de Plug-ins do XR. Verifique se você está nas configurações da Plataforma Universal do Windows e marque Inicializar o XR ao Iniciar.

![Configuração do gerenciamento de plug-ins do XR do Unity](images/mr-learning-base/base-02-section5-step2-3.png)

Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR**, clique no ícone **+** e selecione Windows Mixed Reality para adicionar o SDK do Windows Mixed Reality:

![Configurações de XR do Unity com a adição do SDK do Windows Mixed Reality selecionada](images/mr-learning-base/base-02-section5-step2-4.png)

Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente. Se ela não aparecer, use o menu do Unity para abri-la.

Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:

![Janela do configurador de projeto do MRTK com a propriedade de espacializador de áudio realçada](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto. Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada. Para saber mais sobre este tópico, veja os <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.

Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e, em seguida, use a lista suspensa **Formato de Profundidade** para selecionar a **Profundidade de 16 bits**:

![Habilitação da profundidade de 16 bits do Unity](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto. Para saber mais sobre este tópico, veja a seção <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">Desempenho</a> do MRTK.

Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:

![Configurações de Publicação do Unity com o Nome do pacote configurado](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> O 'Nome do pacote' é o identificador exclusivo do aplicativo. Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.

> [!TIP]
> O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens. Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.

## <a name="creating-and-configuring-the-scene"></a>Como criar e configurar a cena

No menu do Unity, selecione **Arquivo** > **Nova Cena** para criar uma cena:

![Caminho do menu Nova Cena do Unity](images/mr-learning-base/base-02-section6-step1-1.png)

No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** para adicionar o MRTK à cena atual:

![Caminho do menu Adicionar à Cena e Configurar... do Unity](images/mr-learning-base/base-02-section6-step1-2.png)

Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, na janela Inspetor, verifique se o perfil de configuração **MixedRealityToolkit** está definido como **DefaultMixedRealityToolkitConfigurationProfile**:

![Componente MixedRealityToolkit do Unity com DefaultMixedRealityTookitConfigurationProfile selecionado](images/mr-learning-base/base-02-section6-step1-3.png)

No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:

![Caminho do menu Salvar como... do Unity](images/mr-learning-base/base-02-section6-step1-4.png)

Na janela Salvar cena, navegue até a pasta **Cenas** do seu projeto, dê um nome adequado à sua cena (por exemplo, _Introdução_) e clique no botão **Salvar** para salvar a cena:

![Janela de prompt Salvar para salvar a cena do Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>Como criar o aplicativo para o seu HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Compilar o projeto do Unity

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build.

Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar sua cena atual à lista **Cenas no Build** e clique no botão **Build** para abrir a janela Compilar Plataforma Universal do Windows:

![Janela Configurações de Build do Unity com o UWP selecionado](images/mr-learning-base/base-02-section7-step1-1.png)

Na janela Compilar Plataforma Universal do Windows, escolha um local adequado para armazenar seu build, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma nova pasta e dê a ela um nome adequado, por exemplo, _GettingStarted_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](images/mr-learning-base/base-02-section7-step1-2.png)

Aguarde até que o Unity conclua o processo de build:

![Processo de build do Unity em andamento](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilar e implantar o aplicativo

Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra a localização em que você armazenou o build. Navegue dentro da pasta e clique duas vezes no arquivo da solução para abri-lo no Visual Studio:

![Windows Explorer com a solução do Visual Studio recém-criada selecionada](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar-se de que você tenha todos os componentes de pré-requisitos na documentação **[Instalar as Ferramentas](../../install-the-tools.md)** .

Configure o Visual Studio para o HoloLens selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM64** e o **Dispositivo** como destino:

![Visual Studio configurado para implantação no HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> Se você estiver implantando no HoloLens (1ª geração), selecione a arquitetura **x86**.

> [!NOTE]
> Para o HoloLens, você normalmente criará para a arquitetura ARM. No entanto, há um <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conhecido</strong></a> no Unity 2019.3 que causa erros ao selecionar o ARM como a arquitetura de build no Visual Studio. A solução alternativa recomendada é criar para o ARM64. Se essa não for uma opção, acesse **Editar > Configurações de Projeto > Player > Outras Configurações** e desabilite **Trabalhos Gráficos**.

> [!NOTE]
> Se o Dispositivo não for exibido como uma opção de destino, talvez seja necessário alterar o projeto de inicialização para a solução do Visual Studio do projeto IL2CPP para o projeto UWP. Para fazer isso, no Gerenciador de Soluções, clique com o botão direito do mouse no NomeDoSeuProjeto (Universal do Windows) e selecione **Definir como Projeto de Inicialização**.

Conecte o seu HoloLens ao seu computador e, em seguida, selecione **Depurar** > **Iniciar sem Depuração** para criar e implantar no seu dispositivo:

![Caminho do menu Iniciar Sem Depuração do Visual Studio](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> Antes de compilar no dispositivo, ele precisa estar no Modo de Desenvolvedor e emparelhado com o computador de desenvolvimento. Essas duas etapas podem ser concluídas seguindo [estas instruções](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> Você também pode implantar no [Emulador do HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou criar um [Pacote do Aplicativo](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para sideload.

O uso de Iniciar sem Depuração inicia automaticamente o aplicativo no seu dispositivo sem o depurador do Visual Studio anexado.

Selecione **Criar > Implantar Solução** para implantar no seu dispositivo sem iniciar o aplicativo automaticamente.

> [!NOTE]
>Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **Alternar Diagnóstico**. É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho. Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Parabéns

Você acabou de implantar o seu primeiro aplicativo do HoloLens. Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies detectadas pelo HoloLens. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo. Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK. Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.

> [!div class="nextstepaction"]
> [Próximo tutorial: 3. Como configurar os perfis do MRTK](mr-learning-base-03.md)