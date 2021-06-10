---
title: Configurações recomendadas do Unity
description: Saiba mais sobre o desempenho e os comportamentos de publicação do Unity específicos para aplicativos de realidade misturada que podem ser alternados por meio das configurações do projeto.
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: unity, configurações, realidade misturada, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, desempenho, configurações de qualidade, configurações de iluminação, buffer de profundidade, xr, perda de acompanhamento
ms.openlocfilehash: 7516ec89c49a12e7cb143d7e53d00efde0e44c4e
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743380"
---
# <a name="recommended-settings-for-unity"></a>Configurações recomendadas do Unity

O Unity fornece um conjunto de opções padrão que geralmente são o caso médio para todas as plataformas. No entanto, o Unity oferece alguns comportamentos específicos da realidade misturada que podem ser alternados por meio das configurações do projeto.

## <a name="performant-environment-set-up"></a>Configuração de ambiente de desempenho

### <a name="low-quality-settings"></a>Configurações de baixa qualidade

É importante modificar as configurações de  Qualidade do **Unity** para Muito Baixo para que seu aplicativo seja executado e seja bem executado na taxa de quadros apropriada, especialmente para o desenvolvimento do HoloLens. Para desenvolvimento em headsets imersivos, dependendo das especificações da área de trabalho que está pendendo da experiência de VR, ainda é possível obter taxa de quadros sem os parâmetros de qualidade mais baixo.

No Unity 2019 LTS+, você pode definir o nível de qualidade do projeto indo para **Editar** Qualidade das Configurações do Projeto e definindo o Padrão clicando na seta para baixo para o nível  >    >   **Nível  de qualidade muito baixo.

### <a name="lighting-settings"></a>Configurações de iluminação

Semelhante às configurações de cena de Qualidade, é importante definir as configurações de Iluminação ideais para seu aplicativo de Realidade Misturada. No Unity, a configuração de Iluminação que geralmente terá o maior impacto no desempenho em sua cena é o **Realtime Global Lighting.** Você pode desativar o Global Lighting indo para **Configurações** de Iluminação de  >  **Renderização** de  >  **Janelas**  >  **Em Tempo Real.**

Há outra configuração de iluminação, **Iluminação Global Desemocarada.** Essa configuração pode fornecer resultados de desempenho e visualmente impressionantes em headsets imersivos, mas não é aplicável ao desenvolvimento do HoloLens. **O Baked Global Só** é calculado para GameObjects estáticos, que não são encontrados em cenas do HoloLens devido à natureza de um ambiente desconhecido e em mudança.

Leia [Global Desajuste do Unity](https://docs.unity3d.com/Manual/GIIntro.html) para obter mais informações. 

>[!NOTE]
> **O Realtime Global Developers** é **definido por cena e,** portanto, os desenvolvedores devem salvar essa propriedade para cada cena do Unity em seu projeto.

### <a name="single-pass-instancing-rendering-path"></a>Caminho de renderização de instanciamento de passagem única

Em aplicativos de Realidade Misturada, a cena é renderizada duas vezes, uma para cada olho do usuário. Em comparação com o desenvolvimento 3D tradicional, isso efetivamente dobra a quantidade de trabalho que precisa ser computada. É importante selecionar o caminho de renderização mais eficiente no Unity para economizar tempo de CPU e GPU. A renderização de instância de passagem única otimiza o pipeline de renderização do Unity para aplicativos de Realidade Misturada e é recomendável habilitar essa configuração por padrão para cada projeto.

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

### <a name="enable-depth-buffer-sharing"></a>Habilitar o compartilhamento de buffer de profundidade

Para obter melhor estabilidade do holograma da percepção do usuário, é recomendável habilitar a propriedade **Compartilhamento** de Buffer de Profundidade no Unity. Ao ligar isso, o Unity compartilhará o mapa de profundidade produzido pelo seu aplicativo com a Windows Mixed Reality plataforma. A plataforma pode otimizar melhor a estabilidade do holograma especificamente para sua cena para qualquer quadro que está sendo renderizado pelo seu aplicativo.

Como habilitar esse recurso no seu projeto do Unity

1) Abra **Configurações de XR do Player** (acesse **Editar** > **Configurações do Projeto** > **Player** > **Configurações de XR**)
2) Marque a caixa de seleção **Habilitar** o Compartilhamento de Buffer de Profundidade em **SDKs** de Realidade Virtual Windows Mixed Reality expansão ( a caixa de seleção Realidade Virtual Com Suporte  >   deve ser marcada)

Além disso, é recomendável selecionar a profundidade  **de 16** bits na configuração Formato de Profundidade neste painel, especialmente para o Desenvolvimento do HoloLens. Selecionar 16 bits em comparação com 24 bits reduzirá significativamente os requisitos de largura de banda, pois menos dados precisarão ser movidos/processados.

