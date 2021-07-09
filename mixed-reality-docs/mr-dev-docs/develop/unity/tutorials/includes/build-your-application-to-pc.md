---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392489"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. Como alternar a plataforma de build

No menu do Unity, selecione Arquivo > Configurações de Build para abrir a janela Configurações de Build.

Na janela Configurações de build, selecione plataforma **Autônoma de PC, Mac e Linux** e clique em **Alternar plataforma** para alterar a Plataforma de build:

![Como alternar a plataforma de build](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

Quando o Unity concluir a troca da plataforma, clique no ícone x para fechar a janela Configurações de build.

### <a name="2-set-the-project-settings"></a>2. Definir as configurações do projeto

No menu do Unity, selecione **Editar** > **Configurações de projeto** > **Gerenciamento do plug-in XR**, confira se você está na guia Autônomo do Windows e marque a caixa de seleção **OpenXR** e **conjunto de recursos do Windows Mixed Reality**.

![Habilitar o OpenXR e o conjunto de recursos do Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

Na janela Configurações de projeto, selecione **OpenXR**, confira se você está na guia Autônomo do Windows e altere o **modo de envio de Profundidade** de Nenhum para **Profundidade 16 bits**.

Na guia Perfis de interação, clique no símbolo + e adicione **Perfil de interação do olhar** e **Perfil de interação com a mão da Microsoft**.

![Adicionar Perfil de interação do olhar e Perfil de interação com a mão da Microsoft](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

Em **Grupos de recursos do Open XR** > **Todos os recursos** > marque a caixa de seleção **Comunicação Remota de aplicativo holográfico**.

![Habilitar a Comunicação Remota de aplicativo holográfico](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

Em seguida, marque a caixa de seleção **Windows Mixed Reality** e, no grupo do Windows Mixed Reality, selecione **Comunicação Remota de aplicativo holográfico**.

![Habilitar a Comunicação Remota de aplicativo holográfico do Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. Criar o projeto do Unity

No menu do Unity, selecione Arquivo > Configurações de Build para abrir a janela Configurações de Build.

Na janela Configurações de Build, clique no botão ***Adicionar Cenas Abertas** _ para adicionar a cena atual às Cenas. Na lista do Build, clique em _ *Build**:

![Janela Configurações de Build do Unity com a cena adicionada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

Escolha um local adequado para armazenar seu projeto, por exemplo, Documents\MixedRealityLearning. Crie uma pasta e dê a ela um nome adequado, por exemplo, PCHolographicRemoting. Em seguida, clique no botão ***Selecionar Pasta*** para iniciar o processo de build:

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

Aguarde até que o Unity conclua o processo de build.

![Processo de build do Unity em andamento](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

Clique duas vezes no arquivo executável para abrir o Aplicativo Holográfico de Comunicação Remota para PC em seu computador.

> [!NOTE]
> Devido a alguns problemas conhecidos no aplicativo Holográfico de Comunicação Remota para PC criado como UWP, estamos construindo o aplicativo para PC como Autônomo do Windows para OpenXR.


# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1. Definir as configurações do player

Na seção **Configurações de XR**, marque a caixa de seleção **Comunicação Remota Holográfica do WSA com Suporte** e habilite a Comunicação Remota Holográfica.

![Janela Configurações de XR do Unity com a caixa Comunicação Remota Holográfica do WSA com Suporte habilitada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Criar o Projeto do Unity

No menu do Unity, selecione Arquivo > Configurações de Build para abrir a janela Configurações de Build.

Na janela Configurações de Build, clique no botão ***Adicionar Cenas Abertas** _ para adicionar a cena atual às Cenas. Na lista Build, clique no _ *_botão Build_** para abrir a janela Criar Plataforma Universal do Windows:

![Janela Configurações de Build do Unity com a cena adicionada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

Na janela Criar Plataforma Universal do Windows, escolha uma localização adequada para armazenar o seu build, por exemplo, Documents\MixedRealityLearning. Crie uma pasta e dê a ela um nome adequado, por exemplo, PCHolographicRemoting. Em seguida, clique no botão ***Selecionar Pasta*** para iniciar o processo de build:

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Aguarde até que o Unity conclua o processo de build.

![Processo de build do Unity em andamento](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Compilar e implantar o aplicativo

Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra o local em que você armazenou o build. Navegue dentro da pasta e clique duas vezes no arquivo .sln para abri-lo no Visual Studio:

![Windows Explorer com a solução do Visual Studio recém-criada selecionada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar que todos os componentes necessários estejam instalados conforme especificado na documentação Instalar as Ferramentas.

Configure o Visual Studio para PC selecionando a configuração da Versão, a arquitetura x64 e o Computador Local como um destino:

![Visual Studio configurado para Computador Local](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Clique no botão ***Computador Local***. Ele começa a criar e implantar o aplicativo no seu PC. O aplicativo será instalado no seu PC por padrão.
