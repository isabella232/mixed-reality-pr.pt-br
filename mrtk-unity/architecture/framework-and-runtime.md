---
title: Estrutura e runtime
description: Informações relacionadas à estrutura e ao runtime no MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121603"
---
# <a name="framework-and-runtime"></a>Estrutura e runtime

## <a name="changes-to-the-scene"></a>Alterações na cena

Para usar o kit de ferramentas, uma instância do script MixedRealityToolkit deve estar em sua cena.
Para adicionar um, use a opção de menu: Kit de Ferramentas de Realidade Misturada -> Adicionar à Cena e Configurar. Essa instância é responsável por registrar, atualizar e destruir serviços. Também é onde seu perfil de configuração é escolhido.

Além de adicionar o GameObject do MRTK à cena, a opção de menu também:

- Adicione o MixedRealityPlayspace, que é usado por muitos outros componentes do MRTK para levar em conta as transformações de espaço local e do mundo.
- Mova a câmera principal como um filho do MixedRealityPlayspace (e também adicione alguns scripts relacionados à entrada e foco à câmera principal, o que ajuda a apricar o UnityUI e a funcionalidade de entrada relacionada ao foco).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>Runtime e objeto MixedRealityToolkit

O MRTK tem vários serviços principais. Algumas coordenadas entre si; outros são independentes.
Todos compartilham o mesmo ciclo de vida – inicialização, registro, atualização e rebaixamento – e esse ciclo de vida se diferencia do ciclo de vida monoBehaviour do Unity. Esta [postagem média](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explica algumas das informações e da motivação por trás dessa abordagem. O MRTK tem um único objeto que gerencia a vida e o runtime de seus serviços.

Essa entidade garante que:

- quando o jogo é iniciado, a descoberta e a inicialização de serviços ocorrem em uma ordem pré-definida.
- ele fornece um mecanismo para que os serviços se registrem (ou seja, "Eu dá suporte a esse serviço!") e para outros chamadores obterem uma conta desses serviços.
- ele fornece as chamadas Update()/LateUpdate() e as encaminha para os vários serviços (ou seja, por meio de UpdateAllServices/LateUpdateAllServices).
