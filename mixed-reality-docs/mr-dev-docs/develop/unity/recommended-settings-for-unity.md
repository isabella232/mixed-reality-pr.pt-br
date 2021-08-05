---
title: Configurações recomendadas do Unity
description: Saiba mais sobre os comportamentos de desempenho e publicação do Unity específicos para aplicativos de realidade misturados que podem ser alternados por meio de configurações do projeto.
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: unity, configurações, realidade misturada, HoloLens, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, desempenho, configurações de qualidade, configurações de iluminação, buffer de profundidade, xr, perda de rastreamento
ms.openlocfilehash: 736ec4c1cc967eaae1ff53728d6e912c4f03a1f17ef75450c93e58b1a1f0064d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211834"
---
# <a name="recommended-settings-for-unity"></a>Configurações recomendadas do Unity

O Unity fornece um conjunto de opções padrão que geralmente são o caso médio de todas as plataformas. No entanto, o Unity oferece alguns comportamentos específicos para a realidade misturada que pode ser alternada por meio de configurações do projeto.

## <a name="performant-environment-set-up"></a>Configuração de ambiente de alto desempenho

### <a name="low-quality-settings"></a>Configurações de baixa qualidade

é importante modificar as configurações de **qualidade do Unity** para **muito baixa** , de modo que seu aplicativo seja executado e tenha um bom desempenho na taxa de quadros apropriada, especialmente para o desenvolvimento de HoloLens. Para o desenvolvimento de headsets de imersão, dependendo das especificações do desktop capacitando a experiência VR, ainda é possível obter uma taxa de quadros sem os parâmetros de qualidade mais baixos.

no Unity 2019 LTS +, você pode definir o nível de qualidade do projeto acessando **editar**  >  **Project Configurações**  >  **qualidade** e definindo o **padrão** clicando na seta para baixo para o * * nível de baixa qualidade.

### <a name="lighting-settings"></a>Configurações de iluminação

De forma semelhante às configurações de cena de qualidade, é importante definir as configurações de iluminação ideais para seu aplicativo de realidade misturada. No Unity, a configuração de iluminação que geralmente terá o maior impacto no desempenho em sua cena é a **iluminação global em tempo real**. você pode desativar a luminosidade global acessando a iluminação de renderização da **janela** Configurações a iluminação global em  >    >    >  **tempo real**.

Há outra configuração de iluminação, **inclusas global iluminação**. essa configuração pode fornecer resultados de desempenho e visualmente surpreendentes em headsets de imersão, mas não é aplicável para o desenvolvimento de HoloLens. a **iluminação Global inclusas** é calculada apenas para GameObjects estáticos, que não são encontrados em HoloLens cenas devido à natureza de um ambiente desconhecido e em constante alteração.

Leia [iluminação global do Unity](https://docs.unity3d.com/Manual/GIIntro.html) para obter mais informações. 

>[!NOTE]
> A **iluminação global em tempo real** é definida **por cena** e, portanto, os desenvolvedores devem salvar essa propriedade para cada cena do Unity em seu projeto.

### <a name="single-pass-instancing-rendering-path"></a>Caminho de renderização de instância única de passagem

Em aplicativos de realidade misturada, a cena é renderizada duas vezes, uma vez para cada olho para o usuário. Em comparação com o desenvolvimento 3D tradicional, isso efetivamente dobra a quantidade de trabalho que precisa ser computada. É importante selecionar o caminho de renderização mais eficiente no Unity para economizar em tempo de CPU e GPU. A renderização de passagem única em instância otimiza o pipeline de renderização do Unity para aplicativos de realidade misturada e é recomendável habilitar essa configuração por padrão para cada projeto.

Como habilitar esse recurso no seu projeto do Unity

1)  Abra **Configurações de XR do Player** (acesse **Editar** > **Configurações do Projeto** > **Player** > **Configurações de XR**)
2) Selecione **Instância de Passagem Única** no menu suspenso **Método de Renderização de Estéreo** (a caixa de seleção **Realidade Virtual Compatível** precisa estar marcada)

Leia os artigos a seguir do Unity para obter mais detalhes com essa abordagem de renderização.

