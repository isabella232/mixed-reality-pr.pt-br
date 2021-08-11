---
title: HoloLens (1ª geração) e Azure 307 – Machine Learning
description: Conclua este curso para saber como implementar o Azure Machine Learning Studio (clássico) em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realidade misturada, academy, unity, tutorial, api, machine learning, ml, machine learning studio, hololens, imersivo, vr, Windows 10, Visual Studio
ms.openlocfilehash: 062be48afb69bf2c4fa2eddcd816070d4d2575da7f06fe4464fa87f85676796b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198873"
---
# <a name="hololens-1st-gen-and-azure-307-machine-learning"></a>HoloLens (1ª geração) e Azure 307: Aprendizado de máquina

<br>

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. Haverá uma nova série de tutoriais que serão postados no futuro que demonstrarão como desenvolver para HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles são postados.

<br>

![produto final -start](images/AzureLabs-Lab7-0.png)

Neste curso, você aprenderá a adicionar recursos Machine Learning (ML) a um aplicativo de realidade misturada usando o Azure Machine Learning Studio (clássico).

*Azure Machine Learning Studio (clássico)* é um serviço da Microsoft, que fornece aos desenvolvedores um grande número de algoritmos de aprendizado de máquina, que podem ajudar com a entrada, a saída, a preparação e a visualização de dados. Com base nesses componentes, é possível desenvolver um experimento de análise preditiva, iterá-lo e usá-lo para treinar seu modelo. Após o treinamento, você pode tornar seu modelo operacional na nuvem do Azure para que ele possa pontuar novos dados. Para obter mais informações, visite [a página Azure Machine Learning Studio (clássico).](https://azure.microsoft.com/services/machine-learning-studio/)

Depois de concluir este curso, você terá um aplicativo de headset imersivo de realidade misturada e terá aprendido como fazer o seguinte:

1.  Forneça uma tabela de dados de vendas para o portal *do Azure Machine Learning Studio (clássico)* e projete um algoritmo para prever vendas futuras de itens populares.
2.  Crie um **Project** Unity, que pode receber e interpretar dados de previsão do ML serviço.
3.  Exibe os dados de pré-Project visualmente no **unity Project** fornecendo os itens de vendas mais populares, em uma prateleira.

Em seu aplicativo, você deve saber como integrar os resultados ao seu design. Este curso foi projetado para ensinar como integrar um Serviço do Azure ao seu Project Unity. É seu trabalho usar o conhecimento que você ganha com este curso para aprimorar seu aplicativo de realidade misturada.

Este curso é um tutorial autossunte, que não envolve diretamente nenhum outro Laboratório de Realidade Misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 307: Aprendizado de máquina</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente Windows Mixed Reality headsets imersivos (VR), você também pode aplicar o que aprende neste curso para Microsoft HoloLens. Conforme você acompanha o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a HoloLens. Ao usar HoloLens, você pode observar algum eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com Unity e C#. Lembre-se também de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da redação (maio de 2018). Você é livre para usar o software mais recente, conforme listado no artigo Instalar as ferramentas [,](../../install-the-tools.md)embora não seja preciso assumir que as informações neste curso corresponderão perfeitamente ao que você encontrará em um software mais recente do que o listado abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um pc de desenvolvimento [compatível com Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headset imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](../../install-the-tools.md#installation-checklist)
- [O SDK Windows 10 mais recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Um [headset Windows Mixed Reality imersivo (VR)](../../../discover/immersive-headset-hardware-details.md) ou um Microsoft HoloLens [com](/hololens/hololens1-hardware) o modo desenvolvedor habilitado
- Acesso à Internet para instalação do Azure e ML recuperação de dados

## <a name="before-you-start"></a>Antes de começar

Para evitar problemas ao criar este projeto, é fortemente sugerido que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas no tempo de build). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capítulo 1 – Configuração da conta Armazenamento Azure

Para usar a API de Tradutor do Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.
1.  Faça logoff no [Portal do Azure.](https://portal.azure.com)

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, precisará criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ajuda ao instrutor ou a um dos proctors para configurar sua nova conta.

2.  Quando você está conectado, clique em Armazenamento **Contas no** menu à esquerda.

    ![Configuração da conta Armazenamento Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > A palavra **Novo** pode ter sido substituída por **Criar um recurso**, em portais mais novos.

3.  Na guia **Armazenamento,** clique em **Adicionar**.

    ![Configuração da conta Armazenamento Azure](images/AzureLabs-Lab7-2.png)

4.  No painel **Criar Armazenamento Conta:**

    1.  Insira um **Nome** para sua conta, esteja ciente de que esse campo aceita apenas números e letras minúsculas.
    2.  Para **Modelo de implantação,** selecione **Gerenciador de recursos.**
    3.  Para **Tipo de** conta, selecione Armazenamento **(uso geral v1)**.
    4.  Para **Desempenho**, selecione **Standard**.
    5.  Para **Replicação,** **selecione Ra-GRS (armazenamento com redundância geográfica com** acesso de leitura).
    6.  Deixe **Transferência segura necessária como** **Desabilitada.**
    7.  Selecione uma **Assinatura**.
    4. Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses laboratórios) em um grupo de recursos comum.

        > Se você quiser ler mais sobre os Grupos de Recursos do Azure, [visite o artigo do grupo de recursos](/azure/azure-resource-manager/resource-group-portal).
    
    5.  Determine o **Local** do grupo de recursos (se você estiver criando um novo Grupo de Recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

5.  Você também precisará confirmar que entendeu os Termos e Condições aplicados a esse Serviço.

    ![Configuração da conta Armazenamento Azure](images/AzureLabs-Lab7-3.png)

6.  Depois de clicar em **Criar**, você terá que aguardar até que o serviço seja criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal depois que a instância de serviço for criada.

    ![Configuração da conta Armazenamento Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a>Capítulo 2 – O Azure Machine Learning Studio (clássico)

Para usar o *Azure Machine Learning*, você precisará configurar uma instância do serviço Machine Learning para ser disponibilizada para seu aplicativo.

1.  No Portal do Azure, clique em Novo no canto superior esquerdo e pesquise por Machine Learning Workspace do **Studio,** pressione **Enter**. 

    ![O Azure Machine Learning Studio (clássico)](images/AzureLabs-Lab7-5.png)

2.  A nova página fornecerá uma descrição do **serviço Machine Learning Workspace do** Studio. Na parte inferior esquerda deste prompt, clique **no botão** Criar para criar uma associação com esse serviço.

3.  Depois de clicar em **Criar**, um painel será exibido no qual você precisará fornecer alguns detalhes sobre o novo serviço Machine Learning **Studio:**

    1.  Insira o nome do **Workspace desejado** para essa instância de serviço.

    2.  Selecione uma **Assinatura**.

    3. Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses laboratórios) em um grupo de recursos comum. 

        > Se você quiser ler mais sobre os Grupos de Recursos do Azure, [visite o artigo do grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    4.  Determine o **Local** do grupo de recursos (se você estiver criando um novo Grupo de Recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões. Você deve usar o mesmo grupo de recursos usado para criar o Armazenamento Azure no Capítulo anterior.

    5.  Para a **Armazenamento** da conta, clique em Usar existente e, em seguida, clique no menu suspenso e, a partir daí, clique na Armazenamento **conta** criada no último Capítulo.

    6.  Selecione o **nível de preço do Workspace apropriado** para você no menu suspenso.

    7.  Na seção **Plano de serviço Web,** clique **em Criar** novo **e insira** um nome para ele no campo de texto.

    8.  Na seção **Tipo de preço do plano de serviço** Web, selecione o tipo de preço de sua escolha. Uma camada de teste de desenvolvimento chamada **DEVTEST Standard** deve estar disponível para você gratuitamente.

    9.  Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    10. Clique em **Criar**.

        ![o Azure Machine Learning Studio (clássico)](images/AzureLabs-Lab7-6.png)

4.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

5.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![o Azure Machine Learning Studio (clássico)](images/AzureLabs-Lab7-7.png)

6.  Clique na notificação para explorar sua nova instância de serviço.

    ![o Azure Machine Learning Studio (clássico)](images/AzureLabs-Lab7-8.png)

7.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.

8.  na página exibida, na seção **Links adicionais** , clique em **iniciar o Machine Learning Studio**, que direcionará o navegador para o portal do **Machine Learning Studio** .

    ![o Azure Machine Learning Studio (clássico)](images/AzureLabs-Lab7-9.png)

9.  Use o botão **entrar** , na parte superior direita ou no centro, para fazer logon em seu Machine Learning Studio (clássico).

    ![o Azure Machine Learning Studio (clássico)](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a>capítulo 3-o Machine Learning Studio (clássico): configuração do conjunto de configurações

uma das maneiras de Machine Learning algoritmos funciona ao analisar os dados existentes e, em seguida, tentar prever os resultados futuros com base no conjunto de dados existente. Isso geralmente significa que quanto mais dados existentes você tiver, melhor será o algoritmo prevendo resultados futuros.

Uma tabela de exemplo é fornecida para você, para este curso, chamado [ProductsTableCSV e pode ser baixado aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> O arquivo de .zip acima contém o **ProductsTableCSV** e o **. unitypackage**, que serão necessários no [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package). Esse pacote também é fornecido dentro desse capítulo, embora separado para o arquivo CSV.

Este conjunto de dados de exemplo contém um registro dos objetos mais vendidos a cada hora de cada dia do ano de 2017.
        
![o Machine Learning Studio (clássico): configuração do conjunto de configurações](images/AzureLabs-Lab7-11.png)

Por exemplo, no dia 1 de 2017, às às 13:00 (hora 13), o item de vendas melhores era Salt e molho.

Esta tabela de exemplo contém 9998 entradas.

1.  volte para o portal do **Machine Learning Studio (clássico)** e adicione essa tabela como um **conjunto** de uma para seu ML. Para fazer isso, clique no botão **+ novo** no canto inferior esquerdo da tela.

    ![o Machine Learning Studio (clássico): configuração do conjunto de configurações](images/AzureLabs-Lab7-12.png)

2.  Uma seção será exibida na parte inferior e, dentro dela, há painel de navegação à esquerda. Clique em **conjunto** de um e, à direita disso, em **arquivo local**.

    ![o Machine Learning Studio (clássico): configuração do conjunto de configurações](images/AzureLabs-Lab7-13.png)

3.  Upload o novo **conjunto** de novos, seguindo estas etapas:

    1. A janela de carregamento será exibida, onde você poderá **procurar** o novo conjunto de um disco rígido.

        ![o Machine Learning Studio (clássico): configuração do conjunto de configurações](images/AzureLabs-Lab7-14.png)

    2.  Depois de selecionado e de volta à janela carregar, deixe a caixa de seleção sem marcação.

    3.  No campo de texto abaixo, insira **ProductsTableCSV.csv** como o nome do conjunto de (embora deva ser adicionado automaticamente).

    4.  Usando o menu suspenso para **tipo**, selecione **arquivo CSV genérico com um cabeçalho (.csv)**.

    5.  Pressione a escala no canto inferior direito da janela carregar e seu **conjunto** de resultados será carregado.

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a>capítulo 4-o Machine Learning Studio (clássico): o experimento

Antes de criar seu sistema de aprendizado de máquina, você precisará criar um experimento para validar sua teoria sobre seus dados. Com os resultados, você saberá se precisa de mais dados ou se não há nenhuma correlação entre os dados e um resultado possível.

Para começar a criar um experimento:

1.  Clique novamente no botão **+ novo** na parte inferior esquerda da página e **clique em**  >  **experimento em branco** experimento.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-15.png)

2.  Uma nova página será exibida com um experimento em branco:

3.  No painel à esquerda, expanda os conjuntos de itens **salvos**  >  **meus conjuntos** de valores e arraste o **ProductsTableCSV** para a **tela do experimento**.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-16.png)

4.  No painel à esquerda, expanda **Data Transformation**  >  **Sample e Split**. Em seguida, arraste o item **dividir dados** para a **tela do experimento**. O item dividir dados dividirá o conjunto de dados em duas partes. Uma parte que será usada para treinar o algoritmo de aprendizado de máquina. A segunda parte será usada para avaliar a precisão do algoritmo gerado.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-17.png)

5.  No painel direito (enquanto o item dividir dados na tela está selecionado), edite a **fração de linhas no primeiro conjunto** de dado de saída para **0,7**. Isso dividirá os dados em duas partes, a primeira parte será de 70% dos dados e a segunda parte será os 30% restantes. Para garantir que os dados sejam divididos aleatoriamente, verifique se a caixa de seleção **divisão aleatória** permanece marcada.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-18.png)

6.  Arraste uma conexão da base do item **ProductsTableCSV** na tela para a parte superior do item dividir dados. Isso irá conectar os itens e enviar a saída do conjunto de dados **ProductsTableCSV** (os dados) para a entrada Split Data.  

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-19.png)

7.  no painel **experimentos** no lado esquerdo, expanda **Machine Learning**  >  **Train**. Arraste o item **modelo de treinamento** para fora até a tela do experimento. Sua tela deve ter a seguinte aparência.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-20.png)

8.  Na **parte inferior esquerda** _ do item _ *dividir dados**, arraste uma conexão para a **parte superior direita** do item de **modelo de treinamento** . A primeira 70% de divisão do conjunto de um será usada pelo modelo de treinamento para treinar o algoritmo.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-21.png)

