---
title: HoloLens (1ª geração) e Azure 306 – Vídeo de streaming
description: conclua este curso para aprender a implementar Serviços de Mídia do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realidade mista, academia, unity, tutorial, api, serviços de mídia, vídeo de streaming, 360, imersão, vr, Windows 10, Visual Studio
ms.openlocfilehash: 3f3567c140c3162258475c28c2ef149039e3c40ed418ed2801ac8c40dda00a8f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224074"
---
# <a name="hololens-1st-gen-and-azure-306-streaming-video"></a>HoloLens (1º gen) e Azure 306: vídeo de Streaming

<br>

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br> 

![produto final – início do ](images/AzureLabs-Lab6-00.png)
 ![ produto final-início](images/AzureLabs-Lab6-01.png)

neste curso, você aprenderá como conectar seu Serviços de Mídia do Azure a uma experiência Windows Mixed Reality VR para permitir a reprodução de vídeo de streaming 360 em headsets de imersão. 

**Serviços de Mídia do Azure** são uma coleção de serviços que fornece serviços de streaming de vídeo de qualidade de difusão para alcançar públicos maiores nos dispositivos móveis mais populares de hoje. para obter mais informações, visite a [página Serviços de Mídia do Azure](https://azure.microsoft.com/services/media-services).

Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada, que poderá fazer o seguinte:

1. recuperar um vídeo de 360 graus de uma **Armazenamento do azure**, por meio do **serviço de mídia do azure**.

2. Exiba o vídeo de 360 graus recuperado em uma cena do Unity.

3. Navegue entre duas cenas, com dois vídeos diferentes.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com o Project do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 306: streaming de vídeo</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com o Unity e o C#. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no [artigo instalar as ferramentas](../../install-the-tools.md), embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- um PC de desenvolvimento, [compatível com Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para o desenvolvimento de headsets de imersão (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](../../install-the-tools.md#installation-checklist)
- [o SDK de Windows 10 mais recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017,4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- um [headset de Windows Mixed Reality de imersão (VR)](../../../discover/immersive-headset-hardware-details.md)
- Acesso à Internet para a instalação do Azure e recuperação de dados
- Vídeos de 2 360 graus no formato MP4 (você pode encontrar alguns vídeos isentos de royalties nesta [página de download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste seu headset de imersão de realidade misturada.

    > [!NOTE]
    > Você **não** precisará de controladores de animação para este curso. Se você precisar de suporte para configurar o headset de imersão, clique em [link sobre como configurar Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>capítulo 1-o Portal do azure: criando a conta de Armazenamento do azure

para usar o **serviço de Armazenamento do Azure**, será necessário criar e configurar uma **conta de Armazenamento** no portal do Azure.

1.  Faça logon no [portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  depois de fazer logon, clique em **Armazenamento contas** no menu à esquerda.

    ![configuração da conta do Armazenamento do Azure](images/AzureLabs-Lab6-02.png)

3.  na guia **contas Armazenamento** , clique em **adicionar**.

    ![configuração da conta do Armazenamento do Azure](images/AzureLabs-Lab6-03.png)

4.  Na guia **criar conta de armazenamento** :

    1.  Insira um **nome** para sua conta, lembre-se de que esse campo aceita apenas números e letras minúsculas.

    2.  Para **modelo de implantação,** selecione **Gerenciador de recursos**.

    3.  para **tipo de conta**, selecione **Armazenamento (uso geral v1)**.

    4.  Para **desempenho**, selecione **standard *.**

    5.  Para **replicação** , selecione **armazenamento com REDUNDÂNCIA local (LRS)**.

    6.  Deixe a **transferência segura necessária** como **desabilitada**.

    7.  Selecione uma **Assinatura**.

    8.  Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.

    9.  Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

5.  Você precisará confirmar que entendeu os termos e condições aplicados a este serviço.

    ![configuração da conta do Armazenamento do Azure](images/AzureLabs-Lab6-04.png)

6.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![configuração da conta do Armazenamento do Azure](images/AzureLabs-Lab6-05.png)

8.  Neste ponto, você não precisa seguir o recurso, simplesmente vá para o próximo capítulo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capítulo 2-o portal do Azure: criando o serviço de mídia

Para usar o serviço de mídia do Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo (onde o titular da conta precisa ser um administrador).

1.  No portal do Azure, clique em **criar um recurso** no canto superior esquerdo e procure **serviço de mídia,** pressione **Enter**. O recurso que você deseja atualmente tem um ícone rosa; Clique aqui para mostrar uma nova página.

    ![O portal do Azure](images/AzureLabs-Lab6-06.png)

2.  A nova página fornecerá uma descrição do **serviço de mídia**. Na parte inferior esquerda desse prompt, clique no botão **criar** para criar uma associação com esse serviço.

    ![O portal do Azure](images/AzureLabs-Lab6-07.png)

3.  Depois de clicar em **criar** um painel, aparecerá onde você precisa fornecer alguns detalhes sobre o novo serviço de mídia:

    1.  Insira o **nome da conta** desejada para esta instância de serviço.

    2.  Selecione uma **Assinatura**.

    3. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 
    
    > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar grupos de recursos do Azure](/azure/azure-resource-manager/resource-group-portal).

    4.  Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

    5.  para a seção **conta de Armazenamento** , clique na seção **selecionar...** e, em seguida, clique na conta de **Armazenamento** que você criou no último capítulo.

    6.  Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    7.  Clique em **Criar**.

        ![O portal do Azure](images/AzureLabs-Lab6-08.png)

4.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

5.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![O portal do Azure](images/AzureLabs-Lab6-09.png)

6.  Clique na notificação para explorar sua nova instância de serviço.

    ![O portal do Azure](images/AzureLabs-Lab6-10.png)

7.  Clique no **botão Ir para o** recurso na notificação para explorar sua nova instância de serviço.

8.  Na nova página Serviço de Mídia, no painel à esquerda, clique no **link** Ativos, que está quase na metade.

9.  Na próxima página, no canto superior esquerdo da página, clique em **Upload**.

    ![O portal do Azure](images/AzureLabs-Lab6-11.png)

10. Clique no **ícone Pasta** para procurar seus arquivos e selecione o primeiro Vídeo 360 que você gostaria de transmitir. 
    
    > Você pode seguir este [link para baixar um vídeo de exemplo](https://vimeo.com/214401712).

    ![O portal do Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Nomes de arquivo longos podem causar um problema com o codificador: portanto, para garantir que os vídeos não tenham problemas, considere reduzir o tamanho dos nomes de arquivo de vídeo.

11. A barra de progresso ficará verde quando o vídeo terminar de carregar.

    ![O portal do Azure](images/AzureLabs-Lab6-13.png)

12. Clique no texto acima (**yourservicename - Assets**) para retornar à **página Ativos.**

13. Você observará que o vídeo foi carregado com êxito. Clique nele.

    ![O portal do Azure](images/AzureLabs-Lab6-14.png)

14. A página para a que você será redirecionado mostrará informações detalhadas sobre o vídeo. Para poder usar o vídeo, você precisa codiá-lo clicando no botão Codificar no canto superior esquerdo da página. 

    ![O portal do Azure](images/AzureLabs-Lab6-15.png)

15. Um novo painel será exibido à direita, no qual você poderá definir opções de codificação para o arquivo. Deverão ser definidas as seguintes propriedades (algumas já estarão definidas por padrão):

    1.  **Nome do codificador de *mídia Media Encoder Standard***

    2.  **Codificação de conteúdo *predefinido Adaptável Com múltiplas taxas de bits MP4***

    3.  **Nome do *trabalho Media Encoder Standard processamento de Video1.mp4***

    4.  **Nome do ativo de *mídia deVideo1.mp4 -- Media Encoder Standard codificado***

        ![O portal do Azure](images/AzureLabs-Lab6-16.png)

16. Selecione o botão **Criar**.

17. Você observará uma barra com **o** trabalho de Codificação adicionado, clique nessa barra e um painel será exibido com o progresso da codificação exibido nele.

    ![O portal do Azure](images/AzureLabs-Lab6-17.png)

    ![O portal do Azure](images/AzureLabs-Lab6-18.png)

18. Aguarde até que o trabalho seja concluído. Quando terminar, sinta-se à vontade para fechar o painel com o 'X' no canto superior direito desse painel.

    ![O portal do Azure](images/AzureLabs-Lab6-19.png)

    ![O portal do Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > O tempo necessário depende do tamanho do arquivo do vídeo. Esse processo pode levar algum tempo.

19. Agora que a versão codificada do vídeo foi criada, você pode publicá-la para torná-la acessível. Para fazer isso, clique no link azul **Ativos** para voltar para a página de ativos.

    ![O portal do Azure](images/AzureLabs-Lab6-21.png)

20. Você verá o vídeo junto com outro, que é do Tipo de Ativo MP4 com taxa de **_bits multi bits._**

    ![O portal do Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Você pode observar que o novo ativo, juntamente com seu vídeo inicial, é Desconhecido e tem "0" bytes para seu **Tamanho,** basta atualizar sua janela para que ele seja atualizado.

21. Clique nesse novo ativo.

    ![O portal do Azure](images/AzureLabs-Lab6-23.png)

22. Você verá um painel semelhante ao que você usou antes, apenas este é um ativo diferente. Clique no **botão** Publicar localizado na parte superior central da página.

    ![O portal do Azure](images/AzureLabs-Lab6-24.png)

23. Você será solicitado a definir um **Localizador**, que é o ponto de entrada, como arquivo/s em seus Ativos. Para seu cenário, de acordo com as seguintes propriedades:

    1.  **Tipo de localizador**  >  **Progressivo.**

    2.  A **data** e **a hora** serão definidas para você, da data atual, para uma hora no futuro (100 anos nesse caso). Deixe como está ou altere-o para se adequar.

    > [!NOTE]
    > Para obter mais informações sobre Localizadores e o que você pode escolher, visite a [documentação Serviços de Mídia do Azure .](/azure/media-services/media-services-concepts)

24. Na parte inferior desse painel, clique no **botão** Adicionar.

    ![O portal do Azure](images/AzureLabs-Lab6-25.png)

25. Seu vídeo agora é publicado e pode ser transmitido usando seu ponto de extremidade. Mais abaixo, a página é uma **seção Arquivos.** É aqui que estarão as diferentes versões codificadas do vídeo. Selecione a resolução mais alta possível (na imagem abaixo está o arquivo 1920x960) e, em seguida, um painel à direita será exibido. Lá, você encontrará uma **URL de Download**. Copie esse **Ponto de** Extremidade, pois você o usará posteriormente em seu código.

    ![O portal do Azure](images/AzureLabs-Lab6-26.png)    

    ![O portal do Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > Você também pode pressionar o **botão** Reproduzir para reproduzir o vídeo e testá-lo.

26. Agora você precisa carregar o segundo vídeo que usará neste Laboratório. Siga as etapas acima, repetindo o mesmo processo para o segundo vídeo. Certifique-se de copiar o **segundo ponto de extremidade** também. Use o [link a seguir para baixar um segundo vídeo](https://vimeo.com/214402865).

27. Depois que os dois vídeos foram publicados, você estará pronto para passar para o próximo Capítulo.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3 – Configurando o Project

A seguir está uma configuração típica para o desenvolvimento com a Realidade Misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra **o Unity** e clique em **Novo.** 

    ![O portal do Azure](images/AzureLabs-Lab6-28.png)

2.  Agora você precisará fornecer um nome de Project Unity, insira **MR \_ 360VideoStreaming.**. Certifique-se de que o tipo de projeto está definido **como 3D.** De definir o Local como em algum lugar apropriado para você (lembre-se de que mais próximo dos diretórios raiz é melhor). Em seguida, clique **em Criar projeto**.

    ![O portal do Azure](images/AzureLabs-Lab6-29.png)

3.  Com o Unity aberto, vale a pena verificar se o **Editor de Script** padrão está definido como **Visual Studio.** Vá para **_Editar_ *Preferências*** e, em seguida, na nova janela, navegue até **Ferramentas Externas.** Altere **Editor de Script** Externo para Visual Studio **2017.** Feche a **janela Preferências.**

    ![O portal do Azure](images/AzureLabs-Lab6-30.png)

4.  Em seguida, vá para Criar ***arquivo Configurações*** e alternar a plataforma para **Plataforma Universal** Windows , clicando no botão **Alternar Plataforma.**

5.  Além disso, certifique-se de que:

    1. **O Dispositivo de** Destino é definido **como Qualquer Dispositivo.**
    
    2.  **O tipo de** build é definido como **D3D.**

    3.  **O SDK** está definido como **Mais recente instalado.**

    4.  **Visual Studio versão é** definida como **Mais recente instalada.**

    5.  **Build e Executar** são definidos como **Computador Local.**

    6.  Não se preocupe com a configuração **de Cenas** agora, pois você as configurará mais tarde.

    7.  As configurações restantes devem ser deixadas como padrão por enquanto.

        ![Configurando o Project](images/AzureLabs-Lab6-31.png)

6.  Na janela **Criar Configurações,** clique no botão **Player Configurações,** isso abrirá o painel relacionado no espaço em que o **Inspetor** está localizado. 

7. Neste painel, algumas configurações precisam ser verificadas:

    1.  Na guia **Outros Configurações:**

        1.  **A versão do** **Runtime de** Script deve ser **estável** (equivalente ao .NET 3.5).

        2. **Back-end de script** deve ser **.NET.**

        3. **O Nível de Compatibilidade da API** deve **ser .NET 4.6.**

            ![Configurando o Project](images/AzureLabs-Lab6-32.png)

    2.  Mais abaixo no painel, no **XR Configurações** (encontrado abaixo de **Publicar Configurações**), marque Realidade **Virtual** Com Suporte , certifique-se de que o **SDK** Windows Mixed Reality seja adicionado.

        ![Configurando o Project](images/AzureLabs-Lab6-33.png)

    3.  na guia **publicação Configurações** , em **recursos**, marque:

        - **InternetClient**

            ![Configurando o Project do Unity](images/AzureLabs-Lab6-34.png)

8.  depois de fazer essas alterações, feche a janela **Build Configurações** .

9.  salve seu Project **arquivo* * salvar Project * *.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capítulo 4-importando o pacote do InsideOutSphere Unity

> [!IMPORTANT]
> Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar esse [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no **capítulo 5**. Você ainda precisará criar um Project do Unity.

Para este curso, você precisará baixar um pacote de ativos de Unity chamado [**InsideOutSphere. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).

Como importar o **unitypackage**:

1.  Com o painel do Unity na frente, clique em **ativos** no menu na parte superior da tela e, em seguida, clique em **Importar pacote > pacote personalizado**.

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-35.png)

2.  Use o seletor de arquivos para selecionar o pacote **InsideOutSphere. unitypackage** e clique em **abrir**. Uma lista de componentes para este ativo será exibida para você. Confirme a importação clicando em **importar**.

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-36.png)

3.  Depois de concluir a importação, você notará três novas pastas, **materiais**, **modelos** e **pré-fabricados**, foram adicionados à sua pasta de **ativos** . Esse tipo de estrutura de pastas é típico para um projeto do Unity.

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-37.png)

    1.  Abra a pasta **modelos** e você verá que o modelo **InsideOutSphere** foi importado.

    2.  Na pasta **materiais** , você encontrará o material de **InsideOutSpheres**  *LAMBERT1*, junto com um material chamado *ButtonMaterial*, que é usado pelo GazeButton, que será exibido em breve.

    3.  A pasta **pré-fabricados** contém o **InsideOutSphere** pré-fabricado que contém o modelo **InsideOutSphere**  e o *GazeButton*.

    4.  **Nenhum código está incluído**, você escreverá o código seguindo este curso.


4.  Na **hierarquia**, selecione o objeto de **câmera principal** e atualize os seguintes componentes:

    1.  **Transformar**

        1.  Posição = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotation = **X**: 0, **Y**: 0, **Z**: 0.

        3. Escala **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Câmera**

        1. **Limpar sinalizadores**: cor sólida.

        2.  **Planos de recorte**: perto de: 0,1, longe: 6.

            ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-38.png)

5.  Navegue até a pasta **pré-fabricado** e, em seguida, arraste o **InsideOutSphere** pré-fabricado para o painel **hierarquia** .

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-39.png)

6.  Expanda o objeto **InsideOutSphere** dentro da **hierarquia** clicando na pequena seta ao lado dele. Você verá um objeto **filho** abaixo dele chamado **GazeButton**. Isso será usado para alterar cenas e vídeos assim.

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-40.png)

7.  Na janela do Inspetor, clique no componente de transformação do **InsideOutSphere**, verifique se as seguintes propriedades estão definidas:

    |            |    TRANSFORMAÇÃO-POSIÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRANSFORMAÇÃO-ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORMAR EM ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-41.png)

8.  Clique no objeto filho **GazeButton** e defina sua **transformação** da seguinte maneira:

    |            |    TRANSFORMAÇÃO-POSIÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3,6|          **Y** 1,3        |  **Z** 0  |

    |            |    TRANSFORMAÇÃO-ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMAR EM ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capítulo 5 – criar a classe VideoController

A classe **VideoController** hospeda os dois pontos de extremidade de vídeo que serão usados para transmitir o conteúdo do serviço de mídia do Azure.

Para criar esta classe:

1.  clique com o botão direito do mouse na **pasta ativo**, localizada no painel de **Project** e clique em **criar > pasta**. Nomeie a pasta **scripts**.

    ![Criar a classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Criar a classe VideoController](images/AzureLabs-Lab6-44.png)

2.  Clique duas vezes na pasta **scripts** para abri-la.

3.  Clique com o botão direito do mouse dentro da pasta e clique em **criar > \# script C**. Nomeie o script **VideoController**.

    ![Criar a classe VideoController](images/AzureLabs-Lab6-45.png)

4.  clique duas vezes no novo script **VideoController** para abri-lo com **Visual Studio 2017.**

    ![Criar a classe VideoController](images/AzureLabs-Lab6-46.png)

5.  Atualize os namespaces na parte superior do arquivo de código da seguinte maneira:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Insira as variáveis a seguir na classe **VideoController** , juntamente com o método **ativo ()** :

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  Agora é o momento de inserir os pontos de extremidade dos vídeos do serviço de mídia do Azure:

    1.  O primeiro na variável *video1endpoint* .
    
    2.  O segundo na variável *video2endpoint* .

    > [!WARNING]
    > Há um problema conhecido com o uso de *https* no Unity, com a versão 2017.4.1 F1. Se os vídeos fornecerem um erro na reprodução, tente usar "http" em seu lugar.

8.  Em seguida, o método **Start ()** precisa ser editado. Esse método será disparado sempre que o usuário alternar a cena (consequentemente, alternando o vídeo) examinando o botão olhar.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Após o método **Start ()** , insira o método **PlayVideo ()** *IEnumerator* , que será usado para iniciar vídeos diretamente (portanto, nenhum stutter é visto).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. O último método necessário para essa classe é o método **ChangeScene ()** , que será usado para alternar entre cenas.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > O método **ChangeScene ()** usa um recurso C útil \# chamado *operador condicional*. Isso permite que as condições sejam verificadas e, em seguida, os valores retornados com base no resultado da verificação, tudo dentro de uma única instrução. Siga este [link para saber mais sobre o operador condicional](/dotnet/csharp/language-reference/operators/conditional-operator).

11. salve as alterações em Visual Studio antes de retornar ao Unity.

12. De volta ao editor do Unity, clique e arraste a classe **VideoController** [de] {. Underline} a pasta **scripts** para o objeto da **câmera principal** no painel **hierarquia** .

13. Clique na **câmera principal** e examine o **painel Inspetor**. Você observará que, dentro do componente de script recém-adicionado, há um campo com um valor vazio. Este é um campo de referência, que tem como alvo as variáveis públicas no seu código.

14. Arraste o objeto **InsideOutSphere** do **painel hierarquia** para o slot de **esfera** , conforme mostrado na imagem abaixo.

    ![Criar a classe VideoController ](images/AzureLabs-Lab6-47.png)
     ![ criar a classe VideoController](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capítulo 6 – Criar a classe Gaze

Essa classe é responsável por criar um **Raycast** que será projetado para frente da Câmera Principal **para** detectar qual objeto o usuário está olhando. Nesse caso, o **Raycast** precisará identificar se o usuário está olhando para o objeto **GazeButton** na cena e disparar um comportamento.

Para criar esta Classe:

1.  Vá para a **pasta Scripts** criada anteriormente.

2.  Clique com o botão direito do **mouse no painel Project,** **Criar* \# *Script C**. Nomeia o script **como Gaze.**

3.  Clique duas vezes no novo script ***Gaze** _ para abri-lo com _ *Visual Studio 2017.**

4.  Verifique se o namespace a seguir está na parte superior do script e remova qualquer outro:

    ```csharp
    using UnityEngine;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da **classe Gaze:**

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  O código **para os métodos Awake()** e **Start()** agora precisa ser adicionado.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Adicione o seguinte código ao método **Update()** para projetar um Raycast e detectar o acerto de destino:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Salve suas alterações no Visual Studio antes de retornar ao Unity.

9.  Clique e arraste **a classe Gaze** da pasta Scripts para o objeto Câmera Principal no Painel **de** Hierarquia.

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capítulo 7 – Configurar as duas cenas do Unity

A finalidade deste Capítulo é configurar as duas cenas, cada uma hospedando um vídeo para transmitir. Você duplica a cena que já criou, de modo que não precise defini-la novamente, embora edite a nova cena, de modo que o objeto *GazeButton* está em um local diferente e tenha uma aparência diferente. Isso é para mostrar como alterar entre cenas.

1.  Faça isso indo para **Arquivo > Salvar Cena como...**. Uma janela salvar será exibida. Clique no **botão Nova** pasta.

    ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-49.png)

2.  Nomeia a pasta **Cenas**.

3.  A **janela Salvar Cena** ainda estará aberta. Abra a pasta **Cenas recém-criada.**

4.  No campo **Nome do arquivo:** texto, digite **VideoScene1** e pressione **Salvar**.

5.  De volta ao Unity, abra a **pasta Cenas** e clique com o botão esquerdo do mouse no **arquivo VideoScene1.** Use o teclado e pressione **Ctrl + D** para duplicar essa cena

    > [!TIP]
    > O **comando Duplicar** também pode ser executado navegando até **Editar > Duplicado.**

6.  O Unity incrementará automaticamente o número de nomes de cena, mas verificará mesmo assim, para garantir que ele corresponde ao código inserido anteriormente.

    >  Você deve ter **VideoScene1** e **VideoScene2**.

7.  Com suas duas cenas, vá para **Arquivo > Build Configurações**. Com a **janela Criar Configurações** aberta, arraste suas cenas para a seção Cenas no **Build.**

    ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Você pode selecionar ambas as cenas da pasta **Cenas** mantendo o botão **Ctrl** pressionado e clicando com o botão esquerdo em cada cena e, por fim, arrastar ambas.

8.  Feche a **janela Configurações** build e clique duas vezes **em VideoScene2**.

9.  Com a segunda cena aberta, clique no objeto filho **GazeButton** de **InsideOutSphere** e de definido sua Transformação da seguinte maneira:

    |            |    TRANSFORM – POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    TRANSFORMAÇÃO – ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMAÇÃO – ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Com o **filho GazeButton** ainda selecionado, veja o **Inspetor** e o Filtro **de Malha**. Clique no pequeno destino ao lado do **campo Referência de** Malha:

    ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-51.png)

11. Uma **janela pop-up** Selecionar Malha será exibida. Clique duas vezes **na malha** Cubo na lista de **Ativos**.

    ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-52.png)

12. O **Filtro de Malha** será atualizado e agora será um **Cubo**. Agora, clique no ícone **engrenagem** ao lado de **Colisor de Esfera** e clique em **Remover** Componente para excluir o colisor deste objeto.

    ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-53.png)

13. Com o **GazeButton** ainda selecionado, clique **no botão** Adicionar Componente na parte inferior do **Inspetor.** No campo de pesquisa, a caixa **de** tipo e o **Colisor** de Caixa serão uma opção – clique nessa opção para adicionar um **Colisor** de Caixa ao objeto **GazeButton.**

    ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-54.png)

14. O **GazeButton** agora está parcialmente atualizado, para parecer diferente, no entanto, agora você criará um **novo Material**, para que ele pareça completamente diferente e seja mais fácil de reconhecer como um objeto diferente do objeto na primeira cena.

15. Navegue até **a pasta** Materiais, dentro do painel **Project .** Duplique **o Material buttonMaterial** (pressione **Ctrl** D no teclado ou clique com o botão esquerdo do mouse no Material e, na opção de menu Editar  +   arquivo, selecione **Duplicar**).  

    ![Capítulo 7 – Configurar as duas cenas do Unity ](images/AzureLabs-Lab6-55.png)
     ![ Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-56.png)

16. Selecione o novo **Material ButtonMaterial** (aqui chamado **ButtonMaterial 1**) e, dentro do **Inspetor,** clique na **janela Cor de Albedo.** Um pop-up será exibido, em que você pode selecionar outra cor (escolha o que quiser) e, em seguida, feche o pop-up. O Material será sua própria instância e diferente do original.

    ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-57.png)

17. Arraste o **novo Material** para o filho **GazeButton** para atualizar completamente sua aparência, de modo que ele seja facilmente distinguível do botão das primeiras cenas.

    ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-58.png)

18. Neste ponto, você pode testar o projeto no Editor antes de criar o projeto UWP.

    -  Pressione o **botão Reproduzir** no **Editor e** use o headset.

        ![Capítulo 7 – Configurar as duas cenas do Unity](images/AzureLabs-Lab6-59.png)

19. Veja os dois objetos **GazeButton** para alternar entre o primeiro e o segundo vídeo.

## <a name="chapter-8---build-the-uwp-solution"></a>Capítulo 8 – Criar a solução UWP

Depois de garantir que o editor não tenha erros, você estará pronto para Criar.

Para criar:

1.  Salve a cena atual clicando em Arquivo **> Salvar**.

2.  Marque a caixa chamada **Projetos C \# do Unity** (isso é importante porque permitirá que você edite as classes após a conclusão do build).

3.  Vá para **Arquivo > Build Configurações**, clique em **Build**.

4.  Você será solicitado a selecionar a pasta na qual deseja criar a Solução.

5.  Crie uma **pasta BUILDS** e, dentro dessa pasta, crie outra pasta com um nome apropriado de sua escolha.

6.  Clique em sua nova pasta **e,** em seguida, clique em Selecionar Pasta , portanto, para escolher essa pasta, para iniciar o build nesse local.

    ![Capítulo 8 – Criar a solução UWP ](images/AzureLabs-Lab6-60.png)
     ![ Capítulo 8 – Criar a solução UWP](images/AzureLabs-Lab6-61.png)

7.  Depois que o Unity terminar de criar (pode levar algum **tempo),** ele abrirá uma Explorador de Arquivos no local do build.

## <a name="chapter-9---deploy-on-local-machine"></a>Capítulo 9 – Implantar no computador local

Depois que o build tiver sido concluído, **Explorador de Arquivos** janela de Explorador de Arquivos será exibida no local do build. Abra a Pasta que você nomeou e criou e clique duas vezes no arquivo de solução (.sln) dentro dessa pasta para abrir sua solução com Visual Studio 2017.

A única coisa que resta fazer é implantar seu aplicativo no computador (ou *computador local).*

Para implantar no Computador Local:

1.  No **Visual Studio 2017,** abra o arquivo de solução que acabou de ser criado.

2.  Na Plataforma **de Solução**, selecione **x86, Computador Local.**

3.  Na **Configuração da Solução,** selecione **Depurar**.

    ![Capítulo 9 – Implantar no computador local](images/AzureLabs-Lab6-62.png)

4.  Agora você precisará restaurar todos os pacotes para sua solução. Clique com o botão direito do mouse em **sua Solução** e clique em Restaurar NuGet Pacotes **para Solução...**

    > [!NOTE] 
    > Isso é feito porque os pacotes que o Unity criou precisam ser direcionados para trabalhar com suas referências de máquinas locais.

5.  Vá para **o menu Criar** e clique em Implantar **Solução** para fazer sideload do aplicativo em seu computador. Visual Studio primeiro criará e implantará seu aplicativo.

6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para serem lançados.

    ![Capítulo 9 – Implantar no computador local](images/AzureLabs-Lab6-63.png)

Ao executar o aplicativo de Realidade Misturada, você estará dentro do **modelo InsideOutSphere** que você usou em seu aplicativo. Essa esfera será onde o vídeo será transmitido, fornecendo uma exibição de 360 graus, do vídeo de entrada (que foi gravado para esse tipo de perspectiva). Não se estranhe se o vídeo levar alguns segundos para ser carregado, seu aplicativo está sujeito à velocidade da Internet disponível, pois o vídeo precisa ser buscado e baixado, portanto, para transmitir para seu aplicativo.
Quando estiver pronto, altere as cenas e abra seu segundo vídeo, olhando para a esfera vermelha! Em seguida, sinta-se à vontade para voltar, usando o cubo azul na segunda cena!

## <a name="your-finished-azure-media-service-application"></a>Seu aplicativo do Serviço de Mídia do Azure concluído
 
Parabéns, você criou um aplicativo de realidade misturada que aproveita o Serviço de Mídia do Azure para transmitir 360 vídeos.

![resultado do laboratório](images/AzureLabs-Lab6-00.png)

![resultado do laboratório](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

**Exercício 1**

É totalmente possível usar apenas uma única cena para alterar vídeos neste tutorial. Experimente seu aplicativo e faça isso em uma única cena! Talvez até mesmo adicione outro vídeo à combinação.

**Exercício 2**

Experimente o Azure e o Unity e tente implementar a capacidade do aplicativo de selecionar automaticamente um vídeo com um tamanho de arquivo diferente, dependendo da força de uma conexão com a Internet.