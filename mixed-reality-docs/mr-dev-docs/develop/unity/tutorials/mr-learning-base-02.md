---
title: Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como configurar seu projeto do Unity para o MRTK (Kit de Ferramentas de Realidade Misturada) e como implantá-lo no HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 4363d3280036ef2cd93e75233005c00db17eb59b
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088587"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Como inicializar o seu projeto e implantar o primeiro aplicativo

Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> e importar o MRTK. Você também aprenderá mais sobre como configurar, compilar e implantar uma cena básica do Unity do Visual Studio para o HoloLens 2. Depois de implantá-la no HoloLens 2, você verá uma malha de mapeamento espacial que abrange as superfícies percebidas pelo HoloLens. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

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

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a>Como importar os Recursos Essenciais do TextMeshPro

No menu do Unity, selecione **Janela** > **TextMeshPro** > **Importar Recursos Essenciais do TMP** para abrir a janela Importar Pacote do Unity:

![Caminho do menu Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-1.png)

Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:

![Janela Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Os Recursos Essenciais do TextMeshPro são exigidos pelos elementos da interface do usuário do MRTK. Você poderá ignorar esta etapa se não estiver planejando usar os elementos da interface do usuário do MRTK no seu projeto.

## <a name="importing-the-mixed-reality-toolkit"></a>Como importar o Kit de Ferramentas de Realidade Misturada

Para importar o Kit de Ferramentas de Realidade Misturada no projeto do Unity, você terá que usar a [Ferramenta de Recursos da Realidade Misturada](../welcome-to-mr-feature-tool.md) que permite aos desenvolvedores descobrir, atualizar e adicionar pacotes de recursos de Realidade Misturada a projetos do Unity. Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.

Baixe a última versão da Ferramenta de Recursos da Realidade Misturada no [Centro de Download da Microsoft](https://aka.ms/MRFeatureTool). Quando o download for concluído, descompacte o arquivo e salve-o na sua área de trabalho.

> [!NOTE]
> Para executar a Ferramenta de Recursos da Realidade Misturada, instale o [runtime do .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)

> [!NOTE]
> A Ferramenta de Recursos de Realidade Misturada atualmente só é executada no Windows. Para o MacOS, siga este [procedimento](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) para baixar e importar o Kit de Ferramentas de Realidade Misturada no projeto do Unity.

Abra o arquivo executável **MixedRealityFeatureTool** na pasta baixada para iniciar a Ferramenta de Recursos da Realidade Misturada.  

![Abrindo o MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a>Como configurar o projeto do Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Aplicar as configurações do Configurador de Projeto do MRTK

Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer. Caso contrário, você pode abri-la manualmente acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**:

![Caminho do menu Configurar Projeto do Unity no Unity](images/mr-learning-base/base-02-section5-step1-1.png)

Na janela Configurador de Projeto do MRTK, expanda a seção **Modificar Configurações**, verifique se todas as opções estão marcadas e clique no botão **Aplicar** para aplicar as configurações:

![Janela Configurador de Projeto do MRTK no Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:

> * Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho. Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) da documentação [Desempenho](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) do MRTK.
> * Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial. Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.

### <a name="2-configure-additional-project-settings"></a>2. Definir configurações adicionais do projeto

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Como criar a cena e configurar o MRTK

No menu do Unity, selecione **Arquivo** > **Nova Cena** para criar uma cena:

![Caminho do menu Nova Cena do Unity](images/mr-learning-base/base-02-section6-step1-1.png)

No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** para adicionar o MRTK à cena atual:

![Caminho do menu Adicionar à Cena e Configurar... do Unity](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:

![Caminho do menu Salvar como... do Unity](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto. Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Desempenho</a> do MRTK.

![Janela de prompt Salvar para salvar a cena do Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe o seguinte pacote personalizado do Unity:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

Para importar um pacote personalizado do Unity, no menu do Unity selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:

![Como importar um pacote personalizado](images/mr-learning-base/base-02-section7-step1-1.png)

Na janela Importar Pacote..., selecione o **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** que você baixou e clique no botão Abrir:

![Como selecionar um pacote de ativos](images/mr-learning-base/base-02-section7-step1-2.png)

Na janela Importar Pacote do Unity, clique no botão Todos para garantir que todos os ativos sejam selecionados e clique no botão Importar para importar os ativos:

![Como selecionar todos os ativos a serem importados](images/mr-learning-base/base-02-section7-step1-3.png)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![Janela de projeto do Unity após importar os ativos](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a>Como configurar a cena

Na janela Projeto, navegue até a pasta Ativos > MRTK.Tutorials.GettingStarted > Pré-fabricados:

Na janela Projeto, clique e arraste o pré-fabricado **Cubo** para a janela Hierarquia, e na janela Inspetor configure o componente **Transformar** da seguinte forma

* **Posição**: X = 0, Y = 0, Z = 0,5
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Adicionando um cubo à cena](images/mr-learning-base/base-02-section8-step1-1.png)

Para aumentar o foco nos objetos da cena, você pode clicar duas vezes no objeto **Cubo** e aumentar levemente o zoom de novo:

Para interagir e segurar um objeto com as mãos rastreadas, o objeto deve ter um componente Colisor, por exemplo, um **Colisor de Caixa**, um componente **Manipulador de Objetos (script)** e um componente **NearInteractionGrabbable (script)** .

Para adicionar o script de Manipulador de Objetos ao objeto Cubo, mantenha o **Cubo** selecionado na janela Hierarquia, clique no botão **Adicionar Componente** na janela Inspetor e, em seguida, pesquise e selecione o script **Manipulador de Objetos**.

![Como adicionar o Manipulador de Objetos ao Cubo](images/mr-learning-base/base-02-section8-step1-2.png)

Repita o mesmo procedimento para adicionar o **script de Interação Próxima com Objeto Segurável** ao Cubo

![Como adicionar Interação Próxima com Objeto Segurável ao Cubo](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> Quando você adiciona um Object Manipulator (Script), nesse caso, o Constraint Manager (Script) é adicionado automaticamente porque o Object Manipulator (Script) depende dele.

> [!NOTE]
> Para os fins deste tutorial, os colisores já foram adicionados ao Objeto Cubo. Para saber mais sobre os colisores, acesse a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisor</a> do Unity.

Para fazer o teste no editor do Unity, acesse o modo de execução e mantenha pressionada a tecla **Shift da esquerda** ou a tecla **Espaço** para habilitar o controlador. Você pode mover o controlador com o mouse e usar o botão de rolagem para aproximá-lo ou afastá-lo da câmera. Com o ponteiro sobre o Cubo, mantenha pressionado o **botão direito do mouse** para mover o objeto Cubo.

![Modo de Jogo](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a>Como criar o aplicativo para o seu HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Compilar o projeto do Unity

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build.

Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar sua cena atual à lista **Cenas no Build** e clique no botão **Build** para abrir a janela Compilar Plataforma Universal do Windows:

![Janela Configurações de Build do Unity com o UWP selecionado](images/mr-learning-base/base-02-section9-step1-1.png)

Na janela Compilar Plataforma Universal do Windows, escolha um local adequado para armazenar seu build, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma nova pasta e dê a ela um nome adequado, por exemplo, _GettingStarted_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](images/mr-learning-base/base-02-section9-step1-2.png)

Aguarde até que o Unity conclua o processo de build:

![Processo de build do Unity em andamento](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilar e implantar o aplicativo

Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra a localização em que você armazenou o build. Navegue dentro da pasta e clique duas vezes no arquivo da solução para abri-lo no Visual Studio:

![Windows Explorer com a solução do Visual Studio recém-criada selecionada](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar-se de que você tenha todos os componentes de pré-requisitos na documentação **[Instalar as Ferramentas](../../install-the-tools.md)** .

Configure o Visual Studio para o HoloLens selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM64** e o **Dispositivo** como destino:

![Visual Studio configurado para implantação no HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> Se você estiver implantando no HoloLens (1ª geração), selecione a arquitetura **x86**.

> [!NOTE]
> Para o HoloLens, você normalmente criará para a arquitetura ARM. No entanto, há um <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conhecido</strong></a> no Unity 2019.3 que causa erros ao selecionar o ARM como a arquitetura de build no Visual Studio. A solução alternativa recomendada é criar para o ARM64. Se essa não for uma opção, acesse **Editar > Configurações de Projeto > Player > Outras Configurações** e desabilite **Trabalhos Gráficos**.

> [!NOTE]
> Se o Dispositivo não for exibido como uma opção de destino, talvez seja necessário alterar o projeto de inicialização para a solução do Visual Studio do projeto IL2CPP para o projeto UWP. Para fazer isso, no Gerenciador de Soluções, clique com o botão direito do mouse no NomeDoSeuProjeto (Universal do Windows) e selecione **Definir como Projeto de Inicialização**.

Conecte o seu HoloLens ao seu computador e, em seguida, selecione **Depurar** > **Iniciar sem Depuração** para criar e implantar no seu dispositivo:

![Caminho do menu Iniciar Sem Depuração do Visual Studio](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> Antes de compilar no dispositivo, ele precisa estar no Modo de Desenvolvedor e emparelhado com o computador de desenvolvimento. Essas duas etapas podem ser concluídas seguindo [estas instruções](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> Você também pode implantar no [Emulador do HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou criar um [Pacote do Aplicativo](/windows/uwp/packaging/packaging-uwp-apps) para sideload.

O uso de Iniciar sem Depuração inicia automaticamente o aplicativo no seu dispositivo sem o depurador do Visual Studio anexado.

Selecione **Criar > Implantar Solução** para implantar no seu dispositivo sem iniciar o aplicativo automaticamente.

> [!NOTE]
>Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **Alternar Diagnóstico**. É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho. Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Parabéns

Você acabou de implantar o seu primeiro aplicativo do HoloLens. Com o aplicativo aberto, você verá um objeto Cubo em sua frente poderá interagir com ele, movendo-o. Ao caminhar você verá uma malha de mapeamento espacial que sobre as superfícies que são detectadas pelo Microsoft HoloLens. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo. Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK. Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.

> [!div class="nextstepaction"]
> [Próximo tutorial: 3. Como configurar os perfis do MRTK](mr-learning-base-03.md)