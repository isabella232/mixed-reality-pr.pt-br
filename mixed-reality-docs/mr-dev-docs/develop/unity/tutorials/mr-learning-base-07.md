---
title: Como interagir com objetos 3D
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para manipular objetos 3D em aplicativos de realidade misturada e interagir com eles.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, interações de objetos, Controles de Limites
ms.localizationpriority: high
ms.openlocfilehash: 1ab7b3a334639be564717d77d3bbc478a25e8326
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237237"
---
# <a name="7-interacting-with-3d-objects"></a>7. Como interagir com objetos 3D

Neste tutorial, você aprenderá a habilitar a manipulação próxima e distante de objetos 3D e limitar os tipos de manipulação permitidos. Você também aprenderá a adicionar o controle de limites em objetos 3D para facilitar o controle da manipulação de objetos.

## <a name="objectives"></a>Objetivos

* Saber como configurar objetos 3D para interagir com eles
* Saiba como adicionar o controle de limites em objetos 3D

## <a name="manipulating-3d-objects"></a>Como manipular objetos 3D

Nesta seção, você adicionará a capacidade de manipular todas as peças do Rover organizadas na tabela durante o tutorial [Como posicionar objetos na cena](mr-learning-base-04.md).

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar o componente Object Manipulator (Script) a todos os objetos de peças
2. Adicionar o componente NearInteractionGrabbable a todos os objetos de peças
3. Configurar o componente Object Manipulator (Script)

> [!NOTE]
> Para poder **manipular um objeto**, o objeto deve ter os seguintes componentes:
>
> * Componente **Colisor**, por exemplo, um Colisor de Caixa
> * Componente **Object Manipulator (Script)**
>
> Para poder **manipular** e **capturar um objeto com as mãos acompanhadas**, o objeto deve ter os seguintes componentes:
>
> * Componente **Colisor**, por exemplo, um Colisor de Caixa
> * Componente **Object Manipulator (Script)**
> * Componente **NearInteractionGrabbable**

Além disso, você vai configurar o Rover Explorer para poder colocar as peças no Rover e montá-lo completamente.

Na janela Hierarquia, expanda o objeto RoverExplorer > **RoverParts** e selecione todos os seus objetos filho peças do Rover e o objeto **RoverAssembly**; em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes a todos os objetos selecionados:

* Componente **Object Manipulator (Script)**
* Componente **NearInteractionGrabbable**
* Componente **Part Assembly Controller (Script)**

