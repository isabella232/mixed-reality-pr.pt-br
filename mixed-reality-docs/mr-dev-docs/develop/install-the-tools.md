---
title: Instalar as ferramentas
description: Comece aqui com as versões mais atuais do Unity, do Visual Studio e de ferramentas recomendadas para o desenvolvimento do HoloLens e de VR.
author: thetuvix
ms.author: alexturn
ms.date: 09/15/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: ff365d7d772410a2cd752072a878c37dae1d9b19
ms.sourcegitcommit: 7dad5bde71d429bb23c72a4074e60b6668a7f091
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2021
ms.locfileid: "127857476"
---
# <a name="install-the-tools"></a>Instalar as ferramentas

Obtenha as ferramentas necessárias para criar aplicativos para os headsets imersivos (VR) do Microsoft HoloLens e do Windows Mixed Reality. Não há nenhum SDK separado para o desenvolvimento no Windows Mixed Reality; você usará o Visual Studio com o SDK do Windows 10.

Não tem um dispositivo de realidade misturada? Você pode instalar o [emulador do HoloLens](platform-capabilities-and-apis/using-the-hololens-emulator.md) para testar algumas funcionalidades de aplicativos de realidade misturada sem um HoloLens. Você também pode usar o [simulador do Windows Mixed Reality](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) para testar seus aplicativos de realidade misturada para headsets imersivos.

É recomendável instalar o mecanismo de jogos Unity ou Unreal como a maneira mais fácil de começar a criar aplicativos de realidade misturada. No entanto, você também poderá criar com base no DirectX se quiser usar um mecanismo personalizado.

