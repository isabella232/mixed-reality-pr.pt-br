---
title: Orientador de mão
description: Saiba como as mãos 3D são disparadas usando o direito de aprendizado quando o sistema não detecta as mãos do usuário para ajudar a ajudá-las.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Realidade mista do Windows, design, direito à mão, headset de imersão, MRTK, mãos, ajuda, mãos, headsets de realidade misturada, headset de realidade mista do Windows, Headset virtual realismo, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: ec302cecb106b339828adf1c8777c2ea7ec7fa30
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300041"
---
# <a name="hand-coach"></a>Orientador de mão

![Exemplo: à mão](images/HandCoach/MRTK_handCoach.jpg)<br>

A mão do direito aciona as mãos modeladas 3D quando o sistema não detecta as mãos do usuário. Esse recurso é um componente "ensinando" que ajuda a orientar o usuário quando o gesto não foi ensinado. Se os usuários não tiverem feito o gesto especificado por um período, as mãos entrarão em loop com um atraso. A mão da direita poderia ser usada para representar o pressionamento de um botão ou a seleção de um holograma.  

## <a name="hand-coach-provided"></a>Mão da direita fornecida

O modelo de interação atual representa uma ampla variedade de controles de gesto, como rolagem, seleção extrema e quase toque. Abaixo está uma lista completa dos gestos de mão existentes fornecidos no<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:

:::row:::
    :::column:::
       ![Exemplo de próximo Select](images/HandCoach/NearSelect.gif)<br>
       **Exemplo de próximo Select-used mostrar como selecionar botões ou fechar objetos que interagem**<br>
    :::column-end:::
    :::column:::
       ![Exemplo de toque de ar](images/HandCoach/AirTap.gif)<br>
        **Exemplo de toque de ar – usado para mostrar como selecionar objetos que estão distantes**<br>
    :::column-end:::
    :::column:::
       ![Exemplo de movimentação](images/HandCoach/Move.gif)<br>
       **Exemplo de movimentação de um objeto em espaço-usado para mostrar como mover um holograma no espaço**<br>
    :::column-end:::
    :::column:::
       ![Exemplo de rotação](images/HandCoach/Rotate.gif)<br>
       **Exemplo de Rotate-Used para mostrar como girar hologramas ou objetos**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Exemplo de escala](images/HandCoach/Scale.gif)<br>
       **Exemplo de escala-usado para mostrar como manipular hologramas para serem maiores ou menores**<br>
    :::column-end:::
    :::column:::
       ![Exemplo de Palm up](images/HandCoach/PalmUp.gif)<br>
        **Exemplo de Palm up – sugestão de uso, para exibir menus à mão**<br>
    :::column-end:::
    :::column:::
       ![Exemplo de HandFlip](images/HandCoach/HandFlip.gif)<br>
       **Exbordo de mão invertida – outra maneira de exibir menus à mão**<br>
    :::column-end:::
    :::column:::
       ![Exemplo de rolagem](images/HandCoach/Scoll.gif)<br>
       **Exemplo de Scroll – usado para rolar uma lista ou um documento longo**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Conceitos de design

Para Hololens2, criamos interações de mão com base em gestos de instinctual e de mão natural. Acreditamos que eles sejam intuitivos para a maioria dos usuários, portanto, não criamos momentos de aprendizado de gestos dedicados. Em vez disso, criamos o direito de acesso para ajudar os usuários a aprender sobre esses gestos se eles estiverem presos ou não estiverem familiarizados com as interações com o holograma. Sem um momento de aprendizado, sentimos que mostrar aos usuários como executar uma ação demonstrando que seria a melhor opção. Descobrimos que os usuários conseguiram descobrir o gesto, mas precisavam de uma pequena orientação. Se detectarmos que um usuário não interage com um objeto por um período, uma mão orientada seria disparada demonstrando o posicionamento correto e o local do dedo. 

### <a name="intuitive"></a>Simples

