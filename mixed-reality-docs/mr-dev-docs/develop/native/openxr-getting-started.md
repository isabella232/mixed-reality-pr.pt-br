---
title: Introdução ao OpenXR
description: introdução ao uso do padrão de API OpenXR portátil em fones de ouvido Windows Mixed Reality e HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality, OpenXR Ferramentas para Desenvolvedores, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, introdução, 101, extensões de visualização, versão de tempo de execução do OpenXR, status do sistema
ms.openlocfilehash: 6d334b491d231ab5987dd1bc6a3eb43f5e0fe30a82c6525bca1935fbf1cd83bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189136"
---
# <a name="getting-started-with-openxr"></a>Introdução ao OpenXR

Faça o desenvolvimento com o OpenXR em um headset imersivo do HoloLens 2 ou do Windows Mixed Reality na área de trabalho.  se você não tiver acesso a um headset, poderá usar o HoloLens 2 Emulator ou o simulador de Windows Mixed Reality em vez disso.

## <a name="getting-started-with-openxr-for-hololens-2"></a>introdução ao OpenXR para HoloLens 2

para começar a desenvolver aplicativos OpenXR para o HoloLens 2:

1. configure um HoloLens 2 ou siga as instruções para [instalar uma versão recente do emulador HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md). Você já deve ter o OpenXR 1,0 pronto para começar se estiver usando uma imagem de emulador recente ou se o dispositivo tiver atualizado seu sistema operacional.
2. Verifique se você tem o tempo de execução OpenXR mais recente com todas as [extensões](openxr.md#roadmap) presentes iniciando o aplicativo da **loja** no dispositivo ou emulador.
    * Abra o menu no canto superior direito, selecione **downloads e atualizações** e escolha **obter atualizações**.  

> [!NOTE]
> se você estiver usando o emulador, a imagem do emulador será redefinida sempre que você iniciá-lo e, portanto, sua melhor aposta é apenas verificar se você tem [a versão mais recente da imagem do emulador do HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>introdução ao OpenXR para fones de ouvido Windows Mixed Reality

para começar a desenvolver aplicativos OpenXR para a imersão Windows Mixed Reality headsets:

1. certifique-se de que você esteja executando pelo menos o Atualização de maio de 2019 para o Windows 10 (1903), que é o requisito mínimo para Windows Mixed Reality usuários finais executem aplicativos OpenXR.  se você estiver em uma versão anterior do Windows 10, poderá atualizar usando o assistente de <a href="https://www.microsoft.com/software-download/windows10" target="_blank">atualização do Windows 10</a>.
2. configure um Windows Mixed Reality headset ou siga as instruções para [habilitar o simulador de Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).

É isso!  o tempo de execução do Windows Mixed Reality OpenXR é instalado e torna-se ativo automaticamente para todos os usuários de Windows Mixed Reality.  o Microsoft Store mantém o tempo de execução atualizado.

para ativar o Windows Mixed Reality o tempo de execução OpenXR novamente, inicie o Portal de realidade misturada na menu Iniciar e selecione "corrigir" na parte superior da janela.  Se esse botão estiver ausente, o tempo de execução do OpenXR já estará ativo.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Obtendo o Ferramentas para Desenvolvedores OpenXR para Windows Mixed Reality

para experimentar o Windows Mixed Reality tempo de execução OpenXR, você pode instalar o <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">OpenXR Ferramentas para Desenvolvedores para Windows Mixed Reality aplicativo</a>.  Este aplicativo fornece uma demonstração de vários recursos do OpenXR, juntamente com uma página de status do sistema com informações importantes sobre o tempo de execução ativo e o headset atual.

ao usar o emulador HoloLens 2, a maneira mais fácil de instalar o OpenXR Ferramentas para Desenvolvedores para Windows Mixed Reality é por meio do [Portal do dispositivo Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md). navegue até a página "OpenXR" e, em seguida, clique no botão "instalar" em "recursos do desenvolvedor", que também funciona em dispositivos físicos HoloLens 2.

![Ferramentas para Desenvolvedores OpenXR para Windows Mixed Reality aplicativo](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Criando um aplicativo OpenXR de exemplo

Certifique-se de [instalar as ferramentas](../install-the-tools.md) necessárias para o desenvolvimento do OpenXR, caso ainda não tenha feito isso.

o projeto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> mostra um exemplo de OpenXR simples com arquivos de projeto do Win32 e UWP HoloLens 2 no Visual Studio. como a solução contém um projeto HoloLens UWP, você precisará da [carga de trabalho de desenvolvimento Plataforma Universal do Windows](../install-the-tools.md#installation-checklist) instalada no Visual Studio para abri-lo totalmente.

Embora os arquivos de projeto Win32 e UWP sejam separados devido a diferenças no empacotamento e na implantação, o código do aplicativo dentro de cada projeto é quase exatamente o mesmo!

Depois de criar um .EXE de área de trabalho Win32 do OpenXR, você pode usá-lo com um headset VR em qualquer plataforma de VR desktop que dê suporte a OpenXR, seja qual for o tipo de headset.

depois de criar um pacote de aplicativo OpenXR UWP, você pode [implantar esse pacote](../platform-capabilities-and-apis/using-visual-studio.md) em um dispositivo HoloLens 2 ou no HoloLens 2 Emulator.

## <a name="learning-the-openxr-api"></a>Learning a API OpenXR

Para obter um tour pela API do OpenXR, confira este vídeo de 60 minutos do exemplo de <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> no Visual Studio.  O vídeo mostra como cada um dos principais componentes da API OpenXR pode ser usado em seu próprio mecanismo e também demonstra alguns dos aplicativos criados no OpenXR hoje:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrar o carregador do OpenXR a um projeto

Para começar a usar o OpenXR em um projeto existente, você incluirá o carregador do OpenXR.  O carregador descobre o tempo de execução do OpenXR ativo no dispositivo e fornece acesso às funções principais e às funções de extensão que ele implementa.

você pode [fazer referência ao pacote de NuGet oficial do OpenXR](#reference-official-openxr-nuget-package) de seu projeto Visual Studio ou [incluir a origem do carregador OpenXR oficial](#include-official-openxr-loader-source) do repositório Khronos GitHub.  Qualquer uma das abordagens fornecerá acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

se você estiver interessado em experimentar `MSFT_preview` extensões também, poderá [copiar os cabeçalhos de OpenXR](#using-preview-extensions) da realidade misturada do repositório GitHub do reality.

### <a name="reference-official-openxr-nuget-package"></a>OpenXR pacote de NuGet oficial de referência

o <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">pacote de NuGet **OpenXR. Loader**</a> é a maneira mais fácil de fazer referência a um carregador de OpenXR predefinido .DLL em sua solução de Visual Studio C++.  Isso dará acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

para adicionar um OpenXR. Loader NuGet referência de pacote à sua solução de Visual Studio C++:
1. em **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto que usará OpenXR e selecione **gerenciar pacotes de NuGet...**.
2. Alterne para a guia **procurar** e procure **OpenXR. Loader**.
3. Selecione o pacote **OpenXR. Loader** e selecione instalar no painel de detalhes à direita.
4. Selecione OK para aceitar as alterações em seu projeto.
5. Adicione `#include <openxr/openxr.h>` a um arquivo de origem para começar a usar a API OpenXR.

Para ver um exemplo da API OpenXR em ação, confira o aplicativo de exemplo <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Incluir origem do carregador de OpenXR oficial

Se você quiser criar o carregador por conta própria, por exemplo, para evitar o carregador extra .DLL, você pode extrair as fontes oficiais do Khronos OpenXR Loader para seu projeto.  Isso dará acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

Para começar aqui, siga as instruções no <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">repositório Khronos OpenXR-SDK em github</a>.  o projeto está configurado para compilar com CMake-se você estiver usando MSBuild, você precisará copiar o código em seu próprio projeto.

## <a name="using-preview-extensions"></a>Usando extensões de visualização

As `MSFT_preview` extensões listadas no [roteiro de extensão](openxr.md#roadmap) são extensões experimentais do fornecedor sendo visualizadas para coletar comentários.  Essas extensões são apenas para dispositivos de desenvolvedor e serão removidas quando a extensão real for entregue.

Se você estiver interessado em experimentar as extensões disponíveis `MSFT_preview` , siga as etapas a seguir para atualizar seu projeto:
1. Siga uma das abordagens acima para integrar um carregador de OpenXR ao seu projeto.
2. Substitua os cabeçalhos OpenXR padrão em seu projeto pelos <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">cabeçalhos de visualização do repositório OpenXR da realidade misturada em github</a>.

para ativar o suporte de extensão de visualização no seu destino HoloLens 2 ou PC desktop:
  1. Para verificar se você tem o tempo de execução OpenXR mais recente com todas as [extensões](openxr.md#roadmap) presentes, inicie o aplicativo da **loja** de dentro do dispositivo ou emulador de destino, abra o menu no canto superior direito, selecione **downloads e atualizações** e escolha **obter atualizações**.
  2. instale o <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">Ferramentas para Desenvolvedores do OpenXR para Windows Mixed Reality aplicativo</a> do Microsoft Store no dispositivo de destino e execute-o.
  3. navegue até a guia **Configurações do desenvolvedor** e habilite usar o tempo de **execução mais recente do OpenXR**.  Isso habilita o tempo de execução de visualização em seu dispositivo, que tem extensões de visualização ativadas.
     ![guia do OpenXR Ferramentas para Desenvolvedores para Windows Mixed Reality desenvolvedor de aplicativo Configurações](images/mixed-reality-openxr-developer-tools-settings.png)
  4. confirme se a **versão de tempo de execução** mostrada na guia Status do **sistema** do [Ferramentas para Desenvolvedores OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) corresponde à versão necessária das extensões de visualização que você planeja experimentar.  Nesse caso, você deve ver a extensão na lista de **extensões** .  Quando uma extensão estável estiver disponível, sua extensão de visualização será removida.<br />
     ![Ferramentas para Desenvolvedores OpenXR para Windows Mixed Reality guia Status do sistema de aplicativos](images/mixed-reality-openxr-developer-tools-status.png)

Consulte o <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">repositório OpenXR de realidade misturada</a> para obter a documentação dessas extensões de visualização e exemplos de como usá-las.

## <a name="troubleshooting"></a>Solução de problemas

Se você tiver problemas para entrar em funcionamento com o desenvolvimento do OpenXR, confira nossas [dicas de solução de problemas](openxr-troubleshooting.md).