---
title: Reconhecimento de cena
description: Saiba como desenvolver com a compreensão de cena para o HoloLens, incluindo o SDK, as funcionalidades e os cenários de uso comuns.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Compreensão de cena, Mapeamento Espacial, Windows Mixed Reality, Unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, oclusão, SDK
ms.openlocfilehash: dd54be85ed71c3359408c02914470e97ab42b90e
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196391"
---
# <a name="scene-understanding"></a>Reconhecimento de cena

A compreensão de cena fornece aos desenvolvedores de Realidade Misturada uma representação de ambiente estruturada e de alto nível projetada para tornar o desenvolvimento para aplicativos com conhecimento ambiental intuitivo. A compreensão de cena faz isso combinando o poder dos runtimes [](spatial-mapping.md) de realidade misturada existentes, como o mapeamento espacial altamente preciso, mas menos estruturado e os novos runtimes orientados por IA. Combinando essas tecnologias, a compreensão de cena gera representações de ambientes 3D semelhantes aos que você pode ter usado em estruturas como Unity ou ARKit/ARCore. O ponto de entrada Noções básicas de cena começa com um Observador de Cena, que é chamado pelo seu aplicativo para calcular uma nova cena. Atualmente, a tecnologia pode gerar três categorias de objeto distintas, mas relacionadas:

* Malhas simplificadas do ambiente watershes que inferem a estrutura da sala planar sem confusão
* Regiões de plano para posicionamento que chamamos de Quads
* Um instantâneo da malha [de mapeamento](spatial-mapping.md) espacial que se alinha com os dados Quads/Water spatial que superfíciemos

![Malha de mapeamento espacial, superfícies planar rotuladas, malha water spatial](images/SUScenarios.png)

