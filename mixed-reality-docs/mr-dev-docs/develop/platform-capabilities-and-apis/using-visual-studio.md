---
title: Como usar o Visual Studio para implantação e depuração
description: Saiba como compilar, depurar e implantar aplicativos para o HoloLens e o Windows Mixed Reality usando o Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realidade misturada, depurar, implantar
ms.openlocfilehash: c4ffe3a426ad82c324efef20639cf836f16a7f63
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583616"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Como usar o Visual Studio para implantação e depuração

Se você estiver usando o DirectX ou Unity para desenvolver seu aplicativo de realidade misturada, o Visual Studio é sua ferramenta ideal para depuração e implantação. Nesta seção, você aprenderá a:
* Implantar aplicativos no HoloLens ou no headset imersivo do Windows Mixed Reality por meio do Visual Studio.
* Usar o emulador do HoloLens incorporado no Visual Studio.
* Depurar aplicativos de realidade misturada.

## <a name="prerequisites"></a>Pré-requisitos
1. Confira [Instalar as ferramentas](../../develop/install-the-tools.md) para obter instruções de instalação.
2. Crie um projeto de aplicativo universal do Windows no Visual Studio.  Para o HoloLens (1ª geração), use o Visual Studio 2017 ou mais recente.  Para o HoloLens 2, use o Visual Studio 2019 16.2 ou mais recente. Há suporte para C# e C++. (Ou siga as instruções para [criar um aplicativo no Unity](../../develop/unity/tutorials/holograms-100.md).)

## <a name="enabling-developer-mode"></a>Habilitar o modo de desenvolvedor

Comece habilitando o **Modo de Desenvolvedor** no dispositivo, para que o Visual Studio possa se conectar a ele.

### <a name="hololens"></a>HoloLens
1. Ligue o HoloLens e coloque o dispositivo.
2. Use o [gesto de início](../../design/system-gesture.md) para iniciar o menu principal.
3. Selecione o bloco **Configurações** para iniciar o aplicativo no ambiente.
4. Selecione item de menu **Atualização**.
5. Selecione o item de menu **Para desenvolvedores**.
6. Habilite o **Modo de Desenvolvedor** para [implantar aplicativos do Visual Studio](using-visual-studio.md) em seu HoloLens.
7. Opcional: Role para baixo e habilite também o **Portal de Dispositivos**, que permite que você se conecte ao [Portal de Dispositivos do Windows](using-the-windows-device-portal.md) no seu HoloLens de um navegador da Web.

### <a name="windows-pc"></a>Computador Windows

Se você estiver trabalhando com um headset do Windows Mixed Reality conectado ao computador, habilite o **Modo de Desenvolvedor** no computador.
1. Ir para **Configurações**
2. Selecione **Atualização e Segurança**
3. Selecione **Para desenvolvedores**
4. Habilite o **Modo de Desenvolvedor**, leia o aviso de isenção de responsabilidade da configuração escolhida e, em seguida, selecione Sim para aceitar a alteração.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Como implantar um aplicativo via Wi-Fi – HoloLens (1ª geração)
1. Selecione uma configuração de build **x86** para o aplicativo</br>
![Configuração de build x86 no Visual Studio](images/x86setting.png)</br>
2. Selecione **Computador Remoto** no menu suspenso do destino de implantação</br>
![Destino de implantação de computador remoto no Visual Studio](images/remotemachinesetting.png)</br>
3. Para projetos C++ e JavaScript, acesse **Projeto > Propriedades > Propriedades de Configuração > Depuração**. Para projetos C#, uma caixa de diálogo será exibida automaticamente para configurar a conexão.
  a. Insira o endereço IP do dispositivo no campo **Endereço** ou **Nome do Computador**. Localize o endereço IP no HoloLens em **Configurações > Rede e Internet > Opções Avançadas** ou pergunte à Cortana "Qual é meu endereço IP?"
  b. Defina o Modo de Autenticação como **Universal (Protocolo não criptografado)**</br>
  ![Caixa de diálogo de conexão remota no Visual Studio](images/remotedeploy.png)</br>
4. Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</br>
![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)</br>
5. Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN. Siga as instruções de **Como emparelhar o dispositivo** abaixo.

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Como implantar um aplicativo via Wi-Fi – HoloLens 2
1. Selecione uma configuração de build **ARM** ou **ARM64** para o aplicativo</br>
![Configuração de build ARM64 no Visual Studio](images/arm64setting.png)</br>
2. Selecione **Computador Remoto** no menu suspenso do destino de implantação</br>
![Destino de implantação de computador remoto no Visual Studio](images/remotemachinesetting_arm64.png)</br>
3. Para projetos C++ e JavaScript, acesse **Projeto > Propriedades > Propriedades de Configuração > Depuração**. Para projetos C#, uma caixa de diálogo será exibida automaticamente para configurar a conexão.
  a. Insira o endereço IP do dispositivo no campo **Endereço** ou **Nome do Computador**. Localize o endereço IP no HoloLens em **Configurações > Rede e Internet > Opções Avançadas** ou pergunte à Cortana "Qual é meu endereço IP?"
  b. Defina o Modo de Autenticação como **Universal (Protocolo não criptografado)**</br>
  ![Caixa de diálogo de conexão remota no Visual Studio](images/remotedeploy.png)</br>
4. Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</br>
![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)</br>
5. Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN. Siga as instruções de **Como emparelhar o dispositivo** abaixo.

Se o endereço IP do HoloLens for alterado, você poderá alterar o endereço IP do computador de destino acessando **Projeto > Propriedades > Propriedades de Configuração > Depuração**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Como implantar um aplicativo via USB – HoloLens (1ª geração)
1. Selecione uma configuração de build **x86** para o aplicativo</br>
![Configuração de build x86 no Visual Studio](images/x86setting.png)</br>
2. Selecione **Dispositivo** no menu suspenso do destino de implantação</br>
![Implantação de dispositivo no Visual Studio](images/buildsettingsusbdeploy.png)</br>
3. Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</br>
![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)</br>
4. Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN. Siga as instruções de **Como emparelhar o dispositivo** abaixo.

## <a name="deploying-an-app-over-usb---hololens-2"></a>Como implantar um aplicativo via USB – HoloLens 2

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. Selecione uma configuração de build **ARM** ou **ARM64** para o aplicativo</br>
![Configuração de build ARM64 no Visual Studio](images/arm64setting.png)</br>
2. Selecione **Dispositivo** no menu suspenso do destino de implantação</br>
![Implantação de dispositivo no Visual Studio](images/buildsettingsusbdeploy_arm64.png)</br>
3. Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</br>
![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)</br>
4. Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN. Siga as instruções de **Como emparelhar o dispositivo** abaixo.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Como implantar um aplicativo no computador local – headset imersivo

Para usar um headset imersivo do Windows Mixed Reality que se conecta ao computador ou o [simulador de realidade misturada](using-the-windows-mixed-reality-simulator.md):
1. Selecione uma configuração de build **x86** ou **x64** para o aplicativo
2. Selecione **Computador Local** no menu suspenso do destino de implantação
3. Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração

## <a name="pairing-your-device"></a>Como emparelhar o dispositivo

Na primeira vez que implantar um aplicativo no HoloLens por meio do Visual Studio, você deverá fornecer um PIN. No HoloLens, gere um PIN iniciando o aplicativo Configurações, acesse **Atualizar > Para Desenvolvedores** e toque em **Emparelhar**. Quando o PIN for exibido no seu HoloLens, digite-o no Visual Studio. Após a conclusão do emparelhamento, toque em **Concluído** no HoloLens para ignorar a caixa de diálogo. Este computador agora está emparelhado com o HoloLens, e você pode implantar aplicativos automaticamente. Repita essas etapas para todos os computadores usados para implantar aplicativos no HoloLens.

