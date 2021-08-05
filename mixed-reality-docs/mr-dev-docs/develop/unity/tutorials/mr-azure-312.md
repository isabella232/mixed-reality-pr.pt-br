---
title: HoloLens (1ª geração) e Azure 312 – Integração de bots
description: conclua este curso para aprender a criar e implantar um bot, usando Microsoft Bot Framework v4 e se comunicar com ele em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realidade mista, academia, unity, tutorial, api, pesquisa visual computacional, hololens, imersão, vr, microsoft bot framework v4, bot de aplicativo web, bot framework, microsoft bot, Windows 10 Visual Studio
ms.openlocfilehash: 61a39806c2b434cb85d39a9b208ea8659ec8cbc301d8955ee1330bda4149f0db
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189670"
---
# <a name="hololens-1st-gen-and-azure-312-bot-integration"></a>HoloLens (1ª gen) e Azure 312: integração de Bot

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

neste curso, você aprenderá a criar e a implantar um bot usando o Microsoft Bot Framework V4 e se comunicar com ele por meio de um aplicativo Windows Mixed Reality. 

![](images/AzureLabs-Lab312-00.png)

o **Microsoft Bot Framework V4** é um conjunto de APIs projetadas para fornecer aos desenvolvedores as ferramentas para criar um aplicativo de Bot extensível e escalonável. para obter mais informações, visite a [página Microsoft Bot Framework](https://dev.botframework.com/) ou o [repositório Git V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).

depois de concluir este curso, você terá criado um aplicativo Windows Mixed Reality, que poderá fazer o seguinte:

1. Use um **gesto de toque** para iniciar a escuta de bot para a voz dos usuários.
2. Quando o usuário disse algo, o bot tentará fornecer uma resposta.
3. Exiba as respostas de bots como texto, posicionadas próximo ao bot, na cena do Unity.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 312: integração de bots</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> embora este curso se concentre principalmente em HoloLens, você também pode aplicar o que aprende neste curso para que Windows Mixed Reality headsets de imersão (VR). Como os headsets de imersão (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu PC. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets de imersão (VR).

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com o Unity e o C#. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](../../install-the-tools.md) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.

Recomendamos o seguinte hardware e software para este curso:

- um PC de desenvolvimento, [compatível com Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para o desenvolvimento de headsets de imersão (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](../../install-the-tools.md#installation-checklist)
- [o SDK de Windows 10 mais recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017,4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- um [headset de Windows Mixed Reality de imersão (VR)](../../../discover/immersive-headset-hardware-details.md) ou [Microsoft HoloLens](/hololens/hololens1-hardware) com o modo de desenvolvedor habilitado
- Acesso à Internet para o Azure e para a recuperação do bot do Azure. Para obter mais informações, [siga este link](https://dev.botframework.com/).

### <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste sua HoloLens. se você precisar de suporte para configurar seu HoloLens, [visite o artigo HoloLens instalação](/hololens/hololens-setup). 
3.  é uma boa ideia executar a calibragem e o ajuste do Sensor ao começar a desenvolver um novo aplicativo de HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

para obter ajuda sobre a calibração, siga este [link para o artigo HoloLens calibration](/hololens/hololens-calibration#hololens-2).

para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste HoloLens sensor](/hololens/hololens-updates).

## <a name="chapter-1--create-the-bot-application"></a>Capítulo 1 – criar o aplicativo bot

A primeira etapa é criar o bot como um aplicativo Web ASP.Net Core local. Depois de concluir e testar, você o publicará no portal do Azure.

1.  Abra o Visual Studio. Crie um novo projeto, selecione **aplicativo Web ASP .NET Core** como o tipo de projeto (você o encontrará na subseção .NET Core) e chame-o de **MyBot**. Clique em **OK**.

2.  Na janela que aparecerá, selecione **vazio**. Verifique também se o destino está definido como **ASP NET Core 2,0** e se a autenticação está definida como **sem autenticação**. Clique em **OK**.  

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-01.png)

3.  A solução agora será aberta. clique com o botão direito do mouse em solution **Mybot** na **Gerenciador de Soluções** e clique em **Manage NuGet packages for Solution**. 

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-02.png)

4.  Na guia **procurar** , procure **Microsoft. bot. Builder. Integration. AspNet. Core** (certifique-se de que **incluiu a versão prévia** verificada). Selecione a versão do pacote **4.0.1-Preview** e marque as caixas do projeto. Em seguida, clique em **instalar**. Agora você instalou as bibliotecas necessárias para o **bot Framework v4**. feche a página NuGet.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-03.png)

5.  clique com o botão direito do mouse em seu *Project*, **MyBot**, na **Gerenciador de Soluções** e clique em **adicionar** **|** **classe**.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-04.png)

6.  Nomeie a classe **MyBot** e clique em **Adicionar**.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-05.png)

7.  Repita o ponto anterior para criar outra classe chamada **ConversationContext**. 

8.  Clique com o botão direito do mouse em **wwwroot** no **Gerenciador de soluções** e clique em **Adicionar** **|** **novo item**. Selecione a  **página HTML** (você a encontrará na subseção Web). Nomeie o arquivo **default.html**. Clique em **Adicionar**.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-06.png)

