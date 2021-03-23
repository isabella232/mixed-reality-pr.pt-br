---
title: Como importar recursos
description: Saiba como importar e instalar recursos da Ferramenta de Recursos de MR para desenvolvimento do HoloLens e da VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, introdução, noções básicas, unity, visual studio, kit de ferramentas, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, instalação, Windows, HoloLens, emulador, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230799"
---
# <a name="importing-features"></a>Como importar recursos

Depois que os recursos forem baixados, eles poderão ser examinados e importados para o projeto do Unity. Nesta etapa, a janela do aplicativo será parecida com a seguinte imagem:

![Como importar recursos](images/FeatureToolImport.png)

## <a name="features-list"></a>Lista de recursos

A lista **Recursos** contém a coleção de pacotes selecionados durante a descoberta. Cada recurso pode ser selecionado ou desmarcado antes da importação. Os detalhes do pacote podem ser exibidos por meio do link **Detalhes** mostrado abaixo

![Lista de recursos](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>Lista de dependências necessárias

A lista **Dependências necessárias** contém os pacotes que um ou mais dos recursos selecionados exigem para funcionar. Essa lista também conterá dependências de dependências. Cada dependência pode ser selecionada ou desmarcada antes da importação. Os detalhes do pacote podem ser exibidos por meio do link **Detalhes** mostrado abaixo

![Lista de dependências](images/RequiredDependencyList.png)

> [!NOTE]
> Se você desmarcar as dependências necessárias, um ou mais erros de dependência ausente serão exibidos ao carregar o projeto no Unity. Esses recursos não poderão ser usados no projeto.

## <a name="validating-selections"></a>Como validar as seleções

Recomendamos expressamente validar as seleções de recursos antes da importação. Esta etapa vai gerar todos os problemas que provavelmente impedem o desenvolvimento bem-sucedido do projeto.

![Problemas de validação](images/ValidationIssues.png)

A Ferramenta de Recursos de Realidade Misturada fornece duas resoluções de problemas automáticas (descritas nas seções a seguir) e a opção de cancelar e resolver problemas manualmente.

### <a name="enable-dependencies"></a>Habilitar dependências

O botão **Habilitar dependências** selecionará automaticamente as dependências ausentes. Isso é verdadeiro para as dependências que foram selecionadas explicitamente (exibidas na lista **Recursos**) e para aquelas selecionadas implicitamente com base nos requisitos dos recursos escolhidos.

### <a name="disable-features"></a>Desabilitar recursos

A seleção de **Desabilitar recursos** desmarcará automaticamente qualquer recurso que dependa de uma ou mais das dependências que foram desmarcadas. Isso é verdadeiro para pacotes de dependência selecionados implicitamente e recursos selecionados explicitamente.

## <a name="importing"></a>Importação

Selecione **Importar** para adicionar os recursos selecionados e conceder [aprovação final](reviewing-changes.md) antes de atualizar o projeto de destino.

> [!IMPORTANT]
> Se um problema de validação permanecer durante a importação, uma mensagem de aviso será exibida. Recomendamos selecionar Não, clicar em **Validar** e resolver os problemas apresentados.
>
> ![Continuar com problemas de validação](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>Como voltar à etapa anterior

Em **Importar recursos**, a Ferramenta de Recursos de Realidade Misturada permite navegar de volta à [descoberta](discovering-features.md). Selecione **Voltar** para baixar outros pacotes de recursos.

## <a name="see-also"></a>Confira também

- [Bem-vindo(a) à Ferramenta de Recursos de Realidade Misturada](welcome-to-mr-feature-tool.md)
- [Descoberta e aquisição](discovering-features.md)
- [Como exibir detalhes do pacote de recursos](viewing-package-details.md)
- [Como examinar e aprovar as modificações do projeto](reviewing-changes.md)