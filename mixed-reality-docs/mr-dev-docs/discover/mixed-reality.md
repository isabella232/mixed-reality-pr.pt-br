---
title: O que é Realidade Misturada?
description: Discussão sobre Realidade Misturada, demonstrando o uso de dispositivos AR e VR no espectro da Realidade Misturada.
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: Realidade Misturada, holográfico, AR, VR, MR, XR, realidade aumentada, realidade virtual, explicação, estudo de caso, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, o que é realidade virtual, o que é a realidade aumentada
ms.localizationpriority: high
ms.openlocfilehash: e524312b2e479b1c3d05039403aba10de864ae18
ms.sourcegitcommit: 5603dc9f6511707cb8b215f20f6c6485ef480538
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2021
ms.locfileid: "112230207"
---
# <a name="what-is-mixed-reality"></a>O que é Realidade Misturada?

![Apontar e confirmar com as mãos no HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

A Realidade Misturada é uma combinação dos mundos físico e digital, revelando os vínculos entre a interação entre humano, computador e ambiente. Essa nova realidade se baseia em aprimoramentos na pesquisa visual computacional, na capacidade de processamento gráfico, na tecnologia de vídeo e em sistemas de entrada. Contudo, o termo *Realidade Misturada* foi introduzido em um artigo de 1994 de Paul Milgram e Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)". Esse artigo explorou o conceito de *continuum de virtualização* e a categorização de taxonomia aplicada a monitores. Desde então, o aplicativo de Realidade Misturada vai além dos monitores para incluir:
* Entrada ambiental
* som espacial
* Locais e posicionamento nos espaços real e virtual

![A imagem do espectro da Realidade Misturada](images/mixedrealityspectrum-worlds.png)<br>
*Imagem: a Realidade Misturada é o resultado da combinação do mundo físico com o mundo digital.*

<br>

---

## <a name="environmental-input-and-perception"></a>Entrada e percepção do ambiente

Nas últimas décadas, a exploração da relação entre a entrada humana e a do computador continuou, levando à disciplina conhecida como *HCI* ou interação entre humanos e computadores. A entrada humana acontece por meio de diferentes meios, incluindo teclados, mouses, toque, tinta, voz e até mesmo controle estrutural Kinect.

Os avanços nos sensores e no processamento estão criando áreas de entrada do computador em ambientes. A interação entre computadores e ambientes é a compreensão ou a *percepção* ambiental, motivo pelo qual os nomes de API no Windows que revelam informações ambientais são chamados de [APIs de percepção](/uwp/api/Windows.Perception). A entrada do ambiente captura aspectos como a posição de uma pessoa no mundo ([acompanhamento de cabeça](../design/coordinate-systems.md)), superfícies e limites ([mapeamento espacial](../design/spatial-mapping.md) e [reconhecimento de cena](../design/scene-understanding.md)), iluminação do ambiente, som do ambiente, reconhecimento de objetos e localização.

<br>

![Diagrama de Venn mostrando interações entre computadores, seres humanos e ambientes](images/mixed-reality-venn-diagram-300px.png)<br> 
*Imagem: as interações entre computadores, humanos e ambientes.*

<br>

A combinação de todos os três – **processamento do computador, entrada humana e entrada do ambiente** – prepara a criação de experiências de Realidade Misturada verdadeiras. A movimentação no mundo físico é convertida em movimentação no mundo digital. Os limites no mundo físico influenciam as experiências de aplicativos, como jogos, no mundo digital. Sem a entrada do ambiente, as experiências não podem ser combinadas entre realidades físicas e digitais.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>O espectro da Realidade Misturada

Como a Realidade Misturada combina mundos físicos e digitais, elas definem as extremidades polares de um espectro conhecido como o continuum de virtualização. Nós nos referimos à matriz de realidades como o *espectro de Realidade Misturada*. No lado esquerdo, temos a realidade física na qual nós, como humanos, existimos. No lado direito, temos a realidade digital correspondente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realidade aumentada versus virtual

A maioria dos celulares no mercado atualmente tem pouca ou nenhuma funcionalidade de noção do ambiente. As experiências que eles oferecem não podem misturar realidades físicas e digitais. As experiências que sobrepõem elementos gráficos em fluxos de vídeo do mundo físico são *realidade aumentada*. As experiências que ocultam sua exibição para apresentar uma experiência digital são *realidade virtual*. As experiências habilitadas entre a realidade aumentada e virtual formam a *Realidade Misturada*:
* Com base no mundo físico, colocando um objeto digital, como um holograma, como se ele estivesse lá.
* Com base no mundo físico, uma representação digital de outra pessoa – um avatar – mostra o local em que ela estava quando deixou anotações. Em outras palavras, as experiências que representam a colaboração assíncrona em diferentes pontos no tempo.
* Partindo de um mundo digital, os limites físicos do mundo físico, como paredes e móveis, são exibidos digitalmente dentro da experiência para ajudar os usuários a evitar objetos físicos.

