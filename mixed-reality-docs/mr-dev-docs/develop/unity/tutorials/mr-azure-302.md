---
title: HoloLens (1ª geração) e Azure 302 – Pesquisa Visual Computacional
description: Conclua este curso para saber como reconhecer o conteúdo visual em uma imagem fornecida, usando o Azure Pesquisa Visual Computacional em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realidade misturada, academy, unity, tutorial, api, pesquisa visual computacional, hololens, imersivo, vr, Windows 10, Visual Studio
ms.openlocfilehash: 5cac40c2613187776ea9ec5ba1268f1422a084d32322e9c4aca6742ed75d05b2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225898"
---
# <a name="hololens-1st-gen-and-azure-302-computer-vision"></a>HoloLens (1ª geração) e Azure 302: Visão computacional

<br>

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. Haverá uma nova série de tutoriais que serão postados no futuro que demonstrarão como desenvolver para HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles são postados.

<br>

Neste curso, você aprenderá a reconhecer o conteúdo visual em uma imagem fornecida usando as funcionalidades do Azure Pesquisa Visual Computacional em um aplicativo de realidade misturada.

Os resultados de reconhecimento serão exibidos como marcas descritivas. Você pode usar esse serviço sem a necessidade de treinar um modelo de machine learning. Se sua implementação exigir o treinamento de um modelo de machine learning, consulte [MR e Azure 302b](mr-azure-302b.md).

![resultado do laboratório](images/AzureLabs-Lab2-000.png)

