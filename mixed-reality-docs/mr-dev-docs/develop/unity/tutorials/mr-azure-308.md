---
title: HoloLens (1ª geração) e Azure 308 – Notificações entre dispositivos
description: Conclua este curso para aprender a implementar Hubs de Notificação do Azure, Azure Functions e tabelas e Armazenamento do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realidade misturada, academy, unity, tutorial, api, notificação, funções, tabelas, hubs de notificação, hololens, imersivo, vr, Windows 10, Visual Studio
ms.openlocfilehash: 01d096297a9fbe25d39b2846acd2ee89b50edcfd26456f3f20ccd2c9bc26b514
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205225"
---
# <a name="hololens-1st-gen-and-azure-308-cross-device-notifications"></a>HoloLens (1ª geração) e Azure 308: notificações entre dispositivos

<br>

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. Haverá uma nova série de tutoriais que serão postados no futuro que demonstrarão como desenvolver para HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles são postados.

<br>

![produto final -start](images/AzureLabs-Lab8-00.png)

Neste curso, você aprenderá a adicionar recursos de Hubs de Notificação a um aplicativo de realidade misturada usando Hubs de Notificação do Azure, Tabelas do Azure e Azure Functions.

Os Hubs de Notificação do **Azure** são um serviço da Microsoft, que permite aos desenvolvedores enviar notificações por push direcionadas e personalizadas para qualquer plataforma, todas fornecidas na nuvem. Isso pode efetivamente permitir que os desenvolvedores se comuniquem com os usuários finais ou até mesmo se comuniquem entre vários aplicativos, dependendo do cenário. Para obter mais informações, visite a página Hubs de [Notificação](/azure/notification-hubs/notification-hubs-push-notification-overview) **do Azure** .

**Azure Functions** é um serviço da Microsoft, que permite aos desenvolvedores executar pequenos trechos de código, 'funções', no Azure. Isso fornece uma maneira de delegar o trabalho para a nuvem, em vez de seu aplicativo local, o que pode ter muitos benefícios. **Azure Functions** dá suporte a várias linguagens de desenvolvimento, incluindo \# \# C, F, Node.js, Java e PHP. Para obter mais informações, visite a **página Azure Functions** [.](/azure/azure-functions/functions-overview)

**As Tabelas do Azure** são um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados não SQL estruturados na nuvem, tornando-os facilmente acessíveis em qualquer lugar. O serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível. Para obter mais informações, visite a **página Tabelas do Azure** [](/azure/cosmos-db/table-storage-overview)

Depois de concluir este curso, você terá um aplicativo de headset imersivo de realidade misturada e um aplicativo de computador desktop, que poderá fazer o seguinte:

1. O aplicativo de computador desktop permitirá que o usuário mova um objeto no espaço 2D (X e Y), usando o mouse.

2. A movimentação de objetos dentro do aplicativo pc será enviada para a nuvem usando JSON, que estará na forma de uma cadeia de caracteres, contendo uma ID de objeto, tipo e informações de transformação (coordenadas X e Y). 

3. O aplicativo de realidade misturada, que tem uma cena idêntica ao aplicativo da área de trabalho, receberá notificações sobre a movimentação de objeto do serviço Hubs de Notificação (que acabou de ser atualizado pelo aplicativo de computador desktop). 

4. Ao receber uma notificação, que conterá a ID do objeto, o tipo e as informações de transformação, o aplicativo de realidade misturada aplicará as informações recebidas à sua própria cena.

