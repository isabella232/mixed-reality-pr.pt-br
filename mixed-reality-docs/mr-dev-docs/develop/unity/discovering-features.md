---
title: Como descobrir e adquirir recursos
description: Descubra e baixe recursos de Realidade Misturada.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: fef1edd9e7257985a30739794f4b40164345254e3e76cfa740b3fe9699de79f2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203691"
---
# <a name="discovering-and-acquiring-features"></a>Como descobrir e adquirir recursos

As seções deste artigo descrevem como encontrar pacotes de recursos na Ferramenta de Recursos de Realidade Misturada. Veja a captura de tela abaixo se precisar obter uma referência para uma seção específica:

![Como descobrir recursos](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>Recursos disponíveis

### <a name="category"></a>Categoria

A Ferramenta de Recursos de Realidade Misturada exibe uma coleção de categorias de recursos para facilitar a localização do que você deseja. Expanda uma das categorias para exibir a coleção de recursos disponíveis.

> [!NOTE]
> Caso você não encontre a funcionalidade que está procurando, verifique **Outros recursos**.

![Categoria da funcionalidade](images/FeatureCategory.png)

O cabeçalho da categoria na captura de tela acima contém as seguintes propriedades, da esquerda para a direita:

- Botão Expandir e Recolher
- Nome da categoria (por exemplo: Kit de Ferramentas de Realidade Misturada)
- Contagem de recursos selecionados
- Contagem de recursos disponíveis
- Botões de seção

> [!NOTE]
> Os botões de seleção são sensíveis ao contexto. Conforme o estado da seleção de recursos na categoria, um ou mais dos botões `Select All` e `Select None` serão exibidos.

### <a name="feature"></a>Recurso

![Entrada de recurso](images/FeatureEntry.png)

Os recursos são listados na categoria apropriada. Da esquerda para a direita na captura de tela acima, as entradas de recursos contêm:

- Caixa de seleção
- Nome do recurso (por exemplo: Mixed Reality Toolkit Foundation)
- Lista de versões disponíveis
- Link para os [detalhes do pacote de recursos](viewing-package-details.md)

> [!NOTE]
> Se um recurso for fornecido por um programa de Acesso Antecipado (também chamado de versão prévia privada), um ícone de indicador de ![acesso antecipado](images/EarlyAccess.png) será exibido.

## <a name="refresh-the-feature-catalog"></a>Atualizar o catálogo de recursos

Para verificar se há recursos novos e atualizados, clique no botão Atualizar ![botão Atualizar](images/RefreshButton.png) . Isso se conecta ao site do catálogo e recupera as informações mais recentes. Depois que o catálogo for lido, a data e a hora da última atualização serão exibidas.

## <a name="select-features"></a>Selecionar recursos

Os recursos são selecionados expandindo uma categoria, selecionando uma versão e clicando na caixa de seleção:

![Recursos selecionados](images/SelectedFeatures.png)

Para selecionar todos os pacotes de uma categoria, um botão `Select All` é fornecido. `Select None` cancelará a seleção de todos os pacotes selecionados. 

Cada categoria com um ou mais recursos selecionados será atualizada para exibir a contagem.

## <a name="acquiring-features"></a>Como adquirir recursos

Depois de escolher os recursos, selecione **Obter recursos** para iniciar o download dos arquivos do pacote de recursos selecionados.

> [!NOTE]
> Por padrão, os arquivos do pacote de recursos adquiridos anteriormente não serão baixados novamente. Para alterar esse comportamento, confira [Como configurar a ferramenta de recursos](configuring-feature-tool.md).

Quando o download for concluído, a Ferramenta de Recursos de Realidade Misturada passará para a etapa [Como importar recursos](importing-features.md).

## <a name="going-back-to-the-previous-step"></a>Como voltar à etapa anterior

Em **Descobrir recursos**, a Ferramenta de Recursos de Realidade Misturada permite navegar de volta à seleção de projetos. Selecione **Voltar** para iniciar novamente.

## <a name="see-also"></a>Confira também

- [Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada](welcome-to-mr-feature-tool.md)
- [Como configurar a ferramenta de recursos](configuring-feature-tool.md)
- [Como exibir detalhes do pacote de recursos](viewing-package-details.md)
- [Como importar os pacotes selecionados](importing-features.md)
