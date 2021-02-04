---
title: Como autorizar as alterações de projeto
description: Saiba como autorizar as alterações de projeto na Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243845"
---
# <a name="authorizing-project-changes"></a>Como autorizar as alterações de projeto

Antes da modificação do projeto do Unity, as alterações nos arquivos de projeto e de manifesto precisam ser examinadas e aprovadas:

![Como solicitar a autorização](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>Manifest

As alterações de manifesto propostas podem ser exibidas na coluna **Manifesto** à esquerda. O conteúdo é exatamente o que será gravado no manifesto do projeto (**Packages/manifest.json**):

![Visualização do manifesto](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>Arquivos a serem copiados para o projeto

A seção **Arquivos a serem copiados para o projeto** à direita lista os arquivos do pacote de recursos específicos que serão copiados para o projeto do Unity:

![Visualização do manifesto com os arquivos a serem copiados](images/FilesToCopy.png)

## <a name="compare-manifests"></a>Comparar manifestos

Você pode ver uma comparação detalhada lado a lado de todas as alterações propostas selecionando **Comparar**:

![Comparar manifestos](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>Como aprovar as alterações

Quando as alterações propostas forem aprovadas, os arquivos listados serão copiados para o projeto do Unity e o manifesto será atualizado com referências a esses arquivos.

> [!NOTE]
> Os arquivos do pacote de recursos (*.tgz) devem ser adicionados ao controle do código-fonte. Eles são referenciados usando um caminho relativo para permitir que as equipes de desenvolvimento compartilhem os recursos e as alterações de manifesto com facilidade.

 Como parte das modificações, o arquivo **manifest.json** atual será copiado em backup.

> [!IMPORTANT]
> Ao exibir os backups de manifesto, o mais antigo será chamado **manifest.json.backup**. Os backups mais recentes serão anotados com um valor numérico, começando com zero (0).

## <a name="going-back-to-the-previous-step"></a>Como voltar à etapa anterior

Caso você precise fazer alterações às seleções de recursos, use **Voltar** para retornar à etapa [Importar](importing-features.md).

## <a name="see-also"></a>Confira também

- [Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada](welcome-to-mr-feature-tool.md)
- [Como importar os pacotes selecionados](importing-features.md)