Ao animar as mãos, deve ser óbvio e não deve causar qualquer confusão. A animação de mão é uma representação do gesto que você está tentando solicitar que o usuário entenda. 

Por exemplo, se você quiser que um usuário pressione um botão, um botão à mão será disparado.

![Exemplo: mão com o direito ao lado de toque](images/HandCoach/NearSelect_unity.gif)<br>
*Mão da direita demonstrando perto de tocar em uma gem*  

### <a name="hand-scale"></a>Escala manual

Testamos vários tamanhos de mão com os menus da interface do usuário e achamos que, se as mãos fossem verdadeiras para o tamanho, ela deu uma sensação menacing. Se eles fossem muito pequenos, era difícil ver e entender o gesto. 

**Voz e mãos**

Não espere que os usuários possam ouvir um conjunto de instruções por meio de voz e assistir a instruções diferentes por meio da mão. Sequenciar suas instruções para ajudar os usuários a se concentrarem em relação à sua atenção para reduzir a sobrecarga do sensor.


## <a name="can-i-create-my-own"></a>Posso criar o meu próprio?

Sim! Incentivamos você a criar seu próprio gesto exclusivo para seu jogo e contribuir de volta para a Comunidade!
Fornecemos um arquivo Maya de um rigged Hand que pode ser usado para seu aplicativo, que pode ser baixado aqui: <a href="files/HandCoach_MRTK.zip"> baixar HandCoach_MRTK.zip </a>

