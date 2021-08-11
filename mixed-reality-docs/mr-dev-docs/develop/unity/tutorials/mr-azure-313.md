---
title: HoloLens (1ª geração) e Azure 313 – Serviço de Hub IoT
description: Saiba como implementar o Hub IoT do Azure service em uma máquina virtual que executa o Ubuntu 16.4 e visualizar os dados da mensagem usando Microsoft HoloLens headset ou VR.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, mixed reality, academy, edge, iot edge, tutorial, api, notification, functions, tables, hololens, immersive, vr, iot, virtual machine, ubuntu, python, Windows 10, Visual Studio
ms.openlocfilehash: 0a9f1b7c42094b3c441bdb32082f6821f2fd43a1ce3339cf1f58e7bd0fcf8318
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194696"
---
# <a name="hololens-1st-gen-and-azure-313-iot-hub-service"></a>HoloLens (1ª geração) e Azure 313: Serviço do Hub IoT

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. Haverá uma nova série de tutoriais que serão postados no futuro que demonstrarão como desenvolver para HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles são postados.

![resultado do curso](images/AzureLabs-Lab313-00.png)

Neste curso, você aprenderá a implementar um **serviço Hub IoT do Azure em** uma máquina virtual que executa o sistema operacional Ubuntu 16.4. Um **Aplicativo de Funções do Azure** será usado para receber mensagens de sua VM do Ubuntu e armazenar o resultado em um Serviço de Tabela do **Azure.** Em seguida, você poderá exibir esses dados **usando Power BI** no Microsoft HoloLens ou headset imersivo (VR).

O conteúdo deste  curso é aplicável a IoT Edge dispositivos, embora para a finalidade deste curso, o foco será em um ambiente de máquina virtual, para que o acesso a um dispositivo físico do Edge não seja necessário.

Ao concluir este curso, você aprenderá a:

- Implante um **IoT Edge em** uma máquina virtual (so Ubuntu 16), que representará seu dispositivo IoT.
- Adicione um **Modelo Visão Personalizada Tensorflow do Azure** ao módulo do Edge, com o código que analisará as imagens armazenadas no contêiner.
- Configurar o módulo para enviar a mensagem de resultado da análise de volta para o Serviço do **Hub IoT.**
- Use um **Aplicativo de Funções do Azure** para armazenar a mensagem em uma Tabela do **Azure.**
- Configurar o **Power BI** para coletar a mensagem armazenada e criar um relatório.
- Visualize seus dados de mensagem de IoT **no Power BI**.

Os Serviços que você usará incluem:

