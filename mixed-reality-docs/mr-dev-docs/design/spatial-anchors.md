---
title: Âncoras espaciais
description: Práticas recomendadas para usar âncoras espaciais para renderizar hologramas estáveis.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciais, escala mundial, mundo, escala, posição, orientação, âncora, âncora espacial, trancada mundial, bloqueio mundial, persistência, compartilhamento, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens
ms.openlocfilehash: 7f6997e491f76e66845b88ea0897dbb037495ba6
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848216"
---
# <a name="spatial-anchors"></a>Âncoras espaciais

Uma âncora espacial representa um ponto importante no mundo que o sistema rastreia ao longo do tempo. Cada âncora tem um [sistema de coordenadas](coordinate-systems.md)ajustável, com base em outras âncoras ou quadros de referência, para garantir que os hologramas ancorados permaneçam precisamente em vigor.  A renderização de um holograma no sistema de coordenadas de uma âncora fornece o posicionamento mais preciso para esse holograma em um determinado momento. Isso é voltado ao custo de pequenos ajustes ao longo do tempo até a posição do holograma, pois o sistema o move continuamente de volta para o lugar, com base no mundo real.

Você também pode persistir e compartilhar âncoras espaciais entre sessões de aplicativo e entre dispositivos:
* Ao salvar âncoras espaciais locais em disco e carregá-las novamente mais tarde, seu aplicativo pode calcular o mesmo local no mundo real entre várias sessões de aplicativo em um único HoloLens.
* Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem, seu aplicativo pode compartilhar uma âncora espacial entre vários dispositivos HoloLens, Ios e Android. Ao fazer com que cada dispositivo processe um holograma usando a mesma âncora espacial, os usuários verão que o holograma aparecerá no mesmo lugar do mundo real. Isso permite experiências compartilhadas em tempo real.
* Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para a persistência de holograma assíncrona em dispositivos de HoloLens, Ios e Android. Ao compartilhar uma âncora espacial de nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que esses dispositivos não estejam presentes juntos ao mesmo tempo.