9.  Selecione o item **treinar modelo** na tela e, no painel **Propriedades** (no lado direito da janela do navegador), clique no botão **Iniciar seletor de coluna** .

10. Na caixa de texto, digite **produto** e pressione **Enter**, o *produto* será definido como uma coluna para treinar previsões. Depois disso, clique no **tique** no canto inferior direito para fechar a caixa de diálogo de seleção.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-22.png)

11. Você vai treinar um algoritmo de **regressão logística multiclasse** para prever o **produto** mais vendido com base na hora do dia e na data. está além do escopo deste documento para explicar os detalhes dos diferentes algoritmos fornecidos pelo Azure Machine Learning studio, porém, você pode saber mais sobre a folha de consulta do [algoritmo de Machine Learning](/azure/machine-learning/studio/algorithm-cheat-sheet)

12. no painel itens de experimento à esquerda, expanda **Machine Learning**  >  **inicializar**  >  **classificação** de modelo e arraste o item **regressão logística multiclasse** para a tela do experimento.

13. Conexão a saída, da parte inferior da **regressão logística multiclasse**, à entrada superior esquerda do item de modelo de **treinamento** .

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-23.png)

14. na lista de itens de teste no painel à esquerda, expanda **Machine Learning**  >  **pontuação** e arraste o item de **modelo de pontuação** para a tela.

