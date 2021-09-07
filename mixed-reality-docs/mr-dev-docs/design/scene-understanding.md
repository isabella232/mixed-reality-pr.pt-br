---
title: Reconhecimento de cena
description: saiba como desenvolver com compreensão de cena para HoloLens, incluindo o SDK, os recursos e os cenários de uso comuns.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: compreensão da cena, mapeamento espacial, Windows Mixed Reality, Unity, headset de realidade misturada, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, oclusão, SDK
ms.openlocfilehash: 6d950fca4211aef659b1f957ca5e7135ac9764ac
ms.sourcegitcommit: 6b8ccb881fbbdaa5119841eac528e29d7b49bd04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2021
ms.locfileid: "123557313"
---
# <a name="scene-understanding"></a>Reconhecimento de cena

O reconhecimento de cena fornece aos desenvolvedores de Realidade Misturada uma representação de ambiente estruturada e de alto nível, projetada para tornar intuitivo o desenvolvimento de aplicativos ecologicamente corretos. O entendimento da cena faz isso combinando o poder dos tempos de execução de realidade misturados existentes, como o [mapeamento espacial](spatial-mapping.md) altamente preciso, mas menos estrutura, e novos tempos de execução orientados a ia. Ao combinar essas tecnologias, a compreensão da cena gera representações de ambientes 3D semelhantes aos que você pode ter usado em estruturas como Unity ou ARKit/ARCore. O ponto de entrada de compreensão da cena começa com um observador de cena, que é chamado pelo seu aplicativo para computar uma nova cena. Hoje, a tecnologia pode gerar 3 categorias de objeto diferentes, mas relacionadas:

* Malhas de ambiente Watertight simplificadas que inferem na estrutura de sala planar sem aglomeração
* Regiões de plano para posicionamento que chamamos de quatro processadores
* Um instantâneo da malha de [mapeamento espacial](spatial-mapping.md) que se alinha com os dados do quads/Watertight que fazemos

![Malha de mapeamento espacial, superfícies de planar rotuladas, malha Watertight](images/SUScenarios.png)

Este documento destina-se a fornecer uma visão geral do cenário e esclarecer a relação que a cena compreende e o compartilhamento de mapeamento espacial. se você quiser ver a compreensão da cena em ação, confira nossa demonstração de vídeo sobre **conscientização Hologramas espacial** abaixo:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

## <a name="developing-with-scene-understanding"></a>Desenvolvendo com compreensão da cena

Este artigo só serve para apresentar a cena que entende o tempo de execução e os conceitos. Se você estiver procurando documentação sobre como desenvolver com a compreensão da cena, talvez esteja interessado nos seguintes artigos:

[Visão geral do SDK de compreensão da cena](../develop/unity/scene-understanding-SDK.md)

você pode baixar o aplicativo de exemplo de compreensão da cena no site de exemplo GitHub:

