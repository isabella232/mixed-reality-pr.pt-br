---
title: Observador da malha de objeto espacial
description: Documentação sobre o observador de malha espacial no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f28f8dcb320332b8ff8942ae0b442c0817d6d0b790347daa419cfc24dc0d60fc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209106"
---
# <a name="spatial-object-mesh-observer"></a>Observador da malha de objeto espacial

Uma maneira conveniente de fornecer dados de malha de ambiente no editor do Unity é usar a [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe. O *observador de malha de objeto espacial* é um provedor de dados somente editor para o [sistema de conscientização espacial](spatial-awareness-getting-started.md) que permite a importação de dados de modelo 3D para representar uma malha espacial. um uso comum do *observador de malha de objetos espaciais* é importar dados verificados por meio de um Microsoft HoloLens para testar como uma experiência se adapta a diferentes ambientes de dentro do Unity.

## <a name="getting-started"></a>Introdução

Este guia explicará a configuração de um *observador de malha de objeto espacial*. Há três etapas principais para habilitar esse recurso.

1. Adicionar um *observador de malha de objeto espacial* ao perfil do sistema de conscientização espacial
1. Definir o objeto de dados de malha do ambiente
1. [Configurar o restante das propriedades do perfil de observador de malha](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>Configurar um perfil de *observador de malha de objeto espacial*

1. selecione o perfil de configuração *Toolkit realidade misturada* desejada ou selecione o objeto de *Toolkit realidade misturada* em cena
1. Abrir ou expandir a guia *sistema de conscientização espacial*
1. Clique no botão *"Adicionar observador espacial"*

    ![Adicionar observador espacial](../images/spatial-awareness/AddObserver.png)

1. Selecione o tipo de *SpatialObjectMeshObserver*

    ![Selecionar observador de malha de objeto espacial](../images/spatial-awareness/SelectObjectObserver.png)

1. Selecione o *objeto de malha espacial* desejado. Por padrão, o observador é configurado com um modelo de exemplo. esse modelo foi criado usando um Microsoft HoloLens, mas é possível [criar um novo objeto de malha de digitalização](#acquiring-environment-scans).
1. [Configurar o restante das propriedades do perfil de observador de malha](configuring-spatial-awareness-mesh-observer.md)

    ![Selecionar o objeto de malha](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>Notas de perfil do observador de malha de objetos espaciais

Como o *observador de malha de objeto espacial* carrega dados de um modelo 3D, ele não respeita algumas das configurações de observador de malha padrão que são descritas abaixo.

**Intervalo de atualização**

O  *observador de malha de objeto espacial* envia todas as malhas para um aplicativo quando o modelo é carregado. Ele não simula os deltas de tempo entre as atualizações. Um aplicativo pode receber novamente os eventos de malha chamando [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) e [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .

**É observador estacionário**

O *observador de malha de objetos espaciais* considera que todos os objetos de malha 3D sejam estáticos e desconsideram a origem.

**Formas e extensões do observador**

O  *observador de malha de objeto espacial* envia a malha 3D inteira para o aplicativo. A forma e as extensões do observador não são consideradas.

**Nível de detalhe e triângulos/medidor cúbico**

O observador não tenta localizar o modelo 3D LODs ao enviar as malhas para o aplicativo.

## <a name="acquiring-environment-scans"></a>Adquirindo verificações de ambiente

Esta seção descreve informações adicionais para criar e coletar arquivos de *objeto de malha espacial* para uso com o *observador de malha de objeto espacial*.

### <a name="windows-device-portal"></a>Portal de Dispositivos do Windows

o [Portal do dispositivo Windows](/windows/mixed-reality/using-the-windows-device-portal) pode ser usado para baixar a malha espacial, como um arquivo. obj, de um dispositivo Microsoft HoloLens.

1. Examine simplesmente movimentando e exibindo o ambiente desejado com um HoloLens
1. Conexão ao HoloLens usando o Portal do dispositivo Windows
1. Navegar até a página *exibição 3D*
1. Clique no botão *Atualizar* na seção *mapeamento espacial*
1. Clique no botão *salvar* na seção *mapeamento espacial* para salvar o arquivo obj no PC

> [!NOTE]
> **Arquivos HoloToolkit. Room**
>
> Muitos desenvolvedores já usaram o HoloToolkit para verificar ambientes e criar arquivos. Room. a realidade misturada Toolkit agora dá suporte à importação desses arquivos como GameObjects no Unity e usá-los como *objetos de malha espacial* no observador.

## <a name="see-also"></a>Confira também

- [Perfis](../profiles/profiles.md)
- [guia de configuração do perfil da realidade mista Toolkit](../../configuration/mixed-reality-configuration-guide.md)
- [Introdução ao reconhecimento espacial](spatial-awareness-getting-started.md)
- [Configurando observadores de malha no dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configurando os observadores de malha por meio do código](usage-guide.md)
- [Como usar o Portal de Dispositivos do Windows](/windows/mixed-reality/using-the-windows-device-portal)
