---
title: Critérios de qualidade do aplicativo
description: Este documento descreve os principais fatores que impactam a qualidade dos aplicativos de realidade misturada.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: critérios de qualidade do aplicativo, realidade misturada, aplicativo de realidade misturada, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 858b0782c4e6754ee6753d463d5fe498e3a893f6c21b3f1c86ac14f8c0e6c8cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189375"
---
# <a name="app-quality-criteria"></a>Critérios de qualidade do aplicativo

Este documento descreve os principais fatores que impactam a qualidade dos aplicativos de realidade misturada. Para cada fator, as informações a seguir são fornecidas
* Visão geral – uma breve descrição do fator de qualidade e por que ele é importante.
* Impacto do dispositivo – qual tipo de dispositivo de Realidade Misturada da Janela é afetado.
* Critérios de qualidade – como avaliar o fator de qualidade.
* Como medir – métodos para medir (ou experimentar) o problema.
* Recomendações – resumo das abordagens para fornecer uma melhor experiência do usuário.
* Recursos – recursos de design e desenvolvedor relevantes que são úteis para criar experiências de aplicativo melhores.

## <a name="frame-rate"></a>Taxa de quadros

A taxa de quadros é o primeiro pilar da estabilidade do holograma e do conforto do usuário. A taxa de quadros abaixo dos destinos recomendados pode fazer com que os hologramas pareçam tremidos, afetando negativamente a capacidade de insuperabilidade da experiência e potencialmente causando a dor ocular. A taxa de quadros de destino para Windows Mixed Reality experiência em headsets imersivos é de 60 Hz ou 90 Hz, dependendo de quais Windows Mixed Reality compatíveis com os quais você está dando suporte. Por HoloLens, a taxa de quadros de destino é de 60 Hz.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
| O aplicativo atende consistentemente à meta de FPS (quadros por segundo) para o dispositivo de destino: 60 fps no HoloLens; 90 fps em PCs Ultra; e 60 fps em PCs base. | O aplicativo tem quedas de quadro intermitentes não impedindo a experiência principal ou o FPS é consistentemente menor do que a meta desejada, mas não impede a experiência do aplicativo. | O aplicativo está apresentando uma queda na taxa de quadros em média a cada 10 segundos ou menos. |

### <a name="how-to-measure"></a>Como medir