15. Conexão a saída, na parte inferior do **modelo de treinamento**, para a entrada superior esquerda do modelo de **pontuação**.

16. Conexão a saída inferior direita de **dividir dados**, para a entrada superior direita do item de **modelo de pontuação** .

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-24.png)

17. na lista de itens de **teste** no painel à esquerda, expanda **Machine Learning**  >  **avaliar** e arraste o item modelo de **avaliação** para a tela.

18. Conexão a saída do **modelo de pontuação** para a entrada superior esquerda do modelo de **avaliação**.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-25.png)

19. você criou seu primeiro experimento de Machine Learning. Agora você pode salvar e executar o experimento. No menu na parte inferior da página, clique no botão **salvar** para salvar o experimento e, em seguida, clique em **executar** para iniciar o experimento.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-26.png)

20. Você pode ver o **status** do experimento no canto superior direito da tela. Aguarde alguns instantes até que o experimento seja concluído.

    > Se você tiver um grande conjunto de grandes (mundo real), é provável que o experimento possa levar horas para ser executado.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-27.png)

21. Clique com o botão direito do mouse no item **modelo** de avaliação na tela e, no menu de contexto, passe o mouse sobre **os resultados da avaliação** e selecione **Visualizar**.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-28.png)

22. Os resultados da avaliação serão exibidos mostrando as exibições previstas em relação aos resultados reais. Isso usa 30% do conjunto de um original, que foi dividido anteriormente, para avaliar o modelo. Você pode ver que os resultados não são ótimos, idealmente você teria o número mais alto em cada linha ser o item realçado nas colunas.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-29.png)

