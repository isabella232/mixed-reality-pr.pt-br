---
title: Perguntas frequentes sobre acompanhamento
description: Acompanhamento Windows Mixed Reality solução de problemas que vão além da nossa documentação de suporte ao consumidor padrão.
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Solução de Problemas, Erros, Ajuda, Suporte, Acompanhamento
ms.openlocfilehash: fe5462a53de7b196db37edbbf0e56199a17c4c99b54ea1e7d9edf72e0845c9e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199472"
---
# <a name="tracking-faqs"></a>Perguntas frequentes sobre acompanhamento

## <a name="my-headset-has-stopped-tracking"></a>Meu headset parou de rastrear

Certifique-se de que as luzes estão ligadas e se não há nada impedindo as câmeras de acompanhamento de dentro para fora na frente do headset. Se o acompanhamento for perdido, poderá levar alguns segundos para ser retomado. Reiniciar o Windows Mixed Reality portal está acompanhando não é reiniciado.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Posso dar uma olhada, mas não consigo traduzir (estou preso no 3DOF)

Isso significa que o sistema de acompanhamento não pode gerar pose ou o aplicativo parou de usar novos dados de pose para renderizar. Para corrigir o problema:

* Certifique-se de que a sala tenha luz suficiente.
* Certifique-se de que a sala tenha detalhes suficientes para acompanhar.
* Desconectar o dispositivo, Windows Mixed Reality e conectar o dispositivo novamente.
* Se a mensagem persistir, entre em contato com o [atendimento ao cliente](https://support.microsoft.com/)

## <a name="the-view-in-the-hmd-is-frozen"></a>A exibição no HMD está congelada

Isso geralmente significa que o aplicativo ou um componente de nível de sistema falhou. Tente:

1. Pressione o botão "página inicial" para sair do aplicativo.
2. Desconectar o dispositivo, fechar o MRP e conectar o dispositivo novamente.
3. Reinicie o computador.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>O mundo rapidamente se inclina e inclina ou invertida de cabeça para baixo antes de retornar ao normal

Isso pode ser causado por um aplicativo ou componente no nível do sistema atingindo um erro fatal ou uma falta temporária de memória ou recursos de CPU. Para verificar:

1. Abra Gerenciador de Tarefas e verifique se pelo menos 20% da CPU está livre, se há 400 MB de memória disponível e a E/S de disco deve estar abaixo de 80%.
2. Vá para **Visualizador de Eventos > Windows Logs > Aplicativo** para procurar erros de perto do momento do congelamento. Procure qualquer coisa que se refere HoloLens sensores, Realidade Misturada ou o aplicativo que você estava executando nesse momento. Esses logs podem explicar o que causou a falha.
3. Reinicie o COMPUTADOR se o problema persistir.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>O mundo invertia a cabeça para baixo momentaneamente e retornou ao normal

Normalmente, isso é causado por erros na obtenção de dados do sensor do headset para informar os algoritmos de rastreamento. Se isso acontecer com frequência:

1. Conecte o headset a uma porta USB 3.0 diferente.
2. Conecte o headset diretamente ao computador em vez de em um hub USB 3.0.
3. Se o problema persistir, entre em contato com o [atendimento ao cliente.](https://support.microsoft.com/)

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>O mundo está inclinado, mas posso navegar e percorrer Windows Mixed Reality

Se os erros de dados do sensor são registrados nos dados de ambiente em seu computador, isso pode fazer com que Windows Mixed Reality apareçam inclinadas, às vezes permanentemente. Para corrigir isso:

1. Desconectar o headset, fechar Windows Mixed Reality e conectar o headset novamente.
2. Reinicie o computador.
3. Limpe os dados do ambiente.