- [Como maximizar o desempenho de RA e VR com a renderização avançada de estéreo](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Instância de passagem única](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> Um problema comum na renderização com uma instância de passagem única ocorre se os desenvolvedores já têm sombreadores personalizados existentes não escritos para a criação de instância. Depois de habilitar esse recurso, os desenvolvedores poderão perceber que alguns GameObjects são renderizados apenas em um olho. Isso ocorre porque os sombreadores personalizados associados não têm as propriedades apropriadas para a criação de instância.
>
> Confira [Renderização de estéreo de passagem única para o HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) do Unity para saber como resolver esse problema

### <a name="enable-depth-buffer-sharing"></a>Habilitar compartilhamento de buffer de profundidade

Para obter uma melhor estabilidade de holograma da percepção do usuário, é recomendável habilitar a propriedade de **compartilhamento de buffer de profundidade** no Unity. ao ativar essa ação, o Unity compartilhará o mapa de profundidade produzido por seu aplicativo com a plataforma Windows Mixed Reality. Em seguida, a plataforma pode otimizar melhor a estabilidade do holograma especificamente para sua cena para qualquer determinado quadro que esteja sendo renderizado pelo seu aplicativo.

Como habilitar esse recurso no seu projeto do Unity

1) Abra **Configurações de XR do Player** (acesse **Editar** > **Configurações do Projeto** > **Player** > **Configurações de XR**)
2) marque a caixa de seleção **habilitar compartilhamento de Buffer de profundidade** em SDKs da **realidade virtual**  >  **Windows Mixed Reality** expansão (a caixa de seleção **com suporte da realidade virtual** deve ser marcada)

além disso, é recomendável selecionar **profundidade de 16 bits** na configuração de **formato de profundidade** neste painel, especialmente para o desenvolvimento de HoloLens. A seleção de 16 bits em comparação a 24 bits reduzirá significativamente os requisitos de largura de banda, pois menos dados precisarão ser movidos/processados.

para que a plataforma de Windows Mixed Reality otimize a estabilidade do holograma, ela depende do buffer de profundidade para ser preciso e corresponder a qualquer holograma renderizado na tela. Portanto, com o compartilhamento de buffer de profundidade ativado, é importante ao renderizar a cor, para também renderizar a profundidade. No Unity, a maioria dos materiais opacos ou TransparentCutouts renderizará profundidade por padrão, mas os objetos de texto e Transparent não renderizarão a profundidade, embora isso seja dependente de sombreador, etc.

se estiver usando a [realidade misturada Toolkit sombreador padrão](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader), para renderizar a profundidade de objetos transparentes:

1) Selecione o material transparente que está usando o sombreador padrão MRTK e abra a janela do editor de Inspetor
2) Selecione o botão **corrigir agora** dentro do aviso de compartilhamento de buffer de profundidade. Isso também pode ser executado manualmente definindo o **modo de renderização** como **personalizado**; em seguida, defina **modo** como **transparente** e, por fim, defina a **gravação de profundidade** como **on**

> [!IMPORTANT]
> Os desenvolvedores devem ter cuidado com o combate ao Z ao alterar esses valores juntamente com as configurações de plano próximo/longe da câmera. O combate ao Z ocorre quando dois Gameobjects tentam renderizar para o mesmo pixel e devido a limitações na fidelidade do buffer de profundidade (ou seja, z Depth), Unity não pode distinguir qual objeto está na frente do outro. Os desenvolvedores notarão uma cintilação entre dois objetos de jogo à medida que eles *lutarem* pelo mesmo valor de profundidade z. Isso pode ser resolvido alternando para o formato de profundidade de 24 bits, pois haverá um intervalo maior de valores para cada objeto a ser calculado para a profundidade z da câmera.
>
> no entanto, é recomendável, especialmente para o desenvolvimento de HoloLens, modificar os planos próximos e distantes da câmera para um intervalo menor, em vez disso, manter o formato de profundidade de 16 bits. A profundidade z é mapeada de forma não linear para o intervalo de valores nos planos de câmera próximos e distantes. Isso pode ser modificado selecionando a *câmera principal* em sua cena e, em **Inspetor**, alterar os valores de **plano de recorte próximo & longe** para reduzir seu intervalo (ou seja, de 1000m para 100 ms ou outro valor x, etc.)

