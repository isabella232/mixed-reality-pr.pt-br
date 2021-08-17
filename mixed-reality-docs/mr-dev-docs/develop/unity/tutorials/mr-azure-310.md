---
title: HoloLens (1ª geração) e Azure 310 – Detecção de objetos
description: Conclua este curso para aprender a treinar e usar um modelo de machine learning para reconhecer objetos semelhantes e sua posição no mundo real.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, visão personalizada, detecção de objetos, realidade misturada, academy, unity, tutorial, API, hololens, Windows 10, Visual Studio
ms.openlocfilehash: b152aaebbd3858140b79133a8f8e551aab06b4f3
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905744"
---
# <a name="hololens-1st-gen-and-azure-310-object-detection"></a>HoloLens (1ª geração) e Azure 310: Detecção de objetos

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. Haverá uma nova série de tutoriais que serão postados no futuro que demonstrarão como desenvolver para HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles são postados.

<br>

Neste curso, você aprenderá a reconhecer o conteúdo visual personalizado e sua posição espacial dentro de uma imagem fornecida, usando as funcionalidades do Azure Visão Personalizada "Detecção de Objetos" em um aplicativo de realidade misturada.

Esse serviço permitirá que você treine um modelo de machine learning usando imagens de objeto. Em seguida, você usará o modelo treinado para reconhecer objetos semelhantes e aproximar sua localização no mundo real, conforme fornecido pela captura de câmera do Microsoft HoloLens ou uma conexão de câmera a um PC para headsets imersivos (VR).

![resultado do curso](images/AzureLabs-Lab310-00.png)

**Azure Visão Personalizada, a** Detecção de Objetos é um Serviço da Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizados. Esses classificadores podem ser usados com novas imagens para detectar objetos dentro dessa nova imagem, fornecendo Limites de Caixa **dentro** da própria imagem. O Serviço fornece um portal online simples e fácil de usar para simplificar esse processo. Para obter mais informações, visite os seguintes links:

