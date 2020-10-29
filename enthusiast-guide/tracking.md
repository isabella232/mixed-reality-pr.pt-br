---
title: Acompanhamento de perguntas frequentes
description: Solução de problemas avançada do Windows Mixed realm que vai além da nossa documentação de suporte padrão do consumidor.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, solução de problemas, erros, ajuda, suporte, rastreamento
ms.openlocfilehash: b29df6f17bed52d3115faede10cdce91a7ea637f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675495"
---
# <a name="tracking-faqs"></a>Acompanhamento de perguntas frequentes

## <a name="my-headset-has-stopped-tracking"></a>Meu Headset parou o acompanhamento.

Verifique se as luzes estão acesas e se não há nada obstruindo as câmeras de rastreamento internas na frente do headset. Se o rastreamento for perdido, pode levar alguns segundos para retomar. Se não for retomada, reinicie o portal do Windows Mixed Reality. 

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Posso examinar, mas não posso traduzir (estou preso por 3DOF).

Isso significa que o sistema de controle não pode gerar pose ou o aplicativo foi interrompido usando novos dados de pose a serem renderizados. Verifique o seguinte:
* Verifique se a sala tem luz suficiente.
* Verifique se a sala tem detalhes suficientes para acompanhar.
* Desconecte o dispositivo, feche a realidade mista do Windows e conecte o dispositivo novamente.
* Se a mensagem persistir, contate o atendimento [ao cliente](https://support.microsoft.com/)

## <a name="the-view-in-the-hmd-is-completely-frozen"></a>A exibição no HMD é completamente congelada.

Isso geralmente significa que o aplicativo ou um componente de nível de sistema falhou. Tente:
1. Pressione o botão "página inicial" para sair do aplicativo.
2. Desconecte o dispositivo, feche o MRP e conecte o dispositivo novamente.
3. Reinicie o computador.

## <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-down-before-returning-to-normal"></a>O mundo brevemente froze e talvez inclinado ou invertido de cabeça para baixo antes de retornar ao normal.

Isso pode ser causado por um aplicativo ou componente no nível do sistema que está atingindo um erro fatal ou uma falta temporária de memória ou recursos de CPU. Para verificar:
1. Abra o Gerenciador de tarefas e verifique se pelo menos 20% da CPU está livre, se 400 MB de memória está disponível e e/s de disco devem estar abaixo de 80%.
2. Vá para **Visualizador de Eventos > logs do Windows > aplicativo** para procurar quaisquer erros em vez da hora do congelamento. Procure qualquer coisa que se refira a sensores do HoloLens, realidade misturada ou o aplicativo que você estava executando em todo esse tempo. Esses logs podem explicar o que causou a falha.
3. Reinicie o PC se o problema persistir.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>O mundo se inverteu de cabeça momentaneamente e retornou ao normal.

Isso geralmente é causado por erros na obtenção de dados de sensor do headset para informar os algoritmos de controle. Se isso ocorrer com frequência:
1. Conecte o headset em uma porta USB 3,0 diferente.
2. Conecte o headset diretamente no PC, em vez de em um hub USB 3,0.
3. Se o problema persistir, entre em contato com o atendimento [ao cliente](https://support.microsoft.com/).

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>O mundo está inclinado, mas eu posso navegar e percorrer na realidade mista do Windows.

Se os erros de dados do sensor forem registrados nos dados do ambiente em seu computador, isso poderá fazer com que a realidade mista do Windows pareça inclinada, às vezes permanentemente. Para corrigir isso:
1. Desconecte o headset, feche a realidade mista do Windows e conecte o headset novamente.
2. Reinicie o computador.
3. Apague os dados do seu ambiente.