>[!IMPORTANT]
> [O Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) ao usar o formato de profundidade de 16 bits. Assim, alguns efeitos de interface do usuário do Unity e outros efeitos requeridos pelo estêncil não funcionarão a menos que o formato de profundidade de 24 bits esteja selecionado, o que criará um [buffer de estêncil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html).

### <a name="building-for-il2cpp"></a>Compilando para IL2CPP

O Unity preteriu o suporte para o back-end de script do .NET e, portanto, recomenda que os desenvolvedores utilizem o **IL2CPP** para suas compilações do Visual Studio UWP. Embora isso traga várias vantagens, a criação de sua solução do Visual Studio a partir do Unity para **IL2CPP** pode ser mais lenta do que o antigo método .net. Portanto, é altamente recomendável seguir as práticas recomendadas para a criação de **IL2CPP** para economizar em tempo de iteração de desenvolvimento.

1) Aproveite a criação incremental criando seu projeto no mesmo diretório a cada vez, reutilizando os arquivos predefinidos ali
2) Desabilitar verificações de software antimalware para seu projeto & criar pastas
   - abra o **vírus & proteção contra ameaças** em seu aplicativo de configurações de Windows 10
   - selecione **gerenciar Configurações** em **vírus & ameaças proteção configurações**
   - Selecione **Adicionar ou remover exclusões** na seção **exclusões**
   - Selecione **Adicionar uma exclusão** e selecione a pasta que contém o código do projeto de Unity e as saídas de compilação
3) Usar um SSD para compilação

Leia [otimizando os tempos de compilação para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obter mais informações.

> [!NOTE]
> Além disso, pode ser benéfico configurar um [Servidor de Cache](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para projetos do Unity com uma grande quantidade de ativos (excluindo arquivos de script) ou que estejam constantemente alterando cenas/ativos. Ao abrir um projeto, o Unity armazena os ativos qualificados em um formato de cache interno no computador do desenvolvedor. Os itens precisam ser importados novamente e, assim, processados novamente quando modificados. Esse processo pode ser feito uma vez e salvo em um Servidor de Cache e, consequentemente, compartilhado com outros desenvolvedores para economizar tempo, em vez de todos os desenvolvedores processarem a nova importação de novas alterações localmente.

## <a name="publishing-properties"></a>Propriedades de publicação

### <a name="holographic-splash-screen"></a>Tela inicial do Holographic

HoloLens tem uma CPU e uma GPU de classe móvel, o que significa que os aplicativos podem demorar um pouco mais para carregar. Enquanto o aplicativo estiver sendo carregado, os usuários verão apenas preto e, portanto, poderão imaginar o que está acontecendo. Para assegurá-los durante o carregamento, você pode adicionar uma tela inicial do Holographic.

Para alternar a tela inicial do Holographic:

1) ir para a página **editar**  >  **Project Configurações**  >  **Player**
2) selecione a guia **repositório de Windows** e abra a seção imagem de **abertura**
3) aplique sua imagem na propriedade de **imagem de abertura Windows Holographic > Holographic** .
    - Alternar a opção **Mostrar tela inicial do Unity** habilitará ou desabilitará a tela inicial com marca do Unity. se você não tiver uma licença de Pro do unity, a tela inicial da marca do unity será sempre exibida.
    - Se uma **imagem de abertura do Holographic** for aplicada, ela sempre será exibida se a caixa de seleção Mostrar tela inicial do Unity estiver habilitada ou desabilitada. a especificação de uma imagem de abertura holographic personalizada só está disponível para os desenvolvedores com uma licença de Pro do Unity.

|  Mostrar tela inicial do Unity  |  Imagem de abertura do Holographic  |  Comportamento |
|----------|----------|----------|
|  Ativado  |  Nenhum  |  Mostre a tela inicial do Unity padrão por 5 segundos ou até que o aplicativo seja carregado, o que for maior. |
|  Ativado  |  Personalizado  |  Mostre a tela inicial personalizada por 5 segundos ou até que o aplicativo seja carregado, o que for maior. |
|  Desativado  |  Nenhum  |  Mostrar preto transparente (Nothing) até que o aplicativo seja carregado. |
|  Desativado  |  Personalizado  |  Mostre a tela inicial personalizada por 5 segundos ou até que o aplicativo seja carregado, o que for maior. |

