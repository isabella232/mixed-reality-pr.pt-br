---
title: Sombreador padrão MRTK
description: Documentação do MRTKStandardShader
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, sombreador de material
ms.openlocfilehash: 8b570ebb023305cecbeca16b32832417a3f57cce
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145112"
---
# <a name="mrtk-standard-shader"></a>Sombreador padrão MRTK

![Exemplos de sombreador padrão](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

O sistema de sombreamento padrão MRTK utiliza um único sombreador flexível que pode obter visuais semelhantes ao sombreador padrão do Unity, implementar princípios de [sistema de design fluente](https://www.microsoft.com/design/fluent/) e manter o desempenho em dispositivos de realidade misturada.

## <a name="example-scenes"></a>Cenas de exemplo

Você pode encontrar os exemplos de material do sombreador na cena **MaterialGallery** em `MRTK/Examples/Demos/StandardShader/Scenes/` . Todos os materiais nesta cena estão usando o sombreador MRTK/Standard.

![Galeria de materiais](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

Você pode encontrar uma cena de comparação para comparar e testar o sombreador MRTK/Standard em relação ao exemplo de sombreador Unity/Standard na cena **StandardMaterialComparison** em `MRTK/Examples/Demos/StandardShader/Scenes/` .

![Comparação de materiais](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Arquitetura

O sistema de sombreamento MRTK/Standard é um "sombreador Uber" que usa o [recurso variante do programa de sombreador do Unity](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) para gerar automaticamente o código de sombreador ideal com base nas propriedades do material. Quando um usuário seleciona propriedades de material no Inspetor de material, ele só incorre em custo de desempenho para os recursos que eles habilitaram.

## <a name="material-inspector"></a>Inspetor de material

Existe um inspetor de material personalizado para o sombreador MRTK/padrão chamado [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) . O Inspetor Habilita/desabilita automaticamente os recursos do sombreador, com base na seleção do usuário e nos auxílios na configuração do estado de renderização. Para obter mais informações sobre cada recurso **, passe o mouse sobre cada propriedade no editor do Unity para obter uma dica de ferramenta.**

![Inspetor de material](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

A primeira parte do Inspetor controla o estado de renderização do material. O *modo de renderização* determina quando e como um material será renderizado. O objetivo do sombreador MRTK/Standard é espelhar os [modos de renderização encontrados no sombreador do Unity/Standard](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html). O sombreador MRTK/Standard também inclui um modo de renderização *aditivo* e modo de renderização *personalizado* para controle de usuário completo.

| Modo de renderização |         Descrição                                                       |
|----------------|---------------------------------------------------------------------------|
| Opaco         | (Padrão) Adequado para objetos sólidos normais sem áreas transparentes.    |
| Recorte         | Permite a criação de efeitos transparentes que têm bordas duras entre as áreas opacas e transparentes. Nesse modo, não há áreas semi transparentes, a textura é 100% opaca ou invisível. Isso é útil ao usar a transparência para criar a forma de materiais, como reação. |
| Esmaecimento           | Permite que os valores de transparência esmaeçam totalmente um objeto, incluindo quaisquer realças especular ou reflexões que ele possa ter. Esse modo será útil se você quiser animar um objeto esbotão dentro ou fora. Ele não é adequado para renderizar materiais transparentes realistas, como vidro ou vidro transparente, pois as reflexões e realces também serão esbotados. |
| Transparente    | Adequado para renderizar materiais transparentes realistas, como vidro ou vidro transparente. Nesse modo, o material em si assumirá valores de transparência (com base no canal alfa da textura e no alfa da cor da tonalidade). No entanto, as reflexões e realçamentos de iluminação permanecerão visíveis em total clareza, como é o caso com materiais transparentes reais. |
| Aditiva       | Habilita um modo de combinação aditiva, que soma a cor de pixel anterior com a cor de pixel atual. Esse é o modo de transparência preferencial para evitar problemas de classificação de transparência.     |
| Personalizado         | Permite que todos os aspectos do modo de renderização sejam controlados manualmente. Somente para uso avançado.   |

![Renderizando modos](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| Modo de Ressução |             Descrição                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Desativado       | Desabilita a ressarção facial. O descarte só deve ser definido como Off quando uma malha de dois lados é necessária.                                                                                        |
| Front     | Habilita o corte de face frontal.                                                                                                                                                        |
| Voltar      | (Padrão) Habilita [a ressarção facial.](https://en.wikipedia.org/wiki/Back-face_culling) A remoção de face de fundo deve ser habilitada sempre que possível para melhorar o desempenho de renderização. |

## <a name="performance"></a>Desempenho

Uma das principais vantagens de usar o sombreador Standard MRTK sobre o sombreador padrão do Unity é o desempenho. O sombreador padrão MRTK é extensível para utilizar apenas os recursos habilitados. No entanto, o sombreador padrão MRTK também foi escrito para fornecer resultados estética comparáveis como o sombreador padrão do Unity, mas com um custo muito menor. Uma maneira simples de comparar o desempenho do sombreador é por meio do número de operações que precisam ser executadas na GPU. É claro que a magnitude dos cálculos pode flutuar por recursos habilitados e outras configurações de renderização. Mas, em geral, o sombreador padrão do MRTK executa significativamente menos cálculos do que o sombreador padrão do Unity.

Exemplo de estatísticas do sombreador padrão do Unity

![Estatísticas do sombreador padrão do Unity](../images/performance/UnityStandardShader-Stats.PNG)

Exemplo de estatísticas de sombreador padrão MRTK

![Estatísticas do sombreador padrão do MRTK](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> Esses resultados podem ser gerados selecionando e exibindo um [ativo de sombreador](https://docs.unity3d.com/Manual/class-Shader.html) no Inspetor do Unity e, em seguida, clicando no botão *Compilar e mostrar código* .

## <a name="lighting"></a>Iluminação

O MRTK/Standard usa uma aproximação simples para iluminação. Como esse sombreador não calcula a exatidão física e a conservação de energia, ele é renderizado de maneira rápida e eficiente. Blinn-Phong é a técnica de iluminação primária que é combinada com Fresnel e iluminação baseada em imagem para iluminação com base em um aproximado. O sombreador dá suporte às seguintes técnicas de iluminação:

### <a name="directional-light"></a>Luz direcional

O sombreador respeitará a direção, a cor e a intensidade da primeira luz direcional do Unity na cena (se habilitado). Luzes de ponto dinâmico, luzes spot ou qualquer outra luz de Unity não serão consideradas em iluminação em tempo real.

### <a name="spherical-harmonics"></a>Harmônicas esféricas

O sombreador usará investigações leves para luzes aproximadas na cena usando [harmônicas esféricas](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html), se habilitado. Cálculos de harmônicos esféricos são executados por vértice para reduzir o custo de cálculo.

### <a name="lightmapping"></a>Lightmapping

Para iluminação estática, o sombreador respeitará os lightmaps construídos pelo sistema [lightmapping do Unity.](https://docs.unity3d.com/Manual/Lightmapping.html) Basta marcar o renderador como estático (ou lightmap estático) para usar lightmaps.

### <a name="hover-light"></a>Luz de foco

* Consulte [Luz de foco](hover-light.md)

### <a name="proximity-light"></a>Luz de proximidade

* Consulte [Luz de proximidade](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>Suporte ao pipeline de renderização leve com script

O MRTK contém um caminho de atualização para permitir que os desenvolvedores utilizem o LWRP (Lightweight Scriptable Render Pipeline) do Unity com sombreadores do MRTK. Testado no pacote Unity 2019.1.1f1 e Lightweight RP 5.7.2. ou instruções sobre como começar a trabalhar com o LWRP, consulte [esta página](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html).

Para executar a atualização do MRTK, selecione: Kit de Ferramentas de Realidade Misturada **-> Utilitários ->** Atualizar o Sombreador Padrão do MRTK para Pipeline de Renderização Leve

![Atualização de lwrp](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

Depois que a atualização ocorrer, o sombreador MRTK/Standard será alterado e qualquer material de magenta (erro de sombreador) deverá ser corrigido. Para verificar se a atualização ocorreu com êxito, verifique o console para: **Ativos Atualizados/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader** para uso com o Pipeline de Renderização Leve.

## <a name="ugui-support"></a>Suporte à UGUI

O sistema de sombreamento do MRTK Standard funciona com o sistema de interface do usuário [integrado do](https://docs.unity3d.com/Manual/UISystem.html)Unity. Em componentes de interface do usuário do Unity, unity_ObjectToWorld matriz de dados não é a matriz de transformação da transformação local em que o componente Gráfico reside, mas a de sua Tela pai. Muitos efeitos de sombreador MRTK/Standard exigem que a escala de objeto seja conhecida. Para resolver esse problema, o [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) armazenará informações de dimensionamento em atributos de canal UV durante a construção da malha da interface do usuário.

Observe que, ao usar um componente de imagem do Unity, é recomendável especificar "nenhum (Sprite)" para a imagem de origem para impedir que a interface do usuário do Unity gere vértices extras.

Uma tela dentro do MRTK solicitará a adição de um [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) quando um for necessário:

![escalar efeito de malha](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>Combinador de textura

Para melhorar a paridade com o sombreador padrão do Unity por pixel, a suavidade, o emissiva e os valores de oclusão podem ser controlados por meio da [embalagem do canal](http://wiki.polycount.com/wiki/ChannelPacking). Por exemplo:

![exemplo de mapa de canal](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

Ao usar a embalagem de canal, você só precisa criar amostras e carregar uma textura na memória em vez de quatro separadas. Ao escrever seus mapas de textura em um programa como substância ou Photoshop, você pode agrupá-los como o seguinte:

| Canal | Propriedade             |
|---------|----------------------|
| Vermelho     | Metálico             |
| Verde   | Oclusão            |
| Azul    | Emissão (escala de cinza) |
| Alpha   | Suavidade           |

Ou, você pode usar a ferramenta combinador de textura MRTK. Para abrir a ferramenta, selecione: **Kit de ferramentas de realidade mista – utilitários de >-> combinador de textura** , que abrirá a janela abaixo:

![exemplo de combinador de textura](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Essa janela pode ser preenchida automaticamente selecionando um sombreador padrão do Unity e clicando em "preenchimento automático do material padrão". Ou, você pode especificar manualmente uma textura (ou valor constante) por canal vermelho, verde, azul ou alfa. A combinação de textura é acelerada por GPU e não requer que a textura de entrada esteja acessível pela CPU.

## <a name="additional-feature-documentation"></a>Documentação adicional do recurso

Abaixo estão detalhes adicionais sobre alguns detalhes de recursos disponíveis com o sombreador MRTK/padrão.

### <a name="primitive-clipping"></a>Recorte primitivo

![recorte primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* Consulte [Primitivo de recorte](clipping-primitive.md)

### <a name="mesh-outlines"></a>Contornos de malha

Muitas técnicas de contorno de malha são feitas usando uma [técnica de pós-processamento.](https://docs.unity3d.com/Manual/PostProcessingOverview.html) O pós-processamento fornece contornos de excelente qualidade, mas pode ser extremamente caro em muitos dispositivos de Realidade Misturada. Você pode encontrar uma cena que demonstra o uso de contornos de malha na cena  **OutlineExamples** em `MRTK/Examples/Demos/StandardShader/Scenes/` .

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) e [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) podem ser usados para renderizar um contorno em torno de um renderador de malha. A habilitação desse componente introduz uma passagem de renderização adicional do objeto que está sendo descrito, mas foi projetado para ser executado com bom desempenho em dispositivos móveis de Realidade Misturada e não utiliza nenhum processo de postagem. As limitações desse efeito incluem que ele não funciona bem em objetos que não são waterpping (ou que precisam ser dois lados) e problemas de classificação de profundidade podem ocorrer em objetos sobrepostos.

Os comportamentos de contorno são projetados para serem usados em conjunto com o sombreador MRTK/Standard. Os materiais de estrutura geralmente são uma cor clara sólida, mas podem ser configurados para obter uma ampla variedade de efeitos. A configuração padrão de um material de contorno é a seguinte:

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. Gravação de profundidade – deve ser desabilitada para materiais de contorno para garantir que o contorno não impeça a renderização de outros objetos.
2. Vértice– precisa ser habilitado para renderizar o contorno.
3. Usar Smooth Normals – essa configuração é opcional para algumas malhas. Atrução ocorre movendo um vértice ao longo de um vértice normal, em algumas malhas extrudadas ao longo dos normais padrão causará descontinuidades no contorno. Para corrigir essas descontinuidades, marque esta caixa para usar outro conjunto de normais suavizadas que são geradas pelo [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) é um componente que pode ser usado para gerar automaticamente normais suavizados em uma malha. Esse método grupos vértices em uma malha que compartilham o mesmo local no espaço e, em seguida, faz a média dos normais desses vértices. Esse processo cria uma cópia da malha subjacente e deve ser usado somente quando necessário.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. Normalidades suaves geradas por meio de [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) .
2. Normais padrão usadas, observe os artefatos em volta dos cantos do cubo.

### <a name="stencil-testing"></a>Teste de estêncil

Suporte interno de teste de estêncil configurável para alcançar uma ampla gama de efeitos. Como portais:

![teste de estêncil](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>Suporte a cores em instância

O suporte a cores em instância para fornecer milhares de malhas de GPU com instâncias de material exclusivas:

![Propriedades de instância](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Mapeamento de triplanar

O mapeamento de triplanar é uma técnica para textura programaticamente de uma malha. Geralmente usado no terreno, malhas sem UVs ou difícil de desencapsular formas. Essa implementação dá suporte à projeção de espaço local ou mundial, a especificação de suavidade de mesclagem e suporte de mapa normal. Observe que cada textura usada requer três amostras de textura, portanto, use situações de desempenho crítico.

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>Extrusão de vértice

Extrusão de vértice no espaço de mundo. Útil para visualizar volumes de vinculação de extrusão ou transições de entrada/saída.

![escala normal de mapa 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>Diversos

Uma caixa de seleção para controlar otimizações de albedo. Como uma albedo de otimização, as operações são desabilitadas quando nenhuma textura albedo é especificada. Isso é útil para controlar o [carregamento de textura remota](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html).

Basta marcar esta caixa:

![atribuição de albedo](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

As texturas de recorte por pixel, a suavização baseada na borda local e o dimensionamento de mapa normal têm suporte.

![escala normal de mapa 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>Confira também

* [Interativo](../ux-building-blocks/interactable.md)
* [Luz de foco](hover-light.md)
* [Luz de proximidade](proximity-light.md)
* [Primitivo de recorte](clipping-primitive.md)
