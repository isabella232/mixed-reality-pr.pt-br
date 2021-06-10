---
title: Comunicação remota holográfica
description: Documentação do Holographic de comunicação remota MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 196bbb7027389ea75ddc577e4efc397ca779d550
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647180"
---
# <a name="holographic-remoting"></a>Comunicação remota holográfica

O Holographicing Remoting transmite o conteúdo do Holographic de um PC para o Microsoft HoloLens em tempo real, usando uma conexão de cabo Wi-Fi ou USB. Esse recurso pode aumentar significativamente a produtividade do desenvolvedor ao desenvolver aplicativos de realidade misturada.

O XR SDK, conforme mencionado abaixo, refere-se ao [novo pipeline XR do Unity no Unity 2019,3 e posterior](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). Consulte [aqui](../../configuration/getting-started-with-mrtk-and-xrsdk.md) para obter mais informações sobre como usar o SDK do XR com MRTK. O XR herdado refere-se ao pipeline XR existente que está incluído no Unity 2018, preterido no Unity 2019,3 e removido no Unity 2020.

## <a name="initial-setup"></a>Instalação inicial

Para habilitar a comunicação remota com um HoloLens, é importante garantir que o projeto esteja usando os componentes de comunicação remota mais recentes.

1. Abrir o **Gerenciador de pacotes do windows >**
    - Se estiver usando a XR Legacy: Verifique se a versão mais recente do pacote do **Windows Mixed Reality** está instalada.
    - Se estiver usando o SDK do XR: Verifique se a versão mais recente do pacote de **plug-in do Windows XR** está instalada.
1. Verifique se o aplicativo de comunicação remota Holographic mais recente está instalado no HoloLens, por meio do Microsoft Store.

