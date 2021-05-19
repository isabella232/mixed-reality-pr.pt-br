---
title: Visualização de varredura do ambiente
description: Aplicativos que exigem mapeamento espacial usam o dispositivo para coletar dados ao longo do tempo e entre sessões.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Padrões de aplicativo, design, HoloLens, verificação de sala, mapeamento espacial, malha, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143616"
---
# <a name="room-scan-visualization"></a>Visualização de varredura do ambiente

Os aplicativos que exigem mapeamento espacial dependem do dispositivo para coletar dados ao longo do tempo e entre sessões. A conclusão e a qualidade dos dados de mapeamento dependem de muitos fatores, incluindo a quantidade de exploração que o usuário fez, quanto tempo passou desde a exploração e se objetos como móveis e portas foram movidos desde que o dispositivo examinou a área.

Para garantir dados úteis de mapeamento espacial, os desenvolvedores de aplicativos têm várias opções:
* Confie no que pode já ter sido coletado. Esses dados podem estar incompletos inicialmente.
* Peça ao usuário para usar o gesto de bloom para chegar à Windows Mixed Reality e, em seguida, explorar a área que deseja usar para a experiência. Eles podem usar o toque de ar para confirmar se toda a área necessária é conhecida pelo dispositivo.
* Crie uma experiência de exploração personalizada em seu próprio aplicativo.

Em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso. Se você quiser ver a visualização de verificação de sala em ação, confira nossa demonstração de vídeo [Designing Holograms – Spatial Awareness]() abaixo:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Visualização de varredura do ambiente</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a>Criando uma experiência de verificação personalizada

Os aplicativos podem analisar os dados de mapeamento espacial no início da experiência para avaliar se eles querem que o usuário faça etapas adicionais para melhorar sua conclusão e sua qualidade. Se a análise indicar que a qualidade deve ser aprimorada, os desenvolvedores deverão fornecer uma visualização para sobreposição no mundo para indicar:
* Quanto do volume total na proximidade dos usuários precisa fazer parte da experiência
* Onde o usuário deve ir para melhorar os dados

Os usuários não sabem o que torna uma verificação "boa". Eles precisam ser mostrados ou disseram o que procurar se forem solicitados a avaliar uma verificação – Flatness, distância de paredes reais e assim por diante. O desenvolvedor deve implementar um loop de comentários que inclua a atualização dos dados de mapeamento espacial durante a fase de verificação ou exploração.

Em muitos casos, é melhor informar ao usuário o que eles precisam fazer para obter a qualidade de verificação necessária. Por exemplo, examine o teto, procure atrás de mobília e assim por diante.

## <a name="cached-versus-continuous-spatial-mapping"></a>Mapeamento espacial em cache versus contínua

Os dados de mapeamento espacial são os aplicativos de fonte de dados de peso mais intenso que podem ser consumidos. Para evitar problemas de desempenho como quadros descartados ou excedentes, o consumo desses dados deve ser feito com cuidado.

A verificação ativa durante uma experiência pode ser benéfica e prejudicial, portanto, você precisará decidir qual método usar com base na experiência.

### <a name="cached-spatial-mapping"></a>Mapeamento espacial armazenado em cache

Se houver dados de mapeamento espacial em cache, o aplicativo normalmente capturará um instantâneo dos dados de mapeamento espacial e usará esse instantâneo durante a experiência.

**Benefícios**
* Redução da sobrecarga no sistema, enquanto a experiência está em execução levando a um aumento considerável de energia, térmico e ganhos de desempenho de CPU.
* Uma implementação mais simples da experiência principal, uma vez que ela não é interrompida por alterações nos dados espaciais.
* Um único custo individual em qualquer processamento posterior de dados espaciais para física, gráficos e outras finalidades.

**Desvantagens**
* A movimentação de objetos do mundo real ou de pessoas não é refletida pelos dados armazenados em cache. por exemplo, o aplicativo pode considerar uma porta aberta quando é fechado agora.
* Possivelmente mais memória de aplicativo para manter a versão em cache dos dados.

Um bom caso para esse método é um ambiente controlado ou um jogo de topo de tabela.

### <a name="continuous-spatial-mapping"></a>Mapeamento espacial contínuo

Determinados aplicativos podem depender da varredura para atualizar dados de mapeamento espacial.

**Benefícios**
* Você não precisa criar uma experiência de verificação ou exploração separada antecipadamente em seu aplicativo.
* O movimento de objetos do mundo real pode ser refletido pelo jogo, embora com algum atraso.

**Inconvenientes**
* Maior complexidade na implementação da experiência principal.
* Possível sobrecarga do processamento gráfico e físico extra, pois as alterações precisam ser ingeridos incrementalmente por esses sistemas.
* Maior impacto de energia, calor e CPU.

Um bom caso para esse método é aquele em que os hologramas devem interagir com objetos de movimentação, por exemplo, um carro holográfico que conduz no chão pode querer colidir em uma porta, dependendo se ele está aberto ou fechado.

## <a name="see-also"></a>Veja também

* [Mapeamento espacial](spatial-mapping.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Projeto de som espacial](spatial-sound-design.md)