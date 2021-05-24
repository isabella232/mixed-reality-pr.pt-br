---
title: Estabilização de holograma
description: Desempenho de hologramas em diferentes condições de ambiente e taxa de quadros.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, acompanhamento de ambiente, TMP,
ms.openlocfilehash: 338ae2719764b84b7c58c1422e08fe02176eccf0
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333428"
---
# <a name="hologram-stabilization"></a>Estabilização de holograma

## <a name="performance"></a>Desempenho

Para que a plataforma de realidade misturada subjacente e o dispositivo gerem os melhores resultados, é importante alcançar as taxas de quadros. A taxa de quadros de destino (ex: 60 FPS ou 90 FPS) varia entre plataformas e dispositivos. No entanto, os aplicativos de realidade misturada que atendem a taxa de quadros terão hologramas estáveis, bem como controle de cabeça eficiente, acompanhamento manual e muito mais.  

## <a name="environment-tracking"></a>Rastreamento de ambiente

A renderização de Holographic estável depende muito do controle de representação de cabeçalho pela plataforma & dispositivo. O Unity renderizará a cena que todos os quadros da câmera representam estimados e fornecidos pela plataforma subjacente. Se esse controle não seguir corretamente o movimento de cabeçalho real, os hologramas aparecerão visualmente imprecisos. Isso é especialmente evidente e importante para dispositivos AR como o HoloLens, onde os usuários podem relacionar os hologramas virtuais ao mundo real. O desempenho é significativo para o acompanhamento de carga confiável, mas também pode haver [outros recursos importantes](/windows/mixed-reality/environment-considerations-for-hololens). Os tipos de elementos de ambiente que impactam a experiência do usuário dependerão das especificações de plataforma de destino.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

A plataforma Windows Mixed Reality fornece algum [material de referência](/windows/mixed-reality/hologram-stability) para os hologramas de estabilização na plataforma. Há algumas ferramentas importantes que os desenvolvedores podem utilizar para melhorar a experiência visual do holograma para os usuários.

### <a name="depth-buffer-sharing"></a>Compartilhamento de buffer de profundidade

Os desenvolvedores do Unity têm a opção de compartilhar o buffer de profundidade do aplicativo com a plataforma. Isso fornece informações, onde os hologramas existem para um quadro atual, que a plataforma pode utilizar para estabilizar os hologramas por meio de um processo assistido por hardware, conhecido como Reprojeção Late-Stage.

#### <a name="late-stage-reprojection"></a>Reprojeção de estágio atrasado

No final da renderização de um quadro, a plataforma Windows Mixed Reality assume a cor de destinos de renderização de profundidade & produzidos pelo aplicativo e transforma a saída da tela final para levar em conta qualquer movimento leve de cabeça desde a última previsão de pose de cabeça. O loop de jogo de um aplicativo leva tempo para ser executado. Por exemplo, em 60 FPS, isso significa que o aplicativo está levando cerca de 16,667 ms para renderizar um quadro. Embora isso possa parecer uma quantidade mínima de tempo, a posição e a orientação da cabeça do usuário mudarão, resultando em novas matrizes de projeção para a câmera na renderização. A reprojeção de estágio tardio transforma os pixels na imagem final para levar em conta essa nova perspectiva.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>LSR por pixel versus plano de estabilização

