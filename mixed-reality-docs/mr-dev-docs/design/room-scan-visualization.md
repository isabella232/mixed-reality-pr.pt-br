---
title: Visualização de varredura do ambiente
description: Aplicativos que exigem mapeamento espacial usam o dispositivo para coletar dados ao longo do tempo e entre sessões.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, padrões de aplicativo, design, HoloLens, verificação de sala, mapeamento espacial, malha, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, HoloLens
ms.openlocfilehash: 0ebfbd9a1f07ffd0671d36dcc63dbd5303a2cdbceb906839be9736f43de76937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207824"
---
# <a name="room-scan-visualization"></a>Visualização de varredura do ambiente

Os aplicativos que exigem mapeamento espacial dependem do dispositivo para coletar dados ao longo do tempo e entre as sessões. A integridade e a qualidade dos dados de mapeamento dependem de muitos fatores, incluindo a quantidade de explorações que o usuário fez, quanto tempo passou desde a exploração e se objetos como mobília e portas foram movidos desde que o dispositivo examinou a área.

Para garantir dados de mapeamento espacial úteis, os desenvolvedores de aplicativos têm várias opções:
* Conte com o que já pode ter sido coletado. Esses dados podem estar incompletos inicialmente.
* peça ao usuário para usar o gesto de cair para chegar ao Windows Mixed Reality home e, em seguida, explorar a área que desejam usar para a experiência. Eles podem usar o Air-TAP para confirmar se toda a área necessária é conhecida pelo dispositivo.
* Crie uma experiência de exploração personalizada em seu próprio aplicativo.

Em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso. se você quiser ver a visualização da verificação de sala em ação, confira nossa demonstração de vídeo **de conscientização Hologramas espacial** abaixo:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

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

Os aplicativos podem analisar os dados de mapeamento espacial no início da experiência para avaliar se querem que o usuário execute etapas adicionais para melhorar sua integridade e qualidade. Se a análise indicar que a qualidade deve ser melhorada, os desenvolvedores devem fornecer uma visualização para sobreposição no mundo para indicar:
* Quanto do volume total nos arredores dos usuários precisa fazer parte da experiência
* Onde o usuário deve ir para melhorar os dados

Os usuários não sabem o que faz uma verificação "boa". Eles precisam ser mostrados ou disseram o que procurar se forem solicitados a avaliar uma verificação – Flatness, distância de paredes reais e assim por diante. O desenvolvedor deve implementar um loop de comentários que inclua a atualização dos dados de mapeamento espacial durante a fase de verificação ou exploração.

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
* Você não precisa criar uma experiência separada de verificação ou exploração antecipada em seu aplicativo.
* A movimentação de objetos do mundo real pode ser refletida pelo jogo, embora com algum atraso.

**Desvantagens**
* Maior complexidade na implementação da experiência principal.
* Sobrecarga potencial do processamento de elementos gráficos e da física extra, pois as alterações precisam ser ingeridas incrementalmente por esses sistemas.
* Maior capacidade, térmico e impacto na CPU.

Um bom caso para esse método é um em que os hologramas devem interagir com a movimentação de objetos, por exemplo, um carro Holographic que as unidades no chão podem desejar aumentar para uma porta dependendo se ela está aberta ou fechada.

## <a name="see-also"></a>Veja também

* [Mapeamento espacial](spatial-mapping.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Projeto de som espacial](spatial-sound-design.md)