Para que a plataforma Windows Mixed Reality otimize a estabilidade do holograma, ela se baseia no buffer de profundidade para ser precisa e corresponder a todos os hologramas renderizados na tela. Portanto, com o compartilhamento de buffer de profundidade, é importante ao renderizar a cor, também renderizar a profundidade. No Unity, a maioria dos materiais Opaque ou TransparentCutout renderizará a profundidade por padrão, mas os objetos transparentes e de texto não renderizarão a profundidade, embora isso dependa do sombreador etc.

Se estiver usando o [sombreador Standard do Kit de Ferramentas de Realidade Misturada,](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)para renderizar a profundidade para objetos transparentes:

1) Selecione o material transparente que está usando o sombreador padrão do MRTK e abra a janela editor inspetor
2) Selecione o **botão Corrigir Agora** dentro do aviso de compartilhamento de buffer de profundidade. Isso também pode ser executado manualmente definindo o Modo de **Renderização** como **Personalizado;** em seguida, **de definir** Modo **como Transparente** e, por **fim, definir Gravação de Profundidade** como **On**

> [!IMPORTANT]
> Os desenvolvedores devem ter cuidado com o Z-fighting ao alterar esses valores junto com as configurações de plano próximo/distante da câmera. O Z-Fighting ocorre quando dois gameobjects tentam renderizar para o mesmo pixel e devido a limitações na fidelidade do buffer de profundidade (ou seja, z depth), o Unity não pode distinguir qual objeto está na frente do outro. Os desenvolvedores observarão uma cintilação entre dois objetos de jogo *à* medida que eles vão para o mesmo valor de profundidade z. Isso pode ser resolvido alternando para o formato de profundidade de 24 bits, pois haverá um intervalo maior de valores para cada objeto calcular quanto à profundidade z da câmera.
>
> No entanto, é recomendável, especialmente para o desenvolvimento do HoloLens, modificar os planos próximos e distantes da câmera para um intervalo menor e manter o formato de profundidade de 16 bits. A profundidade z é mapeada não linearmente para o intervalo de valores ao longo dos planos de câmera próximos e distantes. Isso pode ser modificado  selecionando a Câmera Principal em sua cena e, em **Inspetor,** altere os valores de Plano de Recorte Próximo **&** Distante para reduzir seu intervalo (ou seja, de 1000 m a 100 m ou outro valor x etc.)

>[!IMPORTANT]
> [O Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) ao usar o formato de profundidade de 16 bits. Portanto, alguns efeitos de interface do usuário do Unity e outros efeitos necessários para estêncil não funcionarão, a menos que o formato de profundidade de 24 bits seja selecionado, o que criará um buffer de [estêncil de 8 bits.](https://docs.unity3d.com/Manual/SL-Stencil.html)

### <a name="building-for-il2cpp"></a>Criando para IL2CPP

O Unity preterido o suporte para o back-end de script do .NET e, portanto, recomenda que os desenvolvedores utilizem **IL2CPP** para seus builds do Visual Studio UWP. Embora isso traga várias vantagens, criar sua solução do Visual Studio do Unity para **IL2CPP** pode ser mais lento do que o antigo método .NET. Portanto, é altamente recomendável seguir as práticas recomendadas para criar **IL2CPP** para economizar no tempo de iteração de desenvolvimento.

1) Aproveite a criação incremental criando seu projeto para o mesmo diretório toda vez, reutilizar os arquivos pré-construídos lá
2) Desabilitar verificações de software anti malware para seu projeto & pastas de build
   - Abra **a proteção contra & de vírus** em seu aplicativo de Windows 10 configurações
   - Selecione **Gerenciar Configurações em** **Configurações de proteção contra & vírus**
   - Selecione **Adicionar ou remover exclusões** na seção **Exclusões**
   - Selecione **Adicionar uma exclusão** e selecione a pasta que contém o código do projeto do Unity e as saídas de build
3) Usar um SSD para criação

Leia [Otimizando os tempos de build para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obter mais informações.

> [!NOTE]
> Além disso, pode ser benéfico configurar um [Servidor de Cache](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para projetos do Unity com uma grande quantidade de ativos (excluindo arquivos de script) ou que estejam constantemente alterando cenas/ativos. Ao abrir um projeto, o Unity armazena os ativos qualificados em um formato de cache interno no computador do desenvolvedor. Os itens precisam ser importados novamente e, assim, processados novamente quando modificados. Esse processo pode ser feito uma vez e salvo em um Servidor de Cache e, consequentemente, compartilhado com outros desenvolvedores para economizar tempo, em vez de todos os desenvolvedores processarem a nova importação de novas alterações localmente.

## <a name="publishing-properties"></a>Propriedades de publicação

### <a name="holographic-splash-screen"></a>Tela inicial holográfica

O HoloLens tem uma CPU e GPU de classe móvel, o que significa que os aplicativos podem levar um pouco mais de tempo para carregar. Enquanto o aplicativo estiver sendo carregado, os usuários verão apenas preto e, portanto, poderão se perguntar o que está acontecendo. Para carregá-los durante o carregamento, você pode adicionar uma tela inicial holográfica.

Para alternar a tela inicial holográfica:

1) Vá para **a página Editar**  >  **Configurações do** Projeto  >  **Player**
2) Selecione a **guia Windows Store** e abra a seção Imagem **Inicial**
3) Aplique sua imagem sob a **propriedade Imagem inicial holográfica do Windows > Holographic.**
    - Ativar/desativar a **opção Mostrar Tela Inicial do Unity** habilita ou desabilita a tela inicial com marca do Unity. Se você não tiver uma licença do Unity Pro, a tela inicial da marca Unity sempre será exibida.
    - Se uma **Imagem Inicial Holográfica** for aplicada, ela sempre será exibida se a caixa de seleção Mostrar Tela Inicial do Unity estiver habilitada ou desabilitada. Especificar uma imagem inicial holográfica personalizada só está disponível para desenvolvedores com uma licença do Unity Pro.

