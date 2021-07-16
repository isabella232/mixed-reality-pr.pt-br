---
title: Desempenho
description: Documentação para entender e ajustar a preformabilidade no MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 6c8e060af585d7994774ea0bb575b6e5172b9558
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281761"
---
# <a name="performance"></a>Desempenho

## <a name="getting-started"></a>Introdução

A maneira mais fácil de racionalizar o desempenho é por meio de uma taxa de quadros ou quantas vezes seu aplicativo pode renderizar uma imagem por segundo. É importante atender à taxa de quadros de destino, conforme descrito pela plataforma que está sendo direcionada (ou seja, [Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/), etc.). por exemplo, em HoloLens, a taxa de quadros de destino é de 60 FPS. Os aplicativos com taxa de quadros baixa podem resultar em experiências de usuário deterioradas, como [estabilização de holograma](../performance/hologram-stabilization.md)worsened, acompanhamento de mundo, acompanhamento de mão e muito mais. para ajudar os desenvolvedores a acompanharem e alcançarem a taxa de quadros de qualidade, a realidade misturada Toolkit fornece uma variedade de ferramentas e scripts.

### <a name="visual-profiler"></a>Criador de perfil Visual

Para controlar continuamente o desempenho durante o tempo de vida do desenvolvimento, é altamente recomendável mostrar sempre um Visual de taxa de quadros durante a execução & depuração de um aplicativo. a realidade misturada Toolkit fornece a ferramenta de diagnóstico do [Visual profiler](../features/diagnostics/using-visual-profiler.md) que fornece informações em tempo real sobre o uso de memória e FPS atuais na exibição do aplicativo. o criador de perfil do Visual pode ser configurado por meio do [sistema de diagnóstico Configurações](../features/diagnostics/diagnostics-system-getting-started.md) no [inspetor de perfis MRTK](../configuration/mixed-reality-configuration-guide.md).

Além disso, é particularmente importante utilizar o criador de perfil do Visual para rastrear a taxa de quadros durante a execução no dispositivo em oposição à execução no editor do Unity ou em um emulador. Os resultados de desempenho mais precisos serão representados durante a execução no dispositivo com [compilações de configuração de versão](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019).