9.  A lista de classes/objetos no **Gerenciador de soluções** deve ser parecida com a imagem abaixo.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-07.png)

10. Clique duas vezes na classe **ConversationContext** . Essa classe é responsável por conter as variáveis usadas pelo bot para manter o contexto da conversa. Esses valores de contexto de conversa são mantidos em uma instância dessa classe, porque qualquer instância da classe **MyBot** será atualizada toda vez que uma atividade for recebida. Adicione o seguinte código à classe:

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Clique duas vezes na classe **MyBot** . Essa classe hospedará os manipuladores chamados por qualquer atividade de entrada do cliente. Nessa classe, você adicionará o código usado para criar a conversa entre o bot e o cliente. Como mencionado anteriormente, uma instância dessa classe é inicializada toda vez que uma atividade é recebida. Adicione o seguinte código a esta classe:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Clique duas vezes na classe **Startup** . Essa classe irá inicializar o bot. Adicione o seguinte código à classe:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Abra o arquivo de classe **programa** e verifique se o código nele é o seguinte:

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. lembre-se de salvar suas alterações, para fazer isso, vá para **arquivo**  >  **salvar tudo**, na barra de ferramentas na parte superior da Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Capítulo 2 – criar o serviço de bot do Azure

Agora que você criou o código para o bot, é necessário publicá-lo em uma instância do serviço de *bot do aplicativo Web* , no portal do Azure. Este capítulo mostrará como criar e configurar o serviço bot no Azure e, em seguida, publicar seu código nele.

1.  Primeiro, faça logon no portal do Azure ( https://portal.azure.com) . 

    1. Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **criar um recurso** no canto superior esquerdo e procure por *bot do aplicativo Web* e clique em **Enter**.

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-08.png)
 
3.  A nova página fornecerá uma descrição do serviço de *bot do aplicativo Web* . Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma associação com esse serviço.

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-09.png)
 
4.  Depois de clicar em **criar**:

    1. Insira o **nome** desejado para esta instância de serviço.
    2. Selecione uma **Assinatura**.
    3. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, [siga este link](/azure/azure-resource-manager/resource-group-portal)

    4. Determine o local do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.
    5. Selecione o **tipo de preço** apropriado para você, se esta for a primeira vez que criar um serviço de *bot de aplicativo Web* , uma camada gratuita (chamada F0) deverá estar disponível para você
    6. O **nome do aplicativo** pode apenas ser deixado o mesmo que o nome do *bot*. 
    7. Deixe o *modelo de bot* como **básico (C#)**.
    8. O *plano/local do serviço de aplicativo* deve ter sido preenchido automaticamente para sua conta.
    9. defina o **Armazenamento do Azure** que você deseja usar para hospedar o Bot. Se você ainda não tiver um, poderá criá-lo aqui.
    10. Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.
    11. Clique em Criar.
 
        ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-10.png)

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-11.png) 
 