[Exemplo de compreensão da cena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Se você não tiver um dispositivo e desejar acessar cenas de exemplo para experimentar a compreensão da cena, há cenas na pasta de ativos de exemplo:

[Cenas de exemplo de compreensão de cena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>.

Se você estiver procurando detalhes específicos sobre o desenvolvimento com a compreensão da cena, consulte a documentação [visão geral do SDK de compreensão da cena](../develop/unity/scene-understanding-SDK.md) .

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

A compreensão da cena fornece novas construções projetadas para simplificar os cenários de posicionamento. Uma cena pode computar primitivos chamados SceneQuads, que descrevem superfícies simples nas quais os hologramas podem ser colocados. Os SceneQuads foram projetados para o posicionamento e a descrição de uma superfície 2D e fornecem uma API para posicionamento nessa superfície. Anteriormente, ao usar a malha de triângulo para fazer o posicionamento, era necessário verificar todas as áreas do Quad e fazer o preenchimento/pós-processamento de orifício para identificar bons locais para o posicionamento do objeto. Isso nem sempre é necessário com o quads, pois a cena que entende o tempo de execução infere quais áreas quádruplas não foram examinadas e invalida áreas que não fazem parte da superfície.

:::row:::
    :::column:::
       ![SceneQuads com inferência desabilitada, capturando áreas de posicionamento para regiões digitalizadas.](images/SUQuads.png)<br>
       **Imagem #1** -SceneQuads com inferência desabilitada, capturando áreas de posicionamento para regiões digitalizadas.
    :::column-end:::
        :::column:::
       ![Quatro processadores com inferência habilitada, o posicionamento não é mais limitado a áreas digitalizadas.](images/SUWatertight.png)<br>
        **#2 de imagem** -quads com inferência habilitada, o posicionamento não está mais limitado a áreas digitalizadas.
    :::column-end:::
:::row-end:::

<br>


Se seu aplicativo pretende colocar hologramas 2D ou 3D em estruturas rígidas de seu ambiente, a simplicidade e a conveniência do SceneQuads para posicionamento é preferível a computar essas informações da malha de [mapeamento espacial](spatial-mapping.md) . Para obter mais informações sobre este tópico, consulte a [referência do SDK de compreensão da cena](../develop/unity/scene-understanding-SDK.md)

**Observação** Para o código de posicionamento herdado que depende da malha de mapeamento espacial, a malha de mapeamento espacial pode ser computada junto com SceneQuads definindo a configuração EnableWorldMesh. Se a API de compreensão da cena não atender aos requisitos de latência do seu aplicativo, recomendamos que você continue a usar a [API de mapeamento espacial](spatial-mapping.md#placement).

### <a name="occlusion"></a>Oclusão

O [mapeamento espacial oclusão](spatial-mapping.md#occlusion) permanece o modo menos latente de capturar o estado em tempo real do ambiente. Embora isso possa ser útil para fornecer oclusão em cenas altamente dinâmicas, talvez você queira considerar a compreensão da cena para o oclusão por vários motivos. Se você usar a malha de mapeamento espacial gerada pela compreensão da cena, poderá solicitar dados do mapeamento espacial que não seria armazenado no cache local e que não está disponível nas APIs de percepção. Usar o mapeamento espacial para oclusão juntamente com malhas Watertight fornecerá valor extra, especificamente a conclusão da estrutura de sala não verificada.

Se seus requisitos puderem tolerar a maior latência de compreensão da cena, os desenvolvedores de aplicativos devem considerar o uso da malha de compreensão Watertight da cena e a malha de mapeamento espacial em harmonia com representações planares. Isso forneceria um cenário "o melhor de ambos os mundos", em que simplificava a Watertight oclusão é casado com uma geometria mais realista que fornece os mapas oclusão mais realistas possíveis.

### <a name="physics"></a>Física

O entendimento da cena gera malhas Watertight que decompõem o espaço com a semântica, especificamente para resolver muitas limitações na física que as malhas de mapeamento espacial impõem. As estruturas Watertight garantem que as conversões de raio de física sejam sempre pressionadas, e a decomposição semântica permite uma geração mais simples de malhas de NAV para navegação em interno. Conforme descrito na seção sobre [oclusão](#occlusion), a criação de uma cena com EnableSceneObjectMeshes e EnableWorldMesh produzirá a malha de conclusão mais física possível. A propriedade Watertight da malha do ambiente impede que testes de colisão falhem nas superfícies. Os dados de malha garantirão que a física esteja interagindo com todos os objetos da cena e não apenas com a estrutura de salas.

### <a name="navigation"></a>Navegação

As malhas de planar decomposta por classe semântica são construções ideais para navegação e planejamento de caminho, facilitando muitos dos problemas descritos na visão geral de [navegação de mapeamento espacial](spatial-mapping.md#navigation) . Os objetos SceneMesh computados na cena são descompostos por tipo de superfície, garantindo que a geração de malha de NAV seja limitada a superfícies que podem ser performadas. Devido à simplicidade das estruturas baixas, a geração de malha de navegação dinâmica em mecanismos 3D, como o Unity, é atingível dependendo dos requisitos em tempo real.

A geração de malhas de navegação precisas ainda requer pós-processamento, ou seja, os aplicativos ainda precisam projetar occluders no chão para garantir que a navegação não passe por resíduos/tabelas e assim por diante. A maneira mais precisa de fazer isso é projetar os dados de malha mundial, que será fornecido se a cena for computada com o sinalizador EnableWorldMesh.

### <a name="visualization"></a>Visualização

Embora a [visualização de mapeamento espacial](spatial-mapping.md#visualization) possa ser usada para comentários em tempo real do ambiente, há muitos cenários em que a simplicidade dos objetos planar e Watertight fornece mais desempenho ou qualidade visual. A projeção de sombra e técnicas de aterramento que são descritas usando o mapeamento espacial podem ser mais agradáveis se projetadas nas superfícies do planar fornecidas por quads ou pela malha Watertight do planar. Isso é especialmente verdadeiro para ambientes/cenários em que a pré-verificação completa não é ideal, pois a cena inferirá, e ambientes completos e suposições de planar minimizarão artefatos.

Além disso, o número total de superfícies retornado pelo mapeamento espacial é limitado pelo cache espacial interno, enquanto a versão de compreensão da cena da malha de mapeamento espacial pode acessar dados de mapeamento espacial que não são armazenados em cache. Por isso, a compreensão da cena é mais adequada à captura de representações de malha para espaços maiores (por exemplo, mais de um único espaço) para visualização ou processamento de malha adicional. A malha mundial retornada com EnableWorldMesh terá um nível consistente de detalhes em todo o mundo, o que pode gerar uma visualização mais agradável se for renderizado como wireframe.

### <a name="see-also"></a>Consulte Também

* [SDK de compreensão da cena](../develop/unity/scene-understanding-SDK.md)
* [Mapeamento espacial](spatial-mapping.md)