---
title: Instalar as ferramentas
description: MRTK-Unity, página de documentação Instalar as ferramentas
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, kit de ferramentas de realidade misturada, instalar, atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador
ms.openlocfilehash: 117b34ae858e789b1366ce5338e23b8f366377ae
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550556"
---
# <a name="install-the-tools"></a>Instalar as ferramentas

Obtenha as ferramentas necessárias para criar aplicativos para os headsets imersivos (VR) do Microsoft HoloLens e do Windows Mixed Reality. Não há nenhum SDK separado para o desenvolvimento no Windows Mixed Reality; você usará o Visual Studio com o SDK do Windows 10.

Não tem um dispositivo de realidade misturada? Você pode instalar o [emulador do HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) para testar algumas funcionalidades de aplicativos de realidade misturada sem um HoloLens. Você também pode usar o [simulador do Windows Mixed Reality](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator) para testar seus aplicativos de realidade misturada para headsets imersivos.

Esta página orientará você na instalação das ferramentas necessárias para usar o MRTK com o Unity. Se você tiver interesse em explorar outras plataformas de desenvolvimento de Realidade Misturada, confira a página [Introdução ao desenvolvimento de Realidade Misturada](/windows/mixed-reality/develop/development?tabs=unity).

Você poderá usar a simulação de entrada do [Kit de Ferramentas de Realidade Misturada do Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) para testar vários tipos de interações de entrada, como acompanhamento da mão e acompanhamento ocular.

|DICA: adicione esta página aos favoritos e acesse-a regularmente para ver atualizações sobre a versão mais recente de cada ferramenta recomendada para o desenvolvimento de realidade misturada.|
|---|

## <a name="installation-checklist"></a>Lista de verificação da instalação

