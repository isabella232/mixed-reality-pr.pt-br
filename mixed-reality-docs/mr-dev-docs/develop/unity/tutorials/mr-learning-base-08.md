---
title: Como usar o acompanhamento de olho
description: Este curso mostra como usar o acompanhamento com os olhos em seus aplicativos de realidade misturada com o MRTK (Kit de Ferramentas de Realidade Misturada).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, acompanhamento do olho
ms.localizationpriority: high
ms.openlocfilehash: 8a12bf37547466a07cd47e34d7fbc41e88ca87d345e2ef4fcd73b749bdfd0322
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227443"
---
# <a name="8-using-eye-tracking"></a>8. Como usar o acompanhamento de olho

Neste tutorial, você aprenderá a habilitar o acompanhamento de olho para o HoloLens 2 e a adicionar acompanhamento de olho a objetos para disparar ações quando o usuário examina os objetos.

> [!NOTE]
> Se você também estiver implantando esse projeto no HoloLens (1ª geração), observe que o acompanhamento de olho só tem suporte no HoloLens 2.

## <a name="objectives"></a>Objetivos

* Saiba como habilitar o acompanhamento de olho para o HoleLens 2
* Saiba como usar o acompanhamento de olho para disparar ações

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Como garantir que a funcionalidade de Entrada de Foco de Olho esteja habilitada

No menu do Unity, selecione Realidade Misturada > Kit de Ferramentas > Utilitários > **Configurar projeto do Unity** para abrir a janela **Configurador de projeto do MRTK**, e na seção **Recursos UWP**, verifique se a opção **Habilitar funcionalidade de entrada do olhar** está esmaecida:

![Janela Configurador de Projeto do MRTK no Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> A funcionalidade de Entrada de Foco deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) quando você configurou o projeto do Unity no início desta série de tutoriais. No entanto, se não estiver habilitada, faça isso agora.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Como habilitar o foco baseado em olho no provedor de foco

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, selecione a guia MixedRealityToolkit > **Entrada** e execute as seguintes etapas:

* Clone o **DefaultHoloLens2InputSystemProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_HoloLens2InputSystemProfile_
* Expandir a seção **Ponteiros**
* Clone o **DefaultMixedRealityPointerProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealityPointerProfile_
* Localize a seção **Configurações de Foco** e marque a caixa de seleção **Acompanhamento de Olho Está Habilitado**

![Componente MixedRealityToolkit do Unity com os perfis recém-criados aplicados e o acompanhamento com os olhos habilitado](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do MRTK](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Como habilitar o controle de olho simulado para o editor do Unity

Na janela hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, navegue até a guia **Entrada** e, em seguida:

* Expanda a seção **Provedores de Dados de Entrada** > **Serviço de Simulação de Entrada**
* Clone o **DefaultMixedRealityInputSimulationProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealityInputSimulationProfile_
* Localize a **Simulação de Olhar** e configure o **Modo de Simulação de Olhar Padrão** como **Eixo Dianteiro da Câmera**

![Unity com o objeto TextMeshPro selecionado](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Como adicionar acompanhamento de olho a objetos

Na janela Hierarquia, expanda **RoverExplorer** > **Botões** e selecione os três objetos do botão filho:

![Unity com objeto Botão selecionado](images/mr-learning-base/base-08-section4-step1-1.png)

Com os três objetos Botão ainda selecionados, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **EyeTrackingTarget** a todos os objetos selecionados:

![Unity com o objeto TextMeshPro selecionado e os componentes adicionados](images/mr-learning-base/base-08-section4-step1-2.png)

Na janela hierarquia, expanda **RoverExplorer** > **Botões** > **Dicas** > **SeeItSayItLabel** > **TextMeshPro**

Em seguida, na janela Hierarquia, selecione o objeto de botão **Dicas** e configure o componente **EyeTrackingTarget** da seguinte maneira:

* Na seção de evento **On Look At Start ()**
  * Clique no ícone pequeno **+** para adicionar outro evento
  * Atribua o objeto **TextMeshPro** do botão **Dicas** ao campo **Nenhum (Objeto)**
  * Na lista suspensa **Sem Função**, selecione **TextMeshPro** > **float fontSize** para atualizar esse valor da propriedade quando o evento for disparado
  * Defina o argumento como **0,06** para aumentar o tamanho da fonte atual de 0,04 em 50%
* Na seção de evento **On Look Away ()**
  * Clique no ícone pequeno **+** para adicionar outro evento
  * Atribua o objeto **TextMeshPro** do botão **Dicas** ao campo **Nenhum (Objeto)**
  * Na lista suspensa **Sem Função**, selecione **TextMeshPro** > **float fontSize** para atualizar esse valor da propriedade quando o evento for disparado
  * Defina o argumento como **0,04** para redefinir o tamanho da fonte de volta para 0,04

![Unity com o objeto Hints TextMeshPro selecionado e o componente EyeTrackingTarget configurado](images/mr-learning-base/base-08-section4-step1-3.png)

**Repita** essa etapa para o objeto de botão **Detalhar** e **Redefinir** para configurar o acompanhamento ocular para os botões restantes.

Se agora você entrar no modo de Jogo e pressionar e manter o botão direito do mouse enquanto move o mouse até que o foco atinja um dos botões, verá o tamanho da fonte do texto aumentar em 50% e ser redefinido de volta ao seu tamanho original ao desviar o olhar:

![Modo de exibição dividida do Modo de reprodução do Unity com o foco sobre o rótulo do botão Detalhar do destino de acompanhamento com os olhos](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a habilitar o acompanhamento de olho para o HoloLens 2 e a adicionar acompanhamento de olho a objetos para disparar ações quando o usuário examina os objetos.

> [!div class="nextstepaction"]
> [Próximo tutorial: 9. Usando comandos de fala](mr-learning-base-09.md)
