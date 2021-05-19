---
title: Observador de malha de objeto espacial
description: Documentação sobre o observador de malha espacial no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144451"
---
# <a name="configuring-mesh-observers-for-the-editor"></a>Configurando os observadores de malha para o editor

Uma maneira conveniente de fornecer dados de malha de ambiente no editor do Unity é usar a [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe. O *observador de malha de objeto espacial* é um provedor de dados somente editor para o [sistema de conscientização espacial](spatial-awareness-getting-started.md) que permite a importação de dados de modelo 3D para representar uma malha espacial. Um uso comum do *observador de malha de objetos espaciais* é importar dados verificados por meio de um Microsoft HoloLens para testar como uma experiência se adapta a diferentes ambientes no Unity.

## <a name="getting-started"></a>Introdução

Este guia explicará a configuração de um *observador de malha de objeto espacial*. Há três etapas principais para habilitar esse recurso.

1. Adicionar um *observador de malha de objeto espacial* ao perfil do sistema de conscientização espacial
1. Definir o objeto de dados de malha do ambiente
1. [Configurar o restante das propriedades do perfil de observador de malha](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>Configurar um perfil de *observador de malha de objeto espacial*

1. Selecione o perfil de configuração do *Kit de ferramentas de realidade misturada* desejado ou selecione o objeto de *Kit de ferramentas do reality*
1. Abrir ou expandir a guia *sistema de conscientização espacial*
1. Clique no botão *"Adicionar observador espacial"*

    ![Adicionar observador espacial](../images/spatial-awareness/AddObserver.png)

1. Selecione o tipo de *SpatialObjectMeshObserver*

    ![Selecionar observador de malha de objeto espacial](../images/spatial-awareness/SelectObjectObserver.png)

1. Selecione o *objeto de malha espacial* desejado. Por padrão, o observador é configurado com um modelo de exemplo. Esse modelo foi criado usando um Microsoft HoloLens, mas é possível [criar um novo objeto de malha de digitalização](#acquiring-environment-scans).
1. [Configurar o restante das propriedades do perfil Observador de Malha](configuring-spatial-awareness-mesh-observer.md)

    ![Selecionar o objeto de malha](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>Notas de perfil do observador da malha de objeto espacial

Como o *Observador* de Malha de Objeto Espacial carrega dados de um modelo 3D, ele não segue algumas das configurações de observador de malha padrão descritas abaixo.

**Intervalo de atualização**

O  *Observador de Malha de Objeto Espacial* envia todas as malhas para um aplicativo quando o modelo é carregado. Ele não simula deltas de tempo entre atualizações. Um aplicativo pode receber os eventos de malha chamando [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) e [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .

**É Observador Estacionário**

O *Observador de Malha de Objeto Espacial* considera todos os objetos de malha 3D como estacionários e desconsidera a origem.

**Forma e extensão do observador**

O  *Observador de Malha de Objeto Espacial* envia toda a malha 3D para o aplicativo. A forma e as extensão do observador não são consideradas.

**Nível de detalhes e triângulos/medidor cúbica**

O Observador não tenta encontrar LODs de modelo 3D ao enviar as malhas para o aplicativo.

## <a name="acquiring-environment-scans"></a>Adquirir verificações de ambiente

Esta seção descreve informações adicionais  para criar e coletar arquivos de Objeto de Malha Espacial para uso com o Observador de *Malha de Objeto Espacial*.

### <a name="windows-device-portal"></a>Portal de Dispositivos do Windows

O [Portal de Dispositivos do Windows](/windows/mixed-reality/using-the-windows-device-portal) pode ser usado para baixar a malha espacial, como um arquivo .obj, de um Microsoft HoloLens dispositivo.

1. Digitalizar simplesmente passeando e exibindo o ambiente desejado com um HoloLens
1. Conectar-se ao HoloLens usando o Portal de Dispositivos do Windows
1. Navegar até a página *exibição 3D*
1. Clique no botão *Atualizar* na seção *mapeamento espacial*
1. Clique no botão *salvar* na seção *mapeamento espacial* para salvar o arquivo obj no PC

> [!NOTE]
> **Arquivos HoloToolkit. Room**
>
> Muitos desenvolvedores já usaram o HoloToolkit para verificar ambientes e criar arquivos. Room. O kit de ferramentas de realidade misturada agora dá suporte à importação desses arquivos como GameObjects no Unity e usá-los como *objetos de malha espacial* no observador.

## <a name="see-also"></a>Confira também

- [Perfis](../profiles/profiles.md)
- [Guia de configuração do perfil do reality Toolkit misto](../../configuration/mixed-reality-configuration-guide.md)
- [Introdução ao reconhecimento espacial](spatial-awareness-getting-started.md)
- [Configurando observadores de malha no dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configurando os observadores de malha por meio do código](usage-guide.md)
- [Como usar o Portal de Dispositivos do Windows](/windows/mixed-reality/using-the-windows-device-portal)