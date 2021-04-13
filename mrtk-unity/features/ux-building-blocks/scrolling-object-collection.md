---
title: Rolagem da coleção de objetos
description: Tipos de menu de visão geral MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, objeto de rolagem
ms.openlocfilehash: 0ed1d61aed203a5daa45c5d89990e66115cc3abb
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300111"
---
# <a name="scrolling-object-collection"></a>Rolagem da coleção de objetos

![Rolagem da coleção de objetos](../images/scrolling-collection/ScrollingCollection_Main.jpg)

A coleção de objetos de rolagem MRTK é um componente de UX que permite a rolagem do conteúdo 3D por meio de uma área de exibição independente. A movimentação de rolagem pode ser disparada pela interação de entrada próxima ou distante e pela paginação discreta. Ele dá suporte a objetos interativos e não interativos.

## <a name="getting-started-with-the-scrolling-object-collection"></a>Introdução à coleção de objetos de rolagem

### <a name="setting-up-the-scene"></a>Configurando a cena

1. Crie uma nova cena do Unity.
1. Adicione MRTK à cena navegando até o **Kit de ferramentas da realidade misturada**  >  **Adicionar à cena e configurar**.

### <a name="setting-up-the-scrolling-object"></a>Configurando o objeto de rolagem

1. Crie um objeto de jogo vazio na cena e altere sua posição para (0, 0, 1).
1. Adicione um componente de [coleção de objetos de rolagem](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) ao objeto Game.

    Quando a coleção de objetos de rolagem for adicionada, um colisor de caixa e um componente de [interação de proximidade Near](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) serão automaticamente anexados ao objeto de jogo raiz. Esses componentes permitem que o objeto de rolagem Ouça eventos de entrada de interação quase e longe, como um ponteiro de toque ou clique.  

    A coleção de objetos de rolagem MRTK tem dois elementos importantes que são criados como objetos de jogo filho na hierarquia de objetos de rolagem raiz:
    * `Container` -Todos os objetos de conteúdo de rolagem devem ser filhos do objeto de jogo do contêiner.
    * `Clipping bounds` -Se a máscara de conteúdo de rolagem estiver habilitada, o elemento limites de recorte garantirá que apenas o conteúdo rolável dentro de seus limites fique visível. O objeto de jogo limites de recorte tem dois componentes: um colisor de caixa desabilitada e uma [caixa de recorte](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).

