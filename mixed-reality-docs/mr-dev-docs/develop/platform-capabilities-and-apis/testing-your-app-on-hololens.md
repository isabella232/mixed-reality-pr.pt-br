---
title: Como testar seu aplicativo no HoloLens
description: Saiba mais sobre diretrizes gerais e sugestões para teste e otimização de desempenho em seus HoloLens de realidade misturada.
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, teste
ms.openlocfilehash: 2f423560191fea8b516db80d533898b5a1f15973442e7bb6cd8878d486e0ffba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212084"
---
# <a name="testing-your-app-on-hololens"></a>Como testar seu aplicativo no HoloLens

Testar HoloLens aplicativos é semelhante ao teste Windows aplicativos. Você ainda precisa considerar a funcionalidade, a interoperabilidade, o desempenho, a segurança, a confiabilidade e assim por diante. No entanto, algumas áreas que não são pop-up em aplicativos de computador ou telefone exigem tratamento especial. Os aplicativos holográficos precisam ser executados sem problemas em um conjunto diversificado de ambientes. Eles também precisam manter o desempenho e o conforto do usuário o tempo todo. Este guia está aqui para ajudá-lo a testar essas áreas.

## <a name="performance"></a>Desempenho

Os aplicativos holográficos precisam ser executados sem problemas em um conjunto diversificado de ambientes. Eles também precisam manter o desempenho e o conforto do usuário o tempo todo. O desempenho é tão importante para a experiência do usuário com um aplicativo Holographic que temos um tópico inteiro dedicado a ele. Certifique-se de ler e seguir [Noções básicas sobre o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Testando 3D em 3D

1. **Teste seu aplicativo no máximo de espaços diferentes possível.** Experimente em salas grandes, salas pequenas, quartos, cozinhas, quartos, escritórios e assim por diante. Leve em consideração também salas com recursos não padrão, como paredes não verticais, paredes curvadas, limites não horizontais. Ele funciona bem ao fazer a transição entre salas, pisos, passando por quartos ou quartos?
2. **Teste seu aplicativo em condições de iluminação diferentes.** Ele responde corretamente a diferentes condições ambientais, como iluminação, superfícies pretas e superfícies transparentes ou reflexivas, como espelhos e paredes de vidro.
3. **Teste seu aplicativo em condições de movimento diferentes.** Coloque o dispositivo e experimente seus cenários em vários estados de movimento. Ele responde corretamente a um movimento diferente ou estado estável?
4. **Teste como seu aplicativo funciona de ângulos diferentes.** Se você tiver um holograma mundo bloqueado, o que acontecerá se o usuário o orienta? O que acontecerá se algo ocorrer entre o usuário e o holograma? E se o usuário olhar para o holograma acima ou abaixo?
5. **Use sinais espaciais e de áudio.** Certifique-se de que seu aplicativo use dicas espaciais e de áudio para impedir que o usuário seja perdido.
6. **Teste seu aplicativo em diferentes níveis de ruído de ambiente.** Se você implementou comandos de voz, tente invocá-los com níveis variados de ruído de ambiente.
7. **Teste seu aplicativo em posição e em posição.** Certifique-se de testar nas posições de estacionamento e de posição.
8. **Teste seu aplicativo de distâncias diferentes.** Os elementos da interface do usuário podem ser lidos e interagidos de longe? Seu aplicativo reage aos usuários se aproximarem demais dos hologramas?
9. **Teste seu aplicativo em relação a interações comuns da barra de aplicativos**. Todos os blocos de aplicativo e aplicativos universais 2D têm uma barra de aplicativos que permite controlar [a](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) posição dos aplicativos no Mundo Misto. Certifique-se de que clicar em Remover encerra o processo do aplicativo normalmente e se o botão Voltar tem suporte no contexto do seu aplicativo universal 2D. Tente dimensionar e mover seu aplicativo no modo [Ajustar](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) enquanto ele estiver ativo e enquanto ele é um peças de aplicativo suspenso.

### <a name="environmental-test-matrix"></a>Matriz de teste ambiental

![Matriz de Teste de Ambiente para HoloLens desenvolvimento de aplicativos](images/environment-matrix-600px.png)

## <a name="comfort"></a>Conforto

1. **Planos de clipe.** Esteja atento ao local em [que os hologramas são renderizados.](hologram-stability.md#hologram-render-distances)
2. **Evite o movimento virtual inconsistente com o movimento de cabeça real.** Evite mover a câmera de uma maneira que não seja representativa do movimento real do usuário. Se seu aplicativo exigir a movimentação do usuário por uma cena, faça com que o movimento seja previsível, minimize a aceleração e deixe o usuário controlar o movimento.
3. **Siga as diretrizes de qualidade do holograma.** Os aplicativos de alto desempenho que implementam [as diretrizes](hologram-stability.md) de qualidade do holograma têm menos probabilidade de resultar em um engano do usuário.
4. **Distribua hologramas horizontalmente em vez de verticalmente.** Forçar o usuário a passar longos períodos de tempo olhando para cima ou para baixo pode levar a uma queda de cabeça.

## <a name="input"></a>Entrada

### <a name="interaction-models"></a>Modelos de interação

Certifique-se de que as interações do holograma funcionem com o modelo [de interação escolhido.](../../design/interaction-fundamentals.md)
Também é uma boa ideia validar com acessórios diferentes, como mouse e teclado, se eles são necessários para dar suporte à acessibilidade.

**Valide quando seu aplicativo tiver um comportamento diferente com o mouse e o toque.** Identifica inconsistências e ajuda com decisões de design para tornar a experiência mais natural para os usuários. Por exemplo, disparar uma ação com base no foco.


### <a name="custom-voice-commands"></a>Comandos de voz personalizados

[A entrada de](../../design/voice-input.md) voz é uma forma natural de interação. A experiência do usuário pode ser mágica ou confusa, dependendo de sua escolha de comandos e de como você os expõe. Como regra, você não deve usar comandos de voz do sistema, como "Select" ou "Hey Cortana" como comandos personalizados. Aqui estão alguns pontos a considerar:
1. **Evite usar comandos que soem semelhantes.** Pode disparar o comando incorreto.
2. **Escolha palavras phoneticalmente ricas quando possível.** Minimiza e/ou evita ativações falsas.

### <a name="peripherals"></a>Periféricos

Os usuários podem interagir com seu aplicativo por meio [de periféricos](../../discover/hardware-accessories.md). Os aplicativos não precisam fazer nada especial para aproveitar essa funcionalidade, no entanto, há algumas coisas que vale a pena verificar.
1. **Validar interações personalizadas.** Coisas como atalhos de teclado personalizados para seu aplicativo.
2. **Valide a alternação de tipos de entrada.** Tentar usar vários métodos de entrada para concluir uma tarefa, como voz, gesto, mouse e teclado, tudo no mesmo cenário.

## <a name="system-integration"></a>Integração do sistema

### <a name="battery"></a>Bateria

Teste seu aplicativo sem uma fonte de alimentação conectada para entender a rapidez com que ele esvazia a bateria. É possível entender facilmente o estado da bateria observando as leituras do LED de energia. 

![Estados de LED que indicam a energia da bateria](images/batterypowerledindication-500px.png)<br>

*Estados de LED que indicam a energia da bateria*

### <a name="power-state-transitions"></a>Transições de estado de energia

Os principais cenários de validação funcionam conforme o esperado ao fazer a transição entre estados de energia. Por exemplo, o aplicativo permanece em sua posição original? Ele persiste corretamente seu estado? Ele continua funcionando conforme o esperado?
1. **Em stand-by/Resume.** Para entrar em espera, é possível pressionar e liberar o botão de energia imediatamente. O dispositivo também entrará em espera automaticamente após 3 minutos de inatividade. Para retomar do modo de espera, é possível pressionar e liberar o botão de energia imediatamente. O dispositivo também será retomado se você conectá-lo ou desconectá-lo de uma fonte de alimentação.
2. **Desligamento/Reinicialização.** Para desligar, pressione e mantenha o botão de energia pressionado continuamente por 6 segundos. Para reiniciar, pressione o botão de energia.

### <a name="multi-app-scenarios"></a>Cenários de vários aplicativos

Valide a funcionalidade principal do aplicativo ao alternar entre aplicativos, especialmente se você tiver implementado uma tarefa em segundo plano. Copiar/colar e Cortana também vale a pena verificar quando aplicável.

## <a name="telemetry"></a>Telemetria

Use telemetria e análise para orientá-lo. A integração da análise ao seu aplicativo ajudará você a obter informações sobre seu aplicativo de seus testadores Beta e usuários finais. Esses dados podem ser usados para ajudar a otimizar seu aplicativo antes do envio para a Store e para atualizações futuras. Há muitas opções de análise por aí. Se você não tiver certeza de onde começar, confira App [Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Perguntas a considerar:
1. Como os usuários estão usando o espaço?
2. Como o aplicativo está colocando objetos no mundo – você pode detectar problemas?
3. Quanto tempo eles gastam em diferentes estágios do aplicativo?
4. Quanto tempo eles gastam no aplicativo?
5. Quais são os caminhos de uso mais comuns que os usuários estão tentando?
6. Os usuários estão atingindo estados ou erros inesperados?

## <a name="emulator-and-simulated-input"></a>Emulator e entrada simulada

O [HoloLens emulador é](using-the-hololens-emulator.md) uma ótima maneira de testar com eficiência seu aplicativo Holographic com diferentes tipos de espaços e características de usuário simulados. Aqui estão algumas sugestões para usar efetivamente o emulador para testar seu aplicativo:
1. **Use as salas virtuais do emulador para expandir seus testes.** O emulador vem com um conjunto de salas virtuais que você pode usar para testar seu aplicativo em ainda mais ambientes.
2. **Use o emulador para ver seu aplicativo de todos os ângulos.** As chaves PageUp/PageDn tornarão o usuário simulado mais alto ou menor.
3. **Teste seu aplicativo com uma HoloLens.** O HoloLens Emulator é uma ótima ferramenta para ajudá-lo a iterar rapidamente em um aplicativo e capturar novos bugs, mas certifique-se de também testar em um HoloLens físico antes de enviar para a Windows Store. Isso é importante para garantir que o desempenho e a experiência sejam ótimos em hardware real.

## <a name="automated-testing-with-perception-simulation"></a>Teste automatizado com simulação de percepção

Alguns desenvolvedores de aplicativos podem querer automatizar testes de seus aplicativos. Além dos testes de unidade simples, você pode usar a pilha [de](perception-simulation.md) simulação de percepção HoloLens automatizar a entrada humana e mundial para seu aplicativo. A API de simulação de percepção pode enviar entrada simulada para o emulador HoloLens ou para um HoloLens.

## <a name="windows-app-certification-kit"></a>Kit de Certificação de Aplicativos Windows

Para dar ao aplicativo a melhor chance de ser publicado na [Windows Store,](../../distribute/submitting-an-app-to-the-microsoft-store.md)valide-o e teste-o localmente antes de enviar para certificação. Se o aplicativo tiver como destino o Windows. Família de dispositivos holográficos, [Windows Kit](/windows/uwp/debug-test-perf/windows-app-certification-kit) de Certificação de Aplicativos executará apenas testes de análise estática local em seu computador. Nenhum teste será executado em seu HoloLens.

## <a name="see-also"></a>Confira também

* [Enviando um aplicativo para a Windows Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)