![Unity com RoverAssembly e todos os objetos de partes da sonda selecionados e os componentes adicionados](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> Para selecionar vários objetos que não estão próximos uns dos outros, mantenha a tecla CTRL pressionada e use o mouse para selecionar qualquer objeto.

> [!NOTE]
> Quando você adiciona um Object Manipulator (Script), nesse caso, o Constraint Manager (Script) é adicionado automaticamente porque o Object Manipulator (Script) depende dele.

> [!NOTE]
> Para os fins deste tutorial, os colisores já foram adicionados às peças do Rover. Para saber mais sobre os colisores, acesse a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisor</a> do Unity.

> [!NOTE]
> O Part Assembly Controller (Script) não faz parte do MRTK, mas foi incluído nos ativos do tutorial.

Com todos os objetos de peças do Rover e o objeto RoverAssembly ainda selecionados, na janela Inspetor, configure o componente **Object Manipulator (Script)** da seguinte maneira:

* Na lista suspensa **Tipo de Manipulação de Duas Mãos**, desmarque a Escala, deixando somente **Mover** e **Girar** habilitados

![Unity com Tipo de Manipulação de Duas Mãos configurado](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> Até agora você habilitou a manipulação de objetos para todos os objetos de peças do Rover e o objeto RoverAssembly.

Na janela Projeto, navegue até a pasta **Pacotes** > **Mixed Reality Toolkit Standard Assets** > **Áudio** para localizar os clipes de áudio:

![Janela Projeto do Unity com a pasta Áudio selecionada](images/mr-learning-base/base-07-section1-step1-3.png)

Na janela Hierarquia, selecione novamente todos os **objetos de peças do Rover** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Audio Sources**, configurando-o da seguinte maneira:

* Atribua o clipe de áudio **MRTK_Scale_Start** ao campo **AudioClip**
* Desmarque a caixa de seleção **Reproduzir ao Ativar**
* Altere **Spatial Blend** para 1

![Unity com todas as partes da sonda selecionadas e o componente Fonte de Áudio adicionado e configurado](images/mr-learning-base/base-07-section1-step1-4.png)

Na janela Hierarquia, expanda o objeto RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** para revelar todos os objetos de dica de posicionamento e, em seguida, selecione a primeira peça do Rover, RoverParts > **Camera_Part** e configure o componente **Part Assembly Controller (Script)** da seguinte maneira:

* Atribua o objeto **Camera_PlacementHint** ao campo **Location To Place**

![Unity com o componente Camera_Part de PartAssemblyController configurado](images/mr-learning-base/base-07-section1-step1-5.png)

**Repita** esta etapa para cada um dos objetos de peças do Rover restantes e o objeto RoverAssembly para configurar o componente **Part Assembly Controller (Script)** da seguinte maneira:

* Para o **Generator_Part**, atribua o objeto **Generator_PlacementHint** ao campo **Location To Place**
* Para o **Lights_Part**, atribua o objeto **Lights_PlacementHint** ao campo **Location To Place**
* Para o **UHFAntenna_Part**, atribua o objeto **UHFAntenna_PlacementHint** ao campo **Location To Place**
* Para o **Spectrometer_Part**, atribua o objeto **Spectrometer_PlacementHint** ao campo **Location To Place**
* Para o **RoverAssembly**, atribua o objeto em si, ou seja, o mesmo objeto **RoverAssembly**, para o campo **Location To Place**

Na janela Hierarquia, selecione o botão RoverExplorer > Botões > **Redefinir** e, na janela Inspetor, configure o evento **OnClick ()** interativo da seguinte maneira:

* Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **PartAssemblyController** > **ResetPlacement ()** para definir essa função como a ação a ser executada quando o evento for disparado

![Unity com o evento OnClick do objeto de botão Redefinir configurado](images/mr-learning-base/base-07-section1-step1-6.png)

Se agora você entrar no modo de Jogo, poderá usar a interação próxima ou distante para posicionar as peças no Rover. Depois que a parte estiver próxima da dica de posicionamento correspondente, ela será encaixada no local e se tornará parte do Rover. Para redefinir os posicionamentos, pressione o botão Reset:

![Modo de exibição dividida do Modo de reprodução do Unity com o botão Redefinir recebendo um clique](images/mr-learning-base/base-07-section1-step1-7.png)

Para saber mais sobre o componente Object Manipulator e suas propriedades associadas, acesse o guia [Manipulador de Objeto](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).

## <a name="adding-bounds-control"></a>Como adicionar o Controle de Limites

O Controle de Limites torna mais fácil e mais intuitivo manipular objetos com uma mão tanto em interações próximas como em distantes fornecendo alças que podem ser usadas para escala e rotação.

Neste exemplo, você adicionará um BoundsControl ao objeto RoverExplorer para que toda a experiência seja facilmente movida, girada e escalonada. Além disso, você vai configurar o Menu para poder ativar e desativar o Controle de Limites.

Na janela Hierarquia, selecione o objeto **RoverExplorer** e, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes:

* Componente **BoundsControl**
* Componente **Object Manipulator (Script)**

Em seguida, **desmarque** a caixa de seleção próxima a todos os componentes para deixá-los **desabilitados** por padrão:

![Unity com o objeto RoverExplorer selecionado e os componentes adicionados e desabilitados](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> A visualização do Controle de Limites é criada no runtime e, portanto, não fica visível até que você entre no modo de Jogo.

> [!NOTE]
>O Object Manipulator (Script) adiciona automaticamente o Constraint Manager (Script)

Na janela Hierarquia, expanda o objeto Menu > **ButtonCollection** para revelar os quatro botões e renomeie o terceiro botão como **BoundsControl_Enable**. Em seguida, na janela Inspetor, configure o componente **Button Config Helper (Script)** da seguinte maneira:

* Altere o **Texto do Rótulo Principal** para **Habilitado**
* Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **BoundsControl** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **marcada**
* Clique no ícone pequeno **+** para adicionar outro evento
* Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **marcada**
* Deixe o **Ícone** como o ícone 'cubo com o controle de limites'

![Unity com o objeto de botão BoundsControl_Enable selecionado e o componente Button Config Helper configurado](images/mr-learning-base/base-07-section2-step1-2.png)

Renomeie o quarto e último botão como **BoundsControl_Disable** e, na janela Inspetor, configure o componente **Button Config Helper (Script)** da seguinte maneira:

* Altere o **Texto do Rótulo Principal** para **Desabilitado**
* Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **BoundsControl** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**
* Clique no ícone pequeno **+** para adicionar outro evento
* Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**
* Altere o **Ícone** para o ícone 'cubo com o controle de limites'

![Unity com o objeto de botão BoundsControl_Disable selecionado e o componente Button Config Helper configurado](images/mr-learning-base/base-07-section2-step1-3.png)

Se agora você entrar no modo de Jogo e habilitar o Controle de Limites clicando no botão Habilitar, poderá usar a interação próxima ou distante para mover, girar e escalar o Controle de Limites e usar o botão Desabilitar para desabilitar o Controle de Limites novamente:

![Modo de exibição dividida do Modo de Jogo do Unity com o Controle de Limites sendo manipulado](images/mr-learning-base/base-07-section2-step1-4.png)

Para saber mais sobre o componente de Controle de Limites e as propriedades associadas a ele, acesse o guia da [Controle de Limites](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como habilitar a manipulação próxima e distante de objetos 3D e como limitar os tipos de manipulação permitidos. Você também aprendeu a adicionar o Controle de Limites em objetos 3D para facilitar o controle da manipulação de objetos.

> [!div class="nextstepaction"]
> [Próximo tutorial: 8. Como usar o acompanhamento de olho](mr-learning-base-08.md)
