---
title: Sombreador padrão do MRTK
description: Documentação do MRTKStandardShader
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, sombreador de Material
ms.openlocfilehash: e740c1cb662f88f7ce925482de9ed758d5f18ee152363a663aa678056ba2825f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191096"
---
# <a name="mrtk-standard-shader"></a>Sombreador padrão do MRTK

![Exemplos de sombreador padrão](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

o sistema de sombreamento padrão MRTK utiliza um único sombreador flexível que pode obter visuais semelhantes ao sombreador padrão do Unity, implementar [Sistema Fluent Design](https://www.microsoft.com/design/fluent/) princípios e manter o desempenho em dispositivos de realidade misturada.

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

| Modo de renderização |         Description                                                       |
|----------------|---------------------------------------------------------------------------|
| Opaco         | Os Adequado para objetos sólidos normais sem áreas transparentes.    |
| Pico         | Permite a criação de efeitos transparentes que têm bordas rígidas entre as áreas opacas e transparentes. Nesse modo, não há áreas transparentes, a textura é de 100% opaca ou invisível. Isso é útil ao usar a transparência para criar a forma de materiais, como vegetação. |
| Esmaecimento           | Permite que os valores de transparência desapareçam completamente um objeto, incluindo quaisquer realces especulares ou reflexos que possam ter. Esse modo será útil se você quiser animar um objeto de esmaecimento ou saída. Não é adequado para renderizar materiais transparentes realistas, como plástico claro ou vidro, pois os reflexões e os destaques também ficarão desbotados. |
| Transparente    | Adequado para renderizar materiais transparentes realistas, como plástico claro ou vidro. Nesse modo, o material por si só assumirá os valores de transparência (com base no canal alfa da textura e no alfa da cor da tonalidade). No entanto, os realces de reflexo e iluminação permanecerão visíveis com clareza total, como é o caso com materiais transparentes reais. |
| Aditiva       | Habilita um modo de mesclagem aditivo, que soma a cor do pixel anterior com a cor atual do pixel. Esse é o modo de transparência preferencial para evitar problemas de classificação de transparência.     |
| Personalizado         | Permite que todos os aspectos do modo de renderização sejam controlados manualmente. Somente para uso avançado.   |

![Renderizando modos](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| Modo de seleção |             Description                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Desativado       | Desabilita a remoção de face. A remoção só deve ser definida como OFF quando uma malha de dois lados é necessária.                                                                                        |
| Front     | Habilita a remoção de face frontal.                                                                                                                                                        |
| Voltar      | Os Permite a [remoção de face de fundo](https://en.wikipedia.org/wiki/Back-face_culling). A remoção de face de fundo deve ser habilitada sempre que possível para melhorar o desempenho de renderização. |

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

O sombreador usará investigações leves para luzes aproximadas na cena usando [harmônicas esféricas](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html), se habilitado. Os cálculos de harmônicas esféricas são executados por vértice para reduzir o custo de cálculo.

### <a name="lightmapping"></a>Lightmapping

Para iluminação estática, o sombreador respeitará o lightmaps criado pelo [sistema Lightmapping](https://docs.unity3d.com/Manual/Lightmapping.html)do Unity. Basta marcar o renderizador como estático (ou lightmap estático) para usar lightmaps.

### <a name="hover-light"></a>Luz de foco

* Confira [luz de foco](hover-light.md)

### <a name="proximity-light"></a>Luz de proximidade

* Confira [luz de proximidade](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>Suporte ao pipeline de processamento com scripts leves

O MRTK contém um caminho de atualização para permitir que os desenvolvedores utilizem o LWRP (Lightweight scripting render Pipeline) leve do Unity com os sombreadores MRTK. Testado no Unity 2019.1.1 F1 e no pacote 5.7.2 leve do RP. ou instruções sobre como começar a usar o LWRP, consulte [esta página](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html).

para executar a atualização do MRTK, selecione: **realidade mista Toolkit-> Utilities-> atualizar o sombreador padrão do MRTK para o Pipeline de renderização leve**

![atualização do lwrp](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

Após a atualização, o sombreador MRTK/Standard será alterado e os materiais magenta (erro de sombreador) deverão ser corrigidos. Para verificar se a atualização ocorreu com êxito, verifique o console para: **ativos atualizados/MixedRealityToolkit/StandardAssets/shaders/MixedRealityStandard. Shader para uso com o pipeline de processamento leve.**

## <a name="ugui-support"></a>Suporte do UGUI

O sistema de sombreamento padrão do MRTK funciona com o [sistema de interface do usuário](https://docs.unity3d.com/Manual/UISystem.html)interno do Unity. Nos componentes da interface do usuário do Unity, a matriz de unity_ObjectToWorld não é a matriz de transformação da transformação local na qual o componente gráfico reside, mas a de sua tela pai. Muitos efeitos de sombreador MRTK/padrão exigem que a escala do objeto seja conhecida. Para resolver esse problema, o [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) armazenará informações de dimensionamento em atributos de canal UV durante a construção da malha da interface do usuário.

Observe que, ao usar um componente de imagem do Unity, é recomendável especificar "nenhum (Sprite)" para a imagem de origem para impedir que a interface do usuário do Unity gere vértices extras.

Uma Tela dentro do MRTK solicitará a adição de um [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) quando for necessário:

![efeito de malha de escala](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>Combinador de textura

Para melhorar a paridade com o sombreador Padrão do Unity por pixel, os valores de smoothness, emissive e occlusion podem ser controlados por meio do empacotamento [de canal](http://wiki.polycount.com/wiki/ChannelPacking). Por exemplo:

![exemplo de mapa de canal](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

Ao usar o empacotamento de canal, você só precisa amostrar e carregar uma textura na memória em vez de quatro separados. Quando você escreve seus mapas de textura em um programa como o Texture ou o Photoshop, você pode empacotá-los manualmente da seguinte forma:

| Canal | Propriedade             |
|---------|----------------------|
| Vermelho     | Metálico             |
| Verde   | Oclusão            |
| Azul    | Emission (Escala de Cinza) |
| Alpha   | Suavidade           |

Ou você pode usar a Ferramenta de Combinador de Textura do MRTK. Para abrir a ferramenta, selecione: Mixed **Reality Toolkit -> Utilities -> Texture Combiner,** que abrirá a janela abaixo:

![Exemplo de combinador de textura](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Essa janela pode ser preenchida automaticamente selecionando um sombreador Padrão do Unity e clicando em "Preenchimento automático do material padrão". Ou você pode especificar manualmente uma textura (ou valor constante) por canal vermelho, verde, azul ou alfa. A combinação de textura é acelerada por GPU e não exige que a textura de entrada seja acessível pela CPU.

## <a name="additional-feature-documentation"></a>Documentação adicional do recurso

Abaixo estão detalhes adicionais sobre alguns detalhes de recursos disponíveis com o sombreador MRTK/Standard.

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
2. Normais padrão usadas, observe os artefatos em torno dos cantos do cubo.

### <a name="stencil-testing"></a>Teste de estêncil

Suporte de teste de estêncil configurável integrado para obter uma ampla variedade de efeitos. Como portais:

![teste de estêncil](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>Suporte a cores em instâncias

Suporte a cores instânciadas para dar milhares de malhas de instância de GPU propriedades de material exclusivas:

![propriedades instânciadas](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Mapeamento de Triplanar

Mapeamento de Triplanar é uma técnica para textura programática de uma malha. Geralmente usado em terrenos, malhas sem UVs ou formas difíceis de desembrulhar. Essa implementação dá suporte à projeção de espaço local ou mundial, à especificação de mesclagem de suavidade e ao suporte normal ao mapa. Observe que cada textura usada requer três amostras de textura, portanto, use com moderação em situações críticas de desempenho.

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>Vértice de vértice

Vértice no espaço do mundo. Útil para visualizar volumes delimitadores extrudados ou transições de malhas de/para fora.

![escala de mapa normal 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>Diversos

Uma caixa de seleção para controlar otimizações de albedo. Como uma otimização, as operações de albedo são desabilitadas quando nenhuma textura de albedo é especificada. Isso é útil para controlar o [carregamento remoto de textura.](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)

Basta marque esta caixa:

![Atribuição de albedo](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

Há suporte para texturas de recorte por pixel, suavização de suavização baseada em borda local e dimensionamento de mapa normal.

![escala de mapa normal 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>Confira também

* [Interativo](../ux-building-blocks/interactable.md)
* [Luz de foco](hover-light.md)
* [Luz de proximidade](proximity-light.md)
* [Primitivo de recorte](clipping-primitive.md)