23. Feche os **resultados**.

24. para usar o modelo de Machine Learning treinado recentemente, você precisa expô-lo como um **serviço Web**. Para fazer isso, clique no item de menu **configurar serviço Web** no menu na parte inferior da página e clique em **serviço Web de previsão**.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-30.png)

25. Uma nova guia será criada e o modelo de treinamento mesclado para criar o novo serviço Web. 

26. No menu na parte inferior da página, clique em **salvar** e em **executar**. Você verá o status atualizado no canto superior direito da tela do experimento.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-31.png)

27. Quando a execução for concluída, um botão **implantar serviço Web** aparecerá na parte inferior da página. Você está pronto para implantar o serviço Web. Clique em **implantar serviço Web** (clássico) no menu na parte inferior da página.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-32.png)

    > O navegador pode solicitar a permissão de um pop-up, que você deve **permitir**, embora seja necessário pressionar **implantar serviço Web** novamente, se a página implantar não for mostrada. 

28. Depois que o experimento tiver sido criado, você será redirecionado para uma página de **painel** onde você terá sua **chave de API** exibida. Copie-o em um bloco de notas por enquanto, você precisará dele em seu código em breve. Depois de anotar sua chave de API, clique no botão **solicitação/resposta** na seção **ponto de extremidade padrão** abaixo da chave.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Se você clicar em testar nesta página, poderá inserir dados de entrada e exibir a saída. Insira o **dia** e a **hora**. Deixe a entrada do **produto** em branco. Em seguida, clique no botão **confirmar** . A saída na parte inferior da página mostrará o JSON que representa a probabilidade de cada produto ser a opção.

