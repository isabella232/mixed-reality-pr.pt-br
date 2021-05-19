---
title: Reconhecimento de cena
description: Saiba como desenvolver com a compreensão de cena para o HoloLens, incluindo o SDK, as funcionalidades e os cenários de uso comuns.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Compreensão de cena, Mapeamento Espacial, Windows Mixed Reality, Unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, oclusão, SDK
ms.openlocfilehash: 06a4fdb6f3ad777c47151950acbd4ccdec9935ca
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143589"
---
# <a name="scene-understanding"></a>Reconhecimento de cena

A compreensão de cena fornece aos desenvolvedores de Realidade Misturada uma representação de ambiente estruturada e de alto nível projetada para tornar o desenvolvimento para aplicativos com conhecimento ambiental intuitivo. A compreensão de cena faz isso combinando o poder dos runtimes [](spatial-mapping.md) de realidade misturada existentes, como o mapeamento espacial altamente preciso, mas menos estruturado e os novos runtimes orientados por IA. Combinando essas tecnologias, a compreensão de cena gera representações de ambientes 3D semelhantes aos que você pode ter usado em estruturas como Unity ou ARKit/ARCore. O ponto de entrada Noções básicas de cena começa com um Observador de Cena, que é chamado pelo seu aplicativo para calcular uma nova cena. Atualmente, a tecnologia pode gerar três categorias de objeto distintas, mas relacionadas:

* Malhas simplificadas do ambiente watershes que inferem a estrutura da sala planar sem confusão
* Regiões de plano para posicionamento que chamamos de Quads
* Um instantâneo da malha [de mapeamento](spatial-mapping.md) espacial que se alinha com os dados Quads/Water spatial que superfíciemos

![Malha de mapeamento espacial, superfícies planar rotuladas, malha water spatial](images/SUScenarios.png)

Este documento destina-se a fornecer uma visão geral do cenário e esclarecer a relação que a Compreensão de cena e o mapeamento espacial compartilham. Se você quiser ver o Reconhecimento de Cena em ação, confira nossa demonstração de vídeo [Designing Holograms – Spatial Awareness]() abaixo:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="developing-with-scene-understanding"></a>Desenvolvendo com o Entendimento de Cena

Este artigo serve apenas para introduzir o runtime e os conceitos do Scene Understanding. Se você estiver procurando documentação sobre como desenvolver com o Entendimento de Cena, talvez esteja interessado nos seguintes artigos:

[Visão geral do SDK de Compreensão de Cena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

Você pode baixar o aplicativo Exemplo de Compreensão de Cena no site do GitHub de exemplo:

[Exemplo de compreensão de cena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Se você não tiver um dispositivo e quiser acessar cenas de exemplo para experimentar o Entendimento de Cena, haverá cenas na pasta de ativos de exemplo:

[Cenas de exemplo de compreensão de cena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>.

Se você estiver procurando detalhes específicos sobre como desenvolver com o Entendimento de Cena, confira a documentação de visão geral do [SDK de](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) Compreensão de Cena.

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

![Ilustrações de cenários comuns de uso de mapeamento espacial: Posicionamento, Oclusão, Física e Navegação](images/sm-concepts-1000px.png)<br>
*Cenários comuns de uso de mapeamento espacial: posicionamento, oclusão, física e navegação.*

<br>

Muitos dos principais cenários para aplicativos com conhecimento ambiental podem ser abordados pelo mapeamento espacial e pela compreensão de cena. Esses principais cenários incluem posicionamento, oclusão, física e assim por diante. Uma diferença principal entre a compreensão de cena e o mapeamento espacial é uma troca de precisão máxima e latência para estrutura e simplicidade. Se seu aplicativo exigir a menor latência possível e os triângulos de malha que somente você deseja acessar, use o Mapeamento Espacial diretamente. Se você estiver fazendo um processamento de nível superior, considere alternar para o modelo de compreensão de cena, pois ele deve fornecer um superconjunto de funcionalidades. Você sempre terá acesso aos dados de mapeamento espacial mais completos e precisos possíveis, pois a Compreensão de cena fornece um instantâneo da malha de mapeamento espacial como parte de sua representação.

As seções a seguir revisitam os principais cenários de mapeamento espacial no contexto do novo SDK de Compreensão de cena.

### <a name="placement"></a>Posicionamento

A compreensão de cena fornece novas construções projetadas para simplificar cenários de posicionamento. Uma cena pode computar primitivos chamados SceneQuads, que descrevem superfícies planas nas quais os hologramas podem ser colocados. SceneQuads foram projetados em torno do posicionamento e descrevem uma superfície 2D e fornecem uma API para posicionamento nessa superfície. Anteriormente, ao usar a malha de triângulo para fazer o posicionamento, era necessário verificar todas as áreas do Quad e fazer o preenchimento/pós-processamento de orifício para identificar bons locais para o posicionamento do objeto. Isso nem sempre é necessário com o quads, pois a cena que entende o tempo de execução infere quais áreas quádruplas não foram examinadas e invalida áreas que não fazem parte da superfície.

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


Se seu aplicativo pretende colocar hologramas 2D ou 3D em estruturas rígidas de seu ambiente, a simplicidade e a conveniência do SceneQuads para posicionamento é preferível a computar essas informações da malha de [mapeamento espacial](spatial-mapping.md) . Para obter mais informações sobre este tópico, consulte a [referência do SDK de compreensão da cena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

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

Embora [a visualização](spatial-mapping.md#visualization) de mapeamento espacial possa ser usada para comentários em tempo real do ambiente, há muitos cenários em que a simplicidade dos objetos planar e waterfast fornece mais desempenho ou qualidade visual. As técnicas de projeção de sombra e de moagem descritas usando o mapeamento espacial podem ser mais desagradadas se projetadas nas superfícies planar fornecidas pelo Quads ou pela malha de water seta planora. Isso é especialmente verdadeiro para ambientes/cenários em que a pré-verificação completa não é ideal porque a cena inferiria e ambientes completos e suposições planar minimizarão os artefatos.

Além disso, o número total de superfícies retornadas pelo Mapeamento Espacial é limitado pelo cache espacial interno, enquanto a versão da compreensão de cena da malha mapeamento espacial pode acessar dados de mapeamento espacial que não são armazenados em cache. Por isso, a Compreensão de cena é mais adequada para capturar representações de malha para espaços maiores (por exemplo, maiores que uma única sala) para visualização ou processamento de malha posterior. A malha mundial retornada com EnableWorldMesh terá um nível consistente de detalhes, o que pode gerar uma visualização mais agradável se renderizada como wireframe.

### <a name="see-also"></a>Consulte Também

* [SDK de compreensão de cena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [Mapeamento espacial](spatial-mapping.md)