---
title: Aspecto espacial do HoloLens (1ª geração) 220 – Som espacial
description: Siga este passo a passo de codificação usando Unity, Visual Studio e HoloLens para saber os detalhes dos conceitos de som espacial.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, som espacial, HoloLens, Mixed Reality Academy, unity, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, Windows 10
ms.openlocfilehash: d53b449916405d8bf42bb8dd63cc1d3cb5d6127bbf9b2989ce7cb09c3762a6e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200354"
---
# <a name="hololens-1st-gen-spatial-220-spatial-sound"></a>HoloLens (1ª geração) Espacial 220: Som espacial

>[!IMPORTANT]
>Os tutoriais do Mixed Reality Academy foram projetados com HoloLens (1ª geração), Unity 2017 e Headsets Imersivos de Realidade Misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos. Esses tutoriais não **_serão_** atualizados com os mais recentes toolsets ou interações que estão sendo usados para HoloLens 2 e podem não ser compatíveis com versões mais recentes do Unity.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

[O som](../../../design/spatial-sound.md) espacial dá vida aos hologramas e dá a eles presença em nosso mundo. Hologramas são compostos de luz e som e, se você perder a visão de seus hologramas, o som espacial poderá ajudá-lo a encontrá-los. O som espacial não é como o som típico que você ouviria na rádio, é o som posicionado no espaço 3D. Com o som espacial, você pode fazer com que os hologramas pareçam estar atrás de você, ao seu lado ou até mesmo na sua cabeça! Neste curso, você vai:

* Configure seu ambiente de desenvolvimento para usar o Som Espacial da Microsoft.
* Use o Som Espacial para aprimorar as interações.
* Use o Som Espacial em conjunto com o [Mapeamento Espacial](../../../design/spatial-mapping.md).
* Entenda o design de som e a combinação de práticas recomendadas.
* Use o som para aprimorar efeitos especiais e trazer o usuário para o mundo da Realidade Misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>MR Espacial 220: som espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um Windows 10 computador configurado com as ferramentas [corretas instaladas.](../../../develop/install-the-tools.md)
* Alguma capacidade básica de programação em C#.
* Você deve ter concluído o [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* Um HoloLens configurado [para desenvolvimento.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
  * Se você ainda precisar do suporte do Unity 5.6, use [esta versão.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip) Esta versão pode não estar mais atualizada.
  * Se você ainda precisar do suporte do Unity 5.5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Esta versão pode não estar mais atualizada.
  * Se você ainda precisar do suporte do Unity 5.4, use [esta versão.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip) Esta versão pode não estar mais atualizada.
* Desarmá-los na área de trabalho ou em outro local fácil de alcançar.

>[!NOTE]
>Se você quiser ver o código-fonte antes de baixar, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Errata e observações

* "Habilitar Apenas Meu Código" precisa ser desabilitado *(* desmarcado ) no Visual Studio em Ferramentas->Opções >Depuração para atingir pontos de interrupção em seu código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1 – Instalação do Unity

### <a name="objectives"></a>Objetivos

* Altere a configuração de som do Unity para usar o Som Espacial da Microsoft.
* Adicione som 3D a um objeto no Unity.

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **Abrir**.
* Navegue até sua Área de Trabalho e localizou a pasta que você desarmou anteriormente.
* Clique na pasta **Starting\Decibel** e pressione o **botão Selecionar** Pasta.
* Aguarde até que o projeto seja carregado no Unity.
* No painel **Project,** abra **Scenes\Decibel.unity.**
* No painel **Hierarquia,** expanda **HologramCollection** e selecione **P0LY.**
* No Inspetor, expanda **AudioSource** e observe que não há nenhuma caixa de **seleção Espacializar.**

Por padrão, o Unity não carrega um plug-in do espacializador. As etapas a seguir habilitam o Som Espacial no projeto.

* No menu superior do Unity, acesse **Editar > Project Configurações > Áudio.**
* Encontre o menu suspenso Plug-in do **Spatializer** e selecione **Espacializador MS HRTF.**
* No painel **Hierarquia,** selecione **HologramCollection > P0LY**.
* No painel **Inspetor,** encontre o componente **Fonte de** Áudio.
* Marque a **caixa de seleção Espacializar.**
* Arraste o **controle deslizante do Spatial Blend** até **3D** ou insira **1** na caixa de edição.

Agora, criaremos o projeto no Unity e configuraremos a solução no Visual Studio.

1. No Unity, selecione **Arquivo > Build Configurações**.
2. Clique **em Adicionar Cenas Abertas** para adicionar a cena.
3. Selecione **Plataforma Windows Universal** na lista **Plataforma** e clique em Mudar **Plataforma**.
4. Se você estiver desenvolvendo especificamente para HoloLens, de definido **Dispositivo de destino** como **HoloLens**. Caso contrário, deixe-o **em Qualquer dispositivo**.
5. Verifique **se o Tipo** de Build está definido como **D3D** e se **o SDK** está definido como Mais recente instalado **(que** deve ser o SDK 16299 ou mais recente).
6. Clique em **Compilar**.
7. Crie uma **nova pasta** chamada "Aplicativo".
8. Clique com um único clique **na pasta** Aplicativo.
9. Pressione **Selecionar Pasta**.

Quando o Unity for feito, uma Explorador de Arquivos será exibida.

1. Abra a **pasta Aplicativo.**
2. Abra a **Solução de Visual Studio Decibel**.

Se estiver implantando no HoloLens:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de Depurar para **Versão** e do ARM para **x86.**
2. Clique na seta para baixo ao lado do botão Computador Local e selecione **Computador Remoto.**
3. Insira **seu HoloLens IP do dispositivo** e descriptografe o Modo de Autenticação como Universal **(Protocolo Não Criptografado).** Clique em **Selecionar**. Se você não sabe o endereço IP do dispositivo, procure Configurações > Rede & **Internet > Opções Avançadas**.
4. Na barra de menus superior, clique em **Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você implanta em seu dispositivo, você precisará [emparelhá-lo com Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).

Se estiver implantando em um headset imersivo:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de Depurar para Versão **e** de ARM para **x64**.
2. Certifique-se de que o destino de implantação está definido como **Computador Local.**
3. Na barra de menus superior, clique em **Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capítulo 2 – Som espacial e interação

### <a name="objectives"></a>Objetivos

* Aprimorar o realismo do holograma usando som.
* Direcionar o olhar do usuário usando som.
* Forneça comentários de gesto usando som.

### <a name="part-1---enhancing-realism"></a>Parte 1 – Aprimorando o realismo

#### <a name="key-concepts"></a>Conceitos Principais

* Espacializar sons de holograma.
* As fontes de som devem ser colocadas em um local apropriado no holograma.

O local apropriado para o som vai depender do holograma. Por exemplo, se o holograma for de um humano, a origem do som deverá ser localizada perto da boca e não dos pés.

#### <a name="instructions"></a>Instruções

As instruções a seguir anexarão um som espacial a um holograma.

* No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.
* No painel **Inspetor** , na mensagem de **áudio**, clique no círculo ao lado de **AudioClip** e selecione **polifocalizar** no pop-up.
* Clique no círculo ao lado de **saída** e selecione **SoundEffects** no pop-up.

Project O decibéi usa um componente **AudioMixer** do Unity para habilitar o ajuste dos níveis de som para grupos de sons. Ao agrupar sons dessa forma, o volume geral pode ser ajustado mantendo o volume relativo de cada som.

* em **áudio**, expanda **Configurações de som 3d**.
* Defina o **nível de Doppler** como **0**.

Definir o nível de Doppler como zero desabilita as alterações em pitch causadas pelo Motion (do holograma ou do usuário). Um exemplo clássico de Doppler é um carro com movimentação rápida. À medida que o carro se aproxima de um ouvinte estacionário, a inclinação do motor aumenta. Quando ele passa o ouvinte, a densidade diminui com distância.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2-direcionando o olhar do usuário

#### <a name="key-concepts"></a>Conceitos Principais

* Use o som para chamar a atenção para hologramas importantes.
* Os ouvidos ajudam a direcionar onde devem ser os olhos.
* O cérebro tem algumas expectativas aprendidas.

Um exemplo de expectativas aprendidas é que os pássaros geralmente estão acima da cabeça dos seres humanos. Se um usuário ouve um som de pássaro, sua reação inicial é Pesquisar. Colocar um pássaro abaixo do usuário pode levar a eles voltados para a direção correta do som, mas não consegue encontrar o holograma com base na expectativa de precisar pesquisar.

#### <a name="instructions"></a>Instruções

As instruções a seguir permitem que P0LY sejam ocultadas para trás, para que você possa usar o som para localizar o holograma.

* No painel **hierarquia** , selecione **gerentes**.
* No painel **Inspetor** , encontre o **manipulador de entrada de fala**.
* Em **manipulador de entrada de fala**, expanda **ir ocultar**.
* Altere **nenhuma função** para **GoHide**.

![Palavra-chave: ir ocultar](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3-comentários do gesto

#### <a name="key-concepts"></a>Conceitos Principais

* Fornecer ao usuário uma confirmação de gesto positivo usando som
* Não sobrecarregar os sons do usuário em alta
* Os sons sutis funcionam melhor – não obscurecem a experiência

#### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda **hologramacollection**.
* Expanda **EnergyHub** e selecione **base**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicionar **manipulador de som de gesto**.
* Em **manipulador de som de gesto**, clique no círculo próximo ao **clipe de navegação** e ao clipe de navegação **atualizado** e selecione **RotateClick** do pop-up para ambos.
* Clique duas vezes em "GestureSoundHandler" para carregar no Visual Studio.

O manipulador de som de gesto executa as seguintes tarefas:

* Criar e configurar um **áudio**.
* Coloque a **audioname** no local do **gameobject** apropriado.
* Reproduz o **AudioClip** associado ao gesto.

#### <a name="build-and-deploy"></a>Compilar e implantar

1. no Unity, selecione **arquivo > Build Configurações**.
2. Clique em **Compilar**.
3. Clique uma vez na pasta do **aplicativo** .
4. Pressione **Selecionar pasta**.

Verifique se a barra de ferramentas diz "versão", "x86" ou "x64" e "dispositivo remoto". Caso contrário, essa é a instância de codificação do Visual Studio. Talvez seja necessário reabrir a solução na pasta do aplicativo.

* Se solicitado, recarregue os arquivos de projeto.
* Como antes, implante do Visual Studio.

Após a implantação do aplicativo:

* Observe como o som muda à medida que você se move ao P0LY.
* Digamos que *"Vá ocultar"* para fazer com que o P0LY se mova para um local por trás de você. Encontre-o pelo som.
* Olhar na base do hub de energia. Toque e arraste para a esquerda ou direita para girar o holograma e observe como o clique do som confirma o gesto.

Observação: há um painel de texto que será rotulado com você. Isso conterá os comandos de voz disponíveis que você pode usar ao longo deste curso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capítulo 3-som espacial e mapeamento espacial

### <a name="objectives"></a>Objetivos

* Confirme a interação entre os hologramas e o mundo real usando som.
* Occlude sons usando o mundo físico.

### <a name="part-1---physical-world-interaction"></a>Parte 1-interação física do mundo

#### <a name="key-concepts"></a>Conceitos Principais

* Os objetos físicos geralmente fazem um som ao encontrar uma superfície ou outro objeto.
* Os sons devem ser apropriados para o contexto na experiência.

Por exemplo, definir uma xícara em uma tabela deve fazer um som mais silencioso do que descartar um Boulder em uma parte do metal.

#### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda **hologramacollection**.
* Expanda **EnergyHub**, selecione **base**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicione **tocar para inserir com som e ação**.
* Em **toque para posicionar com som e ação**:
  * Verifique o **pai ao tocar**.
  * Defina **som de posicionamento** como **local**.
  * Defina **som de retirada** para **retirada**.
  * Pressione a + no canto inferior direito em ambos **na ação de retirada** e **na ação de posicionamento**. Arraste EnergyHub da cena para os campos **nenhum (objeto)** .
    * Em **ação de retirada**, clique em **sem função**  ->  **EnergyHubBase**  ->  **ResetAnimation**.
    * Em **ação de posicionamento**, clique em **sem função**  ->  **EnergyHubBase**  ->  **OnSelect**.

![Toque para posicionar com som e ação](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2-som oclusão

#### <a name="key-concepts"></a>Conceitos Principais

* Som, como claro, pode ser obstruído.

Um exemplo clássico é uma sala de concerto. Quando um ouvinte está fora do Hall e a porta é fechada, a música parece muffled. Normalmente, também há uma redução no volume. Quando a porta é aberta, o espectro completo do som é ouvido no volume real. Sons de alta frequência geralmente são absorvidos mais do que frequências baixas.

#### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicionar **emissor de áudio**.

A classe emissor de áudio fornece os seguintes recursos:

* Restaura todas as alterações no volume de **audioname**.
* Executa uma **física. RaycastNonAlloc** da posição do usuário na direção do **gameobject** ao qual o **AudioEmitter** está anexado.

O método RaycastNonAlloc é usado como uma otimização de desempenho para limitar as alocações, bem como o número de resultados retornados.

* Para cada **IAudioInfluencer** encontrado, chama o método **ApplyEffect** .
* Para cada **IAudioInfluencer** anterior que não é mais encontrado, chame o método **RemoveEffect** .

Observe que as atualizações do AudioEmitter em escalas de tempo humano, em oposição a por quadro. Isso é feito porque as pessoas geralmente não se movem com rapidez suficiente para que o efeito precise ser atualizado com mais frequência do que cada trimestre ou metade de um segundo. Hologramas que o teleport rapidamente de um local para outro pode quebrar a ilusão.

* No painel **hierarquia** , expanda **hologramacollection**.
* Expanda **EnergyHub** e selecione **BlobOutside**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicione **áudio Occluder**.
* Em **áudio Occluder**, defina a **frequência de corte** como **1500**.

Essa configuração limita as frequências de áudio para 1500 Hz e abaixo.

* Defina **passagem de volume** para **0,9**.

Essa configuração reduz o volume do áudio para 90% do seu nível atual.

O áudio Occluder implementa IAudioInfluencer para:

* Aplique um efeito de oclusão usando um **AudioLowPassFilter** que é anexado ao **áudio** , gerenciado, comprar o **AudioEmitter**.
* Aplica a atenuação de volume à Audioname.
* Desabilita o efeito definindo uma frequência de corte neutra e desabilitando o filtro.

A frequência usada como neutra é 22 kHz (22000 Hz). Essa frequência foi escolhida porque está acima da frequência máxima nominal que pode ser ouvida pelo Ear humano, isso não faz nenhum impacto discernido no som.

* No painel **hierarquia** , selecione **SpatialMapping**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicione **áudio Occluder**.
* Em **áudio Occluder**, defina a **frequência de corte** como **750**.

Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a frequência mais baixa é aplicada ao filtro.

* Defina **passagem de volume** para **0,75**.

Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a passagem do volume é aplicada de aditivo.

* No painel **hierarquia** , selecione **gerentes**.
* No painel **Inspetor** , expanda **manipulador de entrada de fala**.
* Em **manipulador de entrada de fala**, expanda ir para o **encargo**.
* Altere **nenhuma função** para **GoCharge**.

![Palavra-chave: ir para a carga](images/gocharge.png)

* Expanda **aqui**.
* Altere **nenhuma função** para **ComeBack**.

![Palavra-chave: Venha aqui](images/comehere.png)

#### <a name="build-and-deploy"></a>Compilar e implantar

* Como antes, compile o projeto no Unity e implante-o no Visual Studio.

Após a implantação do aplicativo:

* Digamos que "faça o *encargo"* para que o P0LY Insira o Hub de energia.

Observe a alteração no som. Ele deve parecer muffled e um pouco mais silencioso. Se você for capaz de se posicionar com uma parede ou outro objeto entre você e o Hub de energia, você deve notar um Muffling adicional do som devido à oclusão pelo mundo real.

* Diga *"Venha aqui"* para que P0LY deixe o Hub de energia e se posicione na frente de você.

Observe que o som oclusão é removido quando o P0LY sai do hub de energia. Se você ainda estiver ouvindo oclusão, P0LY poderá ser obstruído pelo mundo real. Tente mudar para garantir que você tenha uma clara linha de visão para P0LY.

### <a name="part-3---room-models"></a>Parte 3-modelos de sala

#### <a name="key-concepts"></a>Conceitos Principais

* O tamanho do espaço fornece filas subliminal que contribuem para a localização de som.
* Os modelos de sala são definidos por **áudio**.
* O [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece código para definir o modelo de sala.
* Para experiências de realidade misturada, selecione o modelo de sala que melhor se adapta ao espaço do mundo real.

Se você estiver criando um cenário de realidade virtual, selecione o modelo de sala que melhor se adapta ao ambiente virtual.

## <a name="chapter-4---sound-design"></a>Capítulo 4-design de som

### <a name="objectives"></a>Objetivos

* Entenda as considerações sobre o design de som efetivo.
* Aprenda técnicas e diretrizes de combinação.

### <a name="part-1---sound-and-experience-design"></a>Parte 1-design de som e experiência

Esta seção aborda as principais considerações e diretrizes de design de som e experiência.

#### <a name="normalize-all-sounds"></a>Normalizar todos os sons

Isso evita a necessidade de código de caso especial para ajustar os níveis de volume por som, o que pode ser demorado e limita a capacidade de atualizar facilmente os arquivos de som.

#### <a name="design-for-an-untethered-experience"></a>Design de uma experiência não de compartilhamento de Internet

HoloLens é um computador holographic totalmente contido e desvinculado. Os usuários podem e usarão suas experiências ao se moverem. Certifique-se de testar sua mixagem de áudio ao percorrer.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emitir som de locais lógicos em seus hologramas

No mundo real, um cachorro não latido de sua parte final e a voz de um humano não vem de seus pés. Evite emitir seus sons de partes inesperadas de seus hologramas.

Para hologramas pequenos, é razoável ter uma emissão sonora do centro da geometria.

#### <a name="familiar-sounds-are-most-localizable"></a>Os sons conhecidos são mais localizáveis

A voz humana e a música são muito fáceis de localizar. Se alguém chamar seu nome, você poderá determinar com precisão a direção de que a voz veio e de quanto longe. Sons curtos e desconhecidos são mais difíceis de localizar.

#### <a name="be-cognizant-of-user-expectations"></a>Cognizant as expectativas dos usuários

A experiência de vida exerce uma parte em nossa capacidade de identificar o local de um som. Esse é um dos motivos pelos quais a voz humana é particularmente fácil de localizar. É importante estar atento às expectativas aprendidas do usuário ao colocar seus sons.

Por exemplo, quando alguém ouve uma música de pássaro, ele geralmente procura, pois os pássaros tendem a estar acima da linha de visão (voador ou em uma árvore). Não é incomum um usuário ativar a direção correta de um som, mas examinar a direção vertical incorreta e ficar confuso ou frustrado quando não conseguir encontrar o holograma.

#### <a name="avoid-hidden-emitters"></a>Evitar emissores ocultos

No mundo real, se ouvimos um som, geralmente podemos identificar o objeto que está emitindo o som. Isso também deve se manter verdadeiro em suas experiências. Pode ser muito desconcerto para os usuários ouvirem um som, saber de onde o som se origina e não conseguir ver um objeto.

Há algumas exceções a essa diretriz. Por exemplo, sons de ambiente como Crickets em um campo não precisam estar visíveis. A experiência de vida nos dá familiaridade com a origem desses sons sem a necessidade de vê-los.

### <a name="part-2---sound-mixing"></a>Parte 2-mixagem de som

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Direcione sua combinação para o volume de 70% no HoloLens

As experiências de realidade misturada permitem que os hologramas sejam vistos no mundo real. Eles também devem permitir que sons do mundo real sejam ouvidos. Um destino de volume de 70% permite que o usuário Ouça o mundo junto com o som de sua experiência.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens em 100% volume deve se afogar em sons externos

Um nível de volume de 100% é semelhante a uma experiência de realidade virtual. Visualmente, o usuário é transportado para um mundo diferente. O mesmo deve conter verdadeiro forma audível.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Usar o AudioMixer do Unity para ajustar as categorias de sons

Ao projetar sua combinação, geralmente é útil criar categorias de som e ter a capacidade de aumentar ou diminuir seu volume como uma unidade. Isso retém os níveis relativos de cada som, ao mesmo tempo em que permite alterações rápidas e fáceis na combinação geral. As categorias comuns incluem; efeitos de som, Ambience, voz e música em segundo plano.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Misturar sons com base no olhar do usuário

Muitas vezes, pode ser útil alterar a mistura de som em sua experiência com base em onde um usuário está olhando (ou não). Um uso comum para essa técnica é reduzir o nível de volume para hologramas que estão fora do quadro Holographic para tornar mais fácil para o usuário se concentrar nas informações em frente deles. Outro uso é aumentar o volume de um som para chamar a atenção do usuário para um evento importante.

#### <a name="building-your-mix"></a>Criando sua combinação

Ao criar sua combinação, é recomendável começar com o áudio em segundo plano da sua experiência e adicionar camadas com base na importância. Geralmente, isso resulta em cada camada sendo mais sólida do que a anterior.

É recomendável usar sua combinação como um funil invertido, com os sons menos importantes (e geralmente mais silenciosos) na parte inferior, é recomendável estruturar sua combinação semelhante ao diagrama a seguir.

![Estrutura da combinação de som](images/soundlevels.png)

Overs de voz são um cenário interessante. Com base na experiência que você está criando, talvez você queira ter um som estéreo (não localizado) ou espacializar seus overs de voz. Duas experiências publicadas pela Microsoft ilustram exemplos excelentes de cada cenário.

[O HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa uma voz estéreo. Quando o narrador está descrevendo o local que está sendo exibido, o som é consistente e não varia com base na posição do usuário. Isso permite que o narrador descreva a cena sem tirar os sons espacializados do ambiente.

[Fragmentos utilizam](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) uma voz espacializada na forma de um inspetor. A voz do inspetor é usada para ajudar a chamar a atenção do usuário para uma dica importante como se um humano real estivesse na sala. Isso permite uma noção ainda maior de imersão na experiência de resolver o problema.

### <a name="part-3--performance"></a>Parte 3 – Desempenho

#### <a name="cpu-usage"></a>Uso da CPU

Ao usar o Som Espacial, 10 a 12 emissores consumirão aproximadamente 12% da CPU.

#### <a name="stream-long-audio-files"></a>Transmitir arquivos de áudio longos

Os dados de áudio podem ser grandes, especialmente em taxas de exemplo comuns (44,1 e 48 kHz). Uma regra geral é que arquivos de áudio com mais de 5 a 10 segundos devem ser transmitidos para reduzir o uso de memória do aplicativo.

No Unity, você pode marcar um arquivo de áudio para streaming nas configurações de importação do arquivo.

![Configurações de importação de áudio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capítulo 5 – Efeitos especiais

### <a name="objectives"></a>Objetivos

* Adicione profundidade a "Magic Windows".
* Traga o usuário para o mundo virtual.

### <a name="magic-windows"></a>Magic Windows

#### <a name="key-concepts"></a>Conceitos Principais

* Criar exibições em um mundo oculto é visualmente atraente.
* Aprimora o realismo adicionando efeitos de áudio quando um holograma ou o usuário está próximo ao mundo oculto.

#### <a name="instructions"></a>Instruções

* No painel **Hierarquia,** expanda **HologramCollection** e selecione **Escolher**.
* Expanda **Escolher** e **selecione VozSource**.
* No painel **Inspetor,** clique em **Adicionar Componente e** adicione Efeito de Voz do **Usuário.**

Um **componente AudioSource** será adicionado ao **VoiceSource.**

* Em **AudioSource,** de **definido Saída** como **UserVoice (Mixer)**.
* Marque a **caixa de seleção Espacializar.**
* Arraste o **controle deslizante do Spatial Blend** até **3D** ou insira **1** na caixa de edição.
* Expanda **o som 3D Configurações**.
* De **definir o nível do Doppler** como **0.**
* Em **Efeito de Voz do Usuário**, de acordo com o Objeto **Pai** como **o Resultado** da Cena.
* De **definir Distância Máxima** como **1**.

Definir **Distância Máxima** informa ao Efeito de Voz **do** Usuário o quão próximo o usuário deve estar para o objeto pai antes que o efeito seja habilitado.

* Em **Efeito de Voz do Usuário,** **expanda Parâmetros de Responsabilidade**.
* De **definir Profundidade** como **0,1**.
* De **acordo com Toque em 1 Volume**, Toque em Volume **2** e **Toque em 3 Volume** como **0,8**.
* De **definir Volume de Som Original** como **0,5**.

As configurações anteriores definem os parâmetros do **AudioChorusFilter** do Unity usados para adicionar a richness à voz do usuário.

* Em **Efeito de Voz do Usuário,** expanda **Parâmetros de Eco**.
* Definir **Atraso** como **300**
* Definir **a Taxa de Decaimento** como **0,2**.
* De **acordo com o Volume de Som Original** como **0**.

As configurações anteriores definem os parâmetros do **AudioEchoFilter** do Unity usados para fazer com que a voz do usuário ecoe.

O script efeito de voz do usuário é responsável por:

* Medindo a distância entre o usuário e **o GameObject ao** qual o script está anexado.
* Determinar se o usuário está enfrentando o **GameObject** ou não.

O usuário deve estar voltado para o GameObject, independentemente da distância, para que o efeito seja habilitado.

* Aplicando e configurando um **AudioChorusFilter** e um **AudioEchoFilter** no **AudioSource.**
* Desabilitar o efeito desabilitando os filtros.

O Efeito de Voz do Usuário usa o componente Seletor de Fluxo de Microfone, do [MixedRealityToolkit para Unity,](https://github.com/Microsoft/MixedRealityToolkit-Unity)para selecionar o fluxo de voz de alta qualidade e encaminhá-lo para o sistema de áudio do Unity.

* No painel **Hierarquia,** selecione **Gerenciadores**.
* No painel **Inspetor,** expanda Manipulador **de Entrada de Fala**.
* Em **Manipulador de Entrada de Fala,** expanda Mostrar **Valor.**
* Altere **Nenhuma Função** **paraBase.OnEnable.**

![Palavra-chave: Mostrar Oleio](images/showunderworld.png)

* Expanda **Ocultar Resindo.**
* Altere **Nenhuma função** **para OBase.OnDisable.**

![Palavra-chave: Ocultar o Dinheiro](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Compilar e implantar

* Como antes, crie o projeto no Unity e implante no Visual Studio.

Depois que o aplicativo for implantado:

* Face a uma superfície (parede, piso, tabela) e diga *"Mostrar Prédio".*

A operação será mostrada e todos os outros hologramas serão ocultos. Se você não vir o cenário, verifique se você está enfrentando uma superfície do mundo real.

* Abordagem dentro de 1 medidor do holograma de holograma e começar a falar.

Agora há efeitos de áudio aplicados à sua voz!

* Desligue-se da casa e observe como o efeito não é mais aplicado.
* Diga *"Ocultar a Insição"* para ocultar o ressario.

O poder será ocultado e os hologramas ocultos anteriormente reaparecerão.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu **o MR Spatial 220: Som espacial**.

Escutar o mundo e dar vida a suas experiências com som!