29. uma nova página da web será aberta, exibindo as instruções e alguns exemplos sobre a estrutura de solicitação exigida pelo Machine Learning Studio (clássico). Copie o **URI de solicitação** exibido nesta página, no bloco de notas.

    ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-34.png)

Agora você criou um sistema de aprendizado de máquina que fornece o produto mais provável para ser vendido com base nos dados de compra históricos, correlacionados com a hora do dia e dia do ano.

Para chamar o serviço Web, você precisará da URL para o ponto de extremidade de serviço e uma chave de API para o serviço. Clique na guia **consumir** , no menu superior.

A página informações de **consumo** exibirá as informações necessárias para chamar o serviço Web do seu código. Faça uma cópia da **chave primária** e da URL da **solicitação-resposta** . Você precisará deles no próximo capítulo.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capítulo 5-Configurando o Project do Unity

Configure e teste seu headset de imersão de realidade misturada.

> [!NOTE]
>  Você **não** precisará de controladores de animação para este curso. Se você precisar de suporte para configurar o headset de imersão, clique [aqui](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  abra o **unity** e crie um novo Project de unity chamado **sr \_ MachineLearning.** Verifique se o tipo de projeto está definido como **3D**.

2.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar**  >  **preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**. altere o **Editor de Script externo** para **Visual Studio 2017**. Feche a janela **preferências** .

3.  em seguida, vá para Build de **arquivo**  >  **Configurações** e alterne a plataforma para **Plataforma Universal do Windows** clicando no botão **_alternar plataforma_** .

4.  Verifique também se:

    1.  O **dispositivo de destino** está definido como **qualquer dispositivo**.

        > para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.

    2.  O **tipo de compilação** está definido como **D3D**.

    3.  O **SDK** está definido para o **mais recente instalado**.

    4.  **Visual Studio versão** está definida como **mais recente instalada**.

    5.  **Compilar e executar** é definido como **computador local**.

    6.  Não se preocupe com a configuração de **cenas** no momento, pois elas são fornecidas mais tarde.

    7.  As configurações restantes devem ser deixadas como padrão por enquanto.

        ![Configurando o Project do Unity](images/AzureLabs-Lab7-35.png)

5.  na janela **criar Configurações** , clique no botão **Configurações do Player** , isso abrirá o painel relacionado no espaço onde o **inspetor** está localizado. 

6. Nesse painel, algumas configurações precisam ser verificadas:

    1.  na guia **outros Configurações** :

        1.  A **versão de tempo de execução** de **script** deve ser **experimental** (.NET 4,6 equivalente)

        2. O **back-end de script** deve ser **_.net_**

        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Configurando o Project do Unity](images/AzureLabs-Lab7-36.png)

    2.  na guia **publicação Configurações** , em **recursos**, marque:

        - **InternetClient**

            ![Configurando o Project do Unity](images/AzureLabs-Lab7-37.png)

    3.  mais adiante no painel, em **XR Configurações** (encontrado abaixo **Configurações de publicação**), **há suporte para a realidade Virtual** de tique, verifique se o **SDK do Windows Mixed Reality** foi adicionado

        ![Configurando o Project do Unity](images/AzureLabs-Lab7-38.png)

    