7.  Clique na notificação para explorar sua nova instância de serviço. 

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-12.png)
 
8. Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância de serviço do Azure. 

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-13.png)
 
9.  Neste ponto, você precisa configurar um recurso chamado **linha direta** para permitir que o aplicativo cliente se comunique com esse serviço de bot. Clique em **canais** e, na seção **Adicionar um canal em destaque** , clique em **Configurar canal de linha direta**.

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-14.png)

10. Nesta página, você encontrará as **chaves secretas** que permitirão que seu aplicativo cliente seja autenticado com o bot. Clique no botão **Mostrar** e faça uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto. 

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Capítulo 3 – publicar o bot no serviço de bot do aplicativo Web do Azure

Agora que seu serviço está pronto, você precisa publicar seu código de bot, que você criou anteriormente, para o serviço de bot do aplicativo Web criado recentemente.

> [!NOTE] 
> Você precisará publicar o bot no serviço do Azure sempre que fizer alterações na solução/código de bot.

1.  volte para a solução Visual Studio que você criou anteriormente. 
2.  Clique com o botão direito do mouse no projeto **MyBot** , na **Gerenciador de soluções** e clique em **publicar**.

    ![Publicar o bot no serviço de bot do aplicativo Web do Azure](images/AzureLabs-Lab312-16.png)

3.  Na página *escolher um destino de publicação* , clique em **serviço de aplicativo** e **selecione existente**, por fim, clique em **Criar perfil** (talvez seja necessário clicar na seta suspensa junto com o botão *publicar* , se isso não estiver visível).

    ![Publicar o bot no serviço de bot do aplicativo Web do Azure](images/AzureLabs-Lab312-17.png)

4. Se você ainda não estiver conectado à sua conta da Microsoft, precisará fazê-lo aqui.
5. Na página **publicar** , você verá que precisa definir a mesma **assinatura** que usou para a criação do serviço de *bot do aplicativo Web* . Em seguida, defina a **exibição** como **grupo de recursos** e, na estrutura de pastas suspensa, selecione o **grupo de recursos** que você criou anteriormente. Clique em **OK**. 

    ![Publicar o bot no serviço de bot do aplicativo Web do Azure](images/AzureLabs-Lab312-18.png)

6.  Agora, clique no botão **publicar** e aguarde até que o bot seja publicado (pode levar alguns minutos).

    ![Publicar o bot no serviço de bot do aplicativo Web do Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Capítulo 4 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o *Unity* e clique em **novo**. 

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-20.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity. inserir **HoloLens Bot**. Verifique se o modelo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-21.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**. altere o **Editor de Script externo** para **Visual Studio 2017**. Feche a janela **preferências** .

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-22.png)

4.  em seguida, vá para **arquivo > criar Configurações** e selecione **Plataforma Universal do Windows**, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-23.png)

5.  ainda no **arquivo > Build Configurações** e certifique-se de que:

    1.  O **dispositivo de destino** está definido como **HoloLens**

        > Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.

    2.  O **tipo de compilação** está definido como **D3D**

    3.  O **SDK** está definido para o **mais recente instalado**

    4.  **Visual Studio versão** está definida para o **mais recente instalado**

    5.  **Compilar e executar** é definido como **computador local**

    6.  Salve a cena e adicione-a à compilação. 

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.
        
            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-24.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

             ![Configurar o projeto do Unity](images/AzureLabs-Lab312-25.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **BotScene** e clique em **salvar**.

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-26.png)

    7. as configurações restantes, no **Build Configurações**, devem ser deixadas como padrão por enquanto.

6. na janela *criar Configurações* , clique no botão **Configurações do Player** , isso abrirá o painel relacionado no espaço onde o *inspetor* está localizado. 

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-27.png)