|  Mostrar Tela Inicial do Unity  |  Imagem inicial holográfica  |  Comportamento |
|----------|----------|----------|
|  Ativado  |  Nenhum  |  Mostrar a tela inicial padrão do Unity por 5 segundos ou até que o aplicativo seja carregado, o que for mais longo. |
|  Ativado  |  Personalizado  |  Mostrar tela inicial personalizada por 5 segundos ou até que o aplicativo seja carregado, o que for mais longo. |
|  Desativado  |  Nenhum  |  Mostrar preto transparente (Nothing) até que o aplicativo seja carregado. |
|  Desativado  |  Personalizado  |  Mostre a tela inicial personalizada por 5 segundos ou até que o aplicativo seja carregado, o que for maior. |

Leia a [documentação da tela inicial do Unity](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) para obter mais informações.

### <a name="tracking-loss"></a>Controle de perda

Um headset de realidade misturada depende da visualização do ambiente em relação a ele para construir [sistemas de coordenadas com bloqueio mundial](coordinate-systems-in-unity.md), que permitem que os hologramas permaneçam em posição. Quando o headset não consegue se localizar no mundo, diz-se que o fone de ouvido é considerado *perdido*. Nesses casos, a funcionalidade dependente de sistemas de coordenadas bloqueados pelo mundo, como estágios espaciais, âncoras espaciais e mapeamento espacial, não funciona.

Se ocorrer uma perda de controle, o comportamento padrão do Unity será parar de renderizar os hologramas, pausar o [loop do jogo](https://docs.unity3d.com/Manual/ExecutionOrder.html)e exibir uma notificação de rastreamento perdido que siga confortavelmente os usuários olhar. As notificações personalizadas também podem ser fornecidas na forma de uma imagem de perda de rastreamento. Para aplicativos que dependem do acompanhamento de toda a sua experiência, é suficiente deixar que o Unity manipule isso totalmente até que o rastreamento seja readquirido. Os desenvolvedores podem fornecer uma imagem personalizada a ser mostrada durante a perda de controle.

Para personalizar a imagem perdida de rastreamento:

1) Ir para a página Editar configurações do  >  **projeto**  >  
2) Selecione na guia **Windows Store** e abra a seção **imagem de abertura**
3) Aplique a imagem na propriedade de **imagem de perda de > de controle do Windows Holographic** .

#### <a name="opt-out-of-automatic-pause"></a>Recusa de pausa automática

Alguns aplicativos podem não exigir acompanhamento (por exemplo, [aplicativos somente de orientação](coordinate-systems-in-unity.md) , como visualizadores de vídeo de 360 graus) ou talvez precisem continuar o processamento ininterrupto enquanto o rastreamento é perdido. Você pode recusar a perda padrão de comportamento de controle, mas é responsável por ocultar/desabilitar qualquer objeto, o que não será renderizado corretamente em um cenário de perda de rastreamento. Na maioria dos casos, o único conteúdo que é recomendado para ser renderizado nesse caso é o conteúdo de corpo bloqueado, centralizado em toda a câmera principal.

Para recusar o comportamento de pausa automática:

1) Ir para a página **Editar** o  >    >  **Player** de configurações do projeto
2) Selecione a guia **Windows Store** e abra a seção **imagem de abertura**
3) Modifique a caixa de seleção **> do Windows Holographic na pausa de controle de perda e mostrar imagem** .

#### <a name="tracking-loss-events"></a>Rastreando eventos de perda

Para definir o comportamento personalizado quando o rastreamento é perdido, manipule os [eventos de perda de controle](tracking-loss-in-unity.md)global.

### <a name="capabilities"></a>Funcionalidades

Para que um aplicativo aproveite determinadas funcionalidades, ele deve declarar os recursos apropriados em seu manifesto. As declarações de manifesto podem ser feitas no Unity para que elas sejam incluídas em todas as exportações futuras do projeto.

Os recursos podem ser habilitados para um aplicativo de realidade misturada:

1) Ir para a página Editar configurações do  >  **projeto**  >  
2) Selecione a guia **Windows Store** , abra a seção **configurações de publicação** e procure a lista de **recursos**

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