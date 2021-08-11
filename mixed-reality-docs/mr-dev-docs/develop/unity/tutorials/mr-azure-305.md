---
title: HoloLens (1ª geração) e Azure 305 – Funções e armazenamento
description: conclua este curso para aprender a implementar Armazenamento e funções do Azure dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realidade mista, academia, unity, tutorial, api, funções, armazenamento, hololens, imersão, vr, Windows 10, Visual Studio
ms.openlocfilehash: 337b1d3fb23450325805237a6ba975861260760b7d37028b8d717bad99b9d233
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193804"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a>HoloLens (1ª gen) e o Azure 305: funções e armazenamento

<br>

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br> 

![início do produto final](images/AzureLabs-Lab5-00.png)

neste curso, você aprenderá a criar e usar Azure Functions e armazenar dados com um recurso de Armazenamento do Azure, em um aplicativo de realidade misturada.

*Azure Functions* é um serviço da Microsoft, que permite aos desenvolvedores executar pequenas partes de código, ' Functions ', no Azure. Isso fornece uma maneira de delegar trabalho para a nuvem, em vez de seu aplicativo local, que pode ter muitos benefícios. O *Azure Functions* dá suporte a várias linguagens de desenvolvimento, incluindo C \# , F \# , Node.js, Java e php. Para obter mais informações, visite o [artigo Azure Functions](/azure/azure-functions/functions-overview).

o *Azure Armazenamento* é um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados, com o seguro de que ele será altamente disponível, seguro, durável, escalonável e redundante. Isso significa que a Microsoft tratará de toda a manutenção e problemas críticos para você. para obter mais informações, visite o [artigo Armazenamento do Azure](/azure/storage/common/storage-introduction).

Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada que poderá fazer o seguinte:

