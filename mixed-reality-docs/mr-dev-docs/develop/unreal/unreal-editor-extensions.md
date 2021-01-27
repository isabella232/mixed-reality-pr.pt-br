---
title: Extensões do editor no Unreal
description: Saiba como estender o editor do Unreal Engine com os scripts personalizados, as ações com script e os widgets de utilitário.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, extensões do editor, editor do Unreal, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, documentação, guias, recursos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, portabilidade, atualização
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584702"
---
# <a name="editor-extensions-in-unreal"></a>Extensões do editor no Unreal

O Unreal fornece um amplo conjunto de recursos que permitem que você personalize o mecanismo para as suas necessidades. Os recursos variam de simples, mas limitados, a muito potentes, mas complexos. As etapas a seguir são listadas em ordem crescente de complexidade. Em geral, você deve buscar soluções mais simples para o problema e esgotar as opções antes de passar para uma opção mais complexa. Por exemplo, descobrimos que o Script de Construção básico pode ser usado no lugar de plug-ins na maioria das vezes. 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>Scripts de construção

Você pode usar scripts de construção para executar ações de inicialização, que são executadas quando a instância do Blueprint é criada.

* [Script de Construções do usuário](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [Exemplo de blueprint](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [Tutorial em vídeo](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>Ações com script

As ações com script são blueprints do utilitário do editor. Você pode iniciá-las no Editor do Unreal ao:
* Clicar com o botão direito do mouse em **Ativos** no Navegador de Conteúdo
* Ou clicando com o botão direito do mouse em **Atores** no Visor de Nível ou no Contorno do Mundo

As Ações com Script são exclusivamente adequadas para momentos em que você precisa que a sua lógica de Blueprint tenha consciência contextual sobre conjuntos de Ativos ou Atores. Normalmente, uma Ação com Script obtém uma lista de Ativos ou Atores que você selecionou quando a ação foi executada e, em seguida, modifica esses objetos ou os considera no grafo.

* [Ações com script](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [Como executar ações com script na inicialização do projeto](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>Widgets do utilitário do editor

Você pode usar os [Widgets do Utilitário do Editor](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) sempre que desejar adicionar novos elementos da interface do usuário para modificar a IU (interface do usuário) do Editor do Unreal. Os Widgets do Utilitário do Editor são baseados em UMG (Unreal Motion Graphics), para que você possa configurar os Widgets em um Blueprint da mesma forma que faria em qualquer outro Blueprint de Widget do UMG.

Esses Widgets são especificamente para a Interface do Usuário do Editor e você pode usá-los para criar guias personalizadas do Editor. Você pode selecionar essas guias personalizadas no menu do Windows, como você selecionaria as guias do Editor existentes.

## <a name="plugins"></a>Plug-ins

O Unreal permite que você desenvolva e gerencie os próprios [plug-ins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) personalizados para uso com runtime e ferramentas do UE4. Você pode habilitar ou desabilitar os seus plug-ins a qualquer momento no Editor do Unreal. Os plug-ins podem adicionar funcionalidade de jogo de runtime, modificar recursos internos do Engine, criar tipos de arquivo e estender as funcionalidades do Editor.

<!-- ## Engine modifications -->

