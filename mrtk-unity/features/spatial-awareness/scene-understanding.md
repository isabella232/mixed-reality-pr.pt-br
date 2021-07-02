---
title: Observador de compreensão da cena
description: Descreve a compreensão da cena no MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, compreensão da cena
ms.openlocfilehash: d5430e7885055a550347c4ccebc1452f68125922
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176228"
---
# <a name="scene-understanding-observer"></a>Observador de compreensão da cena

o [entendimento da cena](/windows/mixed-reality/scene-understanding) retorna uma representação semântica das entidades de cena, bem como suas formas geométricas no __HoloLens 2__ (HoloLens 1ª Gen não tem suporte).

Alguns casos de uso esperados dessa tecnologia são:
* Coloque objetos na superfície mais próxima de um determinado tipo (por exemplo, parede e piso)
* Construir NAV-malha para jogos de estilo de plataforma
* Fornecer geometria amigável do mecanismo de física como quatro processadores
* Acelere o desenvolvimento, evitando a necessidade de escrever algoritmos semelhantes

A compreensão da cena é introduzida como um recurso __experimental__ no MRTK 2,6. Ele é integrado ao MRTK como um [observador espacial](spatial-awareness-getting-started.md#register-observers) chamado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . a compreensão da cena funciona tanto com o pipeline do xr herdado quanto com o pipeline do SDK do xr (OpenXR (a partir do MRTK 2,7) e o plug-in Windows xr). Em ambos os casos, o `WindowsSceneUnderstandingObserver` é usado.

> [!NOTE] 
> Não há suporte para o uso da compreensão da cena em comunicação remota.

## <a name="observer-overview"></a>Visão geral do observador

Quando solicitado, o retornará [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) com atributos úteis para que o aplicativo entenda seu ambiente. A frequência de observação, o tipo de objeto retornado (por exemplo, parede, piso) e outros comportamentos de observador dependem da configuração do observador por meio do perfil. Por exemplo, se a máscara oclusão for desejada, o observador deverá ser configurado para gerar quatro processadores. A cena observada pode ser salva como um arquivo serializado que pode ser carregado posteriormente para recriar a cena no modo de reprodução do editor.

## <a name="setup"></a>Instalação

> [!IMPORTANT]
> só há suporte para a compreensão da cena no HoloLens 2 e no Unity 2019,4 e superior.

1. Verifique se a plataforma está definida para UWP nas configurações de compilação.
1. Adquira o pacote de compreensão da cena por meio da [ferramenta de funcionalidade de realidade misturada](https://aka.ms/MRFeatureTool).

## <a name="using-scene-understanding"></a>Usando a compreensão da cena

A maneira mais rápida de começar a entender a cena é conferir a cena de exemplo.

### <a name="scene-understanding-sample-scene"></a>Exemplo de cena de compreensão da cena

no Unity, use o Project Explorer para abrir o arquivo de cena no `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e pressione reproduzir!

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> Aplica-se somente a MRTK 2.6.0-ao usar a ferramenta de funcionalidade Mixed Reality ou, de outra forma, importar por meio de UPM, importe o exemplo de demonstrações-SpatialAwareness antes de importar o exemplo experimental-SceneUnderstanding devido a um problema de dependência. consulte [este GitHub problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obter mais informações.

::: moniker-end
A cena demonstra o seguinte:

* Visualização de objetos de cena observados com o na interface do usuário do aplicativo para configurar o observador
* Exemplo de `DemoSceneUnderstandingController` script que mostra como alterar as configurações de observador e ouvir eventos relevantes
* Salvando dados de cena no dispositivo para desenvolvimento offline
* Carregando dados de cena salvos anteriormente (arquivos. bytes) para dar suporte ao fluxo de trabalho de desenvolvimento no editor

> [!IMPORTANT]
> Por padrão, a `ShouldLoadFromFile` Propriedade do observador é definida como false. Para ver a visualização de uma sala de amostra serializada, consulte a seção [Configurando o serviço observador](#configuring-the-observer-service) abaixo e defina a propriedade como true no editor.
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> A cena de exemplo se baseia no pipeline de XR herdado. Se você estiver usando o pipeline do SDK do XR, deverá modificar os perfis de acordo. A cena fornecida compreendendo o perfil do sistema de conscientização espacial ( `DemoSceneUnderstandingSystemProfile` ) e a cena que entende os perfis de observadores ( `DefaultSceneUnderstandingObserverProfile` e `DemoSceneUnderstandingObserverProfile` ) funciona para ambos os pipelines.
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> A cena de exemplo registra um `There is no active AsyncCoroutineRunner when an action is posted.` aviso em determinadas circunstâncias devido à ordem de execução do thread/inicialização. Se você puder confirmar se o `AsyncCoroutineRunner` componente está anexado ao gameobject "controlador de demonstração" e o componente/gameobject permanecer habilitado/ativo na cena (o caso padrão), o aviso poderá ser ignorado com segurança. **No entanto, ao criar uma nova cena com a compreensão da cena, certifique-se de criar um gameobject vazio na raiz e anexar o `AsyncCoroutineRunner` script a ele, caso contrário, a compreensão da cena pode não funcionar corretamente.**
::: moniker-end

#### <a name="configuring-the-observer-service"></a>Configurando o serviço observador

Selecione o objeto de jogo ' MixedRealityToolkit ' e verifique o Inspetor.

![local de compreensão da cena na hierarquia](../images/spatial-awareness/MRTKHierarchy.png)

![Local do MRTK no Inspetor](../images/spatial-awareness/MRTKLocation.png)

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

crie e implante o HoloLens da maneira padrão. Uma vez em execução, vários botões devem aparecer para brincar com os recursos.

Observe que há algum pit que está fazendo consultas ao observador. A configuração incorreta de um resultado de solicitação de busca na carga do evento que não contém os dados esperados. Por exemplo, se um não solicitar quádruplos, nenhuma textura de máscara oclusão estará presente. Como inteligente, nenhuma malha do mundo será exibida se o observador não estiver configurado para solicitar malhas. O `DemoSceneUnderstandingController` script cuida de algumas dessas dependências, mas nem todas.

Os arquivos de cena salvos podem ser acessados por meio do [portal do dispositivo](/windows/mixed-reality/using-the-windows-device-portal) em `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Esses arquivos de cena podem ser usados no editor especificando-os no perfil observador encontrado no Inspetor.

![Local do portal do dispositivo-arquivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de cena serializados no observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Consulte Também

* [Visão geral de compreensão da cena](/windows/mixed-reality/scene-understanding)
* [Visão geral do SDK de compreensão da cena](/windows/mixed-reality/scene-understanding-sdk)
