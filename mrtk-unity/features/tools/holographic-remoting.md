---
title: Comunicação remota holográfica
description: Documentação do MRTK de Remoção Holográfica
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 637f68e5ad5f360aea4b5c0603a682d61d152a89
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144580"
---
# <a name="holographic-remoting"></a>Comunicação remota holográfica

A transmissão de transmissão holográfica transmite conteúdo holográfico de um computador para seu Microsoft HoloLens em tempo real, usando uma conexão de Wi-Fi ou cabo USB. Esse recurso pode aumentar significativamente a produtividade do desenvolvedor ao desenvolver aplicativos de realidade misturada.

O SDK do XR, conforme mencionado abaixo, refere-se ao novo pipeline XR do [Unity no Unity 2019.3 e além de](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). Consulte [aqui](../../configuration/getting-started-with-mrtk-and-xrsdk.md) para obter mais informações sobre como usar o SDK do XR com o MRTK. XR herdado refere-se ao pipeline XR existente incluído no Unity 2018, preterido no Unity 2019.3 e removido no Unity 2020.

## <a name="initial-setup"></a>Instalação inicial

Para habilitar a migração para um HoloLens, é importante garantir que o projeto está usando os componentes de remoting mais recentes.

1. Abrir **janela > Gerenciador de Pacotes**
    - Se estiver usando o XR herdado: verifique se a versão mais recente **do pacote Windows Mixed Reality** está instalada.
    - Se estiver usando o SDK do XR: verifique se a versão mais recente do pacote **do Plug-in** do Windows XR está instalada.
1. Verifique se o aplicativo de Remoção Holográfica mais recente está instalado, no HoloLens, por meio do Microsoft Store.

Continue as instruções [de instalação de XR](#legacy-xr-setup-instructions) herdado ou instruções de instalação do [SDK do XR,](#xr-sdk-setup-instructions) dependendo de qual pipeline é usado no projeto.

## <a name="legacy-xr-setup-instructions"></a>Instruções de configuração de XR herdou

As instruções abaixo aplicam-se apenas à remoting com o HoloLens 2. Se você executar somente a conexão com o HoloLens (1ª geração), pule para Conectar-se ao [HoloLens com Wi-Fi.](#connecting-to-the-hololens-with-wi-fi)

Ao usar um HoloLens 2, o suporte para comunicação de dados articulados de controle de mãos e olhos foi adicionado ao MRTK. Para habilitar esses recursos, siga as etapas documentadas em [Importar DotNetWinRT para o projeto](#import-dotnetwinrt-into-the-project).

Depois de importada, a próxima etapa é selecionar Utilitários do Kit de **Ferramentas** de Realidade  >    >  **Misturada Windows Mixed Reality** Verificar  >  **Configuração**. Esta etapa adiciona uma definição de script que habilita a dependência DotNetWinRT.

> [!NOTE]
> Ao usar o Unity 2019.4 e mais novo, não é necessário executar o utilitário Verificar Configuração.

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

### <a name="removing-hololens-2-specific-remoting-support"></a>Removendo o suporte de remoting específico do HoloLens 2

Se você estiver em conflito ou outros problemas devido à presença do adaptador DotNetWinRT, entre em contato com um dos [nossos recursos de ajuda.](../../index.md#getting-help)

## <a name="xr-sdk-setup-instructions"></a>Instruções de instalação do SDK do XR

Siga as Windows Mixed Reality de instalação do Windows Mixed Reality na página De início do [MRTK e do SDK do XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) e execute a etapa necessária para a redação do HoloLens Remoting no editor.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Conectando-se ao HoloLens com Wi-Fi

Depois que o projeto tiver sido configurado, uma conexão poderá ser estabelecida com o HoloLens.

1. Em **Configurações > build do** arquivo , verifique se o tipo de build do projeto está definido como **Plataforma Universal do Windows**
1. No HoloLens, iniciar o **aplicativo Holographic Remoting.**
1. No Unity, selecione **Janela > XR > Emulação Holográfica (se estiver usando XR herdado) /Windows XR Plugin Remoting (se** estiver usando o SDK do XR).

    ![Iniciar emulação holográfica](../images/tools/remoting/StartHolographicEmulation.png)

1. De **definir Modo de Emulação** como Remoto para **Dispositivo**.

    ![Definir modo de emulação](../images/tools/remoting/SelectEmulationMode.png)

1. (**_Aplica-se somente ao XR herddo_**) Selecione a **Versão do Dispositivo**.

    ![Selecionar Versão do Dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. Usando o Endereço IP exibido pelo aplicativo Holographic Remoting Player, de definido o **campo Computador** Remoto.

    ![Inserir endereço IP](../images/tools/remoting/EnterIPAddress.png)

1. Clique em **Conectar**.

> [!NOTE]
> Se você não conseguir se conectar, certifique-se de que o HoloLens 2 não esteja conectado ao computador e reinicie o Unity.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Conectando-se ao HoloLens com cabo USB

A conexão de cabo USB oferece melhor qualidade de renderização e estabilidade. Para usar a conexão de cabo USB, desconecte-se do HoloLens de Wi-Fi nas configurações do HoloLens e inicie o aplicativo do player de comunicação remota do Holographic. Ele exibirá um endereço IP que começa com 169. Use esse endereço IP na configuração de emulação de Holographic do Unity para se conectar. Depois que o endereço IP para o cabo USB for identificado, será seguro conectar o HoloLens a Wi-Fi novamente.

## <a name="starting-a-remoting-session"></a>Iniciando uma sessão de comunicação remota

Com o Unity conectado ao HoloLens, insira o modo de reprodução no editor.

Quando a sessão estiver concluída, saia do modo de reprodução.

> [!NOTE]
> Há um problema conhecido com algumas versões do Unity, em que o editor pode travar ao entrar no modo de reprodução durante uma sessão de comunicação remota. Esse problema poderá ser manifestado se a janela Holographic estiver aberta quando o projeto for carregado. Para garantir que esse problema não ocorra, sempre feche a caixa de diálogo Holographic antes de sair do Unity.

## <a name="see-also"></a>Confira também

- [Solução de problemas e limitações de comunicação remota do Holographic](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Termos de licença para software Microsoft Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)