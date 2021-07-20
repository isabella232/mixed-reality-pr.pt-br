---
title: O que é Realidade Misturada?
description: Discussão sobre Realidade Misturada, demonstrando o uso de dispositivos AR e VR no espectro da Realidade Misturada.
author: qianw211
ms.author: v-qianwen
ms.date: 07/01/2021
ms.topic: article
keywords: Realidade Misturada, holográfico, AR, VR, MR, XR, realidade aumentada, realidade virtual, explicação, estudo de caso, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, o que é realidade virtual, o que é a realidade aumentada
ms.localizationpriority: high
ms.openlocfilehash: 088bc9a978bd236069ddc1beab40387c607b906e
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634317"
---
# <a name="what-is-mixed-reality"></a>O que é Realidade Misturada?

A realidade misturada é o próximo ciclo na computação, seguida por mainframes, PCs e smartphones. A realidade misturada vai se tornar popular entre consumidores e empresas.  Ela nos livra de experiências vinculadas à tela, oferecendo interações instintivas com os dados em nossos espaços de vida, entre nossas coisas e com nossos amigos.  Os exploradores online, em centenas de milhões em todo o mundo, experimentaram a realidade misturada por meio de dispositivos portáteis.  A RA móvel oferece as soluções de realidade misturada mais populares atualmente em mídias sociais. As pessoas podem nem perceber que os filtros de RA que usam no Instagram são experiências de Realidade Misturada.  O Microsoft Mixed Reality vai aprimorar todas essas experiências do usuário com uma combinação de representações holográficas realmente incríveis de pessoas, alta fidelidade de modelos 3D holográficos e o mundo real ao redor delas.

