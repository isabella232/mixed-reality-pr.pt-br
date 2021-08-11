---
title: Práticas recomendadas gerais
description: Mantenha-se atualizado sobre todas as práticas recomendadas para o desenvolvimento de aplicativos de realidade misturada em um Unreal Engine.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, extensões do editor, editor do Unreal, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, documentação, guias, recursos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, portabilidade, atualização
ms.openlocfilehash: 822e64d873952bdb4bb1fb91da4c85f956a1eb513c92d4afee7bfebb18a824eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203258"
---
# <a name="general-best-practices"></a>Práticas recomendadas gerais

Veja a seguir algumas práticas recomendadas gerais que recomendamos que todos os desenvolvedores sigam ao criar um projeto do Unreal Engine para a Realidade Misturada.

## <a name="constructors"></a>Construtores

Se você precisar do equivalente de um "construtor" nos blueprints, use o [script de construção](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html) do Unreal. A principal vantagem de usar eventos "BeginPlay" é que o script de construtor também é executado no "editor". Na maioria das vezes, os valores podem ser armazenados em cache diretamente no início ou mesmo no tempo de compilação.

> [!NOTE]
> Você pode encontrar mais informações de suporte para scripts de Construção na [visão geral das extensões do editor](unreal-editor-extensions.md#construction-scripts).

## <a name="3d-buttons-and-textures"></a>Botões e texturas em 3D

É natural pensar no desempenho ao criar ou planejar o uso de botões em 3D em aplicativos de realidade misturada. No entanto, nem tudo precisa ser feito de malhas para ser percebido como 3D. Você tem a opção de usar o Paper2D com texturas cuidadosamente criadas para obter a aparência 3D. Isso funciona muito bem para botões que "parecem" 3D, mas são apenas imagens com Photoshop em um quadrupleto. Uma versão sofisticada deles é chamada de [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).

## <a name="variants"></a>Variantes

Use as [Variantes do Unreal](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) em cenários em que você está criando uma cena com várias configurações de objeto no runtime. As variações podem incluir a alteração de materiais ou malhas. 

## <a name="animation"></a>Animação

Aproveite o [Componente spline](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (não o componente de "malha" spline) e os [Nós da linha do tempo](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) se você estiver criando muitas "animações interativas". 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>Comunicações

Use um [Blueprint de Nível](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) se você estiver tendo problemas para localizar objetos dinamicamente ou estiver usando muita largura de banda para se comunicar entre vários atores e blueprints. Lembre-se de que o Unreal Engine 4 não é como o Unity, nem tudo precisa estar dentro de um componente. Blueprints de Nível são um modo perfeitamente válido e recomendado de simplificar a comunicação entre vários atores. As referências de objeto podem até mesmo ser armazenadas em cache na inicialização no OnBeginPlay do Blueprint de Nível.

## <a name="global-state"></a>Estado global

Geralmente, você precisará armazenar o estado específico de nível, como pontuação, dados de nível, informações específicas do player ou qualquer outra coisa que não pertença a um objeto específico. Não ignore o [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html). A maioria das pessoas esquece que ele existe, mas o GameMode pode ser criado por nível e conter dados específicos para cada nível.

## <a name="optimizing-blueprints"></a>Como otimizar blueprints

Se você achar que os seus blueprints estão muito lentos, deixe o Unreal torná-los "nativos" antes de precisar reescrever o código em c++. Tente usar a [nativização](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) automática antes de criar a própria solução personalizada.

![A configuração de blueprints com o método de nativização de blueprint com inclusive destacado](images/unreal-general-practices-img-01.jpg)
