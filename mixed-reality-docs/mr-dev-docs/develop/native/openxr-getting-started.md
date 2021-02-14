---
title: Introdução ao OpenXR
description: Comece a usar o padrão de API OpenXR portátil no Windows Mixed Reality e o fone de ouvido 2 do HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, realidade mista do Windows, OpenXR Ferramentas para Desenvolvedores, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, introdução, 101, extensões de visualização, versão de tempo de execução do OpenXR, status do sistema
ms.openlocfilehash: 99bf2e19c0bd7708f8c2421d7a466e77a6a75d84
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496064"
---
# <a name="getting-started-with-openxr"></a>Introdução ao OpenXR

Faça o desenvolvimento com o OpenXR em um headset imersivo do HoloLens 2 ou do Windows Mixed Reality na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o emulador do HoloLens 2 ou o simulador de realidade mista do Windows.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introdução ao OpenXR para o HoloLens 2

Para começar a desenvolver aplicativos OpenXR para o HoloLens 2:

1. Configure um HoloLens 2 ou siga as instruções para [instalar uma versão recente do emulador do HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md). Você já deve ter o OpenXR 1,0 pronto para começar se estiver usando uma imagem de emulador recente ou se o dispositivo tiver atualizado seu sistema operacional.
2. Verifique se você tem o tempo de execução OpenXR mais recente com todas as [extensões](openxr.md#roadmap) presentes iniciando o aplicativo da **loja** no dispositivo ou emulador.
    * Abra o menu no canto superior direito, selecione **downloads e atualizações** e escolha **obter atualizações**.  

> [!NOTE]
> Se você estiver usando o emulador, a imagem do emulador será redefinida sempre que você iniciá-lo e, portanto, sua melhor aposta é apenas verificar se você tem [a versão mais recente da imagem do emulador do HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introdução ao OpenXR for Windows Mixed realness headsets

Para começar a desenvolver aplicativos OpenXR para headsets de imersão misturadas do Windows:

1. Verifique se você está executando pelo menos o Windows 10 pode 2019 atualização (1903), que é o requisito mínimo para que os usuários finais da realidade mista do Windows executem aplicativos OpenXR.  Se você estiver em uma versão anterior do Windows 10, poderá atualizar usando o assistente de <a href="https://www.microsoft.com/software-download/windows10" target="_blank">atualização do Windows 10</a>.
2. Configure um headset de realidade mista do Windows ou siga as instruções para [habilitar o simulador de realidade mista do Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).

É isso!  O tempo de execução do Windows Mixed Reality OpenXR é instalado e torna-se ativo automaticamente para todos os usuários do Windows Mixed Reality.  O Microsoft Store mantém o tempo de execução atualizado.

Para ativar o Windows Mixed Reality OpenXR Runtime novamente, inicie o portal de realidade misturada no menu iniciar e selecione "corrigir" na parte superior da janela.  Se esse botão estiver ausente, o tempo de execução do OpenXR já estará ativo.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Obtendo o Ferramentas para Desenvolvedores OpenXR para a realidade mista do Windows

Para experimentar o tempo de execução do Windows Mixed Reality OpenXR, você pode instalar o <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicativo OpenXR ferramentas para desenvolvedores for Windows Mixed Reality</a>.  Este aplicativo fornece uma demonstração de vários recursos do OpenXR, juntamente com uma página de status do sistema com informações importantes sobre o tempo de execução ativo e o headset atual.

Ao usar o emulador do HoloLens 2, a maneira mais fácil de instalar o OpenXR Ferramentas para Desenvolvedores for Windows Mixed Reality é por meio do [portal do dispositivo Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md). Navegue até a página "OpenXR" e clique no botão "instalar" em "recursos do desenvolvedor", que também funciona em dispositivos físicos do HoloLens 2.

![OpenXR Ferramentas para Desenvolvedores para o aplicativo Windows Mixed Reality](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Criando um aplicativo OpenXR de exemplo

Certifique-se de [instalar as ferramentas](../install-the-tools.md) necessárias para o desenvolvimento do OpenXR, caso ainda não tenha feito isso.

O projeto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> mostra um exemplo de OpenXR simples com arquivos de projeto Win32 e UWP HoloLens 2 no Visual Studio. Como a solução contém um projeto UWP do HoloLens, você precisará do [plataforma universal do Windows carga de trabalho de desenvolvimento](../install-the-tools.md#installation-checklist) instalada no Visual Studio para abri-lo totalmente.

Embora os arquivos de projeto Win32 e UWP sejam separados devido a diferenças no empacotamento e na implantação, o código do aplicativo dentro de cada projeto é quase exatamente o mesmo!

Depois de criar uma área de trabalho do Win32 do OpenXR. EXE, você pode usá-lo com um headset de VR em qualquer plataforma de VR de área de trabalho que dê suporte a OpenXR, seja qual for o tipo de headset.

Depois de criar um pacote de aplicativo OpenXR UWP, você pode [implantar esse pacote](../platform-capabilities-and-apis/using-visual-studio.md) em um dispositivo do hololens 2 ou no emulador do hololens 2.

## <a name="learning-the-openxr-api"></a>Aprendendo a API do OpenXR

Para obter um tour pela API do OpenXR, confira este vídeo de 60 minutos do exemplo de <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> no Visual Studio.  O vídeo mostra como cada um dos principais componentes da API OpenXR pode ser usado em seu próprio mecanismo e também demonstra alguns dos aplicativos criados no OpenXR hoje:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrar o carregador do OpenXR a um projeto

Para começar a usar o OpenXR em um projeto existente, você incluirá o carregador do OpenXR.  O carregador descobre o tempo de execução do OpenXR ativo no dispositivo e fornece acesso às funções principais e às funções de extensão que ele implementa.

Você pode [fazer referência ao pacote OpenXR do NuGet oficial](#reference-official-openxr-nuget-package) do seu projeto do Visual Studio ou [incluir a origem do carregador de OpenXR oficial](#include-official-openxr-loader-source) do repositório GitHub do Khronos.  Qualquer uma das abordagens fornecerá acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

Se você estiver interessado em experimentar `MSFT_preview` extensões também, poderá [copiar os cabeçalhos de OpenXR de visualização](#using-preview-extensions) do repositório GitHub de realidade misturada.

### <a name="reference-official-openxr-nuget-package"></a>OpenXR pacote NuGet oficial de referência

O <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">pacote NuGet **OpenXR. Loader**</a> é a maneira mais fácil de fazer referência a um carregador OpenXR pré-criado. DLL em sua solução do Visual Studio C++.  Isso dará acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

Para adicionar uma referência de pacote NuGet OpenXR. Loader à sua solução do Visual Studio C++:
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto que usará OpenXR e selecione **gerenciar pacotes NuGet...**.
2. Alterne para a guia **procurar** e procure **OpenXR. Loader**.
3. Selecione o pacote **OpenXR. Loader** e selecione instalar no painel de detalhes à direita.
4. Selecione OK para aceitar as alterações em seu projeto.
5. Adicione `#include <openxr/openxr.h>` a um arquivo de origem para começar a usar a API OpenXR.

Para ver um exemplo da API OpenXR em ação, confira o aplicativo de exemplo <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Incluir origem do carregador de OpenXR oficial

Se você quiser criar o carregador por conta própria, por exemplo, para evitar o carregador extra. DLL, você pode extrair as fontes oficiais do Khronos OpenXR Loader para seu projeto.  Isso dará acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

Para começar aqui, siga as instruções no <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">repositório Khronos OpenXR-SDK no GitHub</a>.  O projeto é configurado para compilar com CMake-se você estiver usando o MSBuild, você precisará copiar o código em seu próprio projeto.

## <a name="using-preview-extensions"></a>Usando extensões de visualização

As `MSFT_preview` extensões listadas no [roteiro de extensão](openxr.md#roadmap) são extensões experimentais do fornecedor sendo visualizadas para coletar comentários.  Essas extensões são apenas para dispositivos de desenvolvedor e serão removidas quando a extensão real for entregue.

Se você estiver interessado em experimentar as extensões disponíveis `MSFT_preview` , siga as etapas a seguir para atualizar seu projeto:
1. Siga uma das abordagens acima para integrar um carregador de OpenXR ao seu projeto.
2. Substitua os cabeçalhos OpenXR padrão em seu projeto pelos <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">cabeçalhos de visualização do repositório OpenXR da realidade misturada no GitHub</a>.

Para ativar o suporte de extensão de visualização no seu PC de destino 2 ou computador desktop:
  1. Para verificar se você tem o tempo de execução OpenXR mais recente com todas as [extensões](openxr.md#roadmap) presentes, inicie o aplicativo da **loja** de dentro do dispositivo ou emulador de destino, abra o menu no canto superior direito, selecione **downloads e atualizações** e escolha **obter atualizações**.
  2. Instale o <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicativo OpenXR ferramentas para desenvolvedores for Windows Mixed Reality</a> da Microsoft Store no dispositivo de destino e execute-o.
  3. Navegue até a guia **configurações do desenvolvedor** e habilite usar o tempo de execução do OpenXR de **visualização mais recente**.  Isso habilita o tempo de execução de visualização em seu dispositivo, que tem extensões de visualização ativadas.
     ![Guia de configurações do desenvolvedor do aplicativo OpenXR Ferramentas para Desenvolvedores para Windows Mixed Reality](images/mixed-reality-openxr-developer-tools-settings.png)
  4. Confirme se a **versão de tempo de execução** mostrada na guia status do **sistema** do [OpenXR ferramentas para desenvolvedores para a realidade mista do Windows](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) corresponde à versão necessária das extensões de visualização que você planeja experimentar.  Nesse caso, você deve ver a extensão na lista de **extensões** .  Quando uma extensão estável estiver disponível, sua extensão de visualização será removida.<br />
     ![Guia de status do sistema de aplicativos do OpenXR Ferramentas para Desenvolvedores para Windows Mixed Reality](images/mixed-reality-openxr-developer-tools-status.png)

Consulte o <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">repositório OpenXR de realidade misturada</a> para obter a documentação dessas extensões de visualização e exemplos de como usá-las.

## <a name="troubleshooting"></a>Solução de problemas

Se você tiver problemas para entrar em funcionamento com o desenvolvimento do OpenXR, confira nossas [dicas de solução de problemas](openxr-troubleshooting.md).