Leia a [documentação da tela inicial do Unity](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) para obter mais informações.

### <a name="tracking-loss"></a>Controle de perda

Um headset de realidade misturada depende da visualização do ambiente em relação a ele para construir [sistemas de coordenadas com bloqueio mundial](coordinate-systems-in-unity.md), que permitem que os hologramas permaneçam em posição. Quando o headset não consegue se localizar no mundo, diz-se que o fone de ouvido é considerado *perdido*. Nesses casos, a funcionalidade dependente de sistemas de coordenadas bloqueados pelo mundo, como estágios espaciais, âncoras espaciais e mapeamento espacial, não funciona.

Se ocorrer uma perda de controle, o comportamento padrão do Unity será parar de renderizar os hologramas, pausar o [loop do jogo](https://docs.unity3d.com/Manual/ExecutionOrder.html)e exibir uma notificação de rastreamento perdido que siga confortavelmente os usuários olhar. As notificações personalizadas também podem ser fornecidas na forma de uma imagem de perda de rastreamento. Para aplicativos que dependem do acompanhamento de toda a sua experiência, é suficiente deixar que o Unity manipule isso totalmente até que o rastreamento seja readquirido. Os desenvolvedores podem fornecer uma imagem personalizada a ser mostrada durante a perda de controle.

Para personalizar a imagem perdida de rastreamento:

1) ir para a página **editar**  >  **Project Configurações**  >  **Player**
2) selecione na guia **repositório de Windows** e abra a seção **imagem de abertura**
3) aplique a imagem sob a propriedade **Windows Holographic > rastrear perda de imagem** .

#### <a name="opt-out-of-automatic-pause"></a>Recusa de pausa automática

Alguns aplicativos podem não exigir acompanhamento (por exemplo, [aplicativos somente de orientação](coordinate-systems-in-unity.md) , como visualizadores de vídeo de 360 graus) ou talvez precisem continuar o processamento ininterrupto enquanto o rastreamento é perdido. Você pode recusar a perda padrão de comportamento de controle, mas é responsável por ocultar/desabilitar qualquer objeto, o que não será renderizado corretamente em um cenário de perda de rastreamento. Na maioria dos casos, o único conteúdo que é recomendado para ser renderizado nesse caso é o conteúdo de corpo bloqueado, centralizado em toda a câmera principal.

Para recusar o comportamento de pausa automática:

1) vá para a página **editar**  >  **Project Configurações**  >  **Player**
2) selecione a guia **repositório de Windows** e abra a seção imagem de **abertura**
3) modifique o **Windows Holographic > na caixa de seleção pausar a perda de rastreamento e mostrar imagem** .

#### <a name="tracking-loss-events"></a>Rastreando eventos de perda

Para definir o comportamento personalizado quando o rastreamento é perdido, manipule os [eventos de perda de controle](tracking-loss-in-unity.md)global.

### <a name="capabilities"></a>Funcionalidades

Para que um aplicativo aproveite determinadas funcionalidades, ele deve declarar os recursos apropriados em seu manifesto. As declarações de manifesto podem ser feitas no Unity para que elas sejam incluídas em todas as exportações futuras do projeto.

Os recursos podem ser habilitados para um aplicativo de realidade misturada:

1) ir para a página **editar**  >  **Project Configurações**  >  **Player**
2) selecione a guia **repositório de Windows** , abra a seção **publicação Configurações** e procure a lista de **recursos**

Os recursos aplicáveis para habilitar as APIs comumente usadas para aplicativos Holographic são:
<br>

|  Funcionalidade  |  APIs que exigem capacidade |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  Integrada  |  VideoCapture e fotocaptura |
|  PicturesLibrary / VideosLibrary  |  VideoCapture, respectivamente (ao armazenar o conteúdo capturado) |
|  Microfone  |  VideoCapture (ao capturar áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (e para usar o criador de perfil do Unity) |

## <a name="see-also"></a>Confira também

* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
* [Noções básicas sobre o desempenho da Realidade Misturada](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)