7. Nesse painel, algumas configurações precisam ser verificadas:

    1. na guia **outros Configurações** :

        1. A **versão de tempo de execução de script** deve ser **Experimental (NET 4,6 equivalente)**; alterar isso exigirá uma reinicialização do editor.
        2. O **back-end de script** deve ser **.net**
        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-28.png)
      
    2. na guia **publicação Configurações** , em **recursos**, marque:

        - **InternetClient**
        - **Microfone**

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-29.png)

    3. mais adiante no painel, em **XR Configurações** (encontrado abaixo **Configurações de publicação**), **há suporte para a realidade Virtual** de tique, verifique se o **SDK do Windows Mixed Reality** foi adicionado.

        ![Configurar o projeto do Unity](images/AzureLabs-Lab312-30.png)

8.  De volta *ao Build Configurações* projetos _C#_ do Unity não está mais es cinza; marque a caixa de seleção ao lado disso. 
9.  Feche a janela Configurações de Build.
10. Salve a cena e o projeto **(ARQUIVO > SALVAR CENA/ARQUIVO > SALVAR PROJETO**).


## <a name="chapter-5--camera-setup"></a>Capítulo 5 – Configuração da câmera

> [!IMPORTANT]
> Se você quiser ignorar o componente Configurar o *Unity* deste curso e continuar diretamente no código, baixe este [Azure-MR-312-Package.unitypackage , importe-o](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)para seu projeto como um Pacote Personalizado e continue no [Capítulo 7.](#chapter-8--create-the-botobjects-class) [](https://docs.unity3d.com/Manual/AssetPackages.html)

1.  No painel *Hierarquia ,* selecione a **Câmera Principal**. 
2.  Depois de selecionado, você poderá ver todos os componentes da **Câmera Principal** no *painel Inspetor*.

    1. O **objeto Câmera deve** ser nomeado Câmera **Principal** (observe a ortografia)
    2. A Marca da Câmera **Principal** deve ser definida como **MainCamera** (observe a ortografia)
    3. Certifique-se **de que a Posição da** Transformação está definida como **0, 0, 0**
    4. De **definir Limpar Sinalizadores** como **Cor Sólida**.
    5. Definir a **cor da** tela de fundo do componente Câmera **como Preto, Alfa 0 (Hex Code: #00000000)**

    ![Instalação da câmera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Capítulo 6 – Importar a biblioteca Newtonsoft

Para ajudá-lo a desselizar e serializar objetos recebidos e enviados ao Serviço de Bot, você precisa baixar a **biblioteca Newtonsoft.** Você encontrará uma versão compatível já organizada com a [estrutura de pastas correta do Unity aqui.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage) 

Para importar a biblioteca Newtonsoft para seu projeto, use o Pacote do Unity que veio com este curso.

1.  Adicione o *.unitypackage* ao Unity usando a **opção** de menu Pacote Personalizado do Pacote de  >    >   Importação de Ativos.

    ![Importar a biblioteca Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  Na caixa **Importar Pacote do Unity** que aparece, verifique se tudo em Plug-ins (e incluindo) **está** selecionado.

    ![Importar a biblioteca Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Clique no **botão Importar** para adicionar os itens ao seu projeto.

4.  Acesse a pasta **Newtonsoft** em **Plug-ins** na exibição do projeto e selecione o plug-in Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Com o plug-in Newtonsoft selecionado, verifique se Qualquer Plataforma está desmarcada e, em seguida, verifique se **WSAPlayer** também está desmarcado **e** clique em **Aplicar**.   Isso é apenas para confirmar se os arquivos estão configurados corretamente.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Marcar esses plug-ins os configura para serem usados apenas no Editor do Unity. Há um conjunto diferente deles na pasta WSA que será usado depois que o projeto for exportado do Unity.

6.  Em seguida, você precisa abrir a **pasta WSA,** dentro da **pasta Newtonsoft.** Você verá uma cópia do mesmo arquivo que acabou de configurar. Selecione o arquivo e, em seguida, no inspetor, verifique se
    -   **Qualquer plataforma** está **desmarcada** 
    -   **somente** **O WSAPlayer** está **marcado**
    -   **O processo de não** está **marcado**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Capítulo 7 – Criar o BotTag

1.  Crie um novo **objeto Tag** chamado **BotTag**. Selecione a Câmera Principal na cena. Clique no menu suspenso Marca no painel Inspetor. Clique em **Adicionar Marca**.

    ![Instalação da câmera](images/AzureLabs-Lab312-32.png)
 
2.  Clique no **+** símbolo. Nomeia a **nova Marca** como **BotTag,** *Salve*.

    ![Instalação da câmera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **Não aplique** o **BotTag** à Câmera Principal. Se você tiver feito isso acidentalmente, altere a marca da Câmera Principal de volta para *MainCamera.*

## <a name="chapter-8--create-the-botobjects-class"></a>Capítulo 8 – Criar a classe BotObjects

O primeiro script que você precisa criar é a classe **BotObjects,** que é uma classe vazia criada para que uma série de outros objetos de classe possa ser armazenada no mesmo script e acessada por outros scripts na cena.

A criação dessa classe é puramente uma opção de arquitetura, esses objetos podem ser hospedados no script de Bot que você criará posteriormente neste curso.

Para criar esta classe: 

1.  Clique com o botão direito *do mouse no painel Project e,* em **seguida, em Criar > Pasta**. Nomeia a **pasta Scripts**. 

    ![Criar pasta de scripts.](images/AzureLabs-Lab312-36.png)

2.  Clique duas vezes na pasta **Scripts** para abri-la. Em seguida, dentro dessa pasta, clique com o botão direito do mouse **e selecione Criar > Script C#.** Nomeia o script **BotObjects**. 

3.  Clique duas vezes no novo script **BotObjects** para abri-lo com **Visual Studio**.

4.  Exclua o conteúdo do script e substitua-o pelo seguinte código:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Salve as alterações no *Visual Studio* antes de retornar ao *Unity.*

## <a name="chapter-9--create-the-gazeinput-class"></a>Capítulo 9 – Criar a classe GazeInput

A próxima classe que você criará é a **classe GazeInput.** Essa classe é responsável por:

- Criar um cursor que representará o *olhar* do jogador.
- Detectar objetos atingidos pelo olhar do jogador e manter uma referência a objetos detectados.

Para criar esta classe: 

1.  Vá para a **pasta Scripts** criada anteriormente. 
2.  Clique com o botão direito do mouse dentro da pasta **Criar > Script C#.** Chame o script **GazeInput.** 
3.  Clique duas vezes no novo script **GazeInput** para abri-lo com **Visual Studio**.
4.  Insira a seguinte linha na parte superior do nome da classe:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Em seguida, adicione as seguintes variáveis dentro **da classe GazeInput,** acima do **método Start():**

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  O código **para o método Start()** deve ser adicionado. Isso será chamado quando a classe for inicializada:

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Implemente um método que insinue e configure o cursor de olhar: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Implemente os métodos que configurarão o Raycast da Câmera Principal e controlarão o objeto focalizado atual.

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Salve as alterações no *Visual Studio* antes de retornar ao *Unity.*

## <a name="chapter-10--create-the-bot-class"></a>Capítulo 10 – Criar a classe Bot

O script que você criará agora é chamado **de Bot**. Essa é a classe principal do seu aplicativo, que armazena: 

- Suas credenciais de Bot de Aplicativo Web
- O método que coleta os comandos de voz do usuário
- O método necessário para iniciar conversas com seu Bot de Aplicativo Web 
- O método necessário para enviar mensagens para seu Bot de Aplicativo Web 

Para enviar mensagens para o Serviço de Bot, a coroutine **SendMessageToBot()** criará uma atividade, que é um objeto reconhecido pelo Bot Framework como dados enviados pelo usuário. 
 
Para criar esta classe: 

1. Clique duas vezes na **pasta Scripts** para abri-la. 
2. Clique com o botão direito do mouse na **pasta Scripts,** clique **em Criar > Script C#.** Nomeia o script **Bot**. 
3. Clique duas vezes no novo script para abri-lo com Visual Studio.
4. Atualize os namespaces para que sejam iguais aos seguintes, na parte superior da classe **Bot:**

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Dentro da **classe Bot,** adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Insira sua Chave Secreta **do Bot na** variável **botSecret.** Você anotou sua Chave **Secreta do Bot** no início deste curso, no Capítulo **[2,](#chapter-2---create-the-azure-bot-service)etapa 10.**

7. O código **para o Awake()** e **Start()** agora precisa ser adicionado. 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Adicione os dois manipuladores que são chamados pelas bibliotecas de fala quando a captura de voz começa e termina. O *DictationRecognizer* interromperá automaticamente a captura da voz do usuário quando o usuário parar de falar.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. O manipulador a seguir coleta o resultado da entrada de voz do usuário e chama a corouttina responsável por enviar a mensagem para o Serviço de Bot de Aplicativo Web.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. A coroutina a seguir é chamada para iniciar uma conversa com o Bot. Você observará que, depois que a chamada de conversa for concluída, ela chamará **SendMessageToCoroutine()** passando uma série de parâmetros que definirão a atividade a ser enviada ao Serviço de Bot como uma mensagem vazia. Isso é feito para solicitar que o Serviço de Bot inicie o diálogo.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. A coroutina a seguir é chamada para criar a atividade a ser enviada ao Serviço de Bot. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. A seguinte corrotina é chamada para solicitar uma resposta depois de enviar uma atividade para o serviço de bot. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. O último método a ser adicionado a essa classe é necessário para exibir a mensagem na cena:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > Você pode ver um erro no console do editor do Unity, sobre a ausência da classe **SceneOrganiser** . Desconsidere esta mensagem, pois você criará essa classe posteriormente no tutorial.

14.  certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Capítulo 11 – criar a classe interações

A classe que você pretende criar agora é chamada de **interações**. essa classe é usada para detectar a HoloLens tocar na entrada do usuário. 

Se o usuário tocar enquanto examina o objeto *bot* na cena e o bot estiver pronto para escutar entradas de voz, o objeto bot mudará de cor para **vermelho** e começará a escutar as entradas de voz. 

Essa classe herda da classe **GazeInput** e, portanto, é capaz de fazer referência ao método **Start ()** e às variáveis dessa classe, denotada pelo uso de **base**. 
 
Para criar esta classe:

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > script C#**. Nomeie o script de **interações**. 
3.  Clique duas vezes no novo script para abri-lo com Visual Studio.
4.  Atualize os namespaces e a herança de classe para ser o mesmo que o seguinte, na parte superior da classe **interações** :

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Dentro da classe **interações** , adicione a seguinte variável:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Em seguida, adicione o método **Start ()** :

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  adicione o manipulador que será disparado quando o usuário executar o gesto de toque na frente da câmera de HoloLens

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Capítulo 12 – criar a classe SceneOrganiser

A última classe necessária neste laboratório é chamada de **SceneOrganiser**. Essa classe configurará a cena programaticamente, adicionando componentes e scripts à câmera principal e criando os objetos apropriados na cena.
 
Para criar esta classe:

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > script C#**. Nomeie o script **SceneOrganiser**. 
3.  Clique duas vezes no novo script para abri-lo com Visual Studio.
4.  Dentro da classe **SceneOrganiser** , adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  Em seguida, adicione os métodos **ativo ()** e **Iniciar ()** :

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Adicione o seguinte método, responsável por criar o objeto bot na cena e configurar os parâmetros e os componentes:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Adicione o seguinte método, responsável por criar o objeto de interface do usuário na cena, representando as respostas do bot:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.
9.  No editor do Unity, arraste o script **SceneOrganiser** da pasta scripts para a câmera principal. O componente de Organizer de cena agora deve aparecer no objeto de câmera principal, conforme mostrado na imagem abaixo.

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Capítulo 13 – antes de criar

Para executar um teste completo de seu aplicativo, você precisará Sideload-lo em seu HoloLens.
Antes de fazer isso, verifique se:

-   Todas as configurações mencionadas no [**capítulo 4**](#chapter-4--set-up-the-unity-project) são definidas corretamente. 
-   O script **SceneOrganiser** é anexado ao objeto da **câmera principal** . 
-   Na classe **bot** , verifique se você inseriu a **chave secreta de bot** na variável **botSecret** .

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Capítulo 14 – criar e Sideloadr para a HoloLens

Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.

1.  navegue até **Configurações de compilação**, **arquivo > build Configurações...**.
2.  na janela **build Configurações** , clique em **compilar**.

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab312-38.png)

3.  Se ainda não estiver, **projetos do Tick Unity C#**.
4.  Clique em **Compilar**. O Unity iniciará uma janela **Explorador de arquivos** , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora e nomeie-a como **aplicativo**. Em seguida, com a pasta de **aplicativo** selecionada, clique em **Selecionar pasta**. 
5.  O Unity começará a criar seu projeto na pasta do **aplicativo** . 
6.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

## <a name="chapter-15--deploy-to-hololens"></a>Capítulo 15 – implantar no HoloLens

Para implantar no HoloLens:

1.  você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que o HoloLens esteja no **modo de desenvolvedor**. Para fazer isso:

    1. enquanto estiver desgastando seu HoloLens, abra o **Configurações**.
    2. Vá para **rede & Internet > Wi-Fi > opções avançadas**
    3. Anote o endereço **IPv4** .
    4. em seguida, navegue de volta para **Configurações** e, em seguida, **atualize & > de segurança para desenvolvedores** 
    5. Defina o modo de desenvolvedor em.

2.  Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com **Visual Studio**.
3.  Na **configuração da solução** , selecione **depurar**.
4.  Na **plataforma da solução**, selecione **x86**, **computador remoto**. 

    ![Implante a solução de Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Vá para o **menu Compilar** e clique em **implantar solução**, para Sideload o aplicativo ao seu HoloLens.
6.  seu aplicativo agora deve aparecer na lista de aplicativos instalados na sua HoloLens, pronto para ser iniciado!

    > [!NOTE]
    > Para implantar em headsets de imersão, defina a **plataforma da solução** como *computador local* e defina a **configuração** a ser *depurada*, com *x86* como a **plataforma**. Em seguida, implante no computador local, usando o **menu Compilar**, selecionando *implantar solução*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Capítulo 16 – usando o aplicativo no HoloLens

- Depois de iniciar o aplicativo, você verá o bot como uma esfera azul na frente de você.

- Use o **gesto de toque** enquanto você estiver nuvens na esfera para iniciar uma conversa. 
 
- Aguarde até que a conversa seja iniciada (a interface do usuário exibirá uma mensagem quando ela ocorrer). Depois de receber a mensagem introdutória do bot, toque novamente no bot para que ele se transforme em vermelho e comece a escutar sua voz. 

- Depois de parar de conversar, seu aplicativo enviará sua mensagem para o bot e você receberá uma resposta que será exibida na interface do usuário. 

- Repita o processo para enviar mais mensagens para o bot (você precisa tocar sempre que desejar receber uma mensagem).

Essa conversa demonstra como o bot pode reter informações (seu nome), enquanto fornece também informações conhecidas (como os itens que estão em estoque).

#### <a name="some-questions-to-ask-the-bot"></a>Algumas perguntas a serem feitas ao bot:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Seu aplicativo Web App bot (v4) concluído

parabéns, você criou um aplicativo de realidade misturada que aproveita o Bot do aplicativo Web do Azure, Microsoft Bot Framework v4.

![Produto final](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

A estrutura de conversa neste laboratório é muito básica. Use o Microsoft LUIS para dar aos seus recursos de reconhecimento de linguagem natural de bot.

### <a name="exercise-2"></a>Exercício 2

Este exemplo não inclui o encerramento de uma conversa e a reinicialização de uma nova. Para que o recurso de bot seja concluído, tente implementar o fechamento na conversa.