![Apontar e confirmar com as mãos no HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

A Realidade Misturada é uma combinação dos mundos físico e digital, revelando as interações naturais e intuitivas 3D entre humanos, computador e ambiente. Essa nova realidade se baseia em aprimoramentos na pesquisa visual computacional, no processamento gráfico, na tecnologia de vídeo, em sistemas de entrada e na computação em nuvem. O termo "Realidade Misturada" foi introduzido em um artigo de 1994 de Paul Milgram e Fumio Kishino intitulado "[Uma taxonomia das exibições visuais de realidade misturada](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)". Esse artigo explorou o conceito de um *continuum de virtualidade* e a taxonomia das exibições visuais. Desde então, o aplicativo de Realidade Misturada vai além dos monitores para incluir:

* Compreensão ambiental: mapeamento espacial e âncoras.
* Compreensão humana: rastreamento manual, rastreamento ocular e entrada de fala.
* Som espacial.
* Localizações e o posicionamento nos espaços real e virtual.
* Colaboração em ativos 3D em espaços de realidade misturada.

![A imagem do espectro da Realidade Misturada](images/mixedrealityspectrum-worlds.png)<br>
*Imagem: a Realidade Misturada é o resultado da combinação do mundo físico com o mundo digital.*

<br>

---

## <a name="environmental-input-and-perception"></a>Entrada e percepção do ambiente

Nas últimas décadas, a relação entre humanos e computadores continuou evoluindo por meio de métodos de entrada.  Uma nova disciplina surgiu, conhecida como interação humano-computador ou HCI. A entrada humana agora pode incluir teclados, mouses, dispositivos de toque, tinta, voz e rastreamento do esqueleto Kinect.

Os avanços nos sensores e na capacidade de processamento estão criando percepções computadorizadas de ambientes com base em métodos de entrada avançados. É por isso que os nomes de API no Windows que revelam informações do ambiente são chamados de [APIs de percepção](/uwp/api/Windows.Perception). As entradas ambientais podem capturar: 

* a posição do corpo de uma pessoa no mundo físico ([rastreamento da cabeça](../design/coordinate-systems.md)) 
* objetos, superfícies e limites ([mapeamento espacial](../design/spatial-mapping.md) e [compreensão de cena)](../design/scene-understanding.md) 
* iluminação e som ambiente
* reconhecimento de objetos
* localizações físicas

<br>

![Diagrama de Venn mostrando interações entre computadores, seres humanos e ambientes](images/mixed-reality-venn-diagram-300px.png)<br> 
*Imagem: as interações entre computadores, humanos e ambientes.*

<br>

Uma combinação dos três elementos essenciais define o estágio para criar experiências reais de Realidade Misturada:

* Processamento de computador alimentado pela nuvem
* Métodos de entrada avançados
* Percepções ambientais

Conforme nos movemos pelo mundo físico, nossos movimentos são mapeados em uma realidade digital. Os limites físicos influenciam experiências de realidade misturada no mundo digital, como jogos ou diretrizes baseadas em tarefas em uma instalação de fabricação. Com a entrada e as percepções ambientais, as experiências começam a se misturar entre as realidades física e digital.

<br>

---

## <a name="the-mixed-reality-spectrum"></a>O espectro da Realidade Misturada

A Realidade Misturada combina os mundos físico e digital.  Essas duas realidades marcam as extremidades polares de um espectro conhecido como o *continuum de virtualidade*. Nós nos referimos a esse espectro de realidades como o *espectro de Realidade Misturada*.  No final do espectro, temos a realidade física de que nós, como humanos, existimos. Na outra extremidade do espectro, temos a realidade digital correspondente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realidade aumentada versus virtual

A maioria dos celulares no mercado atualmente tem pouca ou nenhuma funcionalidade de percepção do ambiente. As experiências que esses celulares oferecem não podem misturar realidades físicas e digitais. 

As experiências que sobrepõem elementos gráficos, fluxos de vídeo ou hologramas no mundo físico são chamadas de "realidade aumentada". As experiências que ocultam sua exibição para apresentar uma experiência digital são uma realidade virtual. As experiências que podem fazer a transição entre a realidade aumentada e a virtual formam a Realidade Misturada, em que você pode:

* Colocar um objeto digital, como um holograma, no mundo físico, como se estivesse fisicamente presente.
* Estar pessoal e digitalmente presente no mundo físico, na forma de um avatar, para colaborar de maneira assíncrona com outras pessoas em diferentes pontos no tempo.
* Na realidade virtual, os limites físicos, como paredes e móveis, aparecem digitalmente dentro da experiência para que os usuários evitem se chocar com obstáculos físicos.

<br>

![O espectro da Realidade Misturada](images/mixedrealityspectrum.png)<br>
*Imagem: o espectro da Realidade Misturada*

<br>

Atualmente, a maioria das experiências de realidade aumentada e realidade virtual disponíveis representa subconjuntos do espectro maior da Realidade Misturada. O Windows 10 é criado com todo o espectro em mente e permite a combinação de representações digitais de pessoas, locais e coisas com o mundo real.

## <a name="devices-and-experiences"></a>Dispositivos e experiências

Há dois tipos principais de dispositivos que fornecem experiências do Windows Mixed Reality:
1. **Dispositivos holográficos** são caracterizados pela capacidade do dispositivo de colocar conteúdo digital no mundo real como se estivesse lá.
2. Os **dispositivos VR de imersão** são caracterizados pela capacidade do dispositivo de criar uma sensação de presença bloqueando o mundo físico e substituindo-o por uma experiência digital totalmente imersiva.

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
> O fato de um dispositivo estar vinculado a um computador separado (por cabo USB ou Wi-Fi) ou não vinculado não reflete se ele é holográfico ou imersivo. Recursos que aprimoram a mobilidade geralmente fornecem experiências melhores. Dispositivos holográficos e imersivos podem ser vinculados ou não vinculados.

As experiências de Realidade Misturada são o resultado de avanços tecnológicos. Atualmente, não há dispositivos que podem executar experiências em todo o espectro. O Windows 10 oferece uma plataforma comum de Realidade Misturada para fabricantes e desenvolvedores de dispositivos. Qualquer determinado dispositivo pode dar suporte a um intervalo específico dentro do espectro de Realidade Misturada. No futuro, novos dispositivos com intervalo mais expansivo são esperados: os dispositivos holográficos serão mais imersivos e os dispositivos imersivos serão mais holográficos.

<br>

![Tipos de dispositivo no espectro da Realidade Misturada](images/Final_WhatIsMixedReality07.png)<br>
*Imagem: local no qual os dispositivos existem no espectro da Realidade Misturada*

Como desenvolvedor de aplicativos ou jogos, que tipo de experiências você deseja criar? As experiências normalmente direcionarão uma parte ou ponto específico no espectro. Você precisará considerar as funcionalidades dos dispositivos a serem destinados. As experiências que dependerem do mundo físico serão melhor executadas no HoloLens.

* **Em direção à esquerda (perto da realidade física).** Os usuários permanecem presentes na realidade física deles e não são induzidos a acreditar que saíram dessa realidade.
* **No meio (Realidade totalmente Misturada).** Essas experiências combinam o mundo real e o mundo digital. Por exemplo, no filme [Jumanji](https://en.wikipedia.org/wiki/Jumanji), a estrutura física da casa em que a história ocorreu foi combinada com um ambiente de selva.
* **Em direção à direita (perto da realidade digital).** Os usuários experimentam uma realidade digital e não têm ciência da realidade física ao redor.

## <a name="next-discovery-checkpoint"></a>Próximo ponto de verificação de descoberta

Você está começando do [percurso de descoberta](get-started-with-mr.md) que criamos para você e explorando as noções básicas da Realidade Misturada. Desse ponto, você poderá prosseguir para o próximo tópico básico: 

> [!div class="nextstepaction"]
> [O que é um holograma?](hologram.md)
