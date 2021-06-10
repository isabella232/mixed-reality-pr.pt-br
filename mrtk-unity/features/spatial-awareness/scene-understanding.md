---
title: Noções básicas sobre a cena
description: descreve a compreensão de cena no MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Compreensão de cena
ms.openlocfilehash: 1ed6f93216fc90e7c6332f2b9c40911d25d96d2a
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743548"
---
# <a name="scene-understanding"></a>Noções básicas sobre a cena

[O Entendimento de](/windows/mixed-reality/scene-understanding) Cena retorna uma representação semântica de entidades de cena, bem como suas formas __geométricas no HoloLens 2__ (não há suporte para o HoloLens 1st Gen).

Alguns casos de uso esperados dessa tecnologia são:
* Colocar objetos na superfície mais próxima de um determinado tipo (por exemplo, parede e piso)
* Construir nav-mesh para jogos de estilo de plataforma
* Fornecer geometria amigável do mecanismo de física como quads
* Acelerar o desenvolvimento evitando a necessidade de escrever algoritmos semelhantes

O Entendimento de Cena é introduzido __como um recurso experimental__ no MRTK 2.6. Ele é integrado ao MRTK como um [observador espacial](spatial-awareness-getting-started.md#register-observers) chamado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . O Entendimento de Cena funciona com o pipeline XR herdado e o pipeline do SDK do XR (tanto o OpenXR (a partir do MRTK 2.7) quanto o Plug-in do Windows XR. Em ambos os `WindowsSceneUnderstandingObserver` casos, o é usado.

> [!NOTE] 
> Não há suporte para o uso da Compreensão de Cena em Remoting.

## <a name="observer-overview"></a>Visão geral do observador

Quando solicitado, o [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) retornará [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) com atributos úteis para o aplicativo entender seu ambiente. A frequência de observação, o tipo de objeto retornado (por exemplo, parede, piso) e outros comportamentos de observador dependem da configuração do observador por meio do perfil. Por exemplo, se a máscara de oclusão for desejada, o observador deverá ser configurado para gerar quads. A cena observada pode ser salva como um arquivo serializado que pode ser carregado posteriormente para recriar a cena no modo de reprodução do editor.

## <a name="setup"></a>Instalação

> [!IMPORTANT]
> O Entendimento de Cena só tem suporte no HoloLens 2 e no Unity 2019.4 e superior.

1. Verifique se a plataforma está definida como UWP nas configurações de build.
1. Adquira o pacote de Compreensão de Cena por meio [da Ferramenta de Recursos de Realidade Misturada](https://aka.ms/MRFeatureTool).

## <a name="using-scene-understanding"></a>Usando a compreensão de cena

A maneira mais rápida de começar a entender a cena é conferir a cena de exemplo.

### <a name="scene-understanding-sample-scene"></a>Cena de exemplo de Compreensão de Cena

No Unity, use o Explorador de Projeto para abrir o arquivo de cena no `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e pressione Reproduzir!

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> Aplica-se somente ao MRTK 2.6.0 – ao usar a Ferramenta de Recursos de Realidade Misturada ou importar por meio de UPM, importe o exemplo Demonstrações – SpatialAwareness antes de importar a amostra Experimental - SceneUnderstanding devido a um problema de dependência. Confira este [problema do GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obter mais informações.

::: moniker-end
A cena demonstra o seguinte:

* Visualização de objetos de cena observados com na interface do usuário do aplicativo para configurar o observador
* Script `DemoSceneUnderstandingController` de exemplo que mostra como alterar as configurações do observador e escutar eventos relevantes
* Salvando dados de cena no dispositivo para desenvolvimento offline
* Carregando dados de cena salvos anteriormente (arquivos .bytes) para dar suporte ao fluxo de trabalho de desenvolvimento no editor

> [!IMPORTANT]
> Por padrão, `ShouldLoadFromFile` a propriedade do observador é definida como false. Para ver a visualização de uma sala de exemplo serializada, consulte a seção configurando o serviço [observador](#configuring-the-observer-service) abaixo e de definir a propriedade como true no editor.
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> A cena de exemplo é baseada no pipeline XR herdado. Se você estiver usando o pipeline do SDK do XR, deverá modificar os perfis de acordo. O perfil do Sistema de Reconhecimento Espacial de Reconhecimento de Cena fornecido ( ) e os perfis de Observador de Reconhecimento de Cena ( e `DemoSceneUnderstandingSystemProfile` ) funcionam para ambos os `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` pipelines.
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> A cena de exemplo registra um `There is no active AsyncCoroutineRunner when an action is posted.` aviso sob determinada circunstância devido à ordem de inicialização/execução do thread. Se você puder confirmar que o componente está anexado ao GameObject "Controlador de Demonstração" e o `AsyncCoroutineRunner` componente/GameObject permanecer habilitado/ativo na cena (o caso padrão), o aviso poderá ser ignorado com segurança.
::: moniker-end

#### <a name="configuring-the-observer-service"></a>Configurando o serviço observador

Selecione o objeto de jogo 'MixedRealityToolkit' e verifique o inspetor.

![local de compreensão de cena na hierarquia](../images/spatial-awareness/MRTKHierarchy.png)

![Local do MRTK no inspetor](../images/spatial-awareness/MRTKLocation.png)

Essas opções permitirão que um configure o `WindowsSceneUnderstandingObserver` .

### <a name="example-script"></a>Script de exemplo

O script de _exemplo DemoSceneUnderstandingController.cs_ demonstra os principais conceitos em trabalhar com o serviço de Compreensão de Cena.

* Assinando eventos de Compreensão de Cena
* Manipulando eventos de Compreensão de Cena
* Configurando o `WindowsSceneUnderstandingObserver` em runtime

As alternâncias no painel na cena alteram o comportamento do observador de compreensão da cena chamando funções públicas deste script de exemplo.

A *acionamento de Pré-fabs* de Instanência demonstrará a criação de objetos desse tamanho para se ajustarem a todos [os SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), coletados perfeitamente em um objeto pai.

![opções do controlador de demonstração](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Notas de aplicativo criadas

Crie e implante no HoloLens da maneira padrão. Uma vez em execução, vários botões devem parecer reproduzir com os recursos.

Observe que há algumas quedas na busca de consultas para o observador. A configuração inefigurada de uma solicitação de busca resulta na falta de conteúdo do evento que contém os dados esperados. Por exemplo, se um não solicitar quads, nenhuma textura de máscara de oclusão estará presente. Da mesma forma, nenhuma malha mundial será exibida se o observador não estiver configurado para solicitar malhas. O `DemoSceneUnderstandingController` script cuida de algumas dessas dependências, mas não de todas.

Os arquivos de cena salvos podem ser acessados por meio do [portal do dispositivo](/windows/mixed-reality/using-the-windows-device-portal) em `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Esses arquivos de cena podem ser usados no editor especificando-os no perfil de observador encontrado no inspetor.

![Portal de Dispositivos local do arquivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de cena serializados no observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Consulte Também

* [Visão geral do Entendimento de Cena](/windows/mixed-reality/scene-understanding)
* [Visão geral do SDK de Compreensão de Cena](/windows/mixed-reality/scene-understanding-sdk)