1.  Permitir que o usuário olhar em uma cena.
2.  Dispare a geração de objetos quando o usuário gazes em um "botão" 3D.
3.  Os objetos gerados serão escolhidos por uma função do Azure.
4.  à medida que cada objeto é gerado, o aplicativo armazenará o tipo de objeto em um *arquivo do azure*, localizado no *azure Armazenamento*.
5.  Ao carregar uma segunda vez, os dados de *arquivo do Azure* serão recuperados e usados para reproduzir as ações de geração da instância anterior do aplicativo.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com o Project do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>MR e Azure 305: funções e armazenamento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> embora este curso se concentre principalmente em headsets de Windows Mixed Reality de imersão (VR), você também pode aplicar o que aprende neste curso para Microsoft HoloLens. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a HoloLens.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com o Unity e o C#. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](../../install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- um PC de desenvolvimento, [compatível com Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para o desenvolvimento de headsets de imersão (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](../../install-the-tools.md#installation-checklist)
- [o SDK de Windows 10 mais recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017,4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- um [headset de Windows Mixed Reality de imersão (VR)](../../../discover/immersive-headset-hardware-details.md) ou [Microsoft HoloLens](/hololens/hololens1-hardware) com o modo de desenvolvedor habilitado
- Uma assinatura para uma conta do Azure para criar recursos do Azure
- Acesso à Internet para a instalação do Azure e recuperação de dados

## <a name="before-you-start"></a>Antes de começar

Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1-o portal do Azure

para usar o **serviço de Armazenamento do Azure**, será necessário criar e configurar uma **conta de Armazenamento** no portal do Azure.

1.  Faça logon no  [portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *Armazenamento conta* e clique em **Enter**.

    ![pesquisa de armazenamento do Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

3.  a nova página fornecerá uma descrição do serviço de *conta de Armazenamento do Azure* . Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.

    ![Criar serviço](images/AzureLabs-Lab5-02.png)

4.  Depois de clicar em **criar**:

    1.  Insira um *nome* para sua conta, lembre-se de que esse campo aceita apenas números e letras minúsculas.

    2.  Para *modelo de implantação*, selecione **Gerenciador de recursos**.

    3.  para *tipo de conta*, selecione **Armazenamento (uso geral v1)**.

    4.  Determine o *local* do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

    5.  Para *replicação* **, selecione leitura-acesso-armazenamento com REDUNDÂNCIA geográfica (ra-grs)**.

    6.  Para *Desempenho*, selecione **Standard**.

    7.  Deixe a *transferência segura necessária* como **desabilitada**.

    8.  Selecione uma *Assinatura*.

    9. Escolha um *grupo de recursos* ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    10. Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    11. Selecione **Criar**.

        ![informações do serviço de entrada](images/AzureLabs-Lab5-03.png)

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Nova notificação no portal do Azure](images/AzureLabs-Lab5-04.png)

7.  Clique nas notificações para explorar sua nova instância de serviço.

    ![ir para o recurso](images/AzureLabs-Lab5-05.png)

8.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. você será levado para sua nova instância de serviço de *conta do Armazenamento* .

    ![teclas de acesso](images/AzureLabs-Lab5-06.png)

9.  Clique em *chaves de acesso* para revelar os pontos de extremidade para este serviço de nuvem. use *Bloco de notas* ou semelhante para copiar uma de suas chaves para uso posterior. Além disso, observe o valor da *cadeia de conexão* , pois ele será usado na classe *azureservices* , que será criada mais tarde.

    ![copiar cadeia de conexão](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capítulo 2-Configurando uma função do Azure

Agora, você escreverá uma **função** **do Azure** no serviço do Azure.

Você pode usar uma **função do Azure** para fazer praticamente tudo o que faria com uma função clássica em seu código, a diferença é que essa função pode ser acessada por qualquer aplicativo que tenha credenciais para acessar sua conta do Azure.

Para criar uma função do Azure:

1.  No *portal do Azure*, clique em **novo** no canto superior esquerdo e procure *aplicativo de funções* e clique em **Enter**.

    ![criar aplicativo de funções](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

2.  A nova página fornecerá uma descrição do serviço aplicativo de funções do *Azure.* Na parte inferior esquerda deste prompt, selecione o **botão** Criar para criar uma associação com esse serviço.

    ![informações do aplicativo de funções](images/AzureLabs-Lab5-09.png)

3.  Depois de clicar em **Criar**:

    1.  Forneça um *Nome do aplicativo*. Somente letras e números podem ser usados aqui (maiúsculas ou inferiores são permitidas).

    2.  Selecione sua Assinatura *preferencial.*

    3. Escolha um *Grupo de Recursos* ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses laboratórios) em um grupo de recursos comum. 

        > Se você quiser ler mais sobre os Grupos de Recursos do Azure, [visite o artigo do grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    4.  Para este exercício, selecione *Windows* como o sistema **operacional escolhido.**

    5.  Selecione *Plano de Consumo* para o Plano de **Hospedagem.**

    6.  Determine o *Local* do grupo de recursos (se você estiver criando um novo Grupo de Recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões. Para obter o desempenho ideal, selecione a mesma região que a conta de armazenamento.

    7.  Por *Armazenamento*, **selecione Usar existente** e, em seguida, usando o menu suspenso, local selecione o armazenamento criado anteriormente.

    8.  Deixe *Application Insights* off para este exercício.

        ![detalhes do aplicativo de funções de entrada](images/AzureLabs-Lab5-10.png)

4.  Selecione o botão **Criar**.

5.  Depois de clicar em **Criar**, você terá que aguardar até que o serviço seja criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal depois que a instância de serviço for criada.

    ![nova notificação do portal do Azure](images/AzureLabs-Lab5-11.png)

7.  Clique nas notificações para explorar sua nova instância de serviço. 

    ![ir para o aplicativo de funções de recurso](images/AzureLabs-Lab5-12.png)

8.  Clique no **botão Ir para o** recurso na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância *do Serviço de Aplicativo* de Funções.

9.  No painel *aplicativo de funções,* passe o mouse sobre Funções *,* encontrado no painel à esquerda e clique no símbolo **+ (adição).**

    ![criar nova função](images/AzureLabs-Lab5-13.png)

10. Na próxima página, verifique se **Webhook + API** está selecionado e, para Escolher um *idioma,* selecione **CSharp,** pois essa será a linguagem usada para este tutorial. Por fim, clique no **botão Criar esta** função.

    ![selecione web hook csharp](images/AzureLabs-Lab5-14.png)

11. Você deve ser levado para a página de código (run.csx), caso não seja, clique na Função recém-criada na lista Funções no painel à esquerda.

    ![abrir nova função](images/AzureLabs-Lab5-15.png)

12. Copie o código a seguir para sua função. Essa função simplesmente retornará um inteiro aleatório entre 0 e 2 quando chamado. Não se preocupe com o código existente, sinta-se à vontade para colar sobre ele.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Selecione **Salvar**.

14. O resultado deve ser parecido com a imagem abaixo.

15. Clique em **Obter URL da** função e anote o ponto de *extremidade* exibido. Você precisará inseri-lo na *classe AzureServices* que você criará posteriormente neste curso.

    ![Obter ponto de extremidade de função](images/AzureLabs-Lab5-16.png)

    ![Inserir ponto de extremidade de função](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3 – Configurando o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com Realidade Misturada e, como tal, é um bom modelo para outros projetos.

Configurar e testar seu headset imersivo de realidade misturada.

> [!NOTE]
> Você não **exigirá** Controladores de Movimento para este curso. Se você precisar de suporte para configurar o headset imersivo, visite o artigo de configuração [de realidade misturada](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra o Unity e clique em **Novo.**

    ![Criar um novo projeto do Unity](images/AzureLabs-Lab5-17.png)

2.  Agora você precisará fornecer um nome de Project Unity. Insira **MR_Azure_Functions**. Certifique-se de que o tipo de projeto está definido **como 3D.** De definir *o Local* como em algum lugar apropriado para você (lembre-se de que mais próximo dos diretórios raiz é melhor). Em seguida, clique **em Criar projeto**.

    ![Dê um nome ao novo projeto do Unity](images/AzureLabs-Lab5-18.png)

3.  Com o Unity aberto, vale a pena verificar se o **Editor de Script** padrão está definido como **Visual Studio**. Vá para **Editar**  >  **Preferências** e, em seguida, na nova janela, navegue até **Ferramentas Externas.** Altere **Editor de Script** Externo para Visual Studio **2017.** Feche a **janela Preferências.**

    ![definir o Visual Studio como editor de script](images/AzureLabs-Lab5-19.png)

4.  Em seguida, **vá** para Criar arquivo Configurações e alternar a plataforma para Plataforma Universal Windows , clicando no  >   **botão Alternar Plataforma.** 

    ![alternar plataforma para uwp](images/AzureLabs-Lab5-20.png)

5.  Vá para **Arquivo**  >  **de Build Configurações** e certifique-se de que:

    1. **O Dispositivo de** Destino é definido **como Qualquer Dispositivo.**

        > Para Microsoft HoloLens, de definido **Dispositivo de Destino** como *HoloLens*.

    2. **O tipo de** build é definido como **D3D**

    3. **O SDK** está definido como **Mais recente instalado**

    4. **Visual Studio versão é** definida como **Mais recente instalada**

    5. **Build e Executar** são definidos como **Computador Local**

    6. Salve a cena e adicione-a ao build.

        1.  Faça isso selecionando **Adicionar Cenas Abertas.** Uma janela salvar será exibida.

            ![adicionar cenas abertas](images/AzureLabs-Lab5-21.png)

        2.  Crie uma nova pasta para essa cena e,  em qualquer futuro, selecione o botão Nova pasta, para criar uma nova pasta, nomeá-la **Cenas**.

            ![criar pasta scenes](images/AzureLabs-Lab5-22.png)

        3.  Abra a pasta **Cenas** recém-criada e, em seguida, no campo Nome do **arquivo:** texto, digite **FunctionsScene** e pressione **Salvar**.

            ![Salvar cena de funções](images/AzureLabs-Lab5-23.png)

6.  As configurações restantes, em **Build Configurações**, devem ser deixadas como padrão por enquanto.

    ![Deixe as configurações de build padrão](images/AzureLabs-Lab5-24.png)

7.  Na janela *Criar Configurações,* clique no botão **Player Configurações,** isso abrirá o painel relacionado no espaço em que o *Inspetor* está localizado.

    ![configurações do player no inspetor](images/AzureLabs-Lab5-25.png)

8.  Neste painel, algumas configurações precisam ser verificadas:

    1.  Na guia **Outros Configurações:**

        1.  **A versão do Runtime de Script** deve ser **Experimental** (equivalente ao .NET 4.6), o que disparará a necessidade de reiniciar o Editor.
        2.  **Back-end de script** deve ser **.NET**
        3.  **O nível de compatibilidade da API** deve ser **.NET 4.6**

    2.  Na guia **Publicação Configurações,** em **Funcionalidades,** verifique:
        
        -  **InternetClient**

            ![definir funcionalidades](images/AzureLabs-Lab5-26.png)

    3.  Mais para baixo no painel, no **XR Configurações** (encontrado abaixo de **Publishing Configurações**), marque **Realidade Virtual** Com Suporte , certifique-se de que Windows Mixed Reality **SDK** foi adicionado.

        ![definir configurações de XR](images/AzureLabs-Lab5-27.png)

9.  De volta *ao Build Configurações* projetos *C# do Unity* não está mais es cinza; marque a caixa de seleção ao lado disso.

    ![tick c# projects](images/AzureLabs-Lab5-28.png)

10.  Feche a janela Configurações de Build.

11. Salve sua cena e Project (**ARQUIVO**  >  **SALVAR CENA/ARQUIVO SALVAR**  >  **PROJETO**).

## <a name="chapter-4---setup-main-camera"></a>Capítulo 4 – Configurar a câmera principal

> [!IMPORTANT]
> Se você quiser ignorar os componentes de Configuração do *Unity* deste curso e continuar diretamente no código, sinta-se à vontade para baixar este [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importá-lo para seu projeto como um [Pacote Personalizado.](https://docs.unity3d.com/Manual/AssetPackages.html) Isso também conterá as DLLs do próximo Capítulo. Após a importação, continue [do Capítulo 7.](#chapter-7---create-the-azureservices-class) 

1.  No Painel *de Hierarquia*, você encontrará um objeto chamado **Câmera Principal**, esse objeto representa o ponto de vista "head" quando você está "dentro" do aplicativo.

2.  Com o Painel do Unity na sua frente, selecione **o GameObject da Câmera Principal.** Você observará que o Painel inspetor *(geralmente* encontrado à direita, dentro do Painel) mostrará os vários componentes desse *GameObject*, com Transformar na parte superior, seguido por *Câmera* e alguns outros componentes.  Você precisará redefinir a Transformação da Câmera Principal para que ela seja posicionada corretamente.

3.  Para fazer isso, selecione o ícone **de** Engrenagem ao lado do componente Transformação da Câmera e selecione **Redefinir**. 

    ![redefinir transformação](images/AzureLabs-Lab5-29.png)

4.  Em seguida, **atualize o** componente Transformar para ter a aparência:

    |         |    TRANSFORM – POSITION   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **S**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORMAÇÃO – ROTAÇÃO |       |
    | :---: | :------------------: | :----:|
    | **X** | **S**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMAÇÃO – ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 1     | 1                 | 1     |

    ![definir a transformação da câmera](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capítulo 5 – Configurando a cena do Unity

1.  Clique com o botão direito do mouse em uma área vazia do Painel *de Hierarquia,* em **Objeto 3D,** adicione um **Plano**.

    ![criar novo plano](images/AzureLabs-Lab5-31.png)

2.  Com o **objeto Plano** selecionado, altere os seguintes parâmetros no Painel *inspetor*:

    |       | TRANSFORM – POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **S**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORMAÇÃO – ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 10    | 1                 | 10    |

    ![definir a posição e a escala do plano](images/AzureLabs-Lab5-32.png)

    ![exibição de cena do plano](images/AzureLabs-Lab5-33.png)

3.  Clique com o botão direito do mouse em uma área vazia do Painel *de Hierarquia,* em **Objeto 3D,** adicione um **Cubo**.

    1.  Renomeie o Cubo como **GazeButton** (com o Cubo selecionado, pressione 'F2').

    2.  Altere os seguintes parâmetros no Painel *inspetor*:

        |       | TRANSFORM – POSITION |       |
        | :---: | :------------------: |:-----:|
        | **X** | **S**                | **Z** |
        | 0     | 3                    | 5     |


        ![definir transformação do botão de olhar](images/AzureLabs-Lab5-34.png)

        ![exibição de cena do botão de olhar](images/AzureLabs-Lab5-35.png)

    3.  Clique no botão **de lista** listada de marcas e clique em **Adicionar Marca** para abrir o painel Marcas *& Camadas*.

        ![adicionar nova marca](images/AzureLabs-Lab5-36.png)

        ![selecionar mais](images/AzureLabs-Lab5-37.png)

    4.  Selecione o **botão + (a mais)** e, no *campo* Novo Nome da Marca, insira **GazeButton** e pressione **Salvar**.

        ![name new tag](images/AzureLabs-Lab5-38.png)

    5.  Clique no objeto **GazeButton** no Painel *hierarquia* e, no Painel *inspetor,* atribua a marca **GazeButton** recém-criada.

        ![atribuir botão de olhar a nova marca](images/AzureLabs-Lab5-39.png)

4.  Clique com o botão direito do mouse no objeto **GazeButton,** no Painel de Hierarquia e adicione um **GameObject** vazio (que será adicionado como *um objeto* filho).

5.  Selecione o novo objeto e renomeie-o **Como FormaSpawnPoint**.

    1.  Altere os seguintes parâmetros no Painel *inspetor*:

        |       | TRANSFORM – POSITION |       |
        | :---: | :------------------: |:----: |
        | **X** |**S**                 | **Z** |
        | 0     | -1                   | 0     |

        ![atualizar transformação de ponto de gerar forma](images/AzureLabs-Lab5-40.png)

        ![exibição da cena do ponto de gerar forma](images/AzureLabs-Lab5-41.png)

6.  Em seguida, você criará **um objeto de Texto 3D** para fornecer comentários sobre o status do serviço do Azure.

    Clique com o botão direito do mouse no **GazeButton** no Painel de Hierarquia novamente e adicione um objeto **3D Object**  >  **3D Text** como um *filho.*

    ![criar novo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  Renomeie o **objeto Text 3D** como **AzureStatusText.**

8.  Altere **a Transformação do objeto AzureStatusText** da seguinte maneira:

    |       | TRANSFORM – POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **S**                | **Z** |
    | 0     | 0                    | -0,6  |

    |       | TRANSFORMAÇÃO – ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 0,1   | 0,1               | 0,1   |


    > [!NOTE]
    > Não se preocupe se ele parece estar fora do centro, pois isso será corrigido quando o componente de Malha de Texto abaixo for atualizado.

9.  Altere **o componente Malha de** Texto para corresponder ao abaixo:

    ![definir componente de malha de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > A cor selecionada aqui é Hex color: **000000FF, embora sinta-se** à vontade para escolher sua própria, apenas verifique se ela está acessível.

10. A estrutura do Painel de Hierarquia agora deve ter esta aparência:

    ![Malha de texto na hierarquia](images/AzureLabs-Lab5-43b.png)

10. Sua cena agora deve ter esta aparência:

    ![Malha de texto na exibição de cena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capítulo 6 – Importar o Azure Armazenamento para Unity

Você estará usando o Azure Armazenamento para Unity (que aproveita o SDK do .Net para Azure). Você pode ler mais sobre isso no [artigo Armazenamento Azure para Unity](/sandbox/gamedev/unity/azure-storage-unity).

Atualmente, há um problema conhecido no Unity que exige que os plug-ins sejam reconfigurados após a importação. Essas etapas (4 a 7 nesta seção) não serão mais necessárias depois que o bug for resolvido.

Para importar o SDK para seu próprio projeto, certifique-se de ter baixado o ['.unitypackage'](https://aka.ms/azstorage-unitysdk)mais recente do GitHub . Em seguida, faça o seguinte:

1.  Adicione o **arquivo .unitypackage** ao Unity usando a **opção** de menu Pacote Personalizado de Importação de  >    >   Ativos.

2.  Na caixa **Importar Pacote do Unity** que aparece, você pode selecionar tudo em **Plug-in**  >  **Armazenamento**. Desmarque todo o resto, pois ele não é necessário para este curso.

    ![importar para o pacote](images/AzureLabs-Lab5-45.png)

3.  Clique no **botão Importar** para adicionar os itens ao seu projeto.

4.  Acesse a pasta *Armazenamento* em *Plug-ins,* no Project exibição e selecione os seguintes plug-ins *somente:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![desmarque Qualquer plataforma](images/AzureLabs-Lab5-46.png)

5.  Com *esses plug-ins específicos selecionados,* desmarque Qualquer  *Plataforma* e *desmarque WSAPlayer* e clique em **Aplicar**. 

    ![aplicar dlls de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Estamos marcando esses plug-ins específicos para serem usados apenas no Editor do Unity. Isso porque há versões diferentes dos mesmos plug-ins na pasta WSA que serão usadas depois que o projeto for exportado do Unity.

6.  Na pasta *Armazenamento* plug-in, selecione apenas:

    -   Microsoft.Data.Services.Client

        ![set não processa para dlls](images/AzureLabs-Lab5-48.png)

7.  Marque a **caixa Não Processar em** Plataforma Configurações clique em **Aplicar**. 

    ![aplicar nenhum processamento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Estamos marcando esse plug-in "Não processar" porque o patchr de assembly do Unity tem dificuldade para processar esse plug-in. O plug-in ainda funcionará mesmo que não seja processado.

## <a name="chapter-7---create-the-azureservices-class"></a>Capítulo 7 – Criar a classe AzureServices

A primeira classe que você criará é *a classe AzureServices.*

A *classe AzureServices* será responsável por:

-   Armazenamento de credenciais da Conta do Azure.

-   Chamando sua Azure App Função.

-   O upload e o download do arquivo de dados em seu Azure Cloud Armazenamento.

Para criar esta Classe:

1.  Clique com o botão *direito* do mouse na Pasta de Ativos, localizada no painel Project, **Criar**  >  **Pasta**. Nomeia a **pasta Scripts**.

    ![criar nova pasta](images/AzureLabs-Lab5-50.png)

    ![pasta call - scripts](images/AzureLabs-Lab5-51.png)

2.  Clique duas vezes na pasta que acabou de ser criada para abri-la.

3.  Clique com o botão direito do mouse dentro da pasta **Criar**  >  **Script C#.** Chame o script *AzureServices*.

4.  Clique duas vezes na nova *classe AzureServices* para abri-la com *Visual Studio*.

5.  Adicione os seguintes namespaces à parte superior do *AzureServices:*

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Adicione os seguintes Campos inspetores dentro da *classe AzureServices:*

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  Em seguida, adicione as seguintes variáveis de membro dentro *da classe AzureServices:*

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Substitua os valores do  ponto *de* extremidade e da cadeia de conexão com os valores do armazenamento do Azure, encontrados no Portal do Azure

8.  O código *para métodos Awake()* e *Start()* agora precisa ser adicionado. Esses métodos serão chamados quando a classe for inicializada:

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > Preencheremos o código para *CallAzureFunctionForNextShape()* em um [capítulo futuro.](#chapter-10---completing-the-azureservices-class)

9.  *Exclua o método Update(),* pois essa classe não o usará.

10. Salve suas alterações no Visual Studio e, em seguida, retorne ao Unity.

11. Clique e arraste *a classe AzureServices* da pasta Scripts para o objeto Câmera Principal no Painel *de Hierarquia*.

12. Selecione a Câmera Principal, pegue o objeto filho **AzureStatusText** abaixo do objeto **GazeButton** e coloque-o dentro do campo de destino de referência **AzureStatusText,** no *Inspetor,* para fornecer a referência ao script *AzureServices.*

    ![atribuir destino de referência de texto de status do Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capítulo 8 – Criar a classe ShapeFactory

O próximo script a ser criado é a *classe ShapeFactory.* A função dessa classe é criar uma nova forma, quando solicitado, e manter um histórico das formas criadas em uma Lista *de Histórico de Formas*. Sempre que uma forma  é criada, a lista Histórico de Formas é atualizada na *classe AzureService* e armazenada em seu *Azure Armazenamento*. Quando o aplicativo é iniciado, se um arquivo armazenado é  encontrado em seu *Azure Armazenamento*, a lista Histórico de Formas é recuperada e reprodução, com o objeto **Texto 3D** fornecendo se a forma gerada é do armazenamento ou novo.

Para criar esta classe:

1.  Vá para a **pasta Scripts** criada anteriormente.

2.  Clique com o botão direito do mouse dentro da pasta **Criar**  >  **Script C#.** Chame o script *ShapeFactory*.

3.  Clique duas vezes no novo script *ShapeFactory* para abri-lo com *Visual Studio*.

4.  Verifique se *a classe ShapeFactory* inclui os seguintes namespaces:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Adicione as variáveis mostradas abaixo à *classe ShapeFactory* e substitua as funções *Start()* e *Awake()* por aquelas abaixo:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  O *método CreateShape()* gera as formas primitivas, com base no parâmetro *inteiro* fornecido. O parâmetro booliana é usado para especificar se a forma criada no momento é de armazenamento ou nova. Coloque o seguinte código em *sua classe ShapeFactory,* abaixo dos métodos anteriores:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Salve suas alterações no Visual Studio antes de retornar ao Unity.

8.  De volta ao Editor do Unity, clique e arraste a *classe ShapeFactory* da pasta **Scripts** para o objeto **Câmera** Principal no Painel *de Hierarquia*.

9. Com a Câmera Principal selecionada, você observará que o componente de script *ShapeFactory* não tem a *referência Desovar Ponto.* Para corrigi-lo, arraste **o objeto ShapeSpawnPoint** do Painel *de* Hierarquia para o destino de referência do **Ponto de** Gerar.

    ![definir o destino de referência de fábrica de formas](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capítulo 9 – Criar a classe Gaze

O último script que você precisa criar é a *classe Gaze.*

Essa classe é responsável por criar um **Raycast** que será projetado para frente da Câmera Principal, para detectar qual objeto o usuário está olhando. Nesse caso, o Raycast precisará identificar se o usuário está olhando para o objeto **GazeButton** na cena e disparar um comportamento.

Para criar esta Classe:

1.  Vá para a **pasta Scripts** criada anteriormente.

2.  Clique com o botão direito do mouse no painel Project, **Criar**  >  **Script C#.** Chame o script *Desalocar*.

3.  Clique duas vezes no novo script *Gaze* para abri-lo com *Visual Studio.*

4.  Verifique se o namespace a seguir está incluído na parte superior do script:

    ```csharp
        using UnityEngine;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da *classe Gaze:*

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Algumas dessas variáveis poderão ser editadas no *Editor*.

6.  O código *para os métodos Awake()* e *Start()* agora precisa ser adicionado.

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Adicione o código a seguir, que criará um objeto de cursor no início, juntamente com o método *Update(),* que executará o método Raycast, juntamente com o local em que o booliana GazeEnabled é alternado:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. Em seguida, *adicione o método UpdateRaycast(),* que projetará um Raycast e detectará o destino de acerto.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Por fim, adicione o método *ResetFocusedObject(),* que alterna a cor atual dos objetos GazeButton, indicando se ele está criando uma nova forma ou não.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Salve suas alterações no Visual Studio antes de retornar ao Unity.

11.  Clique e arraste *a classe Gaze* da pasta Scripts para o objeto Câmera **Principal** no Painel *de Hierarquia*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Capítulo 10 – Concluindo a classe AzureServices

Com os outros scripts em uso, agora é possível *concluir a* *classe AzureServices.* Isso será feito por meio de:

1.  Adicionar um novo método chamado *CreateCloudIdentityAsync()* para configurar as variáveis de autenticação necessárias para se comunicar com o Azure.

    > Esse método também verificará a existência de um Arquivo armazenado anteriormente que contém a Lista de Formas.
    >
    > **Se o arquivo for** encontrado , ele desabilitará o usuário De olhar e disparará a criação de forma, de acordo com o padrão de formas, conforme armazenado no arquivo de Armazenamento do **Azure.** O usuário pode ver  isso, pois a Malha de Texto fornecerá a exibição 'Armazenamento' ou 'Novo', dependendo da origem das formas.
    >
    > **Se nenhum arquivo for encontrado,** ele habilita o Gaze *,* permitindo que o usuário crie formas ao olhar para o objeto **GazeButton** na cena.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  O próximo snippet de código é de dentro do *método Start();* em que uma chamada será feita para o *método CreateCloudIdentityAsync().* Sinta-se à vontade para copiar sobre o *método Start()* atual, com o abaixo:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Preencha o código para o método *CallAzureFunctionForNextShape().* Você usará o Aplicativo de Funções do *Azure criado anteriormente para* solicitar um índice de forma. Depois que a nova forma for recebida, esse método enviará a forma para a *classe ShapeFactory* para criar a nova forma na cena. Use o código abaixo para concluir o corpo *de CallAzureFunctionForNextShape()*.

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  Adicione um método para criar uma cadeia de caracteres concatenando os inteiros armazenados na lista de histórico de formas e salvando-o no arquivo de Armazenamento do *Azure.*

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  Adicione um método para recuperar o texto armazenado no arquivo localizado no arquivo Armazenamento do *Azure* e *deserializá-lo* em uma lista.

6.  Depois que esse processo for concluído, o método reabilitará o olhar para que o usuário possa adicionar mais formas à cena.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Salve suas alterações no Visual Studio antes de retornar ao Unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Capítulo 11 – Criar a solução UWP

Para iniciar o processo de build:

1.  Vá para **Build de**  >  **Arquivo Configurações**.

    ![criar o aplicativo](images/AzureLabs-Lab5-54.png)

2.  Clique em **Compilar**. O Unity iniciará *uma Explorador de Arquivos,* na qual você precisa criar e, em seguida, selecionará uma pasta na qual o aplicativo será criado. Crie essa pasta agora e nomee-a *Aplicativo*. Em seguida, com *a pasta* Aplicativo selecionada, pressione **Selecionar Pasta**.

3.  O Unity começará a criar seu projeto para a *pasta Aplicativo.*

4.  Depois que o Unity terminar de criar (pode levar algum tempo), ele abrirá uma janela do Explorador de Arquivos no local do build (verifique a barra de tarefas, pois ela pode nem sempre aparecer acima das janelas, mas notificará você sobre *a* adição de uma nova janela).

## <a name="chapter-12---deploying-your-application"></a>Capítulo 12 – Implantando seu aplicativo

Para implantar seu aplicativo:

1.  Navegue até *a pasta* Aplicativo que foi criada no [último Capítulo](#chapter-11---build-the-uwp-solution). Você verá um arquivo com o nome de seus aplicativos, com a extensão '.sln', que deve ser clicada duas vezes, portanto, para abri-lo dentro *Visual Studio*.

2.  Na Plataforma **de Solução**, selecione **x86, Computador Local.**

3.  Na **Configuração da Solução,** selecione **Depurar**.

    > Para o Microsoft HoloLens, você pode achar mais fácil definir isso como Computador *Remoto,* para que você não seja obrigado a ficar em seu computador. No entanto, você também precisará fazer o seguinte:
    > - Conheça o Endereço **IP** do seu HoloLens, que pode ser encontrado nas Opções Avançadas de Wi-Fi da Internet Configurações Configurações Network & ; o  >    >    >  IPv4 é o endereço que você deve usar. 
    > - Verifique **se o Modo de** Desenvolvedor está **Em**; encontrado **no** Configurações  >  **atualizar & segurança**  >  **para desenvolvedores**.

    ![implantar solução](images/AzureLabs-Lab5-55.png)

4.  Vá para o menu **Build** e clique em **Implantar Solução** para fazer sideload do aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para serem lançados e testados!

## <a name="your-finished-azure-functions-and-storage-application"></a>Seu aplicativo Azure Functions e Armazenamento concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita os serviços de Azure Functions e Azure Armazenamento Azure. Seu aplicativo poderá desenhar em dados armazenados e fornecer uma ação com base nos dados.

![final product -end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Crie um segundo ponto de adoção e um registro do ponto de o qual um objeto foi criado. Quando você carrega o arquivo de dados, reproduza as formas que estão sendo geradas do local em que foram criadas originalmente.

### <a name="exercise-2"></a>Exercício 2

Crie uma maneira de reiniciar o aplicativo, em vez de precisar abri-lo novamente a cada vez. **Carregar cenas** é um bom ponto para começar. Depois de fazer isso, crie uma maneira de limpar a lista armazenada no *Azure Armazenamento*, para que ela possa ser redefinida facilmente do seu aplicativo.