6.  de volta ao **Build Configurações** projetos do *Unity C#* não estão mais esmaecidos; Marque a caixa de seleção ao lado deste. 

7.  Feche a janela Configurações de Build.

8.  salve seu Project (**arquivo > salvar projeto**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capítulo 6-importando o pacote do MLProducts Unity

Para este curso, você precisará baixar um pacote de ativos do Unity chamado [**Azure-Mr-307. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage). Esse pacote vem completo com uma cena, com todos os objetos criados, para que você possa se concentrar em fazê-lo funcionar. O script **ShelfKeeper** é fornecido, embora só mantenha as variáveis públicas, para fins de estrutura de configuração de cena. Você precisará fazer todas as outras seções. 

Para importar este pacote:

1.  Com o painel do Unity na frente, clique em **ativos** no menu na parte superior da tela e, em seguida, clique em **Importar pacote, pacote personalizado**.

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-39.png)

2.  Use o seletor de arquivos para selecionar o pacote **Azure-Mr-307. unitypackage** e clique em **abrir**.

3.  Uma lista de componentes para este ativo será exibida para você. Confirme a importação clicando em **importar**.

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-40.png)

4.  depois de concluir a importação, você observará que algumas pastas novas apareceram no painel de **Project** do Unity. Esses são os modelos 3D e os respectivos materiais que fazem parte da cena previamente realizada na qual você trabalhará. Você escreverá a maioria do código neste curso.

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-41.png)

5.  na pasta do **painel de Project** , clique na pasta **cenas** e clique duas vezes na cena dentro (chamada de **MR_MachineLearningScene**). A cena será aberta (consulte a imagem abaixo). Se os losangos vermelhos estiverem ausentes, basta clicar no botão **utensílios** , na parte superior direita do **painel Game**.

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capítulo 7-verificando as DLLs no Unity

Para aproveitar o uso de bibliotecas JSON (usadas para serialização e desserialização), uma DLL Newtonsoft foi implementada com o pacote que você colocou. A biblioteca deve ter a configuração correta, embora vale a pena verificar (especialmente se você estiver tendo problemas com o código não funcionando). 

Para fazer isso:

