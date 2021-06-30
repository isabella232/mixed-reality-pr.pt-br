---
title: Estabilidade do holograma
description: O HoloLens estabiliza automaticamente hologramas, mas há etapas que os desenvolvedores podem seguir para melhorar ainda mais a estabilidade do holograma.
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: hologramas, estabilidade, hololens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, taxa de quadros, renderização, reprodução, separação de cores
appliesto:
- HoloLens
ms.openlocfilehash: a4a22221d3238bb7dfed711e6ee1f11edc70238e
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042287"
---
# <a name="hologram-stability"></a>Estabilidade do holograma

Para alcançar hologramas estáveis, o HoloLens tem um pipeline de estabilização de imagem integrado. O pipeline de estabilização funciona automaticamente em segundo plano, portanto, você não precisa seguir nenhuma etapa adicional para habilita-lo. No entanto, você deve exercício de técnicas que melhoram a estabilidade do holograma e evitam cenários que reduzem a estabilidade.

## <a name="hologram-quality-terminology"></a>Terminologia de qualidade do holograma

A qualidade dos hologramas é resultado de um bom ambiente e bom desenvolvimento de aplicativos. Aplicativos em execução em uma constante de 60 quadros por segundo em um ambiente em que o HoloLens pode acompanhar o ambiente garante que o holograma e o sistema de coordenadas correspondentes estão em sincronia. Da perspectiva de um usuário, os hologramas que devem ser estacionários não serão movimentados em relação ao ambiente.