Este documento destina-se a fornecer uma visão geral do cenário e esclarecer a relação que a Compreensão de cena e o mapeamento espacial compartilham. Se você quiser ver o Reconhecimento de Cena em ação, confira nossa demonstração de vídeo **Designing Holograms – Spatial Awareness** abaixo:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Este vídeo foi tirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui.](https://aka.ms/dhapp)*

## <a name="developing-with-scene-understanding"></a>Desenvolvendo com o Entendimento de Cena

Este artigo serve apenas para introduzir o runtime e os conceitos do Scene Understanding. Se você estiver procurando documentação sobre como desenvolver com a compreensão da cena, talvez esteja interessado nos seguintes artigos:

[Visão geral do SDK de compreensão da cena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

Você pode baixar o aplicativo de exemplo de compreensão da cena no site do GitHub de exemplo:

[Exemplo de compreensão da cena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Se você não tiver um dispositivo e desejar acessar cenas de exemplo para experimentar a compreensão da cena, há cenas na pasta de ativos de exemplo:

[Cenas de exemplo de compreensão de cena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>.

Se você estiver procurando detalhes específicos sobre o desenvolvimento com a compreensão da cena, consulte a documentação [visão geral do SDK de compreensão da cena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) .

### <a name="sample"></a>Amostra

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Reconhecimento de cena</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>Cenários de uso comuns

![Ilustrações de cenários de uso de mapeamento espacial comum: posicionamento, oclusão, física e navegação](images/sm-concepts-1000px.png)<br>
*Cenários de uso de mapeamento espacial comum: posicionamento, oclusão, física e navegação.*

<br>

Muitos dos principais cenários para aplicativos com reconhecimento de ambiente podem ser abordados pelo mapeamento espacial e pelo entendimento da cena. Esses cenários principais incluem posicionamento, oclusão, física e assim por diante. Uma diferença importante entre a compreensão da cena e o mapeamento espacial é uma compensação da precisão e da latência máximas até a estrutura e a simplicidade. Se seu aplicativo exigir a menor latência possível e os triângulos de malha que só você deseja acessar, use o mapeamento espacial diretamente. Se estiver fazendo um processamento de nível superior, você pode considerar mudar para o modelo de compreensão da cena, pois ele deve fornecer um superconjunto de funcionalidades. Você sempre terá acesso aos dados de mapeamento espacial mais completos e precisos, pois a compreensão da cena fornece um instantâneo da malha de mapeamento espacial como parte de sua representação.

As seções a seguir revisitam os cenários principais de mapeamento espacial no contexto da nova cena que entende o SDK.

### <a name="placement"></a>Posicionamento

A compreensão da cena fornece novas construções projetadas para simplificar os cenários de posicionamento. Uma cena pode computar primitivos chamados SceneQuads, que descrevem superfícies simples nas quais os hologramas podem ser colocados. SceneQuads foram projetados em torno do posicionamento e descrevem uma superfície 2D e fornecem uma API para posicionamento nessa superfície. Anteriormente, ao usar a malha de triângulo para fazer o posicionamento, era preciso verificar todas as áreas do quad e fazer o preenchimento/pós-processamento de orifícios para identificar bons locais para posicionamento de objeto. Isso nem sempre é necessário com o Quads, pois a compreensão de cena de runtime infere quais áreas quad não foram examinadas e invalida áreas que não fazem parte da superfície.

:::row:::
    :::column:::
       ![SceneQuads com inferência desabilitada, capturando áreas de posicionamento para regiões examinadas.](images/SUQuads.png)<br>
       **Imagem #1** – SceneQuads com inferência desabilitada, capturando áreas de posicionamento para regiões examinadas.
    :::column-end:::
        :::column:::
       ![Quads com inferência habilitada, o posicionamento não está mais limitado a áreas examinadas.](images/SUWatertight.png)<br>
        **Imagem #2** - Quads com inferência habilitada, o posicionamento não está mais limitado a áreas examinadas.
    :::column-end:::
:::row-end:::

<br>


Se seu aplicativo pretende colocar hologramas 2D ou 3D em estruturas rígidas do seu ambiente, a simplicidade e a [](spatial-mapping.md) conveniência do SceneQuads para posicionamento são preferíveis à computação dessas informações da malha de mapeamento espacial. Para obter mais informações sobre este tópico, consulte a Referência [do SDK de compreensão de cena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

**Observação** Para o código de posicionamento herdado que depende da malha de mapeamento espacial, a malha de mapeamento espacial pode ser computada junto com SceneQuads definindo a configuração EnableWorldMesh. Se a API de Compreensão de Cena não atender aos requisitos de latência do aplicativo, recomendamos que você continue a usar a [API de mapeamento espacial](spatial-mapping.md#placement).

### <a name="occlusion"></a>Oclusão

[A oclusão de mapeamento espacial](spatial-mapping.md#occlusion) permanece a maneira menos latente de capturar o estado em tempo real do ambiente. Embora isso possa ser útil para fornecer oclusão em cenas altamente dinâmicas, talvez você queira considerar a Compreensão de cena para oclusão por vários motivos. Se você usar a malha de mapeamento espacial gerada pelo Entendimento de Cena, poderá solicitar dados do mapeamento espacial que não seriam armazenados no cache local e não estão disponíveis nas APIs de percepção. Usar o mapeamento espacial para oclusão juntamente com malhas Watertight fornecerá valor extra, especificamente a conclusão da estrutura de sala não verificada.

Se seus requisitos puderem tolerar a maior latência de compreensão da cena, os desenvolvedores de aplicativos devem considerar o uso da malha de compreensão Watertight da cena e a malha de mapeamento espacial em harmonia com representações planares. Isso forneceria um cenário "o melhor de ambos os mundos", em que simplificava a Watertight oclusão é casado com uma geometria mais realista que fornece os mapas oclusão mais realistas possíveis.

### <a name="physics"></a>Física

O entendimento da cena gera malhas Watertight que decompõem o espaço com a semântica, especificamente para resolver muitas limitações na física que as malhas de mapeamento espacial impõem. As estruturas Watertight garantem que as conversões de raio de física sejam sempre pressionadas, e a decomposição semântica permite uma geração mais simples de malhas de NAV para navegação em interno. Conforme descrito na seção sobre [oclusão](#occlusion), a criação de uma cena com EnableSceneObjectMeshes e EnableWorldMesh produzirá a malha de conclusão mais física possível. A propriedade Watertight da malha do ambiente impede que testes de colisão falhem nas superfícies. Os dados de malha garantirão que a física esteja interagindo com todos os objetos da cena e não apenas com a estrutura de salas.

### <a name="navigation"></a>Navegação

As malhas de planar decomposta por classe semântica são construções ideais para navegação e planejamento de caminho, facilitando muitos dos problemas descritos na visão geral de [navegação de mapeamento espacial](spatial-mapping.md#navigation) . Os objetos SceneMesh computados na cena são descompostos por tipo de superfície, garantindo que a geração de malha de NAV seja limitada a superfícies que podem ser performadas. Devido à simplicidade das estruturas baixas, a geração de malha de navegação dinâmica em mecanismos 3D, como o Unity, é atingível dependendo dos requisitos em tempo real.

A geração de malhas de navegação precisas ainda requer pós-processamento, ou seja, os aplicativos ainda precisam projetar occluders no chão para garantir que a navegação não passe por resíduos/tabelas e assim por diante. A maneira mais precisa de fazer isso é projetar os dados de malha do mundo, que serão fornecidos se a cena for computada com o sinalizador EnableWorldMesh.

### <a name="visualization"></a>Visualização

Embora [a visualização](spatial-mapping.md#visualization) de mapeamento espacial possa ser usada para comentários em tempo real do ambiente, há muitos cenários em que a simplicidade dos objetos planar e waterfast fornece mais desempenho ou qualidade visual. As técnicas de projeção de sombra e de moagem descritas usando o mapeamento espacial podem ser mais desagradadas se projetadas nas superfícies planar fornecidas pelo Quads ou pela malha de water seta planora. Isso é especialmente verdadeiro para ambientes/cenários em que a pré-verificação completa não é ideal porque a cena inferiria e ambientes completos e suposições planar minimizarão os artefatos.

Além disso, o número total de superfícies retornadas pelo Mapeamento Espacial é limitado pelo cache espacial interno, enquanto a versão da compreensão de cena da malha mapeamento espacial pode acessar dados de mapeamento espacial que não são armazenados em cache. Por isso, a Compreensão de cena é mais adequada para capturar representações de malha para espaços maiores (por exemplo, maiores que uma única sala) para visualização ou processamento de malha posterior. A malha mundial retornada com EnableWorldMesh terá um nível consistente de detalhes, o que pode gerar uma visualização mais agradável se renderizada como wireframe.

### <a name="see-also"></a>Consulte Também

* [SDK de compreensão de cena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [Mapeamento espacial](spatial-mapping.md)