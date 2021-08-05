---
title: Estrutura e runtime
description: Informações relacionadas à estrutura e ao tempo de execução no MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f2391ab0c67880c8902092be6fcecefcf30f008c7f31ea76879d399e35e1491b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212667"
---
# <a name="framework-and-runtime"></a>Estrutura e runtime

## <a name="changes-to-the-scene"></a>Alterações na cena

Para usar o kit de ferramentas, uma instância do script MixedRealityToolkit deve estar em sua cena.
para adicionar um use a opção de menu: Mixed reality Toolkit-> adicionar à cena e configurar. Essa instância é responsável por registrar, atualizar e dividir os serviços. Também é onde seu perfil de configuração é escolhido.

Além de adicionar o MRTK gameobject à cena, a opção de menu também será:

- Adicione o MixedRealityPlayspace, que é usado por muitos outros componentes do MRTK por motivos sobre transformações mundiais e de espaço local.
- Mova a câmera principal como um filho do MixedRealityPlayspace (e também adicione alguns scripts relacionados a entrada e olhar à câmera principal, que ajuda o Power UnityUI e olhar funcionalidade de entrada relacionada).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>Objeto MixedRealityToolkit e tempo de execução

O MRTK tem vários serviços principais. Algumas coordenadas entre si; outras são independentes.
Todos compartilham o mesmo ciclo de vida – inicialização, registro, atualização e desmontagem – e esse ciclo de vida está além do ciclo de vida do monocomportamento do Unity. Esta [postagem média](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explica alguns dos planos de fundo e a motivação por trás dessa abordagem. O MRTK tem um único objeto que gerencia a vida e o tempo de execução de seus serviços.

Essa entidade garante que:

- Quando o jogo é iniciado, a descoberta e a inicialização de serviços acontecem em uma ordem predefinida.
- Ele fornece um mecanismo para que os serviços se registrem (ou seja, "Eu tenho suporte a este serviço!") e para outros chamadores para obter uma suspensão desses serviços.
- Ele fornece as chamadas Update ()/LateUpdate () e as encaminha para os vários serviços (por exemplo, por meio de UpdateAllServices/LateUpdateAllServices).