Dependendo do ponto de extremidade do dispositivo e da versão do sistema operacional em execução em um dispositivo Windows Mixed Reality, o algoritmo Late-Stage Reprojection será executado por pixel ou por meio de um plano de [estabilização](/windows/mixed-reality/hologram-stability#stabilization-plane).

##### <a name="per-pixel-depth-based"></a>Baseado em profundidade por pixel

A reprojeção baseada em profundidade por pixel envolve a utilização do buffer de profundidade para modificar a saída da imagem por pixel e, portanto, estabilizar hologramas a várias distâncias. Por exemplo, uma esfera a 1 m de distância pode estar na frente de um pilar que está a 10 m de distância. Os pixels que representam a esfera terão uma transformação diferente dos pixels distantes que representam o pilar se o usuário tiver inclinado ligeiramente a cabeça. A reprojeção por pixel levará em conta essa diferença de distância em cada pixel para uma reprodução mais precisa.

##### <a name="stabilization-plane"></a>Plano de estabilização

Se não for possível criar um buffer de profundidade preciso para compartilhar com a plataforma, outra forma de LSR utilizará um plano de estabilização. Todos os hologramas em uma cena receberão alguma estabilização, mas os hologramas que estão no plano desejado receberão a estabilização máxima de hardware. O ponto e o normal para o plano podem ser fornecidos para a plataforma por meio da API *HolographicSettings.SetFocusPointForFrame* [fornecida pelo Unity.](/windows/mixed-reality/focus-point-in-unity)

#### <a name="depth-buffer-format"></a>Formato de buffer de profundidade

Se tiver como alvo o HoloLens para desenvolvimento, é altamente recomendável utilizar o formato de buffer de profundidade de 16 bits em comparação com o de 24 bits. Isso pode economizar enormemente no desempenho, embora os valores de profundidade tenham menos precisão. Para compensar a precisão mais baixa e evitar o [combate ao z](https://en.wikipedia.org/wiki/Z-fighting), é recomendável reduzir o [plano de clipe distante](https://docs.unity3d.com/Manual/class-Camera.html) do valor padrão 1000m definido pelo Unity.

> [!NOTE]
> Se você estiver usando o *formato de profundidade de 16 bits*, os efeitos necessários do buffer de estêncil não funcionarão porque [o Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. A seleção de *formato de profundidade de 24 bits, por* outro lado, geralmente criará um [buffer de estêncil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html), se aplicável na plataforma de gráficos do ponto de extremidade.

#### <a name="depth-buffer-sharing-in-unity"></a>Compartilhamento de buffer de profundidade no Unity

Para utilizar LSR com base em profundidade, há duas etapas importantes que os desenvolvedores precisam tomar.

1. Em **Editar**  >  **configurações do projeto**, configurações do  >  **Player**  >  **XR**  >  **SDKs de realidade virtual** > habilitar **compartilhamento de buffer de profundidade**
    1. Se estiver direcionando para o HoloLens, é recomendável selecionar **formato de profundidade de 16 bits** também.
1. Ao renderizar a cor na tela, também é possível renderizar a profundidade

O [Gameobjects opaco](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) no Unity geralmente irá gravar em profundidade automaticamente. No entanto, os objetos de texto & transparente geralmente não serão gravados em profundidade por padrão. Se estiver utilizando o sombreador padrão MRTK ou o Text mesh pro, isso poderá ser facilmente remediado.

> [!NOTE]
> Para determinar rapidamente quais objetos em uma cena não gravam no buffer de profundidade visualmente, é possível usar o utilitário de [ *buffer de profundidade de renderização*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) nas configurações do *Editor* no perfil de configuração do MRTK.

##### <a name="transparent-mrtk-standard-shader"></a>Sombreador padrão MRTK transparente

Para materiais transparentes usando o [sombreador padrão MRTK](../features/rendering/MRTK-standard-shader.md), selecione o material para exibi-lo na janela *Inspetor* . Em seguida, clique no botão *corrigir agora* para converter o material para gravação em profundidade (ou seja, Z-gravação ativada).

Antes

![Buffer de profundidade antes de corrigir o sombreador Standard MRTK](../features/images/performance/DepthBufferFixNow_Before.PNG)

After (após)

![MRTK sombreador padrão fixo do buffer de profundidade](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Text Mesh Pro

Para objetos Text Mesh Pro, selecione o GameObject TMP para exibi-lo no inspetor. No componente de material, alternar o sombreador do material atribuído para usar o sombreador TextMeshPro do MRTK.

![Correção de buffer de profundidade pro da malha de texto](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>Sombreador personalizado

Se estiver escrevendo um sombreador personalizado, adicione o  sinalizador [ZWrite](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) à parte superior da definição De passagem do bloco para configurar o sombreador para gravar no buffer de profundidade.

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a>Backings opacos

Se os métodos acima não funcionarem para um determinado cenário (ou seja, usando a interface do usuário do Unity), é possível fazer com que outro objeto escreva no buffer de profundidade. Um exemplo comum é usar o Texto da Interface do Usuário do Unity em um painel flutuante em uma cena. Ao tornar o painel opaco ou, pelo menos, escrever em profundidade, o texto & o painel será estabilizado pela plataforma, pois seus valores z estão tão próximos uns dos outros.

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens)

Além de garantir que as configurações corretas sejam atendidas para garantir a estabilidade visual, é importante garantir que os hologramas permaneçam estáveis em seus locais físicos corretos. Para informar a plataforma sobre locais importantes em um espaço físico, os desenvolvedores podem aproveitar [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) em GameObjects que precisam permanecer em um único lugar. Um [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) é um componente adicionado a um GameObject que assume controle absoluto sobre a transformação desse objeto.

Dispositivos como o HoloLens estão constantemente digitalizando e aprendendo sobre o ambiente. Assim, à medida que o HoloLens rastreia o movimento & posição no espaço, suas estimativas serão atualizadas e o sistema de coordenadas [do Unity ajustado.](/windows/mixed-reality/coordinate-systems-in-unity) Por exemplo, se um GameObject for colocado a 1 m da câmera no início, à medida que o HoloLens acompanha o ambiente, ele poderá perceber que o ponto físico em que o GameObject está localizado está, na verdade, a 1,1 m de distância. Isso resultaria no desa drift do holograma. Aplicar um WorldAnchor a um GameObject permitirá que a âncora controle a transformação do objeto para que o objeto permaneça no local físico correto (ou seja, Atualize para 1.1 m em vez de 1m em tempo de execução). Para manter o [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) entre as sessões de aplicativo, os desenvolvedores podem empregar o [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) para [salvar e carregar WorldAnchors](/windows/mixed-reality/persistence-in-unity).

> [!NOTE]
> Depois que um componente WorldAnchor foi adicionado a um gameobject, não é possível modificar essa transformação do gameobject (ou seja, Transform. Position = x). Um desenvolvedor deve remover o WorldAnchor para editar a transformação.

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

Se você quiser uma alternativa para trabalhar manualmente com âncoras, Confira as ferramentas de bloqueio do Microsoft World. 

> [!div class="nextstepaction"]
> [Instalar com a ferramenta de recurso do Sr](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>Veja também

- [Desempenho](../performance/perf-getting-started.md)
- [Considerações de ambiente para o HoloLens](/windows/mixed-reality/environment-considerations-for-hololens)
- [Instabilidade do holograma Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Ponto de foco no Unity](/windows/mixed-reality/focus-point-in-unity)
- [Sistemas de coordenadas no Unity](/windows/mixed-reality/coordinate-systems-in-unity)
- [Persistência no Unity](/windows/mixed-reality/persistence-in-unity)
- [Entendendo o desempenho da realidade misturada](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Recomendações de desempenho para Unity](/windows/mixed-reality/performance-recommendations-for-unity)