Em seu aplicativo, você deve saber como integrar os resultados ao seu design. Este curso foi projetado para ensinar como integrar um Serviço do Azure ao seu Project Unity. É seu trabalho usar o conhecimento que você ganha com este curso para aprimorar seu aplicativo de realidade misturada. Este curso é um tutorial autossunte, que não envolve diretamente nenhum outro Laboratório de Realidade Misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 308: notificações entre dispositivos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente Windows Mixed Reality headsets imersivos (VR), você também pode aplicar o que aprende neste curso para Microsoft HoloLens. Conforme você acompanha o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a HoloLens. Ao usar HoloLens, você pode observar algum eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com Unity e C#. Lembre-se também de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da redação (maio de 2018). Você é livre para usar o software [](../../install-the-tools.md) mais recente, conforme listado no artigo Instalar as ferramentas, embora não seja preciso assumir que as informações neste curso corresponderão perfeitamente ao que você encontrará em software mais recente do que o listado abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um pc de desenvolvimento [compatível com Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headset imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](../../install-the-tools.md#installation-checklist)
- [O SDK Windows 10 mais recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Um [headset Windows Mixed Reality imersivo (VR)](../../../discover/immersive-headset-hardware-details.md) ou um Microsoft HoloLens [com](/hololens/hololens1-hardware) o modo desenvolvedor habilitado
- Acesso à Internet para instalação do Azure e para acessar Hubs de Notificação

## <a name="before-you-start"></a>Antes de começar

- Para evitar problemas ao criar este projeto, é fortemente sugerido que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas no tempo de build).
- Você deve ser o proprietário do portal do Desenvolvedor Microsoft e do Portal de Registro de Aplicativo, caso contrário, não terá permissão para acessar o aplicativo [no Capítulo 2.](#chapter-2---retrieve-your-new-apps-credentials)

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capítulo 1 – Criar um aplicativo no portal de Desenvolvedor Microsoft

Para usar o Serviço de Hubs de Notificação do **Azure,** você precisará criar um aplicativo no Portal do Desenvolvedor Microsoft, pois seu aplicativo precisará ser registrado para que ele possa enviar e receber notificações.

1.  Faça logoff no [portal Desenvolvedor Microsoft .](https://developer.microsoft.com/dashboard)

    > Você precisará fazer logoff em sua conta Microsoft.

2.  No Painel, clique **em Criar um novo aplicativo.**

    ![criar um aplicativo](images/AzureLabs-Lab8-01.png)

3.  Um pop-up será exibido, no qual você precisará reservar um nome para seu novo aplicativo. Na caixa de texto, insira um nome apropriado; se o nome escolhido estiver disponível, um tique será exibido à direita da caixa de texto. Depois de inserir um nome disponível, clique no botão Reservar nome **do** produto na parte inferior esquerda do pop-up.

    ![inverter um nome](images/AzureLabs-Lab8-02.png)

4.  Com o aplicativo criado agora, você está pronto para passar para o próximo Capítulo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capítulo 2 – Recuperar suas credenciais de novos aplicativos

Faça logoff no Portal de Registro de Aplicativo, onde seu novo aplicativo será listado e recupere as credenciais que serão usadas para configurar o Serviço **de Hubs** de Notificação no **Portal do Azure.**

1.  Navegue até o [Portal de Registro de Aplicativo.](https://apps.dev.microsoft.com)

    ![portal de registro de aplicativo](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Você precisará usar sua conta da Microsoft para fazer logon.  
    > Essa **deve** ser a Conta microsoft que você usou no Capítulo [anterior,](#chapter-1---create-an-application-on-the-microsoft-developer-portal)com o portal do desenvolvedor Windows Store.

2.  Você encontrará seu aplicativo na **seção Meus aplicativos.** Depois de encontrar, clique nele e você será levado para uma nova página que tem o nome do aplicativo mais **Registro**.

    ![seu aplicativo recém-registrado](images/AzureLabs-Lab8-04.png)

3.  Scroll down página de registro para encontrar a seção **Segredos do** Aplicativo e o SID **do Pacote** para seu aplicativo. Copie ambos para uso com a configuração do Serviço de Hubs de Notificação do **Azure** no próximo Capítulo.

    ![segredos do aplicativo](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capítulo 3 – Configurar o Portal do Azure: criar o Serviço de Hubs de Notificação

Com as credenciais dos aplicativos recuperadas, você precisará ir para o Portal do Azure, onde criará um Serviço de Hubs de Notificação do Azure.

1.  Faça logoff no [Portal do Azure.](https://portal.azure.com)

    > [!NOTE] 
    > Se você ainda não tiver uma conta do Azure, precisará criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ajuda ao instrutor ou a um dos proctors para configurar sua nova conta.

2.  Quando você está conectado,  clique em Novo no canto superior esquerdo, pesquise Hub de **Notificação** e clique em **_Inserir_**.

    ![pesquisar hub de notificação](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > A palavra ***New** _ pode ter sido substituída por _*Criar um recurso**, em portais mais novos.

3.  A nova página fornecerá uma descrição do serviço *hubs de* notificação. Na parte inferior esquerda deste prompt, selecione o **botão** Criar para criar uma associação com esse serviço.

    ![criar instância de hubs de notificação](images/AzureLabs-Lab8-07.png)

4.  Depois de clicar em ***Criar***:

    1.  Insira o nome desejado para essa instância de serviço.

    2.  Forneça um **namespace** que você poderá associar a este aplicativo.

    3.  Selecione um **Local.**

    4.  Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses laboratórios) em um grupo de recursos comum.

        > Se você quiser ler mais sobre os Grupos de Recursos do Azure, siga este link sobre como [gerenciar um Grupo de Recursos.](/azure/azure-resource-manager/resource-group-portal) 

    5.  Selecione uma Assinatura **apropriada.**

    6.  Você também precisará confirmar que entendeu os Termos e Condições aplicados a esse Serviço.

    7. Selecione **Criar**.

        ![detalhes do serviço de preenchimento](images/AzureLabs-Lab8-08.png)

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![notificação](images/AzureLabs-Lab8-09.png)

7.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância de serviço do **Hub de notificação** .

    ![ir para o recurso](images/AzureLabs-Lab8-10.png)
    
8.  Na página Visão geral, na metade inferior da página, clique em **Windows (WNS).** O painel à direita será alterado para mostrar dois campos de texto, que exigem o **SID do pacote** e a **chave de segurança** do aplicativo que você configurou anteriormente.

    ![serviço de hubs recém-criado](images/AzureLabs-Lab8-11.png)

9. Depois de copiar os detalhes nos campos corretos, clique em **salvar** e você receberá uma notificação quando o Hub de notificação tiver sido atualizado com êxito.

    ![Copiar detalhes de segurança](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capítulo 4-configurar o portal do Azure: criar serviço de tabela

depois de criar sua instância de serviço de Hubs de notificação, navegue de volta para o Portal do azure, onde você criará um serviço de tabelas do azure criando um recurso de Armazenamento.

1.  Se ainda não estiver conectado, faça logon no [portal do Azure](https://portal.azure.com).

2.  depois de conectado, clique em **novo** no canto superior esquerdo e procure **Armazenamento conta** e clique em **Enter**.

    > [!NOTE] 
    > A palavra ***New** _ pode ter sido substituída por _ * Create a Resource * *, em portais mais recentes.

3.  selecione **Armazenamento conta-blob, arquivo, tabela, fila** na lista.

    ![Pesquisar conta de armazenamento](images/AzureLabs-Lab8-13.png)

4.  a nova página fornecerá uma descrição do serviço de **conta do Armazenamento** . Na parte inferior esquerda deste prompt, selecione o botão **criar** para criar uma instância desse serviço.

    ![criar instância de armazenamento](images/AzureLabs-Lab8-14.png)

5.  Depois de clicar em **criar**, um painel será exibido:

    1. Insira o **nome** desejado para esta instância de serviço (deve estar em letras minúsculas).

    2. Para **modelo de implantação**, clique em **Gerenciador de recursos**.

    3.  para **tipo de conta**, usando o menu suspenso, selecione **Armazenamento (uso geral v1)**.

    4. Selecione um **local** apropriado.
    
    5.  Para o menu suspenso **replicação** , selecione **armazenamento com redundância geográfica e acesso de leitura (ra-grs)**.

    6.  Para **desempenho**, clique em **padrão**.

    7.  Na seção **transferência segura necessária** , selecione **desabilitado**.

    8.  No menu suspenso **assinatura** , selecione uma assinatura apropriada.

    9.  Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    10. Deixe as **redes virtuais** como **desabilitadas** se essa for uma opção para você.

    11. Clique em **Criar**.

        ![preencher detalhes do armazenamento](images/AzureLabs-Lab8-15.png)

6.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal assim que a instância do serviço for criada. Clique nas notificações para explorar sua nova instância de serviço.

    ![Nova notificação de armazenamento](images/AzureLabs-Lab8-16.png)

8.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. você será levado à sua nova página de visão geral da instância do serviço Armazenamento.

    ![ir para o recurso](images/AzureLabs-Lab8-17.PNG)

9. Na página Visão geral, no lado direito, clique em **tabelas**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. O painel à direita será alterado para mostrar as informações do **serviço tabela** , onde você precisa adicionar uma nova tabela. Para fazer isso, clique no **+** botão **tabela** no canto superior esquerdo.

    ![Abrir tabelas](images/AzureLabs-Lab8-19.png)

11. Uma nova página será mostrada, onde você precisa inserir um nome de **tabela**. Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos posteriores. Insira um nome apropriado e clique em **OK**.

    ![criar nova tabela](images/AzureLabs-Lab8-20.png)    

12. Depois que a nova tabela tiver sido criada, você poderá vê-la na página de **serviço tabela** (na parte inferior).

    ![nova tabela criada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capítulo 5-concluindo a tabela do Azure no Visual Studio

Agora que a conta de armazenamento do **serviço de tabela** foi configurada, é hora de adicionar dados a ela, que será usada para armazenar e recuperar informações. A edição das tabelas pode ser feita por meio de **Visual Studio**.

1.  Abra o **Visual Studio**.

2.  No menu, clique em **Exibir**  >  **Cloud Explorer**.

    ![abrir o Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).

    > [!NOTE] 
    > se a assinatura usada para criar suas *contas de Armazenamento* não estiver visível, verifique se você tem: 
    > - Conectado à mesma conta que você usou para o portal do Azure.
    > - Selecione sua assinatura na página de gerenciamento de conta (talvez seja necessário aplicar um filtro de suas configurações de conta):  
    >
    >   ![Localizar assinatura](images/AzureLabs-Lab8-22-5.png)

4.  Os serviços de nuvem do Azure serão mostrados. localize **Armazenamento contas** e clique na seta à esquerda dela para expandir suas contas.

    ![abrir contas de armazenamento](images/AzureLabs-Lab8-23.png)

5.  uma vez expandido, sua **conta de Armazenamento** recém-criada deve estar disponível. Clique na seta à esquerda do armazenamento e, depois de expandida, localize as **tabelas** e clique na seta ao lado dela para revelar a **tabela** que você criou no último capítulo. Clique duas vezes em sua **tabela**.

    ![Abrir tabela de objetos de cena](images/AzureLabs-Lab8-24.png)

6.  sua tabela será aberta no centro da janela de Visual Studio. Clique no ícone de tabela com o **+** (mais) nele.

    ![Adicionar nova tabela](images/AzureLabs-Lab8-25.png)

7.  Uma janela será exibida solicitando que você *adicione a entidade*. Você criará três entidades no total, cada uma com várias propriedades. Você observará que *PartitionKey* e *RowKey* já foram fornecidos, pois eles são usados pela tabela para localizar seus dados. 

    ![partição e chave de linha](images/AzureLabs-Lab8-26.png)

8. Atualize o *valor* de **PartitionKey** e **RowKey** da seguinte maneira (Lembre-se de fazer isso para cada propriedade de linha que você adicionar, ao mesmo tempo em que incrementa o RowKey a cada vez):

    ![Adicionar valores corretos](images/AzureLabs-Lab8-26-5.png)

9.  Clique em **Adicionar Propriedade** para adicionar linhas extras de dados. Faça sua primeira tabela vazia corresponder à tabela abaixo.

10. Clique em **OK** quando terminar.

    ![clique em OK quando terminar](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Verifique se você alterou o **tipo** das entradas **X**, **Y** e **Z** para **Double**. 

11. Você notará que a tabela agora tem uma linha de dados. Clique no **+** ícone (mais) novamente para adicionar outra entidade.

    ![primeira linha](images/AzureLabs-Lab8-27-5.png)

12. Crie uma propriedade adicional e, em seguida, defina os valores da nova entidade para que correspondam às mostradas abaixo.

    ![Adicionar cubo](images/AzureLabs-Lab8-28.png)

13. Repita a última etapa para adicionar outra entidade. Defina os valores dessa entidade como os mostrados abaixo.

    ![Adicionar cilindro](images/AzureLabs-Lab8-29.png)

14. Agora, sua tabela deve ser parecida com a seguinte.

    ![tabela concluída](images/AzureLabs-Lab8-30.png)

15. Você concluiu este capítulo. Certifique-se de salvar.

## <a name="chapter-6---create-an-azure-function-app"></a>Capítulo 6 – Criar um aplicativo de funções do Azure

Crie um Aplicativo de Funções do Azure, que  será chamado pelo aplicativo desktop para atualizar o serviço Tabela e enviar uma notificação por meio do **Hub de Notificação.**

Primeiro, você precisa criar um arquivo que permitirá que a função do Azure carregue as bibliotecas de que precisa.

1.  Abra **Bloco de notas** (pressione Windows Tecla e digite bloco de notas).

    ![abrir bloco de notas](images/AzureLabs-Lab8-31.png)

2.  Com Bloco de notas aberta, insira a estrutura JSON abaixo dela. Depois de fazer isso, salve-o na área de trabalho **comoproject.jsem**. É importante que a nomeação seja correta: verifique se ela **NÃO tem uma extensão .txt** arquivo. Esse arquivo define as bibliotecas que sua função usará, se você tiver usado NuGet ela será familiar.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Faça logoff no [Portal do Azure.](https://portal.azure.com)

4.  Quando você está conectado, clique em **Novo** no canto superior esquerdo e pesquise **Por** Aplicativo de Funções, pressione **Enter**.

    ![pesquisar aplicativo de funções](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > A palavra **Novo** pode ter sido substituída por **Criar um recurso**, em portais mais novos.

5.  A nova página fornecerá uma descrição do serviço **aplicativo de** funções. Na parte inferior esquerda deste prompt, selecione o **botão** Criar para criar uma associação com esse serviço.

    ![instância do aplicativo de funções](images/AzureLabs-Lab8-33.png)

6.  Depois de clicar em **Criar**, preencha o seguinte:

    1. Em **Nome do aplicativo,** insira o nome desejado para essa instância de serviço.

    2. Selecione uma **Assinatura**.

    3. Selecione o tipo de preço apropriado para você, se esta for **a** primeira vez que você cria um Serviço de Aplicativo de Funções, uma camada gratuita deve estar disponível para você.

    4. Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses laboratórios) em um grupo de recursos comum.

        > Se você quiser ler mais sobre os Grupos de Recursos do Azure, siga este link sobre como [gerenciar um Grupo de Recursos.](/azure/azure-resource-manager/resource-group-portal)

    5. Para **SO,** clique Windows, pois essa é a plataforma pretendido.

    6. Selecione um **Plano de Hospedagem** (este tutorial está usando um **Plano de Consumo.**

    7. Selecione um **Local** **(escolha o mesmo local que o armazenamento criado na etapa anterior)**

    8. Para a **Armazenamento,** você deve selecionar o Armazenamento **serviço criado na etapa anterior.**

    9. Você não precisará do *Application Insights* neste aplicativo, portanto, sinta-se à vontade para deixá-lo **desligado.**

    10. Clique em **Criar**.

        ![criar nova instância](images/AzureLabs-Lab8-34.png)

7.  Depois de clicar em **Criar,** você terá que aguardar até que o serviço seja criado, isso pode levar um minuto.

8.  Uma notificação será exibida no portal depois que a instância de serviço for criada.

    ![nova notificação](images/AzureLabs-Lab8-35.png)

9.  Clique nas notificações para explorar sua nova instância de serviço.

10. Clique no **botão Ir para o** recurso na notificação para explorar sua nova instância de serviço. 

    ![ir para o recurso](images/AzureLabs-Lab8-36.png)

11. Clique no **+** ícone (mais) ao lado *de Funções*, para *Criar novo*.

    ![adicionar nova função](images/AzureLabs-Lab8-37.png)

12. No painel central, a **janela Criação** de função será exibida. Ignore as informações na metade superior do painel e clique em **Função personalizada**, que está localizada próxima à parte inferior (na área azul, conforme abaixo).

    ![função personalizada](images/AzureLabs-Lab8-38.png)

13. A nova página dentro da janela mostrará vários tipos de função. Scroll down exibir os tipos roxos e clique no **elemento HTTP PUT.**

    ![http put link](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Talvez seja preciso rolar mais para baixo na página (e essa imagem pode não ser exatamente a mesma, se as atualizações do Portal do Azure foram realizadas), no entanto, você está procurando um elemento chamado *HTTP PUT.*

14. A **janela HTTP PUT** será exibida, na qual você precisará configurar a função (veja abaixo a imagem).

    1.  Para **Idioma,** usando o menu suspenso, selecione \# C.

    2.  Em **Nome,** insinte um nome apropriado.

    3.  No menu **suspenso Nível** de autenticação, selecione **Função**.

    4.  Para a **seção Nome da** tabela, você precisa usar o nome exato usado para criar o serviço **Tabela** anteriormente (incluindo o mesmo caso de letra).

    5.  Na seção **Armazenamento da conta,** use o menu suspenso e selecione sua conta de armazenamento a partir daí. Se ele não estiver  lá, clique no hiperlink Novo junto com o título da seção para mostrar outro painel, em que sua conta de armazenamento deve ser listada.

        ![novo armazenamento](images/AzureLabs-Lab8-40.png)

15. Clique **em** Criar e você receberá uma notificação de que suas configurações foram atualizadas com êxito.

    ![função create](images/AzureLabs-Lab8-41.png)

16. Depois de clicar **em Criar**, você será redirecionado para o editor de funções.

    ![atualizar código de função](images/AzureLabs-Lab8-42.png)

17. Insira o seguinte código no editor de funções (substituindo o código na função ):

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > Usando as bibliotecas incluídas, a função recebe o nome e o local do objeto que foi movido na cena do Unity (como um objeto C#, chamado **UnityGameObject**). Esse objeto é usado para atualizar os parâmetros de objeto dentro da tabela criada. Depois disso, a função faz uma chamada para o serviço do Hub de Notificação criado, que notifica todos os aplicativos inscritos.

18. Com o código em uso, clique em **Salvar**.

19. Em seguida, clique **\<** no ícone (seta) no lado direito da página.

    ![abrir o painel de upload](images/AzureLabs-Lab8-43.png)

20. Um painel deslizará da direita. Nesse painel, clique em **Upload** e um Navegador de Arquivos será exibido.

21. Navegue até o arquivo **project.js,** que você criou  no Bloco de notas anteriormente e clique no **botão** Abrir. Esse arquivo define as bibliotecas que sua função usará.

    ![carregar json](images/AzureLabs-Lab8-44.png)

22. Quando o arquivo for carregado, ele aparecerá no painel à direita. Clicar nele o abrirá no editor **de** funções. Ele deve **ter exatamente** a mesma aparência da próxima imagem (abaixo da etapa 23).

23. Em seguida, no painel à esquerda, abaixo **de Funções**, clique no link **Integrar.**

    ![função integrate](images/AzureLabs-Lab8-45.png)

24. Na próxima página, no canto superior direito, clique em **Editor avançado** (conforme abaixo).

    ![abrir editor avançado](images/AzureLabs-Lab8-46.png)

25. Um **function.jsno** arquivo será aberto no painel central, que precisa ser substituído pelo snippet de código a seguir. Isso define a função que você está criando e os parâmetros passados para a função.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. Seu editor agora deve ser parecido com a imagem abaixo:

    ![voltar para o editor padrão](images/AzureLabs-Lab8-47.png)

27. Você pode observar que os parâmetros de entrada que você acabou de inserir podem não corresponder aos detalhes da tabela e do armazenamento e, portanto, precisarão ser atualizados com suas informações. **Não faça isso aqui,** pois ele será abordado em seguida. Basta clicar no link **Editor** padrão, no canto superior direito da página, para voltar.

28. De volta ao **editor Standard**, clique em Tabela **do Azure Armazenamento (tabela)**, em **Entradas**. 
    
    ![Entradas de tabela](images/AzureLabs-Lab8-47-5.png)

29. Verifique se a seguinte combinação **às suas** informações, pois elas podem ser diferentes (há uma imagem abaixo das seguintes etapas):

    1.  **Nome da** tabela: o nome da tabela que você criou em seu serviço Armazenamento Azure, Tabelas.

    2.  **Armazenamento de conta:** clique em novo **,** que aparece junto com o menu suspenso e um painel será exibido à direita da janela.

        ![novo armazenamento](images/AzureLabs-Lab8-48.png)

        1.  Selecione sua **Armazenamento ,** que você criou anteriormente para hospedar os **Aplicativos de Funções.**

        2. Você observará que o valor **Armazenamento de** conexão da conta foi criado.

        3. Pressione Salvar **quando** terminar.

    3.  A **página Entradas** agora deve corresponder ao mostrado abaixo, mostrando **suas** informações.

        ![entradas concluídas](images/AzureLabs-Lab8-49.png)

30. Em seguida, clique **em Hub de Notificação do Azure (notificação)** – em **Saídas.** Verifique se as seguintes informações são corresponderem às **suas** informações, pois elas podem ser diferentes (há uma imagem abaixo das seguintes etapas):

    1.  **Nome do Hub de** Notificação: esse é o nome da instância de serviço **do Hub** de Notificação que você criou anteriormente.

    2.  **Conexão de namespace dos Hubs de** Notificação: clique **em novo**, que aparece junto com o menu suspenso.

        ![verificar saídas](images/AzureLabs-Lab8-50.png)

    3. O  pop-up Conexão será exibido (veja a imagem abaixo), em que você precisa selecionar o **Namespace** do Hub de **Notificação**, que você definiu anteriormente.

    4. Selecione o **nome do Hub** de Notificação no menu suspenso do meio.

    5.  Defina **o** menu suspenso Política **como DefaultFullSharedAccessSignature**.

    6. Clique no **botão Selecionar** para voltar.

        ![atualização de saída](images/AzureLabs-Lab8-51.png)

31.  A **página Saídas** agora deve corresponder ao abaixo, mas com **suas** informações. Pressione **Salvar**.

> [!WARNING]
> *Não edite o nome do Hub* de Notificação diretamente (tudo isso deve ser feito usando o **Editor Avançado**, desde que você seguiu as etapas anteriores corretamente.

![saídas concluídas](images/AzureLabs-Lab8-50.png)

32. Neste ponto, você deve testar a função para garantir que ela está funcionando. Para fazer isso: 

    1. Navegue até a página de funções mais uma vez:

        ![saídas concluídas](images/AzureLabs-Lab8-50-1.png)

    2. De volta à página de funções, clique **na guia** Teste no lado direito da página para abrir a *folha* Teste:

        ![saídas concluídas](images/AzureLabs-Lab8-50-2.png)

    3. Na caixa **de texto** Corpo da solicitação da folha, colar o código abaixo:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Com o código de teste em prática, clique **no botão** Executar na parte inferior direita e o teste será executado. Os logs de saída do teste serão exibidos na área do console, abaixo do código da função.

        ![saídas concluídas](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Se o teste acima falhar, você precisará verificar se seguiu as etapas acima exatamente, especialmente as configurações no **painel de integração**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capítulo 7 – Configurar o Unity da Área de Trabalho Project

> [!IMPORTANT]
> O aplicativo desktop que você está criando agora **não funcionará** no Editor do Unity. Ele precisa ser executado fora do Editor, seguindo o Building do aplicativo, usando Visual Studio (ou o aplicativo implantado). 

A seguir está uma configuração típica para o desenvolvimento com o Unity e a realidade misturada e, como tal, é um bom modelo para outros projetos.

Configurar e testar seu headset imersivo de realidade misturada.

> [!NOTE] 
> Você não **exigirá** Controladores de Movimento para este curso. Se você precisar de suporte para configurar o headset imersivo, siga este link sobre como [configurar o Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra **o Unity** e clique em **Novo.**

    ![novo projeto do Unity](images/AzureLabs-Lab8-52.png)

2.  Você precisa fornecer um nome de Project Unity, insira **UnityDesktopNotifHub**. Certifique-se de que o tipo de projeto está definido **como 3D.** De definir **o Local** como em algum lugar apropriado para você (lembre-se de que mais próximo dos diretórios raiz é melhor). Em seguida, clique **em Criar projeto**.

    ![criar projeto](images/AzureLabs-Lab8-53.png)

3.  Com o Unity aberto, vale a pena verificar se o **Editor de Script** padrão está definido como **Visual Studio**. Vá para **Editar**  >  **Preferências** e, em seguida, na nova janela, navegue até **Ferramentas Externas.** Altere **Editor de Script** Externo para Visual Studio **2017.** Feche a **janela Preferências.**

    ![definir ferramentas externas do VS](images/AzureLabs-Lab8-54.png)

4.  Em seguida, **vá** para Criar arquivo Configurações e selecione Plataforma universal Windows e clique no botão Alternar  >   **Plataforma** para aplicar sua seleção.

    ![plataformas switch](images/AzureLabs-Lab8-55.png)

5.  Ainda em Build **de**  >  **Arquivo Configurações**, certifique-se de que:

    1.  **O Dispositivo de** Destino está definido **como Qualquer Dispositivo**

        > Esse aplicativo será para sua área de trabalho, portanto, deve ser **Qualquer Dispositivo**

    2.  **O tipo de** build é definido como **D3D**

    3.  **O SDK** está definido como **Mais recente instalado**

    4.  **Visual Studio versão é** definida como **Mais recente instalada**

    5.  **Build e Executar** são definidos como **Computador Local**

    6.  Enquanto estiver aqui, vale a pena salvar a cena e adiá-la ao build.

        1. Faça isso selecionando **Adicionar Cenas Abertas.** Uma janela salvar será exibida.

            ![adicionar cenas abertas](images/AzureLabs-Lab8-56.png)

        2. Crie uma nova pasta para essa cena e,  em qualquer futuro, selecione o botão Nova pasta, para criar uma nova pasta, nomeá-la **Cenas**.

            ![pasta new scenes](images/AzureLabs-Lab8-57.png)

        3. Abra a pasta **Cenas** recém-criada e, em seguida, no campo Nome do **arquivo:** texto, digite Cena da Área de Trabalho **NH \_ \_** e pressione **Salvar**.

            ![novos NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  As configurações restantes, em **Build Configurações**, devem ser deixadas como padrão por enquanto.

6.  Na mesma janela, clique no botão **Player Configurações,** isso abrirá o painel relacionado no espaço em que o **Inspetor** está localizado.

7.  Neste painel, algumas configurações precisam ser verificadas:

    1.  Na guia **Outros Configurações:**

        1.  **A versão do Runtime de Script** deve **ser Experimental (equivalente ao .NET 4.6)**

        2. **Back-end de script** deve ser **.NET**

        3. **O nível de compatibilidade da API** deve ser **.NET 4.6**

            ![Versão 4.6 net](images/AzureLabs-Lab8-59.png)

    2.  Na guia **Publicação Configurações,** em **Funcionalidades,** verifique:

        - **InternetClient**

            ![tique cliente da Internet](images/AzureLabs-Lab8-60.png)

8.  De volta **ao Build Configurações** projetos C *\# do Unity* não estão mais es cinzas; marque a caixa de seleção ao lado disso.

9.  Feche a janela **Configurações de Build**.

10. Salve sua cena e Project **arquivo**  >  **salvar cena/arquivo** salvar  >  **Project**.

    > [!IMPORTANT]
    > Se você quiser ignorar o componente Configurar o *Unity* para este projeto (Aplicativo da Área de Trabalho) e continuar [](https://docs.unity3d.com/Manual/AssetPackages.html)diretamente no código, sinta-se à vontade para baixar esse [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importá-lo para seu projeto como um Pacote Personalizado e, em seguida, continuar do [Capítulo 9.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)  Você ainda precisará adicionar os componentes de script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capítulo 8 – Importando as DLLs no Unity

Você estará usando o Azure Armazenamento para Unity (que aproveita o SDK do .Net para Azure). Para obter mais informações, siga [este link sobre o Azure Armazenamento para Unity.](/sandbox/gamedev/unity/azure-storage-unity)

Atualmente, há um problema conhecido no Unity que exige que os plug-ins sejam reconfigurados após a importação. Essas etapas (4 a 7 nesta seção) não serão mais necessárias depois que o bug for resolvido.

Para importar o SDK para seu próprio projeto, certifique-se de ter baixado o [**.unitypackage**](https://aka.ms/azstorage-unitysdk) mais recente do GitHub. Em seguida, faça o seguinte:

1.  Adicione o **.unitypackage** ao Unity usando a opção de menu Pacote **\> Personalizado \>** do Pacote de Importação de Ativos.

2.  Na caixa **Importar Pacote do Unity** que aparece, você pode selecionar tudo em **_Plug-in_ \> *Armazenamento***.  Desmarque todo o resto, pois ele não é necessário para este curso.

    ![importar para o pacote](images/AzureLabs-Lab8-61.png)

3.  Clique no ***botão Importar*** para adicionar os itens ao seu projeto.

4.  Acesse a pasta **Armazenamento** em **Plug-ins** na exibição Project e selecione os seguintes plug-ins *somente:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![desmarque Qualquer plataforma](images/AzureLabs-Lab8-62.png)

5.  Com *esses plug-ins específicos selecionados,* desmarque Qualquer  **Plataforma** e **desmarque WSAPlayer** e clique em **Aplicar**. 

    ![aplicar dlls de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Estamos marcando esses plug-ins específicos para serem usados apenas no Editor do Unity. Isso porque há versões diferentes dos mesmos plug-ins na pasta WSA que serão usadas depois que o projeto for exportado do Unity.

6.  Na pasta **Armazenamento** plug-in, selecione apenas:

    -   Microsoft.Data.Services.Client

        ![set não processa para dlls](images/AzureLabs-Lab8-64.png)

7.  Marque a **caixa Não Processar em** Plataforma Configurações clique em **_Aplicar_**. 

    ![aplicar nenhum processamento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Estamos marcando este plug-in "não processar", porque o assembly do Unity Patcher tem dificuldade para processar esse plug-in. O plug-in ainda funcionará, embora não seja processado.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capítulo 9-criar a classe TableToScene no projeto de desktop Unity

Agora você precisa criar os scripts que contêm o código para executar este aplicativo.

O primeiro script que você precisa criar é **TableToScene**, que é responsável por:

-   Lendo entidades na tabela do Azure.
-   Usando os dados da tabela, determine quais objetos gerar e em qual posição.

O segundo script que você precisa criar é **CloudScene**, que é responsável por:

-   Registrando o evento de clique com o botão esquerdo, para permitir que o usuário arraste objetos em volta da cena.
-   Serializar os dados de objeto desta cena do Unity e enviá-los para o Aplicativo de funções do Azure.

Para criar esta classe:

1.  clique com o botão direito do mouse na pasta de **ativos** localizada no painel de Project, **crie** a  >  **pasta**. Nomeie a pasta **scripts**.

    ![criar pasta de scripts](images/AzureLabs-Lab8-66.png)

    ![criar a pasta de scripts 2](images/AzureLabs-Lab8-67.png)

2.  Clique duas vezes na pasta recém-criada para abri-la.

3.  Clique com o botão direito do mouse na pasta **scripts** e clique em **criar**  >  **script C#**. Nomeie o script **TableToScene**.

    ![novo script c# ](images/AzureLabs-Lab8-68.png)
     ![ TableToScene renomear](images/AzureLabs-Lab8-69.png)

4.  clique duas vezes no script para abri-lo no Visual Studio 2017.

5.  Adicione os seguintes namespaces:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  Dentro da classe, insira as seguintes variáveis:

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > substitua o valor **accountName** pelo nome do serviço de Armazenamento do azure e pelo valor de **accountKey** pelo valor de chave encontrado no serviço de Armazenamento do azure, no Portal do azure (consulte a imagem abaixo). 
    >
    > ![buscar chave de conta](images/AzureLabs-Lab8-70.png)

7.  Agora, adicione os métodos **Start ()** e **ativo ()** para inicializar a classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  Dentro da classe **TableToScene** , adicione o método que recuperará os valores da tabela do Azure e use-os para gerar os primitivos apropriados na cena.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  Fora da classe **TableToScene** , você precisa definir a classe usada pelo aplicativo para serializar e desserializar as **entidades de tabela**.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Certifique-se de **salvar** antes de voltar para o editor do Unity.

11. Clique na **câmera principal** do painel **hierarquia** , para que suas propriedades apareçam no **Inspetor**.

12. Com a pasta **scripts** aberta, selecione o **arquivo script TableToScene** e arraste-o para a **câmera principal**. O resultado deve ser o seguinte:

    ![Adicionar script à câmera principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capítulo 10 – criar a classe CloudScene no desktop Unity Project

O segundo script que você precisa criar é **CloudScene**, que é responsável por:

-   Registrando o evento de clique com o botão esquerdo, para permitir que o usuário arraste objetos em volta da cena.

-   Serializar os dados de objeto desta cena do Unity e enviá-los para o Aplicativo de funções do Azure.

Para criar o segundo script:

1.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar**, **\# script C**. Nomeie o script **CloudScene**
    
    ![novo script c# ](images/AzureLabs-Lab8-72.png)
     ![ renomear CloudScene](images/AzureLabs-Lab8-73.png)

2.  Adicione os seguintes namespaces:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Insira as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Substitua o valor **azureFunctionEndpoint** pela URL de aplicativo de funções do Azure encontrada no serviço de aplicativo de funções do Azure, no portal do Azure, conforme mostrado na imagem abaixo:

    ![obter URL da função](images/AzureLabs-Lab8-74.png)

5.  Agora, adicione os métodos **Start ()** e **ativo ()** para inicializar a classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  Dentro do método **Update ()** , adicione o seguinte código que irá detectar a entrada do mouse e arrastar, que, por sua vez, moverá Gameobjects na cena. Se o usuário tiver arrastado e descartado um objeto, ele passará o nome e as coordenadas do objeto para o método **UpdateCloudScene ()**, que chamará o serviço de aplicativo de funções do Azure, que atualizará a tabela do Azure e disparará a notificação.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  Agora, adicione o método **UpdateCloudScene ()** , como abaixo:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Salve o código e retorne ao Unity

9.  Arraste o script **CloudScene** para a **câmera principal**. 

    1. Clique na **câmera principal** do painel **hierarquia** , para que suas propriedades apareçam no **Inspetor**. 

    2. Com a pasta **scripts** aberta, selecione o script **CloudScene** e arraste-o para a **câmera principal**. O resultado deve ser o seguinte:

        > ![Arraste o script de nuvem para a câmera principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>capítulo 11-criar o Project de área de trabalho para UWP

Tudo o que é necessário para a seção do Unity deste projeto foi concluído.

1.  navegue até **criar Configurações** (  >  **Configurações de compilação** de arquivo).

2.  na janela **build Configurações** , clique em **compilar**.

    ![Compilar projeto](images/AzureLabs-Lab8-76.png)

3.  Uma janela do **Explorador de arquivos** será Popup, solicitando um local para compilar. Crie uma nova pasta (clicando em **nova pasta** no canto superior esquerdo) e nomeie-a como **Build**.

    ![nova pasta para compilação](images/AzureLabs-Lab8-77.png)

    1.  Abra a nova pasta **Builds** e crie outra pasta (usando a **nova pasta** mais uma vez) e nomeie-a **NH \_ Desktop \_ app**.

        ![nome da pasta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Com o **\_ \_ aplicativo de área de trabalho NH** selecionado. clique em **Selecionar pasta**. O projeto levará um minuto ou mais para ser compilado.

4.  Após a compilação, o **Explorador de arquivos** aparecerá mostrando o local do novo projeto. No entanto, não é necessário abri-lo, pois você precisa criar o outro projeto do Unity primeiro, nos próximos capítulos.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capítulo 12-configurar Project do Unity de realidade misturada

A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o **Unity** e clique em **novo**.

    ![novo projeto do Unity](images/AzureLabs-Lab8-79.png)

2.  agora, você precisará fornecer um nome de Project do Unity, inserir **UnityMRNotifHub**. Verifique se o tipo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar**  >  **preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**. altere o **Editor de Script externo** para **Visual Studio 2017**. Feche a janela **preferências** .

    ![definir editor externo como VS](images/AzureLabs-Lab8-81.png)

4.  em seguida, vá para Build de **arquivo**  >  **Configurações** e alterne a plataforma para **Plataforma Universal do Windows** clicando no botão **alternar plataforma** .

    ![alternar plataformas para UWP](images/AzureLabs-Lab8-82.png)

5.  vá para o **arquivo**  >  **Build Configurações** e verifique se:

    1.  O **dispositivo de destino** está definido para **qualquer dispositivo**

        > para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.

    2.  O **tipo de compilação** está definido como **D3D**

    3.  O **SDK** está definido para o **mais recente instalado**

    4.  **Visual Studio versão** está definida para o **mais recente instalado**

    5.  **Compilar e executar** é definido como **computador local**

    6.  Enquanto isso, vale a pena salvar a cena e adicioná-la à compilação.

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-83.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![nova pasta de cenas](images/AzureLabs-Lab8-84.png)

        3. Abra sua pasta de **cenas** recém-criada e, em seguida, no campo **nome do arquivo:** texto, digite **NH \_ Mr \_ Scene** e pressione **salvar**.

            ![nova cena-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  As configurações restantes, em **Build Configurações**, devem ser deixadas como padrão por enquanto.

6.  Na mesma janela, clique no botão **Player Configurações,** isso abrirá o painel relacionado no espaço em que o **Inspetor** está localizado.    

    ![abrir configurações do player](images/AzureLabs-Lab8-86.png)

7.  Neste painel, algumas configurações precisam ser verificadas:

    1.  Na guia **Outros Configurações:**

        1.  **A versão do Runtime de Script** deve **ser Experimental** (equivalente ao .NET 4.6)
        2.  **Back-end de script** deve ser **_.NET_**
        3.  **O nível de compatibilidade da API** deve ser **.NET 4.6**

            ![compatibilidade de api](images/AzureLabs-Lab8-87.png)

    2.  Mais para baixo no painel, no **XR Configurações** (encontrado abaixo de **Publicar Configurações**), marque Realidade **Virtual** Com Suporte , certifique-se de que o **SDK** Windows Mixed Reality foi adicionado

        ![atualizar configurações de xr](images/AzureLabs-Lab8-88.png)        

    3.  Na guia **Publicação Configurações,** em **Funcionalidades,** em :

        - **InternetClient**           

            ![tique cliente da Internet](images/AzureLabs-Lab8-89.png)

8.  De volta **ao Build Configurações**, os projetos **C#** do Unity não estão mais es cinzas: marque a caixa de seleção ao lado disso.

9.  Com essas alterações feitas, feche a janela Configurações Build.

10. Salve sua cena e Project **arquivo**  >  **salvar cena/arquivo** salvar  >  **Project**.

    > [!IMPORTANT]
    > Se você quiser ignorar o componente Configurar o *Unity* para este projeto (aplicativo de realidade misturada) e continuar diretamente [](https://docs.unity3d.com/Manual/AssetPackages.html)no código, sinta-se à vontade para baixar esse [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importá-lo para seu projeto como um Pacote Personalizado e, em seguida, continuar do [Capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Você ainda precisará adicionar os componentes de script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capítulo 13 – Importando as DLLs no Project

Você usará o Azure Armazenamento para a biblioteca do Unity (que usa o SDK do .Net para o Azure). Siga este [link sobre como usar o Azure Armazenamento com o Unity.](/sandbox/gamedev/unity/azure-storage-unity)
Atualmente, há um problema conhecido no Unity que exige que os plug-ins sejam reconfigurados após a importação. Essas etapas (4 a 7 nesta seção) não serão mais necessárias depois que o bug for resolvido.

Para importar o SDK para seu próprio projeto, certifique-se de ter baixado o [.unitypackage mais recente.](https://aka.ms/azstorage-unitysdk) Em seguida, faça o seguinte:

1.  Adicione o .unitypackage que você baixou do acima ao Unity usando a opção de menu Importar Pacote Personalizado do Pacote de  >    >   Importação de Ativos.

2.  Na caixa **Importar Pacote do Unity** que aparece, você pode selecionar tudo em **Plug-in**  >  **Armazenamento**.

    ![importar pacote](images/AzureLabs-Lab8-90.png)

3.  Clique no **botão Importar** para adicionar os itens ao seu projeto.

4.  Acesse a pasta **Armazenamento** em **Plug-ins** na exibição Project e selecione os seguintes plug-ins *somente:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![selecionar plug-ins](images/AzureLabs-Lab8-91.png)

5.  Com *esses plug-ins específicos selecionados,* desmarque Qualquer  **Plataforma** e **desmarque WSAPlayer** e clique em **Aplicar**. 

    ![aplicar alterações na plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Você está marcando esses plug-ins específicos para serem usados apenas no Editor do Unity. Isso porque há versões diferentes dos mesmos plug-ins na pasta WSA que serão usadas depois que o projeto for exportado do Unity.

6.  Na pasta **Armazenamento** plug-in, selecione apenas:

    -   Microsoft.Data.Services.Client

        ![selecionar cliente de serviços de dados](images/AzureLabs-Lab8-93.png)

7.  Marque a **caixa Não Processar em** Plataforma Configurações clique em **Aplicar**. 

    ![não process](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Você está marcando esse plug-in "Não processar" porque o patchr de assembly do Unity tem dificuldade para processar esse plug-in. O plug-in ainda funcionará mesmo que ele não seja processado.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capítulo 14 – Criando a classe TableToScene no projeto do Unity de realidade misturada

A **classe TableToScene** é idêntica à explicada no [Capítulo 9.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project) Crie a mesma classe no unity de realidade misturada Project o mesmo procedimento explicado no [Capítulo 9.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)

Depois de concluir este Capítulo, ambos os projetos **do Unity** terão essa classe configurada na Câmera Principal.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capítulo 15 – Criando a classe NotificationReceiver no Project

O segundo script que você precisa criar é **NotificationReceiver,** que é responsável por:

-   Registrar o aplicativo com o Hub de Notificação na inicialização.
-   Escutando notificações provenientes do Hub de Notificação.
-   Desselizando os dados do objeto de notificações recebidas.
-   Mova os GameObjects na cena, com base nos dados desterlizados.

Para criar o script **NotificationReceiver:**

1.  Clique com o botão direito do mouse na **pasta Scripts,** clique **em Criar**, **Script \# C**. Nomeia o script **NotificationReceiver**.

    ![criar novo script c# ](images/AzureLabs-Lab8-95.png)
     ![ nomeá-lo NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Clique duas vezes no script para abri-lo.

3.  Adicione os seguintes namespaces:

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Insira as seguintes variáveis:

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Substitua o valor **hubName** pelo nome do serviço hub de notificação e o valor **hubListenEndpoint** pelo valor do ponto de extremidade encontrado na guia Políticas de Acesso, Serviço do Hub de Notificação do Azure, no Portal do Azure (veja a imagem abaixo).

    ![inserir ponto de extremidade de política de hubs de notificação](images/AzureLabs-Lab8-97.png)

6.  Agora, adicione **os métodos Start()** **e Awake()** para inicializar a classe .

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Adicione o **método WaitForNotification** para permitir que o aplicativo receba notificações da Biblioteca do Hub de Notificação sem entrar em conflito com o Thread Principal:

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  O método a seguir, **InitNotificationAsync(),** registrará o aplicativo com o Serviço hub de notificação na inicialização. O código é comentado, pois o Unity não poderá Criar o projeto. Você removerá os comentários ao importar o pacote Nuget do Sistema de Mensagens do Azure Visual Studio.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  O manipulador a seguir, **Channel \_ PushNotificationReceived(),** será disparado sempre que uma notificação for recebida. Ele desselizará a notificação, que será a Entidade de Tabela do Azure que foi movida no Aplicativo da Área de Trabalho e, em seguida, move o GameObject correspondente na cena do MR para a mesma posição. 
    
    > [!IMPORTANT]
    > O código é comentado porque o código faz referência à biblioteca de Mensagens do Azure, que você adicionará depois de criar o projeto do Unity usando o nuget Gerenciador de Pacotes, dentro Visual Studio. Assim, o projeto do Unity não poderá ser build, a menos que seja comentado. Esteja ciente de que, se você criar seu projeto e, em seguida, desejar retornar ao Unity, precisará **comentar** esse código de novo.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Lembre-se de salvar suas alterações antes de voltar para o Editor do Unity.

11. Clique na **Câmera Principal** no painel **Hierarquia** para que suas propriedades apareçam no **Inspetor**.

12. Com a **pasta Scripts** aberta, selecione o script **NotificationReceiver** e arraste-o para a **Câmera Principal.** O resultado deve ser o mesmo abaixo:

    ![arrastar o script do receptor de notificação para a câmera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Se você estiver desenvolvendo isso para o Microsoft HoloLens, será necessário  atualizar o componente Câmera principal da Câmera, para que:
    > - Limpar sinalizadores: cor sólida
    > - Em segundo plano: preto

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capítulo 16 – Criar o Project realidade misturada para a UWP

Este Capítulo é idêntico ao processo de build para o projeto anterior. Tudo o que é necessário para a seção Unity deste projeto agora foi concluído, portanto, é hora de criar a partir do Unity.

1.  Navegue **até Criar Configurações** ( build **de** arquivo  >  **Configurações** ).

2.  No menu **Criar Configurações,** verifique se Projetos **C#** do Unity * está marcado (o que permitirá que você edite os scripts neste projeto, após o build).

3.  Depois de fazer isso, clique em **Criar**.

    ![criar projeto](images/AzureLabs-Lab8-99.png)

4.  Uma **Explorador de Arquivos** janela será aberta, solicitando um local para Build. Crie uma nova pasta (clicando em **Nova Pasta** no canto superior esquerdo) e nomeia-a **BUILDS**.

    ![criar pasta builds](images/AzureLabs-Lab8-100.png)

    1.  Abra a nova **pasta BUILDS** e crie outra pasta (usando Nova **Pasta** mais uma vez) e nomee-a **aplicativo NH \_ MR \_**.

        ![criar NH_MR_Apps pasta](images/AzureLabs-Lab8-101.png)

    2.  Com o **aplicativo NH \_ MR \_** selecionado. clique **em Selecionar Pasta**. O projeto levará um minuto para ser construído.

5.  Após o build, **uma Explorador de Arquivos** janela será aberta no local do novo projeto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>capítulo 17-adicionar pacotes de NuGet à solução UnityMRNotifHub

> [!WARNING] 
> lembre-se de que, depois de adicionar os pacotes de NuGet a seguir (e remover o comentário do código no próximo [capítulo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), o código, quando reaberto no Project do Unity, apresentará erros. Se desejar voltar e continuar a edição no editor do Unity, você precisará comentar o código errosome e, em seguida, remover o comentário novamente mais tarde, quando estiver de volta ao Visual Studio. 

depois que a compilação da realidade misturada for concluída, navegue até o projeto de realidade misturada, que você criou e clique duas vezes no arquivo da solução (. sln) dentro dessa pasta para abrir sua solução com o Visual Studio 2017.
agora, você precisará adicionar o pacote de NuGet **. Messaging. managed WindowsAzure** ; Esta é uma biblioteca que é usada para receber notificações do hub de notificação.

para importar o pacote de NuGet:

1.  Na **Gerenciador de soluções**, clique com o botão direito do mouse em sua solução

2.  clique em **gerenciar pacotes de NuGet**.

    ![abrir o Gerenciador do NuGet](images/AzureLabs-Lab8-102.png)

3.  Selecione a guia ***procurar** _ e procure _ * WindowsAzure. Messaging. Managed * *.

    ![Localizar pacote de mensagens do Windows Azure](images/AzureLabs-Lab8-103.png)

4.  Selecione o resultado (como mostrado abaixo) e, na janela à direita, marque a caixa de seleção ao lado de **Project**. isso fará uma marcação na caixa de seleção ao lado de **Project**, juntamente com a caixa de seleção ao lado do projeto **Assembly-CSharp** e **UnityMRNotifHub** .

    ![todos os projetos em escala](images/AzureLabs-Lab8-104.png)

5.  A versão fornecida inicialmente **pode não** ser compatível com este projeto. Portanto, clique no menu suspenso ao lado de **versão** e clique em **versão 0.1.7.9**, em seguida, clique em **instalar**.

6.  você concluiu a instalação do pacote de NuGet. Localize o código comentado que você inseriu na classe **NotificationReceiver** e remova os comentários.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capítulo 18-editar aplicativo UnityMRNotifHub, classe NotificationReceiver

após ter adicionado os **pacotes de NuGet**, você precisará remover o *comentário* de parte do código dentro da classe **NotificationReceiver** .

Isso inclui:

1. O namespace na parte superior:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Todo o código dentro do método **InitNotificationsAsync ()** :

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> O código acima tem um comentário: Certifique-se *de que você* não tenha desmarcado acidentalmente esse comentário (pois o código não será compilado se você tiver!).

3. E, por fim, o evento **Channel_PushNotificationReceived** :

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Com esses comentários, certifique-se de salvar e, em seguida, vá para o próximo capítulo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capítulo 19 – associar o projeto de realidade misturada ao aplicativo da loja

Agora você precisa associar o projeto de **realidade misturada** ao aplicativo da loja criado no no início do laboratório.

1.  Abra a solução.

2.  clique com o botão direito do mouse no aplicativo UWP Project no painel de Gerenciador de Soluções, acesse **armazenar** e **associe o aplicativo à loja...**.

    ![abrir Associação de armazenamento](images/AzureLabs-Lab8-105.png)

3.  uma nova janela será exibida chamada **associar seu aplicativo com a Windows Store**. Clique em **Avançar**.

    ![ir para a próxima tela](images/AzureLabs-Lab8-106.png)

4.  Ele carregará todos os aplicativos associados à conta em que você fez logon. Se você não estiver conectado à sua conta, poderá **fazer logon** nesta página.

5.  Localize o **nome do aplicativo da loja** que você criou no início deste tutorial e selecione-o. Em seguida, clique em **Próximo**.

    ![Localizar e selecionar o nome do repositório](images/AzureLabs-Lab8-107.png)

6.  Clique em **Associar**.

    ![associar o aplicativo](images/AzureLabs-Lab8-108.png)

7.  Seu aplicativo agora está **associado** ao aplicativo da loja. Isso é necessário para habilitar as notificações.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capítulo 20-implantar aplicativos UnityMRNotifHub e UnityDesktopNotifHub

Este capítulo pode ser mais fácil com duas pessoas, pois o resultado incluirá ambos os aplicativos em execução, um em execução na área de trabalho do computador e o outro no headset de imersão.

O aplicativo de headset de imersão está aguardando para receber alterações na cena (alterações de posição do GameObjects local) e o aplicativo de área de trabalho fará alterações em sua cena local (alterações de posição), que será compartilhada para o aplicativo MR. Faz sentido implantar o aplicativo Sr primeiro, seguido pelo aplicativo de desktop, para que o receptor possa começar a escutar.

Para implantar o aplicativo **UnityMRNotifHub** em seu computador local:

1.  abra o arquivo de solução do seu aplicativo **UnityMRNotifHub** no **Visual Studio 2017**.

2.  Na **plataforma da solução**, selecione **x86, computador local**.

3.  Na **configuração da solução** , selecione **depurar**.

    ![definir configuração do projeto](images/AzureLabs-Lab8-109.png)

4.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.

Para implantar o aplicativo **UnityDesktopNotifHub** no computador local:

1.  abra o arquivo de solução do seu aplicativo **UnityDesktopNotifHub** no **Visual Studio 2017**.

2.  Na **plataforma da solução**, selecione **x86, computador local**.

3.  Na **configuração da solução** , selecione **depurar**.

    ![definir configuração do projeto](images/AzureLabs-Lab8-110.png)

4.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.

6.  Inicie o aplicativo de realidade misturada, seguido pelo aplicativo de desktop.

Com ambos os aplicativos em execução, mova um objeto na cena da área de trabalho (usando o botão esquerdo do mouse). Essas alterações posicionais serão feitas localmente, serializadas e enviadas para o serviço de Aplicativo de funções. O serviço de Aplicativo de funções atualizará a tabela junto com o Hub de notificação. Após ter recebido uma atualização, o Hub de notificação enviará os dados atualizados diretamente para todos os aplicativos registrados (nesse caso, o aplicativo de headsets de imersão), que desserializará os dados de entrada e aplicará os novos dados posicionais aos objetos locais, movendo-os em cena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Seu aplicativo de hubs de notificação do Azure foi concluído
 
Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de hubs de notificação do Azure e permite a comunicação entre aplicativos.
 
![final do produto final](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Você pode solucionar como alterar a cor do GameObjects e enviar essa notificação para outros aplicativos que visualizam a cena?

### <a name="exercise-2"></a>Exercício 2

Você pode adicionar movimento do GameObjects ao seu aplicativo MR e ver a cena atualizada em seu aplicativo de desktop?