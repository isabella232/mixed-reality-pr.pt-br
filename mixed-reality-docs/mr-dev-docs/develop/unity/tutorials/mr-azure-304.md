---
title: HoloLens (1ª geração) e Azure 304 – Reconhecimento facial
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realidade mista, academia, unity, tutorial, api, reconhecimento facial, hololens, imersão, vr, Windows 10, Visual Studio
ms.openlocfilehash: 2547b61669884c524fdd605240322dc9d568039b5a202d0a411317b0e83bd547
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219422"
---
# <a name="hololens-1st-gen-and-azure-304-face-recognition"></a>HoloLens (1ª gen) e Azure 304: reconhecimento facial

<br>

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

![resultado da conclusão deste curso](images/AzureLabs-Lab4-00.png)

Neste curso, você aprenderá a adicionar recursos de reconhecimento facial a um aplicativo de realidade misturada, usando os serviços cognitivas do Azure, com o Microsoft API de Detecção Facial.

O *Azure API de detecção facial* é um serviço da Microsoft, que fornece aos desenvolvedores os algoritmos de face mais avançados, tudo na nuvem. O *API de detecção facial* tem duas funções principais: detecção facial com atributos e reconhecimento facial. Isso permite que os desenvolvedores simplesmente definam um conjunto de grupos para rostos e, em seguida, enviem imagens de consulta para o serviço posteriormente, para determinar a quem uma face pertence. Para obter mais informações, visite a [página de reconhecimento de face do Azure](https://azure.microsoft.com/services/cognitive-services/face/).

após concluir este curso, você terá uma realidade misturada HoloLens aplicativo, que poderá fazer o seguinte:

1. Use um **gesto de toque** para iniciar a captura de uma imagem usando a câmera HoloLens da placa. 
2. Envie a imagem capturada para o serviço de *API de detecção facial do Azure* .
3. Receba os resultados do algoritmo *API de detecção facial* .
4. Use uma interface do usuário simples para exibir o nome de pessoas correspondentes.

Isso ensinará a você como obter os resultados do serviço de API de Detecção Facial em seu aplicativo de realidade mista com base no Unity.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com o Project do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 304: reconhecimento facial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> embora este curso se concentre principalmente em HoloLens, você também pode aplicar o que aprende neste curso para que Windows Mixed Reality headsets de imersão (VR). Como os headsets de imersão (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu PC. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets de imersão (VR).

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com o Unity e o C#. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](../../install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- um PC de desenvolvimento, [compatível com Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para o desenvolvimento de headsets de imersão (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](../../install-the-tools.md)
- [o SDK de Windows 10 mais recente](../../install-the-tools.md)
- [Unity 2017,4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- um [headset de Windows Mixed Reality de imersão (VR)](../../../discover/immersive-headset-hardware-details.md) ou [Microsoft HoloLens](/hololens/hololens1-hardware) com o modo de desenvolvedor habilitado
- Uma câmera conectada ao seu PC (para desenvolvimento de headsets de imersão)
- Acesso à Internet para a instalação do Azure e recuperação de API de Detecção Facial

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste sua HoloLens. se você precisar de suporte para configurar seu HoloLens, [visite o artigo HoloLens instalação](/hololens/hololens-setup). 
3.  é uma boa ideia executar a calibragem e o ajuste do Sensor ao começar a desenvolver um novo aplicativo de HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

para obter ajuda sobre a calibração, siga este [link para o artigo HoloLens calibration](/hololens/hololens-calibration#hololens-2).

para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste HoloLens sensor](/hololens/hololens-updates).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1-o portal do Azure

Para usar o serviço de *API de detecção facial* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.

1.  Primeiro, faça logon no [portal do Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *API de detecção facial*, pressione **Enter**.

    ![Pesquisar API de detecção facial](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

3.  A nova página fornecerá uma descrição do serviço *API de detecção facial* . Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.

    ![informações da API facial](images/AzureLabs-Lab4-02.png)

4.  Depois de clicar em **criar**:

    1. Insira o nome desejado para esta instância de serviço.

    2. Selecione uma assinatura.

    3. Selecione o tipo de preço apropriado para você, se esta for a primeira vez que criar um *serviço de API de detecção facial*, uma camada gratuita (chamada F0) deverá estar disponível para você.

    4. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. O aplicativo UWP, **criador de pessoas**, que você usa mais tarde, requer o uso de ' oeste dos EUA ' para o local.

    6. Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    7. Selecione **criar *.**

        ![Criar serviço de API facial](images/AzureLabs-Lab4-03.png)

5.  Depois de clicar em **criar *,** você precisará aguardar a criação do serviço; isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![notificação de criação de serviço](images/AzureLabs-Lab4-04.png)

7.  Clique nas notificações para explorar sua nova instância de serviço.

    ![ir para notificação de recurso](images/AzureLabs-Lab4-05.png)

8.  Quando estiver pronto, clique no botão **ir para o recurso** na notificação para explorar sua nova instância de serviço.

    ![acessar chaves de API de face](images/AzureLabs-Lab4-06.png)

9.  Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da assinatura ' Key ' de seu serviço. Na página *início rápido* , do seu serviço de *API de detecção facial* , o primeiro ponto é o número 1, para *captar suas chaves.*

10. Na página *serviço* , selecione o hiperlink **teclas** azuis (se estiver na página início rápido) ou o link **chaves** no menu de navegação serviços (à esquerda, indicado pelo ícone "chave"), para revelar suas chaves.

    > [!NOTE] 
    > Anote qualquer uma das chaves e proteja-a, pois você precisará dela mais tarde.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capítulo 2-usando o aplicativo UWP do ' criador de pessoas '

Certifique-se de baixar o aplicativo UWP pré-criado chamado [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Este aplicativo não é o produto final para este curso, apenas uma ferramenta para ajudá-lo a criar suas entradas do Azure, com as quais o projeto posterior dependerá.

O **criador** de pessoas permite que você crie entradas do Azure, que estão associadas a pessoas e grupos de pessoas. O aplicativo coloca todas as informações necessárias em um formato que, posteriormente, pode ser usado pelo FaceAPI para reconhecer as faces de pessoas que você adicionou. 

> FUNDAMENTAL O **criador de pessoas** usa uma limitação básica para ajudar a garantir que você não exceda o número de chamadas de serviço por minuto para a camada de **assinatura gratuita**. O texto verde na parte superior mudará para vermelho e será atualizado como ' ativo ' quando a limitação estiver acontecendo; Se esse for o caso, basta aguardar o aplicativo (ele aguardará até que possa continuar acessando o serviço de face, atualizando como ' IN-ACTIVE ' quando você puder usá-lo novamente).

Esse aplicativo usa as bibliotecas *Microsoft. ProjectOxford. facial* , que permitirão que você faça uso completo da API de detecção facial. essa biblioteca está disponível gratuitamente como um pacote NuGet. Para obter mais informações sobre isso e APIs semelhantes, [visite o artigo de referência de API](/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Essas são apenas as etapas necessárias, as instruções sobre como fazer essas coisas estão mais abaixo do documento. O aplicativo **Person Maker** lhe permitirá:
>
> - Crie um *grupo de pessoas*, que é um grupo composto por várias pessoas que você deseja associar a ela. Com sua conta do Azure, você pode hospedar vários grupos de pessoas.
>
> - Crie uma *pessoa*, que é um membro de um grupo de pessoas. Cada pessoa tem várias imagens de *face* associadas a ela.
>
> -  Atribua *imagens de face* a uma *pessoa*, para permitir que o serviço de API de detecção facial do Azure reconheça uma *pessoa* pela *face* correspondente.
>
> -  *Treine* seu *serviço de API de detecção facial do Azure*.

Lembre-se de que, para treinar esse aplicativo para reconhecer pessoas, você precisará de dez (10) fotos de fechamento de cada pessoa que deseja adicionar ao seu grupo de pessoas. o aplicativo Windows 10 Cam pode ajudá-lo a fazer isso. Você deve garantir que cada foto esteja clara (Evite desfocar, obscurecer ou estar muito longe, do assunto), ter a foto no formato de arquivo jpg ou png, com o tamanho do arquivo de imagem que não seja maior que **4 MB** e não seja menor que **1 KB**.

> [!NOTE]
> se você estiver seguindo este tutorial, não use sua própria face para treinamento, como quando você coloca o HoloLens em, você não pode examinar por conta própria. Use a face de um colega ou colega de aluno.

**Criador de pessoas** em execução:

1.  Abra a pasta **PersonMaker** e clique duas vezes na *solução PersonMaker* para abri-la com *Visual Studio*.

2.  Depois que a *solução PersonMaker* estiver aberta, verifique se:

    1. A *configuração da solução* está definida como **depurar**.

    2. A *plataforma da solução* está definida como **x86**

    3. A *plataforma de destino* é a **máquina local**.

    4.  talvez você também precise *restaurar NuGet pacotes* (clique com o botão direito do mouse na *solução* e selecione **restaurar pacotes de NuGet**).

3.  Clique em *computador local* e o aplicativo será iniciado. Lembre-se de que, em telas menores, todo o conteúdo pode não estar visível, embora você possa rolar mais para baixo para exibi-lo.

    ![interface do usuário do criador de pessoas](images/AzureLabs-Lab4-07.png)

4.  Insira sua **chave de autenticação do Azure**, que você deve ter, do seu serviço de *API de detecção facial* no Azure.

5.  Inserir:

    1. A *ID* que você deseja atribuir ao *grupo de pessoas*. A ID deve estar em minúsculas, sem espaços. Anote essa ID, pois ela será necessária mais tarde no seu projeto do Unity.
    2. O *nome* que você deseja atribuir ao *grupo de pessoas* (pode ter espaços).


6.  Pressione o botão **Criar grupo de pessoas** . Uma mensagem de confirmação deve aparecer abaixo do botão.

> [!NOTE]
> Se você tiver um erro de ' acesso negado ', verifique o local definido para o serviço do Azure. Conforme mencionado acima, este aplicativo foi projetado para o "oeste dos EUA".

> [!IMPORTANT]
> Você observará que também pode clicar no botão **buscar um grupo conhecido** : isso ocorrerá se você já tiver criado um grupo de pessoas e quiser usá-lo, em vez de criar um novo. Lembre-se de que, se você clicar em *criar um grupo de pessoas* com um grupo conhecido, isso também obterá um grupo.

7.  Insira o *nome* da *pessoa* que você deseja criar.

    1. Clique no botão **criar pessoa** .

    2. Uma mensagem de confirmação deve aparecer abaixo do botão.

    3. Se desejar excluir uma pessoa que você criou anteriormente, você poderá escrever o nome na caixa de texto e pressionar **excluir pessoa**

8.  Verifique se você sabe o local de dez (dez) fotos da pessoa que deseja adicionar ao seu grupo.

9.  pressione **criar e abrir pasta** para abrir Windows Explorer na pasta associada à pessoa. Adicione as dez (10) imagens na pasta. Eles devem ser do formato de arquivo *jpg* ou *png* .

10. Clique em **Enviar para o Azure**. Um contador mostrará o estado do envio, seguido por uma mensagem quando for concluído.

11. Depois que o contador for concluído e uma mensagem de confirmação for exibida, clique em **treinar** para treinar o serviço.

Depois que o processo for concluído, você estará pronto para passar para o Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o *Unity* e clique em **novo**. 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab4-08.png)

2.  agora, você precisará fornecer um nome de Project do Unity. Inserir **MR_FaceRecognition**. Verifique se o tipo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab4-09.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**. altere o **Editor de Script externo** para **Visual Studio 2017**. Feche a janela **preferências** .

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab4-10.png)

4.  em seguida, vá para **arquivo > Build Configurações** e alterne a plataforma para **Plataforma Universal do Windows** clicando no botão **alternar plataforma** .

    ![crie Configurações janela, alterne a plataforma para UWP.](images/AzureLabs-Lab4-11.png)

5.  vá para **arquivo > Build Configurações** e verifique se:

    1. O **dispositivo de destino** está definido como **HoloLens**

        > Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.

    2. O **tipo de compilação** está definido como **D3D**
    3. O **SDK** está definido para o **mais recente instalado**
    4. **Visual Studio versão** está definida para o **mais recente instalado**
    5. **Compilar e executar** é definido como **computador local**
    6. Salve a cena e adicione-a à compilação. 

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab4-12.png)

        2. Selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab4-13.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo **nome do arquivo**:, digite **FaceRecScene** e pressione **salvar**.

            ![Dê um nome à nova cena.](images/AzureLabs-Lab4-14.png)

    7. as configurações restantes, no *Build Configurações*, devem ser deixadas como padrão por enquanto.

6. na janela *criar Configurações* , clique no botão **Configurações do Player** , isso abrirá o painel relacionado no espaço onde o *inspetor* está localizado. 

    ![Abra as configurações do Player.](images/AzureLabs-Lab4-15.png)

7. Nesse painel, algumas configurações precisam ser verificadas:

    1. na guia **outros Configurações** :

        1. A **versão de tempo de execução** de **script** deve ser **experimental** (.NET 4,6 equivalente). Alterar isso irá disparar a necessidade de reiniciar o editor.
        2. O **back-end de script** deve ser **.net**
        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Atualize outras configurações.](images/AzureLabs-Lab4-16.png)
      
    2. na guia **publicação Configurações** , em **recursos**, marque:

        - **InternetClient**
        - **Webcam**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab4-17.png)

    3. mais adiante no painel, em **XR Configurações** (encontrado abaixo **Configurações de publicação**), **há suporte para a realidade Virtual** de tique, verifique se o **SDK do Windows Mixed Reality** foi adicionado.

        ![atualize o Configurações X R.](images/AzureLabs-Lab4-18.png)

8.  de volta ao *Configurações de Build*, os projetos do **Unity C#** não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste. 
9.  Feche a janela Configurações de Build.
10. salve sua cena e Project (**arquivo > salvar cena/arquivo > salvar projeto**).

## <a name="chapter-4---main-camera-setup"></a>Capítulo 4-configuração principal da câmera

> [!IMPORTANT]
> Se você quiser ignorar o componente de *configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para [baixar esse. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html). Lembre-se de que esse pacote também inclui a importação da *dll Newtonsoft*, abordada no [capítulo 5](#chapter-5--import-the-newtonsoftjson-library). Com isso importado, você pode continuar do [Capítulo 6.](#chapter-6---create-the-faceanalysis-class)

1.  No Painel *hierarquia,* selecione a **Câmera Principal.**

2.  Depois de selecionado, você poderá ver todos os componentes da **Câmera Principal** no Painel *inspetor.*

    1. O **objeto Camera deve** ser nomeado Câmera **Principal** (observe a ortografia!)

    2. A Marca da Câmera **Principal** deve ser definida como **MainCamera** (observe a ortografia!)

    3. Certifique-se **de que a Posição da** Transformação está definida como **0, 0, 0**

    4. Definir **sinalizadores de limpar** para cor **sólida**

    5. Definir a **cor da** tela de fundo do componente de câmera **como Preto, Alfa 0 (Código Hexadigo: #00000000)**

        ![configurar componentes da câmera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capítulo 5 – Importar o Newtonsoft.Jsna biblioteca

> [!IMPORTANT]
> Se você importou o '.unitypackage' no [último Capítulo,](#chapter-4---main-camera-setup)ignore este Capítulo.

Para ajudá-lo a desselizar e serializar objetos recebidos e enviados ao Serviço de Bot, você precisa baixar oNewtonsoft.Js *na* biblioteca. Você encontrará uma versão compatível já organizada com a estrutura de pastas do Unity correta neste arquivo [de pacote do Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Para importar a biblioteca:

1.  Baixe o pacote do Unity.
2.  Clique em **Ativos,** **Importar Pacote**, **Pacote Personalizado**.

    ![Importar Newtonsoft.Jsem](images/AzureLabs-Lab4-20.png)

3.  Procure o Pacote do Unity que você baixou e clique em Abrir.
4.  Certifique-se de que todos os componentes do pacote estão marcados e clique em **Importar**.

    ![Importar o Newtonsoft.Jsem ativos](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capítulo 6 – Criar a classe FaceAnalysis

A finalidade da classe FaceAnalysis é hospedar os métodos necessários para se comunicar com seu Serviço de Reconhecimento Facial do Azure. 

- Depois de enviar ao serviço uma imagem de captura, ele a analisará, identificará os rostos e determinará se algum pertence a uma pessoa conhecida. 
- Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto da interface do usuário na cena.

Para criar a *classe FaceAnalysis:*

 1. Clique com o botão direito do *mouse* na Pasta Ativos localizada no painel Project e clique em **Criar**  >  **Pasta**. Chame a pasta **Scripts**. 

    ![Crie a classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Clique duas vezes na pasta que acabou de ser criada para abri-la. 
3.  Clique com o botão direito do mouse dentro da pasta e clique **em Criar**  >  **Script C#.** Chame o script *FaceAnalysis.* 
4.  Clique duas vezes no novo script *FaceAnalysis* para abri-lo com Visual Studio 2017.
5.  Insira os seguintes namespaces acima da *classe FaceAnalysis:*

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Agora você precisa adicionar todos os objetos que são usados para desserlizar. Esses objetos precisam ser adicionados **fora** do script *FaceAnalysis* (abaixo do colchete inferior). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. Os *métodos Start()* *e Update()* não serão usados, portanto, exclua-os agora. 

8.  Dentro da *classe FaceAnalysis,* adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Substitua a **chave e** **a personGroupId** pela chave de serviço e a ID do grupo que você criou anteriormente.

9.  Adicione o *método Awake(),* que inicializa a classe , adicionando a classe *ImageCapture* à Câmera Principal e chama o método de criação rótulo:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Adicione o *método CreateLabel(),* que cria o *objeto Label* para exibir o resultado da análise:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Adicione o *método DetectFacesFromImage()* *e GetImageAsByteArray().* O primeiro solicitará que o Serviço de Reconhecimento Facial detecte qualquer face possível na imagem enviada, enquanto o último é necessário para converter a imagem capturada em uma matriz de bytes:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Adicione o *método IdentifyFaces(),* que solicita que o Serviço de Reconhecimento Facial identifique qualquer rosto conhecido detectado anteriormente na imagem enviada.  A solicitação retornará uma ID da pessoa identificada, mas não o nome:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Adicione o *método GetPerson().* Ao fornecer a ID da pessoa,  esse método solicita que o Serviço de Reconhecimento Facial retorne o nome da pessoa identificada:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  **Lembre-se de** Salvar as alterações antes de voltar para o Editor do Unity.
15.  No Editor do Unity, arraste o script FaceAnalysis da pasta Scripts no painel Project para o objeto Câmera Principal no *painel Hierarquia*. O novo componente de script será adicionado à Câmera Principal. 

![Colocar FaceAnalysis na Câmera Principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capítulo 7 – Criar a classe ImageCapture

A finalidade da classe *ImageCapture* é hospedar os métodos necessários para se comunicar com seu Serviço de Reconhecimento Facial do *Azure* para analisar a imagem que você capturará, identificando rostos e determinando se ele pertence a uma pessoa conhecida. Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto da interface do usuário na cena.

Para criar a *classe ImageCapture:*
 
1.  Clique com o botão direito do mouse na **pasta Scripts** que você criou anteriormente e clique **em Criar**, **Script C#.** Chame o script *ImageCapture.* 
2.  Clique duas vezes no novo script *ImageCapture* para abri-lo com Visual Studio 2017.
3.  Insira os seguintes namespaces acima da classe ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Dentro da *classe ImageCapture,* adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Adicione os *métodos Awake()* e *Start()* necessários para inicializar a classe e permitir que o HoloLens capture os gestos do usuário:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Adicione o *TapHandler()* que é chamado quando o usuário executa um *gesto de toque:*

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Adicione o *método ExecuteImageCaptureAndAnalysis(),* que iniciará o processo de Captura de Imagem:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Adicione os manipuladores que são chamados quando o processo de captura de fotos é concluído:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. **Lembre-se de** Salvar as alterações antes de voltar para o Editor do Unity.

## <a name="chapter-8---building-the-solution"></a>Capítulo 8 – Criando a solução

Para executar um teste completo do seu aplicativo, você precisará fazer sideload dele em seu HoloLens.

Antes de fazer isso, verifique se:

-   Todas as configurações mencionadas no Capítulo 3 são definidas corretamente. 
-   O script *FaceAnalysis* é anexado ao objeto Câmera Principal. 
-   A Chave **de Auth e** **a ID do** Grupo foram definidas dentro do script *FaceAnalysis.*

Um ponto em que você está pronto para criar a Solução. Depois que a Solução tiver sido criada, você estará pronto para implantar seu aplicativo.

Para iniciar o processo de build:

1.  Salve a cena atual clicando em Arquivo, Salvar.
2.  Vá para Arquivo, Criar Configurações, clique em Adicionar Cenas Abertas.
3.  Marque Projetos C# do Unity.

    ![Implantar a solução Visual Studio aplicativo](images/AzureLabs-Lab4-24.png)

4.  Pressione Build. Ao fazer isso, o Unity iniciará uma Explorador de Arquivos, na qual você precisará criar e, em seguida, selecionará uma pasta na qual o aplicativo será criado. Crie essa pasta agora, dentro do projeto do Unity, e chame-a de Aplicativo. Em seguida, com a pasta Aplicativo selecionada, pressione Selecionar Pasta. 
5.  O Unity começará a criar seu projeto, até a pasta Aplicativo. 
6.  Depois que o Unity terminar de criar (pode levar algum tempo), ele abrirá uma Explorador de Arquivos no local do build.

    ![Implantar a solução do Visual Studio](images/AzureLabs-Lab4-25.png)

7.  Abra a pasta Aplicativo e, em seguida, abra a nova solução Project (conforme visto acima, MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>Capítulo 9 – Implantando seu aplicativo

Para implantar no HoloLens:

1.  Você precisará do Endereço IP do seu HoloLens (para Implantação Remota) e para garantir que seu HoloLens está no Modo **de Desenvolvedor.** Para fazer isso:

    1. Ao usar o HoloLens, abra o **Configurações**.
    2. Vá para **Rede & Internet > Wi-Fi > Opções Avançadas**
    3. Observe o **endereço IPv4.**
    4. Em seguida, navegue de **volta para Configurações** e, em seguida, para Atualizar & segurança > para **desenvolvedores** 
    5. De configurar o modo de desenvolvedor.

2.  Navegue até o novo build do Unity (a *pasta Aplicativo)* e abra o arquivo de solução com *Visual Studio*.
3.  Na Configuração da Solução, selecione **Depurar**.
4.  Na Plataforma de Solução, selecione **x86**, **Computador Remoto.** 

    ![Alterar a configuração da solução](images/AzureLabs-Lab4-26.png)
 
5.  Vá para o **menu Build e** clique em Implantar **Solução** para fazer sideload do aplicativo em seu HoloLens.
6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser lançado!

> [!NOTE]
> Para implantar no headset imersivo,  de definir a Plataforma  de Solução como Computador *Local* e definir a Configuração como *Depurar*, com *x86* como a **Plataforma**. Em seguida, implante no computador local, usando o **menu Build**, *selecionando Implantar Solução*. 


## <a name="chapter-10---using-the-application"></a>Capítulo 10 – Usando o aplicativo

1.  Usando o HoloLens, iniciar o aplicativo.
2.  Veja a pessoa que você registrou com a *API de Face.* Certifique-se de que:

    -  O rosto da pessoa não está muito distante e claramente visível
    -  A iluminação do ambiente não está muito escura

3.  Use o gesto de toque para capturar a imagem da pessoa.
4.  Aguarde até que o aplicativo envie a solicitação de análise e receba uma resposta.
5.  Se a pessoa tiver sido reconhecida com êxito, o nome da pessoa aparecerá como texto da interface do usuário.
6.  Você pode repetir o processo de captura usando o gesto de toque a cada poucos segundos.

## <a name="your-finished-azure-face-api-application"></a>Seu aplicativo de API de Face do Azure concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de Reconhecimento Facial do Azure para detectar rostos em uma imagem e identificar rostos conhecidos.

![resultado da conclusão deste curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

A API de Detecção Facial do **Azure** é poderosa o suficiente para detectar até 64 faces em uma única imagem. Estenda o aplicativo para que ele possa reconhecer duas ou três faces, entre muitas outras pessoas.

### <a name="exercise-2"></a>Exercício 2

A **API de Face do Azure** também é capaz de fornecer de volta todos os tipos de informações de atributo. Integre isso ao aplicativo. Isso pode ser ainda mais interessante, quando combinado com a [API de Emoção](https://azure.microsoft.com/services/cognitive-services/emotion/).