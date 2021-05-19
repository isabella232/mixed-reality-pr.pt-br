---
title: Compreensão da cena
description: Descreve a compreensão da cena no MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, compreensão da cena
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143881"
---
# <a name="scene-understanding"></a>Compreensão da cena

O [entendimento da cena](/windows/mixed-reality/scene-understanding) retorna uma representação semântica das entidades de cena, bem como suas formas geométricas no __hololens 2__ (não há suporte para o hololens 1ª gen).

Alguns casos de uso esperados dessa tecnologia são:
* Coloque objetos na superfície mais próxima de um determinado tipo (por exemplo, parede e piso)
* Construir NAV-malha para jogos de estilo de plataforma
* Fornecer geometria amigável do mecanismo de física como quatro processadores
* Acelere o desenvolvimento, evitando a necessidade de escrever algoritmos semelhantes

A compreensão da cena está disponível como um recurso __experimental__ a partir do MRTK 2,6. Ele é integrado ao MRTK como um [observador espacial](spatial-awareness-getting-started.md#register-observers) chamado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . A compreensão da cena funciona tanto com o pipeline de XR herdado quanto com o pipeline do SDK do XR. Em ambos os casos, o `WindowsSceneUnderstandingObserver` é usado.

## <a name="observer-overview"></a>Visão geral do observador

Quando solicitado, o retornará [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) com atributos úteis para que o aplicativo entenda seu ambiente. A frequência de observação, o tipo de objeto retornado (por exemplo, parede, piso) e outros comportamentos de observador dependem da configuração do observador por meio do perfil. Por exemplo, se a máscara oclusão for desejada, o observador deverá ser configurado para gerar quatro processadores. A cena observada pode ser salva como um arquivo serializado que pode ser carregado posteriormente para recriar a cena no modo de reprodução do editor.

## <a name="setup"></a>Instalação

> [!IMPORTANT]
> Só há suporte para a compreensão da cena no HoloLens 2 e no Unity 2019,4 e superior.

1. Verifique se a plataforma está definida como UWP nas configurações de build.
1. Adquira o pacote de Compreensão de Cena por meio [da Ferramenta de Recursos de Realidade Misturada](https://aka.ms/MRFeatureTool).

## <a name="using-scene-understanding"></a>Usando a compreensão de cena

A maneira mais rápida de começar a entender a cena é conferir a cena de exemplo.

### <a name="scene-understanding-sample-scene"></a>Cena de exemplo de Compreensão de Cena

No Unity, use o Explorador de Projeto para abrir o arquivo de cena no `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e pressione Reproduzir!

> [!IMPORTANT]
> Ao usar a Ferramenta de Recursos de Realidade Misturada ou importar por meio de UPM, importe o exemplo Demonstrações – SpatialAwareness antes de importar o exemplo Experimental - SceneUnderstanding devido a um problema de dependência. Confira este [problema do GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obter mais informações.

A cena demonstra o seguinte:

* Visualização de objetos de cena observados com na interface do usuário do aplicativo para configurar o observador
* Script `DemoSceneUnderstandingController` de exemplo que mostra como alterar as configurações do observador e escutar eventos relevantes
* Salvando dados de cena no dispositivo para desenvolvimento offline
* Carregando dados de cena salvos anteriormente (arquivos .bytes) para dar suporte ao fluxo de trabalho de desenvolvimento no editor

> [!NOTE] 
> A cena de exemplo é baseada no pipeline XR herdado. Se você estiver usando o pipeline do SDK do XR, deverá modificar os perfis de acordo. O perfil do Sistema de Reconhecimento Espacial de Reconhecimento de Cena fornecido ( ) e os perfis de Observador de Reconhecimento de Cena ( e `DemoSceneUnderstandingSystemProfile` ) funcionam para ambos os `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` pipelines.

#### <a name="configuring-the-observer-service"></a>Configurando o serviço observador

Selecione o objeto de jogo 'MixedRealityToolkit' e verifique o inspetor.

![local de compreensão de cena na hierarquia](../images/spatial-awareness/MRTKHierarchy.png)

![Local do MRTK no inspetor](../images/spatial-awareness/MRTKLocation.png)

Essas opções permitirão que um configure o `WindowsSceneUnderstandingObserver` .

### <a name="example-script"></a>Script de exemplo

O script de exemplo _DemoSceneUnderstandingController. cs_ demonstra os principais conceitos do trabalho com o serviço de compreensão da cena.

* Inscrevendo-se nos eventos de compreensão da cena
* Lidando com eventos de compreensão da cena
* Configurando o `WindowsSceneUnderstandingObserver` em tempo de execução

As alternâncias no painel na cena alteram o comportamento do observador de compreensão da cena chamando funções públicas deste script de exemplo.

Ativar a *instanciação de pré-fabricados*, demonstrará a criação de objetos cujo tamanho se ajusta a todos os [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), coletados de forma organizada em um objeto pai.

![opções do controlador de demonstração](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Notas de aplicativo criadas

Crie e implante no HoloLens da maneira padrão. Uma vez em execução, vários botões devem aparecer para brincar com os recursos.

Observe que há algum pit que está fazendo consultas ao observador. A configuração incorreta de um resultado de solicitação de busca na carga do evento que não contém os dados esperados. Por exemplo, se um não solicitar quádruplos, nenhuma textura de máscara oclusão estará presente. Como inteligente, nenhuma malha do mundo será exibida se o observador não estiver configurado para solicitar malhas. O `DemoSceneUnderstandingController` script cuida de algumas dessas dependências, mas nem todas.

Os arquivos de cena salvos podem ser acessados por meio do [portal do dispositivo](/windows/mixed-reality/using-the-windows-device-portal) em `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Esses arquivos de cena podem ser usados no editor especificando-os no perfil observador encontrado no Inspetor.

![Local do portal do dispositivo-arquivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de cena serializados no observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Consulte Também

* [Visão geral do WMR do mapeamento espacial](/windows/mixed-reality/scene-understanding)
* [Visão geral do WMR do mapeamento espacial](/windows/mixed-reality/scene-understanding-sdk)