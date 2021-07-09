---
title: Tutoriais de introdução – 3. Como configurar os perfis do MRTK
description: Este curso mostra como configurar os perfis do MRTK (Kit de Ferramentas de Realidade Misturada).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, reconhecimento espacial
ms.localizationpriority: high
ms.openlocfilehash: dc30997bbb43b29bf2495aa98be392af6885f6b8
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112907002"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Como configurar os perfis do MRTK

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a personalizar e configurar os perfis do MRTK.

Os <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">perfis do MRTK</a> são uma árvore de perfis aninhados que compõem as informações de configuração sobre como os sistemas e os recursos do MRTK devem ser inicializados. O perfil de nível superior, o Perfil de Configuração, contém perfis aninhados para cada um dos principais sistemas básicos. Cada perfil aninhado foi projetado para configurar o comportamento do respectivo sistema correspondente.

Este exemplo específico mostrará como ocultar a malha de reconhecimento espacial alterando as configurações do Observador de Malha Espacial. No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis do MRTK.

Como você experimentou quando implantou seu projeto no HoloLens 2 durante o [tutorial anterior](mr-learning-base-02.md#congratulations), a malha de <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Reconhecimento Espacial</a> é uma coleção de malhas que representa a geometria do ambiente. É uma visualização útil de ser vista inicialmente, mas em geral, é desativada para evitar a distração visual e o impacto adicional de desempenho da presença dela.

## <a name="objectives"></a>Objetivos

* Saiba como personalizar e configurar perfis do MRTK
* Ocultar a malha de reconhecimento espacial

## <a name="changing-the-spatial-awareness-display-option"></a>Como alterar a opção de exibição de reconhecimento espacial

As principais etapas que você seguirá para ocultar a malha de reconhecimento espacial são:

1. Clonar o perfil de configuração padrão
2. Habilitar o Sistema de Reconhecimento Espacial
3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão
4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão
5. Altere a visibilidade da malha de reconhecimento espacial

> [!NOTE]
> Por padrão, os perfis do MRTK não são editáveis. Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados. Há várias camadas aninhadas de perfis. Portanto, é comum clonar e editar vários perfis ao definir uma ou mais configurações.

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar o perfil de configuração padrão

> [!NOTE]
> O perfil de configuração é o perfil de nível superior. Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, altere o Perfil de Configuração do **MixedRealityToolkit** para o **DefaultHoloLens2ConfigurationProfile**:

![Componente MixedRealityToolkit do Unity com DefaultHoloLens2ConfigurationProfile selecionado](images/mr-learning-base/base-03-section1-step1-1.png)

Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique em **Clonar** para abrir a janela Clonar perfil:

![Botão Copiar e Personalizar do componente MixedRealityToolkit do Unity](images/mr-learning-base/base-03-section1-step1-2.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_HoloLens2ConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:

![Janela pop-up Perfil de Configuração do clone de MixedRealityToolkit do Unity](images/mr-learning-base/base-03-section1-step1-3.png)

Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:

![Componente MixedRealityToolkit do Unity com o HoloLens2ConfigurationProfile personalizado recém-criado aplicado](images/mr-learning-base/base-03-section1-step1-4.png)

No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.

> [!TIP]
> Lembre-se de salvar seu trabalho ao longo dos tutoriais.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar o Sistema de Reconhecimento Espacial

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:

![Componente MixedRealityToolkit do Unity com o Sistema de Reconhecimento Espacial habilitado](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Para projetos futuros, se o seu aplicativo não precisa responder ao ambiente nem interagir com ele, recomendamos manter o reconhecimento espacial desativado para reduzir o custo de desempenho.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão

Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:

![Componente MixedRealityToolkit do Unity com a guia Reconhecimento Espacial selecionada](images/mr-learning-base/base-03-section1-step3-1.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![Janela pop-up Perfil do Sistema de Reconhecimento Espacial do clone de MixedRealityToolkit do Unity](images/mr-learning-base/base-03-section1-step3-2.png)

O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessSystemProfile personalizado recém-criado aplicado](images/mr-learning-base/base-03-section1-step3-3.png)

[!INCLUDE[](includes/configuring-profile.md)]

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Altere a visibilidade da malha de reconhecimento espacial

Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:

![Componente MixedRealityToolkit do Unity com a Opção de Exibição de Observador de Malha Espacial definida como Oclusão](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional. Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.

Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão. Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão. Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) no [Portal de Documentação do MRTK](/windows/mixed-reality/mrtk-unity).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a clonar, personalizar e definir uma configurações e perfis do MRTK.

> [!div class="nextstepaction"]
> [Próximo tutorial: 4. Como posicionar objetos na cena](mr-learning-base-04.md)