O Microsoft Pesquisa Visual Computacional é um conjunto de APIs projetadas para fornecer aos desenvolvedores processamento e análise de imagens (com informações de retorno), usando algoritmos avançados, tudo da nuvem. Os desenvolvedores carregam uma URL de imagem ou imagem e os algoritmos da API do Microsoft Pesquisa Visual Computacional analisam o conteúdo visual, com base nas entradas escolhidas pelo usuário, que podem retornar informações, incluindo, identificar o tipo e a qualidade de uma imagem, detectar rostos humanos (retornando suas coordenadas) e marcar ou categorizar imagens. Para obter mais informações, visite a página [da API de Pesquisa Visual Computacional Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Depois de concluir este curso, você terá um aplicativo HoloLens realidade misturada, que poderá fazer o seguinte:

1.  Usando o gesto toque, a câmera do HoloLens capturará uma imagem.
2.  A imagem será enviada para o Serviço de API do Pesquisa Visual Computacional Azure. 
3.  Os objetos reconhecidos serão listados em um grupo de interface do usuário simples posicionado na Cena do Unity.

Em seu aplicativo, você deve saber como integrar os resultados ao seu design. Este curso foi projetado para ensinar como integrar um Serviço do Azure ao seu projeto do Unity. É seu trabalho usar o conhecimento que você ganha com este curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 302: Pesquisa Visual Computacional</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente no HoloLens, você também pode aplicar o que aprende neste curso a Windows Mixed Reality headsets imersivos (VR). Como os headsets imersivos (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao computador. Conforme você acompanha o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets imersivos (VR).

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
- Uma câmera conectada ao computador (para desenvolvimento de headset imersivo)
- Acesso à Internet para a configuração do Azure e Pesquisa Visual Computacional recuperação da API

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas ao criar este projeto, é fortemente sugerido que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas no tempo de build).
2.  Configurar e testar seu HoloLens. Se você precisar de suporte para configurar seu HoloLens, visite o [artigo HoloLens instalação do .](/hololens/hololens-setup) 
3.  É uma boa ideia executar Calibragem e Ajuste de Sensor ao começar a desenvolver um novo aplicativo HoloLens (às vezes, pode ajudar a executar essas tarefas para cada usuário). 

Para saber mais sobre Calibragem, siga este [link para o artigo HoloLens Calibragem.](/hololens/hololens-calibration#hololens-2)

Para saber mais sobre o Ajuste do Sensor, siga este [link para o HoloLens de Ajuste do Sensor .](/hololens/hololens-updates)

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1 – O Portal do Azure

Para usar o *Pesquisa Visual Computacional de API* do Azure, você precisará configurar uma instância do serviço para ser disponibilizada para seu aplicativo.

1.  Primeiro, faça logoff no [Portal do Azure.](https://portal.azure.com) 

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, precisará criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ajuda ao instrutor ou a um dos proctors para configurar sua nova conta.

2.  Quando você está conectado,  clique em Novo no canto superior esquerdo, pesquise a *API* Pesquisa Visual Computacional e clique em **Inserir**.

    ![Criar um novo recurso no Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > A palavra **Novo** pode ter sido substituída por **Criar um recurso**, em portais mais novos.
 
3.  A nova página fornecerá uma descrição do serviço *Pesquisa Visual Computacional API.* Na parte inferior esquerda desta página, selecione o **botão** Criar para criar uma associação com esse serviço.

    ![Sobre o serviço de API da Pesquisa Visual Computacional](images/AzureLabs-Lab2-01.png)
 
4.  Depois de clicar em **Criar**:

    1. Insira o Nome desejado **para** essa instância de serviço.
    2. Selecione uma **Assinatura**.
    3. Selecione o **Tipo de** Preço apropriado para você, se esta for a primeira vez que você cria um serviço de *API* Pesquisa Visual Computacional, uma camada gratuita (chamada F0) deverá estar disponível para você.
    4. Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses laboratórios) em um grupo de recursos comum. 

        > Se você quiser ler mais sobre os Grupos de Recursos do Azure, [visite o artigo do grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. Determine o Local do grupo de recursos (se você estiver criando um novo Grupo de Recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

    6. Você também precisará confirmar que entendeu os Termos e Condições aplicados a esse Serviço.
    7. Clique em Criar.

        ![Informações de criação de serviço](images/AzureLabs-Lab2-02.png)

5.  Depois de clicar em **Criar**, você terá que aguardar até que o serviço seja criado, isso pode levar um minuto.
6.  Uma notificação será exibida no portal depois que a instância de serviço for criada.

    ![Confira a nova notificação para o novo serviço](images/AzureLabs-Lab2-03.png) 
 
7.  Clique na notificação para explorar sua nova instância de serviço. 

    ![Selecione o botão Ir para Recurso.](images/AzureLabs-Lab2-04.png)
 
8. Clique no **botão Ir para o** recurso na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância de serviço Pesquisa Visual Computacional API. 

    ![Sua nova imagem Pesquisa Visual Computacional serviço de API do Pesquisa Visual Computacional](images/AzureLabs-Lab2-05.png)
 
9.  Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito usando a Chave de Assinatura do serviço.
10. Na  página Início rápido, do serviço de API do *Pesquisa Visual Computacional,* navegue até a primeira *etapa,* Pegue suas chaves e clique em Chaves **(você** também pode fazer isso clicando nas Teclas de hiperlink azul, localizadas no menu de navegação de serviços, anotadas pelo ícone de chave). Isso revelará suas chaves *de serviço.*
11. Fazer uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto. 

12. Go back página *Início* rápido e, a partir daí, busque seu ponto de extremidade. Esteja ciente de que o seu pode ser diferente, dependendo da sua região (que, se for, você precisará fazer uma alteração no código mais tarde). Fazer uma cópia desse ponto de extremidade para uso posterior:

    ![Seu novo serviço Pesquisa Visual Computacional API](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Você pode verificar quais são os vários pontos de extremidade [AQUI.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2 – Configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra *o Unity* e clique em **Novo.** 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab2-06.png)

2.  Agora você precisará fornecer um nome de Project Unity. Insira **MR_ComputerVision**. Certifique-se de que o tipo de projeto está definido **como 3D.** De definir **o Local** como em algum lugar apropriado para você (lembre-se de que mais próximo dos diretórios raiz é melhor). Em seguida, clique **em Criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab2-07.png)

3.  Com o Unity aberto, vale a pena verificar se o **Editor de Script** padrão está definido como **Visual Studio**. Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **Ferramentas Externas.** Altere **Editor de Script** Externo para Visual Studio **2017.** Feche a **janela Preferências.**

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab2-08.png)

4.  Em seguida, vá para Arquivo **> Criar Configurações** e selecione Plataforma **universal** Windows e clique no botão Alternar **Plataforma** para aplicar sua seleção.

    ![Criar Configurações janela, alternar plataforma para UWP.](images/AzureLabs-Lab2-10.png)

5.  Ainda em Arquivo **> Criar Configurações** e certifique-se de que:

    1. **O dispositivo de** destino está definido **como HoloLens**

        > Para os headsets imersivos, de definido **Dispositivo de Destino** como Qualquer *Dispositivo.*

    2. **O tipo de** build é definido como **D3D**
    3. **O SDK** está definido como **Mais recente instalado**
    4. **Visual Studio versão é** definida como **Mais recente instalada**
    5. **Build e Executar** são definidos como **Computador Local**
    6. Salve a cena e adicione-a ao build.

        1. Faça isso selecionando **Adicionar Cenas Abertas.** Uma janela salvar será exibida.
        
            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab2-11.png)

        2. Crie uma nova pasta para essa cena e,  em qualquer futuro, selecione o botão Nova pasta, para criar uma nova pasta, nomeá-la **Cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab2-12.png)

        3. Abra a pasta **Cenas** recém-criada e, em seguida, no campo Nome do arquivo *:* texto, digite **MR_ComputerVisionScene** e clique em **Salvar**.

            ![Dê um nome à nova cena.](images/AzureLabs-Lab2-13.png)

            > Esteja ciente de que você deve salvar suas cenas do Unity dentro da pasta *Ativos,* pois elas devem ser associadas ao unity Project. A criação da pasta scenes (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.

    7. As configurações restantes, em *Build Configurações*, devem ser deixadas como padrão por enquanto.

6. Na janela *Criar Configurações,* clique no botão **Player Configurações,** isso abrirá o painel relacionado no espaço em que o *Inspetor* está localizado. 

    ![Abra as configurações do player.](images/AzureLabs-Lab2-14.png)

7. Neste painel, algumas configurações precisam ser verificadas:

    1. Na guia **Outros Configurações:**

        1. **A versão do Runtime de Script** deve ser **estável** (equivalente ao .NET 3.5).
        2. **Back-end de script** deve ser **.NET**
        3. **O nível de compatibilidade da API** deve ser **.NET 4.6**

            ![Atualize outras configurações.](images/AzureLabs-Lab2-15.png)
      
    2. Na guia **Publicação Configurações,** em **Funcionalidades,** verifique:

        1. **InternetClient**
        2. **Webcam**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab2-16.png)

    3. Mais abaixo no painel, no **XR Configurações** (encontrado abaixo de **Publicar Configurações**), marque Realidade **Virtual** Com Suporte , certifique-se de que o **SDK** Windows Mixed Reality seja adicionado.

        ![Atualize o X R Configurações.](images/AzureLabs-Lab2-17.png)

8.  De volta *ao Build Configurações* projetos _C#_ do Unity não está mais es cinza; marque a caixa de seleção ao lado disso. 
9.  Feche a janela Configurações de Build.
10. Salve sua cena e Project (**ARQUIVO > SALVAR CENA/ARQUIVO > SALVAR PROJETO).**

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3 – Instalação da câmera principal

> [!IMPORTANT]
> Se você quiser ignorar o componente Configurar o *Unity* deste curso e continuar diretamente no código, sinta-se [](https://docs.unity3d.com/Manual/AssetPackages.html)à vontade para baixar esse [.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)importá-lo para seu projeto como um Pacote Personalizado e, em seguida, continuar do [Capítulo 5.](#chapter-5--create-the-resultslabel-class)

1.  No Painel *hierarquia*, selecione a **Câmera Principal**. 
2.  Depois de selecionado, você poderá ver todos os componentes da **Câmera Principal** no Painel *inspetor.*

    1. O **objeto Camera deve** ser nomeado Câmera **Principal** (observe a ortografia!)
    2. A Marca da Câmera **Principal** deve ser definida como **MainCamera** (observe a ortografia!)
    3. Certifique-se **de que a Posição da** Transformação está definida como **0, 0, 0**
    4. Definir **Limpar Sinalizadores como** Cor **Sólida** (ignore isso para headset imersivo).
    5. De **definir** a cor da tela de fundo do componente de câmera como **Preto, Alfa 0 (Código Hexa #00000000)** (ignore isso para headset imersivo).

        ![Atualizar componentes da câmera.](images/AzureLabs-Lab2-18.png)
 
3.  Em seguida, você terá que criar um objeto "Cursor" simples anexado à Câmera **Principal,** que ajudará você a posicionar a saída da análise de imagem quando o aplicativo estiver em execução. Esse Cursor determinará o ponto central do foco da câmera.

Para criar o Cursor:

1.  No Painel *hierarquia*, clique com o botão direito do mouse na **Câmera Principal**. Em **Objeto 3D**, clique em **Sphere**.

    ![Selecione o Objeto de Cursor.](images/AzureLabs-Lab2-19.png)
 
2.  Renomeie a **Esfera** como **Cursor** (clique duas vezes no objeto Cursor ou pressione o botão de teclado 'F2' com o objeto selecionado) e certifique-se de que ele esteja localizado como filho da **Câmera Principal.**

3.  No Painel *hierarquia*, clique com o botão esquerdo do **mouse no Cursor**. Com o Cursor selecionado, ajuste as seguintes variáveis no Painel *inspetor*:

    1. Definir a *posição de transformação* como **0, 0, 5**
    2. Definir a *escala* **como 0,02, 0,02, 0,02**

        ![Atualize a Posição e a Escala da Transformação.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capítulo 4 – Configurar o sistema de rótulos

Depois de capturar uma imagem com a câmera HoloLens, essa imagem será enviada à instância do Serviço de API do *Azure Pesquisa Visual Computacional* para análise. 

Os resultados dessa análise serão uma lista de objetos reconhecidos chamados **Marcas**. 

Você usará Rótulos (como um texto 3D no espaço mundial) para exibir essas Marcas no local em que a foto foi tirada.

As etapas a seguir mostrarão como configurar o **objeto** Label.

1.  Clique com o botão direito do mouse em qualquer lugar no Painel de Hierarquia (o local não importa neste ponto), em **Objeto 3D**, adicione um **Texto 3D**. **Nomeia-o Como LabelText.**

    ![Criar objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  No Painel *hierarquia*, clique com o botão esquerdo do **mouse em LabelText.** Com o **LabelText selecionado,** ajuste as seguintes variáveis no *Painel inspetor*:

    1. Definir a **Posição** **como 0,0,0**
    2. Definir a **escala** **como 0,01, 0,01, 0,01**
    3. Na Malha **de Texto do componente**:
    4. Substitua todo o texto em **Texto** por "..."        
    5. Definir a **âncora** como **Centro Central**
    6. Definir o **Alinhamento** como **Centro**
    7. Definir o **tamanho da guia** como **4**
    8. Definir o **tamanho da fonte** como **50**
    9. Definir a **cor** como **#FFFFFFFF**

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  Arraste o **LabelText** do Painel *de Hierarquia* para a Pasta *do Ativo*, no painel *Project .* Isso fará do **LabelText** um Prefab, de modo que ele possa ser instariado no código.

    ![Crie um pré-fab do objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  Você deve excluir **o LabelText** do Painel *de Hierarquia* para que ele não seja exibido na cena de abertura. Como agora é um pré-fab, que você chamará para instâncias individuais da pasta Ativos, não é necessário mantê-lo dentro da cena. 
5.  A estrutura de objeto final no *Painel de Hierarquia* deve ser como a mostrada na imagem abaixo:

    ![Estrutura final do painel de hierarquia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capítulo 5 – Criar a classe ResultsLabel

O primeiro script que você precisa criar é a *classe ResultsLabel,* que é responsável pelo seguinte: 

- Criando os rótulos no espaço do mundo apropriado, em relação à posição da câmera.
- Exibindo as marcas da imagem Analysis.

Para criar esta classe: 

1.  clique com o botão direito do mouse no *painel de Project* e **crie > pasta**. Nomeie a pasta **scripts**. 

    ![Criar pasta de scripts.](images/AzureLabs-Lab2-24.png)

2.  Com a pasta **scripts** Create, clique duas vezes nela para abrir. Em seguida, dentro dessa pasta, clique com o botão direito do mouse e selecione **criar >** em seguida **script C#**. Nomeie o script *ResultsLabel*. 

3.  Clique duas vezes no novo script *ResultsLabel* para abri-lo com **Visual Studio**.

4.  Dentro da classe, insira o seguinte código na classe *ResultsLabel* :

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.
7.  De volta ao *Editor do Unity*, clique e arraste a classe *ResultsLabel* da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.
8.  Clique na **câmera principal** e examine o *painel Inspetor*.

Você observará que, a partir do script que acabou de arrastar para a câmera, há dois campos: **cursor** e **Label pré-fabricado**.

9.  Arraste o objeto chamado **cursor** do *painel hierarquia* para o slot chamado **cursor**, conforme mostrado na imagem abaixo.
10. arraste o objeto chamado **LabelText** da *pasta ativos* no painel de *Project* para o slot chamado **rótulo pré-fabricado**, conforme mostrado na imagem abaixo. 

    ![Defina os destinos de referência no Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capítulo 6 – criar a classe ImageCapture

A próxima classe que você vai criar é a classe *ImageCapture* . Essa classe é responsável por:

-   capturando uma imagem usando a câmera de HoloLens e armazenando-a na pasta do aplicativo.
-   Capturando gestos de toque do usuário.

Para criar esta classe: 

1.  Vá para a pasta **scripts** que você criou anteriormente. 
2.  Clique com o botão direito do mouse dentro da pasta, **crie > script C#**. Chame o script *ImageCapture*. 
3.  Clique duas vezes no novo script *ImageCapture* para abri-lo com **Visual Studio**.
4.  Adicione os seguintes namespaces à parte superior do arquivo:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe *ImageCapture* , acima do método *Start ()* :

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
A variável **tapsCount** armazenará o número de gestos de toque capturados do usuário. Esse número é usado na nomenclatura das imagens capturadas.

6.  O código para os métodos *ativo ()* e *Iniciar ()* agora precisa ser adicionado. Eles serão chamados quando a classe for inicializada:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implemente um manipulador que será chamado quando ocorrer um gesto de toque. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
O método *TapHandler ()* incrementa o número de toques capturados do usuário e usa a posição atual do cursor para determinar onde posicionar um novo rótulo.

Esse método chama o método *ExecuteImageCaptureAndAnalysis ()* para iniciar a funcionalidade principal deste aplicativo.

8.  Depois que uma imagem for capturada e armazenada, os seguintes manipuladores serão chamados. Se o processo for bem-sucedido, o resultado será passado para o *visionmanager* (que você ainda deseja criar) para análise.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  Em seguida, adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> Neste ponto, você observará um erro exibido no *painel de console do editor do Unity*. Isso ocorre porque o código faz referência à classe *visionmanager* que você criará no próximo capítulo.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capítulo 7 – chamar o Azure e a análise de imagem

O último script que você precisa criar é a classe *visionmanager* . 

Essa classe é responsável por:

-   Carregando a imagem mais recente capturada como uma matriz de bytes.
-   Enviando a matriz de bytes para a instância do serviço de *API da pesquisa Visual computacional do Azure* para análise.
-   Recebendo a resposta como uma cadeia de caracteres JSON.
-   Desserializar a resposta e passar as marcas resultantes para a classe *ResultsLabel* .
 
Para criar esta classe:

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > script C#**. Nomeie o script *visionmanager*. 
3.  Clique duas vezes no novo script para abri-lo com Visual Studio.
4.  Atualize os namespaces para que sejam iguais aos seguintes, na parte superior da classe *visionmanager* :

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  Na parte superior do seu script, *dentro* da classe *visionmanager* (acima do método *Start ()* ), agora você precisa criar duas *classes* que irão representar a resposta JSON desserializada do Azure:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > As classes *TagData* e *AnalysedObject* precisam ter o atributo *[System. Serializable]* adicionado antes que a declaração possa ser desserializada com as bibliotecas do Unity.

6.  Na classe Visionmanager, você deve adicionar as seguintes variáveis:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Certifique-se de inserir sua **chave de autenticação** na variável **authorizationKey** . Você terá anotado sua **chave de autenticação** no início deste curso, [capítulo 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > A variável **visionAnalysisEndpoint** pode ser diferente da especificada neste exemplo. O **oeste-US** se refere estritamente a instâncias de serviço criadas para a região oeste dos EUA. Atualize isso com a [URL do ponto de extremidade](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); Aqui estão alguns exemplos de como isso pode ser:
    > - Europa Ocidental: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Sudeste da Ásia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Leste da Austrália: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  O código para ativo agora precisa ser adicionado. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Em seguida, adicione a corrotina (com o método de fluxo estático abaixo dela), que obterá os resultados da análise da imagem capturada pela classe *ImageCapture* . 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  certifique-se de salvar as alterações em *Visual Studio* antes de retornar ao *Unity*.
10. De volta ao editor do Unity, clique e arraste as classes *visionmanager* e *ImageCapture* da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*. 

## <a name="chapter-8--before-building"></a>Capítulo 8 – antes de Compilar

Para executar um teste completo de seu aplicativo, você precisará Sideload-lo em seu HoloLens.
Antes de fazer isso, verifique se:

-   Todas as configurações mencionadas no [capítulo 2](#chapter-2--set-up-the-unity-project) estão definidas corretamente. 
-   Todos os scripts são anexados ao objeto da **câmera principal** . 
-   Todos os campos no *painel principal do Inspetor de câmera* são atribuídos corretamente.
-   Certifique-se de inserir sua **chave de autenticação** na variável **authorizationKey** .
-   Verifique se você também verificou seu ponto de extremidade em seu script do *visionmanager* e se ele está alinhado à *sua* região (este documento usa o *Oeste-EUA* por padrão).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capítulo 9 – criar a solução UWP e sideloadr o aplicativo
Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.

1.  navegue até *criar Configurações*  -  **arquivo > build Configurações...**
2.  na janela *build Configurações* , clique em **compilar**.

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab2-26.png)

3.  Se ainda não estiver, **projetos do Tick Unity C#**.
4.  Clique em **Compilar**. O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora e nomeie-a como *aplicativo*. Em seguida, com a pasta de *aplicativo* selecionada, pressione **Selecionar pasta**. 
5.  O Unity começará a criar seu projeto na pasta do *aplicativo* . 
6.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do *Explorador de arquivos* no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

## <a name="chapter-10--deploy-to-hololens"></a>Capítulo 10 – implantar no HoloLens

Para implantar no HoloLens:

1.  você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que o HoloLens esteja no **modo de desenvolvedor**. Para fazer isso:

    1. enquanto estiver desgastando seu HoloLens, abra o **Configurações**.
    2. Vá para **rede & Internet > Wi-Fi > opções avançadas**
    3. Anote o endereço **IPv4** .
    4. em seguida, navegue de volta para **Configurações** e, em seguida, **atualize & > de segurança para desenvolvedores** 
    5. Defina o modo de desenvolvedor em.

2.  Navegue até sua nova compilação do Unity (a pasta do *aplicativo* ) e abra o arquivo de solução com *Visual Studio*.
3.  Na Configuração da Solução, selecione **Depurar**.
4.  Na Plataforma de Solução, selecione **x86**, **Computador Remoto.** 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Vá para o **menu Build e** clique em Implantar **Solução** para fazer sideload do aplicativo em seu HoloLens.
6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser lançado!

> [!NOTE]
> Para implantar no headset imersivo,  de definir a Plataforma  de Solução como Computador *Local* e definir a Configuração como *Depurar*, com *x86* como a **Plataforma**. Em seguida, implante no computador local, usando o **menu Build**, *selecionando Implantar Solução*. 

## <a name="your-finished-computer-vision-api-application"></a>Seu aplicativo de API Pesquisa Visual Computacional concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita a API de Pesquisa Visual Computacional do Azure para reconhecer objetos do mundo real e exibir a confiança do que foi visto.

![resultado do laboratório](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Assim como você usou o parâmetro *Tags*  (conforme evidência no ponto de extremidade usado no *VisionManager),* estenda o aplicativo para detectar outras informações; veja quais outros parâmetros você tem acesso a [AQUI.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)

### <a name="exercise-2"></a>Exercício 2

Exibir os dados retornados do Azure, de maneira mais conversacional e acessível, talvez ocultando os números. Como se um bot pudesse estar falando com o usuário.