* Um grafo de taxa de quadros em tempo real é fornecido pelo [Windows Portal de Dispositivos](using-the-windows-device-portal.md#system-performance) em "Desempenho do Sistema".
* Para depuração de desenvolvimento, adicione um contador de diagnóstico de taxa de quadros ao aplicativo. Consulte Recursos para um contador de exemplo.
* As quedas de taxa de quadros podem ser experimentadas no dispositivo enquanto o aplicativo está em execução movendo a cabeça de um lado para outro. Se o holograma mostrar movimento tremumétrico inesperado, a baixa taxa de quadros ou o plano de estabilidade provavelmente será a causa.

### <a name="recommendations"></a>Recomendações

* Adicione um contador de taxa de quadros no início do trabalho de desenvolvimento.
* As alterações que incorrem em uma queda na taxa de quadros devem ser avaliadas e resolvidas adequadamente como um bug de desempenho.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Noções básicas sobre o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Estabilidade e taxa de quadros do holograma](hologram-stability.md#frame-rate)
* [Orçamento de desempenho do ativo](../../design/asset-creation-process.md)
* [Recomendações de desempenho para Unity](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Exibição de Toolkit, contador FPS](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [Realidade Misturada Toolkit, Sombreadores](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Referências externas

* [Unity, Otimizando aplicativos móveis](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Estabilidade do holograma

Hologramas estáveis aumentarão a usabilidade e a acessibilidade do seu aplicativo e criarão uma experiência de exibição mais confortável para o usuário. A qualidade da estabilidade do holograma é resultado do bom desenvolvimento de aplicativos e da capacidade do dispositivo de entender (controlar) seu ambiente. Embora a taxa de quadros seja o primeiro pilar da estabilidade, outros fatores podem afetar a estabilidade, incluindo:

* Uso do plano de estabilização
* Distância para âncoras espaciais
* Acompanhamento

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  Hologramas consistentemente parecem estáveis. | O conteúdo secundário mostra movimentação inesperada; ou movimento inesperado não impede a experiência geral do aplicativo. | O conteúdo primário no quadro mostra movimentação inesperada. |

### <a name="how-to-measure"></a>Como medir

Ao usar o dispositivo e exibir a experiência:

* Mova a cabeça de um lado para outro. Se os hologramas mostrarem movimento inesperado, a baixa taxa de quadros ou o alinhamento inadequado do plano de estabilidade para o plano focal será a causa provável.
* Mova os hologramas e o ambiente, procure comportamentos como nada e jumpiness. Esse tipo de movimento provavelmente é causado pelo dispositivo não acompanhar o ambiente ou pela distância até a âncora espacial.
* Se os hologramas grandes ou múltiplos estão no quadro, observe o comportamento do holograma em várias profundidades ao mover a posição da cabeça de um lado para o outro, se a estrutura aparecer, isso provavelmente será causado pelo plano de estabilização.

### <a name="recommendations"></a>Recomendações

* Adicione um contador de taxa de quadros no início do trabalho de desenvolvimento.
* Use o plano de estabilização.
* Sempre renderizar hologramas ancorados a 3 metros de sua âncora.
* Certifique-se de que seu ambiente está definido para o acompanhamento adequado.
* Projete sua experiência para evitar hologramas em vários níveis de profundidade focal dentro do quadro.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Estabilidade e taxa de quadros do holograma](hologram-stability.md#frame-rate)
* [Estudo de caso, usando o plano de estabilização](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Noções básicas sobre o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](../unity/performance-recommendations-for-unity.md)
* [Âncoras espaciais](../../design/spatial-anchors.md)
* [Tratamento de erros de acompanhamento](../../design/coordinate-systems.md#handling-tracking-errors)
* [Quadro estacionário de referência](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [KIT de adoção do MR, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Hologramas posição em superfícies reais

Desalinhamentos de hologramas com objetos físicos (se destinados a serem colocados em relação um ao outro) são uma indicação clara da não união de hologramas e do mundo real. A precisão do posicionamento deve ser relativa às necessidades do cenário; por exemplo, o posicionamento de superfície geral pode usar o mapa espacial, mas um posicionamento mais preciso exigirá algum uso de marcadores e calibragem.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
| Hologramas alinhar à superfície normalmente no intervalo de centímetros a polegadas. Se você precisar de mais precisão, o aplicativo deverá fornecer um meio eficiente para a colaboração dentro da especificação do aplicativo. | NA | Os hologramas aparecem sem qualificação com o objeto de destino físico, quebrando o plano de superfície ou aparecendo para sair da superfície. Se a precisão for necessária, Hologramas deverá atender à especificação de proximidade do cenário. | 

### <a name="how-to-measure"></a>Como medir

* Hologramas que são colocados no mapa espacial não devem parecer flutuando drasticamente acima ou abaixo da superfície.
* Hologramas que exigem posicionamento preciso deve ter alguma forma de sistema de calibragem e marcador que seja preciso para os requisitos do cenário.

### <a name="recommendations"></a>Recomendações

* O mapa espacial é útil para colocar objetos em superfícies quando a precisão não é necessária.
* Para melhor precisão, use marcadores ou cartazes para definir os hologramas e um controlador Xbox (ou algum mecanismo de alinhamento manual) para calibragem final.
* Considere a quebra de hologramas extra grandes em partes lógicas e alinhe cada parte à superfície.
* Definir incorretamente a ipd (distância interpupária) também pode ter efeito no alinhamento do holograma. Sempre configure HoloLens para o IPD do usuário.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Posicionamento de mapeamento espacial](../../design/spatial-mapping.md#placement)
* [Processo de verificação de sala](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Melhores práticas de âncoras espaciais](../../design/spatial-anchors.md#best-practices)
* [Tratamento de erros de acompanhamento](../../design/coordinate-systems.md#handling-tracking-errors)
* [Mapeamento espacial no Unity](../unity/spatial-mapping-in-unity.md)
* [Visão geral do desenvolvimento do Vuforia](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Bibliotecas Toolkit de mapeamento espacial do MR](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [Kit de adoção do MR, amostra de calibragem de cartaz](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [KIT de adoção do MR, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Referências externas

* [Estudo de caso lowes, alinhamento de precisão](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Exibindo a zona de conforto

Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergem colocando conteúdo e hologramas em várias profundidades. Os usuários que usam HoloLens sempre se acomodarão a 2,0 m para manter uma imagem clara, pois as exibições HoloLens são fixas a uma distância óptica de aproximadamente 2,0 m do usuário. A profundidade inadequada do conteúdo pode levar a um estresse visual ou a um estresse.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

<table>
<tr>
<td> Melhor </td><td><ul>
<li>Coloque o conteúdo em 2 m.</li><li>Quando os hologramas não podem ser colocados a 2 m e conflitos entre convergência e acomodação não podem ser evitados, a zona ideal para posicionamento do holograma está entre 1,25 m e 5 m.</li><li>Em todos os casos, os designers devem estruturar o conteúdo para incentivar os usuários a interagir a mais de 1 m de distância (por exemplo, ajustar o tamanho do conteúdo e os parâmetros de posicionamento padrão).</li><li>A menos que não seja exigido pelo cenário, um plano de recorte deve ser implementado com esmaeçamento começando em 1 m.</li><li>Nos casos em que uma observação mais próxima de um holograma sem movimento é necessária, o conteúdo não deve estar mais próximo de 50 cm.</li>
</ul></td>
</tr><tr>
<td> Encontra</td><td> O conteúdo está dentro das diretrizes de exibição e movimento, mas uso inadequado ou nenhum uso do plano de recorte.</td>
</tr><tr>
<td> Falha </td><td> O conteúdo é apresentado muito próximo (normalmente &lt; 1,25 m ou &lt; 50 cm para hologramas estacionários que exigem uma observação mais próxima.)</td>
</tr>
</table>

### <a name="how-to-measure"></a>Como medir

* O conteúdo normalmente deve estar a 2 m de distância, mas não mais próximo de 1,25 ou mais de 5 m.
* Com poucas exceções, a HoloLens de renderização de recorte deve ser definida como 85CM com esmaeçamento do conteúdo começando em 1 m. Aborde o conteúdo e observe o efeito do plano de recorte.
* O conteúdo estacionário não deve estar mais próximo de 50 cm de distância.

### <a name="recommendations"></a>Recomendações

* Criar conteúdo para a distância de exibição ideal de 2 m.
* De definir a distância de renderização de recorte como 85 cm com esmaeçamento do conteúdo começando em 1 m.
* Para hologramas estacionários que precisam de uma exibição mais próxima, o plano de recorte não deve estar mais próximo de 30 cm e esmaecer deve começar pelo menos 10 cm de distância do plano de recorte.

### <a name="resources"></a>Recursos

* [Distância de renderização](hologram-stability.md#hologram-render-distances)
* [Ponto de foco no Unity](../unity/focus-point-in-unity.md)
* [Experimentando com escala](../../design/scale.md#experimenting-with-scale)
* [Texto, Tamanho da fonte recomendado](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a>Alternamento de profundidade

Independentemente da zona de exibição de problemas de conforto, as demandas para o usuário alternar com frequência ou rapidez entre objetos focal próximos e distantes (incluindo hologramas e conteúdo do mundo real) podem levar à confusão oculoculor e ao conforto geral.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  Alternação de profundidade limitada ou natural que não faz com que o usuário se refocuse de maneira natural. | Alternam a profundidade de um núcleo e foram projetados para a experiência do aplicativo ou com a opção de profundidade abrupta causada por conteúdo inesperado do mundo real. | Alternamento de profundidade consistente ou alternação de profundidade repentina que não é necessária ou fundamental para a experiência do aplicativo. | 

### <a name="how-to-measure"></a>Como medir

* Se o aplicativo exigir que o usuário altere o foco de profundidade de forma consistente e/ou de forma coerente, haverá um problema de alternação de profundidade.

### <a name="recommendations"></a>Recomendações

* Mantenha o conteúdo primário em um plano focal consistente e certifique-se de que o plano de estabilização corresponde ao plano focal. Isso atenuará o estresse oculométricor e a movimentação inesperada do holograma.

### <a name="resources"></a>Recursos

* [Distância de renderização](hologram-stability.md#hologram-render-distances)
* [Ponto de foco no Unity](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Uso de som espacial

No Windows Mixed Reality, o mecanismo de áudio fornece o componente aural da experiência de realidade misturada simulando o som 3D usando simulações de direção, distância e ambiente. O uso de som espacial em um aplicativo permite que os desenvolvedores coloquem os sons de maneira convincente em um espaço tridimensional (esfera) ao redor do usuário. Esses sons, então, parecerão como se fossem provenientes de objetos físicos reais ou dos hologramas de realidade misturada no ambiente do usuário. O som espacial é uma ferramenta poderosa para imersão, acessibilidade e design de UX em aplicativos de realidade misturada.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  O som é espacializado logicamente e a experiência do usuário usa adequadamente o som para ajudar com a descoberta de objetos e comentários do usuário. O som é natural e relevante para objetos e normalizado em todo o cenário. | O áudio espacial é usado adequadamente para invisibilidade, mas ausente como meio de ajudar com comentários do usuário e capacidade de descoberta. | O som não é espacializado conforme o esperado e/ou a falta de som para ajudar o usuário na experiência do usuário. Ou o áudio espacial não foi considerado ou usado no design do cenário. | 

### <a name="how-to-measure"></a>Como medir

* Em geral, os sons relevantes devem emitir dos hologramas de destino (por exemplo, o som do cachorro holográfico.)
* As dicas de som devem ser usadas em toda a experiência do usuário para auxiliar o usuário com comentários ou reconhecimento de ações fora do quadro holográfico.

### <a name="recommendations"></a>Recomendações

* Use áudio espacial para auxiliar na descoberta de objetos e interfaces do usuário.
* Os sons reais funcionam melhor do que sintetizar ou fazer som anormal.
* A maioria dos sons deve ser espacializada.
* Evite emissores invisíveis.
* Evite mascaramento espacial.
* Normalizar todos os sons.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Som espacial](../../design/spatial-sound.md)
* [Projeto de som espacial](../../design/spatial-sound-design.md)
* [Som espacial no Unity](../unity/spatial-sound-in-unity.md)
* [Estudo de caso, som espacial para HoloTour](../../design/case-study-spatial-sound-design-for-holotour.md)
* [Estudo de caso, Uso de som espacial no RoboRaid](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Realidade Misturada Toolkit – Áudio Espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Foco em limites de FOV (quadro holográfico)

Experiências de usuário bem projetadas podem criar e manter um contexto útil do ambiente virtual que se estende em torno dos usuários. Atenuar o efeito dos limites de FOV envolve um design cuidadoso de escala e contexto de conteúdo, uso de áudio espacial, sistemas de diretrizes e a posição do usuário. Se for feito responsabilidade, o usuário se sentirá menos prejudicado pelos limites de FOV enquanto tiver uma experiência de aplicativo confortável.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  O usuário nunca perde o contexto e a exibição é confortável. A assistência de contexto é fornecida para objetos grandes. As diretrizes de descoberta e exibição são fornecidas para objetos fora do quadro. Em geral, o design de movimento e a escala dos hologramas são apropriados para uma experiência de exibição confortável. | O usuário nunca perde o contexto, mas o movimento extra do braço pode ser necessário em situações limitadas. Em situações limitadas, a escala faz com que os hologramas quebrem o quadro vertical ou horizontal, fazendo com que algum movimento do braço veja hologramas. | É provável que o usuário perca o contexto e/ou o movimento consistente do braço para exibir hologramas. Nenhuma orientação de contexto para objetos holográficos grandes, movimentação de objetos fáceis de perder fora do quadro sem diretrizes de descoberta ou hologramas altos exigem movimento regular do corpo para exibição. | 

### <a name="how-to-measure"></a>Como medir

* O contexto de um holograma (grande) é perdido ou não é compreendido devido à recortada nos limites.
* Locais de hologramas são difíceis de encontrar devido à falta de diretores de atenção ou conteúdo que se move rapidamente para dentro e para fora do quadro holográfico.
* O cenário requer movimento normal para cima e para baixo para ver totalmente um holograma, resultando em estresse no braço.

### <a name="recommendations"></a>Recomendações

* Inicie a experiência com objetos pequenos que se ajustam ao FOV e, em seguida, transição com versões visuais para versões maiores.
* Use áudio espacial e diretores de atenção para ajudar o usuário a encontrar conteúdo que está fora do FOV.
* Tanto quanto possível, evite hologramas que cortem verticalmente o FOV.
* Forneça ao usuário diretrizes no aplicativo para melhor localização de exibição.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Quadro holográfico](../../design/holographic-frame.md)
* [Estudo de caso, HoloStudio interface do usuário e aprendizados de design de interação](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Escala de objetos e ambientes](../../design/scale.md)
* [Cursores, dicas visuais](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a>Referências externas

* [Muito ado sobre o FOV](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>O conteúdo reage à posição do usuário

Hologramas deve reagir à posição do usuário aproximadamente da mesma maneira que os objetos "reais". Uma consideração de design notável são elementos de interface do usuário que não podem necessariamente assumir que a posição de um usuário é estacionária e se adaptar ao movimento do usuário. Criar um aplicativo que se adapta corretamente à posição do usuário criará uma experiência mais fácil e facilitará o uso.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

<table>
<tr>
<td> Melhor </td><td> O conteúdo e a interface do usuário se adaptam às posições do usuário, permitindo que o usuário interaja naturalmente com o conteúdo dentro do escopo da movimentação esperada do usuário.</td>
</tr><tr>
<td> Encontra </td><td> A interface do usuário se adapta à posição do usuário, mas pode impedir a exibição do conteúdo de chave que exige que o usuário ajuste sua posição.</td>
</tr><tr>
<td> Falha </td><td><ol>
<li>Os elementos da interface do usuário são perdidos ou bloqueados durante a movimentação, fazendo com que o usuário retorne de maneira não natural a controles (ou encontre).</li><li>Os elementos da interface do usuário limitam a exibição do conteúdo primário.</li><li>A movimentação da interface do usuário não é otimizada para exibir a distância e a dinâmica, especialmente com elementos de interface do usuário <a href="../../design/billboarding-and-tag-along.md">de marcação.</a></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Como medir

* Todas as medidas devem ser feitas dentro de um escopo razoável do cenário. Embora a movimentação do usuário varie, não tente enganar o aplicativo com movimentação extrema do usuário.
* Para elementos da interface do usuário, os controles relevantes devem estar disponíveis, independentemente da movimentação do usuário. Por exemplo, se o usuário estiver exibindo e passeando em torno de um mapa 3D com zoom, o controle de zoom deverá estar prontamente disponível para o usuário, independentemente da localização.

### <a name="recommendations"></a>Recomendações

* O usuário é a câmera e controla o movimento. Deixe-os conduzir.
* Considere o uso de texto e sistemas de menu que, de outra forma, seriam bloqueados pelo mundo ou obscurecidos se um usuário se movimentasse.
* Use tag-along para conteúdo que precisa seguir o usuário, permitindo que o usuário veja o que está na frente dele.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Design de interação](../../discover/hologram.md)
* [Cor, luz e material](../../design/color-light-and-materials.md)
* [Mural e tag-along](../../design/billboarding-and-tag-along.md)
* [Interações instinctuais](../../design/interaction-fundamentals.md)
* [Automovimento e locomoção do usuário](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a>Clareza da interação de entrada

A clareza da interação de entrada é essencial para a usabilidade de um aplicativo e inclui consistência de entrada, abordagem, capacidade de descoberta de métodos de interação. O usuário pode usar interações comuns em toda a plataforma sem relearning. Se o aplicativo tiver entrada personalizada, ele deverá ser claramente comunicado e demonstrado.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  Os métodos de interação de entrada são consistentes Windows Mixed Reality [diretrizes fornecidas.](../../design/interaction-fundamentals.md) Qualquer entrada personalizada não deve ser redundante com a entrada padrão (em vez de usar a interação padrão) e deve ser claramente comunicada e demonstrada ao usuário. | Semelhante ao melhor, mas as entradas personalizadas são redundantes com métodos de entrada padrão. O usuário ainda pode atingir a meta e o progresso por meio da experiência do aplicativo. | Difícil de entender o método de entrada ou o mapeamento de botão. A entrada é altamente personalizada, não dá suporte à entrada padrão, nenhuma instrução ou provavelmente causa problemas de estresse e conforto. | 

### <a name="how-to-measure"></a>Como medir

* O aplicativo usa métodos de [entrada padrão consistentes.](../../design/interaction-fundamentals.md)
* Se o aplicativo tiver entrada personalizada, ele será claramente comunicado por meio de:
* Experiência de primeira a ser executado
* Telas introdutórios
* Dicas de ferramenta
* Orientador de mão
* Seção de ajuda
* Comando de voz

### <a name="recommendations"></a>Recomendações

* Use métodos de entrada padrão sempre que possível.
* Forneça demonstrações, tutoriais e dicas de ferramenta para métodos de entrada não padrão.
* Use um modelo de interação consistente em todo o aplicativo.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Interações instinctuais](../../design/interaction-fundamentals.md)
* [Objetos interagidos](../../design/interactable-object.md)
* [Focar com a cabeça e esperar](../../design/gaze-and-dwell.md)
* [Cursores](../../design/cursors.md)
* [Conforto e olhar](../../design/comfort.md#gaze-direction)
* [Entrada de voz](../../design/voice-input.md)
* [Controladores de movimentos](../../design/motion-controllers.md)
* [Guia de portabilidade de entrada para Unity](../porting-apps/input-porting-guide-for-unity.md)
* [Entrada do teclado no Unity](../unity/keyboard-input-in-unity.md)
* [Foco no Unity](../unity/gaze-in-unity.md)
* [Controladores de movimento no Unity](../unity/motion-controllers-in-unity.md)
* [Gestos no Unity](../unity/gestures-in-unity.md)
* [Entrada de voz no Unity](../unity/voice-input-in-unity.md)
* [Teclado, mouse e entrada do controlador no DirectX](./keyboard-mouse-and-controller-input-in-directx.md)
* [Olhar fixo com cabeça e olhos no DirectX](../native/gaze-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](../native/hands-and-motion-controllers-in-directx.md)
* [Entrada de voz no DirectX](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Estudo de caso: a busca de computação mais pessoal](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Estudo de cast: aprendizados HoloStudio design de interação e interface do usuário](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Aplicativo de exemplo: tabela periódica dos elementos](../unity/periodic-table-of-the-elements.md)
* [Aplicativo de exemplo: módulo lunar](../unity/lunar-module.md)

## <a name="interactable-objects"></a>Objetos interagidos

Há muito tempo, um botão é uma metáfora usada para disparar um evento no mundo abstrato 2D. No mundo da realidade misturada tridimensional, não precisamos mais estar restritos a esse mundo de abstração. Qualquer coisa pode ser um objeto Interacionável que dispara um evento. Um objeto interagente pode ser representado como qualquer coisa, desde uma cafeteira na tabela até um balão flutuando no ar. Independentemente do formulário, os objetos interajantes devem ser claramente reconhecíveis pelo usuário por meio de responsabilidades visuais e de áudio.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  Independentemente da forma, os objetos interajantes são reconhecíveis por meio de dicas visuais e de áudio em três estados: ocioso, direcionado e selecionado. "Veja isso, diga-o" é claro e consistentemente usado em toda a experiência. Os objetos são dimensionados e distribuídos para permitir o direcionamento sem erros. | O usuário pode reconhecer o objeto como interacionável por meio de comentários visuais ou de áudio e pode direcionar e ativar o objeto. | Dado nenhuma indicação visual ou de áudio, o usuário não pode reconhecer um objeto interajante. As interações são propensas a erros devido à escala de objeto ou à distância entre objetos. | 

### <a name="how-to-measure"></a>Como medir

* Objetos interagidos são reconhecíveis como 'interagidos'; incluindo botões, menus e conteúdo específico do aplicativo. Como regra geral, deve haver uma indicação visual e de áudio ao direcionar objetos interagidos.

### <a name="recommendations"></a>Recomendações

* Use comentários visuais e de áudio para interações.
* Os comentários visuais devem ser diferenciados para cada estado de entrada (ocioso, direcionado, selecionado)
* Objetos interacionáveis devem ser dimensionados e colocados para direcionamento sem erros.
* Objetos interagidos agrupados (como uma barra de menus ou lista) devem ter espaçamento adequado para direcionamento.
* Botões e menus que dão suporte ao comando de voz devem fornecer rótulos de texto para a palavra-chave de comando ("Veja, diga")

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Objeto interativo](../../design/interactable-object.md)
* [Texto no Unity](../unity/text-in-unity.md)
* [Caixa delimitadora e barra de aplicativos](../../design/app-bar-and-bounding-box.md)
* [Entrada de voz](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Realidade Misturada Toolkit – UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Verificação de sala

Os aplicativos que exigem dados de mapeamento espacial dependem do dispositivo para coletar automaticamente esses dados ao longo do tempo e entre sessões à medida que o usuário explora seu ambiente com o dispositivo ativo. A conclusão e a qualidade desses dados dependem de vários fatores, incluindo a quantidade de exploração que o usuário fez, quanto tempo passou desde a exploração e se objetos como móveis e portas foram movidos desde que o dispositivo examinou a área. Muitos aplicativos analisarão os dados de mapeamento espacial no início da experiência para avaliar se o usuário deve executar etapas adicionais para melhorar a conclusão e a qualidade do mapa espacial. Se o usuário precisar examinar o ambiente, diretrizes claras deverão ser fornecidas durante a experiência de verificação.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  A visualização da malha espacial diz aos usuários que a verificação está em andamento. O usuário sabe claramente o que fazer e quando a verificação é iniciada e interrompida. | A visualização da malha espacial é fornecida, mas o usuário pode não saber claramente o que fazer e nenhuma informação de progresso é fornecida. | Nenhuma visualização da malha. Nenhuma informação de diretriz fornecida ao usuário sobre onde procurar ou quando a verificação é iniciada/interrompida. |

### <a name="how-to-measure"></a>Como medir

* Durante uma verificação de sala necessária, as diretrizes visuais e de áudio são fornecidas indicando onde procurar e quando iniciar e parar a verificação.

### <a name="recommendations"></a>Recomendações

* Indique quanto do volume total nas proximidades dos usuários precisa fazer parte da experiência.
* Comunique-se quando a verificação for iniciada e parar, como um indicador de progresso.
* Use uma visualização da malha durante a verificação.
* Forneça dicas visuais e de áudio para incentivar o usuário a procurar e mover-se pela sala.
* Informe ao usuário onde ir para melhorar os dados. Em muitos casos, pode ser melhor dizer ao usuário o que ele precisa fazer (por exemplo, examinar o limite, olhar atrás de móveis), para obter a qualidade necessária da verificação.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Visualização de varredura do ambiente](../../design/room-scan-visualization.md)
* [Estudo de caso: expandindo as funcionalidades de mapeamento espacial HoloLens](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Estudo de caso: Design de som espacial para HoloTour](../../design/case-study-spatial-sound-design-for-holotour.md)
* [Estudo de caso: criando uma experiência imersiva em Fragmentos](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Realidade Misturada Toolkit – UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicadores direcionais

Em um aplicativo de realidade misturada, o conteúdo pode estar fora do campo de exibição ou ser ocluído por objetos do mundo real. Um aplicativo bem projetado facilitará para o usuário encontrar conteúdo não visível. Indicadores direcionais alertam um usuário para conteúdo importante e fornecem diretrizes para o conteúdo em relação à posição do usuário. As diretrizes para conteúdo não visível podem assumir a forma de emissores de som, setas direcionais ou missões visuais diretas.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  As responsabilidades visuais e de áudio orientam diretamente o usuário para conteúdo relevante fora do campo de exibição. | Uma seta ou algum indicador que aponta para o usuário na direção geral do conteúdo. | O conteúdo relevante está fora do campo de exibição e diretrizes de localização ruins ou não são fornecidas ao usuário. | 

### <a name="how-to-measure"></a>Como medir

* O conteúdo relevante fora do campo de exibição do usuário pode ser descoberto por meio de dicas visuais e/ou de áudio.

### <a name="recommendations"></a>Recomendações

* Quando o conteúdo relevante estiver fora do campo de exibição do usuário, use indicadores direcionais e missões de áudio para orientar o usuário para o conteúdo. Em muitos casos, um guia visual direto é preferencial em vez de setas direcionais.
* Indicadores direcionais não devem ser integrados ao cursor.

### <a name="resources"></a>Recursos

* [Quadro holográfico](../../design/holographic-frame.md)

## <a name="data-loading"></a>Carregamento de dados

Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento. Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar por quanto tempo o tempo de espera pode ser.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Encontra |  Falha |
--- | --- | ---
|  Indicador visual animado, na forma de uma barra de progresso ou anel, mostrando o progresso durante qualquer carregamento ou processamento de dados. O indicador visual fornece diretrizes sobre quanto tempo a espera pode ser. | O usuário é informado de que o carregamento de dados está em andamento, mas não há nenhuma indicação de quanto tempo a espera pode ser. | Nenhum carregamento de dados ou indicadores de processo para tarefa que demorando mais de 5 segundos. |

### <a name="how-to-measure"></a>Como medir

* Durante o carregamento de dados, verifique se não há nenhum estado em branco por mais de 5 segundos.

### <a name="recommendations"></a>Recomendações

* Forneça um animador de carregamento de dados mostrando o progresso em qualquer situação em que o usuário possa perceber que esse aplicativo está parado ou que parou. Uma regra razoável é qualquer atividade de 'carregamento' que pode levar mais de 5 segundos.

### <a name="resources"></a>Recursos

* [Exibindo o progresso](../../design/progress.md)