- **Hub IoT do Azure** é um serviço Microsoft Azure que permite que os desenvolvedores se conectem, monitorem e gerenciem ativos de IoT. Para obter mais informações, visite a [ **página Hub IoT do Azure serviço** .](https://azure.microsoft.com/services/iot-hub/)

- **Registro de Contêiner do Azure** é um serviço Microsoft Azure que permite aos desenvolvedores armazenar imagens de contêiner para vários tipos de contêineres. Para obter mais informações, visite a [ **página Registro de Contêiner do Azure Service**](https://azure.microsoft.com/services/container-registry/).

- O Aplicativo de Funções do **Azure** é um serviço Microsoft Azure, que permite aos desenvolvedores executar pequenos trechos de código, 'funções', no Azure. Isso fornece uma maneira de delegar o trabalho para a nuvem, em vez de seu aplicativo local, o que pode ter muitos benefícios. **Azure Functions** dá suporte a várias linguagens de desenvolvimento, incluindo \# \# C, F, Node.js, Java e PHP. Para obter mais informações, visite a [ **página Azure Functions** .](/azure/azure-functions/functions-overview)

- **Azure Armazenamento:** tabelas é um serviço Microsoft Azure, que permite aos desenvolvedores armazenar dados estruturados, não SQL na nuvem, tornando-os facilmente acessíveis em qualquer lugar. O Serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível. Para obter mais informações, visite a [ **página Tabelas do Azure**](/azure/cosmos-db/table-storage-overview)

Este curso ensinará como configurar e usar o Serviço do Hub IoT e visualizar uma resposta fornecida por um dispositivo. Você pode aplicar esses conceitos a uma configuração personalizada do Serviço do Hub IoT, que você pode estar criando.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e Azure 313: serviço Hub IoT</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

Para os pré-requisitos mais atualizados para o desenvolvimento com realidade misturada, incluindo com o Microsoft HoloLens, visite o artigo Instalar [as](/windows/mixed-reality/install-the-tools) ferramentas.

> [!NOTE]
> Este tutorial foi projetado para desenvolvedores que têm experiência básica com o Python. Lembre-se também de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da redação (julho de 2018). Você é livre para usar o software [](../../install-the-tools.md) mais recente, conforme listado no artigo Instalar as ferramentas, embora não seja preciso assumir que as informações neste curso corresponderão perfeitamente ao que você encontrará em softwares mais recentes do que os listados abaixo.

O seguinte hardware e software é necessário:

- Windows 10 Fall Creators Update (ou posterior), Modo **de Desenvolvedor habilitado**

    > [!WARNING]
    > Não é possível executar uma Máquina Virtual usando o Hyper-V no Windows 10 Home Edition.

- Windows 10 SDK (versão mais recente)
- Um HoloLens, **modo de desenvolvedor habilitado**
- Visual Studio 2017.15.4 (usado apenas para acessar o Azure Cloud Explorer)
- Acesso à Internet para o Azure e para o Serviço do Hub IoT. Para obter mais informações, siga este [link para a página Serviço do Hub IoT](https://azure.microsoft.com/services/iot-hub/)
- Um modelo de machine learning. Se você não tiver seu próprio modelo pronto para usar, [poderá usar o modelo fornecido com este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- **Software Hyper-V** habilitado em seu computador de Windows 10 desenvolvimento.
- Uma Máquina Virtual executando o Ubuntu (16.4 ou 18.4), em execução em seu computador de desenvolvimento ou, como alternativa, você pode usar um computador separado executando o Linux (Ubuntu 16.4 ou 18.4). Você pode encontrar mais informações sobre como criar uma VM no Windows usando o Hyper-V no capítulo "Antes de [começar".](#before-you-start) (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Antes de começar

1. Configurar e testar seu HoloLens. Se você precisar de suporte para configurar seu HoloLens, visite o [artigo HoloLens instalação do .](/hololens/hololens-setup)
2. É uma boa ideia  executar Calibragem e Ajuste de **Sensor** ao começar a desenvolver um novo aplicativo HoloLens (às vezes, pode ajudar a executar essas tarefas para cada usuário).

Para saber mais sobre Calibragem, siga este [link para o artigo HoloLens Calibragem.](/hololens/hololens-calibration#hololens-2)

Para saber mais sobre o Ajuste do Sensor, siga este [link para o HoloLens de Ajuste do Sensor .](/hololens/hololens-updates)

3. Configurar sua **Máquina Virtual do Ubuntu** usando o **Hyper-V.** Os recursos a seguir ajudarão você com o processo.
    1.  Primeiro, siga este link para baixar o ISO do [Ubuntu 16.04.4 LTS (Xenial Xerus).](https://au.releases.ubuntu.com/16.04/) Selecione a imagem da área de trabalho **do PC de 64 bits (AMD64).**
    2.  **Certifique-se de que o Hyper-V** está habilitado em seu Windows 10 computador. Você pode seguir este link para obter diretrizes sobre como instalar e habilenciar [o Hyper-V no Windows 10](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Inicie o Hyper-V e crie uma nova VM do Ubuntu. Você pode seguir este link para ver [um guia passo a passo sobre como criar uma VM com o Hyper-V.](/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine) Quando solicitado a **"Instalar um** sistema operacional de um arquivo de imagem inicializável", selecione o ISO do **Ubuntu** que você baixou anteriormente.

    > [!NOTE]
    > Não é sugerido usar a Criação Rápida do **Hyper-V.**  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Capítulo 1 – Recuperar o Visão Personalizada modelo

Com este curso, você terá acesso a um modelo de Visão Personalizada [pré-criado](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) que detecta teclados e mouses de imagens. Se você usar isso, vá para [o Capítulo 2.](#chapter-2---the-container-registry-service)

No entanto, você poderá seguir estas etapas se quiser usar seu próprio Visão Personalizada modelo:

1. Na sua **Visão Personalizada Project** vá para a **guia** Desempenho.

    > [!WARNING]
    > Seu modelo deve usar um *domínio* compacto para exportar o modelo. Você pode alterar o domínio dos modelos nas configurações do projeto.

    ![guia desempenho](images/AzureLabs-Lab313-01.png)

2. Selecione a **Iteração** que você deseja exportar e clique em **Exportar**. Uma folha será exibida.

    ![folha exportar](images/AzureLabs-Lab313-02.png)

3. Na folha, clique em **Arquivo do Docker.**

    ![selecionar docker](images/AzureLabs-Lab313-03.png)

4. Clique **em Linux** no menu suspenso e clique em **Baixar**.

    ![Clique em baixar](images/AzureLabs-Lab313-04.png)

5. Descompcompa o conteúdo. Você o usará posteriormente neste curso.

## <a name="chapter-2---the-container-registry-service"></a>Capítulo 2 – O Serviço de Registro de Contêiner

O **Serviço de Registro de Contêiner** é o repositório usado para hospedar seus contêineres.

O **Serviço hub IoT** que você criará e  usará neste curso refere-se ao Serviço de Registro de Contêiner para obter os contêineres a implantar em seu Dispositivo de Borda.

1. Primeiro, siga este [link para o Portal do Azure](https://portal.azure.com/)e faça logon com suas credenciais.

2. Acesse **Criar um recurso e** procure Registro **de Contêiner.**

    ![registro de contêiner](images/AzureLabs-Lab313-05.png)

3. Clique em **Criar**.

    ![](images/AzureLabs-Lab313-06.png)

4. De acordo com os parâmetros de configuração do serviço:

    1. Insira um nome para seu projeto, Neste exemplo, seu **chamado IoTCRegistry**.

    2. Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os Serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comum.

    3. De definir o local do Serviço.

    4. De **definir Usuário administrador** como **Habilitar**.

    5. De **acordo com o SKU** como **Básico.** 

    ![](images/AzureLabs-Lab313-07.png)

5. Clique **em** Criar e aguarde até que os Serviços sejam criados. 

6. Depois que a notificação aparecer informando sobre a criação bem-sucedida do Registro de *Contêiner,* clique em **Ir** para o recurso para ser redirecionado para a página Serviço.

    ![](images/AzureLabs-Lab313-08.png)

7. Na página *Serviço de Registro de* Contêiner, clique em Chaves de **acesso**.

8. Anote (você pode usar seu Bloco de notas) dos seguintes parâmetros:
    1. **Servidor de Logon**
    2. **Nome de usuário**
    3. **Senha**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Capítulo 3 – O Serviço do Hub IoT

Agora você começará a criação e a configuração do Serviço **do Hub IoT.**

1. Se ainda não tiver feito logoff, faça logoff no [Portal do Azure.](https://portal.azure.com)

2.  Depois de conectado, clique **em** Criar um recurso no canto superior esquerdo, pesquise Hub **IoT** e clique em **Inserir**.

 ![pesquisar conta de armazenamento](images/AzureLabs-Lab313-10.png)

3.  A nova página fornecerá uma descrição do **serviço Armazenamento conta.** Na parte inferior esquerda deste prompt, clique **no botão Criar** para criar uma instância desse Serviço.

    ![criar instância de armazenamento](images/AzureLabs-Lab313-11.png)

4.  Depois de clicar em **Criar**, um painel será exibido:

    1. Escolha um **Grupo de Recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os Serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comum.

        > Se você quiser ler mais sobre os Grupos de Recursos do Azure, siga este link sobre como [gerenciar um Grupo de Recursos.](/azure/azure-resource-manager/resource-group-portal)


    2. Selecione um local **apropriado** (use o mesmo local em todos os Serviços que você criar neste curso).

    3. Insira o Nome desejado **para** esta instância de serviço.    

5.  Na parte inferior da página, clique em **Próximo: Tamanho e escala.**

    ![criar instância de armazenamento](images/AzureLabs-Lab313-12.png)

6.  Nesta página, selecione seu tipo de preço e escala **(se** esta for sua primeira instância de Serviço do Hub IoT, uma camada gratuita deverá estar disponível para você).  

7.  Clique em **Revisar + Criar.**

    ![criar instância de armazenamento](images/AzureLabs-Lab313-13.png)

8.  Revise suas configurações e clique em **Criar**.

    ![criar instância de armazenamento](images/AzureLabs-Lab313-14.png)

9. Depois que a notificação aparecer informando sobre a criação bem-sucedida  do Serviço *do Hub IoT,* clique em Ir para o recurso para ser redirecionado para a página Serviço.

    ![criar instância de armazenamento](images/AzureLabs-Lab313-15.png)

10. Role o painel lateral à esquerda até ver *Gerenciamento de Dispositivos*, clique em **IoT Edge**.

    ![criar instância de armazenamento](images/AzureLabs-Lab313-16.png)

11. Na janela que aparece à direita, clique em **Adicionar IoT Edge Dispositivo**. Uma folha será exibida à direita.

12. Na folha, forneça ao novo dispositivo uma **ID do dispositivo** (um nome de sua escolha). Em seguida, clique em **Salvar**. As *Chaves* *Primárias e Secundárias* serão automaticamente gerados, se você tiver **a Geração Automática** tiqueada.

    ![criar instância de armazenamento](images/AzureLabs-Lab313-17.png)

13. Você navegará de volta para a *IoT Edge dispositivos,* na qual o novo dispositivo será listado. Clique em seu novo dispositivo (descrito em vermelho na imagem abaixo). 

    ![criar instância de armazenamento](images/AzureLabs-Lab313-18.png)

14. Na página *Detalhes do* Dispositivo exibida, copie a Cadeia de Conexão **(chave** primária).

    ![criar instância de armazenamento](images/AzureLabs-Lab313-19.png)

15. Go back no painel à esquerda e clique em Políticas de acesso *compartilhado* para abri-lo. 

16. Na página exibida, clique **em iothubowner** e uma folha será exibida à direita da tela. 

17. Anote (no Bloco de notas) da cadeia de conexão **(chave** primária) para uso posterior ao definir a Cadeia de *Conexão* para seu dispositivo.

    ![criar instância de armazenamento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Capítulo 4 – Configurando o ambiente de desenvolvimento

Para criar e implantar módulos para o *Hub IoT no Edge,* você exigirá os seguintes componentes instalados em seu computador de desenvolvimento executando Windows 10:

1.  [Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), ele solicitará que você crie uma conta para poder baixar. 

    [![baixar o Docker para Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > O Docker *Windows 10 pro,* *Enterprise 14393* ou *Windows Server 2016 RTM*, para ser executado. Se você estiver executando outras versões do Windows 10, poderá tentar instalar o Docker usando a [Caixa de Ferramentas do Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3.6](https://www.python.org/downloads/).

    [![baixar o Python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (também conhecido como VS Code)](https://code.visualstudio.com/download).

    [![baixar VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Depois de instalar o software mencionado acima, você precisará reiniciar o computador.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Capítulo 5 – Configurando o ambiente do Ubuntu

Agora você pode passar para a configuração do dispositivo **que executa o sistema operacional Ubuntu.** Siga as etapas abaixo, para instalar o software necessário, para implantar seus contêineres em seu quadro:

> [!IMPORTANT]
> Você sempre deve preceder os comandos do terminal com **sudo** para ser executado como usuário administrador. I.e:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Abra o **Terminal do Ubuntu** e use o seguinte comando para instalar **o pip**:

    > [! DICA] Você pode abrir *o Terminal* facilmente usando o atalho de teclado: **Ctrl + Alt + T.**

    ```bash
        sudo apt-get install python-pip
    ```

2.  Ao longo deste Capítulo, você pode ser solicitado, pelo *Terminal,* a permissão para usar o armazenamento do dispositivo e para que você insira **y/n** (sim ou não), digite **'y'** e pressione a tecla **Enter** para aceitar.

3.  Depois que esse comando for concluído, use o seguinte comando para instalar o **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Depois **que pip** e **curl** são instalados, use o seguinte comando para instalar o **runtime** IoT Edge , isso é necessário para implantar e controlar os módulos em seu quadro:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. Neste ponto, você será solicitado a abrir o arquivo de configuração de *runtime*, para inserir a Cadeia de Conexão do Dispositivo **,** que você anotou (em seu Bloco de notas), ao criar o Serviço de **Hub IoT** ( na etapa [14, do Capítulo 3).](#chapter-3---the-iot-hub-service) Execute a seguinte linha no terminal para abrir esse arquivo:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. O **arquivo config.yaml** será exibido, pronto para edição:

    > [!WARNING]
    > Quando esse arquivo é aberto, pode ser um pouco confuso. Você editará o texto desse arquivo, dentro do *próprio Terminal.* 

    1.  Use as teclas de direção no teclado para rolar para baixo (você precisará rolar um pouco para baixo) para alcançar a linha que contém":

        "**\<ADD DEVICE CONNECTION STRING HERE>**".

    2. Substitua a linha, **incluindo os colchetes**, pela **Cadeia** de Conexão do Dispositivo que você anotou anteriormente.

7. Com a Cadeia de Conexão no local, no teclado, pressione as **teclas Ctrl-X** para salvar o arquivo. Ele solicitará que você confirme digitando **Y.** Em seguida, pressione **a tecla Enter** para confirmar. Você voltará para o *Terminal normal.* 

8. Depois que todos esses comandos são executados com êxito, você terá instalado o **IoT Edge Runtime**. Depois de inicializado, o runtime será inicializado por conta própria sempre que o dispositivo for ligado e ficará em segundo plano, aguardando que os módulos sejam implantados do Serviço do **Hub IoT.**

9.  Execute a seguinte linha de comando para inicializar o *IoT Edge Runtime*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Se você fizer alterações no arquivo .yaml ou na configuração acima, precisará executar a linha de reinicialização acima novamente, no *Terminal*.

10. Verifique o *status IoT Edge Runtime* executando a linha de comando a seguir. O runtime deve aparecer com o status **ativo (em execução)** em texto verde.

    ```bash
        sudo systemctl status iotedge
    ```

11. Pressione as **teclas Ctrl-C** para sair da página de status. Você pode verificar se o *IoT Edge Runtime* está esnovando os contêineres corretamente digitando o seguinte comando:

    ```bash
        sudo docker ps
    ```

12. Uma lista com dois (2) contêineres deve aparecer. Esses são os módulos padrão criados automaticamente pelo Serviço do Hub IoT (edgeAgent e edgeHub). Depois que você criar e implantar seus próprios módulos, eles aparecerão nessa lista, abaixo dos padrões.

## <a name="chapter-6---install-the-extensions"></a>Capítulo 6 – Instalar as extensões

> [!IMPORTANT]
> Os próximos capítulos (6-9) devem ser executados em seu Windows 10 computador.

1. Abra **VS Code**.

2. Clique no **botão Extensões** (quadrado) na barra esquerda do VS Code, para abrir o **painel Extensões**.

3. Pesquise e instale as seguintes extensões (conforme mostrado na imagem abaixo):

    1. Azure IoT Edge
    2. Kit de Ferramentas do Azure IoT
    3. Docker   

    ![Criar seu contêiner](images/AzureLabs-Lab313-24.png)

4. Depois que as extensões são instaladas, feche e abra novamente VS Code.

5. Com VS Code abrir mais uma vez, navegue até **Exibir**  >  **terminal integrado.**

6. Agora você instalará **o Cookiecutter**. No terminal, execute o seguinte comando bash:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! HINT] Se você tiver problemas com este comando: 
    >1. Reinicie VS Code e/ou seu computador.
    >2. Pode ser necessário alternar **o terminal VS Code para** aquele que você está usando para instalar o Python, ou seja, o **PowerShell** (especialmente no caso de o ambiente do Python já estar instalado em seu computador). Com o Terminal aberto, você encontrará o menu suspenso no lado direito do Terminal.
     ![Criar seu contêiner](images/AzureLabs-Lab313-24b.png) 
    >3. Certifique-se de **que o caminho de** instalação do Python seja adicionado como **Variável de** Ambiente em seu computador. Cookiecutter deve fazer parte do mesmo caminho de local. Siga este [link para obter mais informações sobre Variáveis de ambiente,](/windows/win32/procthread/environment-variables) 

7. Depois **que o Cookiecutter** terminar de instalar, você deverá reiniciar o computador para que **o Cookiecutter** seja reconhecido como um comando, dentro do ambiente do sistema.

## <a name="chapter-7---create-your-container-solution"></a>Capítulo 7 – Criar sua solução de contêiner

Neste ponto, você precisa criar o contêiner, com o módulo, para ser esvadado para o *Registro de Contêiner.* Depois de enviar o contêiner por pushed, você usará o Serviço do *Hub IoT Edge* para implantá-lo em seu dispositivo, que está executando o *runtime IoT Edge .*

1. Na VS Code, clique em **Exibir**  >  **paleta de comandos**.

2. Na paleta, pesquise e **execute Azure IoT Edge: nova solução do Iot Edge.**

3. Navegue até um local em que você deseja criar sua solução. Pressione a **tecla Enter** para aceitar o local.

4. Dê um nome à sua solução. Pressione a **tecla Enter** para confirmar o nome fornecido.

5. Agora você será solicitado a escolher a estrutura de modelo para sua solução. Clique **em Módulo python.** Pressione a **tecla Enter** para confirmar essa opção.

6. Dê um nome ao módulo. Pressione a **tecla Enter** para confirmar o nome do módulo. Certifique-se de anotar (com sua Bloco de notas) do nome do módulo, pois ele será usado posteriormente.

7. Você observará que um endereço pré-criado do Repositório de Imagens do *Docker* será exibido na paleta. Ele terá a aparência:

    **localhost:5000/-THE NAME OF YOUR MODULE-**. 

8. Exclua **localhost:5000** e,   em seu lugar, insira o endereço do Servidor de Logon do Registro de Contêiner, que você anotou ao criar o Serviço de Registro de Contêiner **(** na etapa 8, do Capítulo [2).](#chapter-2---the-container-registry-service) Pressione a **tecla Enter** para confirmar o endereço.

9. Neste ponto, a solução que contém o modelo para o módulo do Python será criada e sua estrutura será exibida na guia **Explorar** VS Code, no lado esquerdo da tela. Se a **guia Explorar** não estiver aberta, você poderá abri-la clicando no botão mais alto, na barra à esquerda.

    ![Criar seu contêiner](images/AzureLabs-Lab313-25.png)

10. A última etapa deste Capítulo é clicar e abrir o arquivo **.env** de  dentro da guia **Explorar** e adicionar o nome de usuário e a senha do Registro **de** **Contêiner.** Esse arquivo é ignorado pelo git, mas, ao criar o contêiner, definirá as credenciais para acessar o Serviço **de Registro de Contêiner**.

    ![Criar seu contêiner](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Capítulo 8 – Editando sua solução de contêiner

Agora você concluirá a solução de contêiner atualizando os seguintes arquivos:

- *main <span></span> .py* script python.
- *requirements.txt*.
- *deployment.template.jsem*.
- *Dockerfile.amd64*

Em seguida, você criará a *pasta images,* usada pelo script python para verificar se há imagens para corresponder ao *modelo Visão Personalizada .* Por fim, você adicionará o *arquivolabels.txt,* para ajudar a ler seu modelo e o *arquivo model.pb,* que é seu modelo.

1. Com VS Code, navegue até a pasta do módulo e procure o script chamado **<span></span> .py principal.** Clique duas vezes para abri-lo.

2. Exclua o conteúdo do arquivo e insira o seguinte código:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Abra o arquivo chamado **requirements.txt** e substitua seu conteúdo pelo seguinte:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Abra o arquivo chamado **deployment.template.jsem** e substitua seu conteúdo seguindo as diretrizes abaixo:

    1. Como você terá sua própria estrutura JSON exclusiva, precisará editá-la manualmente (em vez de copiar um exemplo). Para facilitar isso, use a imagem abaixo como um guia.
    2. Áreas que terão uma aparência diferente da sua, mas que você **NÃO deve alterar estão realçadas em amarelo.**
    3. **As seções que você precisa excluir são um vermelho realçada.**
    4. Tenha cuidado para excluir os colchetes corretos e também remover as vírgulas.

        ![Criar seu contêiner](images/AzureLabs-Lab313-27.png)

    5. O JSON concluído deve ser semelhante à imagem a seguir (no entanto, com suas diferenças *exclusivas: nome de usuário/senha/nome do módulo/referências de módulo):*

        ![Criar seu contêiner](images/AzureLabs-Lab313-28.png)

5.  Abra o arquivo chamado **Dockerfile.amd64** e substitua seu conteúdo pelo seguinte:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Clique com o botão direito do mouse na pasta abaixo dos **módulos** (ele terá o nome fornecido anteriormente; no exemplo mais abaixo, ele é chamado *pythonmodule*) e clique em **Nova Pasta**. Nomeia as imagens **de pasta**.

7.  Dentro da pasta, adicione algumas imagens que contêm mouse ou teclado. Essas serão as imagens que serão analisadas pelo modelo tensorflow.

    > [!WARNING]
    > Se você estiver usando seu próprio modelo, precisará alterá-lo para refletir seus próprios dados de modelos.

8.  Agora você precisará recuperar os **arquivoslabels.txt** **e model.pb** da pasta de modelo, que você baixou anteriormente (ou criou de seu próprio **serviço Visão Personalizada**), no [Capítulo 1](#chapter-1---retrieve-the-custom-vision-model). Depois de ter os arquivos, coloque-os em sua solução, juntamente com os outros arquivos. O resultado final deve ser parecido com a imagem abaixo:

    ![Criar seu contêiner](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Capítulo 9 – Empacote a solução como um contêiner

1.  Agora você está pronto para "empacotar" seus arquivos como um contêiner e e push para seu **Registro de Contêiner do Azure**. No VS Code, abra o Terminal Integrado **(** Exibir *Terminal* Integrado ou Ctrl ) e use a seguinte linha para fazer logon no Docker (substitua os valores do comando com as credenciais do  >   seu  + **\`** **Registro de Contêiner do Azure (ACR):** 

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Clique com o botão direito do mouse **no arquivodeployment.template.jsem** e clique em Criar IoT Edge **Solução**. Esse processo de build leva algum tempo (dependendo do seu dispositivo), portanto, esteja preparado para aguardar. Após a finalização do processo de build, **umdeployment.jsno** arquivo terá sido criado dentro de uma nova pasta chamada **config**.

    ![criar implantação](images/AzureLabs-Lab313-30.png)

3. Abra a **Paleta de Comandos** novamente e pesquise **Azure: Entrar.** Siga os prompts usando suas credenciais de conta do Azure; VS Code fornecerá uma opção para Copiar e *Abrir,* que copiará o código do dispositivo que você precisará em breve e abrirá o navegador da Web padrão. Quando solicitado, colar o código do dispositivo para autenticar seu computador.

    ![copiar e abrir](images/AzureLabs-Lab313-31.png)

4. Depois de conectado, você observará, no lado inferior do painel *Explorar,* uma nova seção chamada **Hub IoT do Azure Dispositivos**. Clique nesta seção para expandi-la.

    ![dispositivo de borda](images/AzureLabs-Lab313-32.png)

5. Se o dispositivo não estiver aqui, você precisará clicar com o botão direito do mouse *Hub IoT do Azure Dispositivos* e, em seguida, clicar em Definir Cadeia de Conexão **do Hub IoT**. Em seguida, você verá que a **paleta** de comandos (na parte superior VS Code), solicitará que você insue sua Cadeia *de* Conexão . Esta é a *Cadeia de Conexão* que você anotou no final do Capítulo [3.](#chapter-3---the-iot-hub-service) Pressione a **tecla Enter** depois de copiar a cadeia de caracteres.    

6. O dispositivo deve ser carregado e exibido. Clique com o botão direito do mouse no nome do dispositivo e clique em **Criar Implantação para Dispositivo Único.**

    ![criar implantação](images/AzureLabs-Lab313-33b.png)

7. Você receberá um prompt *Explorador de Arquivos,* no qual poderá navegar até a pasta **config** e, em seguida, selecionar adeployment.js **no** arquivo. Com esse arquivo selecionado, clique no botão **selecionar manifesto de implantação de borda** .

    ![criar implantação](images/AzureLabs-Lab313-34.png)

8. Neste ponto, você forneceu ao seu **serviço de Hub IOT** o manifesto para implantar seu contêiner, como um módulo, do registro de **contêiner do Azure**, implantando-o efetivamente em seu dispositivo.

9. Para exibir as mensagens enviadas do seu dispositivo para o Hub IoT, clique com o botão direito do mouse novamente no nome do dispositivo na seção **dispositivos do Hub IOT do Azure** , no painel **Gerenciador** e clique em **Iniciar Monitoramento de mensagem D2C**. As mensagens enviadas do seu dispositivo devem aparecer no terminal do VS. Seja paciente, pois isso pode levar algum tempo. Consulte o próximo capítulo para depuração e verificando se a implantação foi bem-sucedida.

Este módulo agora fará a iteração entre as imagens na pasta **imagens** e as analisará, com cada iteração. Isso é, obviamente, apenas uma demonstração de como obter o modelo básico de aprendizado de máquina para trabalhar em um ambiente de dispositivo IoT Edge. 

Para expandir a funcionalidade deste exemplo, você pode proceder de várias maneiras. Uma maneira pode ser incluir algum código no contêiner, que captura fotos de uma webcam conectada ao dispositivo e salva as imagens na pasta imagens. 

Outra maneira seria copiar as imagens do dispositivo IoT para o contêiner. Uma maneira prática de fazer isso é executar o seguinte comando no terminal do dispositivo IoT (talvez um aplicativo pequeno possa fazer o trabalho, se desejar automatizar o processo). Você pode testar esse comando executando-o manualmente do local da pasta onde os arquivos são armazenados:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Capítulo 10-Depurando o tempo de execução de IoT Edge

Veja a seguir uma lista de linhas de comando e dicas para ajudá-lo a monitorar e depurar a atividade de mensagens do *tempo de execução de IOT Edge*, do seu **dispositivo Ubuntu**. 

- Verifique o status do *tempo de execução do IOT Edge* executando a seguinte linha de comando:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Lembre-se de pressionar **Ctrl + C** para concluir a exibição do status.

- Liste os contêineres que estão implantados no momento. Se o *serviço Hub IOT* implantou os contêineres com êxito, eles serão exibidos executando a seguinte linha de comando:

    ```bash
        sudo iotedge list
    ```

    Ou

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > O acima é uma boa maneira de verificar se o módulo foi implantado com êxito, como aparecerá na lista; caso contrário, você verá **apenas** o *EdgeHub* e o *edgeAgent*.

- Para exibir os logs de código de um contêiner, execute a seguinte linha de comando:

    ```bash
        journalctl -u iotedge
    ```

**Comandos úteis para gerenciar o tempo de execução de IoT Edge:**

-  Para excluir todos os contêineres no host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Para interromper o *tempo de execução de IOT Edge*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Capítulo 11 – criar serviço de tabela 

navegue de volta para o Portal do azure, no qual você criará um serviço de tabelas do azure, criando um recurso de Armazenamento.

1. Se ainda não estiver conectado, faça logon no [portal do Azure](https://portal.azure.com).

2. depois de conectado, clique em **criar um recurso**, no canto superior esquerdo e procure **Armazenamento conta** e pressione a tecla **Enter** para iniciar a pesquisa.

3. depois de ter aparecido, clique em **Armazenamento conta-blob, arquivo, tabela, fila** na lista.

    ![Pesquisar conta de armazenamento](images/AzureLabs-Lab313-35.png)

4. a nova página fornecerá uma descrição do serviço de **conta do Armazenamento** . Na parte inferior esquerda desse prompt, clique no botão **criar** para criar uma instância desse serviço.

    ![criar instância de armazenamento](images/AzureLabs-Lab313-36.png)

5. Depois de clicar em **criar**, um painel será exibido:

    1. Insira o **nome** desejado para esta instância de serviço (*deve estar em letras minúsculas*).

    2. Para **modelo de implantação**, clique em **Gerenciador de recursos**.

    3. para **tipo de conta**, usando o menu suspenso, clique em **Armazenamento (uso geral v1)**.

    4. Clique em um **local** apropriado.
    
    5. Para o menu suspenso **replicação** , clique em **armazenamento com redundância geográfica e acesso de leitura (ra-grs)**.

    6. Para **desempenho**, clique em **padrão**.

    7. Na seção **transferência segura necessária** , clique em **desabilitado**.

    8. No menu suspenso **assinatura** , clique em uma assinatura apropriada.

    9. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    10. Deixe as **redes virtuais** como **desabilitadas**, se essa for uma opção para você.

    11. Clique em **Criar**.

        ![preencher detalhes do armazenamento](images/AzureLabs-Lab313-37.png)

6. Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

7. Uma notificação será exibida no portal assim que a instância do serviço for criada. Clique nas notificações para explorar sua nova instância de serviço.

    ![Nova notificação de armazenamento](images/AzureLabs-Lab313-38.png)

8. clique no botão **ir para recurso** na notificação e você será levado para a página de visão geral da nova Armazenamento instância do serviço.

    ![ir para o recurso](images/AzureLabs-Lab313-39.png)

9. Na página Visão geral, no lado direito, clique em **tabelas**.
    
    ![tabelas](images/AzureLabs-Lab313-40.png)

10. O painel à direita será alterado para mostrar as informações do **serviço tabela** , onde você precisa adicionar uma nova tabela. Para fazer isso, clique no botão **+ tabela** no canto superior esquerdo.

    ![Abrir tabelas](images/AzureLabs-Lab313-41.png)

11. Uma nova página será mostrada, onde você precisa inserir um nome de **tabela**. Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos posteriores (criando Aplicativo de funções e Power BI). Insira **IoTMessages** como o nome (você pode escolher o seu próprio, apenas lembre-se dele quando usado mais tarde neste documento) e clique em **OK**. 

12. Depois que a nova tabela tiver sido criada, você poderá vê-la na página de **serviço tabela** (na parte inferior).

    ![nova tabela criada](images/AzureLabs-Lab313-42.png)  

13. agora, clique em **chaves de acesso** e faça uma cópia do nome da conta de **Armazenamento** e da **chave** (usando seu Bloco de notas). você usará esses valores posteriormente neste curso, ao criar o **Aplicativo de funções do Azure**.

    ![nova tabela criada](images/AzureLabs-Lab313-43.png) 

14. usando o painel à esquerda novamente, role até a seção *serviço tabela* e clique em **tabelas** (ou **procure tabelas**, em portais mais recentes) e faça uma cópia da **URL da tabela** (usando seu Bloco de notas). você usará esse valor posteriormente neste curso, ao vincular sua tabela ao seu aplicativo **Power BI** .

    ![nova tabela criada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Capítulo 12 – concluindo a tabela do Azure

Agora que a conta de armazenamento do **serviço de tabela** foi configurada, é hora de adicionar dados a ela, que será usada para armazenar e recuperar informações. A edição das tabelas pode ser feita por meio de **Visual Studio**.

1. abra **Visual Studio** (**não** Visual Studio Code).

2. No menu, clique em **Exibir**  >  **Cloud Explorer**.

    ![abrir o Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).

    > [!WARNING] 
    > se a assinatura usada para criar suas *contas de Armazenamento* não estiver visível, verifique se você tem: 
    > - Conectado à mesma conta que você usou para o portal do Azure.
    > - Selecione sua assinatura na página de gerenciamento de conta (talvez seja necessário aplicar um filtro de suas configurações de conta):  
    >
    >   ![Localizar assinatura](images/AzureLabs-Lab313-46.png)

4. Os serviços de nuvem do Azure serão mostrados. localize **Armazenamento contas** e clique na seta à esquerda dela para expandir suas contas.

    ![abrir contas de armazenamento](images/AzureLabs-Lab313-47.png)

5. uma vez expandido, sua **conta de Armazenamento** recém-criada deve estar disponível. Clique na seta à esquerda do armazenamento e, depois de expandida, localize as **tabelas** e clique na seta ao lado dela para revelar a **tabela** que você criou no último capítulo. Clique duas vezes em sua **tabela**.

6. sua tabela será aberta no centro da janela de Visual Studio. Clique no ícone de tabela com o **+** (mais) nele.

    ![Adicionar nova tabela](images/AzureLabs-Lab313-48.png)

7. Uma janela será exibida solicitando que você *adicione a entidade*. Você criará apenas uma entidade, embora ela terá três propriedades. Você observará que *PartitionKey* e *RowKey* já foram fornecidos, pois eles são usados pela tabela para localizar seus dados. 

    ![partição e chave de linha](images/AzureLabs-Lab313-49.png)

8. Atualize os seguintes valores:

    - Nome: **PartitionKey**, valor: **PK_IoTMessages** 

    - Nome: **RowKey**, valor: **RK_1_IoTMessages** 

9. Em seguida, clique em **Adicionar Propriedade** (na parte inferior esquerda da janela *Adicionar entidade* ) e adicione a seguinte propriedade:

    - **MessageContent**, como uma *cadeia de caracteres*, deixe o valor vazio.

10. Sua tabela deve corresponder à que está na imagem abaixo:

    ![Adicionar valores corretos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > O motivo pelo qual a entidade tem o número 1 na chave de linha, é porque você talvez queira adicionar mais mensagens, caso deseje fazer experiências com este curso.

11. Clique em **OK** quando terminar. Sua tabela agora está pronta para ser usada.

## <a name="chapter-13---create-an-azure-function-app"></a>Capítulo 13-criar uma Aplicativo de funções do Azure 

Agora é hora de criar uma *aplicativo de funções do Azure*, que será chamada pelo serviço de *Hub IOT* para armazenar as mensagens de dispositivo *IOT Edge* no serviço **tabela** , que você criou no capítulo anterior.

Primeiro, você precisa criar um arquivo que permitirá que o Azure function carregue as bibliotecas necessárias.

1.  abra **Bloco de notas** (pressione a *tecla Windows* e digite *Notepad*).

    ![abrir bloco de notas](images/AzureLabs-Lab313-51.png)

2.  com Bloco de notas aberto, insira a estrutura JSON abaixo dela. Depois de fazer isso, salve-o na área de trabalho como **project.jsem**. Esse arquivo define as bibliotecas que sua função usará. Se você tiver usado NuGet, ele parecerá familiar.
    
    > [!WARNING]
    > É importante que a nomenclatura esteja correta; Verifique se ele **não tem uma extensão de arquivo .txt** . Consulte abaixo para obter referência:
    >
    > ![Salvar JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Faça logon no [portal do Azure](https://portal.azure.com).

4.  Depois de fazer logon, clique em **criar um recurso** no canto superior esquerdo e procure **aplicativo de funções** e pressione a tecla **Enter** para pesquisar. Clique em *aplicativo de funções* nos resultados para abrir um novo painel.

    ![Pesquisar o aplicativo de funções](images/AzureLabs-Lab313-53.png)

5.  O novo painel fornecerá uma descrição do serviço de **aplicativo de funções** . Na parte inferior esquerda deste painel, clique no botão **criar** para criar uma associação com esse serviço.

    ![instância do aplicativo de funções](images/AzureLabs-Lab313-54.png)

6.  Depois de clicar em **criar**, preencha o seguinte:

    1. Para **nome do aplicativo**, insira o nome desejado para esta instância de serviço.

    2. Selecione uma **Assinatura**.

    3. Selecione o tipo de preço apropriado para você, se esta for a primeira vez que criar um **serviço de aplicativo de funções**, uma camada gratuita deverá estar disponível para você.

    4. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. para o **so**, clique em Windows, pois essa é a plataforma pretendida.

    6. Selecione um **plano de hospedagem** (este tutorial está usando um **plano de consumo**.

    7. Selecione um **local** (escolha o mesmo local do armazenamento que você criou na etapa anterior)

    8. para a seção **Armazenamento** , **você deve selecionar o serviço Armazenamento que você criou na etapa anterior**.

    9. você não precisará de *Application Insights* neste aplicativo, portanto, fique à vontade para deixá-lo **desativado**.

    10. Clique em **Criar**.

        ![criar nova instância](images/AzureLabs-Lab313-55.png)

7.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

8.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Nova notificação](images/AzureLabs-Lab313-56.png)

9.  Clique na notificação, depois que a implantação for bem-sucedida (concluída).

10. Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. 

    ![ir para o recurso](images/AzureLabs-Lab313-57.png)

11. No lado esquerdo do painel novo, clique no **+** ícone (mais) ao lado de *funções*, para criar uma nova função.

    ![Adicionar nova função](images/AzureLabs-Lab313-58.png)

12. No painel central, a janela de criação da **função** será exibida. Role para baixo e clique em **função personalizada**.

    ![função personalizada](images/AzureLabs-Lab313-59.png)

13. Role para baixo na próxima página, até encontrar o **Hub IOT (Hub de eventos)** e clique nele.

    ![função personalizada](images/AzureLabs-Lab313-60.png)

14. Na folha **Hub IOT (Hub de eventos)** , defina o **idioma** como **C#** e clique em **novo**.

    ![função personalizada](images/AzureLabs-Lab313-61.png)

15. Na janela que será exibida, verifique se **Hub IOT** está selecionado e se o nome do campo *Hub IOT* corresponde ao nome do *serviço do Hub IOT* que você criou anteriormente ([na etapa 8, do capítulo 3](#chapter-3---the-iot-hub-service)). Em seguida, clique no botão **selecionar** .

    ![função personalizada](images/AzureLabs-Lab313-62.png)

16. De volta à folha **Hub IOT (Hub de eventos)** , clique em **criar**.

    ![função personalizada](images/AzureLabs-Lab313-63.png)

17. Você será redirecionado para o editor de funções.

    ![função personalizada](images/AzureLabs-Lab313-64.png)

18. Exclua todo o código e substitua-o pelo seguinte:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. altere as seguintes variáveis, para que elas correspondam aos valores apropriados (**tabela** e valores de **Armazenamento** , da [etapa 11 e 13, respectivamente, do capítulo 11](#chapter-11---create-table-service)), que você encontrará em sua **conta de Armazenamento**:

    - **tablename**, com o nome da sua **tabela** localizado em sua **conta de Armazenamento**.
    - **tableURL**, com a URL da sua **tabela** localizada em sua **conta de Armazenamento**.
    - **storageAccountName**, com o nome do valor correspondente ao nome do seu Armazenamento nome da **conta** .
    - **storageAccountKey**, com a chave que você obteve no serviço de Armazenamento que você criou anteriormente.

    ![função personalizada](images/AzureLabs-Lab313-65.png)

20. Com o código em vigor, clique em **salvar**.

21. Em seguida, clique no **\<** ícone (seta), no lado direito da página.

    ![função personalizada](images/AzureLabs-Lab313-66.png)

22. Um painel será deslizado da direita. nesse painel, clique em **Upload** e um *navegador de arquivos* será exibido.

23. navegue até e clique em **project.jsno** arquivo, que você criou em **Bloco de notas** anteriormente e, em seguida, clique no botão **abrir** . Esse arquivo define as bibliotecas que sua função usará.

    ![função personalizada](images/AzureLabs-Lab313-67.png)

24. Quando o arquivo for carregado, ele será exibido no painel à direita. Clicar nele irá abri-lo no editor de **funções** . Ele deve ser **exatamente** o mesmo que a próxima imagem.

    ![função personalizada](images/AzureLabs-Lab313-68.png)

25. Neste ponto, seria bom testar a capacidade da sua função de armazenar a mensagem em sua *tabela*. No canto superior direito da janela, clique em **testar**.

    ![função personalizada](images/AzureLabs-Lab313-69.png)

26. Insira uma mensagem no **corpo da solicitação**, conforme mostrado na imagem acima, e clique em **executar**. 

27. A função será executada, exibindo o status do resultado (você notará o **status verde 202 aceito**, acima da janela de *saída* , o que significa que ele foi uma chamada bem-sucedida):

    ![resultado da saída](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Capítulo 14-exibir mensagens ativas

se agora você abrir Visual Studio (**não** Visual Studio Code), poderá visualizar o resultado da mensagem de teste, pois ele será armazenado na área da cadeia de caracteres *MessageContent* .

![função personalizada](images/AzureLabs-Lab313-71.png)

Com o serviço tabela e Aplicativo de funções em vigor, suas mensagens do dispositivo Ubuntu aparecerão na sua tabela *IoTMessages* . se ainda não estiver em execução, inicie o dispositivo novamente e você poderá ver as mensagens de resultado do seu dispositivo, e módulo, em sua tabela, usando Visual Studio *Cloud Explorer*.

![Visualizar dados](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>capítulo 15-instalação do Power BI

para visualizar os dados de seu dispositivo IOT, você irá configurar **Power BI** (versão da área de trabalho) para coletar os dados do serviço *tabela* que você acabou de criar. a versão *HoloLens* do Power BI usará esses dados para visualizar o resultado.

1.  abra o Microsoft Store no Windows 10 e procure **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Baixe o aplicativo. Depois de concluir o download, abra-o.

3.  faça logon no *Power BI* com sua **conta do Microsoft 365**. Você pode ser redirecionado para um navegador, para se inscrever. depois de se inscrever, volte para o aplicativo Power BI e entre novamente.

4.  Clique em **obter dados** e, em seguida, clique em **mais..**..

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  clique em **azure**, **tabela do azure Armazenamento** e, em seguida, clique em **Conexão**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Você será solicitado a inserir a URL da **tabela** que você coletou anteriormente ([na etapa 13 do capítulo 11](#chapter-11---create-table-service)), ao criar o serviço tabela. Depois de inserir a URL, exclua a parte do caminho referente à tabela "subpasta" (que foi IoTMessages, neste curso). O resultado final deve ser exibido na imagem abaixo. Em seguida, clique em **OK**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  você será solicitado a inserir a chave de **Armazenamento** que você anotou ([na etapa 11 do capítulo 11](#chapter-11---create-table-service)) antes de criar a tabela Armazenamento. em seguida, clique em **Conexão**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Um **painel de navegador** será exibido, marque a caixa ao lado de sua tabela e clique em **carregar**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. sua tabela agora foi carregada em Power BI, mas ela requer uma consulta para exibir os valores nela. Para fazer isso, clique com o botão direito do mouse no nome da tabela localizado no **painel campos** , no lado direito da tela. Em seguida, clique em **Editar consulta**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Um **Editor de Power Query**  será aberto como uma nova janela, exibindo a tabela. Clique no **registro** do Word na coluna *conteúdo* da tabela para visualizar o conteúdo armazenado.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Clique em na **tabela**, na parte superior esquerda da janela. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Clique em **fechar & aplicar**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Depois de terminar de carregar a consulta, no **painel campos**, no lado direito da tela, marque as caixas correspondentes ao **nome** e ao **valor** dos parâmetros para visualizar o conteúdo da coluna **MessageContent** .

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Clique no **ícone de disco azul** na parte superior esquerda da janela para salvar seu trabalho em uma pasta de sua escolha.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Agora você pode clicar no botão Publicar para carregar sua tabela em seu espaço de trabalho. Quando solicitado, clique em **meu espaço de trabalho** e clique em *selecionar*. Aguarde até que ele exiba o resultado bem-sucedido do envio.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> o capítulo a seguir é HoloLens específico. o Power BI não está disponível atualmente como um aplicativo de imersão, no entanto, você pode executar a versão da área de trabalho no Portal do Windows Mixed Reality (também conhecido como Cliff House), por meio do aplicativo de desktop.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>capítulo 16-exibir dados de Power BI no HoloLens

1. no HoloLens, faça logon no **Microsoft Store**, tocando em seu ícone na lista de aplicativos.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. pesquise e baixe o aplicativo **Power BI** .

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. inicie o **Power BI** na sua lista de aplicativos. 

4. **Power BI** pode solicitar que você faça logon na sua **conta do Microsoft 365**.

5. Uma vez dentro do aplicativo, o espaço de trabalho deve ser exibido por padrão, conforme mostrado na imagem abaixo. Se isso não acontecer, basta clicar no ícone do espaço de trabalho no lado esquerdo da janela.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Seu aplicativo de Hub IoT foi concluído

Parabéns, você criou com êxito um serviço de Hub IoT, com um dispositivo de borda de máquina virtual simulado. seu dispositivo pode comunicar os resultados de um modelo de aprendizado de máquina para um serviço tabela do azure, facilitado por uma Aplicativo de funções do azure, que é lida em Power BI e visualizada em uma Microsoft HoloLens.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Expanda a estrutura de mensagens armazenada na tabela e exiba-a como um grafo. Talvez você queira coletar mais dados e armazená-los na mesma tabela, para serem exibidos posteriormente.

### <a name="exercise-2"></a>Exercício 2

Crie um módulo adicional de "captura de câmera" para ser implantado na placa IoT, para que ele possa capturar imagens por meio da câmera a ser analisada.