Continue nas [instruções de instalação do XR Legacy](#legacy-xr-setup-instructions) ou nas [instruções de instalação do XR SDK](#xr-sdk-setup-instructions) , dependendo de qual pipeline é usado no projeto.

## <a name="legacy-xr-setup-instructions"></a>Instruções de instalação do XR Legacy

As instruções a seguir se aplicam somente à comunicação remota com o HoloLens 2. Se você executar apenas a comunicação remota com o HoloLens (1º gen), pule para [se conectar ao HoloLens com Wi-Fi](#connecting-to-the-hololens-with-wi-fi).

Ao usar um HoloLens 2, o suporte para dados de controle de mão e de acompanhamento de comunicação remota foi adicionado ao MRTK. Para habilitar esses recursos, siga as etapas documentadas em [importar DotNetWinRT para o projeto](#import-dotnetwinrt-into-the-project).

Depois de importado, a próxima etapa é selecionar o **Misto reality**  >  **Toolkit**  >  **utilitários**  >  **Windows Mixed Reality**  >  **check Configuration**. Esta etapa adiciona uma definição de script que habilita a dependência DotNetWinRT.

> [!NOTE]
> Ao usar o Unity 2019,4 e mais recente, não é necessário executar o utilitário verificar configuração.

Para habilitar o acompanhamento de junções de mão e acompanhamento de olho, siga as etapas na seção **depuração de comunicação remota do HoloLens 2 via importação de pacote do Unity** e relacionadas.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Depuração de comunicação remota do HoloLens 2 por meio da importação de pacote do Unity

Se as junções de HoloLens 2 Hands e o acompanhamento de olho não estiverem trabalhando em relação à comunicação remota, haverá alguns pontos comuns de possíveis problemas. Eles estão listados abaixo na ordem em que devem ser verificados.

Esses problemas são especialmente relevantes quando executados no **Unity 2019,3** ou posterior.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importar DotNetWinRT para o projeto

1. Baixe a [ferramenta de funcionalidade de realidade misturada](https://aka.ms/MRFeatureTool)

1. Na exibição **descobrir recursos** , selecione *projeções do WinRT de realidade misturada*

    ![Selecionar pacote DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. Clique em **obter recursos** e continue para [importar o pacote](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT definir gravações nas configurações do Player

> [!NOTE]
> Ao usar o Unity 2019,4 e mais recente, o DOTNETWINRT_PRESENT definir está contido nos arquivos. asmdef apropriados e não nas configurações do Unity Player. A etapa verificar configuração não é necessária.

A partir do MRTK versão 2.5.0, por motivos de desempenho, essa #define não é mais definida automaticamente. Para habilitar esse sinalizador, use o item de menu **Mixed Reality Toolkit**  >    >  **Windows Mixed Reality**  >  **check Configuration** .

> [!Note]
> O item de configuração de verificação não exibe uma confirmação. Para confirmar que a definição foi definida, navegue até as configurações do Player do Unity. A partir daí, na guia UWP, verifique em outras configurações para que os scripts definam símbolos. Verifique se DOTNETWINRT_PRESENT está escrito corretamente na lista. Se isso estiver lá, essa etapa foi bem-sucedida.

![DotNetWinRT presente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>Removendo o suporte a comunicação remota específico do HoloLens 2

Se você estiver executando conflitos ou outros problemas devido à presença do adaptador DotNetWinRT, entre [em contato com um dos nossos recursos de ajuda](../../index.md#getting-help).

## <a name="xr-sdk-setup-instructions"></a>Instruções de instalação do XR SDK

Siga as [instruções de configuração do Windows Mixed Reality na página Introdução ao SDK do MRTK e do XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) e certifique-se de executar a etapa necessária para a comunicação remota do HoloLens no editor.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Conectando-se ao HoloLens com Wi-Fi

Depois que o projeto tiver sido configurado, uma conexão poderá ser estabelecida com o HoloLens.

1. Em **arquivo > configurações de compilação**, verifique se o tipo de compilação do projeto está definido como **plataforma universal do Windows**
1. No HoloLens, inicie o aplicativo de **comunicação remota do Holographic** .
1. No Unity, selecione **Window > XR > emulação de Holographic (se estiver usando o SDK XR)/Windows XR com o plug-in remoto (se estiver usando o kit do XR)**.

    ![Iniciar emulação de Holographic](../images/tools/remoting/StartHolographicEmulation.png)

1. Defina o **modo de emulação** como **remoto para dispositivo**.

    ![Definir modo de emulação](../images/tools/remoting/SelectEmulationMode.png)

1. (**_Aplica-se somente a XR herdado_**) Selecione a **versão do dispositivo**.

    ![Selecionar versão do dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. Usando o endereço IP exibido pelo aplicativo de player de comunicação remota do Holographic, defina o campo **máquina remota** .

    ![Inserir endereço IP](../images/tools/remoting/EnterIPAddress.png)

1. Clique em **Conectar**.

> [!NOTE]
> Se você não puder se conectar, verifique se o seu HoloLens 2 não está conectado ao seu PC e reinicie o Unity.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Conectando-se ao HoloLens com cabo USB

A conexão de cabo USB fornece melhor qualidade de renderização e estabilidade. Para usar a conexão de cabo USB, desconecte-se do HoloLens de Wi-Fi nas configurações do HoloLens e inicie o aplicativo do player de comunicação remota do Holographic. Ele exibirá um endereço IP que começa com 169. Use esse endereço IP na configuração de emulação de Holographic do Unity para se conectar. Depois que o endereço IP para o cabo USB for identificado, será seguro conectar o HoloLens a Wi-Fi novamente.

## <a name="starting-a-remoting-session"></a>Iniciando uma sessão de comunicação remota

Com o Unity conectado ao HoloLens, insira o modo de reprodução no editor.

Quando a sessão estiver concluída, saia do modo de reprodução.

> [!NOTE]
> Há um problema conhecido com algumas versões do Unity, em que o editor pode travar ao entrar no modo de reprodução durante uma sessão de comunicação remota. Esse problema poderá ser manifestado se a janela Holographic estiver aberta quando o projeto for carregado. Para garantir que esse problema não ocorra, sempre feche a caixa de diálogo Holographic antes de sair do Unity.

## <a name="see-also"></a>Confira também

- [Solução de problemas e limitações de comunicação remota do Holographic](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Termos de licença para software Microsoft Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)