> [!NOTE]
> se estiver compilando para Windows Mixed Reality, implante com [compilações de configuração mestras](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![Interface do criador de perfil Visual](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>Janela de otimização

A [janela MRTK Optimize](../features/tools/optimize-window.md) oferece informações e ferramentas de automação para ajudar a misturar realidade os desenvolvedores configurarem seus ambientes para obter os melhores resultados de desempenho e identificar possíveis afunilamentos em sua cena & ativos. Determinadas configurações importantes no Unity podem ajudar a fornecer resultados significativamente mais otimizados para projetos de realidade misturada.

Em geral, essas configurações envolvem configurações de renderização ideais para realidade misturada. Os aplicativos de realidade misturada são exclusivos em comparação com o desenvolvimento tradicional de gráficos 3D, pois há duas telas (ou seja, dois olhos) para renderizar para toda a cena.

As configurações recomendadas mencionadas abaixo podem ser configuradas automaticamente em um projeto do Unity aproveitando a janela MRTK optimize.

![MRTK otimizar Configurações de janela](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Criador de perfil do Unity

O [Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html) é uma ferramenta útil para investigar detalhes do desempenho do aplicativo em um nível quadro a quadro.

#### <a name="time-spent-on-the-cpu"></a>Tempo gasto na CPU

![Exemplo de criador de perfil do Unity Graph](../features/images/performance/UnityProfilerGraph.png)

Para manter taxas de quadros confortáveis (geralmente 60 quadros por segundo), os aplicativos precisam atingir um tempo máximo de quadro de 16,6 milissegundos de tempo de CPU. para ajudar a identificar o custo da funcionalidade do MRTK, a realidade misturada da Microsoft Toolkit contém marcadores para caminhos de código de loop interno (por quadro). Esses marcadores usam o seguinte formato, para auxiliar na compreensão da funcionalidade específica que está sendo utilizada:

```
[MRTK] className.methodName
```

> [!Note]
> Pode haver dados adicionais após o nome do método. Isso é usado para identificar uma funcionalidade de execução condicional e potencialmente cara que pode ser evitada por pequenas alterações no código do aplicativo.

![Exemplo de hierarquia do criador de perfil do Unity](../features/images/performance/UnityProfilerHierarchy.png)

Neste exemplo, a hierarquia foi expandida para mostrar que o método UpdateHandData da classe WindowsMixedRealityArticulatedHand está consumindo 0,44 MS de tempo de CPU durante o quadro que está sendo analisado. Esses dados podem ser usados para ajudar a determinar se um problema de desempenho está relacionado ao código do aplicativo ou a partir de outro lugar no sistema.

É altamente recomendável que os desenvolvedores instrumentem o código do aplicativo de maneira semelhante. As principais áreas de foco da instrumentação de código do aplicativo são dentro dos manipuladores de eventos, pois esses métodos são cobrados no loop de atualização do MRTK à medida que os eventos são gerados. Os tempos de quadros altos dentro do loop de atualização MRTK podem ser indícios de um código caro nos métodos do manipulador de eventos.

## <a name="recommended-settings-for-unity"></a>Configurações recomendadas do Unity

### <a name="single-pass-instanced-rendering"></a>Single-Pass renderização de instância

A configuração de renderização padrão para o XR no Unity é [de várias passagens](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html). Essa configuração instrui o Unity a executar todo o pipeline de renderização duas vezes, uma para cada olho. Isso pode ser otimizado selecionando-se a [renderização de passagem única](https://docs.unity3d.com/Manual/SinglePassInstancing.html) em vez disso. Essa configuração aproveita as [matrizes de destino de renderização](https://en.wikipedia.org/wiki/Multiple_Render_Targets) para poder executar uma única chamada de desenho que instâncias para o [destino de renderização](https://en.wikipedia.org/wiki/Render_Target) apropriado para cada olho. Além disso, esse modo permite que todo o processamento seja feito em uma única execução do pipeline de renderização. Portanto, selecionar a renderização de passagem única em instância como o caminho de renderização para um aplicativo de realidade misturada pode [economizar tempo substancial tanto na GPU & da CPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) quanto na configuração de renderização recomendada.

No entanto, para emitir uma única chamada de desenho para cada malha para cada olho, a criação de [instâncias de GPU](https://docs.unity3d.com/Manual/GPUInstancing.html) deve ser suportada por todos os sombreadores. A instanciação permite que a GPU multiplexe chamadas de empates em ambos os olhos. Os sombreadores internos do Unity, bem como o [sombreador padrão do MRTK](../features/rendering/mrtk-standard-shader.md) , contêm as instruções de instanciação necessárias no código do sombreador. Se estiver escrevendo sombreadores personalizados para o Unity, esses sombreadores talvez precisem ser atualizados para dar suporte à renderização de passagem única em instância.

#### <a name="example-code-for-custom-shader"></a>[Exemplo de código para sombreador personalizado](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a>Configurações de qualidade

O Unity fornece [predefinições para controlar a qualidade](https://docs.unity3d.com/Manual/class-QualitySettings.html) de renderização para cada ponto de extremidade de plataforma. Essas predefinições controlam quais recursos gráficos podem ser habilitados, como sombras, suavização de serrilhado, iluminação global e muito mais. É recomendável reduzir essas configurações e otimizar o número de cálculos executados durante a renderização.

*Etapa 1:* Atualizar projetos do Unity da realidade mista para usar a configuração de nível de *baixa qualidade*  
**Editar**  >  **Project Configurações**, em seguida, selecione a categoria **qualidade** > selecione *baixa qualidade* para a plataforma UWP

*Etapa 2:* Para cada arquivo de cena do Unity, desabilite [a iluminação global em tempo real](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**Janela**  >  do **Renderização**  >  **Configurações**  >  de iluminação [Desmarque *a iluminação global em tempo real*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>Compartilhamento de buffer de profundidade (HoloLens)

se estiver desenvolvendo para a plataforma Windows Mixed Reality e, em particular HoloLens, habilitar o *compartilhamento de Buffer de profundidade* em *XR Configurações* poderá ajudar na [estabilização do holograma](../performance/hologram-stabilization.md). No entanto, o processamento do buffer de profundidade pode incorrer em um custo de desempenho, especialmente se estiver usando o [formato de profundidade de 24 bits](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html). Portanto, é *altamente recomendável* configurar o buffer de profundidade para a precisão de 16 bits.

Se o [combate ao z](https://en.wikipedia.org/wiki/Z-fighting) ocorrer devido ao formato de bit inferior, confirme se o plano de [clipe distante](https://docs.unity3d.com/Manual/class-Camera.html) de todas as câmeras está definido com o menor valor possível para o aplicativo. O Unity, por padrão, define um plano de recorte distante de 1000m. em HoloLens, um plano distante de 50 milhões é geralmente mais do que suficiente para a maioria dos cenários de aplicativos.

> [!NOTE]
> Se você estiver usando o *formato de profundidade de 16 bits*, os efeitos necessários do buffer de estêncil não funcionarão porque [o Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. A seleção de *formato de profundidade de 24 bits, por* outro lado, geralmente criará um buffer de estêncil de 8 bits, se aplicável na plataforma de gráficos do ponto de extremidade.
>
> Se estiver usando um [componente de máscara](https://docs.unity3d.com/Manual/script-Mask.html) que requer o buffer de estêncil, considere usar [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) em vez disso, que não requer o buffer de estêncil e, portanto, pode ser usado em conjunto com um formato de *profundidade de 16 bits*.

> [!NOTE]
> para determinar rapidamente quais objetos em uma cena não gravam no buffer de profundidade visualmente, é possível usar o utilitário de [ *buffer de profundidade de renderização*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) sob o *Editor Configurações* no perfil de configuração MRTK.

### <a name="optimize-mesh-data"></a>Otimizar dados de malha

As configurações de [dados de malha de otimização](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) tentam remover atributos de vértice não utilizados em seu aplicativo. A configuração executa isso executando sobre cada passagem de sombreador em cada material que está em cada malha na compilação. Isso é bom para o tamanho dos dados do jogo e o desempenho do tempo de execução, mas pode atrapalhar drasticamente os tempos de compilação.

É recomendável desabilitar essa configuração durante o desenvolvimento e reabilitar durante a criação da compilação "mestre". a configuração pode ser encontrada em **editar**  >  **Project Configurações**  >  **Player**  >  **Configurações**  >  **otimizar dados de malha**.

## <a name="general-recommendations"></a>Recomendações gerais

O desempenho pode ser um desafio ambíguo e em constante mudança para os desenvolvedores de realidade misturada e o espectro de conhecimento para racionalizar o desempenho é vasto. No entanto, há algumas recomendações gerais para entender como abordar o desempenho de um aplicativo.

É útil simplificar a execução de um aplicativo nas partes que são executadas na *CPU* ou na *GPU* e, portanto, identificar se um aplicativo está limitado por qualquer componente.  Pode haver afunilamentos que abrangem ambas as unidades de processamento e alguns cenários exclusivos que precisam ser investigados cuidadosamente. No entanto, para começar, é bom entender onde um aplicativo está sendo executado pela maior quantidade de tempo.

### <a name="gpu-bounded"></a>GPU vinculada

Como a maioria das plataformas para aplicativos de realidade misturada está utilizando a [renderização estereoscópico](https://en.wikipedia.org/wiki/Stereoscopy), é muito comum que haja associação à GPU devido à natureza da renderização de uma tela "de largura dupla". Futhermore, plataformas de realidade mista móvel, como HoloLens ou Oculus Quest, serão limitadas pela CPU de classe móvel & capacidade de processamento de GPU.

Ao se concentrar na GPU, geralmente há dois estágios importantes que um aplicativo deve concluir todos os quadros.

1. Executar o [sombreador de vértice](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. Executar o [sombreador de pixel](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (também conhecido como o sombreador de fragmento)

Sem aprofundar-se no campo complexo de gráficos de computação & [pipelines de renderização](https://en.wikipedia.org/wiki/Graphics_pipeline), cada estágio do sombreador é um programa que é executado na GPU para produzir o seguinte.

1. Os sombreadores de vértice transformam vértices de malha em coordenadas no espaço da tela (ou seja, código executado por vértice)
2. Sombreadores de pixel calculam a cor a ser desenhada para um fragmento de pixel e malha específico (ou seja, execução de código por pixel)

Em relação ao ajuste de desempenho, geralmente é mais proveitosa concentrar-se na otimização das operações no sombreador de pixel. Um aplicativo pode precisar apenas desenhar um cubo que terá apenas 8 vértices. No entanto, o espaço da tela que ocupa o cubo provavelmente está na ordem de milhões de pixels. Portanto, reduzir o código do sombreador por meio de 10 operações pode economizar significativamente mais trabalho se for reduzido no sombreador de pixel do que o sombreador de vértice.

Esse é um dos principais motivos para aproveitar o [sombreador padrão do MRTK](../features/rendering/mrtk-standard-shader.md) , pois esse sombreador geralmente executa muitas instruções por pixel & vértice do que o sombreador padrão do Unity enquanto obtém resultados estética comparáveis.

|    Otimizações de CPU      |             Otimizações de GPU              |
|---------------------------|--------------------------------------------|
| Lógica de simulação de aplicativo      | Operações de renderização |
| Simplificar a física          | Reduzir cálculos de iluminação |
| Simplifique animações       | Reduzir a contagem de polígonos & # de objetos desenháveis |
| Gerenciar coleta de lixo | Reduzir o número de objetos transparentes |
| Referências de cache          | Evitar efeitos de pós-processamento/tela inteira  |

### <a name="draw-call-instancing"></a>Chamar instanciação de chamada

Um dos erros mais comuns no Unity que reduz o desempenho é a clonagem de materiais em tempo de execução. Se GameObjects compartilhar o mesmo material e/ou for a mesma malha, eles poderão ser otimizados em chamadas de desenho único por meio de técnicas como *[envio em lote estático](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, *[envio em lote dinâmico](https://docs.unity3d.com/Manual/DrawCallBatching.html)* e *[instanciação de GPU](https://docs.unity3d.com/Manual/GPUInstancing.html)*. No entanto, se as propriedades modificadas do desenvolvedor do material de um [processador estiver](https://docs.unity3d.com/ScriptReference/Renderer-material.html) em tempo de execução, o Unity criará uma cópia clonada do material atribuído.

Por exemplo, se houver um cubo 100 em uma cena, um desenvolvedor pode querer atribuir uma cor exclusiva a cada em tempo de execução. O acesso de [*Renderer. material. Color*](https://docs.unity3d.com/ScriptReference/Material-color.html) em C# fará com que o Unity crie um novo material na memória para esse renderizador/gameobject específico. Cada um dos cubos 100 terá seu próprio material e, portanto, não poderá ser mesclado em uma chamada de desenho, mas se tornará 100 solicitações de chamada de desenho da CPU para a GPU.

Para superar esse obstáculo e ainda atribuir uma cor exclusiva por cubo, os desenvolvedores devem aproveitar o [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a>Ferramentas de desempenho do Unity

O Unity fornece excelentes ferramentas de desempenho que são criadas no editor.

- [Criador de perfil do Unity](https://docs.unity3d.com/Manual//Profiler.html)
- [Depurador de quadros do Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

Se estimar a compensação de desempenho aproximada entre um sombreador e outro, será útil compilar cada sombreador e exibir o número de operações por estágio do sombreador. Isso pode ser feito selecionando um [ativo de sombreador](https://docs.unity3d.com/Manual/class-Shader.html) e clicando no botão *Compilar e mostrar código* . Isso compilará todas as variantes do sombreador e abrirá o Visual Studio com os resultados. Observação: os resultados da estatística produzidos podem variar dependendo de quais recursos foram habilitados em materiais utilizando o sombreador fornecido. O Unity compilará apenas as variantes do sombreador que estão sendo usadas diretamente no projeto atual.

Exemplo de estatísticas do sombreador padrão do Unity

![Estatísticas do sombreador padrão do Unity 1](../features/images/performance/UnityStandardShader-Stats.PNG)

Exemplo de estatísticas de sombreador padrão MRTK

![MRTK do sombreador padrão 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>Confira também

### <a name="unity"></a>Unity

- [Otimização de desempenho de Unity para iniciantes](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Tutoriais de otimização de desempenho do Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Práticas recomendadas de otimização do Unity](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [Otimizando o desempenho de gráficos](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [Guia prático de otimização móvel](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [Configurações recomendado para o Unity](/windows/mixed-reality/recommended-settings-for-unity)
- [Entendendo o desempenho da realidade misturada](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Recomendações de desempenho para Unity](/windows/mixed-reality/performance-recommendations-for-unity)
- [guia de rastreamento de eventos para Windows Unity](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [Diretrizes de desempenho](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [Ferramentas de desempenho](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>Otimização de malha

- [Otimizar modelos 3D](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Práticas recomendadas para converter e otimizar modelos 3D em tempo real](/dynamics365/mixed-reality/import-tool/best-practices)