A terminologia a seguir pode ajudá-lo ao identificar problemas com o ambiente, taxas de renderização inconsistentes ou baixas ou qualquer outra coisa.
* **Precisão.** Depois que o holograma é bloqueado e colocado no mundo real, ele deve permanecer onde está colocado em relação ao ambiente ao redor e independentemente do movimento do usuário ou alterações de ambiente pequenas e esparsas. Se um holograma aparecer posteriormente em um local inesperado, será um problema *de precisão.* Esses cenários poderão ocorrer se duas salas distintas parecer idênticas.
* **Jitter.** Os usuários observam trem tremulações como uma grande frequência de um holograma, o que pode acontecer quando o acompanhamento do ambiente degrada. Para usuários, a solução está executando o [ajuste do sensor](/hololens/hololens-updates).
* **Trepidação.** Frequências de renderização baixas resultam em movimento irregular e imagens duplas de hologramas. O Hologramer é especialmente perceptível em hologramas com movimento. Os desenvolvedores precisam manter uma [constante de 60 FPS.](hologram-stability.md#frame-rate)
* **Deriva.** Os usuários veem o desmando como um holograma parece se mover para fora do local em que foi originalmente colocado. O desacordo ocorre quando você coloca os hologramas longe das [âncoras espaciais,](../../design/spatial-anchors.md)especialmente em partes não mapeadas do ambiente. Criar hologramas próximos a âncoras espaciais reduz a probabilidade de desacordo.
* **Jumpiness.** Quando um holograma "aparece" ou "salta" para fora de seu local ocasionalmente. A preparação pode ocorrer à medida que o acompanhamento ajusta os hologramas para corresponder à compreensão atualizada do seu ambiente.
* **Nadar.** Quando um holograma parece estar em movimento correspondente ao movimento da cabeça do usuário. O nada ocorre quando o aplicativo não implementou totalmente [a reprojetação](hologram-stability.md#reprojection)e se o HoloLens não está [calibrado](/hololens/hololens-calibration) para o usuário atual. O usuário pode reprisar o [aplicativo de calibragem](/hololens/hololens-calibration) para corrigir o problema. Os desenvolvedores podem atualizar o plano de estabilização para aprimorar ainda mais a estabilidade.
* **Separação de cores.** As exibições no HoloLens são exibições sequenciais de cores, que piscam canais de cores vermelho-verde-azul-verde a 60 Hz (campos de cor individuais são mostrados a 240 Hz). Sempre que um usuário rastreia um holograma móvel com os olhos, as bordas à frente e à parte inferior do holograma são separadas em suas cores constituintes, produzindo um efeito de arco. O grau de separação depende da velocidade do holograma. Em alguns casos mais raros, mover a cabeça deles rapidamente ao olhar para um holograma estacionário também pode resultar em um efeito de arco, que é chamado de *[separação de cores.](hologram-stability.md#color-separation)*

## <a name="frame-rate"></a>Taxa de quadros

A taxa de quadros é o primeiro pilar da estabilidade do holograma. Para que os hologramas pareçam estáveis no mundo, cada imagem apresentada ao usuário deve ter os hologramas desenhados no ponto correto. O é exibido na atualização do HoloLens 240 vezes por segundo, mostrando quatro campos de cores separados para cada imagem renderizada recentemente, resultando em uma experiência do usuário de 60 FPS (quadros por segundo). Para fornecer a melhor experiência possível, os desenvolvedores de aplicativos devem manter 60 FPS, o que se traduz em fornecer consistentemente uma nova imagem para o sistema operacional a cada 16 milissegundos.

**60 FPS** Para desenhar hologramas para parecer que estão no mundo real, o HoloLens precisa renderizar imagens da posição do usuário. Como a renderização de imagem leva tempo, o HoloLens prevê onde a cabeça do usuário estará quando as imagens são mostradas nas exibições. No entanto, esse algoritmo de previsão é uma aproximação. O HoloLens tem hardware que ajusta a imagem renderizada para levar em conta a discrepância entre a posição de cabeça prevista e a posição real da cabeça. O ajuste faz com que a imagem que o usuário vê apareça como se fosse renderizada do local correto e os hologramas se sintam estáveis. As atualizações de imagem funcionam melhor com pequenas alterações e não podem corrigir completamente certas coisas na imagem renderizada, como motion-parallax.

Ao renderizar em 60 FPS, você está fazendo três coisas para ajudar a tornar hologramas estáveis:
1. Minimizar a latência geral entre renderizar uma imagem e essa imagem que está sendo vista pelo usuário. Em um mecanismo com um jogo e um thread de renderização em execução em lockstep, a execução a 30FPS pode adicionar 33,3 ms de latência extra. Reduzir a latência diminui o erro de previsão e aumenta a estabilidade do holograma.
2. Tornando-o para que cada imagem que alcance os olhos do usuário tenha uma quantidade consistente de latência. Se você renderizar a 30 fps, a exibição ainda exibirá imagens a 60 FPS, o que significa que a mesma imagem será exibida duas vezes em uma linha. O segundo quadro terá 16,6 ms de latência maior do que o primeiro quadro e terá que corrigir uma quantidade mais pronunciada de erro. Essa inconsistência na magnitude do erro pode causar 60 Hz indesejados.
3. Reduzir a aparência de trepidação, que é caracterizada pelo movimento irregular e por imagens duplas. Um movimento mais rápido do holograma e taxas de renderização mais baixas estão associados a uma trepidação mais acentuada. Tentar manter 60 FPS o tempo todo ajudará a evitar o uso de um holograma móvel determinado.

**Consistência da taxa de quadros** A consistência da taxa de quadros é tão importante quanto um quadro alto por segundo. Ocasionalmente, quadros descartados são inevitáveis para qualquer aplicativo com conteúdo avançado e o HoloLens implementa alguns algoritmos sofisticados para se recuperar de falhas ocasionais. No entanto, uma taxa de quadros constantemente flutuante é muito mais perceptível para um usuário do que executar consistentemente com taxas de quadros menores. Por exemplo, um aplicativo que renderiza suavemente para cinco quadros (60 FPS durante esses cinco quadros) e, em seguida, descarta todos os outros quadros para os próximos 10 quadros (30 FPS durante esses 10 quadros) aparecerá mais instável do que um aplicativo que renderiza consistentemente em 30 FPS.

Em uma observação relacionada, o sistema operacional reduz os aplicativos para 30 FPS quando a captura [de realidade misturada](/hololens/holographic-photos-and-videos) está em execução.

**Análise de desempenho** Há diferentes tipos de ferramentas que podem ser usadas para fazer o parâmetro de comparação da taxa de quadros do aplicativo, como:
* GPUView
* Depurador de Gráficos do Visual Studio
* Profilers integrados a mecanismos 3D, como o Unity

## <a name="hologram-render-distances"></a>Distâncias de renderização do holograma

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

O sistema visual humano integra vários sinais dependentes de distância quando ele fixa e se concentra em um objeto .
* [Acomodação](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) – o foco de um olho individual.
* [Convergência](https://en.wikipedia.org/wiki/Convergence_(eye)) – dois olhos se movendo para dentro ou para fora para o centro em um objeto .
* [Visão visionária](https://en.wikipedia.org/wiki/Stereopsis) – disparidades entre as imagens esquerda e direita que dependem da distância de um objeto do ponto de fixação.
* Sombreamento, tamanho angular relativo e outras dicas monocular (olho único).

A convergência e a acomodação são exclusivas porque suas responsabilidades extratinais relacionadas a como os olhos mudam para perceber objetos a distâncias diferentes. Na exibição natural, a convergência e a acomodação são vinculadas. Quando os olhos visualizam algo próximo (por exemplo, seu nariz), os olhos se cruzam e acomodam a um ponto próximo. Quando os olhos visualizam algo no infinito, os olhos se tornam paralelos e o olho se acomoda ao infinito. 

Os usuários que usam o HoloLens sempre se acomodarão a 2,0 m para manter uma imagem clara, pois as exibições do HoloLens são fixas a uma distância óptica de aproximadamente 2,0 m do usuário. Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergem colocando conteúdo e hologramas em várias profundidades. Quando os usuários acomodam e convergem para distâncias diferentes, o vínculo natural entre as duas responsabilidades é desfeito, o que pode levar a estresse visual ou estresse, especialmente quando a magnitude do conflito é grande. 

O medo do conflito de acomodação-de-veracidade pode ser evitado ou minimizado mantendo o conteúdo convergido o mais próximo possível de 2,0 m (ou seja, em uma cena com muita profundidade, coloque as áreas de interesse próximas de 2,0 m, quando possível). Quando o conteúdo não pode ser colocado perto de 2,0 m, o medo do conflito de acomodação-de-veracidade é maior quando o olhar do usuário entre diferentes distâncias. Em outras palavras, é muito mais confortável olhar para um holograma fixo a 50 cm de distância do que para um holograma a 50 cm que se move para frente e para longe de você com o tempo.

Colocar o conteúdo a 2,0 m também é vantajoso porque as duas exibições são projetadas para se sobrepor totalmente a essa distância. Para imagens colocadas fora desse plano, conforme elas se movem para fora do lado do quadro holográfico, elas aparecerão de uma exibição enquanto ainda estão visíveis na outra. Essa consulta pode ser uma interrupção na percepção de profundidade do holograma.

**Distância ideal para colocação dos hologramas partindo do usuário**

![Distância ideal para colocação dos hologramas partindo do usuário](images/distanceguiderendering-750px.png)

**Planos de clipe** Para o máximo de conforto, recomendamos a distância de renderização de recorte em 85 cm com o esmaeçamento do conteúdo começando em 1 m. Em aplicativos em que os hologramas e os usuários são estacionários, os hologramas podem ser exibidos de maneira confortável até 50 cm. Nesses casos, os aplicativos devem colocar um plano de clipes não mais próximo de 30 cm e esmaecer devem iniciar pelo menos 10 cm de distância do plano de clipe. Sempre que o conteúdo estiver mais próximo de 85 cm, é importante garantir que os usuários não se movam com frequência mais próximos ou mais distantes dos hologramas ou que os hologramas não se movam com frequência para mais perto ou para mais longe do usuário, pois essas situações têm maior probabilidade de causar o ressarquite do conflito de acomodação de verão. O conteúdo deve ser projetado para minimizar a necessidade de interação mais próxima de 85 cm do usuário, mas quando o conteúdo deve ser renderizado mais próximo de 85 cm, uma boa regra geral para os desenvolvedores é projetar cenários em que usuários e/ou hologramas não se movem em profundidade mais de 25% do tempo.

**Práticas recomendadas** Quando os hologramas não podem ser colocados a 2 m e conflitos entre convergência e acomodação não podem ser evitados, a zona ideal para o posicionamento do holograma está entre 1,25 m e 5 m. Em todos os casos, os designers devem estruturar o conteúdo para incentivar os usuários a interagir a mais de 1 m de distância (por exemplo, ajustar o tamanho do conteúdo e os parâmetros de posicionamento padrão).

## <a name="reprojection"></a>Reprojetação
O HoloLens tem uma técnica sofisticada de estabilização holográfica assistida por hardware conhecida como reprojeção. A reprojeção leva em conta o movimento e a alteração do ponto de vista (CameraPose) à medida que a cena é animada e o usuário move a cabeça.  Os aplicativos precisam tomar ações específicas para melhor utilização da Reprojeção.


Há quatro tipos principais de Reprojeção
* **Reprojeção de profundidade:**  Produz os melhores resultados com a menor quantidade de esforço do aplicativo.  Todas as partes da cena renderizada são estabilizadas independentemente com base em sua distância do usuário.  Alguns artefatos de renderização podem estar visíveis onde há alterações nítidas em profundidade.  Essa opção só está disponível em headsets 2 e de imersão.
* **Reprojeção do planar:**  Permite o controle preciso do aplicativo sobre estabilização.  Um plano é definido pelo aplicativo e tudo nesse plano será a parte mais estável da cena.  Quanto mais um holograma estiver longe do plano, menos estável será.  Essa opção está disponível em todas as plataformas do Windows MR.
* **Reprojeção automática de planar:**  O sistema define um plano de estabilização usando informações no buffer de profundidade.  Essa opção está disponível no HoloLens geração 1 e no HoloLens 2.
* **Nenhum:** Se o aplicativo não faz nada, a Reprojeção do planar é usada com o plano de estabilização fixo em 2 metros na direção do olhar da cabeça do usuário, normalmente produzindo resultados de subpadrão.

Os aplicativos precisam executar ações específicas para habilitar os diferentes tipos de Reprojeção
* **Reprojeção de profundidade:** O aplicativo envia seu buffer de profundidade ao sistema para cada quadro renderizado.  No Unity, a Reprojeção de profundidade é feita com a opção de **buffer de profundidade compartilhada** no painel de **configurações de realidade mista do Windows** em **XR plugin Management**.  Aplicativos DirectX chamam CommitDirect3D11DepthBuffer.  O aplicativo não deve chamar SetFocusPoint.
* **Reprojeção do planar:** Em todos os quadros, os aplicativos informam ao sistema o local de um plano a ser estabilizado.  Os aplicativos do Unity chamam SetFocusPointForFrame e devem ter o **buffer de profundidade compartilhado** desabilitado.  Os aplicativos DirectX chamam SetFocusPoint e não devem chamar CommitDirect3D11DepthBuffer.
* **Reprojeção automática de planar:** Para habilitar o, o aplicativo precisa enviar seu buffer de profundidade ao sistema como faria para a Reprojeção de profundidade. Os aplicativos que usam o MRTK (Kit de ferramentas de realidade misturada) podem configurar o [provedor de configurações da câmera](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) para usar a Reprojeção do autoplanar. Aplicativos nativos devem definir o `DepthReprojectionMode` no [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) para `AutoPlanar` cada quadro. Para o HoloLens geração 1, o aplicativo não deve chamar SetFocusPoint.

### <a name="choosing-reprojection-technique"></a>Escolhendo a técnica de Reprojeção

Tipo de estabilização |    Headsets imersivos |    Geração de HoloLens 1 | HoloLens 2
--- | --- | --- | ---
Reprojeção de profundidade |    Recomendado |   N/D |   Recomendado<br/><br/>Os aplicativos do Unity devem usar o Unity 2018.4.12 +, Unity 2019.3 + ou Unity 2020.3 +. Caso contrário, use a Reprojeção automática de planar.
Reprojeção automática de planar | N/D |   Padrão recomendado |   Recomendado se a Reprojeção de profundidade não fornecer os melhores resultados<br/><br/>Os aplicativos do Unity são recomendados para usar o Unity 2018.4.12 +, Unity 2019.3 + ou Unity 2020.3 +.  As versões anteriores do Unity funcionarão com resultados de Reprojeção ligeiramente degradados.
Reprojeção do planar |   Não recomendado |   Recomendado se o planar automático não fornecer os melhores resultados | Use se nenhuma das opções de profundidade fornecer os resultados desejados    

### <a name="verifying-depth-is-set-correctly"></a>A verificação de profundidade está definida corretamente
            
Quando um método de Reprojeção usa o buffer de profundidade, é importante verificar se o conteúdo do buffer de profundidade representa a cena renderizada do aplicativo.  Vários fatores podem causar problemas. Se houver uma segunda câmera usada para renderizar sobreposições de interface do usuário, por exemplo, é provável que seja possível substituir todas as informações de profundidade da exibição real.  Objetos transparentes geralmente não definem profundidade.  Uma renderização de texto não definirá profundidade por padrão.  Haverá problemas visíveis na renderização quando a profundidade não corresponder aos hologramas renderizados.
            
O HoloLens 2 tem um visualizador para mostrar onde a profundidade está e não está sendo definida, que pode ser habilitada no portal do dispositivo.  Na guia estabilidade do holograma das **exibições**  >   , marque a caixa de seleção **Exibir visualização de profundidade no headset** .  As áreas que têm profundidade definida corretamente serão azuis.  Itens renderizados que não têm profundidade definida são marcados em vermelho e precisam ser corrigidos.  

> [!NOTE]
> A visualização da profundidade não aparecerá na captura de realidade misturada.  Ele só é visível por meio do dispositivo.
            
Algumas ferramentas de exibição de GPU permitirão a visualização do buffer de profundidade.  Os desenvolvedores de aplicativos podem usar essas ferramentas para garantir que a profundidade esteja sendo definida corretamente.  Consulte a documentação para obter as ferramentas do aplicativo.

### <a name="using-planar-reprojection"></a>Usando a Reprojeção do planar
> [!NOTE]
> Para headsets de imersão de área de trabalho, a definição de um plano de estabilização geralmente é produtiva, pois oferece menos qualidade visual do que fornecer o buffer de profundidade do seu aplicativo ao sistema para habilitar a Reprojeção baseada em profundidade por pixel. A menos que seja executado em um HoloLens, geralmente você deve evitar definir o plano de estabilização.

![Plano de estabilização para objetos 3D](images/stab-plane-500px.jpg)

O dispositivo tentará escolher este plano automaticamente, mas o aplicativo deve ajudar selecionando o ponto de foco na cena. Os aplicativos do Unity em execução em um HoloLens devem escolher o melhor ponto de foco com base em sua cena e passá-lo para [SetFocusPoint ()](../unity/focus-point-in-unity.md). Um exemplo de configuração do ponto de foco no DirectX está incluído no modelo de cubo padrão de rotação.

O Unity enviará seu buffer de profundidade ao Windows para habilitar a Reprojeção por pixel quando você executar seu aplicativo em um headset de imersão conectado a um PC desktop, que fornece uma qualidade de imagem ainda melhor sem trabalho explícito pelo aplicativo. Você só deve fornecer um ponto de foco quando seu aplicativo estiver em execução em um HoloLens ou a Reprojeção por pixel será substituída.


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

O posicionamento do ponto de foco em grande parte depende do que o holograma está olhando. O aplicativo tem o vetor olhar para referência e o designer de aplicativo sabe qual conteúdo ele deseja que o usuário observe.

A única coisa mais importante que um desenvolvedor pode fazer para estabilizar os hologramas é renderizar em 60 FPS. Soltar abaixo de 60 FPS reduzirá drasticamente a estabilidade do holograma, seja qual for a otimização do plano de estabilização.

**Práticas recomendadas** Não há uma maneira universal de configurar o plano de estabilização e ele é específico do aplicativo. Nossa principal recomendação é experimentar e ver o que funciona melhor para seu cenário. No entanto, tente alinhar o plano de estabilização com o máximo de conteúdo possível, pois todo o conteúdo desse plano é perfeitamente estabilizado.

Por exemplo:
* Se você tiver apenas conteúdo planar (leitura de aplicativo, aplicativo de reprodução de vídeo), alinhe o plano de estabilização com o plano que tem seu conteúdo.
* Se houver três pequenas que estão bloqueadas pelo mundo, torne o plano de estabilização "recortar", embora os centros de todas as suas interações que estão atualmente na exibição do usuário.
* Se sua cena tiver conteúdo em profundidades consideravelmente diferentes, favoreça mais objetos.
* Certifique-se de ajustar o ponto de estabilização a cada quadro para coincidir com o holograma que o usuário está olhando

**Itens a serem evitados** O plano de estabilização é uma excelente ferramenta para atingir hologramas estáveis, mas se for usado incorretamente, isso poderá resultar em instabilidade de imagem grave.
* Não "dispare e esqueça". Você pode terminar com o plano de estabilização por trás do usuário ou anexado a um objeto que não está mais no modo de exibição do usuário. Verifique se o plano de estabilização normal está definido para frente de câmera oposta (por exemplo,-Camera. Forward)
* Não altere rapidamente o plano de estabilização entre extrema e frente
* Não deixe o plano de estabilização definido para uma distância/orientação fixa
* Não deixe o plano de estabilização ser cortado pelo usuário
* Não defina o ponto de foco ao executar em um computador desktop em vez de um HoloLens e, em vez disso, confie na Reprojeção baseada em profundidade por pixel.

## <a name="color-separation"></a>Separação de cores 

Devido à natureza de exibições do HoloLens, um artefato chamado "separação de cores" pode, às vezes, ser percebido. Ele se manifesta como a imagem que separa em cores de base individuais – vermelho, verde e azul. O artefato pode ser especialmente visível ao exibir objetos brancos, pois eles têm grandes quantidades de vermelho, verde e azul. É mais pronunciado quando um usuário rastreia visualmente um holograma que está se movendo pelo quadro Holographic em alta velocidade. Outra maneira de o artefato ser manifestar é a distorção/desformação de objetos. Se um objeto tiver cores de alto contraste e/ou puras, como vermelho, verde, azul, a separação de cores será percebida como deformação de partes diferentes do objeto.

**Um exemplo de qual é a separação de cores de um cursor redondo branco de cabeçalho e arredondado como um usuário gira sua cabeça para o lado:**

![Um exemplo de qual é a separação de cores de um cursor redondo branco de cabeçalho de cabeça como um usuário gira sua cabeça para o lado.](images/colorseparationofroundwhitecursor-300px.png)

Embora seja difícil evitar completamente a separação de cores, há várias técnicas disponíveis para atenuá-la.

**A separação de cores pode ser vista em:**
* Objetos que estão se movendo rapidamente, incluindo objetos com a cabeça bloqueada, como o [cursor](../../design/cursors.md).
* Objetos que estão substancialmente longe do plano [de estabilização](hologram-stability.md#reprojection).

**Para atenuar os efeitos da separação de cores:**
* Faça com que o objeto atrase o olhar do usuário. Ele deve aparecer como se tivesse alguma inércia e estivesse anexado ao olhar "na chuva". Essa abordagem retarda o cursor (reduzindo a distância de separação) e o coloca atrás do ponto de vista provável do usuário. Desde que ele seja rapidamente catch up quando o usuário parar de mudar o foco, parece natural.
* Se você quiser mover um holograma, tente manter sua velocidade de movimento abaixo de 5 graus/segundo se você espera que o usuário a siga com os olhos.
* Use *luz* em vez *de geometria* para o cursor. Uma fonte de iluminação virtual anexada ao olhar será percebida como um ponteiro interativo, mas não causará separação de cores.
* Ajuste o plano de estabilização para corresponder aos hologramas em que o usuário está olhando.
* Tornar o objeto vermelho, verde ou azul.
* Alternar para uma versão desfocado do conteúdo. Por exemplo, um cursor branco arredondado pode ser alterado para uma linha ligeiramente desfoque orientada na direção do movimento.

Como antes, renderizar em 60 FPS e definir o plano de estabilização são as técnicas mais importantes para a estabilidade do holograma. Se estiver enfrentando uma separação de cores perceptível, primeiro certifique-se de que a taxa de quadros atenda às expectativas.

## <a name="see-also"></a>Confira também
* [Noções básicas sobre o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Cor, luz e materiais](../../design/color-light-and-materials.md)
* [Interações instinctuais](../../design/interaction-fundamentals.md)
* [Estabilização do holograma do MRTK](/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization)