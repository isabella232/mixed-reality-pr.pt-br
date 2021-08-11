---
title: Focar com o olhar e confirmar
description: Saiba mais sobre o modelo de entrada de focar com o olhar e confirmar.
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Acompanhamento do Olhar, Realidade Misturada, Entrada, Foco do Olhar, Direcionamento de Foco, HoloLens 2, Seleção baseada no Olhar, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, foco
ms.openlocfilehash: 12ffc24c39a9f8be329972516d42730dc98899d3ebba8359e9fea6ebbf6d02c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197820"
---
# <a name="eye-gaze-and-commit"></a>Focar com o olhar e confirmar

_Focar com o olhar e confirmar_ é um caso especial de modelo de entrada de [focar e confirmar](gaze-and-commit.md) que envolve escolher um objeto como alvo olhando para ele. Você pode executar uma ação no alvo com uma entrada secundária _confirmar_, como um gesto de mão, um comando de voz ou uma entrada de periférico, como um controlador de jogo. 

Com o HoloLens 2, temos a excelente oportunidade de tornar o recurso de _focar com o olhar e confirmar_ mais rápido e mais confortável usando o foco com o olhar em vez do foco com a cabeça. Para estender o modelo de interação comum de [focar com a cabeça e confirmar](gaze-and-commit.md): 
1. Olhe para um alvo 
2. Para confirmar sua intenção de selecionar o alvo, use uma entrada secundária explícita, como:  
   - Gesto de mão (por exemplo, fechar e abrir os dedos indicador e polegar)
   - Pressionamento de botão (por exemplo, em um teclado Bluetooth ou um clicador)
   - Comando de voz (por exemplo, "Selecionar")
   - Espera (ou seja, o usuário simplesmente continua olhando para o alvo para selecioná-lo)

No entanto, o foco com o olhar se comporta de maneira diferente em relação ao foco com a cabeça em algumas circunstâncias e traz muitos desafios únicos. 

Nas [Diretrizes de design de foco com o olhar](eye-tracking.md), resumimos as vantagens e os desafios gerais ao usar o acompanhamento ocular como uma entrada no seu aplicativo holográfico. Nesta seção, abordaremos considerações de design específicas de _focar com o olhar e confirmar_.
Primeiro, nossos olhos se movem incrivelmente rápido e são ótimos para focalizar algo rapidamente na visão. O foco com o olhar é ideal para ações rápidas de foco com o olhar e confirmação, especialmente quando combinadas com confirmações rápidas, como pressionar um botão ou fechar e abrir os dedos indicador e polegar.

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demonstração dos conceitos de design de rastreamento da cabeça e dos olhos

Se quiser ver os conceitos de design de rastreamento da cabeça e dos olhos em ação, confira abaixo nosso vídeo de demonstração do **Projetando hologramas - Rastreamento da cabeça e rastreamento dos olhos**. Depois de assistir ao vídeo, prossiga para saber mais sobre os tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*
   
## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Diretrizes de design para o foco com o olhar e confirmação

**Não mostrar um cursor**: embora seja quase impossível interagir sem um cursor ao usar o foco com a cabeça, o cursor passa rapidamente a ser uma distração e um incômodo durante o uso do foco com o olhar. Em vez de depender de um cursor para informar ao usuário que o acompanhamento ocular está funcionando e detectou corretamente o alvo que estava sendo observado no momento, use realces visuais sutis.

**Dê preferência para retornos de focalização sutis**: O que pode funcionar como um ótimo retorno visual para o foco com a cabeça pode resultar em uma experiência terrível e cansativa usando o foco com o olhar. Lembre-se de que seus olhos são extremamente rápidos, movendo-se rapidamente entre os pontos no seu campo de visão. Alterações de realce rápidas e repentinas (ativar/desativar) podem resultar em retornos oscilantes ao olhar ao redor. Portanto, ao fornecer o retorno de focalização, recomendamos usar um realce sutil de movimento de entrada (e de saída ao distanciar o olhar). Isso significa que, inicialmente, você mal notaria o retorno ao olhar para um alvo. No decorrer de 500 a 1000 ms, o realce aumentaria de intensidade. Enquanto os usuários novatos poderiam continuar olhando para o alvo para garantir que o sistema determinasse corretamente o alvo focalizado, os usuários experientes poderiam focar com o olhar e confirmar rapidamente, sem esperar o retorno atingir a intensidade máxima. Também recomendamos usar um movimento de saída ao esmaecer o retorno da focalização. As pesquisas mostram que alterações rápidas de movimento e contraste são perceptíveis na visão periférica (a área do campo de visão para a qual você não está olhando).
O esmaecimento não precisa ser tão lento quanto o movimento de entrada. Ele só é essencial quando você tiver alto contraste ou alterações de cor no realce. Se, inicialmente, o retorno de focalização for sutil, você provavelmente não perceberá nenhuma diferença.

**Esteja atento à sincronização dos sinais de foco e confirmação**: A sincronização dos sinais de entrada pode ser mais acessível para simples comandos de fechar e abrir dedos indicador e polegar e pressionamentos de botão. É algo que exige atenção caso você deseje usar ações de confirmação mais complexas que possam envolver comandos de voz longos ou gestos de mão complicados. Imagine que você olhe para um alvo e emita um comando de voz longo. Pense no tempo necessário para dizer isso e no tempo que o sistema precisou para detectar o que você disse: o foco do seu olhar já vai ter mudado para um novo alvo na cena. Informe os usuários de que eles precisam manter o olhar fixo no alvo até que o comando seja reconhecido ou processe a entrada de maneira a determinar o início do comando e o que o usuário estava olhando naquele momento.

## <a name="see-also"></a>Veja também

* [Interação ocular] (eye-gaze-interaction.md)
* [Acompanhamento ocular no HoloLens 2] (eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
