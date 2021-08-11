---
title: Criar modelos 3D para uso em casa
description: requisitos de ativos e diretrizes de criação para modelos 3d a serem usados na Windows Mixed Reality página inicial em fones de ouvido HoloLens e de imersão (VR).
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, modelagem, diretrizes de modelagem, requisitos de ativos, diretrizes de criação, iniciador, iniciador 3D, textura, materiais, complexidade, triângulos, malha, polígonos, policontagem, limites, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 9fdd485c67a757d40b049c08f114ce9982aafc27e9103c4b31c21fd8af08d186
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207676"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Criar modelos 3D para uso em casa

a [Windows Mixed Reality página inicial](../discover/navigating-the-windows-mixed-reality-home.md) é o ponto de partida onde os usuários vão antes de iniciar os aplicativos. ao projetar seu aplicativo para Windows Mixed Reality fones de ouvido, use um [modelo 3d como um inicializador de aplicativo](implementing-3d-app-launchers.md) e coloque [links 3d profundos na página inicial do Windows Mixed Reality](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles). este artigo descreve as diretrizes para a criação de modelos 3d compatíveis com a página inicial do Windows Mixed Reality.

## <a name="asset-requirements-overview"></a>Visão geral dos requisitos de ativo

ao criar modelos 3d para Windows Mixed Reality, há alguns requisitos que todos os ativos devem atender: 
1. [Exportando](#exporting-models) -os ativos devem ser entregues no formato de arquivo. glb (glTF binário)
2. [Modelagem](#modeling-guidelines) -os ativos devem ser inferiores a 10.000 triângulos, não têm mais de 64 nós e 32 submalhas por LOD
3. Os [materiais](#material-guidelines) -texturas não podem ser maiores que 4096 x 4096 e o menor mapa MIP não deve ser maior que 4 em qualquer uma das dimensões
4. [Animação](#animation-guidelines) -as animações não podem ter mais de 20 minutos em 30 FPS (36.000 quadros-chave) e devem conter <= 8192 de destino de Morph
5. [Otimizando](#optimizations) -os ativos devem ser otimizados usando o [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). *necessário nas versões do sistema operacional Windows <= 1709** e recomendado no Windows versões do sistema operacional >= 1803

o restante deste artigo inclui uma visão geral detalhada desses requisitos e diretrizes adicionais para garantir que seus modelos funcionem bem com o Windows Mixed Reality home. 

## <a name="detailed-guidance"></a>Diretrizes detalhadas

### <a name="exporting-models"></a>Exportando modelos

a Windows Mixed Reality home espera que os ativos 3d sejam entregues usando o formato de arquivo. glb com imagens inseridas e dados binários. Glb é a versão binária do formato glTF, que é um padrão aberto isento de royalties para entrega de ativos 3D mantido pelo grupo Khronos. à medida que o glTF evolui como um padrão do setor para conteúdo 3d interoperável, o suporte da Microsoft é para o formato entre aplicativos Windows e experiências. Se você não tiver criado um ativo glTF antes de encontrar uma [lista de exportadores e conversores com suporte](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) na página GitHub do grupo de trabalho do glTF.  

### <a name="modeling-guidelines"></a>Diretrizes de modelagem

Windows espera que os ativos sejam gerados usando as diretrizes de modelagem a seguir para garantir a compatibilidade com a experiência de residência de realidade misturada. Ao modelar em seu programa de sua escolha, tenha em mente as seguintes recomendações e limitações:
1. O eixo para cima deve ser definido como "Y".
2. O ativo deve enfrentar "encaminhar" em direção ao eixo Z positivo.
3. Todos os ativos devem ser criados no plano de chão na origem da cena (0, 0, 0)
4. As unidades de trabalho devem ser definidas como medidores e ativos para que os ativos possam ser criados em escala mundial
5. Todas as malhas não precisam ser combinadas, mas é recomendável se você estiver direcionando dispositivos com restrição de recursos
6. Todas as malhas devem compartilhar um material, com apenas um conjunto de textura usado para todo o ativo
7. UVs deve ser disposta em uma organização quadrada no espaço de 0-1. Evite texturas de divisão, embora elas sejam permitidas.
8. Não há suporte para UVs
9. Não há suporte para materiais de dois lados

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Contagens de triângulos e níveis de detalhes (LODs)

a página inicial do Windows Mixed Reality não dá suporte a modelos com mais de 10.000 triângulos. É recomendável triangular suas malhas antes de exportar para garantir que elas não excedam essa contagem. Windows O Sr também dá suporte a LODs (níveis adicionais de geometria de detalhes) para garantir uma experiência de alto desempenho e de alta qualidade. [O WindowsMRAssetConverter o](https://github.com/Microsoft/glTF-Toolkit/releases) ajudará a combinar 3 versões do seu modelo em um único modelo. glb. Windows determina qual LOD deve ser exibido com base na quantidade de espaço de tela que o modelo está ocupando. Há suporte apenas para três níveis de LOD com as seguintes contagens de triângulo recomendadas:
<br>

|  Nível de LOD  |  Contagem de triângulos recomendada  |  Contagem de triângulo máxima | 
|------|------|------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

### <a name="node-counts-and-submesh-limits"></a>Contagens de nós e limites de submalha

a página inicial do Windows Mixed Reality não dá suporte a modelos com mais de 64 nós ou 32 submalhas por LOD. Os nós são um conceito na [especificação glTF](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) que definem os objetos na cena. As submalhas são definidas na matriz de [primitivos](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) na malha no objeto. 

|  Recurso |  Descrição  |  Máximo com suporte | Documentação |
|------|------|------|------|
|  Nós |  Objetos na cena glTF |  64 por LOD | [Aqui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submalhas |  Soma de primitivos em todas as malhas |  32 por LOD | [Aqui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Diretrizes do material

As texturas devem ser preparadas usando um fluxo de trabalho de commãos de metal de PBR Comece criando um conjunto completo de texturas, incluindo albedo, normal, oclusão, metal e áspero. Windows Mixed Reality dá suporte a texturas com resoluções até 4096x4096, mas é recomendável que você crie em 512x512. As texturas devem ser criadas em resoluções em múltiplos de 4. Esse é um requisito para o formato de compactação aplicado às texturas nas etapas de exportação descritas abaixo. Ao gerar mapas MIP ou uma textura, o MIP mais baixo deve ser um máximo de 4x4.
<br>

|  Tamanho de textura recomendado  |  Tamanho máximo da textura | MIP mais baixo
|----|----|----|
|  512x512  |  4096x4096 | 4x4 máx.|

### <a name="albedo-base-color-map"></a>Mapa de albedo (cor de base)

Cor bruta sem informações de iluminação. Esse mapa também contém as informações de reflexão e difusa para o metal (branco no mapa metálico) e as superfícies do isolador (preto no mapa metálico), respectivamente.

### <a name="normal"></a>Normal

Mapa normal de espaço tangente

### <a name="roughness-map"></a>Mapa de irregularidade

Descreve a microsuperfície do objeto. O White 1,0 é um esboço preto 0,0 é suave. Esse mapa dá ao ativo o maior caractere, pois ele realmente descreve a superfície. Por exemplo, arranhões, impressões digitais, manchas, sujeira e assim por diante.

### <a name="ambient-occlusion-map"></a>Mapa de oclusão de ambiente

Mapa de escala de valor mostrando áreas de obstruído Light, que bloqueia reflexões

### <a name="metallic-map"></a>Mapa metálico

Informa ao sombreador se algo está metal ou não. Metal bruto = 1,0 branco não metal = 0,0 preto. Pode haver valores cinzas em transição que indicam algo que cobre o metal bruto, como sujeira, mas, em geral, esse mapa deve ser apenas preto e branco.

## <a name="optimizations"></a>Otimizações

Windows Mixed Reality home oferece uma série de otimizações sobre a especificação glTF principal definida usando extensões personalizadas. Essas otimizações são necessárias em Windows versões <= 1709 e recomendadas em versões mais recentes do Windows. Você pode otimizar facilmente qualquer modelo glTF 2.0 usando o [Windows Mixed Reality Asset Converter disponível no GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Essa ferramenta executará o empacotamento de textura e otimizações corretos, conforme especificado abaixo. Para uso geral, recomendamos usar o WindowsMRAssetConverter, mas se você precisar de mais controle sobre a experiência e quiser criar seu próprio pipeline de otimização, poderá consultar a especificação detalhada abaixo.  

> [!NOTE]
> Para ver uma lista definitiva de quais são as possibilidades para limites exatos de modelo, consulte o artigo otimização de modelo [3D](/dynamics365/mixed-reality/guides/3d-content-guidelines/optimize-models) para uso em aplicativos do Dynamics 365.

### <a name="materials"></a>Materiais

Para melhorar o tempo de carregamento de ativos em ambientes de Realidade Misturada Windows MR dá suporte à renderização de texturas DDS compactadas empacotadas de acordo com o esquema de empacotamento de textura definido nesta seção. As texturas DDS são referenciadas usando a [extensão MSFT_texture_dds .](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds) A compactação de texturas é altamente recomendada. 

#### <a name="hololens"></a>HoloLens

HoloLens experiências de realidade misturada baseadas em dados esperam que as texturas sejam empacotadas usando uma configuração de duas texturas usando a seguinte especificação de empacotamento:
<br>

|  Propriedade glTF  |  Textura  |  Esquema de empacotamento | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Vermelho (R), Verde (G), Azul (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normal (RG), Aproximação (B), Cinza (A) | 


Ao compactar as texturas DDS, a seguinte compactação é esperada em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Headsets imersivos (VR)

As experiências de Windows Mixed Reality para headsets imersivos (VR) esperam que as texturas sejam empacotadas usando uma configuração de 3 texturas usando a seguinte especificação de empacotamento:

##### <a name="windows-os--1803"></a>Windows Sistema operacional >= 1803

<br>

|  Propriedade glTF  |  Textura  |  Esquema de empacotamento | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Vermelho (R), Verde (G), Azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Oclusão (R), Aproximação (G), Cinza (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Ao compactar as texturas DDS, a seguinte compactação é esperada em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows Sistema operacional <= 1709
<br>

|  Propriedade glTF  |  Textura  |  Esquema de empacotamento | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Vermelho (R), Verde (G), Azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Aproximação (R), Cinza (G), Oclusão (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Ao compactar as texturas DDS, a seguinte compactação é esperada em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Adicionando LODs de malha

Windows O MR usa LODs de nó geometry para renderizar modelos 3D em diferentes níveis de detalhes, dependendo da cobertura na tela. Embora esse recurso tecnicamente não seja necessário, ele é recomendado para todos os ativos. Atualmente, Windows dá suporte a três níveis de detalhes. O LOD padrão é 0, que representa a qualidade mais alta. Outros LODs são numerados sequencialmente, por exemplo, 1, 2 e ficam progressivamente menores em qualidade. O [Windows Mixed Reality Asset Converter](https://github.com/Microsoft/glTF-Toolkit/releases) dá suporte à geração de ativos que atendem a essa especificação de LOD aceitando vários modelos glTF e mesclando-os em um único ativo com níveis de LOD válidos. A tabela a seguir descreve os destinos esperados de ordenação de LOD e triângulo:
<br>

|  Nível lod  |  Contagem de triângulos recomendada  |  Contagem máxima de triângulos | 
|-------|-------|-------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

Ao usar LODs, sempre especifique 3 níveis de LOD. LODs ausentes fará com que o modelo não seja renderizar inesperadamente à medida que o sistema LOD alterna para o nível de LOD ausente. GlTF 2.0 atualmente não dá suporte a LODs como parte da especificação principal. OS LODs devem ser definidos usando a [extensão MSFT_LOD .](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)

### <a name="screen-coverage"></a>Cobertura de tela

OS LODs são exibidos Windows Mixed Reality com base em um sistema orientado pelo valor de cobertura de tela definido em cada LOD. Os objetos que estão consumindo uma parte maior do espaço da tela são exibidos em um nível mais alto de LOD. A cobertura de tela não faz parte da especificação glTF 2.0 principal e deve ser especificada usando MSFT_ScreenCoverage na seção "extras" da extensão [MSFT_lod](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  Nível lod  |  Intervalo recomendado  |  Intervalo padrão | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  0,5 | 
|  LOD 1 |  Menos de 50%-20%  |  0,2 | 
|  LOD 2 |  Menos de 20% a 1%  |  0,01 | 
|  LOD 4  |  Menos de 1%  |  - | 

## <a name="animation-guidelines"></a>Diretrizes de animação

> [!NOTE]
> esse recurso foi adicionado como parte da [atualização Windows 10 de abril de 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018). em versões mais antigas do Windows essas animações não reproduzirão, no entanto, elas ainda serão carregadas se forem criadas de acordo com as diretrizes neste artigo.  

a página de realidade misturada dá suporte a objetos glTF animados em fones de ouvido HoloLens e de imersão (VR). Se você quiser disparar animações em seu modelo, precisará usar a extensão de mapa de animação no formato glTF. Essa extensão permite disparar animações no modelo glTF com base na presença do usuário no mundo, por exemplo, disparar uma animação quando o usuário estiver próximo ao objeto ou enquanto estiver olhando para ele. Se você glTF objeto tem animações, mas não define gatilhos, as animações não serão reproduzidas. A seção a seguir descreve um fluxo de trabalho para adicionar esses gatilhos a qualquer objeto glTF animado.

### <a name="tools"></a>Ferramentas

Primeiro, baixe as ferramentas a seguir se você ainda não as tiver. Essas ferramentas facilitarão a abertura de qualquer modelo glTF, a visualização, a realização de alterações e o salvamento de back como glTF ou. glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Ferramentas de glTF para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Abrindo e visualizando o modelo

Comece abrindo o modelo glTF no VSCode arrastando o arquivo. glTF para a janela do editor. Se você tiver um. glb em vez de um arquivo. glTF, poderá importá-lo no VSCode usando o complemento de ferramentas do glTF que você baixou. Acesse "Exibir-> paleta de comandos" e comece digitando "glTF" na paleta de comandos e selecione "glTF: Import from glb", que exibirá um seletor de arquivos para você importar um. glb com. 

Depois de abrir o modelo glTF, você deverá ver o JSON na janela do editor. Você também pode visualizar o modelo em um visualizador 3D ao vivo usando o clicando com o botão direito do mouse no nome do arquivo e selecionando o atalho do comando "glTF: Visualizar 3D Model" no menu do clique com o botão direito do mouse. 

### <a name="adding-the-triggers"></a>Adicionando os gatilhos

Os gatilhos de animação são adicionados ao modelo glTF JSON usando a extensão de mapa de animação. a extensão de mapa de animação está documentada publicamente [aqui no GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (observação: esta é uma extensão de rascunho). Para adicionar a extensão ao modelo, basta rolar até o final do arquivo glTF no editor e adicionar o bloco "extensionsUsed" e "Extensions" ao arquivo, caso ainda não existam. Na seção "extensionsUsed", você adicionará uma referência à extensão "EXT_animation_map" e no bloco "Extensions", você adicionará seus mapeamentos às animações no modelo.

Conforme observado [na especificação](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) , você define o que dispara a animação usando a cadeia de caracteres "semântica" em uma lista de "animações", que é uma matriz de índices de animação. No exemplo abaixo, especificamos a animação a ser reproduzida enquanto o usuário está nuvens no objeto:

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
a semântica de gatilhos de animação a seguir tem suporte na página inicial do Windows Mixed Reality.  
* "Sempre": loop de uma animação constantemente
* "Retido": em loop durante toda a duração de um objeto ser capturado.
* "Olhar": em loop enquanto um objeto está sendo examinado
* "Proximidade": em loop enquanto um visualizador está próximo de um objeto
* "Apontando": em loop enquanto um usuário está apontando para um objeto

### <a name="saving-and-exporting"></a>Salvando e exportando

Depois de fazer as alterações no modelo glTF, você poderá salvá-lo diretamente como glTF. Você também pode clicar com o botão direito do mouse no nome do arquivo no editor e selecionar "glTF: exportar para GLB (arquivo binário)" para exportar um. glb. 

### <a name="restrictions"></a>Restrições

As animações não podem ter mais de 20 minutos e não podem conter mais de 36.000 quadros-chave (20 minutos a 30 FPS). Além disso, ao usar animações baseadas em destino morph, não exceda 8192 vértices de destino de metamorfose ou menos. exceder essas contagens fará com que o ativo animado não seja suportado na Windows Mixed Reality página inicial. 

|Recurso|Máximo|
|-----|-----|
|Duração|20 minutos|
|Quadros chave|36.000| 
|Vértices de destino de Morph|8192|

## <a name="gltf-implementation-notes"></a>notas de implementação do glTF

Windows O Sr não dá suporte à inversão de geometria usando escalas negativas. A geometria com escalas negativas provavelmente resultará em artefatos visuais.

o ativo glTF deve apontar para a cena padrão usando o atributo scene a ser renderizado pelo Windows MR. além disso, o Windows carregador do sr glTF antes da [atualização Windows 10 abril de 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) **requer** acessadores:
* Deve ter valores mínimo e máximo.
* O tipo escalar deve ser ComponentType UNSIGNED_SHORT (5123) ou UNSIGNED_INT (5125).
* O tipo VEC2 e VEC3 deve ser o ComponentType FLOAT (5126).

As seguintes propriedades de material são usadas na especificação Core glTF 2,0, mas não são necessárias:
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: deve apontar para uma textura armazenada em DDS.
* emissiveTexture: deve apontar para uma textura armazenada em DDS.
* emissiveFactor
* alphamode

As seguintes propriedades de material são ignoradas da especificação principal:
* Todos os UVs
* metalRoughnessTexture: deve usar a embalagem de textura otimizada da Microsoft definida abaixo
* normalTexture: deve usar a embalagem de textura otimizada da Microsoft definida abaixo
* normalScale
* occlusionTexture: deve usar a embalagem de textura otimizada da Microsoft definida abaixo
* occlusionStrength

Windows O Sr não dá suporte a linhas e pontos de modo primitivo. 

Há suporte apenas para um único atributo de vértice UV.

## <a name="more-resources"></a>Mais recursos

* [exportadores e conversores glTF](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [Toolkit glTF](https://github.com/Microsoft/glTF-Toolkit)
* [Especificação do glTF 2,0](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Especificação de extensão do Microsoft glTF LOD](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Especificação de extensões de empacotamento de textura do PC Mixed Reality](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens Especificação de extensões de empacotamento de textura de realidade misturada](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Especificação de extensões glTF do Microsoft DDS Textures](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Confira também

* [Implementar inicializadores de aplicativos 3D (aplicativos UWP)](implementing-3d-app-launchers.md)
* [Implementar inicializadores de aplicativos 3D (aplicativos Win32)](implementing-3d-app-launchers-win32.md)
* [Como navegar na página inicial do Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)