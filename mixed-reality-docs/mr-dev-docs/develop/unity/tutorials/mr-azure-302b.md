---
title: HoloLens (1ª geração) e Azure 302b – Visão Personalizada
description: Conclua este curso para aprender a treinar um modelo de aprendizado de máquina e, em seguida, use o modelo treinado para reconhecer objetos semelhantes em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, realidade mista, academia, unity, tutorial, api, visão personalizada, hololens, imersão, vr, Windows 10, Visual Studio
ms.openlocfilehash: 25f07dddf53cf8c279f99d230d1bd4d206a663eba884abc0dd32313bce4b7b43
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217442"
---
# <a name="hololens-1st-gen-and-azure-302b-custom-vision"></a>HoloLens (1ª gen) e 302b do Azure: visão personalizada

<br>

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>


Neste curso, você aprenderá a reconhecer o conteúdo Visual personalizado dentro de uma imagem fornecida, usando os recursos de Visão Personalizada do Azure em um aplicativo de realidade misturada.

Este serviço permitirá que você treine um modelo de aprendizado de máquina usando imagens de objeto. em seguida, você usará o modelo treinado para reconhecer objetos semelhantes, conforme fornecido pela captura de câmera de Microsoft HoloLens ou uma câmera conectada ao seu PC para fones de ouvido (VR) de imersão.

![resultado do curso](images/AzureLabs-Lab302b-00.png)

O Azure Visão Personalizada é um serviço cognitiva da Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizados. Esses classificadores podem ser usados com novas imagens para reconhecer ou classificar objetos dentro dessa nova imagem. O serviço fornece um portal online simples e fácil de usar para simplificar o processo. Para obter mais informações, visite a [página de serviço de visão personalizada do Azure](/azure/cognitive-services/custom-vision-service/home).

Após a conclusão deste curso, você terá um aplicativo de realidade misturada que poderá trabalhar em dois modos:

-   **Modo de análise**: configurar o serviço de visão personalizada manualmente carregando imagens, criando marcas e treinando o serviço para reconhecer objetos diferentes (nesse caso, mouse e teclado). em seguida, você criará um aplicativo HoloLens que capturará imagens usando a câmera e tentará reconhecer esses objetos no mundo real.

-   **Modo de treinamento**: você irá implementar o código que habilitará um "modo de treinamento" em seu aplicativo. o modo de treinamento permitirá que você capture imagens usando a câmera do HoloLens, carregue as imagens capturadas no serviço e treine o modelo de visão personalizada.