* [Página de Visão Personalizada Azure](/azure/cognitive-services/custom-vision-service/home)
* [Limites e cotas](/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Após a conclusão deste curso, você terá um aplicativo de realidade misturada que poderá fazer o seguinte:

1. O usuário poderá olhar *para* um objeto, que ele treinou usando o Serviço de Visão Personalizada do Azure, Detecção de Objetos.
2. O usuário usará o gesto *toque* para capturar uma imagem do que está vendo.
3. O aplicativo enviará a imagem para o Serviço de Visão Personalizada Azure.
4. Haverá uma resposta do Serviço que exibirá o resultado do reconhecimento como texto de espaço no mundo. Isso será feito utilizando o Acompanhamento Espacial do Microsoft HoloLens, como uma maneira de entender a  posição do mundo do objeto reconhecido e, em seguida, usando a Marca associada ao que é detectado na imagem, para fornecer o texto do rótulo.

O curso também abrange o carregamento manual de imagens, a criação de marcas e o treinamento do  Serviço para reconhecer objetos diferentes (no exemplo fornecido, uma xícara) definindo a Caixa de Limite dentro da imagem que você enviar.

> [!IMPORTANT]
> Após a criação e o uso do aplicativo, o desenvolvedor deve navegar de volta para o Serviço de Visão Personalizada do Azure e identificar as previsões feitas pelo Serviço e determinar se elas estavam corretas ou não (marcando qualquer coisa que o Serviço perdeu e ajustando as Caixas *Delimitadora).* Em seguida, o Serviço pode ser treinado de novo, o que aumentará a probabilidade de reconhecer objetos do mundo real.

Este curso ensinará como obter os resultados do Serviço de Visão Personalizada do Azure, Detecção de Objetos, em um aplicativo de exemplo baseado no Unity. Você pode aplicar esses conceitos a um aplicativo personalizado que você pode estar criando.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 310: detecção de objetos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com Unity e C#. Lembre-se também de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da redação (julho de 2018). Você é livre para usar o software [](../../install-the-tools.md) mais recente, conforme listado no artigo Instalar as ferramentas, embora não seja preciso assumir que as informações neste curso corresponderão perfeitamente ao que você encontrará em software mais recente do que o listado abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um computador de desenvolvimento
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](../../install-the-tools.md#installation-checklist-for-hololens)
- [O SDK Windows 10 mais recente](../../install-the-tools.md#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](../../install-the-tools.md#installation-checklist-for-hololens)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist-for-hololens)
- Um [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details) com o modo de desenvolvedor habilitado
- Acesso à Internet para a configuração do Azure e Visão Personalizada recuperação do serviço
-  Uma série de pelo menos quinze (15) imagens são necessárias) para cada objeto que você gostaria que o Visão Personalizada reconhecesse. Se desejar, você pode usar as imagens já fornecidas com este curso, [uma série de xícaras](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas ao criar este projeto, é fortemente sugerido que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas no tempo de build).
2.  Configurar e testar seu HoloLens. Se você precisar de suporte para isso, [visite o artigo HoloLens instalação do .](/hololens/hololens-setup)
3.  É uma boa ideia executar Calibragem e Ajuste de Sensor ao começar a desenvolver um novo aplicativo HoloLens (às vezes, pode ajudar a executar essas tarefas para cada usuário).

Para saber mais sobre Calibragem, siga este [link para o artigo HoloLens Calibragem.](/hololens/hololens-calibration#hololens-2)

Para saber mais sobre Ajuste do Sensor, siga este [link para o HoloLens de Ajuste do Sensor .](/hololens/hololens-updates)

## <a name="chapter-1---the-custom-vision-portal"></a>Capítulo 1 – O portal Visão Personalizada dados

Para usar o Serviço de Visão Personalizada do **Azure,** você precisará configurar uma instância dele para ser disponibilizada para seu aplicativo.

1.  Navegue [até a página principal Visão Personalizada **Serviço** de Visão Personalizada .](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)

2.  Clique em **Ponto de Partida**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Entre no portal de Visão Personalizada.

    ![](images/AzureLabs-Lab310-02.png)

4.  Se você ainda não tiver uma conta do Azure, precisará criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ajuda ao instrutor ou a um dos proctors para configurar sua nova conta.

5.  Depois de fazer logon pela primeira vez, você será solicitado com o painel *Termos de* Serviço. Clique na caixa de seleção *para concordar com os termos*. Em seguida, **clique em Concordo.**

    ![](images/AzureLabs-Lab310-03.png)

6.  Depois de concordar com os termos, agora você está na *seção Meus Projetos.* Clique em **Novo Project**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Uma guia será exibida no lado direito, o que solicitará que você especifique alguns campos para o projeto.

    1.  Inserir um nome para seu projeto

    2.  Inserir uma descrição para seu projeto (**Opcional**)

    3.  Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comum.

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Se você quiser ler mais sobre os Grupos de Recursos do [Azure, navegue até os Documentos associados](/azure/azure-resource-manager/resource-group-portal)

    4.  De definir os **Project como** Detecção de **Objetos (versão prévia)**.

8.  Depois de terminar, clique em **Criar projeto** e você será redirecionado para a página Visão Personalizada Projeto de Serviço.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2 – Treinar seu projeto Visão Personalizada projeto

Uma vez no portal Visão Personalizada, seu objetivo principal é treinar seu projeto para reconhecer objetos específicos em imagens.

Você precisa de pelo menos quinze (15) imagens para cada objeto que você gostaria que seu aplicativo reconhecesse. Você pode usar as imagens fornecidas com este curso ([uma série de xícaras](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Para treinar seu Visão Personalizada projeto:

1.  Clique no botão **+** ao lado de **Marcas**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Adicione um **nome** para a marca que será usada para associar suas imagens. Neste exemplo, estamos usando imagens de xícaras para reconhecimento, portanto, nomeemos a marca para isso, **Cup**. Clique **em Salvar** quando terminar.

    ![](images/AzureLabs-Lab310-07.png)

3.  Você observará que **sua Marca** foi adicionada (talvez seja necessário recarregar sua página para que ela seja exibida). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Clique em **Adicionar imagens** no centro da página.

    ![](images/AzureLabs-Lab310-09.png)

5.  Clique em **Procurar arquivos locais** e navegue até as imagens que você gostaria de carregar para um objeto, com o mínimo de quinze (15).

    > [!TIP]
    >  Você pode selecionar várias imagens por vez para carregar.

    ![](images/AzureLabs-Lab310-10.png)

6.  Pressione **Upload arquivos** depois de selecionar todas as imagens com as que você gostaria de treinar o projeto. Os arquivos começarão a ser carregados. Depois de confirmar o upload, clique em **Feito.**

    ![](images/AzureLabs-Lab310-11.png)

7.  Neste ponto, suas imagens são carregadas, mas não marcadas.

    ![](images/AzureLabs-Lab310-12.png)

8.  Para marcar suas imagens, use o mouse. À medida que você passar o mouse sobre sua imagem, um realçando de seleção o auxiliará desenhando automaticamente uma seleção em torno do objeto. Se não for preciso, você poderá desenhar seu próprio. Isso é feito mantendo o clique com o botão esquerdo do mouse e arrastando a região de seleção para abranger o objeto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Após a seleção do objeto dentro da imagem, um pequeno prompt solicitará que você *adicione a Marca de Região.* Selecione a marca criada anteriormente ('Cup', no exemplo acima) ou, se você estiver adicionando mais marcas, digite-a e clique no **botão + (adição).**

    ![](images/AzureLabs-Lab310-14.png) 

10. Para marcar a próxima imagem, você pode clicar na seta à direita da folha ou fechar a folha de marca (clicando no **X** no canto superior direito da folha) e, em seguida, clicar na próxima imagem. Quando a próxima imagem estiver pronta, repita o mesmo procedimento. Faça isso para todas as imagens que você carregou, até que todas elas sejam marcadas. 

    > [!NOTE]
    >  Você pode selecionar vários objetos na mesma imagem, como a imagem abaixo: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Depois de marcar todos eles,  clique no botão marcado, à esquerda da tela, para revelar as imagens marcadas. 

    ![](images/AzureLabs-Lab310-16.png)

12. Agora você está pronto para treinar seu Serviço. Clique no **botão Treinar** e a primeira iteração de treinamento será iniciada.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Depois que ele for criado, você poderá ver dois botões chamados **Tornar padrão e** URL de **Previsão.** Clique em **Tornar padrão primeiro** e, em seguida, clique em URL de **Previsão.**

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > O ponto de extremidade fornecido com isso é definido como qualquer *iteração* que tenha sido marcada como padrão. Assim, se você posteriormente fizer uma *nova Iteração* e atualizá-la como padrão, não precisará alterar seu código.

14. Depois de clicar na **URL** de Previsão, abra *Bloco de notas* e copie a **URL** (também chamada de Ponto de Extremidade de Previsão ) e a Chave de Previsão do Serviço , para que você possa **recuperá-la** quando precisar dela mais tarde no código. 

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3 – Configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra **o Unity** e clique em **Novo.**

    ![](images/AzureLabs-Lab310-21.png)

2.  Agora você precisará fornecer um nome de projeto do Unity. Insira **CustomVisionObjDetection.** Certifique-se de que o tipo de projeto está definido como **3D** e de definir o **Local** como em algum lugar apropriado para você (lembre-se de que mais próximo dos diretórios raiz é melhor). Em seguida, clique **em Criar projeto**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Com o Unity aberto, vale a pena verificar se o **Editor de Script** padrão está definido como **Visual Studio**. Vá para **Editar*  >  *Preferências** e, em seguida, na nova janela, navegue até **Ferramentas Externas.** Altere **Editor de Script Externo** para **Visual Studio**. Feche a **janela Preferências.**

    ![](images/AzureLabs-Lab310-23.png)

4.  Em seguida, vá para Arquivo **> Criar** Configurações  e alternar a Plataforma para Plataforma Universal Windows *Plataforma* e, em seguida, clique no botão **Alternar Plataforma.**

    ![](images/AzureLabs-Lab310-24.png)

5.  Na mesma janela **Criar Configurações,** verifique se o seguinte está definido:

    1.  **O dispositivo de** destino está definido **como HoloLens**        
    2.  **O tipo de** build é definido como **D3D**
    3.  **O SDK** está definido como **Mais recente instalado**
    4.  **Visual Studio versão é** definida como **Mais recente instalada**
    5.  **Build e Executar** são definidos como **Computador Local**            
    6.  As configurações restantes, em **Build Configurações**, devem ser deixadas como padrão por enquanto.

        ![](images/AzureLabs-Lab310-25.png)

6.  Na mesma **janela Criar Configurações,** clique no botão **Player Configurações,** isso abrirá o painel relacionado no espaço em que o **Inspetor** está localizado.

7. Neste painel, algumas configurações precisam ser verificadas:

    1.  Na guia **Outros Configurações:**

        1.  **A versão do Runtime de Script** deve ser **Experimental** (equivalente ao .NET 4.6), o que disparará a necessidade de reiniciar o Editor.

        2. **Back-end de script** deve ser **.NET.**

        3. **O nível de compatibilidade da API** deve **ser .NET 4.6.**

            ![](images/AzureLabs-Lab310-26.png)

    2.  Na guia **Configurações** publicação, em **Funcionalidades,** verifique:

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Mais abaixo no painel, no **XR Configurações** (encontrado abaixo de **Publicar Configurações**), marque **Realidade Virtual** Com Suporte e, em seguida, certifique-se de que o **SDK** Windows Mixed Reality seja adicionado.

        ![](images/AzureLabs-Lab310-29.png)

8.  De volta **ao Build Configurações**, os Projetos C *\# do Unity* não estão mais es cinzas: marque a caixa de seleção ao lado disso.

9.  Feche a janela **Configurações de Build**.

10. No **Editor**, clique em **Editar**  >  **Project Configurações**  >  **Gráficos**.

    ![](images/AzureLabs-Lab310-30.png)

11. No Painel **inspetor,** os *gráficos Configurações* serão abertos. Scroll down até que você veja uma matriz chamada **Sempre Incluir Sombreadores**. Adicione um slot aumentando a variável **Tamanho** em um (neste exemplo, era 8, portanto, a fizemos 9). Um novo slot será exibido, na última posição da matriz, conforme mostrado abaixo:

    ![](images/AzureLabs-Lab310-31.png)

12. No slot, clique no círculo de destino pequeno ao lado do slot para abrir uma lista de sombreadores. Procure o **sombreador Herdado/Transparente/Difuso** e clique duas vezes nele. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capítulo 4 – Importando o pacote do Unity CustomVisionObjDetection

Para este curso, você é fornecido com um Pacote de Ativos do Unity **chamado Azure-MR-310.unitypackage**. 

> [DICA] Todos os objetos com suporte do Unity, incluindo cenas inteiras, podem ser empacotados em um **arquivo .unitypackage** e exportados/importados em outros projetos. É a maneira mais segura e eficiente de mover ativos entre diferentes **projetos do Unity.**

Você pode encontrar o [pacote Azure-MR-310 que você precisa baixar aqui.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)

1.  Com o painel do Unity na  sua frente, clique em **Ativos** no menu na parte superior da tela e clique em Importar Pacote > Pacote Personalizado .

    ![](images/AzureLabs-Lab310-33.png)

2.  Use o seletor de arquivos para selecionar **o pacote Azure-MR-310.unitypackage** e clique em **Abrir**. Uma lista de componentes para esse ativo será exibida para você. Confirme a importação clicando no **botão** Importar.

    ![](images/AzureLabs-Lab310-34.png)

3.  Depois de terminar a importação, você observará que as pastas do pacote agora foram adicionadas à pasta **Ativos.** Esse tipo de estrutura de pastas é típico para um projeto do Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  A **pasta Materiais** contém o material usado pelo **Cursor de Gaze.** 

    2.  A **pasta Plug-ins** contém a DLL newtonsoft usada pelo código para desterializar a resposta web do serviço. As duas (2) versões diferentes contidas na pasta e na subpa pasta são necessárias para permitir que a biblioteca seja usada e criada pelo Editor do Unity e pelo build UWP. 

    3.  A **pasta Prefabs** contém os pré-requisitos contidos na cena. Eles são:

        1.  O **GazeCursor**, o cursor usado no aplicativo. Trabalhará em conjunto com o pré-fab SpatialMapping para ser capaz de ser colocado na cena sobre objetos físicos.
        2.  O **Rótulo**, que é o objeto de interface do usuário usado para exibir a marca de objeto na cena quando necessário.
        3.  **SpatialMapping**, que é o objeto que permite que o aplicativo use criar um mapa virtual, usando o Microsoft HoloLens do controle espacial.

    4.  A **pasta Cenas** que atualmente contém a cena pré-criada para este curso.

4.  Abra a **pasta Cenas,** no painel **Project ,** e clique duas vezes no **ObjDetectionScene** para carregar a cena que você usará para este curso.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Nenhum código está incluído,** você escreverá o código seguindo este curso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capítulo 5 – Criar a classe CustomVisionAnalyser.

Neste ponto, você está pronto para escrever algum código. Você começará com a **classe CustomVisionAnalyser.**

> [!NOTE]
> As chamadas para o **serviço Visão Personalizada**, feitas no código mostrado abaixo, são feitas usando a API REST **Visão Personalizada .** Usando isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante por conta própria). Esteja ciente de que a Microsoft **oferece Visão Personalizada SDK** que também pode ser usado para fazer chamadas ao Serviço. Para obter mais informações, visite [o Visão Personalizada SDK do .](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)

Essa classe é responsável por:

- Carregando a imagem mais recente capturada como uma matriz de bytes.

- Enviar a matriz de byte  para sua instância do Serviço Visão Personalizada Azure para análise.

- Recebendo a resposta como uma cadeia de caracteres JSON.

- Desselizando a resposta e passando  a Previsão resultante para a classe **SceneOrganiser,** que cuidará de como a resposta deve ser exibida.

Para criar esta classe:

1.  Clique com o botão direito **do** mouse na Pasta de **Ativos**, localizada no painel Project e clique **em Criar**  >  **Pasta**. Chame a pasta **Scripts**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Clique duas vezes na pasta recém-criada para abri-la.

3.  Clique com o botão direito do mouse dentro da pasta e clique **em Criar**  >  **\# Script C.** Nomeia o script **CustomVisionAnalyser.**

4.  Clique duas vezes no novo script **CustomVisionAnalyser** para abri-lo com **Visual Studio.**

5.  Certifique-se de que você tenha os seguintes namespaces referenciados na parte superior do arquivo:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  Na classe **CustomVisionAnalyser,** adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Insira a Chave de **Previsão do Serviço** na variável **predictionKey** e no ponto **de** extremidade de previsão na **variável predictionEndpoint.** Você os [copiou Bloco de notas anteriormente, no Capítulo 2, Etapa 14.](#chapter-2---training-your-custom-vision-project)

7.  O código **para o Awake()** agora precisa ser adicionado para inicializar a variável instance:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Adicione a coroutine (com o método **getImageAsByteArray()** estático abaixo dele), que obterá os resultados da análise da imagem, capturada pela **classe ImageCapture.**

    > [!NOTE]
    > Na **coroutine AnalyseImageCapture,** há uma chamada para a **classe SceneOrganiser** que você ainda deve criar. Portanto, **deixe essas linhas comentadas por enquanto.**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. **Exclua os** métodos **Start() e Update(),** pois eles não serão usados. 

10.  Salve as alterações no **Visual Studio**, antes de retornar ao **Unity.**

> [!IMPORTANT]
> Conforme mencionado anteriormente, não se preocupe com o código que pode parecer ter um erro, pois você fornecerá mais classes em breve, o que as corrigirá.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capítulo 6 – Criar a classe CustomVisionObjects

A classe que você criará agora é a **classe CustomVisionObjects.**

Esse script contém vários objetos usados por outras classes para serializar e desserlizar as chamadas feitas ao serviço Visão Personalizada.

Para criar esta classe:

1.  Clique com o botão direito do mouse **na pasta Scripts** e clique **em Criar**  >  **\# Script C.** Chame o script **CustomVisionObjects.**

2.  Clique duas vezes no novo script **CustomVisionObjects** para abri-lo com **Visual Studio.**

3.  Certifique-se de que você tenha os seguintes namespaces referenciados na parte superior do arquivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  **Exclua os métodos Start()** e **Update()** dentro da **classe CustomVisionObjects,** essa classe agora deve estar vazia.

    > [!WARNING]
    > É importante que você siga a próxima instrução com cuidado. Se você colocar as novas declarações de classe dentro da classe **CustomVisionObjects,** receberá erros de compilação no capítulo [10](#chapter-10---create-the-imagecapture-class), informando que **AnalysisRootObject** e **BoundingBox** não foram encontrados.

5.  Adicione as classes a *seguir fora* da **classe CustomVisionObjects.** Esses objetos são usados pela biblioteca **Newtonsoft** para serializar e serializar os dados de resposta:

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Salve as alterações no **Visual Studio**, antes de retornar ao **Unity.**

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capítulo 7 – Criar a classe SpatialMapping

Essa classe definirá o **Colisor de Mapeamento** Espacial na cena para poder detectar colisões entre objetos virtuais e objetos reais.

Para criar esta classe:

1.  Clique com o botão direito do mouse **na pasta Scripts** e clique **em Criar**  >  **\# Script C.** Chame o script **SpatialMapping.**

2.  Clique duas vezes no novo script **SpatialMapping** para abri-lo com **Visual Studio.**

3.  Certifique-se de que você tenha os seguintes namespaces referenciados acima da **classe SpatialMapping:**

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro **da classe SpatialMapping,** acima do **método Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Adicione **o Awake()** e **Start():**

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  **Exclua o método Update().**

7.  Salve as alterações no **Visual Studio**, antes de retornar ao **Unity.**


## <a name="chapter-8---create-the-gazecursor-class"></a>Capítulo 8 – Criar a classe GazeCursor

Essa classe é responsável por configurar o cursor no local correto no espaço real, fazendo uso do **SpatialMappingCollider**, criado no capítulo anterior.

Para criar esta classe:

1.  Clique com o botão direito do mouse **na pasta Scripts** e clique **em Criar**  >  **\# Script C.** Chamar o **gazecursor de script**

2.  Clique duas vezes no novo script **GazeCursor** para abri-lo com **Visual Studio.**

3.  Certifique-se de que você tenha o seguinte namespace referenciado acima da **classe GazeCursor:**

    ```csharp
    using UnityEngine;
    ```

4.  Em seguida, adicione a variável a seguir **dentro da classe GazeCursor,** acima do **método Start().** 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Atualize **o método Start()** com o seguinte código:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Atualize **o método Update()** com o seguinte código:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > Não se preocupe com o erro para que **a classe SceneOrganiser** não seja encontrada, você o criará no próximo capítulo.

7. Salve as alterações no **Visual Studio**, antes de retornar ao **Unity.**

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capítulo 9 – Criar a classe SceneOrganiser

Essa classe vai:

-   Configurar a *Câmera Principal anexando* os componentes apropriados a ela.

-   Quando um objeto é detectado, ele será responsável por calcular **sua** posição no mundo real e colocar um Rótulo de Marca próximo a ele com o Nome da Marca **apropriado.**    

Para criar esta classe:

1.  Clique com o botão direito do mouse **na pasta Scripts** e clique **em Criar**  >  **\# Script C.** Nomeia o script **SceneOrganiser**.

2.  Clique duas vezes no novo script **SceneOrganiser** para abri-lo com **Visual Studio.**

3.  Certifique-se de que você tenha os seguintes namespaces referenciados acima da **classe SceneOrganiser:**

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro **da classe SceneOrganiser,** acima do **método Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  **Exclua os** métodos **Start() e Update().**

6.  Sob as variáveis, adicione **o método Awake(),** que inicializa a classe e configura a cena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Adicione o **método PlaceAnalysisLabel(),** que insinuará o rótulo na cena (que, neste ponto, é invisível para o usuário).  Ele também coloca o quad (também invisível) em que a imagem é colocada e se sobrepõe ao mundo real. Isso é importante porque as coordenadas da caixa recuperadas do Serviço após a análise são rastreadas de volta para esse quad para determinar a localização aproximada do objeto no mundo real. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Adicione o **método FinaliseLabel().** Ele é responsável por:

    *   Definindo *o texto* Rótulo com a *Marca* da Previsão com a confiança mais alta.
    *   Chamar o cálculo da *Caixa Delimitada* no objeto quad, posicionado anteriormente e colocar o rótulo na cena.
    *   Ajustando a profundidade do rótulo usando um Raycast em direção à *Caixa Delimitante*, que deve colidir com o objeto no mundo real.
    * Redefinindo o processo de captura para permitir que o usuário capture outra imagem.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Adicione o **método CalculateBoundingBoxPosition(),** que hospeda vários  cálculos necessários para converter as coordenadas da Caixa Delimitante recuperadas do Serviço e recriá-las proporcionalmente no quad.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Salve as alterações no **Visual Studio**, antes de retornar ao **Unity.**

    > [!IMPORTANT]
    > Antes de continuar, abra a **classe CustomVisionAnalyser** e, dentro do  método **AnalyseLastImageCaptured(),** descomenta as seguintes linhas:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> Não se preocupe com a mensagem da classe **ImageCapture** 'não foi possível encontrar', você a criará no próximo capítulo.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capítulo 10 – Criar a classe ImageCapture

A próxima classe que você criará é a **classe ImageCapture.**

Essa classe é responsável por:

*   Capturando uma imagem usando a HoloLens e o armazenamento dela na *pasta* Aplicativo.
*   Manipulando *gestos* de toque do usuário.

Para criar esta classe:

1.  Vá para a **pasta Scripts** criada anteriormente.

2.  Clique com o botão direito do mouse dentro da pasta e clique **em Criar**  >  **\# Script C.** Nomeia o script **ImageCapture.**

3.  Clique duas vezes no novo script **ImageCapture** para abri-lo com **Visual Studio.**

4.  Substitua os namespaces na parte superior do arquivo pelo seguinte:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro **da classe ImageCapture,** acima do **método Start():**

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implemente um manipulador que será chamado quando ocorrer um gesto de toque:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Quando o cursor está **verde,** isso significa que a câmera está disponível para tirar a imagem. Quando o cursor está **vermelho,** isso significa que a câmera está ocupada.

8.  Adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e para quando ela estiver pronta para ser analisada. O resultado é passado para **o CustomVisionAnalyser para** análise.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Salve as alterações no **Visual Studio**, antes de retornar ao **Unity.**

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capítulo 11 – Configurando os scripts na cena

Agora que você escreveu todo o código necessário para este projeto, é hora de configurar os scripts na cena e nos pré-requisitos para que eles se comportem corretamente.

1.  No **Editor do Unity,** no Painel **hierarquia,** selecione a **Câmera Principal.**
2.  No Painel inspetor **,** com a Câmera  **Principal** selecionada, clique em Adicionar Componente e, em seguida, pesquise script **SceneOrganiser** e clique duas vezes para adicioná-lo.

    ![](images/AzureLabs-Lab310-38.png)

3.  No Painel Project , abra a pasta **Prefabs**, arraste  o pré-fab Rótulo para **a** área de entrada De destino de referência vazia Rótulo, no script  **SceneOrganiser** que você acabou de adicionar à Câmera Principal , conforme mostrado na imagem abaixo: 

    ![](images/AzureLabs-Lab310-39.png)

4.  No Painel **hierarquia**, selecione o **filho GazeCursor** da **Câmera Principal.**
5.  No Painel **inspetor**, com o **GazeCursor** selecionado, clique em Adicionar Componente e, em seguida, pesquise o script **GazeCursor** e clique duas vezes para adicioná-lo. 

    ![](images/AzureLabs-Lab310-40.png)

6.  Novamente, no **Painel de Hierarquia**, selecione o filho **SpatialMapping** da **Câmera Principal**.
7.  No Painel **inspetor**, com **SpatialMapping** selecionado, clique em Adicionar Componente e, em seguida, pesquise o script **SpatialMapping** e clique duas vezes para adicioná-lo.

    ![](images/AzureLabs-Lab310-41.png)

Os scripts restantes que você não definiu serão adicionados pelo código no script **SceneOrganiser,** durante o runtime.

## <a name="chapter-12---before-building"></a>Capítulo 12 – Antes de criar

Para executar um teste completo do seu aplicativo, você precisará fazer sideload dele em seu Microsoft HoloLens.

Antes de fazer isso, verifique se:

-  Todas as configurações mencionadas no [capítulo 3](#chapter-3---set-up-the-unity-project) estão definidas corretamente.
- O script **SceneOrganiser** é anexado ao objeto da **câmera principal** .
- O script **GazeCursor** é anexado ao objeto **GazeCursor** .
- O script **SpatialMapping** é anexado ao objeto **SpatialMapping** .
- No [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), etapa 6:

    - Certifique-se de inserir sua **chave de previsão de serviço** na variável **predictionKey** .
    - Você inseriu o **ponto de extremidade de previsão** na classe **predictionEndpoint** .

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capítulo 13-criar a solução UWP e Sideload seu aplicativo

Agora você está pronto para criar seu aplicativo como uma solução UWP que poderá ser implantada no Microsoft HoloLens. Para iniciar o processo de compilação:

1.  vá para **arquivo > Build Configurações**.

2.  **\# Projetos em tique Unity C**.

3.  Clique em **Adicionar cenas de abertura**. Isso adicionará a cena aberta no momento à compilação.

    ![](images/AzureLabs-Lab310-42.png)

4.  Clique em **Compilar**. O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora e nomeie-a como **aplicativo**. Em seguida, com a pasta de **aplicativo** selecionada, clique em **Selecionar pasta**.

5.  O Unity começará a criar seu projeto na pasta do **aplicativo** .

6.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

7.  para implantar o no Microsoft HoloLens, você precisará do endereço IP desse dispositivo (para implantação remota) e para garantir que ele também tenha o **modo de desenvolvedor** definido. Para fazer isso:

    1.  enquanto estiver desgastando seu HoloLens, abra o **Configurações**.

    2.  Vá para **rede &**  >  Opções avançadas **de Internet Wi-Fi**  >  

    3.  Anote o endereço **IPv4** .

    4.  em seguida, navegue de volta para **Configurações** e, em seguida, **atualize a segurança**  >  **do & para desenvolvedores**

    5.  Defina o **modo de desenvolvedor** *em*.

8.  Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com **Visual Studio**.

9.  Na configuração da solução, selecione **depurar**.

10. Na plataforma da solução, selecione **x86, computador remoto**. você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o Microsoft HoloLens, nesse caso, que você anotou).

    ![](images/AzureLabs-Lab310-43.png)

11. Vá para o menu **Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu HoloLens.

12. seu aplicativo agora deve aparecer na lista de aplicativos instalados na sua Microsoft HoloLens, pronto para ser iniciado!

### <a name="to-use-the-application"></a>Para usar o aplicativo:

* Examine um objeto, que você tem treinado com sua **serviço de visão personalizada do Azure, detecção de objetos** e use o **gesto de toque**.
* Se o objeto for detectado com êxito, um *texto de rótulo* de espaço mundial será exibido com o nome da marca.

> [!IMPORTANT]
> Sempre que você captura uma foto e a envia para o serviço, pode voltar para a página de serviço e treinar novamente o serviço com as imagens recentemente capturadas. No início, você provavelmente também precisará corrigir as *caixas delimitadores* para ser mais preciso e treinar novamente o serviço.

> [!NOTE]
> o texto do rótulo colocado pode não aparecer próximo ao objeto quando os sensores de Microsoft HoloLens e/ou o SpatialTrackingComponent no Unity falharem em colocar os colisor apropriados, em relação aos objetos do mundo real. Tente usar o aplicativo em uma superfície diferente, se esse for o caso.

## <a name="your-custom-vision-object-detection-application"></a>Seu Visão Personalizada, aplicativo de detecção de objeto

Parabéns, você criou um aplicativo de realidade misturada que aproveita o Visão Personalizada do Azure, a API de detecção de objeto, que pode reconhecer um objeto de uma imagem e, em seguida, fornecer uma posição aproximada para esse objeto no espaço 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Adicionando ao rótulo de texto, use um cubo semitransparente para encapsular o objeto real em uma *caixa delimitadora* 3D.

### <a name="exercise-2"></a>Exercício 2

Treine sua Serviço de Visão Personalizada para reconhecer mais objetos.

### <a name="exercise-3"></a>Exercício 3

Tocar um som quando um objeto for reconhecido.

### <a name="exercise-4"></a>Exercício 4

Use a API para treinar novamente seu serviço com as mesmas imagens que seu aplicativo está analisando, para tornar o serviço mais preciso (faça a previsão e o treinamento simultaneamente).
