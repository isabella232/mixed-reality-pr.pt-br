---
title: sr Sharing 250-fones de ouvido HoloLens e de imersão
description: siga este passo a passo de codificação usando o Unity, Visual Studio, HoloLens e Windows Mixed Reality headsets para aprender os detalhes do compartilhamento de hologramas entre dispositivos de realidade misturada.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, imersiva, controlador de movimento, compartilhamento, controlador Xbox, rede, dispositivo cruzado
ms.openlocfilehash: 9f1b136193feefece3235d853503c05c69dbd451f9c2916fb178f1bcac0e3972
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208306"
---
# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>Compartilhamento do MR 250: HoloLens e headsets imersivos

>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](../develop/unity/tutorials/mr-learning-base-01.md) foi postada para o HoloLens 2.

com a flexibilidade do Plataforma Universal do Windows (UWP), é fácil criar um aplicativo que abranja vários dispositivos. Com essa flexibilidade, podemos criar experiências que aproveitam os pontos fortes de cada dispositivo. este tutorial abordará uma experiência compartilhada básica que é executada em HoloLens e Windows Mixed Reality headsets de imersão. Este conteúdo foi originalmente entregue na conferência do Microsoft Build 2017 em Seattle, WA.

**Neste tutorial, nós iremos:**

* Configure uma rede usando o UNET.
* Compartilhe hologramas entre dispositivos de realidade misturada.
* Estabeleça uma exibição diferente do aplicativo dependendo de qual dispositivo de realidade misturada está sendo usado.
* crie uma experiência compartilhada em que HoloLens os usuários guiam os usuários do headset com um quebra-cabeças simples.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Compartilhamento do MR 250: HoloLens e headsets imersivos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* um computador Windows 10 com as [ferramentas de desenvolvimento necessárias](../develop/install-the-tools.md) e [configurado para dar suporte a um headset de imersão Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Um controlador Xbox que funciona com seu PC.
* pelo menos um dispositivo HoloLens e um headset de imersão.
* Uma rede que permite a difusão UDP para descoberta.

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/MixedReality250/archive/master.zip) exigidos pelo projeto. Extraia os arquivos para um local fácil de lembrar.
* este projeto requer [uma versão recomendada do Unity com suporte a Windows Mixed Reality](../develop/install-the-tools.md).

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível em github](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capítulo 1 – holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Objetivos

Verifique se o ambiente de desenvolvimento está pronto para ser usado com um projeto simples.

### <a name="what-we-will-build"></a>O que vamos criar

um aplicativo que mostra um holograma em HoloLens ou um headset de imersão Windows Mixed Reality.

### <a name="steps"></a>Etapas

* Abra o Unity.
    * Selecione **Abrir**.
    * Navegue até onde você extraiu os arquivos de projeto.
    * Clique em **Selecionar Pasta**.
    * *Levará algum tempo para que o Unity processe o projeto pela primeira vez.*
* Verifique se a realidade misturada está habilitada no Unity.
    * abra a caixa de diálogo configurações de compilação (**Control + Shift + B** ou **arquivo > build Configurações...**).
    * selecione **Plataforma Universal do Windows** , em seguida, clique em **alternar plataforma**.
    * selecione **editar>Player Configurações**.
    * no painel **inspetor** no lado direito, expanda **XR Configurações**.
    * Verifique a caixa **suporte à realidade virtual** .
    * *Windows Mixed Reality deve ser o SDK da realidade Virtual.*
* Crie uma cena.
    * Na **hierarquia** , clique na **câmera principal** selecionar **excluir**.
    * Em **HoloToolkit > entrada > pré-fabricados** arraste **MixedRealityCameraParent** para a **hierarquia**.
* adicionar Hologramas à cena
    * Em **AppPrefabs** , arraste **Skybox** para a **exibição cena**.
    * De **AppPrefabs** , arraste **os gerentes** para a **hierarquia**.
    * Da **ilha** de arrastar **AppPrefabs** para a **hierarquia**.
* Salvar e compilar
    * Salvar ( **controle + S** ou **arquivo > salvar cena**)
    * Como essa é uma nova cena, você precisará nomeá-la. O nome não é importante, mas usamos SharedMixedReality.
* Exportar para Visual Studio
    * abra o menu compilar (**Control + Shift + B** ou **File > build Configurações**)
    * Clique em **Adicionar abrir cenas.**
    * Verificar **projetos do Unity C#**
    * Clique em **Compilar**.
    * Na janela Explorador de arquivos que aparece, crie uma nova pasta chamada **aplicativo**.
    * Clique uma vez na pasta do **aplicativo** .
    * Pressione **Selecionar pasta.**
    * **Aguarde a conclusão da compilação**
    * Na janela Explorador de arquivos que aparece, navegue até a pasta do **aplicativo** .
    * Clique duas vezes em **SharedMixedReality. sln** para iniciar o Visual Studio
* Compilar a partir de Visual Studio
    * Usando o destino de alteração da barra de ferramentas superior para **liberar** e **x86**.
    * Clique na seta ao lado de **computador local** e selecione o **dispositivo** para implantar no HoloLens
    * Clique na seta ao lado de **dispositivo** e selecione **computador local** para implantar para o headset de realidade misturada.
    * Clique em **depurar->iniciar sem Depurar** ou **controlar + F5** para iniciar o aplicativo.

### <a name="digging-into-the-code"></a>Aprofundando-se no código

No painel projeto, navegue até **Assets\HoloToolkit\Input\Scripts\Utilities** e clique duas vezes em **MixedRealityCameraManager. cs** para abri-lo.

**Visão geral:** MixedRealityCameraManager. cs é um script simples que ajusta as configurações de nível de qualidade e de segundo plano com base no dispositivo. a chave aqui é HolographicSettings. IsDisplayOpaque, que permite que um script detecte se o dispositivo é um HoloLens (IsDisplayOpaque retorna false) ou um headset de imersão (IsDisplayOpaque retorna true).

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Neste ponto, o aplicativo apenas renderizará um holograma. Adicionaremos interação com o holograma posteriormente. Ambos os dispositivos processarão o holograma da mesma forma. O headset de imersão também renderizará uma fundo azul céu e nuvens.

## <a name="chapter-2---interaction"></a>Capítulo 2-interação

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Objetivos

mostre como tratar a entrada para um aplicativo Windows Mixed Reality.

### <a name="what-we-will-build"></a>O que vamos criar

criando o aplicativo no capítulo 1, adicionaremos funcionalidade para permitir que o usuário pegue o holograma e coloque-o em uma superfície do mundo real em HoloLens ou em uma tabela virtual em um headset de imersão.

**Atualizador de entrada:** em HoloLens o gesto de seleção é o **toque de ar**. Em headsets de imersão, usaremos **o botão a** no controlador Xbox. Para obter mais informações, confira a [visão geral do modelo de interação](../design/interaction-fundamentals.md).

### <a name="steps"></a>Etapas

* Adicionar Gerenciador de entrada
    * No **HoloToolkit > entrada > pré-requisitos** arraste **InputManager** para Hierarquia como um filho de **Gerentes**. 
    * No **HoloToolkit> entrada > pré-> cursor** arraste **Cursor** para **Hierarquia**.
* Adicionar mapeamento espacial
    * No **HoloToolkit > SpatialMapping > Prefabs** arraste **SpatialMapping** para **Hierarquia**.
* Adicionar Playspace Virtual
    * Em **Hierarquia,** **expanda MixedRealityCameraParent** selecione **Limite**
    * No **painel** Inspetor, marque a caixa para habilitar **Limite**
    * Em **AppPrefabs,** arraste **VRRoom para** **Hierarquia**.
* Adicionar WorldAnchorManager
    * Em **Hierarquia**, selecione **Gerenciadores**.
    * No **Inspetor**, clique em **Adicionar Componente**.
    * Digite **World Anchor Manager**.
    * Selecione **Gerenciador de Âncoras Do** Mundo para adicioná-lo.
* Adicionar TapToPlace à Ilha
    * Em **Hierarquia,** expanda **Ilha**.
    * Selecione **MixedRealityLand.**
    * No **Inspetor**, clique em **Adicionar Componente**.
    * Digite **Toque em Colocar e** selecione-o.
    * Marque **Colocar Pai ao tocar em**.
    * De **definir Deslocamento de** Posicionamento como **(0, 0,1, 0)**.
* Salvar e criar como antes

### <a name="digging-into-the-code"></a>Aprofundar-se no código

**Script 1 – GamepadInput.cs**

No painel do projeto, navegue **até Assets\HoloToolkit\Input\Scripts\InputSources** e clique duas vezes em **GamepadInput.cs** para abri-lo. No mesmo caminho no painel do projeto, clique duas vezes em **InteractionSourceInputSource.cs**.

Observe que ambos os scripts têm uma classe base comum, BaseInputSource.

BaseInputSource mantém uma referência a um InputManager, que permite que um script acione eventos. Nesse caso, o evento InputClicked é relevante. Isso será importante lembrar quando chegarmos ao script 2, TapToPlace. No caso de GamePadInput, sondamos o botão A no controlador a ser pressionado e, em seguida, geramos o evento InputClicked. No caso de InteractionSourceInputSource, geramos o evento InputClicked em resposta ao TappedEvent.

**Script 2 – TapToPlace.cs**

No painel do projeto, navegue **até Assets\HoloToolkit\SpatialMapping\Scripts** e clique duas **vezes em TapToPlace.cs** para abri-lo.

A primeira coisa que muitos desenvolvedores querem implementar ao criar um aplicativo Holographic é mover Hologramas com entrada de gesto. Como tal, nos esforçamos para comentar completamente esse script. Vale a pena realçá-los para este tutorial.

Primeiro, observe que TapToPlace implementa IInputClickHandler. IInputClickHandler expõe as funções que lidam com o evento InputClicked gerado por GamePadInput.cs ou InteractionSourceInputSource.cs. OnInputClicked é chamado quando um BaseInputSource detecta um clique enquanto o objeto com TapToPlace está em foco. O airtapping no HoloLens ou pressionar o botão A no controlador Xbox disparará o evento.

O segundo é o código a ser executado em atualização para ver se uma superfície está sendo procurada para que possamos colocar o objeto do jogo em uma superfície, como uma tabela. O headset imersivo não tem um conceito de superfícies reais, portanto, o objeto que representa a parte superior da tabela (Cubo > TableThingy do Vroom >) foi marcado com a camada física SpatialMapping, de modo que a cast de raio em Atualização colidirá com a parte superior da tabela virtual.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Desta vez, você pode selecionar a ilha para movê-la. No HoloLens você pode mover a ilha para uma superfície real. No headset imersivo, você pode mover a ilha para a tabela virtual que adicionamos.

## <a name="chapter-3---sharing"></a>Capítulo 3 – Compartilhamento

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Objetivos

Verifique se a rede está configurada corretamente e detalha como as âncoras espaciais são compartilhadas entre dispositivos.

### <a name="what-we-will-build"></a>O que vamos criar

Converteremos nosso projeto em um projeto multijogador. Adicionaremos interface do usuário e lógica para hospedar ou ingressar sessões. HoloLens os usuários se verão na sessão com nuvens sobre suas cabeça e os usuários de headset imersivos terão nuvens próximas de onde a âncora está. Os usuários nos headsets imersivos verão a HoloLens usuários relativos à origem da cena. HoloLens os usuários verão o holograma da ilha no mesmo local. É fundamental observar que os usuários nos headsets imersivos não estarão na ilha durante este capítulo, mas se comportarão de maneira muito semelhante ao HoloLens, com uma exibição de olho de pássaros da ilha.

### <a name="steps"></a>Etapas

* Remover Ilha e VRRoom
    * Em **Hierarquia,** clique com o botão direito do mouse **em Ilha,** **selecione Excluir**
    * Em **Hierarquia,** clique com o botão direito **do mouse em VRRoom** selecione **Excluir**
* Adicionar Usland
    * Em **AppPrefabs,** arraste **Usland para** **Hierarquia**.
* Em **AppPrefabs,** arraste cada um dos seguintes para **Hierarquia**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Salvar e criar como antes

### <a name="digging-into-the-code"></a>Aprofundar-se no código

No painel do projeto, navegue até **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** e clique duas vezes em **UnetAnchorManager.cs.** A capacidade de um HoloLens compartilhar informações de acompanhamento com outro HoloLens de modo que ambos os dispositivos possam compartilhar o mesmo espaço é quase mágica. O poder da realidade misturada fica ativo quando duas ou mais pessoas podem colaborar usando os mesmos dados digitais.

Algumas coisas a ser destacada neste script:

Na função start, observe a verificação de **IsDisplayOpaque.** Nesse caso, vamos simular que a Âncora está estabelecida. Isso porque os headsets imersivos não expõem uma maneira de importar ou exportar âncoras. Se estamos executando em um HoloLens, no entanto, esse script implementa o compartilhamento de âncoras entre os dispositivos. O dispositivo que inicia a sessão criará uma âncora para exportação. O dispositivo que ingressar em uma sessão solicitará a âncora do dispositivo que iniciou a sessão.

**Exportadores:**

Quando um usuário cria uma sessão, NetworkDiscoveryWithAnchors chamará a função CreateAnchor UNETAnchorManagers. Vamos seguir o fluxo CreateAnchor.

Começamos fazendo algumas tarefas de limpeza, limpando todos os dados que podemos ter coletado para âncoras anteriores. Em seguida, verificamos se há uma âncora armazenada em cache a ser carregada. Os dados de âncora tendem a estar entre 5 e 20 MB, portanto, o reutilizamento de âncoras armazenadas em cache pode economizar na quantidade de dados que precisamos transferir pela rede. Veremos como isso funciona um pouco mais tarde. Mesmo que estamos reutilizando a âncora, precisamos preparar os dados de âncora no caso de novas junções de cliente que não tenham a âncora.

Falando em preparar os dados de âncora, a classe WorldAnchorTransferBatch expõe a funcionalidade para preparar dados de âncora para envio para outro dispositivo ou aplicativo e a funcionalidade para importar os dados de âncora. Como estamos no caminho de exportação, adicionaremos nossa âncora ao WorldAnchorTransferBatch e chamaremos a função ExportAsync. ExportAsync chamará o retorno de chamada writeBuffer à medida que gerar dados para exportação. Quando todos os dados foram exportados, ExportComplete será chamado. No WriteBuffer, adicionamos a parte de dados a uma lista que podemos manter para exportação. Em ExportarComplete, convertemos a lista em uma matriz. A variável AnchorName também é definida, o que disparará outros dispositivos para solicitar a âncora se eles não a têm.

Em alguns casos, a âncora não exportará ou criará tão poucos dados que tentaremos novamente. Aqui, basta chamar CreateAnchor novamente.

Uma função final no caminho de exportação é AnchorFoundRemotely. Quando outro dispositivo encontrar a âncora, esse dispositivo dirá ao host e o host a usará como um sinal de que a âncora é uma "boa âncora" e pode ser armazenada em cache.

**Importação:**

Quando um HoloLens insinte uma sessão, ele precisa importar uma âncora. Na função Update do UNETAnchorManager, o ancoraname é sondado. Quando o nome da âncora é alterado, o processo de importação é iniciado. Primeiro, tentamos carregar a âncora com o nome especificado do repositório de âncora local. Se já o tiver, podemos usá-lo sem baixar os dados novamente. Se não tivermos, chamamos o WaitForAnchor, que iniciará o download.

Quando o download for concluído, NetworkTransmitter_dataReadyEvent será chamado. Isso sinalizará o loop de atualização para chamar ImportAsync com os dados baixados. ImportAsync chamará ImportComplete quando o processo de importação for concluído. Se a importação for bem-sucedida, a âncora será salva no repositório local do Player. O PlayerController. cs realmente faz a chamada para AnchorFoundRemotely para permitir que o host saiba que uma boa âncora foi estabelecida.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

desta vez, um usuário com um HoloLens hospedará uma sessão usando o botão **iniciar sessão** na interface do usuário. outros usuários, em HoloLens ou um headset de imersão, selecionarão a sessão e, em seguida, selecionarão o botão de **sessão de junção** na interface do usuário. se você tiver várias pessoas com dispositivos HoloLens, eles terão nuvens vermelhas sobre seus cabeçotes. também haverá uma nuvem azul para cada headset de imersão, mas as nuvens azuis não estarão acima dos headsets, pois os headsets não estão tentando encontrar o mesmo espaço de coordenadas do mundo que os dispositivos HoloLens.

Esse ponto no projeto é um aplicativo de compartilhamento independente; Ele não faz muita coisa e pode agir como uma linha de base. Nos próximos capítulos, começaremos a criar uma experiência para as pessoas gostarem. Para obter mais orientações sobre o design de experiência compartilhada, acesse aqui.

## <a name="chapter-4---immersion-and-teleporting"></a>Capítulo 4-imersão e teleportabilidade

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Objetivos

Atenda à experiência de cada tipo de dispositivo de realidade misturada.

### <a name="what-we-will-build"></a>O que vamos criar

Atualizaremos o aplicativo para colocar os usuários de headsets imersivas na ilha com uma exibição imersiva. HoloLens os usuários ainda terão a visão panorâmica da ilha. Os usuários de cada tipo de dispositivo podem ver outros usuários como aparecem no mundo. por exemplo, os usuários de headsets de imersão podem ver os outros avatars em outros caminhos na ilha, e eles veem os HoloLens usuários como nuvens giant acima da ilha. os usuários do headset de imersão também verão o cursor do olhar ray do usuário HoloLens se o usuário HoloLens estiver olhando para a ilha. HoloLens os usuários verão um avatar na ilha para representar cada usuário do headset de imersão.

**Entrada atualizada para o dispositivo de imersão:**

* Os botões do amortecedor esquerdo e do amortecedor direito no controlador Xbox giram o Player
* Manter o botão Y no controlador Xbox habilitará um cursor [teleport](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) . Se o cursor tiver um indicador de seta girando quando você liberar o botão Y, você será teleportado para o local do cursor.

### <a name="steps"></a>Etapas

* Adicionar MixedRealityTeleport a MixedRealityCameraParent
    * Em **hierarquia**, selecione **Usland**.
    * No **Inspetor**, habilite o **controle de nível**.
    * Em **hierarquia**, selecione **MixedRealityCameraParent**.
    * No **Inspetor**, clique em **Adicionar componente**.
    * Digite **teleport de realidade misturada** e selecione-o.

### <a name="digging-into-the-code"></a>Aprofundando-se no código

Os usuários do headset de imersão serão conectados a seus PCs com um cabo, mas nossa ilha é maior do que o cabo é longo. Para compensar, precisamos da capacidade de mover a câmera independentemente do movimento do usuário. Consulte a [página de conforto](../design/comfort.md) para obter mais informações sobre como criar seu aplicativo de realidade misturada (em particular e Locomotion).

Para descrever esse processo, será útil definir dois termos. Primeiro, **Dolly** será o objeto que move a câmera independentemente do usuário. Um objeto de jogo filho do **Dolly** será a **câmera principal**. A câmera principal é anexada à cabeça do usuário.

No painel projeto, navegue até **Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **MixedRealityTeleport. cs**.

MixedRealityTeleport tem dois trabalhos. Primeiro, ele lida com a rotação usando os amortecedores. Na função Update, pesquisamos por ' ButtonUp ' em LeftBumper e RightBumper. GetButtonUp retorna true no primeiro quadro em que um botão está ativo depois de ter sido desativado. Se um dos botões tivesse sido gerado, sabemos que o usuário precisa girar.

Quando giramos, fazemos um fade out e esmaecemos usando um script simples chamado ' Fade Control '. Fazemos isso para impedir que o usuário veja um movimento não natural que poderia levar a discomfort. O efeito de fade in e saída é bastante simples. Temos um buraco de cruz preto na frente da **câmera principal**. Ao desbotar, fazemos a transição do valor alfa de 0 para 1. Isso gradualmente faz com que os pixels pretos do Quad sejam renderizados e obscurecem qualquer coisa por trás deles. Ao retroceder, fazemos a transição do valor alfa de volta para zero.

Quando calculamos a rotação, observe que estamos girando nosso **Dolly** , mas calculando a rotação em toda a **câmera principal**. Isso é importante, pois o mais distante da **câmera principal** está longe de 0, 0, a rotação menos precisa em relação ao Dolly se tornaria do ponto de vista do usuário. Na verdade, se você não girar a posição da câmera, o usuário será movido em um arco em volta do **Dolly** em vez de girar.

O segundo trabalho para MixedRealityTeleport é manipular a movimentação de **Dolly**. Isso é feito em SetWorldPosition. SetWorldPosition usa a posição do mundo desejada, a posição onde o usuário deseja percieve que estar. Precisamos colocar nosso **Dolly** nessa posição menos a posição local da **câmera principal**, pois esse deslocamento será adicionado a cada quadro.

Um segundo script chama SetWorldPosition. Vamos examinar esse script. No painel projeto, navegue até **Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **TeleportScript. cs**.

Esse script é um pouco mais envolvido do que MixedRealityTeleport. O script está verificando se o botão Y no controlador Xbox será mantido. Enquanto o botão é mantido para baixo, um cursor teleport é renderizado e o script converte um Ray a partir da posição de olhar do usuário. Se esse raio colidir com uma superfície que está mais ou menos apontando para cima, a superfície será considerada uma boa superfície para teleport e a animação no cursor teleport será habilitada. Se o raio não colidir com uma superfície mais ou menos apontando para cima, a animação no cursor será desabilitada. Quando o botão Y é liberado e o ponto calculado do raio é uma posição válida, o script chama SetWorldPosition com a posição do raio interseccionado.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Desta vez, você precisará encontrar um amigo.

mais uma vez, um usuário com o HoloLens irá hospedar uma sessão. Outros usuários ingressarão na sessão. O aplicativo fará com que os três primeiros usuários ingressem de um headset de imersão em um dos três caminhos na ilha. Sinta-se à vontade para explorar a ilha nesta seção.

Detalhes a serem observados:

1. você pode ver os rostos nas nuvens, o que ajuda um usuário imersos a ver qual direção um usuário HoloLens está olhando.
2. Os avatars na ilha têm pescoços que giram. Eles não seguirão o que o usuário está fazendo é realidade real (não temos essas informações), mas isso faz uma boa experiência.
3. se o usuário HoloLens estiver olhando a ilha, os usuários do imersos poderão ver o cursor.
4. as nuvens que representam os HoloLens usuários convertem sombras.

## <a name="chapter-5---finale"></a>Capítulo 5 – final

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Objetivos

Crie uma experiência interativa colaborativa entre os dois tipos de dispositivo.

### <a name="what-we-will-build"></a>O que vamos criar

com base no capítulo 4, quando um usuário com um headset de imersão fica perto de um quebra-cabeça na ilha, o HoloLens usuários receberão uma dica de ferramenta com uma pista para o quebra-cabeça. Depois que todos os usuários do headset de imersão passarem do quebra-cabeças e para a "área pronta" na sala de Rocket, o Rocket será iniciado.

### <a name="steps"></a>Etapas

* Em **hierarquia**, selecione **Usland**.
* No **Inspetor**, em **controle de nível**, marque **habilitar colaboração**.

### <a name="digging-into-the-code"></a>Aprofundando-se no código

Agora vamos examinar LevelControl. cs. Esse script é o núcleo da lógica do jogo e mantém o estado do jogo. Como esse é um jogo para vários jogadores usando UNET, precisamos entender como os dados fluem, pelo menos o suficiente para modificar este tutorial. Para obter uma visão geral mais completa do UNET, consulte a documentação do Unity.

No painel do projeto, navegue **até Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **LevelControl.cs.**

Vamos entender como um headset imersivo indica que eles estão prontos para o lançamento do foguete. A preparação para o Lançamento do Foguete é comunicada definindo um dos três bools em uma lista de bools que correspondem aos três caminhos na ilha. O bool de um caminho será definido quando o usuário atribuído ao caminho estiver sobre o painel marrom dentro da sala de foguetes. Ok, agora para os detalhes.

Vamos começar na função Update(). Você observará que há uma função 'cheat'. Nós o utilizamos em desenvolvimento para testar a sequência de lançamento e redefinição de foguetes. Ele não funcionará na experiência de vários usuários. Esperamos que, no momento em que você internalize a seguinte idemação, você possa fazê-la funcionar. Depois de verificarmos se devemos colar, verificamos se o jogador local está imerso. Queremos nos concentrar em como vemos que estamos na meta. Dentro da verificação if (Insíbrida), há uma chamada para CheckGoal ocultando-se atrás do bool **EnableCollaboration.** Isso corresponde à caixa de seleção que você verificou ao concluir as etapas deste capítulo. Dentro de EnableCollaboration, vemos uma chamada para CheckGoal().

CheckGoal faz alguns cálculos para ver se estamos mais ou menos em posição no painel. Quando estamos, depurar.log "Chegou na meta" e, em seguida, chamamos 'SendAtGoalMessage()'. Em SendAtGoalMessage, chamamos playerController.SendAtGoal. Para economizar algum tempo, este é o código:

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

Observe que SendAtGoalMessage chama CmdSendAtGoal, que chama levelState.SetGoalIndex, que está de volta em LevelControl.cs. À primeira vista, isso parece estranho. Por que não chamar SetGoalIndex em vez desse roteamento estranho por meio do controlador do player? O motivo é que estamos em conformidade com o modelo de dados que o UNET usa para manter os dados em sincronia. Para evitar a confusão e a reação, o UNET requer que cada objeto tenha um usuário que tenha autoridade para alterar as variáveis sincronizadas. Além disso, somente o host (o usuário que iniciou a sessão) pode alterar os dados diretamente. Os usuários que não são o host, mas têm autoridade, precisam enviar um 'comando' para o host, o que alterará a variável. Por padrão, o host tem autoridade sobre todos os objetos, exceto pelo objeto gerado para representar o usuário. Em nosso caso, esse objeto tem o script playercontroller. Há uma maneira de solicitar autoridade para um objeto e, em seguida, fazer alterações, mas optemos por aproveitar o fato de que o controlador do player tem auto autoridade e roteia comandos por meio do controlador do player.

Dito de outra forma, quando nos encontramos em nosso objetivo, o jogador precisa dizer ao host e o host dirá a todos os outros.

De volta a LevelControl.cs, veja SetGoalIndex. Aqui, estamos definindo o valor de um valor em uma lista de sincronização (AtGoal). Lembre-se de que estamos no contexto do host enquanto fazemos isso. Semelhante a um comando, um RPC é algo que o host pode emitir que fará com que todos os clientes executem algum código. Aqui chamamos 'RpcCheckAllGoals'. Cada cliente verificará individualmente se todos os três AtGoals estão definidos e, em caso afirmacional, lançará o foguete.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Com base no capítulo anterior, iniciaremos a sessão como antes. Desta vez, à medida que os usuários no headset imersivo chegarem à "porta" em seu caminho, uma dica de ferramenta aparecerá que somente os usuários HoloLens podem ver. Os HoloLens usuários são responsáveis por comunicar essa dica aos usuários no headset imersivo. O foguete será lançado para o espaço depois que cada avatar tiver entrado no painel marrom correspondente dentro do vulcão. A cena será redefinida após 60 segundos para que você possa fazer isso novamente.

## <a name="see-also"></a>Confira também

* [Entrada do MR 213: controladores de movimentos](mixed-reality-213.md)