---
title: Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada
description: Conheça os conceitos básicos da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 1244f9cd4da0d6ae0b5c6f92698f87f0edd812e2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757084"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada

![Imagem da faixa da Ferramenta de Recursos de Realidade Misturada](images/feature-tool-banner.jpg)

> [!IMPORTANT]
> No momento, a Ferramenta de Recursos de Realidade Misturada só está disponível para o Unity. Se você estiver realizando o desenvolvimento no Unreal, veja a documentação de [instalação das ferramentas](../install-the-tools.md).

A Ferramenta de Recursos de Realidade Misturada é uma nova maneira para os desenvolvedores descobrirem, atualizarem e adicionarem pacotes de recursos de Realidade Misturada em projetos do Unity. Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação. Se você nunca trabalhou com um arquivo de manifesto antes, é um arquivo JSON que contém todos os seus pacotes de projetos. Depois de validar os pacotes desejados, a ferramenta Recurso de Realidade Misturada os baixará no projeto de sua escolha.

## <a name="system-requirements"></a>Requisitos de sistema

Para executar a Ferramenta de Recursos de Realidade Misturada, você precisará do seguinte:

* [Runtime do .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> Atualmente, a Ferramenta de Recursos de Realidade Misturada só é executada no Windows, mas o suporte ao macOS estará disponível em breve.

## <a name="download"></a>Baixar

Depois de configurar seu ambiente:

* [Baixe a última versão da Ferramenta de Recursos da Realidade Misturada](https://aka.ms/MRFeatureTool) no Centro de Download da Microsoft.
* Quando o download for concluído, descompacte o arquivo e salve-o na área de trabalho
    * Recomendamos criar um atalho para o arquivo executável para obter acesso mais rápido

> [!NOTE]
> Se não estiver usando o Gerenciador de Pacotes do Unity, siga nossas [instruções do UPM](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).

## <a name="changes-in-this-release"></a>Alterações nessa versão

A versão 1.0.2103 Beta inclui as seguintes correções:

* Melhorias no download de detecção de erros.
* Atualizações sobre como os manifestos são gravados para evitar falhas na atualização correta.
* O Escpaing foi removido dos caminhos de arquivo no manifesto do projeto.

Os seguintes recursos foram adicionados nesta atualização:

* O catálogo de recursos agora é armazenado em cache. Para verificar se há novos recursos e atualizações, use o botão Atualizar na Descoberta.
* A seleção de projeto foi transferida da etapa Importar para antes da Descoberta.
* Os pacotes disponíveis são filtrados pela versão especificada do Unity do projeto.
* A exibição de descoberta agora mostra os pacotes instalados no momento.

## <a name="1-getting-started"></a>1. Introdução

Inicie a Ferramenta de Recursos de Realidade Misturada por meio do arquivo executável, que exibe a página inicial na primeira inicialização:

![Introdução](images/FeatureToolStart.png)

Na página inicial, você poderá:

* [Definir](configuring-feature-tool.md) as configurações da ferramenta usando o botão de **ícone de engrenagem**
* Usar o botão de **ponto de interrogação** para iniciar o navegador da Web padrão e ver nossa documentação
* Selecione **Iniciar** para começar a descobrir os pacotes de recursos

## <a name="2-selecting-your-unity-project"></a>2. Como selecionar o projeto do Unity

Para garantir que todos os recursos descobertos são compatíveis com a versão do Unity do seu projeto, o primeiro passo é apontar a Ferramenta de Recursos de Realidade Misturada para seu projeto usando o botão de **elipse** (à direita do campo de caminho do projeto).

![Selecionar o projeto do Unity](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo. É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.

Depois de localizar a pasta do projeto, clique em Abrir para retornar à Ferramenta de Recursos de Realidade Misturada.

> [!IMPORTANT]
> A Ferramenta de Recursos de Realidade Misturada executa a validação para garantir que ela tenha sido direcionada para a pasta do projeto do Unity. A pasta deve conter as pastas `Assets`, `Packages` e `Project Settings`.

## <a name="3-discovering-and-acquiring-feature-packages"></a>3. Como descobrir e adquirir pacotes de recursos

> [!NOTE]
> A versão 1.0.2103 Beta agora armazena em cache o conteúdo do catálogo de recursos sempre que o servidor é acessado. Essa alteração permite o acesso rápido aos recursos disponíveis, em detrimento da exibição dos dados absolutos mais recentes. Para atualizar o catálogo, use o botão **Atualizar**.

Os recursos são agrupados por categoria para facilitar a localização dos itens. Por exemplo, a categoria **Kit de Ferramentas de Realidade Misturada** traz vários recursos para sua escolha:

![Descoberta e aquisição](images/FeatureToolDiscovery.png)

Quando a Ferramenta de Recursos de Realidade Misturada reconhece os recursos importados anteriormente, ela exibe uma mensagem de notificação para cada um.

![Notificação do recurso importado](images/feature-tool-imported-note.png)


Depois de fazer suas escolhas, selecione **Obter recursos** para buscar todos os pacotes necessários do catálogo. Para obter mais informações, confira [Como descobrir e adquirir recursos](discovering-features.md).

## <a name="4-importing-feature-packages"></a>4. Como importar pacotes de recursos

Após a aquisição, o conjunto completo de pacotes é apresentado, juntamente com uma lista de dependências necessárias. Caso você precise alterar qualquer seleção de recurso ou pacote, esta é a hora:

![Importando pacotes](images/FeatureToolImport.png)

Recomendamos expressamente usar o botão **Validar** para garantir que o projeto do Unity possa importar os recursos selecionados com êxito. Após a validação, você verá uma caixa de diálogo pop-up com uma mensagem de êxito ou uma lista dos problemas identificados.

Escolha **Importar** para continuar.

> [!NOTE]
> Depois que você clicar no botão **Importar**, se algum problema persistir, uma mensagem simples será exibida. A recomendação é clicar em Não e usar o botão **Validar** para ver e resolver os problemas.

Para obter mais informações, confira [Como importar recursos](importing-features.md).

## <a name="5-reviewing-and-approving-project-changes"></a>5. Como examinar e aprovar as alterações do projeto

A etapa final é examinar e aprovar as alterações propostas para os arquivos de manifesto e de projeto:

* As alterações propostas no manifesto são exibidas à esquerda
* Os arquivos a serem adicionados ao projeto são listados à direita
* O botão **Comparar** permite a exibição lado a lado do manifesto atual e das alterações propostas

![Autorização](images/FeatureToolApprovalRequest.png)

Para obter mais informações, confira [Como examinar e aprovar as modificações do projeto](reviewing-changes.md).

## <a name="6-project-updated"></a>6. Projeto atualizado

Quando as alterações propostas forem aprovadas, o projeto de destino do Unity será atualizado para referenciar os recursos de Realidade Misturada selecionados.

![Projeto atualizado](images/FeatureToolProjectUpdated.png)

A pasta **Pacotes** do projeto do Unity agora tem uma subpasta **MixedReality** com os arquivos do pacote de recursos e o manifesto conterá as referências apropriadas.

Volte ao Unity, aguarde até que os novos recursos selecionados sejam carregados e comece a criar!

## <a name="see-also"></a>Confira também

- [Como configurar a ferramenta de recursos](configuring-feature-tool.md)
- [Descoberta e aquisição](discovering-features.md)
- [Como exibir detalhes do pacote de recursos](viewing-package-details.md)
- [Como importar os pacotes selecionados](importing-features.md)
- [Como examinar e aprovar as modificações do projeto](reviewing-changes.md)