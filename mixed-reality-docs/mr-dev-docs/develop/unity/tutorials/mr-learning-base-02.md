---
title: Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como configurar seu projeto do Unity para o MRTK (Kit de Ferramentas de Realidade Misturada) e como implantá-lo no HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 2ce119e1dd18eacf02088d00e99fb70d06bf956e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008216"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Como inicializar o seu projeto e implantar o primeiro aplicativo

Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> e importar o MRTK. Você também aprenderá mais sobre como configurar, compilar e implantar uma cena básica do Unity do Visual Studio para o HoloLens 2. Depois de implantá-la no HoloLens 2, você verá uma malha de mapeamento espacial que abrange as superfícies percebidas pelo HoloLens. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.

## <a name="objectives"></a>Objetivos

* Saiba como configurar o Unity para o desenvolvimento no HoloLens.
* Saiba como criar e implantar seu aplicativo no HoloLens.
* Experimente a malha de mapeamento espacial, as malhas de mão e o contador da taxa de quadros no dispositivo HoloLens 2.

## <a name="creating-the-unity-project"></a>Como criar o projeto do Unity

1. Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:

![Hub do Unity com a seta para baixo do botão "Novo" realçada](images/mr-learning-base/base-02-section1-step1-1.png)

2. No menu suspenso, selecione a versão do Unity especificada nos [Pré-requisitos](mr-learning-base-01.md#prerequisites):

![Selecionar a versão do Unity](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Se a versão específica do Unity não estiver disponível no Hub do Unity, você poderá iniciar a instalação em <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Arquivos de Download</a> do Unity.

3. Na janela **Criar um projeto**, faça o seguinte:

    * Verifique se **Modelos** está definido como **3D**.
    * Na caixa **Nome do Projeto**, insira um nome adequado para seu projeto (por exemplo, "Tutoriais do MRTK").
    * Clique no botão de três pontos ao lado de **Localização** e procure a pasta em que deseja salvar o projeto.

> [!CAUTION]
> Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres. Por conta disso, você deve salvar o projeto do Unity próximo à raiz da unidade.

    * Selecione o botão **Criar**. Isso cria e inicia o projeto do Unity.

![Hub do Unity com a janela "Criar um projeto" preenchida](images/mr-learning-base/base-02-section1-step1-3.png)

A barra de status mantém você atualizado sobre seu progresso.

![A barra de progresso do Unity mantém você atualizado sobre o status de "criar projeto"](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Como alternar a plataforma de build

1. Na barra de menus, selecione **Arquivo** > **Configurações de Build...**

![Caminho do menu Configurações de Build... do Unity](images/mr-learning-base/base-02-section2-step1-1.png)

2. Na janela **Configurações de Build**, selecione **Plataforma Universal do Windows** e clique no botão **Mudar Plataforma**:

![Janela Configurações de Build do Unity com o UWP selecionado para alternar a plataforma da opção Autônomo](images/mr-learning-base/base-02-section2-step1-2.png)

3. Aguarde até que o Unity termine de mudar a plataforma e feche a janela **Configurações de Build**.

## <a name="importing-the-textmeshpro-essential-resources"></a>Como importar os Recursos Essenciais do TextMeshPro

Os Recursos Essenciais do TextMeshPro são exigidos pelos elementos da interface do usuário do MRTK. Se não estiver planejando usar os elementos de interface do usuário do MRTK no seu projeto, ignore esta etapa.

1. Na barra de menus, selecione **Janela** > **TextMeshPro** > **Importar Recursos Essenciais do TMP**.

![Caminho do menu Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-1.png)

2. Na janela **Importar Pacote do Unity**, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:

![Janela Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>Como importar o Kit de Ferramentas de Realidade Misturada

1. Baixe o pacote personalizado do Unity:

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. Na barra de menus, selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** .
3. Na caixa de diálogo **Importar pacote...** , procure a localização do pacote recém-baixado, selecione-o e clique no botão **Abrir**.
4. Na janela **Importar Pacote do Unity**, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos.

## <a name="selecting-mrtk-and-project-settings"></a>Como selecionar as configurações de projeto e do MRTK

Depois que o Unity terminar de importar o pacote da seção anterior, a janela **Configurador de Projeto do MRTK** será exibida. Caso contrário, você pode abri-la manualmente acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**:

![Caminho do menu Configurar Projeto do Unity no Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. Na janela **Configurador de Projeto do MRTK**, expanda a seção **Modificar Configurações**, se necessário, e verifique se todas as opções estão selecionadas.

![Janela Configurador de Projeto do MRTK no Unity com a opção Modificar Configurações exibida](images/mr-learning-base/base-02-section5-step1-2.png)

2. Para aplicar as configurações, clique no botão **Aplicar**.

![Botão Aplicar no MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> Você está usando o XR herdado interno do Unity em vez do novo Sistema de Plug-ins do XR, porque o novo sistema não é totalmente compatível com as [versões recomendadas do Unity e do MRTK](mr-learning-base-01.md#prerequisites) para esta série de tutoriais. Se você receber algum aviso sobre o XR interno ser preterido, ignore-o.

> [!TIP]
> A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:
>
> * Habilitar o XR herdado: habilita a VR para o projeto.
> * Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho. Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) da documentação [Desempenho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) do MRTK.
> * Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial. Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.

3. Na barra de menus, selecione **Editar** > **Configurações de Projeto...** .

4. Na janela **Configurações de Projeto**, selecione **Player**, clique na lista suspensa **Configurações de XR** e escolha a caixa ao lado de **Realidade Virtual Compatível**:

![Configurações de XR no Unity com a opção Realidade Virtual Compatível exibida](images/mr-learning-base/base-02-section5-step2-2.png)

Isso importa o SDK do Windows Mixed Reality:

![Configurações de XR no Unity com a opção SDKs de Realidade Virtual exibida](images/mr-learning-base/mixed-reality-sdk.png)

Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela **Configurador de Projeto do MRTK** será exibida novamente. Caso contrário, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity** para abri-lo.

5. Na janela **Configurador de Projeto do MRTK**, clique na lista suspensa **Espacializador de áudio** e selecione **Espacializador MS HRTF**.

![Configurações de projeto com as opções Espacializador de áudio exibidas](images/mr-learning-base/base-02-section5-step2-3.png)

6. Clique no botão **Aplicar**. Isso fechará a janela **Configurador de Projeto do MRTK**.

    > [!TIP]
    > A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto. Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada. Para saber mais sobre este tópico, veja os Tutoriais sobre áudio espacial.

7. Na janela **Configurações de Projeto**, clique na lista suspensa **Formato de Profundidade** e selecione **Profundidade de 16 bits**:

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Configurações de XR do Unity com profundidade de 16 bits selecionada.":::

    > [!TIP]
    > A redução do formato de profundidade para 16 bits é opcional, mas pode ajudar a aprimorar o desempenho gráfico no projeto. Para saber mais sobre este tópico, veja a seção [Compartilhamento de buffer de profundidade (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) da documentação [Desempenho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) do MRTK.

8. Clique na lista suspensa **Configurações de Publicação** e, na caixa **Nome do pacote**, insira um nome adequado (por exemplo, "MRTK-Tutoriais-Getting-Started").

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Configurações de Publicação do Unity com o Nome do pacote configurado.":::

    **Nome do Pacote e Nome do Produto**

    - O 'Nome do pacote' é o identificador exclusivo do aplicativo. Você deve criar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.
    - O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens. Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Configurações de Projeto do Unity com o Nome de produto configurado.":::

9. Feche a janela **Configurações de Projeto**.

## <a name="creating-and-configuring-the-scene"></a>Como criar e configurar a cena

1. Na barra de menus, selecione **Arquivo** > **Nova Cena**.
2. Para adicionar o MRTK à cena, na barra de menus, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** .

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Caminho do menu Adicionar à Cena e Configurar... do Unity.":::

3. Na janela **Hierarquia**, verifique se **MixedRealityToolkit** está selecionado.

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Verificar se MixedRealityTookit está selecionado.":::

4. Na seção **MixedRealityToolkit** da janela **Inspetor**, confirme se o perfil de configuração está definido como **DefaultMixedRealityToolkitConfigurationProfile**:

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Componente MixedRealityToolkit do Unity com DefaultMixedRealityTookitConfigurationProfile selecionado.":::

    > [!IMPORTANT]
    > Normalmente, você usará o DefaultHoloLens2ConfigurationProfile ao desenvolver para o HoloLens. No entanto, para este tutorial, você usará o DefaultMixedRealityToolkitConfigurationProfile. No próximo tutorial, [Como configurar os perfis do MRTK](mr-learning-base-03.md), você o trocará pelo DefaultHoloLens2ConfigurationProfile.

5. Na barra de menus, selecione **Arquivo** > **Salvar como...**
6. Na caixa de diálogo **Salvar Cena**, procure a pasta **Cenas** do projeto. Na caixa **Nome do arquivo**, dê um nome adequado à sua cena (por exemplo, "\_GettingStarted\_") e clique no botão **Salvar**.

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Janela do prompt Salvar para salvar a cena do Unity.":::

## <a name="building-and-deploying-to-your-hololens-2"></a>Build e implantação no HoloLens 2

> Antes do build no seu dispositivo, confirme o seguinte:
- Seu dispositivo está no Modo de Desenvolvedor.
- Ele está emparelhado com o computador de desenvolvimento. Caso contrário, você verá a seguinte caixa de diálogo no Visual Studio durante o processo de build:

![Como inserir o PIN para emparelhamento de dispositivos](images/mr-learning-base/pin-request.png)

 Para saber mais sobre essas duas etapas, confira [Como usar o Visual Studio para implantação e depuração](../../platform-capabilities-and-apis/using-visual-studio.md).

1. Na barra de menus, selecione **Arquivo** > **Configurações de Build...** .
2. Na janela **Configurações de Build**, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**.

![Adicionar a cena atual à lista "Cenas no Build"](images/mr-learning-base/base-02-section7-step1-1.png)

3. Clique no botão **Compilar**.

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Clique no botão Compilar.":::

4. Na caixa de diálogo **Compilar Plataforma Universal do Windows**, escolha uma localização adequada para armazenar o build (por exemplo, o ideal é criar uma pasta "Builds" na pasta "Tutoriais do MRTK"). Crie uma pasta e dê a ela um nome adequado (por exemplo, "GettingStarted"). Selecione a pasta e clique no botão **Selecionar Pasta** para iniciar o processo de build.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Janela Build do Unity com a pasta de build exibida.":::

    Uma barra de status será exibida e manterá você atualizado sobre o progresso do build.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Processo de build do Unity em andamento.":::

    > [!TIP]
    > Você também pode implantar no [Emulador do HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou criar um [Pacote do Aplicativo](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para sideload.

5. Quando o processo de build for concluído, no Explorador de Arquivos, procure a localização em que você armazenou o build e clique duas vezes no arquivo de solução para abri-lo no Visual Studio:

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Windows Explorer com o arquivo de solução do Visual Studio recém-criado selecionado.":::

    > [!NOTE]
    > Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar-se de que você tenha todos os componentes de pré-requisitos na documentação **[Instalar as Ferramentas](../../install-the-tools.md)** .

6. Configure o Visual Studio para o HoloLens selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM64** e **Dispositivo** como o destino.

    > [!TIP]
    > Se você estiver implantando no HoloLens (1ª geração), selecione a arquitetura **x86**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio configurado para implantação no HoloLens 2.":::

    > [!NOTE]
    > Para o HoloLens, você normalmente criará para a arquitetura ARM. No entanto, há um <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conhecido</strong></a> no Unity 2019.3 que causa erros ao selecionar o ARM como a arquitetura de build no Visual Studio. A solução alternativa recomendada é criar para o ARM64. Se essa não for uma opção, acesse **Editar > Configurações de Projeto > Player > Outras Configurações** e desabilite **Trabalhos Gráficos**.

    > [!NOTE]
    > Se o Dispositivo não for exibido como uma opção de destino, talvez seja necessário alterar o projeto de inicialização para a solução do Visual Studio do projeto IL2CPP para o projeto UWP. Para fazer isso, no Gerenciador de Soluções, clique com o botão direito do mouse em NomeDoProjeto (Universal do Windows) e selecione **Definir como Projeto de Inicialização**.

7. Conecte o HoloLens ao computador e siga um destes procedimentos:
- Para compilar o aplicativo, implante-o no HoloLens e inicie-o automaticamente sem o depurador do Visual Studio anexado. Na barra de menus, selecione **Depurar** > **Iniciar Sem Depuração**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Caminho do menu Iniciar Sem Depuração do Visual Studio.":::

- Para compilar e implantar o aplicativo no HoloLens, mas não o iniciar automaticamente, na barra de menus, selecione **Build > Implantar Solução**.

    > [!NOTE]
    >Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **Alternar Diagnóstico**. É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho. Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Parabéns

Você acabou de implantar o seu primeiro aplicativo do HoloLens. Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies detectadas pelo HoloLens. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo. Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK. Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.

> [!div class="nextstepaction"]
> [Próximo tutorial: 3. Como configurar os perfis do MRTK](mr-learning-base-03.md)
