---
title: Como configurar a Ferramenta de Recursos de Realidade Misturada
description: Saiba como baixar e instalar os pacotes do Unity de Realidade Misturada por meio da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731928"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Como configurar a Ferramenta de Recursos de Realidade Misturada

Ao usar a Ferramenta de Recursos de Realidade Misturada, você tem acesso a três categorias de configurações diferentes que podem ser personalizadas conforme desejado:

* [Configurações de download](#download-settings)
* [Configurações do recurso](#feature-settings)
* [Configurações de importação](#import-settings)

## <a name="download-settings"></a>Configurações de download

![Configurações de download](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>Substituir arquivos de pacote existentes

A habilitação dessa configuração faz com que os arquivos de pacote sejam baixados toda vez que são adquiridos. 

* **Recomendamos manter essa opção desabilitada para reduzir o uso de largura de banda da rede**
* Por padrão, os arquivos de pacote adquiridos anteriormente não são baixados novamente

### <a name="package-cache"></a>Cache de pacote

Altere essa configuração para atualizar o local de download dos pacotes de recursos.

> [!NOTE]
> Essa configuração é **somente leitura** nesta versão. As versões futuras poderão torná-la configurável.

## <a name="feature-settings"></a>Configurações do recurso

![Configurações do recurso](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>Mostrar versões prévias

Habilite essa configuração para adquirir as versões prévias.
* Por padrão, as versões prévias não são mostradas na Ferramenta de Recursos de Realidade Misturada 

> [!NOTE]
> Uma versão prévia é definida como contendo a designação **"-preview"** na versão do pacote.

### <a name="show-early-access-program-features"></a>Mostrar recursos do programa de acesso antecipado

Habilite essa configuração para adquirir recursos de versões dos programas de acesso antecipado registrados.

* Por padrão, os recursos de acesso antecipado não são mostrados na Ferramenta de Recursos de Realidade Misturada 

> [!NOTE]
> A habilitação de `Show early access program features` sem `Show preview releases` pode fazer com que os pacotes de acesso antecipado não sejam exibidos na Descoberta.

## <a name="import-settings"></a>Configurações de importação

![Configurações de importação](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>Substituir os arquivos de pacote existentes

Por padrão, a Ferramenta de Recursos de Realidade Misturada remove as cópias anteriores dos pacotes que estão sendo importados para reduzir o tamanho do arquivo e as computações desnecessárias. 

* Desmarque essa configuração para manter todas as versões

### <a name="project-relative-import-path"></a>Caminho relativo de importação do projeto

Altere essa configuração para atualizar o caminho da pasta do projeto na qual os pacotes de recursos são copiados durante a importação. 

* Por exemplo, se a pasta do projeto for **C:\GalaxyExplorer**, o caminho de importação totalmente qualificado será **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Essa configuração é **somente leitura** nesta versão. As versões futuras poderão torná-la configurável.

## <a name="early-access-settings"></a>Configurações de acesso antecipado

![Configurações de acesso antecipado](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>Solicitar confirmação antes de remover um programa de acesso antecipado

Essa configuração determina se um aviso será exibido toda vez que um programa de acesso antecipado for removido.

### <a name="my-previews"></a>Minhas versões prévias

A lista de programas de acesso antecipado registrados. Use `Add`, `Edit` e `Remove` para gerenciar a coleção de programas registrados.

## <a name="diagnostic-settings"></a>Configurações de Diagnóstico

![Configurações de Diagnóstico](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>Arquivo de log

Exibe o caminho para o arquivo de log de diagnóstico.

## <a name="see-also"></a>Confira também

- [Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada](welcome-to-mr-feature-tool.md)