Para experiências em escala de pé ou em escala de sala para headsets de área de trabalho que permanecerão dentro de um diâmetro de 5 metros, você normalmente pode usar o [quadro de referência](coordinate-systems.md#stage-frame-of-reference) em vez de âncoras espaciais, que fornece um único sistema de coordenadas no qual processar todo o conteúdo. No entanto, se seu aplicativo permitir que os usuários perfrentem mais de 5 metros no HoloLens, talvez operando em todo um andar de um edifício, você precisará de âncoras espaciais para manter o conteúdo estável.

Ainda que as âncoras espaciais sejam excelentes para hologramas que devam permanecer fixos no mundo, quando uma âncora é colocada, ela não pode ser movida. Há alternativas para âncoras que são mais apropriadas para hologramas dinâmicos que marcam junto com o usuário. É melhor posicionar hologramas dinâmicos usando um quadro de referência estacionário (a base para as coordenadas do mundo do Unity) ou um quadro de referência anexado.

## <a name="best-practices"></a>Práticas recomendadas

Essas diretrizes de âncora espacial vão ajudá-lo a renderizar hologramas estáveis que acompanham com precisão o mundo real.

### <a name="create-spatial-anchors-where-users-place-them"></a>Criar âncoras espaciais onde os usuários as posicionam

Normalmente, os usuários são aqueles explicitamente colocando âncoras espaciais.

Por exemplo, no HoloLens, um aplicativo pode interceptar o [olhar](gaze-and-commit.md) Ray do usuário com a malha de [mapeamento espacial](spatial-mapping.md) para permitir que o usuário decida onde posicionar um holograma. Quando o usuário toca para posicionar esse holograma, crie uma âncora espacial no ponto de interseção e coloque o holograma na origem do sistema de coordenadas da âncora.

Âncoras espaciais locais são fáceis e de alto desempenho para criar. O sistema combina dados internos se várias âncoras puderem compartilhar seus dados de sensor subjacentes. É recomendável criar uma nova âncora espacial local para cada holograma que um usuário insere explicitamente, exceto nos casos descritos abaixo, como grupos rígidos de hologramas.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Sempre processe hologramas ancorados a 3 metros de sua âncora

Âncoras espaciais estabilizam o sistema de coordenadas perto da origem da âncora. Se você renderizar hologramas mais de 3 metros da origem, os hologramas podem apresentar erros posicionais perceptíveis em proporção à distância dessa origem devido a efeitos de braço de alavanca. Isso funcionará se o usuário estiver próximo da âncora, já que o holograma está longe do usuário. Em outras palavras, o erro angular do holograma distante será pequeno. No entanto, se o usuário se movimentar até esse holograma distante, ele será grande em sua exibição, fazendo com que os efeitos de braço de alavanca da origem de ancoragem distante sejam óbvios.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Agrupe hologramas que devem formar um cluster rígido

Vários hologramas podem compartilhar a mesma âncora espacial se o aplicativo espera que esses hologramas mantenham as relações fixas entre si.

Por exemplo, se você estiver animando um sistema solar Holographic em uma sala, é melhor vincular todos os objetos do sistema solar a uma única âncora no centro. Dessa forma, eles mudarão suavemente com base em um do outro. Nesse caso, é o sistema solar como um todo que é ancorado, mesmo que suas partes de componente estejam mudando dinamicamente em relação à âncora.

A principal advertência para manter a estabilidade do holograma é seguir a regra de 3 medidores acima.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Renderizar hologramas altamente dinâmicos usando o quadro fixo de referência em vez de uma âncora espacial local

Se você tiver um holograma altamente dinâmico, como um caractere percorrendo uma sala ou uma interface de usuário flutuante que segue ao longo do usuário, é melhor ignorar âncoras espaciais locais e renderizar esses hologramas diretamente no sistema de coordenadas fornecido pelo [quadro estacionário de referência](coordinate-systems.md#stationary-frame-of-reference). No Unity, você consegue fazer isso colocando os hologramas diretamente em coordenadas mundiais sem um WorldAnchor. Os hologramas em um quadro estacionário de referência podem apresentar descompasso quando o usuário estiver longe do holograma. Mas isso é menos provável de ser perceptível para hologramas dinâmicos: ou o holograma está constantemente se movendo de forma constante ou seu movimento o mantém constantemente perto do usuário onde a descompasso será minimizada.

Um caso interessante de hologramas dinâmicos é o de um objeto que é animado de um sistema de coordenadas ancorado para outro. Por exemplo, você pode ter dois castelos 10 metros de distância, cada um em sua própria âncora espacial com um Castle acionando um Cannonball no outro Castle. Quando o Cannonball é acionado, você pode renderizá-lo no local apropriado no quadro estacionário de referência para coincidir com o Cannon no sistema de coordenadas ancorado do primeiro Castle. Ele pode seguir sua trajetória no quadro de referência fixo, já que voa por 10 metros pelo ar. Como o Cannonball atinge o outro Castle, você pode movê-lo para o sistema de coordenadas ancorado da segunda Castle para permitir cálculos de física com os corpos rígidos de Castle.

Se você estiver compartilhando um holograma altamente dinâmico entre dispositivos, escolha uma âncora espacial de nuvem para atuar como pai, pois os quadros de referência não podem ser compartilhados entre dispositivos.  No entanto, você deve garantir que o holograma dinâmico ou os dispositivos que o estão exibindo permanecem dentro do raio de 3 metros da âncora para que o holograma pareça estável em todos os dispositivos.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evite a criação de uma grade de âncoras espaciais

Você pode estar tentado a fazer com que seu aplicativo descartar uma grade comum de âncoras espaciais enquanto o usuário percorra, fazendo a transição de objetos dinâmicos da âncora para a âncora à medida que eles se movimentam. No entanto, isso envolve mais gerenciamento para seu aplicativo, sem o benefício dos dados de sensor profundo que o próprio sistema mantém internamente. Nesses casos, você obterá resultados melhores colocando seus hologramas no quadro estacionário de referência, conforme descrito na seção acima.
Quando você estiver preposicionando um conjunto de âncoras espaciais de nuvem em um espaço estático, considere colocar as âncoras espaciais nos locais dos hologramas-chave que o usuário apresenta de acordo com o princípio acima, em vez de criar uma grade arbitrária de âncoras. Isso garante que você obterá estabilidade máxima para esses hologramas importantes.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Libere as ancoras âncoras espaciais locais de que não precisa mais

Enquanto uma âncora espacial local está ativa, o sistema prioriza a manutenção dos dados do sensor que estão próximos dessa âncora. Se você não estiver mais usando uma âncora espacial, pare de acessar seu sistema de coordenadas. Isso permite que seus dados de sensor subjacentes sejam removidos conforme necessário.

Isso é especialmente importante para âncoras locais que você persistiu no repositório de âncora espacial. Os dados do sensor por trás dessas âncoras serão mantidos permanentemente para permitir que seu aplicativo encontre essa âncora em sessões futuras, o que reduz o espaço disponível para controlar outras âncoras. Mantenha apenas âncoras locais que você precisa localizar novamente em sessões futuras. É recomendável removê-los da loja quando eles não forem mais significativos para o usuário.

Nas âncoras espaciais de nuvem, o armazenamento pode ser dimensionado conforme seu cenário exigir. Você pode armazenar quantas âncoras de nuvem precisar, liberando-as quando souber que os usuários não precisarão da âncora novamente.

## <a name="see-also"></a>Consulte também

* [Sistemas de coordenadas](coordinate-systems.md)
* [Experiências compartilhadas em realidade misturada](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* [Persistência no Unity](../develop/unity/persistence-in-unity.md)
* [Âncoras espaciais no DirectX](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Estudo de caso - Como olhar através dos buracos na sua realidade](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)
