---
title: Estudo de caso – Criando uma galaxy na realidade misturada
description: Saiba mais sobre o aplicativo "Galaxy Explorer" e como ele foi criado para o microsft HoloLens e após uma sondagem do Twitter de 24 horas por desenvolvedores da comunidade.
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, compartilhe sua ideia, estudo de caso
ms.openlocfilehash: 5891fbc052c52cd90176214d1eff8ef019a2bcfc80dbd5264489deced0fb1664
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208024"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Estudo de caso – Criando uma galaxy na realidade misturada

Antes Microsoft HoloLens ser enviado, perguntamos à nossa comunidade de desenvolvedores que tipo de aplicativo ele gostaria de ver um build de equipe interno experiente para o novo dispositivo. Mais de 5.000 ideias foram compartilhadas e, após uma sondagem do Twitter de 24 horas, o vencedor foi uma ideia chamada [Galaxy Explorer.](../develop/unity/galaxy-explorer.md)

Paulo Zibits, líder de arte no projeto, e Luccin, engenheiro gráfico da equipe, falam sobre o esforço colaborativo entre a arte e a engenharia que levou à criação de uma representação interativa precisa da galaxia Da Via Leite no Galaxy Explorer.

## <a name="the-tech"></a>A tecnologia

Nossa [equipe](../develop/unity/galaxy-explorer.md#meet-the-team) , que é de dois designers, três desenvolvedores, quatro artista, um produtor e um testador, tinha seis semanas para criar um aplicativo totalmente funcional que permitisse que as pessoas aprendesse e explorasse a grande e abilidade de nossa Galaxy Via Leite.

Queríamos aproveitar ao máximo a capacidade do HoloLens renderizar objetos 3D diretamente em seu espaço de vida, portanto, decidimos criar uma galaxia realista em que as pessoas seriam capazes de ampliar e ver estrelas individuais, cada uma em suas próprias perspectivas.

Na primeira semana de desenvolvimento, criamos algumas metas para nossa representação da Galaxy Via Leite: ela precisava ter profundidade, movimento e se sentir volumoso– cheia de estrelas que ajudariam a criar a forma da galaxia.

O problema com a criação de uma galaxia animada que tinha bilhões de estrelas era que o grande número de elementos individuais que precisam de atualização seria muito grande por quadro para HoloLens animar usando a CPU. Nossa solução envolve uma combinação complexa de arte e ciência.

## <a name="behind-the-scenes"></a>Nos bastidores

Para permitir que as pessoas explorem estrelas individuais, nossa primeira etapa foi descobrir quantas partículas poderíamos renderizar ao mesmo tempo.

### <a name="rendering-particles"></a>Renderizar partículas

As CPUs atuais são ótimas para processar tarefas seriais e até algumas tarefas paralelas de uma só vez (dependendo de quantos núcleos elas têm), mas as GPUs são muito mais eficazes no processamento de milhares de operações em paralelo. No entanto, como eles geralmente não compartilham a mesma memória que a CPU, a troca de dados entre a CPU<>GPU pode se tornar rapidamente um gargalo. Nossa solução era fazer uma galaxy na GPU e ela precisava residir completamente na GPU.

Começamos testes de estresse com milhares de partículas de ponto em vários padrões. Isso nos permitiu obter a galaxy no HoloLens para ver o que funcionou e o que não funcionou.

### <a name="creating-the-position-of-the-stars"></a>Criando a posição das estrelas

Um de nossos membros da equipe já escreveu o código C# que geraria estrelas em sua posição inicial. As estrelas estão em uma elipse e sua posição pode ser descrita por (**curveOffset**, **ellipseSize**, **elevação**) em **que curveOffset** é o ângulo da estrela ao longo da elipse, **ellipseSize** é a dimensão da elipse ao longo de X e Z e eleva a elevação adequada da estrela dentro da galaxia. Portanto, podemos criar um buffer ([ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)do Unity ) que seria inicializado com cada atributo de estrela e enviá-lo na GPU em que ele residiria para o restante da experiência. Para desenhar esse buffer, usamos [DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) do Unity, que permite executar um sombreador (código em uma GPU) em um conjunto arbitrário de pontos sem ter uma malha real que representa a galaxy:

**Cpu:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**Gpu:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Começamos com padrões circulares brutos com milhares de partículas. Isso nos deu a prova de que precisávamos de que poderíamos gerenciar muitas partículas E execute-as em velocidades de desempenho, mas não estávamos satisfeitos com a forma geral da galaxia. Para melhorar a forma, fizemos várias tentativas de padrões e sistemas de partículas com rotação. Inicialmente, eles eram promissores porque o número de partículas e o desempenho permaneceram consistentes, mas a forma se abaixou próximo ao centro e as estrelas estavam emitindo externamente, o que não era realista. Precisávamos de uma emissão que nos permitisse manipular o tempo e fazer com que as partículas se movem de forma realista, em loop cada vez mais próximo do centro da galaxia.

![Tentamos vários padrões e sistemas de partícula que giram, como estes.](images/galaxy-patterns-500px.png)

Tentamos vários padrões e sistemas de partícula que giram, como estes.

Nossa equipe pesquisou sobre a maneira como as coisas funcionam e fizemos um sistema de partícula personalizado especificamente para a galaxia, de modo que poderíamos mover as partículas em elipses com base na["](https://en.wikipedia.org/wiki/Density_wave_theory)teoria da onda de densidade ", que teoriza que os braços de uma galaxia são áreas de densidade mais alta, mas em fluxo constante, como um congestionamento de tráfego. Ele parece estável e sólido, mas as estrelas estão realmente se movendo para dentro e para fora dos braços conforme elas se movem ao longo de suas respectivas reellipses. Em nosso sistema, as partículas nunca existem na CPU– geramos os cartões e orientamos todos eles na GPU, portanto, todo o sistema é simplesmente o estado inicial + hora. Ele progride desta forma:

![Progressão do sistema de partículas com renderização de GPU](images/spiral-galaxy-arms-500px.jpg)

Progressão do sistema de partículas com renderização de GPU


Depois que as reellipses suficientes são adicionadas e são definidas para girar, as reações começaram a formar "braços" em que o movimento das estrelas converge. O espaçamento das estrelas ao longo de cada caminho elíptico recebeu alguma aleatoriedade e cada estrela foi adicionada um pouco de aleatoriedade posicional. Isso criou uma distribuição muito mais natural de movimento em estrela e forma de arm. Por fim, adicionamos a capacidade de impulsionar a cor com base na distância do centro.

### <a name="creating-the-motion-of-the-stars"></a>Criando o movimento das estrelas

Para animar o movimento em estrela geral, precisamos adicionar um ângulo constante para cada quadro e fazer com que as estrelas se movem ao longo de suas re elipses em uma velocidade radial constante. Esse é o principal motivo para usar **curveOffset.** Tecnicamente, isso não está correto, pois as estrelas se movem mais rapidamente ao longo dos lados longos das re elipses, mas o movimento geral foi bom.

![As estrelas se movem mais rapidamente no arco longo, mais lentamente nas bordas.](images/ellipse-movement.jpg)

As estrelas se movem mais rapidamente no arco longo, mais lentamente nas bordas.


Com isso, cada estrela é totalmente descrita por (**curveOffset**,  **elipseSize** **,** elevação , **Idade**) em que Idade é um acúmulo do tempo total passado desde que a cena foi carregada.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

Isso nos permitiu gerar dezenas de milhares de estrelas uma vez no início do aplicativo e, em seguida, animamos um único conjunto de estrelas ao longo das curvas estabelecidas. Como tudo está na GPU, o sistema pode animar todas as estrelas em paralelo sem custo para a CPU.

![Esta é a aparência dele ao desenhar quads em branco.](images/drawing-white-quads-300px.jpg)

Esta é a aparência dele ao desenhar quads em branco.



Para tornar cada quad face da câmera, utilizamos um sombreador de geometria para transformar cada posição de estrela em um retângulo 2D na tela que conterá nossa textura em estrela.

![Os títulos em vez de quads.](images/drawing-white-quads-300px.jpg)

Os títulos em vez de quads.


Como queríamos limitar o redesenhado (número de vezes que um pixel será processado) o máximo possível, giramos nossos quads para que eles tenham menos sobreposição.

### <a name="adding-clouds"></a>Adicionando nuvens

Há muitas maneiras de obter uma sensação volumosa com partículas– desde raios dentro de um volume até desenhar o máximo de partículas possíveis para simular uma nuvem. A criação de raios em tempo real seria muito cara e difícil de criar, portanto, primeiro tentamos criar um sistema de imposterização usando um método para renderizar florestas em jogos, com muitas imagens 2D de árvores voltadas para a câmera. Quando fazemos isso em um jogo, podemos ter texturas de árvores renderizadas de uma câmera que gira, salvar todas essas imagens e, em runtime, selecionar a imagem que corresponde à direção da exibição. Isso não funciona tão bem quando as imagens são hologramas. A diferença entre o olho esquerdo e o olho direito faz com que precisemos de uma resolução muito maior, ou então ele parece simples, com alias ou repetitivo.

Em nossa segunda tentativa, tentamos ter o máximo de partículas possível. Os melhores visuais foram obtidos quando extraímos as partículas aditivamente e as desfocados antes de adiá-las à cena. Os problemas típicos com essa abordagem estavam relacionados à quantidade de partículas que poderíamos desenhar em um único momento e à quantidade de área de tela que elas abordavam, mantendo ainda 60fps. Desfocar a imagem resultante para obter essa sensação de nuvem geralmente era uma operação muito cara.

![Sem textura, essa seria a aparência das nuvens com 2% de opacidade.](images/clouds-without-texture-300px.jpg)

Sem textura, essa seria a aparência das nuvens com 2% de opacidade.



Ser aditivo e ter muitos deles significa que teremos vários quads sobre si, sombreando repetidamente o mesmo pixel. No centro da galaxia, o mesmo pixel tem centenas de quads sobre si e isso tinha um custo enorme ao fazer a tela inteira.

Fazer nuvens de tela inteira e tentar desfocar essas nuvens seria uma má ideia, portanto, em vez disso, decidimos deixar o hardware fazer o trabalho para nós.

### <a name="a-bit-of-context-first"></a>Um pouco de contexto primeiro

Ao usar texturas em um jogo, o tamanho da textura raramente corresponderá à área em que desejamos usá-la, mas podemos usar diferentes tipos[](/previous-versions/visualstudio/visual-studio-2015/debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)de filtragem de textura para obter a placa gráfica para interpolar a cor que queremos dos pixels da textura (Filtragem de textura). A filtragem que nos interessa é a [filtragem bilinear](/windows/win32/direct3d9/bilinear-texture-filtering) que calculará o valor de qualquer pixel usando os quatro vizinhos mais próximos.

![Original antes da filtragem](images/texture-1.png)

![Resultado após a filtragem](images/texture-2.png)

Usando essa propriedade, vemos que sempre que tentamos desenhar uma textura em uma área duas vezes maior, ela desfoque o resultado.

Em vez de renderizar em uma tela inteira e perder esses milissegundos valiosos que poderíamos gastar em outra coisa, renderizamos para uma pequena versão da tela. Em seguida, copiando essa textura e alongando-a por um fator de 2 várias vezes, voltaremos à tela inteira enquanto desfoque o conteúdo no processo.

![X3 upscale de volta para resolução completa.](images/galaxy-resolutions-300px.png)

X3 upscale de volta para resolução completa.



Isso nos permitiu obter a parte da nuvem com apenas uma fração do custo original. Em vez de adicionar nuvens na resolução completa, pintamos apenas 1/64 dos pixels e apenas estendemos a textura de volta para a resolução completa.

![Esquerda, com um upscale de 1/8º para resolução completa; e à direita, com 3 de upscale usando a potência de 2.](images/stars-upscaled-300px.jpg)

Esquerda, com um upscale de 1/8º para resolução completa; e à direita, com 3 de upscale usando a potência de 2.


Observe que tentar passar de 1/64 do tamanho para o tamanho completo em uma só vez pareceria completamente diferente, pois a placa gráfica ainda usaria 4 pixels em nossa configuração para sombrear uma área maior e os artefatos começarão a aparecer.

Em seguida, se adicionarmos estrelas de resolução completa com cartões menores, obteremos a galaxia completa:

![Resultado quase final da renderização de galaxy usando estrelas de resolução completa](images/full-galaxy-500px.png)

Quando estávamos no caminho certo com a forma, adicionamos uma camada de nuvens, trocamos os pontos temporários por aqueles pintados no Photoshop e adicionamos alguma cor adicional. O resultado foi uma Galaxy Via Leitena que nossas equipes de engenharia e arte se sentiram bem e atendeu às nossas metas de profundidade, volume e movimento, tudo isso sem taxar a CPU.

![Nossa galaxia da Via Leite final em 3D.](images/final-galaxy-500px.jpg)

Nossa galaxia da Via Leite final em 3D.


### <a name="more-to-explore"></a>Mais para explorar

Disponibilizamos o código de software livre para o aplicativo Galaxy [](https://github.com/Microsoft/GalaxyExplorer) Explorer e o disponibilizamos no GitHub para os desenvolvedores se basearem.

Está interessado em saber mais sobre o processo de desenvolvimento do Galaxy Explorer? Confira todas as nossas atualizações de projeto anteriores no [canal Microsoft HoloLens YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).

## <a name="about-the-authors"></a>Sobre os autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Luccin</b> é um engenheiro de software e engenheiro de visuais sofisticados. Ele era engenheiro gráfico do Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Paulo Zibits</b> é um líder de arte e um entusiado espacial que gerenciava a equipe de modelagem 3D do Galaxy Explorer e buscava ainda mais partículas.</td>
</tr>
</table>


## <a name="see-also"></a>Confira também
* [Galaxy Explorer no GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Atualizações de projeto do Galaxy Explorer no YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)