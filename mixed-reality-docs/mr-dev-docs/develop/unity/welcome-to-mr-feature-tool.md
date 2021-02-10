---
title: Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada
description: Conheça os conceitos básicos da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 0aad81ddd625467dd9159232d590b1a4bf68d06b
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570249"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada

![Imagem da faixa da Ferramenta de Recursos de Realidade Misturada](images/feature-tool-banner.png)

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

## <a name="1-getting-started"></a>1. Introdução

Inicie a Ferramenta de Recursos de Realidade Misturada por meio do arquivo executável, que exibe a página inicial na primeira inicialização:

![Introdução](images/FeatureToolStart.png)

Na página inicial, você poderá:

* [Definir](configuring-feature-tool.md) as configurações da ferramenta usando o botão de **ícone de engrenagem**
* Usar o botão de **ponto de interrogação** para iniciar o navegador da Web padrão e ver nossa documentação
* Selecione **Iniciar** para começar a descobrir os pacotes de recursos

## <a name="2-discovering-and-acquiring-feature-packages"></a>2. Como descobrir e adquirir pacotes de recursos

O catálogo do pacote de recursos é recuperado assim que você clica em Iniciar. Os recursos são agrupados por categoria para facilitar a localização dos itens. Por exemplo, a categoria **Kit de Ferramentas de Realidade Misturada** traz vários recursos para sua escolha:

![Descoberta e aquisição](images/FeatureToolDiscovery.png)

Depois de fazer suas escolhas, selecione **Obter recursos** para buscar todos os pacotes necessários do catálogo. Para obter mais informações, confira [Como descobrir e adquirir recursos](discovering-features.md).

## <a name="3-importing-feature-packages"></a>3. Como importar pacotes de recursos

Após a aquisição, o conjunto completo de pacotes é apresentado, juntamente com uma lista de dependências necessárias. Caso você precise alterar qualquer seleção de recurso ou pacote, esta é a hora:

![Importando pacotes](images/FeatureToolImport.png)

Recomendamos expressamente usar o botão **Validar** para garantir que o projeto do Unity possa importar os recursos selecionados com êxito. Após a validação, você verá uma caixa de diálogo pop-up com uma mensagem de êxito ou uma lista dos problemas identificados.

Você também precisará definir a localização do projeto de destino do Unity antes da importação. Use o botão de **reticências** à esquerda do campo do caminho do projeto para a busca. Quando terminar de navegar no sistema de arquivos, abra a pasta que contém o projeto de destino do Unity.

> [!NOTE]
> A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo. É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.

Escolha **Importar** para continuar.

> [!NOTE]
> Depois que você clicar no botão **Importar**, se algum problema persistir, uma mensagem simples será exibida. A recomendação é clicar em Não e usar o botão **Validar** para ver e resolver os problemas.

Para obter mais informações, confira [Como importar recursos](importing-features.md).

## <a name="4-reviewing-and-approving-project-changes"></a>4. Como examinar e aprovar as alterações do projeto

A etapa final é examinar e aprovar as alterações propostas para os arquivos de manifesto e de projeto:

* As alterações propostas no manifesto são exibidas à esquerda
* Os arquivos a serem adicionados ao projeto são listados à direita
* O botão **Comparar** permite a exibição lado a lado do manifesto atual e das alterações propostas

![Autorização](images/FeatureToolApprovalRequest.png)

Para obter mais informações, confira [Como examinar e aprovar as modificações do projeto](reviewing-changes.md).

## <a name="5-project-updated"></a>5. Projeto atualizado

Quando as alterações propostas forem aprovadas, o projeto de destino do Unity será atualizado para referenciar os recursos de Realidade Misturada selecionados:

![Projeto atualizado](images/FeatureToolProjectUpdated.png)

A pasta **Pacotes** do projeto do Unity agora tem uma subpasta **MixedReality** com os arquivos do pacote de recursos e o manifesto conterá as referências apropriadas.

Volte ao Unity, aguarde até que os novos recursos selecionados sejam carregados e comece a criar!

## <a name="see-also"></a>Confira também

- [Como configurar a ferramenta de recursos](configuring-feature-tool.md)
- [Descoberta e aquisição](discovering-features.md)
- [Como exibir detalhes do pacote de recursos](viewing-package-details.md)
- [Como importar os pacotes selecionados](importing-features.md)
- [Como examinar e aprovar as modificações do projeto](reviewing-changes.md)