Se você estiver usando o Unity, poderá usar a simulação de entrada do [Kit de Ferramentas de Realidade Misturada do Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) para testar vários tipos de interações de entrada, como entrada por acompanhamento da mão e acompanhamento ocular. Para projetos do Unreal, use o [plug-in das Ferramentas de UX](https://github.com/microsoft/MixedReality-UXTools-Unreal) para testar interações comuns de entrada e recursos de experiência do usuário.

>[!TIP]
>Adicione esta página aos favoritos e acesse-a regularmente para se manter atualizado sobre a versão mais recente de cada ferramenta recomendada para o desenvolvimento de realidade misturada.

<br>

## <a name="installation-checklist"></a>Lista de verificação da instalação

| Ferramenta | Observações |
|---------|---------|
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (link de instalação manual)</a><br><br>Instale a versão mais recente do Windows 10, para que o sistema operacional do seu computador corresponda à plataforma para a qual você está compilando aplicativos de realidade misturada.  | **Instalação do Windows 10** <br> Você pode instalar a versão mais recente do Windows 10 via Windows Update nas Configurações ou criando uma mídia de instalação, usando o link na coluna à esquerda. <br><br>Veja as [notas de versão atuais](/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md) para obter informações sobre os recursos mais recentes de realidade misturada disponíveis em cada versão do Windows 10. **Ative o modo de desenvolvedor no seu computador** em Configurações > Atualização e Segurança > Para Desenvolvedores. <br><br> **Observação para computadores empresariais e corporativos**<br>Se o computador for gerenciado pelo departamento de TI da sua organização, talvez seja necessário contatá-los para atualizar. <br><br> **"N" versões do Windows**<br> Headsets imersivos (VR) do Windows Mixed Reality não são compatíveis com as versões "N" do Windows. |
| ![Imagem do logotipo do Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 ou superior)** (link de instalação)</a> <br><br>Ambiente de desenvolvimento integrado (IDE) completo para Windows e muito mais. Você usará o Visual Studio para escrever o código, depurar, testar e implantar. | **Instalação do Visual Studio 2019** <br> Certifique-se de instalar as seguintes cargas de trabalho: <br><br>*● Desenvolvimento para desktop com C++*<br>*● Desenvolvimento da UWP (Plataforma Universal do Windows)*<br>*● Desenvolvimento de jogos com Unity (**se estiver planejando usar o Unity**)*<br><br>Na carga de trabalho da UWP, **confira se os seguintes componentes estão incluídos para instalação**:<br><br>*● SDK do Windows 10 versão 10.0.19041.0 ou 10.0.18362.0*<br>*● Conectividade do dispositivo USB (necessária para implantar/depurar no HoloLens via USB)*<br>*● Ferramentas da Plataforma Universal do Windows C++ (v142) (necessárias ao usar o Unity)*<br><br>**Observação sobre o HoloLens (1ª geração) e headsets do Windows Mixed Reality para desktop**<br>Se você estiver desenvolvendo apenas aplicativos HoloLens (1ª geração) ou headsets do Windows Mixed Reality para desktop, use o Visual Studio 2017 e o SDK do Windows instalado por ele.<br><br>**Problemas conhecidos**<br>há alguns problemas conhecidos com a depuração de aplicativos de realidade misturada no Visual Studio 2019 versão 16.0.  Verifique se você atualizou o **Visual Studio 2019 para a versão 16.8 ou superior**. |
| ![Logotipo do Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2172762" target="_blank">**Emulador do HoloLens 2 (Windows Holographic, versão 21H1, atualização de setembro de 2021)** (Link de instalação: 10.0.20348.1010)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador do HoloLens (1ª geração)** (link de instalação: 10.0.17763.134)</a> <br><br>O emulador opcional permite executar aplicativos em uma imagem da máquina virtual do HoloLens sem um HoloLens físico.<br> <br> | Consulte [Usando o emulador do HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) para saber mais sobre como começar a usar o emulador opcional.<br> <br> **O sistema deve ser compatível com Hyper-V** para a instalação do emulador ser bem-sucedida. Consulte a seção de Requisitos de sistema abaixo para obter detalhes. <br> <br> **Observação sobre o Emulador do HoloLens (1ª geração)** <br>  O Visual Studio 2017 é necessário para concluir a instalação com êxito. Se você estiver instalando o emulador do HoloLens (1ª geração) com o Visual Studio 2019, desmarque os modelos do VS e [instale-os por meio do Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Instalar o mecanismo de sua preferência

Agora que você tem o Windows 10, o Visual Studio e o SDK do Windows 10 prontos para uso, vamos instalar e configurar o mecanismo de sua escolha.

> [!div class="nextstepaction"]
> [Escolha do seu mecanismo](choosing-an-engine.md)

## <a name="troubleshooting"></a>Solução de problemas

### <a name="setting-developer-mode-is-grayed-out"></a>A configuração Modo de Desenvolvedor está esmaecida

Se você estiver com problemas para habilitar o Modo de Desenvolvedor no dispositivo, talvez você não seja o [proprietário do dispositivo](/hololens/security-adminless-os). No modo de vários usuários, a pessoa que usa o dispositivo pela primeira vez é o proprietário do dispositivo; os usuários subsequentes não terão as permissões necessárias para habilitar o Modo de Desenvolvedor nem outras alterações de configuração. No entanto, há uma exceção em que o primeiro usuário poderá não ser o proprietário do dispositivo: em um ambiente de Autopilot, que é detalhado na [documentação de segurança do HoloLens](/hololens/security-adminless-os#device-owner).

Entre as soluções possíveis estão:

* Fazer com que o proprietário do dispositivo ative o Modo de Desenvolvedor antes de passar o dispositivo para outros usuários ou desenvolvedores
* Sugerir que o administrador de TI/MDM habilite a [política ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) do CSP para o dispositivo específico ou para um grupo de dispositivos do desenvolvedor.
    * Essa política pode ser definida por [Pacotes de provisionamento](/hololens/hololens-provisioning) ou via [MDM para dispositivos HoloLens](/hololens/hololens-mdm-configure)
* Usar o [ARC (Complemento de Recuperação Avançada)](/hololens/hololens-recovery)

> [!NOTE]
> Saiba mais sobre o gerenciamento de dispositivos na visão geral do **[gerenciamento de dispositivos HoloLens](/hololens/hololens-csp-policy-overview)** .

#### <a name="i-cant-deploy-over-usb"></a>Não consigo implantar via USB

Se não for possível implantar um aplicativo diretamente por USB, verifique se você atendeu a todos os requisitos de instalação listados acima e siga nosso [tutorial passo a passo](unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).
