---
title: Estabilização do holograma
description: Desempenho de hologramas em diferentes condições de ambiente e taxa de quadros.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Acompanhamento de ambiente, TMP,
ms.openlocfilehash: 7aab167f2d850a4bca88a2cc40aae4f3cc50fb4b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176486"
---
# <a name="hologram-stabilization"></a>Estabilização do holograma

## <a name="performance"></a>Desempenho

Para que a plataforma de realidade misturada subjacente e o dispositivo produzam os melhores resultados, é importante obter taxas de quadros de desempenho. A taxa de quadros de destino (por ex. 60 FPS ou 90 FPS) variará entre plataformas e dispositivos. No entanto, os aplicativos de realidade misturada que atenderem à taxa de quadros terão hologramas estáveis, bem como acompanhamento de cabeça eficiente, acompanhamento de mão e muito mais.  

## <a name="environment-tracking"></a>Acompanhamento de ambiente

A renderização holográfica estável depende muito do acompanhamento de pose de cabeça pela plataforma & dispositivo. O Unity renderizará a cena a cada quadro da câmera, que são estimados e fornecidos pela plataforma subjacente. Se esse acompanhamento não seguir corretamente o movimento real da cabeça, os hologramas aparecerão visualmente imprecisos. Isso é especialmente evidente e importante para dispositivos AR como HoloLens em que os usuários podem relacionar hologramas virtuais ao mundo real. O desempenho é significativo para o acompanhamento de cabeça confiável, mas também [pode haver outros](/windows/mixed-reality/environment-considerations-for-hololens)recursos importantes. Os tipos de elementos de ambiente que impactam a experiência do usuário dependerão das especificações da plataforma de alvo.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

A Windows Mixed Reality de dados fornece algum [material de referência](/windows/mixed-reality/hologram-stability) para estabilizar hologramas na plataforma. No entanto, há algumas ferramentas importantes que os desenvolvedores podem utilizar para melhorar a experiência visual do holograma para os usuários.

### <a name="depth-buffer-sharing"></a>Compartilhamento de buffer de profundidade

Os desenvolvedores do Unity têm a opção de compartilhar o buffer de profundidade do aplicativo com a plataforma. Isso fornece informações, em que os hologramas existem para um quadro atual, que a plataforma pode utilizar para estabilizar hologramas por meio de um processo assistido por hardware conhecido como Late-Stage Reprojection.

#### <a name="late-stage-reprojection"></a>Reprodução de estágio tardio

No final da renderização de um quadro, a plataforma Windows Mixed Reality leva a cor de destinos de renderização de profundidade & produzidos pelo aplicativo e transforma a saída da tela final para levar em conta qualquer pequeno movimento de cabeça desde a última previsão de pose de cabeça. O loop de jogo de um aplicativo leva tempo para ser executado. Por exemplo, em 60 FPS, isso significa que o aplicativo está levando cerca de 16,667 ms para renderizar um quadro. Embora isso possa parecer uma quantidade mínima de tempo, a posição e a orientação da cabeça do usuário mudarão, resultando em novas matrizes de projeção para a câmera na renderização. A reprojeção de estágio tardio transforma os pixels na imagem final para levar em conta essa nova perspectiva.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>LSR por pixel versus plano de estabilização