Para desemparelhar seu HoloLens de todos os computadores emparelhados:
* Inicie o aplicativo **Configurações**, acesse **Atualização > Para Desenvolvedores** e toque em **Desmarcar**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Como implantar um aplicativo no Emulador do HoloLens (1ª geração)
1. Verifique se você **[instalou o Emulador do HoloLens](../install-the-tools.md)** .
2. Selecione uma configuração de build **x86** para o aplicativo.</br>
![Configuração de build x86 no Visual Studio](images/x86setting.png)</br>
3. Selecione **Emulador do HoloLens** no menu suspenso do destino de implantação</br>
![Destino do emulador no Visual Studio](images/deployemulator.png)</br>
4. Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</br>
![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)</br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Como implantar um aplicativo no Emulador do HoloLens 2
1. Verifique se você **[instalou o Emulador do HoloLens](../install-the-tools.md)** .
2. Selecione uma configuração de build **x86** ou **x64** para o aplicativo.</br>
![Configuração de build x86 no Visual Studio](images/x86setting.png)</br>
3. Selecione **Emulador do HoloLens 2** no menu suspenso do destino de implantação</br>
![Destino do emulador no Visual Studio](images/deployemulator2.png)</br>
4. Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</br>
![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)</br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Depurador de Gráficos do HoloLens (1ª geração)

As ferramentas Diagnóstico de Gráficos do Visual Studio são úteis quando você quer escrever e otimizar um aplicativo holográfico. Confira [Diagnóstico de Gráficos do Visual Studio no MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) para obter detalhes completos.

**Para iniciar o Depurador de Gráficos**
1. Siga as instruções acima para definir um dispositivo ou um emulador como destino
2. Acesse **Depurar > Gráficos > Iniciar Diagnóstico**
3. Na primeira vez que você iniciar o diagnóstico com um HoloLens, talvez você receba um erro de "acesso negado". Reinicialize o HoloLens para permitir que as permissões atualizadas entrem em vigor e tente novamente.

## <a name="profiling"></a>Criação de perfil

As ferramentas de criação de perfil do Visual Studio permitem que você analise o desempenho e o uso de recursos do seu aplicativo. Isso inclui ferramentas para otimizar a CPU, a memória, os elementos gráficos e o uso da rede. Confira [Executar ferramentas de diagnóstico sem depuração no MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) para obter detalhes completos.

**Para iniciar as ferramentas de criação de perfil com o HoloLens**
1. Siga as instruções acima para definir um dispositivo ou um emulador como destino
2. Acesse **Depurar > Iniciar Ferramentas de Diagnóstico sem Depuração...**
3. Selecione as ferramentas que deseja usar
4. Selecione **Iniciar**
5. Na primeira vez que você iniciar o diagnóstico sem fazer a depuração com um HoloLens, talvez você receba um erro de "acesso negado". Reinicialize o HoloLens para permitir que as permissões atualizadas entrem em vigor e tente novamente.

## <a name="debugging-an-installed-or-running-app"></a>Como depurar um aplicativo instalado ou em execução

Use o Visual Studio para depurar um aplicativo universal do Windows instalado sem a implantação por meio de um projeto do Visual Studio. Isso será útil se você quiser depurar um pacote do aplicativo instalado ou um aplicativo que já esteja em execução.
1. Acesse **Depurar -> Outros Destinos de Depuração-> Depurar Pacote do Aplicativo Instalado**
2. Selecione o destino **Computador Remoto** para o HoloLens ou **Computador Local** para headsets imersivos.
3. Insira o endereço IP do **dispositivo**
4. Escolha o Modo de Autenticação **Universal**
5. A janela mostrará os aplicativos em execução e inativos. Escolha aquele que deseja depurar.
6. Escolha o tipo de código para depuração (Gerenciado, Nativo, Misto)
7. Selecione **Anexar** ou **Iniciar**

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity, você está no meio do estágio de implantação. Deste ponto, você pode prosseguir para o próximo tópico:

> [!div class="nextstepaction"]
> [Como fazer a implantação no emulador do HoloLens](using-the-hololens-emulator.md)

Ou vá diretamente para a adição de serviços avançados:

> [!div class="nextstepaction"]
> [Serviços avançados](../../develop/unity/unity-development-overview.md#5-adding-services)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) a qualquer momento.

## <a name="see-also"></a>Veja também
* [Instalar as ferramentas](../install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como implantar e depurar aplicativos UWP (Plataforma Universal do Windows)](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [Habilitar o dispositivo para desenvolvimento](/windows/uwp/get-started/enable-your-device-for-development)