| Ferramenta | Observações |
|---------|---------|
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (link de instalação manual)</a><br><br>Instale a versão mais recente do Windows 10, para que o sistema operacional do seu computador corresponda à plataforma para a qual você está compilando aplicativos de realidade misturada.  | **Instalação do Windows 10** <br> Você pode instalar a versão mais recente do Windows 10 via Windows Update nas Configurações ou criando uma mídia de instalação, usando o link na coluna à esquerda. <br><br>Veja as [notas de versão atuais](/windows/mixed-reality/enthusiast-guide/mixed-reality-software) para obter informações sobre os recursos mais recentes de realidade misturada disponíveis em cada versão do Windows 10. **Ative o modo de desenvolvedor no seu computador** em Configurações > Atualização e Segurança > Para Desenvolvedores. <br><br> **Observação para computadores empresariais e corporativos**<br>Se o computador for gerenciado pelo departamento de TI da sua organização, talvez seja necessário contatá-los para atualizar. <br><br> **"N" versões do Windows**<br> Headsets imersivos (VR) do Windows Mixed Reality não são compatíveis com as versões "N" do Windows. |
| ![Imagem do logotipo do Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 ou superior)** (link de instalação)</a> <br><br>Ambiente de desenvolvimento integrado (IDE) completo para Windows e muito mais. Você usará o Visual Studio para escrever o código, depurar, testar e implantar. | **Instalação do Visual Studio 2019** <br> Certifique-se de instalar as seguintes cargas de trabalho: <br><br>*● Desenvolvimento para desktop com C++*<br>*● Desenvolvimento da UWP (Plataforma Universal do Windows)*<br><br>Na carga de trabalho da UWP, certifique-se de verificar o seguinte componente opcional caso você esteja desenvolvendo para o HoloLens:<br><br>*● Conectividade do dispositivo USB*<br><br>**Observação sobre o Unity**<br>A menos que você esteja tentando instalar intencionalmente uma versão (não LTS) mais recente do Unity para uma finalidade específica, recomendamos *não* instalar a carga de trabalho do Unity como parte da instalação do Visual Studio. Em vez disso, instale o fluxo **2019 LTS do Unity**, conforme indicado abaixo.<br><br>**Problemas conhecidos**<br>há alguns problemas conhecidos com a depuração de aplicativos de realidade misturada no Visual Studio 2019 versão 16.0.  Verifique se você atualizou o **Visual Studio 2019 para a versão 16.8 ou superior**. |
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**SDK do Windows 10 (10.0.18362.0)** (link de instalação manual)</a> <br><br>Fornece os cabeçalhos, bibliotecas, metadados e ferramentas mais recentes para a compilação de aplicativos do Windows 10 no HoloLens 2. | **Para criar aplicativos do HoloLens 2, você precisará instalar o SDK do Windows, build 18362 ou posterior.**<br> <br> Se você estiver desenvolvendo aplicativos somente para headsets do Windows Mixed Reality de área de trabalho ou HoloLens (1ª geração), poderá usar o SDK do Windows instalado pelo Visual Studio 2019. |
| ![Logotipo do Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">**Emulador do HoloLens 2 (Windows Holographic, versão 20H2, atualização de fevereiro de 2021)** (Link de instalação: 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador do HoloLens (1ª geração)** (link de instalação: 10.0.17763.134)</a> <br><br>O emulador permite executar aplicativos em uma imagem de máquina virtual do HoloLens sem um HoloLens físico.<br> <br> | Veja [Usando o emulador do HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) para obter mais informações sobre como começar a usar o emulador.<br> <br> **O sistema deve ser compatível com Hyper-V** para a instalação do emulador ser bem-sucedida. Consulte a seção de Requisitos de sistema abaixo para obter detalhes. <br> <br> **Observação sobre o Emulador do HoloLens (1ª geração)** <br>. Se você estiver instalando o emulador do HoloLens (1ª geração) com o Visual Studio 2019, desmarque os modelos do VS e [instale-os por meio do Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="unity"></a>Unity

Agora que você tem o Windows 10, o Visual Studio e o SDK do Windows 10 prontos para uso, vamos usar o Unity como mecanismo para a criação.

### <a name="1-download-the-latest-version"></a>1. Baixar a última versão

Recomendamos usar o fluxo [LTS (Suporte de Longo Prazo) do Unity](https://unity3d.com/unity/qa/lts-releases), pois ele é a melhor versão para iniciar projetos. Atualize para a última revisão para obter as correções estáveis mais recentes.

* A recomendação atual é usar o [Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4). O Unity 2018.4 LTS também tem suporte.
* Se você quiser usar a versão prévia dos recursos de [Realidade Misturada OpenXR](/windows/mixed-reality/develop/unity/openxr-getting-started) com o MRTK, será necessário o ter o Unity 2020.2 ou superior.
* Caso você precise usar outra versão do Unity por motivos específicos, o Unity dá suporte a instalações lado a lado de versões diferentes.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Instalar a Ferramenta de Recursos de Realidade Misturada

A [Ferramenta de Recursos de Realidade Misturada](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) é uma nova maneira para os desenvolvedores descobrirem e adicionarem pacotes de recursos de Realidade Misturada em projetos do Unity.

Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação. Depois de validar os pacotes desejados, a ferramenta Recurso de Realidade Misturada os baixará no projeto do Unity de sua escolha.

#### <a name="importing-the-mixed-reality-toolkit"></a>Como importar o Kit de Ferramentas de Realidade Misturada

É possível baixar o pacote do Kit de Ferramentas de Realidade Misturada seguindo as [instruções de instalação e uso](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements) e selecionando o pacote do Mixed Reality Toolkit Foundation.

Se preferir baixar manualmente os pacotes do MRTK do GitHub, visite a página de lançamento em [Kit de Ferramentas de Realidade Misturada – Unity (GitHub)](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurar seu computador para o desenvolvimento de Realidade Misturada

O SDK do Windows 10 funciona melhor no sistema operacional Windows 10. Esse SDK também é compatível com: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Observe que nem todas as ferramentas são compatíveis com sistemas operacionais mais antigos.

| Observação: desenvolva e implante seus aplicativos para o HoloLens, os headsets imersivos de VR ou ambos. Verifique se você atende aos requisitos abaixo, dependendo das suas necessidades. |
|---|

#### <a name="for-hololens-development"></a>Desenvolvimento para o HoloLens

Ao configurar seu computador para o desenvolvimento para o HoloLens, verifique se ele atende aos requisitos de sistema do [Unity](https://docs.unity3d.com/Manual/system-requirements.html) e do Visual Studio. Se desejar executar seu aplicativo em um dispositivo HoloLens, você precisará seguir as [instruções de instalação do Portal de Dispositivos do Windows](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal). Se você pretende usar o [emulador do HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator), verifique se o computador também atende aos [requisitos do sistema do emulador do HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements).

Para começar a usar o emulador do HoloLens, veja [Usando o emulador do HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).

Se você planeja desenvolver para headsets imersivos (VR) do HoloLens e do Windows Mixed Reality, use as recomendações e requisitos de sistema descritos na próxima seção.

### <a name="hololens-troubleshooting"></a>Solução de problemas do HoloLens

A configuração Modo de Desenvolvedor está esmaecida

Se você estiver com problemas para habilitar o Modo de Desenvolvedor no dispositivo, talvez você não seja o [proprietário do dispositivo](/hololens/security-adminless-os). No modo de vários usuários, a pessoa que usa o dispositivo pela primeira vez é o proprietário do dispositivo; os usuários subsequentes não terão as permissões necessárias para habilitar o Modo de Desenvolvedor nem outras alterações de configuração. No entanto, há uma exceção em que o primeiro usuário poderá não ser o proprietário do dispositivo: em um ambiente de Autopilot, que é detalhado na [documentação de segurança do HoloLens](/hololens/hololens2-compliance).

Entre as soluções possíveis estão:

* Fazer com que o proprietário do dispositivo ative o Modo de Desenvolvedor antes de passar o dispositivo para outros usuários ou desenvolvedores
* Sugerir que o administrador de TI/MDM habilite a [política ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) do CSP para o dispositivo específico ou para um grupo de dispositivos do desenvolvedor.
Essa política pode ser definida por [Pacotes de provisionamento](/hololens/hololens-provisioning) ou via [MDM para dispositivos HoloLens](/hololens/hololens-mdm-configure)
* Usar o [ARC (Complemento de Recuperação Avançada)](/hololens/hololens-recovery)

| Observação: saiba mais sobre o gerenciamento de dispositivos na visão geral do gerenciamento de dispositivos HoloLens.|
|---|

Não consigo implantar via USB

Se não for possível implantar um aplicativo diretamente por USB, verifique se você atendeu a todos os requisitos de instalação listados acima e siga nosso [tutorial passo a passo](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2).

Requisitos do headset imersivo (VR)

| Observação: as diretrizes a seguir são as especificações atuais mínimas e recomendadas para seu computador de desenvolvimento para headset imersivo (VR) e são atualizadas regularmente.|
|---|

| Aviso: não confunda essas informações com as [diretrizes de compatibilidade mínima de hardware do computador](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que descrevem as especificações do computador do consumidor, que é o alvo do seu jogo ou aplicativo de headset imersivo (VR).|
|---|

Se seu computador de desenvolvimento de headset imersivo não tiver portas HDMI e/ou USB 3.0 padrão, você precisará de [adaptadores](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar o headset.

Atualmente, há [problemas conhecidos](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) com algumas configurações de hardware, especialmente em notebooks com gráficos híbridos.

. | Mínimo | Recomendado
--- |--- |---
Processador | Notebook: CPU Intel Mobile Core i5 de 7ª geração, Dual-Core com Hyper Threading Área de trabalho: CPU Intel i5 de 6ª geração, Dual-Core com Hyper Threading OU equivalente a AMD FX4350 4,2Ghz Quad-Core| Área de trabalho: Intel Desktop i7 6ª geração (6 núcleos) OU GPU AMD Ryzen 5 1600 (6 núcleos, 12 threads) | Notebook: NVIDIA GTX 965M, GPU equivalente ou superior a AMD RX 460M (2GB) com capacidade DX12 Computador: NVIDIA GTX 960/1050, GPU equivalente ou superior a AMD Radeon RX 460 (2GB) com capacidade DX12 | Área de trabalho: NVIDIA GTX 980/1060, GPU equivalente ou superior a AMD Radeon RX 480 (2GB) com capacidade DX12
Versão WDDM do driver da GPU | Driver WDDM 2.2
Potência do design térmico | 15W ou mais
Portas de vídeo | Uma porta de vídeo disponível para headset (HDMI 1.4 ou DisplayPort 1.2 para headsets de 60 Hz, HDMI 2.0 ou DisplayPort 1.2 para headsets de 90 Hz)
Resolução da tela | Resolução: SVGA (800 x 600) ou maior Profundidade de bits: 32 bits de cores por pixel
Memória | 8 GB de RAM ou mais | 16 GB de RAM ou mais
Armazenamento | > 10 GB de espaço livre adicional
Portas USB | 1 x porta USB disponível para headset (USB 3.0 Tipo A) Observação: a USB deve fornecer um mínimo de 900mA
Bluetooth | Bluetooth 4.0 (para conexão de acessórios)

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Agora que você tem as ferramentas instaladas, recomendamos seguir nossa série de tutoriais do MRTK HoloLens 2.
> [!div class="nextstepaction"]
> [Série de tutoriais do HoloLens 2](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)