<br>

![O espectro da Realidade Misturada](images/mixedrealityspectrum.png)<br>
*Imagem: o espectro da Realidade Misturada*

<br>

Atualmente, a maioria das ofertas de realidade aumentada e realidade virtual disponíveis representa uma parte pequena desse espectro e elas são consideradas subconjuntos do espectro maior da Realidade Misturada. O Windows 10 é criado com todo o espectro em mente e permite a combinação de representações digitais de pessoas, locais e coisas com o mundo real.


## <a name="devices-and-experiences"></a>Dispositivos e experiências

Há dois tipos principais de dispositivos que fornecem experiências do Windows Mixed Reality:
1. **Dispositivos holográficos** são caracterizados pela capacidade do dispositivo de colocar conteúdo digital no mundo real como se estivesse lá.
2. **Dispositivos de imersão** são caracterizados pela capacidade do dispositivo de criar uma sensação de “presença”, ocultando o mundo físico e substituindo-o por uma experiência digital.

<table>
<tr>
<th width="30%"> Característica</th><th width="35%"> Dispositivos holográficos</th><th width="35%"> Dispositivos imersivos</th>
</tr><tr>
<td><strong>Dispositivo de exemplo</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Exibição</strong></td><td> Monitor transparente. Permite que o usuário veja o ambiente físico ao usar o headset.</td><td> Monitor opaco. Bloqueia o ambiente físico ao usar o headset.</td>
</tr><tr>
<td><strong>Movimentação</strong></td><td> Movimentação completa de seis graus de liberdade, rotação e conversão.</td><td> Movimentação completa de seis graus de liberdade, rotação e conversão.</td>
</tr>
</table> 


> [!NOTE]
> O fato de um dispositivo estar conectado ou vinculado a um computador separado (por cabo USB ou Wi-Fi) ou ser autônomo (não conectado) não reflete se ele é holográfico ou imersivo. Certamente, os recursos que aprimoram a mobilidade produzem melhores experiências, e os dispositivos holográficos e de imersão podem estar conectados ou não.

O avanço tecnológico permite experiências de Realidade Misturada, mas não há dispositivos atualmente que possam executar experiências em todo o espectro. O Windows 10 oferece uma plataforma comum de Realidade Misturada para fabricantes e desenvolvedores de dispositivos. Atualmente, os dispositivos podem dar suporte a um intervalo específico dentro do espectro de Realidade Misturada, com novos dispositivos expandindo esse intervalo. No futuro, os dispositivos holográficos serão mais imersivos, e os dispositivos imersivos serão mais holográficos.

<br>

![Tipos de dispositivo no espectro da Realidade Misturada](images/Final_WhatIsMixedReality07.png)<br>
*Imagem: local no qual os dispositivos existem no espectro da Realidade Misturada*

É melhor considerar qual tipo de experiência um desenvolvedor de aplicativo ou jogo deseja criar. As experiências normalmente direcionarão uma parte ou ponto específico no espectro. Os desenvolvedores devem considerar as funcionalidades dos dispositivos que desejam direcionar. As experiências que dependerem do mundo físico serão melhor executadas no HoloLens.
* **Em direção à esquerda (perto da realidade física).** Os usuários permanecem presentes no ambiente físico deles e nunca são induzidos a acreditar que saíram desse ambiente.
* **No meio (Realidade totalmente Misturada).** Essas experiências combinam o mundo real e o mundo digital. Os espectadores que viram o filme [Jumanji](https://en.wikipedia.org/wiki/Jumanji) podem reconciliar como a estrutura física da casa em que a história ocorreu foi combinada com um ambiente de selva.
* **Em direção à direita (perto da realidade digital).** Os usuários experimentam um ambiente digital e não sabem o que ocorre no ambiente físico ao redor deles.

## <a name="next-discovery-checkpoint"></a>Próximo ponto de verificação de descoberta

Se estiver seguindo a [jornada de descoberta](get-started-with-mr.md) que apresentamos, você estará no meio da exploração dos fundamentos da Realidade Misturada. Desse ponto, você poderá prosseguir para o próximo tópico básico: 

> [!div class="nextstepaction"]
> [O que é um holograma?](hologram.md)