![Rolando elementos da coleção de objetos](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>Adicionando conteúdo ao objeto de rolagem

A coleção de objetos de rolagem pode ser combinada com uma [coleção de objetos de grade](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) para o conteúdo de layout em uma grade de elementos alinhados que têm tamanho e espaçamento uniformes.

1. Crie um objeto de jogo vazio como um filho do contêiner de rolagem.
1. Adicione um componente de coleção de objetos de grade ao objeto Game.
1. Para uma rolagem de coluna única vertical, na guia Inspetor, configure a coleção de objetos de grade como segue:
    * **Número de colunas**: 1
    * **Layout**: coluna e linha
    * **Âncora**: superior esquerda
1. Altere a **largura** e a **altura** da célula de acordo com as dimensões dos objetos de conteúdo.
1. Adicione os objetos de conteúdo como filhos do objeto de grade.
1. Pressione **Atualizar coleção**.

![Layout de grade](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> Qualquer material de objeto de conteúdo de rolagem deve usar o [sombreador padrão MRTK](../rendering/MRTK-standard-shader.md) para que o efeito de recorte na área visível funcione corretamente.

> [!NOTE]
> Se a máscara de conteúdo de rolagem estiver habilitada, a coleção de objetos de rolagem adicionará um componente de [instância de material](../rendering/material-instance.md) a qualquer objeto de conteúdo que tenha um processador anexado. Esse componente é usado para gerenciar o tempo de vida dos materiais em instância e melhorar o desempenho da memória.

### <a name="configuring-the-scrolling-viewable-area"></a>Configurando a área visível de rolagem

1. Para a rolagem vertical por meio de uma única coluna de objetos, na guia Inspetor, configure a coleção de objetos de rolagem como segue:
    * **Células por camada**: 1
    * Escolha o número de **camadas por página** de acordo com o número desejado de linhas visíveis
1. Altere a **largura**, a **altura** e a **profundidade** da célula de página de acordo com as dimensões dos objetos de conteúdo.

Observe como os objetos de conteúdo pertencentes à área visível de rolagem agora estão desabilitados, enquanto os objetos que interseccionam o wireframe de rolagem podem ser parcialmente mascarados pelo primitivo de recorte.

![Área visível](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>Testando a coleção de objetos de rolagem no editor

1. Pressione reproduzir e segurar a barra de espaço para mostrar uma medida de simulação de entrada.
1. Mova a mão até que o colisador de rolagem ou qualquer conteúdo interativo de rolagem esteja em foco e dispare a movimentação de rolagem clicando e arrastando para cima e para baixo com o mouse esquerdo.

## <a name="controlling-the-scrolling-object-from-code"></a>Controlando o objeto de rolagem do código

A coleção de objetos de rolagem MRTK expõe alguns métodos públicos que permitem mover o contêiner de rolagem ajustando sua posição de acordo com a `pagination` configuração de propriedades.

Um exemplo de como acessar a interface de paginação da coleção de objetos de rolagem está disponível para uso na ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` pasta. O script de exemplo de [paginação rolável](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) pode ser vinculado a qualquer coleção de objetos de rolagem existente na cena. O script pode ser referenciado por componentes de cena expondo eventos de Unity (por exemplo, o [botão MRTK](button.md)).

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }       
}
```

## <a name="scrolling-object-collection-properties"></a>Propriedades da coleção de objetos de rolagem

| Geral                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Direção da rolagem             | A direção na qual o conteúdo deve rolar.|

| Paginação                   |               Descrição                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Células por camada               | Número de células em uma linha na exibição de rolagem para cima ou no número de células em uma coluna na exibição de rolagem esquerda-direita.                                                                                                         |
| Camadas por página               | Número de camadas visíveis na área de rolagem.                                                                                                                                                                         |
| Célula da página                    | Dimensões da célula de paginação.                  |

| Configurações avançadas            |                  Descrição                                                                                                                                                                                    |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Modo de edição de máscara               | Edite modos para definir os limites de mascaramento da caixa de recorte. Escolha ' automático ' para usar automaticamente os valores de paginação. Escolha ' manual ' para habilitar a manipulação direta do objeto da caixa de recorte.|
| Modo de edição do colisor           | Edite modos para definir os limites de conflito de interação da rolagem. Escolha ' automático ' para usar automaticamente os valores de paginação. Escolha ' manual ' para habilitar a manipulação direta do colisor.|
| Pode rolar                   | Habilita/desabilita a rolagem com interação quase/longe.                  |
| Usar em pré-renderização            | Alterna se o scrollingObjectCollection usará o evento OnPreRender da câmera para gerenciar a visibilidade do conteúdo.                  |
| Curva de paginação             | Curva de animação para paginação.                  |
| Comprimento da animação             | A quantidade de tempo (em segundos) que o PaginationCurve levará para avaliar.                  |
| Limite de rolagem Delta à mão  | A distância, em metros, o ponteiro atual pode viajar ao longo da direção da rolagem antes de disparar um arrasto de rolagem.                  |
| Distância do toque frontal         | Distância, em metros, para posicionar um plano XY local usado para verificar se uma interação de toque começou na frente da exibição de rolagem.                  |
| Limite de liberação            | Retire o valor, em metros, dos limites de rolagem necessários para a transição do toque envolvido para o lançamento.                  |

| Velocidade |               Descrição                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tipo de velocidade       | O tipo desejado de queda de velocidade para o Rolador.                                                                                        |
| Multiplicador Velocity     | Quantidade de velocidade (extra) a ser aplicada ao Rolador.                                                                                                                                                        |
| Redução de velocidade     | Quantidade de queda aplicada à velocidade. |
| Multiplicador de retorno     | Multiplicador para adicionar mais retorno à rolagem de uma lista ao usar queda por quadro ou queda por item. |

| Opções de depuração |            Descrição                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Máscara habilitada       | Modo de visibilidade do conteúdo de rolagem. O valor padrão irá mascarar todos os objetos fora da área de rolagem visível.                                                                                        |
| Mostrar planos de limite     | Se for true, o editor renderizará os planos de limite de liberação de toque em volta dos limites de rolagem.                                                                                                                                                        |
| Depurar paginação     | Use esta seção para depurar a paginação de rolagem durante o tempo de execução. |

| Eventos|    DESCRIÇÃO                                                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ao clicar em       | Evento disparado quando o colisador de fundo da rolagem ou qualquer um de seus conteúdos interativos recebe um clique.                                                                                        |
| No toque iniciado     | Evento disparado quando o colisador de fundo da rolagem ou qualquer um de seus conteúdos interativos recebe um toque próximo à interação.                                                                                                                                                        |
| No toque encerrado     | Evento disparado quando uma interação de toque ativo é encerrada com o ponteiro de interação próximo que atravessa um dos planos de limite de liberação. |
| Na dinâmica iniciada     | Evento disparado quando o contêiner de rolagem começa a ser movido por interação, velocidade fallofff ou paginação. |
| No impulso encerrado     | Evento disparado quando o contêiner de rolagem para de ser movido por interação, velocidade fallofff ou paginação. |

## <a name="scrolling-example-scene"></a>Cena de exemplo de rolagem

A cena de exemplo **ScrollingObjectCollection. Unity** consiste em três exemplos roláveis, cada um com uma configuração de queda de velocidade diferente. A cena de exemplo contém paredes para mostrar o comportamento de posicionamento da superfície que está desabilitado por padrão na hierarquia. A cena de exemplo pode ser encontrada na ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` pasta.

![Cena de exemplo de coleção de objetos de rolagem](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>Exemplo de rolagem pré-fabricados

Para sua conveniência, dois pré-fabricados de coleta de objetos de rolagem estão disponíveis para uso. O exemplo de pré-fabricados pode ser encontrado na ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` pasta.

![Rolando a coleção de objetos pré-fabricados](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>Confira também

* [Primitivo de recorte](../rendering/clipping-primitive.md)
* [Instância de material](../rendering/material-instance.md)
* [Sombreador padrão](../rendering/MRTK-standard-shader.md)
* [Coleção de objetos](object-collection.md)