Este curso ensinará a você como obter os resultados do Serviço de Visão Personalizada em um aplicativo de exemplo baseado em Unity. Será necessário aplicar esses conceitos a um aplicativo personalizado que você possa estar criando.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 302b: Visão Personalizada</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Uma câmera conectada ao seu PC (para desenvolvimento de headsets de imersão)
- Acesso à Internet para a instalação do Azure e recuperação de API de Visão Personalizada
- Uma série de pelo menos cinco (5) imagens (dez (10) recomendado) para cada objeto que você deseja que a Serviço de Visão Personalizada reconheça. Se desejar, você pode usar [as imagens já fornecidas com este curso (um mouse de computador e um teclado) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste sua HoloLens. se você precisar de suporte para configurar seu HoloLens, [visite o artigo HoloLens instalação](/hololens/hololens-setup). 
3.  é uma boa ideia executar a calibragem e o ajuste do Sensor ao começar a desenvolver um novo aplicativo de HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

para obter ajuda sobre a calibração, siga este [link para o artigo HoloLens calibration](/hololens/hololens-calibration#hololens-2).

para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste HoloLens sensor](/hololens/hololens-updates).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Capítulo 1-o portal de Serviço de Visão Personalizada

Para usar o *serviço de visão personalizada* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.

1.  Primeiro, [navegue até a página principal do *serviço de visão personalizada*](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  clique no botão **Introdução** .

    ![Introdução ao Serviço de Visão Personalizada](images/AzureLabs-Lab302b-01.png)

3.  Entre no portal de *serviço de visão personalizada* .

    ![Entrar no portal](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

4.  Depois de fazer logon pela primeira vez, você será solicitado com o painel *termos de serviço* . Clique na caixa de seleção para concordar com os termos. Em seguida, clique em **concordo**.

    ![Termos de serviço](images/AzureLabs-Lab302b-03.png)

5.  Tendo acordado os termos, você será navegado até a seção de *projetos* do Portal. Clique em **novo Project**.

    ![Criar um novo projeto](images/AzureLabs-Lab302b-04.png)

6.  Uma guia será exibida no lado direito, o que solicitará que você especifique alguns campos para o projeto.

    1.  Insira um *nome* para o seu projeto.

    2.  Insira uma *Descrição* para seu projeto (*opcional*).

    3.  Escolha um *grupo de recursos* ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).

    4. definir os *tipos de Project* como **classificação**
    
    5. Defina os *domínios* como **geral**.

        ![Definir os domínios](images/AzureLabs-Lab302b-05.png)

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

7.  Quando terminar, clique em **criar projeto**, você será redirecionado para a página Serviço de visão personalizada, projeto.

## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2-treinando seu Visão Personalizada projeto

Uma vez no portal de Visão Personalizada, seu objetivo principal é treinar seu projeto para reconhecer objetos específicos em imagens. Você precisa de pelo menos cinco (5) imagens, embora dez (10) seja preferencial, para cada objeto que você deseja que seu aplicativo reconheça. [Você pode usar as imagens fornecidas com este curso (um mouse de computador e um teclado)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Para treinar seu projeto de Serviço de Visão Personalizada:

1.  Clique no **+** botão ao lado de **marcas.**

    ![Adicionar nova marca](images/AzureLabs-Lab302b-06.png)

2.  Adicione o **nome** do objeto que você deseja reconhecer. Clique em **Save**.

    ![Adicionar nome do objeto e salvar](images/AzureLabs-Lab302b-07.png)

3.  Você notará que sua **marca** foi adicionada (talvez seja necessário recarregar sua página para que ela apareça). Clique na caixa de seleção ao lado de sua nova marca, se ainda não estiver marcada.

    ![Habilitar nova marca](images/AzureLabs-Lab302b-08.png)

4.  Clique em **Adicionar imagens** no centro da página.

    ![Adicionar imagens](images/AzureLabs-Lab302b-09.png)

5.  Clique em **procurar arquivos locais** e pesquise, em seguida, selecione as imagens que você deseja carregar, com o mínimo de cinco (5). Lembre-se de que todas essas imagens devem conter o objeto que você está treinando.

    > [!NOTE]
    >  Você pode selecionar várias imagens de cada vez para carregar.

6.  Depois que você puder ver as imagens na guia, selecione a marca apropriada na caixa **minhas marcas** .

    ![Selecionar marcas](images/AzureLabs-Lab302b-10.png)

7.  clique em **Upload arquivos**. Os arquivos começarão a ser carregados. Depois de confirmar o carregamento, clique em **concluído**.

    ![Carregar arquivos](images/AzureLabs-Lab302b-11.png)

8.  Repita o mesmo processo para criar uma nova **marca** chamada **teclado** e carregar as fotos apropriadas para ela. Certifique-se de **desmarcar a seleção** do *mouse* depois de criar as novas marcas, para mostrar a janela *Adicionar imagens* .

9.  Depois de configurar as duas marcas, clique em **treinar** e a primeira iteração de treinamento começará a criar.

    ![Habilitar iteração de treinamento](images/AzureLabs-Lab302b-12.png)

10. Depois de compilado, você poderá ver dois botões chamados **Make Default** e **predição URL**. Clique em **tornar padrão** primeiro e, em seguida, clique em **URL de previsão**.

    ![Criar URL de previsão e padrão](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > A URL do ponto de extremidade fornecida por isso é definida para qualquer *iteração* marcada como padrão. Dessa forma, se você fizer uma nova *iteração* e atualizá-la como padrão, não será necessário alterar seu código.

11. depois de clicar em *URL de previsão*, abra *Bloco de notas*, copie e cole a **URL** e a chave de **previsão**, para que você possa recuperá-la quando precisar mais tarde no código.

    ![Copiar e colar URL e Prediction-Key](images/AzureLabs-Lab302b-14.png)

12. Clique no **engrenagem** na parte superior direita da tela.

    ![Clique no ícone de engrenagem para abrir as configurações](images/AzureLabs-Lab302b-15.png)

13. copie a **chave de treinamento** e cole-a em uma *Bloco de notas*, para uso posterior.

    ![Copiar chave de treinamento](images/AzureLabs-Lab302b-16.png)

14. além disso, copie sua **Id de Project** e cole-a em seu arquivo de *Bloco de notas* , para uso posterior.

    ![Copiar ID do projeto](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o *Unity* e clique em **novo**.

    ![Criar um novo projeto do Unity](images/AzureLabs-Lab302b-17.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity. Insira **AzureCustomVision.** Verifique se o modelo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Definir configurações de projeto](images/AzureLabs-Lab302b-18.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar*  >  *preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**. altere o **Editor de Script externo** para **Visual Studio 2017**. Feche a janela **preferências** .

    ![Configurar ferramentas externas](images/AzureLabs-Lab302b-19.png)

4.  em seguida, vá para **arquivo > criar Configurações** e selecione **Plataforma Universal do Windows**, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.

    ![Definir configurações de compilação ](images/AzureLabs-Lab302b-20.png)

5.  ainda no **arquivo > Build Configurações** e certifique-se de que:

    1.  O **dispositivo de destino** está definido como **HoloLens**

        > Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.
        
    2.  O **tipo de compilação** está definido como **D3D**
    3.  O **SDK** está definido para o **mais recente instalado**
    4.  **Visual Studio versão** está definida para o **mais recente instalado**
    5.  **Compilar e executar** é definido como **computador local**
    6.  Salve a cena e adicione-a à compilação. 

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Adicionar cena aberta à lista de Build](images/AzureLabs-Lab302b-21.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![Criar nova pasta de cena](images/AzureLabs-Lab302b-22.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo:* , digite **CustomVisionScene** e clique em **salvar**.

            ![Nomear novo arquivo de cena](images/AzureLabs-Lab302b-23.png)

            > Lembre-se de que você deve salvar as cenas do Unity na pasta *ativos* , pois elas devem ser associadas ao projeto do Unity. Criar a pasta de cenas (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.
            
    7.  as configurações restantes, no *Build Configurações*, devem ser deixadas como padrão por enquanto.

        ![Configurações de compilação padrão](images/AzureLabs-Lab302b-24.png)

6.  na janela *criar Configurações* , clique no botão **Configurações do Player** , isso abrirá o painel relacionado no espaço onde o *inspetor* está localizado.

7. Nesse painel, algumas configurações precisam ser verificadas:

    1.  na guia **outros Configurações** :

        1.  A **versão de tempo de execução de script** deve ser **Experimental (.NET 4,6 equivalente)**, o que irá disparar uma necessidade de reiniciar o editor.

        2. O **back-end de script** deve ser **.net**

        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

        ![Definir compantiblity de API](images/AzureLabs-Lab302b-25.png)

    2.  na guia **publicação Configurações** , em **recursos**, marque:

        1. **InternetClient**

        2.  **Webcam**

        3. **Microfone**

        ![Definir configurações de publicação](images/AzureLabs-Lab302b-26.png)

    3.  mais adiante no painel, em **XR Configurações** (encontrado abaixo **Configurações de publicação**), **há suporte para a realidade Virtual** de tique, verifique se o **SDK do Windows Mixed Reality** foi adicionado.

    ![Definir configurações de XR](images/AzureLabs-Lab302b-27.png)

8.  de volta ao *Build Configurações* *\# projetos Unity C* não estão mais esmaecidos; marque a caixa de seleção ao lado disso.

9.  Feche a janela Configurações de Build.

10.  Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Capítulo 4-importando a DLL Newtonsoft no Unity

> [!IMPORTANT]
> Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, sinta-se à vontade para baixar este [Azure-Mr-302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importá-lo em seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar no [capítulo 6](#chapter-6---create-the-customvisionanalyser-class).

Este curso requer o uso da biblioteca **Newtonsoft** , que você pode adicionar como uma DLL aos seus ativos. O pacote que contém [essa biblioteca pode ser baixado deste link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Para importar a biblioteca Newtonsoft para seu projeto, use o pacote do Unity que acompanha este curso.

1.  Adicione o *. unitypackage* ao Unity usando a opção de menu * >   >   *pacote* personalizado do *pacote* de *importação* de ativos* .

2.  Na caixa **Importar pacote de Unity** que é exibida, verifique se tudo em (e incluindo) **plug-ins** está selecionado.

    ![Importar todos os itens de pacote](images/AzureLabs-Lab302b-28.png)

3.  Clique no botão **importar** para adicionar os itens ao seu projeto.

4.  Vá para a pasta **Newtonsoft** em **plug-ins** na exibição do projeto e selecione o *Newtonsoft.Jsno plug-in*.

    ![Selecionar plug-in Newtonsoft](images/AzureLabs-Lab302b-29.png)

5.  Com a *Newtonsoft.Jsno plug-in* selecionado, verifique se **qualquer plataforma** está **desmarcada** e, em seguida, verifique se **WSAPlayer** também está **desmarcado** e clique em **aplicar**. Isso é apenas para confirmar que os arquivos estão configurados corretamente.

    ![Configurar plug-in Newtonsoft](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Marcar esses plug-ins os configura para ser usado apenas no editor do Unity. Há um conjunto diferente deles na pasta WSA que será usada depois que o projeto for exportado do Unity.

6.  Em seguida, você precisa abrir a pasta **WSA** , dentro da pasta **Newtonsoft** . Você verá uma cópia do mesmo arquivo que acabou de configurar. Selecione o arquivo e, no Inspetor, verifique se
    -   **Qualquer plataforma** está **desmarcada** 
    -   **somente** **WSAPlayer** está **marcado**
    -   Não **processar** está **marcado**

    ![Definir as configurações da plataforma de plug-in newtonsoft](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Capítulo 5 – Configuração da câmera

1.  No Painel hierarquia, selecione a *Câmera Principal.*

2.  Depois de selecionado, você poderá ver todos os componentes da *Câmera Principal* no Painel *inspetor.*

    1.  O *objeto da* câmera deve ser nomeado Câmera **Principal** (observe a ortografia!)

    2.  A Marca da Câmera **Principal** deve ser definida como **MainCamera** (observe a ortografia!)

    3.  Certifique-se **de que a Posição da** Transformação está definida como **0, 0, 0**

    4.  Definir **Limpar Sinalizadores como** Cor **Sólida** (ignore isso para headset imersivo).

    5.  De **definir** a cor da tela de fundo do componente da câmera como **Preto, Alfa 0 (Código Hexa #00000000)** (ignore isso para headset imersivo).

    ![Configurar propriedades do componente Câmera](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Capítulo 6 – Criar a classe CustomVisionAnalyser.

Neste ponto, você está pronto para escrever algum código.

Você começará com a *classe CustomVisionAnalyser.*

> [!NOTE]
> As chamadas para o **serviço Visão Personalizada de** dados feitas no código mostrado abaixo são feitas usando Visão Personalizada API REST do **.** Usando isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante por conta própria). Esteja ciente de que a Microsoft oferece **um SDK Visão Personalizada Service** que também pode ser usado para fazer chamadas ao Serviço. Para obter mais informações, visite [o Visão Personalizada do SDK do Serviço.](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)

Essa classe é responsável por:

-   Carregando a imagem mais recente capturada como uma matriz de bytes.

-   Enviar a matriz de byte  para sua instância do Serviço Visão Personalizada Azure para análise.

-   Recebendo a resposta como uma cadeia de caracteres JSON.

-   Desselizando a resposta e passando  a Previsão resultante para a classe *SceneOrganiser,* que cuidará de como a resposta deve ser exibida.

Para criar esta classe:

1.  Clique com o botão *direito* do mouse na Pasta *de Ativos* localizada no painel Project e clique **em Criar > Pasta**. Chame a pasta **Scripts**.

    ![Criar pasta de scripts](images/AzureLabs-Lab302b-33.png)

2.  Clique duas vezes na pasta que acabou de ser criada para abri-la.

3.  Clique com o botão direito do mouse dentro da pasta e clique **em Criar**  >  **\# Script C.** Nomeia o script *CustomVisionAnalyser*.

4.  Clique duas vezes no novo script *CustomVisionAnalyser* para abri-lo com **Visual Studio**.

5.  Atualize os namespaces na parte superior do arquivo para corresponder ao seguinte:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  Na classe *CustomVisionAnalyser,* adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Insira sua Chave de **Previsão na** variável **predictionKey** e **no** ponto de extremidade de previsão na **variável predictionEndpoint.** Você as *copiou para Bloco de notas* anteriormente no curso.

7.  O código **para o Awake()** agora precisa ser adicionado para inicializar a variável instance:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Exclua os **métodos Start()** e **Update().**

9.  Em seguida, adicione a coroutina (com o método **estático GetImageAsByteArray()** abaixo dele), que obterá os resultados da análise da imagem capturada pela *classe ImageCapture.*

    > [!NOTE]
    > Na **coroutine AnalyseImageCapture,** há uma chamada para a *classe SceneOrganiser* que você ainda deve criar. Portanto, **deixe essas linhas comentadas por enquanto.**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  Salve as alterações no **Visual Studio** antes de retornar ao **Unity.**

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Capítulo 7 – Criar a classe CustomVisionObjects

A classe que você criará agora é a *classe CustomVisionObjects.*

Esse script contém vários objetos usados por outras classes para serializar e desserlizar as chamadas feitas ao *serviço Visão Personalizada .*

> [!WARNING]
> É importante que você anote o ponto de extremidade que o serviço Visão Personalizada fornece, pois a estrutura JSON abaixo foi configurada para funcionar com a [*Visão Personalizada Previsão v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Se você tiver uma versão diferente, talvez seja necessário atualizar a estrutura abaixo.

Para criar esta classe:

1.  Clique com o botão direito do mouse **na pasta Scripts** e clique **em Criar**  >  **\# Script C.** Chame o script *CustomVisionObjects*.

2.  Clique duas vezes no novo script **CustomVisionObjects** para abri-lo com **Visual Studio**.

3.  Adicione os seguintes namespaces à parte superior do arquivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  **Exclua os métodos Start()** **e Update()** dentro da *classe CustomVisionObjects;* essa classe agora deve estar vazia.

5.  Adicione as classes a **seguir fora** da *classe CustomVisionObjects.* Esses objetos são usados pela biblioteca *Newtonsoft* para serializar e serializar os dados de resposta:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Capítulo 8 – Criar a classe VoiceRecognizer

Essa classe reconhecerá a entrada de voz do usuário.

Para criar esta classe:

1.  Clique com o botão direito do mouse **na pasta Scripts** e clique **em Criar**  >  **\# Script C.** Chame o script *VoiceRecognizer.*

2.  Clique duas vezes no novo script **VoiceRecognizer** para abri-lo com **Visual Studio**.

3.  Adicione os seguintes namespaces acima da *classe VoiceRecognizer:*

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro *da classe VoiceRecognizer,* acima do *método Start():*

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Adicione os **métodos Awake()** e **Start(),** que configurarão as palavras-chave do usuário a serem *reconhecidas* ao associar uma marca a uma imagem:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  **Exclua o método Update().**

7.  Adicione o seguinte manipulador, que é chamado sempre que a entrada de voz é reconhecida:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Salve as alterações no **Visual Studio** antes de retornar ao **Unity.**

> [!NOTE]
> Não se preocupe com o código que pode parecer ter um erro, pois você fornecerá mais classes em breve, o que corrigirá isso.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Capítulo 9 – Criar a classe CustomVisionTrainer

Essa classe encadeará uma série de chamadas à Web para treinar o *Visão Personalizada Service*. Cada chamada será explicada em detalhes logo acima do código.

Para criar esta classe:

1.  Clique com o botão direito do mouse **na pasta Scripts** e clique **em Criar**  >  **\# Script C.** Chame o script *CustomVisionTrainer*.

2.  Clique duas vezes no novo script *CustomVisionTrainer* para abri-lo com **Visual Studio**.

3.  Adicione os seguintes namespaces acima da *classe CustomVisionTrainer:*

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro *da classe CustomVisionTrainer,* acima do **método Start().** 

    > [!NOTE]
    > A URL de treinamento usada aqui é fornecida na *documentação Visão Personalizada Treinamento 1.2* e tem uma estrutura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Para obter mais informações, visite a [*API de referência Visão Personalizada Treinamento v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > É importante que você anote o ponto de extremidade que o serviço Visão Personalizada fornece para o modo de treinamento, pois a estrutura JSON usada (dentro da classe **CustomVisionObjects)** foi configurada para trabalhar com o Treinamento do [*Visão Personalizada v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). Se você tiver uma versão diferente, talvez seja necessário atualizar a *estrutura Objetos.*

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Certifique-se de adicionar o valor **da** Chave de Serviço (Chave de Treinamento) **e Project ID,** que você anotou anteriormente; esses são os valores coletados do portal anteriormente no curso [(Capítulo 2, etapa 10 em diante)](#chapter-2---training-your-custom-vision-project).

5.  Adicione os seguintes **métodos Start()** **e Awake().** Esses métodos são chamados na inicialização e contêm a chamada para configurar a interface do usuário:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  **Exclua o método Update().** Essa classe não precisará dela.

7.  Adicione o **método RequestTagSelection().** Esse método é o primeiro a ser chamado quando uma imagem foi capturada e armazenada no dispositivo e agora está pronto para ser enviado para o serviço *Visão Personalizada*, para treiná-la. Esse método exibe, na interface do usuário de treinamento, um conjunto de palavras-chave que o usuário pode usar para marcar a imagem que foi capturada. Ele também alerta a classe *VoiceRecognizer* para começar a escutar o usuário para entrada de voz.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Adicione o **método VerifyTag().** Esse método receberá a entrada de voz reconhecida pela classe **VoiceRecognizer,** verificará sua validade e iniciará o processo de treinamento.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Adicione o **método SubmitImageForTraining().** Esse método iniciará o processo de treinamento Visão Personalizada Service. A primeira etapa é recuperar a **ID da** Marca do Serviço associado à entrada de fala validada do usuário. A **ID da marca** será carregada junto com a imagem.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Adicione o **método TrainCustomVisionProject().** Depois que a imagem tiver sido enviada e marcada, esse método será chamado. Ele criará uma nova Iteração que será treinada com todas as imagens anteriores enviadas para o Serviço mais a imagem recém-carregada. Depois que o treinamento for concluído, esse método chamará um método para definir a Iteração recém-criada como **Padrão,** de modo que o ponto de extremidade que você está usando para análise seja a **iteração** treinada mais recente.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Adicione o **método SetDefaultIteration().** Esse método definirá a iteração criada e treinada anteriormente como *Padrão.* Depois de concluído, esse método terá que excluir a iteração anterior existente no Serviço. No momento da redação deste curso, há um limite máximo de dez (10) ierções permitidas ao mesmo tempo no Serviço.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Adicione o **método DeletePreviousIteration().** Esse método encontrará e excluirá a iteração não padrão anterior:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. O último método a adicionar nessa classe é o **método GetImageAsByteArray(),** usado nas chamadas à Web para converter a imagem capturada em uma matriz de byte.

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. Salve as alterações no **Visual Studio** antes de retornar ao **Unity.**

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Capítulo 10 – Criar a classe SceneOrganiser

Essa classe vai:

-   Crie um **objeto Cursor** para anexar à Câmera Principal.

-   Crie um **objeto Label** que será exibido quando o Serviço reconhecer os objetos do mundo real.

-   Configurar a Câmera Principal anexando os componentes apropriados a ela.

-   Quando estiver no **Modo** de Análise , gera os Rótulos em runtime, no espaço de mundo apropriado em relação à posição da Câmera Principal e exibe os dados recebidos do serviço Visão Personalizada.

-   Quando estiver **no Modo de Treinamento,** gerará a interface do usuário que exibirá as diferentes fases do processo de treinamento.

Para criar esta classe:

1.  Clique com o botão direito do mouse **na pasta Scripts** e clique **em Criar**  >  **\# Script C.** Nomeia o script *SceneOrganiser*.

2.  Clique duas vezes no novo script *SceneOrganiser* para abri-lo com **Visual Studio**.

3.  Você só precisará de um namespace, remova os outros acima da *classe SceneOrganiser:*

    ```csharp
    using UnityEngine;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro *da classe SceneOrganiser,* acima do **método Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  **Exclua os** métodos **Start() e Update().**

6.  Logo abaixo das variáveis, adicione **o método Awake(),** que inicializa a classe e configura a cena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  Agora, adicione o **método CreateCameraCursor()** que cria e posiciona o cursor da Câmera Principal e o **método CreateLabel(),** que cria o **objeto Analysis Label.**

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Adicione o **método SetCameraStatus(),** que manipulará mensagens destinadas à malha de texto, fornecendo o status da câmera.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Adicione os **métodos PlaceAnalysisLabel()** e **SetTagsToLastLabel(),** que gerarão e exibirão os dados do serviço Visão Personalizada na cena.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Por fim, adicione o **método CreateTrainingUI(),** que gerará a interface do usuário exibindo os vários estágios do processo de treinamento quando o aplicativo estiver no Modo de Treinamento. Esse método também será aproveitado para criar o objeto de status da câmera.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Salve as alterações no **Visual Studio** antes de retornar ao **Unity.**

> [!IMPORTANT]
> Antes de continuar, abra a **classe CustomVisionAnalyser** e, dentro do  método **AnalyseLastImageCaptured(),** descomenta as seguintes linhas:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Capítulo 11 – Criar a classe ImageCapture

A próxima classe que você criará é a *classe ImageCapture.*

Essa classe é responsável por:

-   Capturando uma imagem usando a HoloLens e o armazenamento dela na Pasta *do* Aplicativo.

-   Manipulando gestos de toque do usuário.

-   Manter o *valor Enum* que determina se o aplicativo será executado no modo *de* análise ou *no Modo de* Treinamento.

Para criar esta classe:

1.  Vá para a **pasta Scripts** criada anteriormente.

2.  Clique com o botão direito do mouse dentro da pasta e clique **em Criar > Script \# C.** Nomeia o script *ImageCapture.*

3.  Clique duas vezes no novo script **ImageCapture** para abri-lo com **Visual Studio**.

4.  Substitua os namespaces na parte superior do arquivo pelo seguinte:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro *da classe ImageCapture,* acima do **método Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  Agora, é necessário adicionar o código para os métodos **Awake()** e **Start():**

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implemente um manipulador que será chamado quando ocorrer um gesto de toque.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > No *modo análise,* o **método TapHandler** atua como uma opção para iniciar ou parar o loop de captura de fotos.
    >
    > No *modo* de treinamento, ele capturará uma imagem da câmera.
    >
    > Quando o cursor está verde, isso significa que a câmera está disponível para tirar a imagem.
    >
    > Quando o cursor está vermelho, isso significa que a câmera está ocupada.

8.  Adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e para quando ela estiver pronta para ser analisada. O resultado é passado para *o CustomVisionAnalyser* ou o *CustomVisionTrainer,* dependendo de qual modo o código está definido.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Salve as alterações no **Visual Studio** antes de retornar ao **Unity.**

11. Agora que todos os scripts foram concluídos, volte para o Editor do Unity e, em seguida, clique e arraste a **classe SceneOrganiser** da pasta **Scripts** para o objeto **Câmera** Principal no Painel *de Hierarquia*.

## <a name="chapter-12---before-building"></a>Capítulo 12 – Antes de criar

Para executar um teste completo do seu aplicativo, você precisará fazer sideload dele em seu HoloLens.

Antes de fazer isso, verifique se:

- Todas as configurações mencionadas no [Capítulo 2](#chapter-2---training-your-custom-vision-project) são definidas corretamente.

- Todos os campos na Câmera **Principal,** painel Inspetor, são atribuídos corretamente.

- O script **SceneOrganiser** é anexado ao **objeto Câmera** Principal.

- Insira sua Chave de **Previsão na** variável **predictionKey.**

- Você inseriu o ponto **de extremidade de previsão** na **variável predictionEndpoint.**

- Você inseriu sua Chave **de Treinamento** na **variável trainingKey,** da *classe CustomVisionTrainer.*

- Você inseriu sua **Project ID na** variável **projectId** da *classe CustomVisionTrainer.*

## <a name="chapter-13---build-and-sideload-your-application"></a>Capítulo 13 – Criar e fazer sideload do aplicativo

Para iniciar o *processo de build:*

1.  Vá para **Arquivo > Build Configurações**.

2.  Projetos **C do Unity \# de** Escala .

3.  Clique em **Compilar**. O Unity iniciará **uma Explorador de Arquivos,** na qual você precisa criar e, em seguida, selecionará uma pasta na qual o aplicativo será criado. Crie essa pasta agora e nomee-a **Aplicativo**. Em seguida, com **a pasta** Aplicativo selecionada, clique **em Selecionar Pasta**.

4.  O Unity começará a criar seu projeto para a **pasta Aplicativo.**

5.  Depois que o Unity terminar de criar (pode levar algum tempo), ele abrirá uma janela do Explorador de Arquivos no local do build (verifique a barra de tarefas, pois ela pode nem sempre aparecer acima das janelas, mas notificará você sobre **a** adição de uma nova janela).

Para implantar no HoloLens:

1.  Você precisará do Endereço IP do seu HoloLens (para Implantação Remota) e para garantir que seu HoloLens está no Modo **de Desenvolvedor.** Para fazer isso:

    1.  Ao usar o HoloLens, abra o **Configurações**.

    2.  Acesse Opções **Avançadas de**  >  **Wi-Fi**  >   da Internet & Rede

    3.  Observe o **endereço IPv4.**

    4.  Em seguida, navegue de **volta para Configurações** e, em seguida, para Atualizar & **Segurança**  >  **para Desenvolvedores**

    5.  De **definir o modo de desenvolvedor em**.

2.  Navegue até o novo build do Unity (a **pasta Aplicativo)** e abra o arquivo de solução com **Visual Studio**.

3.  Na *Configuração da Solução,* selecione **Depurar**.

4.  Na Plataforma *de Solução*, selecione **x86, Computador Remoto.** Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o HoloLens, nesse caso, que você anotou).

    ![Definir endereço IP](images/AzureLabs-Lab302b-34.png)

5. Vá para **o** menu Criar e clique **em Implantar Solução** para fazer sideload do aplicativo em seu HoloLens.

6. Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser lançado!

> [!NOTE]
> Para implantar no headset imersivo,  de definir a Plataforma  de Solução como Computador *Local* e definir a Configuração como *Depurar*, com *x86* como a **Plataforma**. Em seguida, implante no computador local, usando o item **de** menu Build, *selecionando Implantar Solução*. 

## <a name="to-use-the-application"></a>Para usar o aplicativo:

Para alternar a  funcionalidade do  aplicativo entre o modo de treinamento e o modo de previsão, você precisa atualizar a variável **AppMode,** localizada no método **Awake()** localizado dentro da *classe ImageCapture.*

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
ou
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

No *modo de* treinamento:

- Veja Mouse **ou** **Teclado e** use o gesto **de toque**.

- Em seguida, será exibido um texto solicitando que você forneça uma marca.

- Digamos **mouse** ou **Teclado.**


No *modo de previsão:*

- Veja um objeto e use o gesto **de toque**.

- O texto será exibido fornecendo o objeto detectado, com a maior probabilidade (isso é normalizado).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Capítulo 14 – Avaliar e aprimorar seu Visão Personalizada modelo

Para tornar seu serviço mais preciso, você precisará continuar a treinar o modelo usado para previsão. Isso é feito por meio do uso de seu novo aplicativo, com os modos de *treinamento* e *previsão* , com o último, que exige que você visite o portal, que é o que é abordado neste capítulo. Esteja preparado para revisitar seu portal muitas vezes, para melhorar continuamente seu modelo.

1. Acesse o portal de Visão Personalizada do Azure novamente e, quando estiver em seu projeto, selecione a guia *previsões* (do centro superior da página):

    ![Selecione a guia previsões](images/AzureLabs-Lab302b-35.png)

2. Você verá todas as imagens que foram enviadas para o serviço enquanto o aplicativo estava em execução. Se você passar o mouse sobre as imagens, elas fornecerão as previsões que foram feitas para essa imagem:

    ![Lista de imagens de previsão](images/AzureLabs-Lab302b-36.png)

3. Selecione uma das imagens para abri-la. Uma vez aberto, você verá as previsões feitas para essa imagem à direita. Se as previsões estiverem corretas e você quiser adicionar essa imagem ao modelo de treinamento do serviço, clique na caixa de entrada *minhas marcas* e selecione a marca que deseja associar. Quando tiver terminado, clique no botão *salvar e fechar* na parte inferior direita e continue na próxima imagem.

    ![Selecionar imagem para abrir](images/AzureLabs-Lab302b-37.png)

4. Depois de voltar à grade de imagens, você notará que as imagens às quais você adicionou marcas (e salvas) serão removidas. Se você encontrar alguma imagem que ache que não tem seu item marcado dentro delas, poderá excluí-las clicando no tique nessa imagem (pode fazer isso para várias imagens) e, em seguida, clicando em *excluir* no canto superior direito da página de grade. No pop-up que segue, você pode clicar em *Sim, excluir* ou *não*, para confirmar a exclusão ou cancelá-la, respectivamente. 

    ![Excluir imagens](images/AzureLabs-Lab302b-38.png)

5. Quando você estiver pronto para continuar, clique no botão de *trem* verde no canto superior direito. Seu modelo de serviço será treinado com todas as imagens que você forneceu agora (o que o tornará mais preciso). Quando o treinamento for concluído, certifique-se de clicar no botão *tornar padrão* mais uma vez, para que sua *URL de previsão* continue a usar a iteração mais atualizada do seu serviço.

    ![Iniciar o modelo de serviço de treinamento ](images/AzureLabs-Lab302b-39.png) ![ selecione criar opção padrão](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Seu aplicativo de API Visão Personalizada concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita a API de Visão Personalizada do Azure para reconhecer objetos do mundo real, treinar o modelo de serviço e exibir a confiança do que foi visto.

![Exemplo de projeto concluído](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Treine sua **serviço de visão personalizada** para reconhecer mais objetos.

### <a name="exercise-2"></a>Exercício 2

Como uma maneira de expandir o que você aprendeu, conclua os seguintes exercícios:

Tocar um som quando um objeto for reconhecido.

### <a name="exercise-3"></a>Exercício 3

Use a API para treinar novamente seu serviço com as mesmas imagens que seu aplicativo está analisando, para tornar o serviço mais preciso (faça a previsão e o treinamento simultaneamente).