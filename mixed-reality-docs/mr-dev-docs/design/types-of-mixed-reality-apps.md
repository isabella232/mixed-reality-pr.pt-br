---
title: Tipos de aplicativos de realidade misturada
description: Saiba mais sobre as experiências com suporte da plataforma de Realidade Misturada, desde ambientes imersivos até camadas de informações leves sobre o ambiente de um usuário.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, padrões de aplicativo, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens
ms.openlocfilehash: 13d4f538148b2c6b6f4df422c6c423f2b2710ca1ba2d98fe4f952c14284035f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218908"
---
# <a name="types-of-mixed-reality-apps"></a>Tipos de aplicativos de realidade misturada

Uma das vantagens de desenvolver aplicativos para Windows Mixed Reality é o espectro de experiências que a plataforma pode dar suporte. Desde ambientes virtuais de imersão completa até disposição em camadas de informações leves sobre o ambiente atual de um usuário, o Windows Mixed Reality fornece um conjunto robusto de ferramentas para dar vida a qualquer experiência. É importante que um criador de aplicativos entenda, no início do processo de desenvolvimento, onde ao longo desse espectro sua experiência está. Essa decisão, em última análise, afetará o design do aplicativo e o caminho tecnológico para o desenvolvimento.

## <a name="enhanced-environment-apps-hololens-only"></a>Aplicativos de ambiente aprimorados (HoloLens somente)

Uma das maneiras mais poderosas pelas quais a realidade misturada pode agregar valor é permitir que os desenvolvedores coloquem informações digitais ou conteúdo no ambiente atual de um usuário. Essa abordagem é popular para aplicativos em que o posicionamento contextual do conteúdo digital no mundo real é fundamental e manter o ambiente real do usuário "presente" durante sua experiência é fundamental. Os usuários também podem se mover entre tarefas digitais do mundo real com facilidade. Isso dá ainda mais confiança à promessa de que os aplicativos de realidade misturada que o usuário vê realmente fazem parte de seu ambiente.

![Aplicativos de ambiente aprimorados](images/enhancedenvironmentapps-640px.jpg)<br>
*Aplicativos de ambiente aprimorados*

**Usos de exemplo**
* Um aplicativo de estilo de bloco de notas de realidade misturada que permite que os usuários criem e coloquem anotações em seu ambiente
* Um aplicativo de tv de realidade misturada colocado em um local confortável para exibição
* Um aplicativo de cozinha de realidade misturada colocado acima da ilha da cozinha para ajudar uma tarefa de preparo
* Um aplicativo de realidade misturada que dá aos usuários a sensação de "visão de raio x" (ou seja, um holograma colocado sobre e imita um objeto do mundo real, permitindo que o usuário veja "dentro dele" holográficomente)
* Anotações de realidade misturada colocadas em toda a fábrica para dar as informações necessárias do trabalho
* Descoberta de maneira de realidade misturada em um espaço de escritório
* Experiências de tabela de realidade misturada (ou seja, experiências de estilo de jogo de tabuleiro)
* Aplicativos de comunicação de realidade misturada, como Skype

## <a name="blended-environment-apps"></a>Aplicativos de ambiente blended

Considerando Windows Mixed Reality capacidade do usuário de reconhecer e mapear o ambiente do usuário, ele é capaz de criar uma camada digital que pode ser sobreposição no espaço do usuário. A camada fina respeita a forma e os limites do ambiente do usuário, mas o aplicativo pode optar por transformar determinados elementos mais adequados para aprofundar o usuário no aplicativo. Isso é chamado de aplicativo de ambiente mesclado. Ao contrário de um aplicativo de ambiente aprimorado, os aplicativos de ambiente mistos só podem se preocupar o suficiente com o ambiente para melhor usar sua mágica para incentivar o comportamento específico do usuário (como incentivar a movimentação ou a exploração) ou substituindo elementos por alterações (um contador de cozinha é marcado para mostrar um padrão de bloco diferente). Esse tipo de experiência pode até mesmo transformar um elemento em um objeto totalmente diferente, mas ainda manter as dimensões aproximadas do objeto como sua base (uma ilha da cozinha é transformada em um terreno para um jogo de crime).

![Aplicativos de ambiente blended](images/blendedenvironmentapps-640px.jpg)<br>
*Aplicativos de ambiente blended*

**Usos de exemplo**
* Um aplicativo de design de interiores de realidade misturada que pode pintar paredes, sobresspesadas ou pisos em cores e padrões diferentes
* Um aplicativo de realidade misturada que permite que um designer automotivo em camadas novas i iterações de design para uma atualização futura de carro sobre um carro existente
* Uma colcha é "coberta" e substituída por uma estande de frutas de realidade misturada no jogo dos filhos
* Uma mesa é "coberta" e substituída por uma realidade misturada em um jogo de crime
* Uma cerca suspensa é "coberta" e substituída por uma sinalização usando aproximadamente a mesma forma e dimensão
* Um aplicativo que permite que os usuários se afoguem em suas paredes reais ou imersivas do mundo, que revelam um mundo mágico

## <a name="immersive-environment-apps"></a>Aplicativos de ambiente imersivos

Os aplicativos de ambiente imersivos são centralizados em um ambiente que altera completamente o mundo do usuário e pode coloca-los em um tempo e espaço diferentes. Esses ambientes podem se sentir reais, criando experiências imersivas e empolgantes que são limitadas apenas pela criatividade do criador do aplicativo. Ao contrário dos aplicativos de ambiente mistos, uma vez Windows Mixed Reality identifica o espaço do usuário, um aplicativo de ambiente imersivo pode desconsiderar totalmente o ambiente atual do usuário e substituí-lo por um de seus próprios. Essas experiências também podem separar o tempo e o espaço, o que significa que um usuário pode andar pelas ruas de Rome em uma experiência imersiva, permanecendo relativamente ainda em seu espaço do mundo real. O contexto do ambiente do mundo real pode não ser importante para um aplicativo de ambiente imersivo.

![Aplicativos de ambiente imersivos](images/windows-mixed-reality-640px.jpg)<br>
*Aplicativos de ambiente imersivos*

**Usos de exemplo**
* Um aplicativo imersivo que permite que um usuário faça um tour por um espaço separado do próprio (ou seja, percorrendo um prédio, um prédio, um tour popular)
* Um aplicativo imersivo que orquestra um evento ou um cenário em torno do usuário (ou seja, uma guerra ou um desempenho)

## <a name="see-also"></a>Veja também

* [Visão geral do desenvolvimento](../develop/development.md)
* [Modelo de aplicativo](app-model.md)
* [Modos de exibição do aplicativo](app-views.md)
