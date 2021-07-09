---
title: Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como configurar seu projeto do Unity para o MRTK (Kit de Ferramentas de Realidade Misturada) e como implantá-lo no HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175969"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Como inicializar o seu projeto e implantar o primeiro aplicativo

Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do MRTK (Kit de Ferramentas de Realidade Misturada) e importar o MRTK. Você também aprenderá mais sobre como configurar, compilar e implantar uma cena básica do Unity do Visual Studio para o HoloLens 2. Depois de implantá-la no HoloLens 2, você verá uma malha de mapeamento espacial que abrange as superfícies percebidas pelo HoloLens. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.

## <a name="objectives"></a>Objetivos

* Saiba como configurar o Unity para o desenvolvimento no HoloLens
* Saiba como criar e implantar o seu aplicativo no HoloLens
* Experimente a malha de mapeamento espacial, as malhas de mão e o contador da taxa de quadros no dispositivo HoloLens 2

### <a name="steps-overview"></a>Visão geral das etapas
:::row:::
    :::column:::
       ![Visão Geral da Etapa 1](images/mr-learning-base/base-02-overview-step1.png) **1. Criar um novo projeto do Unity**
    :::column-end:::
    :::column:::
       ![Visão Geral da Etapa 2](images/mr-learning-base/base-02-overview-step2.png) **2. Importar o MRTK para o projeto**
    :::column-end:::
    :::column:::
       ![Visão Geral da Etapa 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configurar uma nova cena com o MRTK**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![Visão Geral da Etapa 4](images/mr-learning-base/base-02-overview-step4.png) **4. Compilar o Projeto do Unity**
    :::column-end:::
    :::column:::
       ![Visão Geral da Etapa 5](images/mr-learning-base/base-02-overview-step5.png) **5. Compilar o Projeto do UWP**
    :::column-end:::
    :::column:::
       ![Visão Geral da Etapa 6](images/mr-learning-base/base-02-overview-step6.png) **6. Executar o Projeto no Dispositivo**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>Como criar o projeto do Unity

Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

Na lista suspensa, selecione a **versão** do Unity especificada em [Pré-requisitos](mr-learning-base-01.md#prerequisites):

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> Se a versão específica do Unity não estiver disponível no Hub do Unity, você poderá iniciar a instalação em <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Arquivos de Download</a> do Unity.

Na janela Criar um novo projeto:

* Verifique se **Modelos** está definido como **3D**
* Insira um **Nome de Projeto** adequado, por exemplo, _Tutoriais do MRTK_
* Escolha um **Local** adequado para armazenar seu projeto, por exemplo, _D:\MixedRealityLearning_
* Clique no botão **Criar** para criar e iniciar o novo projeto do Unity

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres. Consequentemente, você deve salvar o projeto do Unity próximo à raiz da unidade.

Aguarde até que o Unity crie o projeto:

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>Como alternar a plataforma de build

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build:

![Caminho do menu Configurações de Build... do Unity](images/mr-learning-base/base-02-section2-step1-1.png)

Na janela Configurações de Build, selecione **Plataforma Universal do Windows** e:

1. Defina o **Dispositivo de destino** como **HoloLens**
2. Defina a **Arquitetura** como **ARM 64** 
3. Defina **Tipo de Build** como **Projeto D3D**
4. Defina **Versão do SDK de destino** como **Última instalação**
5. Defina **Versão Mínima da Plataforma** como **10.0.1024.0**
6. Defina **Versão do Visual Studio** como **Instalação mais recente**
7. Defina **Compilar e executar em** como **Dispositivo USB**
8. Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar
9. Pressione o botão Alternar Plataforma

![Configurações de Build do Unity com conjunto de configurações da Plataforma Universal do Windows](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

Aguarde até que o Unity termine de mudar a plataforma:

![Alternância de plataforma do Unity em andamento](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

Quando o Unity terminar de alternar a plataforma, clique no ícone **x** para fechar a janela Configurações de Build.

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>Como importar o Kit de ferramentas de Realidade Misturada e configurar o projeto do Unity

Para importar o Kit de Ferramentas de Realidade Misturada no projeto do Unity, você terá que usar a [Ferramenta de Recursos da Realidade Misturada](../welcome-to-mr-feature-tool.md) que permite aos desenvolvedores descobrir, atualizar e adicionar pacotes de recursos de Realidade Misturada a projetos do Unity. Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.

Baixe a última versão da Ferramenta de Recursos da Realidade Misturada no [Centro de Download da Microsoft](https://aka.ms/MRFeatureTool). Quando o download for concluído, descompacte o arquivo e salve-o na sua área de trabalho.

> [!NOTE]
> Para executar a Ferramenta de Recursos da Realidade Misturada, instale o [runtime do .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)

Abra o arquivo executável **MixedRealityFeatureTool** na pasta baixada para iniciar a Ferramenta de Recursos da Realidade Misturada.  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Como criar a cena e configurar o MRTK

No menu do Unity, selecione **Arquivo** > **Nova Cena**:

![Caminho do menu Nova Cena do Unity](images/mr-learning-base/base-02-section6-step1-1.png)

Na janela **Nova Cena**, selecione **Básico (Interno)** e clique em **criar** para criar uma nova cena:

![Janela Nova Cena do Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> A captura de tela acima é da Versão 2020 do Unity. Se você estiver usando o Unity 2019, ao clicar em **criar**, uma nova cena vazia será criada.

No menu do Unity, selecione **Realidade Misturada** > **Kit de Ferramentas** > **Adicionar à Cena e Configurar...** para adicionar o MRTK à cena atual:

![Caminho do menu Adicionar à Cena e Configurar... do Unity](images/mr-learning-base/base-02-section6-step1-2.png)

Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, na janela Inspetor, verifique se o perfil de configuração **MixedRealityToolkit** está definido como **DefaultMixedRealityToolkitConfigurationProfile**:

![Componente MixedRealityToolkit do Unity com DefaultMixedRealityTookitConfigurationProfile selecionado](images/mr-learning-base/base-02-section6-step1-3.png)

No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:

![Caminho do menu Salvar como... do Unity](images/mr-learning-base/base-02-section6-step1-4.png)

Salve a cena no projeto em **Ativos** > **Cenas**.

![Janela de prompt Salvar para salvar a cena do Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>Adicionando interação à mão a um objeto

No menu do Unity, selecione **GameObject** > **Objeto 3D** > **Cubo** para adicionar um objeto de cubo à cena.

![Adicionando um cubo à cena](images/mr-learning-base/base-02-section8-step1-1.png)

Clique no objeto **Cubo** na janela Hierarquia, e na janela Inspetor configure o componente **Transformar** da seguinte forma

* **Posição**: X = 0, Y = -0.1, Z = 0,5
* **Rotação**: X = 0, Y = 0, Z = 0
* **Escala**: X = 0,1, Y = 0,1, Z = 0,1

1 unidade Unity é 1 metro. Atualizamos o tamanho do cubo para 10x10x10 cm, posicionado a 50cm da posição do headset (0, 0, 0). 10cm abaixo do nível dos olhos para uma interação confortável. 

Se você usar a escala padrão (1, 1, 1), o cubo ficará muito grande. Se você usar a posição padrão (0, 0, 0), o cubo será colocado na mesma posição que o headset, e você não poderá vê-lo até que você se mova para trás.

![Ajustando informações de transformação](images/mr-learning-base/base-02-section8-step1-1b.png)

Para aumentar o foco nos objetos da cena, você pode clicar duas vezes no objeto **Cubo** e aumentar levemente o zoom de novo. Ou você pode usar a tecla F para aplicar zoom e focar no objeto.

Para interagir e pegar um objeto com as mãos acompanhadas, o objeto deve ter:
 * Componente colisor, como **Colisor de Caixa** (o cubo do Unity já tem um Colisor de Caixa por padrão)
 * Componente **Object Manipulator (Script)**
 * Componente **NearInteractionGrabbable(Script)**

O script **ObjectManipulator** do MRTK torna um objeto móvel, dimensionável e giratório usando uma ou as duas mãos. Esse script dá suporte ao modelo de entrada de manipulação direta, pois permite que o usuário toque os hologramas diretamente com as mãos.

Para adicionar o script de Manipulador de Objetos ao objeto Cubo, mantenha o **Cubo** selecionado na janela Hierarquia, clique no botão **Adicionar Componente** na janela Inspetor e, em seguida, pesquise e selecione o script **Manipulador de Objetos**.

![Como adicionar o Manipulador de Objetos ao Cubo](images/mr-learning-base/base-02-section8-step1-2.PNG)

Repita o mesmo procedimento para adicionar o **script de Interação Próxima com Objeto Segurável** ao Cubo

![Como adicionar Interação Próxima com Objeto Segurável ao Cubo](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> Quando você adiciona um Object Manipulator (Script), nesse caso, o Constraint Manager (Script) é adicionado automaticamente porque o Object Manipulator (Script) depende dele.

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>Testando seu aplicativo no editor do Unity com a simulação de entrada do MRTK

Com a simulação de entrada do MRTK, você pode testar vários tipos de interações no editor do Unity sem compilar e implantar em um dispositivo. Isso permite que você itere rapidamente suas ideias no processo de design e desenvolvimento. Use combinações de teclado e mouse para controlar as entradas simuladas.

Clique no botão reproduzir e insira o modo de reprodução. Mantenha pressionada a tecla **Shift da Esquerda** ou a tecla **Espaço** para exibir o controlador (mãos simuladas). Você pode mover o controlador com o mouse e usar o botão de rolagem para aproximá-lo ou afastá-lo da câmera. Com o ponteiro sobre o Cubo, mantenha pressionado o **botão esquerdo do mouse** para segurar o objeto Cubo.

* Pressione as teclas **W, A, S, D, Q, E** para mover a câmera.
* Mantenha o **Botão direito do mouse** pressionado e mova o mouse para examinar.
* Para exibir as mãos simuladas, pressione **Barra de espaço (à direita)** ou **tecla SHIFT esquerda**
* Para manter as mãos simuladas no modo de exibição, pressione as teclas **T** ou **Y**
* Para girar as mãos simuladas, pressione e mantenha pressionada a tecla **Ctrl** e mova o mouse

![Modo de Jogo](images/mr-learning-base/base-02-section8-step1-4.gif)


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
>Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **“Alternar Diagnóstico”** . É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho. Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Parabéns

Você acabou de implantar o seu primeiro aplicativo do HoloLens. Com o aplicativo aberto, você verá um objeto Cubo em sua frente poderá interagir com ele, movendo-o. Ao caminhar você verá uma malha de mapeamento espacial que sobre as superfícies que são detectadas pelo Microsoft HoloLens. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo. Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK. Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.

> [!div class="nextstepaction"]
> [Próximo tutorial: 3. Como configurar os perfis do MRTK](mr-learning-base-03.md)