-  Clique com o botão esquerdo do mouse no arquivo Newtonsoft dentro da pasta plugins e examine o **painel Inspetor**. Verifique se **todas as plataformas** estão marcadas. Vá para a **guia UWP** e verifique também se **não processar** está marcado.

    ![Importando as DLLs no Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capítulo 8-criar a classe ShelfKeeper

A classe **ShelfKeeper** hospeda métodos que controlam a interface do usuário e os produtos gerados na cena.

Como parte do pacote importado, você receberá essa classe, embora ela esteja incompleta. Agora é hora de concluir essa classe:

1.  clique duas vezes no script **ShelfKeeper** , na pasta **Scripts** , para abri-lo com **Visual Studio 2017**.

2.  Substitua todo o código existente no script pelo código a seguir, que define a data e a hora e tem um método para mostrar um produto.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  certifique-se de salvar as alterações em **Visual Studio** antes de retornar ao **Unity**.

4.  De volta ao editor do Unity, verifique se a classe **ShelfKeeper** é semelhante à seguinte:

    ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Se o seu script não tiver os destinos de referência (ou seja, *Data (malha de texto)*), basta arrastar os objetos correspondentes do **painel hierarquia** para os campos de destino. Veja abaixo a explicação, se necessário:
    > 
    > 1.  Abra a matriz de **ponto de geração** dentro do script do componente **ShelfKeeper** clicando nela com o botão esquerdo. Uma subseção será exibida chamada de **tamanho**, o que indica o tamanho da matriz. Digite **3** na caixa de texto ao lado de **tamanho** e pressione **Enter**, e três slots serão criados abaixo.
    > 2. Na **hierarquia** , expanda o objeto de **exibição de hora** (clicando com o botão esquerdo do mouse na seta ao lado dele). Em seguida, clique na **_câmera principal_,*de dentro da hierarquia _***, para que o **Inspetor** mostre suas informações.
    > 3. Selecione a **câmera principal** no **painel hierarquia**. Arraste os objetos de **Data** e **hora** do **painel hierarquia** para os slots de texto de **Data** e **hora** dentro do **Inspetor** da **câmera principal** no componente **ShelfKeeper** .
    > 4. Arraste os **pontos de geração** do **painel hierarquia** (abaixo do objeto *prateleira* ) para os **três** destinos de referência de **elemento** abaixo da matriz de **ponto de geração** , conforme mostrado na imagem.
    > 
    >     ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capítulo 9-criar a classe ProductPrediction

A próxima classe que você vai criar é a classe **ProductPrediction** .

Essa classe é responsável por:

-   consultando a instância do **serviço de Machine Learning** , fornecendo a data e hora atuais.

-   Desserializando a resposta JSON em dados utilizáveis.

-   Interpretação dos dados, recuperação dos 3 produtos recomendados.

-   Chamar os métodos da classe **ShelfKeeper** para exibir os dados na cena.

Para criar esta classe:

1.  vá para a pasta **Scripts** no painel de **Project**.

2.  Clique com o botão direito do mouse dentro da pasta, **crie**  >  **script C#**. Chame o script **ProductPrediction**.

3.  clique duas vezes no novo script **ProductPrediction** para abri-lo com **Visual Studio 2017**.

4.  Se a caixa de diálogo **modificação de arquivo detectada** for exibida, clique em **_recarregar solução_*.

5.  Adicione os seguintes namespaces à parte superior da classe ProductPrediction:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  Dentro da classe **ProductPrediction** , insira os dois objetos a seguir que são compostos de várias classes aninhadas. essas classes são usadas para serializar e desserializar o JSON para o serviço de Machine Learning.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  Em seguida, adicione as seguintes variáveis acima do código anterior (para que o código relacionado ao JSON esteja na parte inferior do script, abaixo de todos os demais códigos e do caminho):

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > certifique-se de inserir a **chave primária** e o **ponto de extremidade de solicitação-resposta**, no Portal Machine Learning, nas variáveis aqui. As imagens abaixo mostram onde você teria levado a chave e o ponto de extremidade. 
    >  
    > ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![o Machine Learning Studio (clássico): o experimento](images/AzureLabs-Lab7-53-2.png)

8.  Insira este código dentro do método **Start ()** . O método **Start ()** é chamado quando a classe é inicializada:

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  este é o método que coleta a data e a hora de Windows e a converte em um formato que o nosso experimento Machine Learning pode usar para comparar com os dados armazenados na tabela.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. Você pode **excluir** o método **Update ()** , pois essa classe não o usará.

11. adicione o seguinte método que irá comunicar a data e hora atuais para o ponto de extremidade Machine Learning e receber uma resposta no formato JSON.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. Adicione o método a seguir, que é responsável pela desserialização da resposta JSON e pela comunicação do resultado da desserialização para a classe **ShelfKeeper** . Esse resultado será o nome dos três itens previstos para vender o máximo em data e hora atuais. Insira o código abaixo na classe **ProductPrediction** , abaixo do método anterior.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. salve **Visual Studio** e vá de volta para o **Unity**.

14. Arraste o script da classe **ProductPrediction** da pasta **script** para o objeto **principal da câmera** .

15. salve a cena e o **arquivo** de projeto  >  **salvar cena/arquivo**  >  **salvar Project**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capítulo 10 – criar a solução UWP

Agora é hora de criar seu projeto como uma solução UWP, para que ele possa ser executado como um aplicativo autônomo.

Para compilar:

1.  Salve a cena atual clicando em **arquivo**  >  **salvar cenas**.

2.  ir para o Build do **arquivo**  >  **Configurações**

3.  Marque a caixa chamada **projetos do Unity C#** (isso é importante porque ele permitirá que você edite as classes após a conclusão da compilação).

4.  Clique em **Adicionar e abrir cenas**,

5.  Clique em **Compilar**.

    ![Compilar a solução UWP](images/AzureLabs-Lab7-54.png)

6.  Você será solicitado a selecionar a pasta na qual deseja criar a solução.

7.  Crie uma pasta **Builds** e dentro dessa pasta crie outra pasta com um nome apropriado de sua escolha.

8.  Clique na nova pasta e, em seguida, clique em **Selecionar pasta** para iniciar a compilação nesse local.

    ![Compilar a solução UWP](images/AzureLabs-Lab7-55.png)

    ![Compilar a solução UWP](images/AzureLabs-Lab7-56.png)

9.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

## <a name="chapter-11---deploy-your-application"></a>Capítulo 11 – implantar seu aplicativo

Para implantar seu aplicativo:

1.  Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com **Visual Studio**.

2.  com o Visual Studio aberto, você precisa restaurar NuGet pacotes, o que pode ser feito clicando com o botão direito do mouse em sua solução de MachineLearningLab_Build, na Gerenciador de Soluções (localizada à direita de Visual Studio) e, em seguida, clicando em restaurar pacotes de NuGet:

    ![Adicionar pacotes do NuGet](images/AzureLabs-Lab7-57.png)

3.  Na configuração da solução, selecione **depurar**.

4.  Na plataforma da solução, selecione **x86**, **computador local**. 

    > para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador. No entanto, também será necessário fazer o seguinte:
    > - conheça o **endereço IP** do seu HoloLens, que pode ser encontrado na *Configurações > rede & Internet > Wi-Fi opções avançadas*; o IPv4 é o endereço que você deve usar. 
    > - Verificar se o modo **de** **desenvolvedor** está ativado; encontrado em *Configurações > atualização & > de segurança para desenvolvedores*.

    ![Adicionar pacotes do NuGet](images/AzureLabs-Lab7-58.png)

5.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu PC.

6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.

Ao executar o aplicativo de realidade misturada, você verá o banco que foi configurado em sua cena do Unity e a partir da inicialização, os dados configurados no Azure serão buscados. Os dados serão desserializados em seu aplicativo, e os três resultados principais para sua data e hora atuais serão fornecidos visualmente, como três modelos no banco.


## <a name="your-finished-machine-learning-application"></a>seu aplicativo Machine Learning concluído
 
parabéns, você criou um aplicativo de realidade misturada que aproveita as Azure Machine Learning para fazer previsões de dados e exibi-las em sua cena.

![Adicionar pacotes do NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Exercício

**Exercício 1**

Experimente a ordem de classificação do seu aplicativo e faça com que as três previsões inferiores apareçam na prateleira, pois esses dados seriam potencialmente úteis também.

**Exercício 2**

Usando **tabelas do Azure** , preencha uma nova tabela com informações de clima e crie um novo experimento usando os dados.