![Exemplo de mãos animadas no Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Exemplo de mão animada ao investigar uma caixa no Maya*


**Ferramenta de criação recomendada**

Entre artistas 3D, muitos optam por usar o [Maya do Autodesk, que pode usar o HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar a maneira como os ativos são criados. O arquivo hands fornecido é um arquivo binário Maya, portanto, é recomendável usar Maya para animar e exportar as mãos. Se você preferir usar outro programa 3D, aqui está um <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Baixe HandCoachMRTK_FBX.zip </a> para criar sua própria configuração de controlador. 

Se estiver usando o arquivo do Maya Hand disponível para download fornecido, é recomendável reduzir verticalmente as mãos no Unity para 0,6.

![Exemplo: mão de Rig do dispositivo em Maya](images/HandCoach/MayaExample.png)<br>
*Rigged hands*

### <a name="technical-specs"></a>Especificações técnicas

*   O arquivo de dois mãos está disponível no formato ASCII Maya
*    A mão direita e esquerda está disponível no formato binário Maya
*   Definir o arquivo Maya para 24 FPS
*   Dentro do arquivo, há uma mão esquerda e direita, que pode ser usada para dois gestos de mão ou de entrega única. A mão direita só estará visível por padrão.
*   É recomendável deixar um buffer de cerca de 10 quadros no início e no final para esmaecer
*   Se animar um objeto com um destino especificado, sua prática recomendada será animar para uma caixa padrão ou NULL.
*   Se a mão estiver animando um objeto físico, como uma caixa, sua melhor prática para não animar a tradução em Maya, mas esperar para animá-la no Unity ou no código.
*   A animação visível deve ser 1,5 segundos para que todas as informações significativas sejam transmitidas
*   Quando você sentir satisfeito com sua animação:
    *   Selecionar todas as junções e distortar quadros-chave
    *   Exclua os controladores, selecione as junções e a malha e exporte como um FBX
    *  Se houver várias animações, você poderá usar o exportador de jogos interno do Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Exportando do Maya

Depois de estar satisfeito com sua animação
* Selecionar todas as junções: selecionar hierarquia de >

     ![Exemplo: hierarquia no menu](images/HandCoach/Hierarchy.png)<br>
* Distortar sua animação: alternar para animação > chave > animação de torta

     ![Exemplo: distortar local do menu de animação](images/HandCoach/BakeAnimation.png)<br>
* Excluir o dispositivo de controlador: contorno > MainR_Grp ou MainL_Grp

     ![Exemplo: local do menu de equipamentos do controlador](images/HandCoach/ControllerRig.png)<br>

* Exportar como FBX: selecione JNT + malha: arquivo > exportar seleção (caixa de opção) > exportar seleção

     ![Exemplo: exportar local do menu de seleção](images/HandCoach/OptionBox.png)<br>

     ![Exemplo: local do menu](images/HandCoach/SelectionExport.png)<br>

     ![Exemplo: local do menu de opções de exportação](images/HandCoach/FBXSelection.png)<br>


 Ao exportar como um FBX e trazido para o Unity, dimensione as mãos para 0,6. Descobrimos que esse foi um equilíbrio perfeito para a exibição das mãos. 

![Exemplo: configurações de Unity](images/HandCoach/HandHintScale.png)<br>
*Configurações de Unity para HandCoach_R pré-fabricado encontradas em MRTK*


## <a name="implementing-hands-into-your-unity-project"></a>Implementando mãos em seu projeto do Unity

### <a name="best-practices"></a>Práticas recomendadas

* Sugerimos reduzir verticalmente as mãos no Unity para 0,6
* As mãos devem ser executadas duas vezes e, se não forem concluídas, passarão continuamente em loop até que o gesto seja concluído. As mãos devem ser repetidas duas vezes para garantir que o usuário tenha tempo para se registrar e ver o gesto. As mãos devem aparecer e desaparecer entre os loops. 
 *  Se as mãos do usuário estiverem visíveis por câmeras HL2, mas os usuários não estiverem fazendo a interação necessária, as mãos serão exibidas após 10 segundos.
*   Se as mãos do usuário não estiverem visíveis por câmeras HL2, as mãos aparecerão após 5 segundos.  
*   Se as mãos do usuário forem visivelmente rastreadas por câmeras HL2s no meio da animação, a animação será concluída e desaparecer.
*   Se você estiver incluindo a voz, sugerimos que ela corresponda ao gesto da mão.
*   Se você tiver ensinado as mãos pelo menos uma vez, repita o gesto se detectar que o usuário está preso.
*   Se as posições de dedos/mãos específicas forem críticas, verifique se os usuários podem ver claramente essas nuances na animação. Experimente Angling as mãos para que as partes mais importantes fiquem claramente visíveis. 
* Se você perceber distorção nas mãos, precisará ir para as configurações de qualidade do Unity aumentar o número de Bones. 
 Acesse as configurações de projeto de > de edição do Unity > qualidade > outros pesos do Blend >. Verifique se "4 Bones" estão selecionados para ver as junções suaves.

   ![Exemplo: janela de configurações do projeto](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>O que evitar

* Dimensionar as mãos muito grandes
* colocar as mãos muito próximas ao usuário
* As mãos só devem ser ensinadas uma vez. O excesso de ensino pode causar confusão e bagunças
* Colocando-o no Unity, baixe o MRTK mais recente aqui: https://github.com/microsoft/MixedRealityToolkit-Unity
  * Material: Teaching_Hand2
  * Scripts: consulte as diretrizes do MRTK para o <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> MRTK Hand </a>
  * Configuração por projeto
    * Cena definida como UWP: a instrução pode ser encontrada no [projeto do Unity de configuração](../develop/unity/Configure-Unity-Project.md) para o Windows Mixed Reality

## <a name="see-also"></a>Confira também

* [Interação-conceitos básicos](interaction-fundamentals.md)
* [Processo de criação de ativos](asset-creation-process.md)
* [Gestos](./interaction-fundamentals.md)
* [Instalar as ferramentas](../develop/install-the-tools.md)
* [Configurar projeto do Unity](../develop/unity/Configure-Unity-Project.md)
* [Visão geral do desenvolvimento do Unity](../develop/unity/unity-development-overview.md)
* [MRTK 101](../out-of-scope/mrtk-101.md)