Dependendo do ponto de extremidade do dispositivo e da versão do sistema operacional em execução em um dispositivo Windows Mixed Reality, o algoritmo Late-Stage Reprojection será executado por pixel ou por meio de um plano de [estabilização](/windows/mixed-reality/hologram-stability#stabilization-plane).

##### <a name="per-pixel-depth-based"></a>Baseado em profundidade por pixel

A reprojeção baseada em profundidade por pixel envolve a utilização do buffer de profundidade para modificar a saída da imagem por pixel e, portanto, estabilizar hologramas a várias distâncias. Por exemplo, uma esfera a 1 m de distância pode estar na frente de um pilar que está a 10 m de distância. Os pixels que representam a esfera terão uma transformação diferente dos pixels distantes que representam o pilar se o usuário tiver inclinado ligeiramente a cabeça. A reprojeção por pixel levará em conta essa diferença de distância em cada pixel para uma reprodução mais precisa.

##### <a name="stabilization-plane"></a>Plano de estabilização

Se não for possível criar um buffer de profundidade preciso para compartilhar com a plataforma, outra forma de LSR utilizará um plano de estabilização. Todos os hologramas em uma cena receberão alguma estabilização, mas os hologramas que estão no plano desejado receberão a estabilização máxima de hardware. O ponto e o normal para o plano podem ser fornecidos para a plataforma por meio da API *HolographicSettings.SetFocusPointForFrame* [fornecida pelo Unity.](/windows/mixed-reality/focus-point-in-unity)

#### <a name="depth-buffer-format"></a>Formato de buffer de profundidade

Se o direcionamento HoloLens desenvolvimento, é altamente recomendável utilizar o formato de buffer de profundidade de 16 bits em comparação com 24 bits. Isso pode economizar muito no desempenho, embora os valores de profundidade tenham menos precisão. Para compensar a precisão mais baixa e evitar o [](https://docs.unity3d.com/Manual/class-Camera.html) [z-fighting](https://en.wikipedia.org/wiki/Z-fighting), é recomendável reduzir o plano de corte distante do valor padrão de 1000 m definido pelo Unity.

> [!NOTE]
> Se estiver usando o formato de profundidade de *16* bits, os efeitos necessários do buffer de estêncil não funcionarão porque o Unity não cria um buffer de [estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. Selecionar o formato de profundidade de *24* bits geralmente criará um buffer de estêncil de [8 bits,](https://docs.unity3d.com/Manual/SL-Stencil.html)se aplicável na plataforma de gráficos do ponto de extremidade.

#### <a name="depth-buffer-sharing-in-unity"></a>Compartilhamento de buffer de profundidade no Unity

Para utilizar a LSR baseada em profundidade, há duas etapas importantes que os desenvolvedores precisam seguir.

1. Em **Editar**  >  **Project Configurações**  >  **Player**  >  **XR Configurações** SDKs de Realidade  >  **Virtual** > habilitar o **compartilhamento de buffer de profundidade**
    1. Se estiver direcionando HoloLens, é recomendável selecionar o formato de profundidade de **16** bits também.
1. Ao renderizar a cor na tela, a profundidade de renderização também

[GameObjects opacos](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) no Unity geralmente gravarão em profundidade automaticamente. No entanto, objetos & de texto transparente geralmente não serão escritos em profundidade por padrão. Se estiver utilizando o Sombreador Padrão do MRTK ou a malha de texto Pro, isso poderá ser facilmente corrigido.

> [!NOTE]
> Para determinar rapidamente quais objetos em uma cena não são escritos no buffer de profundidade visualmente, é possível usar o utilitário [ *Buffer*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) de Profundidade de Renderização no *editor Configurações* no perfil configuração do MRTK.

##### <a name="transparent-mrtk-standard-shader"></a>Sombreador padrão transparente do MRTK

Para materiais transparentes usando o [sombreador padrão do MRTK,](../features/rendering/MRTK-standard-shader.md)selecione o material para exibi-lo na *janela Inspetor.* Em seguida, *clique no botão Corrigir* Agora para converter o material para gravar em profundidade (ou seja, Z-Write On).

Antes

![Buffer de profundidade antes de corrigir o sombreador padrão do MRTK](../features/images/performance/DepthBufferFixNow_Before.PNG)

After (após)

![Sombreador padrão mrtk de buffer de profundidade fixo](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Malha de texto Pro

Para Objetos de Pro texto, selecione o GameObject TMP para exibi-lo no inspetor. No componente de material, alternar o sombreador do material atribuído para usar o sombreador TextMeshPro do MRTK.

![Correção do buffer de Pro texto](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

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

Dispositivos como HoloLens estão constantemente digitalizando e aprendendo sobre o ambiente. Assim, à medida que HoloLens o movimento & posição no espaço, suas estimativas serão atualizadas e o sistema de coordenadas [do Unity ajustado.](/windows/mixed-reality/coordinate-systems-in-unity) Por exemplo, se um GameObject for colocado a 1 m da câmera no início, à medida que o HoloLens rastreia o ambiente, ele poderá perceber que o ponto físico em que o GameObject está localizado está, na verdade, a 1,1 m de distância. Isso resultaria no desa drift do holograma. Aplicar um WorldAnchor a um GameObject permitirá que a âncora controle a transformação do objeto para que o objeto permaneça no local físico correto (ou seja, atualize para 1,1 m de distância em vez de 1 m em runtime). Para [persistir WorldAnchors entre](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) sessões de aplicativo, os desenvolvedores podem [empregar o WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) para [salvar e carregar o WorldAnchors.](/windows/mixed-reality/persistence-in-unity)

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
> [Instalar com a Ferramenta de Recursos do MR](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>Veja também

- [Desempenho](../performance/perf-getting-started.md)
- [Considerações sobre ambiente para HoloLens](/windows/mixed-reality/environment-considerations-for-hololens)
- [Estabilidade do holograma Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Ponto de foco no Unity](/windows/mixed-reality/focus-point-in-unity)
- [Sistemas de coordenadas no Unity](/windows/mixed-reality/coordinate-systems-in-unity)
- [Persistência no Unity](/windows/mixed-reality/persistence-in-unity)
- [Noções básicas sobre o desempenho da realidade misturada](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Recomendações de desempenho para Unity](/windows/mixed-reality/performance-recommendations-for-unity)
