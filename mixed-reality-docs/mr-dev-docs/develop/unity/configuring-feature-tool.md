---
title: Como configurar a Ferramenta de Recursos de Realidade Misturada
description: Saiba como baixar e instalar os pacotes do Unity de Realidade Misturada por meio da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243856"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Como configurar a Ferramenta de Recursos de Realidade Misturada

Ao usar a Ferramenta de Recursos de Realidade Misturada, você tem acesso a três categorias de configurações diferentes que podem ser personalizadas conforme desejado:

* [Configurações de download](#download-settings)
* [Configurações do recurso](#feature-settings)
* [Configurações de importação](#import-settings)

![Configurações](images/FeatureToolSettings.png)

## <a name="download-settings"></a>Configurações de download

### <a name="overwrite-existing-package-files"></a>Substituir arquivos de pacote existentes

A habilitação dessa configuração faz com que os arquivos de pacote sejam baixados toda vez que são adquiridos. 
* **Recomendamos manter essa opção desabilitada para reduzir o uso de largura de banda da rede**
* Por padrão, os arquivos de pacote adquiridos anteriormente não são baixados novamente

### <a name="package-cache"></a>Cache de pacote

Altere essa configuração para atualizar o local de download dos pacotes de recursos.

> [!NOTE]
> Essa configuração é **somente leitura** nesta versão. As versões futuras poderão torná-la configurável.

## <a name="feature-settings"></a>Configurações do recurso

### <a name="include-preview-releases"></a>Incluir versões prévias

Habilite essa configuração para adquirir as versões prévias.
* Por padrão, as versões prévias não são mostradas na Ferramenta de Recursos de Realidade Misturada 

> [!NOTE]
> Uma versão prévia é definida como contendo a designação **"-preview"** na versão do pacote.

## <a name="import-settings"></a>Configurações de importação

### <a name="replace-existing-package-files"></a>Substituir os arquivos de pacote existentes

Por padrão, a Ferramenta de Recursos de Realidade Misturada remove as cópias anteriores dos pacotes que estão sendo importados para reduzir o tamanho do arquivo e as computações desnecessárias. 
* Desmarque essa configuração para manter todas as versões

### <a name="project-relative-import-path"></a>Caminho relativo de importação do projeto

Altere essa configuração para atualizar o caminho da pasta do projeto na qual os pacotes de recursos são copiados durante a importação. 
* Por exemplo, se a pasta do projeto for **C:\GalaxyExplorer**, o caminho de importação totalmente qualificado será **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Essa configuração é **somente leitura** nesta versão. As versões futuras poderão torná-la configurável.

## <a name="see-also"></a>Confira também

- [Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada](welcome-to-mr-feature-tool.md)