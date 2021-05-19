---
title: Estabilização de holograma
description: Desempenho de hologramas em diferentes condições de ambiente e taxa de quadros.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, acompanhamento de ambiente, TMP,
ms.openlocfilehash: e2c83e7e4ca909e31803d55aabbc0c2344e89139
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143892"
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

No final da renderização de um quadro, a plataforma Windows Mixed Reality usa a cor & profundidade de renderização de destino produzida pelo aplicativo e transforma a saída da tela final para considerar qualquer movimento de cabeça pequeno desde a última previsão de pose de cabeçote. O loop do jogo de um aplicativo leva tempo para ser executado. Por exemplo, às 60 FPS, isso significa que o aplicativo está demorando ~ 16.667 MS para renderizar um quadro. Embora isso possa parecer uma quantidade de tempo miniscule, a posição e a orientação do usuário de sua cabeça serão alteradas, resultando em novas matrizes de projeção para a câmera em renderização. A Reprojeção de etapa tardia transforma os pixels na imagem final para considerar essa nova perspectiva.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>Plano de estabilização vs por pixel LSR

Dependendo do ponto de extremidade do dispositivo e da versão do sistema operacional em execução em um dispositivo Windows Mixed Reality, o algoritmo de Reprojeção Late-Stage será executado por pixel ou por meio de um [plano de estabilização](/windows/mixed-reality/hologram-stability#stabilization-plane).

##### <a name="per-pixel-depth-based"></a>Baseado em profundidade por pixel

A Reprojeção baseada em profundidade por pixel envolve a utilização do buffer de profundidade para modificar a saída da imagem por pixel e, portanto, estabilizar os hologramas em várias distâncias. Por exemplo, uma esfera de 1 e r de esferas pode estar na frente de um pilar que está 10 milhões. Os pixels que representam a esfera terão uma transformação diferente do que os pixels distantes que representam o pilar se o usuário tiver disparado um pouco a cabeça. A Reprojeção por pixel levará em conta essa diferença de distância em cada pixel para uma Reprojeção mais precisa.

##### <a name="stabilization-plane"></a>Plano de estabilização

Se não for possível criar um buffer de profundidade preciso para compartilhar com a plataforma, outra forma de LSR utilizará um plano de estabilização. Todos os hologramas em uma cena receberão alguma estabilização, mas os hologramas que dependem do plano desejado receberão a estabilização máxima de hardware. O ponto e o normal do plano podem ser fornecidos para a plataforma por meio da API *HolographicSettings. SetFocusPointForFrame* [fornecida pelo Unity](/windows/mixed-reality/focus-point-in-unity).

#### <a name="depth-buffer-format"></a>Formato de buffer de profundidade

Se estiver direcionando o HoloLens para desenvolvimento, é altamente recomendável utilizar o formato de buffer de profundidade de 16 bits em comparação com 24 bits. Isso pode economizar muito no desempenho, embora os valores de profundidade tenham menos precisão. Para compensar a precisão mais baixa e evitar o [](https://docs.unity3d.com/Manual/class-Camera.html) [z-fighting](https://en.wikipedia.org/wiki/Z-fighting), é recomendável reduzir o plano de corte distante do valor padrão de 1000 m definido pelo Unity.

> [!NOTE]
> Se estiver usando o formato de profundidade de *16* bits, os efeitos necessários do buffer de estêncil não funcionarão porque o Unity não cria um buffer de [estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. Selecionar o formato de profundidade de *24* bits geralmente criará um buffer de estêncil de [8 bits,](https://docs.unity3d.com/Manual/SL-Stencil.html)se aplicável na plataforma de gráficos do ponto de extremidade.

#### <a name="depth-buffer-sharing-in-unity"></a>Compartilhamento de buffer de profundidade no Unity

Para utilizar a LSR baseada em profundidade, há duas etapas importantes que os desenvolvedores precisam seguir.

1. Em **Editar**  >  **Configurações do Projeto Configurações do**  >  **Player**  >  **XR,** os SDKs de Realidade Virtual >  >   Habilitar o **Compartilhamento de Buffer de Profundidade**
    1. Se estiver direcionando o HoloLens, é recomendável selecionar o formato de profundidade de **16** bits também.
1. Ao renderizar a cor na tela, a profundidade de renderização também

[GameObjects opacos](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) no Unity geralmente gravarão em profundidade automaticamente. No entanto, objetos & de texto transparente geralmente não serão escritos em profundidade por padrão. Se estiver utilizando o Sombreador Padrão do MRTK ou o Text Mesh Pro, isso poderá ser facilmente corrigido.

> [!NOTE]
> Para determinar rapidamente quais objetos em uma cena não são *escritos* no buffer de profundidade visualmente, é possível usar o utilitário [ *Buffer*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) de Profundidade de Renderização nas Configurações do Editor no perfil configuração do MRTK.

##### <a name="transparent-mrtk-standard-shader"></a>Sombreador padrão transparente do MRTK

Para materiais transparentes usando o [sombreador padrão do MRTK,](../features/rendering/MRTK-standard-shader.md)selecione o material para exibi-lo na *janela Inspetor.* Em seguida, *clique no botão Corrigir* Agora para converter o material para gravar em profundidade (ou seja, Z-Write On).

Antes

![Buffer de profundidade antes de corrigir o sombreador padrão do MRTK](../features/images/performance/DepthBufferFixNow_Before.PNG)

Depois

![Sombreador padrão mrtk de buffer de profundidade fixo](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Malha de texto pro

Para objetos pro de malha de texto, selecione o TMP gameobject para exibi-lo no Inspetor. No componente material, alterne o sombreador para o material atribuído para usar o sombreador MRTK TextMeshPro.

![Correção de buffer de profundidade do pro de malha de texto](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>Sombreador personalizado

Se estiver escrevendo um sombreador personalizado, adicione o [sinalizador ZWrite](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) à parte superior da definição de bloco *Pass* para configurar o sombreador para gravar no buffer de profundidade.

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

##### <a name="opaque-backings"></a>Backups opacos

Se os métodos acima não funcionarem para um determinado cenário (ou seja, usando a interface do usuário do Unity), é possível ter outro objeto gravado no buffer de profundidade. Um exemplo comum é usar o texto da interface do usuário do Unity em um painel flutuante em uma cena. Ao tornar o painel opaco ou, pelo menos, gravar em profundidade, o texto & painel será estabilizado pela plataforma, já que seus valores z são tão próximos uns dos outros.

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens)

Além de garantir que as configurações corretas sejam atendidas para garantir a estabilidade Visual, é importante garantir que os hologramas permaneçam estáveis em seus locais físicos corretos. Para informar a plataforma em locais importantes em um espaço físico, os desenvolvedores podem aproveitar o [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) no Gameobjects que precisam permanecer em um só lugar. Um [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) é um componente adicionado a um gameobject que assume o controle absoluto sobre a transformação desse objeto.

Dispositivos como o HoloLens estão constantemente digitalizando e aprendendo sobre o ambiente. Assim, como o HoloLens acompanha a movimentação & posição no espaço, suas estimativas serão atualizadas e o [sistema de coordenadas do Unity será ajustado](/windows/mixed-reality/coordinate-systems-in-unity). Por exemplo, se um gameobject é colocado 1 m da câmera na inicialização, como o HoloLens rastreia o ambiente, ele pode perceber que o ponto físico onde o gameobject está localizado é, na verdade, a 1,1 m. Isso resultaria na descompasso do holograma. Aplicar um WorldAnchor a um gameobject permitirá que a âncora controle a transformação do objeto para que o objeto permaneça no local físico correto (ou seja, atualize para 1,1 m de distância em vez de 1 m em runtime). Para [persistir WorldAnchors entre](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) sessões de aplicativo, os desenvolvedores podem [empregar o WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) para [salvar e carregar o WorldAnchors.](/windows/mixed-reality/persistence-in-unity)

> [!NOTE]
> Depois que um componente WorldAnchor tiver sido adicionado a um GameObject, não será possível modificar a transformação desse GameObject (ou seja, transform.position = x). Um desenvolvedor deve remover o WorldAnchor para editar a transformação.

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

Se você quiser uma alternativa para trabalhar manualmente com Âncoras, confira As Ferramentas de Bloqueio do Microsoft World. 

> [!div class="nextstepaction"]
> [Instal with the MR Feature Tool](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>Veja também

- [Desempenho](../performance/perf-getting-started.md)
- [Considerações sobre o ambiente para HoloLens](/windows/mixed-reality/environment-considerations-for-hololens)
- [Estabilidade do holograma Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Ponto de foco no Unity](/windows/mixed-reality/focus-point-in-unity)
- [Sistemas de coordenadas no Unity](/windows/mixed-reality/coordinate-systems-in-unity)
- [Persistência no Unity](/windows/mixed-reality/persistence-in-unity)
- [Noções básicas sobre o desempenho da realidade misturada](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Recomendações de desempenho para Unity](/windows/mixed-reality/performance-recommendations-for-unity)